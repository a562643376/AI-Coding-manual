# MCP Server 相关

本文档记录在 TRAE CN 中使用 MCP Server 时可能遇到的问题并提供解决方法。

## TRAE 未读取到 MCP Server 中的工具

使用添加了 MCP Server 的 Builder with MCP 或者自定义智能体时，即使在对话中明确要求模型调用某个 MCP Server 中的工具，模型依然无法调用或识别该工具。

**原因：**

受模型上下文窗口大小的限制，TRAE 仅会预留一部分固定的上下文空间，用于向模型传递 MCP Server 及其工具的描述信息。目前存在以下限制：

- 所有 MCP Server 描述信息的字符数上限：8,000

- 所有 MCP Server 工具的数量上限：40

当 MCP Server 的配置达到任一上限时，TRAE 会按工具维度丢弃无法容纳的工具描述信息。

**解法**：

- 在智能体配置面板中，取消勾选当前任务不需要的 MCP Server 和工具。这将释放部分上下文窗口，确保核心 MCP Server 的工具能被完整读取。

- 修改 MCP Server 和工具的 `description` 字段，使用更简练的描述，避免冗长。

- 仅使用当前场景必需的工具。如果一个 MCP Server 包含大量工具（接近或超过 40 个），建议将其拆分为多个功能更专注的小型 MCP Server，并按需启用。

## 模型无法完整读取 MCP Server 的响应内容

MCP Server 执行成功，但在下一轮对话中，模型要么无法读取 MCP Server 的任何响应内容，要么只能读取部分内容。

**原因**：

受模型上下文窗口大小的限制，TRAE 会对 MCP Server 的响应内容进行动态裁剪，以确保整体上下文能够被模型正常处理。该裁剪机制受以下因素影响：

- **模型上下文窗口大小的不同**

- 不同模型支持的上下文窗口存在差异，目前主流模型的上下文窗口通常在 45K 左右。但 MCP Server 的响应内容无法独占全部上下文空间。

- **当前对话的上下文占用情况**

- MCP Server 响应内容可用的上下文受当前对话中已引入上下文内容的影响，例如 `#File`、`#Doc`、`#Folder` 等引用内容。

- **工具调用历史的累积影响**

- 随着 MCP Server 工具调用次数增加，历史工具响应会持续占用上下文空间。当可用空间不足时，TRAE 会优先裁剪较早的工具调用响应内容。

**解法**：

- 新建对话，这是最直接且有效的释放上下文窗口的方法。

- 减少非必要的上下文引用，仅引用当前任务绝对必需的代码片段、文件、文件夹等。

- 如果你是该 MCP Server 的开发者，可以尝试优化工具的返回数据结构，例如精简输出和结构化摘要。

## 错误：您必须提供一个命令

当 MCP Server 通过 `npx` 启动时，系统的 Node.js 版本需为 20 及以上。升级 Node.js 后重启 TRAE，即可解决相关问题。

## npm 相关报错

如果报错信息中出现以下内容，这类问题通常与 npm 的本地缓存异常有关。

- `cannot find module 'xxx'`

- `Error: EACCES: permission denied, mkdir 'xxx'`

- `/Users/xxx/.npm/_npx/__cache/...`

- `/Users/xxx/.npm/_npx/<一串 16 进制数字>/node_modules/...`

按顺序尝试以下命令，每执行一条命令后，重启一次 TRAE，并检查问题是否已解决。

npm cache clean --forcesudo npm cache clean --forcerm -rf ~/.npm/_npxsudo rm -rf ~/.npm/_npx

如果该错误依然存在，则需进一步检查 npm 版本：

1. 在错误日志中查找类似下图所示的信息。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/472c858e0bd6459f80968eb979e7f3fb~tplv-goo7wpa0wc-quality:q75.awebp)

2. 确认当前 npm 版本是否过旧。

3. 如果是 npm 6.x 或更低版本，升级 npm。

4. 升级完成后，重新启动 TRAE 并再次尝试。

## WSL 环境下无法使用 npx 命令

在 WSL 环境中，`node` 命令可以正常执行，但 `npm` 或 `npx` 命令无法使用。

**原因**：

WSL 默认预装的 Node.js 往往是精简版本（通常位于 /usr/bin/node ），不包含 `npm` 包管理工具。由于 `npx` 是 `npm` 的一部分，因此也无法运行。

**解法**：

在终端执行以下命令，安装缺失的 `npm` 工具：

sudo apt install npm

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
