# 跟学项目: 全栈研究控制台交付版

## 所属阶段

Stage 7: Full-stack Delivery

## 项目目标

设计一个可交付的全栈 Agent 产品。它需要支持前端发起研究任务，后端通过 Agent runtime 执行任务，流式返回状态和结果，并具备部署、追踪和评测方案。

## 对应知识点

- 全链路组装
- Agent Server
- Streaming integration
- Deployment
- Observability / Evaluation
- 交付与选型说明

对应阅读:

- [Stage 7 Overview](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/01-overview.md)
- [Stage 7 Concepts](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/02-concepts.md)
- [Stage 7 Methods](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-7-fullstack-delivery/03-methods.md)

## 最终产出

- 一张全链路系统图
- 一份前后端与 runtime 链路说明
- 一份部署和追踪方案
- 一份评测与验收说明
- 一份选型说明

## AI 带学步骤

### Step 1: 画全链路

要做什么:

- 从用户入口一直画到 runtime、数据层和结果回流

为什么先做:

- 全栈交付先看链路闭不闭合

知识点关联:

- 全链路组装法

### Step 2: 设计流式与 Agent Server 链路

要做什么:

- 说明前端如何实时接收状态与结果

为什么先做:

- 全栈 Agent 的体验和运行时必须连起来

知识点关联:

- 全链路组装法

### Step 3: 设计部署与运行

要做什么:

- 说明系统如何运行、如何对外提供服务、如何定位问题

为什么先做:

- 交付不能停在结构图层面

知识点关联:

- 部署前置思维

### Step 4: 设计评测与验收

要做什么:

- 写出交付版的核心验收指标

为什么先做:

- 没有验收，就没有交付标准

知识点关联:

- 交付三问法

### Step 5: 写选型说明

要做什么:

- 说明为什么这套交付链路合理

为什么先做:

- 交付是有取舍的，不是堆配置

知识点关联:

- 选型说明法

## 阶段检查点

- 能说清全链路
- 能解释 Agent Server 位置
- 能说明如何部署和追踪
- 能给出交付验收指标

## 与 Codex 的配合方式

推荐对 Codex 说:

- 先根据 Stage 7 的概念文件，带我一步步完成这个全栈 Agent 交付方案
- 每一步先解释对应知识点，再帮我检查交付链路
- 不要一开始就给最终交付图，先让我自己画，再帮我修正
