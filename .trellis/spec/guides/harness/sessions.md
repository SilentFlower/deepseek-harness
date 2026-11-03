# Session 与投影

Session 日志拥有可重建的模型历史和持久状态。当前类型由[Session 子系统](../../../../docs/subsystems/session.md)和[源定义](../../../../packages/core/session/src/index.ts)维护；格式及历史读写约束见[版本状态](../../../../docs/session-format-status.md)和[会话防御规则](../../../../docs/defensive-patterns/conversation-and-session.md)。

## 事件与读取

模型可见输入必须能从事件日志重建。新输入扩展领域事件及 `SessionEventMap`，不要只改变请求内存。仅用于 UI 绘制的数据留在客户端；进程内实时状态由自己的快照与通知提供。修改循环扩展点需要同步架构文档。

事件字段与消费者先做完整查询，使用现有品牌 ID 和判别字段。当前读取者消费当前逻辑格式；旧的已提交 generation 保持不可变，格式迁移由相邻版本迁移包和 JSONL 提供者各自负责。不得以增加字段为由机械升级格式号，也不加入推测性的降级或 fallback；按[持久类型审核](../../../../docs/cookbook/reviewing-persistence-type-changes.md)确认读取安全性。

## 领域投影

新增或扩展投影时必须使用 [dsh-session-projection](../../../../.agents/skills/dsh-session-projection/SKILL.md)。领域包拥有 definition、state schema、客户端 view 与私有 handle；注册表承担已提交事件的折叠与快照读取。需要初始化的注册必须先等待成功，再暴露依赖该投影的行为。

| 示例 | 阅读重点 |
| --- | --- |
| [标题服务](../../../../packages/session/session-title/src/index.ts) | 标题和有界输入聚合、领域定义及日志写入 |
| [Goal 服务](../../../../packages/goal/goal/src/index.ts) | 严格回放失败的保留，以及持久状态与进程内激活状态的区别 |
| [投影纯类型入口](../../../../packages/session/session-projection/src/types.ts) | 声明合并表、客户端值和 summary 排除标记 |
| [JSONL generation 选择](../../../../packages/session/session-persistence-jsonl/src/generation.ts) | 持久文件代际的物理归属 |

不要在多个控制器里重复扫描事件或维护第二份领域 fold。checkpoint 可用性、state version 和 wire view 的具体要求交由投影技能与[投影 README](../../../../packages/session/session-projection/README.md)定义。

## 验证

参考[标题投影测试](../../../../packages/session/session-title/tests/projection.spec.ts)和[投影兼容测试](../../../../packages/session/session-projection/tests/compatibility.spec.ts)，覆盖既有日志、延迟注册、无关事件、checkpoint 和卸载中受影响的行为。循环、Session 生命周期及事件表变更还要更新 TypeScript 与 Python SDK 的预期输出，不能只运行单元测试。快照位置按[共享质量指南](../quality.md)选择。
