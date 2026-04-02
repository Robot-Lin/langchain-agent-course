# 08 Session Roadmap

这一章建议拆成 4 次学习会话，每次都遵循“读知识 -> 画链路 -> 补交付 -> 让 Codex 评审”的节奏。

## Session 1: 先建立全链路心智模型

目标：

- 先看清全栈 Agent 的完整交付链路。
- 建立“交付不是模块堆叠，而是链路闭环”的意识。

建议动作：

1. 阅读 [01-overview.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/01-overview.md) 和 [02-concepts.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/02-concepts.md)。
2. 重点读 [02-concepts.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/02-concepts.md) 里后半段的代码教材。
3. 随便选 2 个你熟悉的 Agent 想法，判断它们离“可交付产品”还差什么。
4. 让 Codex 帮你纠正对交付层的误解。

## Session 2: 学会全栈组装与选型

目标：

- 把一个 Agent 方案拆成完整交付层。
- 学会 Agent Server、streaming 和 deployment 在产品中的角色。

建议动作：

1. 阅读 [03-methods.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/03-methods.md)。
2. 重点读 `03-methods.md` 里的 API 对照附录。
3. 用一个真实需求画出最小交付链路。
4. 用 [09-case-comparisons.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/09-case-comparisons.md) 做对照。

## Session 3: 做跟学项目

目标：

- 把前端、后端、runtime、streaming、评测和部署真正串起来。

建议动作：

1. 按 [04-guided-project.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/04-guided-project.md) 做一遍引导项目。
2. 用 [10-full-project-reading.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/10-full-project-reading.md) 扫一遍全项目结构。
3. 产出一张完整系统图、一份交付说明和一份全项目组件地图。
4. 让 Codex 站在交付评审角度做反馈。

## Session 4: 做 challenge 与放行

目标：

- 把理解迁移到新问题。
- 用 review checklist 做阶段放行。

建议动作：

1. 完成 [05-challenges.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/05-challenges.md)。
2. 用 [06-review-checklist.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/06-review-checklist.md) 自测。
3. 按 [07-codex-workshop.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/07-codex-workshop.md) 让 Codex 做一次正式交付评审。
4. 重点检查自己能不能把 Agent Server、threads、runs、streaming 和 traces 对应到完整调用链上。

## 本章完成标志

如果你已经能：

- 用自然语言说清一个 Agent 产品的完整交付链路。
- 能设计 deployment、observability 和 evaluation 的基础方案。
- 能给出有取舍逻辑的选型说明。

那就可以进入 Stage 8 的毕业项目层。
