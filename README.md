# GEO-AI

**Nature 系列 AI × 遥感 / 地球科学 论文清单** —— 2024-11 ～ 2026-11，116 篇，可搜索 / 筛选 / 排序 / 导出的单页交互表格。

> 在线浏览：[https://joelulu.github.io/GEO-AI/](https://joelulu.github.io/GEO-AI/)（需在仓库 Settings → Pages 开启 `main / root`）

## 这是什么

面向 **GIS + AI 算法工程师** 的文献地图：只收 Nature 正刊及 Nature Portfolio 系列里 **AI/ML 作为核心方法、作用在遥感或地球科学数据上、并产出实质制图 / 预报 / 反演 / 归因 / 基准** 的工作。按上线日期倒序，每条给出中文主题、AI 方法、数据与观测、核心发现、阅读提示、算法标签和 DOI。

| 维度 | 数量 |
|---|---|
| 合并总篇数 | **116** |
| 2026 / 2025 / 2024 | **90** / 25 / 1 |
| Nature 正刊 / 子刊 | 12 / 69 |
| 数据期刊 / Scientific Reports / 观点综述 | 22 / 6 / 7 |
| 优先精读 ★ | 37 |

数据来源为三份清单按 DOI 去重：初版检索 39 篇、自建清单 64 篇、2026 方法向补检索 27 篇；三份交叉核验 14 篇，合并后互补性强（重合率 21.9%）。

## 五条阅读路线

页面里可一键筛选，这里只列要点：

1. **生成式模型 / Diffusion** — GenCast 扩散集合、生成式降尺度、GAP 生成式同化、条件生成地震动、扩散降尺度横评与 RainShift OOD 基准。
2. **基础模型 / 自监督 / 多模态** — SkySense++、AlphaEarth 嵌入、WorldTensor、AgroFusion、FTPD-ML、CHMv2。
3. **加速 / 轻量化 / 超分** — LMW-YOLO、LDA-YOLO、降阶 EOF 空间加速、ViSIR/ViFOR 频域超分、FuXi-CFD。
4. **时空建模 / 神经算子 / 物理约束** — Quake Neural Operator、Transformer 神经算子、物理引导风场、Cross-Unet、资料同化与 ML 融合。
5. **评测 / 可信 / 泛化** — 甲烷单盲测试、SHAP 归因、跨地理泛化、架构消融与偏差审计。

## 文件结构

```
index.html            # 站点入口，纯前端零依赖，离线打开也完整可用
data/papers.csv       # 19 列全字段（UTF-8 BOM，Excel 直接打开）
data/papers.md        # Markdown 表格
data/papers.json      # 结构化数据 + 分类字典 + 五条路线的 DOI 列表
favicon.svg
.nojekyll             # 避免 GitHub Pages 的 Jekyll 处理
```

## 本地预览

```bash
git clone https://github.com/joelulu/GEO-AI.git
cd GEO-AI
python -m http.server 8000
# 打开 http://localhost:8000
```

`index.html` 不依赖任何 CDN，直接双击打开也能用（下载链接需经 HTTP 服务才能生效）。

## 口径与核验

- **期刊范围**：Nature 正刊及 Nature Portfolio 全系（Nature Machine Intelligence、Nature Geoscience、Nature Communications、Nature Food / Water / Climate Change / Sensors、Communications Earth & Environment / Physics / Sustainability、npj 系列、Scientific Data、Scientific Reports 等）。数据期刊与 Scientific Reports 单独标注层级。
- **纳入标准**：AI/ML 是核心方法，作用于遥感影像或地学数据，产出实质性制图、预报、反演、归因或可复用基准。观点 / 综述 / 社论与数据描述符保留但显式标注；纯方法学无地学落地者剔除。
- **核验方式**：逐条用 Crossref 核对 DOI → 标题、期刊、上线日期；OpenAlex 摘要与 Nature 官网补方法 / 数据 / 结论；中文要点为人工策展。
- **日期**：使用 published online，与正式卷期年份可能不同。部分 2026 年上线的 Scientific Reports 论文 DOI 含 2025 字样，属正常编号。

## 局限

非 Nature Portfolio 全量枚举，Nature Communications 体量极大仍可能遗漏。3 篇论文摘要未获取（据题名与 Crossref 元数据归纳，页面阅读提示中已标注需核对原文）。1 篇行星遥感属范围边缘扩展。

---

Curated by [joelulu](https://github.com/joelulu) · 数据来源 Crossref / OpenAlex / Nature Portfolio / 公开中文解读 · 检索执行日 2026-11-20
