# LangChain

## 官方定位

根据官方 overview，LangChain 是构建 agents 的高层入口，强调快速上手、标准化组件和实用开发体验。官方同时明确，LangChain agents 建立在 LangGraph 之上。

参考:

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)

## 为什么先学 LangChain

- 它让你更快拥有一个可工作的高层 Agent
- 它很适合新手建立“组件化”的理解
- 它把模型、工具、结构化输出、middleware 等常见问题收拢得比较清晰

## 这部分的核心知识点

- Agent 的高层搭建方式
- Tools 与 toolkits
- Structured output
- Middleware
- 基础 human-in-the-loop
- RAG 风格的知识接入

## 适合用 LangChain 的场景

- 需要快速验证一个 Agent 想法
- 系统复杂度还不高
- 主要目标是先把产品能力跑通
- 希望先利用现成抽象，而不是自己编排底层状态机

## 学习时要避免的误区

- 把 LangChain 当成“几个 API 调用的集合”
- 看不到它与 LangGraph 的上下层关系
- 在其实需要图编排时，仍强行把复杂逻辑塞进高层封装

## 本课程会如何教这一部分

- 先讲高层抽象解决的问题
- 再讲典型 Agent 组件
- 再做 2 到 3 个适合新手的 LangChain 项目
- 最后再引出为什么需要 LangGraph
