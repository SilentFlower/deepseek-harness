# Python SDK 与运行时规范

`python/sdk` 提供同步 SDK，`python/sdk-runtime` 提供运行时分发与资源解析；开发流程见[Python 开发文档](../../../../python/development.md)，包能力分别归属 [SDK README](../../../../python/sdk/README.md)与[运行时 README](../../../../python/sdk-runtime/README.md)。

## 开发前阅读项（Pre-Development Checklist）

先读[共享指南](../index.md)，核对 [SDK 协议](../../../../packages/sdk/protocol/README.md)、Python 模型、调用者与预期输出。涉及 Session、循环或事件时再读[会话规范](../harness/sessions.md)。

## 类型、进程与资源

| 示例 | 阅读重点 |
| --- | --- |
| [models.py](../../../../python/sdk/src/deepseek_harness/models.py) | Pydantic 模型、判别联合、字段别名与 optional/null 差异 |
| [client.py](../../../../python/sdk/src/deepseek_harness/client.py) | stdio JSON-RPC、响应队列、reader 线程、取消与关闭所有权 |
| [运行时资源解析](../../../../python/sdk-runtime/src/deepseek_harness_runtime/_resources.py) | 下载 manifest、平台匹配、可执行权限和 sidecar 验证 |
| [运行时解析测试](../../../../python/sdk/tests/test_runtime_resolution.py) | 无密钥的路径、平台与资源错误验证 |

SDK 启动普通 `dsh --profile sdk`，通过 profile 和有序 patches 定制组合，不暴露任意 argv 替换。显式传入 Harness home，避免测试或脚本使用个人产品数据。回调、reader、子进程和通知订阅分别有明确完成与取消路径，关闭后不留下悬挂等待者。

不要照搬 TypeScript 字段名而遗漏 Python alias，也不要把缺失、null 和空值混用。公开类与方法记录参数、返回、异常和上下文管理行为；类型与 API 变化同步两种 SDK 的行为证据。

## 质量检查项（Quality Check）

按[开发文档](../../../../python/development.md)选择 pytest、已构建运行时和 installed-wheel 场景。fake peer 测试、源码 carrier 测试与安装 wheel 的验证分别说明覆盖范围；未构建平台的跳过不算通过。普通 SDK 改动不执行发布或替代原生平台验证。
