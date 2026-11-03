# 质量与验证

检查按改动影响选择，完整策略由[测试文档](../../../docs/testing.md)、[开发文档](../../../docs/development.md)和[推送前检查技能](../../../.agents/skills/dsh-pre-push-checks/SKILL.md)维护。以下用于判断验证种类，具体命令从根 [package.json](../../../package.json)及拥有者配置读取。

## 类型与文档

沿用现有缩进，限制差异范围。TypeScript 使用严格类型、显式导入、包名跨包导入及本地 `.ts` 导入；不新增 `as unknown`。公开方法说明参数、非空返回、失败、取消和所有权；事件 JSDoc 还说明 `@mode` 与载荷参数。纯类型留在纯类型文件和入口。

同时维护受影响的 README、JSDoc、子系统文档及必需的双语配对。注释描述调用者需要的行为与不变量，复杂代码说明非显然原因；不要保存实现过程或评审对话。完整要求见[文风标准](../../../.agents/skills/dsh-prose-standard/SKILL.md)。

## 按影响选证据

| 改动 | 验证入口与示例 |
| --- | --- |
| 包内算法、服务行为 | 拥有包的 `tests/*.spec.ts`；例如[标题投影测试](../../../packages/session/session-title/tests/projection.spec.ts) |
| 注册、HMR、异步生命周期 | 观察 fiber 卸载后注册移除，并等待消费者与资源清理完成 |
| 产品插件与组合 | 经 Loader 和真实 profile 的非单元测试；[profile 测试规则](../../../apps/cli/tests/profiles/AGENTS.md) |
| 模型或产品输出 | 对应 keyless recorded-session 场景；[快照规则](../../../snapshots/AGENTS.md) |
| 非 Session 的 CLI、ARIA、生成器输出 | 拥有者的 `tests/expected/`，使用对应 `test:expected` 或 Web 检查 |
| 公开入口、依赖或打包 | 构建产物、hygiene 与 owning built smoke |
| 文档 | `test:docs`、`doc-sync` 和文档流程要求的 lint；自定义规范目录另核对链接与格式 |
| 测试、脚本或 TypeScript | 最新 `build:artifacts` 后的 `build:check`，或完整 `build` |

源码检查通过 tsconfig paths 解析 `src`；产物测试通过公开导出解析 `lib`，两者不混用。参考[构建布局](../../../docs/development.md#typescript-project-layout)、[投影兼容组合](../../../packages/session/session-projection/tests/loader-compatibility.e2e.ts)和[工具产物导出检查](../../../packages/core/tools/tests/exports.built.e2e.ts)。

## 运行约束

只执行能够覆盖受影响行为的检查，不默认重跑全仓。使用 pnpm 脚本的 Vitest 过滤器时直接传文件或 `-t`，不插入独立的 `--`；同时核对实际选中的测试数量。覆盖率和测试选择分别设定，CI 的覆盖率检查是 `test:coverage`。

测试与其他进程并发运行。端口用系统分配，路径用私有临时根，子进程必须等待退出；改变资源与异步测试时应用[CI 可靠性技能](../../../.agents/skills/dsh-ci-test-reliability/SKILL.md)。只报告真正执行的命令；缺少密钥的实网测试和缺少平台的验证保留明确限制。
