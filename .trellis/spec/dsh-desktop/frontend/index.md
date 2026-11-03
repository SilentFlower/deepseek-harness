# @deepseek-ai/dsh-desktop 开发入口

修改目录：`apps/desktop`。本页用于定位该包与适用规则；具体公开行为以包文档和源码为准。

## 开发前阅读项（Pre-Development Checklist）

- 阅读[共享指南](../../guides/index.md)和专题：[apps](../../guides/apps/index.md)、[client](../../guides/client/index.md)。
- 阅读[包文档](../../../../apps/desktop/README.md)、[manifest](../../../../apps/desktop/package.json)和[Welcome 入口](../../../../apps/desktop/src/client/welcome.tsx)，确认相关类型、配置、导出与消费者；Electron 编排另读 [main](../../../../apps/desktop/src/main.ts)。
- 测试位置：[apps/desktop/tests](../../../../apps/desktop/tests)。

## 专属规范

- [Welcome 与壳页面](welcome-and-shell.md)：独立 React 页面、preload、账户状态和窗口卸载。
- [Desktop 二开入口](../backend/architecture-and-development.md)：选择工作区插件、Electron 与 Host 的修改位置。
- [IPC 与认证](../backend/ipc-and-authentication.md)及[更新与设置](../backend/updates-and-settings.md)：原生操作的权限与结果。

## 质量检查项（Quality Check）

- 按[验证选择](../../guides/quality.md)核对本次行为、生命周期与公开入口，执行受影响路径的检查。
- 同步该包实际变化的类型、消费者与文档；只报告已经取得的验证证据。
