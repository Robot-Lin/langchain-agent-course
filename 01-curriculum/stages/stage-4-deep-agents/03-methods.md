# 03 Methods

这一章关注的不是 `Stage 4` 的术语定义，而是拿到一个复杂目标以后，应该怎样把它组织成一个复杂任务型 Agent。

## 方法一: 复杂目标拆解法

面对复杂任务，先拆四层:

1. 总目标
2. 阶段目标
3. 子任务角色
4. 汇总结果

这样做的原因是:

- 不让系统一上来就处理“巨型目标”
- 让复杂任务有可管理层次
- 让汇总结果从一开始就被考虑进去

如果没有这四层，复杂任务很容易在“目标看起来很大”与“子任务各自散跑”之间失控。

## 方法二: context 分层法

建议至少把上下文分成三类:

- 长期资料
- 当前任务状态
- 当前子任务指令

不要把这三类揉成一个巨大 prompt。

一个成熟的 context 分层设计会回答:

- 哪些信息所有角色都要知道
- 哪些信息只属于当前阶段
- 哪些信息只该给某个子任务
- 哪些信息应该在汇总后上收，而不应横向散发

## 方法三: subagent 必要性判断法

每增加一个子代理，都先问 3 个问题:

1. 这个子任务是否明显独立。
2. 它是否需要单独上下文。
3. 它是否真的能降低主代理复杂度。

如果三个问题都答不清，先不要拆。

这一步最重要的不是“拆得多”，而是“拆得值不值”。

## 方法四: 汇总与回收设计法

复杂任务不是“拆完就结束”，还要设计:

- 子代理返回什么
- 主代理如何汇总
- 结果如何进入下一阶段
- 最终输出如何收束

如果没有汇总与回收设计，系统很容易变成:

- 很多子任务都做了
- 结果也很多
- 但没有一个真正围绕总目标收敛

## 方法五: 复杂任务治理法

建议至少设计以下治理点:

- 目标偏航检查
- 关键阶段审批
- 子任务失败回收
- 汇总结果质量检查

复杂任务系统最常见的风险，不是“某一步突然大错”，而是“每一步都像有道理，但整体慢慢偏航”。

所以治理点的作用，不是拖慢系统，而是防止系统越跑越散。

## 方法六: 何时使用 Deep Agents

当任务出现下面这些情况时，优先考虑 Deep Agents:

- 目标复杂到需要主动规划
- 信息组织本身就是核心难点
- 需要多个子任务角色
- 需要更强的复杂任务执行能力

反过来，如果只是:

- 普通审批流
- 中等复杂工作流
- 主流程仍然清楚

那么 `LangGraph` 可能已经足够。

## 方法七: 复杂任务边界说明法

在 `Stage 4`，你应该开始练习写这样一段话:

> 这个任务更适合 Deep Agents，因为它的难点不只在控制流，而在目标拆解、上下文分层、子任务角色分工和结果汇总。单纯画出图还不够，还需要更强的复杂任务组织结构。

这段话很重要，因为它在训练一种能力:

- 不只是会组织复杂任务
- 还知道为什么需要这一层能力

## 方法八: 用 Codex 做复杂任务评审

在 `Stage 4`，最推荐的 AI 协作方式不是让 Codex 直接生成整套复杂任务方案，而是让它扮演:

- 目标拆解评审员
- context 分层评审员
- subagent 必要性审查员
- 汇总与回收评审员
- 复杂任务治理提醒员

推荐提问方式:

- 帮我检查这个总目标是不是拆得还不够清楚。
- 只从 context 分层角度批评我的方案，不要帮我加更多角色。
- 帮我判断哪些子代理是真必要，哪些只是把复杂度重命名。
- 帮我看看我的汇总机制是不是会让结果越来越散。

## Stage 4 的方法目标

真正掌握本阶段，不是“会说 planning、context engineering、subagents 这些词”，而是能把复杂任务整理成一个可执行、可管理、可治理的 Agent 结构。

## 附录：Stage 4 API 对照读法

这一节把 `Stage 4` 的知识点和 Deep Agents 官方 API 做一张清晰对照表。

目标不是背 API，而是回答：

- 这个知识点会落到哪个模块
- 这段代码为什么写在这里
- 这个 API 在项目里通常负责哪一层

### 总表

