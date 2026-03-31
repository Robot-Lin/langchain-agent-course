# 08 Session Roadmap

这一章建议拆成 4 次学习会话，每次都遵循“读知识 -> 画结构 -> 做判断 -> 让 Codex 评审”的节奏。

## Session 1: 把边界分开

目标：

- 先彻底分清 MCP、RAG、memory、数据库、API。
- 建立“工程层不是附加题”的意识。

建议动作：

1. 阅读 [01-overview.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/01-overview.md) 和 [02-concepts.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/02-concepts.md)。
2. 自己举 3 个需求，分别判断应该落在哪一层。
3. 让 Codex 纠正你的边界混淆点。

## Session 2: 学会分层设计

目标：

- 把一个复杂 Agent 方案拆成工程层。
- 先学边界，再学接入。

建议动作：

1. 阅读 [03-methods.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/03-methods.md)。
2. 用一个真实需求画出最小系统架构。
3. 用 [09-case-comparisons.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/09-case-comparisons.md) 做对照。

## Session 3: 做跟学项目

目标：

- 把知识层、工具层、数据层、观测层、治理层真正串起来。

建议动作：

1. 按 [04-guided-project.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/04-guided-project.md) 做一遍引导项目。
2. 产出一张完整架构图和一份治理清单。
3. 让 Codex 站在架构评审角度做反馈。

## Session 4: 做挑战题与放行

目标：

- 把理解迁移到新问题。
- 用 review checklist 做阶段放行。

建议动作：

1. 完成 [05-challenges.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/05-challenges.md)。
2. 用 [06-review-checklist.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/06-review-checklist.md) 自测。
3. 按 [07-codex-workshop.md](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-5-agent-engineering/07-codex-workshop.md) 让 Codex 做一次正式评审。

## 本章完成标志

如果你已经能：

- 用自然语言说清一个 Agent 的工程分层。
- 不再混淆 memory、RAG 和数据库。
- 能为系统写出基本 observability、evaluation 和治理方案。

那就可以进入 Stage 6 的前端与体验层。
