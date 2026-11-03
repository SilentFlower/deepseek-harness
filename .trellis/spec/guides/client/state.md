# 状态与资源

领域对象、交互 store 和组件局部状态分别拥有不同寿命。详细规则见[客户端指令](../../../../packages/client/AGENTS.md)、[Web Client 架构](../../../../docs/subsystems/web-client.md)和[资源子系统](../../../../docs/subsystems/client-resources.md)。

## 数据通道

父组件已知的数据从 owner props 传入；仅当前组件需要的数据留在局部状态；跨入口共享或需要跨卸载保留的交互状态进入注册时声明的 store。Session、frame、连接等业务对象留在对象层，store 不复制它们。渲染依赖的外部可变值必须通过框架 hook 读取，派生值使用纯计算，避免另建订阅和镜像状态。

| 示例 | 阅读重点 |
| --- | --- |
| [设置 store 工厂](../../../../packages/client/ui-settings-general/src/client/shell-store.ts) | 声明 init 与完整 actions；实例由注册作用域创建和共享 |
| [Session 对象](../../../../packages/api/session-controller/src/client/sessions/session.ts) | 业务状态和读取生命周期留在对象层 |
| [Session 通知器](../../../../packages/api/session-controller/src/client/sessions/notifier.ts) | 用户动作、结构更新和可见流式更新各自的发布时机 |
| [资源注册与 hook](../../../../packages/client/resources/src/client/index.ts) | provider、资源 source 与统一 `useResource` 通道 |

组件通过 `props.useStore` 读取，通过 `props.actions` 修改。业务组件不调用 `useSyncExternalStore` 或手接 subscribe；注册私有响应值放进 inject 的 `hooks` compartment，由 renderer 生成 hook。observable 的对象和未变化时的 snapshot 引用均保持稳定。

## 生命周期

资源组件通过 `useResource` 使用现有缓存、pin 和轮询，不在功能组件中重建这些机制。异步请求需要保留其消费的 Session 或资源引用到完成；重连、替换和卸载使旧结果失效，不能把过期结果提交到新的对象。

effect 不用于把渲染可推导的状态写回父组件。布局测量必须说明 CSS 无法表达的原因、像素测量的必要性和注入 hook 的归属。

## 验证

参考[资源测试](../../../../packages/client/resources/tests/resources.client.spec.ts)与[资源注册测试](../../../../packages/client/resources/tests/apply.client.spec.ts)。按实际改动覆盖并发消费者、缓存复用、对象替换、重连和卸载。既要验证渲染更新，也要验证消费者释放后监听、请求和 pin 终止。
