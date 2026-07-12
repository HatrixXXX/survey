# MICRO 论文图谱分析

## 1. 会议定位

本报告中的 `MICRO` 指 IEEE/ACM International Symposium on Microarchitecture。项目把它作为微架构、处理器、加速器、memory system、GPU/异构架构、安全和真实系统架构的 P0 来源。这个定位仍沿用首轮 claim <a id="MICRO-001-C001"></a>[MICRO-001-C001](#MICRO-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。2016-2025 的 accepted-paper corpus 来自 MICRO official program 页面，共 890 行；2026 仍是 partial，不生成 accepted-paper 或 award 行。第二轮新增了全量 screening、候选 evidence matrix、SIGMICRO Test-of-Time award rows，并对少量高价值 DOI/作者字段做了可靠回填。

| 年份 | papers.csv 记录数 | awards.csv 记录数 | 状态 |
|---|---:|---:|---|
| 2016 | 61 | 7 | 完全的 |
| 2017 | 63 | 1 | 完全的 |
| 2018 | 75 | 7 | 完全的 |
| 2019 | 79 | 8 | 完全的 |
| 2020 | 82 | 7 | 完全的 |
| 2021 | 94 | 6 | 完全的 |
| 2022 | 89 | 6 | 完全的 |
| 2023 | 101 | 5 | 完全的 |
| 2024 | 123 | 6 | 完全的 |
| 2025 | 123 | 8 | 完全的 |
| 2026 | 0 | 0 | normal_2026_partial |

本轮新增或修正的来源包括 MICRO-49/MICRO-51/MICRO-57/MICRO-58/MICRO-59 official pages、SIGMICRO Test-of-Time page、已有 DOI URL、DBLP/Crossref exact-title metadata。没有可靠来源的 abstract、keywords、PDF、artifact 和 code 字段没有补写。

## 3. 第二轮 Screening

`MICRO_screening_matrix.csv` 覆盖 papers 和 awards 两张表，共 951 行。筛选决定只使用 `deep_read`、`index_only`、`exclude_non_main`、`needs_review`。

| 决策 | count |
|---|---:|
| deep_read | 144 |
| index_only | 659 |
| needs_review | 135 |
| exclude_non_main | 13 |

`deep_read` 主要覆盖 official award/source rows、首轮代表论文、3DGS/neural rendering/point-cloud/SLAM、LLM/KV/MoE、PIM/CXL、FPGA/generator、benchmark/profiling/modeling 和 security/correctness 样本。`needs_review` 主要保留题名/解析不足以确定具体研究问题的行。

## 4. Venue 内小领域图谱

| subfield_id | 子领域 | evidence rows | 活跃年数 | 地位 |
|---|---|---:|---|---|
| [MICRO-SF01](subfields.md#MICRO-SF01) | 3D/神经场景加速 | 22 | 2016-2025 | venue_provisional |
| [MICRO-SF02](subfields.md#MICRO-SF02) | LLM/Transformer 服务内存架构 | 24 | 2016-2025 | venue_provisional |
| [MICRO-SF03](subfields.md#MICRO-SF03) | 稀疏张量和 DNN 加速器建模 | 9 | 2016-2023 | venue_provisional |
| [MICRO-SF04](subfields.md#MICRO-SF04) | PIM/CXL/近内存系统 | 20 | 2016-2025 | venue_provisional |
| [MICRO-SF05](subfields.md#MICRO-SF05) | FPGA/生成器和加速器可用性 | 5 | 2016-2022 | venue_provisional |
| [MICRO-SF06](subfields.md#MICRO-SF06) | 基准/分析/模型有效性 | 9 | 2016-2022 | venue_provisional |
| [MICRO-SF07](subfields.md#MICRO-SF07) | 安全/正确的加速器和推测设计 | 10 | 2017-2025 | venue_provisional |
| [MICRO-SF08](subfields.md#MICRO-SF08) | 核心预测和指令效率 | 1 | 2023-2023 | venue_provisional |
| [MICRO-SF09](subfields.md#MICRO-SF09) | 量子/非常规计算架构 | 1 | 2020-2020 | venue_provisional |

这些小领域不是全局 taxonomy 的稳定结论，只是 MICRO 内部 第二轮 证据。大领域词如 FPGA、GPU、EDA、HPC 只作为平台或来源上下文，不作为主 topic。

## 5. 获奖来源回顾

第二轮复核后，`awards.csv` 包含 annual best-paper/candidate/session rows 和 SIGMICRO Test-of-Time rows。主要变化：

- 2016：Graphicionado 改为 official Best Paper Award winner；补入 Spectral Profiling 作为 Best Paper Award winner，并补入 4 个 Best Paper Candidates session rows。
- 2018：补入 `End-to-End Automated Exploit Generation...`；2018 仍只找到 Best Paper Session，winner 未找到 canonical source，相关行保持 `needs_review`。
- 2019-2025：official program/home pages 支撑大多数 winner/runner-up/candidate rows。
- 2025 Delegato：作者字段用 MICRO-58 official program 修正。
- Test-of-Time：补入 SIGMICRO official ToT page 上 2016-2025 winner rows。ToT 原始论文多为 1994-2007，不强行对齐到本轮 2016-2025 accepted-paper ids。

## 6. 代表论文与证据矩阵

`MICRO_paper_evidence_matrix.csv` 当前有 101 条 evidence rows。每条都包含 WHY、HOW、WHAT、IMPACT 和 EVIDENCE。影响力字段只做初审：official award/ToT 是可验证 venue signal；citation、artifact reuse、benchmark standardization 和产业/工具链采纳没有证据时写 `impact_unverified` 或保留未验证说明。

重点阅读路线：

- 3D/神经场景加速：Tigris、Fusion-3D、GauSPU、GCC、RTGS、REACT3D、PointISA。
- LLM/Transformer 服务内存架构：DFX、FlashLLM、Stratum、Kelle、LongSight、DECA、StreamTensor、LLM.265。
- 稀疏张量和 DNN 加速器建模：Cambricon-X、Simba、ExTensor、Sparse Tensor Core、Sparseloop、TeAAL。
- PIM/CXL/近内存系统：Ambit、BEER、TRiM、Demystifying CXL Memory、PyPIM、ComPASS、Beyond Page Migration、Delegato。
- FPGA/生成器和加速器可用性：从高级深度神经模型到FPGAs、gem5-Aladdin、TAPAS、OverGen、DFX。
- 基准测试/分析/模型有效性：NVBit、APOLLO、TIP、Sparseloop、TeAAL、A Mess of Memory System Benchmarking。
- 安全/正确加速器和推测设计：STT、CEASER、Graphene、SecureLoop、CryptoMMU、ZKP联合设计。

## 7. 发展脉络

2016-2018 的 MICRO 已经出现 sparse neural-network accelerator、graph accelerator、FPGA/generator、PIM 和 security/correctness 信号。2019-2021 的主线变成 sparse tensor、多芯片 DNN inference、RowHammer/DRAM reliability、runtime power/profiling 和 recommendation co-design。2022-2025 明显加入 LLM/Transformer serving、CXL/PIM compatibility、3DGS/neural-scene acceleration 和 benchmark validity。

趋势判断只基于多篇或跨年份 evidence rows：

- AI acceleration 从 CNN/sparse-NN datapath 走向 LLM serving-state 和 memory-system co-design。证据：Cambricon-X、Simba、DFX、FlashLLM、Stratum、Kelle、LongSight、DECA、StreamTensor、LLM.265。
- Memory-centric thread 持续存在，但问题从“内存里能不能算”转向接口、协议、CXL、Python-facing PIM、page migration 和 chiplet-locality。证据：Ambit、BEER、TRiM、Demystifying CXL Memory、PyPIM、ComPASS、Beyond Page Migration、Delegato。
- 3DGS/neural rendering 是近年前沿，不是成熟长线学派。证据：Tigris、Fusion-3D、GauSPU、GCC、RTGS、REACT3D、PointISA。
- Evaluation/tooling 成为独立方法线索。证据：NVBit、APOLLO、TIP、Sparseloop、TeAAL、A Mess of Memory System Benchmarking。

## 8. 团队线索

本报告只保留团队线索，不做排名。所有这些都需要后续 author/affiliation entity disambiguation。

| 团队/机构线索 | 关联方向 | 证据状态 | 使用限制 |
|---|---|---|---|
| MIT / NVIDIA sparse/modeling line | sparse、modeling | MICRO corpus team_signal | 需要后续 author/affiliation entity disambiguation；不做排名 |
| ETH / Mutlu memory line | memory | MICRO corpus team_signal | 需要后续 author/affiliation entity disambiguation；只作为阅读入口 |
| UIUC / Torrellas security/memory line | security、memory | MICRO corpus team_signal | 需要后续 author/affiliation entity disambiguation；不写成团队强弱判断 |
| BSC / UPC methodology/data-movement line | methodology、data movement | MICRO corpus team_signal | 需要后续 author/affiliation entity disambiguation；不做排名 |
| Georgia Tech / Yingyan Lin 3D reconstruction/rendering line | 3D reconstruction、rendering | MICRO corpus team_signal | 需要后续 author/affiliation entity disambiguation；只作为方向入口 |
| ICT-CAS / Cambricon sparse/precision/LLM line | sparse、precision、LLM | MICRO corpus team_signal | 需要后续 author/affiliation entity disambiguation；不做排名 |
| Tsinghua / Beihang 3DGS/point-cloud line | 3DGS、point-cloud | MICRO corpus team_signal | 需要后续 author/affiliation entity disambiguation；只作为阅读入口 |
| FPGA/generator 相关作者群 | FPGA、generator | MICRO corpus author-cluster signal | 需要后续 author/affiliation entity disambiguation；不写成团队强弱判断 |

## 9. 对博士入门者的阅读路线

先读：Cambricon-X、Ambit、Simba、STT、BEER、APOLLO、DFX、Sparseloop、Fusion-3D、GCC。

再扩展：Graphicionado、gem5-Aladdin、TAPAS、NVBit、Tigris、TRiM、RecPipe、Archytas、OverGen、SecureLoop、TeAAL、GauSPU、A Mess of Memory System Benchmarking、Stratum、Kelle、LLM.265、RTGS、REACT3D、PointISA。

## 10. 与用户方向的连接点

MICRO 对 3DGS/神经渲染/FPGA 加速方向有直接连接。2024-2025 的 Fusion-3D、GauSPU、GCC、RTGS、REACT3D、PointISA 说明 3D/显式 primitive/SLAM 已经进入体系结构会议的问题空间；不过这些都是近年信号，长期影响还没在本轮证实。更稳的使用方式是把这些工作拆成数据结构、tile/binning/sorting、visibility、访存、同步、训练/推理闭环和边缘实时性，再与 MICRO 的 sparse tensor、LLM state management、PIM/CXL、FPGA/generator 和 benchmark/modeling 证据对齐。

## 11. 缺失来源

- ACM DL / IEEE Xplore 的 abstract、keyword、PDF 批量导出。
- Tool、benchmark、artifact 和 code repository 的可运行性来源。
- MICRO 2026 accepted papers、session 和 award 完整官方列表；这在 2026-06-27 属于 `normal_2026_partial`。
- 2018/2023 best-paper winner 的 canonical source，如果官方后续页面或 business meeting slides 可得。
- 跨 ISCA/HPCA/ASPLOS/DAC/ICCAD/FPGA/FCCM/FPL/FPT/MLSys 的同主题对照矩阵。
