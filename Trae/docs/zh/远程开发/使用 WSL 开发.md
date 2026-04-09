# 使用 WSL 开发

Windows Subsystem for Linux (WSL) 支持在 Windows 系统上无缝运行 Linux 环境，TRAE CN 的远程开发功能进一步扩展了这一能力，使你能够像连接远程服务器一样，直接在本地 WSL 环境中编写、调试和运行代码。

WSL 远程开发提供了接近原生 Linux 的开发体验，同时保留了 Windows 的易用性。无论是构建服务端应用、嵌入式开发，还是需要在 Linux 环境下测试代码，WSL 远程开发都能提供高效、一致的开发体验，无需虚拟机或双系统。本文档将介绍如何在 TRAE CN 中配置和使用 WSL 进行远程开发。

流程图**本地 PC**TRAE CN 客户端UI 插件UI 插件**WSL 发行版**TRAE CN 服务端工作区插件AI 后端终端调试器端口暴露文件系统文件系统文件系统映射/mnt/c文件系统

## 使用限制

当前仅支持 WSL 2，暂不支持 WSL 1。

## 前置条件

- PC 的操作系统为 Windows。

- 你已了解 WSL。若你是 WSL 的初学者，建议先阅读 [WSL 官方说明文档](https://learn.microsoft.com/en-us/windows/wsl/)进行了解。

- 你已在 PC 本地安装 WSL 2。若未安装，参考[此文档](https://learn.microsoft.com/en-us/windows/wsl/install)完成安装。

## 连接 WSL

1. 打开远程资源管理器，然后在右上角选择 **WSL 连接目标**。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/da0ba6e7c6cb43439a506d82e0a66b31~tplv-goo7wpa0wc-quality:q75.awebp)

2. 在 **WSL 连接目标** 文案右侧，点击 **+**（添加发行版）按钮。

- 界面上显示 WSL 发行版选择面板。

3. 选择你想安装的 WSL 发行版。当前的可选项为 Ubuntu 20.04 LTS、Ubuntu 22.04 LTS 和 Ubuntu 24.04 LTS。

- TRAE CN 开始安装所选的 WSL 发行版。你可以在 **终端** 面板中查看安装进度。

- 提示若 **终端** 面板中提示你创建帐号和密码，创建即可，否则直接等待安装完成。

4. 安装完成后，点击 **WSL 连接目标** 文案右侧的 **刷新** 按钮。

- 列表中显示已安装的 WSL 发行版。

5. 将鼠标悬浮至需连接的 WSL 发行版，然后点击 **在新窗口连接** 或 **在当前窗口连接** 按钮，或右击该发行版，然后在快捷菜单中选择。

- TRAE CN 开始连接至指定的 WSL 发行版。连接完成后，界面左下角显示已连接的 WSL 发行版。

6. 打开文件夹或克隆 Git 仓库进行开发。

## 断开与 WSL 的连接

- 直接退出 TRAE CN，下次打开后会优先提示你连接 WSL。

- 在顶部菜单栏中，选择 **文件** > **关闭远程连接**。

## 快捷操作面板说明

使用 Alt + Ctrl + O 快捷键可打开 WSL 快捷操作面板。

你可以在面板上进行以下操作：

|  | **编号** | **说明** |
| --- | --- | --- |
|  | 1 | 点击后，直接连接到默认的 WSL 发行版。 |
|  | 2 | 点击后，可以选择指定的 WSL 发行版进行连接。 |
|  | 3 | 点击后，在界面左侧打开远程资源管理器 - WSL 面板。 |

## 更多功能

### 设置默认连接的 WSL 发行版

TRAE CN 下载的第一个 WSL 发行版会被自动设置为 “默认 Distro”。下载更多发行版后，你可以右击某个发行版，然后在快捷菜单中选择 **设置为默认 Distro**。

### 管理插件

插件可分别在本地的 UI / 服务端，或 WSL 中运行。在插件市场的 **已安装** 列表中，你可以查看本地和 WSL 中安装的插件，然后按需管理它们。

![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/aaf25b409e934ec69cfb63155c204a36~tplv-goo7wpa0wc-quality:q75.awebp)

### 在 WSL 中打开终端

在顶部菜单栏中，选择 **终端** > **新建终端**，在 WSL 中打开终端，然后执行所需命令。

![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/309b56960fe24938bf3c36c0ea9ae057~tplv-goo7wpa0wc-quality:q75.awebp)

### 远程调试

连接到 WSL 后，可以使用 TRAE CN 的调试功能，与本地调试类似。在 launch.json 文件中选择启动配置并按 F5 键开始调试，应用程序将在远程主机上启动，调试器会附加到其中。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
