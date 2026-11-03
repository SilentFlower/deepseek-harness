# 客户端开发规范

适用于 `packages/client/`、API 和实验包中的浏览器实现，以及 `apps/web` 的界面集成。客户端的运行、组件绑定与数据通道由[客户端指令](../../../../packages/client/AGENTS.md)和[Web Client 架构](../../../../docs/subsystems/web-client.md)定义。

## 开发前阅读项（Pre-Development Checklist）

先读[共享指南](../index.md)、[客户端指令](../../../../packages/client/AGENTS.md)与[组件防御规则](../../../../docs/defensive-patterns/client-components.md)。读取相关 SlotMap、组件 props、store 和注入声明后，再选择专题。

| 专题 | 适用改动 |
| --- | --- |
| [组件与 slots](slots.md) | 插件组合、props、注入、跨功能依赖与导出 |
| [状态与资源](state.md) | 领域对象、store、observable、资源读取与重连 |
| [界面与本地化](ui.md) | 文案、CSS、响应式、反馈、无障碍与 GUI 证据 |

## 质量检查项（Quality Check）

- 组件只消费派生 props，业务数据和订阅有明确的所有者。
- Host 与 Client 的编译、依赖和导出分别按[包规范](../harness/packages.md)核对。
- 按[界面专题](ui.md)选择行为、布局、字典、真实流程与 PR 演示证据。
