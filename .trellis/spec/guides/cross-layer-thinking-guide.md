# 跨层变更

事件、配置、持久化数据或 RPC 变更需要从生产者追踪到全部消费者。类型与语义归属见[架构](../../../docs/architecture.md)、[子系统索引](../../../docs/subsystems/README.md)和[远程 API 防御规则](../../../docs/defensive-patterns/remote-and-api.md)。

## 追踪数据

先写明输入在哪里解析、谁拥有业务语义、何时提交，以及哪些读取者消费结果。常见路径是工具或命令 → 领域服务 → Session 事件 → 投影 → API/SDK → 客户端；配置变更还需检查 profile、bundle 和 overlay。

| 路径 | 已有示例 | 必查事项 |
| --- | --- | --- |
| 持久状态到 UI | [Goal 服务](../../../packages/goal/goal/src/index.ts)、[Goal 客户端](../../../packages/client/ui-goal/src/client/index.ts) | 持久目标和进程内激活状态分别有所有者，成功响应不建立第二份领域状态 |
| 日志到增量读取 | [标题服务](../../../packages/session/session-title/src/index.ts)、[投影测试](../../../packages/session/session-title/tests/projection.spec.ts) | 日志回放、延迟注册、checkpoint 和卸载得到一致结果 |
| SDK 协议到 Python | [SDK 协议](../../../packages/sdk/protocol/README.md)、[Python 模型](../../../python/sdk/src/deepseek_harness/models.py) | 字段别名、可选值、错误分类及两种语言的预期输出一致 |

## 变更检查

- 模型可见输入能够从 Session 日志重建；仅用于绘制的 UI 数据不写入日志。
- 在模型 JSON、配置、文件、持久化、worker、进程和 wire 输入处校验；同进程的强类型调用不增加重复的敌意输入防御。
- 先查现有类型与纯类型入口，再修改声明合并表、判别联合和消费者；闭合联合使用 `assertNever`，可扩展联合保留有说明的默认路径。
- 持久化类型变更按[审核流程](../../../docs/cookbook/reviewing-persistence-type-changes.md)确认；Session 格式以[状态页](../../../docs/session-format-status.md)为准。
- 循环、Session 生命周期和事件表变更同时覆盖 TypeScript 与 Python SDK；外部可感知的不兼容变更使用[升级指南流程](../../../.agents/skills/dsh-create-upgrade-guide/SKILL.md)。

## 验证

选取覆盖实际组合的测试，并验证重放、重连、失败、撤销与真实输出中受影响的路径。模型或产品行为需要可离线重放的记录快照；[测试策略](../../../docs/testing.md)决定其归属，不能以局部类型检查代替行为证据。
