# Turn、Step 与模型请求

适用于修改 inbox、请求准备、提示词准入和工具续步。先读[循环实现](../../../../packages/core/agent-loop/src/agent.ts)的 `preStep`、`turn`、`step`、`prepareRequest`、`buildRequest`，完整提示词策略归[包文档](../../../../packages/core/agent-loop/README.md#turn-and-step-flow)。

## 一步的准备与提交

turn 在领取输入前打开；`agent/pre-step` 在 `step/start` 前运行。拒绝或首次改写为空的输入可以结束一个没有 step 的 turn，不能为此发送空模型请求。`agent/turn-stopping` 是串行通知；pre-step 和 request 等 waterfall 只有调用 `next()` 才继续委托。

每个 step 固定一次模型选择和 `ResolvedToolSet`，供组装、请求重试和工具执行共同使用。`agent/request` 不能偷偷改变已固定的 provider、model 或 reasoning effort；模型切换通过 `agent.model.select()` 进入后续 step。

异步请求控制调整和 `prepareCall()` 完成并检查取消后，才能提交 system 与接受的 user 消息。取消发生在这两个准备阶段时，不能留下已提交输入。重试不重新领取用户输入、不重新执行 pre-step；运行时上下文可刷新，但用户批次只提交一次。

## 请求必须能从日志重建

- 使用已准备调用的能力决定提示词准入，不从上一条 `request/context` 推断当前能力。system 节点的追加、清空和替换由[提示词投影](../../../../packages/core/system-prompt/src)规则处理。
- `request/header` 记录最终 config 和工具声明，`request/context` 记录实际路由能力；提示词由 `system/message` 表达，不能重新塞进 `header.system`。
- surface 替换及显式 `startsRequestSeries` 会影响请求系列。包装 pre-step 的 enter 决定时保留该标记，不能只返回新的 messages。
- 从 Session 派生并冻结请求；保留消息身份以复用冻结结果，取消 signal 仍必须可用。不能在送往适配器前额外注入未记录的模型内容。

## Inbox 与工具续步

[ReactLoopInbox](../../../../packages/core/agent-loop/src/inbox.ts)通过持久化 splice 更新两个待处理列表；领取也是日志操作。不要另建仅内存队列。`inject()` 可在 idle 时暂存上下文而不启动 turn；唤醒、steer 与取消后的排队行为按现有驱动实现保持。

工具执行传完整原始 batch、当前 step 的 `toolSet` 和最新并发配置；工具返回的上下文进入下一步队列。仅在工具 batch 已结算后释放该 step 的准入集合。工具结束 turn 时，也要保留期间新到的 steering 所要求的续步。

## 验证选择

请求变化对照 [request-reconstruction](../../../../packages/core/agent-loop/tests/request-reconstruction.spec.ts)、[request-freeze](../../../../packages/core/agent-loop/tests/request-freeze.spec.ts)和 [system-prompt-admission](../../../../packages/core/agent-loop/tests/system-prompt-admission.spec.ts)；检查取消时没有提前提交输入、重试不重复输入、实际请求能从日志恢复。

队列和续步变化对照 [inbox](../../../../packages/core/agent-loop/tests/inbox.spec.ts)、[runtime-context](../../../../packages/core/agent-loop/tests/runtime-context.spec.ts)和 [tool-order](../../../../packages/core/agent-loop/tests/tool-order.spec.ts)。涉及模型输出或 Session 事件时，按[质量指南](../../guides/quality.md)补齐快照与两个 SDK 消费者的验证。
