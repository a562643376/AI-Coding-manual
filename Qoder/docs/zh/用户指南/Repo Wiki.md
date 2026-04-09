> ## Documentation Index
> Fetch the complete documentation index at: https://docs.qoder.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Repo Wiki

Repo Wiki 会为你的项目自动生成结构化文档，并持续跟踪代码与文档的变更。

当你在开发过程中查询知识点、代码解释、增加功能特性时，Repo Wiki 会深入分析项目结构和代码实现，结合Repo Wiki 与上下文信息，给出更准确、详细的解答和文档支持，并且让智能体具备更深入代码库认知。

<div id="wiki-generation">
  ## **Wiki 生成**
</div>

仓库中的 Wiki 不是静态的——它会与代码保持同步。

Wiki 会在三种关键情况下更新。了解它们的触发时机与原因，有助于你保持 Wiki 的实时更新。

1. **初次生成 Wiki**

   当你首次打开项目时，默认不存在 Wiki。你可以一键从零生成。

   <img src="https://mintcdn.com/qoder/MxebqBNSE_eI2_QT/images/zh-08.png?fit=max&auto=format&n=MxebqBNSE_eI2_QT&q=85&s=e5e71c356d69dfcfa0f5a90cc232ac67" alt="Zh 08 Pn" width="2880" height="1800" data-path="images/zh-08.png" />

   <Note>
     典型生成耗时：约 120 分钟（以包含 4,000 个文件的仓库为例）。
   </Note>
2. **检测到代码变更**

   初次生成后，系统会持续监控代码的变更。

   如果你修改了已被 Wiki 记录的内容（例如函数签名、类定义、API 端点），系统会检测到当前代码与现有 Wiki 的不一致。你可以点击 **更新** 仅重新生成受影响的部分。

   <img src="https://mintcdn.com/qoder/MxebqBNSE_eI2_QT/images/zh-09.png?fit=max&auto=format&n=MxebqBNSE_eI2_QT&q=85&s=7b787256081d23484c9ef2e6bc310ee2" alt="Zh 09 Pn" width="2880" height="1800" data-path="images/zh-09.png" />

   <Note>
     请将代码变更控制在 10,000 行以内，以避免 Wiki 生成错误。
   </Note>
3. **Git 目录同步**

   > 仅适用于 0.2.0 及更高版本。

   如果你直接在 Git 目录中编辑 Markdown 文件，系统会检测到 Git 内容与 Wiki 不一致。你可以点击 **同步** 将 Git 中的变更同步并更新 Wiki。

   <img src="https://mintcdn.com/qoder/MxebqBNSE_eI2_QT/images/zh-10.png?fit=max&auto=format&n=MxebqBNSE_eI2_QT&q=85&s=ff5ef594f47af610cbef9cfd404773c3" alt="Zh 10 Pn" width="2880" height="1800" data-path="images/zh-10.png" />

   <Note>
     请不要编辑 Git 文件 `repowiki/…/meta`——这可能导致 Wiki 无法加载。该文件由系统自动管理。
   </Note>

<div id="limitations">
  ## **限制**
</div>

* 每个项目最多 10,000 个文件

  <Note>
    如果项目包含超过 10,000 个文件，建议在 Qoder 设置 → 代码库索引 → 索引排除 中排除非必要路径。
  </Note>
* 仅支持 Git 仓库且至少包含一次提交

<div id="wiki-sharing">
  ## **Wiki 共享**
</div>

> 仅适用于 0.2.0 及更高版本。

我们支持 Wiki 共享，助力团队内的知识更高效流动。

当你在本地生成 Wiki 时，系统会在代码仓库中自动创建一个专用目录：`.qoder/repowiki`。

<img src="https://mintcdn.com/qoder/94gqZHuJy25MiDXm/images/03.png?fit=max&auto=format&n=94gqZHuJy25MiDXm&q=85&s=eff7fdc2ed7ccfa27dab145170363412" alt="03 Pn" width="2880" height="1800" data-path="images/03.png" />

你可以将该目录提交并推送到远程分支。团队成员随后可通过 `git pull` 拉取生成的 Wiki 内容——无需额外配置。

<div id="multi-language-support">
  ## **多语言支持**
</div>

> 仅适用于 0.2.0 及更高版本。

Wiki 系统支持**多语言**——你可以在生成 Wiki 时选择首选语言。目前支持 **English** 和 **中文**。

在生成 Wiki 时，系统会根据你的语言选择，在 Git 目录下为每种选定的语言自动创建独立目录（例如 `repowiki/zh/`、`repowiki/en/`）。

<div id="use-cases">
  ## **使用场景**
</div>

* **架构与实现相关查询**\
  智能体凭借预构建的架构知识，几乎无需调用工具，即可快速解答诸如“X 是如何实现的？”或“哪些服务依赖此模块？”之类的问题。
* **智能体驱动的开发任务**\
  在上下文宽度受限时，Repo Wiki 可加速代码定位，支持以下任务：
  * 添加新功能
  * 修复漏洞

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
