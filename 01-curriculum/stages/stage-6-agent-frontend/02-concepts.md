# 02 Concepts

## 1. Agent UX 不等于聊天 UX

普通聊天界面的核心是消息往返，而 Agent 产品界面的重点通常还包括：

- 任务阶段
- 计划可见性
- 工具执行状态
- 审批节点
- 结构化结果
- 历史与来源感
- 失败与恢复反馈

如果这些都被压进一条消息流里，用户很快就会失去方向感。

## 2. Structured output 在前端中的价值

官方前端文档强调 structured output 不只是为了后端消费，它也让前端可以更稳定地渲染结果。课程里最关键的理解是：

- 结果可以变成卡片、表格、摘要区和下一步区。
- 用户能更快区分结论、依据、不确定点和建议动作。
- 前端可以少依赖“猜文本结构”来做界面。

参考：

- [Frontend structured output](https://docs.langchain.com/oss/python/langchain/frontend/structured-output)
- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)

## 3. Human-in-the-loop 在前端中的价值

human-in-the-loop 如果只停留在后端 interrupt，用户体验是不完整的。真正的产品体验还需要：

- 审批前预览动作
- 审批原因说明
- 明确的批准 / 拒绝 / 修改入口
- 审批后结果反馈

课程里最关键的理解是：审批不是一个技术事件，而是一个需要被界面承接的产品时刻。

参考：

