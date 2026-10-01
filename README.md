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


## 按功能使用仓库

| 科研阶段 | 先进入 | 再进入 | 结果/证据 |
|---|---|---|---|
| 文献发现与方法选择 | bioinformatics-literature-workbench | nature-methods-bioinformatics-catalog | DOI、方法卡片、功能入口和限制 |
| 原始 count 与 bulk RNA-seq | rnaseq-analysis-template | bioinformatics-methods-cookbook | QC、edgeR QL、DE、ORA/GSEA、TF activity |
| 单细胞/空间方法 | nature-methods-bioinformatics-catalog | bioinformatics-methods-cookbook | 输入审计、baseline、模型输出和样本级汇总 |
| 机制证据管理 | research-evidence-notebook | literature-workbench | claim、替代解释和验证实验 |
| 网络药理学与对接 | network-pharmacology-target-acquisition | ligand-receptor-docking-workflow | 成分-靶点、配体/受体、结构与 MD 交接 |

### 方法状态的统一含义

- `baseline-function`：依赖轻、结果可解释，适合先建立基线。
- `runtime/integration-required`：必须接入真实 AnnData、BAM、GTF、FASTA 或 transcript count。
- `manifest-only`：当前只固定 checkpoint、输入和版本，不能把配置文件当作已完成推理。
- `sample-level-required`：CellRank、embedding、niche 和细胞比例等输出需要回到 sample/donor 后才进入条件比较。


## 新增的近期方法分支

方法目录已经加入三个新的 Nature Methods 方向，统一由 `execution_mode` 标记为 manifest-only：

- **Mellon**：cell-state density 与时间连续化；先固定 representation，再把 density 按 sample/donor 汇总。
- **MISO**：多模态空间组学整合；先审计 shared spot/cell key、坐标和图像特征。
- **SCMMIB**：paired/unpaired/mosaic 多模态整合 benchmark；按任务记录 accuracy、robustness 和 scalability。

它们适合作为 APAP/IR/CRLM 单细胞或空间项目的候选扩展，不替代 bulk RNA-seq 主统计模型，也不把 manifest 当作模型已完成推理。


## 近期方法继续扩展

- **scMultiBench**：多任务多模态整合评估，按 reduction、batch correction、clustering、classification、imputation、feature selection、spatial registration 和 split 记录。
- **NaRMBench**：nanopore direct-RNA 修饰检测评估，按 RNA002/RNA004 chemistry、ground truth、retraining 和 site-level calibration 记录。

这两个方向保留在 catalog 的 manifest-only 分支，适合方法筛选和审计；真正的 benchmark 数值要在官方环境中重新运行。

- **PINNACLE**：单细胞蛋白上下文和靶点优先级；先审计 expression、PPI network、cell-type/tissue metadata，再在 held-out 任务上比较排序基线。

- **PHLOWER**：多模态复杂分支轨迹；先审计共享 cell ID、模态预处理和 root/direction，再比较 branch stability。
## 空间数据基础设施

- **SpatialData / P019**：进入空间模型前先固定元素、坐标、单位、变换和平台 reader；入口为 `python/16_spatialdata_manifest.py`。
- 它用于互操作和可追溯性，不自动修复 segmentation/registration，也不替代空间生物学验证。
## 通用 Python 工具层

- **scikit-bio / P020**：序列、表格、距离、多样性、taxonomy 和系统发育的通用入口；先固定操作、格式、ID、metadata 和统计设计。
- 入口为 `python/17_scikit_bio_manifest.py`，不自动替代样本级设计或生物学验证。
## 空间域聚类共识层

- **SACCELERATOR / P021**：在 SpatialData/MISO/Nicheformer 后比较空间聚类方法、空间指标与专家共识；入口为 `python/18_saccelerator_manifest.py`。
- 手工标签作为比较证据，不能自动当作真值；高分歧区域要回到原始图像和独立验证。

## 空间 foundation model 扩展

- **Novae / P022**：图结构 foundation model，支持 spot/cell 空间域、跨 gene panel/组织/技术平台迁移、原生 batch correction、空间可变基因/通路和组织架构分析。
- 入口：`python/19_novae_manifest.py`；在 SpatialData 坐标/元素审计后固定 panel、batch/section split、checkpoint hash，并用 held-out section、marker 或图像验证。
- 当前状态是 `manifest-only`，完整阅读卡片在 literature-workbench 的 P022，模型推理仍需官方环境。

## 多模态与空间模拟扩展

- **scMultiSim / P023**：R/Bioconductor 模拟器，使用 cell differential tree、GRN 和可控互作/技术噪声生成 RNA、ATAC、velocity 与空间 truth。
- 入口：`python/20_scmultisim_manifest.py`；先固定参数、seed、负对照和 benchmark split，再将模拟结果与经验数据 sanity check 分开记录。
- 当前状态是 `manifest-only`，完整阅读卡片在 literature-workbench 的 P023。
