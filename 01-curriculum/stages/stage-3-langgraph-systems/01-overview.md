# 01 Overview

## 这一章到底在解决什么问题

`Stage 2` 让我们学会了如何用 `LangChain` 快速做出一个高层 Agent 原型。但原型能工作，不代表系统能长期、稳定、可恢复地工作。

当你的项目开始出现下面这些情况时，高层封装就会逐渐不够用:

- 明显的多阶段流程
- 多分支决策
- 人工审批与中断等待
- 长任务执行
- 失败后需要恢复，而不是从头重来
- 前端需要看到系统正在做什么

这时候真正的问题已经不是“怎么让模型回答得更好”，而是:

> 怎样把任务控制逻辑显式化，怎样让系统在运行中保持可控、可恢复、可解释。

这就是 `LangGraph` 在课程里的位置。

## 本阶段的学习目标

完成这一阶段后，学习者应该具备以下能力:

- 解释为什么某些项目已经不适合继续停留在高层原型层
- 把一个复杂任务拆成图结构，而不是隐式流程
- 为图式工作流设计合理的 state
- 设计分支、interrupt、恢复与审批机制
- 理解 durable execution、persistence 和 streaming 的系统意义
- 说明为什么当前项目必须使用 LangGraph

## 为什么 Stage 3 放在 Stage 4 前面

因为 `Deep Agents` 适合复杂任务组织，但在进入更复杂的任务 harness 之前，学习者先要真正理解:

- 工作流为什么要显式建模
- 状态为什么要显式设计
- 审批为什么要成为图中的正式节点或暂停点
- 恢复为什么不是“重来一次”

如果这一步没建立，后面学习复杂任务系统时，学习者很容易只看到“能力变多了”，却看不到控制逻辑、状态管理和系统边界。

## LangGraph 在新版架构里的位置

根据官方新版文档，`LangGraph` 是一个用于构建 stateful、long-running agent systems 的底层编排框架，强调 durable execution、streaming、human-in-the-loop、memory 和 production-ready control。

这意味着:

- `LangChain` 更像高层入口
- `LangGraph` 更像底层 runtime / orchestration 层
- 你在这一章学的，不只是“更复杂的框架”，而是“运行时级别的系统设计”

参考:

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)

## 本阶段不追求什么

这一章虽然比前两章更系统，但仍然有意不追求以下内容:

- 不追求多 Agent 组织
- 不追求 Deep Agents 的复杂任务 harness
- 不追求全栈交付与部署
- 不追求完整产品化

这一章只追求一件事:

> 把一个复杂任务从“隐式流程”推进成“显式可控的图系统”。

## 推荐学习方式

这一章最适合用 `图式理解 -> state 设计 -> 分支与 interrupt -> 恢复与 streaming -> 项目跟做 -> 架构复盘` 的方式推进。

建议你按下面节奏走:

### Session 1: 理解为什么这里需要图

- 阅读 [02-concepts.md](./02-concepts.md)
- 先回答“为什么高层原型在这里开始不够用了”
- 先理解 LangGraph 和 LangChain 的层次区别

### Session 2: 学 state 与图式控制

- 阅读 [03-methods.md](./03-methods.md)
- 把一个 Stage 2 项目拆成图
- 练习 state 最小集设计

### Session 3: 学 interrupt、恢复与 persistence

- 阅读 [02-concepts.md](./02-concepts.md)
- 学会区分普通澄清与正式 interrupt
- 理解 persistence 与 durable execution 的关系

### Session 4: 做案例判断

- 阅读 [09-case-comparisons.md](./09-case-comparisons.md)
- 挑 3 个场景判断为什么它们已经需要 LangGraph
- 训练“运行时系统思维”

### Session 5: 跟做引导项目

- 阅读 [04-guided-project.md](./04-guided-project.md)
- 配合 [Stage 3 跟学项目](../../../03-projects/stage-3/guided-project-approval-workflow-agent.md)
- 先完成一个带审批的工作流设计

### Session 6: 独立完成课后项目

- 阅读 [05-challenges.md](./05-challenges.md)
- 开始 [Stage 3 课后项目](../../../03-projects/stage-3/homework-project-multi-stage-research-workflow.md)
- 让 Codex 按 state、interrupt、恢复路径和边界做评审

### Session 7: 阶段放行

- 用 [06-review-checklist.md](./06-review-checklist.md) 自测
- 回答“为什么这个项目必须使用 LangGraph”
- 回答“interrupt 在这里真正暂停了什么”

更细的节奏见 [08-session-roadmap.md](./08-session-roadmap.md)。

## 本阶段的核心产出

学完这一阶段后，建议至少留下这些材料:

- 一张 `LangGraph 工作流图`
- 一份 `state 字段说明`
- 一份 `interrupt 设计清单`
- 一份 `恢复路径说明`
- 一份 `为什么必须使用 LangGraph 的边界解释`
- 一份 `运行时失败路径清单`

## 进入 Stage 4 前必须能回答的 4 个问题

如果下面 4 个问题答不清，建议不要急着进入 `Deep Agents`:

1. 哪些问题是 state 设计问题，而不是 prompt 问题。
2. interrupt 在这个项目里真正暂停了什么。
3. durable execution 与 persistence 为什么重要。
4. 为什么这个系统必须使用 LangGraph，而不是继续停留在 LangChain 高层。

## 与官方文档的关系

这一章紧贴 LangGraph 官方新版主线，重点围绕:

- stateful systems
- durable execution
- interrupts
- persistence
- streaming
- human-in-the-loop
- memory 与运行时状态的关系

可作为背景阅读:

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Durable execution](https://docs.langchain.com/oss/python/langgraph/durable-execution)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)
- [Persistence](https://docs.langchain.com/oss/python/langgraph/persistence)
- [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)
- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)

## 一句话总结

`Stage 3` 的任务不是把 Agent 做得更复杂，而是学会如何把复杂任务变成一个状态清楚、运行可控、失败可恢复的图系统。
