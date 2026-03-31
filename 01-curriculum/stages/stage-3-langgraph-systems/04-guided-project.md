# 04 Guided Project

本阶段引导项目选择 `带人工审批的流程 Agent`。它最能体现 LangGraph 的真正价值。

## 项目目标

设计一个任务执行工作流。系统需要先理解请求，再生成执行计划，在关键动作前暂停等待审批，审批通过后继续执行，失败时能够回退或重新决策。

## 这一项目为什么适合 Stage 3

- 它必须用 state
- 它必须有分支
- 它必须有 interrupt
- 它必须考虑恢复

## Step 1: 先画主路径

例如:

- 接收任务
- 生成计划
- 请求审批
- 执行动作
- 输出结果

## Step 2: 定义 state

至少包括:

- 原始任务
- 当前阶段
- 当前计划
- 审批状态
- 执行结果
- 失败信息

## Step 3: 补关键分支

例如:

- 审批通过
- 审批拒绝
- 执行失败
- 输入不完整

## Step 4: 设计 interrupt

把中断放在:

- 审批前
- 关键信息缺失时

## Step 5: 设计恢复策略

例如:

- 审批拒绝后返回计划修订
- 执行失败后回到策略选择节点

## Step 6: 复盘为什么这已经不适合只用 LangChain

项目做完后，学习者必须回答:

- 为什么这里已经需要显式图编排
- 为什么 interrupt 不能只靠 prompt 模拟

配套项目包:

- [Stage 3 跟学项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-3/guided-project-approval-workflow-agent.md)
- [Stage 3 课后项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-3/homework-project-multi-stage-research-workflow.md)
