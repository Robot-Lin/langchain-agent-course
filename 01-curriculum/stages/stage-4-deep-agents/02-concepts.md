# 02 Concepts

这一章的目标不是让你背 API，而是把 `Stage 4` 中最关键的复杂任务概念讲清楚。

## 1. Deep Agents 是什么

根据官方新版文档，`Deep Agents` 是一个面向复杂任务的高层入口，强调复杂任务处理、planning、context engineering 和更强的任务完成能力。

它适合的不是所有 Agent，而是那些真正具备下面特征的任务:

- 目标复杂
- 任务长
- 资料多
- 需要拆子任务
- 需要在执行中持续修正

对学习者来说，最重要的理解是:

> Deep Agents 解决的不是“普通任务做得更快”，而是“复杂任务怎样被组织得更清楚”。

参考:

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [When to use the Deep Agents SDK](https://docs.langchain.com/oss/python/concepts/products#when-to-use-the-deep-agents-sdk)

## 2. 什么任务开始适合 Deep Agents

如果任务具备下面这些特征，就开始更像 Deep Agents 场景:

- 目标开放而复杂
- 单一线性流程难以覆盖
- 子任务差异明显
- 需要多个角色视角
- 中间结果必须被汇总与回收
- 需要持续纠偏和治理

反过来，如果任务只是:

- 明确流程
- 固定阶段
- 中等复杂度审批与恢复

那么很多时候 `LangGraph` 已经足够，不一定需要 Deep Agents。

## 3. 什么是 planning

在复杂任务里，planning 不只是“列步骤”，而是:

- 理解目标
- 划分阶段
- 决定顺序
- 识别依赖
- 在执行中修正路径

所以 planning 的价值不在于“让系统看起来聪明”，而在于:

> 让复杂目标被分解成可管理的阶段性推进过程。

## 4. 什么是 context engineering

官方文档强调，context engineering 是为模型提供合适上下文的工程，而不是简单“多给点资料”。

这里最关键的是 3 件事:

- 给对的信息
- 在对的时机给
- 给到对的角色

这通常意味着:

- 长期资料和当前任务状态分层
- 子任务上下文隔离
- 汇总上下文与执行上下文分开

也就是说，context engineering 的核心不是“更多”，而是“更有组织”。

参考:

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)

## 5. 什么是 subagents

subagents 不只是“多开几个 agent”。

它们更适合出现于这些场景:

- 子任务天然独立
- 子任务需要不同视角或角色
- 子任务需要单独上下文
- 主代理不应该持有所有细节

subagents 的真正价值是:

- 降低主代理负担
- 提高任务分解清晰度
- 让复杂任务的组织结构更可控

如果一个子代理并没有带来上下文隔离、职责独立或复杂度降低，那它很可能只是“把复杂度重新命名”。

## 6. customization 与边界

官方 customization 文档说明了 Deep Agents 可以配置其核心行为。课程里的重点不是参数，而是判断:

- 什么能力应该交给主代理
- 什么能力应该拆给子代理
- 什么上下文应该被隔离
- 什么地方必须留给人类确认

这意味着，Deep Agents 的 customization 不是“调更多旋钮”，而是:

> 为复杂任务设计更清楚的任务组织边界。

参考:

- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

## 7. human-in-the-loop 在复杂任务里的意义

复杂任务并不意味着彻底自动化，很多时候反而更需要人类在关键阶段介入。

比如:

- 目标方向确认
- 关键中间结论审核
- 最终输出前纠偏
- 高风险外部动作确认

官方 Deep Agents 文档也明确说明，HITL 是通过 LangGraph 的 interrupt 能力支撑的。

这说明一个重要事实:

> 复杂任务越长、越开放、越难完全定义，就越需要正式治理点，而不是越应该放手让系统自己跑到底。

参考:

- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)

## 8. 复杂任务的真正难点不是工具，而是组织

很多学习者会误以为复杂任务主要难在:

- 工具多
- 数据多
- 步骤多

这些当然重要，但真正更难的通常是:

- 目标怎么拆
- 上下文怎么分层
- 子任务怎么分工
- 结果怎么回收
- 偏航怎么治理

也就是说，复杂任务型 Agent 的难点，常常不只是“流程复杂”，而是“任务组织本身复杂”。

## 9. 复杂任务为什么容易失控

复杂任务系统的风险往往不是单点失败，而是逐步偏航。

典型风险包括:

- 主目标被淡化
- 子任务各自做得很好，但整体跑偏
- 上下文越堆越乱
- 子代理边界不清，结果重复或冲突
- 汇总阶段把一堆零散内容拼在一起，无法收束

所以在 `Stage 4`，治理的意义非常重要。你不是只要“能拆”，还要“能收”。

## 10. Deep Agents 与 LangGraph 的关系

一个很容易误解的问题是: Deep Agents 是不是“替代”了 LangGraph。