- [Frontend human-in-the-loop](https://docs.langchain.com/oss/python/langchain/frontend/human-in-the-loop)
- [Human-in-the-loop middleware](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)
- [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)

## 4. Streaming 的产品意义

streaming 不只是“字一个个冒出来”。在 Agent 系统里，streaming 可以承载：

- 当前阶段更新
- 工具执行反馈
- 中间结果回显
- 子任务进度
- 等待审批提示

也就是说，streaming 是“实时反馈系统状态”的能力，而不是纯视觉效果。

参考：

- [LangChain streaming](https://docs.langchain.com/oss/python/langchain/streaming)
- [LangGraph streaming](https://docs.langchain.com/oss/python/langgraph/streaming)

## 5. 状态可视化

一个好的 Agent 前端，通常应该让用户看见：

- 当前任务处于哪个阶段
- 下一步大概是什么
- 是否卡在工具执行或人工审批
- 哪一步失败了
- 系统是否还能继续

状态可视化的价值不是“更炫”，而是增强控制感和信任感。

## 6. 历史、来源与记忆感

当 Agent 具备 memory、RAG、tools 和复杂工作流后，前端必须帮助用户理解：

- 当前结果来自哪里
- 哪部分是历史上下文
- 哪部分是实时检索
- 哪部分是系统执行动作后的结果

如果来源感缺失，用户就很难判断是否应该信任这个结果。

## 7. Agent Chat UI 与多面板界面

官方文档给出了 Agent Chat UI 的方向，但课程里还要进一步理解边界：

- 对简单任务，增强版 chat UI 可能够用。
- 对复杂任务，多面板界面通常更合适。

常见面板可能包括：

- 输入区
- 对话区
- 计划区
- 工具状态区
- 审批区
- 结果区
- 历史区

参考：

- [Agent Chat UI](https://docs.langchain.com/oss/python/langchain/ui#agent-chat-ui)

## 8. Stage 6 的结论

Agent 前端的本质，不是把后端结果显示出来，而是把系统的行动、状态、风险和可控性翻译成人真正能理解和使用的体验。

## 9. 代码教材：最小 Agent 前端界面

这一节开始直接把官方前端文档里的能力，对回到可读的前端代码结构。

### 9.1 `useStream` 是前端主入口

官方 `Human-in-the-Loop` 和 `Structured output` 文档里，前端最核心的入口都是 `useStream`。

```tsx
import { useStream } from "@langchain/react";

const AGENT_URL = "http://localhost:2024";

export function Chat() {
  const stream = useStream<typeof myAgent>({
    apiUrl: AGENT_URL,
    assistantId: "research_console",
  });

  return <div>{stream.messages.map((msg) => <Message key={msg.id} message={msg} />)}</div>;
}
```

逐段理解：

- `useStream(...)`
  把前端连接到 agent server。
- `apiUrl`
  指向 agent server 或部署地址。
- `assistantId`
  指明要连接的 graph / assistant。
- `stream.messages`
  是最基础的 UI 数据源，消息区通常围绕它渲染。

这段代码的效果不是“做聊天框”，而是建立整个 UI 与 agent 运行时之间的数据连接。

### 9.2 Structured output 怎么被提取出来

官方 `Structured output` 文档里最关键的一点是：
structured output 最终存在最后一个 `AIMessage` 的 `tool_calls` 里。

```tsx
import { AIMessage } from "@langchain/core/messages";

function extractStructuredOutput<T>(messages: any[]): T | null {
  const aiMessages = messages.filter(AIMessage.isInstance);
  if (aiMessages.length === 0) return null;

  const lastAI = aiMessages[aiMessages.length - 1];
  const toolCall = lastAI.tool_calls?.[0];
  if (!toolCall) return null;

  return toolCall.args as T;
}
```

逐段理解：

- `AIMessage.isInstance`
  先把真正的 AI 消息筛出来。
- `lastAI.tool_calls?.[0]`
  从最后一个 AI 消息里取 structured output tool call。
- `toolCall.args`
  就是前端真正要渲染的结构化数据。

这也是 Stage 6 很关键的一点：
结果卡片不是“从一段自然语言里猜出来的”，而是直接从结构化对象里渲染出来的。

### 9.3 结果卡片为什么比长文本更好

官方文档给的模式是：先拿到 typed object，再把每个字段映射成合适的 UI。

```tsx
function RecipeCard({ recipe }: { recipe: Recipe }) {
  return (
    <div className="recipe-card">
      <h3>{recipe.title}</h3>
      <p>{recipe.description}</p>
      <div>{recipe.servings} servings</div>

      <ul>
        {recipe.ingredients.map((ing, i) => (
          <li key={i}>
            {ing.amount} {ing.unit} {ing.name}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

逐段理解：

- 标题、描述、数组、数字指标，都会落到不同组件表现上。
- 这让 UI 不再依赖“把长文本硬拆成几段”。
- 同样的模式可以迁移到研究结果卡片、审批摘要卡片、来源面板。

### 9.4 Streaming 时为什么不能直接渲染完整结果

官方文档明确提醒：streaming 过程中，tool call 的 `args` 可能还是不完整 JSON。

```tsx
function extractStructuredOutput<T>(
  messages: any[],
  requiredFields: string[] = [],
): T | null {
  const aiMessages = messages.filter(AIMessage.isInstance);
  if (aiMessages.length === 0) return null;

  const lastAI = aiMessages[aiMessages.length - 1];
  const toolCall = lastAI.tool_calls?.[0];
  if (!toolCall?.args) return null;

  const args = toolCall.args as Record<string, unknown>;
  const hasRequired = requiredFields.every((field) => args[field] !== undefined);
  if (requiredFields.length > 0 && !hasRequired) return null;

  return args as T;
}
```

逐段理解：

- 先判断 `toolCall.args` 是否存在
- 再判断关键字段是否已经到齐
- 没到齐时不要抢着渲染完整卡片

这背后的产品意义是：
前端要对“流式生成中的半成品状态”有耐心，不要过早渲染出误导用户的内容。

### 9.5 Progressive rendering 怎么做

官方推荐在 schema 有自然顺序时，逐步渲染部分字段。

```tsx
function ProgressiveRecipeCard({ messages }: { messages: any[] }) {
  const partial = extractStructuredOutput<Partial<Recipe>>(messages);
  if (!partial) return null;

  return (
    <div className="recipe-card">
      {partial.title && <h3>{partial.title}</h3>}
      {partial.description && <p>{partial.description}</p>}
      {partial.ingredients && (
        <ul>
          {partial.ingredients.map((ing, i) => (
            <li key={i}>{ing.amount} {ing.unit} {ing.name}</li>
          ))}
        </ul>
      )}
    </div>
  );
}
```

逐段理解：

- 前端不是只有“加载中”和“完成”两种状态。
- 只要部分字段已经稳定，就可以先展示。
- 这对研究结果、计划清单、审批预览都很有价值。

### 9.6 Human-in-the-loop 前端承接的是 `stream.interrupt`

官方 `Human-in-the-Loop` 文档里最关键的前端字段是 `stream.interrupt`。

```tsx
import { useStream } from "@langchain/react";

export function Chat() {
  const stream = useStream<typeof myAgent>({
    apiUrl: "http://localhost:2024",
    assistantId: "human_in_the_loop",
  });

  const interrupt = stream.interrupt;

  return (
    <div>
      {stream.messages.map((msg) => (
        <Message key={msg.id} message={msg} />
      ))}
      {interrupt && (
        <ApprovalCard
          interrupt={interrupt}
          onRespond={(response) =>
            stream.submit(null, { command: { resume: response } })
          }
        />
      )}
    </div>
  );
}
```

逐段理解：

- `stream.interrupt`
  是 UI 是否显示审批卡的判断条件。
- `onRespond(...)`
  是用户决定 approve / reject / edit 的回调。
- `stream.submit(null, { command: { resume: response } })`
  则把用户决定送回后端，继续运行。

所以前端不是“等后端做完再刷新”，而是 agent 执行流的一部分。

### 9.7 ApprovalCard 里最关键的不是样式，而是决策结构

官方文档给出的 `ApprovalCard` 模式里，真正重要的是三种决策：

- approve
- reject
- edit

```tsx
function ApprovalCard({ interrupt, onRespond }) {
  const request = interrupt.value;
  const action = request.actionRequests[0];
  const config = request.reviewConfigs[0];

  if (!action || !config) return null;

  return (
    <div>
      <pre>{JSON.stringify(action.args, null, 2)}</pre>
      {config.allowedDecisions.includes("approve") && (
        <button onClick={() => onRespond({ decision: "approve" })}>
          Approve
        </button>
      )}
      {config.allowedDecisions.includes("reject") && (
        <button onClick={() => onRespond({ decision: "reject", reason: "Need revision" })}>
          Reject
        </button>
      )}
    </div>
  );
}
```

逐段理解：

- `actionRequests`
  描述 agent 想做什么动作。
- `reviewConfigs`
  决定 UI 应该显示哪些按钮。
- `decision`
  是最核心的交互结果。

这说明审批 UI 的本质不是弹个框，而是把运行时动作结构化呈现给用户。

### 9.8 Streaming 的事件类型为什么要分开承接

官方 `Streaming` 文档强调前端要区分不同 stream modes：

```python
for chunk in agent.stream(
    {"messages": [{"role": "user", "content": "What is the weather in SF?"}]},
    stream_mode=["updates", "custom"],
    version="v2",
):
    print(chunk["type"])
    print(chunk["data"])
```

对前端来说，这意味着至少要区分：

- `messages`
  文本 token、tool call chunk
- `updates`
  某一步完成后的状态更新
- `custom`
  自定义进度、提示、工具状态

也就是说，真正好的 Agent UI，不会把所有流都塞成同一种“聊天文本”。

### 9.9 Agent Chat UI 的价值是什么

官方 `Agent Chat UI` 文档给出的不是一套最终设计，而是一个很实用的基线：

- 支持实时 chat
- 支持 tool visualization
- 支持 interrupts
- 支持 time-travel debugging 和 state forking

课程里最重要的理解不是“要不要直接用它”，而是：
它告诉你 Agent 前端最少要承接哪些运行时能力。

### 9.10 这一节读完后你至少要会什么

你至少要能用自然语言解释：

- `useStream` 为什么是前端 agent UI 的主入口
- structured output 为什么比纯文本更适合复杂结果展示
- 为什么 streaming 过程中不能盲目假设数据已经完整
- `stream.interrupt` 和 `stream.submit(... resume ...)` 如何组成审批闭环
- 为什么 Agent 前端必须承接不同类型的 stream 事件，而不是只渲染聊天内容
