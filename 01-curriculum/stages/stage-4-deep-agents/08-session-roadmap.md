# 08 Session Roadmap

这个文件把 `Stage 4` 拆成一组真正可以执行的学习 session。你可以自己按节奏推进，也可以让 Codex 按这个顺序一节一节带你学。

## 建议总时长

- 轻量模式: 5 到 6 天
- 标准模式: 1 到 2 周
- 深挖模式: 2 周以上

## Session 1: 什么任务适合 Deep Agents

### 学习目标

- 理解 Deep Agents 在新版体系中的角色
- 建立复杂任务边界意识
- 知道哪些任务并不适合直接上 Deep Agents

### 先读什么

- [01-overview.md](./01-overview.md)
- [02-concepts.md](./02-concepts.md)
- [03-methods.md](./03-methods.md) 末尾附录

### 要做什么

- 用自己的话解释 Deep Agents 解决什么问题
- 写出 3 个适合 Deep Agents 的场景
- 写出 3 个不适合 Deep Agents 的场景

### 交付物

- 一段 120 到 180 字的理解复述
- 一张 Deep Agents 与 LangGraph 的边界对比表

## Session 2: 复杂目标拆解

### 学习目标

- 学会把复杂目标拆成阶段、角色和汇总目标
- 避免“一个大目标全塞给一个 agent”

### 先读什么

- [03-methods.md](./03-methods.md)
- [02-concepts.md](./02-concepts.md) 后半部分代码教材

### 要做什么

- 选一个复杂目标
- 写出总目标、阶段目标、子任务角色和最终汇总目标

### 交付物

- 一份复杂目标拆解图

## Session 3: context engineering

### 学习目标

- 理解 context engineering 不是“塞更多上下文”
- 学会为不同角色和阶段分层上下文

### 先读什么

- [02-concepts.md](./02-concepts.md)
- [03-methods.md](./03-methods.md)
- [02-concepts.md](./02-concepts.md) 后半部分代码教材

### 要做什么

- 为一个复杂任务写出 context 分层
- 区分长期资料、当前状态、当前子任务上下文

### 交付物

- 一份 context 分层说明

## Session 4: subagents 与治理

### 学习目标

- 学会判断 subagents 是否必要
- 学会设计审核点和方向修正点

### 先读什么

- [02-concepts.md](./02-concepts.md)
- [09-case-comparisons.md](./09-case-comparisons.md)
- [02-concepts.md](./02-concepts.md) 后半部分代码教材

### 要做什么

- 为一个复杂任务设计至少 3 个角色
- 说明每个角色为什么存在
- 写出至少 3 个治理点或审核点

### 交付物

- subagent 分工表
- 治理点清单

## Session 5: 跟做深度研究 Agent

### 学习目标

- 把概念和方法落实到复杂任务型 Agent 项目上
- 练习目标拆解、context 分层、角色分工和治理四件套

### 先读什么

- [04-guided-project.md](./04-guided-project.md)
- [10-full-project-reading.md](./10-full-project-reading.md)
- [Stage 4 跟学项目](../../../03-projects/stage-4/guided-project-deep-research-agent.md)

### 要做什么

- 按步骤完成深度研究 Agent 设计
- 每一步都说明对应概念

### 交付物

- 深度研究 Agent 设计说明
- context 分层说明
- subagent 分工说明
- 治理点说明

## Session 6: 独立完成课后项目

### 学习目标

- 在没有标准答案的情况下独立设计复杂任务型 Agent
- 接受基于目标拆解与治理的评审

### 先读什么

- [05-challenges.md](./05-challenges.md)
- [Stage 4 课后项目](../../../03-projects/stage-4/homework-project-content-strategy-agent.md)

### 要做什么

- 独立完成内容策略 Agent 方案
- 让 Codex 按目标拆解、context、subagents 和治理来评审

### 交付物

- 内容策略 Agent 方案
- 自评结果
- Codex 评审反馈

## Session 7: 阶段复盘与放行

### 学习目标

- 确认自己是否真正具备复杂任务组织思维
- 为进入工程化整合阶段做准备

### 先读什么

- [06-review-checklist.md](./06-review-checklist.md)
- [07-codex-workshop.md](./07-codex-workshop.md)

### 要做什么

- 回答 Stage 4 放行问题
- 说明为什么这里需要上下文分层
- 说明为什么这些子代理是必要的

### 放行标准

你至少应该能稳定做到:

- 说明为什么任务更适合 Deep Agents
- 把复杂目标拆出清楚层次
- 设计上下文分层
- 判断 subagents 是否必要
- 设计治理点防止任务偏航

## 建议学习闭环

每完成一个 session，都做一次同样的闭环:

1. 复述这节最核心的一句话。
2. 写下你拆清了哪些复杂目标。
3. 写下你新增了哪些上下文与治理意识。
4. 让 Codex 只从复杂任务评审角度给你反馈。

如果你希望真正按节奏开始学，现在最适合从 `Session 1` 正式推进。
