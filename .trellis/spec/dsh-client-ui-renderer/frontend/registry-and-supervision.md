# 注册所有权、Store 实例与错误监督

适用于修改 SlotRegistry、声明等待、store 释放及错误隔离。纯声明校验归 [SlotCore](../../../../packages/client/ui-slots/src/index.ts)，本包的 [registry](../../../../packages/client/ui-renderer/src/client/registry.ts)负责 Cordis effect、实例和 renderer 安装，React 错误隔离归 [scoped-slots](../../../../packages/client/ui-renderer/src/client/scoped-slots.tsx)。

## 保留调用者所有权

`register` 和 `registerFactory` 保持 prototype 方法，让 Cordis service proxy 在调用时绑定调用者的 `this.ctx`。改成实例箭头属性会把贡献固定到服务自身 fiber，破坏插件卸载；不能仅凭类型等价替换写法。

renderer、locale、root 数据和 scope adapter 的安装均由 effect 管理。重复安装按各自接口拒绝，卸载只移除自己安装的对象，不能解除后来替换的注册。

`slots.inject` 等实际 declaration epoch，而不是任意 entries 变化。声明已存在时同步运行，collapse 时撤销，后续重新声明时重建；等待者自身卸载要取消等待。多贡献的 generator setup 失败时必须逆序回滚已装部分，不能留半组界面。

## 两类 Store 生命周期

普通共享 handle 以挂载引用计数拥有实例，最后持有者卸载才释放。非 root 实例还绑定确切 scope Context，旧 Context 清理不能删除同 key 新 Context 的实例。scope 结束释放内存实例，不等于清除持久化状态。

Factory 独占 store 用 occurrence 作为身份。render 阶段记录保持弱引用，只有提交的 occurrence 进入强持有集合；effect 重放中的 setup/cleanup 必须幂等并保持预期实例身份，不能把一次 render 就当作长期挂载。独占 Factory store 的持久化限制见[props 与 store](../../dsh-client-ui-slots/frontend/props-and-stores.md)。

## 错误与授权

保留的 render 绑定每次检查所属 registration 仍存活及 children 授权。释放后的调用抛 `StaleAuthorizationError`，调用未授权 key 抛 `SlotOwnershipError`，不能因同名位置重建而自动续授权。

普通遮蔽类型的贡献渲染崩溃可 abdicate，让同一 cell 的下一个存活者接替；ledger 注册仍保留。chain 不按同样方式 abdicate。Factory occurrence 的崩溃不得撤销共享 Factory 定义；定义与 fallback 的错误归定义，调用者传入局部 Component 的错误归调用者。

错误隔离按贡献身份和 scope incarnation 重置。不要让 A 的崩溃状态黏到接替者 B，也不要把所有 occurrence 的错误都归给同一个 Factory。

## 验证选择

[registry](../../../../packages/client/ui-renderer/tests/registry.client.spec.ts)验证贡献、等待、store 与卸载；[stale-authorization](../../../../packages/client/ui-renderer/tests/stale-authorization.client.spec.tsx)验证过期绑定；[scoped-slots-real-core](../../../../packages/client/ui-renderer/tests/scoped-slots-real-core.client.spec.tsx)与 [factory-slots](../../../../packages/client/ui-renderer/tests/factory-slots.client.spec.tsx)验证真实 registry、接替和错误归属。修改异步关联路径时同时检查卸载后监听和实例均已释放。
