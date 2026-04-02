# 02 Concepts

这一章的目标不是让你背 API，而是把 `Stage 2` 中最关键的高层概念讲清楚。

## 1. LangChain 在新版体系里的角色

根据官方新版文档，`LangChain` 是一个高层开源框架，提供了 prebuilt agent architecture 和丰富的模型、工具集成，帮助你快速搭建自定义 agent。

更重要的是，官方也明确说了: LangChain 的 agents 构建在 `LangGraph` 之上。

这意味着:

- 你现在用的是高层入口
- 但它不是“脱离 runtime 的轻包装”
- 而是把复杂度放在更合适的层次处理

对学习者来说，最重要的理解是:

> `LangChain` 的价值不只是少写代码，而是帮助你更快地把一个 Agent 设计组织成高层原型。

参考:

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [Agents](https://docs.langchain.com/oss/python/langchain/agents)

如果你想立刻把这一节对到代码，直接继续读本文件后半部分的“代码教材：最小 LangChain 原型”。

## 2. 什么是高层 Agent 原型

在这套课程里，高层 Agent 原型指的是这样一种系统:

- 已经有清楚的任务目标
- 已经接入必要工具
- 已经定义清楚输出结构
- 已经有基础控制逻辑
- 已经能处理主路径
- 已经有最基础的失败和审核意识

但它通常还没有:

- 复杂状态机
- 明显的多分支长流程
- durability / resume 设计
- 复杂 interrupt / recovery 逻辑
- 多 Agent 编排

你可以把它理解成:

> 它已经不只是想法，但也还不是复杂系统。

## 3. Agents 与 `create_agent`

LangChain 官方在新版 agents 文档中把 `create_agent` 作为高层入口之一。这个信号很重要，因为它说明官方鼓励开发者先从统一、高层、可快速成型的 agent 入口开始，而不是从零散组件乱拼。

对课程设计来说，这意味着 `Stage 2` 的重点不是“手工堆很多底层零件”，而是先学会:

- 如何定义模型角色
- 如何挂接工具
- 如何规定输出
- 如何附加 middleware
- 如何理解系统边界

也就是说，你在这一章学的是“怎么组织一个 agent”，而不只是“怎么调用一个模型”。

## 4. Tools 的真正价值

在 `Stage 1`，我们已经知道工具是 Agent 接触外部世界的桥。到 `Stage 2`，你要再往前走一步:

> 工具不只是“能力扩展”，还是高层原型边界设计的一部分。

一个高层原型里的工具最值得看的是:

- 这个工具是否真的必要
- 输入输出是否稳定
- 工具说明是否清楚
- 工具是否让任务更清楚，而不是更乱

在 `LangChain` 里，工具接入被统一进 agent 架构里，这让学习者可以先聚焦“任务和能力怎么组织”，而不是一开始被底层编排细节淹没。

## 5. Structured output 为什么特别重要

`structured output` 是 `Stage 2` 里最值得优先建立的习惯之一。

因为一旦你进入高层 Agent 原型开发，系统输出就不该只是一段“看起来回答得不错”的自然语言，而应该尽量变成:

- 可解析
- 可验证
- 可复用
- 可传给后续系统
- 可交给前端渲染

官方文档也明确指出，structured output 允许 agents 输出符合 schema 的结构化结果。

参考:

- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)

对应代码教材：

- 本文件后半部分的“示例 3：先设计 structured output”
- [03-methods.md](./03-methods.md) 末尾附录里的 `response_format`、`ToolStrategy`

对学习者来说，最重要的结论是:

> 在高层 Agent 原型里，先设计输出结构，再去设计 prompt，通常会更稳。

## 6. Middleware 是高层控制逻辑的关键层

很多新手会把所有规则都塞进 prompt 里，例如:

- 什么时候可以调用工具
- 什么时候要先问用户
- 什么时候要做风险拦截
- 什么时候要人工审核

这样做短期看起来快，长期会很乱。

