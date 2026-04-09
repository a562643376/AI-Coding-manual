# CUE

CUE 是一款旨在提升开发效率的智能编程工具，支持代码补全、Cue-Pro、智能导入等功能。

## 功能说明

### 基础功能

基础功能包含代码补全、多行修改、修改点预测和修改点跳转。

**平台选项**：代码补全 · 多行修改 · 修改点预测 · 修改点跳转

理解当前文件中的已有代码，自动续写相关代码。![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/3ccae78833dc4270921c77c5a57f1885~tplv-goo7wpa0wc-quality:q75.awebp)

### Cue-Pro

Cue-Pro 是一种仓库级的链式补全功能。它通过学习你的编辑顺序，结合 LLM 的深度推理与工具调用能力，在完整仓库上下文下识别整体编辑意图，并生成多条连续、相关的编辑建议。这些建议会按照贴合你编码心流的顺序呈现，与真实的编码过程自然融合，帮助你以更符合思考链路的方式完成复杂修改。

### 智能导入 (Beta)

对于 Python、TypeScript 和 Golang 项目，CUE 可以识别并导入所需的依赖模块。

### 智能重命名 (Beta)

对于 Python、TypeScript 和 Golang 项目，修改变量和函数名称后，CUE 可以识别引用了该变量或函数的其他位置，并提示你将这些位置的变量或函数名称也一并修改。

## 开启/关闭 CUE

CUE 为全局设置，无论在 IDE 还是 SOLO 模式下进行启用或关闭，都会同时对两种模式生效。

1. 在 IDE 模式界面中，点击界面右上角的 **设置** 图标，进入设置中心。

- 或

- 在 SOLO 模式界面中，点击对话面板右上角的 **设置** 图标，进入设置中心。

2. 在左侧导航栏中，选择 **CUE**，进入 **CUE** 面板。

3. 打开/关闭 **Tab-Cue**、**智能导入**、**智能重命名** 开关。

- 提示Tab-Cue 为全局开关。关闭 Tab-Cue 功能后，智能导入和智能重命名功能将同步被关闭。

- 你还可以点击界面右下角的 **CUE**，然后在面板中打开或关闭 **Context Understanding Engine** 开关来全局管理 CUE 功能。

## 开启/关闭 Cue-Pro

Cue-Pro 为全局设置，无论在 IDE 还是 SOLO 模式下进行启用或关闭，都会同时对两种模式生效。

- **IDE 模式**：

1. 在左侧 **资源管理器** 中，点击 **Cue-Pro** 视图右上角的 **···** 按钮。

2. 在面板中打开/关闭 Cue-Pro。

- **SOLO 模式**：

1. 打开工具面板，选择 **编辑器**。

2. 在右侧 **资源管理器** 底部的 **Cue-Pro** 视图中，点击右上角的 **···** 按钮。

3. 在面板中打开/关闭 Cue-Pro。

![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/b2d5d3876bab4d6ebb25bc6a0d8838ee~tplv-goo7wpa0wc-quality:q75.awebp)

## CUE 的休眠与唤醒

让 CUE 在一段时间内休眠，不触发相关功能。

1. 点击 IDE 右下角的 **CUE** 图标，打开 CUE 设置面板。

2. 选择 **休眠** 选项。

3. 选择 CUE 的休眠时长。

- CUE 进入休眠，IDE 右下角显示 “Cue Snoozed”，**休眠** 选项右侧显示倒计时。点击倒计时处的 **X** 可随时取消休眠。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/4664ecb813f74c76b5a95692d9f2d834~tplv-goo7wpa0wc-quality:q75.awebp)

## 自动显示摘要

打开右下角 CUE 设置面板中的 **自动显示摘要** 开关后，将鼠标停在 CUE 图标上时，可查看 CUE 本次推荐编辑的意图。

## 快捷键

|  | **目的** | **快捷键** |
| --- | --- | --- |
|  | 跳转至修改点所在位置 | Tab |
|  | 一次性完整接受一个建议的修改 | Tab |
|  | 逐字接受一个建议的修改 | macOS：`Command + →`<br>Windows：`Ctrl + →` |
|  | 拒绝一个建议的修改 | Escape |
|  | 预览采纳后的代码状态 | macOS：Option<br>Windows：Alt |
|  | 展开/关闭 Cue-Pro 视图 | macOS：`Control + Shift + C`<br>Windows：`Shift + Windows + C` |
|  | 跳转至 Cue-Pro 提供的下一个变更 | macOS：`Command + ↓`<br>Windows：`Alt + ↓` |
|  | 跳转至 Cue-Pro 提供的上一个变更 | macOS：`Command + ↑`<br>Windows：`Alt + ↑` |

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../weixin.jpg)
