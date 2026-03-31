# Stage 1 教学包

`Stage 1` 是整套课程的地基。这里不急着写代码，也不急着学框架，而是先训练一件更重要的事: 判断一个问题到底应不应该做成 Agent，以及应该做成什么样的 Agent。

如果这一阶段打不牢，后面的 `LangChain`、`LangGraph`、`Deep Agents` 很容易学成“会堆功能”，却不会做取舍，不会做边界设计，也不会设计能长期运行的系统。

## 这一阶段的目标

完成这一阶段后，学习者应该能做到:

- 说清 `Agent` 是系统设计问题，不只是提示词问题
- 判断一个需求是否真的需要 Agent，而不是普通应用逻辑
- 区分 `工具`、`状态`、`记忆`、`知识库`、`人工审批` 各自解决的问题
- 在不写代码的前提下，画出一个最小可行 Agent 的系统结构
- 识别一个 Agent 方案的失败路径、风险边界和人工接管点

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
10. [Stage 1 配套项目](../../../03-projects/stage-1/README.md)

## 本阶段最核心的 5 个问题

- `Agent` 和“会回答问题的聊天机器人”到底差在哪
- 什么情况下必须接工具，什么情况下根本不该加工具
- 什么信息应该做成状态，什么信息应该做成记忆，什么只是外部知识
- 什么动作一定要停下来给人看，而不能让系统自己执行
- 一个方案即使“演示能跑”，为什么仍然可能不适合上线

## 这一阶段的学习产物

学完以后，学习者手里应该至少有这些可见产物:

- 一份最小 Agent 设计画布
- 一份需求拆解表
- 一份失败路径清单
- 一份审批与人工介入说明
- 一段可以用自然语言解释清楚的系统架构描述

## 对后续阶段的作用

这一章训练的不是 API 熟练度，而是后面所有阶段都会反复使用的底层能力:

- 系统视角
- 边界意识
- 需求压缩能力
- 风险识别能力
- 最小可行设计能力

如果你准备正式开始学习，优先打开 [01-overview.md](./01-overview.md)；如果你准备带着用户上课，优先打开 [08-session-roadmap.md](./08-session-roadmap.md)。
