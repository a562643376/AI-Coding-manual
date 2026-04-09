> ## Documentation Index
> Fetch the complete documentation index at: https://docs.qoder.com/llms.txt
> Use this file to discover all available pages before exploring further.

# MCP

模型上下文协议（MCP）通过与外部系统和数据源的无缝集成，扩展了 Qoder 的功能。本文介绍 MCP 的核心概念、支持的传输类型、配置步骤以及实际用例。

<div id="what-is-mcp">
  ## 什么是 MCP？
</div>

[MCP](https://modelcontextprotocol.io/introduction) 是一种开放协议，用于标准化应用如何向大语言模型（LLM）提供 context 和工具。通过以一致的接口暴露功能，MCP 使 LLM 能够以结构化且安全的方式与外部系统（如 API、数据库和本地工具）进行交互。

<div id="why-use-mcp">
  ### 为什么使用 MCP
</div>

MCP 通过标准化接口使 Qoder 智能体能够连接到各类外部系统和数据源，从而增强智能体在以下方面的能力：

* 获取实时信息
* 在外部系统中执行操作
* 处理结构化或非结构化数据

它支持个性化工作流，帮助开发者构建更智能、具备上下文感知能力的 AI 助手。

<div id="how-it-works">
  ### 工作原理
</div>

MCP 服务通过 MCP 协议公开其能力（例如函数和数据访问）。Qoder 会基于用户输入和工具元数据发现并调用这些能力。

Qoder 支持两种标准传输方式：

* **标准输入/输出（STDIO）**
  * 通过 stdin/stdout 流进行通信。
  * 适用于本地工具和命令行集成。
  * 需要本地环境配置——最适合专业开发者。
* **服务发送事件（SSE）**
  * 客户端到服务使用 HTTP POST 发起请求，服务到客户端通过事件流返回响应。
  * 远程托管——易于配置与使用。
  * 强烈推荐给初学者和快速原型制作。
  * 也支持 Streamable HTTP。

<div id="limitations">
  > **Note:** MCP（Model Context Protocol）服务仅在智能体模式下受支持，且最多可同时使用 10 个 MCP 服务。
</div>

<div id="configure-mcp-servers">
  ## 配置 MCP 服务
</div>

1. 在 Qoder IDE 的右上角，点击用户图标，或使用键盘快捷键（`⌘` `⇧` `,`（macOS）或 `Ctrl` `Shift` `,`（Windows）），然后选择 **Qoder 设置**。

2. 在左侧导航窗格中，点击 **MCP**。

3. 选择以下任一方式：

* 连接到你自己的 MCP 服务

a. 在 **我的服务** 选项卡中，点击右上角的 **+ 添加**。

b. 在弹出的 JSON 文件中，添加你的服务配置信息：

* Name
  * 传输类型（STDIO 或 SSE）
  * 命令和参数（用于 STDIO）
  * URL（用于 SSE 或 Streamable HTTP）

    > **Note:** 对于 Streamable HTTP，使用与 SSE 相同的方式配置URL，Qoder 会自动识别并使用

    示例：

    ```json  theme={null}
    {
     "mcpServers": {
     "github": {
     "command": "npx",
     "args": [
     "-y",
     "@modelcontextprotocol/server-github"
     ],
     "env": {
     "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
     }
     }
     }
    }
    ```

    c. 关闭文件，并在提示时点击 **保存**。

保存后，新服务会出现在你的列表中，链接图标表示连接成功。展开该条目可以查看可用工具。

> **提示：** 在服务详情中，可以通过 **服务超时时长（Request Timeout）** 下拉框设置每次 MCP 请求的超时时长。当请求执行时间超过该时长时，本次调用会自动终止，并在会话中显示超时提示。

> * 在 MCP 广场 中使用 MCP 服务

a. 点击 **MCP 广场** 选项卡。

b. 浏览可用服务列表，在目标服务上点击 **安装**。

> **注意：** 某些 MCP 服务需要额外的环境变量（如 API\_KEY 或 ACCESS\_TOKEN）才能运行。这些需要手动配置。

> c. 前往 **我的服务** 选项卡以确认安装。展开详情以查看工具列表。

> **注意：** 如果服务因缺少依赖而启动失败，点击一键修复。若问题仍然存在，请手动安装依赖。有关故障排查，请参阅 [MCP 常见问题](https://docs.qoder.com/troubleshooting/mcp-common-issue)。

<div id="use-mcp-tools">
  ## 使用 MCP 工具
</div>

Qoder 会根据以下内容自动选择合适的 MCP 工具：

* 你的输入提示
* 工具的名称和描述

在 Qoder 调用 MCP 工具之前，会先请求你确认。若要自动运行后续的所有 MCP 服务，请勾选此确认。随后，智能体会基于该工具的输出继续执行工作流的下一步。

### 步骤 

1. 在智能会话面板中，切换到智能体模式并输入你的请求。
2. 调用工具前，Qoder 会先请求确认。按 `⌘` `⏎`（macOS）或 `Ctrl` `Enter`（Windows）执行。
3. 执行后，结果会显示在聊天中。

   展开响应以查看详细的输入与输出。
4. 查看生成的代码，并按需接受更改。

<div id="example-scenarios">
  ## 示例方案
</div>

<div id="scenario-1-retrieve-and-process-web-content-remote-mcp-via-sse">
  ### 场景 1：检索并处理网页内容（通过 SSE 的远程 MCP）
</div>

使用 MCP 服务将网页内容从 HTML 获取并转换为 Markdown，便于阅读。

**步骤 1：获取 MCP SSE 服务端点**

1. 访问官方 MCP 市场网站。
2. 复制 [fetch server](https://mcpservers.org/servers/modelcontextprotocol/fetch) 的 SSE 端点 URL。

**步骤 2：添加 MCP 服务**

在 Qoder IDE 中，进入 **MCP** 页面，并按以下内容编辑 MCP 服务：

* Name:`fetch`
* Type:`SSE`
* Server endpoint: 粘贴刚才复制的 URL。

示例：

```json  theme={null}
{
  "mcpServers": {
    "fetch": {
      "type": "sse",
      "url": "https://mcp.api-inference.modelscope.net/******/sse"
    }
  }
}
```

**步骤 3：完成配置**

保存后，链接图标将显示服务已就绪。展开详情以查看工具列表。

**步骤 4：在 Qoder 中使用**

在智能体模式中，输入：

```plaintext  theme={null}
总结此文档：https://docs.qoder.com/user-guide/chat/overview
```

<div id="scenario-2-query-city-weather-local-mcp-via-stdio">
  ### 场景 2：查询城市天气（通过 STDIO 的本地 MCP）
</div>

使用本地 MCP 服务获取实时天气数据。

**步骤 1：检查前置条件**

确保已安装 Node.js。你可以让 Qoder 帮你验证：

```plaintext  theme={null}
检查本地环境，确保已安装 Node.js
```

**步骤 2：添加 MCP 服务**

在 Qoder IDE 中，打开 **MCP** 页面，并按以下设置配置 MCP 服务：

* 名称：`weather`
* 类型：`STDIO`
* 命令：`npx`
* 参数：

```shellscript  theme={null}
-y @h1deya/mcp-server-weather
```

示例：

```json  theme={null}
{
  "mcpServers": {
    "weather": {
      "command": "npx",
      "args": [
        "-y",
        "@h1deya/mcp-server-weather"
      ]
    }
  }
}
```

**步骤 3：完成配置**

保存后，链接图标会显示服务已就绪。展开详细信息即可查看工具列表。

**步骤 4：在 Qoder 中使用**

在 Agent 模式下，输入例如以下提示：

```plaintext  theme={null}
查看美国旧金山的天气
```

然后继续：

```plaintext  theme={null}
美国明天有天气预警吗？
```

<div id="references">
  ## 参考
</div>

* [MCP 常见问题](https://docs.qoder.com/troubleshooting/mcp-common-issue)
* [终端执行异常](https://docs.qoder.com/troubleshooting/terminal-execution-exceptions)

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
