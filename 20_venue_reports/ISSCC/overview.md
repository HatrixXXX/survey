# ISSCC 论文图谱分析

## 1. 会议定位

本报告中的 `ISSCC` 指 IEEE International Solid-State Circuits Conference。它在本项目中作为集成电路和芯片实作顶级来源处理：和 ISCA/MICRO/HPCA 这类体系结构会议不同，ISSCC 的证据重点是已经做成、可测量、可发表的芯片电路，而不是 simulator 或系统原型。它适合观察 AI/ML accelerator、processor/GPU/SoC、compute-in-memory、memory interface、imager/sensor、低功耗端侧平台和 power-management 技术如何落到硅实现。对应 claim <a id="ISSCC-001-C001"></a>[ISSCC-001-C001](#ISSCC-001-C001)。

本轮 第二轮 把 ISSCC 的 broad circuit coverage 当作范围边界，而不是缺陷。RF、analog、power、wireline、sensors、memory、processors 等方向会进入索引，但只有和硬件加速、专用加速器、软硬协同、3D/神经渲染、端侧感知和平台硅约束直接相关的行进入深读。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 主体来自 DBLP ISSCC TOC/API、DOI/IEEE Xplore 元数据和既有 venue corpus；第二轮 对部分代表行补充了 ISSCC advance-program URL/session，但没有写成完整 final-program parsing。`awards.csv` 保留 ISSCC official award winners page 与 handout URL；A07 已对齐到 [ISSCC-2017-P0079](../../10_corpus/ISSCC/id_index.md#ISSCC-2017-P0079) 和 DOI `10.1109/ISSCC.2017.7870315`，A13-A23 仍是 handout placeholder，需要 paper-level extraction。2026 按 `normal_2026_partial` 处理，不能判断长期影响。对应 claim <a id="ISSCC-001-C002"></a>[ISSCC-001-C002](#ISSCC-001-C002)、<a id="ISSCC-001-C003"></a>[ISSCC-001-C003](#ISSCC-001-C003)、<a id="ISSCC-001-C010"></a>[ISSCC-001-C010](#ISSCC-001-C010)、<a id="ISSCC-001-C023"></a>[ISSCC-001-C023](#ISSCC-001-C023)。

| 年份 | papers.csv 记录数 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 205 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2017 | 209 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2018 | 207 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2019 | 202 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2020 | 211 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2021 | 212 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2022 | 212 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2023 | 211 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2024 | 245 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2025 | 258 | 完全的 | DBLP ISSCC TOC/API; DOI/IEEE Xplore 可用 |
| 2026 | 269 | partial | DBLP ISSCC TOC/API； DOI/IEEE Xplore（如果有）；截至 2026 年 6 月 27 日，部分长期影响 |

第二轮 全量筛选结果：`papers.csv` 2441 行和 `awards.csv` 23 行全部进入 `ISSCC_screening_matrix.csv`，筛选决定分布为 `{'index_only': 2362, 'deep_read': 83, 'exclude_non_main': 8, 'needs_review': 11}`。`ISSCC_paper_evidence_matrix.csv` 写入 72 条 evidence rows，包含 WHY/HOW/WHAT/IMPACT/EVIDENCE。对应 claim <a id="ISSCC-001-C014"></a>[ISSCC-001-C014](#ISSCC-001-C014)、<a id="ISSCC-001-C016"></a>[ISSCC-001-C016](#ISSCC-001-C016)。

## 3. Venue 内小领域

| 一级领域 | venue 内小领域 | 核心问题 | 代表论文 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|---|
| T01/T02/T05 | CNN/RNN 和低功耗 Edge-AI 加速器硅 | DNN/edge-AI 如何在低功耗芯片中实现数据复用、低电压、精度调节和实测能效 | Eyeriss；Envision； DNPU； UNPU; ANP-I； NVE | 2016-2024 | 连接专用 AI accelerator 和端侧推理 | deep_read 证据，venue_provisional |
| T05/T10 | CIM/PIM 和近内存 MAC | 存储墙如何变成 SRAM/ReRAM/MRAM/DRAM/HBM 阵列、读出、精度和带宽问题 | Conv-RAM； ReRAM nvCIM； 7纳米SRAMCIM； HBM2 FIM； STT-MRAM NMC | 2018-2026 | 连接 memory-centric accelerator | deep_read 证据，venue_split_candidate |
| T01/T02/T05 | Transformer/LLM 令牌处理加速器 | attention、token latency、KV/cache、低比特 LLM 和 speculative decoding 如何落到芯片 | TranCIM；近似Transformer；稀疏 Transformer 处理器；Slim-Llama； T-REX； SoulMate | 2022-2026 | 直接连接 LLM/Transformer 专用加速 | deep_read 证据，cross_venue_candidate |
| T03/T04 | 3D 感知、SLAM、NeRF/3DGS 和传感 | 3D sensing、SLAM、NeRF、3DGS 和 spatial computing 如何变成实时低功耗硅流水线 | CNN-SLAM；神经SLAM；MetaVRain； LSPU；Space-Mate；NeuGPU； 3DGS处理器； IRIS | 2016-2026 | 与 3DGS/神经渲染方向直接相关 | deep_read 证据，cross_venue_candidate |
| T06/T10/T12 | 产品规模 AI/HPC 平台硅 | GPU/CPU/chiplet/AI SoC 如何处理 HBM、die-to-die、package、cache/memory hierarchy 和企业/datacenter workload | A100;Telum；Ponte Vecchio； MI300/MI350；Spyre；Maia；四芯片组 AI SoC | 2017-2026 | 连接 GPU/NPU/ASIC 平台谱系 | deep_read 证据，venue_provisional |

完整小领域说明见 `20_venue_reports/ISSCC/subfields.md`。原始大 cluster 仍保留在 `papers.csv`，但 第二轮 报告不把 “AI/ML”、“CIM”、“HPC”、“sensors” 这类大词当主 topic。

## 4. 接受论文筛选

`ISSCC_screening_matrix.csv` 对每个 paper/award row 给出具体 topic_hint、workload_hint、bottleneck_hint、mechanism_hint、platform_hint、evaluation_hint、artifact_signal 和 user_relevance。7 条 row 被标为 `exclude_non_main`，原因是 front matter 或 proceedings-volume metadata，而不是正式技术论文。对应 claim <a id="ISSCC-001-C015"></a>[ISSCC-001-C015](#ISSCC-001-C015)。

Deep-read 触发条件包括：award paper、首轮代表论文、CIM/PIM/near-memory、CNN/RNN/LLM/Transformer accelerator、产品级 AI/HPC 平台、3D vision/SLAM/NeRF/3DGS、工具/benchmark/artifact 或近期前沿 row。多数非相关 RF/analog/power/wireline 行保留为 `index_only`，用于 venue 覆盖，不写成项目主线。

## 5. Award Papers 分析

ISSCC 官方 award winners 页面和 handout URL 仍是奖项 canonical source 的主要入口。已解析且与 paper row 对齐的 award paper 继续保留为 `verified`；A07 在 第二轮 中补齐到 [ISSCC-2017-P0079](../../10_corpus/ISSCC/id_index.md#ISSCC-2017-P0079)，但保留 title/authors minor variant note。A05 是 forum presenter award，不作为 accepted technical paper deep-read。A13-A23 是 handout availability placeholder，仍为 `needs_review`；2021 handout link rot、2023 redirect/html source 仍未解决。对应 claim [ISSCC-001-C010](#ISSCC-001-C010)、[ISSCC-001-C023](#ISSCC-001-C023)。

## 6. 代表性论文与影响力初审

第二轮 对 deep-read 行记录 citation_signal、adoption_signal、artifact_signal、benchmark_signal 和 query date；citation count 只作为影响力线索，不单独证明 milestone。对应 claim <a id="ISSCC-001-C024"></a>[ISSCC-001-C024](#ISSCC-001-C024)。

| 子领域 | 代表性证据 | 影响审核状态 |
|---|---|---|
| CNN/RNN edge-AI 加速器 | Eyeriss、Envision、DNPU、UNPU | Eyeriss/Eyeriss-v2/JSSC/ISCA 谱系已验证为信号；产品采用未断言 |
| CIM/PIM/NMC | Conv-RAM、ReRAM nvCIM、7nm SRAM CIM、HBM2 FIM、STT-MRAM NMC | 三星 HBM-PIM 有官方行业/后续来源；大多数宏行仅保留引用/后续 |
| Transformer/LLM | TranCIM、近似 Transformer、稀疏 Transformer、Slim-Llama、T-REX、SoulMate | 多年趋势得到验证； 2025-2026年长期影响主要为needs_review/impact_unverified |
| 3D/SLAM/NeRF/3DGS | CNN-SLAM、NeuroSLAM、MetaVRain、LSPU、Space-Mate、NeuGPU、3DGS 处理器、IRIS | 跨年度 ISSCC 证据已验证；artifact/代码重用和cross-venue稳定性仍然开放 |
| 平台芯片 | A100、Telum/Telum II、Ponte Vecchio、MI300/MI350、Spyre、Maia、四芯片 SoC | 官方产品/平台页面验证了多个采用信号；每个源都保留精确的平台映射 |

## 7. 发展脉络

2016-2018 的 early CNN/RNN accelerator silicon 由 Eyeriss、Envision、DNPU、UNPU 支撑。2018-2022 的 CIM/NMC 路线横跨 SRAM、ReRAM、MRAM、analog/digital、inference/training 和 HBM-PIM。2022-2026 的 Transformer/LLM silicon 从 sparse/approximate attention 和 CIM token pipeline 扩展到 Llama、T-REX、SoulMate、speculative decoding 和 visual autoregressive rows。2019-2026 的 3D/SLAM/neural-rendering silicon 从 CNN-SLAM/NeuroSLAM 到 MetaVRain、LSPU、Space-Mate、NeuGPU、3DGS processor、IRIS 和 2026 visual-autoregressive rows。2021-2026 的 product-scale platform row 强调 HBM、chiplet、die-to-die、package、enterprise inference 和 datacenter GPU/AI accelerator。对应 claim <a id="ISSCC-001-C017"></a>[ISSCC-001-C017](#ISSCC-001-C017) 到 <a id="ISSCC-001-C022"></a>[ISSCC-001-C022](#ISSCC-001-C022)。

## 8. 团队线索

本轮没有做 affiliation/entity disambiguation，因此不写机构排名。以下线索只作为后续 entity disambiguation 入口，不代表团队强弱。对应 claim <a id="ISSCC-001-C013"></a>[ISSCC-001-C013](#ISSCC-001-C013)。

| 团队/机构线索 | 关联方向 | 证据状态 | 使用限制 |
|---|---|---|---|
| MIT Eyeriss | DNN accelerator、spatial/dataflow line | conservative team_signal | 只作为后续 entity disambiguation 入口；不代表团队强弱 |
| KAIST edge-AI | edge-AI silicon | conservative team_signal | 只作为后续 entity disambiguation 入口；不写机构排名 |
| KU Leuven / imec | circuit/system silicon lines | conservative team_signal | 只作为后续 entity disambiguation 入口；不代表团队强弱 |
| NTHU / TSMC CIM | CIM | conservative team_signal | 只作为后续 entity disambiguation 入口；不写机构排名 |
| Samsung HBM-PIM | HBM-PIM | conservative team_signal | 只作为后续 entity disambiguation 入口；不代表团队强弱 |
| Tsinghua / UCSB Transformer | Transformer accelerator/silicon | conservative team_signal | 只作为后续 entity disambiguation 入口；不写机构排名 |
| Yoo / Han / Kim / Park / Song / Ryu neural-rendering string cluster | neural rendering | string-cluster signal | 只作为后续 entity disambiguation 入口；不代表团队强弱 |
| IBM / NVIDIA / Intel / AMD / Microsoft / Rebellions company-team signals | company-team silicon/platform signals | company-team signal | 只作为后续 entity disambiguation 入口；不写机构排名 |

## 9. 对博士入门者的阅读路线

先读 SF01 的 Eyeriss/Envision/DNPU/UNPU，理解算法负载如何转成 dataflow、片上存储、精度和能效指标。再读 SF02 的 Conv-RAM、ReRAM/SRAM/MRAM CIM 和 Samsung HBM-PIM，理解 memory wall 在 ISSCC 里如何变成阵列和接口问题。第三条线读 SF03 的 TranCIM、approximate Transformer、Slim-Llama/T-REX/SoulMate，把 LLM/Transformer 的 token bottleneck 接到芯片。第四条线读 SF04 的 CNN-SLAM、MetaVRain、Space-Mate、NeuGPU、3DGS/IRIS，对接 3DGS/神经渲染。最后读 SF05 的 A100/Telum/Ponte/MI300/MI350/Spyre/Maia，补上真实平台硅的 memory、I/O、chiplet 和 package constraints。

## 10. 与我的方向的连接点

对 3DGS/神经渲染，ISSCC 已有直接相邻的硅实现信号，包括 NeRF/SLAM processor、LiDAR-SLAM SoC、NeuGPU、3D Gaussian Splatting processor/SoC 和 visual autoregressive accelerator。可迁移连接点包括 image sensor/SPAD/ToF/LiDAR 前端、3D-stacked memory/near-memory、GPU/AI SoC、chiplet/die-to-die bandwidth、低功耗端侧平台和 power management。对 FPGA/加速器，ISSCC 的价值是提供真实物理边界和 PPA/存储/I/O/供电/测量闭环，而不是替代 HLS/FPGA 方法论文。

## 11. 缺失来源

- 2016-2026 ISSCC official final program PDF 的逐页解析、session name 和 track 回填。
- IEEE Xplore abstract、affiliation、keywords 和 PDF first page 的批量抽取。
- ISSCC award handout 的 paper-level 人工复核表。
- ISSCC 与 JSSC/VLSI/CICC/A-SSCC/Hot Chips 的同一芯片后续扩展论文对照。
- 完整 citation graph、artifact/code reuse 和 benchmark standardization audit。
