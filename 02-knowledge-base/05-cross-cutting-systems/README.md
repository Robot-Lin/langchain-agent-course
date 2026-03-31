# Cross-cutting Systems

这一层是把 Agent 从概念项目升级为真实系统的关键。

## 课程会覆盖的横向能力

- Tools
- Structured output
- Memory
- MCP
- RAG
- 数据库与存储
- 后端 API
- 观测与评测
- Guardrails
- Skill 化能力封装

## 每个主题解决什么问题

- Tools: 让 Agent 能行动，而不是只会回答
- Structured output: 让输出可消费、可验证、可进入后续系统
- Memory: 让系统具备跨轮和跨任务的连续性
- MCP: 让 Agent 能以标准协议接入外部工具和上下文能力
- RAG: 让 Agent 在受控知识范围内工作
- 数据库与存储: 让状态、知识、用户数据有可靠落点
- 后端 API: 让 Agent 真正接入业务系统
- 观测与评测: 让你知道 Agent 到底哪里好、哪里坏
- Guardrails: 让系统更安全、更可控
- Skill: 让高频能力被封装和复用

## 关键认知

- Agent 的价值不只来自模型，更来自系统连接能力
- MCP 和 RAG 都是“扩展上下文与能力”的方法，但它们解决的问题不同
- 数据层、权限层、观测层是 Agent 工程化的核心

## 相关官方入口

- [Model Context Protocol (MCP)](https://docs.langchain.com/oss/python/langchain/mcp)
- [Build a RAG agent with LangChain](https://docs.langchain.com/oss/python/langchain/rag)
- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)
