# 固定版本的第三方源码

`vendor/` 是复制并固定版本的源码，不是 Git submodule。上游版本、固定来源和本地修改的唯一记录归属 [vendor/README.md](../../../../vendor/README.md)；新增依赖遵循[新增 vendor 教程](../../../../docs/cookbook/adding-a-vendored-package.md)。

## 开发前阅读项（Pre-Development Checklist）

先读 README 中对应 manifest 行、本地修改记录和 sync procedure，再读受影响上游源码与 Harness 消费者。不要把普通产品修改扩展为 vendor 文风清理；[文风技能](../../../../.agents/skills/dsh-prose-standard/SKILL.md)明确排除 vendor。

## 修改与消费者

vendor 使用重新命名的 `@deepseek-ai` 包名和 `workspace:~` 关系。更新通过归属 README 的同步步骤进行，并逐条重新应用或退役本地修改。不要手动调整上游固定信息却遗漏源码，也不要把本地补丁直接当作上游行为。

Harness 对框架的使用可从[资源注册插件](../../../../packages/client/resources/src/client/index.ts)、[Loader 组合测试](../../../../packages/experimental/inspector/tests/loader-composition.host.spec.ts)和[框架配置测试](../../../../scripts/cordis-config-access.spec.ts)追踪。检查当前版本的导出和事件签名，不依赖对其他 Cordis 版本的记忆。

## 质量检查项（Quality Check）

修改对应的本地记录，覆盖当前消费者和框架行为测试，并执行 README 要求的安装、完整测试与构建。这个同步流程的全量要求不扩展到仅引用 vendor 的普通功能任务；新包、发布和许可变更分别遵循其拥有者流程。
