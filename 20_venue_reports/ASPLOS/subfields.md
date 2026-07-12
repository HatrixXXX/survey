# ASPLOS 第二轮小领域深读

检索/写入日期：`2026-06-27`  
输入范围：`10_corpus/venues/ASPLOS/` 与 `20_venue_reports/ASPLOS/`。本文件只讨论 ASPLOS venue 内部信号。

## 1. 范围

第二轮共筛选 `papers.csv` 1161 行和 `awards.csv` 40 行，写入 `ASPLOS_screening_matrix.csv` 1201 行。父 agent 最终确定 `deep_read` 论文 103 篇，包括 award paper、首轮代表论文、3DGS/neural rendering、LLM serving/training、CXL/tiered memory、compiler/HLS、FPGA/reconfigurable、sparse dataflow、security/verification、xUI 等与项目方向相关的论文。

`ASPLOS_paper_evidence_matrix.csv` 对这 103 篇记录 WHY/HOW/WHAT/IMPACT/EVIDENCE。citation/adoption/artifact 信号均写检索日期；没有可靠证据的长期影响写为 `impact_unverified` 或 `partial`。

## 2. 小领域图谱

| subfield_id | 标签 | deep_read 论文 | 活跃年数 | 证据状态 |
|---|---|---:|---|---|
| <a id="ASPLOS-SF01"></a>[ASPLOS-SF01](#ASPLOS-SF01) | 3DGS 和神经渲染加速 | 7 | 2024-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF02"></a>[ASPLOS-SF02](#ASPLOS-SF02) | SLAM、机器人与具身 AI 极端边缘 | 7 | 2024-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF03"></a>[ASPLOS-SF03](#ASPLOS-SF03) | LLM 服务、注意力和以内存为中心的推理 | 25 | 2022-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF04"></a>[ASPLOS-SF04](#ASPLOS-SF04) | 分布式LLM 训练和 GPU 通信 | 8 | 2024-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF05"></a>[ASPLOS-SF05](#ASPLOS-SF05) | 持久、分层、远端和 CXL 内存系统 | 11 | 2016-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF06"></a>[ASPLOS-SF06](#ASPLOS-SF06) | 编译器 IR、HLS/dataflow 和张量代码生成 | 14 | 2021-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF07"></a>[ASPLOS-SF07](#ASPLOS-SF07) | FPGA/云虚拟化和可重构平台 | 6 | 2020-2022 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF08"></a>[ASPLOS-SF08](#ASPLOS-SF08) | 稀疏且不规则的加速器数据流 | 7 | 2021-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF09"></a>[ASPLOS-SF09](#ASPLOS-SF09) | 硬件正确性、安全性和验证 | 11 | 2016-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF10"></a>[ASPLOS-SF10](#ASPLOS-SF10) | 内存分析、预取、和基准基础设施 | 4 | 2020-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF11"></a>[ASPLOS-SF11](#ASPLOS-SF11) | FHE 和新兴安全/模拟 workload | 2 | 2025-2026 | 来源支持；影响证据混合 |
| <a id="ASPLOS-SF12"></a>[ASPLOS-SF12](#ASPLOS-SF12) | 用户级异步通知和内核绕过运行时 | 1 | 2025-2025 | 来源支持；影响证据混合 |

## 3. 小领域深读

### [ASPLOS-SF01](#ASPLOS-SF01)：3DGS 和神经渲染加速

- 研究问题：3DGS/neural rendering 的渲染核心、训练内存和 VR/on-device 管线加速。
- 背景和现状：本组覆盖 2024, 2025, 2026，共有 7 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：host/device offloading and pipelining; workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2024-P0077](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0077) GSCore: Efficient Radiance Field Rendering via Architectural Support for 3D Gaussian Splatting; [ASPLOS-2025-P0097](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0097) MetaSapiens: Real-Time Neural Rendering with Efficiency-Aware Pruning and Accelerated Foveated Rendering; [ASPLOS-2026-P0014](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0014) ASDR: Exploiting Adaptive Sampling and Data Reuse for CIM-based Instant Neural Rendering; [ASPLOS-2026-P0028](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0028) CLM: Removing the GPU Memory Barrier for 3D Gaussian Splatting; [ASPLOS-2026-P0063](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0063) GS-Scale: Unlocking Large-Scale 3D Gaussian Splatting Training via Host Offloading; [ASPLOS-2026-P0094](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0094) Nebula: Infinite-Scale 3D Gaussian Splatting in VR via Collaborative Rendering and Accelerated Stereo Rasterization。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2024-P0077](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0077); [ASPLOS-2025-P0097](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0097); [ASPLOS-2026-P0014](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0014); [ASPLOS-2026-P0028](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0028); [ASPLOS-2026-P0063](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0063); [ASPLOS-2026-P0094](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0094); [ASPLOS-2026-P0096](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0096)。
- artifact / benchmark 信号：3 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2024-P0077；ASPLOS-2025-P0097；ASPLOS-2026-P0014；ASPLOS-2026-P0028；ASPLOS-2026-P0063；ASPLOS-2026-P0094` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 SIGGRAPH/HPCA/ISCA/MLSys 的 neural rendering、3DGS training、mobile rendering 形成交叉；对 3DGS 加速器方向最直接。

### [ASPLOS-SF02](#ASPLOS-SF02)：SLAM、机器人与具身 AI 极端边缘

- 研究问题：SLAM、机器人优化、embodied AI、item-level intelligence 的低时延、可靠性和生命周期约束。
- 背景和现状：本组覆盖 2024, 2025, 2026，共有 7 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2024-P0118](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0118) ORIANNA: An Accelerator Generation Framework for Optimization-based Robotic Applications; [ASPLOS-2024-P0147](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0147) SlimSLAM: An Adaptive Runtime for Visual-Inertial Simultaneous Localization and Mapping; [ASPLOS-2025-P0139](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0139) ReCA: Integrated Acceleration for Real-Time and Efficient Cooperative Embodied Autonomous Agents; [ASPLOS-2025-P0162](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0162) SuperNoVA: Algorithm-Hardware Co-Design for Resource-Aware SLAM; [ASPLOS-2026-P0006](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0006) AGS: Accelerating 3D Gaussian Splatting SLAM via CODEC-Assisted Frame Covisibility Detection; [ASPLOS-2026-P0037](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0037) CREATE: Cross-Layer Resilience Characterization and Optimization for Efficient yet Reliable Embodied AI Systems。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2024-P0118](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0118); [ASPLOS-2024-P0147](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0147); [ASPLOS-2025-P0139](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0139); [ASPLOS-2025-P0162](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0162); [ASPLOS-2026-P0006](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0006); [ASPLOS-2026-P0037](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0037); [ASPLOS-2026-P0082](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0082)。
- artifact / benchmark 信号：1 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2024-P0118；ASPLOS-2024-P0147；ASPLOS-2025-P0139；ASPLOS-2025-P0162；ASPLOS-2026-P0006；ASPLOS-2026-P0037` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 ICRA/IROS/RSS、MLSys、edge-AI venue 交叉；适合连接具身智能和低功耗硬件。