不是。

更准确的理解是:

- LangGraph 解决运行时控制与流程编排
- Deep Agents 更强调复杂任务组织层

所以 `Stage 4` 不是在离开 LangGraph，而是在它之上进入更复杂的任务组织维度。

## 11. 什么时候不该用 Deep Agents

下面这些情况通常不必急着用 Deep Agents:

- 主任务很清楚
- 流程阶段明确但不复杂
- 没有明显子任务角色差异
- 控制流难度大于目标组织难度

这些情况下，`LangGraph` 或者更高层的 `LangChain` 往往已经足够。

## 12. 这一章真正想让你记住的话

进入 `Stage 5` 之前，先记住这句话:

> 复杂任务型 Agent 的难点，不只是流程更复杂，而是目标拆解、上下文组织、角色分工和治理设计都开始成为系统核心。

## 13. 代码教材：最小 Deep Agent 原型

这一节不是项目文档，而是 `Stage 4` 的代码教材。

目标很明确：

- 用最小代码示例讲清 `Deep Agents` 如何把复杂任务组织起来
- 用逐段解释把概念、API 和效果连接起来
- 给后面的项目读码、读主代理和读子代理提供“标准参照物”

所有示例都尽量贴近官方最新版 Deep Agents 文档的能力主线：

- `create_deep_agent`
- 内建 planning / `write_todos`
- context management / filesystem backends
- subagents
- `memory`
- `interrupt_on`
- `response_format`

### 示例 1：最小 `create_deep_agent`

对应官方文档：

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)

```python
from deepagents import create_deep_agent


def get_weather(city: str) -> str:
    """Get weather for a given city."""
    return f"It's always sunny in {city}!"


agent = create_deep_agent(
    tools=[get_weather],
    system_prompt="You are a helpful assistant.",
)

result = agent.invoke(
    {
        "messages": [
            {"role": "user", "content": "What is the weather in sf?"}
        ]
    }
)
```

#### 逐段解释

`from deepagents import create_deep_agent`

- 这是最新版 Deep Agents 的高层入口。
- 它不是普通 `create_agent` 的同义词，而是复杂任务 harness 的入口。

`tools=[get_weather]`

- 你仍然可以传普通工具。
- 但 Deep Agents 的真正差别不只在工具，而在内建任务组织能力。

`system_prompt=...`

- 依然重要，但系统真正变强的地方不只是 prompt，而是 planning、context 和 subagents 的内建组织能力。

### 示例 2：把复杂任务交给 harness，而不是手工堆 planner

对应官方文档：

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)

```python
from deepagents import create_deep_agent


agent = create_deep_agent(
    model="openai:gpt-5.2",
    system_prompt=(
        "You are a research assistant. "
        "Break complex work into clear steps and keep progress visible."
    ),
)
```

#### 逐段解释

这一段看起来很短，但课程里最重要的理解是：

- Deep Agents 自带 planning 和复杂任务 harness
- 你不是从零开始自己手搓一个 planner、task queue 和 subagent loop
- 这也是它和纯 LangGraph 工作流的一个关键差异

官方文档里把这条线讲得很明确：

- built-in task planning
- subagent spawning
- file systems for context management
- long-term memory

### 示例 3：显式加 `subagents`

对应官方文档：

- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)
- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)

```python
from deepagents import create_deep_agent


def web_search(query: str) -> str:
    """Search the web for a topic."""
    return f"Search results for: {query}"


agent = create_deep_agent(
    tools=[web_search],
    subagents=[
        {
            "name": "researcher",
            "description": "Conducts focused research on a topic",
            "system_prompt": (
                "You are a research subagent. "
                "Return only a concise synthesis, not raw search logs."
            ),
            "tools": [web_search],
        }
    ],
)
```

#### 逐段解释

`subagents=[...]`

- 这里不是简单“多开一个 agent”。
- 真正要看的是：为什么这个子代理值得存在，它隔离了什么上下文。

`system_prompt` for subagent

- 子代理不是主代理 prompt 的复制品。
- 它通常应该有更窄、更清楚的角色边界。

`Return only a concise synthesis`

- 这是课程里特别重要的一点：
  子代理存在的价值之一，就是把重工作隔离掉，然后把结果压缩回主代理。

### 示例 4：`context_schema` 与运行时上下文

对应官方文档：

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)

```python
from dataclasses import dataclass
from deepagents import create_deep_agent
from langchain.tools import tool, ToolRuntime


@dataclass
class Context:
    user_id: str
    role: str


@tool
def fetch_user_data(query: str, runtime: ToolRuntime[Context]) -> str:
    """Fetch data for the current user."""
    return f"Data for user {runtime.context.user_id}: {query}"


agent = create_deep_agent(
    tools=[fetch_user_data],
    context_schema=Context,
)
```

#### 逐段解释

`context_schema=Context`

