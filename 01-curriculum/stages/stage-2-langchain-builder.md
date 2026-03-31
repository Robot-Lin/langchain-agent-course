# Stage 2: LangChain Builder

## Stage Goal

`Stage 2` 的任务是把学习者从系统判断推进到高层框架实践。学完这一阶段，学习者应该能利用 `LangChain` 把一个合理的 Agent 设计推进成可工作的高层原型，并知道什么时候继续留在高层封装是合理的。

## What You Will Learn

- LangChain 在新版架构中的角色与价值
- 高层 Agent 原型与复杂工作流系统的差别
- tools、structured output、middleware、short-term memory、human-in-the-loop 的高层用法
- 如何把 Stage 1 的设计变成可演示原型
- 如何判断项目何时逼近 LangGraph 边界

## Learning Outcomes

完成这一阶段后，你应该能:

- 设计一个 LangChain 高层 Agent 原型
- 为原型定义清楚的最小工具集和 structured output
- 说明哪些控制逻辑适合放进 middleware
- 判断项目当前为什么适合留在 LangChain
- 识别从高层原型过渡到 LangGraph 的触发信号

## Recommended Path

1. [Stage 2 教学包入口](./stage-2-langchain-builder/README.md)
2. [Stage Overview](./stage-2-langchain-builder/01-overview.md)
3. [Core Concepts](./stage-2-langchain-builder/02-concepts.md)
4. [Case Comparisons](./stage-2-langchain-builder/09-case-comparisons.md)
5. [Methods](./stage-2-langchain-builder/03-methods.md)
6. [Session Roadmap](./stage-2-langchain-builder/08-session-roadmap.md)
7. [Guided Project](./stage-2-langchain-builder/04-guided-project.md)
8. [Challenges](./stage-2-langchain-builder/05-challenges.md)
9. [Review Checklist](./stage-2-langchain-builder/06-review-checklist.md)
10. [Codex Workshop](./stage-2-langchain-builder/07-codex-workshop.md)

## Official Backbone

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [Agents](https://docs.langchain.com/oss/python/langchain/agents)
- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)
- [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)
- [Build a RAG agent with LangChain](https://docs.langchain.com/oss/python/langchain/rag)

## Stage Projects

- [Stage 2 Projects](../../03-projects/stage-2/README.md)
- [Guided Project: Research Assistant](../../03-projects/stage-2/guided-project-research-assistant.md)
- [Homework Project: Structured Interview Agent](../../03-projects/stage-2/homework-project-structured-interview-agent.md)

## Stage Gate

如果你还不能稳定回答下面这些问题，建议继续停留在 `Stage 2`:

- LangChain 的高层抽象到底帮你省掉了什么
- 为什么 structured output 比很多人想象得更重要
- 哪些控制逻辑不该全部塞进 prompt
- 当前项目为什么适合或不适合继续留在 LangChain
- 哪些迹象说明该开始进入 LangGraph