`middleware` 的意义，就是把这些“系统行为控制”从 prompt 的混合文本里剥出来，放到更清楚、更可维护的位置。

在 `Stage 2`，你不需要把 middleware 学得很深，但要先建立一个意识:

> 不是所有控制逻辑都应该写进 prompt。很多关键规则更适合放在 middleware 或系统控制层。

参考:

- [Middleware integrations](https://docs.langchain.com/oss/python/integrations/middleware/index)

对应代码教材：

- 本文件后半部分的“示例 4：用 middleware 放控制逻辑”
- [03-methods.md](./03-methods.md) 末尾附录里的 `middleware`

## 7. Human-in-the-loop 可以在高层就接入

很多学习者会误以为: human-in-the-loop 必须等到复杂工作流阶段再做。

官方新版文档并不是这个思路。LangChain 在高层就提供了 human-in-the-loop middleware，让你能对敏感工具调用加审核。

这说明一个很重要的设计原则:

> 安全边界不是复杂系统专属的事，高层原型阶段就应该开始建立。

适合在高层先接入 human-in-the-loop 的场景:

- 对外发送内容
- 修改关键数据
- 使用敏感工具
- 费用敏感的操作

参考:

- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)

对应代码教材：

- 本文件后半部分的“示例 4：用 middleware 放控制逻辑”
- [03-methods.md](./03-methods.md) 末尾附录里的 `HumanInTheLoopMiddleware`

## 8. Short-term memory 的位置

在 `Stage 2`，学习者第一次会更具体地接触 memory，不是为了“一上来全接”，而是为了知道高层原型里什么时候短期记忆值得接入。

典型场景包括:

- 当前对话里已经澄清过目标
- 上一轮工具结果需要在本轮继续使用
- 用户已经给过格式偏好或局部约束

官方文档把 short-term memory 视为 thread-scoped memory。对这一阶段来说，最重要的不是实现细节，而是判断:

- 现在是否真的需要它
- 需要保留哪一类上下文
- 不需要保留的内容不要硬塞

参考:

- [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)
- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)

对应代码教材：

- 本文件后半部分的“示例 5：加上 short-term memory”
- [03-methods.md](./03-methods.md) 末尾附录里的 `checkpointer`、`state_schema`

## 9. LangChain 与高层 RAG Agent

`LangChain` 不只适合做纯工具型 agent，也适合做高层 RAG agent 原型。

这一阶段的重点不是把 RAG 做复杂，而是理解:

- 检索能力如何纳入 agent
- 资料接入后，输出边界如何变化
- 为什么一旦知识输入来自外部资料，structured output 和失败校验会更重要

参考:

