# 实验能力规范

实验状态、可选交付和 Official 标记分别表达不同事实；规则归属见[实验目录指令](../../../../packages/experimental/AGENTS.md)与[状态说明](../../../../packages/experimental/README.md#status)。实验代码遵循和其他包相同的安全、生命周期、文档和测试要求。

## 开发前阅读项（Pre-Development Checklist）

读取[Harness 规范](../harness/index.md)、包 README、manifest 与[实验命名策略](../../../../scripts/experimental-package-policy.ts)。含浏览器实现的包再读[客户端规范](../client/index.md)，不可根据所在分组跳过客户端规则。

## 依赖与组合

正式包和应用的生产依赖不能引入实验包；实验目录可依赖正式包或其他实验包，测试通过 devDependencies 使用实验能力。默认产品还验证间接安装、运行时导入和组合配置，不能只看一条直接依赖。

参考 [Inspector manifest](../../../../packages/experimental/inspector/package.json)的 Host/Client 声明、[测试专用组合](../../../../packages/experimental/inspector/tests/loader-composition.host.spec.ts)及[默认产品隔离检查](../../../../scripts/verify-default-product-isolation.ts)。opt-in 行为由显式 profile、bundle 或 patch 激活，不加入默认产品来方便测试。

发布不代表转为稳定能力；转正需要正式归属、命名、公开能力、限制、测试与载荷审查。不得因为目录名含 experimental 就默认 `private: true`；以发布策略的明确例外为准。

## 质量检查项（Quality Check）

- 包命名、发布元数据和默认产品隔离符合现行策略。
- 可见能力有真实 Loader 组合、快照和受影响的产物测试。
- 浏览器部分遵循 slots、状态和本地化规则；生命周期无实验状态豁免。
