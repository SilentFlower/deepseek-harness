# Welcome 与壳页面开发

适用于修改独立 Welcome、更新对话框和 preload 映射。主工作区是共享客户端应用，扩展规则见 [ui-slots](../../dsh-client-ui-slots/frontend/index.md)；本目录的独立页面由 Electron 管理，不在这里复制一套工作区业务 UI。

## 页面与能力入口

| 页面 | 阅读入口 |
| --- | --- |
| Welcome | [welcome.tsx](../../../../apps/desktop/src/client/welcome.tsx)、[WelcomePage](../../../../apps/desktop/src/client/WelcomePage.tsx)、[WelcomeApi](../../../../apps/desktop/src/welcome-api.ts) |
| Welcome 原生桥 | [preload-welcome](../../../../apps/desktop/src/preload-welcome.ts)、[welcome-window](../../../../apps/desktop/src/welcome-window.ts)、[welcome-backend](../../../../apps/desktop/src/welcome-backend.ts) |
| 产品页原生桥 | [preload-app](../../../../apps/desktop/src/preload-app.ts)及 [IPC 规范](../backend/ipc-and-authentication.md) |
| 更新和强制阻断页面 | [update-dialog](../../../../apps/desktop/src/update-dialog.ts)、[mandatory-update-window](../../../../apps/desktop/src/mandatory-update-window.ts)及各自隔离 preload |

修改页面同时追踪主进程中确切窗口、频道处理器的安装与移除。不能把普通壳页或 Welcome 的权限自动授予嵌入网页。

## Welcome 状态

`needsWelcome()` 从当前账户与独立 API key 两个事实决定入口，不能新增一个容易过期的 onboarding-completed 标志替代它。skip 不写完成设置；失效账户有可用 API key 时仍能进入工作区。

renderer 通过安全 `AccountView` 和具名操作展示登录状态，Host 保管账户凭据。API key 草稿属于输入表单；只在明确保存时传给已定义操作，不写入日志、analytics 或错误详情。保存失败使用安全结果，不能把 Host 原始异常显示给用户。

异步操作要在页面变更、attempt 变化和卸载后丢弃旧结果，重复提交与取消由现有状态保护。`onAccountState` 返回的订阅在卸载时释放，pagehide unmount React root；不要让已经关闭的窗口继续提交 UI 变化。

## 外观、文案与交互

Welcome 使用共享 design-platform 样式和现有 primitives；主工作区沿客户端 tokens 与 CSS Modules 规范。壳 copy 通过 [Desktop locale](../../../../apps/desktop/src/locale.ts)传入，不能硬编码一种语言或读另一页面的全局服务。

原生对话框与更新 overlay 保持各自焦点、Escape、模态和 fullscreen 规则。安装动作只请求主进程确认，不在 renderer 决定 URL、版本或退出，见[更新规范](../backend/updates-and-settings.md)。

## 验证选择

[welcome-renderer](../../../../apps/desktop/tests/welcome-renderer.client.spec.tsx)验证表单、状态和卸载；[welcome-startup](../../../../apps/desktop/tests/welcome-startup.spec.ts)、[welcome-window](../../../../apps/desktop/tests/welcome-window.spec.ts)、[welcome-host](../../../../apps/desktop/tests/welcome-host.spec.ts)验证入口和原生桥；[welcome-flow](../../../../apps/desktop/tests/welcome-flow.e2e.ts)覆盖真实组合。测试期望归拥有者目录；可见交互变化另需目标平台的真实窗口与按 PR 要求录制的演示。
