# Remote SSH 相关

本文档记录在使用 Remote SSH 时可能遇到的问题并提供解决方法。

## 错误码

| **错误码** | **错误内容** | **解决方案** |
| --- | --- | --- |
| 1001 | 创建目录失败 | 检查磁盘剩余空间，确保有足够的空间用于创建目录。<br>确保有 `~/.trae-cn-server` 目录的写入权限。 |
| 1002 | 创建目录失败 | 同 1001 错误码。 |
| 1003 | 远程主机上启动 TRAE CN 服务端失败 | 检查远程主机的系统版本是否满足要求。 |
| 2001 | 下载安装包失败 | 检查网络联通性，然后重试。 |
| 2002 | 解压安装包失败 | 可能是由于安装包的下载过程被截断，导致下载的文件异常，重新安装后再尝试解压。 |
| 3001 | 远程主机上启动 TRAE CN 服务端失败 | 检查远程主机的系统版本是否满足要求。 |

## 连接超时问题

|  | **连接超时原因** | **解决方案** |
| --- | --- | --- |
|  | 服务器未启动，或网络无法连接 | **若连接失败**：<br>检查远程主机的 TRAE CN 服务端是否正常运行。<br>确认网络连接无异常。<br>**若连接成功**：继续排查其他潜在问题。 |
|  | 远程主机名称包含大写字母 | **升级客户端**：将 TRAE CN 客户端更新至最新版本。<br>**修改主机名**：将配置文件中的主机名称全部改为小写字母。 |
|  | 不支持服务器的默认 shell | 目前，一些 shell 会导致连接异常，比如 fish。将用户的默认 shell 改成 bash 和 zsh 以解决该问题。 |
|  | 本地 `~/.ssh/config` 文件位置变动 | 如果挪动过本地的 `~/.ssh/config` 文件的位置，可能会遇到这个问题。将 `~/.ssh/config` 文件放回原先的位置以解决该问题。 |

若以上解决方案仍无法解决你的问题，可以通过《[支持](https://docs.trae.cn/ide/support)》中提供的渠道联系我们。请在问题反馈中提供以下信息，以便我们尽快定位问题并协助你解决:

- IDE 截图（尽量截取完整的 IDE 界面图，以便我们分辨异常信息）。

- 日志（从输出面板复制 Remote-SSH 相关的完整日志）。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/231947d282bd44f2a24b9ac1fad903e9~tplv-goo7wpa0wc-quality:q75.awebp)

- 如果是连接超时问题，附上 `ssh -vvv <host>` 命令的完整输出结果，我们会根据此信息定位超时的原因。

- ssh -vvv test# 此处会输出大量日志，请复制完整的日志

## 网络问题

如果 AI 报告 997 错误，这通常表示你的服务器存在网络连接问题。

执行以下命令，确认你的服务器是否能成功连接到 TRAE CN 的服务：

curl -vvv "https://trae.cn"

如果以上 `curl` 命令在执行时报错，请先解决网络问题。

## 环境兼容性问题

在 Linux 上，可能会由于 GLIBC 问题导致进程无法启动。

**问题现象**

- 你无法在对话面板中与 AI 对话。

- 服务器端存在全局注入的动态库（如安全软件、监控组件，例如 `/etc/thunder/``libthunder.so`）。

**根本原因**

TRAE CN Server 为了保证在老旧系统上的兼容性，自带了一个较旧版本的 `libstdc++.so``.6`。

当系统环境中有程序（或被强制注入的库）由新版编译器编译，并依赖新版 `GLIBCXX` 符号时，TRAE CN 自带的旧库无法满足需求，从而导致加载失败。

**解决方案**

1. 在 Linux 服务器上执行以下命令，检查是否存在 `libstdc++` 版本冲突。

- grep -r "version \`GLIBCXX_.*' not found" ~/.trae-cn-server/manager-logs/

- 如果命令输出类似以下内容，说明确实存在 `libstdc++` 版本冲突，继续完成以下步骤来解决该冲突。

- .../libstdc++.so.6: version `GLIBCXX_3.4.30' not found (required by /etc/thunder/libthunder.so)

2. 找到 TRAE CN Server 的安装目录。

- 提示该目录通常在 `~/.trae-cn-server/bin/stable-<commit-id>-debian10/` 下。你也可以从报错日志中提取准确的路径。

3. 重命名自带的 `libstdc++.so``.6`：

1. 进入 `lib/trae-helper` 目录（或报错日志中指示的包含 `libstdc++.so``.6` 的目录）。

2. 重命名自带的库文件。

- # 示例路径，请根据实际的路径调整cd ~/.trae-cn-server/bin/stable-*-debian10/lib/trae-helper/# 备份并重命名自带的库文件，迫使程序使用系统的 libstdc++.so.6mv libstdc++.so.6 libstdc++.so.6.bak

4. 重启服务：

1. 完全退出本地的 TRAE CN。

2. 重启 TRAE CN。

3. 尝试重新连接远程服务器。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
