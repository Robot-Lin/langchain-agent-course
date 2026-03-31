# 02 Concepts

## 1. 全栈 Agent 交付到底是什么

课程里的“全栈交付”不是简单指前端加后端，而是指:

- 用户界面
- 前后端交互
- Agent runtime
- 数据与知识层
- 流式执行链路
- 评测与观测
- 部署与运行

这些必须一起构成可运行产品。

## 2. Agent Server 的角色

官方文档说明了 Agent Server 作为一种面向 Agent 应用的运行和 API 入口。

课程里的关键理解是:

- 它不是普通业务 API 的替代品
- 它更像 Agent 系统的交付入口与执行边界
- 它帮助把运行中的 Agent 能力暴露给外部系统和前端

参考:

- [Agent Server](https://docs.langchain.com/langsmith/agent-server)
- [Agent Server API reference](https://docs.langchain.com/langsmith/server-api-ref)

## 3. Deployment 的意义

官方文档中的 LangSmith Deployment 不只是“发布上线”，还包括:

- 运行时环境
- Agent Server
- durable execution
- 运行与管理能力

课程里的关键理解是:

- 部署不是最后一步，而是产品生命周期的一部分

参考:

- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [LangChain deploy](https://docs.langchain.com/oss/python/langchain/deploy)

## 4. Streaming integration

官方文档里 Streaming API 和 Agent Server 的关系说明了一个关键点:

- 前端不是被动等待结果
- 它需要和运行中的 Agent 持续同步

课程里的关键理解是:

- 全栈 Agent 产品要把实时执行链路接起来
- 流式能力会直接影响交付体验

参考:

- [Streaming API](https://docs.langchain.com/langsmith/streaming)

## 5. Observability 与 Evaluation 在交付中的位置

到了全栈交付层，observability 和 evaluation 已经不是“研发自用工具”，而是产品可靠性的组成部分。

你需要知道:

- 系统是否正常运行
- 哪些路径失败最多
- 用户实际效果是否稳定

## 6. 框架选型与迁移

这一阶段要开始明确:

- 为什么当前产品适合 LangChain / LangGraph / Deep Agents 的哪一层
- 是否需要引入其他前端或服务层框架
- 哪些地方未来可能迁移

交付阶段的选型，必须考虑:

- 团队复杂度
- 维护成本
- 用户体验要求
- 运行时需求

## 7. Stage 7 最重要的结论

全栈 Agent 交付的核心，不是把不同部分拼在一起，而是让它们形成一个可以持续运行、被用户理解、被团队维护、被产品迭代的完整闭环。
