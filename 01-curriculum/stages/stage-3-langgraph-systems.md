# Stage 3: LangGraph Systems

## 阶段目标

- 从“调用 Agent”升级到“设计状态化系统”
- 学会用图表达分支、循环、恢复和审批
- 让 Agent 具备更稳定的执行能力

## 关联官方主线

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Durable execution](https://docs.langchain.com/oss/python/langgraph/durable-execution)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)
- [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

## 学习重点

- State 设计
- 节点与边
- 条件分支
- 循环与恢复
- Interrupts
- Human-in-the-loop

## 阅读知识

- 为什么复杂 Agent 需要图而不是链
- durable execution 的业务价值
- interrupt 如何支撑审批和人工接管

## 方法掌握

- 状态建模法:
  先列出状态对象
  再列出状态变化
  再列出触发条件
  最后设计人工介入点

- 图式设计法:
  从主路径开始
  再补错误分支
  再补审批与恢复

## 引导项目

- 带人工审批的采购 Agent
- 多阶段研究与汇总 Agent

## 主动练习

- 把一个 LangChain 原型重写成 LangGraph 设计图
- 指出新增了哪些状态和控制流能力

## 放行标准

- 能解释为什么这里必须用图
- 能设计一个含 interrupt 的工作流
- 能说明失败恢复策略

## 详细教学包

- [Stage 3 入口](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/README.md)
- [核心概念](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/02-concepts.md)
- [方法模板](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/03-methods.md)
- [引导项目](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/04-guided-project.md)
- [主动练习](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/05-challenges.md)
- [考核与复盘](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/06-review-checklist.md)
- [与 Codex 对练](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/07-codex-workshop.md)
