# Stage 1: Agent Foundations

## Stage Goal

`Stage 1` 的任务是建立 Agent 学习的底层判断力，而不是急着进入框架实现。学完这一阶段，学习者应该能先判断一个需求是否真的需要 Agent，再决定后续是否进入 `LangChain`、`LangGraph` 或 `Deep Agents`。

## What You Will Learn

- Agent 与普通聊天机器人的本质差别
- 什么情况下需要工具，什么情况下不需要
- 什么情况下需要状态、记忆与知识库
- 什么情况下必须设置 human-in-the-loop
- 为什么很多“看起来很聪明”的系统其实不适合上线
- 如何在不写代码的前提下完成最小 Agent 设计

## Learning Outcomes

完成这一阶段后，你应该能:

- 判断一个场景是否值得设计成 Agent
- 用自然语言讲清楚一个最小可行 Agent 的系统结构
- 识别失败路径、风险点和人工接管点
- 在进入框架实现前先完成系统边界设计

## Recommended Path

1. [Stage 1 教学包入口](./stage-1-agent-foundations/README.md)
2. [Stage Overview](./stage-1-agent-foundations/01-overview.md)
3. [Core Concepts](./stage-1-agent-foundations/02-concepts.md)
4. [Case Comparisons](./stage-1-agent-foundations/09-case-comparisons.md)
5. [Methods](./stage-1-agent-foundations/03-methods.md)
6. [Session Roadmap](./stage-1-agent-foundations/08-session-roadmap.md)
7. [Guided Project](./stage-1-agent-foundations/04-guided-project.md)
8. [Challenges](./stage-1-agent-foundations/05-challenges.md)
9. [Review Checklist](./stage-1-agent-foundations/06-review-checklist.md)
10. [Codex Workshop](./stage-1-agent-foundations/07-codex-workshop.md)

## Stage 1 Deliverables

- 一份最小 Agent 设计画布
- 一份需求拆解表
- 一份失败路径清单
- 一份审批与人工介入说明
- 一段自然语言架构说明

## Stage Projects

- [Stage 1 Projects](../../03-projects/stage-1/README.md)
- [Guided Project: FAQ Agent](../../03-projects/stage-1/guided-project-faq-agent.md)
- [Homework Project: Learning Coach Agent](../../03-projects/stage-1/homework-project-learning-coach.md)

## Stage Gate

如果你还不能稳定回答下面这些问题，建议继续停留在 `Stage 1`:

- 为什么这个需求需要 Agent，而不是普通应用逻辑
- 哪些地方必须接工具，哪些地方不该加工具
- 哪些信息属于状态，哪些属于记忆，哪些只是知识库
- 哪些动作必须停下来交给人确认
- 这个系统最可能失败在哪
