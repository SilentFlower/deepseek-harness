# 共享开发指南

每次开发先按本页确定阅读范围。仓库总规则见 [AGENTS.md](../../../AGENTS.md)，具体目录可能另有 `AGENTS.md`；源类型和现行文档优先于相似代码中的历史写法。

## 开发前阅读项（Pre-Development Checklist）

1. 读取任务需求与受影响目录的指令，按[范围表](../index.md)选读专题。
2. 修改 `packages/` 前读[架构](../../../docs/architecture.md)与[防御规则索引](../../../docs/defensive-patterns/README.md)对应页面；修改客户端还读客户端规范。
3. 读取相关类、事件、请求、返回值和直接消费者；用 `rg` 查找现有实现及配置使用者，再确定改动位置。
4. 需要新抽象或共享逻辑时读[复用指南](code-reuse-thinking-guide.md)；改动事件、RPC、持久化或多层数据流时读[跨层指南](cross-layer-thinking-guide.md)。
5. 按[质量与验证](quality.md)选择能够验证实际行为的检查。

## 专题

| 专题 | 解决的问题 |
| --- | --- |
| [复用与职责](code-reuse-thinking-guide.md) | 如何选择现有实现、注册扩展点和共享代码位置 |
| [跨层变更](cross-layer-thinking-guide.md) | 如何追踪类型、日志、投影、RPC 和 SDK 消费者 |
| [质量与验证](quality.md) | 如何选择源码、构建产物、快照和文档的验证入口 |

## 按职责选读

实际工作区保留独立入口，共同约定集中在以下专题。跨层包按本次修改的实现选择多个专题。

| 专题 | 目录与实现 |
| --- | --- |
| [Harness](harness/index.md) | 服务、工具、API、Session、存储和共享库 |
| [客户端](client/index.md) | 浏览器插件、组件、对象层和状态 |
| [应用](apps/index.md) | CLI、Desktop、Host、profile 与 Web 构建 |
| [实验能力](experimental/index.md) | opt-in 组合、依赖隔离和转正 |
| [Python](python/index.md) | SDK 与运行时分发 |
| [原生能力](native/index.md) | addon、launcher 与平台载荷 |
| [第三方源码](vendor/index.md) | 固定来源及同步流程 |
| [脚本](tooling/index.md) | 检查、生成器与构建聚合 |
| [性能](benchmarks/index.md) | 合成负载、预算和报告 |
| [网站](website/index.md) | VitePress 投影与主题 |
| [文档](docs/index.md) | 归属、文风、双语与验证 |

## 质量检查项（Quality Check）

- 规则和示例指向当前文件，未从其他项目引入目录、命令或框架假设。
- 非显然的公开行为由 JSDoc 与归属 README 说明；文档编辑适用[文风标准](../../../.agents/skills/dsh-prose-standard/SKILL.md)。
- 报告仅列实际执行的检查及结果；未执行、跳过和失败分别说明。
