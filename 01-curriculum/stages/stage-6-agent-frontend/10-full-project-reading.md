# 10 Full Project Reading

这一章的全项目阅读目标，不是只看懂一个 `ApprovalCard` 或一个 `stream renderer`，而是看懂 Agent 前端如何把后端运行时状态翻译成完整可控的用户界面。

## 一、全项目阅读顺序

建议按下面顺序扫完整个前端项目：

1. 页面入口与布局壳层
2. `useStream` 或流式数据接入层
3. 消息流与结构化结果渲染层
4. 审批与 interrupt 处理层
5. 状态面板与来源展示层
6. 线程、历史和重开流程
7. UI 组件库与样式层

## 二、你至少要能找到哪些文件

做 Stage 6 项目时，至少要能在项目里找到这些职责块：

- `page.tsx`、`App.tsx`、`layout.tsx`
  页面入口、整体布局、面板组织。
- `use-agent-stream.ts`、`chat.tsx`
  `useStream` 调用、提交请求、恢复 interrupt。
- `messages/`
  消息气泡、工具消息、结构化消息提取。
- `components/approval-card.tsx`
  审批卡片、approve / reject / edit。
- `components/result-card.tsx`
  structured output 的卡片、表格、摘要区。
- `components/state-panel.tsx`
  阶段状态、timeline、progress、source panel。
- `lib/extract-structured-output.ts`
  从消息流里提取 tool call args 或 structured output。
- `thread/`、`history/`
  线程切换、历史恢复、重新开始。

## 三、一条完整请求应该怎么穿过去

Agent 前端的一条完整主路径，通常要能被你讲成这样：

1. 用户在输入区提交问题。
2. 页面入口通过 `useStream` 把请求送到 agent server。
3. 前端开始收到 `messages`、`updates`、`custom` 等流式事件。
4. 消息区渲染文本、工具调用、结构化结果或中间状态。
5. 如果后端触发 interrupt，审批层渲染 review card。
6. 用户 approve / reject / edit 后，通过 `submit(..., { command: { resume: ... } })` 恢复执行。
7. 结果区、来源区和状态区同步刷新。
8. 用户可以查看历史线程、重新开始或继续当前任务。

## 四、这一章必须做的全项目解释

做完项目后，你至少要能完整解释：

- 哪个文件负责连接 `useStream`
- 哪个文件负责提取 structured output
- 哪个文件负责审批 UI
- 哪个文件负责 streaming 状态展示
- 哪个文件负责历史线程或重开流程
- 哪个文件负责来源面板或状态面板

## 五、框架能力要怎么对回代码

你必须能把这些官方能力，对回应的实现点：

- `useStream`
  对应前端流式接入 hook
- `stream.messages`
  对应消息流渲染层
- `stream.interrupt`
  对应审批卡片渲染条件
- `stream.submit(..., { command: { resume: ... } })`
  对应恢复执行逻辑
- `tool_calls`
  对应 structured output 提取逻辑
- `switchThread(null)`
  对应“重新开始”或切线程逻辑
- `stream_mode="messages" / "updates" / "custom"`
  对应前端需要承接的不同事件类型

## 六、最容易漏掉的全项目问题

- 只会解释聊天区，不会解释审批、来源、状态和历史区
- 知道有 structured output，但不知道它是从哪里被提取出来的
- 知道有 interrupt，但不知道恢复执行的代码在哪里
- 会讲静态布局，但讲不清流式事件如何驱动 UI 刷新

## 七、本章的读码完成标准

如果你已经能：

- 沿目录讲清整个前端系统的职责分层
- 用一条请求把输入、stream、interrupt、结果卡片串起来
- 把官方 LangChain 前端文档能力，对回真实文件和组件树
- 指出最值得优先审查的 3 个体验或状态风险点

那这章的全项目理解才算完成。
