# Profile 与应用启动

profile 和 bundle 的组合语义由[架构](../../../../docs/architecture.md#profiles-and-bundles)与[app-boot README](../../../../packages/boot/app-boot/README.md)维护。profile 选择有序 bundle，用户 patch 与命令行 overlay 继续应用在其上。

## 启动与配置

支持的应用统一使用 `dsh` 启动器，不新增绕过 profile 的 package bin、demo 或 SDK 任意 argv 通道。CLI 解析参数并交给 profile boot，功能插件通过声明的服务读取应用参数。

| 示例 | 阅读重点 |
| --- | --- |
| [CLI bin](../../../../apps/cli/src/bin.ts) | 统一应用分发入口 |
| [profile-boot](../../../../apps/cli/src/profile-boot.ts) | profile、patch、就绪提交和关闭的共同拥有者 |
| [基础 bundle manifest](../../../../packages/bundle/base/package.json) | bundle 载荷与配置声明 |
| [Desktop README](../../../../apps/desktop/README.md) | 分发资源、私有 Host 与产品数据的归属 |

`cordis.yml` 的 `!!js` 只用于允许的 config 和 disabled 位置；其他元数据保持字面值。缺少依赖或引用在能够判断的最早点明确失败，不依赖条目顺序或静默跳过。普通 bundle、函数插件和库的安装方式不同，先检查 manifest 和入口导出。

## 验证

跨包 profile 行为放在 [apps/cli/tests/profiles](../../../../apps/cli/tests/profiles/AGENTS.md)，包私有 Loader 配置放在拥有者的 fixtures。改动 CLI 输出需对应输出证据，改动安装/产物路径还需 packed 或 built smoke。参考[默认 Web 隔离测试](../../../../apps/cli/tests/profiles/web/tests/web-default-isolation.expected.e2e.ts)。签名与发布遵循应用自己的 SOP，不从启动变更推导发布权限。
