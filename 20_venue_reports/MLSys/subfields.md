# MLSys 小领域深读

## 1. 范围与语料

- 语料库：`486` paper rows和 `25` award rows。 2019-2025 年会议记录行有官方会议记录页面； 2026 年仍为 `partial`，因为最终proceedings卷未公开。
- 筛选矩阵涵盖 `511` 行。决定很重要：`{'index_only': 342, 'deep_read': 134, 'needs_review': 35}`。
- 证据矩阵记录 `109` 有界deep-readpaper rows。读取深度计数：`{'full_pdf': 104, 'title': 3, 'official_page+artifact_docs': 1, 'abstract': 1}`。少数非 PDF 行被显式标记为 `abstract`、`title` 或 `official_page+artifact_docs`。
- 引用/采用审核是初步的。引文查找日期为 `2026-06-27`；大多数 Semantic Scholar/OpenAlex 调用返回 429，而少数 2026 行在其evidence rows中记录了明确的 Semantic Scholar 计数。
- artifact/代码行是 `runnable_unchecked`；在此过程中未执行任何 artifact 或基准测试。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | 活跃年数 | evidence rows | 证据状态 |
|---|---|---|---:|---:|---|
| <a id="MLSys-SF01"></a>[MLSys-SF01](#MLSys-SF01) | LLM 服务状态/缓存/注意力系统 | 为 KV 状态下的 Transformer/LLM workload、前缀重用、注意力延迟、内存压力和服务 SLO 提供服务。 | 2021-2026 | 23 | venue_provisional;包括 2026 部分行 |
| <a id="MLSys-SF02"></a>[MLSys-SF02](#MLSys-SF02) | 编译器/自动调整/内核生成协同设计 | 将模型图、动态程序和演进内核转变为跨硬件后端的优化可执行计划。 | 2019-2026 | 9 | venue_provisional;包括 2026 部分行 |
| <a id="MLSys-SF03"></a>[MLSys-SF03](#MLSys-SF03) | 分布式培训、通信和加速器编排 | 跨加速器和异构集群放置、调度、通信和重新实现 ML workload。 | 2019-2022 | 6 | venue_provisional |
| <a id="MLSys-SF04"></a>[MLSys-SF04](#MLSys-SF04) | 稀疏/MoE/图形/推荐系统 | 利用稀疏、专家路由、图形和嵌入密集型 workload，而不会丢失局部性或负载平衡。 | 2021-2025 | 13 | venue_provisional |
| <a id="MLSys-SF05"></a>[MLSys-SF05](#MLSys-SF05) | 基准测试/分析/模拟/再现性 | 测量、调试、模拟和比较 ML 系统，超越单一加速数字。 | 2019-2026 | 15 | venue_provisional;包括 2026 部分行 |
| <a id="MLSys-SF06"></a>[MLSys-SF06](#MLSys-SF06) | 边缘/设备上 TinyML 运行时 | 在 MCU/mobile/edge 内存、功耗和后端碎片约束下部署 ML/LLM 推理。 | 2020-2026 | 14 | venue_provisional;包括 2026 部分行 |
| <a id="MLSys-SF07"></a>[MLSys-SF07](#MLSys-SF07) | 3DGS/神经渲染/视频/XR 系统 | 满足交互式视觉/生成延迟、FPS、稀疏 3D 计算和渲染质量限制。 | 2022-2026 | 8 | venue_provisional;包括 2026 部分行 |
| <a id="MLSys-SF08"></a>[MLSys-SF08](#MLSys-SF08) | 硬件加速器、内存和互连协同设计 | 将加速器基板约束暴露给 ML 系统设计，而不将主题简化为通用硬件标签。 | 2019-2026 | 13 | venue_provisional;包括 2026 部分行 |
| <a id="MLSys-SF09"></a>[MLSys-SF09](#MLSys-SF09) | RAG/向量索引存储系统 | 减少向量索引存储开销，同时保留类似 RAG 系统的检索质量和延迟。 | 2026-2026 | 1 | venue_provisional;包括 2026 部分行 |
| <a id="MLSys-SF10"></a>[MLSys-SF10](#MLSys-SF10) | 云分配、生产生命周期和训练状态系统 | 在不确定性下的生产分配、云服务和优化器/训练状态管理中使用预测器或状态压缩。 | 2021-2025 | 7 | venue_provisional |

## 3. 小领域深读

### [MLSys-SF01](#MLSys-SF01)。 LLM 服务状态/缓存/注意力系统

- 研究问题：在 KV 状态下服务 Transformer/LLM workload、前缀重用、注意力延迟、内存压力和服务 SLO。
- 背景：反复出现的瓶颈是 `LLM/Transformer inference and serving` 的 `KV/cache/state memory, attention latency, TTFT/TPOT, throughput, batching and SLO attainment`。
- 本 venue 的现状：2021 年至 2026 年期间有 23 行证据。这是最密集的 MLSys 第二波线。它从Transformer数据移动和大型Transformer推理开始，然后通过AWQ、SLoRA、Prompt Cache、FlashInfer、QServe、Seesaw、FlashAttention-4、FlexiCache、Kitty和OPKV成为KV/cache/attention-serving线。 2026 行显示了向 KV 驻留、量化、稀疏性、编码代理重用和内核/工具循环的转变。
- 方法谱系：注意力内核、KV 压缩/卸载、前缀/缓存重用、量化、批处理、调度。
- 代表论文：[MLSys-2021-P0016](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0016)； [MLSys-2023-P0013](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0013)； [MLSys-2024-P0004](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0004); [MLSys-2024-P0005](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0005); [MLSys-2024-P0020](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0020); [MLSys-2024-P0025](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0025); [MLSys-2024-P0027](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0027); [MLSys-2024-P0028](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0028); [MLSys-2024-P0032](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0032); [MLSys-2025-P0015](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0015); [MLSys-2025-P0026](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0026)； [MLSys-2025-P0028](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0028)；....
- 团队线索：Google/TPU、MIT HAN Lab、UW/CMU/NVIDIA、Berkeley/Sky 和 ​​Toronto/Pekhimenko 风格的作者字符串出现，但没有进行团队排名。
- workload/artifact 信号：[MLSys-2021-P0016](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0016)； [MLSys-2024-P0005](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0005); [MLSys-2024-P0032](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0032); [MLSys-2025-P0015](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0015); [MLSys-2025-P0028](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0028); [MLSys-2025-P0038](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0038); [MLSys-2025-P0046](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0046); [MLSys-2026-P0022](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0022); [MLSys-2026-P0057](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0057); [MLSys-2026-P0060](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0060)； [MLSys-2026-P0085](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0085)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF02](#MLSys-SF02)。编译器/自动调整/内核生成协同设计

- 研究问题：将模型图、动态程序和演进内核转变为跨硬件后端的优化可执行计划。
- 背景：反复出现的瓶颈是 `ML kernels, model graphs, dynamic programs, HLS/operator generation` 的 `search cost, graph capture, backend portability, compile time, hardware utilization`。
- 本 venue 的当前状态：2019-2026 年有 9 行证据。编译器系列从宽松的图形替换、AutoPhase、学习成本模型、Cortex 和 torch.fx 到 2026 内核/运算符生成工作（例如 AccelOpt 和 Flashlight）。这与 HLS/EDA/加速器工作流程相关，但 MLSys 证据主要是面向系统/编译器，而不是面向物理设计。
- 方法谱系：图形重写、学习成本模型、HLS 阶段排序、程序捕获、DSL、生成内核。
- 代表论文：[MLSys-2019-P0018](../../10_corpus/MLSys/id_index.md#MLSys-2019-P0018)； [MLSys-2020-P0004](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0004)； [MLSys-2020-P0005](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0005); [MLSys-2021-P0001](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0001); [MLSys-2021-P0015](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0015); [MLSys-2022-P0044](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0044); [MLSys-2024-P0007](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0007); [MLSys-2026-P0005](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0005); [MLSys-2026-P0059](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0059)。
- 团队线索：出现 Berkeley/MIT/Stanford/PyTorch/Google/UT Austin/Georgia Tech/Microsoft Research 风格的作者字符串；所有这些仍然只是entity disambiguation输入。
- workload/artifact 信号：[MLSys-2020-P0005](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0005)； [MLSys-2024-P0007](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0007); [MLSys-2026-P0005](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0005); [MLSys-2026-P0059](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0059)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF03](#MLSys-SF03)。分布式训练、通信和加速器编排

- 研究问题：跨加速器和异构集群放置、调度、通信和重新实现 ML workload。
- 背景：反复出现的瓶颈是 `distributed DNN training/inference and large-scale accelerator orchestration` 的 `collective communication, placement, pipeline bubbles, rematerialization memory, cluster scheduling`。
- 本 venue 的当前状态：2019-2022 年有 6 个evidence rows。编排系列从 SOAP/FlexFlow 式布局和 all-reduce 系统到 Checkmate、网内聚合和 Pathways。它支持cross-venue 挂钩 HPCA/ISCA/MICRO 以实现内存、集合和加速器规模执行。
- 方法谱系：并行搜索、集体、网络内聚合、重新实现、异步数据流。
- 代表论文：[MLSys-2019-P0008](../../10_corpus/MLSys/id_index.md#MLSys-2019-P0008)； [MLSys-2019-P0009](../../10_corpus/MLSys/id_index.md#MLSys-2019-P0009)； [MLSys-2020-P0006](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0006); [MLSys-2020-P0008](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0008); [MLSys-2021-P0025](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0025); [MLSys-2022-P0029](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0029)。
- 团队线索：Jia-Zaharia-Aiken、Berkeley/Stoica、IBM/Baidu 和 Google Pathways 作者字符串出现；没有排名。
- workload/artifact 信号：[MLSys-2019-P0008](../../10_corpus/MLSys/id_index.md#MLSys-2019-P0008)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF04](#MLSys-SF04)。稀疏/MoE/图形/推荐系统

- 研究问题：利用稀疏、专家路由、图形和嵌入密集型 workload，而不丢失局部性或负载平衡。
- 背景：反复出现的瓶颈是 `MoE, GNN, recommendation, embeddings, sparse neighborhood workloads` 的 `sparse routing, load imbalance, irregular memory access, embedding storage, graph rematerialization`。
- 本 venue 的当前状态：2021-2025 年有 13 行证据。该小领域收集稀疏、MoE、图形和推荐 workload。证据涵盖从 TT-Rec/ROBE/GPU semiring/TorchSparse 到 Tutel、MegaBlocks、Lancet、COMET 和 MiLo。它可以在cross-venue综合过程中分为 MoE 服务/训练、稀疏图/点云和推荐嵌入。
- 方法谱系：稀疏内核、专家路由、嵌入压缩、图调度、块稀疏执行。
- 代表论文：[MLSys-2021-P0032](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0032)； [MLSys-2021-P0048](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0048); [MLSys-2022-P0014](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0014)； [MLSys-2022-P0033](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0033); [MLSys-2022-P0037](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0037)； [MLSys-2023-P0022](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0022); [MLSys-2023-P0027](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0027); [MLSys-2023-P0039](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0039); [MLSys-2024-P0022](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0022); [MLSys-2024-P0029](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0029); [MLSys-2024-P0031](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0031)； [MLSys-2025-P0007](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0007)；....
- 团队线索：Meta/FB recsys、RAPIDS/NVIDIA、Microsoft Tutel、Stanford/Matei Zaharia、ByteDance/Flux 和 MIT HAN Lab 字符串出现；没有排名。
- workload/artifact 信号：[MLSys-2023-P0039](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0039)； [MLSys-2024-P0031](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0031)； [MLSys-2025-P0007](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0007)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF05](#MLSys-SF05)。基准测试/分析/模拟/再现性

- 研究问题：测量、调试、模拟和比较 ML 系统，超越单一加速数。
- 背景：反复出现的瓶颈是 `training/inference benchmarks, profilers, simulators, execution traces` 的 `measurement coverage, trace fidelity, reproducibility, variance, profiler overhead`。
- 本 venue 的当前状态：2019-2026 年有 15 行证据。这条线是 MLSys 的核心标识：数据验证、MLPerf、方差核算、RL-Scope、URSABench、Hotline、ReLM、VIDUR、MLCommons Chakra、FlashInfer-Bench、ProfInfer 和 XProf。工具可用性与标准化不同，因此基准/采用 claim 仍然仅限于源范围。
- 方法谱系：基准测试套件、分析器、模拟器、标准化跟踪、方差核算。
- 代表论文：[MLSys-2019-P0012](../../10_corpus/MLSys/id_index.md#MLSys-2019-P0012)； [MLSys-2020-P0015](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0015); [MLSys-2021-P0006](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0006)； [MLSys-2021-P0039](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0039); [MLSys-2022-P0050](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0050)； [MLSys-2023-P0019](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0019); [MLSys-2023-P0037](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0037); [MLSys-2023-P0042](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0042); [MLSys-2024-P0006](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0006); [MLSys-2024-P0035](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0035); [MLSys-2025-P0053](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0053)； [MLSys-2026-P0058](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0058)；....
- 团队线索：出现 Google/TFDV、MLCommons、UofT/Pekhimenko/Reddi、CMU/Microsoft、MLCommons/Chakra 和 OpenXLA/XProf 字符串；没有排名。
- workload/artifact 信号：[MLSys-2019-P0012](../../10_corpus/MLSys/id_index.md#MLSys-2019-P0012)； [MLSys-2020-P0015](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0015)； [MLSys-2021-P0006](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0006); [MLSys-2021-P0039](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0039)； [MLSys-2022-P0050](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0050); [MLSys-2023-P0019](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0019); [MLSys-2023-P0037](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0037); [MLSys-2024-P0006](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0006); [MLSys-2024-P0035](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0035); [MLSys-2025-P0053](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0053)； [MLSys-2026-P0058](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0058)； [MLSys-2026-P0099](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0099)；....所有 artifact 都是 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF06](#MLSys-SF06)。边缘/设备上 TinyML 运行时

- 研究问题：在 MCU/移动/边缘内存、功耗和后端碎片约束下部署 ML/LLM 推理。
- 背景：反复出现的瓶颈是 `TinyML, mobile, MCU, on-device inference and edge attention` 的 `memory, power, backend fragmentation, integer/low-bit compute, observability`。
- 本 venue 的当前状态：2020-2026 年有 14 行证据。边缘线连接MCU量化、MicroNets、TensorFlow Lite Micro、ML-EXray、MLPerf Mobile、vMCU、边缘稀疏内核、ExecuTorch、IntAttention和ProfInfer。它是通往机器人/嵌入式部署和 FPGA 式资源限制的有用桥梁。
- 方法谱系：低精度、运行时内存管理、整数注意力、边缘内核、部署工具链。
- 代表论文：[MLSys-2020-P0014](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0014)； [MLSys-2021-P0027](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0027)； [MLSys-2021-P0031](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0031); [MLSys-2021-P0045](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0045); [MLSys-2022-P0020](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0020); [MLSys-2022-P0023](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0023); [MLSys-2022-P0024](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0024); [MLSys-2024-P0036](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0036); [MLSys-2025-P0011](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0011); [MLSys-2025-P0025](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0025); [MLSys-2025-P0029](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0029)； [MLSys-2025-P0030](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0030)；....
- 团队线索：TensorFlow/TinyML、ARM、MLCommons mobile、Meta/PyTorch ExecuTorch 和边缘注意作者字符串出现；没有排名。
- workload/artifact 信号：[MLSys-2021-P0027](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0027)； [MLSys-2022-P0024](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0024); [MLSys-2026-P0052](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0052); [MLSys-2026-P0083](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0083)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF07](#MLSys-SF07)。 3DGS/神经渲染/视频/XR 系统

- 研究问题：满足交互式视觉/生成延迟、FPS、稀疏 3D 计算和渲染质量约束。
- 背景：反复出现的瓶颈是 `video, XR, point-cloud, 3DGS/neural rendering, video diffusion` 的 `interactive latency, sparse convolution, sorting/rasterization, video throughput, memory traffic`。
- 本 venue 的当前状态：2022-2026 年有 8 行证据。视觉系统产品线正在兴起而不是固定下来。 TorchSparse 和 XRBench 是较早的相邻锚点； 2026 年添加了 Spira、StreamDiffusionV2 和 SwiftGS。 SwiftGS 直接针对 3DGS，但它仍然是 2026 年的部分行，不应被视为没有 cross-venue evidence的稳定venue谱系。
- 方法谱系：稀疏卷积、流式传输、渲染系统协同优化、生成编解码器、基准/评估。
- 代表论文：[MLSys-2022-P0045](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0045)； [MLSys-2023-P0014](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0014)； [MLSys-2023-P0045](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0045); [MLSys-2025-P0044](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0044); [MLSys-2026-P0146](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0146); [MLSys-2026-P0148](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0148); [MLSys-2026-P0150](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0150); [MLSys-2026-P0166](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0166)。
- 团队线索：MIT HAN/Song Han、XRBench、SPIN/MPI-SWS、Adobe/Berkeley/MIT 风格的视觉系统字符串出现；没有排名。
- workload/artifact 信号：[MLSys-2022-P0045](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0045)； [MLSys-2023-P0045](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0045); [MLSys-2026-P0146](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0146); [MLSys-2026-P0148](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0148); [MLSys-2026-P0150](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0150); [MLSys-2026-P0166](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0166)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF08](#MLSys-SF08)。硬件加速器、内存和互连协同设计

- 研究问题：将加速器基板约束暴露给 ML 系统设计，而不将主题简化为通用硬件标签。
- 背景：反复出现的瓶颈是 `accelerator kernels, memory hierarchy, NoC/IMC/chiplet/ASIC workflows` 的 `hardware utilization, on-chip/off-chip memory, interconnect collectives, PPA/deployability`。
- 本 venue 的当前状态：2019-2026 年有 13 行证据。这是硬件感知的 MLSys 系列：空间加速器、Transformer 数据移动、片上层次结构、混合精度/可靠性、MCM 分区、协同设计、Torch2Chip、NoC 集体和 AIMC 可部署性。在声称起源或主导地位之前，应该将其与建筑和 EDA venue进行比较。
- 方法谱系：加速器协同设计、NoC 集合、内存层次结构、数字格式、专用内核。
- 代表论文：[MLSys-2019-P0025](../../10_corpus/MLSys/id_index.md#MLSys-2019-P0025)； [MLSys-2020-P0019](../../10_corpus/MLSys/id_index.md#MLSys-2020-P0019)； [MLSys-2021-P0010](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0010); [MLSys-2021-P0011](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0011); [MLSys-2021-P0038](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0038); [MLSys-2022-P0002](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0002); [MLSys-2022-P0031](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0031); [MLSys-2022-P0046](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0046); [MLSys-2023-P0036](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0036); [MLSys-2024-P0033](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0033); [MLSys-2025-P0012](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0012)； [MLSys-2026-P0001](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0001)；....
- 团队线索：Olukotun、SPCL、Toronto/Pekhimenko、Google Edge TPU、Cornell/SeoLab、ETH/Bologna 和 AIMC 字符串出现；没有排名。
- workload/artifact 信号：[MLSys-2026-P0001](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0001)； [MLSys-2026-P0002](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0002)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF09](#MLSys-SF09)。 RAG/向量索引存储系统

- 研究问题：减少向量索引存储开销，同时保留类似 RAG 系统的检索质量和延迟。
- 背景：反复出现的瓶颈是 `RAG/vector search and embedding-index storage` 的 `index storage, embedding recomputation cost, retrieval latency, update overhead`。
- 本 venue 的当前状态：2026-2026 年有 1 个evidence rows。 LEANN 将在 2026 年创建一个以存储为中心的 RAG/向量索引信号。它是有奖项支持的，但还太新，不能视为稳定的 MLSys 子领域。
- 方法谱系：嵌入重新计算、邻近图压缩、存储感知索引。
- 代表论文：[MLSys-2026-P0086](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0086)。
- 团队线索：LEANN 出现 Berkeley/Databricks 风格的作者字符串；没有排名。
- workload/artifact 信号：[MLSys-2026-P0086](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0086)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

### [MLSys-SF10](#MLSys-SF10)。云分配、生产生命周期和训练状态系统

- 研究问题：在不确定性下，在生产分配、云服务和优化器/训练状态管理中使用预测器或状态压缩。
- 背景：反复出现的瓶颈是 `VM allocation, cloud serving, optimizer-state memory, production ML lifecycle` 的 `misprediction, heterogeneity, optimizer memory, production drift, cloud cost/SLOs`。
- 本 venue 的当前状态：2021-2025 年有 7 行证据。该小领域将生产分配和状态管理行与 LLM 服务和加速器设计分开。 VM生命周期分配和LAVA形成直接2023-2025线程； APOLLO 是一个单论文优化器状态信号，在成为趋势之前需要跨年度证据。
- 方法谱系：生命周期预测、分布适应、内存高效优化器、部署验证。
- 代表论文：[MLSys-2021-P0029](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0029)； [MLSys-2022-P0038](../../10_corpus/MLSys/id_index.md#MLSys-2022-P0038)； [MLSys-2023-P0043](../../10_corpus/MLSys/id_index.md#MLSys-2023-P0043); [MLSys-2025-P0005](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0005); [MLSys-2025-P0021](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0021); [MLSys-2025-P0023](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0023); [MLSys-2025-P0054](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0054)。
- 团队线索：出现 Microsoft/Azure/Google 云和优化器状态作者字符串；没有排名。
- workload/artifact 信号：[MLSys-2021-P0029](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0029)。所有 artifact 均为 `runnable_unchecked`；没有进行复制。
- 开放问题：引文图、artifact 重用、独立采用、精确的 DOI 覆盖范围和cross-venue比较仍然开放，除非单个evidence rows标记了已验证的较窄事实。

## 4. 趋势证据和边界

- 趋势判断使用多篇论文或跨年份组。单纸信号（例如 APOLLO 和 LEANN）被标记为候选行或里程碑行，而不是稳定小领域。
- 即使 OpenReview PDF 可读，2026 行也是不完整的。最终的会议记录卷、DOI/会议记录元数据和 artifact 徽章需要稍后审核。
- `Practical Unstructured Sparsity for Efficient LLM Inference` 和 `ViRuleEval` 仍然是标题级/源限制行。它们的机制尚未推断。
- `ForeCache` 似乎对应于 arXiv `CacheWise`，但标题变体需要在撰写确定的书目 claim 之前进行程序确认。
- 3DGS/神经渲染是一种新兴的 MLSys 信号，受 TorchSparse/XRBench/Spira/StreamDiffusionV2/SwiftGS 支持，但稳定的谱系 claim 需要与graphics and architecture venues 进行 cross-venue comparison。

## 5. Remaining 缺失来源

- MLSys 2026 年最终论文集卷、DOI/论文集元数据和 artifact 徽章。
- 超出来源本地 claim 的引用图和采用/重用证据。大多数引文 API 在 2026 年 6 月 27 日返回 429；检索到的计数仅记录在行级证据中。
- 2019-2020 年规范官方奖项获奖者来源。
- 隶属关系明确的作者/团队/机构时间表。当前的团队字段仅包含作者字符串且未排名。
