# 窗口、退出与原生能力

适用于修改窗口显隐、托盘、原生菜单、外部页面或本地文件交互。主编排在 [main](../../../../apps/desktop/src/main.ts)，窗口行为的公开说明归 [Desktop README](../../../../apps/desktop/README.md#closing-the-window-and-quitting)。

## 关闭、退出与重启

主窗口的 close 默认隐藏并保留同一文档和 Host；不能销毁 React 页面、重载 URL 或停止任务。Windows 首次隐藏需要现有 [background-notice](../../../../apps/desktop/src/background-notice.ts)确认；托盘、第二次启动和系统激活复用已有窗口。Welcome 关闭按自身平台规则处理。

普通 quit 经 [quit-confirmation](../../../../apps/desktop/src/quit-confirmation.ts)询问 Host 当前工作和已加载会话的定时提醒；未知检查结果按可能有工作处理。并发退出共用一次决定，旧检查或旧对话框答案不能在安装器接管后再触发退出。

操作系统结束会话、开发重启、致命恢复和已授权安装交接有各自跳过确认的入口，不能把一个全局布尔永久留到下次普通退出。macOS 关机可能被其他应用取消，后续重新 show/focus 时要恢复正常退出语义。

真正退出先阻止新启动与发布，等待 Host、嵌入页面、文件准备和自有后台工作释放。Host 的子进程退出是否已确认与任务是否干净收尾是不同事实；安装所需的更严格条件见[更新规范](updates-and-settings.md)。

## 原生能力的实现位置

| 能力 | 优先扩展的已有所有者 |
| --- | --- |
| 窗口菜单、快捷键与编辑转发 | [keybindings](../../../../apps/desktop/src/keybindings.ts)、[keyboard](../../../../apps/desktop/src/keyboard.ts)、[preload-menu](../../../../apps/desktop/src/preload-menu.ts) |
| Windows 标题栏与窗口状态 | [windows-layout](../../../../apps/desktop/src/windows-layout.ts)、[preload-windows](../../../../apps/desktop/src/preload-windows.ts)，保留全屏与 overlay 的输入限制 |
| 文件夹选择与文件动作 | [directory-picker](../../../../apps/desktop/src/directory-picker.ts)、[file-actions](../../../../apps/desktop/src/file-actions.ts)，复用具名 API 与窗口所有权检查 |
| 系统文件拖出 | [file-drag](../../../../apps/desktop/src/file-drag.ts)及 [Host 资源授权](../../../../apps/desktop-host/src/file-drag.ts)，保持租借源文件与临时副本的不同释放责任 |
| 托盘和重复启动 | [tray](../../../../apps/desktop/src/tray.ts)、[single-instance](../../../../apps/desktop/src/single-instance.ts)，不能另起第二个 Host |

保持 BrowserWindow 的 `nodeIntegration: false`、`contextIsolation: true`、`sandbox: true`、`webSecurity: true`；新增原生能力通过 preload 定义，不能为省一次 IPC 放开窗口权限。

窗口外观和遮挡逻辑按平台判断，业务组件从已发布的窗口状态适配，不自行访问 Electron。原生壳文案由 [locale](../../../../apps/desktop/src/locale.ts)维护，嵌入 Web 的文案由客户端 locale 维护，不能用翻译文本作内部状态判断。

## 验证选择

[main-startup](../../../../apps/desktop/tests/main-startup.spec.ts)、[quit-confirmation](../../../../apps/desktop/tests/quit-confirmation.spec.ts)、[single-instance](../../../../apps/desktop/tests/single-instance.spec.ts)验证显隐、退出交错和重用。具体原生能力跑其拥有者测试；原生焦点、托盘、全屏、系统退出与文件交付需要目标操作系统的真实 Electron 证据，jsdom 与 mocked main 不能代替。
