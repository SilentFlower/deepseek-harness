# 性能验证规范

`benchmarks/` 承担跨包用户路径的性能检查；包内诊断留在拥有者并使用 `.perf.ts`。完整规则由[基准目录指令](../../../../benchmarks/AGENTS.md)和[性能技能](../../../../.agents/skills/dsh-speed-up-perf/SKILL.md)维护。

## 开发前阅读项（Pre-Development Checklist）

先明确用户场景、合成输入、测量起止点、机器参考、预算算法与已知排除项。读取对应生产入口、worker、常量和报告逻辑；不要先改阈值或从实测较快推断行为等价。

## 测量模式

| 示例 | 阅读重点 |
| --- | --- |
| [Session 打开基准](../../../../benchmarks/session-open/session-open.bench.ts) | 固定工作量、多个独立进程、端点与预算 |
| [构建 worker 支持](../../../../benchmarks/support/built-worker.ts) | plain Node 运行已构建代码及超时与进程所有权 |
| [报告接口](../../../../benchmarks/support/scaling-report.ts) | 时间、CPU、内存和场景元数据 |
| [浏览器重连基准](../../../../benchmarks/active-stream-reconnect/reconnect.bench.client.ts) | 浏览器用户路径与构建后的 Client |

使用固定合成输入，不使用用户数据、记录 Session、环境中的仓库或网络服务。进程样本使用新子进程和私有临时根；浏览器样本使用新的浏览器与测试组合。测量真实产品入口，不复制产品算法，也不为测量增加公开 API。

预算断言前通过 `recordTimings` 记录时间和 CPU/等待说明，通过 `recordPeakMemory` 记录进程峰值内存。时间比例不用于内存或无量纲比值；预算由审阅的源码常量维护，不由环境变量覆盖。

## 质量检查项（Quality Check）

检查 worker 在 plain Node 下解析到构建产物、失败后子进程和根目录均已清理、样本与汇总足以重算结论。优化同时提供行为保持证据和前后测量；完整要求及执行入口从目录指令、根 scripts 与 owning benchmark 读取。
