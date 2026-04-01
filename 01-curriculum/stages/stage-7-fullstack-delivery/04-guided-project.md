# 04 Guided Project

本章引导项目选择 `全栈研究控制台交付版`。它把前端、后端、Agent runtime、流式链路、评测和交付收成一个完整产品。

## 项目目标

设计一个全栈 Agent 产品。它需要支持用户在前端发起研究任务，通过后端和 Agent runtime 执行任务，流式返回状态和结果，并具备 deployment、observability 和 evaluation 思路。

## 为什么这个项目适合 Stage 7

因为它同时具备：

- 真实用户入口
- 前后端链路
- Agent runtime
- streaming integration
- 观测与评测闭环
- 产品交付与迭代空间

这正好覆盖 Stage 7 的核心能力。

## 项目最终交付物

完成这个项目时，至少要交付：

- 一张全栈系统图
- 一份前后端与 runtime 链路说明
- 一份 deployment 与运行方案
- 一份 observability 与 evaluation 方案
- 一份框架选型与取舍说明

## Step 1: 画完整链路

至少包括：

- 前端
- 请求入口
- Agent Server / runtime
- 工具与知识层
- 观测与评测层

这一阶段先看链路是否闭环，不急着抠实现细节。

## Step 2: 设计前后端流式链路

明确：

- 用户如何接收实时状态
- 前端如何承接中断与审批
- Agent 运行中的反馈如何回到产品界面

## Step 3: 设计交付与运行方案

明确：

- 系统如何运行
- 如何部署
- 如何追踪和排障
- 如何做版本迭代

## Step 4: 设计评测与验收

明确：

- 哪些指标决定这一版可以交付
- 如何判断产品是否稳定可用
- 如何在上线后继续评估表现

## Step 5: 写选型说明

明确：

- 为什么这里用当前主线框架
- 为什么不用更轻或更重的替代方案
- 未来如果规模变化，架构如何调整

## Step 6: 复盘为什么这已经是产品交付而不只是项目设计

项目做完后，必须回答：

- 哪些部分让它从“工程方案”变成“可交付产品”
- 哪些部分还只是原型层
- 下一版要优先补什么

## Codex 在这个项目里怎么配合

你可以让 Codex：

- 检查系统链路是否缺层
- 检查 deployment、observability、evaluation 是否只是口号
- 检查前端与运行时之间的反馈链路是否闭环
- 检查选型说明是否真的有取舍逻辑

但不要让 Codex 直接替你输出最终交付稿。你真正要练的是交付判断。

## 配套项目入口

- [Stage 7 跟学项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-7/guided-project-fullstack-research-console.md)
- [Stage 7 课后项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-7/homework-project-agent-product-delivery.md)
