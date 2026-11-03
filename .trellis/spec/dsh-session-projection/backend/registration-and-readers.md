# 注册就绪、同步读取与卸载

适用于修改投影服务初始化、准备 Session、保留读取器和 HMR。类型与实现归 [ProjectionHandle 和注册表](../../../../packages/session/session-projection/src/index.ts)，兼容用法归[包文档](../../../../packages/session/session-projection/README.md#deprecated-plugin-compatibility)。

## 两种就绪不能合并

领域服务必需的投影声明 `sessionProjections` 依赖，通常在 `[Service.init]` 中等待 `register()` 成功，再暴露同步方法或安装使用该 handle 的回调。注册失败应使该次激活失败；不能改成可选注册加另一条恢复路径。

Session 的异步加载所有者另行完成历史准备，才发布给同步读取者。getter 不承担 hydration、文件 I/O 或 Promise 等待。注册表的单元及 Session 错误范围必须保留，不能为了抢先准备把消费者特有的异常移到所有事件处理里。

## Handle 和读取器

handle 私有保留；同一个运行时需要多个状态时，传由 `handle.readerFor(session)` 组成的具名回调对象。reader 是同步的 `() => S`，捕获确切 Session；创建它不读取、不缓存、不准备、不做 I/O，也不拥有 dispose。

registration 属于调用者 fiber，显式释放需等待 `handle.dispose()`。最后一个注册撤销后退出全局驱动、快照和通知，但保留的 handle 仍以原定义读取新事件；后来的同 key 新版本不会接管旧 reader。不要把注销等同于旧 reader 失效，也不要因保留 reader 而重新注册贡献。

新代码 await 注册并返回 void，不把 await 得到的 handle 当作 Cordis disposer 返回或 yield。注册返回值的旧 callable-thenable 兼容行为不能用来设计新生命周期；需要原生 Promise 的测试断言用 `Promise.resolve()` 接住旧返回值。

## 在途卸载

注册期间可能到达事件。只有确需避免漏事件时才提前装监听；同时保证 owner 已释放后不能继续安装 effect。改变已有同步读取方式前，检查插件、CLI、GUI 与两个 SDK 的全部消费者，不能用 Promise 替换同步结果。

`onChanged` 按单元通知，`onEventChanged` 在一个事件驱动完成后合并客户端变化。部分驱动或监听失败时仍需保留此前已经发生的变化和既有错误传播，不能向客户端宣称整个事件回滚。

## 验证选择

[registration-reader](../../../../packages/session/session-projection/tests/registration-reader.spec.ts)验证精确 Session、同步错误及卸载后的原定义；[compatibility](../../../../packages/session/session-projection/tests/compatibility.spec.ts)和 [Loader 组合](../../../../packages/session/session-projection/tests/loader-compatibility.e2e.ts)验证返回值与 effect 所有权。领域服务的生命周期修改还需覆盖延迟注册、拒绝、替换和等待中卸载，断言资源与日志均已结算。