### [ASPLOS-SF03](#ASPLOS-SF03)：LLM 服务、注意力和以记忆为中心的推理

- 研究问题：LLM/Transformer attention、PIM/NPU/CXL、speculative decoding、KV/cache 和 serving runtime。
- 背景和现状：本组覆盖 2022, 2023, 2024, 2025, 2026，共有 25 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：FPGA runtime/compiler/platform co-design; formal verification, invariant learning, or model checking; prefetching and hardware hints; processing-in-memory or memory-centric mapping; runtime scheduling and resource allocation。
- 代表工作：[ASPLOS-2022-P0019](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0019) DOTA: detect and omit weak attentions for scalable transformer acceleration; [ASPLOS-2023-P0048](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0048) FLAT: An Optimized Dataflow for Mitigating Attention Bottlenecks; [ASPLOS-2024-P0001](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0001) 8-bit Transformer Inference and Fine-tuning for Edge Accelerators; [ASPLOS-2024-P0015](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0015) AttAcc! Unleashing the Power of PIM for Batched Transformer-based Generative Model Inference; [ASPLOS-2024-P0033](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0033) CMC: Video Transformer Acceleration via CODEC Assisted Matrix Condensing; [ASPLOS-2024-P0054](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0054) ExeGPT: Constraint-Aware Resource Scheduling for LLM Inference。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2022-P0019](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0019); [ASPLOS-2023-P0048](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0048); [ASPLOS-2024-P0001](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0001); [ASPLOS-2024-P0015](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0015); [ASPLOS-2024-P0033](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0033); [ASPLOS-2024-P0054](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0054); [ASPLOS-2024-P0111](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0111); [ASPLOS-2024-P0152](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0152)。
- artifact / benchmark 信号：11 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2022-P0019；ASPLOS-2023-P0048；ASPLOS-2024-P0001；ASPLOS-2024-P0015；ASPLOS-2024-P0033；ASPLOS-2024-P0054` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 MLSys/OSDI/SOSP/SC/HPCA 的 LLM serving、PIM、KV cache 和 speculative decoding 交叉。

### [ASPLOS-SF04](#ASPLOS-SF04)：分布式 LLM 训练和 GPU 通信

- 研究问题：大模型训练并行、通信重叠、MoE、heterogeneous GPU/network 和 collective abstraction。
- 背景和现状：本组覆盖 2024, 2025, 2026，共有 8 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：host/device offloading and pipelining; runtime scheduling and resource allocation; sparse dataflow, pruning, or irregular scheduling; workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2024-P0028](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0028) Centauri: Enabling Efficient Scheduling for Communication-Computation Overlap in Large Model Training via Communication Partitioning; [ASPLOS-2024-P0128](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0128) PrimePar: Efficient Spatial-temporal Tensor Partitioning for Large Transformer Model Training; [ASPLOS-2025-P0065](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0065) FlexSP: Accelerating Large Language Model Training via Flexible Sequence Parallelism; [ASPLOS-2025-P0070](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0070) FSMoE: A Flexible and Scalable Training System for Sparse Mixture-of-Experts Models; [ASPLOS-2025-P0158](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0158) Spindle: Efficient Distributed Training of Multi-Task Large Models via Wavefront Scheduling; [ASPLOS-2025-P0184](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0184) Vela: A Virtualized LLM Training System with GPU Direct RoCE。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2024-P0028](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0028); [ASPLOS-2024-P0128](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0128); [ASPLOS-2025-P0065](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0065); [ASPLOS-2025-P0070](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0070); [ASPLOS-2025-P0158](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0158); [ASPLOS-2025-P0184](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0184); [ASPLOS-2026-P0092](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0092); [ASPLOS-2026-P0145](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0145)。
- artifact / benchmark 信号：2 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2024-P0028；ASPLOS-2024-P0128；ASPLOS-2025-P0065；ASPLOS-2025-P0070；ASPLOS-2025-P0158；ASPLOS-2025-P0184` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 SC/MLSys/OSDI、NVIDIA/Microsoft GPU communication 生态交叉。

