# Harness 运行时规范

适用于 `packages/` 的服务、提供者、工具、API、会话与存储。浏览器代码同时读取[客户端入口](../client/index.md)，实验目录再读[实验能力入口](../experimental/index.md)。

## 开发前阅读项（Pre-Development Checklist）

先读[架构](../../../../docs/architecture.md)、[包级指令](../../../../packages/AGENTS.md)、[共享指南](../index.md)，以及受影响包的 README 和源类型。按[防御规则表](../../../../docs/defensive-patterns/README.md)读取对应页面，再选本层专题。

| 专题 | 适用改动 |
| --- | --- |
| [包与编译入口](packages.md) | 新包、导出、依赖、Host/Client 编译配置 |
| [插件与生命周期](plugins.md) | 注入、注册、事件、HMR、并发和撤销 |
| [Session 与投影](sessions.md) | 日志、恢复、投影、checkpoint、SDK 输出 |
| [工具与提供者](tools.md) | 能力定义、配置、工具执行和模型输出 |
| [存储、API 与错误](storage-and-errors.md) | 非 Session 数据、持久化、远程调用和失败处理 |

## 质量检查项（Quality Check）

- 修改所有当前消费者，保持公开类型、文档和实际行为一致。
- 新能力有完整的定义、提供者和消费者；业务行为接入注册机制。
- 注册随 fiber 卸载撤销；异步工作在依赖释放前停止并完成。
- 按[共享验证指南](../quality.md)覆盖实际组合、回放和产物中受影响的路径。
