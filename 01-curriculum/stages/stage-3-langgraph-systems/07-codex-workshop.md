# 07 Codex Workshop

这一部分是给学习者在 Stage 3 直接拿来用的 Codex 对练脚本。

## 模式一: 图式思维讲解

可以对 Codex 说:

- 用一个真实场景解释为什么这个需求应该用 LangGraph
- 解释 state、interrupt、durable execution 各自解决什么问题
- 用高层原型和图式系统对比同一个任务

## 模式二: 工作流拆解陪练

可以对 Codex 说:

- 帮我把这个任务拆成 LangGraph 工作流
- 先画主路径，再补分支，再补审批和恢复
- 每一步都说明对应的是哪个 Stage 3 知识点

## 模式三: State 评审

可以对 Codex 说:

- 帮我检查这个 state 设计是不是过重或过轻
- 哪些字段真正影响后续路径，哪些字段只是噪音

## 模式四: Interrupt 设计评审

可以对 Codex 说:

- 站在风险控制角度，指出我应该在哪些节点设置 interrupt
- 如果不设置这些中断，会发生什么

## 模式五: 课后项目导师模式

可以对 Codex 说:

- 我现在做 Stage 3 课后项目，请不要直接给我完整答案
- 先检查我的工作流图、state、interrupt 和恢复策略
- 最后按验收标准帮我评分

## 推荐学习动作

1. 先把 Stage 2 原型升级成图
2. 再定义 state
3. 再设计 interrupt 与恢复
4. 最后让 Codex 评审是否真的需要 LangGraph