- [Build a RAG agent with LangChain](https://docs.langchain.com/oss/python/langchain/rag)

## 10. 什么时候继续留在 LangChain 是合理的

如果你的项目具备下面这些特征，通常继续留在 LangChain 高层是合理的:

- 主路径比较清楚
- 控制逻辑不复杂
- 分支数量少
- 任务生命周期短
- 不需要复杂恢复机制
- human-in-the-loop 还只是局部审核，而不是主流程核心

这时继续用高层 abstractions 能提高迭代速度。

## 11. 什么时候开始逼近 LangGraph 边界

如果你的项目开始出现这些迹象，就说明 `Stage 3` 会变得重要:

- 你需要明显的多分支流程
- 你需要复杂状态机
- 你需要中断、审批、恢复成为系统核心能力
- 你需要长生命周期任务
- 你需要把确定性流程与 agentic steps 精细混编

这时继续把所有东西都硬塞在高层原型里，维护成本会迅速上升。

## 12. 这一章真正想让你记住的话

进入 `Stage 3` 之前，先记住这句话:

> `LangChain` 的真正价值不是“少写点代码”，而是帮你更快地做出高层可工作的 Agent 原型，同时让你更早看清自己的系统边界。

如果你准备进入代码层，下一步直接继续阅读本文件后半部分的代码教材，再去看 [03-methods.md](./03-methods.md) 末尾的 API 对照附录。

## 13. 代码教材：最小 LangChain 原型

这一节不是项目文档，而是 `Stage 2` 的代码教材。

目标很明确：

- 用最小代码示例讲清 `LangChain` 高层原型怎么搭
- 用逐段解释把概念、API 和效果连接起来
- 给后面的项目读码提供“标准参照物”

所有示例都尽量贴近 LangChain 官方 Docs 的能力主线：

- `create_agent`
- `@tool`
- `response_format`
- `middleware`
- `HumanInTheLoopMiddleware`
- `checkpointer`

### 示例 1：最小 `create_agent`

对应官方文档：

- [Agents](https://docs.langchain.com/oss/python/langchain/agents)
- [LangChain v1 create_agent](https://docs.langchain.com/oss/python/releases/langchain-v1#create_agent)

```python
from langchain.agents import create_agent

agent = create_agent(
    model="openai:gpt-5",
    tools=[],
    system_prompt="You are a concise research assistant.",
)

result = agent.invoke(
    {
        "messages": [
            {"role": "user", "content": "Give me a two-sentence summary of LangChain."}
        ]
    }
)
```

#### 逐段解释

`from langchain.agents import create_agent`

- 从高层入口导入 Agent 创建函数。
- 这也是新版 LangChain 官方推荐的标准入口之一。

`agent = create_agent(...)`

- 在这里把高层原型装起来。
- 你现在还没有显式写图、写节点、写状态机。
- 这就是 `Stage 2` 的重点：先用高层抽象跑通主路径。

`model="openai:gpt-5"`

- 指定模型。
- 这一层先关心“用哪个模型完成高层任务”，还不去展开 runtime 细节。

`tools=[]`

- 工具列表先留空。
- 这能帮助你意识到：Agent 不一定一开始就需要工具。

`system_prompt=...`

- 这是高层行为定位，不是系统全部控制逻辑。
- 后面我们会看到，很多规则其实不该全塞在 prompt 里。

`agent.invoke({...})`

- 用统一入口驱动执行。
- 输入采用消息格式，和官方 agent 主线保持一致。

### 示例 2：给 Agent 加一个最小工具

对应官方文档：

- [Agents](https://docs.langchain.com/oss/python/langchain/agents)

```python
from langchain.agents import create_agent
from langchain.tools import tool


@tool
def lookup_topic(topic: str) -> str:
    """Return a short note for a topic."""
    notes = {
        "langchain": "LangChain is the high-level agent development layer.",
        "langgraph": "LangGraph is the runtime and orchestration layer.",
    }
    return notes.get(topic.lower(), "No note found.")


agent = create_agent(
    model="openai:gpt-5",
    tools=[lookup_topic],
    system_prompt="You answer using the provided tool when useful.",
)
```

#### 逐段解释

`@tool`

- 把一个普通 Python 函数包装成 LangChain 可用工具。
- `Stage 2` 要先理解的是：工具不是“越多越好”，而是“要不要接进高层原型”。

`def lookup_topic(topic: str) -> str`

- 输入输出尽量简单稳定。
- 这是一个好工具的起点：清楚、单一、可预测。

`tools=[lookup_topic]`

- 把工具挂进 agent。
- 从这一步开始，Agent 才不只是“会说”，而是能借外部能力完成任务。

### 示例 3：先设计 `structured output`

对应官方文档：

- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)

```python
from pydantic import BaseModel, Field
from langchain.agents import create_agent


class ResearchSummary(BaseModel):
    summary: str = Field(description="One short paragraph summary")
    key_findings: list[str] = Field(description="The main findings")
    confidence: float = Field(description="Confidence score from 0 to 1")
    needs_more_information: bool = Field(description="Whether follow-up research is needed")


agent = create_agent(
    model="openai:gpt-5",
    tools=[lookup_topic],
    response_format=ResearchSummary,
)
```

#### 逐段解释

`class ResearchSummary(BaseModel)`

- 用 `Pydantic` 描述你真正想要的输出结构。
- 这一步是 `Stage 2` 最关键的设计动作之一。

`summary`

- 给用户看的短摘要。

`key_findings`

- 让输出不只是“一段泛泛总结”。

`confidence`

- 给系统和用户一个判断边界。

`needs_more_information`

- 这是典型的“后续流程判断字段”。
- 它让结果可以继续被系统消费，而不只是被人阅读。

`response_format=ResearchSummary`

- 直接把 schema 交给 agent。
- 按官方文档，LangChain 会根据模型能力选择合适策略。

### 示例 4：用 middleware 放控制逻辑

对应官方文档：

- [LangChain v1 create_agent](https://docs.langchain.com/oss/python/releases/langchain-v1#create_agent)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)

```python
from langchain.agents import create_agent
from langchain.agents.middleware import HumanInTheLoopMiddleware
from langgraph.checkpoint.memory import InMemorySaver


agent = create_agent(
    model="openai:gpt-5",
    tools=[lookup_topic],
    middleware=[
        HumanInTheLoopMiddleware(
            interrupt_on={
                "lookup_topic": False,
                "send_email": {"allowed_decisions": ["approve", "reject"]},
            }
        )
    ],
    checkpointer=InMemorySaver(),
)
```

#### 逐段解释

`HumanInTheLoopMiddleware`

- 这说明高层原型也可以接审核点。
- 不必等到 LangGraph 阶段才开始建立安全边界。

`interrupt_on={...}`

- 不是所有工具都需要审批。
- 这里把“安全工具”和“敏感工具”分开。

`checkpointer=InMemorySaver()`

- 官方文档明确说，HITL 需要 checkpointing 来处理中断。
- 这也是一个很重要的新版架构信号：
  即使你现在在 LangChain 高层，底下其实已经在吃 LangGraph 的运行时能力。

### 示例 5：加上 `short-term memory`

对应官方文档：

- [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)

```python
from langchain.agents import create_agent
from langgraph.checkpoint.memory import InMemorySaver


agent = create_agent(
    model="openai:gpt-5",
    tools=[lookup_topic],
    checkpointer=InMemorySaver(),
)

result = agent.invoke(
    {
        "messages": [
            {"role": "user", "content": "Remember that I care most about LangGraph."}
        ]
    },
    {"configurable": {"thread_id": "thread-1"}},
)
```

#### 逐段解释

`checkpointer=InMemorySaver()`

- 这是高层原型接 thread-scoped short-term memory 的最小方式。

`thread_id`

- 把当前交互绑定到一个线程。
- 这一点非常重要，因为 short-term memory 不是“全局都记住”，而是“和这条线程相关”。

### 示例 6：把它们合起来看

```python
from pydantic import BaseModel, Field
from langchain.agents import create_agent
from langchain.tools import tool


@tool
def lookup_topic(topic: str) -> str:
    """Return a short note for a topic."""
    notes = {
        "langchain": "LangChain is the high-level agent development layer.",
        "langgraph": "LangGraph is the runtime and orchestration layer.",
    }
    return notes.get(topic.lower(), "No note found.")


class ResearchSummary(BaseModel):
    summary: str = Field(description="One short paragraph summary")
    key_findings: list[str] = Field(description="The main findings")
    confidence: float = Field(description="Confidence score from 0 to 1")
    needs_more_information: bool = Field(description="Whether follow-up research is needed")


agent = create_agent(
    model="openai:gpt-5",
    tools=[lookup_topic],
    response_format=ResearchSummary,
)
```

#### 为什么这个组合适合 `Stage 2`

- 有高层 agent 入口
- 有最小工具
- 有 structured output
- 但还没有复杂状态图
- 也还没有长流程编排

这正是 `Stage 2` 想让你先掌握的“够用复杂度”。

### 这一节最该记住的 4 句话

1. `create_agent` 是新版 LangChain 高层入口之一。
2. 工具先求最小、清楚、稳定。
3. 先设计 `structured output`，再去调 prompt。
4. middleware、HITL、short-term memory 都说明高层原型并不等于“没有系统控制”。
