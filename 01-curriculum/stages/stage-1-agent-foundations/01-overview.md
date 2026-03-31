# 01 Overview

## 这一章到底在解决什么问题

很多人一接触 Agent，就会马上问:

- 用哪个模型
- 用哪个框架
- 要不要上多 Agent
- 怎么接工具

这些问题都重要，但都不应该是第一问。

`Stage 1` 要先解决的是更根本的问题:

> 一个需求到底应不应该做成 Agent，以及如果要做，最小、最清楚、最安全的版本应该长什么样。

这一步如果不做，后面很容易出现三种常见问题:

- 把一个根本不需要 Agent 的需求，硬做成 Agent
- 把一个本来很简单的场景，做得过度复杂
- 把一个高风险系统，做成“看起来能跑但不可信”的原型

## 本阶段的学习目标

完成这一阶段后，学习者应该具备以下能力:

- 能解释 `Agent` 的本质是“围绕目标运行的系统”，不只是模型输出
- 能判断一个需求是否需要 `工具`、`状态`、`记忆` 和 `人工审批`
- 能把模糊需求拆成输入、动作、输出、失败路径和治理边界
- 能用自然语言完整说明一个最小可行 Agent 的系统结构
- 能在不写代码的情况下，先完成设计、审查和复盘

## 为什么 Stage 1 放在最前面

因为后面所有框架学习，本质上都在回答同一件事:

- `LangChain` 帮你更快地搭高层 Agent
- `LangGraph` 帮你更稳地编排状态化系统
- `Deep Agents` 帮你处理复杂任务、规划和上下文工程

但如果学习者一开始就不清楚:

- 这个目标到底是什么
- 系统边界在哪里
- 哪些动作允许自动执行
- 哪些信息必须跨轮保留
- 哪些失败是不能接受的

那框架越强，系统越容易“高配乱跑”。

所以 `Stage 1` 的意义不是“延迟实战”，而是先建立一套可以支撑实战的判断力。

## 本阶段不追求什么

这一章有意不追求以下内容:

- 不追求 API 细节
- 不追求写出复杂工作流
- 不追求多工具联动
- 不追求多 Agent 编排
- 不追求“演示效果惊艳”

这一章只追求一件事:

> 把一个模糊的 Agent 想法，压缩成一个合理、可解释、可迭代的最小系统。

## 推荐学习方式

这章最适合用 `阅读 -> 判断 -> 口头解释 -> 画结构 -> 小项目 -> 复盘` 的方式学，而不是一口气看完文档。

建议你按下面节奏推进:

### Session 1: 建立心智模型

- 阅读 [02-concepts.md](./02-concepts.md)
- 先回答 “Agent 和聊天机器人差在哪”
- 用自己的话复述 “为什么不是所有需求都要做成 Agent”

### Session 2: 学会判断边界

- 阅读 [09-case-comparisons.md](./09-case-comparisons.md)
- 挑 3 个案例，分别判断是否需要工具、状态、记忆、审批
- 训练 “少即是多” 的设计意识

### Session 3: 学会拆需求

- 阅读 [03-methods.md](./03-methods.md)
- 练习最小 Agent 设计画布
- 把一个自己的想法压缩成单一目标系统

### Session 4: 跟做引导项目

- 阅读 [04-guided-project.md](./04-guided-project.md)
- 配合 [Stage 1 跟学项目](../../../03-projects/stage-1/guided-project-faq-agent.md)
- 让 Codex 只做导师，不直接替你完成

### Session 5: 独立完成课后项目

- 阅读 [05-challenges.md](./05-challenges.md)
- 开始 [Stage 1 课后项目](../../../03-projects/stage-1/homework-project-learning-coach.md)
- 让 Codex 按验收标准评审你的方案

### Session 6: 阶段复盘

- 用 [06-review-checklist.md](./06-review-checklist.md) 自测
- 回答 “我最初把什么想复杂了”
- 回答 “我现在如何区分状态、记忆和知识库”

更细的教学节奏见 [08-session-roadmap.md](./08-session-roadmap.md)。

## 本阶段的核心产出

学完这一阶段后，建议至少留下这些材料:

- 一份 `最小 Agent 设计画布`
- 一份 `需求拆解表`
- 一份 `失败路径清单`
- 一份 `人工介入与审批点说明`
- 一段 `150-300 字的自然语言架构说明`

这些产出不是形式主义，它们是后面进入 `LangChain`、`LangGraph` 和 `Deep Agents` 的起点。

## 进入 Stage 2 前必须能回答的 4 个问题

如果下面 4 个问题回答不清，最好不要急着进入 `LangChain`:

1. 为什么这个需求需要 Agent，而不是普通应用逻辑或问答系统。
2. 这个 Agent 最少需要哪些外部能力，哪些能力其实不该现在就加。
3. 哪些信息属于状态，哪些属于记忆，哪些只是外部知识。
4. 这个系统最容易失败在哪，失败后谁来接管。

## 与官方文档的关系

这一章虽然还不进入具体框架实现，但它的思路与 LangChain 官方文档是一致的:

- Agent 价值不只是生成回答，而是围绕目标调用能力、执行流程和产生可用结果
- Memory 需要区分不同作用域，不能把所有历史粗暴塞进上下文
- Human-in-the-loop 不是附加功能，而是系统边界的一部分

可作为背景阅读:

- [LangChain Overview](https://docs.langchain.com/oss/python/langchain/overview)
- [Memory Overview](https://docs.langchain.com/oss/python/concepts/memory)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)

## 一句话总结

`Stage 1` 的任务不是教你“做出一个看起来像 Agent 的东西”，而是让你具备判断一个 Agent 设计是否合理的能力。
