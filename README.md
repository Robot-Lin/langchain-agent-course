# LangChain Agent Course

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
![Course Stages](https://img.shields.io/badge/Stages-1--8-blue)
![Project Mode](https://img.shields.io/badge/Learning-Project--Based-orange)
![Agent Stack](https://img.shields.io/badge/Stack-LangChain%20%7C%20LangGraph%20%7C%20Deep%20Agents%20%7C%20LangSmith-black)
![Build Status](https://img.shields.io/badge/Status-Code%20Reading%20Track%20Integrated-success)

一个面向 IDE + Codex 协作学习的完整 Agent 教学课程，围绕 `LangChain`、`LangGraph`、`Deep Agents`、`LangSmith` 展开，并系统覆盖 `MCP`、`RAG`、`Memory`、数据库、后端 API、前端 Agent UX、评测、观测、部署与毕业项目。

这套课程的目标不是只让学习者“调通一个 Agent”，而是让学习者在 AI Agent 的帮助下，从后端到前端构建一个功能完整、结构清晰、可评测、可迭代的 Agent 产品，并且看得懂它是如何被实现出来的。

## Why This Repo Exists

这套课程要解决的不是“如何快速跑一个 Demo”，而是下面这条完整学习链路：

- 判断一个需求是否真的需要 Agent
- 选择合适的框架层级
- 搭建可工作的 Agent 系统
- 补齐工具、知识、状态、评测和治理
- 做出真正可用的前端体验
- 交付一个从后端到前端闭环的 Agent 产品
- 学会看懂、解释和审核 AI 帮你写出来的代码

## Who This Course Is For

适合这样的学习者：

- 对 Agent 已经有基础了解
- 有一定提示词构建能力
- 能描述自己的需求、流程或产品想法
- 想在 IDE 中和 Codex 结对学习，而不是只看文档
- 希望最终做出一个可演示、可解释、可迭代的 Agent 项目

## What You Will Be Able To Do

完成这套课程后，学习者应该能：

- 判断一个问题是否真的需要 Agent
- 说清 `LangChain`、`LangGraph`、`Deep Agents` 的分工与边界
- 设计 Agent 的工具层、知识层、状态层、体验层、治理层和评测层
- 说明 `LangSmith` 在观测、评测、部署和工程闭环中的角色
- 在 AI Agent 协作下完成一个从后端到前端的 Agent 产品原型
- 看懂 Agent 项目里的关键代码、关键文件和关键逻辑
- 对 AI 写出的代码做审核判断，而不是只接受结果
- 从目录、文件、函数、调用链到框架能力，整体理解一个 Agent 项目
- 清楚解释自己的架构、交付路径、风险边界和下一步迭代方向

## Quick Start

如果你是第一次进入这个仓库，建议按下面顺序开始：

1. [Start Here](./00-start-here/README.md)
2. [Course Roadmap](./01-curriculum/course-roadmap.md)
3. [Learning Loop](./01-curriculum/learning-loop.md)
4. [Stages Index](./01-curriculum/stages/README.md)
5. [Stage 1 Course Pack](./01-curriculum/stages/stage-1-agent-foundations/README.md)

常用入口：

- [Project Teaching Protocol](./03-projects/ai-project-teaching-protocol.md)
- [Official Docs & LangSmith Knowledge Base](./02-knowledge-base/08-official-docs-and-langsmith/README.md)
- [Course Build Status](./COURSE_BUILD_STATUS.md)
- [Repository Roadmap](./ROADMAP.md)
- [Changelog](./CHANGELOG.md)

## Course Roadmap Snapshot

```text
Stage 1  Agent Foundations     -> 判断一个需求是否真的需要 Agent
Stage 2  LangChain Builder     -> 搭出高层 Agent 原型
Stage 3  LangGraph Systems     -> 设计状态、分支、审批与恢复
Stage 4  Deep Agents           -> 处理复杂任务、规划、子代理与上下文工程
Stage 5  Agent Engineering     -> 接入 MCP / RAG / Memory / DB / API / LangSmith Eval
Stage 6  Agent Frontend        -> 设计 Agent UX、Streaming、审批界面、状态可视化
Stage 7  Full-stack Delivery   -> 组装、部署、追踪、LangSmith 观测与交付
Stage 8  Capstone Mastery      -> 完成毕业项目、答辩、复盘与迁移
```

## Current Build Snapshot

当前已经完成：

- `Stage 1-8` 的教材级教学包
- 每个阶段的知识、方法、引导项目、主动练习、放行清单、Codex 对练、session 路线和案例对照
- 分阶段项目目录与 AI 项目教学协议
- 全栈 Agent 学习路径、阶段放行标准与 Rubric
- 官方 LangChain Docs 与 LangSmith 已纳入课程知识来源
- 仓库首页、课程总导航和高频入口校准
- 课程主设计里已明确加入“代码理解与审核”要求
- `Stage 1-8` 的项目、考核与对练都已经接入读码主线
- `Stage 2-8` 的主讲义已经开始内置代码教材、API 对照和全项目阅读入口
- 课程整体已统一到新版官方架构：
  `LangChain` 负责高层 Agent 开发，
  `LangGraph` 负责 runtime / orchestration，
  `Deep Agents` 负责复杂任务组织，
  `LangSmith` 负责 observability / evaluation / deployment

当前仍适合继续增强：

- 更细的 lesson 级讲义
- 更厚的知识库模块
- 可运行参考实现与前端原型
- 更完整的答辩模板、评审模板和毕业项目支撑材料

## How Learning Works

每个阶段都不是单纯“看概念”，而是按同一闭环推进：

1. 阅读知识
2. 理解方法
3. 阅读代码示例与 API 对照
4. 跟做引导项目
5. 阅读并解释关键代码
6. 独立完成课后项目
7. 接受阶段考核
8. 做复盘与迁移

从 `Stage 2` 开始，知识文档本身已经逐步改造成“概念 + 代码示例 + 逐段解释 + API 对照 + 全项目阅读”的连续教材，而不是把读码内容拆散到很多零碎文件里。

查看：

- [Learning Loop](./01-curriculum/learning-loop.md)
- [Competency Matrix](./01-curriculum/competency-matrix.md)
- [Stage Gates](./01-curriculum/stage-gates.md)

## Project-Based Teaching Design

每个阶段都配两类项目：

- `Guided Project`
  AI 先读知识文件，再读项目文件，按知识点顺序一步步带学
- `Homework Project`
  只给需求与验收标准，不直接给完整答案，由学习者独立完成，再由 AI 做评审

此外，所有项目都训练一条额外主线：

- 用户要能看懂不同功能分别由哪些文件和代码负责
- 用户要能用自然语言解释关键实现逻辑
- 用户要能对 AI 写出的代码做审核判断，而不是只接受结果
- 用户最终要能逐步看懂整个项目，而不是只懂几个关键代码块

查看：

- [AI Project Teaching Protocol](./03-projects/ai-project-teaching-protocol.md)
- [Project Catalog](./03-projects/project-catalog.md)
- [Project Templates](./03-projects/templates/README.md)
- [Official Docs & LangSmith Knowledge Base](./02-knowledge-base/08-official-docs-and-langsmith/README.md)

## Repository Guide

- [Start Here](./00-start-here/README.md)
- [Curriculum](./01-curriculum/README.md)
- [Knowledge Base](./02-knowledge-base/README.md)
- [Projects](./03-projects/README.md)
- [Assessments](./04-assessments/README.md)
- [Codex Collaboration](./05-codex-collaboration/README.md)

## Vision

这套课程的最终目标不是“会用几个 Agent 框架”，而是让学习者真正掌握一套构建方法：

从问题判断，到系统设计，到框架选择，到工程化落地，到前端体验，再到全栈交付与毕业项目。

也就是在 AI Agent 的帮助下，学会构建真正可用的 Agent 产品，并且看得懂它是如何被实现出来的。
