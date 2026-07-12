# ISPA 小领域深读

## 1. 范围与语料

本文件是 ISPA 第二轮 的 venue 内小领域深读。范围只限 ISPA，不把 ISPA 写成 ISPASS。

- Corpus：`papers.csv` 1437 行，`awards.csv` 10 行。
- Screening：`ISPA_screening_matrix.csv` 1447 行，其中 `deep_read` 59 行、`index_only` 1107 行、`needs_review` 260 行、`exclude_non_main` 21 行。
- Evidence：`ISPA_paper_evidence_matrix.csv` 49 篇 parent-selected paper rows。
- Read depth：多数为 title/DOI/proceedings metadata 级；没有完成 full PDF 批量精读。影响力没有独立证据时统一写 `impact_unverified`。
- 2026：截至 2026-06-27 未找到 accepted papers/proceedings/awards，按 `normal_2026_partial` 处理。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="ISPA-SF01"></a>[ISPA-SF01](#ISPA-SF01) | 分析和性能表征 | 如何解释 workload 和 accelerator/system 的真实性能瓶颈 | 分析、CNN 部署、无服务器、H100、OpenMP 工具 | 测量覆盖范围、I/O 管道、workload 代表性 | 分析、表征、工具辅助分析 | 2016, 2020-2022, 2024-2025 | venue_provisional |
| <a id="ISPA-SF02"></a>[ISPA-SF02](#ISPA-SF02) | FPGA/HLS DNN 实现 | 如何把 CNN/RNN/NAS 负载落到 FPGA、HLS 或 FPGA cluster | LSTM、MobileNetV2、CNN、HLS4ML | 片上存储、数据流、实现工作 | FPGA 映射、半流、NAS、HLS4ML | 2017, 2020-2021, 2024 | venue_provisional |
| <a id="ISPA-SF03"></a>[ISPA-SF03](#ISPA-SF03) | 以内存为中心PIM 和混合内存 | 如何减少 PMem/PIM/CXL/hybrid memory 的数据搬运和持久化开销 | CNN、KV 存储、图形、LLM 检查点、CXL | 内存带宽、持久性、热页放置 | PIM、PMem 模型、检查点、页面调度 | 2017, 2021-2022, 2024-2025 | venue_provisional；注意到一处标题冲突 |
| <a id="ISPA-SF04"></a>[ISPA-SF04](#ISPA-SF04) | GPU 运行时调度和卸载 | 如何在 GPU kernel、DMA offload 和 GPU cluster 中控制低时延和公平性 | GPU 内核、分布式 DL、卸载、集群 | 抢占、通信重叠、DMA 争用、弹性 | 运行时调度、共享、非抢占式调度 | 2017, 2021-2022, 2025 | venue_provisional |
| <a id="ISPA-SF05"></a>[ISPA-SF05](#ISPA-SF05) | DNN 算子编译器、低精度和数据流 | 如何让 DNN/Transformer 算子在 accelerator 上提高利用率并降低数据搬运 | CNN、ViT、稀疏注意力、GEMM、卷积 | 算子利用、精度、稀疏性、布局 | 层融合、量化、收缩数据流、稀疏注意力、布局转换 | 2020-2025 | venue_provisional |
| <a id="ISPA-SF06"></a>[ISPA-SF06](#ISPA-SF06) | graph/GNN 不规则缓存 | 如何缓解 graph/GNN 的不规则访存和 feature cache 压力 | GNN 推理/训练、图 | 随机访问、特征缓存压力 | 分区缓存、分阶段缓存 | 2021-2022 | venue_provisional 但样本较小 |
| <a id="ISPA-SF07"></a>[ISPA-SF07](#ISPA-SF07) | 图形、3DGS 和 Web3D 系统 | 如何处理 rendering/3DGS/Web3D 的 cache、precision、atomic 和 load-balance 问题 | 平铺图形、3D 高斯、Web3D、3DGS 训练 | 缓存局部性、精度、边缘缓存、原子争用 | 缓存管理、混合精度、DAG 缓存、原子合并 | 2018, 2024-2025 | venue_provisional；直接用户相关前沿 |
| <a id="ISPA-SF08"></a>[ISPA-SF08](#ISPA-SF08) | 边缘/自主/应用程序运行时边界 | 哪些 edge/autonomous/application ML 论文只提供系统边界，不能直接支撑 accelerator 趋势 | 自动驾驶、边缘智能、ROS 2、物流 Transformer | 延迟、安全、应用程序部署 | 异常检测、定价、调度、Transformer 应用程序 | 2021, 2023-2024 | 边界证据 |
| <a id="ISPA-SF09"></a>[ISPA-SF09](#ISPA-SF09) | 安全/区块链/网络边界 | 哪些 award/network/security 行应从 accelerator 趋势中排除 | 区块链、网络测量、路由、共识 | 验证、路由、测量 | 区块链、草图、共识 | 2021, 2023 | 负边界 |
| <a id="ISPA-SF10"></a>[ISPA-SF10](#ISPA-SF10) | 字符串 workload 加速 | 如何为 string matching/string operations 做 application-specific acceleration | 字符串集匹配、字符串操作 | 内存访问和吞吐量 | FPGA 加速、通用字符串加速器 | 2016, 2018 | venue_provisional |

## 3. 小领域深读

### [ISPA-SF01](#ISPA-SF01)。分析和性能表征

Research problem：ISPA 中一部分论文不是提出新硬件，而是解释 workload 行为和性能瓶颈。代表行包括 [ISPA-2016-P0003](../../10_corpus/ISPA/id_index.md#ISPA-2016-P0003)、[ISPA-2020-P0417](../../10_corpus/ISPA/id_index.md#ISPA-2020-P0417)、[ISPA-2021-P0534](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0534)、[ISPA-2022-P0758](../../10_corpus/ISPA/id_index.md#ISPA-2022-P0758)、[ISPA-2024-P1142](../../10_corpus/ISPA/id_index.md#ISPA-2024-P1142)、[ISPA-2025-P1339](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1339)。

Method lineage：早期是 memory access pattern profiling；2020 年出现 CNN 在 commercial accelerators 部署时的 I/O pipeline characterization；2021 年 award row CE-Dedup 提供 CNN training data deduplication 边界信号；2022 年扩展到 serverless workload characterization；2024-2025 年出现 H100 confidential AI workload 和 LLM-assisted OpenMP parallelization tooling。

Team signals：只保留作者字符串，未做entity disambiguation。Artifact/code 没有运行或复用检查。

Open questions：需要 PDF 级复核这些工具/characterization 是否提供公开 workload、脚本或 benchmark。

### [ISPA-SF02](#ISPA-SF02)。 FPGA/HLS DNN 实施

Research problem：把神经网络负载落到 FPGA/HLS 时，主要瓶颈是数据流、片上存储、资源约束和实现自动化。代表行包括 [ISPA-2017-P0172](../../10_corpus/ISPA/id_index.md#ISPA-2017-P0172)、[ISPA-2020-P0435](../../10_corpus/ISPA/id_index.md#ISPA-2020-P0435)、[ISPA-2021-P0561](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0561)、[ISPA-2021-P0617](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0617)、[ISPA-2024-P0956](../../10_corpus/ISPA/id_index.md#ISPA-2024-P0956)。

Method lineage：2017 年是 LSTM FPGA accelerator；2020 年出现 MobileNetV2 semi-streaming FPGA inference；2021 年有 CNN storage/dataflow 和 FPGA-oriented lightweight NAS；2024 年转向 HLS4ML 和 FPGA cluster。

Representative work：`Automatic Implementation of Large-Scale CNNs on FPGA Cluster Based on HLS4ML` 有 Crossref DOI 和 citation count 初查，但没有 artifact 运行检查。不能写成“可复现”。

Cross-venue hook：交给 FPGA/FCCM/FPL/FPT 对照 HLS4ML、FPGA cluster、NAS 和 CNN dataflow 是否是跨会议稳定线。

### [ISPA-SF03](#ISPA-SF03)。以内存为中心的 PIM 和混合内存

Research problem：PMem、PIM、CXL 和 hybrid memory 论文共同指向数据搬运、容量和持久化开销。代表行包括 [ISPA-2017-P0118](../../10_corpus/ISPA/id_index.md#ISPA-2017-P0118)、[ISPA-2021-P0587](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0587)、[ISPA-2022-P0713](../../10_corpus/ISPA/id_index.md#ISPA-2022-P0713)、[ISPA-2024-P0908](../../10_corpus/ISPA/id_index.md#ISPA-2024-P0908)、[ISPA-2025-P1363](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1363)、[ISPA-2025-P1401](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1401)。

Method lineage：2017 年 racetrack-memory PIM CNN 是早期近存计算信号；2021-2022 年转到 PMem KV/graph；2024 年出现 LLM checkpointing over hybrid memory；2025 年出现 CXL hot-page scheduling 和 racetrack remapping。

Risk：deep-read prompt 中 [ISPA-2021-P0587](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0587) 标题和本地 `papers.csv` 不一致；最终写入使用本地标题 `HyperKV: A High Performance Concurrent Key-Value Store for Persistent Memory`，并保留 `needs_review`。

### [ISPA-SF04](#ISPA-SF04)。 GPU 运行时调度和卸载

Research problem：GPU kernel、distributed DL、DMA offload 和 GPU cluster 都需要在吞吐、低时延、公平性之间取舍。代表行包括 [ISPA-2017-P0210](../../10_corpus/ISPA/id_index.md#ISPA-2017-P0210)、[ISPA-2021-P0662](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0662)、[ISPA-2022-P0716](../../10_corpus/ISPA/id_index.md#ISPA-2022-P0716)、[ISPA-2025-P1327](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1327)、[ISPA-2025-P1424](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1424)。

Trend evidence：2017 年是 preemption-aware kernel scheduling；2021 年是 GPU sharing scheduler for distributed deep learning；2022 年是 DMA offloading scheduler；2025 年转向 GPU cluster scheduling。该趋势由跨年份多篇论文支撑，但 adoption 未验证。

### [ISPA-SF05](#ISPA-SF05)。 DNN 运算符编译器，低精度，数据流

Research problem：DNN/Transformer operator 侧的瓶颈包括 fusion、layout conversion、低精度、稀疏和 dataflow。代表行包括 [ISPA-2020-P0428](../../10_corpus/ISPA/id_index.md#ISPA-2020-P0428)、[ISPA-2021-P0488](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0488)、[ISPA-2021-P0504](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0504)、[ISPA-2023-P0872](../../10_corpus/ISPA/id_index.md#ISPA-2023-P0872)、[ISPA-2024-P1052](../../10_corpus/ISPA/id_index.md#ISPA-2024-P1052)、[ISPA-2024-P1098](../../10_corpus/ISPA/id_index.md#ISPA-2024-P1098)、[ISPA-2024-P1128](../../10_corpus/ISPA/id_index.md#ISPA-2024-P1128)、[ISPA-2024-P1220](../../10_corpus/ISPA/id_index.md#ISPA-2024-P1220)、[ISPA-2025-P1268](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1268)、[ISPA-2025-P1399](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1399)。

Method lineage：2020 年 DLFusion 把 layer fusion 和 autotuning 放到 accelerator compiler 上；2021 年 stochastic/mixed precision 和 reconfigurable architecture 合流；2023 年是 systolic-friendly compression；2024-2025 年扩展到 sparse attention、GEMM layout/autotuning、ViT operators、regular sparsity 和 RISC-V quantization vector unit。

Cross-venue hook：需要和 DAC/ICCAD 的 compiler/co-design，以及 MICRO/HPCA 的 operator/dataflow accelerator 对照。

### [ISPA-SF06](#ISPA-SF06)。图/GNN不规则缓存

Research problem：GNN inference/training 的主要瓶颈是不规则访存和 feature cache。代表行是 [ISPA-2021-P0627](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0627) 和 [ISPA-2022-P0750](../../10_corpus/ISPA/id_index.md#ISPA-2022-P0750)。

Current state：样本少，但 PCGraph 和 SCGraph 构成 inference/training 两个方向的缓存线索。不能单独写成成熟趋势，只能作为 venue_provisional。

### [ISPA-SF07](#ISPA-SF07)。图形、3DGS 和 Web3D 系统

Research problem：这条线最接近用户的 3DGS/neural rendering 方向。代表行包括 [ISPA-2018-P0372](../../10_corpus/ISPA/id_index.md#ISPA-2018-P0372)、[ISPA-2024-P0942](../../10_corpus/ISPA/id_index.md#ISPA-2024-P0942)、[ISPA-2025-P1278](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1278)、[ISPA-2025-P1323](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1323)。

Method lineage：2018 年 Tail-PASS 是 tiled graphics rendering hardware 的 cache-management 线索；2024 年 AMQGaussian 是 3D Gaussian mixed-precision representation；2025 年 Web3D caching 和 GSGPU 分别指向 edge caching 与 3DGS training GPU architecture。GSGPU 的 evidence 当前只有 proceedings TOC/DOI metadata，impact 写 `impact_unverified`。

Cross-venue hook：需要和 MICRO/HPCA/ASPLOS/graphics venue 以及 FPGA venue 对照 3DGS 的 sorting、atomic、memory、precision 和 training pipeline。

### [ISPA-SF08](#ISPA-SF08)。边缘/自治/应用程序运行时边界

这类论文包括 autonomous driving anomaly/uncertainty、distributed edge-intelligence pricing、O2O logistics Transformer 和 ROS 2 scheduling。它们有助于描述部署约束，但不能直接支撑硬件加速趋势。[ISPA-2024-P1073](../../10_corpus/ISPA/id_index.md#ISPA-2024-P1073) 在 deep-read prompt 与本地标题存在冲突，最终使用本地 `papers.csv` 的 ROS 2 标题并标 `needs_review`。

### [ISPA-SF09](#ISPA-SF09)。安全/区块链/网络边界

2021 和 2023 的一部分 award rows 属于 blockchain、routing、network measurement 或 consensus。它们进入 deep_read 是因为 award/source 审计需要，不用于 accelerator 代表趋势。

### [ISPA-SF10](#ISPA-SF10)。字符串 workload 加速

`SCADIS` 和 `WEAVER` 显示 ISPA 早期 application-specific acceleration 不只围绕 DNN，也有 string-set matching/string operations。这条线对 3DGS 不直接相关，但对“负载驱动 accelerator”有方法参考价值。

## 4. 发展趋势

- Accelerator 线从 early FPGA/PIM/string accelerator 走向 compiler、systolic/sparse、GEMM/ViT/quantization 和 3DGS。证据集合：[ISPA-2016-P0059](../../10_corpus/ISPA/id_index.md#ISPA-2016-P0059)、[ISPA-2017-P0118](../../10_corpus/ISPA/id_index.md#ISPA-2017-P0118)、[ISPA-2020-P0428](../../10_corpus/ISPA/id_index.md#ISPA-2020-P0428)、[ISPA-2023-P0872](../../10_corpus/ISPA/id_index.md#ISPA-2023-P0872)、[ISPA-2024-P1052](../../10_corpus/ISPA/id_index.md#ISPA-2024-P1052)、[ISPA-2024-P1220](../../10_corpus/ISPA/id_index.md#ISPA-2024-P1220)、[ISPA-2025-P1268](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1268)、[ISPA-2025-P1323](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1323)、[ISPA-2025-P1399](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1399)。
- GPU runtime 从 kernel scheduling 扩展到 distributed DL sharing、DMA offloading 和 GPU cluster scheduling。证据集合：[ISPA-2017-P0210](../../10_corpus/ISPA/id_index.md#ISPA-2017-P0210)、[ISPA-2021-P0662](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0662)、[ISPA-2022-P0716](../../10_corpus/ISPA/id_index.md#ISPA-2022-P0716)、[ISPA-2025-P1327](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1327)、[ISPA-2025-P1424](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1424)。
- Memory-centric 线从 racetrack/PIM 与 PMem 扩展到 LLM checkpointing、CXL 和 racetrack remapping。证据集合：[ISPA-2017-P0118](../../10_corpus/ISPA/id_index.md#ISPA-2017-P0118)、[ISPA-2021-P0587](../../10_corpus/ISPA/id_index.md#ISPA-2021-P0587)、[ISPA-2022-P0713](../../10_corpus/ISPA/id_index.md#ISPA-2022-P0713)、[ISPA-2024-P0908](../../10_corpus/ISPA/id_index.md#ISPA-2024-P0908)、[ISPA-2025-P1363](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1363)、[ISPA-2025-P1401](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1401)。
- 3DGS/Web3D 是近年 frontier，不是成熟线。证据集合：[ISPA-2024-P0942](../../10_corpus/ISPA/id_index.md#ISPA-2024-P0942)、[ISPA-2025-P1278](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1278)、[ISPA-2025-P1323](../../10_corpus/ISPA/id_index.md#ISPA-2025-P1323)，外加 2018 graphics cache bridge [ISPA-2018-P0372](../../10_corpus/ISPA/id_index.md#ISPA-2018-P0372)。

## 5. 方法变化

ISPA 的加速器相关论文早期偏 application-specific accelerator 和 runtime scheduling；2020 年以后，compiler/autotuning、storage/dataflow、low precision、sparse attention、GEMM layout、HLS4ML 和 GPU cluster scheduling 变多。这个判断只限 title/DOI/proceedings 级 evidence，不能替代 PDF-level taxonomy。

## 6. 缺失来源

- 缺 ISPA 2016-2025 IEEE Xplore/DBLP 批量 abstract、keywords、PDF metadata。
- 缺 2019 可解析 TOC 或官方 program。
- 缺 2022、2024、2025 canonical award pages。
- 缺 3DGS/GSGPU、AMQGaussian、HLS4ML、DLFusion 等重点论文的 PDF/artifact/code audit。
- 缺作者entity disambiguation和跨会议 team/entity 对照。
