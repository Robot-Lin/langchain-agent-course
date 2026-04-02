# 03 Methods

这一章关注的不是 `Stage 2` 的概念定义，而是拿到一个 LangChain 项目以后，应该怎么下手。

如果你更适合“先看代码，再反推方法”，建议先读完 [02-concepts.md](./02-concepts.md) 后半部分的代码教材，再回到本文件。

## 方法一: 高层原型四步法

面对一个 `LangChain` 项目，先做四步:

1. 定义唯一主任务
2. 定义必要工具
3. 定义 structured output
4. 定义基础控制逻辑

这四步的意义分别是:

- 主任务决定系统边界
- 工具决定外部能力
- 输出决定系统是否可验证、可复用
- 控制逻辑决定系统是否可控

如果你在 `Stage 2` 上来就先想 prompt 细节，而不是先过这四步，原型通常会很快变乱。

## 方法二: 先设计输出，再设计 prompt

这是 `Stage 2` 最值得建立的习惯之一。

在开始写 prompt 前，先问自己:

- 我最后到底要什么结构的结果
- 谁要消费这个结果
- 这个结果是给人看，还是给系统继续处理
- 如果结果不结构化，后续会出什么问题

在高层 Agent 原型里，structured output 往往比 prompt 文案更决定系统质量。

原因很简单:

- prompt 决定生成方式
- output schema 决定系统是否真正可用

## 方法三: 工具最小化

不要一上来就给 Agent 很多工具。

推荐顺序:

1. 零工具版本
2. 单工具版本
3. 必要时再增加第二个工具

只有当你能说明:

> 新增这个工具会让系统完成什么原本做不到的事情

才应该继续加。

这一步的重点不是“工具越强越好”，而是“工具和任务边界是否匹配”。

## 方法四: 用 middleware 放控制逻辑，而不是全塞进 prompt

适合优先放进 middleware 的内容通常包括:

- human-in-the-loop 审核
- 特定工具限制
- 简单风险拦截
- 行为守护规则

这样做的好处是:

- 系统更容易解释
- 控制层次更清楚
- 将来迁移到更复杂框架时更顺

换句话说，`Stage 2` 就要开始练习“控制逻辑分层”，而不是把所有系统规则都混成一段 prompt。

## 方法五: 高层原型失败复盘法

`Stage 2` 的失败通常来自 5 类问题:

- 主任务定义不清
- 工具设计不清
- structured output 不清
- 控制逻辑缺失
- 高层边界判断错误

每次复盘都建议按这 5 类去查，而不要只问“模型今天怎么答得不好”。

一个高质量复盘，至少要回答:

- 主任务是不是太散了
- 工具是不是为了显得高级而接入的
- 输出是不是人能看懂但系统不能消费
- 控制逻辑是不是全靠 prompt 硬扛
- 这个问题是不是其实已经更适合 LangGraph 了

## 方法六: 高层原型边界说明法

在 `Stage 2`，你应该开始练习写这样一段话:

> 这个项目目前适合留在 LangChain，因为它的主路径清楚、控制逻辑有限、状态复杂度不高。虽然它已经有工具、structured output 和基础审核需求，但还不需要复杂图编排、恢复机制和长生命周期任务管理。

这段话非常重要，因为它在训练一种能力:

- 不只是会搭原型
- 还知道为什么当前这层抽象足够

## 方法七: 何时停止留在 LangChain

出现下面这些情况时，应该开始准备进入 `Stage 3`:

- 你需要明显的多分支流程
- 你需要恢复和中断成为主流程能力
- 你需要复杂状态控制
- 你发现 middleware 和 prompt 已经扛不住系统复杂度
- 你开始用很多人为规则拼接一个“看起来像流程引擎”的东西

这时继续停留在高层封装里，维护成本往往会迅速上升。

## 方法八: 用 Codex 做高层原型评审

在 `Stage 2`，最推荐的 AI 协作方式不是让 Codex 直接给你整套实现，而是让它扮演:

- 高层架构评审员
- 工具边界审查员
- structured output 审查员
- middleware / 控制逻辑审查员
- LangChain 与 LangGraph 分界提醒员

推荐提问方式:

- 帮我检查这个项目的主任务是否过散。
- 帮我看看这个 structured output 是否真的可被后续系统消费。
- 请只从工具边界角度批评我的方案，不要帮我加功能。
- 请判断我的控制逻辑是不是已经开始逼近 LangGraph。

## Stage 2 的方法目标

真正掌握本阶段，不是“会调用 LangChain”，而是能把一个合理的 Agent 设计推进成结构清楚、输出可靠、可演示、可评审的高层原型。

## 附录：Stage 2 API 对照读法

