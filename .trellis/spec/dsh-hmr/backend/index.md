# @deepseek-ai/dsh-hmr 开发入口

修改目录：`packages/boot/hmr`。本页用于定位该包与适用规则；具体公开行为以包文档和源码为准。

## 开发前阅读项（Pre-Development Checklist）

- 阅读[共享指南](../../guides/index.md)和专题：[harness](../../guides/harness/index.md)。
- 阅读[包文档](../../../../packages/boot/hmr/README.md)、[manifest](../../../../packages/boot/hmr/package.json)和[源码/入口](../../../../packages/boot/hmr/src/index.ts)，确认相关类型、配置、导出与消费者。
- 测试位置：[packages/boot/hmr/tests](../../../../packages/boot/hmr/tests)。

## 质量检查项（Quality Check）

- 按[验证选择](../../guides/quality.md)核对本次行为、生命周期与公开入口，执行受影响路径的检查。
- 同步该包实际变化的类型、消费者与文档；只报告已经取得的验证证据。
