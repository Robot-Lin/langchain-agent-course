# 课程路线图

## 课程设计原则

- 从系统判断进入，而不是直接陷入 API 细节
- 从单 Agent 到复杂系统，逐步增加复杂度
- 从概念理解到架构选择，再到项目实践与交付
- 每个阶段都有可交付成果
- 每个阶段都尽量可以在“少写代码、与 Codex 共学”的前提下推进

## Stage 0: 学习环境与协作方式

目标：

- 建立和 Codex 协作的学习方式
- 明确 Agent 学习不只是提示词工程
- 看懂课程整体地图

产出：

- 一份个人学习目标说明
- 一份场景偏好清单
- 一份自己的 Agent 学习问题清单

## Stage 1: Agent 基础心智模型

目标：

- 理解 Agent 的最小组成
- 建立模型、工具、状态、记忆、策略和交互之间的关系
- 能说清 Agent 与普通聊天机器人的差别

核心主题：

- Agent 的系统结构
- 工具使用与动作选择
- 短期记忆与长期记忆
- 任务拆解与执行边界
- 失败路径与安全边界

建议项目：

- FAQ 助手
- 单工具研究助理
- 结构化信息抽取助手

## Stage 2: LangChain 入门到实用

目标：

- 用 LangChain 搭出高层 Agent 原型
- 理解模型接入、tools、structured output、memory、middleware
- 学会选择“够用的复杂度”

核心主题：

- LangChain 的定位
- 高层 Agent 原型
- Tools 与 structured output
- Middleware
- 基础 human-in-the-loop

建议项目：

- 单工具研究助理
- 结构化面试 Agent
- 日程与知识库助手

## Stage 3: LangGraph 系统化设计

目标：

- 从“调用 Agent”切换到“编排 Agent”
- 学会用图结构表达状态机、分支、循环、恢复和中断
- 为更复杂场景建立稳固底座

核心主题：

- Graph 思维
- State 设计
- Durable execution
- Interrupts
- Human-in-the-loop
- Multi-step workflow

建议项目：

- 带人工审批的流程 Agent
- 多阶段研究工作流
- 带恢复能力的任务执行系统

## Stage 4: Deep Agents 复杂任务实战

目标：

- 理解 Deep Agents 适合解决什么问题
- 学会规划、上下文工程、子代理和复杂任务拆解
- 搭出更像“资深执行助理”的系统

核心主题：

- Planning
- Context engineering
- Subagents
- Human approval
- 长任务与复杂目标执行

建议项目：

- 深度研究 Agent
- 内容策略 Agent
- 代码库导航与实现顾问

## Stage 5: Agent Engineering

目标：

- 把 Agent 做成真实工程系统，而不是 Demo
- 补上知识接入、工具协议、数据层、后端接口、LangSmith 观测评测与治理

核心主题：

- MCP
- RAG
- Memory / 数据库 / API 边界
- LangSmith Observability
- LangSmith Evaluation
- Governance

建议项目：

- 企业知识与流程一体化 Agent 后端
- 多源支持 Agent
- CRM / 工单 / 日程整合 Agent

## Stage 6: Agent Frontend

目标：

- 理解 Agent UX 与普通聊天 UX 的差别
- 学会设计流式反馈、审批界面、状态可视化和结构化结果展示
- 把系统能力翻译成用户真正能理解和使用的体验

核心主题：

- Agent UX
- Structured output rendering
- Streaming
- Human-in-the-loop UI
- History / source visibility
- Multi-panel experience

建议项目：

- 研究控制台前端
- 企业 Agent 仪表盘
- 多面板任务工作台

## Stage 7: Full-stack Delivery

目标：

- 把前后端、Agent runtime、数据层和知识层组装成完整产品
- 学会 deployment、LangSmith observability、LangSmith evaluation 和版本迭代
- 具备交付全栈 Agent 产品的能力

核心主题：

- Full-stack architecture
- Agent Server
- Streaming integration
- Deployment
- LangSmith Observability
- LangSmith Evaluation
- Framework selection

建议项目：

- 全栈研究控制台交付版
- 企业审批助手全栈版
- 多工具工作台 Agent

## Stage 8: Capstone Mastery

目标：

- 独立完成一个毕业级 Agent 产品
- 同时覆盖后端、知识层、前端、交互、评测、交付与复盘
- 形成可迁移的方法，而不是只完成一个项目

候选方向：

- 深度研究助手
- 学习教练 Agent
- 企业流程审批助手
- 创作者工作台
- 个人操作系统型 Agent

毕业要求：

- 能在 AI Agent 协作下完成一个从后端到前端的完整项目
- 能解释其架构、状态、知识、工具、交互、评测和交付设计
- 能完成一次完整复盘并规划后续迭代

## 官方文档锚点

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Model Context Protocol (MCP)](https://docs.langchain.com/oss/python/langchain/mcp)
- [LangChain frontend human-in-the-loop](https://docs.langchain.com/oss/python/langchain/frontend/human-in-the-loop)
- [LangSmith Observability](https://docs.langchain.com/langsmith/observability)
- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
