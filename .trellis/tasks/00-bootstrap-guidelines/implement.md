# 实施与验证

- [x] 确认 00 任务、初始干净工作区及模板重复情况。
- [x] 读取架构、各目录规则、相关类型、代表源码和测试。
- [x] 移除已核对的初始化模板，按职责范围编写索引与专题。
- [x] 同步 Trellis 配置，核对原工作区覆盖及默认范围。
- [x] 专项检查规范链接与锚点、模板残留、段落换行和索引覆盖。
- [x] 运行 `pnpm run test:docs`、`pnpm run doc-sync`、`pnpm run lint` 和 `git diff --check`；按实际结果记录失败或通过，不扩大到产品全量测试。
- [x] 完成 Check-All 和规范更新评估，保存任务进度与待交付事项。

验证使用仓库要求的 Node 版本。仓库文档检查默认不扫描 `.trellis/spec/`，因此规范专项检查必须单独执行，不能用全仓文档通过替代。

## 实际验证结果

本次使用 Node 24.9.0。DSH 改动包括 `.trellis/spec/`、本任务目录、Trellis 配置的默认包键及用户选定的十份技能文档措辞。另按用户要求同步本地 Flower/Skill-Garden 的作者源、快照、断言测试和编译产物；产品 API 与工作流行为保持不变。

| 检查 | 结果 |
| --- | --- |
| 规范专项检查：复用仓库 Markdown AST 和链接检查器，核对配置、父索引、段落和模板残留 | 通过：393 个原工作区、498 个包/层入口、524 份 Markdown；全部路径与锚点有效 |
| `get_context.py --mode packages --json` | 通过：Monorepo，393 个包均有规范层，默认包为有效的 `cordis` |
| `spec_router.py` 的 Session/投影与客户端/slots 查询 | 通过：均返回相关共享专题且置信度为 high |
| `validate_package` 的默认键检查 | `cordis` 有效；npm 全名 `@deepseek-ai/cordis` 无效 |
| `pnpm run verify-concrete-terms` | 修复后通过 |
| `pnpm run test:docs` | 修复后 21 项全部通过 |
| `pnpm run doc-sync` | 修复后 43 项全部通过，含文档构建和类型检查 |
| `pnpm run lint` | 通过；实验包现有 unused-disable warning 不在本次改动内 |
| `pnpm run build` | 10 项全部通过，包含最新构建产物和 Host/Client aggregate check |
| `git diff --check`、改动范围与任务文件结尾换行 | 通过 |

## 已修复的基线问题

CHK-001（P2，verification）已按用户选择修复：以下五份技能文档及 `.claude/skills/trellis-meta/references/` 下对应副本共十二处措辞改为明确的 Patch 操作/应用记录。双平台逐字节相同，管理标记与行数保持不变；Flower 状态、版本锁和模板哈希未被手工修改。DSH 的十份文档与修订后的源头 canonical 编译结果逐字节相同。

- `.agents/skills/trellis-meta/references/customize-local/change-skills-or-commands.md:67`
- `.agents/skills/trellis-meta/references/customize-local/overview.md:30`
- `.agents/skills/trellis-meta/references/local-architecture/bundled-skills.md:20`
- `.agents/skills/trellis-meta/references/local-architecture/generated-files.md:61`
- `.agents/skills/trellis-meta/references/local-architecture/overview.md:24`、`:50`

初次检查的 `test:docs` 为 20/21、`doc-sync` 为 42/43；修复后均已全部通过。构建、lint 与规范专项检查的输入不受此次措辞修订影响，沿用当前有效证据。

## Flower 源头同步

- 作者源：`vendor/skill-garden/.trellis/0.6/overrides/patches/skills/trellis-meta/` 的六份内容文件，以及 `overrides/conflicts.json` 中两条固定文案断言。
- 父仓：对应的七份 `enhancements/0.6/overrides/` 快照、`enhancements/MANIFEST.json`、一条既有 overlay 测试断言及子模块引用。
- 编译产物：已重新生成 `compiled-targets/0.6.14/full/`，profile 覆盖 21 个平台；937 个文件的产物检查通过。
- `npm run sync`、`npm run patch:targets`、`npm run patch:targets:check` 已执行。
- `node scripts/check-patch-conflicts.mjs` 通过：57 个 Patch、241 个 operation、1364 个 ready target、0 warning，并验证源与快照一致。
- `node scripts/check-ai-context-budget.mjs --strict`、`node scripts/check-output-templates.mjs` 通过；预算检查保留原有的 states-total 提示。
- `node scripts/ci-impact.mjs --rules` 通过：JavaScript 111 项、Python 72 项全部通过。

三个业务仓库均已提交并推送，远端提交已逐一核对。子仓提交后已在 Flower 根重跑 `npm run sync`，父仓提交后的 `check-snapshot.mjs` 已通过，确认快照、子模块引用及 Patch 结果一致。DSH 的 pre-commit 检查和 pre-push 五项类型检查通过。未执行全局安装、升级或发版。

## 检查与规范评估结论

Check-All 修复重检通过，CHK-001 已修复，无剩余 CHK/FBK。检查范围覆盖 DSH 的规范与技能文案、Skill-Garden 作者源及编译产物、Flower 的发布快照和对应测试；不涉及产品 API、状态字段或可执行命令变更。DSH 的 lint/build 结果继续有效。规范评估为 no-op：现有规范已覆盖本次文案、源码归属和生成产物要求，无新增可执行约定。实现、验证与业务推送均已完成，任务通过进度 helper 写入完成态与 Close，任务记录单独提交。
