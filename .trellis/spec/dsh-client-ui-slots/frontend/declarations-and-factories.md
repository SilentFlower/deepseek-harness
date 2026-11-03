# Slot 声明、路由与 Component Factory

适用于新增界面扩展位置、调整组合或修改 SlotCore。先读 [SlotMap 与 SlotFactoryMap 类型](../../../../packages/client/ui-slots/src/index.ts)、[Slots 子系统](../../../../docs/subsystems/slots.md)和[客户端指令](../../../../packages/client/AGENTS.md)。本包承载不依赖 React 运行时的组合规则，Cordis 与 React 的集成归 [ui-renderer](../../dsh-client-ui-renderer/frontend/index.md)。

## 选择组合方式

父组件拥有的扩展位置使用普通 slot：在 `SlotMap` 声明类型，在父注册的 `children` 同时声明 runtime spec 和渲染授权，子贡献再向该 key 注册。命名沿组合路径；不要重复声明父组件已拥有的位置。

设计为复用的组件或组合使用 `SlotFactoryMap` 与 `registerFactory()`，无需凑出多个调用者。定义的 `children` 仍是全局唯一的普通 slot；局部 `slots` 才是每次 render occurrence 的组件选择，二者不能互换。

业务插件注册到已有位置；只有 shell 渲染 root。全局浮层使用已声明的 `shell.overlay`，不能注册 root 把整个应用框架遮蔽掉。

## 路由与占位身份

| kind | 修改时必须保持 |
| --- | --- |
| `single` | 同一 priority 的占位冲突拒绝；不同 priority 可形成遮蔽 |
| `keyed` | `key` 对应实际业务分派身份；同 key 同 priority 冲突拒绝 |
| `list` | `id` 标识贡献；同 id 同 priority 冲突拒绝，不用数组位置伪造身份 |
| `chain` | 必须有纯 `select`；按 priority、同优先级按注册顺序寻找首个非 null 结果，全部落空才用 fallback |

不要把 `renderSlotChain` 与普通 `renderSlot` 混用。组件只能渲染本次注册声明的 children；通过 props 转交 renderer 时仍保留原授权身份。

## 声明的生命周期

移除父贡献会递归 collapse 它声明的 children、子贡献和 store 挂载。旧 disposer 必须幂等，旧渲染授权不能对后来同名声明继续有效。declaration epoch 只在声明与 collapse 时变化，不能用普通 entry version 代替。

跨插件贡献用 `ctx.slots.inject(key, callback)` 等待实际 slot 声明；回调可返回同步 disposer 或同步 generator，将多次注册作为可回滚的一组。不要依赖配置顺序、延时或无关业务 service 当声明已存在的信号。其 effect 集成见[注册与监督](../../dsh-client-ui-renderer/frontend/registry-and-supervision.md)。

Factory 调用通过 `renderFactorySlot()`，继承当前位置 scope，不能自带 Session 身份。局部 Component 使用稳定函数身份；在 render 中新建组件函数会重挂其子树，调用者必须确实需要这项状态重置。

## 验证选择

[core](../../../../packages/client/ui-slots/tests/core.client.spec.ts)验证冲突、递归 collapse 与 Factory；[type-chain](../../../../packages/client/ui-slots/tests/type-chain.client.spec.tsx)验证派生授权和错误类型组合；[dynamic-keys](../../../../packages/client/ui-slots/tests/dynamic-keys.client.spec.ts)验证动态声明。涉及真实渲染时补 [Factory 渲染](../../../../packages/client/ui-renderer/tests/factory-slots.client.spec.tsx)和[过期授权](../../../../packages/client/ui-renderer/tests/stale-authorization.client.spec.tsx)。
