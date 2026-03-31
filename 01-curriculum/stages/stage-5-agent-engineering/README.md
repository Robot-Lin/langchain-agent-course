# Stage 5 教学包

这是课程里把 Agent 从“能跑的复杂系统”推进到“可接入真实业务的工程系统”的关键单元。它承接 Stage 4，把学习者带入 MCP、RAG、memory、数据库、后端 API、observability、evaluation 和 governance 的完整工程视角。

## 学完这一章之后应该做到什么

- 能解释 MCP、RAG、memory、数据库、API、observability、evaluation 各自在系统里解决什么问题。
- 能为一个 Agent 设计知识层、工具层、数据层、服务层和治理层，而不是把所有能力混成一个黑箱。
- 能用自然语言画出“一个真实 Agent 产品后端”是如何接外部能力、接知识、接数据、接观测的。
- 能判断一个方案为什么还只是 Demo，或者为什么已经具备进入真实业务系统的基础。

## 建议学习顺序

1. [01-overview.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/01-overview.md)
2. [02-concepts.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/02-concepts.md)
3. [03-methods.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/03-methods.md)
4. [08-session-roadmap.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/08-session-roadmap.md)
5. [09-case-comparisons.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/09-case-comparisons.md)
6. [04-guided-project.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/04-guided-project.md)
7. [05-challenges.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/05-challenges.md)
8. [06-review-checklist.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/06-review-checklist.md)
9. [07-codex-workshop.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/07-codex-workshop.md)
10. [Stage 5 配套项目](X:/AI%20work/LangChain%20Tutorial/03-projects/stage-5/README.md)

## 本章的核心问题

- MCP 和普通 tool 接入到底差在哪里。
- RAG、memory、数据库分别存什么，为什么不能混用。
- 为什么 Agent 一接真实业务就必须考虑权限、审计和观测。
- 为什么 evaluation 不是最后补上的测试，而是系统设计的一部分。
- 为什么“能回答”不等于“能上线”。

## 本章在整套课程里的作用

Stage 5 训练的是工程化结构感：

- 你开始把 Agent 看成一个系统，而不是一个聪明的模型。
- 你开始关心它看了什么、调了什么、存了什么、为什么这么做。
- 你开始能解释一个真实 Agent 后端是如何落地的。
