# 02 Concepts

## 1. 全栈 Agent 交付到底是什么

课程里的“全栈交付”不是简单指前端加后端，而是指这些层形成可运行产品：

- 用户界面
- 前后端通信
- Agent runtime
- 知识与数据层
- 实时反馈链路
- 观测与评测层
- 部署与运行层

只有这些层真正闭环，系统才从工程方案进入产品交付。

## 2. Agent Server 的角色

官方文档把 Agent Server 描述成面向 Agent 应用的运行与 API 入口。课程里最关键的理解是：

- 它不是普通业务 API 的替代品。
- 它更像 Agent 系统的交付入口和运行边界。
- 它把运行中的 Agent 能力暴露给前端和外部系统。

参考：

- [Agent Server](https://docs.langchain.com/langsmith/agent-server)
- [Agent Server API reference](https://docs.langchain.com/langsmith/server-api-ref)

## 3. Deployment 的意义

官方的 deployment 文档强调的不是“把代码发出去”这么简单，而是运行、管理、扩展和维护 Agent 产品。课程里最关键的理解是：

- deployment 不是最后一步，而是产品生命周期的一部分。
- 交付方案会直接影响系统是否稳定、是否可维护、是否可扩展。

参考：

- [LangSmith Deployment](https://docs.langchain.com/langsmith/deployment)
- [LangChain deploy](https://docs.langchain.com/oss/python/langchain/deploy)

## 4. Streaming integration

全栈 Agent 产品的前端不该被动等待最终结果。Streaming integration 的意义是：

- 前端和运行中的 Agent 持续同步。
- 前端能展示中间状态、阶段更新和等待点。
- 产品体验和运行状态真正连接起来。

参考：

- [Streaming API](https://docs.langchain.com/langsmith/streaming)
- [LangGraph streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

## 5. Observability 与 Evaluation 在交付中的位置

到了全栈交付层，observability 和 evaluation 已经不再是“研发内部工具”，而是产品可靠性的组成部分。你需要知道：

- 系统是否正常运行
- 哪条路径最容易失败
- 用户真实体验是否稳定
- 某次更新是否让质量变差

参考：

- [LangSmith Observability](https://docs.langchain.com/langsmith/observability)
- [LangSmith Evaluation](https://docs.langchain.com/langsmith/evaluation)
- [Evaluation types](https://docs.langchain.com/langsmith/evaluation-types)

## 6. 交付验收不等于功能列表

很多项目把“有这些功能”当成“可以交付”，这是错误的。交付验收更应关注：

- 链路是否完整
- 结果是否可理解
- 状态是否可追踪
- 故障是否可定位
- 版本是否可迭代

## 7. 框架选型与迁移

到了这一章，学习者必须开始明确：

- 为什么当前产品适合 LangChain、LangGraph 或 Deep Agents 中的哪一层。
- 是否还需要其他前端或服务层框架来完成产品化。
- 未来如果用户规模、团队规模或业务复杂度变化，架构应该怎么调整。

## 8. Stage 7 的结论

全栈 Agent 交付的核心，不是把不同部分拼在一起，而是让它们形成一个可以持续运行、被用户理解、被团队维护、被产品迭代的完整闭环。

## 9. 代码教材：最小全栈交付链路

这一节开始不只讲交付概念，还直接把官方 Docs 里的 Agent Server、Streaming API 和 Deployment 能力，对回最小全栈代码结构。

### 9.1 Agent Server SDK 客户端长什么样

官方 `Streaming API` 文档里，前后端最关键的交付接口是 LangGraph SDK client。

```python
from langgraph_sdk import get_client

client = get_client(url="<DEPLOYMENT_URL>", api_key="<API_KEY>")
assistant_id = "agent"

thread = await client.threads.create()
thread_id = thread["thread_id"]
```

逐段理解：

- `get_client(...)`
  创建与部署好的 Agent Server 通信的 SDK 客户端。
- `assistant_id`
  对应部署出来的 graph / assistant。
- `client.threads.create()`
  在持久化交互里创建一个 thread。
- `thread_id`
  后续 runs、streaming、恢复执行都会围绕它进行。

这段代码的效果不是“调用一个函数”，而是建立了用户会话和后端运行时之间的持久上下文。

### 9.2 一次最小 streaming run 怎么发起

```python
async for chunk in client.runs.stream(
    thread_id,
    assistant_id,
    input={"topic": "ice cream"},
    stream_mode="updates",
):
    print(chunk.data)
```

逐段理解：

- `client.runs.stream(...)`
  发起一次流式 run。
- `thread_id`
  指定这次运行属于哪个持久线程。
- `assistant_id`
  指定用哪个部署出来的 agent。
- `stream_mode="updates"`
  表示按节点步骤回传状态更新。

这就是全栈交付里最关键的主路径之一：
前端不只是“请求一个最终结果”，而是在监听一个运行中的 agent。

### 9.3 JavaScript 侧全栈调用长什么样

```ts
import { Client } from "@langchain/langgraph-sdk";

const client = new Client({ apiUrl: "<DEPLOYMENT_URL>", apiKey: "<API_KEY>" });
const assistantID = "agent";

const thread = await client.threads.create();
const threadID = thread["thread_id"];

const streamResponse = client.runs.stream(threadID, assistantID, {
  input: { topic: "ice cream" },
  streamMode: "updates",
});

for await (const chunk of streamResponse) {
  console.log(chunk.data);
}
```

逐段理解：

- `new Client(...)`
  是浏览器 / Next.js / Node 服务端连接部署好的 agent 的入口。
- `threads.create()`
  表示这不是单次请求，而是 thread-aware 的交互。
- `runs.stream(...)`
  把后端运行过程直接暴露给前端消费。

### 9.4 Stateless run 什么时候有用

官方文档特别指出，不是所有运行都必须创建 thread。

```python
async for chunk in client.runs.stream(
    None,
    assistant_id,
    input=inputs,
    stream_mode="updates",
):
    print(chunk.data)
```

逐段理解：

- `thread_id = None`
  表示这是一次 stateless run。
- 适合一次性任务、无需恢复、无需长期对话状态的场景。

这一点在交付层很重要，因为它直接影响：

- 你要不要保存上下文
- 你要不要维护线程生命周期
- 前端要不要承接“继续之前的线程”

### 9.5 已在运行的后台任务如何重新加入

官方 `Streaming API` 文档里另一个很实用的能力是 `join_stream`。

```python
async for chunk in client.runs.join_stream(
    thread_id,
    run_id,
):
    print(chunk)
```

逐段理解：

- `run_id`
  指向某个已经存在的后台运行。
- `join_stream(...)`
  允许客户端重新连上这个运行并继续接收流式输出。

这对真实产品很重要，因为用户会断网、切标签页、刷新页面、切换设备。

### 9.6 Agent Server 在架构里的位置

官方 `Agent Server` 文档强调它不是普通 API 替代品，而是：

- assistants
- threads
- runs
- cron jobs

这些运行时原语的统一交付入口。

课程里最重要的理解是：

- API server 负责接收请求、创建 runs、读取 threads、转发 streaming
- queue worker 负责真正执行 graph 和写 checkpoints
- Postgres 负责 assistants、threads、runs、checkpoints、store
- Redis 负责短期 signaling、cancellation 和 streaming pub/sub

也就是说，Stage 7 不是在讲“前端怎么调后端”，而是在讲“整个运行闭环如何真正进入生产形态”。

### 9.7 Deployment 文档最值得学的不是命令，而是运行模型

官方 `LangSmith Deployment` 文档里最重要的是下面这条工作流：

1. Test locally
2. Configure
3. Choose hosting & deploy your agent
4. Monitor

课程里最重要的理解是：

- deployment 从设计阶段就开始影响产品边界
- 你必须知道用 Cloud、Hybrid、Self-hosted 时谁在管基础设施
- 交付不是“把代码放上去”，而是把观测、流式、持久化、扩缩容一起放进去

### 9.8 全栈链路为什么一定要带 observability

到了这一章，trace 不再只是研发调试工具。

你至少要在系统里清楚：

- 哪些 runs 进入哪个 `LANGSMITH_PROJECT`
- 哪些 tags / metadata 用来区分版本、租户、实验
- 前端报的错误能不能回到对应 run
- 线上失败 traces 能不能回流到 evaluation dataset

所以 Stage 7 的 trace 代码，不只是“能看到一点日志”，而是整个交付可维护性的入口。

### 9.9 这一节读完后你至少要会什么

你至少要能用自然语言解释：

- SDK client、thread、run、assistant_id 四者的关系
- 为什么 streaming run 比普通 request/response 更贴近 Agent 产品
- stateless run 和 thread-based run 的差别
- Agent Server 为什么需要 API server、queue worker、持久化和 streaming pub/sub
- deployment 为什么是产品生命周期的一部分，而不是最后一步
