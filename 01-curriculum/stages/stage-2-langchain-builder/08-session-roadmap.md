# 08 Session Roadmap

这个文件把 `Stage 2` 拆成一组真正可以执行的学习 session。你可以自己按节奏推进，也可以让 Codex 按这个顺序一节一节带你学。

## 建议总时长

- 轻量模式: 4 到 5 天
- 标准模式: 1 周左右
- 深挖模式: 1 到 2 周

## Session 1: LangChain 为什么是高层入口

### 学习目标

- 理解 LangChain 在新版体系中的位置
- 知道它和 LangGraph 的上下层关系
- 明白为什么它适合作为第一次框架实践入口

### 先读什么

- [01-overview.md](./01-overview.md)
- [02-concepts.md](./02-concepts.md)
- [03-methods.md](./03-methods.md) 末尾附录

### 要做什么

- 用自己的话解释 LangChain 到底帮你抽象了什么
- 写出 3 个“当前适合留在 LangChain”的场景
- 写出 2 个“已经开始逼近 LangGraph”的迹象

### 交付物

- 一段 120 到 180 字的理解复述
- 一张 LangChain 与 LangGraph 的分层对比表

## Session 2: Tools 与 structured output

### 学习目标

- 建立“工具最小化”意识
- 理解为什么 structured output 是高层原型核心能力

### 先读什么

- [02-concepts.md](./02-concepts.md)
- [03-methods.md](./03-methods.md)
- [02-concepts.md](./02-concepts.md) 后半部分代码教材

### 要做什么

- 选一个你自己的 Agent 想法
- 只给它保留一个最必要工具
- 设计一版 structured output 字段草案

### 交付物

- 一份最小工具清单
- 一份 structured output 字段说明

## Session 3: Middleware、short-term memory 与 HITL

### 学习目标

- 理解哪些控制逻辑不该全塞在 prompt 里
- 能判断什么时候短期记忆值得接入
- 理解高层原型也需要 human-in-the-loop

### 先读什么

- [02-concepts.md](./02-concepts.md)
- [09-case-comparisons.md](./09-case-comparisons.md)
- [02-concepts.md](./02-concepts.md) 后半部分代码教材

### 要做什么

- 写出 3 条适合放进 middleware 的规则
- 判断你的场景是否需要 short-term memory
- 写出 2 个需要人工审核的动作

### 交付物

- middleware 规则清单
- 短期记忆判断说明
- HITL 场景列表

## Session 4: 高层原型四步法

### 学习目标

- 学会把一个 Stage 1 方案推进成 LangChain 原型
- 熟悉主任务、工具、输出、控制逻辑四步法

### 先读什么

- [03-methods.md](./03-methods.md)
- [03-methods.md](./03-methods.md) 末尾附录

### 要做什么

- 选择一个 Stage 1 方案
- 用四步法重写成 LangChain 高层原型
- 写出“为什么现在还不需要 LangGraph”

### 交付物

- 一份 LangChain 高层原型设计说明
- 一段高层边界说明

## Session 5: 跟做单工具研究助理

### 学习目标

- 把概念和方法落实到一个具体原型项目
- 练习单工具、structured output、基础控制逻辑三件套

### 先读什么

- [04-guided-project.md](./04-guided-project.md)
- [Stage 2 跟学项目](../../../03-projects/stage-2/guided-project-research-assistant.md)

### 要做什么

- 按步骤完成研究助理原型设计
- 每一步都说明对应的知识点

### 交付物

- 单工具研究助理原型说明
- 工具定义
- 输出 schema
- 边界复盘
- 一份最小代码讲解

## Session 6: 独立完成课后项目

### 学习目标

- 在没有标准答案的情况下独立做高层原型设计
- 接受基于结构和边界的评审

### 先读什么

- [05-challenges.md](./05-challenges.md)
- [Stage 2 课后项目](../../../03-projects/stage-2/homework-project-structured-interview-agent.md)

### 要做什么

- 独立完成 structured interview agent 方案
- 让 Codex 按工具、输出、控制逻辑和边界来评审

### 交付物

- 结构化面试 Agent 方案
- 自评结果
- Codex 评审反馈

## Session 7: 阶段复盘与放行

### 学习目标

- 确认是否真的掌握了 LangChain 高层原型思路
- 确认是否准备进入 LangGraph

### 先读什么

- [06-review-checklist.md](./06-review-checklist.md)
- [07-codex-workshop.md](./07-codex-workshop.md)

### 要做什么

- 回答 Stage 2 的放行问题
- 说明一个项目为什么适合或不适合继续留在 LangChain
- 说出 3 个逼近 LangGraph 的迹象

### 放行标准

你至少应该能稳定做到:

- 不把 LangChain 理解成“方便点的 API 包装器”
- 不乱加工具
- 优先设计输出结构
- 能把控制逻辑从 prompt 中适当分层
- 能说清项目何时该进入 LangGraph

## 建议学习闭环

每完成一个 session，都做一次同样的闭环:

1. 复述这节最核心的一句话。
2. 写下你删掉了哪些多余能力。
3. 写下你新增了哪些结构化设计意识。
4. 让 Codex 只从评审视角给你反馈。

如果你希望真正按节奏开始学，现在最适合从 `Session 1` 正式推进。
