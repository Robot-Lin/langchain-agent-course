# 04 Guided Project

本阶段引导项目选择 `企业知识与流程一体化 Agent` 的后端版。它能把 MCP、RAG、数据层、API、评测和治理集中练到。

## 项目目标

设计一个工程化 Agent 系统。它能够接收企业内部问题，检索知识库，调用受控工具或 MCP 能力访问流程系统，在需要时读取业务数据，并通过观测和评测机制持续验证输出质量。

## 这一项目为什么适合 Stage 5

- 它同时需要知识层和工具层
- 它必须处理数据边界
- 它必须考虑 API 和业务系统连接
- 它必须有观测、评测和治理设计

## Step 1: 先画分层架构

至少画出:

- Agent 层
- MCP / 工具层
- RAG / 知识层
- 数据 / 数据库层
- API / 业务层
- Observability / Evaluation 层

## Step 2: 区分 memory、知识库和数据库

明确:

- 什么属于用户连续性信息
- 什么属于文档检索
- 什么属于业务状态和记录

## Step 3: 设计外部能力接入

明确:

- 哪些能力通过 MCP 接入
- 哪些能力通过 API 接入
- 哪些能力必须设权限和审批

## Step 4: 设计观测与评测

至少写清:

- 要记录哪些运行轨迹
- 要看哪些质量指标
- 如何知道系统是否变差

## Step 5: 设计治理清单

例如:

- 哪些动作高风险
- 哪些数据敏感
- 哪些调用必须审计

## Step 6: 复盘为什么这是工程问题，不只是 Agent 设计问题

项目做完后，学习者必须回答:

- 为什么 Agent 做到这里已经不只是模型和工作流
- 为什么没有评测和治理，系统就不算完整

配套项目包:

- [Stage 5 跟学项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-5/guided-project-enterprise-agent-backend.md)
- [Stage 5 课后项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-5/homework-project-multi-source-support-agent.md)
