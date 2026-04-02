# 04 Guided Project

本章的引导项目是 全栈研究控制台交付版。这一章的重点不是把项目做得最大，而是把本章知识点真实落到功能、文件、代码和审核判断上。

## 项目目标

把前端、后端、Agent runtime、观测和部署打成一条真实可交付的产品链路。

## 对应知识点

Agent Server、deployment、streaming integration、observability、evaluation、framework selection

## 知识点如何落到代码上

重点映射到这些实现层：

- frontend request flow、backend routes、agent runtime entry、streaming transport、trace hooks、deploy config
- 主路径输入如何进入系统
- 关键状态、关键判断或关键输出在哪里形成

## 推荐推进顺序

1. 先画全栈主路径
2. 再拆前端、后端、runtime 与观测层职责
3. 补部署与环境边界
4. 整理失败路径和恢复策略
5. 回头对照 [02-concepts.md](./02-concepts.md) 里的代码教材和 [03-methods.md](./03-methods.md) 里的 API 对照
6. 最后按 [10-full-project-reading.md](./10-full-project-reading.md) 扫完整个交付系统

## 本章必须完成的代码导读

做完项目设计或实现后，至少补做下面这轮读码：

- 先列出关键文件或关键模块
- 再说清它们各自负责什么
- 再解释一条主路径如何从输入走到输出
- 再补一张全项目组件与文件地图
- 最后指出如果你来审核，会优先看哪 2 到 3 个风险点

## 最终交付物

- 全栈主路径说明、部署方案、观测方案、关键调用链讲解
- 一份全项目组件与文件地图
- 一份主路径解释
- 一份用户审核要点清单

## 推荐给 Codex 的说法

- 请沿着一次真实请求，把前端、后端、runtime 和 trace 入口都带我读一遍。
- 不要只告诉我结果，先告诉我每个知识点落到了哪些文件和逻辑上。
- 如果我讲不清楚代码逻辑，不要直接进入下一步。

