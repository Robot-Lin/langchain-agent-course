# 跟学项目: 研究控制台前端

## 所属阶段

Stage 6: Agent Frontend

## 项目目标

设计一个研究 Agent 控制台前端。它需要支持用户发起任务、看到计划与执行状态、接收 streaming 更新、审批关键动作，并查看结构化研究结果。

## 对应知识点

- Agent UX
- 界面分区
- Streaming 反馈
- Structured output 展示
- 审批交互

对应阅读:

- [Stage 6 Overview](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/01-overview.md)
- [Stage 6 Concepts](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/02-concepts.md)
- [Stage 6 Methods](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-6-agent-frontend/03-methods.md)

## 最终产出

- 一张前端结构图
- 一份任务旅程说明
- 一份状态和审批交互说明
- 一份结果展示结构说明
- 一份为什么这不是普通聊天框的说明

## AI 带学步骤

### Step 1: 画任务旅程

要做什么:

- 定义用户从发起任务到查看结果的全过程

为什么先做:

- 没有任务旅程，界面会变成组件堆砌

知识点关联:

- 任务旅程设计法

### Step 2: 设计界面分区

要做什么:

- 把输入、计划、状态、审批和结果分开

为什么先做:

- Agent 信息类型比普通 chat 多得多

知识点关联:

- Agent 界面分区法

### Step 3: 设计 streaming 与状态反馈

要做什么:

- 明确哪些信息实时出现

为什么先做:

- 长任务必须让用户始终有反馈

知识点关联:

- 流式反馈设计法

### Step 4: 设计审批和可控性交互

要做什么:

- 定义审批前后用户能做什么

为什么先做:

- Agent 的可控性主要通过交互体现

知识点关联:

- 可控性设计法

### Step 5: 设计结果结构化展示

要做什么:

- 将结果分成摘要、依据、不确定点和下一步

为什么先做:

- 复杂结果不该只塞进对话气泡

知识点关联:

- 结果结构化展示法

## 阶段检查点

- 能说清任务旅程
- 能说明界面分区
- 能解释 streaming 和审批设计
- 能说明为什么这样展示结果

## 与 Codex 的配合方式

推荐对 Codex 说:

- 先根据 Stage 6 的概念文件，带我一步步完成这个 Agent 前端控制台
- 每一步先解释对应知识点，再帮我检查前端结构
- 不要一开始就给最终界面，先让我自己画分区，再帮我修正
