> ## Documentation Index
> Fetch the complete documentation index at: https://docs.qoder.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Experts 模式

专家团（Experts）模式是 Qoder 面向复杂开发任务推出的多智能体协作功能。用户只需提出需求，系统就会自动拆解任务、组建专家团队，并行完成方案设计、编码实现、测试验证与质量检查，最终交付可落地的工程结果。

**一句话理解**：你提需求，AI 专家团帮你交付结果。

## 核心工作流

<img src="https://mintcdn.com/qoder/sZjjL5qUAB9BWNe-/images/experts-team-mode.png?fit=max&auto=format&n=sZjjL5qUAB9BWNe-&q=85&s=205914532ff41c6fb772cf9de94284a0" alt="专家团协作模式" width="1368" height="582" data-path="images/experts-team-mode.png" />
当你发起一个需求，**Team Lead** 会作为整个任务的「大脑」——理解目标、拆解任务、协调全局、质量把关，并根据任务需要动态「拉起」不同领域的专家并行协作：

| 角色            | 职责说明                |
| ------------- | ------------------- |
| **Team Lead** | 理解需求、拆解任务、协调调度、质量把关 |
| **前端专家**      | 负责 UI/UX 实现与交互逻辑    |
| **后端专家**      | 设计 API、数据库、服务架构     |
| **QA 专家**     | 编写测试用例，覆盖边界场景       |
| **代码评审专家**    | 确保代码规范、安全与可维护性      |
| **调研专家**      | 评估技术选型，对比方案优劣       |
| **运维专家**      | 规划部署、监控与弹性伸缩策略      |
| **UX 设计师**    | 提供界面原型与用户体验建议       |

专家之间并行执行、互不等待，Team Lead 实时对齐，确保所有输出最终拼成一个整体。

## 使用指南

### 1. 切换到 专家团（Experts）模式

在 Qoder 聊天面板顶部，点击模式切换按钮，选择 **专家团（Experts）模式**。

<img src="https://mintcdn.com/qoder/sZjjL5qUAB9BWNe-/images/experts-mode-switcher.png?fit=max&auto=format&n=sZjjL5qUAB9BWNe-&q=85&s=81fc5f83bd1dbbd4cc1b5569c06b20ad" alt="切换到 Experts 模式" width="946" height="342" data-path="images/experts-mode-switcher.png" />
切换后，你只需用自然语言描述需求，Team Lead 会自动理解目标、制定方案并协调专家团队执行。

### 2. 需求规划

专家团（Experts）模式内置了[生成规划能力](/zh/user-guide/chat/plan-agent)，在执行任务前会先生成实施方案：

1. **描述需求**：清晰说明目标、技术栈偏好、质量要求等
2. **生成计划**：Team Lead 分析需求并生成结构化的实施计划
3. **审阅调整**：你可以在执行前修改计划，补充遗漏的步骤
4. **确认执行**：计划确认后，专家团队开始并行工作

### 3. 任务列表

在任务执行过程中，聊天面板底部会显示实时任务列表：

* **待开始**：等待执行的任务项
* **进行中**：当前正在执行的任务
* **已完成**：已完成的任务项

点击单个任务，你可以随时，查看每个任务的执行进度、过程和结果

<img src="https://mintcdn.com/qoder/sZjjL5qUAB9BWNe-/images/experts-task-progress.png?fit=max&auto=format&n=sZjjL5qUAB9BWNe-&q=85&s=707a302ce8ccfe23cdbe31e81d70342c" alt="任务列表与执行进度" width="2254" height="1522" data-path="images/experts-task-progress.png" />

此外，当任务需要用户确认或介入时，通知会展示在对话框上方，方便你及时处理。
<img src="https://mintcdn.com/qoder/sZjjL5qUAB9BWNe-/images/experts-task-notification.png?fit=max&auto=format&n=sZjjL5qUAB9BWNe-&q=85&s=6ddea4b1bb3c1ca52ab4dc18ad3c6d29" alt="任务通知提示" width="3024" height="1774" data-path="images/experts-task-notification.png" />

Experts 模式下，Team Lead 将自主调度并执行绝大部分任务，仅极少数情况需要你介入确认：

* 终端命令命中黑名单或被识别为高风险操作
* 工具调用次数达到上限
* 其他需人工强干预的异常情况

### 4. 子智能体（专家）

Team Lead 会根据任务需要动态调度不同领域的专家子智能体，在会话流中，你可以看到每个专家智能体执行的状态，点击可查看详情。专家之间互不阻塞、并行执行，Team Lead 负责实时对齐和整合结果。

<img src="https://mintcdn.com/qoder/sZjjL5qUAB9BWNe-/images/experts-subagents.png?fit=max&auto=format&n=sZjjL5qUAB9BWNe-&q=85&s=b80b36f26667fea3dbdf9c07dd440785" alt="子智能体并行执行" width="2326" height="1566" data-path="images/experts-subagents.png" />

