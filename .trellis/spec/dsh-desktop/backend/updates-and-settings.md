# 壳设置、更新状态与安装交接

适用于修改 Desktop 设置、渠道切换、自动检查、强制策略和安装。入口为 [settings-file](../../../../apps/desktop/src/settings-file.ts)、[update-settings](../../../../apps/desktop/src/update-settings.ts)、[update-coordinator](../../../../apps/desktop/src/update-coordinator.ts)及 [main 安装编排](../../../../apps/desktop/src/main.ts)。完整产品行为归 [Updates](../../../../apps/desktop/README.md#updates)。

## 设置的存储与生效

壳在 Host 启动前也需要的设置归 Electron `userData/desktop/settings.json`，不塞进 Cordis 或 Host settings。`DesktopSettingsFile` 只处理文档读取、校验和写入，不选择业务默认值、不应用运行时渠道，也不 watch 文件。

read 不创建文件；启动 initialize 明确创建缺失文档且不覆盖已有内容。缺失、读失败、JSON/结构错误及字段错误分别处理，字段独立校验。保存获取同一 writer lock，保留未知和无关字段；不能用内存旧副本覆盖磁盘新文档。

`allowTestAuthPopupWindow` 的缺失或错误可按拥有者规则降级为 false；显式无效的更新渠道必须暂停普通更新，不能悄悄改成默认源。外部文件变更与 UI 明确保存的生效时点不同，见[本地设置说明](../../../../apps/desktop/README.md#local-desktop-settings)。

写失败区分未写、结果未知、已写但锁清理失败。结果未知不能自动重试；已写不能谎称回滚。错误摘要只暴露路径与分类，不能泄漏设置文档内容。

## 渠道与目标身份

更新的 checked/downloaded/handed-off 目标由主进程拥有，不能仅靠 UI phase 判断安装资格。产品 renderer 只获得 `DesktopUpdatePresentation` 并打开原生确认，不提供下载地址、目标版本或安装授权。

渠道切换先保存，再使旧 generation 失效，取消并等待旧检查/下载，撤销旧目标资格，清理适配器后检查新源。相同版本号也不能跨渠道复用旧确认。保存失败保留原运行状态；目标清理失败暂停更新，等待明确恢复。

普通检查不自动下载，下载完成不自动安装，退出也不隐式安装。安装与下载分别持有版本和 revision；旧对话框、旧下载事件及旧请求不能改变新渠道状态。安装准备和安装器接管期间拒绝渠道变更。

## 任务保护与恢复

1. 在同一次确认里检查任务并获得中断决定；不能把先前一次普通下载同意当作安装同意。
2. 经 [Host task control](../../../../apps/desktop-host/src/update-tasks.ts)锁住新请求，排空已准入请求，再检查新增任务；状态未知或出现未获中断同意的新工作时拒绝安装。
3. 清理嵌入 Platform 文档和自有临时资源，要求 Host 干净关闭，再交给安装器。强杀后退出不满足更新的干净收尾要求。
4. 确认旧进程已退出但收尾或安装器启动失败时，先恢复当前版本 Host，再允许新确认；未确认旧进程退出时不能启动替代 Host。替代 Host 重新认证后刷新当前页面所需的 port、cookie 和 injections。

已知强制更新的 blocking 状态在配置错误和 Host 恢复期间继续保持，只能由有效的新策略结果解除。不能把网络失败或换源当作策略批准。策略归 [mandatory-update-policy](../../../../apps/desktop/src/mandatory-update-policy.ts)，安装资格仍由 coordinator 与主进程决定。

## 验证选择

[settings-file](../../../../apps/desktop/tests/settings-file.spec.ts)、[update-settings](../../../../apps/desktop/tests/update-settings.spec.ts)验证字段和写入结果；[update-coordinator](../../../../apps/desktop/tests/update-coordinator.spec.ts)验证 generation、并发及独立确认；[host-update-tasks](../../../../apps/desktop/tests/host-update-tasks.spec.ts)验证请求排空与任务复查；[mandatory-update-policy](../../../../apps/desktop/tests/mandatory-update-policy.spec.ts)验证强制状态。真实下载与安装的不同证据要求见[打包验证](packaging-and-verification.md)。
