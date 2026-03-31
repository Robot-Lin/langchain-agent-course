# 01 Overview

## 这一章到底在解决什么问题

`Stage 3` 教会了我们如何把复杂任务设计成可控、可恢复的图系统。但有些任务的难点，已经不只是“流程复杂”，而是任务目标本身就非常复杂。

例如:

- 目标开放且模糊
- 信息量巨大
- 需要多个子任务角色
- 需要持续规划和修正
- 需要把很多中间结果组织起来，而不是只走一个固定流程

这时候问题往往不再只是“流程怎么编排”，而是:

> 怎样组织复杂任务本身，怎样给不同子任务分配上下文，怎样在任务持续推进中保持方向不散、结果可收束。

这就是 `Deep Agents` 在课程里的位置。

## 本阶段的学习目标

完成这一阶段后，学习者应该具备以下能力:

- 识别什么任务适合使用 Deep Agents
- 把复杂目标拆成阶段目标、角色目标和汇总目标
- 设计上下文分层，而不是把所有信息混成一个大 prompt
- 判断哪些子任务真的需要 subagents
- 设计复杂任务中的审核点、方向修正点和治理点
- 说明为什么这里更适合 Deep Agents，而不是普通 LangGraph 工作流

## 为什么 Stage 4 放在 Stage 5 前面

因为工程化系统可以很复杂，但如果学习者还不会组织复杂任务本身，那么后面的 MCP、RAG、数据库、评测和部署会很容易变成“往混乱任务上继续叠功能”。

`Stage 4` 的作用，就是先把复杂任务的组织方式讲清楚:

- 怎么拆目标
- 怎么分角色
- 怎么分上下文
- 怎么回收结果
- 怎么防止任务偏航

只有这一步建立了，后面进入工程化整合时，系统才不会只是“技术更多”，而是真正更完整。

## Deep Agents 在新版架构里的位置

根据官方新版文档，`Deep Agents` 是面向复杂任务的高层入口之一，强调复杂任务处理、planning、context engineering 和更强的任务完成能力。

官方产品概念页也明确给出 “When to use the Deep Agents SDK”，说明它适合的是复杂任务组织，而不是所有 Agent 场景。

对学习者来说，最重要的理解是:

> Deep Agents 不是“比 LangGraph 更高级”这么简单，而是当复杂任务的难点开始落在规划、上下文组织和角色协作上时，更合适的任务组织层。

参考:

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [When to use the Deep Agents SDK](https://docs.langchain.com/oss/python/concepts/products#when-to-use-the-deep-agents-sdk)

## 本阶段不追求什么

这一章虽然更复杂，但仍然有意不追求以下内容:

- 不追求多到失控的子代理设计
- 不追求“越像自动公司越好”的幻想
- 不追求全量工程化集成
- 不追求前端产品化

这一章只追求一件事:

> 把一个复杂目标整理成一个可执行、可管理、可治理的 Agent 结构。

## 推荐学习方式

这一章最适合用 `任务拆解 -> 上下文分层 -> subagent 判断 -> 汇总与治理 -> 项目跟做 -> 边界复盘` 的方式推进。

建议你按下面节奏走:

### Session 1: 理解 Deep Agents 解决什么问题

- 阅读 [02-concepts.md](./02-concepts.md)
- 先回答“什么任务已经超出普通工作流的舒适区”
- 先理解 Deep Agents 和 LangGraph 的关系

### Session 2: 学复杂目标拆解与 context engineering

- 阅读 [03-methods.md](./03-methods.md)
- 把一个复杂目标拆成阶段、角色和汇总目标
- 练习 context 分层设计

### Session 3: 学 subagents 与治理

- 阅读 [02-concepts.md](./02-concepts.md)
- 判断哪些子任务真的需要 subagents
- 设计审核点、方向修正点和回收机制

### Session 4: 做案例判断

- 阅读 [09-case-comparisons.md](./09-case-comparisons.md)
- 挑 3 个场景判断为什么它们更适合或不适合 Deep Agents
- 训练复杂任务边界意识

### Session 5: 跟做引导项目

- 阅读 [04-guided-project.md](./04-guided-project.md)
- 配合 [Stage 4 跟学项目](../../../03-projects/stage-4/guided-project-deep-research-agent.md)
- 先完成一个复杂研究 Agent 设计

### Session 6: 独立完成课后项目

- 阅读 [05-challenges.md](./05-challenges.md)
- 开始 [Stage 4 课后项目](../../../03-projects/stage-4/homework-project-content-strategy-agent.md)
- 让 Codex 按目标拆解、context、subagents 与治理来评审

### Session 7: 阶段放行

- 用 [06-review-checklist.md](./06-review-checklist.md) 自测
- 回答“为什么这里需要上下文分层”
- 回答“为什么这些子代理是真必要，而不是炫技”

更细的节奏见 [08-session-roadmap.md](./08-session-roadmap.md)。

## 本阶段的核心产出

学完这一阶段后，建议至少留下这些材料:

- 一份 `复杂目标拆解图`
- 一份 `context 分层说明`
- 一份 `subagent 分工说明`
- 一份 `汇总与回收机制说明`
- 一份 `治理点与审核点清单`
- 一份 `为什么这里更适合 Deep Agents 的边界说明`

## 进入 Stage 5 前必须能回答的 4 个问题

如果下面 4 个问题答不清，建议不要急着进入工程化整合阶段:

1. 为什么这个复杂任务需要上下文分层。
2. 为什么这里的 subagents 是真必要，而不是炫技。
3. 为什么复杂任务的失控风险不只是“答错了”。
4. 为什么这个任务更适合 Deep Agents，而不是普通 LangGraph 工作流。

## 与官方文档的关系

这一章紧贴 Deep Agents 官方新版主线，重点围绕:

- overview
- planning
- context engineering
- customization
- human-in-the-loop
- 适用边界判断

可作为背景阅读:

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)
- [When to use the Deep Agents SDK](https://docs.langchain.com/oss/python/concepts/products#when-to-use-the-deep-agents-sdk)

## 一句话总结

`Stage 4` 的任务不是把 Agent 做得更花哨，而是学会如何组织一个复杂目标，使它在多阶段、多角色、多层上下文中仍然可执行、可管理、可治理。
