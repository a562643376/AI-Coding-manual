# 添加 MCP Server

你可以直接从 TRAE 内置的 MCP 市场中添加合适的 MCP Server，或手动配置。

## 从 MCP 市场添加 MCP Server

MCP 市场中提供了社区中热门的 MCP Server，你可以选择需要的 MCP Server 进行添加。

1. 在 IDE 模式界面中，点击界面右上角的 **设置** 图标，进入设置中心。

- 或

- 在 SOLO 模式界面中，点击对话面板右上角的 **设置** 图标，进入设置中心。

2. 在左侧导航栏中，选择 **MCP**，打开 **MCP** 窗口。

3. 在 **MCP** 窗口的右上角，点击 **添加** > **从市场添加**。若你是首次添加 MCP Server，还可以直接点击窗口中部的 **从市场添加** 按钮。

- 你将进入 MCP 市场。

- ![image](https://p16-arcosite-sg.ibyteimg.com/tos-alisg-i-k9wyc2ijk0-sg/07574e4208c244f88e93962651c6da47~tplv-k9wyc2ijk0-quality:q75.awebp)

4. 在 MCP 市场中找到所需的 MCP Server。

5. 点击右侧的 **+** 按钮。

6. 在弹窗中填入 MCP Server 的配置信息。

- 提示对于标记为 “Local” 的 MCP Server，需要在本地安装 NPX 或 UVX 后才能使用。配置内容中的 `env` 信息（例如 API Key、Token、Access Key 等字段）须替换为真实信息。
- 对于标记为 “Local” 的 MCP Server，需要在本地安装 NPX 或 UVX 后才能使用。
- 配置内容中的 `env` 信息（例如 API Key、Token、Access Key 等字段）须替换为真实信息。

7. 点击 **确认** 按钮。

## 手动配置 MCP Server

如果在市场中无法找到想要的 MCP Server，或者想使用自己开发的 MCP Server，则需要手动添加。

1. 在 IDE 模式界面中，点击界面右上角的 **设置** 图标，进入设置中心。

- 或

- 在 SOLO 模式界面中，点击对话面板右上角的 **设置** 图标，进入设置中心。

2. 在左侧导航栏中，选择 **MCP**，打开 **MCP** 窗口。

3. 在 MCP 窗口的右上角，点击 **添加** > **手动添加**。若你是首次添加 MCP Server，还可以直接点击窗口中部的 **手动添加** 按钮。

- 界面上显示 **手动配置** 窗口。

- ![image](https://p16-arcosite-sg.ibyteimg.com/tos-alisg-i-k9wyc2ijk0-sg/514dfaf04f28449b837b3fe23afcf075~tplv-k9wyc2ijk0-quality:q75.awebp)

4. 填入 MCP Server 的配置内容。详情参考 “[MCP Server 配置说明](#1c9a7b75)“ 部分。

- 提示优先使用 NPX 或 UVX 配置。

- 若你希望添加一个全新的 MCP Server，将 JSON 配置内容填入输入框中，然后点击 **确认** 按钮。该 MCP Server 将被添加至 MCP 列表中。

- 若你已在其他 IDE 中配置了 MCP Server，并希望在 TRAE 中复用。你可以点击 **原始配置（JSON）** 按钮，然后将 MCP Server 的 JSON 配置内容粘贴至 TRAE 的 mcp.json 文件中。粘贴完成后，MCP 列表中将自动添加相应的 MCP Server。

## 项目级 MCP Server

你可以在项目根目录下的 `.trae/` 目录中创建 `mcp.json` 文件，并在其中声明一个或多个 MCP Server 配置。当实际需要调用相关能力时，TRAE 会自动从该文件中加载对应的 MCP Server 配置。

> **警告**

> 请务必确保工作区内所有项目文件均为可信来源，避免加载恶意配置文件导致出现安全风险。

若需启用项目级 MCP：

1. 前往 **设置** > **MCP**。

2. 打开 **启用项目级 MCP** 开关。

3. 在弹窗中完成确认。

## MCP Server 配置说明

你可以使用 JSON 文件来配置自定义 MCP Server。

### stdio 类型 MCP Server 的配置

stdio 类型的 MCP Server 通过标准输入（stdin）和标准输出（stdout）与客户端进行通信。其配置包含以下字段：

| **字段** | **是否必填** | **描述** |
| --- | --- | --- |
| command | 是 | 用于启动 MCP Server 的可执行命令。该命令必须位于系统 `PATH` 中，或使用可执行文件的完整路径。 **注意**：命令中不能包含空格，否则会导致解析错误。 |
| args | 否 | 启动命令的参数列表。每个参数必须为字符串类型。 |
| env | 否 | 传递给 MCP Server 的环境变量，每个环境变量的值必须为字符串。 |

示例：

{  "mcpServers": {    "mcp_name": {      "command": "npx",      "args": ["-y", "@modelcontextprotocol/server-github"],      "env": {        "API_Key": "value"      }    }  }}

### HTTP 类型 MCP Server 的配置

HTTP 类型的 MCP Server 通过 HTTP 或 HTTPS 协议与远程服务进行通信，其配置包含以下字段：

| **字段** | **是否必填** | **描述** |
| --- | --- | --- |
| url | 是 | 远程 MCP Server 的访问地址，需为合法的 HTTP 或 HTTPS URL。 |
| headers | 否 | 自定义的 HTTP 请求头，用于在请求中携带额外信息（如鉴权信息等）。 |

示例：

{  "mcpServers": {    "mcp_name": {      "url": "https://example.com/mcp",      "headers": {        "Authorization": "Bearer xxxx-xxxxxxx"      }    }  }}

### 超时配置

stdio 类型的 MCP Server 支持通过 `env` 字段来设置超时时间：

"env": {    "START_MCP_TIMEOUT_MS": "60000" // 启动 MCP Server 的超时时间（单位：ms）    "RUN_MCP_TIMEOUT_MS": "60000"   // 调用 MCP Server tools 的超时时间（单位：ms）}

HTTP 类型的 MCP Server 配置支持通过 `headers` 字段来设置超时时间：

"headers": {    "START_MCP_TIMEOUT_MS": "60000" // 启动 MCP Server 的超时时间（单位：ms）    "RUN_MCP_TIMEOUT_MS": "60000"   // 调用 MCP Server tools 的超时时间（单位：ms）}

### 变量引用

MCP Server 的配置支持使用变量。目前仅支持 `${workspaceFolder}`。

在 MCP Server 启动时，`${workspaceFolder}` 会被自动替换为当前项目的实际根目录路径，可用于构造与项目路径相关的命令参数或文件路径。

{  "mcpServers": {    "mcp_name": {      "command": "node",      "args": [        "${workspaceFolder}/plugins/mcp.js"      ]    }  }}

在上述示例中， `args` 里的 `${workspaceFolder}` 会被解析为工作区的真实路径。这样无论项目存放于何处，MCP Server 都能正确找到并加载 `plugins/mcp.js` 脚本。

## 添加火山引擎的 MCP Server

[火山引擎 MCP Server 市场](https://www.volcengine.com/mcp-marketplace)提供了涵盖计算、存储、数据库等云服务的 MCP Server，你可以在 TRAE 中使用它们。使用说明参考火山引擎官网对每个 MCP Server 的介绍。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../../weixin.jpg)