这一节把 `Stage 2` 的知识点和 LangChain 官方 API 做一张清晰对照表。

目标不是背 API，而是回答：

- 这个知识点会落到哪个模块
- 这段代码为什么写在这里
- 这个 API 在项目里通常负责哪一层

### 总表

| 课程知识点 | 主要 API / 模块 | 在项目里通常负责什么 |
| --- | --- | --- |
| 高层 Agent 入口 | `langchain.agents.create_agent` | 装配高层 agent 主入口 |
| 工具接入 | `langchain.tools.tool` | 把 Python 函数包装成 agent 可调用工具 |
| 结构化输出 | `response_format` | 让结果变成可验证、可复用结构 |
| Tool strategy | `langchain.agents.structured_output.ToolStrategy` | 用 tool calling 方式完成结构化输出 |
| Human-in-the-loop | `langchain.agents.middleware.HumanInTheLoopMiddleware` | 对敏感工具调用加审核 |
| 短期记忆 | `checkpointer` | 给线程级上下文提供持久化能力 |
| 自定义状态 | `state_schema` | 给 agent 增加自定义状态字段 |
| 中间控制逻辑 | `middleware` | 把控制规则从 prompt 中拆出来 |

### 1. `create_agent`

官方来源：

- [Agents](https://docs.langchain.com/oss/python/langchain/agents)
- [LangChain v1 create_agent](https://docs.langchain.com/oss/python/releases/langchain-v1#create_agent)

它在课程里的意义：

- `Stage 2` 的高层原型入口
- 帮你先把模型、工具、输出和 middleware 装起来

你在项目里看到它时，要先问：

- 这个 agent 的主任务是什么
- 这里挂了哪些工具
- 这里有没有 response_format
- 这里有没有 middleware

### 2. `@tool`

官方来源：

- [Agents](https://docs.langchain.com/oss/python/langchain/agents)

它在课程里的意义：

- 把“外部能力”变成 agent 可调用的标准单元

你在项目里看到它时，要先问：

- 这个工具真的必要吗
- 输入输出是否稳定
- 工具是让主路径更清楚，还是更混乱

### 3. `response_format`

官方来源：

- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)

它在课程里的意义：

- 把“输出长什么样”提前固定下来
- 这是从提示词思维转向系统结构思维的重要节点

你在项目里看到它时，要先问：

- 这个 schema 是给谁消费的
- 它是只给人看，还是还能给系统继续处理
- 哪些字段会决定后续控制逻辑

### 4. `ToolStrategy`

官方来源：

- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)

它在课程里的意义：

- 当模型不能直接走 provider-native structured output 时，用 tool calling 方式完成结构化输出

你在项目里看到它时，要先问：

- 这里为什么要显式指定 `ToolStrategy`
- 这个 schema 验证失败时，系统应该怎么处理

### 5. `HumanInTheLoopMiddleware`

官方来源：

- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)

它在课程里的意义：

- 在高层原型阶段就开始建立审核边界

你在项目里看到它时，要先问：

- 哪些工具需要审核
- 哪些工具不需要审核
- 为什么这里需要 checkpointing

### 6. `checkpointer`

官方来源：

- [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)

它在课程里的意义：

- 给线程级上下文、短期记忆和中断恢复提供持久化基础

你在项目里看到它时，要先问：

- 这里是为了 short-term memory，还是为了处理 interrupts
- 当前线程边界是什么

### 7. `state_schema`

官方来源：

- [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)

它在课程里的意义：

- 在高层层面给 agent 增加更明确的状态字段

你在项目里看到它时，要先问：

- 默认 messages 已经够了吗
- 这里新增状态字段是为了什么
- 这个状态是真需要，还是只是“想记更多”

### 8. `middleware`

官方来源：

- [LangChain v1 create_agent](https://docs.langchain.com/oss/python/releases/langchain-v1#create_agent)
- [Middleware integrations](https://docs.langchain.com/oss/python/integrations/middleware/index)

它在课程里的意义：

- 把系统行为控制从 prompt 里拆出来

你在项目里看到它时，要先问：

- 这里控制的是模型调用、工具调用，还是输入输出
- 这条规则为什么不直接写进 prompt

### 读代码时的固定顺序

以后在 `Stage 2` 看到一份 LangChain 代码，先按这个顺序读：

1. 找 `create_agent`
2. 看 tools
3. 看 `response_format`
4. 看 middleware
5. 看 `checkpointer` / `state_schema`
6. 再看 `invoke` 的输入输出

### 这一节最该记住的话

`Stage 2` 不是让你背很多 LangChain API，而是学会把“主任务、工具、输出、控制逻辑、短期状态”映射到一组清楚的高层接口上。
