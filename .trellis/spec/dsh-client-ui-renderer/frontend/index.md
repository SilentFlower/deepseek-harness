# @deepseek-ai/dsh-client-ui-renderer 开发入口

修改目录：`packages/client/ui-renderer`。本页用于定位该包与适用规则；具体公开行为以包文档和源码为准。

## 开发前阅读项（Pre-Development Checklist）

- 阅读[共享指南](../../guides/index.md)和专题：[harness](../../guides/harness/index.md)、[client](../../guides/client/index.md)。
- 阅读[包文档](../../../../packages/client/ui-renderer/README.md)、[manifest](../../../../packages/client/ui-renderer/package.json)和[源码/入口](../../../../packages/client/ui-renderer/src/client/index.ts)，确认相关类型、配置、导出与消费者。
- 测试位置：[packages/client/ui-renderer/tests](../../../../packages/client/ui-renderer/tests)。

## 专属规范

| 专题 | 修改时重点 |
| --- | --- |
| [挂载与响应绑定](bindings-and-mount.md) | boot 交接、裸来源转 hook、scope 与重新连接 |
| [注册与错误监督](registry-and-supervision.md) | 调用者 fiber、store 实例、过期授权和崩溃接替 |

## 质量检查项（Quality Check）

- 按[验证选择](../../guides/quality.md)核对本次行为、生命周期与公开入口，执行受影响路径的检查。
- 同步该包实际变化的类型、消费者与文档；只报告已经取得的验证证据。
