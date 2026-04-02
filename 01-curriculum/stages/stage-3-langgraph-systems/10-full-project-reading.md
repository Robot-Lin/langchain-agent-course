# 10 Full Project Reading

这一节是 `Stage 3` 的全项目读图入口。

目标不是只看 1 到 2 个关键节点，而是把一个 LangGraph 项目当成完整系统来理解：

- 整体目录如何组织
- 哪些文件定义 state
- 哪些文件定义 nodes
- 哪些文件负责 routing / interrupt / resume
- 哪些地方接 checkpointer、streaming 和状态查询

## 全项目阅读顺序

### 第一步：先找图入口

优先找这些位置：

- `StateGraph(...)`
- `builder = StateGraph(...)`
- `graph = builder.compile(...)`

先回答：

- 这张图围绕什么 state schema 运行
- 哪些节点被接进来了
- 有没有显式 `checkpointer`

### 第二步：读 state 文件或 state 区块

优先看：

- `TypedDict` / `Pydantic` state schema
- reducer 定义
- 与审批、恢复、回显相关的字段

先回答：

- 哪些字段决定主路径
- 哪些字段用于 interrupt / resume
- 哪些字段只为前端状态展示服务

### 第三步：读 nodes

逐个看 node 时，不要先纠结细节，先记录三件事：

- 输入依赖哪些 state 字段
- 返回更新了哪些 state 字段
- 有没有副作用、工具调用或 `interrupt`

## 第四步：读 router 和分支逻辑

优先找：

- `add_conditional_edges(...)`
- 返回 `Command(goto=...)` 的节点
- 命名像 `route_*`、`decide_*`、`branch_*` 的函数

先回答：

- 分支判断基于哪些 state
- 哪些分支是核心路径，哪些是失败路径
- 拒绝、失败、重试是否有明确去向

## 第五步：读 interrupt / resume 设计

优先找：

- `interrupt(...)`
- `Command(resume=...)`
- `thread_id`
- `graph.invoke(...)` / `graph.stream(...)` 的恢复调用

先回答：

- 为什么停在这里
- resume 后会回到哪个节点
- 这个节点 resume 时会不会重跑前半段逻辑
- interrupt 前的副作用是否幂等

## 第六步：读 persistence 和状态历史

优先找：

- `compile(checkpointer=...)`
- `graph.get_state(...)`
- `graph.get_state_history(...)`

先回答：

- 当前项目是否真的有 persistence 基础
- 审批、恢复、调试是否依赖 `thread_id`
- 审核时能不能拿历史检查点当证据

## 第七步：读 streaming 与前端消费点

优先找：

- `graph.stream(...)` / `graph.astream(...)`
- `stream_mode`
- `version="v2"`
- 消费 `chunk["type"]` 的前端或服务端代码

先回答：

- 前端到底看到的是 `updates`、`values` 还是 `messages`
- 哪个节点更新最适合显示给用户
- interrupt 信息是如何暴露到界面层的

## 读完整个项目后必须能回答的 10 个问题

1. 这张图的唯一主任务是什么。
2. 哪个 state 字段最关键。
3. 哪个节点最像主路径起点。
4. 哪个 router 或 `Command` 最决定后续走向。
5. 项目里最关键的 interrupt 在哪里。
6. 为什么 resume 后不是从头重来。
7. 这张图依赖什么 checkpointer。
8. 前端或调用方如何知道图当前运行到哪。
9. 如果要审核，最该先看哪 3 个文件。
10. 这套系统为什么已经不能只留在 LangChain 高层原型。

## 推荐给 Codex 的说法

- 请不要只挑 2 个重点模块，带我把这个 LangGraph 项目按目录完整扫一遍。
- 先讲整图结构，再讲 state，再讲 nodes，再讲 router、interrupt 和 persistence。
- 每看完一层都让我自己复述，如果我讲不清楚就先不要进入下一层。
- 最后请你像评审一样指出这整套图最值得先检查的 3 个风险点。
