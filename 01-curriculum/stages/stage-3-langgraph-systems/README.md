# Stage 3 教学包

`Stage 3` 是整套课程里最重要的架构升级点之一。这里我们从“高层原型设计”正式进入“状态化系统设计”，学习者会第一次真正面对 `state`、`branching`、`interrupt`、`recovery`、`persistence` 和 `streaming` 这些运行时问题。

如果说 `Stage 2` 训练的是“怎么把一个合理设计推进成高层原型”，那 `Stage 3` 训练的就是:

> 当任务开始变长、变复杂、变有状态时，怎样把一个 Agent 从原型推进成可控、可恢复、可审核的系统。

## 这一阶段的目标

完成这一阶段后，学习者应该能做到:

- 理解 `LangGraph` 在新版架构中的角色
- 把一个复杂任务拆成图式工作流，而不只是高层封装
- 为工作流设计合理的 `state`
- 设计关键分支、interrupt、恢复路径和审批点
- 理解 `durable execution`、`persistence`、`streaming` 在真实业务里的意义
- 判断为什么当前项目必须使用 `LangGraph`，而不应继续硬塞在 `LangChain` 高层

## 建议学习顺序

1. [01-overview.md](./01-overview.md)
2. [02-concepts.md](./02-concepts.md)
3. [09-case-comparisons.md](./09-case-comparisons.md)
4. [03-methods.md](./03-methods.md)
5. [08-session-roadmap.md](./08-session-roadmap.md)
6. [04-guided-project.md](./04-guided-project.md)
7. [05-challenges.md](./05-challenges.md)
8. [06-review-checklist.md](./06-review-checklist.md)
9. [07-codex-workshop.md](./07-codex-workshop.md)
10. [Stage 3 配套项目](../../../03-projects/stage-3/README.md)

## 本阶段最核心的 6 个问题

- 为什么高层原型在这里开始不够用了
- `state` 到底应该保存什么，而不该保存什么
- `interrupt` 为什么不是普通澄清，而是正式的运行时暂停点
- `durable execution` 和 `persistence` 真正解决了什么问题
- `streaming` 为什么不只是“UI 更酷”，而是系统反馈能力的一部分
- 什么样的任务结构说明你已经进入 LangGraph 的世界，而不是 LangChain 高层原型

## 这一阶段的学习产物

学完以后，学习者手里应该至少有这些可见产物:

- 一张 LangGraph 工作流图
- 一份 state 字段设计说明
- 一份 interrupt 设计说明
- 一份恢复路径说明
- 一份“为什么这里必须使用 LangGraph”的边界说明
- 一份阶段化失败路径清单

## 对后续阶段的作用

这一章训练的不是“会画图”，而是后面进入 Deep Agents、工程化系统与全栈 Agent 产品所必须具备的中层系统能力:

- 图式思维
- 状态建模能力
- 流程编排意识
- 审批与恢复设计能力
- 面向真实任务的可控性意识

如果你准备正式开始学习，优先打开 [01-overview.md](./01-overview.md)；如果你准备按节奏带学，优先打开 [08-session-roadmap.md](./08-session-roadmap.md)。
