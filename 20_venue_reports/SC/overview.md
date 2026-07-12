# SC 论文图谱分析

## 1. 会议定位

`SC` 在本项目中按 Systems P0 会议处理。正文不把 HPC、GPU 或 AI systems 当主 topic，而按具体瓶颈写：memory/offload、LLM serving、low-precision kernels、graph/GNN、collectives、storage/I/O、runtime、compiler/AD、profiling/reproducibility、resilience、FPGA/PIM/near-data 和 3D/visual scientific imaging。

## 2. Corpus and 第二轮 Outputs

- `papers.csv`：`1014` 行。 `awards.csv`：`22` 行。
- `SC_screening_matrix.csv`：`1036` 行，决策：`deep_read` 106、`exclude_non_main` 8、`index_only` 876、`needs_review` 46。
- `SC_paper_evidence_matrix.csv`：`85` 行，影响状态：`impact_unverified` 33、`partial` 52。
- 有针对性的修复：2018 DOI 回填、ORBIT-2/RAPTOR/X-MoE 的 SC25 会话 URL、SC19 奖项论文对齐、SC21 官方奖项来源、SC26 normal partial标记。

| 年 | paper rows | accepted_paper 行数 | 地位 |
|---|---:|---:|---|
| 2016 | 88 | 87 | 完全的 |
| 2017 | 65 | 65 | 完全的 |
| 2018 | 75 | 74 | 完全的 |
| 2019 | 90 | 90 | 完全的 |
| 2020 | 102 | 102 | 完全的 |
| 2021 | 115 | 115 | 完全的 |
| 2022 | 88 | 88 | 完全的 |
| 2023 | 100 | 100 | 完全的 |
| 2024 | 109 | 109 | 完全的 |
| 2025 | 181 | 128 | 混合的；为审计而保留的非主要行 |
| 2026 | 1 | 0 | partial |

## 3. 奖项来源审计

