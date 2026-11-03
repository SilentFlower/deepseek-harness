# 投影状态、视图与恢复

适用于新增或修改可恢复的 Session 派生状态。先读 [ProjectionDefinition](../../../../packages/session/session-projection/src/index.ts)、[投影规则](../../../../.agents/skills/dsh-session-projection/SKILL.md)和[包文档](../../../../packages/session/session-projection/README.md)。

## 选择状态的归属

需要重启恢复的 Session 事实放进投影，包括仅 Host 使用的状态。进程资源、注册句柄、Promise 和外部连接留在运行时所有者。业务消费者使用拥有该投影的领域服务；不要把定义或 handle 变成公共业务读接口。

`init(header, inheritedEventCount)` 从精确继承长度建立初态，不能从首个 live seq 或标记事件猜 cut。`apply(state, event)` 必须同步、确定、无 I/O，不调用工具、模型或 Cordis hooks；运行时 effect 另由事件监听负责，回放不能重做副作用。

优先维护固定大小或缓慢增长的当前状态。确需线性增长时说明当前消费者及内存、回放、每事件成本；不要习惯性保存整段事件索引，也不要在 cache miss 中隐藏全日志扫描。

## 两层引用决定通知

无关事件返回原 state 引用，避免触发视图计算。内部状态变化但客户端值未变时，`wire.view` 复用原视图引用；结构相等的新对象仍会发布变化。状态和视图都必须是各自 schema 接受的 JSON，客户端收到的是完整值。

没有 `wire` 的单元仍参与 checkpoint。需要排除 Session 列表摘要的 key，同时维护类型标记 `SessionProjectionSummaryExcluded<T>` 与 `wire.summary: false`；可空值的 null 放在标记外。不要用全局注册表的 key 是否存在判断某个 Session 是否启用业务能力。

## Checkpoint 与尾部回放

状态字段或 fold 语义变化时更新 `stateVersion`。checkpoint 是缓存，缺失、不兼容或越过日志末尾的行都不能替代真实历史；从 checkpoint 加后缀恢复的结果须与完整回放一致。

水位是包含端点的 `SessionSeqCursor`，读取起点是 `SessionLogOffset`；空日志使用 -1 水位。使用注册表的 `restoreFloor`、`restore` 和准备流程，不手写减一或跳过尾部校验。物理保存与冷读取归 [session-projection-cache](../../../../packages/session/session-projection-cache/README.md)。

## 验证选择

[registry](../../../../packages/session/session-projection/tests/registry.spec.ts)覆盖状态、视图引用、通知、可用及失效 checkpoint；[summary](../../../../packages/session/session-projection/tests/summary.spec.ts)覆盖全量与摘要差异。新增领域投影还需在拥有包验证完整回放、checkpoint 加后缀、未知事件不变及回放无副作用；不能只验证注册表测试通过。
