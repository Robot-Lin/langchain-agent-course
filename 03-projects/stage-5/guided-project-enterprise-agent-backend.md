# 跟学项目: 企业 Agent 后端架构

## 所属阶段

Stage 5: Agent Engineering

## 项目目标

设计一个工程化 Agent 后端架构。它需要能检索企业知识、接入 MCP 或工具能力访问外部系统、读写业务数据，并通过 observability、evaluation 和治理机制保持可控。

## 对应知识点

- MCP 接入
- RAG
- Memory / DB / API 分层
- Observability
- Evaluation
- 权限治理

对应阅读:

- [Stage 5 Overview](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/01-overview.md)
- [Stage 5 Concepts](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/02-concepts.md)
- [Stage 5 Methods](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/03-methods.md)

## 最终产出

- 一张分层架构图
- 一份知识层与工具层说明
- 一份数据层与 API 说明
- 一份指标与追踪方案
- 一份权限治理清单

## AI 带学步骤

### Step 1: 画工程分层

要做什么:

- 先把 Agent、MCP、RAG、数据、API、观测、治理分层画出来

为什么先做:

- 没有分层，后续所有能力都会混在一起

知识点关联:

- 横向能力分层法

### Step 2: 区分知识与数据

要做什么:

- 明确哪些是 memory，哪些是知识库，哪些是数据库

为什么先做:

- 这是工程边界的核心问题

知识点关联:

- 知识接入选择法

### Step 3: 设计外部能力接入

要做什么:

- 明确什么走 MCP，什么走 API，什么需要权限控制

为什么先做:

- 外部接入能力是系统风险和价值都最高的部分之一

知识点关联:

- 先画边界，再接能力

### Step 4: 设计观测与评测

要做什么:

- 写出要追踪的步骤和要衡量的指标

为什么先做:

- 没有追踪和指标，系统无法持续迭代

知识点关联:

- 观测与评测前置法

### Step 5: 设计治理清单

要做什么:

- 为每个外部能力写权限和审批规则

为什么先做:

- 真正的企业系统不能只看功能，不看风险

知识点关联:

- 权限治理清单法

## 阶段检查点

- 能说清分层结构
- 能区分知识和数据边界
- 能说明 MCP 和 API 的角色
- 能写出观测与治理方案

## 与 Codex 的配合方式

推荐对 Codex 说:

- 先根据 Stage 5 的概念文件，带我一步步完成这个工程化 Agent 架构
- 每一步先解释对应知识点，再帮我检查分层是否清楚
- 不要一开始就给完整架构，先让我自己分层，再帮我修正
