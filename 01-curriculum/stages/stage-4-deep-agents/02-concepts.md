# 02 Concepts

这一章的目标不是让你背 API，而是把 `Stage 4` 中最关键的复杂任务概念讲清楚。

## 1. Deep Agents 是什么

根据官方新版文档，`Deep Agents` 是一个面向复杂任务的高层入口，强调复杂任务处理、planning、context engineering 和更强的任务完成能力。

它适合的不是所有 Agent，而是那些真正具备下面特征的任务:

- 目标复杂
- 任务长
- 资料多
- 需要拆子任务
- 需要在执行中持续修正

对学习者来说，最重要的理解是:

> Deep Agents 解决的不是“普通任务做得更快”，而是“复杂任务怎样被组织得更清楚”。

参考:

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [When to use the Deep Agents SDK](https://docs.langchain.com/oss/python/concepts/products#when-to-use-the-deep-agents-sdk)

## 2. 什么任务开始适合 Deep Agents

如果任务具备下面这些特征，就开始更像 Deep Agents 场景:

- 目标开放而复杂
- 单一线性流程难以覆盖
- 子任务差异明显
- 需要多个角色视角
- 中间结果必须被汇总与回收
- 需要持续纠偏和治理

反过来，如果任务只是:

- 明确流程
- 固定阶段
- 中等复杂度审批与恢复

那么很多时候 `LangGraph` 已经足够，不一定需要 Deep Agents。

## 3. 什么是 planning

在复杂任务里，planning 不只是“列步骤”，而是:

- 理解目标
- 划分阶段
- 决定顺序
- 识别依赖
- 在执行中修正路径

所以 planning 的价值不在于“让系统看起来聪明”，而在于:

> 让复杂目标被分解成可管理的阶段性推进过程。

## 4. 什么是 context engineering

官方文档强调，context engineering 是为模型提供合适上下文的工程，而不是简单“多给点资料”。

这里最关键的是 3 件事:

- 给对的信息
- 在对的时机给
- 给到对的角色

这通常意味着:

- 长期资料和当前任务状态分层
- 子任务上下文隔离
- 汇总上下文与执行上下文分开

也就是说，context engineering 的核心不是“更多”，而是“更有组织”。

参考:

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)

## 5. 什么是 subagents

subagents 不只是“多开几个 agent”。

它们更适合出现于这些场景:

- 子任务天然独立
- 子任务需要不同视角或角色
- 子任务需要单独上下文
- 主代理不应该持有所有细节

subagents 的真正价值是:

- 降低主代理负担
- 提高任务分解清晰度
- 让复杂任务的组织结构更可控

如果一个子代理并没有带来上下文隔离、职责独立或复杂度降低，那它很可能只是“把复杂度重新命名”。

## 6. customization 与边界

官方 customization 文档说明了 Deep Agents 可以配置其核心行为。课程里的重点不是参数，而是判断:

- 什么能力应该交给主代理
- 什么能力应该拆给子代理
- 什么上下文应该被隔离
- 什么地方必须留给人类确认

这意味着，Deep Agents 的 customization 不是“调更多旋钮”，而是:

> 为复杂任务设计更清楚的任务组织边界。

参考:

- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

## 7. human-in-the-loop 在复杂任务里的意义

复杂任务并不意味着彻底自动化，很多时候反而更需要人类在关键阶段介入。

比如:

- 目标方向确认
- 关键中间结论审核
- 最终输出前纠偏
- 高风险外部动作确认

官方 Deep Agents 文档也明确说明，HITL 是通过 LangGraph 的 interrupt 能力支撑的。

这说明一个重要事实:

> 复杂任务越长、越开放、越难完全定义，就越需要正式治理点，而不是越应该放手让系统自己跑到底。

参考:

- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)

## 8. 复杂任务的真正难点不是工具，而是组织

很多学习者会误以为复杂任务主要难在:

- 工具多
- 数据多
- 步骤多

这些当然重要，但真正更难的通常是:

- 目标怎么拆
- 上下文怎么分层
- 子任务怎么分工
- 结果怎么回收
- 偏航怎么治理

也就是说，复杂任务型 Agent 的难点，常常不只是“流程复杂”，而是“任务组织本身复杂”。

## 9. 复杂任务为什么容易失控

复杂任务系统的风险往往不是单点失败，而是逐步偏航。

典型风险包括:

- 主目标被淡化
- 子任务各自做得很好，但整体跑偏
- 上下文越堆越乱
- 子代理边界不清，结果重复或冲突
- 汇总阶段把一堆零散内容拼在一起，无法收束

所以在 `Stage 4`，治理的意义非常重要。你不是只要“能拆”，还要“能收”。

## 10. Deep Agents 与 LangGraph 的关系

一个很容易误解的问题是: Deep Agents 是不是“替代”了 LangGraph。

不是。

更准确的理解是:

- LangGraph 解决运行时控制与流程编排
- Deep Agents 更强调复杂任务组织层

所以 `Stage 4` 不是在离开 LangGraph，而是在它之上进入更复杂的任务组织维度。

## 11. 什么时候不该用 Deep Agents

下面这些情况通常不必急着用 Deep Agents:

- 主任务很清楚
- 流程阶段明确但不复杂
- 没有明显子任务角色差异
- 控制流难度大于目标组织难度

这些情况下，`LangGraph` 或者更高层的 `LangChain` 往往已经足够。

## 12. 这一章真正想让你记住的话

进入 `Stage 5` 之前，先记住这句话:

> 复杂任务型 Agent 的难点，不只是流程更复杂，而是目标拆解、上下文组织、角色分工和治理设计都开始成为系统核心。
