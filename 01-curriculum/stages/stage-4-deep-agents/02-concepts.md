# 02 Concepts

## 1. Deep Agents 在新版架构中的位置

根据官方 overview，Deep Agents 是构建复杂 Agent 的高层入口之一，强调复杂任务处理、规划、context engineering 和更强的任务完成能力。

参考:

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [When to use the Deep Agents SDK](https://docs.langchain.com/oss/python/concepts/products#when-to-use-the-deep-agents-sdk)

## 2. Deep Agents 解决的不是“普通任务更快做”

它更适合:

- 目标复杂
- 任务长
- 信息层级多
- 需要拆子任务
- 需要对子任务结果进行汇总与迭代

如果任务很简单，直接上 Deep Agents 反而可能过度设计。

## 3. 什么是 planning

复杂任务里，规划不只是列出步骤，而是:

- 理解目标
- 组织阶段
- 决定顺序
- 在执行中修正路径

重点在于:

- 规划服务任务完成
- 不是为了让系统“看起来更聪明”

## 4. 什么是 context engineering

官方文档强调 context engineering 是为模型提供合适上下文的工程，而不是简单“多给点资料”。

它的关键在于:

- 给对的信息
- 在对的时间给
- 给到对的角色

这通常意味着:

- 长期资料和短期状态分层
- 子任务上下文隔离
- 汇总上下文与执行上下文分开

参考:

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)

## 5. 什么是 subagents

子代理不是“多开几个 agent”这么简单。

它适合出现在:

- 子任务差异明显
- 需要不同角色视角
- 主代理不应该持有全部细节

子代理的价值是:

- 降低主代理负担
- 提高任务分解清晰度
- 让复杂任务更可组织

## 6. Deep Agents 与 Human-in-the-loop

官方文档也明确提到，Deep Agents 支持 human-in-the-loop，并通过 LangGraph 的 interrupt 能力实现。

这说明复杂任务并不意味着完全自动化，反而更需要关键审批点。

参考:

- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)

## 7. 自定义与边界

官方 customization 文档说明 Deep Agents 可以配置其核心行为。

课程里的重点不是 API 参数，而是理解:

- 什么能力应该交给主代理
- 什么能力应该拆给子代理
- 什么上下文应该被隔离
- 什么地方必须留给人类确认

参考:

- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

## 8. Stage 4 最重要的结论

复杂任务型 Agent 的难点，不只是“流程复杂”，更是目标拆解、上下文组织、角色分工和治理设计。
