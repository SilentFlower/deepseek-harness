# Desktop 二开入口与数据归属

适用于选择 Desktop 功能的实现位置。先读[Desktop 架构](../../../../docs/architecture.md#desktop-application)和[包文档](../../../../apps/desktop/README.md)，再按下表进入具体实现；界面、Host 业务与 Electron 原生操作分别有自己的所有者。

## 从需求定位实现

| 要修改的能力 | 入口与约束 |
| --- | --- |
| 工作区页面、侧栏、工具卡和设置内容 | `packages/client/` 对应插件，通过 [slots](../../dsh-client-ui-slots/frontend/index.md) 组合；Desktop 复用 Web 应用 |
| 窗口、菜单、托盘和原生能力 | [main](../../../../apps/desktop/src/main.ts)与[窗口规范](windows-and-native.md) |
| Host 启动、任务检查和关闭 | [desktop-host](../../dsh-desktop-host/backend/startup-and-shutdown.md)，继续使用共享 profile runner |
| Electron 与网页的能力桥 | [IPC 与认证](ipc-and-authentication.md)，同步类型、preload、主进程和客户端消费者 |
| 独立 Welcome 与壳页面 | [Welcome 与本地页面](../frontend/welcome-and-shell.md)，不等同于客户端插件 |
| 更新渠道、本地设置与重启安装 | [更新与设置](updates-and-settings.md)，由 Electron 拥有 |
| 发行资源、目标架构与安装包 | [打包与验证](packaging-and-verification.md)，从源码一路核对到产物 |

## 启动链

Electron 的主窗口先加载已打包的 Web 静态资源，等待 Host boot injections 后在同一文档激活客户端。私有 Host 运行在 Electron Node mode，经 `runProfile` 加载完整 Web 应用；RPC 和流仍归 Web 的协议。不能为 Desktop 业务另起一个绕过 `dsh` profile 的 Node 应用入口。

入口责任分别见 [DesktopBackendController](../../../../apps/desktop/src/backend-controller.ts)、[DesktopHostProcess](../../../../apps/desktop/src/host-process.ts)和 [Host main](../../../../apps/desktop-host/src/index.ts)。改变重试或重启时先确认旧 Host 已完成清理，不能让两个尝试同时发布 ready。

## 三类目录

| 数据 | 所有者及处理要求 |
| --- | --- |
| 签名包内的 dsh 与生产依赖 | 应用资源和 runtime descriptor；不复制到 profile，也不在首次启动用 pnpm 重装 |
| `$DSH_HOME/profiles/desktop` | Desktop 的插件与 profile 声明；共享初始化保留用户 patch、已安装包和 lockfile，包管理走共享 Plugin Manager |
| Electron `userData` | 浏览器数据、Desktop 壳偏好及本地记录；不随 `DSH_HOME` 改位置，具体设置见[更新与设置](updates-and-settings.md) |

不要通过清空 profile 修复官方 runtime，也不要把 npm CLI 和 Desktop 的包安装状态合并。保留用户包的解析优先级，源码与规则见 [project-manager](../../../../apps/desktop/src/project-manager.ts)和[安装归属](../../../../apps/desktop/README.md#installation-ownership)。

## 本地开发与验证

开发启动参数、构建和调试端口由 [scripts/dev.ts](../../../../apps/desktop/scripts/dev.ts)及 [Develop](../../../../apps/desktop/README.md#develop)维护。`dev:desktop` 构建后启动，`start:desktop` 使用已有产物；菜单 Reload 和 Restart 都不重编译源码。开发 home、临时 runtime project 与 Electron userData 分开，复现问题前核对实际使用目录。

新增环境设置先确认是构建期公开值、Host 环境还是壳设置，不能混用。登录 shell 环境的过滤和回退归 [login-shell-environment](../../../../apps/desktop/src/login-shell-environment.ts)；包操作专用 Node launcher 不应改写所有 agent 子进程的执行环境。

定位开发链变化的证据入口为 [development-project](../../../../apps/desktop/tests/development-project.spec.ts)、[node-environment](../../../../apps/desktop/tests/node-environment.spec.ts)、[login-shell-environment](../../../../apps/desktop/tests/login-shell-environment.spec.ts)和 [main-startup](../../../../apps/desktop/tests/main-startup.spec.ts)。平台启动、原生界面和安装包仍按[验证分层](packaging-and-verification.md#按影响选择验证)取得对应环境的证据。
