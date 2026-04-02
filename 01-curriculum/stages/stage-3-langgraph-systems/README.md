# Stage 3 教学包

这是 Stage 3 的课程入口。这一章的核心目标是：从高层原型进入运行时图系统，学会把状态、节点、分支和恢复机制读明白。

## 学完这一章之后应该做到什么

- 覆盖并理解这一章的核心能力：state、branching、interrupt、durable execution、streaming、审批与恢复
- 不只会描述架构，还能把知识点和实现方式连接起来
- 看懂这一章里最关键的一类代码或伪代码结构
- 开始建立“整张图 + 整个项目”理解能力，而不是只停在几个节点
- 在 AI 帮助下完成原型或方案后，能自己做审核判断

## 这一章要重点看懂什么代码

- 重点看懂 state 定义、node 函数、路由条件、interrupt 位置、resume 逻辑和失败分支。
- 用户至少要能指出哪个文件、模块或函数在负责哪个功能
- 用户至少要能讲清一条主路径是如何从输入走到输出的
- 用户还要能逐步解释整张图如何被拆成多个文件、节点和运行时能力

## 建议学习顺序

1. [01-overview.md](./01-overview.md)
2. [02-concepts.md](./02-concepts.md)
3. [03-methods.md](./03-methods.md)
4. [09-case-comparisons.md](./09-case-comparisons.md)
5. [08-session-roadmap.md](./08-session-roadmap.md)
6. [04-guided-project.md](./04-guided-project.md)
7. [10-full-project-reading.md](./10-full-project-reading.md)
8. [05-challenges.md](./05-challenges.md)
9. [06-review-checklist.md](./06-review-checklist.md)
10. [07-codex-workshop.md](./07-codex-workshop.md)
11. [配套项目目录](../../../03-projects/stage-3/README.md)

## 这一章的代码学习要求

- 先说清知识点，再看知识点如何落到代码上
- 先读 `02-concepts.md` 后半部分的最小代码示例，再进入项目代码
- 看代码时优先看主路径，不急着把所有细节一次看完
- 每完成一个小节，都要能用自然语言解释新增逻辑
- 不把 AI 已经写好了误当成自己已经掌握了
- 在看懂主路径后，要继续做一次整图和全项目扫描

## 对项目学习的要求

- 用户应能解释为什么某条边存在、为什么某个字段必须进 state、为什么某处必须 interrupt。
- 跟学项目里要做代码导读，课后项目里要做代码审核
- 最终不仅要交出结果，还要交出我看懂了什么代码、哪些节点、哪些文件以及整张图如何被组织的说明

## 本章在整套课程里的作用

能产出工作流图、state 设计、恢复路径说明、全项目文件地图，并能读懂图执行对应的代码结构。
