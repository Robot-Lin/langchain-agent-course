# Stage 7 教学包

这是 Stage 7 的课程入口。这一章的核心目标是：把前后端、运行时、观测和部署打通，学会看懂全栈 Agent 产品的真实主路径。

## 学完这一章之后应该做到什么

- 覆盖并理解这一章的核心能力：Agent Server、deployment、streaming integration、observability、evaluation、framework selection
- 不只会描述架构，还能把知识点和实现方式连接起来
- 看懂这一章里最关键的一类代码或伪代码结构
- 在 AI 帮助下完成原型或方案后，能自己做审核判断

## 这一章要重点看懂什么代码

- 重点看懂前后端边界、server routes、streaming 通道、trace 上报、环境配置和部署入口。
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
10. [配套项目目录](../../../03-projects/stage-7/README.md)

## 这一章的代码学习要求

- 先说清知识点，再看知识点如何落到代码上
- 看代码时优先看主路径，不急着把所有细节一次看完
- 每完成一个小节，都要能用自然语言解释新增逻辑
- 不把 AI 已经写好了误当成自己已经掌握了

## 对项目学习的要求

- 用户应能解释一个请求如何从前端进入后端，再进入 Agent runtime，并返回结果和观测数据。
- 跟学项目里要做代码导读，课后项目里要做代码审核
- 最终不仅要交出结果，还要交出我看懂了什么代码的说明

## 本章在整套课程里的作用

能产出全栈主路径说明、部署方案、观测方案，并能沿调用链讲解关键代码。
