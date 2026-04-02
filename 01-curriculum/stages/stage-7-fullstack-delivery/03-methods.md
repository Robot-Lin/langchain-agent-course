# 03 Methods

本文关注 Stage 7 的全栈交付方法。目标不是“知道怎么部署”，而是学会把一个 Agent 系统推进成真正可交付、可验证、可迭代的产品。

## 方法一: 全链路组装法

先按链路组装系统：

1. 用户入口
2. 前端交互
3. 请求与流式通信
4. Agent runtime
5. 知识 / 数据 / 工具层
6. 观测 / 评测 / 运行层

这样做的原因是：交付的关键在于链路完整，而不是模块清单很长。

## 方法二: 可演示性优先法

先确保系统能被完整演示：

- 用户能触发
- 系统能响应
- 状态能被看见
- 结果能被理解
- 故障能被解释

很多系统技术上很复杂，但演示链路不完整，说明它还不是产品。

## 方法三: 交付三问法

每个版本都问：

- 能不能跑
- 能不能看见
- 能不能评估

如果缺任意一个，交付都不完整。

## 方法四: 部署前置法

在设计阶段就考虑：

- 运行在哪里
- 如何暴露给前端
- 如何追踪和扩容
- 如何排障和回放

## 方法五: 选型说明法

每个全栈 Agent 产品都应该写一段简短说明：

- 为什么当前主线选 LangChain / LangGraph / Deep Agents
- 为什么前端采用当前交互形态
- 为什么当前部署与追踪方式合理

## 方法六: 交付复盘法

每次复盘都固定检查：

- 用户链路是否顺畅
- 技术链路是否闭环
- 团队是否能快速定位问题
- 当前架构是否仍然适合下一版产品

## 方法目标

真正掌握 Stage 7，不是“会说 deployment、Agent Server 这些词”，而是能把一个 Agent 系统从设计推进成真正可交付、可验证、可迭代的产品。

## 附录：Stage 7 API 对照表

这一节把官方交付文档里最关键的能力，对回代码阅读时应该识别的点。

### Agent Server / SDK 层

- `get_client(url=..., api_key=...)` / `new Client({ apiUrl, apiKey })`
  作用：创建访问 Agent Server 的 SDK 客户端。
  看代码时要找：前端或 BFF 是在哪里初始化它的。

- `assistant_id`
  作用：标识部署出来的 graph / assistant。
  看代码时要找：不同功能、不同图、不同环境是怎么区分的。

- `client.threads.create()`
  作用：创建持久化线程。
  看代码时要找：线程什么时候创建、什么时候复用、什么时候清理。

- `client.runs.stream(...)`
  作用：发起一次流式运行。
  看代码时要找：前端主路径、server route 转发、run 生命周期。

- `client.runs.join_stream(...)` / `joinStream(...)`
  作用：重新接入已在运行的后台任务。
  看代码时要找：断线恢复、页面刷新恢复、后台任务观察。

- `thread_id=None` / `null`
  作用：创建 stateless run。
  看代码时要找：哪些请求不需要长期线程。

### Streaming 交付层

- `stream_mode="updates"`
  作用：按节点更新回传状态。
  看代码时要找：状态面板、timeline、步骤可视化。

- `stream_mode="messages-tuple"`
  作用：按 token 流式返回模型输出。
  看代码时要找：逐字输出、tool call chunk 展示。

- `stream_mode="custom"`
  作用：传自定义进度或业务信号。
  看代码时要找：进度条、提示横幅、后台状态。

- `stream_subgraphs=True`
  作用：把子图输出一起 stream 出来。
  看代码时要找：多 agent / 子图时的来源区分。

### 交付配置层

- `langgraph.json`
  作用：声明 graph 注册、依赖和运行结构。
  看代码时要找：graph 名称、部署入口、依赖边界。

- `Dockerfile`
  作用：打包运行环境。
  看代码时要找：依赖安装、启动命令、镜像边界。

- `.env` / `.env.example`
  作用：配置 API keys、LangSmith project、部署地址。
  看代码时要找：哪些变量驱动环境差异。

### Observability / Evaluation 层

- `LANGSMITH_PROJECT`
  作用：按环境、产品、实验组织 traces。
  看代码时要找：trace 分组是否清楚。

- trace tags / metadata
  作用：让 run 可以按版本、租户、实验筛选。
  看代码时要找：前后端共享哪些识别信息。

- evaluation dataset / experiment
  作用：让交付版本有可重复比较的质量基线。
  看代码时要找：线上 traces 怎么回流到离线评测。

### 读 API 时最重要的原则

不要把这些 SDK 调用和部署配置当成“上线命令大全”。你真正要问的是：

- 这个 API 对应交付链路里的哪一段
- 这段调用跟哪个 thread / run / graph / trace 绑定
- 如果它失败了，用户、前端、后端、runtime 各会卡在哪里
