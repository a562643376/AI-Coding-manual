# Python 相关

本文档记录使用 TRAE CN 进行 Python 编程时可能遇到的问题并提供解决方法。

## Python 无法通过 “Command/Ctrl + 鼠标左键” 跳转到函数定义

语法检测、跳转函数定义等类似的功能是由该语言对应的 Language Server Provider（简称 LSP）提供。以 Python 为例，如遇到了 Python 文件里无法通过快捷键跳转到函数定义，可能的原因有以下几种：

- Trae CN 中未安装 Python 相关的 LSP 插件，如 Python、Pylance、Pyright 等。

- Python 相关的 LSP 插件由于某些原因（如仓库过大等）未能加载成功。

- 受限于插件开发者的[服务条款限制](https://marketplace.visualstudio.com/items/ms-python.vscode-pylance/license)，Python 相关的 LSP 插件只能在特定产品中使用，如由 Microsoft 开发的 Python 插件明确提出只能在 VS Code 中使用。

同样以 Python 为例，针对无法跳转到函数定义的问题，可按照以下步骤逐一排查：

1. 进入插件市场，检查是否已安装了 Python 相关的 LSP 插件。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/25d30ec59b1840ef910ca166d92c06d0~tplv-goo7wpa0wc-quality:q75.awebp)

2. 若已安装了由 ms-python 提供的 Pylance 插件，将其卸载。

- 提示在 VS Code 中安装 Python 时一般会自动安装 Pylance，所以从 VS Code 或 Cursor 导入配置到 Trae CN 后，更容易遇到 LSP 不生效的问题。

3. 搜索并安装开源社区中 Python 相关的 Language Server，如 BasedPyright。

1. 打开 Editor 设置，搜索 pyright type checking mode。

4. 安装 BasedPyright 后，打开任意 Python 文件，鼠标右击任一一处引用的函数，在出现的菜单中可看到 “转到定义” 等菜单项，即说明 LSP 插件正常可用。

## Python 代码中，使用 F2 键修改变量名会使每一行后都添加空行

微软的 Python 插件自带了语言服务 Jedi，无需使用它。前往插件市场，然后安装 BasedPyright 插件进行使用。

## 无法使用代码跳转功能

参考以下解决方法：

- Python 插件 2025.6.1 版本在某些项目上会报错，你可以安装 BasedPyright 插件作为替代。

- 检查 Python 语言服务插件，如 BasedPyright 插件是否被禁用。若被禁用，需将其开启。

- 检查 Python 语言服务是否崩溃。若奔溃，使用 Command/Ctrl + Shift + P 快捷键打开命令面板，然后使用 **Python：重启语言服务器** 命令来重启 LSP。

## 语法高亮功能失效

打开插件市场，然后找到 Python 插件。若插件的状态如下图所示，需卸载后再重新安装。

![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/05c9fb99bf374db5af60c5afb9dbd107~tplv-goo7wpa0wc-quality:q75.awebp)

## 无法自动激活 Conda/venv 环境

目前 Python 插件的已知 Bug 如下：

- [https://github.com/microsoft/vscode-python/issues/25051](https://github.com/microsoft/vscode-python/issues/25051)

- [https://github.com/microsoft/vscode-python/issues/25284](https://github.com/microsoft/vscode-python/issues/25284)

- [https://github.com/microsoft/vscode-python/issues/25267](https://github.com/microsoft/vscode-python/issues/25267)

此问题的临时解决方案如下：

1. 使用 Command/Ctrl + Shift + P 快捷键打开命令面板。

2. 点击 **首选项：打开用户设置（JSON）** 选项来打开 settings.json 文件。

- ![image](https://p9-arcosite.byteimg.com/tos-cn-i-goo7wpa0wc/3d8be525720843c1bfce025164eb9bb2~tplv-goo7wpa0wc-quality:q75.awebp)

3. 在 settings.json 文件中添加以下配置：

- "python.experiments.optOutFrom": [    "pythonTerminalEnvVarActivation"  ],

4. 保存文件，然后重启 IDE。

##

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
