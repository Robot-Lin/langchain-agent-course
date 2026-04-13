# Project Trainning

这份文档是一张完整的项目训练地图，目标是用一组彼此衔接的项目，逐步掌握：

- `LangChain`
- `LangSmith`
- `LangGraph`
- `Deep Agents`

文档不追求列很多题目，而追求三件事：

1. 项目有顺序
2. 技术栈有升级路径
3. 每一层都知道自己在补什么能力

---

## 0. 文件夹结构

当前 `Project Trainning` 目录已经整理成：

```text
03-projects/Project Trainning/
├─ README.md
├─ 01-langchain-langsmith/
│  └─ README.md
├─ 02-langchain-langgraph/
│  └─ README.md
└─ 03-deep-agents-langsmith/
   └─ README.md
```

阅读顺序建议：

1. 先看当前文件，理解总路线和启动规则
2. 再按学习阶段进入对应子目录
3. 真正开始做项目时，再按启动规则选择开始模式

各子目录入口：

- [01-langchain-langsmith/README.md](/X:/AI%20work/LangChain%20Tutorial/03-projects/Project%20Trainning/01-langchain-langsmith/README.md)
- [02-langchain-langgraph/README.md](/X:/AI%20work/LangChain%20Tutorial/03-projects/Project%20Trainning/02-langchain-langgraph/README.md)
- [03-deep-agents-langsmith/README.md](/X:/AI%20work/LangChain%20Tutorial/03-projects/Project%20Trainning/03-deep-agents-langsmith/README.md)

---

## 0. 启动规则

这部分是后续新的 Agent 在读取本文件时必须优先遵守的启动规则。

### 默认启动顺序

当 Agent 准备和用户开始某个项目时，必须按下面顺序执行：

1. 先问用户：**现在要做哪个项目**
2. 用户选定项目后，再给出下面 3 个开始选项
3. 用户选完模式后，Agent 再进入对应协作流程
4. 如果用户已经写出项目框架，Agent 必须先帮助用户分析框架的可行性、潜在漏洞与风险
5. 只有在确认框架没有明显问题后，Agent 才与用户一起进入实现阶段

### 用户选定项目后，必须提供的 3 个开始选项

1. `通过调用 MCP 学习所需知识点`
2. `告诉用户项目框架，由用户自己书写这个框架`
3. `用户自定义开始模式`

### 启动阶段禁止事项

在用户没有明确选择开始模式之前，Agent 不应该：

- 直接替用户压成可执行规格
- 直接替用户设计完整方案
- 跳过项目确认阶段
- 默认替用户选开始模式

另外，在用户已经写出项目框架但还没有经过分析之前，Agent 不应该：

- 直接跳进代码实现
- 跳过可行性检查
- 跳过风险提示
- 在未说明问题的情况下默认框架完全可行

### 框架分析阶段的要求

当用户已经写出项目框架之后，Agent 必须增加一个中间步骤：

1. 分析这个框架是否可行
2. 指出潜在漏洞、边界缺失和隐藏风险
3. 判断是否存在明显会导致项目失控的问题
4. 如果整体可行，明确告诉用户可以进入实现
5. 然后再与用户一起实现项目

这里的要求是：

- Agent 可以指出问题，但不要直接替用户重写框架
- Agent 应该以评审和协作的方式帮助用户修正
- 目标是让用户保留自己的项目定义权，同时减少明显设计风险

### 启动规则一句话总结

**先确认项目，再确认开始模式；如果用户写了框架，先做可行性与风险分析；确认基本可行后，再进入共同实现。**

---

## 1. 官方依据

### LangChain

