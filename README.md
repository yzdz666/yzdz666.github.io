# yzdz666.github.io

个人主页。纯静态，无构建步骤，无外部依赖。

- 线上地址：https://yzdz666.github.io/
- 首页：`index.html`
- 404：`404.html`
- 站点地图：`sitemap.xml`
- 抓取规则：`robots.txt`（已指向 sitemap）

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

## 图标与头像

站点图标取自 QQ 头像（`q1.qlogo.cn`，540×540 动图），用第一帧做了去雪花处理，只保留人物剪影，缩到小尺寸仍可辨认。

| 文件 | 用途 |
|---|---|
| `favicon.ico` | 根目录默认图标，含 16/32/48 |
| `assets/favicon-16x16.png` / `favicon-32x32.png` | 浏览器标签页 |
| `assets/apple-touch-icon.png` | iOS 添加到主屏幕（180） |
| `assets/android-chrome-192x192.png` / `-512x512.png` | Android / PWA |
| `site.webmanifest` | PWA 清单，名称、主题色、图标 |
| `assets/avatar.png` | 导航栏与关于区静态头像 |
| `assets/avatar.gif` | 关于区动图（进入视口后才加载，`prefers-reduced-motion` 下不加载） |
| `assets/og-image.png` | 社交分享图 1200×630 |

更换头像时，只需按同一命名覆盖 `assets/` 下的文件，并重新生成 `favicon.ico`。

## 页面交互

- 主题三态切换（跟随系统 / 浅色 / 深色），存 `localStorage`
- 项目按类型筛选（全部 / 机器人 / 音乐 / AI / 工具），带计数
- 导航随滚动高亮当前区块，顶部进度条同步滚动
- 回到顶部按钮、数字滚动、卡片逐条入场
- 关于区头像进入视口后由静态图切换为动图
- 已关闭移动端点击高亮与鼠标点击后的焦点框；键盘 Tab 仍有可见焦点

## SEO

- 标题、描述按「人名 + 代表项目」组织，描述控制在 75 字内
- `canonical`、`og:*`、`twitter:*` 全部指向正式域名，分享图为 1200×630
- `JSON-LD` 使用 `ProfilePage` / `Person` / `WebSite` / `ItemList` 四个节点，`sameAs` 关联 GitHub
- 语义结构：唯一 `h1`（含隐藏的品牌名）、三个带 `aria-labelledby` 的区块、时间线用 `<time datetime>`
- `h1` 的视觉文案保持不变，品牌名通过 `.sr-only` 提供给搜索引擎与读屏
- 站点地图与 `robots.txt` 已在根目录，`404.html` 标记 `noindex`

改完内容后，记得同步 `sitemap.xml` 里的 `lastmod`。
