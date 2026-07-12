# ASP-DAC 论文图谱分析

## 1. 会议定位

本报告中的 `ASP-DAC` 指 Asia and South Pacific Design Automation Conference。项目 registry 把它放在 EDA 组，优先级 P1。本轮把 ASP-DAC 作为设计自动化、system-level design、物理实现闭环、verification/security、PIM/CIM、3D IC/chiplet、HLS/DSE 和软硬协同设计的区域性核心来源处理。这个定位对应 claim <a id="ASP-DAC-001-C001"></a>[ASP-DAC-001-C001](#ASP-DAC-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 有 1660 行，主体来自 DBLP ASP-DAC proceedings TOC/API；2026 同时有 ASP-DAC 官方 accepted-paper ID 页面和官方 program abstract 页面。2026 年仍保持 `partial`，原因是 ASP-DAC official award archive 尚未覆盖 2026。Best Paper 和 10-year MIP 优先使用 ASP-DAC 官方 Award Archive；该 archive 在本轮可结构化确认 2016-2024。2025 Best Paper 使用 ASP-DAC 2025 official program 验证；2025 10-year MIP 未找到官方可核验题名。2026 Best Paper/MIP 仍按 SIGDA E-News 记录为 `needs_review`。对应 claim <a id="ASP-DAC-001-C002"></a>[ASP-DAC-001-C002](#ASP-DAC-001-C002) 到 <a id="ASP-DAC-001-C004"></a>[ASP-DAC-001-C004](#ASP-DAC-001-C004)，以及 第二轮 claim <a id="ASP-DAC-001-C200"></a>[ASP-DAC-001-C200](#ASP-DAC-001-C200) 到 <a id="ASP-DAC-001-C203"></a>[ASP-DAC-001-C203](#ASP-DAC-001-C203)。

| 年份 | 论文.csv 行 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 135 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2017 | 147 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2018 | 137 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2019 | 130 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2020 | 115 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2021 | 153 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2022 | 122 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2023 | 127 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2024 | 157 | 完全的 | DBLP ASP-DAC 会议记录 TOC/API |
| 2025 | 222 | 完全的 | DBLP 加上 ASP-DAC 选定论文的官方程序行 |
| 2026 | 215 | partial | DBLP 加上 ASP-DAC 官方接受/节目页面；奖项存档待定 |

## 3. 第二轮 Outputs

第二次补充写入了三个 subfield 文件：

- `ASP-DAC_screening_matrix.csv`: 覆盖 1691 行，包含 papers.csv 和 awards.csv 全量筛选。
- `ASP-DAC_paper_evidence_matrix.csv`: 54 行，包含 WHY/HOW/WHAT/IMPACT/EVIDENCE。
- `20_venue_reports/ASP-DAC/subfields.md`: venue 内小领域、路线、趋势、团队线索和缺口。

筛选决定只使用 `deep_read`、`index_only`、`exclude_non_main`、`needs_review`。本轮生成的分布是 `{'index_only': 1133, 'needs_review': 444, 'deep_read': 114}`。这些决定是 venue 内工作流状态，不等同于论文质量排名。

## 4. Topic Taxonomy and 小领域

一级 topic 仍沿用项目 taxonomy；第二轮 把报告拆成更具体的 venue-local subfields。大领域词只作为上下文，不作为主 topic。

| subfield_id | 小领域 | 核心问题 | 代表论文/信号 | 状态 |
|---|---|---|---|---|
| [ASPDAC-SF01](subfields.md#ASPDAC-SF01) | HLS 缓冲区、时序和内存限制下的 DSE 数据流 | FIFO sizing、timing、memory/HBM、graph fusion 如何在 HLS 阶段提前收敛 | 先进先出顾问； HLS-定时器；超内存分配； FESTAL；基于 FPGA 的 CNN 的设计空间探索 | venue_provisional |
| [ASPDAC-SF02](subfields.md#ASPDAC-SF02) | LLM 辅助 RTL/HLS 生成和断言基准测试 | 硬件代码/断言生成如何被 benchmark、验证和评估 | RTLLM；断言LLM；雷克斯；流量；超级传奇；断言矿工 | venue_provisional |
| [ASPDAC-SF03](subfields.md#ASPDAC-SF03) | DL 模型到 FPGA 编译和架构探索 | DNN/Transformer 如何通过 compiler/overlay/architecture DSE 映射到 FPGA | 自动编译器；整体FPGA架构探索 | venue_provisional |
| [ASPDAC-SF04](subfields.md#ASPDAC-SF04) | 布局、可布线性、时序和 3D PDN 约束下的实现收敛优化 | placement/routing/timing/PDN 如何兼顾速度与 full-flow PPA | DREAMplaceFPGA；精细地图； C3PO； DPO-3D; SPIRAL | cross_venue_candidate |
| [ASPDAC-SF05](subfields.md#ASPDAC-SF05) | 内存和边缘限制下的 3DGS/NeRF 和点云加速 | neural rendering/3D perception 的访存、延迟、训练与边缘部署问题 | 布斯-NeRF； GS规范；尖峰-NeRF； BOA-3DGS；平衡GS； HERO | venue_provisional |
| [ASPDAC-SF06](subfields.md#ASPDAC-SF06) | PIM/CIM 和图、NN 和 LLM workload 的近内存映射 | graph/NN/Transformer/LLM/KV cache 的数据搬运问题 | 图SAR；基于连接的PIM；最优数据分配； PRIMATE； BLADE; M3DKV | venue_provisional |
| [ASPDAC-SF07](subfields.md#ASPDAC-SF07) | 低功耗、近似和非易失性 AI 架构 | 能耗、精度、器件和延迟之间的取舍 | 败家子;光学 NN FFT;近似 FFT；维达 | venue_provisional |
| [ASPDAC-SF08](subfields.md#ASPDAC-SF08) | EDA/网表、模型和新兴存储器的安全性/可靠性 | netlist、EDA 模型和新型存储的安全/可靠性问题 | 网表逆向工程；过程变化感知数据管理； ML EDA 中的模型提取攻击 | venue_provisional |
| [ASPDAC-SF09](subfields.md#ASPDAC-SF09) | 电路仿真和模拟/混合信号数值加速 | circuit simulation sparse solver 的 runtime/robustness | 用于电路仿真的随机 GMRES | insufficient_evidence |

## 5. Award Papers 分析

2016-2024 Best Paper/MIP 仍以 ASP-DAC official award archive 为 canonical source。Second wave 解决了两处奖项元数据问题：[ASPDAC-2016-A16](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2016-A16) 已对齐到 [ASPDAC-2016-P0081](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2016-P0081) 和 DOI `10.1109/ASPDAC.2016.7428056`；[ASPDAC-2025-A28](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2025-A28) 的作者串按 official program 更新为 Baiyu Chen、Jiawen Cheng、Wenjian Yu。2025 MIP 未写成确定事实。2026 的 FESTAL、C3PO 和 2016 FPGA CNN DSE MIP 信号仍是 `needs_review`，因为 current ASP-DAC award archive 没有 2026 rows。

奖项只说明 ASP-DAC 的正式认可或待复核认可信号，不自动证明长期影响。Best Paper 和 10-year MIP 是强候选信号；除 MIP 奖项名称本身以外，后续影响仍需要 citation、artifact、工具链复用或跨 venue 证据补齐。

## 6. 代表论文和 Evidence

代表论文的详细 WHY/HOW/WHAT/IMPACT/EVIDENCE 已移入 `ASP-DAC_paper_evidence_matrix.csv`。这里保留阅读路线：

- HLS/FPGA/数据流：[ASPDAC-2016-P0078](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2016-P0078)、[ASPDAC-2026-P0002](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0002)、[ASPDAC-2026-P0053](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0053)、[ASPDAC-2026-P0116](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0116)、[ASPDAC-2026-P0168](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0168)。
- LLM/EDA 基准测试和断言：[ASPDAC-2024-P0085](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2024-P0085)、[ASPDAC-2025-P0003](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2025-P0003)、[ASPDAC-2025-P0006](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2025-P0006)、[ASPDAC-2025-P0053](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2025-P0053)、[ASPDAC-2026-P0098](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0098)、[ASPDAC-2026-P0114](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0114)、[ASPDAC-2026-P0152](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0152)。
- 3DGS/NeRF/点云：[ASPDAC-2024-P0090](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2024-P0090)、[ASPDAC-2025-P0157](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2025-P0157)、[ASPDAC-2026-P0032](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0032)、[ASPDAC-2026-P0069](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0069)、[ASPDAC-2026-P0159](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0159)、[ASPDAC-2026-P0191](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0191)。
- PIM/CIM/近内存：[ASPDAC-2019-P0025](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2019-P0025)、[ASPDAC-2021-P0142](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2021-P0142)、[ASPDAC-2022-P0057](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2022-P0057)、[ASPDAC-2024-P0104](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2024-P0104)、[ASPDAC-2025-P0126](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2025-P0126)、[ASPDAC-2026-P0175](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0175)、[ASPDAC-2026-P0199](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0199)。
- 物理闭合/3D IC/chiplet：[ASPDAC-2022-P0080](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2022-P0080)、[ASPDAC-2024-P0031](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2024-P0031)、[ASPDAC-2024-P0078](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2024-P0078)、[ASPDAC-2026-P0095](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0095)、[ASPDAC-2026-P0214](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0214)。

## 7. 发展脉络

- 2016-2018：award/MIP 信号集中在 Boolean/logic 表示、netlist reverse engineering、neuromorphic precision、energy-harvesting NVP、racetrack/SSD/3D IC 等主题。
- 2019-2022：PIM 和 graph processing 更清楚地进入 award 层，代表行包括 GraphSAR、Connection-based PIM 和 Optimal Data Allocation。
- 2023-2024：AI for EDA/security、GPU-parallel mapping、chiplet SI/PI、open FPGA placement 和 LLM-RTL benchmark 出现更具体的工具/benchmark线索。
- 2025-2026：HLS/dataflow closure、LLM-for-hardware-design、3DGS/NeRF、LLM/PIM/KV cache、commercial-quality placement 和 3D PDN closure 形成一组近年前沿信号。

这些判断都有多篇论文或跨年份支撑，但只限 ASP-DAC venue 内部。跨会议强弱要等 DAC/ICCAD/DATE/TCAD/FPGA/FCCM/FPL 对照。

## 8. 影响力初审

本轮只做初审，不做完整 citation/adoption audit。

| paper_id | 信号 | 地位 |
|---|---|---|
| [ASPDAC-2024-P0085](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2024-P0085) RTLLM | OpenAlex cited_by_count=141； GitHub artifact； RTLLM2.0/RTL-Coder/VFlow后续使用；检查过 2026-06-27 | 验证基准信号 |
| [ASPDAC-2022-P0080](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2022-P0080) DREAMPlaceFPGA | OpenAlex cited_by_count=22； GitHub artifact； DREAMPlaceFPGA-MP 谱系；检查过 2026-06-27 | 已验证的工具信号 |
| [ASPDAC-2025-P0003](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2025-P0003) 断言LLM | OpenAlex cited_by_count=14； GitHub artifact； AssertMiner 后续关系；检查过 2026-06-27 | 已验证/部分基线信号 |
| [ASPDAC-2026-P0002](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0002) FIFO顾问 | 公共 GitHub 代码；早期 OpenAlex 计数；检查过 2026-06-27 | partial |
| [ASPDAC-2026-P0095](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0095) C3PO | NVIDIA 研究页面和官方项目摘要；无产品采用来源 | needs_review award/adoption |
| [ASPDAC-2026-P0168](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0168) FESTAL | 官方节目摘要和SIGDA获奖信号；无官方奖项档案行 | needs_review |
| 大多数其他行 | DOI/仅限官方摘要或奖项来源证据 | impact_unverified |

没有执行仓库。 `code_available` 表示找到源仓库；它并不意味着 `artifact_evaluated`。

## 9. 团队线索

团队线索只写为 author-string/institution-string signals，不做排名。

| 团队/机构线索 | 关联方向 | 证据状态 | 使用限制 |
|---|---|---|---|
| HKUST / Zhiyao Xie / Hongce Zhang | RTLLM、AssertLLM | author-string/institution-string signal | 需要 entity disambiguation 后才能写成长期团队事实 |
| CUHK / Bei Yu / Evangeline Young | physical design、3D PDN、placement | author-string/institution-string signal | 需要 entity disambiguation；不做排名 |
| UT Austin / David Z. Pan | DREAMPlaceFPGA、optical/placement lines | author-string/institution-string signal | 需要 entity disambiguation；不写成团队强弱判断 |
| PKU / Yun Liang | FPGA dataflow synthesis | author-string/institution-string signal | 需要 entity disambiguation 后才能写成长期团队事实 |
| SJTU / Guohao Dai | video diffusion、3DGS | author-string/institution-string signal | 需要 entity disambiguation；只作为阅读入口 |
| Fudan / Wai-Shing Luk / Lingli Wang | FPGA memory、HBM | author-string/institution-string signal | 需要 entity disambiguation；不做排名 |
| NVIDIA EDA research | C3PO | institution-string signal | 需要 entity disambiguation；不写成长期团队事实 |

## 10. 对博士入门者的阅读路线

必读 10 篇：RTLLM、DREAMPlaceFPGA、FESTAL、HLS-Timer、BOA-3DGS、BalanceGS、GraphSAR、Connection-based PIM、FineMap、C3PO。

扩展阅读：Design Space Exploration of FPGA-based CNNs、FIFOAdvisor、UltraMalloc、AssertLLM、MetRex、VFlow、SuperSAGA、Spiking-NeRF、GSNorm、M3DKV、BLADE、DPO-3D、SPIRAL、ViDA、randomized GMRES for circuit simulation。

## 11. 与我的方向的连接点

ASP-DAC 对 3DGS/FPGA/机器人芯片方向有直接但很新的信号：2025-2026 的 GSNorm、Spiking-NeRF、BOA-3DGS、BalanceGS 和 HERO 直接触及 neural rendering/3DGS/NeRF；FESTAL、HLS-Timer、FIFOAdvisor 和 UltraMalloc 对 FPGA pipeline、buffer、timing、HBM 和 dataflow synthesis 有参考价值；BLADE、M3DKV、PRIMATE、Transformer Hetero-CiM 连接 LLM/Transformer 访存墙；C3PO、DPO-3D、FineMap、DREAMPlaceFPGA 提醒加速器方案最后还要过 placement、routing、timing、PDN 和 PPA。

## 12. 缺失来源

- 2016-2024 每年官方 final program PDF 的结构化 session/track/abstract 抽取。
- 2025 10-year MIP 的官方可核验题名。
- 2026 官方 ASP-DAC award archive rows。
- ACM DL / IEEE Xplore abstracts、keywords、PDF URL、artifact/citation 批量导出。
- RTLLM/AssertLLM/MetRex/FIFOAdvisor 等 artifact 的可运行性检查。
- 跨 DAC/ICCAD/DATE/TCAD/FPGA/FCCM/FPL 的 subfield 对照矩阵。
