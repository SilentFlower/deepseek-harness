# Session 所有权、Fork 与持久化

适用于修改 SessionStore 生命周期、fork、尾部修复和耐久性。Session 拥有逻辑事件，物理文件和迁移归[持久化服务](../../../../packages/session/session-persistence/README.md)与[格式目录](../../../../packages/session/session-format-catalog/README.md)。

## 注册与准备

高级组合通过 `prepare`、`enter`、`announce` 保持有序生命周期；`enter` 后立即接住其 disposer，保证公告失败可回滚。它再次检查 id 冲突，旧准备对象不能覆盖现有同 id 实例。释放绑定确切对象，并在创建或追加的同步发布结束后完成延迟 detach，见 [SessionStore](../../../../packages/core/session/src/index.ts)及 [SessionPreparation](../../../../packages/core/session/src/preparation.ts)。

需要运行 Agent 的消费者通过 `ctx.agents.create()` 发布，不能把独立构造 Session 等同于已拥有持久化写路径。高级初始化与释放顺序见[Agent 生命周期](../../dsh-agent-loop/backend/lifecycle.md)。

## Fork 的精确切点

`SessionSeq` 表示已有事件或包含端点，`SessionLogOffset` 表示间隙、长度或排他读位置；不要把事件总数当成最后一个事件序号。空日志水位使用的 `-1` 只属于 `SessionSeqCursor`。

[buildForkSeed](../../../../packages/core/session/src/fork.ts)复制到包含 boundary 的前缀，再追加 child-owned 的继承标记与未闭合尾部的结束事件。`inheritedEventCount` 只计算复制前缀，不能把标记或修复事件算进继承区。传入普通恢复 seed 不自动表示 fork。

只为开放尾部补缺失工具结果与 step/turn 结束；闭合历史保持不变。fork 的未知结果与进程中断的未知结果使用各自语义，不能因父会话可能继续执行就替子会话断言工具未执行。共同实现归 [repair](../../../../packages/core/session/src/repair.ts)。

## 持久化与恢复读取

`append()` 完成表示逻辑事件已经提交，不等于 write-behind 已落盘。需要耐久检查点时等待 `ctx.sessions.flush(session)`；其所有监听器结算后才报告失败或成功，布尔返回值说明是否有监听器参与。

物理格式迁移在构造当前逻辑 Session 前完成；不要在 Session 消费者里按历史文件名或旧版本再做兼容解析。已提交历史代不可覆盖、移动或删除，完整规则归[格式状态](../../../../docs/session-format-status.md)。

新生产读取不要调用已弃用的 `eventAt()`、`snapshotEvents()`、`ownEvents()` 或包装它们。日志长度读 `seq`，恢复状态使用[投影规范](../../dsh-session-projection/backend/state-and-replay.md)，需要冷历史时走拥有者的异步读取接口。

## 验证选择

[store-membership](../../../../packages/core/session/tests/store-membership.spec.ts)和 [preparation](../../../../packages/core/session/tests/preparation.spec.ts)覆盖准备、公告和 detach；[fork](../../../../packages/core/session/tests/fork.spec.ts)、[repair](../../../../packages/core/session/tests/repair.spec.ts)、[sequence-types](../../../../packages/core/session/tests/sequence-types.spec.ts)覆盖切点和修复。耐久性变化还需通过实际 persistence provider 与 [Agent 恢复测试](../../../../packages/core/agent-loop/tests/resume.spec.ts)验证，纯内存 Session 测试不能证明已落盘。
