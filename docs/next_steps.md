# 下一步使用顺序

## 第一次使用

1. 在 Zotero 中整理一批核心论文。
2. 从 Better BibTeX 导出 metadata 到 literature workbench。
3. 为每篇论文复制 paper-note 模板。
4. 把可核查结论登记到 evidence notebook。

## APAP RNA-seq

1. 将 count matrix 和 sample metadata 放到本地项目，不上传原始敏感数据。
2. 在 `rnaseq-analysis-template/config/project.yml` 登记设计、对比和阈值。
3. 先完成样本 QC，再运行 edgeR QL。
4. 把 DE、ORA、GSEA、PROGENy、GSVA 和 TF 活性结果的解释依据回链到文献。

## 维护

每次分析产生新结论时，同步更新 `project_status.yml`、文献 claims 和方法版本。不要只保存最终图片。

## 蛋白上下文方法

1. 在 literature-workbench 登记 P017 / PINNACLE，并固定官方代码、网络版本和 checkpoint。
2. 在 nature-methods-bioinformatics-catalog 运行 `python/14_pinnacle_manifest.py`。
3. 用 PPI degree、random walk 或 GAT 做 baseline，在 cell-type/tissue 分层的 held-out split 上报告排序指标。
4. 将候选靶点回链到 evidence notebook，并安排独立互作、扰动或药效验证。

## 多模态复杂分支轨迹

1. 在 literature-workbench 登记 P018 / PHLOWER，并固定官方版本和输入模态。
2. 在 nature-methods-bioinformatics-catalog 运行 `python/15_phlower_manifest.py`。
3. 先用 CellRank 或图拉普拉斯 baseline，报告共享 cell ID、root/direction 和 branch stability。
4. 将候选转录因子回链到 evidence notebook，并用时间、扰动或空间数据验证。
## 空间数据基础设施

1. 在 literature-workbench 登记 P019 / SpatialData，并固定平台、reader、元素类型、坐标系、单位和变换链。
2. 在 nature-methods-bioinformatics-catalog 运行 `python/16_spatialdata_manifest.py`，先检查 table/image/labels/shapes/points 的 linkage。
3. 对照平台原生 viewer 检查一小块组织的坐标、分割和配准，再进入 Nicheformer、MISO 或传统邻域分析。
4. 将读写/坐标审计与生物学解释分开记录，不能把互操作成功当作空间机制证据。
## 通用序列/表格工具

1. 在 literature-workbench 登记 P020 / scikit-bio，固定操作、格式、序列/样本 ID、metadata、距离/树约定和统计设计。
2. 在 nature-methods-bioinformatics-catalog 运行 `python/17_scikit_bio_manifest.py`，再安装官方环境执行具体 API。
3. 以 assay-specific baseline 和样本/重复层级结果进行比较，不把单次库调用当作机制证据。
4. 将解析参数、随机种子、软件版本和输入哈希写入 evidence notebook。
