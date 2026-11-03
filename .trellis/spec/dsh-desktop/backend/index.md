# @deepseek-ai/dsh-desktop 开发入口

修改目录：`apps/desktop`。本页用于定位该包与适用规则；具体公开行为以包文档和源码为准。

## 开发前阅读项（Pre-Development Checklist）

- 阅读[共享指南](../../guides/index.md)和专题：[apps](../../guides/apps/index.md)。
- 阅读[包文档](../../../../apps/desktop/README.md)、[manifest](../../../../apps/desktop/package.json)和[源码/入口](../../../../apps/desktop/src)，确认相关类型、配置、导出与消费者。
- 测试位置：[apps/desktop/tests](../../../../apps/desktop/tests)。

## 二开专属规范

| 专题 | 修改时重点 |
| --- | --- |
| [架构、入口与开发](architecture-and-development.md) | Electron / Host / Web 分工、目录归属和调试入口 |
| [IPC 与认证](ipc-and-authentication.md) | preload、来源验证、Host cookie 与嵌入页权限 |
| [窗口与原生能力](windows-and-native.md) | 隐藏和退出、菜单、托盘、文件及清理 |
| [更新与设置](updates-and-settings.md) | 设置原子写入、渠道、安装授权、任务保护与恢复 |
| [打包与验证](packaging-and-verification.md) | ESM/CJS、目标资源、依赖、签名和平台证据 |
| [Welcome 与壳页面](../frontend/welcome-and-shell.md) | 独立页面、账户安全状态、本地化与卸载 |
| [私有 Host](../../dsh-desktop-host/backend/startup-and-shutdown.md) | ready、控制请求、请求排空和 shutdown acknowledgement |

## 质量检查项（Quality Check）

- 按[验证选择](../../guides/quality.md)核对本次行为、生命周期与公开入口，执行受影响路径的检查。
- 同步该包实际变化的类型、消费者与文档；只报告已经取得的验证证据。