**部分专家能力列举**

* Web 端验证能力：用于 Web 端功能验证，可自动打开网页、执行交互、截图反馈。详见 [浏览器智能体](/zh/user-guide/chat/browser-agent)。
* 代码评审能力：自动检查代码规范、潜在安全问题、性能瓶颈等。
* 调研能力：从互联网检索技术资料和最佳实践，辅助技术调研与决策。详见 [浏览器智能体](/zh/user-guide/chat/browser-agent)。

### 5. 自定义子智能体（专家）

除了内置专家，你还可以创建自定义子智能体来扩展专家团能力。比如针对特定技术栈、业务场景或团队规范，定制专属专家。详见 [子智能体文档](/zh/extensions/subagent)。

### 6. 专家自演进机制

大多数 AI 工具能完成任务，却无法沉淀经验——每次面对新需求都要重新理解上下文。Experts 模式内置双向进化机制，让你的 AI 团队持续成长：

| 进化维度                   | 说明                                |
| ---------------------- | --------------------------------- |
| **Expert Skill（个体进化）** | 每位专家在任务中持续优化专项能力，用得越多，越了解你的技术栈和偏好 |
| **Team Skill（团队进化）**   | 系统记录每次组队经验，下次遇到相似任务直接召集历史最优阵容     |

<img src="https://mintcdn.com/qoder/sZjjL5qUAB9BWNe-/images/experts-skill-evolution.png?fit=max&auto=format&n=sZjjL5qUAB9BWNe-&q=85&s=9e38b3d8bf00b1bc4cbaa05f93b2b910" alt="专家技能进化" width="2314" height="1528" data-path="images/experts-skill-evolution.png" />

## 什么场景适合用 Experts 模式？

Experts 模式为中大型工程任务而生——当你期望端到端一次性交付高质量结果时，它能发挥最大价值。以下是三类典型场景：

| 场景            | 示例任务                      | Experts 如何帮你                              |
| ------------- | ------------------------- | ----------------------------------------- |
| **前后端全栈开发**   | 开发用户管理模块（注册、登录、信息管理）      | Team Lead 生成方案，前后端专家并行开发，QA 同步测试，代码评审把关质量 |
| **复杂问题定位与修复** | 线上性能瓶颈，涉及多个微服务            | Team Lead 召集后端和运维专家，协同分析日志、追踪调用链、定位并修复    |
| **技术方案调研**    | 评估 GraphQL 替代 RESTful API | 调研专家搜集资料，前后端专家评估技术栈影响，输出可执行调研报告           |

<Note>
  对于简单、明确的文件修改，智能体（Agent）模式依然是更高效的选择。
</Note>

## 最佳实践

1. 让 Experts 更懂你的意图

| 技巧         | 说明                    |
| ---------- | --------------------- |
| **描述最终目标** | 说清楚你想要什么结果，而不只是要做什么操作 |
| **提供上下文**  | 相关的业务背景、现有代码结构、技术约束   |
| **明确质量要求** | 是否需要测试、文档、代码规范检查      |
| **说明优先级**  | 哪些是必须的，哪些是可选的         |

2. 随时干预，无需中断

在专家团执行过程中，你可以随时介入调整，无需停止当前对话：

* **修正方向**：发现偏离预期？直接说明需要改进的点，Team Lead 会实时调整
* **补充需求**：有新想法或遗漏？随时补充，专家团队会增量完善
* **变更优先级**：需求变化？告知新的侧重点，团队会重新分配资源

## 开始使用

专家团（Experts）模式已上线，立即体验：

**Your AI expert team, ready to build alongside you.**

你拿到的，不只是代码——是一份经过规划、实现、测试、评审的完整交付物。

<Note>
  为确保最佳产品品质，我们将分阶段开放访问权限：

  * **Pro+、Ultra、Teams 用户**：立即开通体验
  * **Pro 用户**：优先审核

  权限开通后，您将收到邮件通知。
  👉 [立即体验](https://qoder.com/ide?waitlist)
</Note>

## 常见问题

1. 执行过程中可以修改需求吗？
   可以。你可以随时补充信息或调整方向，Team Lead 会协调专家团队适应变化。

2. 专家团（Experts）模式的成本和耗时如何？
   专家团（Experts）模式适合中高复杂度任务。相比单 Agent，耗时会增加，但质量提升显著（内部测试显示质量提升约 67%）。对于简单任务，单 Agent 更高效。

3. 专家模式的终端工具运行机制是？
   在专家模式中，终端工具会自动运行 Terminal 命令无需每次手动确认，其中潜在危险命令会自动在沙箱环境中运行。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../../weixin.jpg)