SC21 奖励行现在使用官方 SC21 奖励页面。 [SC-2019-A07](../../10_corpus/SC/id_index.md#SC-2019-A07) 与 [SC-2019-P0066](../../10_corpus/SC/id_index.md#SC-2019-P0066) 和 DOI `10.1145/3295500.3356181` 对齐。 SC17 仍为 `needs_review`； SC26 仍然是 `normal_2026_partial`。

## 4. 小领域

| 子领域 | evidence rows | 地位 |
|---|---:|---|
| [SC-SF01](subfields.md#SC-SF01) AI 训练内存/卸载扩展 | 8 | venue_provisional / 矩阵 |
| [SC-SF02](subfields.md#SC-SF02) LLM 和Transformer服务系统 | 3 | venue_provisional / 矩阵 |
| [SC-SF03](subfields.md#SC-SF03) 低精度和融合的 GPU 内核 | 6 | venue_provisional / 矩阵 |
| [SC-SF04](subfields.md#SC-SF04) 稀疏图、张量和 GNN 系统 | 15 | venue_provisional / 矩阵 |
| [SC-SF05](subfields.md#SC-SF05) 通信、集合和互连协同设计 | 14 | venue_provisional / 矩阵 |
| [SC-SF06](subfields.md#SC-SF06) 存储、I/O 和数据移动 | 13 | venue_provisional / 矩阵 |
| [SC-SF07](subfields.md#SC-SF07) 运行时调度和资源管理 | 3 | venue_provisional / 矩阵 |
| [SC-SF08](subfields.md#SC-SF08) 编译器、AD、DSL 和自动调优 | 4 | venue_provisional / 矩阵 |
| [SC-SF09](subfields.md#SC-SF09) 分析、再现性和基准测试 | 7 | venue_provisional / 矩阵 |
| [SC-SF10](subfields.md#SC-SF10) 弹性、功率、热量和数值正确性 | 4 | venue_provisional / 矩阵 |
| [SC-SF11](subfields.md#SC-SF11) FPGA、PIM 和近数据加速 | 5 | venue_provisional / 矩阵 |
| [SC-SF12](subfields.md#SC-SF12) 3D 重建和视觉科学成像 | 3 | venue_provisional / 矩阵 |

## 5. 代表性发现

- AI 训练内存/卸载中的evidence rows：[SC-2017-P0012](../../10_corpus/SC/id_index.md#SC-2017-P0012)、[SC-2021-P0115](../../10_corpus/SC/id_index.md#SC-2021-P0115)、[SC-2024-P0040](../../10_corpus/SC/id_index.md#SC-2024-P0040)、[SC-2025-P0087](../../10_corpus/SC/id_index.md#SC-2025-P0087) 和 [SC-2025-P0179](../../10_corpus/SC/id_index.md#SC-2025-P0179) 支持从科学 DL 到内存墙 LLM/MoE 训练的跨年线。
- LLM 服务：[SC-2024-P0061](../../10_corpus/SC/id_index.md#SC-2024-P0061)、[SC-2024-P0082](../../10_corpus/SC/id_index.md#SC-2024-P0082)、[SC-2024-P0083](../../10_corpus/SC/id_index.md#SC-2024-P0083)、[SC-2025-P0045](../../10_corpus/SC/id_index.md#SC-2025-P0045)、[SC-2025-P0057](../../10_corpus/SC/id_index.md#SC-2025-P0057)、[SC-2025-P0063](../../10_corpus/SC/id_index.md#SC-2025-P0063) 和 [SC-2025-P0167](../../10_corpus/SC/id_index.md#SC-2025-P0167) 将服务分为分析、GPU 共享、推测解码、异构集群、专家缓存和管道调度。
- Graph/GNN：[SC-2018-P0043](../../10_corpus/SC/id_index.md#SC-2018-P0043)、[SC-2022-P0088](../../10_corpus/SC/id_index.md#SC-2022-P0088)、[SC-2024-P0093](../../10_corpus/SC/id_index.md#SC-2024-P0093)、[SC-2025-P0089](../../10_corpus/SC/id_index.md#SC-2025-P0089)、[SC-2025-P0100](../../10_corpus/SC/id_index.md#SC-2025-P0100) 和 [SC-2025-P0102](../../10_corpus/SC/id_index.md#SC-2025-P0102) 将稀疏/图布局连接到多 GPU 和十亿边训练。
- FPGA/PIM/near-data：[SC-2020-P0040](../../10_corpus/SC/id_index.md#SC-2020-P0040)、[SC-2023-P0042](../../10_corpus/SC/id_index.md#SC-2023-P0042)、[SC-2025-P0048](../../10_corpus/SC/id_index.md#SC-2025-P0048)、[SC-2025-P0162](../../10_corpus/SC/id_index.md#SC-2025-P0162) 和 [SC-2025-P0174](../../10_corpus/SC/id_index.md#SC-2025-P0174) 是直接加速器/近内存挂钩。采用和基准标准化尚未得到验证。
- 3D/视觉成像：[SC-2020-P0067](../../10_corpus/SC/id_index.md#SC-2020-P0067) 是直接 3D 重建； [SC-2025-P0097](../../10_corpus/SC/id_index.md#SC-2025-P0097) 是邻近视觉/气候基础建模。这并不能证明 3DGS 是一个既定的 SC 主题。

## 6. 团队线索

团队线索仅是活动线索，不是排名。entity disambiguation 仍然开放。

| 团队/机构线索 | 关联方向 | 代表行 | 使用限制 |
|---|---|---|---|
| Microsoft DeepSpeed 行 | LLM/HPC software stack | [SC-2021-P0115](../../10_corpus/SC/id_index.md#SC-2021-P0115)、[SC-2022-P0021](../../10_corpus/SC/id_index.md#SC-2022-P0021) | 仅是活动线索；不做排名 |
| ETH / SPCL 通信行 | communication、collectives、HPC communication | [SC-2019-P0066](../../10_corpus/SC/id_index.md#SC-2019-P0066)、[SC-2022-P0034](../../10_corpus/SC/id_index.md#SC-2022-P0034)、[SC-2023-P0053](../../10_corpus/SC/id_index.md#SC-2023-P0053)、[SC-2024-P0060](../../10_corpus/SC/id_index.md#SC-2024-P0060) | entity disambiguation 仍开放；不写成团队强弱判断 |
| Wayne State / Cheng 图和 GEMM 行 | graph、GEMM | corpus activity signal | 仅是活动线索；不做排名 |
| ORNL / RIKEN / ANL Climate-AI/profiling 行 | Climate-AI、profiling | corpus activity signal | entity disambiguation 仍开放；只作为阅读入口 |
| FPGA/PIM 加速器行 | FPGA、PIM acceleration | corpus activity signal | 仅是活动线索；不写成排名 |
