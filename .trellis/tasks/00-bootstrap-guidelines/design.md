# 规范组织

## 职责范围

仓库是一个 Git 仓库中的 pnpm Monorepo，没有嵌套 Git 仓库或 submodule。保留 Trellis 配置中原有的 393 个工作区及路径，仅将无效默认包键修正为已有的 `cordis`。每个工作区保留独立规范入口；共享专题按 Harness、客户端、实验能力、应用、Python、原生代码、第三方源码、脚本、基准、网站和文档组织。

## 导航

`.trellis/spec/index.md` 解释包与专题选择；`guides/index.md` 提供通用阅读入口。每个 `<package>/<layer>/index.md` 链接该包的 README、实际源码/测试位置，以及适用的共享专题，并列出开发前阅读项和质量检查项。纯二进制平台包使用 packaging 层，浏览器实现使用 frontend 层；其他运行时与库代码使用 backend 层。共享规则集中在 `guides/`，不把 393 个实际工作区合并为虚拟包。

## 用户选定的修复

用户选择修复 CHK-001。范围为 `.agents/skills/trellis-meta/references/` 中五份文档与 `.claude/skills/` 的对应副本，共十二处术语。此次以明确的 Patch 操作记录、来源或首次备份记录替换含混措辞，保持工作流和运行时行为不变。两平台文件逐字节同步；本地文案修订保留为可见差异，不手工修改 Flower 状态、版本锁或模板哈希。后续 Flower 更新需要保留或重新应用这项本地修订。

## 源头同步

用户进一步要求同步到本地 Flower 仓库。真实作者源位于 `/root/project/flower-trellis/vendor/skill-garden/.trellis/0.6/overrides/patches/skills/trellis-meta/`，它是独立 Git 子模块。修改六份 `content` 文件，同步两条固定文案断言及对应测试，不改 selector、baseline、Patch 操作声明或协议字段；父仓通过 `npm run sync` 生成 `enhancements/`，通过 `npm run patch:targets` 更新子仓内 canonical 编译产物。运行匹配的规则、冲突、产物、预算和输出模板检查。提交前保留各仓本地差异，不修改已安装的全局 npm 包，不执行发版。

## 事实来源

已有 `AGENTS.md`、`docs/architecture.md`、`docs/defensive-patterns/`、`docs/testing.md` 和包 README 是规则来源；源码和测试提供局部用法。没有使用代码图服务，所有示例通过本地文件读取核对。第三方源码仅用于理解现有依赖，不在本任务中修改或进行文风审查。

## 一致性与恢复

同步修改配置、索引和任务记录。仅移除内容与初始化样本完全相同的规范模板，任何不一致文件都中止删除。保留 Trellis 运行脚本和模板哈希记录。检查全部 393 个配置工作区的入口，验证共享专题、浏览器和实验能力的附加规则可发现。全部变更可通过 Git 差异审阅和恢复。
