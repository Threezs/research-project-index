# Research Project Index

这是我的科研仓库总入口，用来回答三个问题：每个仓库负责什么、当前项目进行到哪一步、下一步要做什么。

## 仓库地图

| 仓库 | 用途 | 主要语言 |
|---|---|---|
| [bioinformatics-literature-workbench](https://github.com/Threezs/bioinformatics-literature-workbench) | 文献元数据、阅读笔记、逐条证据、数据集登记 | R / Quarto |
| [zotero-literature-tools](https://github.com/Threezs/zotero-literature-tools) | Zotero/BibTeX、DOI、PubMed 辅助工具 | R + Python |
| [research-evidence-notebook](https://github.com/Threezs/research-evidence-notebook) | claim-level 证据和机制关系 | R / Markdown |
| [research-compendium-template-r](https://github.com/Threezs/research-compendium-template-r) | 通用可复现研究项目骨架 | R + Quarto |
| [rnaseq-analysis-template](https://github.com/Threezs/rnaseq-analysis-template) | bulk RNA-seq 统计、富集和活性分析 | R + Python |
| [bioinformatics-methods-cookbook](https://github.com/Threezs/bioinformatics-methods-cookbook) | 可复用分析配方和方法解释 | R + Python |
| [nature-methods-bioinformatics-catalog](https://github.com/Threezs/nature-methods-bioinformatics-catalog) | 近期 Nature Methods 等方法、官方代码和 turnkey 入口 | R + Python |
| [RNA_pipeline](https://github.com/Threezs/RNA_pipeline) | GEO/本地矩阵的 Snakemake 上游流程 | Snakemake + R |
| [network-pharmacology-target-acquisition](https://github.com/Threezs/network-pharmacology-target-acquisition) | 网络药理学项目与结果归档 | R + 中文文档 |
| [ligand-receptor-docking-workflow](https://github.com/Threezs/ligand-receptor-docking-workflow) | 受体/配体处理与 AutoDock Vina 流程 | Python + PowerShell |

## 项目入口

- **APAP 24h bulk RNA-seq**：先使用 rnaseq-analysis-template，把文献依据和方法选择写入 literature/evidence 仓库。
- **单细胞和空间方法选择**：先查 nature-methods-bioinformatics-catalog 的 catalog.csv，再把所选入口、版本和限制写进项目 config。
- **IR 肝损伤**：使用 evidence notebook 管理 SAA1/2、LCN2、中性粒细胞、CD177/PECAM1 和 S100A8/A9-CD36 的证据等级；没有直接证据的内容先保留为 hypothesis。
- **CRLM**：把肿瘤细胞状态、EMT/侵袭/血管生成/代谢适应相关论文放入 literature workbench，再在 evidence notebook 形成机制链。
- **网络药理学和分子对接**：保留现有仓库作为项目结果仓库，通用脚本和审计规则放入 cookbook。

## 当前阶段

状态表见 project_status.yml。每次重要运行后更新：

- 数据是否已登记；
- 关键脚本和依赖是否锁定；
- 结果是否已审阅；
- 是否已经形成可写入论文的结论；
- 下一步验证是什么。

## 运行约定

每个项目尽量保留：

1. 原始输入登记和哈希；
2. 设计、对比和阈值；
3. 完整结果表；
4. 绘图数据和最终图片；
5. 图注、方法版本和审计记录。
