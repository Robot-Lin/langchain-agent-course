# 02 Concepts

这一章的目标不是让你先学 API，而是把 `Stage 3` 中最关键的运行时概念讲清楚。

## 1. LangGraph 是什么

根据官方新版文档，`LangGraph` 是一个用于构建 `stateful`、`long-running` agent systems 的底层编排框架，核心能力包括:

- durable execution
- interrupts
- persistence
- streaming
- human-in-the-loop
- memory 与状态管理

对学习者来说，最重要的理解是:

> `LangGraph` 不是“更复杂的 LangChain”，而是你第一次真正进入 Agent runtime 设计的地方。

参考:

- [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)

## 2. 为什么这里需要图，而不是继续用链式高层原型

链式思维适合主路径非常清楚的任务，例如:

- 接收输入
- 调用工具
- 生成结果

但一旦系统开始出现这些结构，图会更合适:

- 分支
- 循环
- 中断等待
- 审批
- 恢复
- 长生命周期任务

图的价值不在于“形式更高级”，而在于它能把控制流显式化。

这件事非常重要，因为一旦控制流不显式，系统会慢慢变成:

- 只有作者自己看得懂
- 只能靠 prompt 暗示行为
- 失败时很难恢复
- 审批和暂停都像“外挂功能”

## 3. 什么是 state

在 LangGraph 里，`state` 不是附属品，而是系统运行过程中的共享上下文和进度容器。

它通常会包含:

- 原始任务
- 当前阶段
- 当前计划
- 中间结果
- 审批状态
- 错误信息
- 最终结果或待交付内容

设计 state 的关键不在于“存更多”，而在于:

> 只保存真正会影响后续路径、恢复逻辑和审查逻辑的信息。

你可以把 state 理解成“图系统的运行时事实表”。

## 4. 什么是 durable execution

官方文档把 `durable execution` 定义为一种让工作流在故障后能够从中断处继续，而不是从头开始的技术。

在业务里，它真正解决的是:

- 长任务不会因为一次失败就彻底作废
- 审批后可以自然恢复继续执行
- 运行中断不等于整个系统重来

它的意义不是“技术上更强”，而是:

> 让一个工作流在真实环境里更像系统，而不是一次性 demo。

参考:

