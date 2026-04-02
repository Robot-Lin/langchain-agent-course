# 08 Session Roadmap

这一章建议拆成 4 次学习会话，每次都遵循“读知识 -> 画旅程 -> 画分区 -> 让 Codex 评审”的节奏。

## Session 1: 先建立 Agent UX 心智模型

目标：

- 先彻底分清普通聊天 UI 和 Agent 产品 UI。
- 建立“前端不是皮肤，而是控制与理解层”的意识。

建议动作：

1. 阅读 [01-overview.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/01-overview.md) 和 [02-concepts.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/02-concepts.md)。
2. 重点读 [02-concepts.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/02-concepts.md) 里后半段的代码教材。
3. 随便选 2 个你熟悉的 Agent 想法，判断哪些信息不该只放在聊天流。
4. 让 Codex 帮你纠正对 Agent UX 的误解。

## Session 2: 学会前端分区与任务旅程

目标：

- 把一个 Agent 方案拆成前端层。
- 先学任务旅程，再学界面分区。

建议动作：

1. 阅读 [03-methods.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/03-methods.md)。
2. 重点读 `03-methods.md` 里的 API 对照附录。
3. 用一个真实需求画出最小前端结构。
4. 用 [09-case-comparisons.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/09-case-comparisons.md) 做对照。

## Session 3: 做跟学项目

目标：

- 把 streaming、审批、状态和结构化结果真正串起来。

建议动作：

1. 按 [04-guided-project.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/04-guided-project.md) 做一遍引导项目。
2. 用 [10-full-project-reading.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/10-full-project-reading.md) 扫一遍全项目结构。
3. 产出一张完整前端结构图、一份任务旅程说明和一份全项目组件地图。
4. 让 Codex 站在产品体验评审角度做反馈。

## Session 4: 做 challenge 与放行

目标：

- 把理解迁移到新问题。
- 用 review checklist 做阶段放行。

建议动作：

1. 完成 [05-challenges.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/05-challenges.md)。
2. 用 [06-review-checklist.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/06-review-checklist.md) 自测。
3. 按 [07-codex-workshop.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/07-codex-workshop.md) 让 Codex 做一次正式体验评审。
4. 重点检查自己能不能把 `useStream`、structured output、interrupt 和 streaming 事件对应到完整组件链路上。

## 本章完成标志

如果你已经能：

- 用自然语言说清一个 Agent 前端为什么不能只是聊天框。
- 能设计状态、审批和结果展示的层次。
- 能让用户看清系统在做什么、做到了哪里、哪里需要接管。

那就可以进入 Stage 7 的全栈交付层。
