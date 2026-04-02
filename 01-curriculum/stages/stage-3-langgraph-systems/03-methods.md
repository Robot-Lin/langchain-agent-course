# 03 Methods

这一章关注的不是 `Stage 3` 的概念定义，而是拿到一个复杂任务以后，应该怎样把它设计成图系统。

## 方法一: 图式设计四步法

面对一个 LangGraph 项目，先做四步:

1. 先画主路径
2. 再补关键分支
3. 再补失败与恢复
4. 最后补审批与人工介入

这个顺序很重要，因为它能防止你一开始就陷入“图越画越乱”的状态。

四步的意义分别是:

- 主路径帮助你定住系统主骨架
- 分支说明系统真的有决策结构
- 恢复说明系统能在真实环境里工作
- 审批说明系统知道什么时候该停下来

## 方法二: state 最小集设计法

每设计一个 state 字段，都先问 3 个问题:

1. 这个信息会不会影响后续路径。
2. 这个信息是不是恢复执行时必须知道。
3. 这个信息是不是审批、回显或状态展示时必须展示。

如果三个问题都是否，那通常先不要放进 state。

这一步最容易犯的错误就是“为了保险把所有东西都塞进去”。

成熟的 state 设计追求的是:

- 足够支持运行
- 足够支持恢复
- 足够支持解释
- 但不过载

## 方法三: interrupt 门设计法

给工作流明确设置中断门。

常见位置包括:

- 调用高风险工具前
- 提交最终结果前
- 外部输入缺失时
- 任务方向需要用户确认时

interrupt 的核心不是“停”，而是:

> 停在最该停的位置，并且停下来以后能继续。

所以设计 interrupt 时至少要回答:

- 为什么这里必须停
- 谁来决定是否继续
- 继续时从哪里恢复
- 拒绝后走哪条分支

## 方法四: 恢复路径设计法

不要只设计成功路径。至少补三类恢复:

- 工具失败后的恢复
- 审批拒绝后的恢复
- 输入不足时的恢复

一个成熟的恢复路径设计，应该避免两种糟糕情况:

- 一失败就从头开始
- 一失败就让用户完全接管，没有系统支持

恢复设计的目标不是“保证永不失败”，而是:

> 让失败变成图里可处理的状态，而不是系统崩掉后的空白。

## 方法五: 显式分支设计法

很多新手其实已经遇到了分支，只是还在用 prompt 暗示模型“自己决定”。

在 LangGraph 阶段，要刻意把分支显式化。

比如:

- 审批通过 / 拒绝
- 信息足够 / 不足
- 工具成功 / 失败
- 需要继续 / 可以结束

你不需要把所有可能都画成图，但需要把真正影响路径的判断显式画出来。

## 方法六: streaming 与前端可见性设计法

在 LangGraph 里，streaming 不是装饰，而是运行反馈的一部分。

所以在设计工作流时，建议同步思考:

- 哪些阶段需要对用户可见
- 哪些中间状态值得前端显示
- 哪些暂停点需要明确提示原因

这一步会帮助你避免一个常见问题:

- 系统内部其实跑了很多步骤
- 但用户体验上像“卡住了”

## 方法七: 从 LangChain 升级到 LangGraph 的判断法

如果项目开始出现下面这些情况，优先考虑升级:

- 你想显式控制流程，而不是让模型隐式决定
- 你需要正式暂停和恢复
- 你需要把任务拆成清楚节点
- 你需要运行中状态可见
- 你需要图层级的可解释性

换句话说，升级到 LangGraph 的信号，不是“我想用更高级的框架”，而是:

> 我的任务结构已经要求我把控制逻辑显式建模。

## 方法八: 图式复盘法

每次复盘都检查:

- state 是否过重或过轻
- 分支是否真的必要
- interrupt 是否放对位置
- 恢复是否只是“从头重来”
- 前端是否能看见执行状态

一个高质量复盘，不只是检查图能不能画出来，而是检查图能不能支撑真实任务。

## 方法九: 用 Codex 做图系统评审

在 `Stage 3`，最推荐的 AI 协作方式不是让 Codex 直接替你画完整图，而是让它扮演:

- state 审查员
- interrupt 审查员
- 恢复路径审查员
- LangChain / LangGraph 分界提醒员
- 工作流可解释性评审员

推荐提问方式:

- 帮我检查这套 state 里哪些字段其实不该放进去。
- 帮我判断我的 interrupt 是否停在正确位置。
- 只从恢复路径角度批评我的图，不要帮我加更多能力。
- 帮我看看这个系统是不是已经真的比 Stage 2 更适合 LangGraph。

## Stage 3 的方法目标

真正掌握本阶段，不是“会画图”，而是能把复杂任务的控制逻辑、状态逻辑和恢复逻辑设计成一个可解释、可恢复、可审核的系统。

## 附录：Stage 3 API 对照读法

这一节把 `Stage 3` 的知识点和 LangGraph 官方 API 做一张清晰对照表。

目标不是背 API，而是回答：