- 这是官方最新版里非常值得注意的一点。
- runtime context 并不会自动变成 prompt 文本，而是作为每次运行的静态配置传下去。

`ToolRuntime[Context]`

- 工具可以直接读 runtime context。
- 这让“用户元数据 / 权限 / API key / feature flag”这类东西不需要硬塞进 prompt。

这也是 context engineering 的一个核心升级：

- 不是把所有信息都变成模型可见文本
- 而是把该给工具和系统层的信息放在 runtime context

### 示例 5：`memory` 和 AGENTS.md

对应官方文档：

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

```python
from deepagents import create_deep_agent


agent = create_deep_agent(
    memory=["/project/AGENTS.md", "~/.deepagents/preferences.md"],
)
```

#### 逐段解释

`memory=[...]`

- 这里的 memory 在 Deep Agents 里通常不是“对话里临时记住一句话”。
- 它更像始终注入的记忆文件，常常用来放项目约定、偏好和长期指令。

课程里要特别记住：

- memory 是 always loaded
- skills 是按需 progressive disclosure

也就是说：

- 记忆放“总是重要”的东西
- 技能放“按需展开”的工作流知识

### 示例 6：`interrupt_on` 和人类审核

对应官方文档：

- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)

```python
from langchain.tools import tool
from deepagents import create_deep_agent
from langgraph.checkpoint.memory import MemorySaver


@tool
def delete_file(path: str) -> str:
    """Delete a file."""
    return f"Deleted {path}"


@tool
def read_file(path: str) -> str:
    """Read a file."""
    return f"Contents of {path}"


checkpointer = MemorySaver()

agent = create_deep_agent(
    tools=[delete_file, read_file],
    interrupt_on={
        "delete_file": True,
        "read_file": False,
    },
    checkpointer=checkpointer,
)
```

#### 逐段解释

`interrupt_on={...}`

- 这说明 Deep Agents 的人类审核并不是抽象概念，而是工具级别的风险控制。

`checkpointer=checkpointer`

- 官方文档明确要求：human-in-the-loop 需要 checkpointer。
- 这再次说明 Deep Agents 仍然建立在 LangGraph runtime 能力之上。

### 示例 7：`response_format`

对应官方文档：

- [Customize Deep Agents](https://docs.langchain.com/oss/python/deepagents/customization)

```python
from pydantic import BaseModel, Field
from deepagents import create_deep_agent


class ResearchReport(BaseModel):
    summary: str = Field(description="Short summary of the research result")
    key_findings: list[str] = Field(description="Main findings")
    open_questions: list[str] = Field(description="What remains unclear")


agent = create_deep_agent(
    tools=[],
    response_format=ResearchReport,
)
```

#### 逐段解释

`response_format=ResearchReport`

- Deep Agents 也支持 structured output。
- 这很重要，因为复杂任务不是只能输出长文本报告，也可以输出可被后续系统消费的结构。

`structured_response`

- 官方文档说明结构化结果会落在 deep agent state 的 `structured_response` 里。
- 这也是后面前端渲染和自动审核的重要基础。

### 示例 8：用后端区分“当前线程工作区”和“长期记忆”

对应官方文档：

- [Context engineering in Deep Agents](https://docs.langchain.com/oss/python/deepagents/context-engineering)

```python
from deepagents import create_deep_agent
from deepagents.backends import CompositeBackend, StateBackend, StoreBackend
from langgraph.store.memory import InMemoryStore


def make_backend(runtime):
    return CompositeBackend(
        default=StateBackend(runtime),
        routes={"/memories/": StoreBackend(runtime)},
    )


agent = create_deep_agent(
    store=InMemoryStore(),
    backend=make_backend,
    system_prompt=(
        "Save durable user preferences under /memories/ when they are important "
        "across future conversations."
    ),
)
```

#### 逐段解释

`CompositeBackend(...)`

- 这是课程里特别值得讲清的地方：
  Deep Agents 的 context 管理不只是“给上下文”，还包括“把信息存到哪里”。

`default=StateBackend(runtime)`

- 当前线程内工作区。

`routes={"/memories/": StoreBackend(runtime)}`

- 把某些路径路由到跨线程持久层。

这正是官方文档里 long-term memory 的核心思想：

- 不是所有文件都长期保存
- 只有某些路径进入 durable store

### 这一节最该记住的 6 句话

1. `create_deep_agent` 是复杂任务 harness 的高层入口。
2. Deep Agents 的强项不只是工具，而是 planning、context 和 subagents 的内建组织。
3. 子代理的价值在于 context isolation，而不是“多开几个角色”。
4. runtime context、memory、skills、backend 各有职责，不该混成一个大 prompt。
5. `interrupt_on` 和 `checkpointer` 说明复杂任务仍然要正式治理。
6. Deep Agents 也支持 structured output，所以复杂任务结果同样可以被系统化消费。
