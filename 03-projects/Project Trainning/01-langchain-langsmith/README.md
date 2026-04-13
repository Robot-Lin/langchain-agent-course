# LangChain + LangSmith

这一层是训练主线的起点。

目标是先掌握：

- `create_agent`
- `tools`
- `structured output`
- `middleware`
- 基础 `workflow`
- `LangSmith tracing`
- `LangSmith evaluation`

这一层不追求显式图编排，而是先把高层 agent 原型做稳、看懂、评估清楚。

---

## 当前项目

1. `行程信息整理器`
   练最小 agent、最小 tool、结构化输出和 tracing。

2. `招聘 JD 与简历匹配助手`
   练多输入分析、结构化判断、middleware 和 evaluation。

3. `Obsidian 第二大脑整理与更新审批助手`
   练 retrieval、memory、审批、checkpointer 和更完整的 LangSmith 闭环。

---

## 这一层你该学会什么

- 什么时候该用 `LangChain`
- 怎么用 `create_agent`
- 怎么设计单一职责工具
- 怎么先设计 `response_format`
- 怎么区分 prompt、schema、middleware
- 怎么用 LangSmith 看 trace
- 怎么用 LangSmith 做基础 evaluation

---

## 推荐顺序

1. `行程信息整理器`
2. `招聘 JD 与简历匹配助手`
3. `Obsidian 第二大脑整理与更新审批助手`

---

## 进入项目前

开始任一项目时，先回到总入口：

[README.md](/X:/AI%20work/LangChain%20Tutorial/03-projects/Project%20Trainning/README.md)

然后按启动规则执行：

1. 先确认做哪个项目
2. 再选择开始模式
3. 如果用户写了框架，先做可行性与风险分析
4. 再进入共同实现
