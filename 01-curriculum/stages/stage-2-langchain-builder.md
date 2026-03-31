# Stage 2: LangChain Builder

## 阶段目标

- 用 LangChain 搭建高层 Agent 原型
- 建立组件化 Agent 设计理解
- 能判断什么问题用 LangChain 已经足够

## 关联官方主线

- [LangChain overview](https://docs.langchain.com/oss/python/langchain/overview)
- [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)
- [Human-in-the-loop](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)

## 学习重点

- 模型接入
- Tools 与 toolkits
- Structured output
- Middleware
- 基础 human-in-the-loop

## 阅读知识

- LangChain 为什么是高层入口
- LangChain 与 LangGraph 的上下层关系
- 组件化如何帮助快速做原型

## 方法掌握

- 高层 Agent 设计法:
  先定义结果格式
  再定义工具边界
  再定义对话与上下文策略
  最后加失败处理

- 原型收缩法:
  先做一条主路径
  不急着多工具
  不急着多角色

## 引导项目

- 单工具研究助理
- 结构化面试官
- 文档知识问答 Agent 的高层版本

## 主动练习

- 把一个需求分别写成:
  普通聊天应用
  LangChain 高层 Agent
- 比较二者在可靠性和可扩展性上的差异

## 放行标准

- 能独立说清 tools、structured output、middleware 的职责
- 能完成一个 LangChain 原型
- 能判断什么时候不该继续停留在高层封装

## 详细教学包

- [Stage 2 入口](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/README.md)
- [核心概念](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/02-concepts.md)
- [方法模板](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/03-methods.md)
- [引导项目](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/04-guided-project.md)
- [主动练习](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/05-challenges.md)
- [考核与复盘](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/06-review-checklist.md)
- [与 Codex 对练](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-2-langchain-builder/07-codex-workshop.md)
