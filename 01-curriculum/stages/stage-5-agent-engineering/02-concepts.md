# 02 Concepts

## 1. 工程化层不是“附加题”

很多新手会把工程化理解成“项目做完后再补的部分”。这在 Agent 场景里通常会出问题。
因为 Agent 一旦：

- 连接外部知识
- 调用外部工具
- 接触业务数据
- 对外执行动作

它就已经是一个系统问题，而不只是 prompt 问题。

## 2. 什么是 MCP

官方把 MCP 解释为一种开放协议，用标准方式把外部能力暴露给模型或 Agent。课程里最重要的理解不是“它是一种新工具”，而是：

- 它标准化了能力暴露方式。
- 它让 Agent 接入外部系统时更一致。
- 它让“工具接入”逐渐从临时拼装变成可复用接口。

参考：

- [Model Context Protocol (MCP)](https://docs.langchain.com/oss/python/langchain/mcp)

## 3. 什么是 RAG

RAG 不是“给模型更多上下文”这么简单。它真正解决的是：

- 模型知识过期。
- 回答必须基于受控资料。
- 回答需要引用外部文档而不是靠记忆猜测。

在工程视角下，RAG 是知识层，不是状态层，也不是业务数据层。

参考：

- [Build a RAG agent with LangChain](https://docs.langchain.com/oss/python/langchain/rag)

## 4. memory、知识库、数据库的区别

这是 Stage 5 最重要的边界之一。

### memory

memory 记录的是连续性。比如：

- 用户偏好
- 当前会话上下文
- 长期用户设定
- 某个任务中需要记住的中间事实

参考：

- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)
- [Long-term memory](https://docs.langchain.com/oss/python/langchain/long-term-memory)

### 知识库

知识库用于检索外部资料。它服务的是“查找与引用”，比如：

- 公司制度文档
- 产品文档
- 研究资料
- 常见问题手册

### 数据库

数据库承载的是业务真相和系统状态，比如：

- 订单
- 客户记录
- 工单状态
- 审批日志
- 执行记录

如果把这三者混为一谈，系统就会出现边界模糊、治理困难、追责困难的问题。

## 5. 后端 API 的角色

后端 API 不只是让前端拿数据，它还是 Agent 与业务系统之间的重要边界。

它通常负责：

- 暴露受控业务能力。
- 屏蔽底层服务复杂度。
- 统一权限和审计。
- 把 Agent 的动作转成可管理的系统调用。

课程里要学的重点不是某个框架，而是 API 作为边界层的责任。

## 6. Observability

Agent 的可观测性不是“看最终回答好不好”，而是看：

- 中间步骤是什么。
- 调用了哪些工具。
- 哪一步检索失败了。
- 哪一步 reasoning 或状态更新偏掉了。
- 哪个环节导致了错误输出。

参考：

- [LangSmith Observability](https://docs.langchain.com/oss/python/langchain/observability)
- [Tracing quickstart](https://docs.langchain.com/langsmith/observability-quickstart)

## 7. Evaluation

官方把 evaluation 拆成明确的持续流程，而不是一次性的测试动作。课程里最关键的理解是：

- Evaluation 要覆盖上线前和运行中。
- 不同类型的 Agent 要有不同指标。
- RAG、聊天、工作流、动作型 agent 的评测目标不同。

参考：

- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
- [Evaluation types](https://docs.langchain.com/langsmith/evaluation-types)
- [Evaluate a RAG application](https://docs.langchain.com/langsmith/evaluate-rag-tutorial)

## 8. Governance 与权限

只要 Agent 开始触碰真实系统，治理就不是可选项。你至少要回答：

- 谁可以触发哪些能力。
- 哪些动作需要确认或审批。
- 哪些数据可以读，哪些数据不能读。
- 哪些行为必须留下审计记录。

## 9. Stage 5 的结论

一个真正可用的 Agent 系统，不只是“回答得聪明”，而是它知道自己连了什么、查了什么、存了什么、做了什么，并且这些过程都能被追踪、评测和治理。
