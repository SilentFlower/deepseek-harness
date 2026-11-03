# 脚本、构建与生成器规范

脚本负责可复现的构建、静态检查和派生文件。先读[脚本目录指令](../../../../scripts/AGENTS.md)、[开发文档](../../../../docs/development.md)与[共享质量指南](../quality.md)，再阅读实际输入、扫描范围及运行入口。

## 开发前阅读项（Pre-Development Checklist）

读取拥有者脚本、对应 spec、根 package script 和 [run-gates](../../../../scripts/run-gates.ts)中的聚合接入。修改检查规则时明确合法输入、必须拒绝的输入和未纳入范围，不以降低扫描数量或禁用规则解决失败。

## 实现与派生文件

| 示例 | 阅读重点 |
| --- | --- |
| [仓库文件发现](../../../../scripts/repo-files.ts) | 规范化相对路径、符号链接去重和明确拒绝不支持的 glob |
| [路径别名生成器](../../../../scripts/gen-tsconfig-paths.ts) | 有标记区域、稳定输出和 `--check` 的只读漂移判断 |
| [工作区规则](../../../../scripts/check-workspace-constraints.ts) | 真实 manifest、职责分类和发布载荷检查 |
| [Markdown 链接检查](../../../../scripts/verify-md-links.ts) | AST 读取、文件目标和锚点分别验证 |

启动 pnpm 时不经 shell；跨平台差异归到需要它的脚本。源码所有权检查使用语法感知发现，并保护空语料或被缩窄的语料。先修改拥有者，再重新生成目录和参考页，不直接修改生成区。

## 质量检查项（Quality Check）

每条新接受/拒绝规则有对应有效与无效输入证据，顶层聚合实际执行该检查。参考[文档网站投影测试](../../../../scripts/project-doc-site.spec.ts)的目录、输出清理和非法输入验证。涉及资源或子进程的测试按[CI 可靠性技能](../../../../.agents/skills/dsh-ci-test-reliability/SKILL.md)验证并发和清理；TypeScript 变更执行最新产物之后的 build:check。
