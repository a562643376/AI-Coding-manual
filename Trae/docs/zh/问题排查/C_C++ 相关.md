# C/C++ 相关

本文档记录使用 TRAE CN 进行 C/C++ 编程时可能遇到的问题并提供解决方法。

## 无法识别 `#include` 指令、跳转功能失效

检查是否同时安装了 clangd 和 Microsoft C/C++ 插件。这两个插件不能同时安装，否则会冲突，导致跳转等功能异常。如果同时安装上述两个插件，卸载其中一个。建议保留你平时主要使用的插件。

此外，你需要让你的编译工具生成一个 compile_commands.json 文件，声明哪些文件需要编译，每个文件的编译参数是什么。目前 clangd 插件和 Microsoft C/C++ 插件都支持 compile_commands.json 文件（详见[此文档](https://clangd.llvm.org/installation#project-setup)）。你可以将 compile_commands.json 文件放在项目根目录，或者根目录下的 build 文件夹中。

如果你使用的构建工具是 CMake，可以执行以下命令来生成一个 compile_commands.json 文件：

cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=1

如果你使用的构建工具是 XMake，使用以下命令：

xmake project -k compile_commands

## 配置 C++ 远程调试时，报错 “配置的类型‘cppdbg’不受支持”

该错误通常是因为远程环境未安装必需的 C/C++ 插件。确保在远程机器（或远程开发环境）中安装了 Microsoft 的 C/C++ 插件（通常名称为 `ms-vscode.cpptools`），以支持 `cppdbg` 调试类型。

安装完成后，重启远程环境，再次尝试调试。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
