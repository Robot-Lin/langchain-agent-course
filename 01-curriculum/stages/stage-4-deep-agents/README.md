# Stage 4 教学包

`Stage 4` 是课程里从“可控工作流”进入“复杂任务型 Agent”设计的关键单元。它承接 `Stage 3`，把学习者从“会设计图系统”推进到“会组织复杂任务本身”。

如果说 `Stage 3` 解决的是“流程怎么显式控制”，那 `Stage 4` 解决的是:

> 当目标本身就复杂、任务本身就很长、上下文本身就很多时，怎样把它组织成一个可执行、可治理、可修正的 Agent 系统。

## 这一阶段的目标

完成这一阶段后，学习者应该能做到:

- 理解 `Deep Agents` 在新版架构中的位置
- 判断什么任务适合使用 `Deep Agents`，什么任务并不适合
- 理解 planning、context engineering、subagents、human-in-the-loop 和复杂任务治理之间的关系
- 把一个复杂目标拆成阶段、角色、上下文层次和汇总机制
- 说明为什么当前任务更适合 `Deep Agents`，而不是普通 LangGraph 工作流

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
10. [Stage 4 配套项目](../../../03-projects/stage-4/README.md)

## 本阶段最核心的 6 个问题

- 什么任务已经超出普通工作流的舒适区
- planning 为什么不是“多想几步”这么简单
- context engineering 为什么不是“塞更多上下文”
- subagents 什么时候必要，什么时候只是制造复杂度
- 复杂任务型 Agent 如何避免慢慢失控
- 为什么这里更适合 Deep Agents，而不是继续强化一个普通 LangGraph 图

## 这一阶段的学习产物

学完以后，学习者手里应该至少有这些可见产物:

- 一份复杂目标拆解图
- 一份 context 分层设计说明
- 一份 subagent 角色分工说明
- 一份汇总与回收机制说明
- 一份复杂任务治理与审核点清单
- 一份“为什么这里更适合 Deep Agents”的边界说明

## 对后续阶段的作用

这一章训练的不是“术语理解”，而是后面进入工程化系统、前端体验和全栈交付前必须具备的复杂任务设计能力:

- 复杂目标拆解能力
- 上下文组织能力
- 角色分工能力
- 复杂任务治理意识
- 面向开放目标的 Agent 设计能力

如果你准备正式开始学习，优先打开 [01-overview.md](./01-overview.md)；如果你准备按节奏带学，优先打开 [08-session-roadmap.md](./08-session-roadmap.md)。