### [ASPLOS-SF05](#ASPLOS-SF05)：持久、分层、远端和 CXL 内存系统

- 研究问题：持久内存安全、tiered/far/disaggregated memory、CXL fabric 与 bridge synthesis。
- 背景和现状：本组覆盖 2016, 2017, 2019, 2020, 2021, 2022, 2025, 2026，共有 11 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：CXL fabric/interface and coherence/verification mechanisms; workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2016-P0016](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2016-P0016) Failure-Atomic Persistent Memory Updates via JUSTDO Logging; [ASPLOS-2016-P0021](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2016-P0021) High-Performance Transactions for Persistent Memories; [ASPLOS-2017-P0003](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2017-P0003) An Analysis of Persistent Memory Use with WHISPER; [ASPLOS-2019-P0040](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2019-P0040) Nimble Page Management for Tiered Memory Systems; [ASPLOS-2019-P0059](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2019-P0059) Software-Defined Far Memory in Warehouse-Scale Computers; [ASPLOS-2020-P0059](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2020-P0059) Mitosis: Transparently Self-Replicating Page-Tables for Large-Memory Machines。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2016-P0016](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2016-P0016); [ASPLOS-2016-P0021](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2016-P0021); [ASPLOS-2017-P0003](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2017-P0003); [ASPLOS-2019-P0040](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2019-P0040); [ASPLOS-2019-P0059](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2019-P0059); [ASPLOS-2020-P0059](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2020-P0059); [ASPLOS-2021-P0013](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0013); [ASPLOS-2022-P0011](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0011)。
- artifact / benchmark 信号：6 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2016-P0016；ASPLOS-2016-P0021；ASPLOS-2017-P0003；ASPLOS-2019-P0040；ASPLOS-2019-P0059；ASPLOS-2020-P0059` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 MICRO/ISCA/HPCA/FAST/EuroSys 的 PM/CXL/disaggregation 交叉。

### [ASPLOS-SF06](#ASPLOS-SF06)：编译器 IR、HLS/dataflow 和张量代码生成

- 研究问题：accelerator generator IR、HLS/dataflow、MLIR/tensor compiler、e-graph 和 operator fusion。
- 背景和现状：本组覆盖 2021, 2022, 2023, 2024, 2025, 2026，共有 14 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：compiler IR/lowering and design-space transformation; e-graph rewriting/extraction or anti-unification; workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2021-P0001](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0001) A compiler infrastructure for accelerator generators; [ASPLOS-2022-P0035](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0035) HeteroGen: transpiling C to heterogeneous HLS code with automated test generation and program repair; [ASPLOS-2023-P0060](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0060) HIR: An MLIR-based Intermediate Representation for Hardware Accelerator Description; [ASPLOS-2023-P0107](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0107) Sigma: Compiling Einstein Summations to Locality-Aware Dataflow; [ASPLOS-2023-P0108](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0108) Simulator Independent Coverage for RTL Hardware Languages; [ASPLOS-2024-P0017](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0017) Automatic Generation of Vectorizing Compilers for Customizable Digital Signal Processors。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2021-P0001](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0001); [ASPLOS-2022-P0035](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0035); [ASPLOS-2023-P0060](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0060); [ASPLOS-2023-P0107](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0107); [ASPLOS-2023-P0108](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0108); [ASPLOS-2024-P0017](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0017); [ASPLOS-2024-P0082](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0082); [ASPLOS-2025-P0140](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0140)。
- artifact / benchmark 信号：8 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2021-P0001；ASPLOS-2022-P0035；ASPLOS-2023-P0060；ASPLOS-2023-P0107；ASPLOS-2023-P0108；ASPLOS-2024-P0017` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 DAC/ICCAD/DATE/CGO/MLSys/FCCM 的 HLS、MLIR、tensor compiler 和 e-graph 交叉。

