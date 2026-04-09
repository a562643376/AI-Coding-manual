# Go 相关

本文档记录使用 TRAE CN 进行 Go 编程时可能遇到的问题并提供解决方法。

## 安装 gopls 时出现如下报错: go/pkg/sumdb/sum.golang.org/latest: no such file or directory

检查当前用户是否有 ~/go 目录的写入权限。如果没有该权限，可以使用以下命令修改权限：

sudo chmod -R 777 ~/go

## Go 1.17 版本无法使用语言服务

Trae IDE 会根据用户当前使用的 Go 版本自动安装对应的 gopls 二进制文件。但如果你使用的是 Go 1.17，Trae IDE 无法通过 `go` 命令正确识别该版本的 gopls 二进制文件，因此可能会导致无法使用语言服务。此时，先手动删除已安装的 gopls 二进制文件、dlv 文件和 staticcheck 文件，然后重启 Trae ID。

rm ~/go/bin/gopls // 删除 /go/bin 目录中的 gopls 文件rm ~/go/bin/dlv // 删除 /go/bin 目录中的 dlv 文件rm ~/go/bin/staticcheck // 删除 /go/bin 目录中的 staticcheck 文件

## go.mod 文件报错 “"{{context.GOARCH}} {{context.Compiler}}": invalid char '{'”

使用以下步骤来解决该问题：

1. 使用 Command/Ctrl + Shift + P 快捷键打开命令面板，点击 **首选项：打开用户设置（JSON）** 选项来打开 settings.json 文件，然后检查该文件中是否存在 `go.buildFlags` 配置。若有，删除该配置。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/3d8be525720843c1bfce025164eb9bb2~tplv-goo7wpa0wc-quality:q75.awebp)

2. 若步骤一无法解决问题，使用 Command/Ctrl + Shift + P 快捷键打开命令面板，然后使用 **Go：Install/Update Tools** 命令来重装 Go Tools。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/40d0b6f934f349edb063d7bbe309c2a6~tplv-goo7wpa0wc-quality:q75.awebp)

## 无法在代码间跳转

若无法在代码间跳转，任何函数和类都显示正在加载中，且重启 Trae IDE 无法解决该问题，尝试以下步骤：

1. 打开终端，执行 `go env` 命令，检查是否配置了内网的 `GOPROXY`。如果没有配置内网代理，将无法拉取 Go 依赖，导致代码分析和跳转功能异常。

- 下图中为未配置内网 `GOPROXY` 的示例：

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/65074ad26f2b44d4934024c148bc2642~tplv-goo7wpa0wc-quality:q75.awebp)

2. 如果未配置内网的 `GOPROXY`，请根据公司或网络环境，正确设置内网的 `GOPROXY`。

3. 配置完成后，重新启动 Trae IDE。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
