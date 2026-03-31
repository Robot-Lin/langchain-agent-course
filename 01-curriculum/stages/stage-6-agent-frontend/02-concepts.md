# 02 Concepts

## 1. Agent UX 不等于聊天 UX

普通聊天界面的核心是消息往返，而 Agent 产品界面的重点通常还包括：

- 任务阶段
- 计划可见性
- 工具执行状态
- 审批节点
- 结构化结果
- 历史与来源感
- 失败与恢复反馈

如果这些都被压进一条消息流里，用户很快就会失去方向感。

## 2. Structured output 在前端中的价值

官方前端文档强调 structured output 不只是为了后端消费，它也让前端可以更稳定地渲染结果。课程里最关键的理解是：

- 结果可以变成卡片、表格、摘要区和下一步区。
- 用户能更快区分结论、依据、不确定点和建议动作。
- 前端可以少依赖“猜文本结构”来做界面。

参考：

- [Frontend structured output](https://docs.langchain.com/oss/python/langchain/frontend/structured-output)
- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)

## 3. Human-in-the-loop 在前端中的价值

human-in-the-loop 如果只停留在后端 interrupt，用户体验是不完整的。真正的产品体验还需要：

- 审批前预览动作
- 审批原因说明
- 明确的批准 / 拒绝 / 修改入口
- 审批后结果反馈

课程里最关键的理解是：审批不是一个技术事件，而是一个需要被界面承接的产品时刻。

参考：

- [Frontend human-in-the-loop](https://docs.langchain.com/oss/python/langchain/frontend/human-in-the-loop)
- [Human-in-the-loop middleware](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)

## 4. Streaming 的产品意义

streaming 不只是“字一个个冒出来”。在 Agent 系统里，streaming 可以承载：

- 当前阶段更新
- 工具执行反馈
- 中间结果回显
- 子任务进度
- 等待审批提示

也就是说，streaming 是“实时反馈系统状态”的能力，而不是纯视觉效果。

参考：

- [LangChain streaming](https://docs.langchain.com/oss/python/langchain/streaming)
- [LangGraph streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

## 5. 状态可视化

一个好的 Agent 前端，通常应该让用户看见：

- 当前任务处于哪个阶段
- 下一步大概是什么
- 是否卡在工具执行或人工审批
- 哪一步失败了
- 系统是否还能继续

状态可视化的价值不是“更炫”，而是增强控制感和信任感。

## 6. 历史、来源与记忆感

当 Agent 具备 memory、RAG、tools 和复杂工作流后，前端必须帮助用户理解：

- 当前结果来自哪里
- 哪部分是历史上下文
- 哪部分是实时检索
- 哪部分是系统执行动作后的结果

如果来源感缺失，用户就很难判断是否应该信任这个结果。

## 7. Agent Chat UI 与多面板界面

官方文档给出了 Agent Chat UI 的方向，但课程里还要进一步理解边界：

- 对简单任务，增强版 chat UI 可能够用。
- 对复杂任务，多面板界面通常更合适。

常见面板可能包括：

- 输入区
- 对话区
- 计划区
- 工具状态区
- 审批区
- 结果区
- 历史区

参考：

- [Agent Chat UI](https://docs.langchain.com/oss/python/langchain/ui#agent-chat-ui)

## 8. Stage 6 的结论

Agent 前端的本质，不是把后端结果显示出来，而是把系统的行动、状态、风险和可控性翻译成人真正能理解和使用的体验。