### [ASPLOS-SF07](#ASPLOS-SF07)：FPGA/云虚拟化和可重构平台

- 研究问题：cloud FPGA virtualization、CPU/FPGA research platforms、CGRA realization 和 FPGA compile/runtime。
- 背景和现状：本组覆盖 2020, 2021, 2022，共有 6 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：FPGA runtime/compiler/platform co-design; compiler IR/lowering and design-space transformation; workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2020-P0085](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2020-P0085) Virtualizing FPGAs in the Cloud; [ASPLOS-2021-P0011](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0011) Compiler-driven FPGA virtualization with SYNERGY; [ASPLOS-2021-P0072](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0072) When application-specific ISA meets FPGAs: a multi-layer virtualization framework for heterogeneous cloud FPGAs; [ASPLOS-2022-P0023](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0023) Enzian: an open, general, CPU/FPGA platform for systems software research; [ASPLOS-2022-P0051](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0051) PLD: fast FPGA compilation to make reconfigurable acceleration compatible with modern incremental refinement software development; [ASPLOS-2022-P0057](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0057) REVAMP: a systematic framework for heterogeneous CGRA realization。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2020-P0085](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2020-P0085); [ASPLOS-2021-P0011](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0011); [ASPLOS-2021-P0072](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0072); [ASPLOS-2022-P0023](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0023); [ASPLOS-2022-P0051](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0051); [ASPLOS-2022-P0057](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0057)。
- artifact / benchmark 信号：1 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2020-P0085；ASPLOS-2021-P0011；ASPLOS-2021-P0072；ASPLOS-2022-P0023；ASPLOS-2022-P0051；ASPLOS-2022-P0057` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 FPGA/FCCM/FPL、OSDI/EuroSys 的 cloud FPGA 和平台系统交叉。

### [ASPLOS-SF08](#ASPLOS-SF08)：稀疏且不规则的加速器数据流

- 研究问题：SpGEMM/sparse attention/automata/dynamic orchestration 等不规则数据流。
- 背景和现状：本组覆盖 2021, 2022, 2023, 2024, 2026，共有 7 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：sparse dataflow, pruning, or irregular scheduling; workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2021-P0024](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0024) Gamma: leveraging Gustavson’s algorithm to accelerate sparse matrix multiplication; [ASPLOS-2021-P0038](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0038) Mind mappings: enabling efficient algorithm-accelerator mapping space search; [ASPLOS-2022-P0001](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0001) A full-stack search technique for domain optimized deep learning accelerators; [ASPLOS-2023-P0049](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0049) Flexagon: A Multi-dataflow Sparse-Sparse Matrix Multiplication Accelerator for Efficient DNN Processing; [ASPLOS-2023-P0113](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0113) Spada: Accelerating Sparse Matrix Multiplication with Adaptive Dataflow; [ASPLOS-2024-P0112](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0112) ngAP: Non-blocking Large-scale Automata Processing on GPUs。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2021-P0024](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0024); [ASPLOS-2021-P0038](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0038); [ASPLOS-2022-P0001](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2022-P0001); [ASPLOS-2023-P0049](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0049); [ASPLOS-2023-P0113](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2023-P0113); [ASPLOS-2024-P0112](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0112); [ASPLOS-2026-P0002](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0002)。
- artifact / benchmark 信号：2 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2021-P0024；ASPLOS-2021-P0038；ASPLOS-2022-P0001；ASPLOS-2023-P0049；ASPLOS-2023-P0113；ASPLOS-2024-P0112` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 ISCA/MICRO/HPCA/SC 的 sparse accelerator 和 graph/automata processing 交叉。

