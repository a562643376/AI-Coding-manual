> ## Documentation Index
> Fetch the complete documentation index at: https://docs.qoder.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Credits

<div id="what-are-qoder-credits">
  ## **什么是 Qoder Credits？**
</div>

Credits 是 Qoder 中高级 AI 模型的资源配额，用于衡量 AI 执行任务时消耗的计算资源。以下操作会消耗 Credits：

* Inline Chat
* Ask 模式
* Agent 模式
* Quest Mode
* Repo Wiki

实际消耗量取决于任务复杂度和所用模型。各功能的具体消耗可参考下方的[消耗参考表](https://docs.qoder.com/zh/Credits#task-and-credits-consumption-guide)。

<div id="how-to-deduct-the-credits">
  ## **扣减规则**
</div>

系统会优先消耗最先到期的 Credits，帮助您最大化利用资源。

即使 Credits 全部耗尽，Qoder 仍会提供每日限量的基础模型调用，确保核心功能不中断。

<div id="error">
  ## **失败请求**
</div>

模型调用失败时不扣减 Credits，仅在调用成功时计费。

<div id="task-and-credits-consumption-guide">
  ## **消耗参考表**
</div>

不同任务使用不同模型，成本各异。下表基于线上数据统计得出，展示各类操作的典型 Credits 消耗：

> 以 Ask 为例：单次请求调用高级模型，消耗一定量的输入/输出 Token，Credits 按模型和 Token 总量计算。Agent 请求通常在后台触发多次模型调用，消耗大于 Ask；Quest Mode 同理。Repo Wiki 的消耗取决于为代码仓库生成知识库所需的推理量。

以下数值为统计估算，实际扣减以实时用量为准。我们也在持续优化，力求用更少的资源完成同等工作。

|           | Median (50K context window) | Median (200K context window) |
| :-------- | :-------------------------- | :--------------------------- |
| Ask       | \~ 3 Credits / User Request | \~ 4 Credits / User Request  |
| Agent     | \~ 7 Credits / User Request | \~ 12 Credits / User Request |
| Quest     | /                           | \~ 100 Credits / Quest Task  |
| Repo Wiki | /                           | \~ 50 Credits / Repository   |

<Note>
  随着新功能上线，Credits 消耗率可能会调整，以反映实际资源使用情况。
</Note>

<div id="usage">
  ## 用量查看
</div>

可以在 Usage 页面查看 Credits 的历史记录和当前用量。

<div id="checking-your-credits-usage">
  ## **查看 Credits 使用情况**
</div>

登录 Qoder 官网，点击右上角头像，进入 **Settings > Usage**。

在这里可以看到当前方案信息，以及各类 Credits 的可用余额和使用明细：

* **Plan Credits**：方案包含的 Credits，在当前订阅周期内有效，周期结束时归零。
* **Add-on Credits（资源包）**：通过购买或活动获得，仅供个人使用。详见[个人资源包](https://docs.qoder.com/zh/account/pricing#credit-pack)。
* **消耗优先级**：优先使用最先到期的 Credits；到期时间相同时，先扣 Plan Credits，再扣 Add-on Credits。
* **到期时间**：不同来源的 Credits 到期时间各异，可在 Credits Log 中查看。实际到期时间可能因升级等操作而提前，详见下方日志说明。

<Tabs>
  <Tab title="Pro / Pro+ 用户">
    **获取更多 Credits**：Credits 耗尽后，基础模型仍可使用，但有相应限额。可以随时[升级方案](https://qoder.com/pricing)或[购买资源包](https://docs.qoder.com/zh/account/pricing#credit-pack)来补充。
  </Tab>

  <Tab title="Ultra 用户">
    **获取更多 Credits**：Credits 耗尽后，基础模型仍可使用，但有相应限额。你可以随时[购买资源包](https://docs.qoder.com/zh/account/pricing#credit-pack)来补充。
  </Tab>
</Tabs>

<div id="credits-log-credits-history-and-tracking">
  ## **Credits 日志**
</div>

Credits 日志记录了所有 Credits 的获取历史，包含获取原因、数量、生效日期和到期日期。

常见的获取类型：

| Description     | 说明            |
| :-------------- | :------------ |
| Plan Credits    | 方案包含的 Credits |
| Credit Purchase | 资源包购买         |
| Bonus Credits   | 活动赠送          |

<Warning>
  日志中的到期日期为发放时的初始预估值。升级方案等操作可能导致实际到期日期提前，请结合方案变更记录确认。
</Warning>

Credits 日志仅展示获取记录。如需查看当前可用余额，请查看 Usage 页面中的 Credits 卡片。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
