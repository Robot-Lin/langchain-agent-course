# 02 Concepts

## 1. LangGraph 在新版架构中的位置

根据官方 overview，LangGraph 是用于构建 stateful、long-running agent systems 的底层编排框架，重点在 durable execution、streaming、human-in-the-loop、memory 和 production-ready control。

参考:

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)

## 2. 为什么需要图

链式思维适合主路径很清晰的任务。

但一旦系统开始出现:

- 分支
- 循环
- 失败重试
- 人工审批
- 长流程暂停与恢复

就更适合用图来表达。

图的价值不在“形式高级”，而在它能把控制流显式化。

## 3. 什么是 state

State 是图执行过程中的共享上下文和进度容器。

它通常包括:

- 当前任务阶段
- 已完成步骤
- 中间结果
- 用户确认状态
- 错误信息
- 审批结果

设计 state 的关键不是“多存一点”，而是只存真正影响后续路径的内容。

## 4. Durable execution

官方文档强调 durable execution 可以让系统在失败、暂停后继续执行，而不是从头来过。

它的实际意义是:

- 长任务不会因为一次中断彻底作废
- 审批后的恢复更自然
- 生产环境中的稳定性更强

参考:

- [Durable execution](https://docs.langchain.com/oss/python/langgraph/durable-execution)

## 5. Interrupts

官方文档将 interrupts 定义为暂停图执行的能力。

它特别适合:

- 等待人工审批
- 等待外部输入
- 暂停高风险动作

重要理解:

- interrupt 不是普通对话澄清
- 它是系统执行流程里的正式暂停点

参考:

- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)

## 6. Streaming

Streaming 在 LangGraph 里不仅是“边生成边显示”，还关系到:

- 用户是否知道系统正在做什么
- 前端是否能同步任务进展
- 长任务是否能维持可见反馈

参考:

- [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

## 7. Human-in-the-loop 与 LangGraph

高层 LangChain 可以先做基础 HITL，但真正复杂的审批、暂停、恢复，通常会落到 LangGraph 的 interrupt 与 persistence 能力上。

这意味着:

- 人工介入不只是“问一下用户”
- 而是运行时设计的一部分

## 8. LangGraph 与记忆

官方 memory 文档也明确指出，短期 memory 与运行时状态管理和 LangGraph 有紧密关系。

这说明:

- state 不是可有可无的补丁
- 而是复杂 Agent 系统的基础能力

参考:

- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)

## 9. Stage 3 最重要的结论

当你开始需要设计任务阶段、分支、审批、恢复和可见进度时，你已经不只是在做“一个会调用模型的原型”，而是在设计一个运行中的系统。
