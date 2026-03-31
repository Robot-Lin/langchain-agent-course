# LangChain Agent Course

一个面向 IDE + Codex 协作学习的完整 Agent 教学课程，围绕 `LangChain`、`LangGraph`、`Deep Agents` 展开，并系统覆盖 `MCP`、`RAG`、`Memory`、数据库、后端 API、前端 Agent UX、评测、观测、部署与毕业项目。

这不是一份单次写完的“教程文档”，而是一套可以持续扩建的课程工程。目标是让学习者不是只会“调用一个 Agent”，而是能在 AI Agent 的帮助下，从后端到前端构建一个功能完整、结构清晰、可评测、可迭代的 Agent 产品。

## What This Repo Covers

- 从 Agent 基础心智模型开始，而不是直接堆 API
- 逐步掌握 LangChain 高层原型、LangGraph 状态化系统、Deep Agents 复杂任务组织
- 系统学习 MCP、RAG、Memory、数据库、后端接口、前端 Agent UX、评测、观测、部署
- 把 Agent 做成真正可用的前端产品，而不是只有聊天框
- 最终完成一个从后端到前端的毕业级 Agent 项目

## Who This Course Is For

适合这样的学习者：

- 对 Agent 已经有基础了解
- 有一定提示词构建能力
- 知道 Anthropic Skill 一类能力封装思路
- 能描述自己的需求和产品想法
- 希望在 IDE 中与 Codex 结对学习、拆题、设计和落地

## Learning Goal

完成这套课程后，学习者应能：

- 判断一个需求是否真的需要 Agent
- 知道什么时候该用 LangChain、什么时候该下沉到 LangGraph、什么时候适合 Deep Agents
- 设计 Agent 的工具层、知识层、状态层、体验层、治理层和评测层
- 在 AI Agent 协作下完成一个从后端到前端的 Agent 产品原型
- 能清楚解释自己的架构、交付路径、风险边界和下一步迭代方向

## Official Reference Backbone

这套课程当前以 LangChain 官方新版文档为主线依据：

