# 04 Guided Project

本阶段引导项目选择 `研究控制台前端`。它能同时训练流式交互、结构化展示、状态面板和审批区域。

## 项目目标

设计一个 Agent 前端控制台。它需要支持用户发起研究任务，查看计划和执行状态，看到流式更新，在关键节点审批，并查看结构化研究结果。

## 这一项目为什么适合 Stage 6

- 它天然需要 streaming
- 它天然需要状态可视化
- 它天然需要结构化结果展示
- 它可以自然加入审批面板

## Step 1: 设计任务旅程

明确:

- 用户如何发起任务
- 系统如何反馈已接收
- 用户如何看到执行过程
- 用户如何审批
- 用户如何查看结果

## Step 2: 设计界面分区

至少包括:

- 输入区
- 任务与计划区
- 执行状态区
- 审批区
- 结果区

## Step 3: 设计 streaming 反馈

明确:

- 哪些内容实时更新
- 哪些内容按阶段展示

## Step 4: 设计结果展示

将结果拆成:

- 结论摘要
- 关键依据
- 不确定点
- 下一步建议

## Step 5: 设计审批体验

明确:

- 审批前看见什么
- 可以批准、拒绝或修改什么

## Step 6: 复盘为什么这个前端比聊天框更适合 Agent

项目做完后，学习者必须回答:

- 哪些能力聊天框难以承载
- 为什么状态和审批必须单独可见

配套项目包:

- [Stage 6 跟学项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-6/guided-project-research-console-ui.md)
- [Stage 6 课后项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-6/homework-project-enterprise-agent-dashboard.md)
