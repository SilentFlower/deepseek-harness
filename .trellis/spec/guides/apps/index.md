# 应用入口与组合

适用于 `apps/` 的 CLI、Desktop、Host、Web 构建和安装相关代码。受支持的 Node 应用由命名 `dsh` profile 启动；具体规则见[应用启动架构](../../../../docs/architecture.md#application-launch)。

## 开发前阅读项（Pre-Development Checklist）

先读[共享指南](../index.md)和应用自己的 README。修改组合时读[profile 与启动](profiles.md)，修改 Web 入口时读[Web 构建](web-build.md)及[客户端规范](../client/index.md)。应用涉及底层服务时还要读取[Harness 规范](../harness/index.md)。

## Desktop 二开

先从 [Desktop 专属规范](../../dsh-desktop/backend/index.md)选择 Electron、Host 或共享客户端的实现位置；独立本地页面读 [Welcome 规范](../../dsh-desktop/frontend/welcome-and-shell.md)，Node-mode 后端读 [Host 生命周期](../../dsh-desktop-host/backend/startup-and-shutdown.md)。打包、签名和安装后的验证按 Desktop 的专题执行。

## 质量检查项（Quality Check）

- Node 应用由 `dsh` profile 启动，组合配置与 resolver manifest 的依赖匹配。
- CLI、Desktop、SDK 的用户数据目录、就绪与关闭规则保持显式。
- 配置变更通过真实 Loader/profile 验证；安装与发布路径使用构建产物证据。
