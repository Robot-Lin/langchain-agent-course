# 跟学项目: 深度研究 Agent

## 所属阶段

Stage 4: Deep Agents

## 项目目标

设计一个复杂任务型 Deep Agent。它需要接收研究主题，规划研究路线，拆出多个子任务角色，分层组织上下文，并在关键阶段汇总结果和请求人工修正方向。

## 对应知识点

- 复杂目标拆解
- Context engineering
- Subagents
- 复杂任务治理
- Human-in-the-loop

对应阅读:

- [Stage 4 Overview](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/01-overview.md)
- [Stage 4 Concepts](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/02-concepts.md)
- [Stage 4 Methods](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/03-methods.md)

## 最终产出

- 一份复杂目标拆解图
- 一份 context 分层说明
- 一份子代理角色说明
- 一份治理点与审批点清单
- 一份为什么更适合 Deep Agents 的说明

## AI 带学步骤

### Step 1: 定义复杂总目标

要做什么:

- 明确最终研究结果是什么

为什么先做:

- 复杂任务最容易从目标层就发散

知识点关联:

- 复杂目标拆解法

### Step 2: 拆阶段目标

要做什么:

- 将总目标拆成研究阶段

为什么先做:

- 不拆阶段，后续角色和上下文会全部混在一起

知识点关联:

- 复杂目标拆解法

### Step 3: 设计 context 分层

要做什么:

- 区分长期资料、当前状态和子任务上下文

为什么先做:

- context engineering 是这一阶段核心

知识点关联:

- Context 分层法

### Step 4: 设计子代理角色

要做什么:

- 为收集、分析、汇总等任务定义角色

为什么先做:

- 子代理只有真正降低复杂度时才有价值

知识点关联:

- Subagent 必要性判断法

### Step 5: 设计治理点

要做什么:

- 识别偏航、审批和质量检查点

为什么先做:

- 复杂任务最怕慢慢跑偏

知识点关联:

- 复杂任务治理法

## 阶段检查点

- 能说清总目标和阶段目标
- 能说明 context 分层
- 能解释为什么需要这些子代理
- 能写出治理点与审批点

## 与 Codex 的配合方式

推荐对 Codex 说:

- 先根据 Stage 4 的概念文件，带我一步步完成这个 Deep Agent 设计
- 每一步先解释对应知识点，再帮我检查复杂任务拆解
- 不要一开始就给我完整方案，先让我自己拆，再帮我修正
