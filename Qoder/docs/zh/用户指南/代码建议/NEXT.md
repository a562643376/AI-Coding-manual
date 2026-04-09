> ## Documentation Index
> Fetch the complete documentation index at: https://docs.qoder.com/llms.txt
> Use this file to discover all available pages before exploring further.

# NEXT

> 预测你的编码意图，生成下一段代码。

行间建议预测（NEXT）可以基于当前完整代码的上下文，结合代码修改和光标所在位置，动态预测代码变更，让开发者只需 Tab 一下，即可高效完成代码变更。

借助 Qoder NEXT，你可以：

* 在光标附近一次性编辑多行。
* 根据最近的更改和此前接受的编辑获取建议。
* 在文件中无缝跳转到下一个建议。
* 自动导入依赖项。
* 获取跨文件的修改建议，无需手动搜索相关变更。

<div id="how-it-works">
  ## **工作原理**
</div>

Qoder 会根据更改代码与 NEXT 提示的宽度，自动Inline 、 Side by Side的方式显示建议：

* 如果二者合计宽度超过编辑器宽度，建议将以Inline形式显示。
* 否则，将Side by Side显示，便于对比。

接受或拒绝建议：

* 将鼠标悬停在 **接受**/**拒绝**上，或
* 按 `Tab` 接受，按 `Esc` 拒绝。

如果下一个编辑位置不在当前视图中：

* 点击 **Tab to Jump** 或按 `Tab` 跳转至同一文件中的编辑位置。
* 若为其他文件中的编辑，点击 **Tab to Jump** 或按 `Tab` 前往目标文件的编辑位置。

预览建议的更改

* 按住 `⌥`（Mac）键 / `Alt`（Windows）键预览修改内容。
* 松开恢复原始代码。

<div id="enable-nes">
  ## **设置**
</div>

<div id="enable-nes">
  ### 启用 NEXT
</div>

1. 在 Qoder IDE 右上角，点击用户图标，或使用键盘快捷键（macOS：`⌘` `⇧` `,`；Windows：`Ctrl` `Shift` `,`），然后选择 **Qoder Settings**。
2. 在弹出的面板中，点击 **行间建议**。
3. 开启 **NEXT**。

<div id="trigger-when-commenting">
  ### 发表评论时触发
</div>

NEXT 在注释块中默认启用。你可以在“设置”中将其关闭。

<div id="auto-import">
  ### 自动导入
</div>

开启后，NEXT 会自动为 TypeScript 导入所需模块

<div id="quick-settings">
  ### 快速设置
</div>

点击右下角的 NEXT 图标以打开快速设置，你可以：

1. 全局开启或关闭 NEXT。

针对特定文件扩展名启用或禁用 NEXT，例如 Markdown 或纯文本。

<div id="display-behavior">
  ## **显示行为**
</div>

NEXT 支持对删除、修改和新增进行智能化编辑，并根据变更类型呈现相应的Diff视图。

<div id="scenarios">
  ## **使用场景**
</div>

以下是一些常见场景，展示 Qoder NEXT 如何提升你的编码效率：

* **单文件内的多点预测**\
  当你修改变量或函数名时，NEXT 会自动识别同一文件中所有相关的使用位置，并在多个位置给出更新建议。
* **自动依赖导入**\
  当你编写引用外部库或模块的代码时，NEXT 会自动检测并添加所需的 import 语句，免去手动导入的麻烦。
* **函数级自动补全** \
  NEXT 会基于你的上下文预测整个函数实现，生成具有完整逻辑和结构的函数体，而不仅仅是逐行给出建议。
* **跨文件编辑预测**\
  当你在一个文件中进行修改时，NEXT 会分析你的代码库，并主动在其他文件中提出相关修改建议，免去你手动查找依赖的工作。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../../weixin.jpg)
