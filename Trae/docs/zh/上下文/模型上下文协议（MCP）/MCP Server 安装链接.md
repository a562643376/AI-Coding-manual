# MCP Server 安装链接

你可以通过 TRAE 的 Schema 链接将 MCP Server 安装至 TRAE。

## 安装链接说明

链接的格式如下：

trae-cn://trae.ai-ide/mcp-import?type=${TYPE}&name=${NAME}&config=${BASE64_ENCODED_CONFIG}

链接中各组成部分的说明如下：

| **组成部分** | **是否必填** | **描述** |
| --- | --- | --- |
| `trae-cn://` | 是 | 协议方案，需使用 `trae-cn://`。 |
| `trae.ai``-ide` | 是 | 固定部分，Schema 链接处理程序。 |
| `/mcp-import` | 是 | 固定部分，Schema 路径。 |
| `type` | 是 | MCP Server 的类型。可选值：`stdio`、`http`。 |
| `name` | 否 | MCP Server 的自定义名称。 |
| `config` | 是 | Base64 编码的 JSON 配置。 |

## 生成安装链接

你可以通过自动生成或手动生成两种方式来生成 MCP Server 的安装链接。

### 自动生成

1. 打开 [TRAE MCP 安装链接生成工具](https://codepen.io/acdzh/full/WbweJjr?pkg=trae_cn&lang=zh)。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/17ceb3bb8e9b411787db12f4feade86c~tplv-goo7wpa0wc-quality:q75.awebp)

2. 在 **JSON 配置** 处，输入 MCP Server 的 JSON 配置。

- **安装链接** 处自动生成该 MCP Server 的安装链接。

3. 点击 **复制链接** 按钮，复制该 MCP Server 的安装链接。

### 手动生成

以下述 GitHub MCP Server 为例，说明手动生成安装链接的流步骤。

{  "mcpServers": {    "github": {      "command": "npx",      "args": ["-y", "@modelcontextprotocol/server-github"],      "env": {        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"      }    }  }}

步骤如下：

1. 获取 MCP Server 的类型、自定义名称、以及 JSON 配置。

- 在本示例中：

- `type`：`stdio`

- `name`：`github`

- `config`：

- {  "command": "npx",  "args": [    "-y",    "@modelcontextprotocol/server-github"  ],  "env": {    "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"  }}

2. 依次对 `config` JSON 对象进行 `JSON.stringify()` 序列化、Base64 编码，以及 URL 编码。

- 在本示例中：

- `JSON.stringify()` 序列化结果：`{"command":"npx","args":["-y","@modelcontextprotocol/server-github"],"env":{"GITHUB_PERSONAL_ACCESS_TOKEN":"<YOUR_TOKEN>"}}`

- Base64 编码结果：`eyJjb21tYW5kIjoibnB4IiwiYXJncyI6WyIteSIsIkBtb2RlbGNvbnRleHRwcm90b2NvbC9zZXJ2ZXItZ2l0aHViIl0sImVudiI6eyJHSVRIVUJfUEVSU09OQUxfQUNDRVNTX1RPS0VOIjoiPFlPVVJfVE9LRU4+In19`

- URL 编码结果：`eyJjb21tYW5kIjoibnB4IiwiYXJncyI6WyIteSIsIkBtb2RlbGNvbnRleHRwcm90b2NvbC9zZXJ2ZXItZ2l0aHViIl0sImVudiI6eyJHSVRIVUJfUEVSU09OQUxfQUNDRVNTX1RPS0VOIjoiPFlPVVJfVE9LRU4%2BIn19`

3. 将链接模板中的 `$NAME`、`$TYPE` 和 `$BASE64_ENCODED_CONFIG` 替换为 MCP Server 的实际名称、类型和 URL 编码后的 JSON 配置。

- 在本示例中，最终安装链接为 `trae-cn://``trae.ai``-ide/mcp-import?type=stdio&name=github&config=eyJjb21tYW5kIjoibnB4IiwiYXJncyI6WyIteSIsIkBtb2RlbGNvbnRleHRwcm90b2NvbC9zZXJ2ZXItZ2l0aHViIl0sImVudiI6eyJHSVRIVUJfUEVSU09OQUxfQUNDRVNTX1RPS0VOIjoiPFlPVVJfVE9LRU4%2BIn19`

## 通过安装链接导入 MCP Server

1. 将复制的 MCP Server 安装链接粘贴至浏览器的地址栏中，然后按下回车键。

2. 在浏览器的弹窗中，确认打开 TRAE CN。

3. 在 TRAE CN 中弹出的 **手动配置** 窗口中，确认 MCP Server 的配置，然后点击 **确认** 按钮。

- 该 MCP Server 已被导入。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../../weixin.jpg)
