# PPoPP 论文图谱分析

## 1. 会议定位

PPoPP 是并行编程社区的主会之一，关注语言、编译器、runtime、工具、同步、GPU/异构系统、并行算法和应用系统。它不是硬件结构会议，但经常处理硬件暴露给软件栈的问题：访存、同步、调度、Tensor Core/矩阵单元、GPU/异构平台、分布式通信。这个定位见 claim <a id="PPOPP-001-C001"></a>[PPOPP-001-C001](#PPOPP-001-C001)。

对硬件加速和软硬协同研究来说，PPoPP 的价值主要是 workload decomposition 和系统软件接口。它把新负载拆成并行模式、访存模式、同步模式和 runtime/compiler 接口；这些线索可以和 ASPLOS/MICRO/ISCA/HPCA 的硬件机制、SC/MLSys 的大规模系统证据对照。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 含 355 条主会 accepted-paper 记录，年度计数为：2016: 29, 2017: 29, 2018: 28, 2019: 29, 2020: 28, 2021: 31, 2022: 29, 2023: 31, 2024: 32, 2025: 38, 2026: 51。`awards.csv` 含 30 条 award / nominee / candidate 记录，年度计数为：2016: 2, 2017: 1, 2018: 1, 2019: 5, 2020: 1, 2021: 2, 2022: 4, 2023: 2, 2024: 1, 2025: 4, 2026: 7。第二波后，paper rows 和 award rows 均为 `verified`，论文 DOI 缺口为 0。计数和过滤口径见 <a id="PPOPP-001-C002"></a>[PPOPP-001-C002](#PPOPP-001-C002) 到 <a id="PPOPP-001-C004"></a>[PPOPP-001-C004](#PPOPP-001-C004)，第二轮 矩阵见 <a id="PPOPP-001-C022"></a>[PPOPP-001-C022](#PPOPP-001-C022) 和 <a id="PPOPP-001-C023"></a>[PPOPP-001-C023](#PPOPP-001-C023)。

主要来源是 SIGPLAN/Researchr 官方 program/home 页面、SIGPLAN OpenTOC、DBLP 年度索引、Crossref/OpenAlex、DOI/ACM 页面和作者 PDF。第二波新增修正包括：2019 Best Paper winner 从 ACM 2019 awards archive 证据和 W&M 二级来源合并确认；2020 Best Paper 从 PPoPP 2020 官方首页补齐；2021、2022、2023 award rows 按官方首页/ACM archive 纠正；2018 vSensor/VerifiedFT 和 2020/2023/2025 residual DOI rows 已按 Crossref/ACM/DBLP/作者 PDF 回填。见 <a id="PPOPP-001-C017"></a>[PPOPP-001-C017](#PPOPP-001-C017) 到 <a id="PPOPP-001-C027"></a>[PPOPP-001-C027](#PPOPP-001-C027)。

## 3. 第二轮小领域图谱

| subfield_id | 子领域 | evidence rows | 代表性证据 |
| --- | --- | ---: | --- |
| [PPOPP-SF01](subfields.md#PPOPP-SF01) | 同步回收和持久数据结构 | 11 | [PPoPP-2016-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2016-P0023)|[PPoPP-2018-P0001](../../10_corpus/PPoPP/id_index.md#PPoPP-2018-P0001)|[PPoPP-2020-P0020](../../10_corpus/PPoPP/id_index.md#PPoPP-2020-P0020)|[PPoPP-2021-P0013](../../10_corpus/PPoPP/id_index.md#PPoPP-2021-P0013)|[PPoPP-2022-P0018](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0018)|[PPoPP-2022-P0019](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0019)|[PPoPP-2022-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0023)|[PPoPP-2022-P0029](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0029)|[PPoPP-2023-P0018](../../10_corpus/PPoPP/id_index.md#PPoPP-2023-P0018) |
| [PPOPP-SF02](subfields.md#PPOPP-SF02) | 任务编译器运行时和编程模型 | 5 | [PPoPP-2017-P0018](../../10_corpus/PPoPP/id_index.md#PPoPP-2017-P0018)|[PPoPP-2019-P0017](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0017)|[PPoPP-2022-P0016](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0016)|[PPoPP-2023-P0015](../../10_corpus/PPoPP/id_index.md#PPoPP-2023-P0015)|[PPoPP-2026-P0005](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0005) |
| [PPOPP-SF03](subfields.md#PPOPP-SF03) | 不规则图搜索和硬件单元映射 | 7 | [PPoPP-2016-P0011](../../10_corpus/PPoPP/id_index.md#PPoPP-2016-P0011)|[PPoPP-2017-P0017](../../10_corpus/PPoPP/id_index.md#PPoPP-2017-P0017)|[PPoPP-2019-P0016](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0016)|[PPoPP-2022-P0006](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0006)|[PPoPP-2023-P0005](../../10_corpus/PPoPP/id_index.md#PPoPP-2023-P0005)|[PPoPP-2025-P0004](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0004)|[PPoPP-2026-P0009](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0009) |
| [PPOPP-SF04](subfields.md#PPOPP-SF04) | 张量核稀疏模板和科学内核 | 9 | [PPoPP-2019-P0018](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0018)|[PPoPP-2019-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0023)|[PPoPP-2021-P0020](../../10_corpus/PPoPP/id_index.md#PPoPP-2021-P0020)|[PPoPP-2022-P0008](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0008)|[PPoPP-2024-P0025](../../10_corpus/PPoPP/id_index.md#PPoPP-2024-P0025)|[PPoPP-2025-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0023)|[PPoPP-2025-P0025](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0025)|[PPoPP-2026-P0024](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0024)|[PPoPP-2026-P0028](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0028) |
| [PPOPP-SF05](subfields.md#PPOPP-SF05) | 分布式培训通信和诊断 | 5 | [PPoPP-2021-P0005](../../10_corpus/PPoPP/id_index.md#PPoPP-2021-P0005)|[PPoPP-2022-P0010](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0010)|[PPoPP-2022-P0011](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0011)|[PPoPP-2026-P0029](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0029)|[PPoPP-2026-P0032](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0032) |
| [PPOPP-SF06](subfields.md#PPOPP-SF06) | LLM 推理状态和注意力内核 | 6 | [PPoPP-2021-P0028](../../10_corpus/PPoPP/id_index.md#PPoPP-2021-P0028)|[PPoPP-2025-P0017](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0017)|[PPoPP-2026-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0023)|[PPoPP-2026-P0038](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0038)|[PPoPP-2026-P0045](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0045)|[PPoPP-2026-P0047](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0047) |
| [PPOPP-SF07](subfields.md#PPOPP-SF07) | 分析调试能量和证据工具 | 6 | [PPoPP-2018-P0012](../../10_corpus/PPoPP/id_index.md#PPoPP-2018-P0012)|[PPoPP-2019-P0015](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0015)|[PPoPP-2022-P0017](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0017)|[PPoPP-2025-P0005](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0005)|[PPoPP-2026-P0013](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0013)|[PPoPP-2026-P0037](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0037) |
| [PPOPP-SF99](subfields.md#PPOPP-SF99) | 领域模拟 artifact 的边界奖励证据 | 1 | [PPoPP-2023-P0014](../../10_corpus/PPoPP/id_index.md#PPoPP-2023-P0014) |

完整筛选矩阵写入 `PPoPP_screening_matrix.csv`，覆盖 385 行，其中 `deep_read` 80 行、`index_only` 305 行、`needs_review` 0 行。80 条 `deep_read` 包括 50 篇 paper rows 和 30 条 award rows；award rows 已折叠进 50 条 paper evidence。证据矩阵写入 `PPoPP_paper_evidence_matrix.csv`。

## 4. Accepted Papers 聚类结果

第二波之后，聚类仍是 venue-local subfield seed，不是最终 taxonomy。主 topic 不写成 “GPU/EDA/ML systems/HPC” 这类大领域词，而拆成更具体的问题：同步/回收/持久化数据结构，task compiler/runtime，irregular graph/search/tree mapping，matrix/Tensor-unit sparse/scientific kernel reformulation，distributed training communication，LLM inference/attention/KV，profiling/debugging/energy/data evidence tools。

[PPOPP-SF99](subfields.md#PPOPP-SF99) 只保留 BioDynaMo 这一条 Best Artifact 边界证据。它说明 PPoPP 会出现 domain simulation artifact，但单篇 artifact 不足以形成 venue 内趋势。

## 5. 奖项复核

第二波 award-source 复核后，`awards.csv` 30 条均为 verified。

- 2019 Best Paper Award：`Lightweight hardware transactional memory profiling` 从 ACM 2019 awards archive 证据和 W&M 二级来源合并确认；父 agent 直接抓 ACM 页面时遇到 403/Cloudflare，所以 confidence 保持 medium，见 <a id="PPOPP-001-C024"></a>[PPOPP-001-C024](#PPOPP-001-C024)。
- 2020 Best Paper Award：PPoPP 2020 官方首页确认 winner 是 `Non-Blocking Interpolation Search Trees with Doubly-Logarithmic Running Time`，见 [PPOPP-001-C017](#PPOPP-001-C017)。
- 2021 Best Paper / Best Artifact：官方首页确认 Best Paper 是 `Synthesizing Optimal Collective Algorithms`；NBR Best Artifact 使用 ACM 2021 archive 作为 canonical source，见 <a id="PPOPP-001-C018"></a>[PPOPP-001-C018](#PPOPP-001-C018) 和 <a id="PPOPP-001-C026"></a>[PPOPP-001-C026](#PPOPP-001-C026)。
- 2022 Best Papers/Artifact：官方首页列出三篇 Best Papers 和 PathCAS artifact，见 <a id="PPOPP-001-C019"></a>[PPOPP-001-C019](#PPOPP-001-C019)。
- 2023 Best Paper/Artifact：官方首页确认 Best Paper 是 parallel biconnectivity，Best Artifact 是 BioDynaMo，见 <a id="PPOPP-001-C020"></a>[PPOPP-001-C020](#PPOPP-001-C020)。

## 6. 研究脉络和用户相关性

PPoPP 对硬件加速研究的价值主要在以下几条线：

- Matrix/Tensor-unit reformulation：Adaptive Sparse Tiling、EGEMM-TC、QGTC、ConvStencil、FlashSparse、BerryBees、HierCut、Trojan Horse 说明 PPoPP 持续讨论如何把 sparse/stencil/graph/scientific kernels 重排为矩阵/张量硬件更容易执行的形式。
- LLM / Transformer runtime：TurboTransformers 到 MARLIN、JanusQuant、Laser、FlashAttention-T、MetaAttention，说明近年 PPoPP 开始覆盖 serving、KV cache、attention tensorization 和多后端 framework。这是前沿线索，不是长期影响结论。
- Distributed training communication：Synthesizing Optimal Collective Algorithms、Near-Optimal Sparse Allreduce、BAGUALU、COCCL、CCL-D 提供 collective synthesis、sparse allreduce、压缩通信和训练异常诊断的证据线。
- Irregular graph / spatial search：Gunrock/Groute 到 RTNN/RT-BarnesHut、parallel biconnectivity、UFO Trees，是图、空间查询和动态树负载映射到 GPU/ray-tracing hardware 的软件侧证据。
- Task compiler/runtime：Tapir、OpenCilk 和 2026 oversubscription scheduling 体现并行结构如何暴露给 compiler/runtime。
- Profiling / evidence tools：Featherlight、TxSampler、PerFlow、EVeREST、PRISM、BEEMS 说明 PPoPP 持续出现测量、诊断、运行时控制和数据压缩工具。

## 7. 团队线索

本轮只记录 team_signal，不做排名。这些只是论文作者字符串线索，未完成 affiliation/entity disambiguation。

| 作者/团队线索 | 关联方向 | 证据状态 | 使用限制 |
|---|---|---|---|
| Trevor Brown / Dan Alistarh / Guy Blelloch / Naama Ben-David 等 | 并发、持久化对象 | 论文作者字符串线索 | 未完成 affiliation/entity disambiguation；不做排名 |
| Torsten Hoefler 相关论文 | sparse allreduce、LLM inference | 论文作者字符串线索 | 未完成 affiliation/entity disambiguation；只作为阅读入口 |
| Guangming Tan / Dingwen Tao 等 | GPU compression、diagnostics、collective | 论文作者字符串线索 | 未完成 affiliation/entity disambiguation；不写成团队强弱判断 |
| Yufei Ding / Yuke Wang / Boyuan Feng 相关论文 | Tensor Core、GNN、extended precision | 论文作者字符串线索 | 未完成 affiliation/entity disambiguation；不做排名 |

## 8. 影响审计

本轮 evidence matrix 合并了 OpenAlex citation signal，所有 citation 字段都写明 `query_date=2026-06-27`。这些引用数只作为影响力线索，不能单独证明里程碑地位。artifact/code reuse、benchmark standardization、industry/toolchain adoption 没有完成专门审计；没有证据的字段保持 `impact_unverified` 或 `*_unverified`。官方 award/artifact labels 只作为 award/artifact signal，不等同于长期影响力。

## 9. 缺失来源

- `papers.csv` 仍没有 abstract/keywords 字段；本轮 evidence 是 abstract/official-page/citation-index 级，不承诺每篇 PDF 级精读。
- ACM PDF/article 页面在本环境多次返回 403/Cloudflare；能用作者 PDF 的行已写入 `pdf_url`，但没有系统做 full-PDF extraction。
- artifact/code URL、artifact reuse、benchmark standardization、citation structure 和 industry/toolchain adoption 仍需要后续专门审计。
- team_signal 未做 affiliation/entity disambiguation，不做团队排名。
- 2025-2026 论文只作为 frontier evidence，不能写成已成经典。