### [ASPLOS-SF09](#ASPLOS-SF09)：硬件正确性、安全性和验证

- 研究问题：MCM/interface verification、side-channel/sanitizer、formal HLS/system software、DRAM/CXL security。
- 背景和现状：本组覆盖 2016, 2017, 2024, 2025, 2026，共有 11 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：formal verification, invariant learning, or model checking; workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2016-P0011](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2016-P0011) COATCheck; [ASPLOS-2017-P0053](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2017-P0053) TriCheck; [ASPLOS-2024-P0040](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0040) CSSTs: A Dynamic Data Structure for Partial Orders in Concurrent Execution Analysis; [ASPLOS-2024-P0070](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0070) GIANTSAN: Efficient Memory Sanitization with Segment Folding; [ASPLOS-2025-P0064](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0064) FlexProf: Flexible, Side-Channel-Free Memory Access; [ASPLOS-2025-P0076](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0076) H-Houdini: Scalable Invariant Learning。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2016-P0011](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2016-P0011); [ASPLOS-2017-P0053](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2017-P0053); [ASPLOS-2024-P0040](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0040); [ASPLOS-2024-P0070](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0070); [ASPLOS-2025-P0064](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0064); [ASPLOS-2025-P0076](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0076); [ASPLOS-2025-P0166](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0166); [ASPLOS-2025-P0185](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0185)。
- artifact / benchmark 信号：3 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2016-P0011；ASPLOS-2017-P0053；ASPLOS-2024-P0040；ASPLOS-2024-P0070；ASPLOS-2025-P0064；ASPLOS-2025-P0076` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 S&P/USENIX Security/DAC/ICCAD/CAV、ISCA/MICRO 的 security/verification 交叉。

### [ASPLOS-SF10](#ASPLOS-SF10)：内存分析、预取和基准基础架构

- 研究问题：PM/cache/prefetch/profiling 的 workload、benchmark、measurement artifact。
- 背景和现状：本组覆盖 2020, 2021, 2024, 2026，共有 4 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：prefetching and hardware hints; workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2020-P0001](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2020-P0001) A Benchmark Suite for Evaluating Caches' Vulnerability to Timing Attacks; [ASPLOS-2021-P0002](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0002) A hierarchical neural model of data prefetching; [ASPLOS-2024-P0122](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0122) PDIP: Priority Directed Instruction Prefetching; [ASPLOS-2026-P0035](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0035) CounterPoint: Using Hardware Event Counters to Refute and Refine Microarchitectural Assumptions。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2020-P0001](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2020-P0001); [ASPLOS-2021-P0002](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2021-P0002); [ASPLOS-2024-P0122](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2024-P0122); [ASPLOS-2026-P0035](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0035)。
- artifact / benchmark 信号：1 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2020-P0001；ASPLOS-2021-P0002；ASPLOS-2024-P0122；ASPLOS-2026-P0035` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 MICRO/HPCA/ISCA 的 cache/prefetch benchmark、FAST/OSDI 的 workload characterization 交叉。

