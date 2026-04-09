# AI-Coding-manual

中文离线手册：整合 [Qoder](https://docs.qoder.com/zh/) 与 [TRAE 文档](https://docs.trae.cn) 公开帮助站点的 Markdown。目录结构与官方「文档」侧栏分组一致，阅读顺序可参考 [list.md](list.md)。

## 目录说明

| 路径 | 说明 |
| --- | --- |
| `Qoder/docs/zh/` | Qoder 中文文档 |
| `Trae/docs/zh/` | TRAE 中文文档 |
| `weixin.jpg` | 文末统一引用的二维码配图 |

正文已去除官方站点底栏中的 Mintlify 声明；每篇末尾附有微信公众号相关配图（`@weixin.jpg` + 相对路径图片），便于在 GitHub 上直接浏览。

## 更新导出

在 `caiji` 仓库中执行：

```text
py tools/export_ai_coding_manual.py
```

然后在 `AI-Coding-manual` 目录内提交并推送。

说明：导出时只会覆盖 `Qoder/`、`Trae/` 及根目录的 `weixin.jpg`、`list.md`、`README.md`、`.gitignore`，不会删除 `.git`，以便在同一文件夹内直接 `git push`。
