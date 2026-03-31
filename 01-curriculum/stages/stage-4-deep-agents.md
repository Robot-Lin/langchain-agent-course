# Stage 4: Deep Agents

## Stage Goal

`Stage 4` 的任务是让学习者从图系统设计升级到复杂任务组织设计。学完这一阶段，学习者应该能利用 `Deep Agents` 思维，把一个开放、长程、多角色、多层上下文的任务组织成可执行、可管理、可治理的 Agent 结构。

## What You Will Learn

- Deep Agents 在新版架构中的角色与价值
- 什么任务适合或不适合 Deep Agents
- planning、context engineering、subagents、human-in-the-loop 与治理的关系
- 如何把复杂目标拆成阶段、角色和汇总结构
- 如何判断任务为什么更适合 Deep Agents 而不是普通 LangGraph 工作流

## Learning Outcomes

完成这一阶段后，你应该能:

- 识别复杂任务型 Agent 的适用边界
- 设计复杂目标拆解图
- 设计上下文分层
- 判断并设计必要的 subagents
- 设计治理点和审核点防止任务偏航
- 说明为什么当前任务更适合 Deep Agents

## Recommended Path

1. [Stage 4 教学包入口](./stage-4-deep-agents/README.md)
2. [Stage Overview](./stage-4-deep-agents/01-overview.md)
3. [Core Concepts](./stage-4-deep-agents/02-concepts.md)
4. [Case Comparisons](./stage-4-deep-agents/09-case-comparisons.md)
5. [Methods](./stage-4-deep-agents/03-methods.md)
6. [Session Roadmap](./stage-4-deep-agents/08-session-roadmap.md)
7. [Guided Project](./stage-4-deep-agents/04-guided-project.md)
8. [Challenges](./stage-4-deep-agents/05-challenges.md)
9. [Review Checklist](./stage-4-deep-agents/06-review-checklist.md)
10. [Codex Workshop](./stage-4-deep-agents/07-codex-workshop.md)

## Official Backbone

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)
- [When to use the Deep Agents SDK](https://docs.langchain.com/oss/python/concepts/products#when-to-use-the-deep-agents-sdk)

## Stage Projects

- [Stage 4 Projects](../../03-projects/stage-4/README.md)
- [Guided Project: Deep Research Agent](../../03-projects/stage-4/guided-project-deep-research-agent.md)
- [Homework Project: Content Strategy Agent](../../03-projects/stage-4/homework-project-content-strategy-agent.md)

## Stage Gate

如果你还不能稳定回答下面这些问题，建议继续停留在 `Stage 4`:

- 为什么这个复杂任务需要上下文分层
- 为什么这里的 subagents 是真必要，而不是炫技
- 为什么复杂任务的失控风险不只是“答错了”
- 为什么这个任务更适合 Deep Agents，而不是普通 LangGraph 工作流
- 你的汇总与治理机制如何防止任务越跑越散