- [Agents](https://docs.langchain.com/oss/python/langchain/agents)
- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)
- [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)
- [Knowledge base](https://docs.langchain.com/oss/python/langchain/knowledge-base)
- [Context engineering](https://docs.langchain.com/oss/python/langchain/context-engineering)
- [MCP](https://docs.langchain.com/oss/python/langchain/mcp)
- [LangChain v1 `create_agent`](https://docs.langchain.com/oss/python/releases/langchain-v1#create_agent)

### LangGraph

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)
- [LangGraph Graph API](https://docs.langchain.com/oss/python/langgraph/graph-api)
- [LangGraph Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)
- [LangGraph Persistence](https://docs.langchain.com/oss/python/langgraph/persistence)
- [LangGraph Durable Execution](https://docs.langchain.com/oss/python/langgraph/durable-execution)

### Deep Agents

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)
- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Human-in-the-loop in Deep Agents](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)

### LangSmith

- [LangSmith Observability](https://docs.langchain.com/langsmith/observability)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [Trace Deep Agents applications](https://docs.langchain.com/langsmith/trace-deep-agents)

---

## 2. 总路线总览

当前路线分成 3 层：

1. `LangChain + LangSmith`
   先练高层 agent 原型、工具接入、结构化输出、基础控制和观测

2. `LangChain + LangGraph`
   再练状态、分支、中断、恢复、持久化和 durable execution

3. `Deep Agents + LangSmith`
   最后练复杂任务组织、多角色、多子代理和 context engineering

最重要的顺序关系是：

- 先会搭 agent
- 再会观察和评估 agent
- 再会让系统有状态、可暂停、可恢复
- 最后再做复杂任务组织

---

## 3. 当前已决定的项目清单

### 第一层：LangChain + LangSmith 主线项目

1. `行程信息整理器`
2. `招聘 JD 与简历匹配助手`
3. `Obsidian 第二大脑整理与更新审批助手`

### 第二层：LangChain + LangGraph 进阶项目

1. `旅行助手图系统`
2. `多轮面试模拟与反馈系统`
3. `研究任务分阶段执行系统`
4. `Obsidian 第二大脑更新审批图系统`

### 第三层：Deep Agents + LangSmith 项目

1. `个人知识学习教练`
2. `多来源情报监控与周报助手`
3. `内容创作流水线助手`

---

## 4. 第一层：LangChain + LangSmith 主线项目

这一层的目标不是做复杂系统，而是先把 LangChain 高层原型练稳，并且从一开始就学会用 LangSmith 观察和评估。

### 项目 1：行程信息整理器

**难度定位**：初级

**项目目标**：
用户输入零散的行程信息，例如日期、出发地、目的地、航班、酒店、交通方式和提醒事项。系统将这些信息整理成结构化结果，并指出缺失项或待确认项。

**适合练什么**：
- `create_agent`
- 单一职责 `tool`
- `structured output / response_format`
- 最小 `workflow`
- `LangSmith tracing`

**推荐最小工具**：
- 地点信息读取工具
- 日期标准化工具
- 时区或天气查询工具（可选）

**推荐输出结构**：
- `trip_summary`
- `schedule_items`
- `transportation`
- `accommodation`
- `missing_information`
- `important_reminders`

**LangSmith 重点**：
- 追踪每次 agent 调用和 tool 调用
- 检查结构化输出是否稳定
- 找出最容易导致 schema 缺字段的输入

---

### 项目 2：招聘 JD 与简历匹配助手

**难度定位**：中级

**项目目标**：
用户输入岗位描述和简历内容，系统输出匹配度判断、优势项、缺口项、风险点、建议补充内容和下一步行动建议。

**适合练什么**：
- 多输入分析
- `structured output`
- `middleware`
- 可选 `retrieval`
- `LangSmith tracing + evaluation`

**推荐最小工具**：
- JD 文本读取工具
- 简历文本读取工具
- 岗位信息读取或网页抓取工具（可选）

**推荐输出结构**：
- `match_score`
- `strengths`
- `gaps`
- `risks`
- `suggested_resume_improvements`
- `next_step`

**LangSmith 重点**：
- 为不同 JD / 简历样本建立测试集
- 评估匹配分、优势、缺口等字段是否稳定
- 对比 prompt 或 schema 调整前后的结果变化

---

### 项目 3：Obsidian 第二大脑整理与更新审批助手

**难度定位**：高级

**项目目标**：
围绕 Obsidian 第二大脑，系统负责检索相关笔记、回答问题、整理标签与分类、提出合并/重命名/删除/归档建议，并对危险变更发起人工审批。

**适合练什么**：
- `knowledge base / retrieval`
- `short-term memory`
- `checkpointer`
- `HumanInTheLoopMiddleware`
- `LangSmith tracing + evaluation + deployment`

**推荐最小工具**：
- 本地知识库检索工具
- 文档读取工具
- 标签与分类建议工具
- 变更执行工具
- Obsidian 笔记更新工具

**推荐输出结构**：
- `answer`
- `related_notes`
- `proposed_changes`
- `change_risk_level`
- `requires_human_review`
- `final_status`

**LangSmith 重点**：
- 观察检索、memory、审批节点如何协同
- 评估回答质量、检索命中率、变更建议准确性
- 后续如果长期自用，可进入 deployment

---

## 5. 第一层的能力覆盖总结

这 3 个项目加起来，已经可以覆盖 LangChain 高层原型阶段的大多数核心能力，尤其是：

- `create_agent`
- `tools`
- `structured output`
- `middleware`
- `short-term memory`
- `checkpointer`
- `knowledge base / retrieval`
- `human-in-the-loop`
- `LangSmith tracing`
- `LangSmith evaluation`

相对偏弱的部分是：

- `dynamic model selection`
- `MCP` 的真实多工具接入

但这两块都可以从第三个项目继续扩展，而不需要换掉主线。

---

## 6. 第二层：LangChain + LangGraph 进阶项目

这一层的目标是把高层 agent 升级为真正的 stateful runtime system，开始练：

- `state`
- `conditional routing`
- `interrupt`
- `persistence`
- `durable execution`

### 项目 1：旅行助手图系统

**重点能力**：
- 状态设计
- 分支
- 变更确认
- 恢复执行

**为什么值得做**：
旅行场景天然会出现行程冲突、信息补全、方案确认和变更恢复，非常适合做图系统。

---

### 项目 2：多轮面试模拟与反馈系统

**重点能力**：
- 多轮状态推进
- 条件分支
- 阶段性总结

**为什么值得做**：
它很适合练“什么时候继续追问、什么时候结束、什么时候进入反馈总结”。

---

### 项目 3：研究任务分阶段执行系统

**重点能力**：
- 阶段推进
- 循环判断
- 累积状态
- 最终总结

**为什么值得做**：
它很适合练 reducer、状态累积和“信息够不够”的迭代判断。

---

### 项目 4：Obsidian 第二大脑更新审批图系统

**重点能力**：
- 高风险写操作
- 审批
- `interrupt`
- `persistence`
- `durable execution`

**为什么值得做**：
它能把你在第一层做过的知识库项目，自然升级到 LangGraph 的运行时控制层。

---

## 7. 第三层：Deep Agents + LangSmith 项目

在完成前两层之后，再进入 Deep Agents 会更顺，因为这时你已经理解了：

- LangChain 的高层 agent 装配
- LangGraph 的状态、分支、中断与恢复
- LangSmith 的 tracing、evaluation 和 deployment 基础

这一层的目标不再只是“一个 agent 完成一个任务”，而是开始练：

- 多角色 / 多子代理分工
- context engineering
- 长任务组织
- complex memory
- 多子代理场景下的 LangSmith 监控

**统一要求**：
这一层的项目都必须默认接入 `LangSmith` 监控，至少包括：
- tracing
- 关键节点观测
- 子代理调用链可见
- 后续可扩展 evaluation

### 项目 1：个人知识学习教练

**项目目标**：
用户输入想学习的内容，系统检索互联网与本地知识来源，筛选资料，生成课纲，并配置多个角色作为助教和同学，与用户一起学习。

**推荐角色拆分**：
- `research_agent`
- `curation_agent`
- `curriculum_agent`
- `teaching_assistant_agent`
- `peer_learning_agent`
- `review_agent`

**推荐输出结构**：
- `learning_goal`
- `recommended_materials`
- `curriculum_outline`
- `current_session_focus`
- `assistant_feedback`
- `peer_challenge`
- `next_learning_step`

**核心训练价值**：
- 理解多角色分工
- 理解 context engineering
- 理解复杂任务里的 memory
- 学会在多子代理系统中使用 LangSmith

---

### 项目 2：多来源情报监控与周报助手

**项目目标**：
系统持续从多个信息源收集内容，做去重、排序、主题聚合和重点识别，最后生成周报并给出后续跟进建议。

**推荐角色拆分**：
- `source_collection_agent`
- `dedup_agent`
- `priority_agent`
- `weekly_summary_agent`
- `followup_agent`

**推荐输出结构**：
- `collection_summary`
- `top_signals`
- `duplicates_removed`
- `weekly_report`
- `followup_actions`

**核心训练价值**：
- 理解阶段性信息流动
- 学会做长链路信息处理型多代理系统
- 学会在持续监控类任务中使用 LangSmith

---

### 项目 3：内容创作流水线助手

**项目目标**：
围绕一个主题，从选题、资料收集、提纲、初稿、改写、风格统一到发布前审核，构建完整内容创作流水线。

**推荐角色拆分**：
- `topic_agent`
- `research_agent`
- `outline_agent`
- `draft_agent`
- `rewrite_agent`
- `editor_agent`
- `review_agent`

**推荐输出结构**：
- `topic_direction`
- `research_notes`
- `outline`
- `draft`
- `edited_version`
- `review_feedback`
- `publish_recommendation`

**核心训练价值**：
- 理解多阶段任务组织
- 学会设计创作类子代理分工
- 学会把 LangSmith 用在长链路内容系统上

---

## 8. 推荐练习顺序

### 第一层推荐顺序

1. `行程信息整理器`
2. `招聘 JD 与简历匹配助手`
3. `Obsidian 第二大脑整理与更新审批助手`

### 第二层推荐顺序

1. `旅行助手图系统`
2. `多轮面试模拟与反馈系统`
3. `研究任务分阶段执行系统`
4. `Obsidian 第二大脑更新审批图系统`

### 第三层推荐顺序

1. `个人知识学习教练`
2. `内容创作流水线助手`
3. `多来源情报监控与周报助手`

---

## 9. 你现在的完整技术栈路线

### 第一步：LangChain + LangSmith

- 行程信息整理器
- 招聘 JD 与简历匹配助手
- Obsidian 第二大脑整理与更新审批助手

目标：
学会高层 agent 原型、工具、结构化输出、基础控制，以及 tracing / evaluation。

### 第二步：LangChain + LangGraph

- 旅行助手图系统
- 多轮面试模拟与反馈系统
- 研究任务分阶段执行系统
- Obsidian 第二大脑更新审批图系统

目标：
学会状态设计、分支、中断、恢复、持久化和 durable execution。

### 第三步：Deep Agents + LangSmith

- 个人知识学习教练
- 多来源情报监控与周报助手
- 内容创作流水线助手

目标：
学会复杂任务组织、多角色分工、context engineering 和多子代理观测。

---

## 10. 这份文档怎么用

最推荐的用法是：

1. 一次只选一个项目
2. 先用自然语言写出：
   - 用户是谁
   - 主任务是什么
   - 不做什么
   - 最小工具是什么
   - 输出结构字段是什么
3. 再把它推进成项目文件结构和代码实现
4. 每做完一个项目，回头看这张路线图，确认自己补到了哪些能力

如果你是把这份文档当成长期训练地图来看，那它最适合作为：

**你的 LangChain -> LangGraph -> Deep Agents -> LangSmith 项目升级路线图。**

---

## 11. 项目启动交互框架

这部分是给后续新的 Agent 看的启动规则。

目标是：当用户真正开始做项目时，Agent 不要直接替用户压成可执行规格，也不要越过用户直接开始设计方案，而是先进入一个固定的项目启动流程。

### 第一步：先确认用户要做哪个项目

当 Agent 读取这份文档并准备开始一个新项目时，必须先问用户：

**“你现在要做哪个项目？”**

项目优先从本文件当前已决定的项目清单里选择。

如果用户没有明确指定，Agent 可以把当前项目清单列给用户选，但不能直接替用户决定。

### 第二步：用户选定项目后，必须提供 3 个启动选项

当用户选定某个项目之后，Agent 必须继续给出下面 3 个选项，让用户决定怎么开始：

1. `通过调用 MCP 学习所需知识点`
2. `告诉用户项目框架，由用户自己书写这个框架`
3. `用户自定义开始模式`

这里的要求是：

- Agent 不能跳过这一步
- Agent 不能默认替用户选择
- Agent 要把这 3 个选项明确呈现出来

### 选项 1：通过调用 MCP 学习所需知识点

如果用户选择这个模式，Agent 应该：

- 先调用对应官方文档 MCP
- 梳理该项目所需的核心知识点
- 按“问题 -> 原因 -> 概念 -> 代码 -> 文件位置 -> 主路径/状态流 -> 练习”的顺序展开
- 帮助用户先理解所需技术，而不是立刻写项目方案

这个模式适合：

- 用户还不熟悉当前技术栈
- 用户希望先补知识，再开始设计和开发

### 选项 2：告诉用户项目框架，由用户自己书写框架

如果用户选择这个模式，Agent 应该：

- 先把“项目框架模板”告诉用户
- 让用户自己来填写这个框架
- Agent 只负责引导、校准和补充风险提醒
- 不要直接替用户重写框架

这里的“项目框架模板”默认至少包括：

1. 用户是谁
2. 主任务是什么
3. 当前不做什么
4. 输入是什么
5. 输出是什么
6. 最小工具是什么
7. 关键控制逻辑是什么
8. 什么算第一版完成

这个模式适合：

- 用户希望自己练系统设计能力
- 用户希望通过自然语言来主导项目定义

### 选项 3：用户自定义开始模式

如果用户选择这个模式，Agent 应该：

- 先听用户说明自己想怎么开始
- 再按照用户指定的方式协作
- 只有当用户的模式明显缺少关键边界时，才做最小提醒
- 不要强行切回前两个模式

这个模式适合：

- 用户已经有自己的学习或开发节奏
- 用户想指定特殊起步方式

### 启动阶段的默认约束

无论用户选择哪一种模式，Agent 都应该遵守下面的默认约束：

- 先确认项目，再开始技术或实现讨论
- 不要跳过用户选择过程
- 不要直接替用户压成可执行规格，除非用户明确要求
- 如果涉及教学，继续遵守本仓库已有的 MCP 教学规则
- 如果涉及项目协作，优先让用户掌握项目边界和主路径，而不是直接堆实现

### 一句话总结

后续新的 Agent 读取这份文档后，启动一个项目时应遵循这个顺序：

**先问做哪个项目 -> 再给 3 个开始选项 -> 再按用户选择的模式进入项目。**

