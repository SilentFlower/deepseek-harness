# Preload、IPC 与 Host 认证

适用于新增 Desktop 原生 API、调整 boot、HTTP/WebSocket 转发或嵌入页面。先读 [ipc 类型与频道](../../../../apps/desktop/src/ipc.ts)、[preload-app](../../../../apps/desktop/src/preload-app.ts)、[main 处理器](../../../../apps/desktop/src/main.ts)和 [web-document](../../../../apps/desktop/src/web-document.ts)。

## 三条通信路径

| 路径 | 用途与修改要求 |
| --- | --- |
| 产品网页 → Host HTTP/WebSocket | 共享 Web API、插件管理与流；复用现有鉴权和业务服务 |
| 产品或壳页面 → Electron IPC | 具名原生操作和安全状态；由各自 preload 暴露最小 API |
| Electron → 私有 Host Node IPC | boot injections、ready/fatal、任务检查与 shutdown；生命周期归 [Host 规范](../../dsh-desktop-host/backend/startup-and-shutdown.md) |

不要给 renderer 暴露原始 `ipcRenderer`、文件系统、shell、任意 pnpm argv 或可任意选频道的代理。新增操作先定义 typed API，再同时维护 preload 映射、主进程验证、消费者和卸载；订阅 API 返回 unsubscribe。

## 认证与来源

主文档是 `dsh-app://app`，本地更新等壳页面是 `dsh-app://shell`。来源检查使用 `assertDesktopSender`；要求主窗口或主 frame 的操作还须检查确切 webContents 与 senderFrame。仅检查 scheme/hostname 不足以授权所有敏感操作，不能把另一窗口或嵌入 frame 当主产品窗口。

Node IPC、Electron IPC、文件和网络数据均在进入处按实际字段验证；同进程已类型化的调用不另加猜测性 fallback。payload 字段必须从当前声明读取，不能因类似旧频道就扩大接受范围。

Host ready URL 经认证交换得到的 cookie 留在主进程。HTTP 转发丢弃页面提供的 cookie/origin，使用当前 Host 的凭据；响应不能把认证 `set-cookie` 交给页面 cookie jar。WebSocket 只有确切产品 webContents、当前 Host authority、匹配 ws/wss scheme 及产品 origin 才能附带认证。

静态文件保持路径包含检查、GET/HEAD 和 MIME 处理；Host 不可用时动态请求失败，不能返回伪成功空结果。插件 bundle 的缓存策略与响应头处理归 `forwardWebRequest`，保持流式和取消传递。

## 嵌入网页的独立权限

主窗口开启 webview 不等于允许任意 guest 接入。guest 必须符合主进程发出的 lease 与 partition，并保持 sandbox、context isolation、web security，无 Node 和 guest preload，见 [browser-guests](../../../../apps/desktop/src/browser-guests.ts)。

Platform 账户文档使用独立的 [platform-view](../../../../apps/desktop/src/platform-view.ts)与 [platform preload](../../../../apps/desktop/src/preload-platform-account.ts)。凭据仅通过私有路径交给受信页面，不传给 Harness renderer；origin、账户分区与关闭后的存储清理规则按其 owning 实现维护。不要为复用新页面而扩大账户 token 的可读范围。

## 验证选择

[preload-app](../../../../apps/desktop/tests/preload-app.spec.ts)和 [web-document](../../../../apps/desktop/tests/web-document.spec.ts)验证 API、认证与文件处理；[platform-view](../../../../apps/desktop/tests/platform-view.spec.ts)验证独立账户文档；涉及真正 sandboxed preload 的改动使用 [preload e2e](../../../../apps/desktop/tests/preload.e2e.ts)或 [platform preload e2e](../../../../apps/desktop/tests/platform-preload.e2e.ts)。同时包含错误窗口、错误 frame、错误 origin、过期 Host 和订阅释放的拒绝路径。
