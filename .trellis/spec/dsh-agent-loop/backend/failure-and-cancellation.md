# 流式结算、失败与取消

适用于修改请求重试、流式消息、工具异常和 turn 收尾。实现入口是 [ReactLoopAgent](../../../../packages/core/agent-loop/src/agent.ts)、[AssistantStreamAttempt](../../../../packages/core/agent-loop/src/assistant-stream.ts)及 [Session 工具恢复](../../../../packages/core/session/src/repair.ts)。

## 流式结果与日志

每个已启动的 assistant attempt 只有一个终结通知；成功的 committed 通知必须晚于对应 `assistant/message` 提交。失败、重试和无可保留内容的尝试写入 log-only 的 `assistant/attempt`，不能把它当作模型历史消息。

取消时保留已经交付的可保留内容，形成带 `interrupted: true` 的消息。组装或持久化结算失败时，终结状态必须反映未提交；不能让客户端把仅存在于实时流中的内容当作已保存消息。

## 重试归属

适配器的终结错误交给 `agent/request-error`，明确返回 retry 才重试。waterfall 中间件、工具和结果处理自身抛出的错误结束当前 turn，不能统一套模型重试。取消优先于重试决定；一个 turn 失败后，循环仍需能够处理后续输入。

`max-tokens` 在同一 turn 中保持，不得被后续正常 step 覆盖；被截断响应中的不完整工具调用不能执行。完整行为见[失败说明](../../../../packages/core/agent-loop/README.md#failure-and-cancellation)。

## 工具结果与安全恢复

| 已记录事实 | 收尾要求 |
| --- | --- |
| 取消阻止调用分派 | 记录配对的 call/result，结果为 `ABORTED_BEFORE_DISPATCH` |
| assistant 请求了工具，但没有 call 开始记录 | 缺失结果使用 `TOOL_NOT_STARTED` |
| 有 call 开始记录但没有已提交结果 | 使用 `TOOL_OUTCOME_UNKNOWN`，保留结果未知这一事实 |

先等待已启动分派结算，再补齐缺失结果；保留已提交结果和原始失败。结果未知时不能自动重新执行可能有副作用的操作。恢复失败也需要向调用者报告，不能只留下一个看似闭合的 turn。

`turn/end` 记录取消原因的可持久化副本，不能直接冻结或记录仍可能被传输库修改的 `AbortSignal.reason` 对象。

## 验证选择

[request-error](../../../../packages/core/agent-loop/tests/request-error.spec.ts)验证重试归属与取消优先级；[cancel](../../../../packages/core/agent-loop/tests/cancel.spec.ts)和 [tool-calls](../../../../packages/core/agent-loop/tests/tool-calls.spec.ts)覆盖未分派和结果未知路径；[loop](../../../../packages/core/agent-loop/tests/loop.spec.ts)覆盖实时通知、提交失败和 max-tokens。改变恢复内容时同时检查 [Session repair](../../../../packages/core/session/tests/repair.spec.ts)与请求重建。
