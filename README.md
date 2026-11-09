# 本土美妆 · 视频素材审核分析周报（公开版）

> **Beauty Video Ad Review — Weekly Analysis Report (Public Edition)**
> A single-page, zero-build data story that connects review-volume KPIs → rejection-tag breakdown → remediation guidance → policy-change attribution.

![HTML](https://img.shields.io/badge/HTML5-single%20page-E34F26?style=flat-square)
![ECharts](https://img.shields.io/badge/ECharts-5.4.3-4C8BF5?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-22863a?style=flat-square)
![Pages](https://img.shields.io/badge/GitHub-Pages-24292f?style=flat-square)

一份**纯静态、无构建步骤**的单页分析报告。打开 `beauty_review_weekly_20261108.html` 即可阅读全部图表，也可以直接推到 GitHub 用 Pages 托管。

---

## 在线预览

- **GitHub Pages**：`https://mmorningmao.github.io/report/beauty_review_weekly_20261108.html`（把 `mmorningmao` 换成你的账号 / 组织名）
- **本地**：直接双击 `beauty_review_weekly_20261108.html`，或起一个静态服务：

```bash
git clone https://github.com/mmorningmao/report.git
cd report
python3 -m http.server 8000
# → http://localhost:8000
```

ECharts 已放进 `vendor/`，**离线也能渲染**，不依赖 CDN。

启用 Pages：仓库 **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `/(root)` → Save**。

---

## 报告里有什么

| 模块 | 内容 |
| --- | --- |
| **1 · 初审大盘** | 近双周四项 KPI（初审总量 / 初审通过率 / 视频元素总量 / 视频元素通过率）、按数据源拆分的绝对值表、YTD 逐月「柱 + 双线」图、近 14 天四指标组合图，以及两次审核尺度放宽拐点的收益归因 |
| **2 · Top10 可整改拒绝标签** | Top10 拒绝量水平条形图；每条标签逐一给出近 30 天趋势、负面 / 正面矢量示意帧、规则解读、整改建议与高命中名单 |
| **口径与数据说明** | 统计口径、标签剔除规则、案例帧性质说明 |

复盘周期：**2026-10-26 ~ 2026-11-08（W44 + W45，近双周 14 天）**。
完整的字段字典与图表读法见 [`docs/DATA-NOTES.md`](docs/DATA-NOTES.md)。

---

## 目录结构

```
report/
├── beauty_review_weekly_20261108.html                  # 报告正文，GitHub Pages 入口
├── README.md                   # 本文件
├── LICENSE                     # MIT
├── .gitignore
├── data/
│   └── report-data.json        # 页面图表所用的完整数据（与内嵌 DATA 一致）
├── docs/
│   └── DATA-NOTES.md           # 统计口径、字段字典、图表读法
└── vendor/
    └── echarts.min.js          # 本地化依赖（Apache-2.0），离线可用
```

---

## 技术栈与图表约定

- **HTML5 + CSS3 + 原生 JS**，无框架、无打包器、无 npm 依赖
- **ECharts 5.4.3** 绘制：月度柱线组合图、14 天双柱双线图、Top10 水平条形图、10 张标签趋势迷你图
- **内嵌 SVG** 绘制 20 张正负案例示意帧，不引用任何外部图片
- 图表约定：数值标签一律置于**条形外侧**；绝对量与通过率**分置左右双轴**；量级差异大的比较优先用水平条形；单图高度受控，避免长图

---

## 发布前检查

1. **替换仓库地址占位符**：把 `mmorningmao` 换成你的 GitHub 账号 / 组织名（出现在 `beauty_review_weekly_20261108.html` 顶栏与页脚链接、本文件的预览链接中）。

   ```bash
   grep -rl 'mmorningmao' . --exclude-dir=.git | xargs sed -i '' 's/mmorningmao/YOUR_GITHUB_NAME/g'
   ```

2. **确认披露授权**：按需求，本公开版**原样保留了报告中的客户名称、销售 RTX、内部业务口径与全部数值**，未做匿名化或改写。公开发布前请确认这些内容已获得对外披露许可。
3. 直接 `git init && git add . && git commit && git push` 即可，无需任何构建。

---

## License

正文与代码：**MIT**，见 [`LICENSE`](LICENSE)。
`vendor/echarts.min.js` 为 Apache ECharts，遵循 **Apache-2.0** 许可。
