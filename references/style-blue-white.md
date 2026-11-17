# 蓝白商务简历风格（可选）

一套「白底 + 深蓝强调色」的单页 A4 简历视觉方案。适用于后端 / 全栈 / Agent 等技术岗，
视觉上比纯白模板更有层次，但保持克制：只用一种主色，不堆装饰。

主色统一为 `#1A5FB4`，浅色底统一为 `#EAF2FD` / `#EFF6FF`，分隔线为 `#BFDBFE`。

## 设计基调

- 白色纸张背景，正文 `#1F2937`，标题与强调色 `#1A5FB4`。
- 允许**极淡**渐变（仅头部一条，白→浅蓝）与**极淡**投影（头像、按钮），除此之外不加装饰。
- 不用彩色大色块、不用条纹背景、不用动效。
- 全篇只有一种强调色，避免蓝 + 其他彩色混用。

## 设计 token

| 用途 | 值 |
|---|---|
| 主色 / 图标 / 章节标题 / 链接 | `#1A5FB4` |
| 深色标题（公司名、项目名） | `#0F2F5F` |
| 正文 | `#1F2937` |
| 浅色底（章节标题、日期标签） | `#EAF2FD` |
| 浅色底（信息块） | `#EFF6FF` |
| 分隔线 / 浅色描边 | `#BFDBFE` |
| 链接下划线 | `#93C5FD` |
| 正文字号 / 行高 | 16px / 21.5px |
| 姓名 | 24px / 29px，字重 700，字距 1px |
| 章节标题 | 17.6px / 22px，字重 700 |

## 组件规则

1. **头部信息区**：整块加 `linear-gradient(135deg,#E8F1FD 0%,#F6FAFF 45%,#FFFFFF 100%)`，
   底部圆角 12px；头像 80×112、圆角 8px，外加 `0 0 0 3px #DBEAFE` 描边和极淡投影。
2. **章节标题**：浅蓝圆角底块（`background:#EAF2FD;padding:1px 9px;border-radius:6px`），
   标题文字用主色，左侧保留图标；标题下方保留 1px 浅蓝分隔线。
3. **实习 / 项目标题行**：左侧 4px 深蓝竖条 + 10px 内边距；公司名、项目名用深藏蓝 `#0F2F5F`。
4. **日期**：浅蓝圆角标签（`background:#EAF2FD;color:#1A5FB4;padding:0 7px;border-radius:9px`），
   只加水平内边距，保证行高不变。
5. **按钮 / 标签**（GitHub 地址、在线体验）：深蓝底白字，图标必须显式设为白色，
   链接用 `<a>` 并加 `target="_blank" rel="noopener"`；`text-decoration:none`。
6. **项目简介**：不加底色、不加边框、不加阴影，与正文同字号，仅「项目简介」四个字用主色加粗。
7. **列表**：`▸` 符号用主色；关键数字加粗；技术名词可用等宽字体或加粗。
8. **技能区**：单列 4–5 行，类别名（后端框架、数据中间件等）用主色加粗；行距 8px。

## 可直接复用的 CSS

```css
body { color:#1F2937; font-family:"Noto Sans SC","Microsoft YaHei",sans-serif; }
h1 { font-size:24px; line-height:29px; font-weight:700; letter-spacing:1px; }
h2 { font-size:17.6px; line-height:22px; font-weight:700; display:flex; align-items:center;
     column-gap:3px; margin:0 -4px; color:#1A5FB4; background:#EAF2FD;
     padding:1px 9px; border-radius:6px; }
.hline { height:1px; background:#BFDBFE; margin:0 -4px; }

.hdr { background:linear-gradient(135deg,#E8F1FD 0%,#F6FAFF 45%,#FFFFFF 100%);
       border-radius:0 0 12px 12px; }
.photo { box-shadow:0 0 0 3px #DBEAFE, 0 6px 14px rgba(26,95,180,.16); }

.jobhead, .phead { padding-left:10px; border-left:4px solid #1A5FB4; border-radius:3px; }
.jobhead b, .phead b { color:#0F2F5F; }
.jobhead .date, .phead .date { background:#EAF2FD; color:#1A5FB4; padding:0 7px;
                               border-radius:9px; font-weight:700; }

.pill.dark { background:#1A5FB4; color:#fff; }
.pill.dark i { color:#fff; }
.phead a.pill { text-decoration:none; }

.box { background:none; border:0; padding:0; box-shadow:none; }
ul.bul li .bullet { color:#1A5FB4; }
.skl b { color:#1A5FB4; }
a.gh { color:#1A5FB4; text-decoration-color:#93C5FD; }
i[class^="i-"] { color:#1A5FB4; }
```

## 一页排满

- 页面按 A4（794 × 1123px，`@page{margin:0}`）排版，正文底部目标落在 1080–1102px。
- 首次排完若底部留白超过 60px，优先调行距与间距，不要加内容：
  正文行高 20.5 → 21.5 → 22px；列表项间距 3 → 5px；章节上间距 9 → 14 → 16px；
  技能行距 6 → 8px。
- 如果还超出，再按「措辞压缩 → 删低价值条目」处理；字号保持 16px 不变。
- 打印时保留背景色：`-webkit-print-color-adjust:exact; print-color-adjust:exact;`。

## 链接与 PDF

- 所有链接使用真实 `<a href="...">`，不要用 `<span>` 伪装按钮。
- 外链统一 `target="_blank" rel="noopener"`。
- Chrome 导出 PDF 时会保留链接注解，导出后可用 `pypdf` 检查 `/Annots` 中的 `/URI`。
