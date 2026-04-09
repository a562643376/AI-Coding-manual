# MCP 教程：实现网页自动化测试

在现代化的 Web 开发中，自动化测试已成为确保应用质量、加速迭代周期的关键环节。Playwright 凭借其跨浏览器支持、强大的自动化能力以及灵活的 API，成为自动化端到端测试的理想选择。本最佳实践将详细介绍如何在 TRAE IDE 中高效集成 Playwright 这一 MCP Server，构建自动化测试解决方案，帮助你快速验证网页的交互逻辑，减少人工测试成本，提升整体开发效率。

## Playwright 支持的能力

Playwright MCP Server 支持的能力如下：

|  | **API 方法** | **能力** |
| --- | --- | --- |
|  | start_codegen_session | 开始一个新的代码生成会话，用于记录 Playwright 操作。 |
|  | end_codegen_session | 结束代码生成会话并生成测试文件。 |
|  | get_codegen_session | 获取关于代码生成会话的信息。 |
|  | clear_codegen_session | 清除代码生成会话而不生成测试文件。 |
|  | playwright_navigate | 导航到一个 URL。 |
|  | playwright_screenshot | 对当前页面或特定元素进行截图。 |
|  | playwright_click | 点击页面上的元素。 |
|  | playwright_iframe_click | 点击 iframe 中的元素。 |
|  | playwright_iframe_fill | 在页面中的 iframe 里填充某个元素. |
|  | playwright_fill | 填写输入字段。 |
|  | playwright_select | 使用 Select 标签选择页面上的元素。 |
|  | playwright_hover | 悬停在页面的元素上。 |
|  | playwright_upload_file | 将文件上传到页面中的 `input[type="file"]` 元素. |
|  | playwright_evaluate | 在浏览器控制台执行 JavaScript。 |
|  | playwright_console_logs | 检索浏览器的控制台日志（带过滤选项）。 |
|  | playwright_resize | 使用自定义尺寸或设备预设来调整浏览器视口大小。支持 143 种以上的设备预设，包括 iPhone、iPad、各类 Android 设备以及桌面浏览器，并提供正确的 User-Agent 和触控（Touch）模拟。 |
|  | playwright_close | 关闭浏览器并释放所有资源。 |
|  | playwright_get | 执行 HTTP GET 请求。 |
|  | playwright_post | 执行 HTTP POST 请求。 |
|  | playwright_put | 执行 HTTP PUT 请求。 |
|  | playwright_patch | 执行 HTTP PATCH 请求。 |
|  | playwright_delete | 执行 HTTP DELETE 请求。 |
|  | playwright_expect_response | 请求 Playwright 开始等待某个 HTTP 响应。该工具只会启动等待操作，但不会阻塞或等待该操作完成。 |
|  | playwright_assert_response | 等待并校验之前已发起的 HTTP 响应等待操作。 |
|  | playwright_custom_user_agent | 为浏览器设置自定义 User Agent。 |
|  | playwright_get_visible_text | 获取当前页面的可见文本内容。 |
|  | playwright_get_visible_html | 获取当前页面的 HTML 内容。默认情况下，输出结果会移除所有 `<script>` 标签，除非显式将 `removeScripts` 设置为 `false`。 |
|  | playwright_go_back | 在浏览器历史中后退。 |
|  | playwright_go_forward | 在浏览器历史中前进。 |
|  | playwright_drag | 将元素拖动到目标位置。 |
|  | playwright_press_key | 按下键盘键。 |
|  | playwright_save_as_pdf | 将当前页面保存为 PDF 文件。 |
|  | playwright_click_and_switch_tab | 点击一个链接并切换到新打开的标签页。 |

## 效果展示

以下为部分使用 TRAE IDE 自动化测试网页的效果展示：

