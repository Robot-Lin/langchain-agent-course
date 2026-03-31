# 04 Guided Project

本阶段引导项目选择 `深度研究 Agent`。它最能体现复杂目标、上下文分层和子任务角色的必要性。

## 项目目标

设计一个深度研究 Agent。它需要接收研究主题，规划研究路径，拆分多个子任务，汇总各阶段发现，并在关键时刻允许人工调整方向或批准输出。

## 这一项目为什么适合 Stage 4

- 它需要规划
- 它需要 context engineering
- 它需要角色分工
- 它需要复杂任务治理

## Step 1: 定义复杂总目标

先写清:

- 最终要交付什么研究结果
- 什么不在这个 Agent 当前范围内

## Step 2: 拆阶段目标

例如:

- 定义研究问题
- 收集资料
- 对比观点
- 汇总结论
- 形成最终输出

## Step 3: 设计子代理角色

例如:

- 资料搜集角色
- 观点整理角色
- 总结汇总角色

## Step 4: 设计 context 分层

明确:

- 哪些上下文给主代理
- 哪些上下文给子代理
- 哪些结果需要回流到总控层

## Step 5: 设计治理点

例如:

- 研究方向是否偏航
- 是否需要人工确认研究范围
- 输出前是否需要审阅

## Step 6: 复盘为什么这不仅仅是 LangGraph

项目做完后，学习者必须回答:

- 为什么这里不仅是工作流问题
- 为什么上下文组织和角色分工成为核心

配套项目包:

- [Stage 4 跟学项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-4/guided-project-deep-research-agent.md)
- [Stage 4 课后项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-4/homework-project-content-strategy-agent.md)