- [Durable execution](https://docs.langchain.com/oss/python/langgraph/durable-execution)

## 5. 什么是 persistence

`persistence` 是 LangGraph 内置的持久化层，它会保存图状态，使得:

- interrupt 后可以恢复
- 可以查看某一线程的状态
- 执行过程可以跨中断持续

这意味着 persistence 不是“可选增强”，而是很多运行时能力的基础设施。

对学习者来说，最重要的结论是:

> 如果没有 persistence，很多你以为的“审批”“暂停”“恢复”其实都只是表面模拟。

参考:

- [Persistence](https://docs.langchain.com/oss/python/langgraph/persistence)

## 6. 什么是 interrupt

`interrupt` 是正式的图执行暂停点。

它特别适合:

- 等待人工审批
- 等待外部输入
- 高风险动作前暂停
- 方向需要用户确认时暂停

这里最关键的理解是:

> interrupt 不是普通聊天里的追问，而是运行时里的正式暂停与等待。

所以你在 `Stage 3` 学 interrupt，不是在学“多问一句”，而是在学“把暂停设计进系统控制流里”。

参考:

- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)

## 7. 为什么 human-in-the-loop 在这里更完整

在 `Stage 2`，我们已经知道高层也可以接基本的 human-in-the-loop。

到了 `Stage 3`，这件事会变得更完整，因为人工介入不再只是“一个附加检查”，而是会真正嵌入到图里，成为:

- 中断点
- 审批节点
- 恢复分支
- 方向修正机制

这也是为什么很多真正复杂的 HITL 系统最终都会落到 LangGraph 这一层。

## 8. 什么是 streaming

很多人第一次看到 streaming，只会想到“边生成边显示”。

但在 LangGraph 里，streaming 的更深层意义是:

- 用户是否知道系统正在做什么
- 前端是否能同步任务进展
- 长任务是否能保持可见反馈
- 系统是否具备“持续可观察”的运行体验

所以 streaming 不只是 UI 体验问题，它也是运行时透明度的一部分。

参考:

- [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

## 9. state 与 memory 的关系

在 `Stage 1-2`，我们已经知道 memory 不能和知识库混在一起。

到了 `Stage 3`，还要再补一层理解:

- state 更偏向运行中的流程事实
- memory 更偏向跨轮或跨线程需要保留的信息
- LangGraph 管理短期 memory 时，与运行时状态有紧密关系

官方 memory 文档里也明确提到，LangGraph 会把短期 memory 作为线程范围的管理能力来处理。

参考:

- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)

## 10. 分支、恢复与可解释性

一旦你进入 LangGraph，另一个重要变化是:

- 你不能只设计成功路径
- 你必须设计分支和恢复
- 你必须让图的行为可解释

这意味着一个好的图系统，不只是“能走通”，还应该让你回答这些问题:

- 为什么走到了这个分支
- 为什么在这里暂停
- 为什么会回退到这一步
- 为什么恢复后不是从头重来

## 11. 什么时候项目已经明显需要 LangGraph

如果一个项目具备下面这些特征，它通常已经明显需要 LangGraph:

- 流程阶段很明确
- 分支不是偶发，而是系统核心
- 审批和等待是主流程的一部分
- 失败恢复不能只是“重试一次”
- 你需要前端看到运行中的阶段变化

这时继续用高层封装硬撑，系统通常会越来越难解释，也越来越难维护。

## 12. 这一章真正想让你记住的话

进入 `Stage 4` 之前，先记住这句话:

> 当你开始设计阶段、分支、暂停、恢复和可见进度时，你已经不只是在做一个会调用模型的原型，而是在设计一个运行中的系统。

## 13. 代码教材：最小 LangGraph 工作流

这一节不是项目文档，而是 `Stage 3` 的代码教材。

目标很明确：

- 用最小代码示例讲清 `LangGraph` 的 runtime 结构
- 用逐段解释把概念、API 和效果连接起来
- 给后面的项目读图、读码和审核提供“标准参照物”

所有示例都尽量贴近 LangGraph 官方 Docs 的能力主线：

- `StateGraph`
- `START` / `END`
- `add_node`
- `add_edge`
- `add_conditional_edges`
- `interrupt`
- `Command`
- `checkpointer`
- `stream(..., version="v2")`

### 示例 1：最小 `StateGraph`

对应官方文档：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)
- [Graph API overview](https://docs.langchain.com/oss/python/langgraph/graph-api)

```python
from typing_extensions import TypedDict
from langgraph.graph import StateGraph, START, END


class WorkflowState(TypedDict):
    request: str
    status: str


def classify_request(state: WorkflowState):
    return {"status": "classified"}


graph = (
    StateGraph(WorkflowState)
    .add_node("classify_request", classify_request)
    .add_edge(START, "classify_request")
    .add_edge("classify_request", END)
    .compile()
)
```

#### 逐段解释

`class WorkflowState(TypedDict)`

- 这里不是定义数据库模型，而是定义运行时共享状态。
- `Stage 3` 最重要的变化就是：状态成了图系统的正式输入。

`def classify_request(state: WorkflowState)`

- 节点本质上就是读取 state 并返回 state 更新的函数。
- 它不应该偷偷修改外部变量，而应该显式返回更新。

`StateGraph(WorkflowState)`

- 这一步说明整张图围绕哪个 state schema 运行。
- 你后面所有 node、edge、interrupt 都会建立在这个 schema 上。

`add_node(...)`

- 把具体处理逻辑挂到图里。

`add_edge(START, ...)` / `add_edge(..., END)`

- 用显式边把控制流画出来。
- 这也是 LangGraph 和“全靠 prompt 隐式决定”最根本的区别。

### 示例 2：显式分支与条件路由

对应官方文档：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)

```python
from typing import Literal
from typing_extensions import TypedDict
from langgraph.graph import StateGraph, START, END


class ApprovalState(TypedDict):
    approved: bool
    status: str


def review_request(state: ApprovalState):
    return {"status": "reviewed"}


def route_after_review(state: ApprovalState) -> Literal["approved_path", "rejected_path"]:
    return "approved_path" if state["approved"] else "rejected_path"


def approved_path(state: ApprovalState):
    return {"status": "approved"}


def rejected_path(state: ApprovalState):
    return {"status": "rejected"}


builder = StateGraph(ApprovalState)
builder.add_node("review_request", review_request)
builder.add_node("approved_path", approved_path)
builder.add_node("rejected_path", rejected_path)
builder.add_edge(START, "review_request")
builder.add_conditional_edges("review_request", route_after_review)
builder.add_edge("approved_path", END)
builder.add_edge("rejected_path", END)
graph = builder.compile()
```

#### 逐段解释

`route_after_review(...)`

- 这里把“走哪条路径”的判断显式写出来。
- 这比在 prompt 里暗示模型“自己决定下一步”更可解释。

`add_conditional_edges(...)`

- 这是 `Stage 3` 最值得看懂的 API 之一。
- 它让“图为什么走到这里”变成可读、可审查的代码事实。

`approved_path` / `rejected_path`

- 分支不是抽象概念，而是后续节点和状态更新的区别。

### 示例 3：`interrupt` 与 `Command(resume=...)`

对应官方文档：

- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)

