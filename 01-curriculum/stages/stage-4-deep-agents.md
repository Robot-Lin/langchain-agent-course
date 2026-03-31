# Stage 4: Deep Agents

## 阶段目标

- 理解复杂任务型 Agent 的组织方式
- 学会规划、上下文工程、子代理和复杂任务治理
- 识别 Deep Agents 的适用边界

## 关联官方主线

- [Deep Agents overview](https://docs.langchain.com/oss/python/deepagents/overview)
- [Context engineering](https://docs.langchain.com/oss/python/deepagents/context-engineering)
- [Customization](https://docs.langchain.com/oss/python/deepagents/customization)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/deepagents/human-in-the-loop)

## 学习重点

- 复杂任务规划
- Context engineering
- Subagents
- 人类审批
- 任务分解与长期执行

## 阅读知识

- Deep Agents 与普通 Agent 的差别
- 为什么复杂任务的难点是上下文组织而不只是工具调用
- 什么情况下 subagents 是必要的

## 方法掌握

- 复杂任务拆解法:
  先拆目标
  再拆阶段
  再拆角色
  再设计回收与汇总机制

- 上下文工程法:
  只给完成当前任务真正需要的上下文
  将长期资料、短期状态和任务指令分层管理

## 引导项目

- 深度研究 Agent
- 创作者内容策划 Agent
- 代码库理解顾问

## 主动练习

- 选择一个复杂任务，写出:
  主代理职责
  子代理职责
  审批点
  输出汇总方式

## 放行标准

- 能清楚解释 Deep Agents 的定位
- 能设计子代理协作结构
- 能指出复杂任务 Agent 的失控风险

## 详细教学包

- [Stage 4 入口](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/README.md)
- [核心概念](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/02-concepts.md)
- [方法模板](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/03-methods.md)
- [引导项目](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/04-guided-project.md)
- [主动练习](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/05-challenges.md)
- [考核与复盘](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/06-review-checklist.md)
- [与 Codex 对练](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-4-deep-agents/07-codex-workshop.md)
