# Props、响应数据与 Store 声明

适用于设计组件数据输入、inject 和交互状态。框架类型归 [ui-slots](../../../../packages/client/ui-slots/src/index.ts)及 [store 类型](../../../../packages/client/ui-slots/src/store.ts)，通用数据选择见[共享状态指南](../../guides/client/state.md)。

## 使用派生 Props

普通组件从 `PropsRuntime`、`PropsRenderSlots`、`PropsRenderFactories`、`PropsStore` 与 `InjectFace` 组合所需份额；本地化等附加份额继续从声明派生。Factory 使用对应 `FactoryComponentPropsOf`、`FactoryLocalComponentPropsOf` 等类型，不能手写复制框架字段。

owner 是父渲染点已知的数据；inject 从 apply 闭包声明的依赖取得普通值和回调。组件不接收 Context、不读取服务或业务 React Context。React 内容通过 slot 组合，不能为跨包复用把 ReactNode 塞进新业务 props。

## 选择数据寿命

| 数据 | 声明位置与访问方式 |
| --- | --- |
| 父组件已知 | owner props，在 renderSlot 调用点传入 |
| 仅当前组件需要 | 组件局部状态 |
| 跨入口共享或需跨重挂保留 | 注册时声明 store，`useStore` 读，`actions` 写 |
| 注册者私有的响应值 | inject 的 `hooks` 或已支持的 `keyedHooks` compartment，由 renderer 生成 hook |
| Session、workspace 等领域对象 | 既有标准来源或领域对象层，不能复制进交互 store |

渲染时读取外部可变数据必须走框架生成的 hook。inject 不自制订阅 hook、selector props 或整个服务对象；组件不镜像外部 snapshot 到本地 state。派生值纯计算，资源读取使用既有 `useResource`。

## Store 与 Factory 的实例

store 由导出的 `createXXXStore()` 工厂定义，完整 actions 是写接口。共享 handle 在 apply 中创建并交给注册，不放模块顶层；组件不自行调用工厂或 `.create()`。测试可直接创建实例以验证 store 行为。

共享 handle 不能挂到不同 scope。传入普通注册的 store 工厂由框架创建注册所属 handle；传入 Factory 定义的 store 工厂则延迟到 occurrence 物化，为每个位置创建独占 handle。后者拒绝声明持久化 key，不能让多个 occurrence 写同一份持久状态。

observable 对象及未变化时的 snapshot 引用都保持稳定。同一 key 的来源变化时，通过原发布通道让消费者观察到更新，不在渲染层补第二套缓存或同步 effect。

## 验证选择

[type-chain](../../../../packages/client/ui-slots/tests/type-chain.client.spec.tsx)验证 owner、inject、store 与 child props 的组合约束；[core](../../../../packages/client/ui-slots/tests/core.client.spec.ts)验证跨 scope 挂载。真实实例寿命由 [renderer registry](../../../../packages/client/ui-renderer/tests/registry.client.spec.ts)和 [factory-slots](../../../../packages/client/ui-renderer/tests/factory-slots.client.spec.tsx)验证；组件测试只需要真实派生 props 和可驱动的普通数据。
