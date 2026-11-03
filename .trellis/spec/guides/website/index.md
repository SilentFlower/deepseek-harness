# 文档网站规范

网站负责把归属文档投影成 VitePress 页面；内容仍在 `docs/` 和包 README。规则见[网站指令](../../../../website/AGENTS.md)与[文档流程](../../../../.agents/skills/dsh-doc/SKILL.md)，文档写作另读[文档专题](../docs/index.md)。

## 开发前阅读项（Pre-Development Checklist）

读取 publication manifest、projector、主题实现和对应测试，明确改动影响页面来源、路由、语言、构建产物还是交互。不要在网站目录新增文档副本。

## 代码归属

| 示例 | 阅读重点 |
| --- | --- |
| [website/docs.ts](../../../../website/docs.ts) | canonical source、两种语言的路由与导航元数据 |
| [文档 projector](../../../../scripts/project-doc-site.ts) | Markdown 链接、投影 frontmatter 与 raw Markdown 输出 |
| [website/build.ts](../../../../website/build.ts) | 输出路径校验和不穿越符号链接的清理 |
| [投影测试](../../../../scripts/project-doc-site.spec.ts) | 文档单一来源、路由与非法目录处理 |

`.generated/`、`.cache/`、`.dist/` 是可丢弃输出，不编辑或提交。交互增强与 Markdown 投影保持分离；路由、主题、语言、源码变化和卸载需要关闭活动视图并释放监听与滚动锁。布局和剪贴板等浏览器能力的具体限制由网站指令及拥有者实现定义。

## 质量检查项（Quality Check）

网站变更按网站指令执行 `pnpm docs:check`，覆盖测试与生产构建。内容路由变更检查双语、原始 Markdown、链接和锚点；交互变更还需要生产浏览器证据。构建成功不等于网站已经发布。
