# 应用挂载与响应绑定

适用于修改 boot 交接、框架 hook、scope 标准数据和重新连接。入口为 [client apply 与 mount](../../../../packages/client/ui-renderer/src/client/index.ts)、[bind](../../../../packages/client/ui-renderer/src/client/bind.ts)、[bindings](../../../../packages/client/ui-renderer/src/client/bindings.tsx)及 [scoped-slots](../../../../packages/client/ui-renderer/src/client/scoped-slots.tsx)。

## Boot 到 React

Web boot kernel 等完整客户端 roster 和启动审计完成后调用 `ctx.uiRenderer.mount(container)`。存在 `[data-dsh-boot]` 时先 hydration 保留 loading DOM，再切到应用；没有 loading DOM 时创建 root 并同步提交。mount 返回的 disposer 负责 unmount，不能只删除容器内容而留下 React root。

本包安装 SlotRegistry 与 renderer，唯一 Context 级 root 渲染在框架内部。业务插件只注册组件和 Factory，不直接导入 renderer 或用另一个 React root 插进应用。

## Observable 到 Hook

对象层提供 `getSnapshot`、`subscribe` 的裸来源；renderer 才把它们绑定为 selector hook。`bindSnapshotSelector` 保留来源方法的接收者与稳定订阅闭包，默认用 `Object.is` 比较。不要在对象层放 React hook，也不把 source 直接交给业务组件手工订阅。

来源对象是 hook 缓存的身份，未变化的 snapshot 必须复用引用。optional source 暂无值时仍保持 hook 调用顺序，不能因 Session 缺失就跳过 hook。keyed 来源的 key/member 解析沿既有适配，不能把字符串 member 当成 selector。

## Scope 与重连

`root`、`session`、`session-maybe` 的标准 props 由安装的 domain adapter 和当前位置 binding 合成；Session 选择语义属于 adapter 的业务所有者。renderer 不自行恢复 Session、扫描完整日志或在缺失时创建替代业务对象。

同 id 的新 Session Context 是新生命周期；store 与错误隔离不能仅按字符串 id 判断是否仍是旧实例。来源注册或撤销后要发布原子 binding 变化，让已经挂载的消费者也能获得当前数据。

React、React DOM、Cordis 与静态框架库依赖 Web shell 的共享模块身份。不能为了修一个动态包导入问题，把另一份 React 或 ui-slots 私有打进 bundle；模块声明以[客户端指令](../../../../packages/client/AGENTS.md#shared-modules-and-the-module-graph)为准。

## 验证选择

[app](../../../../packages/client/ui-renderer/tests/app.client.spec.tsx)验证 boot DOM 交接；[bind](../../../../packages/client/ui-renderer/tests/bind.client.spec.tsx)与 [keyed-hook-member](../../../../packages/client/ui-renderer/tests/keyed-hook-member.client.spec.tsx)验证订阅及 selector；[reconnect](../../../../packages/client/ui-renderer/tests/reconnect.client.spec.tsx)、[session-provider](../../../../packages/client/ui-renderer/tests/session-provider.client.spec.tsx)验证重连和缺失 scope。改变 assembled UI 时按[客户端验证阶梯](../../../../packages/client/AGENTS.md#before-you-push-the-local-check-ladder)补组合证据。
