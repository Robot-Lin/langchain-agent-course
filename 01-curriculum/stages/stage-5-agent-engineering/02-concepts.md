# 02 Concepts

## 1. 工程化层不是“附加题”

很多新手会把工程化理解成“项目做完后再补的部分”。这在 Agent 场景里通常会出问题。
因为 Agent 一旦：

- 连接外部知识
- 调用外部工具
- 接触业务数据
- 对外执行动作

它就已经是一个系统问题，而不只是 prompt 问题。

## 2. 什么是 MCP

官方把 MCP 解释为一种开放协议，用标准方式把外部能力暴露给模型或 Agent。课程里最重要的理解不是“它是一种新工具”，而是：

- 它标准化了能力暴露方式。
- 它让 Agent 接入外部系统时更一致。
- 它让“工具接入”逐渐从临时拼装变成可复用接口。

参考：

- [Model Context Protocol (MCP)](https://docs.langchain.com/oss/python/langchain/mcp)

## 3. 什么是 RAG

RAG 不是“给模型更多上下文”这么简单。它真正解决的是：

- 模型知识过期。
- 回答必须基于受控资料。
- 回答需要引用外部文档而不是靠记忆猜测。

在工程视角下，RAG 是知识层，不是状态层，也不是业务数据层。

参考：

- [Build a RAG agent with LangChain](https://docs.langchain.com/oss/python/langchain/rag)

## 4. memory、知识库、数据库的区别

这是 Stage 5 最重要的边界之一。

### memory

memory 记录的是连续性。比如：

- 用户偏好
- 当前会话上下文
- 长期用户设定
- 某个任务中需要记住的中间事实

参考：

- [Memory overview](https://docs.langchain.com/oss/python/concepts/memory)
- [Long-term memory](https://docs.langchain.com/oss/python/langchain/long-term-memory)

### 知识库

知识库用于检索外部资料。它服务的是“查找与引用”，比如：

- 公司制度文档
- 产品文档
- 研究资料
- 常见问题手册

### 数据库

数据库承载的是业务真相和系统状态，比如：

- 订单
- 客户记录
- 工单状态
- 审批日志
- 执行记录

如果把这三者混为一谈，系统就会出现边界模糊、治理困难、追责困难的问题。

## 5. 后端 API 的角色

后端 API 不只是让前端拿数据，它还是 Agent 与业务系统之间的重要边界。

它通常负责：

- 暴露受控业务能力。
- 屏蔽底层服务复杂度。
- 统一权限和审计。
- 把 Agent 的动作转成可管理的系统调用。

课程里要学的重点不是某个框架，而是 API 作为边界层的责任。

## 6. Observability

Agent 的可观测性不是“看最终回答好不好”，而是看：

- 中间步骤是什么。
- 调用了哪些工具。
- 哪一步检索失败了。
- 哪一步 reasoning 或状态更新偏掉了。
- 哪个环节导致了错误输出。

参考：

- [LangSmith Observability](https://docs.langchain.com/oss/python/langchain/observability)
- [Tracing quickstart](https://docs.langchain.com/langsmith/observability-quickstart)

## 7. Evaluation

官方把 evaluation 拆成明确的持续流程，而不是一次性的测试动作。课程里最关键的理解是：

- Evaluation 要覆盖上线前和运行中。
- 不同类型的 Agent 要有不同指标。
- RAG、聊天、工作流、动作型 agent 的评测目标不同。

参考：

- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
- [Evaluation types](https://docs.langchain.com/langsmith/evaluation-types)
- [Evaluate a RAG application](https://docs.langchain.com/langsmith/evaluate-rag-tutorial)

## 8. Governance 与权限

只要 Agent 开始触碰真实系统，治理就不是可选项。你至少要回答：

- 谁可以触发哪些能力。
- 哪些动作需要确认或审批。
- 哪些数据可以读，哪些数据不能读。
- 哪些行为必须留下审计记录。

## 9. Stage 5 的结论

一个真正可用的 Agent 系统，不只是“回答得聪明”，而是它知道自己连了什么、查了什么、存了什么、做了什么，并且这些过程都能被追踪、评测和治理。

## 10. 代码教材：最小工程化 Agent 系统

这一节开始不只讲概念，还直接把官方 Docs 里的工程化能力，对回最小代码结构。

### 10.1 MCP 接入的最小代码

这段结构直接对应官方 `Model Context Protocol (MCP)` 文档：

```python
from dataclasses import dataclass

from langchain.agents import create_agent
from langchain_mcp_adapters.client import MultiServerMCPClient


@dataclass
class RequestContext:
    user_id: str


client = MultiServerMCPClient(
    {
        "jobs": {
            "transport": "http",
            "url": "http://localhost:8000/mcp",
            "headers": {"Authorization": "Bearer demo-token"},
        }
    }
)

tools = await client.get_tools()

agent = create_agent(
    "openai:gpt-4.1",
    tools,
    context_schema=RequestContext,
)
```

逐段理解：

- `MultiServerMCPClient`
  负责连接一个或多个 MCP server。
- `transport`
  表示用什么方式通信。官方支持 `http` 和 `stdio`。
- `client.get_tools()`
  把 MCP server 暴露出的能力转成 LangChain tools。
- `create_agent(..., tools, context_schema=...)`
  把工具装进高层 agent，并声明运行时上下文结构。

这段代码的效果不是“生成回答”，而是先把工程系统的工具层接进来。

### 10.2 MCP 拦截器为什么重要

Stage 5 不只是会接工具，还要学会在调用工具之前做工程控制。官方 Docs 里最关键的是 `tool_interceptors`。

```python
from langchain_mcp_adapters.client import MultiServerMCPClient
from langchain_mcp_adapters.interceptors import MCPToolCallRequest
from langchain.messages import ToolMessage


async def require_authentication(request: MCPToolCallRequest, handler):
    runtime = request.runtime
    state = runtime.state
    is_authenticated = state.get("authenticated", False)

    if request.name == "export_data" and not is_authenticated:
        return ToolMessage(
            content="Authentication required before export.",
            tool_call_id=runtime.tool_call_id,
        )

    return await handler(request)


client = MultiServerMCPClient(
    {...},
    tool_interceptors=[require_authentication],
)
```

逐段理解：

- `request.runtime.state`
  允许你读当前运行状态。
- `request.name`
  告诉你当前在调哪个工具。
- `ToolMessage(...)`
  允许你在不真正调用工具的前提下，直接返回受控结果。
- `tool_interceptors=[...]`
  表示把治理、审计、重试、动态 header 注入等逻辑，包在工具调用外层。

这就是工程层和玩具 demo 的差别：工具不是“能调就行”，而是“谁能调、什么时候调、调失败怎么办”。

### 10.3 RAG 在工程系统里的最小实现

官方 `Build a RAG agent with LangChain` 文档里最值得学的不是完整 demo，而是检索工具如何被包装成系统能力。

```python
from langchain.tools import tool


@tool(response_format="content_and_artifact")
def retrieve_context(query: str):
    """Retrieve information to help answer a query."""
    retrieved_docs = vector_store.similarity_search(query, k=2)
    serialized = "\n\n".join(
        f"Source: {doc.metadata}\nContent: {doc.page_content}"
        for doc in retrieved_docs
    )
    return serialized, retrieved_docs
```

逐段理解：

- `@tool(...)`
  把检索能力包装成 agent 可调用工具。
- `similarity_search(...)`
  从索引中取出相关文档。
- `response_format="content_and_artifact"`
  是这里最关键的点。
  文本结果给模型看，原始文档对象留给系统继续处理、展示或审计。

这段代码帮助你看清：
RAG 不只是“给模型塞上下文”，而是先把检索做成一段独立、可追踪、可复用的系统能力。

### 10.4 RAG 的另一种工程写法：middleware 注入

如果你不想让 agent 自己决定是否搜索，官方 Docs 还给了两步式链路。

```python
from langchain.agents.middleware import dynamic_prompt, ModelRequest


@dynamic_prompt
def prompt_with_context(request: ModelRequest) -> str:
    last_query = request.state["messages"][-1].text
    retrieved_docs = vector_store.similarity_search(last_query)

    docs_content = "\n\n".join(doc.page_content for doc in retrieved_docs)

    return (
        "Use the following context to answer the question. "
        "If the context is insufficient, say you don't know.\n\n"
        f"{docs_content}"
    )
```

逐段理解：

- `dynamic_prompt`
  是 LangChain 高层里把运行时上下文注入模型提示的方式。
- `request.state`
  让 middleware 能读当前消息状态。
- `similarity_search(...)`
  在进模型前就完成检索。

这种写法更适合：

- 查询总是应该检索
- 想减少多次模型调用
- 想把 RAG 路径固定死，方便评测和审查

### 10.5 LangSmith tracing 在代码里长什么样

官方 `Trace LangChain applications` 文档最重要的一点是：很多情况下不需要改主逻辑，只要启用 tracing 配置，LangChain 代码就会自动产生 trace。

```python
import os

from langchain_core.output_parsers import StrOutputParser
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI


os.environ["LANGSMITH_TRACING"] = "true"
os.environ["LANGSMITH_API_KEY"] = "your-api-key"
os.environ["LANGSMITH_PROJECT"] = "stage-5-agent-engineering"

prompt = ChatPromptTemplate.from_messages(
    [
        ("system", "You are a helpful assistant."),
        ("user", "Question: {question}\nContext: {context}"),
    ]
)
model = ChatOpenAI(model="gpt-4.1-mini")
chain = prompt | model | StrOutputParser()
result = chain.invoke(
    {"question": "Summarize this trace", "context": "Trace context goes here"}
)
```

逐段理解：

- `LANGSMITH_TRACING=true`
  打开 tracing。
- `LANGSMITH_PROJECT`
  把运行归组到指定项目。
- `prompt | model | parser`
  是最小 runnable 链。
- `chain.invoke(...)`
  本身就会被记录成 trace。

Stage 5 要掌握的不是环境变量本身，而是：
你必须知道 trace 是在哪一层开启的，项目名怎么分，哪些运行该被采样或标记。

### 10.6 给 traces 打标签和 metadata

工程项目不能只有 traces，还要让 traces 可筛选。

```python
from langchain_core.output_parsers import StrOutputParser
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI


prompt = ChatPromptTemplate.from_messages(
    [("system", "You are a helpful AI."), ("user", "{input}")]
)
model = ChatOpenAI().with_config(
    {"tags": ["retrieval"], "metadata": {"layer": "model"}}
)
chain = (prompt | model | StrOutputParser()).with_config(
    {"tags": ["stage-5"], "metadata": {"feature": "enterprise-agent"}}
)
```

逐段理解：

- `with_config(...)`
  给某个 runnable 附加 tags 和 metadata。
- tags / metadata 会向子运行继承
  所以这是做筛选、聚类、线上排查的重要入口。

### 10.7 Evaluation 在 Stage 5 里先学什么

官方 `LangSmith Evaluation` 文档把评测分成：

- offline evaluation
- online evaluation

这一章先建立系统理解，不急着背 SDK 细节，先掌握这条工程闭环：

1. 先拿真实或合成样本建 dataset。
2. 再写 evaluator。
3. 用 experiment 跑离线比较。
4. 把线上失败 trace 回流到 dataset。

也就是说，Stage 5 的评测不是“写一个分数函数”，而是学会把评测放进研发闭环。

### 10.8 这一节读完后你至少要会什么

你至少要能用自然语言解释：

- MCP client 是怎么把外部能力接进 agent 的
- interceptor 为什么比“直接调用工具”更工程化
- RAG tool 和 dynamic prompt 的差别
- LangSmith tracing 是怎么在 LangChain runnable 层自动生效的
- 为什么 evaluation 是系统闭环，不只是测试脚本
