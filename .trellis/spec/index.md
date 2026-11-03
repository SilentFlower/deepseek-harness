# DeepSeek Harness 开发规范

本目录供开发任务按职责选读。详细规则由仓库 `AGENTS.md`、包 README、子系统文档和技能各自维护；这里提供阅读顺序、源码示例和检查入口。

## 按包选读

先读[共享指南](guides/index.md)，再从 [Trellis 配置](../config.yaml)选择实际工作区，读取 `<package>/<layer>/index.md`。每个包的入口链接自己的 README、源码和测试，再链接下表中适用的共享专题。npm 工作区由 [pnpm-workspace.yaml](../../pnpm-workspace.yaml)定义；共享专题不替代包配置。

| 修改路径 | 规范入口 |
| --- | --- |
| `packages/`，包括其他范围的 Host 插件 | [Harness 运行时](guides/harness/index.md) |
| `packages/client/`，其他包的浏览器实现 | [客户端](guides/client/index.md) |
| `packages/experimental/` | [实验能力](guides/experimental/index.md)，浏览器部分加读[客户端](guides/client/index.md) |
| `apps/` 的 CLI、Desktop 和 Host 入口 | [应用启动](guides/apps/index.md) |
| `apps/web/` 的构建和浏览器入口 | [Web 应用构建](guides/apps/index.md)及客户端规范 |
| `python/` | [Python SDK 与运行时](guides/python/index.md) |
| `native/` | [原生能力](guides/native/index.md) |
| `vendor/` | [固定版本的第三方源码](guides/vendor/index.md) |
| `scripts/`，根构建和检查配置 | [脚本与生成器](guides/tooling/index.md) |
| `benchmarks/` | [性能验证](guides/benchmarks/index.md) |
| `website/` | [文档网站](guides/website/index.md) |
| `docs/`、包 README、Agent 指令 | [文档写作](guides/docs/index.md) |

跨包任务读取所有受影响包的入口。API、实验包中的浏览器实现同样遵循客户端规则。没有独立 npm 包的脚本、Python SDK 和文档从共享专题进入。包的公开能力、配置和限制始终先读其 README 与源类型，目录地图见 [packages/README.md](../../packages/README.md)。

## 核心模块专题

以下模块在包入口下提供独立专题，按实际修改路径选读；其余工作区继续通过各自索引与共享指南定位。

| 模块 | 专属规范入口 |
| --- | --- |
| Agent 循环 | [生命周期、请求与失败恢复](dsh-agent-loop/backend/index.md) |
| Session | [事件历史、Fork 与耐久性](dsh-session/backend/index.md) |
| Tools | [注册准入、策略与结果](dsh-tools/backend/index.md) |
| Session 投影 | [状态回放、注册与同步读取](dsh-session-projection/backend/index.md) |
| UI slots | [声明、Factory、Props 与 Store](dsh-client-ui-slots/frontend/index.md) |
| UI renderer | [挂载、绑定、实例与错误监督](dsh-client-ui-renderer/frontend/index.md) |
| Desktop | [二开入口、原生桥、窗口、更新与打包](dsh-desktop/backend/index.md)，含 [Welcome](dsh-desktop/frontend/index.md)与[私有 Host](dsh-desktop-host/backend/index.md) |

## 维护

增加规范时同步直接父索引；增加工作区时同步包配置和对应入口。只有源码、测试或现行规则能够支持的约定才进入规范。项目规则的详细定义保留在原归属文档，规范链接到它；任务计划与检查结果留在任务目录。
