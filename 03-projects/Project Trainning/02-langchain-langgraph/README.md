# LangChain + LangGraph

这一层是在 `LangChain + LangSmith` 之后的进阶层。

目标是把高层 agent 升级成真正的运行时系统，开始掌握：

- `state`
- `conditional routing`
- `interrupt`
- `persistence`
- `durable execution`

这一层的关键不再只是“做出 agent”，而是“让系统能分支、暂停、恢复、继续执行”。

---

## 当前项目

1. `旅行助手图系统`
   练状态设计、分支、变更确认和恢复执行。

2. `多轮面试模拟与反馈系统`
   练多轮状态推进、条件分支和阶段性总结。

3. `研究任务分阶段执行系统`
   练阶段推进、循环判断、累积状态和最终总结。

4. `Obsidian 第二大脑更新审批图系统`
   练高风险写操作、审批、interrupt、persistence 和 durable execution。

---

## 这一层你该学会什么

- 为什么 LangChain 不够时会进入 LangGraph
- `state` 为什么是图系统核心
- `conditional edges` 和 `Command` 怎么控制路径
- `interrupt + checkpointer` 为什么一起出现
- 什么叫 durable execution

---

## 推荐顺序

1. `旅行助手图系统`
2. `多轮面试模拟与反馈系统`
3. `研究任务分阶段执行系统`
4. `Obsidian 第二大脑更新审批图系统`

---

## 进入项目前

开始任一项目时，先回到总入口：

[README.md](/X:/AI%20work/LangChain%20Tutorial/03-projects/Project%20Trainning/README.md)

然后按启动规则执行：

1. 先确认做哪个项目
2. 再选择开始模式
3. 如果用户写了框架，先做可行性与风险分析
4. 再进入共同实现
