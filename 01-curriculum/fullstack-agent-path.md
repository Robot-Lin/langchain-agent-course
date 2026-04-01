# 全栈 Agent 成长路径

这套课程的最终目标不是“会用某个框架”，而是让学习者能在 AI Agent 的协作下完成一个从后端到前端的 Agent 项目。

## 最终目标画像

学习者在完成课程后，应具备以下能力：

- 能定义一个真实用户场景
- 能在 `LangChain`、`LangGraph`、`Deep Agents` 之间做合理选型
- 能设计知识层、工具层、状态层、数据层和交互层
- 能把后端 Agent 系统与前端体验连接起来
- 能完成部署、观测、评测和后续迭代

## 全栈能力拆解

### 后端层

- 模型接入
- Agent runtime / orchestration
- 工具接入
- MCP
- RAG
- 数据存储
- API 与服务边界

### 中台与治理层

- 短期与长期 memory
- 权限与审批
- Observability
- Evaluation
- 日志、审计与失败恢复

### 前端层

- 聊天与任务界面
- 流式输出
- 工具状态与任务计划展示
- 审批交互
- 历史记录
- 用户反馈与解释能力

## 各 Stage 如何指向全栈目标

- `Stage 1`：建立系统视角与 Agent 心智模型
- `Stage 2`：用 LangChain 搭出高层 Agent 原型
- `Stage 3`：用 LangGraph 设计状态化、可恢复的运行时系统
- `Stage 4`：用 Deep Agents 组织复杂任务、规划与子代理
- `Stage 5`：接上知识、工具、数据、协议与治理
- `Stage 6`：把 Agent 变成真正可用的前端产品体验
- `Stage 7`：做全栈整合、部署、评测和产品化
- `Stage 8`：完成一个完整毕业项目

## 官方新版架构主线

这套路径建立在 LangChain 官方新版架构定义上：

- `LangChain` 负责高层 Agent 开发入口与高层原型装配
- `LangGraph` 负责底层 runtime / orchestration，包括 durable execution、streaming、interrupts、stateful control
- `Deep Agents` 负责复杂任务组织层，强调 planning、subagents、context engineering
- `LangSmith` 负责 deployment、observability、evaluation 等工程闭环

## 一句话理解三者关系

- 先用 `LangChain` 把高层原型搭出来
- 当运行时控制复杂度上升时，下潜到 `LangGraph`
- 当任务组织复杂度上升时，引入 `Deep Agents`

## 参考文档

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
