# 上野散步 AI Guide — 独立网站版 / スタンドアロン版

这是可以独立部署的静态网站，没有构建步骤，也没有任何依赖。
ビルド不要・依存なしの静的サイトです。

## 文件结构 / 構成

```
ueno-guide-site/
├── index.html   页面本体（HTML + CSS + JS 都在这一个文件里）
├── img/         网站用图片（首页背景、景点照片、GBase 图标；来源见页脚「照片来源」）
└── README.md
```

## 第一步：部署 / デプロイ

任选一种方式，把整个文件夹原样上传即可。

- **Vercel**：New Project → 上传或导入这个文件夹 → Framework 选 “Other” → Deploy。
- **GitHub Pages**：把文件夹内容推到仓库 → Settings → Pages → Branch: `main` / root。
- **本地预览**：直接双击 `index.html` 也能打开。

## 第二步、第三步：接入 GBase 聊天窗口 / GBase の埋め込み

1. 在 GBase 管理界面「WEBサイトへの埋め込み」取得 JavaScript 嵌入代码。
2. 打开 `index.html`，搜索 `GBase チャットボット埋め込みコード`，把代码粘贴在这段注释的下方（`</body>` 之前）。
3. 重新部署。

注意：只粘贴 GBase 提供的**公开嵌入代码**，不要把 API key（`ak-...`）写进网页。网页源代码任何人都能看到。

## 页面里的 AI 部分 / AI 部分の動作

| 功能 | 独立版的行为 |
| --- | --- |
| 右下角聊天窗口 | 接入 GBase 后由 GBase bot 回答（依据 GBase 知识库） |
| 首页搜索框、「AI 向导」页的聊天框 | 提示游客使用右下角的 GBase 聊天按钮 |
| 「AI 规划路线」表单 | 用内置规则从 4 条示范路线中挑选并调整（`localPlan()` 函数），不调用外部 AI |

以后如果 GBase 提供可以从网页调用的 API，可以把 `ask()` 和 `localPlan()` 改为调用 GBase，让站内聊天框和路线规划也由 GBase 回答。

## 图片注意事项 / 画像について

- 首页背景 `hero-pond.jpg` 是 AI 生成的示意图。
- `hero-sakura.jpg`、`lotus-benten.jpg`、`ameyoko-night.jpg`、`tnm2.jpg` 是项目提供的素材，正式公开前请确认使用授权（例如 shutterstock 图片需购买授权）。
- 其他照片来自 Wikimedia Commons，页脚已标注作者与许可证，请勿删除。
- `gbase-logo.svg` 取自 gbase.ai 官网。

## 内容来源 / 情報源

- 设施信息：基础知识库 `01_Ueno_Tourism_Guide_CN_JP.docx`（UENO-KB-001）。
- 营业时间、票价、花期等动态信息请定期对照官方网站更新。
