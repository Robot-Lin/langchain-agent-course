# Stage 4 教学包

这是 Stage 4 的课程入口。这一章的核心目标是：把学习者带入复杂任务型 Agent，学会阅读规划、上下文装配和子代理协作。

## 学完这一章之后应该做到什么

- 覆盖并理解这一章的核心能力：planning、context engineering、subagents、task decomposition、复杂任务治理
- 不只会描述架构，还能把知识点和实现方式连接起来
- 看懂这一章里最关键的一类代码或伪代码结构
- 在 AI 帮助下完成原型或方案后，能自己做审核判断

## 这一章要重点看懂什么代码

- 重点看懂 planner、task queue、subagent contract、context builder 和 review hooks。
- 用户至少要能指出哪个文件、模块或函数在负责哪个功能
- 用户至少要能讲清一条主路径是如何从输入走到输出的

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
10. [配套项目目录](../../../03-projects/stage-4/README.md)

## 这一章的代码学习要求

- 先说清知识点，再看知识点如何落到代码上
- 看代码时优先看主路径，不急着把所有细节一次看完
- 每完成一个小节，都要能用自然语言解释新增逻辑
- 不把 AI 已经写好了误当成自己已经掌握了

## 对项目学习的要求

- 用户应能解释为什么要拆子任务、上下文为何这样组装、子代理之间如何交接。
- 跟学项目里要做代码导读，课后项目里要做代码审核
- 最终不仅要交出结果，还要交出我看懂了什么代码的说明

## 本章在整套课程里的作用

能产出复杂任务拆解、上下文设计和子代理边界说明，并读懂主代理如何调度子代理。
