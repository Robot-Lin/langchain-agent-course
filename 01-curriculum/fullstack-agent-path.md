# 全栈 Agent 成长路径

本课程的最终目标不是“会用某个框架”，而是让学习者能在 AI Agent 的协助下完成一个从后端到前端的 Agent 项目。

## 最终目标画像

学习者在完成课程后，应具备以下能力:

- 能定义一个真实用户场景
- 能选择 LangChain、LangGraph 或 Deep Agents 的合适层级
- 能设计知识层、工具层、状态层和交互层
- 能把后端 Agent 系统与前端体验连接起来
- 能完成部署、观测、评测和迭代

## 全栈能力拆解

### 后端层

- 模型接入
- Agent runtime
- 工具接入
- MCP
- RAG
- 数据存储
- API 与服务边界

### 中台与治理层

- 记忆
- 权限与审批
- Observability
- Evaluation
- 日志、审计、失败恢复

### 前端层

- 聊天与任务界面
- 流式输出
- 工具状态与任务计划展示
- 审批交互
- 历史记录
- 用户反馈与解释性

## 各 Stage 如何指向全栈目标

- Stage 1: 建立系统视角
- Stage 2: 先把高层 Agent 做出来
- Stage 3: 学会设计稳定工作流和状态机
- Stage 4: 学会处理复杂任务和多代理
- Stage 5: 接上知识、工具、数据与治理
- Stage 6: 让 Agent 变成真正可用的前端产品
- Stage 7: 做全栈整合、部署、评测和产品化
- Stage 8: 完成一个完整毕业项目

## 官方文档主线支撑

- LangChain 负责高层 Agent 入口
- LangGraph 负责 durable execution、streaming、memory、interrupts
- Deep Agents 负责复杂任务型 Agent 能力
- LangSmith 负责部署、观测、评测等工程闭环

参考:

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
