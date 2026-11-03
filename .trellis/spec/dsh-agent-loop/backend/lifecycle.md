# Agent 创建、恢复与释放

适用于修改 Agent 工厂、初始化和卸载路径。消费者通过 `ctx.agents` 使用公开接口；具体循环留在本包，接口与事件定义归 [agent 包](../../../../packages/core/agent/src)。

## 修改入口

读 [AgentLoop](../../../../packages/core/agent-loop/src/index.ts) 的 `initializeAgent`、`createAgent` 和 `resumeWith`，再读[生命周期说明](../../../../packages/core/agent-loop/README.md#creation-and-teardown)。新增业务能力先选择[架构中的扩展点](../../../../docs/architecture.md#where-new-behavior-goes)，确需改变循环顺序时同步架构说明。

## 初始化必须保持的顺序

1. 在创建资源前接好调用者取消、调用者 fiber 和工厂卸载的清理责任；持久化句柄晚于取消返回时仍须关闭。
2. 保存构造阶段历史，进入 SessionStore，完成 `session/created`，再执行 setup 和其 commit。
3. 进入 AgentRegistry 并等待串行 `agent/created` 完成后，才允许已排队输入驱动循环。
4. 任一步失败都等待回滚完成；保留已存事件和恢复出的 inbox，不让失败的初始化启动新 turn。

Session 在 setup 中可写；`session/created` 的同步通知尚未完成时不可写。不要提前发布 Agent 来绕过 setup 所需的依赖，也不要把这些步骤拆成无顺序保证的兄弟 effect。

## 释放与同名实例

所有竞争的释放入口汇合到同一个等待结果：取消并等待驱动静止，释放 scope，关闭并排空持久化写句柄，最后移除 Agent 与 Session。写事件的监听和投影读取必须存活到驱动收尾完成；清理失败仍需继续释放其他资源，并向等待者报告失败。

detach 必须绑定进入注册表的确切对象。旧生命周期的 disposer 不得删除后来的同 id 实例。配置恢复只有遇到 `SessionPersistenceNotFoundError` 才转为首次创建；损坏、占用和后端错误不能变成空白 Session。

## 验证选择

| 修改点 | 必须保留的断言与证据入口 |
| --- | --- |
| setup、created、取消 | [resource-lifecycle](../../../../packages/core/agent-loop/tests/resource-lifecycle.spec.ts)：失败回滚、延迟资源和通知配对 |
| scope 与工厂卸载 | [scope-lifecycle](../../../../packages/core/agent-loop/tests/scope-lifecycle.spec.ts)、[shutdown-drain](../../../../packages/core/agent-loop/tests/shutdown-drain.spec.ts)：收尾先于资源释放 |
| 恢复与配置重载 | [resume](../../../../packages/core/agent-loop/tests/resume.spec.ts)、[config-session-id](../../../../packages/core/agent-loop/tests/config-session-id.spec.ts)：身份、持久化占用及原历史保留 |

异步路径用明确屏障制造交错，不能用等待若干微任务替代顺序断言。通用验证选择见[质量指南](../../guides/quality.md)。
