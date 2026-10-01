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

## 多模态复杂分支轨迹\n\n1. 在 literature-workbench 登记 P018 / PHLOWER，并固定官方版本和输入模态。\n2. 在 nature-methods-bioinformatics-catalog 运行 `python/15_phlower_manifest.py`。\n3. 先用 CellRank 或图拉普拉斯 baseline，报告共享 cell ID、root/direction 和 branch stability。\n4. 将候选转录因子回链到 evidence notebook，并用时间、扰动或空间数据验证。\n