| 课程知识点 | 主要 API / 模块 | 在项目里通常负责什么 |
| --- | --- | --- |
| 高层入口 | `deepagents.create_deep_agent` | 装配复杂任务 harness 主入口 |
| 主模型 | `model=` / `init_chat_model(...)` | 指定主代理所用模型 |
| 普通工具 | `tools=` | 给主代理接自定义工具 |
| 子代理 | `subagents=` | 提供上下文隔离和角色分工 |
| 运行时上下文 | `context_schema=` / `ToolRuntime[...]` | 向工具和系统层传递 per-run 配置 |
| 始终注入记忆 | `memory=` | 加载 AGENTS.md 等长期上下文 |
| 按需技能 | `skills=` | 提供 progressive disclosure 能力 |
| 风险治理 | `interrupt_on=` | 对敏感工具加审批和编辑控制 |
| 状态持久化 | `checkpointer=` | 支撑 HITL、恢复与长任务 |
| 结构化结果 | `response_format=` | 让复杂任务输出可验证结构 |
| 文件系统与长期记忆 | `backend=` / `store=` | 控制当前线程工作区和跨线程持久化 |

### 1. `create_deep_agent`

官方来源：

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

它在课程里的意义：

- `Stage 4` 的 harness 入口
- 把 planning、filesystem、subagents、memory 和治理能力组织起来

你在项目里看到它时，要先问：

- 这个复杂任务到底为什么需要 harness
- 当前配置里最关键的复杂度来源是什么

### 2. `tools=`

官方来源：

- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

它在课程里的意义：

- 把主代理真正可调用的外部能力接进来

你在项目里看到它时，要先问：

- 这些工具是给主代理还是本该下放给子代理
- 工具描述是否真的能帮助模型正确选用

### 3. `subagents=`

官方来源：

- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)
- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)

它在课程里的意义：

- 把复杂任务拆成具备 context isolation 的子任务结构

你在项目里看到它时，要先问：

- 这个子代理是否真的需要独立上下文
- 子代理返回的是摘要还是原始噪音
- 主代理和子代理的边界是否清楚

### 4. `context_schema=`

官方来源：

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)

它在课程里的意义：

- 把每次运行的静态配置正规化，而不是混进 prompt

你在项目里看到它时，要先问：

- 这是该给模型看的上下文，还是该给工具看的上下文
- 哪些信息应该进 runtime context，哪些不该

### 5. `memory=`

官方来源：

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

它在课程里的意义：

- 注入始终应生效的长期记忆文件

你在项目里看到它时，要先问：

- 这些内容是不是每次都必须加载
- 这里是否错误地把技能材料塞进了 memory

### 6. `skills=`

官方来源：

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

它在课程里的意义：

- 提供按需加载的能力说明和工作流知识

你在项目里看到它时，要先问：

- 这份 skill 是否足够聚焦
- 这里是不是本该拆成 memory 和 skills 两层

### 7. `interrupt_on=`

官方来源：

- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)

它在课程里的意义：

- 为敏感工具配置审批策略

你在项目里看到它时，要先问：

- 哪些工具允许 approve / edit / reject
- 决策列表是否匹配风险等级
- 这里有没有忘记配 checkpointer

### 8. `checkpointer=`

官方来源：

- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)

它在课程里的意义：

- 支撑长任务和人类介入的持久化基础

你在项目里看到它时，要先问：

- 当前只是开发期 saver，还是生产级 saver
- thread_id 是否被稳定复用

### 9. `response_format=`

官方来源：

- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

它在课程里的意义：

- 让复杂任务的结果可以结构化落盘和被下游消费

你在项目里看到它时，要先问：

- 结构化结果是给谁消费的
- 哪些字段会影响后续审核或前端展示

### 10. `backend=` / `store=`

官方来源：

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

它在课程里的意义：

- 决定文件系统、工作区和长期记忆如何分层存储

你在项目里看到它时，要先问：

- 当前工作文件和长期记忆是否被混在一起
- 哪些路径应该路由到 durable store

### 读代码时的固定顺序

以后在 `Stage 4` 看到一份 Deep Agents 代码，先按这个顺序读：

1. 找 `create_deep_agent(...)`
2. 看 `tools=`
3. 看 `subagents=`
4. 看 `context_schema=` / `memory=` / `skills=`
5. 看 `interrupt_on=` / `checkpointer=`
6. 看 `backend=` / `store=`
7. 再看 `response_format=` 和 `invoke(...)`

### 这一节最该记住的话

`Stage 4` 不是让你背 Deep Agents 的配置项，而是学会把“目标拆解、上下文层次、子代理边界、风险治理、长期记忆”映射到一组清楚的 harness 配置上。
