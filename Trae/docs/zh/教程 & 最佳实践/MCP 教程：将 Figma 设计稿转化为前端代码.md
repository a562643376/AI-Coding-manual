# MCP 教程：将 Figma 设计稿转化为前端代码

还在手动从设计稿提取样式、编写基础代码？试试 TRAE IDE 的模型上下文协议（MCP）功能吧。通过使用 MCP Server - Figma AI Bridge，自动将你的 Figma 设计稿转换为整洁的前端代码，并生成相应的网页。简单高效，无需复杂配置，跟随文中的步骤操作，即可体验智能化的设计交付。让我们开始吧！

## Figma AI Bridge 支持的能力

Figma AI Bridge 支持的能力如下：

|  | **API 方法** | **能力** |
| --- | --- | --- |
|  | get_figma_data | 当无法获取 `nodeId` 时，获取整个 Figma 设计稿的布局信息。 |
|  | download_figma_images | 基于图像或图标节点的 ID，下载 Figma 设计稿中所使用的 SVG 和 PNG 图像。 |

## 效果展示

![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/5fdbb1bf196049f28d57689d35a3efdf~tplv-goo7wpa0wc-quality:q75.awebp)

## 操作步骤

跟随教程，在项目中集成 MCP Server - Figma AI Bridge，配置智能体，然后使用指令自动生成前端页面。

### 第一步：安装 TRAE IDE

前往 [TRAE CN 官网](https://www.trae.com.cn/?utm_source=content&utm_medium=doc_mcp&utm_campaign=figma)，下载 TRAE IDE 的安装包，然后将其安装至你的计算机。

### 第二步：获取 Figma 的 Access Token

配置 Figma AI Bridge 时，需要填入你的 Figma Personal Acccess Token。你可以在 Figma 安全设置中心获取它。步骤如下：

1. 登录 [Figma](https://www.figma.com/)。

2. 点击页面左上角的用户头像，然后在菜单中选择 **Settings**。

- 界面上显示设置窗口。

3. 在窗口的顶部菜单中，选择 **Security**。

- 你已进入安全设置面板。

4. 移动至 **Personal access tokens** 部分，然后点击 **Generate new token** 按钮。

- 界面上显示 **Generate new token** 弹窗。

5. 配置你的 Figma Personal Access Token：

1. 输入 Token 的名称。

2. 设置 Token 的有效期。

3. 勾选所有权限。

6. 点击窗口底部的 **Generate token** 按钮。

- Figma Personal Access Token 已生成，你会在后续配置 MCP Server - Figma AI Bridge 时用到它。

### 第三步：添加 MCP Server - Figma AI Bridge

1. 打开 TRAE IDE。

2. 在 IDE 模式界面中，点击界面右上角的 **设置** 图标，进入设置中心。

- 或

- 在 SOLO 模式界面中，点击对话面板右上角的 **设置** 图标，进入设置中心。

3. 在左侧导航栏中，选择 **MCP**，打开 **MCP** 窗口。

4. 在 **MCP** 窗口的右上角，点击 **添加** > **从市场添加**。若你是首次添加 MCP Server，还可以直接点击窗口中部的 **从市场添加** 按钮。

- 你将进入 MCP 市场。

5. 在 MCP 市场中找到 Figma AI Bridge。

6. 点击右侧的 **+** 按钮。

7. 在弹窗中，输入先前在 Figma 页面上创建的 Figma Personal Access Token。

8. 点击 **确认** 按钮。

- MCP Server - Fimga AI Bridge 配置完成，并已自动添加至内置智能体 - Builder with MCP。

- 添加完成后，你可以直接使用 Builder with MCP 智能体来体验 Figma AI Bridge（参考“第五步”）。若你希望创建一个自定义智能体，通过配置提示词和工具来使其更好地处理你的需求，请继续往下操作。

### 第四步：创建自定义智能体并为其配置 Figma AI Bridge

智能体（Agent）是你面向不同开发场景的编程助手。你可以创建自定义智能体，通过灵活配置提示词和工具集，使其更高效地帮你完成复杂任务。

1. 在 AI 对话输入框中输入 **@**，然后点击浮起面板底部的 **创建智能体** 按钮。

- 你将进入以下 **创建智能体** 面板。

2. 配置该智能体：

1. (可选) 上传智能体的头像。

2. 输入智能体的名称（例如：Figma 助手）。

3. (可选) 配置智能体的提示词。参考提示词如下，你可以直接使用或根据需求制订提示词。

- 根据用户提供的 Figma 链接，精准还原 UI 设计，生成响应式的 HTML 格式的前端页面代码。代码结构清晰，视觉细节与设计稿高度一致。禁止擅自修改设计内容，确保忠实还原。

4. 在 **工具-MCP** 部分，仅勾选 **Figma AI Bridge**。

5. 在 **工具-内置** 部分，勾选 **阅读**、**编辑**、**终端**、**预览**、**联网搜索**。

3. 点击底部的 **创建** 按钮。

- 配置了 Figma AI Bridge 的智能体创建成功。你可以点击 **立即使用** 按钮，开启与智能体的对话。

### 第五步：开启对话，完成设计需求

在上一环节中，点击 **立即使用** 按钮后，TRAE IDE 会将你引导至 AI 对话框，并默认选用 **Figma 助手** 智能体（若未创建自定义智能体，则使用 **Builder with MCP**）。你可以与该智能体对话，输入 Figma 设计稿的地址，然后描述你的需求，让智能体创建相应的前端页面。

**提示**

请确保配置 Access Token 的账号拥有设计稿的访问权限。

1. 在本地新建一个文件夹，然后在 TRAE IDE 中打开它。

2. 在 AI 对话输入框右下角，选择你想使用的模型。

3. 前往 Figma 设计稿页面，选中设计稿并右击，然后在菜单中选择 **Copy/Paste as** > **Copy link to selection**。

- 已复制该设计稿的链接。

4. 在 AI 对话输入框中，粘贴所复制的设计稿的链接。

5. 在设计稿链接的标签后输入你的需求并发送。例如：“请严格按照我提供的 Figma 链接内容生成 HTML 前端页面。UI 要严格还原设计稿，需要实现响应式设计”。

- 智能体开始调用 Figma AI Bridge 中的工具和服务，读取设计稿的内容，自动生成文件，填入前端代码，并生成一个 index.html 文件供你预览效果。以下输出过程供参考：

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/296c65183f9a4addb5eb7c80550a64b9~tplv-goo7wpa0wc-quality:q75.awebp)

6. 智能体完成输出后，双击文件夹中的 index.html 文件，在浏览器中预览效果。

7. 持续与智能体对话，优化前端页面，直至达到让你满意的效果。

## 了解更多

若想了解更多模型上下文协议（MCP）和智能体的相关信息，参阅以下文档：

- 概览

- 智能体概述

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