- **打开网页**：该示例中，TRAE IDE 自动打开了 [https://docs.trae.com.cn/ide/model-context-protocol](https://docs.trae.com.cn/ide/model-context-protocol) 页面。

- **打开网页并点击页面上的超链接**：该示例中，TRAE IDE 自动打开了 [https://docs.trae.com.cn/ide/model-context-protocol](https://docs.trae.com.cn/ide/model-context-protocol) 页面，并点击了 “MCP 官方文档” 这一添加了超链接的文字。

## 操作步骤

跟随教程，在项目中集成 MCP Server - Playwright，配置智能体，然后使用指令来测试网页。

### 第一步：安装 TRAE IDE

前往 [TRAE CN 官网](https://www.trae.com.cn/?utm_source=content&utm_medium=doc_mcp&utm_campaign=figma)，下载 TRAE IDE 的安装包，然后将其安装至你的计算机。

### 第二步：安装 Playwright

若想在 TRAE IDE 中使用 Playwright 进行网页自动化测试，需要先在本地计算机上完成 Playwright 的安装。步骤如下：

1. 安装 Python 3。

2. 运行 `pip3 install playwright` 命令，安装 Playwright 的 Python 客户端库，使其可以在 Python 代码中使用 `playwright` 模块。开始安装后，终端会展示以下内容：

- xxxxxxxxxxx ~ % pip3 install playwrightCollecting playwright  Obtaining dependency information for playwright from https://files.pythonhosted.org/packages/32/4a/5f2ff6866bdf88e86147930b0be86b227f3691f4eb01daad5198302a8cbe/playwright-1.51.0-py3-none-macosx_11_0_arm64.whl.metadata  Downloading playwright-1.51.0-py3-none-macosx_11_0_arm64.whl.metadata (3.5 kB)Collecting pyee<13,>=12 (from playwright)  Obtaining dependency information for pyee<13,>=12 from https://files.pythonhosted.org/packages/25/68/7e150cba9eeffdeb3c5cecdb6896d70c8edd46ce41c0491e12fb2b2256ff/pyee-12.1.1-py3-none-any.whl.metadata  Downloading pyee-12.1.1-py3-none-any.whl.metadata (2.9 kB)  ...

3. 运行 `python3 -m playwright install` 命令，安装 Playwright 所需的浏览器（Chromium/Firefox/WebKit）。开始安装后，终端会展示以下内容：

- xxxxxxxxxxx ~ % python3 -m playwright installDownloading Chromium 134.0.6998.35 (playwright build v1161) from https://cdn.playwright.dev/dbazure/download/playwright/builds/chromium/1161/chromium-mac-arm64.zip124.1 MiB [==================  ] 89% 3.5sError: Request to https://cdn.playwright.dev/dbazure/download/playwright/builds/chromium/1161/chromium-mac-arm64.zip timed out after 30000ms    at ClientRequest.rejectOnTimeout (/Library/Frameworks/Python.framework/Versions/3.12/lib/python3.12/site-packages/playwright/driver/package/lib/server/utils/network.js:76:15)...

### 第三步：添加 MCP Server - Playwright

1. 打开 TRAE IDE。

2. 在 IDE 模式界面中，点击界面右上角的 **设置** 图标，进入设置中心。

- 或

- 在 SOLO 模式界面中，点击对话面板右上角的 **设置** 图标，进入设置中心。

3. 在左侧导航栏中，选择 **MCP**，打开 **MCP** 窗口。

4. 在 **MCP** 窗口的右上角，点击 **添加** > **从市场添加**。若你是首次添加 MCP Server，还可以直接点击窗口中部的 **从市场添加** 按钮。

- 你将进入 MCP 市场。

5. 在 MCP 市场中找到 Playwright。

6. 点击右侧的 **+** 按钮。

- 界面上显示 **添加 MCP Server** 弹窗。

7. 点击 **介绍页面**。

- **预览** 窗口出现并展示 MCP Server - Playwright 在 GitHub 上的介绍页面。

8. 滚动页面至 **Configuration to use Playwright Server** 部分，复制 JSON 配置内容，然后将其粘贴至 **添加 MCP Server** 弹窗中的配置内容输入框，

- 提示配置内容中的 `env` 信息（例如 API Key、Token、Access Key 等字段）须替换为真实信息。

9. 点击 **确认** 按钮。

- 添加完成后，你可以直接使用 Builder with MCP 智能体来体验 Playwright（参考“第五步”）。若你希望创建一个自定义智能体，通过配置提示词和工具来使其更好地处理你的需求，请继续往下操作。

### 第四步：创建自定义智能体并为其配置 Playwright

智能体（Agent）是你面向不同开发场景的编程助手。你可以创建自定义智能体，通过灵活配置提示词和工具集，使其更高效地帮你完成复杂任务。

1. 在 AI 对话输入框中输入 **@**，然后点击浮起面板底部的 **创建智能体** 按钮。

- 你将进入以下 **创建智能体** 面板。

2. 配置该智能体：

1. (可选) 上传智能体的头像。

2. 输入智能体的名称（例如：网页测试助手）。

3. (可选) 配置智能体的提示词。参考提示词如下，你可以直接使用或根据需求制订提示词。

- 你是一个专业的网页自动化测试专家，精通 Playwright 自动化测试工具。你的任务是根据用户的指令帮助其测试网页。

4. 在 **工具-MCP** 部分，仅勾选 **Playwright**。

5. 在 **工具-内置** 部分，勾选 **阅读**、**编辑**、**终端**、**预览**、**联网搜索**。

3. 点击底部的 **创建** 按钮。

- 配置了 MCP Server - Playwright 的智能体创建成功。点击 **立即使用** 按钮，开启与智能体的对话。

### 第五步：开启对话，自动测试网页

在上一环节中，点击 **立即使用** 按钮后，系统会自动跳转至 AI 对话框，并默认选用 **网页测试助手** 智能体（若未创建自定义智能体，则使用 **Builder with MCP**）。你可以与该智能体对话，描述你的测试需求，智能体会调用 Playwright 提供的工具和服务来自动执行任务。步骤如下：

1. 在本地新建一个文件夹，然后在 TRAE IDE 中打开它。

2. 在 AI 对话输入框右下角，选择你想使用的模型。

3. 在输入框中粘贴待测试页面的 URL（例如：https://docs.trae.com.cn/ide/model-context-protocol）。

4. 输入测试指令并发送。例如：打开该页面、打开该页面并截图、打开该页面并点击页面上的超链接，等等。

- **提示**你可以根据 “Playwright 支持的能力” 部分来设计指令。

- TRAE IDE 将调用 Playwright MCP Server 中的工具和服务完成相应操作。以下输出过程供参考：

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/3ea3c712694b45efa3e4849cf1888044~tplv-goo7wpa0wc-quality:q75.awebp)

## 了解更多

若想了解更多模型上下文协议（MCP）和智能体的相关信息，参阅以下文档：

- 概览

- 智能体概述

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
