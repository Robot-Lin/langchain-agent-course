# LangGraph

## 官方定位

根据官方 overview，LangGraph 是用于构建 stateful、long-running agent systems 的底层编排框架，强调 durable execution、streaming、human-in-the-loop、memory 和 production-ready control。

参考:

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)
- [Durable execution](https://docs.langchain.com/oss/python/langgraph/durable-execution)

## 为什么它是核心必修

- 真正复杂的 Agent，迟早会碰到状态、分支、恢复、中断和审批
- 只有理解 LangGraph，你才会真正理解“Agent 作为系统”是怎么被可靠地跑起来的
- 它是从 Demo 走向产品化的重要分水岭

## 这部分的核心知识点

- State 设计
- Graph 节点与边
- 条件分支和循环
- Durable execution
- Interrupts
- Human-in-the-loop
- Multi-agent orchestration

## 适合用 LangGraph 的场景

- 复杂长任务
- 需要人工审批
- 需要可恢复执行
- 多步骤工作流
- 多代理协作

## 新手在这里会发生的认知升级

- 从“一步一步调用模型”升级到“设计一个会演化的系统”
- 从“输出对不对”升级到“状态怎么流转、失败怎么恢复、人工如何介入”

## 本课程会如何教这一部分

- 先从图式心智模型入手
- 再讲 state 与 control flow
- 再做真实业务型项目，如审批流、研究流、执行流