### [ASPLOS-SF11](#ASPLOS-SF11)：FHE 和新兴安全/模拟 workload

- 研究问题：FHE deep learning、tensor-algebra RTL simulation 等新 workload 的 compiler/runtime 加速。
- 背景和现状：本组覆盖 2025, 2026，共有 2 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：workload-specific hardware/software co-design mechanism。
- 代表工作：[ASPLOS-2025-P0112](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0112) Orion: A Fully Homomorphic Encryption Framework for Deep Learning; [ASPLOS-2026-P0127](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0127) RTeAAL Sim: Using Tensor Algebra to Represent and Accelerate RTL Simulation。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2025-P0112](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0112); [ASPLOS-2026-P0127](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-P0127)。
- artifact / benchmark 信号：2 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 `ASPLOS-2025-P0112；ASPLOS-2026-P0127` 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 CCS/PPML、DAC/ICCAD、simulation tool venues 交叉。

### [ASPLOS-SF12](#ASPLOS-SF12)：用户级异步通知和内核绕过运行时

- 研究问题：user-level interrupt、kernel-bypass I/O/storage/accelerator notification。
- 背景和现状：本组覆盖 2025，共有 1 篇 deep_read 证据。它说明 ASPLOS 在这个方向上关注 workload、runtime、memory/interface、compiler 和 hardware 的共同设计，而不是只按 `FPGA`、`HPC`、`ML systems` 这类大标签归类。
- 技术路线：user-level interrupt and kernel-bypass notification extensions。
- 代表工作：[ASPLOS-2025-P0058](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0058) Extended User Interrupts (xUI): Fast and Flexible Notification without Polling。
- 团队线索：只记录作者/机构字符串线索，不做强弱排序；需要后续entity disambiguation。当前可见线索来自这些论文集合：[ASPLOS-2025-P0058](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0058)。
- artifact / benchmark 信号：1 篇有 code/artifact/dataset 或 benchmark 信号；全部未运行，不能写成已复现。
- 发展趋势：趋势判断只基于多篇/跨年份 evidence。当前证据集合 [ASPLOS-2025-P0058](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0058) 支撑该方向在 ASPLOS 内持续出现；2026 论文的长期影响统一保守处理。
- 跨会议 hook：与 OSDI/SOSP/NSDI/EuroSys 的 kernel-bypass I/O、storage 和 accelerator runtime 交叉。

## 4. 剩余差距

- `papers.csv` 没有 abstract/keywords 字段；本轮不扩 schema，不猜摘要或关键词。
- 2024 artifact awards 和更早历史 award rows 仍需专门补表。
- citation count 来自 Crossref 或 Semantic Scholar 等单一索引，只作为影响力线索，不用于强弱排序。
- artifact/code 只记录可获得 URL，没有运行，状态为 `runnable_unchecked` 或 `artifact_unverified`。
- 团队线索未做entity disambiguation，不做团队强弱排序。