```python
from typing import Literal, Optional
from typing_extensions import TypedDict
from langgraph.checkpoint.memory import MemorySaver
from langgraph.graph import StateGraph, START, END
from langgraph.types import Command, interrupt


class ApprovalState(TypedDict):
    action_details: str
    status: Optional[Literal["pending", "approved", "rejected"]]


def approval_node(state: ApprovalState) -> Command[Literal["proceed", "cancel"]]:
    decision = interrupt(
        {
            "question": "Approve this action?",
            "details": state["action_details"],
        }
    )
    return Command(goto="proceed" if decision else "cancel")


def proceed_node(state: ApprovalState):
    return {"status": "approved"}


def cancel_node(state: ApprovalState):
    return {"status": "rejected"}


builder = StateGraph(ApprovalState)
builder.add_node("approval", approval_node)
builder.add_node("proceed", proceed_node)
builder.add_node("cancel", cancel_node)
builder.add_edge(START, "approval")
builder.add_edge("proceed", END)
builder.add_edge("cancel", END)
graph = builder.compile(checkpointer=MemorySaver())
```

#### 逐段解释

`interrupt(...)`

- 这不是普通追问，而是正式的运行时暂停点。
- 它暂停时，图会依赖 persistence / checkpointing 保存状态。

`Command(goto=...)`

- 这里把“恢复后走哪条边”显式返回。
- 它不是给用户看的文字，而是控制流对象。

`compile(checkpointer=MemorySaver())`

- 如果没有 checkpointer，很多 interrupt / resume 场景就只是表面上像，实际上不能稳妥恢复。
- 官方文档也明确把 checkpointing 作为 interrupt 的前提。

### 示例 4：同一节点里同时更新状态并决定下一步

对应官方文档：

- [Use the graph API](https://docs.langchain.com/oss/python/langgraph/use-graph-api)

```python
from typing import Literal
from typing_extensions import TypedDict
from langgraph.graph import StateGraph, START
from langgraph.types import Command


class RouteState(TypedDict):
    route: str


def decide_next_step(state: RouteState) -> Command[Literal["fast_path", "slow_path"]]:
    goto = "fast_path" if state["route"] == "fast" else "slow_path"
    return Command(
        update={"route": state["route"]},
        goto=goto,
    )
```

#### 逐段解释

`Command(update=..., goto=...)`

- 这是 `Stage 3` 很重要的一层理解：
  某些节点不只是算结果，还负责运行时跳转。
- 这让“状态更新”和“控制流决定”可以在一个节点里显式结合。

### 示例 5：`stream(..., version="v2")`

对应官方文档：

- [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

```python
from typing_extensions import TypedDict
from langgraph.graph import StateGraph, START, END


class StreamState(TypedDict):
    topic: str
    joke: str


def generate_joke(state: StreamState):
    return {"joke": f"This is a joke about {state['topic']}"}


graph = (
    StateGraph(StreamState)
    .add_node("generate_joke", generate_joke)
    .add_edge(START, "generate_joke")
    .add_edge("generate_joke", END)
    .compile()
)

for chunk in graph.stream(
    {"topic": "ice cream"},
    stream_mode="updates",
    version="v2",
):
    if chunk["type"] == "updates":
        for node_name, state in chunk["data"].items():
            print(node_name, state)
```

#### 逐段解释

`stream_mode="updates"`

- 这里拿到的不是最终整张 state，而是每一步更新了什么。
- 这对前端显示“系统现在进行到哪一步”特别关键。

`version="v2"`

- 官方现在推荐统一的 `StreamPart` 结构。
- 这样你拿到的 chunk 有稳定的 `type / ns / data` 形状，便于前后端和审核工具一起消费。

### 示例 6：看历史 state，而不是盲猜发生了什么

对应官方文档：

- [Persistence](https://docs.langchain.com/oss/python/langgraph/persistence)

```python
config = {"configurable": {"thread_id": "approval-123"}}

latest_snapshot = graph.get_state(config)
history = list(graph.get_state_history(config))
```

#### 逐段解释

`thread_id`

- 这是运行时线程指针。
- 你要恢复、查看历史、继续审批，都要靠它定位同一条线程。

`graph.get_state(...)`

- 看最新状态快照。
- 它能帮助你回答“当前系统到底停在什么位置”。

`graph.get_state_history(...)`

- 看整条线程的历史检查点。
- 这正是“恢复不是重来”和“审核要看证据”能够成立的基础。

### 这一节最该记住的 5 句话

1. `StateGraph` 不是高级装饰，而是运行时控制流的正式载体。
2. 节点返回的是 state 更新，不是随意副作用。
3. `add_conditional_edges` 让分支显式可解释。
4. `interrupt` 要和 checkpointer、thread_id 一起理解。
5. `stream(..., version="v2")` 和 `get_state_history(...)` 让图系统真正可见、可审、可恢复。
