# 执行策略、并发与工具结果

适用于修改工具 body、策略 waterfall、batch 调度和结果呈现。先读 [ToolDefinition 与执行结果](../../../../packages/core/tools/src/contracts.ts)、[共享 pipeline](../../../../packages/core/tools/src/pipeline.ts)和 [batch](../../../../packages/core/tools/src/batch.ts)。完整执行语义归[包文档](../../../../packages/core/tools/README.md#execution-and-cancellation)。

## 策略不能被绕过

共享 pipeline 的先后关系为 pre-execute waterfall、单调 guard、execute 包装、post-execute、最终内容变换及结果通知。waterfall 的允许决定不是最终授权；guard 只能否决，后续监听不能重新允许。策略必须在执行操作处生效，schema 过滤和界面隐藏不能代替它。

输入已记录且向用户展示，pre-execute 不支持悄悄重写参数。调用身份和快照参数保持不变；execute 包装即使替换 signal，实际 body 仍合并调用者取消。

## 并发与取消

只有 `isConcurrencySafe()` 明确返回 true 的调用可重叠，其余形成独占屏障。分类异常不能被当成安全；开始前还要考虑当前定义和准入。并发上限约束在途执行，结果和追加上下文按模型输入顺序提交，不能按完成先后重排。

body 观察或转发 `exec.signal`，并在自己启动的工作静止后才结算。取消前未调用 body 的结果是 `ABORTED_BEFORE_DISPATCH`；已启动调用排空后，取消只把成功改成 `ABORTED`，保留已有拒绝、工具失败及超时等更具体原因。

内部调度失败通过 `ToolBatchExecutionError.partial` 保留已提交结果和上下文；拥有 step 的调用者停止依赖工作并补缺失日志。不能靠 `Promise.race` 先返回取消，再放任有副作用的 body 继续运行。

## 规范值、模型内容与 UI

工具返回符合 `output.schema` 的无损 JSON 规范值，`output.render` 生成模型内容，`presentationMeta` 提供可持久化的呈现数据。仅替换或脱敏 content 不会移除程序调用者拿到的规范值；需要拒绝访问时必须阻止执行或替换该值。

`projectContent` 在 post-execute 前安装预备内容，策略仍可替换；`finalizeContent` 在最终物化前执行，必须同步、全定义且不抛错。不要把失败结果强行改为成功值，也不能同时用一个 accept 决定替换 value 和 content。

Host presenter 保持纯函数；Web 工具卡从原始参数、最终 content、失败状态和持久化 meta 派生，通过 slots 选择渲染器，不传 Host 产生的 React 内容或 presenter 结果。具体 UI 扩展归[客户端 slots 规范](../../dsh-client-ui-slots/frontend/declarations-and-factories.md)。

## 验证选择

[tools](../../../../packages/core/tools/tests/tools.spec.ts)验证策略、取消和结果；[execution-mode](../../../../packages/core/tools/tests/execution-mode.spec.ts)验证分类；调度变更同时覆盖 [Agent tool-order](../../../../packages/core/agent-loop/tests/tool-order.spec.ts)。参数与输出校验看 [schema](../../../../packages/core/tools/tests/schema.spec.ts)、[json-schema](../../../../packages/core/tools/tests/json-schema.spec.ts)；改变 Native/PTC 可见结果还需各自组合与模型快照。
