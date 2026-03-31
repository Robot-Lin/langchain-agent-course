# 跟学项目: FAQ Agent

## 所属阶段

Stage 1: Agent Foundations

## 项目目标

设计一个面向课程新手的 FAQ Agent。它能够理解用户的问题，结合课程目录给出学习路径建议，并在问题不清晰时先追问。

## 对应知识点

- Agent 与聊天机器人的差别
- 工具的必要性判断
- 状态的最小化设计
- 失败路径识别
- 人工介入与澄清点

对应阅读:

- [Stage 1 Overview](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-1-agent-foundations/01-overview.md)
- [Stage 1 Concepts](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-1-agent-foundations/02-concepts.md)
- [Stage 1 Methods](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-1-agent-foundations/03-methods.md)

## 最终产出

- 一份 FAQ Agent 自然语言架构说明
- 一张最小系统图
- 一份风险与失败点清单
- 一份用户澄清策略

## AI 带学步骤

### Step 1: 明确用户与目标

要做什么:

- 识别谁在使用它
- 明确它的唯一主任务

为什么先做:

- 不先定目标，后面会自然堆功能

知识点关联:

- 最小 Agent 设计法

### Step 2: 定义输入与输出

要做什么:

- 说明用户会问什么
- 说明系统要返回什么

为什么先做:

- 输出不明确，系统就不可验证

知识点关联:

- 输出结构与边界判断

### Step 3: 判断工具是否必要

要做什么:

- 判断是否需要读取课程目录
- 判断是否需要外部搜索

为什么先做:

- 工具不是越多越好，先保留必要能力

知识点关联:

- 工具边界

### Step 4: 判断状态与记忆

要做什么:

- 判断是否需要保留上一轮上下文
- 判断是否需要长期记忆

为什么先做:

- 避免把状态、记忆和知识库混在一起

知识点关联:

- 状态与记忆区分

### Step 5: 写出失败路径

要做什么:

- 列出至少 5 个失败点

为什么先做:

- Agent 的质量不只是看主路径能不能跑

知识点关联:

- 失败前置设计

### Step 6: 设计澄清与人工介入点

要做什么:

- 判断哪些问题系统不能直接答

为什么先做:

- 让系统懂得停下来，比盲目输出更重要

知识点关联:

- human-in-the-loop 的基础意识

## 阶段检查点

- 能用一句话讲清项目目标
- 能说明为什么只保留最少工具
- 能说明为什么这里不需要长期记忆
- 能列出失败点和澄清策略

## 与 Codex 的配合方式

推荐对 Codex 说:

- 先根据 Stage 1 的概念文件，带我一步步完成这个 FAQ Agent
- 每一步先解释对应知识点，再推进下一步
- 不要一次给我最终答案，先让我自己回答，再帮我修正
