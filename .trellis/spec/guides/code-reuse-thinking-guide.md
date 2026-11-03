# 复用与职责选择

新增工具、服务、状态或配置前，先找已有的定义、实现与消费者。具体规则见[包级指令](../../../packages/AGENTS.md)、[能力定义](../../../docs/glossary.md#capability-seam)和[包结构防御规则](../../../docs/defensive-patterns/package-surface.md)。

## 查找顺序

先查符号、配置键、事件名和导出，再查包 README 与[扩展指南](../../../docs/cookbook/extension-cookbook.md)。跨包使用已声明的包入口，包内使用带 `.ts` 的相对导入；不要为测试或单一内部调用扩大公开 API。

| 需求 | 现有示例 | 阅读重点 |
| --- | --- | --- |
| 执行命令 | [ShellExecutor](../../../packages/shell/shell/src/index.ts)、[LocalBashExecutor](../../../packages/shell/bash-local/src/index.ts)、[Bash 工具](../../../packages/shell/tool-bash/src/index.ts) | 定义、提供者、消费者分别承担默认值、执行机制和工具呈现 |
| 注册人类命令 | [命令注册表](../../../packages/interaction/commands/src/index.ts) | 从现有注册 API 获得撤销句柄，不向循环添加业务分支 |
| 多入口共享交互状态 | [设置 store 工厂](../../../packages/client/ui-settings-general/src/client/shell-store.ts) | 工厂声明状态和完整动作，实例由注册作用域拥有 |

## 提取判断

共享代码必须有当前消费者与明确归属。服务、控制器和网关保留通用调度，业务规则进入自己的包并通过注册接入。优先评估能够删除自维护实现和测试的成熟依赖；不要仅为了统一命名而建立新层。

避免模块级可变缓存、全局当前对象和跨 UI 功能包的运行时导入。组件行为通过 slots、注入回调和声明的 store 共享；详见[客户端组合](client/slots.md)。部署差异由拥有实现的 `Config` 校验，不以隐藏常量或测试专用开关代替配置。

## 验证

搜索全部消费者后再改签名、常量或配置键。注册类行为需要卸载后撤销的证据；状态和派生值需要明确唯一来源。复用不能绕过所有者的权限、生命周期或错误处理。
