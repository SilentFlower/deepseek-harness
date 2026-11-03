# 插件与生命周期

注册是一种需要撤销的副作用，所属 Context 和 fiber 决定其生命周期。语义见 [Cordis primer](../../../../docs/cordis-primer.md)、[包级指令](../../../../packages/AGENTS.md)和[通用防御规则](../../../../docs/defensive-patterns/general.md)。

## 注入与注册

需要服务的插件声明 `inject` 或 `static inject`；可选服务通过 `ctx.get(name)` 读取。不要以配置顺序或定时等待代替依赖声明。注册 API 返回 disposer 或有文档的注册句柄；贡献通过 `ctx.effect()`、`ctx.on()` 或内部已经管理 effect 的注册 API 进入 fiber。

| 示例 | 阅读重点 |
| --- | --- |
| [命令注册表](../../../../packages/interaction/commands/src/index.ts)的 `CommandRuntime.register` | 注册及 scoped layer 的所有者 |
| [标题服务](../../../../packages/session/session-title/src/index.ts)的 `register` | 提供者的异步撤销、在途任务与服务释放 |
| [资源客户端](../../../../packages/client/resources/src/client/index.ts)的 `apply` | 服务面与后注册消费者之间的撤销顺序 |
| [Goal 服务](../../../../packages/goal/goal/src/index.ts)的初始化方法 | 等待投影注册成功后安装后续监听 |

## 事件与异步工作

事件使用声明合并和有类型的载荷；事件文档说明模式及参数。Waterfall 监听调用 `next()` 才继续，直接返回会截断后续监听。标题服务的 `llm/stream` 监听提供局部示例；不要把所有异步事件都视为广播。

一个异步操作由一个控制器或事务拥有取消、就绪、完成与撤销；额外状态必须对应独立所有者或独立完成时点。共享可变数据归服务或实例所有，避免模块级 Map、全局当前对象或隐式单例。先停止并等待消费者，再释放它依赖的服务、文件或进程；卸载错误不能吞掉未知结果。

## 验证

对注册项卸载 fiber 后观察实际移除；参考[标题投影卸载测试](../../../../packages/session/session-title/tests/projection.spec.ts)和[标题提供者生命周期测试](../../../../packages/session/session-title/tests/provider.spec.ts)。新增异步测试使用[CI 可靠性规则](../../../../.agents/skills/dsh-ci-test-reliability/SKILL.md)，验证失败和取消后的静止状态。专门做 Cordis 生命周期审查时使用[对应审查技能](../../../../.agents/skills/cordis-styling-nitpicking/SKILL.md)。
