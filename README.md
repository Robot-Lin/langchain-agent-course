# LangChain Agent 学习课程

这是一个面向 IDE 内协作学习的 Agent 教学系统。课程围绕 LangChain、LangGraph、Deep Agents 展开，并把 MCP、RAG、数据库、后端、前端、Skill、评测、部署、人机协作一起纳入完整知识体系。

这套课程不是一次性写完的“大课本”，而是一个可以持续扩建的学习工程。我们会像搭积木一样，从外层框架到内层细节，逐步把知识库、项目库、考核系统和实战模板补齐。

## 课程目标

- 让学习者在不手写代码为主的前提下，通过问答、Vibe Coding、与 Codex 协作的方式，真正理解 Agent 系统如何被设计、拆解、构建、验证和迭代。
- 让学习者不仅会“调用一个 Agent”，而且知道什么时候该用 LangChain，什么时候该下沉到 LangGraph，什么时候该直接采用 Deep Agents。
- 让学习者具备从需求描述到可落地 Agent 产品原型的完整能力，包括后端能力、工具接入、知识接入、用户体验和部署思维。

## 目标用户画像

- 对 Agent 已经有基础认知
- 有一定提示词构建经验
- 知道 Anthropic Skill 这类能力封装的思路
- 能够清楚描述自己的需求和产品想法
- 希望在 IDE 环境里和 Codex 一起学习、拆题、搭建、验证

## 官方架构主线

这套课程当前以 LangChain 官方新版文档为架构依据。

- LangChain: 高层 Agent 开发框架，主打更快做出可用 Agent。
- LangGraph: 更底层的 Agent runtime 和 workflow orchestration，主打状态、持久化、恢复、interrupt、人机协作和生产级控制。
- Deep Agents: 更适合复杂任务的高层入口，强调规划、上下文工程、子代理、长期任务执行和复杂问题求解。

官方参考入口:

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Model Context Protocol (MCP)](https://docs.langchain.com/oss/python/langchain/mcp)

## 当前已经搭好的第一层结构

- [00-start-here/README.md](X:/AI%20work/LangChain%20Tutorial/00-start-here/README.md)
- [01-curriculum/course-roadmap.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/course-roadmap.md)
- [01-curriculum/learning-loop.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/learning-loop.md)
- [01-curriculum/fullstack-agent-path.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/fullstack-agent-path.md)
- [01-curriculum/stages/README.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/README.md)
- [01-curriculum/competency-matrix.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/competency-matrix.md)
- [01-curriculum/stage-gates.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stage-gates.md)
- [02-knowledge-base/README.md](X:/AI%20work/LangChain%20Tutorial/02-knowledge-base/README.md)
- [03-projects/project-catalog.md](X:/AI%20work/LangChain%20Tutorial/03-projects/project-catalog.md)
- [03-projects/ai-project-teaching-protocol.md](X:/AI%20work/LangChain%20Tutorial/03-projects/ai-project-teaching-protocol.md)
- [03-projects/fullstack-capstone/README.md](X:/AI%20work/LangChain%20Tutorial/03-projects/fullstack-capstone/README.md)
- [04-assessments/README.md](X:/AI%20work/LangChain%20Tutorial/04-assessments/README.md)
- [04-assessments/rubric.md](X:/AI%20work/LangChain%20Tutorial/04-assessments/rubric.md)
- [05-codex-collaboration/README.md](X:/AI%20work/LangChain%20Tutorial/05-codex-collaboration/README.md)
- [COURSE_BUILD_STATUS.md](X:/AI%20work/LangChain%20Tutorial/COURSE_BUILD_STATUS.md)

## 使用方式

- 先读 [00-start-here/README.md](X:/AI%20work/LangChain%20Tutorial/00-start-here/README.md)
- 再看 [01-curriculum/course-roadmap.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/course-roadmap.md)
- 再看 [01-curriculum/learning-loop.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/learning-loop.md)
- 然后进入 [01-curriculum/stages/README.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/README.md) 按阶段学习
- 然后按阶段进入知识库和项目库
- 项目学习时，先看 [03-projects/ai-project-teaching-protocol.md](X:/AI%20work/LangChain%20Tutorial/03-projects/ai-project-teaching-protocol.md)
- 每完成一段，就回到 [01-curriculum/stage-gates.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stage-gates.md) 做阶段检查

## 共建原则

- 先搭框架，再补细节
- 先统一概念，再做项目
- 先做可验证的小系统，再做复杂大系统
- 先会描述和拆解，再逐步理解实现
- 尽量通过 Codex 结对协作，而不是把学习过程变成“纯复制代码”
