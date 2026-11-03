# 工具与提供者

能力由 Service Definition、Service Provider 和 Consumer 共同组成。新行为优先通过[架构中的扩展点](../../../../docs/architecture.md#where-new-behavior-goes)接入；新增工具按[工具教程](../../../../docs/cookbook/adding-a-tool.md)设计输入、执行、输出与 UI 呈现。

## 定义与执行

定义应服务所有当前消费者，避免把工具 schema、Loader、UI 或提供者细节写进通用服务。默认值与上限由实现的显式 `resolve(request): Spec` 统一解析，执行方法只消费已解析值。

| 角色 | 示例 | 关注点 |
| --- | --- | --- |
| Service Definition | [ShellExecutor](../../../../packages/shell/shell/src/index.ts)、[Shell 类型](../../../../packages/shell/shell/src/types.ts) | 请求与 spec、取消、返回句柄及进程结果语义 |
| Service Provider | [LocalBashExecutor](../../../../packages/shell/bash-local/src/index.ts) | 校验配置、解析默认值，通过 subprocess 管理进程 |
| Consumer | [Bash 工具](../../../../packages/shell/tool-bash/src/index.ts) | 模型参数、工作目录、后台 job、结构化结果与纯 presenter |

部署可调项进入有 schema 的 `Config`。在模型 JSON、配置和进程输入处完成必要校验；强类型进程内接口不重复猜测无效输入。权限决定必须在实际执行路径中强制生效，不能只隐藏 schema 或提示词。

## 输出与呈现

提示词、schema、结果和诊断使用模型需要的概念。限制在完整的输出值形成时计算，计入包装、元数据和多字节内容。错误区分执行失败、取消和未知结果；具体处理按[错误规则](storage-and-errors.md)。

Host presenter 保持纯函数，Web 卡片读取原始调用、结果事件和持久元数据；UI 格式不进入工具领域模型。新增模型可见内容要有日志表示和对应快照。

## 验证

参考 [Shell 服务测试](../../../../packages/shell/shell/tests/service.spec.ts)、[Bash 工具测试](../../../../packages/shell/tool-bash/tests/tools.spec.ts)和[组合测试](../../../../packages/shell/tool-bash/tests/integration.spec.ts)。同时计划当前改动需要的能力定义、真实组合、取消/卸载和模型输出证据；产品可见插件需要 Loader 真实组合，不能只靠手工挂载插件的单元测试。
