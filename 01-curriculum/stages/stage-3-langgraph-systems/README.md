# Stage 3 教学包

这是课程中从“高层原型”进入“状态化系统设计”的关键单元。它承接 Stage 2，把学习者带入 LangGraph 的图式思维。

## 这一阶段学完之后应该做到什么

- 能解释为什么复杂 Agent 需要图，而不只是高层封装
- 能设计 state、节点、边、分支和中断
- 能理解 durable execution、interrupts、streaming 的实际业务意义
- 能设计一个带人工审批和恢复策略的 LangGraph 工作流

## 建议学习顺序

1. [01-overview.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/01-overview.md)
2. [02-concepts.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/02-concepts.md)
3. [03-methods.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/03-methods.md)
4. [04-guided-project.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/04-guided-project.md)
5. [05-challenges.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/05-challenges.md)
6. [06-review-checklist.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/06-review-checklist.md)
7. [07-codex-workshop.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/07-codex-workshop.md)
8. [Stage 3 配套项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-3/README.md)

## 本阶段的核心问题

- 为什么高层原型在这里开始不够用
- state 到底应该保存什么
- interrupt 和审批为什么是系统设计问题
- durable execution 真正解决了什么
- streaming 为什么不仅是“UI 更炫”，而是系统反馈能力

## 对整个课程的作用

Stage 3 是课程中最重要的架构升级点之一。

它训练的是:

- 图式思维
- 状态建模
- 工作流编排
- 审批与恢复设计
- 面向真实任务的可靠性思维