- [LangChain Overview](https://docs.langchain.com/oss/python/langchain/overview)
- [LangGraph Overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Deep Agents Overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Model Context Protocol (MCP)](https://docs.langchain.com/oss/python/langchain/mcp)
- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)

## Course Structure

### Stage 1-8

课程已经搭成完整的八阶段结构：

| Stage | Theme | Outcome |
| --- | --- | --- |
| 1 | Agent Foundations | 建立 Agent 系统判断力 |
| 2 | LangChain Builder | 搭建高层 Agent 原型 |
| 3 | LangGraph Systems | 设计状态化、可审批、可恢复系统 |
| 4 | Deep Agents | 处理复杂任务、规划、上下文工程、子代理 |
| 5 | Agent Engineering | 接入 MCP、RAG、数据层、评测、治理 |
| 6 | Agent Frontend | 设计 Agent UX、流式交互、审批界面 |
| 7 | Full-stack Delivery | 组装全栈产品、部署、评测、交付 |
| 8 | Capstone Mastery | 完成毕业项目、答辩、复盘与迁移 |

阶段入口：

- [Stages Index](./01-curriculum/stages/README.md)
- [Course Roadmap](./01-curriculum/course-roadmap.md)
- [Stage Gates](./01-curriculum/stage-gates.md)

## How Learning Works

每个阶段都不是单纯“看概念”，而是按同一闭环推进：

1. 阅读知识
2. 理解方法
3. 跟做引导项目
4. 独立完成课后项目
5. 接受阶段考核
6. 做复盘与迁移

查看：

- [Learning Loop](./01-curriculum/learning-loop.md)
- [Competency Matrix](./01-curriculum/competency-matrix.md)

## Project-Based Teaching Design

每个阶段都配两类项目：

- `Guided Project`
  AI 先读知识文件，再读项目文件，按知识点顺序一步步带学
- `Homework Project`
  只给需求与验收标准，不直接给完整答案，由学习者独立完成，再由 AI 做评审

项目机制说明：

- [AI Project Teaching Protocol](./03-projects/ai-project-teaching-protocol.md)
- [Project Catalog](./03-projects/project-catalog.md)
- [Project Templates](./03-projects/templates/README.md)

分阶段项目入口：

- [Stage 1 Projects](./03-projects/stage-1/README.md)
- [Stage 2 Projects](./03-projects/stage-2/README.md)
- [Stage 3 Projects](./03-projects/stage-3/README.md)
- [Stage 4 Projects](./03-projects/stage-4/README.md)
- [Stage 5 Projects](./03-projects/stage-5/README.md)
- [Stage 6 Projects](./03-projects/stage-6/README.md)
- [Stage 7 Projects](./03-projects/stage-7/README.md)
- [Stage 8 Projects](./03-projects/stage-8/README.md)

## Repository Guide

### Start Here

- [00-start-here](./00-start-here/README.md)
- [How to Learn with Codex](./00-start-here/how-to-learn-with-codex.md)

### Curriculum

- [Curriculum Index](./01-curriculum/README.md)
- [Full-stack Agent Path](./01-curriculum/fullstack-agent-path.md)

### Knowledge Base

- [Knowledge Base Index](./02-knowledge-base/README.md)
- [Agent Foundations](./02-knowledge-base/01-agent-foundations/README.md)
- [LangChain](./02-knowledge-base/02-langchain/README.md)
- [LangGraph](./02-knowledge-base/03-langgraph/README.md)
- [Deep Agents](./02-knowledge-base/04-deep-agents/README.md)
- [Cross-cutting Systems](./02-knowledge-base/05-cross-cutting-systems/README.md)
- [Frontend Agent Experience](./02-knowledge-base/06-frontend-agent-experience/README.md)
- [Agent Framework Landscape](./02-knowledge-base/07-agent-framework-landscape/README.md)

### Assessments

- [Assessments](./04-assessments/README.md)
- [Rubric](./04-assessments/rubric.md)

### Codex Collaboration

- [Codex Collaboration](./05-codex-collaboration/README.md)
- [Session Patterns](./05-codex-collaboration/session-patterns.md)

## Recommended Reading Order

如果你是第一次进入这个仓库，建议按下面顺序开始：

1. [Start Here](./00-start-here/README.md)
2. [Course Roadmap](./01-curriculum/course-roadmap.md)
3. [Learning Loop](./01-curriculum/learning-loop.md)
4. [Stages Index](./01-curriculum/stages/README.md)
5. [Stage 1 Course Pack](./01-curriculum/stages/stage-1-agent-foundations/README.md)

## Current Build Status

当前已经完成：

- Stage 1 到 Stage 8 的完整教学包骨架
- 每个阶段的知识、方法、引导项目、课后项目、验收标准、Codex 对练脚本
- 项目教学协议与分阶段项目目录
- 全栈 Agent 学习路径、阶段放行标准与 Rubric

当前仍可继续增强：

- 每个知识模块继续扩写成更厚的教材
- 每个项目继续扩成更完整的教学案例包
- 加入更多练习题、案例库、错题库
- 补更多前端原型模板与可运行示例

查看：

- [COURSE_BUILD_STATUS.md](./COURSE_BUILD_STATUS.md)

## How to Use This Repo with Codex

推荐在 IDE 中直接和 Codex 配合：

- 让 Codex 先讲解某个阶段
- 让 Codex 按项目文件一步步带学
- 做课后项目时要求 Codex 只做导师和评审，不直接给最终答案
- 做完后让 Codex 按验收标准打分和指出缺口

## Contribution Direction

如果后续继续扩建这个仓库，最值得优先补的方向是：

- Stage 1-8 的更深知识解释文档
- 每个阶段的完整案例包
- 可运行 demo 和前端原型
- 开源协作说明、许可证与贡献流程

查看：

- [CONTRIBUTING.md](./CONTRIBUTING.md)
- [LICENSE](./LICENSE)

## Vision

这套课程的最终目标不是“会用几个 Agent 框架”，而是让学习者真正掌握一套构建方法：

从问题判断，到系统设计，到框架选择，到工程化落地，到前端体验，再到全栈交付与毕业项目。

也就是在 AI Agent 的帮助下，学会构建真正可用的 Agent 产品。
