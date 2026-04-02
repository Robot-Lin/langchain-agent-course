# Official Docs and LangSmith

这一节的作用，是把课程里的知识、教程、项目和官方 LangChain Docs 主线正式连起来。

## 为什么这部分要单独存在

这套课程不是只靠课程作者的解释来教学。

从现在开始，课程还会明确依赖两类官方来源：

- `LangChain Docs`
  作为框架能力、技术细节、代码实现方式的官方知识来源
- `LangSmith Docs`
  作为 observability、evaluation、deployment 等工程闭环能力的官方知识来源

## 这部分负责解决什么问题

- 某个知识点在官方文档里到底对应哪一页
- 某个技术能力在项目里应如何合理落地
- 某段代码或某个设计到底在用哪个框架能力
- LangSmith 在课程里到底放在哪一层

## LangSmith 在课程里的正式定位

在这套课程里，`LangSmith` 不再只是“顺带提一下的工具”，而是正式负责：

- tracing / observability
- evaluation
- deployment
- 作为工程闭环与调试反馈的一部分

它主要出现在：

- `Stage 5`
  作为工程化 Agent 系统的观测与评测能力
- `Stage 7`
  作为全栈交付、部署与追踪能力
- `Stage 8`
  作为毕业项目验证、复盘与演示支撑

## 官方文档锚点

### LangChain

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [Agents](https://docs.langchain.com/oss/python/langchain/agents)
- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)
- [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)
- [Model Context Protocol (MCP)](https://docs.langchain.com/oss/python/langchain/mcp)

### LangGraph

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Durable execution](https://docs.langchain.com/oss/python/langgraph/durable-execution)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)
- [Persistence](https://docs.langchain.com/oss/python/langgraph/persistence)
- [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

### Deep Agents

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)
- [When to use the Deep Agents SDK](https://docs.langchain.com/oss/python/concepts/products#when-to-use-the-deep-agents-sdk)

### LangSmith

- [LangSmith Observability](https://docs.langchain.com/langsmith/observability)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)

## 课程里的使用规则

从现在开始，课程内的知识讲解、教程和项目建议遵循下面的原则：

- 概念先在课程里讲清，再对到官方 Docs 页面
- 技术细节和代码细节尽量对到官方 Docs 锚点
- 做项目时，AI 应指出当前步骤对应哪个官方 Docs 页面
- 讲代码时，不只讲“这段代码做了什么”，还要讲“它在官方文档对应哪个能力”

## 你在学习时怎么用这一部分

- 如果你想确认一个框架能力的官方说法，从这里找入口
- 如果你想把某段代码对回框架能力，从这里找锚点
- 如果你想确认 LangSmith 在课程里应该出现在哪一层，也从这里回查
