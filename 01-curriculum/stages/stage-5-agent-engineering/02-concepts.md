# 02 Concepts

## 1. 工程化层在课程里的位置

这一层不是额外附加题，而是 Agent 走向真实系统的必要部分。

没有这层，Agent 往往只能停留在:

- Demo
- 单机实验
- 只对单次输入有效的原型

## 2. 什么是 MCP

官方文档将 MCP 定义为一种开放协议，用于把外部工具和上下文能力以标准方式暴露给模型或 Agent。

课程里的关键理解是:

- MCP 不只是“又一种工具”
- 它是标准化接入外部能力的协议方式
- 它让 Agent 能更稳定地接入外部系统和能力源

参考:

- [Model Context Protocol (MCP)](https://docs.langchain.com/oss/python/langchain/mcp)

## 3. 什么是 RAG

RAG 是通过检索外部知识，让 Agent 在受控知识范围内回答或决策。

它解决的是:

- 模型知识过期
- 需要引用特定文档
- 需要在限定知识边界内工作

参考:

- [Build a RAG agent with LangChain](https://docs.langchain.com/oss/python/langchain/rag)

## 4. Memory、知识库、数据库的区别

这是本阶段最重要的边界问题之一。

- Memory: 系统保留与用户、任务、偏好相关的连续性信息
- 知识库: 供检索的外部资料和文档
- 数据库: 系统状态、业务数据、审计记录等可靠存储

如果三者混在一起，系统会很难治理。

参考:

- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)
- [Long-term memory](https://docs.langchain.com/oss/python/langchain/long-term-memory)

## 5. 后端 API 的角色

后端 API 是 Agent 与业务系统连接的主要边界之一。

它通常负责:

- 数据读写
- 业务动作触发
- 权限控制
- 与前端交互的数据通路

课程里的重点不是某一种框架，而是理解 API 作为系统边界的作用。

## 6. Observability

LangSmith 官方文档把 observability 放在调试、追踪和理解 Agent 运行过程的核心位置。

课程里的关键理解是:

- 你不能只看最终结果
- 你还要看中间步骤、工具调用、状态变化和失败路径

参考:

- [LangSmith Observability](https://docs.langchain.com/oss/python/langchain/observability)

## 7. Evaluation

LangSmith 官方文档明确区分不同评测方式，并强调评测应在上线前和运行中都持续发生。

课程里的关键理解是:

- Evaluation 不是“偶尔测一下”
- 它是持续验证系统质量的机制
- RAG、聊天、工作流都需要不同评测视角

参考:

- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
- [Evaluate a RAG application](https://docs.langchain.com/langsmith/evaluate-rag-tutorial)

## 8. 治理与权限

当 Agent 开始接工具、接业务系统、接知识和数据时，治理就变成一等公民。

课程里需要重点考虑:

- 谁能触发什么能力
- 哪些动作需要审批
- 哪些数据能被读取
- 哪些操作必须有日志与审计

## 9. Stage 5 最重要的结论

一个真正可用的 Agent 系统，不只是“会做任务”，还必须知道自己接了什么、存了什么、看了什么、做了什么，以及如何被验证和追踪。
