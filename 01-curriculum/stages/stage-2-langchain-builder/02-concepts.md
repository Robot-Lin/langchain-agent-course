# 02 Concepts

## 1. LangChain 在新版架构中的位置

根据官方 overview，LangChain 是构建 agents 的高层入口，强调更快做出可用 Agent，同时它的 agents 建立在 LangGraph 之上。

这意味着:

- 你可以先从高层抽象开始
- 但它背后并不是“没有 runtime”，而是 LangGraph 在承担底层执行能力

参考:

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [Agent runtimes like LangGraph](https://docs.langchain.com/oss/python/concepts/products#agent-runtimes-like-langgraph)

## 2. 什么是高层 Agent 原型

在本课程里，高层 Agent 原型指的是:

- 已经具备任务目标
- 已经接入必要工具
- 已经有清晰输出格式
- 已经能处理主路径
- 已经能做基础失败控制

但它通常还没有:

- 复杂状态机
- 多分支长流程
- 可恢复中断系统
- 复杂多代理编排

## 3. Tools 与 toolkits

LangChain 的核心价值之一，是把外部能力以工具形式纳入统一调用入口。

重点不在于“接了多少工具”，而在于:

- 工具边界是否清楚
- 工具输入输出是否稳定
- 工具是否真的必要

这一阶段最应该学会的是:

- 让工具服务任务
- 而不是让任务为了展示工具而存在

## 4. Structured output

官方文档强调 structured output 可以让 Agent 输出可解析、可消费、可进入后续系统的结果。

它的重要性在于:

- 输出不再只是给人看
- 输出还能给程序、数据库、前端和后续步骤使用
- 结构化输出能显著减少“看起来答得不错，但系统没法接”的问题

参考:

- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)

## 5. Middleware

Middleware 是高层 Agent 中非常关键的一层。

它适合放置:

- 人工审核
- 守护逻辑
- 特定规则
- 风险控制

它的意义是:

- 不把所有行为都塞进 prompt
- 让系统控制逻辑更清楚

参考:

- [Middleware integrations](https://docs.langchain.com/oss/python/integrations/middleware/index)

## 6. Human-in-the-loop at high level

新版 LangChain 官方文档明确把 human-in-the-loop 作为 middleware 能力之一。

这说明高层 Agent 也可以在不下沉到底层图编排时，先把审核和批准机制接进去。

适合场景:

- 敏感工具调用
- 对外发送
- 关键数据修改

参考:

- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)

## 7. LangChain 与 RAG 的关系

LangChain 不只适合做纯工具型 Agent，也很适合做高层 RAG Agent 原型。

这一阶段的重点不是把 RAG 做复杂，而是先理解:

- 检索能力如何被纳入 Agent
- 为什么知识接入会改变 Agent 的回答边界

参考:

- [Build a RAG agent with LangChain](https://docs.langchain.com/oss/python/langchain/rag)

## 8. Stage 2 最重要的结论

LangChain 不是“少写点代码的 API 包装器”，而是一个帮助你快速搭起高层 Agent 结构的框架。

这一阶段真正要学会的是:

- 如何合理利用高层抽象
- 如何在不过度复杂化的前提下做出实用原型
- 如何知道什么时候该停止继续堆高层封装
