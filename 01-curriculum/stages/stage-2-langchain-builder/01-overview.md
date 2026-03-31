# 01 Overview

## 这一章到底在解决什么问题

`Stage 1` 解决的是判断问题:

- 这个需求是否真的需要 Agent
- 这个系统边界应该如何定义
- 哪些能力必须有，哪些能力暂时不该加

`Stage 2` 解决的是另一个问题:

> 如果现在已经确认要做一个 Agent，怎样用高层框架最快、最稳地搭出一个能工作的原型。

这就是 `LangChain` 在课程里的位置。

它不是这套体系里最底层的 runtime，也不是“电池全包”的复杂任务系统，而是一个非常适合学习者第一次真正动手搭 Agent 原型的高层入口。

## 本阶段的学习目标

完成这一阶段后，学习者应该具备以下能力:

- 解释 `LangChain` 为什么适合作为高层 Agent 开发入口
- 说明高层 Agent 原型和复杂工作流系统的差别
- 能围绕任务、工具、structured output、middleware 设计一个最小原型
- 能说清为什么当前版本适合停留在 `LangChain`，而不是过早转向 `LangGraph`
- 能看出一个高层原型何时开始逼近 `LangGraph` 的边界

## 为什么 Stage 2 放在 Stage 3 前面

因为学习者第一次进入框架实践时，最容易犯的错误有两个:

- 一上来就掉进复杂状态机和编排细节
- 还没把主路径跑通，就开始追求“完整系统架构”

`LangChain` 适合放在这里，是因为它让你先把注意力放在:

- 任务定义
- 工具接入
- 输出结构
- 基础控制逻辑
- 高层安全与审核边界

而不是一开始就掉进复杂图编排、恢复逻辑和分支状态设计。

## LangChain 在新版架构里的位置

根据 LangChain 官方新版文档，`LangChain` 是高层 Agent 开发框架，提供了预置的 agent architecture，帮助开发者快速构建自定义 agents。官方同时也明确说明，LangChain 的 agents 是构建在 `LangGraph` 之上的。

这意味着:

- 你可以先从高层 abstractions 开始
- 但这并不代表它“没有 runtime”
- 而是 runtime 的复杂度被收拢在更合适的位置

你在 `Stage 2` 最该学会的，不是“把 LangChain 当成黑盒”，而是:

> 什么时候它帮了你，什么时候你已经开始顶到它的边界。

参考:

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [Agents](https://docs.langchain.com/oss/python/langchain/agents)

## 本阶段不追求什么

这一章有意不追求以下内容:

- 不追求复杂分支和长流程编排
- 不追求 durable execution
- 不追求复杂 interrupt / resume 机制
- 不追求多 Agent 组织
- 不追求完整生产系统治理

这些内容都重要，但它们更适合在后续阶段再深入。

`Stage 2` 只追求一件事:

> 把一个结构清楚的 Agent 设计，推进成一个高层可运行、可演示、可评审的原型。

## 推荐学习方式

这一章最适合用 `概念理解 -> 组件判断 -> 原型设计 -> 跟做项目 -> 独立项目 -> 边界复盘` 的方式推进。

建议你按下面节奏走:

### Session 1: 理解 LangChain 为什么适合作为高层入口

- 阅读 [02-concepts.md](./02-concepts.md)
- 先回答“LangChain 到底帮我省掉了什么”
- 先理解它和 LangGraph 的上下层关系

### Session 2: 学会设计高层原型

- 阅读 [03-methods.md](./03-methods.md)
- 练习最小工具、structured output、middleware 三件套
- 把一个 Stage 1 方案推进成高层原型草案

### Session 3: 做案例判断

- 阅读 [09-case-comparisons.md](./09-case-comparisons.md)
- 挑 3 个场景判断为什么现在还适合 LangChain
- 训练“什么时候别急着进入 LangGraph”

### Session 4: 跟做引导项目

- 阅读 [04-guided-project.md](./04-guided-project.md)
- 配合 [Stage 2 跟学项目](../../../03-projects/stage-2/guided-project-research-assistant.md)
- 先完成一个高层研究助理原型设计

### Session 5: 独立完成课后项目

- 阅读 [05-challenges.md](./05-challenges.md)
- 开始 [Stage 2 课后项目](../../../03-projects/stage-2/homework-project-structured-interview-agent.md)
- 让 Codex 按 structured output、工具边界、控制逻辑来评审

### Session 6: 阶段放行

- 用 [06-review-checklist.md](./06-review-checklist.md) 做自测
- 回答“为什么现在这个项目适合留在 LangChain”
- 回答“哪些迹象说明我该开始学 LangGraph 了”

更细的节奏见 [08-session-roadmap.md](./08-session-roadmap.md)。

## 本阶段的核心产出

学完这一阶段后，建议至少留下这些材料:

- 一份 `LangChain 高层原型说明`
- 一份 `最小工具清单`
- 一份 `structured output 字段设计`
- 一份 `middleware / 控制逻辑说明`
- 一份 `原型失败点清单`
- 一份 `为什么当前仍适合 LangChain 的边界解释`

## 进入 Stage 3 前必须能回答的 4 个问题

如果下面 4 个问题答不清，建议不要急着进入 `LangGraph`:

1. `LangChain` 的高层抽象到底帮你省掉了什么。
2. 为什么 `structured output` 对 Agent 原型特别重要。
3. 为什么 `middleware` 能让系统控制逻辑更清楚。
4. 什么迹象说明继续停留在高层封装已经不够用了。

## 与官方文档的关系

这一章紧贴 LangChain 官方新版主线，重点围绕:

- 高层 agents
- tools
- structured output
- middleware
- short-term memory
- human-in-the-loop
- 高层 RAG agent 原型

可作为背景阅读:

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [Agents](https://docs.langchain.com/oss/python/langchain/agents)
- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)
- [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)
- [Build a RAG agent with LangChain](https://docs.langchain.com/oss/python/langchain/rag)

## 一句话总结

`Stage 2` 的任务不是把 Agent 做复杂，而是学会如何借助 `LangChain` 把一个合理的设计推进成高层可工作的原型。
