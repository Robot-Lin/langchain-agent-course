# Deep Agents + LangSmith

这一层是在 `LangChain + LangGraph` 之后的复杂任务组织层。

目标是掌握：

- `subagents`
- context engineering
- 长任务组织
- 多角色分工
- complex memory
- 多子代理系统的 LangSmith 监控

这一层不再只是“一个 agent 怎么跑”，而是开始理解“复杂任务如何拆成多个 agent 协作”。 

---

## 当前项目

1. `个人知识学习教练`
   练多角色、上下文分工和学习型复杂任务。

2. `多来源情报监控与周报助手`
   练多来源采集、主题聚合、去重、重点识别和连续监控。

3. `内容创作流水线助手`
   练选题、调研、提纲、初稿、改写、审核的多阶段流水线。

---

## 这一层你该学会什么

- 为什么 Deep Agents 不是简单“多开几个 agent”
- context engineering 为什么是核心
- subagents 之间该如何分工
- memory 在复杂任务里怎么发挥作用
- 怎么用 LangSmith 看多子代理调用链

---

## 推荐顺序

1. `个人知识学习教练`
2. `内容创作流水线助手`
3. `多来源情报监控与周报助手`

---

## 统一要求

这一层的每个项目都必须默认接入 `LangSmith` 监控，至少包括：

- tracing
- 关键节点观测
- 子代理调用链可见
- 后续可扩展 evaluation

---

## 进入项目前

开始任一项目时，先回到总入口：

[README.md](/X:/AI%20work/LangChain%20Tutorial/03-projects/Project%20Trainning/README.md)

然后按启动规则执行：

1. 先确认做哪个项目
2. 再选择开始模式
3. 如果用户写了框架，先做可行性与风险分析
4. 再进入共同实现
