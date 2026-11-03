# @deepseek-ai/dsh-client-ui-renderer 开发入口

修改目录：`packages/client/ui-renderer`。本页用于定位该包与适用规则；具体公开行为以包文档和源码为准。

## 开发前阅读项（Pre-Development Checklist）

- 阅读[共享指南](../../guides/index.md)和专题：[harness](../../guides/harness/index.md)。
- 阅读[包文档](../../../../packages/client/ui-renderer/README.md)、[manifest](../../../../packages/client/ui-renderer/package.json)和[源码/入口](../../../../packages/client/ui-renderer/src/index.ts)，确认相关类型、配置、导出与消费者。
- 测试位置：[packages/client/ui-renderer/tests](../../../../packages/client/ui-renderer/tests)。

## 实现归属

[Host 入口](../../../../packages/client/ui-renderer/src/index.ts)是无行为的 `apply`；实际 registry、React 绑定和应用挂载由[浏览器规范](../frontend/index.md)维护。新增界面能力从浏览器注册位置扩展，不在 Host 占位入口复制 renderer。

## 质量检查项（Quality Check）

- 按[验证选择](../../guides/quality.md)核对本次行为、生命周期与公开入口，执行受影响路径的检查。
- 同步该包实际变化的类型、消费者与文档；只报告已经取得的验证证据。
