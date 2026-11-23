# GEO-AI

**Nature 系列 AI × 遥感 / 地球科学 论文清单** —— 2024-11 ～ 2026-11，116 篇，可搜索 / 筛选 / 排序 / 导出的单页交互表格。

> 在线浏览：[https://joelulu.github.io/GEO-AI/](https://joelulu.github.io/GEO-AI/)（GitHub Pages，部署自 `main` 分支根目录）

## 这是什么

面向 **GIS + AI 算法工程师** 的文献地图：只收 Nature 正刊及 Nature Portfolio 系列里 **AI/ML 作为核心方法、作用在遥感或地球科学数据上、并产出实质制图 / 预报 / 反演 / 归因 / 基准** 的工作。按上线日期倒序，每条给出中文主题、AI 方法、数据与观测、核心发现、阅读提示、算法标签和 DOI。

| 维度 | 数量 |
|---|---|
| 合并总篇数 | **116** |
| 2026 / 2025 / 2024 | **90** / 25 / 1 |
| Nature 正刊 / 子刊 | 12 / 76 |
| 数据期刊 / 方法期刊 | 22 / 6 |
| 研究论文 / 数据描述符 / 观点·社论 | 87 / 22 / 7 |
| 两源以上同时收录 | 19 |
| 优先精读 ★ | 37 |

## 六个正交筛选维度

表格把原先混在一起的字段拆成互不干扰的独立维度，任一组合都能正确叠加：

| 维度 | 取值 | 说明 |
|---|---|---|
| **期刊层级** | 正刊 / 子刊 / 数据期刊 / 方法期刊 | 只表示期刊在 Nature Portfolio 中的位置 |
| **文章类型** | 研究论文 / 数据描述符 / 观点·综述 / 社论 | 与层级正交，独立一列 |
| **任务族** | 气象与气候、水文与洪涝、地质灾害、农业、生态与碳、土地利用、冰冻圈、海洋与水质、基础模型与方法等 11 类 | 由宽泛学科领域收敛而来 |
| **AI 角色** | 表征学习 / 生成模拟 / 超分降尺度 / 加速轻量化 / 分割制图 / 归因可解释等 9 类 | AI 具体在做什么；**多标签**，一篇可同时占多个角色，故各类计数之和大于 116 |
| **证据状态** | 摘要核对 / 来源清单策展 | 中文要点的依据强度 |
| **来源** | 初版检索 / 自建清单 / 方法向新增 / 多源交叉 | 该 DOI 出现在哪几份检索清单里 |

页面上另有「年份」下拉，与上述六个维度叠加使用，共 7 个筛选器。

早期版本把期刊缩写（`Sci Rep`）与文章类型（`观点·综述`）都塞进「层级」一个字段，按层级筛选时会混进不相关内容，现已拆开。

## 数据文件

| 文件 | 说明 |
|---|---|
| [`data/master.json`](data/master.json) | **主数据**。每条 29 个字段 + 六个维度的字典与计数 + 来源成对交叉统计，适合二次开发 |
| [`data/papers.csv`](data/papers.csv) | 25 列全字段表，UTF-8 BOM，Excel 直接打开 |
| [`data/papers.json`](data/papers.json) | 页面同款精简数据，含统计与五条阅读路线 |
| [`data/papers.md`](data/papers.md) | Markdown 表格，便于贴进笔记 |

`master.json` 的结构：

```json
{
  "schema_version": "1.0",
  "count": 116,
  "dimensions": {
    "tier":          {"label": "期刊层级", "values": [], "counts": {}},
    "article_type":  {"label": "文章类型", "values": [], "counts": {}},
    "task_family":   {"label": "任务族",   "values": [], "counts": {}},
    "ai_role":       {"label": "AI 角色",  "values": [], "counts": {}},
    "evidence":      {"label": "证据状态", "values": [], "counts": {}},
    "source":        {"label": "来源",     "values": [], "counts": {}, "pairwise": {}}
  },
  "stats": { "total": 116, "y2026": 90, "multi_source": 19 },
  "tracks": [],
  "papers": [ { "doi": "", "tier": "", "article_type": "", "domain": "", "ai_role": ["", ""], "members": [], "evidence": "" } ]
}
```

其中 `ai_role` 是**数组**（多标签），`dimensions.ai_role.counts` 是按标签展开后的计数，`sum(counts) = 189 > 116`，属预期行为。

## 来源与去重

三份检索结果按 DOI 去重合并：

- **多源交叉 19 篇** —— 同时出现在两份以上清单，交叉核验通过。其中「初版检索 × 自建清单」14 篇、「自建清单 × 方法向新增」5 篇。
- **自建清单 45 篇** / **初版检索 25 篇** / **方法向新增 27 篇** —— 各自独有的部分，合计 97 篇。

> 早期版本把「同时出现在自建清单与方法向新增」的 5 篇只算进单一来源，于是得出「重合 14 篇」的说法，漏计了这部分。现在按每篇 DOI 实际出现在几份清单中计数，页面统计、CSV、JSON 与 Markdown 四处同源，`116 = 97 单源 + 19 多源`。

## 五条阅读路线

按 AIGC、扩散模型与模型压缩可复用的方法设计重排，页面上可一键筛选：

1. 生成式模型 / Diffusion 在地学里到底怎么用（8 篇）
2. 基础模型 / 自监督 / 多模态表征（10 篇）
3. 加速 / 轻量化 / 超分（7 篇）
4. 时空建模 / 神经算子 / 物理约束（8 篇）
5. 评测 / 可信 / 泛化（8 篇）

## 口径与核验

- **期刊范围**：Nature 正刊及 Nature Portfolio 全系，含 Nature Machine Intelligence、Nature Geoscience、Nature Communications、Nature Food、Nature Water、Nature Climate Change、Nature Sensors、Communications 与 npj 系列、Scientific Data、Scientific Reports。
- **截取窗口**：`published online` 在 2024-11-01 ～ 2026-11-20 之间；正式卷期年份可能不同。
- **核验方式**：全部 116 条经 Crossref 核对 DOI → 标题 / 期刊 / 上线日期；中文要点依据 Nature 官网与 OpenAlex 摘要人工策展。
- **局限**：非 Nature Portfolio 全量枚举，Nature Communications 体量极大仍可能遗漏；任务族与 AI 角色由题名、摘要与标签规则归类，交叉主题需看「具体任务」列细化。

## 本地预览

纯前端零依赖，双击 `index.html` 即可，也可起本地服务：

```bash
python -m http.server 8000
# 打开 http://localhost:8000
```

交互全部在前端完成：搜索覆盖标题 / 方法 / 数据 / 结论 / 标签 / DOI 及新增维度；七个下拉框可任意叠加；点表头排序；「导出当前结果 CSV」只导出筛选后的行。

## 重新生成

```bash
cd research
python build_v3.py        # 从主数据生成 index.html + data/*.{csv,json,md}
node test_reset.js        # 27 项回归测试（筛选状态与数据完整性）
```

`research/data_v3.py` 是唯一数据源：它把 `data_merged.py` 的原始记录做维度拆分并统计，`build_v3.py` 只负责渲染。要加论文就改 `data_v3.py` 上游的 `data_papers.py` / `user64.tsv` / `verified_extra.json`，再跑一次构建。

## 署名

Curated by [joelulu](https://github.com/joelulu) · 数据来源 Crossref / OpenAlex / Nature Portfolio · 检索执行日 2026-11-20
