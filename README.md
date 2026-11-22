# yzdz666.github.io

个人主页。纯静态，无构建步骤，无外部依赖。

- 线上地址：https://yzdz666.github.io/
- 首页：`index.html`
- 404：`404.html`

## 本地预览

```bash
python3 -m http.server 8080
# 打开 http://127.0.0.1:8080
```

## 改内容

所有内容都在 `index.html` 里，CSS 与 JS 内联。配色变量集中在文件顶部 `:root`：

| 变量 | 用途 |
|---|---|
| `--ink` | 主文字 / 实心按钮底色 |
| `--ink-2` / `--ink-3` / `--ink-4` | 次级文字，逐级变浅 |
| `--paper` | 页面底色 |
| `--surface` | 卡片底色 |
| `--line` / `--line-2` | 分割线，后者略深 |

`@media (prefers-color-scheme: dark)` 里有一份暗色覆盖，跟随系统切换。

项目卡片是普通 `<a>` 标签，复制一段改标题、描述、链接、Star 数即可。

## 部署

仓库名必须是 `yzdz666.github.io`，推送到 `main` 分支即自动发布（Pages 源：`main` / `/`）。
`CNAME` 不存在时使用默认域名。
