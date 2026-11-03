# 存储、API 与错误

Session 持久化和普通存储是不同的所有者。先读[存储子系统](../../../../docs/subsystems/storage.md)、[远程/API 防御规则](../../../../docs/defensive-patterns/remote-and-api.md)和 [dsh-error-handling](../../../../.agents/skills/dsh-error-handling/SKILL.md)，确定谁负责验证、提交、恢复和用户报告。

## 数据所有权

[Storage hub](../../../../packages/storage/storage/src/index.ts)注册 backend 和数据形式，本身不做 IO；领域数据形式拥有语义，后端拥有介质。不要把业务规则放进 backend 或 API 通用分发层，也不要把 Session 日志旁路到普通键值存储。

| 示例 | 阅读重点 |
| --- | --- |
| [JSON backend](../../../../packages/storage/storage-json/src/index.ts) | 显式 root、异步打开的所有权、原子发布及关闭 |
| [SQLite backend](../../../../packages/storage/storage-sqlite/src/index.ts) | 单元版本、并发打开保护、失败后阻止后续使用 |
| [SQLite schema](../../../../packages/storage/storage-sqlite/src/schema.ts) | 当前 schema 版本与数据库初始化归属 |
| [StorageError](../../../../packages/storage/storage/src/error.ts) | 稳定判别码与诊断文本分离 |

SQLite schema 版本单调增加；持久化数据和类型变更先应用[持久类型审核](../../../../docs/cookbook/reviewing-persistence-type-changes.md)，外部不兼容改动同时记录升级指南。不要把 rollback 失败当作恢复成功。

## API 与失败

Remote 方法使用 Typert 声明的服务与类型，通用网关负责传输和路由，领域服务负责业务。参考 [SessionController](../../../../packages/api/session-controller/src/index.ts)与[Agent 控制器](../../../../packages/api/session-controller/src/agent.ts)对领域错误的翻译；客户端通过[生成 Remote 聚合](../../../../packages/api/remotes/README.md)消费接口，不复制签名。

失败用结构化类型表达；用户报告提供可执行的恢复信息。提交成功后才通知派生状态，避免先发布再回滚。无法保证结果或状态可信时停止依赖工作并明确报告；重试由能够判断幂等和恢复条件的所有者决定。空 catch 命名错误与忽略原因，try 仅包含需要忽略的一条操作。

## 验证

[SQLite 测试](../../../../packages/storage/storage-sqlite/tests/sqlite-backend.spec.ts)展示真实介质和失败语义的验证位置。根据改动检查并发打开、版本不匹配、提交/回滚失败、关闭中调用和跨进程结果中受影响的路径；不得仅测错误文本或让未经提交的状态进入读取视图。
