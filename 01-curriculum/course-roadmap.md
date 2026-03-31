# 课程路线图

## 课程设计原则

- 从外层系统观进入，而不是直接掉进 API 细节
- 从单 Agent 到复杂系统逐步加复杂度
- 从概念理解到架构选择再到项目实践
- 每个阶段都有可交付成果
- 每个阶段都能在“基本不手写代码”的前提下推进

## Stage 0: 学习环境与心智准备

目标:

- 建立和 Codex 协作的学习方式
- 明确 Agent 学习的范围不是只有提示词
- 看懂课程整体地图

产出:

- 一份个人学习目标说明
- 一份场景偏好清单
- 一份你自己的 Agent 学习问题清单

## Stage 1: Agent 基础心智模型

目标:

- 理解 Agent 的最小组成
- 建立模型、工具、状态、记忆、策略、交互之间的关系
- 能说清楚 Agent 与普通聊天机器人的差别

核心主题:

- Agent 的系统结构
- 工具使用与动作选择
- 短期记忆与长期记忆
- 任务拆解与执行边界
- 失败路径与安全边界

建议项目:

- 单工具研究助理
- FAQ 助手
- 结构化信息抽取助手

## Stage 2: LangChain 入门到实用

目标:

- 用 LangChain 搭出高层 Agent 原型
- 理解模型接入、工具、结构化输出、基础 memory、middleware
- 学会选择“够用的复杂度”

核心主题:

- LangChain 的定位
- Agent 构建基本路径
- Tools 与 toolkits
- Structured output
- Middleware
- 基础人机协作

建议项目:

- 浏览器研究助手
- 结构化面试官
- 日程与知识库助理

## Stage 3: LangGraph 系统化设计

目标:

- 从“调用 Agent”转向“编排 Agent”
- 学会用图结构表达状态机、分支、循环、恢复、中断
- 为更复杂场景建立稳固底座

核心主题:

- Graph 思维
- State 设计
- Durable execution
- Interrupts
- Human-in-the-loop
- Multi-agent orchestration

建议项目:

- 带人工审批的采购 Agent
- 多阶段研究与汇总 Agent
- 带恢复能力的任务执行工作流

## Stage 4: Deep Agents 复杂任务实战

目标:

- 理解 Deep Agents 适合解决什么问题
- 学会规划、上下文工程、子代理、复杂任务分解
- 能搭出更像“资深执行助手”的系统

核心主题:

- Deep Agents 的产品定位
- Context engineering
- Subagents
- Human approval
- 长任务与复杂目标执行

建议项目:

- 深度研究 Agent
- 内容策划 Agent
- 代码库导航与实现顾问

## Stage 5: 横向能力层

目标:

- 把 Agent 做成真实系统，而不是玩具 Demo
- 补上知识接入、工具生态、状态存储、数据层、观测和评测

核心主题:

- MCP
- RAG
- 数据库与存储
- 后端服务与 API
- LangSmith 观测与评测
- Guardrails 与权限边界
- Skill 化与能力封装

建议项目:

- 多源知识问答 Agent
- 企业知识检索与流程执行 Agent
- CRM / 工单 / 日程三系统集成 Agent

## Stage 6: 前端与 Agent 交互体验

目标:

- 理解一个可用 Agent 为什么一定离不开好的交互设计
- 学会设计流式输出、审批界面、计划可视化、历史记录、失败反馈
- 搭出用户愿意长期使用的界面

核心主题:

- Chat UX 与 Agent UX 的区别
- 流式交互
- 工具状态可视化
- 审批与可控性设计
- 任务历史和记忆可见性
- 多模态与多面板交互

建议项目:

- 研究控制台
- 任务执行面板
- 带审批流的企业助手前端

## Stage 7: 全栈交付、部署与产品化

目标:

- 把前面的 Agent 能力整合成真正可交付的全栈系统
- 理解从开发、测试、部署、观测到迭代的完整链条
- 学会让前端、后端、知识层、工具层和运行时协同工作

核心主题:

- Full-stack agent architecture
- 后端 API 与 Agent Server
- 前后端通信模式
- 流式输出与任务状态同步
- Deployment
- Observability
- Evaluation
- 权限、审计与产品化边界
- 框架选型与迁移思维

建议项目:

- 研究控制台产品化版本
- 企业审批助手全栈版
- 多工具工作台 Agent

## Stage 8: 毕业项目与掌握闭环

目标:

- 独立设计一个完整 Agent 产品
- 同时覆盖后端、知识层、前端、交互、评测、部署和迭代

候选方向:

- 深度研究助手
- 销售支持 Agent
- 学习教练 Agent
- 创作者内容工作台
- 企业内部流程自动化助手
- 个人操作系统型 Agent

毕业要求:

- 能在 AI Agent 协作下完成一个从后端到前端的完整项目
- 能解释其架构、状态、知识、工具、交互、评测和部署设计
- 能进行一次完整复盘并规划后续迭代

## 官方文档锚点

- LangChain: 更适合快速构建高层 Agent
- LangGraph: 核心优势是 durable execution、streaming、human-in-the-loop、memory
- Deep Agents: 是当前官方推荐的复杂任务入门路径之一

参考:

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [LangChain frontend human-in-the-loop](https://docs.langchain.com/oss/python/langchain/frontend/human-in-the-loop)
- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
