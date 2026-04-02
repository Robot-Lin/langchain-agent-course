# 08 Session Roadmap

这个文件把 `Stage 3` 拆成一组真正可以执行的学习 session。你可以自己按节奏推进，也可以让 Codex 按这个顺序一节一节带你学。

## 建议总时长

- 轻量模式: 5 到 6 天
- 标准模式: 1 到 2 周
- 深挖模式: 2 周以上

## Session 1: 为什么这里需要图

### 学习目标

- 理解 LangGraph 在新版体系里的角色
- 明白为什么高层原型在这里开始不够用了
- 建立“显式控制流”的意识

### 先读什么

- [01-overview.md](./01-overview.md)
- [02-concepts.md](./02-concepts.md)
- [03-methods.md](./03-methods.md) 末尾附录

### 要做什么

- 用自己的话解释为什么某些任务必须用图
- 写出 3 个“高层原型不够用”的迹象
- 选一个 Stage 2 项目，说明它会在什么地方逼近 LangGraph

### 交付物

- 一段 120 到 180 字的理解复述
- 一张 LangChain 与 LangGraph 的边界对比表

## Session 2: state 设计

### 学习目标

- 理解 state 为什么是图系统核心
- 学会 state 最小集设计法
- 避免把所有上下文都塞进 state

### 先读什么

- [02-concepts.md](./02-concepts.md)
- [03-methods.md](./03-methods.md)
- [02-concepts.md](./02-concepts.md) 后半部分代码教材

### 要做什么

- 选一个工作流场景
- 写出 state 字段草案
- 标出每个字段为什么存在

### 交付物

- 一份 state 字段说明
- 一份“不放进 state 的信息”清单

## Session 3: interrupt、审批与恢复

### 学习目标

- 理解 interrupt 是正式暂停点，而不是普通追问
- 学会放置审批门
- 学会设计基本恢复路径

### 先读什么

- [02-concepts.md](./02-concepts.md)
- [03-methods.md](./03-methods.md)
- [02-concepts.md](./02-concepts.md) 后半部分代码教材

### 要做什么

- 选一个场景，设置至少 2 个 interrupt 点
- 为至少 2 类失败设计恢复路径
- 说明为什么这些点必须停下来

### 交付物

- interrupt 设计清单
- 恢复路径清单

## Session 4: persistence、durable execution 与 streaming

### 学习目标

- 理解 persistence 为什么是运行时能力基础
- 理解 durable execution 在真实任务中的价值
- 理解 streaming 是运行反馈能力的一部分

### 先读什么

- [02-concepts.md](./02-concepts.md)
- [09-case-comparisons.md](./09-case-comparisons.md)
- [02-concepts.md](./02-concepts.md) 后半部分代码教材

### 要做什么

- 用自己的话解释 persistence 和 durable execution 的关系
- 写出前端为什么需要看到图运行状态
- 说明一个没有 streaming 可见性的长任务会带来什么问题

### 交付物

- 一段运行时能力说明
- 一份“前端可见状态”清单

## Session 5: 跟做审批工作流 Agent

### 学习目标

- 把概念和方法落实到一个正式 LangGraph 项目上
- 练习 state、interrupt、恢复和审批三件套

### 先读什么

- [04-guided-project.md](./04-guided-project.md)
- [10-full-project-reading.md](./10-full-project-reading.md)
- [Stage 3 跟学项目](../../../03-projects/stage-3/guided-project-approval-workflow-agent.md)

### 要做什么

- 按步骤完成审批工作流设计
- 每一步都说明对应概念

### 交付物

- 审批工作流图
- state 说明
- interrupt 说明
- 恢复策略说明

## Session 6: 独立完成课后项目

### 学习目标

- 在没有标准答案的情况下独立设计图系统
- 接受基于 state 与控制流的评审

### 先读什么

- [05-challenges.md](./05-challenges.md)
- [Stage 3 课后项目](../../../03-projects/stage-3/homework-project-multi-stage-research-workflow.md)

### 要做什么

- 独立完成多阶段研究工作流方案
- 让 Codex 按 state、interrupt、恢复与边界来评审

### 交付物

- 多阶段工作流方案
- 自评结果
- Codex 评审反馈

## Session 7: 阶段复盘与放行

### 学习目标

- 确认自己是否真正具备 LangGraph 运行时思维
- 为进入 Deep Agents 做准备

### 先读什么

- [06-review-checklist.md](./06-review-checklist.md)
- [07-codex-workshop.md](./07-codex-workshop.md)

### 要做什么

- 回答 Stage 3 放行问题
- 说明 interrupt 在你的项目里真正暂停了什么
- 说明为什么恢复不是“重来一次”

### 放行标准

你至少应该能稳定做到:

- 用图显式表达控制流
- 为流程设计合理 state
- 把审批与暂停设计进系统
- 为失败设计恢复路径
- 说明为什么项目必须使用 LangGraph

## 建议学习闭环

每完成一个 session，都做一次同样的闭环:

1. 复述这节最核心的一句话。
2. 写下你显式化了哪些原本隐式存在的控制流。
3. 写下你新增了哪些状态与恢复意识。
4. 让 Codex 只从图系统评审角度给你反馈。

如果你希望真正按节奏开始学，现在最适合从 `Session 1` 正式推进。
