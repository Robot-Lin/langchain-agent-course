# 跟学项目: 带人工审批的流程 Agent

## 所属阶段

Stage 3: LangGraph Systems

## 项目目标

设计一个 LangGraph 工作流。它需要接收用户任务，生成执行计划，在关键动作前暂停等待审批，审批通过后继续执行，失败时能够返回修订或重新规划。

## 对应知识点

- 图式设计
- State 建模
- Interrupt
- Durable execution
- 恢复路径设计

对应阅读:

- [Stage 3 Overview](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/01-overview.md)
- [Stage 3 Concepts](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/02-concepts.md)
- [Stage 3 Methods](X:/AI%20work/LangChain%20Tutorial/01-curriculum/stages/stage-3-langgraph-systems/03-methods.md)

## 最终产出

- 一张工作流图
- 一份 state 字段说明
- 一份 interrupt 设计说明
- 一份恢复策略
- 一份为什么必须使用 LangGraph 的说明

## AI 带学步骤

### Step 1: 画主路径

要做什么:

- 定义接收任务、生成计划、请求审批、执行、输出结果的主路径

为什么先做:

- 主路径决定图的主骨架

知识点关联:

- 图式设计四步法

### Step 2: 设计 state

要做什么:

- 列出会影响后续执行和恢复的字段

为什么先做:

- 没有 state，就没有真正的图式系统

知识点关联:

- State 最小集设计法

### Step 3: 设置 interrupt

要做什么:

- 在审批前和关键信息缺失时设置中断

为什么先做:

- 系统需要在关键节点正式停住

知识点关联:

- Interrupt 门设计

### Step 4: 设计恢复路径

要做什么:

- 设计审批拒绝、执行失败、信息补充后的恢复方案

为什么先做:

- 不可恢复的流程在真实任务里很脆弱

知识点关联:

- 恢复路径设计

### Step 5: 做边界复盘

要做什么:

- 判断为什么这个系统不能只用 Stage 2 的高层原型

为什么先做:

- 让学习者真正感受到 LangGraph 的必要性

知识点关联:

- 从 LangChain 升级到 LangGraph 的判断法

## 阶段检查点

- 能说清主路径
- 能给出最小 state
- 能说明 interrupt 位置
- 能写出恢复策略

## 与 Codex 的配合方式

推荐对 Codex 说:

- 先根据 Stage 3 的概念文件，带我一步步完成这个 LangGraph 审批流程项目
- 每一步先解释对应知识点，再帮我检查工作流设计
- 不要一开始就替我画完整图，先让我自己拆，再帮我修正
