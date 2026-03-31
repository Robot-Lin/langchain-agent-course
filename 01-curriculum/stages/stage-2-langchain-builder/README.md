# Stage 2 教学包

`Stage 2` 是整套课程第一次真正进入框架实践的阶段。它承接 `Stage 1` 的系统判断，把学习者从“知道一个 Agent 该怎么想”推进到“知道一个高层 Agent 原型该怎么搭”。

这一阶段聚焦的不是复杂编排，而是如何借助 `LangChain` 的高层抽象，更快、更稳地把一个合理的 Agent 设计推进成可演示、可验证、可迭代的原型。

## 这一阶段的目标

完成这一阶段后，学习者应该能做到:

- 理解 `LangChain` 在新版架构中的位置
- 用 `LangChain` 设计一个高层 Agent 原型
- 说清 `tools`、`structured output`、`middleware`、`short-term memory`、`human-in-the-loop` 在高层 Agent 中分别解决什么问题
- 判断哪些需求继续留在 `LangChain` 高层就够了
- 判断什么时候一个项目已经开始逼近 `LangGraph` 的边界

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
10. [Stage 2 配套项目](../../../03-projects/stage-2/README.md)

## 本阶段最核心的 6 个问题

- `LangChain` 在新版体系里到底帮我们抽象了什么
- 什么叫“高层 Agent 原型”
- 为什么 `structured output` 在这一阶段特别重要
- 为什么 `middleware` 能把控制逻辑从 prompt 里剥出来
- `short-term memory` 在高层原型里什么时候值得接入
- 什么情况下继续留在 `LangChain` 是合理的，什么情况下应该准备转向 `LangGraph`

## 这一阶段的学习产物

学完以后，学习者手里应该至少有这些可见产物:

- 一份 LangChain 高层 Agent 原型说明
- 一份最小工具清单
- 一份 structured output 设计草案
- 一份 middleware / 控制逻辑说明
- 一份“为什么现在还适合留在 LangChain”的边界说明

## 对后续阶段的作用

这一章训练的不是“会不会调用 API”，而是后面进入 `LangGraph` 之前必须具备的高层工程意识:

- 组件化思维
- 高层原型设计能力
- 输出结构意识
- 工具边界意识
- 从原型到系统的升级判断能力

如果你准备正式开始学习，优先打开 [01-overview.md](./01-overview.md)；如果你准备按节奏带学，优先打开 [08-session-roadmap.md](./08-session-roadmap.md)。
