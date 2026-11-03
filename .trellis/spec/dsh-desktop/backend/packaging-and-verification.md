# Desktop 构建、资源与验证

适用于修改依赖、preload、发行资源、签名和更新适配器。构建入口见 [tsdown](../../../../apps/desktop/tsdown.config.ts)、[package-target](../../../../apps/desktop/scripts/package-target.ts)与 [builder 配置](../../../../apps/desktop/scripts/electron-builder-config.mjs)；具体发行操作归 [Package](../../../../apps/desktop/README.md#package)，本页用于选择二开后的检查范围。

## 编译与依赖

主程序保持 ESM；sandboxed preload 由单独构建生成 CJS。这是 Electron preload 的执行要求，不能因仓库统一 ESM 就把输出格式一并替换。preload 可 external 的模块受 Electron sandbox 限制，不能留下任意 Node 或工作区运行时 import。

主 bundle、独立 worker、preload 和 Welcome 页面有不同构建输入及可用依赖。新增依赖先判断应内联还是由安装包 manifest 携带，再核对 [desktop-bundle-imports](../../../../apps/desktop/scripts/desktop-bundle-imports.mjs)的产物检查；源码下能解析不说明安装后能解析。

Desktop bundling 依赖已有工作区构建输出；保持构建排序，不在并行工作区编译尚未完成时读取半成品 `lib`。业务源码与产物检查的职责见[共享质量指南](../../guides/quality.md)。

## 发行资源

runtime descriptor 绑定壳版本、Host 协议、Node、包记录和目标文件；修改资源布局同时核对 [release](../../../../apps/desktop/src/release.ts)、[runtime-tree](../../../../apps/desktop/src/runtime-tree.ts)、[prepare-runtime](../../../../apps/desktop/scripts/prepare-runtime.ts)和 [prepare-package-set](../../../../apps/desktop/scripts/prepare-package-set.ts)。不要手改生成描述文件来掩盖缺失资源。

目标包的 OS/arch 与 Electron、原生 addon、primary runtime 一致；不能从构建机的 node_modules 猜目标依赖。随包 pnpm 和 Node launcher 用于既有包操作路径，不要求用户另装全局 pnpm。可支持的发行目标以 `DesktopPackageTargetName` 为准，新增 Linux 等目标需要完整打包、资源和验证支持。

原生模块位置、asar unpack、文件包含与排除规则以 [runtime-file-policy](../../../../apps/desktop/scripts/runtime-file-policy.ts)及 builder 为准。删除看似重复的载荷前先验证安装后真实运行路径，不能只靠源码测试。

签名与更新源属于发行配置；本地 unsigned 或 unpacked 产物不证明正式签名、发布或 installed update 可用。Windows 操作先读[签名说明](../../../../apps/desktop/windows-signing/README.md)，更新库集成读[适配器兼容记录](../../../../apps/desktop/tests/updates/electron-updater/README.md)。

## 按影响选择验证

| 改动 | 证据入口与覆盖范围 |
| --- | --- |
| 控制器、设置、IPC 分类 | 受影响拥有者的 `tests/*.spec.ts`，明确覆盖取消、拒绝和清理 |
| preload 或真实页面 | [preload e2e](../../../../apps/desktop/tests/preload.e2e.ts)等真实 Electron 场景；mocked ipc 不证明 sandbox 加载成功 |
| 打包依赖、资源布局 | [desktop-bundle-imports](../../../../apps/desktop/tests/desktop-bundle-imports.spec.ts)、[runtime-file-policy](../../../../apps/desktop/tests/runtime-file-policy.spec.ts)、[packaged-runtime-verification](../../../../apps/desktop/tests/packaged-runtime-verification.spec.ts)，再检查目标平台 unpacked 产物 |
| 下载、校验、渠道适配 | [本地 updater qualification](../../../../apps/desktop/README.md#local-updater-qualification)与[测试归属](../../../../apps/desktop/tests/README.md)，区分真实下载和替代安装器 |
| 签名、安装与旧版升级 | 在目标 OS 取得签名安装包和真实 installed-update 证据；Windows 流程见[安装升级验证](../../../../apps/desktop/tests/installed-update/README.md) |
| 工作区中可见 GUI | 按[客户端阶梯](../../../../packages/client/AGENTS.md#before-you-push-the-local-check-ladder)检查；PR 的交互演示按[录制技能](../../../../.agents/skills/record-browser-gif/SKILL.md)要求执行 |

不能用 Linux 单元测试替代 macOS/Windows 的窗口、签名、安装和系统行为验证。报告区分已跑、缺平台、缺凭据及未覆盖的安装路径；范围无关的发布脚本和上传不属于普通文档或源码修改的验证。
