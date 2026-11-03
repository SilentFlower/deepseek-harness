# 界面与本地化

产品可见改动使用 [dsh-client-ui-ux](../../../../.agents/skills/dsh-client-ui-ux/SKILL.md)；响应式、触控、截断、键盘和宽度切换使用 [dsh-responsive-ui](../../../../.agents/skills/dsh-responsive-ui/SKILL.md)。组件规则由[客户端指令](../../../../packages/client/AGENTS.md)维护。

## 文案与视觉

文案属于类型化字典，通过 `t` 或已经本地化的 primitive props 进入组件。文本、提示、placeholder、ARIA 名称和格式模板一起检查。英文使用 sentence case；插件标题和描述同样适用。不要把实现细节带入产品流程。

| 示例 | 阅读重点 |
| --- | --- |
| [Goal 字典](../../../../packages/client/ui-goal/src/client/locales.ts) | 键联合与各语言完整性，示例只用于字典类型模式 |
| [GoalBar](../../../../packages/client/ui-goal/src/client/GoalBar.tsx) | `t`、本地化控件标签、局部编辑和错误反馈 |
| [GoalBar CSS](../../../../packages/client/ui-goal/src/client/GoalBar.module.css) | 现有视觉 token、容器约束和截断布局 |

先找已有 primitives、图标和视觉 token，再新增组件或样式。反馈位置按操作上下文选择；错误提供可执行信息，保留用户输入。菜单、overlay 和 tooltip 同时考虑焦点、关闭、滚动、窄窗口、触控与键盘，不依赖 hover 才能完成操作。

## 验证与演示

运行受影响客户端测试、字典和 `verify-client-ui-i18n` 检查；布局或交互变化补充实际浏览器证据。产品可见行为需要对应记录快照，归属见[测试策略](../../../../docs/testing.md)。涉及 GUI 的 PR 按 [record-browser-gif](../../../../.agents/skills/record-browser-gif/SKILL.md)录制真实服务器和模型流程；目录选择器采用根指令要求的 [browse picker overlay](../../../../apps/web/tests/pin-browse-picker.overlay.yml)。

官方插件图标另用[插件 artwork 技能](../../../../.agents/skills/dsh-official-plugin-artwork/SKILL.md)并遵守设计审批规则；工具栏动作图标按现有 primitives 体系选择。
