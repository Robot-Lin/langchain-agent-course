# 10 Full Project Reading

这一章的全项目阅读目标，不是只看懂某个 `retriever` 或某个 `trace hook`，而是看懂一个工程化 Agent 系统如何由多层文件共同组成。

## 一、全项目阅读顺序

建议按下面顺序扫完整个项目：

1. Agent 入口
2. Tool / MCP 接入层
3. Retrieval / Knowledge 层
4. Memory / Store / Database 层
5. API / Service 层
6. LangSmith trace / evaluation 层
7. Governance / audit 层

## 二、你至少要能找到哪些文件

做 Stage 5 项目时，至少要能在项目里找到这些职责块：

- `agent.py` 或 `app.py`
  Agent 主入口，负责接收请求、装配工具、组织主流程。
- `mcp_client.py` 或 `tools/`
  MCP 客户端、工具适配器、权限注入、拦截器。
- `retrieval.py` 或 `rag/`
  检索工具、向量检索、上下文拼装。
- `store.py`、`memory.py`、`db.py`
  长期偏好、业务状态、数据库连接与持久化。
- `api.py`、`routes.py`、`service.py`
  HTTP 边界、请求校验、服务编排。
- `observability.py`、`evaluation.py`
  LangSmith tracing、project/tags、离线或在线评测入口。
- `policy.py`、`governance.py`
  权限、审批、速率限制、审计记录。

## 三、一条完整请求应该怎么穿过去

工程化 Agent 的主路径，通常要能被你讲成这样：

1. 前端或调用方把请求送到 API 层。
2. API 层做输入校验、身份识别、最小权限判断。
3. Agent 入口根据请求装配工具、上下文和可用服务。
4. MCP 或本地工具层决定能调用哪些外部能力。
5. 如果需要知识补充，检索层去查文档或索引。
6. 如果需要用户偏好或业务状态，数据层去查 store 或数据库。
7. Agent 产出结果后，trace 和 evaluation 层记录运行信息。
8. 治理层决定哪些调用要拦截、审计或升级人工处理。

## 四、这一章必须做的全项目解释

做完项目后，你至少要能完整解释：

- 哪个文件负责接入 MCP
- 哪个文件负责检索和文档引用
- 哪个文件负责长期存储或数据库写入
- 哪个文件负责 API 边界
- 哪个文件负责 LangSmith tracing
- 哪个文件负责评测
- 哪个文件负责治理与权限

## 五、框架能力要怎么对回代码

你必须能把这些官方能力，对回应的实现点：

- `MultiServerMCPClient`
  对应 MCP 客户端文件或工具装配文件
- `tool_interceptors`
  对应工具调用前后的控制逻辑文件
- `create_agent`
  对应 Agent 主入口
- `@tool`
  对应检索或外部能力包装函数
- `dynamic_prompt` 或 `AgentMiddleware`
  对应 RAG 注入或上下文增强逻辑
- `LANGSMITH_TRACING`、`with_config`、`tracing_context`
  对应观测与追踪设置

## 六、最容易漏掉的全项目问题

- 只会解释 agent 文件，不会解释它依赖的 service、store、policy
- 知道检索发生了，但不知道数据是在哪一层被序列化和引用的
- 知道有 LangSmith，但不知道 trace 是自动启用、选择性启用，还是在特定运行里启用
- 会讲主路径，但讲不清失败路径和治理路径

## 七、本章的读码完成标准

如果你已经能：

- 沿目录讲清整个工程系统的职责分层
- 用一条请求把关键文件串起来
- 把官方 LangChain / LangSmith 文档能力，对回真实代码位置
- 指出系统最值得优先审查的 3 个风险层

那这章的全项目理解才算完成。
