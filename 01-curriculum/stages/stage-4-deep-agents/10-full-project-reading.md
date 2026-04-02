# 10 Full Project Reading

这一节是 `Stage 4` 的全项目读码入口。

目标不是只看 1 到 2 个关键角色，而是把一个 Deep Agents 项目当成完整系统来理解：

- 整体目录如何组织
- 哪些文件定义主代理
- 哪些文件定义子代理
- 哪些地方定义 context、memory、skills 和 backend
- 哪些地方定义治理点、审核点和 structured output

## 全项目阅读顺序

### 第一步：先找 harness 入口

优先找这些位置：

- `create_deep_agent(...)`
- 主代理配置对象
- `agent.invoke(...)`

先回答：

- 主代理到底承担什么总目标
- 这个项目为什么不是普通 LangChain 或 LangGraph 就够了
- 当前最关键的复杂度来自哪里

### 第二步：读主代理配置

优先看：

- `model=`
- `tools=`
- `subagents=`
- `context_schema=`
- `memory=` / `skills=`
- `interrupt_on=`
- `backend=` / `store=`

先回答：

- 哪些能力属于主代理
- 哪些能力被下放到子代理
- 哪些上下文是 always loaded，哪些是 on-demand

### 第三步：读子代理

逐个看子代理时，先记录三件事：

- 它为什么存在
- 它隔离了什么上下文
- 它返回给主代理的是什么级别的结果

## 第四步：读 context、memory 和 skills

优先找：

- `context_schema`
- `ToolRuntime[...]`
- `memory=[...]`
- `skills=[...]`
- `AGENTS.md` / `SKILL.md`

先回答：

- 哪些信息是 runtime context
- 哪些信息是长期记忆
- 哪些信息是按需展开的技能
- 哪些东西被错误地混成了一个大 prompt

## 第五步：读 backend 和长期记忆

优先找：

- `backend=`
- `store=`
- `CompositeBackend`
- `StateBackend`
- `StoreBackend`

先回答：

- 当前线程工作区存在哪里
- 长期记忆存在哪里
- 哪些路径会进入 durable store

## 第六步：读治理与人工审核

优先找：

- `interrupt_on=`
- `checkpointer=`
- 子代理上的局部 `interrupt_on`
- review / approval / quality check 相关逻辑

先回答：

- 哪些操作需要审批
- 审批后如何恢复
- 复杂任务偏航时，系统怎么被拉回主目标

## 第七步：读 structured output 与结果回收

优先找：

- `response_format=`
- `structured_response`
- 汇总节点或汇总函数

先回答：

- 子代理返回的是原始噪音还是收束后的结果
- 主代理最终如何把结果压成统一输出
- 前端和审核层消费的到底是什么结构

## 读完整个项目后必须能回答的 10 个问题

1. 这个项目的总目标为什么适合 Deep Agents。
2. 主代理最核心的职责是什么。
3. 哪个子代理最关键，它为什么值得存在。
4. 哪一层在做 context isolation。
5. 哪些内容属于 memory，哪些属于 skills。
6. 长期记忆和当前线程工作区是如何分开的。
7. 哪些工具或动作设置了 interrupt_on。
8. 最终结果是如何被汇总和收束的。
9. 如果要审核，最该先看哪 3 个文件。
10. 这套系统为什么不能只是“多开几个 agent”这么简单。

## 推荐给 Codex 的说法

- 请不要只挑 2 个重点模块，带我把这个 Deep Agents 项目按目录完整扫一遍。
- 先讲主代理，再讲子代理，再讲 context、memory、skills、backend 和治理层。
- 每看完一层都让我自己复述，如果我讲不清楚就先不要进入下一层。
- 最后请你像评审一样指出这整套复杂任务系统最值得先检查的 3 个风险点。
