# 02 Concepts

## 1. 全栈 Agent 交付到底是什么

课程里的“全栈交付”不是简单指前端加后端，而是指这些层形成可运行产品：

- 用户界面
- 前后端通信
- Agent runtime
- 知识与数据层
- 实时反馈链路
- 观测与评测层
- 部署与运行层

只有这些层真正闭环，系统才从工程方案进入产品交付。

## 2. Agent Server 的角色

官方文档把 Agent Server 描述成面向 Agent 应用的运行与 API 入口。课程里最关键的理解是：

- 它不是普通业务 API 的替代品。
- 它更像 Agent 系统的交付入口和运行边界。
- 它把运行中的 Agent 能力暴露给前端和外部系统。

参考：

- [Agent Server](https://docs.langchain.com/langsmith/agent-server)
- [Agent Server API reference](https://docs.langchain.com/langsmith/server-api-ref)

## 3. Deployment 的意义

官方的 deployment 文档强调的不是“把代码发出去”这么简单，而是运行、管理、扩展和维护 Agent 产品。课程里最关键的理解是：

- deployment 不是最后一步，而是产品生命周期的一部分。
- 交付方案会直接影响系统是否稳定、是否可维护、是否可扩展。

参考：

- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [LangChain deploy](https://docs.langchain.com/oss/python/langchain/deploy)

## 4. Streaming integration

全栈 Agent 产品的前端不该被动等待最终结果。Streaming integration 的意义是：

- 前端和运行中的 Agent 持续同步。
- 前端能展示中间状态、阶段更新和等待点。
- 产品体验和运行状态真正连接起来。

参考：

- [Streaming API](https://docs.langchain.com/langsmith/streaming)
- [LangGraph streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

## 5. Observability 与 Evaluation 在交付中的位置

到了全栈交付层，observability 和 evaluation 已经不再是“研发内部工具”，而是产品可靠性的组成部分。你需要知道：

- 系统是否正常运行
- 哪条路径最容易失败
- 用户真实体验是否稳定
- 某次更新是否让质量变差

参考：

- [LangSmith Observability](https://docs.langchain.com/langsmith/observability)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
- [Evaluation types](https://docs.langchain.com/langsmith/evaluation-types)

## 6. 交付验收不等于功能列表

很多项目把“有这些功能”当成“可以交付”，这是错误的。交付验收更应关注：

- 链路是否完整
- 结果是否可理解
- 状态是否可追踪
- 故障是否可定位
- 版本是否可迭代

## 7. 框架选型与迁移

到了这一章，学习者必须开始明确：

- 为什么当前产品适合 LangChain、LangGraph 或 Deep Agents 中的哪一层。
- 是否还需要其他前端或服务层框架来完成产品化。
- 未来如果用户规模、团队规模或业务复杂度变化，架构应该怎么调整。

## 8. Stage 7 的结论

全栈 Agent 交付的核心，不是把不同部分拼在一起，而是让它们形成一个可以持续运行、被用户理解、被团队维护、被产品迭代的完整闭环。
