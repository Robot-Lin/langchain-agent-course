# 03 Methods

本文关注 Stage 5 的工程化设计方法。目标不是记住更多名词，而是学会如何把一个 Agent 方案变成有边界、有落点、有观测的系统。

## 方法一: 横向能力分层法

先把系统拆成几层：

- Agent 层
- Tool / MCP 层
- Knowledge / RAG 层
- Memory / Data 层
- API / Service 层
- Observability / Evaluation 层
- Governance 层

这样做的目的，是让每一层只负责一种主要职责。

## 方法二: 先画边界，再接能力

每当你想加一种新能力，不要先想“怎么接”，先问：

- 它属于哪一层。
- 它的输入输出是什么。
- 它接触什么敏感信息。
- 它失败后会造成什么后果。
- 它如何被追踪和审计。

## 方法三: 知识接入决策法

面向任何“信息需求”，先判断它属于哪一类：

- 这是用户偏好或跨会话连续性吗。
- 这是需要检索的文档知识吗。
- 这是业务真实状态或交易数据吗。

只有先回答这个问题，才能决定该用 memory、RAG 还是数据库。

## 方法四: 观测与评测前置法

不要等系统搭完才想“如何验证”。设计阶段就要写清楚：

- 哪些步骤必须 trace。
- 哪些输出要被抽样评估。
- 哪些失败信号要被监控。
- 哪些指标能说明系统质量真的在变好或变差。

## 方法五: 最小权限清单法

对于每个外部能力，都写出最小治理清单：

- 谁能调用。
- 调用前是否需要确认。
- 调用后是否需要记录。
- 是否存在不可逆后果。
- 是否允许自动执行。

## 方法六: 工程化复盘法

每次复盘一个 Agent 系统，都固定检查：

- 分层是不是清楚。
- 数据落点是不是清楚。
- 知识边界是不是清楚。
- 关键行为能不能被追踪。
- 输出质量有没有明确评测方式。
- 风险动作有没有治理机制。

## 方法目标

真正掌握 Stage 5，不是“知道 MCP、RAG、LangSmith 这些词”，而是能把一个需求拆成真实系统需要的层，并说清每一层为什么存在。

## 附录：Stage 5 API 对照表

这一节把你在官方 Docs 里会反复看到的能力，对回到代码阅读时应该识别的点。

### MCP 接入层

- `MultiServerMCPClient`
  作用：连接多个 MCP servers。
  看代码时要找：客户端初始化文件、server 配置、transport 选择。

- `client.get_tools()`
  作用：把 MCP tools 拉进 LangChain。
  看代码时要找：工具装配点、agent 初始化点。

- `client.session("server_name")`
  作用：显式管理 stateful session。
  看代码时要找：哪些 server 需要持久连接，为什么默认无状态不够。

- `tool_interceptors=[...]`
  作用：在工具调用前后做工程控制。
  看代码时要找：认证、审计、重试、动态参数注入。

- `request.override(...)`
  作用：不可变地改请求参数或 header。
  看代码时要找：用户上下文注入、权限 header 注入、参数修正。

- `request.runtime.context`
  作用：读调用时传入的上下文。
  看代码时要找：user_id、tenant_id、api_key、role。

- `request.runtime.store`
  作用：读长期记忆或持久化偏好。
  看代码时要找：用户偏好、历史限制、组织级配置。

- `request.runtime.state`
  作用：读当前运行状态。
  看代码时要找：认证状态、流程标记、临时中间值。

### RAG / Knowledge 层

- `@tool(response_format="content_and_artifact")`
  作用：把检索能力包装成 tool，并同时保留原始 artifact。
  看代码时要找：文档元数据在哪里继续被用。

- `vector_store.similarity_search(...)`
  作用：相似度检索。
  看代码时要找：搜索参数、k 值、过滤器、结果序列化。

- `dynamic_prompt`
  作用：在模型调用前动态注入上下文。
  看代码时要找：何时固定检索，何时让模型决定要不要检索。

- `AgentMiddleware.before_model`
  作用：在进模型前修改状态或消息。
  看代码时要找：把检索结果塞进 state、追加上下文、保存原始文档。

### Agent / Service 层

- `create_agent(...)`
  作用：创建高层 agent。
  看代码时要找：tools、middleware、context_schema、store 都在哪一处被汇总。

- `context_schema=...`
  作用：声明运行时上下文结构。
  看代码时要找：调用方传什么上下文，工具层如何消费。

- `store=InMemoryStore()` 或其他 store
  作用：把长期存储接进 agent。
  看代码时要找：长期偏好和业务数据库边界是否清楚。

### LangSmith 观测与评测层

- `LANGSMITH_TRACING`
  作用：打开 tracing。
  看代码时要找：是在环境变量、程序启动、还是某个局部 context 里开启。

- `LANGSMITH_PROJECT`
  作用：trace 分组。
  看代码时要找：项目名是否按环境、功能或实验分开。

- `with_config({"tags": ..., "metadata": ...})`
  作用：给 traces 打标签和元数据。
  看代码时要找：线上排障、实验对比、用户分群如何实现。

- `ls.tracing_context(...)`
  作用：选择性 tracing。
  看代码时要找：哪些请求被采样、哪些阶段被强制记录。

### 读 API 时最重要的原则

不要把 API 当成待背列表。你真正要问的是：

- 这个 API 解决的是哪一层的问题
- 它的输入输出是什么
- 它会把哪一段代码和哪一段调用链连起来
- 如果不用它，系统复杂度会转移到哪里
