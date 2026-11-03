# 组件与 slots

界面插件通过注册组合；组件不持有 Context。完整语义见[客户端指令](../../../../packages/client/AGENTS.md)、[Slots 子系统](../../../../docs/subsystems/slots.md)和[组件防御规则](../../../../docs/defensive-patterns/client-components.md)。

## 声明与派生 props

父组件声明其 `children` 中允许渲染的 slot，注册者为这些位置贡献组件；只有 shell 渲染 root。可复用组合使用 `registerFactory()`，身份稳定的局部组件通过 factory slots 传递。组件 props 由 `PropsRuntime`、`PropsRenderSlots`、factory、store 和 inject 等派生类型组合，不手写框架已经定义的字段。

| 示例 | 阅读重点 |
| --- | --- |
| [GeneralSection](../../../../packages/client/ui-settings-general/src/client/GeneralSection.tsx) | 通过 `PropsRuntime` 与 `PropsRenderSlots` 获取授权的子位置 |
| [Goal 插件](../../../../packages/client/ui-goal/src/client/index.ts) | `apply` 负责注册与注入，组件接收数据、回调和 hooks compartment |
| [Goal 注入类型](../../../../packages/client/ui-goal/src/client/slots.ts) | Remote 结果、动作与私有 observable 的分工 |

注入只使用声明的依赖，提供普通数据与回调；ReactNode 通过 slot 组合。业务组件不读取 ctx、React Context、服务类或外部订阅对象。新数据先检查框架 hooks、声明的 store 和 inject 回调，无法表达时回到框架扩展点讨论。

## 包依赖与导出

UI 功能包不运行时导入另一功能包的实现，也不以 `dsh.client.external` 绕过依赖规则。共享行为通过服务、共享 UI 通过 slots，纯共享运行时代码归窄职责静态库。浏览器依赖与 Host 依赖分别声明，详细规则以客户端指令及校验器为准。

`/client` 的运行时导出限制在 Loader 所需项和规则允许的工厂；测试直接相对导入内部文件。现有代码不自动构成新增导出的许可。新增超出允许集合的值导出需要按客户端指令取得明确决定。

## 验证

检查每个 `renderSlot` 都获得声明授权，组件 key 对应实际身份，factory 组件身份在预期生命周期内稳定。参考 [Goal 客户端测试](../../../../packages/client/ui-goal/tests/user-text-rules.client.spec.ts)对内部实现的直接导入；运行受影响包的客户端测试与对应 Web 组合证据。
