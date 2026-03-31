# 02 Concepts

## 1. 为什么 Agent UX 不等于聊天 UX

普通聊天界面的重点是消息往返。

Agent 产品界面的重点还包括:

- 任务进度
- 工具状态
- 计划可见性
- 审批节点
- 历史与记忆
- 失败反馈

如果这些都隐藏在一条消息流里，用户会很快失去掌控感。

## 2. Structured output 在前端中的价值

官方前端文档强调 structured output 不只是给后端消费，它也能让前端以更稳定方式渲染结果。

这意味着:

- 结果可以变成卡片、表格、分区视图
- 用户可以清楚区分不同类型结果
- 系统更容易显示“结论、依据、不确定点、下一步”

参考:

- [Frontend structured output](https://docs.langchain.com/oss/python/langchain/frontend/structured-output)

## 3. Human-in-the-loop 在前端中的价值

官方前端文档强调 human-in-the-loop 的核心是让重要动作在用户批准后执行。

从前端角度看，这意味着:

- 需要审批面板
- 需要预览动作
- 需要继续或拒绝的入口

参考:

- [Frontend human-in-the-loop](https://docs.langchain.com/oss/python/langchain/frontend/human-in-the-loop)

## 4. Streaming 的产品意义

Streaming 不只是“字一个个冒出来”。

在 Agent 系统里，streaming 可以承载:

- 当前阶段更新
- 工具执行反馈
- 中间结果回显
- 长任务进度

参考:

- [LangChain streaming](https://docs.langchain.com/oss/python/langchain/streaming)
- [LangGraph streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

## 5. 状态可视化

一个好的 Agent 前端，通常应该让用户看到:

- 当前任务处于什么阶段
- 下一步大概是什么
- 有没有等待审批
- 哪一步失败了

这类可视化不是“好看”，而是控制感的来源。

## 6. 历史、记忆与来源感

当 Agent 具备 memory、RAG、工具和复杂流程后，前端必须帮助用户理解:

- 当前结果来自哪里
- 哪部分是历史上下文
- 哪部分是实时检索
- 哪部分是系统行动结果

## 7. Agent Chat UI 与多面板界面

官方 UI 文档说明了标准 Agent Chat UI 的方向，但课程里要再往前一步:

- 对简单任务，可以用增强版 chat
- 对复杂任务，更适合多面板结构

例如:

- 输入区
- 计划区
- 执行状态区
- 审批区
- 历史记录区

参考:

- [Agent Chat UI](https://docs.langchain.com/oss/python/langchain/ui#agent-chat-ui)

## 8. Stage 6 最重要的结论

一个 Agent 前端的本质，不是把后端结果显示出来，而是把系统的行动、状态、风险和可控性翻译成人真正能理解和使用的体验。
