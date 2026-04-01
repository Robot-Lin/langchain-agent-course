# 跟学项目: 单工具研究助理

## 所属阶段
Stage 2: LangChain Builder

## 项目目标

设计一个单工具研究助理，接收研究问题，调用一个查询工具，并输出结构化研究摘要。

## 对应知识点

LangChain 在新版架构中的位置、tool 最小化、structured output、middleware、高层 human-in-the-loop

对应阅读：

- [阶段概览](../../01-curriculum/stages/stage-2-langchain-builder/01-overview.md)
- [阶段概念](../../01-curriculum/stages/stage-2-langchain-builder/02-concepts.md)
- [阶段方法](../../01-curriculum/stages/stage-2-langchain-builder/03-methods.md)
- [阶段案例对照](../../01-curriculum/stages/stage-2-langchain-builder/09-case-comparisons.md)

## 最终交付物

- 一份项目目标与边界说明
- 一份知识点到功能的映射表
- 一份功能到文件或模块的映射表
- 一份关键逻辑解释
- 一份用户审核清单

## 这份项目要重点看懂什么代码

- agent 入口函数、tool 定义、structured output schema、middleware 决策点、问题澄清逻辑
- 哪段逻辑在处理输入
- 哪段逻辑在处理状态、工具、检索、审批或展示
- 哪段逻辑在决定系统下一步怎么走

## 推荐带学步骤

1. 先用自然语言说清这个项目解决什么问题，不急着写代码。
2. 把本项目对应的知识点逐条列出来，并说明它们会落到哪些功能上。
3. 再让 Codex 带你把功能映射到文件、模块、函数、节点或组件。
4. 每做完一步，都要求 Codex 解释新增代码分别实现了什么。
5. 在进入下一步前，先由你自己复述这一小步的代码逻辑。
6. 最后再整理成一条完整主路径，说明输入如何一步步变成输出。

## 推荐给 Codex 的说法

- 先根据这一阶段的知识文件带我做项目，不要一上来直接给完整实现。
- 每一步先解释知识点，再解释这些知识点会落到哪些代码上。
- 每一步结束后，带我做一次代码导读，告诉我哪个功能对应哪个文件或函数。
- 如果我没讲清楚代码逻辑，不要直接进入下一步。

## 阶段检查点

- 能说清这个项目的主任务和边界
- 能指出至少 3 个关键文件、模块或逻辑块
- 能解释至少 2 段关键实现逻辑
- 能说明如果要审核这份代码，自己会重点看哪里
