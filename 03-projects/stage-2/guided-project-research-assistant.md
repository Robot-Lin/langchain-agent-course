# 跟学项目: 单工具研究助理

## 所属阶段

Stage 2: LangChain Builder

## 项目目标

设计一个 LangChain 高层 Agent 原型。它能够接收一个研究问题，调用单一查询工具收集信息，并输出结构化研究摘要。

## 对应知识点

- LangChain 的高层定位
- 工具最小化
- Structured output
- Middleware 思维
- 高层人工审核意识

对应阅读:

- [Stage 2 Overview](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/01-overview.md)
- [Stage 2 Concepts](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/02-concepts.md)
- [Stage 2 Methods](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/03-methods.md)

## 最终产出

- 一份 LangChain 原型说明
- 一份工具定义
- 一份结构化输出设计
- 一份控制逻辑说明
- 一份高层边界复盘

## AI 带学步骤

### Step 1: 明确唯一主任务

要做什么:

- 确定这个原型只做一件事: 回答研究问题并输出摘要

为什么先做:

- 高层原型最怕一开始就变成“什么都想做”

知识点关联:

- 高层原型四步法

### Step 2: 只保留一个工具

要做什么:

- 选择一个最必要的查询工具

为什么先做:

- 先验证主路径，不让工具复杂度喧宾夺主

知识点关联:

- 工具最小化

### Step 3: 设计 structured output

要做什么:

- 定义摘要的字段和用途

为什么先做:

- 没有结构化输出，结果很难复用和评估

知识点关联:

- 先设计输出，再设计提示词

### Step 4: 设计基础控制逻辑

要做什么:

- 判断何时先追问，何时直接查询，何时输出结果

为什么先做:

- 高层 Agent 也需要最基本的流程控制

知识点关联:

- Middleware 外挂法

### Step 5: 做高层边界复盘

要做什么:

- 判断当前方案为什么还适合 LangChain
- 判断未来在哪些地方会逼近 LangGraph

为什么先做:

- 让学习者尽早感知框架边界

知识点关联:

- 何时停止留在 LangChain

## 阶段检查点

- 能说清唯一主任务
- 能解释为什么只保留一个工具
- 能给出结构化输出字段
- 能说明控制逻辑和边界

## 与 Codex 的配合方式

推荐对 Codex 说:

- 先根据 Stage 2 的概念文件，带我一步步完成这个 LangChain 研究助理
- 每一步先解释对应知识点，再推进设计
- 不要一次给我最终实现，先让我自己做选择，再帮我纠偏
