# 工具注册、作用域与 Step 准入

适用于新增工具、条件可用性、Agent 限制或 executor 选择。实现入口为 [ToolsService](../../../../packages/core/tools/src/index.ts)，定义与准入类型归 [contracts](../../../../packages/core/tools/src/contracts.ts)。工具编写步骤见[添加工具](../../../../docs/cookbook/adding-a-tool.md)。

## 注册与可见性

工具通过调用者的 `ctx.tools.register()` 注册并随其 fiber 撤销；Agent 私有贡献使用 `agent.ctx`。同作用域同名冲突拒绝，较近作用域可遮蔽继承贡献。限制在允许的作用域内相交，不能用根 Context 的全局变更模拟一个 Agent 的限制。

`definitions`、`schemas` 和 `get` 不带 `toolSet` 时只检查已注册内容，不执行条件，也不能据此认定条件工具可执行。执行路径使用 `executable`，不能通过直接取 definition 再调用 body 绕过准入和策略。

## 一步共用一个选择

`resolve({ agent, modelSelection, signal })` 每步评估一次 `when`，完整成功后交出 `ResolvedToolSet`。条件只决定是否参与，不执行工具工作、不改注册；抛错是 `TOOL_ACTIVATION_FAILED`，不能吞成普通不可用。

提示词声明、Native 调用和 PTC 内部子调用使用同一个 set，重试继续复用；batch 结算后才 dispose。不能只从 schema 隐藏工具，却让执行器仍接受同名调用。

准入绑定确切 Agent 和原始注册。注销、增加限制、同名替换或 set 关闭后，尚未开始的调用不能复用旧许可；在途条件返回也不能复活已撤销贡献。没有 resolved set 的调用不准执行条件工具。

## Executor 的责任

每作用域只注册一个 executor，较近作用域决定选择。选中的 provider 卸载后，新 batch 必须报告不可用，不能静默改由祖先或另一个 provider 执行。已接受 batch 保留其选定 provider 到结算。

`describe()` 与 `execute()` 的输入输出归 [ToolExecutor](../../../../packages/core/tools/src/executor.ts)。只做呈现变换不能增减实际 callable 集合。不要在循环里按工具名称判断 Native/PTC 特例；传输差异留在各 executor。

## 验证选择

[activation](../../../../packages/core/tools/tests/activation.spec.ts)覆盖每步评估、失败、取消及旧注册失效；[scoped](../../../../packages/core/tools/tests/scoped.spec.ts)覆盖遮蔽、限制和撤销。executor 或声明发生变化时，加读 [Agent executor 组合](../../../../packages/core/agent-loop/tests/tool-executors.spec.ts)与 [tool updates](../../../../packages/core/agent-loop/tests/tool-updates.spec.ts)，验证模型声明和实际执行一致。
