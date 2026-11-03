# Web 构建与浏览器入口

`apps/web` 拥有浏览器应用的 Vite 入口，界面能力由客户端插件提供。包职责见[应用 manifest](../../../../apps/web/package.json)与[客户端架构](../../../../docs/subsystems/web-client.md)；产品 Node 服务仍走统一 `dsh web` 启动流程。

## 构建职责

| 文件 | 归属 |
| --- | --- |
| [main.ts](../../../../apps/web/src/main.ts) | 浏览器入口 |
| [vite.config.ts](../../../../apps/web/vite.config.ts) | Web 打包、资产与模块解析 |
| [product-isolation.ts](../../../../apps/web/product-isolation.ts) | 默认产品构建的实验能力隔离 |
| [Web 测试说明](../../../../apps/web/tests/README.md) | 真实浏览器流程与测试运行方式 |

业务 UI 放在拥有功能的插件包，避免堆入应用入口。浏览器与 Host 程序的 imports、external 和依赖声明分别检查；私有 WebWorker preview 不成为新的 Node 应用入口，也不自动进入默认产品。

## 验证

改变构建或公开入口时验证产物、默认产品隔离和相关 browser smoke。改变 UI 行为时使用[客户端验证要求](../client/ui.md)，真实流程应加载产品组合，不以只渲染组件的测试替代应用证据。
