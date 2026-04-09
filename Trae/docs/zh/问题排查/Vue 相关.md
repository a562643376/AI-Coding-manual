# Vue 相关

本文档记录使用 TRAE CN 进行 Vue 编程时可能遇到的问题并提供解决方法。

## Vue 文件未高亮，无法跳转

需要安装 Vue - Official 插件实现 Vue 的语法高亮以及语言服务。你可以通过以下两种方式安装：

- 打开 .vue 文件时，IDE 界面右下角会提醒安装 Vue - Official 插件，可以点击安装。

- 在插件市场搜索 Vue - Official，安装该插件。

## Vue 服务器短时间内多次崩溃，无法重启

若出现 “The Vue server crashed 5 times in the last 3 minutes. The server will not be restarted. See the output for more information“ 错误，检查是否安装了3.0.0-alpha.6 版本的 Vue - Official 插件。若是，卸载该版本，然后安装其他版本。

## 行注释功能失效

若行注释功能（macOS： command + /；Windows：ctrl + /）失效，一般是因为 Vue 的语言服务已崩溃，使用以下步骤重启：

1. 使用 Command/Ctrl + Shift + P 快捷键打开命令面板。

2. 使用 **Vue：Restart Vue and TS servers** 命令重启 Vue 的语言服务。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/30919f7a96a84249b3b419e120d884b3~tplv-goo7wpa0wc-quality:q75.awebp)

## 代码折叠失效

若代码折叠失效，一般是因为 Vue 的语言服务已崩溃，使用以下步骤重启：

1. 使用 Command/Ctrl + Shift + P 快捷键打开命令面板。

2. 选择 **Vue：Restart Vue and TS servers** 命令。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/30919f7a96a84249b3b419e120d884b3~tplv-goo7wpa0wc-quality:q75.awebp)

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
