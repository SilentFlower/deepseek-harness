# 文档与指令规范

文档先确定读者、用途和归属，再组织内容。完整结构和预算由[文档指令](../../../../docs/AGENTS.md)维护；写作使用 [dsh-doc](../../../../.agents/skills/dsh-doc/SKILL.md)和 [dsh-prose-standard](../../../../.agents/skills/dsh-prose-standard/SKILL.md)，不会因为文件是规范就放宽事实准确性。

## 开发前阅读项（Pre-Development Checklist）

读取目标页、父导航、关联源码/测试与双语记录。按 tutorial、reference、包能力、Agent 指令或任务记录确定结构，不将产品能力、决策理由、过程计划和验证结果混放。

## 内容与归属

| 内容 | 归属及示例 |
| --- | --- |
| 公开能力、配置与限制 | 包 README；[JSONL 持久化参考](../../../../packages/session/session-persistence-jsonl/README.md) |
| 跨包结构与语义 | [架构](../../../../docs/architecture.md)与[子系统](../../../../docs/subsystems/README.md) |
| 可执行教程 | [新增包教程](../../../../docs/cookbook/adding-a-package.md) |
| 长期决策理由 | [Agent Notes 范围](../../../../.agents/notes/README.md)；机械和局部 UI 修改通常不新建记录 |
| 任务计划与验证结果 | 对应 `.trellis/tasks/` 任务，不进入现行产品说明 |

每个事实由一个页面维护，其他位置链接过去。按实际格式使用 metadata 与对应模板；简短 Agent 规则和解析器要求的文件遵循其格式，不机械套用长篇页面结构。普通文档描述当前行为，每段占一条物理行；类型清单和生成区由源定义与生成器维护。

双语页面同轮维护结构与行数并更新 pairing 记录；不自动调用仅由用户明确触发的翻译技能。注释和 JSDoc 保留非显然行为、失败、时间和所有权，不记录推理过程或评审历史。归档 Agent Notes 保持冻结，文风清理排除 vendor。

## 质量检查项（Quality Check）

操作、配置和平台行为以真实执行证据为准；不能验证时明确其验证归属，不写成已确认事实。执行文档流程要求的 `test:docs`、`doc-sync`、lint 和差异检查，生成参考还要运行对应 freshness 检查。`.trellis/spec/` 不在默认 Markdown 链接扫描内，规范变更需要额外验证全部本地链接、锚点、导航和模板残留。
