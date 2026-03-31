# 04 Guided Project

本阶段引导项目选择 `研究控制台产品化版`。它能把前端、后端、Agent runtime、流式更新、评测和交付完整连起来。

## 项目目标

设计一个全栈 Agent 产品。它需要支持用户在前端发起研究任务，通过后端和 Agent runtime 执行任务，流式返回状态和结果，并具备部署、观测和评测思路。

## 这一项目为什么适合 Stage 7

- 它有真实用户入口
- 它有前后端链路
- 它有 Agent runtime
- 它有流式更新
- 它需要部署与评测闭环

## Step 1: 画完整系统图

至少包括:

- 前端
- 请求入口
- Agent Server / runtime
- 工具与知识层
- 观测与评测层

## Step 2: 设计前后端流式链路

明确:

- 用户如何收到实时状态
- 中断和审批如何回到前端

## Step 3: 设计交付与运行方案

明确:

- 系统如何运行
- 如何部署
- 如何调试和追踪

## Step 4: 设计评测与验收

明确:

- 哪些指标决定这一版可交付
- 如何判断产品是否可用

## Step 5: 写选型说明

明确:

- 为什么这里用当前主线框架
- 为什么不是别的更轻或更重方案

## Step 6: 复盘为什么这已经是产品交付，而不只是项目设计

项目做完后，学习者必须回答:

- 哪些部分使它从“工程方案”变成“产品交付”

配套项目包:

- [Stage 7 跟学项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-7/guided-project-fullstack-research-console.md)
- [Stage 7 课后项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-7/homework-project-agent-product-delivery.md)
