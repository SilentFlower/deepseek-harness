# 私有 Host 启动、控制与关闭

适用于修改 Electron 的 Node-mode Host。先读 [Host main](../../../../apps/desktop-host/src/index.ts)、[DesktopHostProcess](../../../../apps/desktop/src/host-process.ts)与[Desktop 启动链](../../dsh-desktop/backend/architecture-and-development.md)。本包运行现有 Web profile，不另行定义工具、会话或模型循环。

## Ready 的含义

Host 用当前安装 runtime 的 dsh 作为 anchor 加载 Desktop profile，通过共享 `runProfile` 启动。默认参数使用 loopback 和系统分配端口；不能假设 Desktop 也在 Web 的固定端口上。插件依赖与配置仍交给共享 Loader。

`starting` 携带本次 runId；应用、控制器和必要贡献初始化成功后，才发送带 authenticated URL 与 boot injections 的 ready。fatal 同时保留用户摘要与完整诊断；不能因为监听已打开就过早宣告整个客户端可用。

Electron 对 Host 消息验证 discriminator 和载荷；控制请求带 requestId、有明确 deadline、取消和 finally 清理。扩展消息时同步发送者、接收联合类型、验证器和拒绝路径。release metadata 中的 Host 协议归 [host-protocol](../../../../apps/desktop/src/host-protocol.ts)，不要只改一侧常量。

## 检查任务与请求准入

[update-tasks](../../../../apps/desktop-host/src/update-tasks.ts)把 running Agent、排队 inbox，以及全局和 Agent 的 running/stopping job 视为活动任务。API 读取本身不是任务，但安装锁必须拒绝新请求，等待已接受请求完成，再复查它们产生的工作。

[quit-inspection](../../../../apps/desktop-host/src/quit-inspection.ts)在相同任务判断上增加当前已加载会话的 armed schedule。不能为退出检查去恢复所有磁盘会话，也不能把服务缺失或检查失败答成无任务。controller 随 Context 释放后拒绝继续检查。

新增 Host 业务通过已有服务或贡献扩展，保持共享服务依赖声明；不要在这个编排入口按业务类型堆积分支。文件拖出等跨进程请求必须保留其领域授权、取消和资源所有权。

## 关闭与结果

Host 收到 shutdown 或父进程断开时，合并到同一个 stopping Promise：先取消并等待自己持有的资源读取任务，再等待已启动应用的 shutdown，成功后发送 `shutdown-complete`，断开 IPC 并结束进程。失败启动由启动路径报告，不能为未完成关闭发送成功 acknowledgement。

父进程的 stop 要等待真实 close，超过优雅期限才升级终止。`requireGraceful` 还要求未超时、退出码成功并收到 shutdown acknowledgement；单纯退出不能证明任务干净收尾。已确认退出但未干净收尾与尚未确认退出分别报告，供 Electron 决定能否恢复 Host 或交给安装器。

## 验证选择

[host-process](../../../../apps/desktop/tests/host-process.spec.ts)验证消息、deadline、父子断开与关闭确认；[backend-controller](../../../../apps/desktop/tests/backend-controller.spec.ts)验证启动取消及重试串行；[host-update-tasks](../../../../apps/desktop/tests/host-update-tasks.spec.ts)与 [quit-inspection](../../../../apps/desktop-host/tests/quit-inspection.spec.ts)验证任务和提醒范围。影响真实 Loader 或关闭的变更还需[已构建 Host 场景](../../../../apps/desktop/tests/fixtures/host-update-qualification.mjs)，不能只用手工 mock Context 证明组合可用。
