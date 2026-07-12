# VLSI 论文图谱分析

## 1. 会议定位

本报告中的 `VLSI` 指 IEEE/JSAP Symposium on VLSI Technology and Circuits。它在本项目中作为集成电路、器件、工艺、电路和系统实作的关键来源处理。和体系结构会议相比，VLSI 更强调已测量芯片、电路、器件、封装和 process/design co-optimization；和 ISSCC/JSSC 相比，它同时保留 Technology 与 Circuits 两条线，因此适合观察新器件、memory、CIM、chiplet、power delivery 和 accelerator SoC 如何在同一会议内互相靠近。对应 claim <a id="VLSI-001-C001"></a>[VLSI-001-C001](#VLSI-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。2016-2025 的 `papers.csv` 主体来自 Crossref/DOI proceedings metadata；2026 年使用官方 Technical Program PDF 和少量 MapYourShow official pages，并继续标为 `partial` / `needs_review`。奖项数据第二轮复核了 VLSI 官方 Best Student、Best Demo 和 Test of Time 页面，修正了 2016 wrong-year rows，并补入官方页面能支撑的缺失 demo / Test-of-Time rows。对应 claim <a id="VLSI-001-C002"></a>[VLSI-001-C002](#VLSI-001-C002)、<a id="VLSI-001-C003"></a>[VLSI-001-C003](#VLSI-001-C003)、<a id="VLSI-001-SW003"></a>[VLSI-001-SW003](#VLSI-001-SW003)、<a id="VLSI-001-SW004"></a>[VLSI-001-SW004](#VLSI-001-SW004)。

| 年份 | papers.csv 记录数 | 状态 | 主要来源 |
| --- | ---: | --- | --- |
| 2016 | 204 | 完全的 | Crossref DOI/会议记录元数据 |
| 2017 | 237 | 完全的 | Crossref DOI/会议记录元数据 |
| 2018 | 203 | 完全的 | Crossref DOI/会议记录元数据 |
| 2019 | 242 | 完全的 | Crossref DOI/会议记录元数据 |
| 2020 | 231 | 完全的 | Crossref DOI/会议记录元数据 |
| 2021 | 134 | 完全的 | Crossref DOI/会议记录元数据 |
| 2022 | 198 | 完全的 | Crossref DOI/会议记录元数据 |
| 2023 | 196 | 完全的 | Crossref DOI/会议记录元数据 |
| 2024 | 200 | 完全的 | Crossref DOI/会议记录元数据 |
| 2025 | 199 | 完全的 | Crossref DOI/会议记录元数据 |
| 2026 | 247 | partial | 官方 VLSI 2026 技术计划 PDF |

`awards.csv` 现有 50 行，类别计数为 `{'best_student_paper': 20, 'artifact_award': 7, 'best_demo_paper': 8, 'test_of_time': 15}`。其中没有唯一 paper_id 或属于历史 Test-of-Time 的行不会被写成 2016-2026 accepted-paper 事实。

## 3. 第二轮 Screening

第二轮 full screening 覆盖 2341 行：`papers.csv` 2291 行，`awards.csv` 50 行。筛选决定计数为 `{'index_only': 2133, 'exclude_non_main': 55, 'deep_read': 143, 'needs_review': 10}`。筛选矩阵路径是 `VLSI_screening_matrix.csv`，所有 `topic_hint` 都描述具体问题或瓶颈，不把 IC、AI、FPGA、EDA、HPC 这类大标签作为主 topic。对应 claim <a id="VLSI-001-SW001"></a>[VLSI-001-SW001](#VLSI-001-SW001)。

| subfield_id | 子领域 | evidence rows | 活跃年数 | 地位 |
|---|---|---:|---|---|
| [VLSI-SF01](subfields.md#VLSI-SF01) | 神经渲染和 3D 高斯映射芯片 | 4 | 2023-2026 | cross_venue_candidate |
| [VLSI-SF02](subfields.md#VLSI-SF02) | 机器人技术和嵌入式边缘 SoC | 10 | 2018-2026 | cross_venue_candidate |
| [VLSI-SF03](subfields.md#VLSI-SF03) | Transformer 和 LLM 令牌级加速器 | 17 | 2022-2026 | venue_provisional |
| [VLSI-SF04](subfields.md#VLSI-SF04) | CIM/PIM 和内存墙加速器 | 23 | 2016-2026 | venue_split_candidate |
| [VLSI-SF05](subfields.md#VLSI-SF05) | 边缘视觉和传感器内感知 | 15 | 2017-2026 | venue_provisional |
| [VLSI-SF06](subfields.md#VLSI-SF06) | 小芯片、3D 集成和加速器扩展 | 13 | 2016-2026 | venue_provisional |
| [VLSI-SF07](subfields.md#VLSI-SF07) | 低精度和稀疏神经 SoC | 15 | 2016-2024 | venue_provisional |
| [VLSI-SF08](subfields.md#VLSI-SF08) | 实现桥、编译器和可基准测试芯片 | 4 | 2018-2026 | venue_provisional |

## 4. Accepted Papers 聚类与小领域

原始 `topic_cluster_label` 仍作为 venue-level bucket，不作为最终 topic。当前 cluster 计数如下：

| 簇 | rows |
|---|---:|
| 生物电子学、安全、量子和其他电路 | 504 |
| 器件技术、CMOS 缩放、存储器和工艺集成 | 492 |
| 模拟、RF、有线、无线和数据转换器电路 | 458 |
| AI/ML 加速器、处理器和计算 SoC | 241 |
| 边缘视觉、机器人、成像仪和嵌入式传感 | 178 |
| 小芯片、3D 集成、高级封装和互连 | 166 |
| 内存计算、近内存和非易失性 AI 内存 | 131 |
| 处理器、供电、SoC 基础设施和 DTCO | 121 |

第二轮 deep dive 把这些粗桶拆成八个 venue-local 小领域：neural rendering/3D Gaussian mapping、robotics/embodied edge SoCs、Transformer/LLM token accelerators、CIM/PIM、edge vision/in-sensor perception、chiplet/3D integration、low-precision/sparse neural SoCs、compiler/benchmark/DTCO bridge。详细 WHY/HOW/WHAT/IMPACT/EVIDENCE 见 `VLSI_paper_evidence_matrix.csv`，subfield 解释见 `subfields.md`。对应 claim <a id="VLSI-001-SW002"></a>[VLSI-001-SW002](#VLSI-001-SW002)、<a id="VLSI-001-SW007"></a>[VLSI-001-SW007](#VLSI-001-SW007)、<a id="VLSI-001-SW008"></a>[VLSI-001-SW008](#VLSI-001-SW008)。

## 5. Award Papers 与官方来源

Best Student Paper 页面、Best Demo archive 页面和 Test of Time 页面是本轮奖项 canonical source。第二轮处理要点：

- 2016 A01/A02 原先是 wrong-year rows，已替换为官方 2016 Best Student Paper winners；Circuits 行保留 `title_variant_needs_review`，等 final program/PDF 复核。对应 claim [VLSI-001-SW004](#VLSI-001-SW004)。
- 2017、2019、2021、2022、2024、2025 的若干 Best Demo rows 已补入；2019 gas-molecule demo 因本地有两个同题 paper_id 候选，保留 `needs_review`。对应 claim <a id="VLSI-001-SW005"></a>[VLSI-001-SW005](#VLSI-001-SW005)。
- Test of Time rows 是奖项年份在本轮范围内，但被表彰论文多为历史论文；它们只作为影响力线索，不计入 accepted-paper deep_read。对应 claim <a id="VLSI-001-SW006"></a>[VLSI-001-SW006](#VLSI-001-SW006)。
- 没找到 canonical source 的 ordinary best paper / distinguished paper 不新增，不把 unverified 奖项写成事实。

## 6. 代表性论文和证据矩阵

本轮 evidence matrix 记录 112 篇 deep_read 论文。它们不是排名，而是按问题覆盖选出的 anchor / formation / milestone / frontier / method-bridge rows。

| 子领域 | 代表论文线索 |
|---|---|
| 神经渲染/3D 高斯 | [VLSI-2023-P0154](../../10_corpus/VLSI/id_index.md#VLSI-2023-P0154) NeRPIM； [VLSI-2026-P0099](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0099) 拾穗者； [VLSI-2026-P0103](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0103) 高斯排序单元 |
| 机器人/体现边缘 | [VLSI-2018-P0104](../../10_corpus/VLSI/id_index.md#VLSI-2018-P0104) Navion； [VLSI-2025-P0172](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0172) MAVERIC; [VLSI-2026-P0062](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0062) Sirius |
| Transformer / LLM 代币硅 | [VLSI-2022-P0031](../../10_corpus/VLSI/id_index.md#VLSI-2022-P0031)； [VLSI-2025-P0100](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0100) 阿德莉亚； [VLSI-2025-P0116](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0116) CELLA; [VLSI-2026-P0117](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0117) SPECTRA; [VLSI-2026-P0119](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0119) 推理 LLM 加速器 |
| CIM/PIM | [VLSI-2016-P0076](../../10_corpus/VLSI/id_index.md#VLSI-2016-P0076); [VLSI-2019-P0114](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0114)； [VLSI-2021-P0093](../../10_corpus/VLSI/id_index.md#VLSI-2021-P0093) CHIMERA; [VLSI-2021-P0121](../../10_corpus/VLSI/id_index.md#VLSI-2021-P0121) PIMCA; [VLSI-2026-P0120](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0120) 2nm 数字 CIM 编译器 |
| 边缘视觉/传感器内 | [VLSI-2017-P0005](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0005)； [VLSI-2021-P0078](../../10_corpus/VLSI/id_index.md#VLSI-2021-P0078)； [VLSI-2025-P0136](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0136); [VLSI-2024-P0004](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0004) |
| Chiplet / 3D 缩放 | [VLSI-2022-P0191](../../10_corpus/VLSI/id_index.md#VLSI-2022-P0191) Occamy； [VLSI-2024-P0174](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0174)； [VLSI-2026-P0142](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0142); [VLSI-2026-P0238](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0238) |

Citation/adoption/artifact/benchmark fields include query date `2026-06-27` where present. No citation count is used as a ranking; missing adoption evidence is written as `impact_unverified` or `needs_review`。对应 claim <a id="VLSI-001-SW012"></a>[VLSI-001-SW012](#VLSI-001-SW012)。

## 7. 发展脉络

2016-2018 年，VLSI 的加速器相关信号主要来自 SRAM/low-power neural processors、Navion 视觉惯导和 early memory-centric classifiers。2019-2021 年，computational memory、PCM/RRAM/MRAM/FeFET CIM、PIMCA、CHIMERA 让 memory-wall 从口号变成阵列、电路和系统问题。2022-2024 年，foundry digital/analog SRAM CIM、Transformer inference/learning、chiplet/HBM 和 edge SoC 信号增多。2025-2026 年，frontier 靠近 LLM token/speculative decoding、reasoning/RLFT、3D Gaussian occupancy、embodied-AI chiplets、2nm CIM compiler、3D/photonic memory compute。所有趋势均由多篇或跨年份论文支撑，2026 部分仍是 official-program partial。

## 8. 团队线索

本轮没有完成 affiliation disambiguation，因此只写 team_signal，不写机构排名。以下线索都只是作者/机构字符串和论文集合线索，不代表强弱排序。

| 团队/机构线索 | 关联方向 | 代表线索 | 使用限制 |
|---|---|---|---|
| MIT / Sze-Karaman | edge/robotics vision silicon | Navion、Gleanmer | 只作为后续 entity disambiguation 入口；不写机构排名 |
| Princeton / Verma | SRAM/MRAM CIM | SRAM/MRAM CIM 相关论文集合 | 只是作者/机构字符串和论文集合线索；不代表强弱排序 |
| Stanford + TSMC | CIM / accelerator silicon | CHIMERA、MINOTAUR | 只作为后续 entity disambiguation 入口；不写机构排名 |
| IBM analog AI 与 Polimi + IBM | PCM computational memory | analog AI、PCM computational memory | 只是作者/机构字符串和论文集合线索；不代表强弱排序 |
| KAIST / Hoi-Jun Yoo | neural rendering、path-planning、edge-AI SoC | neural rendering、path-planning、edge-AI SoC rows | 只作为后续 entity disambiguation 入口；不写机构排名 |
| Tsinghua / HKUST | digital CIM、edge LLM | digital CIM、edge LLM rows | 只是作者/机构字符串和论文集合线索；不代表强弱排序 |
| Berkeley / Shao 和 Michigan low-power SoC | robotics、edge SoC | robotics/edge SoC rows | 只作为后续 entity disambiguation 入口；不写机构排名 |
| TSMC / imec / Sony | 3DIC、packaging、sensor integration | 3DIC、packaging、sensor integration rows | 只是作者/机构字符串和论文集合线索；不代表强弱排序 |

## 9. 对博士入门者的阅读路线

第一条线读 CIM/PIM：从 2016 SRAM classifier、2019 computational memory、2021 PIMCA/CHIMERA 到 2025-2026 Transformer/CNN nonvolatile processor 和 2nm digital CIM compiler，重点看数据搬运如何变成阵列、ADC/DAC、数值格式和外围电路问题。第二条线读 edge robotics/vision：Navion、micro-robotic vision SoC、GPPU、MAVERIC、Gleanmer、Sirius，重点看 real-time、低功耗和传感器输入约束。第三条线读 LLM token hardware：per-vector 4-bit transformer accelerator、Adelia、CELLA、SPECTRA、reasoning LLM accelerator，重点看 prefill/decode、KV/cache、speculative decoding 和 token energy。第四条线读 chiplet/3D：Occamy、die-to-die/CoWoS/SoIC、3D integration 和 HBM，理解大模型和高带宽负载的物理边界。

## 10. 缺失来源

- 2016-2025 官方 final/advance program PDF 的逐页抽取与 session name 回填。
- IEEE Xplore affiliation、abstract、keywords 和 PDF 首页批量抽取。
- VLSI 与 JSSC/ISSCC/CICC/A-SSCC/Hot Chips 的 same-chip follow-on 对照。
- 2026年期末论文集DOI元数据。
- Artifact/code reuse、benchmark standardization、industry/toolchain adoption 的系统审计。
