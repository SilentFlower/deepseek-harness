# @deepseek-ai/dsh-agent-loop 开发入口

修改目录：`packages/core/agent-loop`。本页用于定位该包与适用规则；具体公开行为以包文档和源码为准。

## 开发前阅读项（Pre-Development Checklist）

- 阅读[共享指南](../../guides/index.md)和专题：[harness](../../guides/harness/index.md)。
- 阅读[包文档](../../../../packages/core/agent-loop/README.md)、[manifest](../../../../packages/core/agent-loop/package.json)和[源码/入口](../../../../packages/core/agent-loop/src/index.ts)，确认相关类型、配置、导出与消费者。
- 测试位置：[packages/core/agent-loop/tests](../../../../packages/core/agent-loop/tests)。

## 专属规范

| 专题 | 修改时重点 |
| --- | --- |
| [创建、恢复与释放](lifecycle.md) | 初始化事务、通知顺序、同 id 生命周期和关闭写路径 |
| [Turn、Step 与请求](steps-and-requests.md) | 输入准入、模型选择、请求日志与工具续步 |
| [失败与取消](failure-and-cancellation.md) | 流式结算、重试归属、未知工具结果和 turn 收尾 |

## 质量检查项（Quality Check）

- 按[验证选择](../../guides/quality.md)核对本次行为、生命周期与公开入口，执行受影响路径的检查。
- 同步该包实际变化的类型、消费者与文档；只报告已经取得的验证证据。
