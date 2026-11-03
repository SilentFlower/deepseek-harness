# 包与编译入口

包的创建、职责命名与发布内容由[新增包教程](../../../../docs/cookbook/adding-a-package.md)、[包级指令](../../../../packages/AGENTS.md)和[包结构防御规则](../../../../docs/defensive-patterns/package-surface.md)维护。先区分服务插件、函数插件、普通库与 bundle，再选择现有结构。

## 文件与导入

包通常使用 `packages/<group>/<package>/src/`、包级 `tests/`、README、manifest 与 tsconfig。`src/types.ts` 只放类型；跨包通过 manifest 声明的包入口导入，包内相对导入带 `.ts`。服务包默认导出服务类；函数插件具名导出 `name`、`inject`、`Config` 和 `apply`，不要混用两种插件形式。

| 示例 | 可以参考的内容 |
| --- | --- |
| [Shell 服务](../../../../packages/shell/shell/src/index.ts) | 抽象服务类、Context 声明合并、默认服务导出 |
| [Bash 工具](../../../../packages/shell/tool-bash/src/index.ts) | 函数插件、配置接口和运行时 schema |
| [Scope 库](../../../../packages/core/scope/package.json) | 普通库的公开入口及类型声明位置 |
| [基础 bundle](../../../../packages/bundle/base/package.json) | `dsh.bundle` 元数据及组合归属 |

工作区依赖的声明与外部性由[依赖校验器](../../../../scripts/verify-package-dependencies.ts)维护；Harness 包使用 `workspace:*`，vendor/native 使用 `workspace:~`。不要用深层源码导入绕过公开入口，也不要为测试增加产品导出。

## 编译程序

源码检查的路径解析指向 `src`，发布和进程运行使用构建后的 `lib`。编译布局见[开发文档](../../../../docs/development.md#typescript-project-layout)。普通包根 tsconfig 是编译程序；同时拥有独立 Host 与 Client 程序的包使用叶配置，根配置只列 references，聚合配置引用相应叶配置。

参考 [ui-settings-general 根配置](../../../../packages/client/ui-settings-general/tsconfig.json)、[Host 叶配置](../../../../packages/client/ui-settings-general/tsconfig.host.json)和[Client 叶配置](../../../../packages/client/ui-settings-general/tsconfig.client.json)。普通双入口客户端插件不因此强制拆分程序。

## 验证

修改 exports、依赖、编译或运行入口时核对实际发布载荷，并按[质量指南](../quality.md)执行构建、hygiene 和拥有者的产物 smoke。参考[工具公开导出测试](../../../../packages/core/tools/tests/exports.built.e2e.ts)。更新 API 时同时更新全部消费者和归属文档。
