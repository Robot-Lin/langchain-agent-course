# Stage 3: LangGraph Systems

## Stage Goal

`Stage 3` 的任务是让学习者从高层原型设计升级到运行时系统设计。学完这一阶段，学习者应该能利用 `LangGraph` 把一个复杂任务设计成状态清楚、可中断、可恢复、可审核的图系统。

## What You Will Learn

- LangGraph 在新版架构中的角色与价值
- 为什么复杂任务需要显式图编排
- state、branching、interrupt、persistence、durable execution、streaming 的关系
- 如何把 Stage 2 原型升级成图系统
- 如何判断项目为什么必须使用 LangGraph

## Learning Outcomes

完成这一阶段后，你应该能:

- 设计一个 LangGraph 工作流图
- 为图设计合理 state
- 说明 interrupt 为什么停在这里
- 设计基础恢复路径
- 说明 durable execution 与 persistence 的业务意义
- 判断为什么当前项目已经不适合继续停留在 LangChain 高层

## Recommended Path

1. [Stage 3 教学包入口](./stage-3-langgraph-systems/README.md)
2. [Stage Overview](./stage-3-langgraph-systems/01-overview.md)
3. [Core Concepts](./stage-3-langgraph-systems/02-concepts.md)
4. [Case Comparisons](./stage-3-langgraph-systems/09-case-comparisons.md)
5. [Methods](./stage-3-langgraph-systems/03-methods.md)
6. [Session Roadmap](./stage-3-langgraph-systems/08-session-roadmap.md)
7. [Guided Project](./stage-3-langgraph-systems/04-guided-project.md)
8. [Challenges](./stage-3-langgraph-systems/05-challenges.md)
9. [Review Checklist](./stage-3-langgraph-systems/06-review-checklist.md)
10. [Codex Workshop](./stage-3-langgraph-systems/07-codex-workshop.md)

## Official Backbone

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Durable execution](https://docs.langchain.com/oss/python/langgraph/durable-execution)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)
- [Persistence](https://docs.langchain.com/oss/python/langgraph/persistence)
- [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)
- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)

## Stage Projects

- [Stage 3 Projects](../../03-projects/stage-3/README.md)
- [Guided Project: Approval Workflow Agent](../../03-projects/stage-3/guided-project-approval-workflow-agent.md)
- [Homework Project: Multi-stage Research Workflow](../../03-projects/stage-3/homework-project-multi-stage-research-workflow.md)

## Stage Gate

如果你还不能稳定回答下面这些问题，建议继续停留在 `Stage 3`:

- 哪些问题是 state 设计问题，而不是 prompt 问题
- interrupt 在你的项目里真正暂停了什么
- 为什么 durable execution 与 persistence 很重要
- 你的恢复路径是不是只是“重来一次”
- 为什么当前项目必须使用 LangGraph
