# 原生能力规范

原生包独立维护平台载荷和版本，仍属于同一个 Git 与 pnpm 工作区。完整规则见[原生目录指令](../../../../native/system/AGENTS.md)、[README](../../../../native/README.md)与[launcher CLI 约定](../../../../native/system/docs/cli-contract.md)。

## 开发前阅读项（Pre-Development Checklist）

读取[共享指南](../index.md)、原生调用者、入口类型和平台 manifest。区分 JavaScript 入口、可审计 C 源码、预构建平台包和测试 syscall fixture，按受影响能力选择实际平台检查。

## 能力与平台

| 示例 | 阅读重点 |
| --- | --- |
| [Landlock JavaScript API](../../../../native/system/packages/entry/src/index.ts) | grants、探测和 launcher argv 的共同归属 |
| [flock 入口](../../../../native/system/packages/entry/src/flock.ts) | 延迟加载、异步锁与调用者持有 fd 的责任 |
| [flock C 实现](../../../../native/system/packages/entry/src/flock.c) | 稳定 Node-API、异步工作与 errno |
| [Linux x64 载荷声明](../../../../native/system/packages/linux-x64/prebuilds.json) | 平台与二进制载荷矩阵 |

使用稳定 Node-API v8，不使用 V8/NAN 或实验接口。Linux glibc、musl 与 macOS 载荷分别构建；不加入安装时编译 fallback 或环境变量选择运行二进制的通道。缺少锁实现不能视为获得锁，缺少隔离能力不能绕过限制。

fd 由调用者持有到异步锁操作完成，关闭遵守底层锁语义。`./landlock-run` 与 `./flock` 是独立能力出口，不能合并成隐式加载 addon 的根入口。

## 质量检查项（Quality Check）

根据 [native manifest](../../../../native/system/package.json)与目录指令选择 TypeScript、原生构建、真实进程和打包检查。参考 [flock 测试](../../../../native/system/test/flock.test.js)、[launcher 测试](../../../../native/system/test/launcher.test.js)与[发布载荷测试](../../../../native/system/test/release-packing.test.js)。平台包检查文件格式、架构、Node-API、权限和安装后的真实能力；本机通过不能代替其他平台矩阵。