- 这个知识点会落到哪个模块
- 这段代码为什么写在这里
- 这个 API 在项目里通常负责哪一层

### 总表

| 课程知识点 | 主要 API / 模块 | 在项目里通常负责什么 |
| --- | --- | --- |
| 图入口 | `langgraph.graph.StateGraph` | 定义整张图围绕哪个 state 运行 |
| 图起止点 | `START` / `END` | 明确控制流的起点与终点 |
| 节点接入 | `add_node` | 把处理逻辑挂到图里 |
| 顺序边 | `add_edge` | 定义固定控制流 |
| 条件边 | `add_conditional_edges` | 定义显式路由与分支 |
| 运行中跳转 | `langgraph.types.Command` | 同时更新状态并决定下一步 |
| 动态暂停 | `langgraph.types.interrupt` | 设置正式暂停点并等待外部输入 |
| 持久化 | `compile(checkpointer=...)` | 让 interrupt、恢复、历史状态成立 |
| 线程状态读取 | `get_state` / `get_state_history` | 读取快照与历史检查点 |
| 运行反馈 | `stream(..., version=\"v2\")` | 把更新、消息和任务事件流式输出 |

### 1. `StateGraph`

官方来源：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)
- [Graph API overview](https://docs.langchain.com/oss/python/langgraph/graph-api)

它在课程里的意义：

- `Stage 3` 的 runtime 入口
- 告诉你整张图的共享 state 是什么

你在项目里看到它时，要先问：

- 这个 state schema 是否过重或过轻
- 图是围绕什么运行事实在组织

### 2. `START` / `END`

官方来源：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)

它在课程里的意义：

- 把控制流起点和终点显式化

你在项目里看到它时，要先问：

- 这条主路径是如何进入图的
- 图在哪些条件下真正结束

### 3. `add_node`

官方来源：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)

它在课程里的意义：

- 把处理逻辑和图结构连接起来

你在项目里看到它时，要先问：

- 这个节点负责什么
- 它返回的 state 更新是否足够清楚
- 这里有没有不该放进节点的副作用

### 4. `add_edge`

官方来源：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)

它在课程里的意义：

- 表达固定顺序路径

你在项目里看到它时，要先问：

- 这条边是不是固定必经
- 这里有没有本该显式分支却被硬塞成顺序路径

### 5. `add_conditional_edges`

官方来源：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)

它在课程里的意义：

- 把路由判断显式写出来

你在项目里看到它时，要先问：

- 条件函数到底基于哪些 state 字段在判断
- 路由是否真的覆盖了关键分支
- 这条判断是不是应该被审核

### 6. `Command`

官方来源：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)

它在课程里的意义：

- 让节点可以同时做状态更新和控制流跳转

你在项目里看到它时，要先问：

- 这里为什么不用普通 edge
- 这个节点是不是既在更新 state，又在决定 goto
- `Command(resume=...)` 是在图输入侧恢复，还是在节点返回侧跳转

### 7. `interrupt`

官方来源：

- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)

它在课程里的意义：

- 正式暂停图执行，等待外部输入

你在项目里看到它时，要先问：

- 这里为什么必须停
- payload 是否是 JSON 可序列化
- 节点在 resume 时会不会重跑前半段逻辑
- 这里前面的副作用是否幂等

### 8. `compile(checkpointer=...)`

官方来源：

- [Persistence](https://docs.langchain.com/oss/python/langgraph/persistence)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)

它在课程里的意义：

- 让 checkpoint、interrupt、恢复和历史快照真正可用

你在项目里看到它时，要先问：

- 当前用的是开发期 saver 还是生产级 saver
- 这条线程如何用 `thread_id` 定位

### 9. `get_state` / `get_state_history`

官方来源：

- [Persistence](https://docs.langchain.com/oss/python/langgraph/persistence)

它在课程里的意义：

- 让你能从“我猜系统停在哪里”升级到“我直接看快照和历史”

你在项目里看到它时，要先问：

- 当前快照反映的是哪个 super-step
- 我是要看最新状态，还是整条线程历史

### 10. `stream(..., version=\"v2\")`

官方来源：

- [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

它在课程里的意义：

- 让运行中的图对前端和调试层可见

你在项目里看到它时，要先问：

- 这里到底需要 `updates`、`values`、`messages` 还是 `custom`
- 为什么这里要显式用 `version=\"v2\"`
- 前端到底消费的是哪个 `chunk[\"type\"]`

### 读代码时的固定顺序

以后在 `Stage 3` 看到一份 LangGraph 代码，先按这个顺序读：

1. 找 `StateGraph(...)`
2. 看 state schema
3. 看 `add_node`
4. 看 `add_edge` / `add_conditional_edges`
5. 看 `interrupt` / `Command`
6. 看 `compile(checkpointer=...)`
7. 再看 `invoke` / `stream` / `get_state_history`

### 这一节最该记住的话

`Stage 3` 不是让你背很多 LangGraph API，而是学会把“状态、节点、分支、暂停、恢复、可见性”映射到一组显式的运行时接口上。
