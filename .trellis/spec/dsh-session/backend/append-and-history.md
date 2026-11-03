# 事件追加与模型历史

适用于修改 Session 事件、追加校验、消息投影和 surface 替换。先读 [Session 类型](../../../../packages/core/session/src/types.ts)、[append 与 commit](../../../../packages/core/session/src/index.ts)及 [surface](../../../../packages/core/session/src/surface.ts)，精确字段归源类型和[包文档](../../../../packages/core/session/README.md#append-and-derive)。

## 追加的原子性

`append()` 在读取载荷前检查写权限，对 JSON 做无损快照，随后再次检查权限并校验候选事件，再进入日志和通知。拒绝追加不得改变 seq、模型历史或事件流。不要把校验推迟到持久化 flush，也不能保存调用者仍能修改的对象。

store-owned Session 在进入注册表并成功完成 `session/created` 前保持只读，detach 后也不可写。`session/event` 观察者不能重入 append；通知的异常按现有逐监听器隔离规则处理，不能把已经提交的事件描述为回滚成功。

## 新增事件时的决定

| 事件用途 | 必须一起检查 |
| --- | --- |
| 模型可见消息 | `surfaceOp`、消息来源、派生历史和请求重建；模型看到的内容必须可由日志恢复 |
| 修改已有消息内容 | `@messageProjection` 声明及纯投影注册；离线读取者也要提供同一组定义 |
| 仅日志事实 | 不得夹带 surface 元数据或意外进入模型历史 |
| 实验包私有记录 | 遵循 [plugin record 规则](../../../../packages/core/session/README.md#write-experimental-plugin-records)，不能用它承载必需的模型内容 |

事件表是声明合并的类型表；扩展事件时检查当前读取者的未知事件处理，并按[持久化类型审查](../../../../docs/cookbook/reviewing-persistence-type-changes.md)判断兼容性、登记和版本要求，不能仅凭字段新增就决定是否升版本。

## Surface 与缓存

替换范围使用当前 surface 顺序中的包含端点，且必须覆盖完整被替换节点。首个 system 节点受特殊保护；清空提示词必须处理所有仍生效的 system 节点，不能只隐藏最后一个。不要直接修改日志来实现压缩或内容脱敏。

`deriveMessages()` 返回新数组，但其中消息为共享的深冻结对象。尾部增长可增量派生；内容替换或消息投影使缓存按 content generation 重建。修改缓存时同时验证值和身份，不能只验证 JSON 相等。

工具新增声明由对应历史 `request/header` 的引用确定，不能拿当前 registry 或最新 header 解释旧事件。工具失败字段与消息 `isError` 保持一致。

## 验证选择

[json](../../../../packages/core/session/tests/json.spec.ts)、[canonical-envelopes](../../../../packages/core/session/tests/canonical-envelopes.spec.ts)验证拒绝后无变更；[surface](../../../../packages/core/session/tests/surface.spec.ts)、[message-projections](../../../../packages/core/session/tests/message-projections.spec.ts)、[derived-cache](../../../../packages/core/session/tests/derived-cache.spec.ts)验证替换与身份；[developer-header](../../../../packages/core/session/tests/developer-header.spec.ts)验证历史工具声明引用。
