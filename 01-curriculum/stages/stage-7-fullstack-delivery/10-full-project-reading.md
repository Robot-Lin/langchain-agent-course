# 10 Full Project Reading

这一章的全项目阅读目标，不是只看懂某个 `route.ts` 或某个 `deploy config`，而是看懂一个全栈 Agent 产品如何把前端、后端、runtime、流式通道和观测系统串成闭环。

## 一、全项目阅读顺序

建议按下面顺序扫完整个交付项目：

1. 前端入口与请求发起层
2. API / BFF / server routes 层
3. Agent runtime 入口层
4. Streaming 与线程管理层
5. Knowledge / tools / store 层
6. LangSmith tracing / evaluation 层
7. 部署与环境配置层

## 二、你至少要能找到哪些文件

做 Stage 7 项目时，至少要能在项目里找到这些职责块：

- `app/page.tsx`、`frontend/`
  前端请求入口、流式展示、线程 UI。
- `app/api/`、`routes.py`、`server.py`
  HTTP 边界、server routes、代理层或 BFF。
- `graph.py`、`agent.py`
  Agent runtime 主入口，graph / agent 装配点。
- `client.ts`、`langgraph-sdk.ts`
  Agent Server SDK 客户端、thread / run 调用。
- `tools/`、`rag/`、`store/`
  外部能力、检索、长期存储、数据库。
- `observability/`、`evaluation/`
  LangSmith trace、project 配置、评测回流。
- `Dockerfile`、`langgraph.json`、`.env.example`
  部署、环境变量、graph 注册与运行配置。

## 三、一条完整请求应该怎么穿过去

全栈交付的一条主路径，通常要能被你讲成这样：

1. 用户在前端触发一个新任务。
2. 前端通过 API route 或 SDK 调用 Agent Server。
3. 如果需要持久化线程，系统先创建或复用 thread。
4. 系统发起 run 或 streaming run。
5. Agent runtime 执行 graph，并与 tools / RAG / store 交互。
6. Streaming 通道把 updates、messages、custom data 回传给前端。
7. LangSmith 同步记录 traces、tags、metadata、运行状态。
8. 部署层和环境配置保证这条链路在真实环境里可运行、可恢复、可排障。

## 四、这一章必须做的全项目解释

做完项目后，你至少要能完整解释：

- 哪个文件负责前端请求发起
- 哪个文件负责 API 边界或 BFF
- 哪个文件负责 graph / agent runtime 入口
- 哪个文件负责 thread 和 run 的创建
- 哪个文件负责 streaming 通道
- 哪个文件负责 LangSmith trace 和评测入口
- 哪个文件负责部署配置和环境变量

## 五、框架能力要怎么对回代码

你必须能把这些官方能力，对回应的实现点：

- `Client({ apiUrl, apiKey })`
  对应 Agent Server SDK 客户端文件
- `client.threads.create()`
  对应线程初始化逻辑
- `client.runs.stream(...)`
  对应全栈流式主路径
- `client.runs.joinStream(...)`
  对应重连或加入正在进行中的后台任务
- `thread_id = None` / `null`
  对应 stateless runs
- `assistant_id`
  对应部署出来的 graph / assistant 标识
- `LANGSMITH_PROJECT`、trace tags、metadata
  对应可观测性配置文件或初始化逻辑
- `langgraph.json`、Dockerfile、环境变量
  对应部署结构和运行配置

## 六、最容易漏掉的全项目问题

- 只会解释前端和 graph，看不清中间的 API 或 SDK 边界
- 知道能 stream，但不知道 thread、run、assistant_id 三者关系
- 知道有 traces，但不知道它们在哪一层被配置和继承
- 会讲主路径，但讲不清断线重连、后台 run、stateless run 的差别

## 七、本章的读码完成标准

如果你已经能：

- 沿目录讲清整个交付系统的职责分层
- 用一条请求把前端、后端、runtime、streaming、trace 串起来
- 把官方 Agent Server / Deployment / Streaming API 对回真实文件和配置
- 指出最值得优先审查的 3 个交付风险点

那这章的全项目理解才算完成。
