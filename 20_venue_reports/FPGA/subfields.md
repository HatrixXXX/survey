# FPGA 小领域深读

## 1. 范围与语料

- Venue：`FPGA` / ACM-SIGDA 现场可编程门阵列国际研讨会。
- 语料库：`papers.csv` 2016-2026 年有 409 行论文； `awards.csv` 有 12 行奖励。根据项目惯例，2026 年仍为 `partial`。
- 筛选：`FPGA_screening_matrix.csv` 涵盖 421 个来源行：409 篇论文和 12 个奖项来源行。
- deep-read集：44 个选定的paper rows，加上按论文 ID 合并的 12 个重复的获奖来源行。
- 证据：`FPGA_paper_evidence_matrix.csv` 记录 WHY/HOW/WHAT/IMPACT/EVIDENCE。引文/采用检查标有查询日期 `2026-06-27`；大多数下游影响仍然是 `impact_unverified` 或 `not_audited`。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="FPGA-SF01"></a>[FPGA-SF01](#FPGA-SF01) | HLS/DSL/编译器到硬件闭包 | 转换高级程序、DSL，并转换为正确的、时序封闭的 FPGA 实现 | HLS 内核、DSL 程序、生成的加速器 | 生产力、正确性、调度、时序闭包 | 源转换，DSE，形式检查，物理感知实现 | 2018-2026 | venue_provisional；支持 [FPGA-2018-P0027](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0027)、[FPGA-2019-P0027](../../10_corpus/FPGA/id_index.md#FPGA-2019-P0027)、[FPGA-2021-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0007)、[FPGA-2021-P0008](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0008)、[FPGA-2022-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0001)、[FPGA-2023-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2023-P0001)、[FPGA-2024-P0010](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0010)、[FPGA-2026-P0008](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0008) |
| <a id="FPGA-SF02"></a>[FPGA-SF02](#FPGA-SF02) | FPGA 上的神经和低精度推理 | 在精度和延迟约束下将神经 workload 映射到 LUT/DSP/内存资源 | CNN、LSTM、BNN、KAN、量化实时神经网络 | 带宽、DSP/LUT 利用率、低 batch 延迟 | 量化、稀疏性、streaming dataflow、LUT-native evaluation | 2016-2026 | venue_provisional；支持 [FPGA-2016-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0001)、[FPGA-2016-P0002](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0002)、[FPGA-2017-P0002](../../10_corpus/FPGA/id_index.md#FPGA-2017-P0002)、[FPGA-2017-P0003](../../10_corpus/FPGA/id_index.md#FPGA-2017-P0003)、[FPGA-2026-P0004](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0004)、[FPGA-2026-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0007) |
| <a id="FPGA-SF03"></a>[FPGA-SF03](#FPGA-SF03) | LLM/生成推理和 KV/注意力系统 | 支持类似 Transformer 和状态记忆、注意力和边缘/数据中心约束下的生成推理 | Transformer、LLM 预填充/解码、KV 缓存、视频生成、RWKV、FlashAttention | 状态内存、解码延迟、注意力带宽、量化质量 | KV/缓存放置、稀疏注意力、查表 matmul、混合精度 | 2024-2026 | 前沿；支持 [FPGA-2024-P0006](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0006)、[FPGA-2024-P0020](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0020)、[FPGA-2025-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2025-P0001)、[FPGA-2025-P0023](../../10_corpus/FPGA/id_index.md#FPGA-2025-P0023)、[FPGA-2025-P0029](../../10_corpus/FPGA/id_index.md#FPGA-2025-P0029)、[FPGA-2026-P0005](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0005)、[FPGA-2026-P0018](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0018)、[FPGA-2026-P0019](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0019)、[FPGA-2026-P0042](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0042) |
| <a id="FPGA-SF04"></a>[FPGA-SF04](#FPGA-SF04) | 以内存/存储为中心的 FPGA系统 | 减少片上、HBM/HMC、NVMe、CXL 和主机内存之间的数据移动 | 内存分区、HMC/HBM、NVMe-HLS、CXL KV 缓存 | 片外带宽、银行冲突、存储/主机延迟 | 内存分区、图表银行、近存储、互连一代 | 2016-2026 | venue_provisional；支持 [FPGA-2016-P0015](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0015)、[FPGA-2018-P0024](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0024)、[FPGA-2021-P0009](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0009)、[FPGA-2021-P0010](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0010)、[FPGA-2023-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2023-P0001)、[FPGA-2026-P0005](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0005) |
| <a id="FPGA-SF05"></a>[FPGA-SF05](#FPGA-SF05) | 流/数据流/缓冲管道 | 维持生产者-消费者管道和流计算 | 数据流电路的吞吐量，脉动数组、稀疏/事件流 | 管道停顿、缓冲区大小、占用不平衡 | Buffer Placement、管道、平铺、脉动映射 | 2020-2026 | venue_provisional；支持 [FPGA-2020-P0017](../../10_corpus/FPGA/id_index.md#FPGA-2020-P0017)、[FPGA-2021-P0008](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0008)、[FPGA-2024-P0022](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0022)、[FPGA-2026-P0042](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0042) |
| <a id="FPGA-SF06"></a>[FPGA-SF06](#FPGA-SF06) | 稀疏/图/张量不规则加速 | 处理图、稀疏矩阵和稀疏注意力 workload 中的随机访问和负载不平衡 | 图分析、SpMM、稀疏注意力、事件视觉 | 不规则内存访问、负载不平衡、稀疏格式开销 | 分区、稀疏布局、近内存/HBM、块聚合 | 2016-2026 | venue_provisional；由 [FPGA-2016-P0012](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0012)、[FPGA-2018-P0024](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0024)、[FPGA-2022-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0007)、[FPGA-2023-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2023-P0007)、[FPGA-2026-P0006](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0006) |
| <a id="FPGA-SF07"></a>[FPGA-SF07](#FPGA-SF07) | 支持 FPGA/HLS 的基准/分析/再现性 | 使 FPGA claim 与单个加速数字相比具有可比性 | HLS 套件、内存微基准测试、资源预测器、RISC-V 编排、HPC 比较 | 覆盖范围、再现性、基线公平性 | 基准测试套件、微基准测试、代理建模、方法比较 | 2018-2026 | venue_provisional；由 [FPGA-2018-P0027](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0027)、[FPGA-2020-P0035](../../10_corpus/FPGA/id_index.md#FPGA-2020-P0035)、[FPGA-2021-P0009](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0009)、[FPGA-2025-P0022](../../10_corpus/FPGA/id_index.md#FPGA-2025-P0022)、[FPGA-2026-P0044](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0044)、[FPGA-2026-P0050](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0050) 支持 |
| <a id="FPGA-SF08"></a>[FPGA-SF08](#FPGA-SF08) | 物理感知 FPGA 架构/CAD | 探索实际设计的结构并关闭布线/时序/频率 | FPGA 结构、布线、布局、布局规划、多芯片闭合 | 可布线性、频率、面积延迟权衡 | 架构探索、布线、布局规划、物理感知映射 | 2016-2026 | venue_provisional；由 [FPGA-2016-P0009](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0009)、[FPGA-2021-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0007)、[FPGA-2022-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0001) 支持 |
| <a id="FPGA-SF09"></a>[FPGA-SF09](#FPGA-SF09) | 云/数据中心 FPGA 和多租户系统 | 将 FPGA 系统集成到具有部署和隔离约束的服务器/云环境中 | 云 DNN、数据中心内存系统、云原生验证 | 主机设备开销、部署摩擦、隔离 | 云映射、虚拟化/控制平面方法、验证加速 | 2019-2026 | venue_provisional；支持 [FPGA-2019-P0006](../../10_corpus/FPGA/id_index.md#FPGA-2019-P0006)、[FPGA-2021-P0009](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0009)、[FPGA-2026-P0038](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0038) |
| <a id="FPGA-SF10"></a>[FPGA-SF10](#FPGA-SF10) | 机器人/事件视觉边缘加速 | 满足 FPGA/SoC 平台上的实时感知和操作约束 | 视觉 SLAM、机器人操作、基于事件的视觉 | 控制循环延迟、传感器管道确定性、功率包络 | HW/SW 协同设计、稀疏数据流、流式管道 | 2022-2024 | venue_provisional 但线路较小；由 [FPGA-2022-P0023](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0023)、[FPGA-2022-P0024](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0024)、[FPGA-2024-P0022](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0022) |

## 3. 小领域深读

### [FPGA-SF01](#FPGA-SF01) 支持。 HLS/DSL/编译器到硬件的收敛

- 研究问题：如何在不损失正确性、QoR 或时序收敛的情况下提高高级加速器设计的效率。
- 背景：语料库中的早期 HLS 工作表现为基准/工具流工作，然后转向 DSL、物理感知实现、存储集成和形式正确性。
- 本 venue 的当前状态：HeteroCL、AutoBridge、RapidStream、DONGLE 和 HLS 的形式验证形成了 2019-2024 年可见的奖励支持序列。 LSQ 替换的 2026 年亚军将动态 HLS 内存排序保持在前沿集中。
- 方法谱系：HLS 基准测试和 DSL 抽象 -> 物理感知布局规划/流水线 -> 并行实现和存储编排 -> 形式验证和动态 HLS 内存电路。
- 代表论文：[FPGA-2018-P0027](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0027)、[FPGA-2019-P0027](../../10_corpus/FPGA/id_index.md#FPGA-2019-P0027)、[FPGA-2021-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0007)、[FPGA-2021-P0008](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0008)、[FPGA-2022-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0001)、[FPGA-2023-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2023-P0001)、[FPGA-2024-P0010](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0010)、[FPGA-2026-P0008](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0008)。
- 团队线索：仅包含作者字符串的信号包括 Cornell/UCLA/Zhiru Zhu/Jason Cong 行和 EPFL/Paolo Iennedynamic-HLS 行。这些不是消除实体歧义的排名。
- workload/artifact signal：Rosetta、HeteroCL、AutoBridge、AutoSA、RapidStream 和选定的 2026 个 HLS 行具有代码/artifact signal，全部为 `runnable_unchecked`。
- 开放问题：完整的 DOI/abstract 覆盖范围和 artifact 执行状态仍然开放；需要与 FCCM/FPL/FPT 和 DAC/ICCAD 进行cross-venue比较。

### [FPGA-SF02](#FPGA-SF02)。 FPGA

- 上的神经和低精度推理 研究问题：如何将神经模型映射到 FPGA LUT/DSP/内存资源，同时控制精度、延迟和能量。
- 背景：语料库从 2016 年的 CNN/OpenCL 和嵌入式 CNN 加速器开始，到 2017 年通过 BNN 和稀疏 LSTM 锚点，并在 2026 年达到 LUT-native KAN 和高粒度量化。
- 当前在此 claim：这条线很广泛，而不是一个单一的 workload：CNN/LSTM/BNN、推荐器、KAN 和实时神经网络量化多年来一直在出现。
- 方法谱系：固定 CNN 数据路径 -> 低位/稀疏神经推理框架 -> 特定于应用程序的推荐加速 -> LUT 原生和高粒度量化。
- 代表论文：[FPGA-2016-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0001)、[FPGA-2016-P0002](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0002)、[FPGA-2017-P0002](../../10_corpus/FPGA/id_index.md#FPGA-2017-P0002)、[FPGA-2017-P0003](../../10_corpus/FPGA/id_index.md#FPGA-2017-P0003)、[FPGA-2018-P0026](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0026)、[FPGA-2026-P0004](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0004)、[FPGA-2026-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0007)。
- 团队线索：仅作者字符串信号包括 Tsinghua/Huazhong/Yu Wang 线、Stanford/NVIDIA/Song Han 线和 USC/Viktor Prasanna 线。不进行排名。
- workload/artifact 信号：FINN 和 KANELÉ 有代码信号； ESE 和 FASTCF 有官方奖励信号；超出奖项/代码可用性的影响未经审核。
- 开放问题：LUT-native ML 和 Transformer/LLM 推理是否应该在cross-venue综合后拆分。

### [FPGA-SF03](#FPGA-SF03)。 LLM/生成推理和 KV/注意力系统

- 研究问题：当状态内存、预填充/解码平衡、注意力内核和边缘/数据中心约束占主导地位时，如何支持类 Transformer 和生成推理。
- 背景：这是 FPGA 的最新前沿，不是成熟的 2016-2026 趋势。最早选定的证据从 2024 年 Transformer/LLM 行开始，并在 2025-2026 年加强。
- 本 venue 的当前状态：FlightLLM、FlightVGM、Transformer 推理行、CXL-SpecKV、TeLLMe、RWKV 和 FlashAttention 行显示venue现在正在接受 LLM/生成系统和内核。
- 方法谱系：空间/顺序 Transformer 加速 -> 完整的 LLM 映射流程 -> 视频生成稀疏化/混合精度 -> KV-cache 分解、三元/表查找 matmul、稀疏注意力、RWKV 和 FlashAttention 内核。
- 代表论文：[FPGA-2024-P0006](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0006)、[FPGA-2024-P0020](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0020)、[FPGA-2025-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2025-P0001)、[FPGA-2025-P0023](../../10_corpus/FPGA/id_index.md#FPGA-2025-P0023)、[FPGA-2025-P0029](../../10_corpus/FPGA/id_index.md#FPGA-2025-P0029)、[FPGA-2026-P0005](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0005)、[FPGA-2026-P0018](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0018)、[FPGA-2026-P0019](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0019)、[FPGA-2026-P0039](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0039)、[FPGA-2026-P0042](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0042)。
- 团队线索：仅作者字符串信号包括 Tsinghua/SJTU/Infinigence 风格的 FlightLLM/FlightVGM 线路和 UCI-CORSA TeLLMe 线路；entity disambiguation仍然开放。
- workload/artifact 信号：FlightLLM、KANELÉ、CXL-SpecKV 和 TeLLMe 具有 code/PDF/artifact 信号； TeLLMe Zenodo artifact 被记录为访问受限/runnable_unchecked。
- 开放问题：无法推断 2026 行的引用和采用影响；需要 cross-venue 挂钩 ISCA/MICRO/HPCA/MLSys。

### [FPGA-SF04](#FPGA-SF04)。以内存/存储为中心的 FPGA 系统

- 研究问题：如何减少片外流量并将内存/存储带宽暴露给 FPGA 加速器。
- 背景：内存分区出现较早； HMC/HBM、数据中心内存分析、NVMe 和 CXL/KV 缓存稍后变得可见。
- 本 venue 的当前状态：证据支持从 LMC 和 HMC 图形分析到 HBM Connect 和 DONGLE 到 CXL-SpecKV 的以内存为中心的路线。
- 方法谱系：内存分区 -> 图形存储/访问协同优化 -> 内存微基准测试和 HBM 互连 -> 直接 NVMe 编排 -> 基于 CXL 的推测 KV 缓存。
- 代表论文：[FPGA-2016-P0015](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0015)、[FPGA-2018-P0024](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0024)、[FPGA-2021-P0009](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0009)、[FPGA-2021-P0010](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0010)、[FPGA-2023-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2023-P0001)、[FPGA-2026-P0005](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0005)。
- 团队线索：仅包含作者字符串的信号包括宾夕法尼亚大学/Jing Li DONGLE 和 FastLM/CXL-SpecKV 行；没有团队排名。
- workload/artifact 信号：DONGLE 有官方奖励/ACM DOI 信号； CXL-SpecKV 有代码信号；内存微基准测试具有基准测试/分析信号。
- 开放问题：需要与 HPCA/ASPLOS/ISCA 内存系统工作进行cross-venue比较。

### [FPGA-SF05](#FPGA-SF05)。流/数据流/缓冲管道

- 研究问题：如何防止数据流电路和流内核在缓冲区、延迟和生产者-消费者不平衡约束下停止。
- 背景：所选证据集中在数据流缓冲、脉动数组、事件/稀疏数据流和注意力内核。
- 该venue当前状态：Buffer Placement 是最明确的有奖支持的锚点； AutoSA 连接编译器生成的脉动数组；最近的事件愿景和 FlashAttention 行显示了前沿 workload。
- 方法谱系：数据流Buffer Placement -> 编译器生成的脉动映射 -> 可组合稀疏/事件数据流 -> 流水线 FlashAttention 内核。
- 代表论文：[FPGA-2020-P0017](../../10_corpus/FPGA/id_index.md#FPGA-2020-P0017)、[FPGA-2021-P0008](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0008)、[FPGA-2024-P0022](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0022)、[FPGA-2026-P0042](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0042)。
- 团队线索：仅包含作者字符串的信号包括 EPFL/Paolo Ienne/Lana Josipović 和 UCLA-VAST/AutoSA 行。
- workload/artifact 信号：AutoSA 有代码信号；Buffer Placement 有 Award/DOI 信号。
- 开放问题：这是否仍然是一个单独的小领域，还是与cross-venue综合中的 HLS/DSL 闭包合并。

### [FPGA-SF06](#FPGA-SF06)。稀疏/图/张量不规则加速

- 研究问题：如何处理随机访问、稀疏布局开销以及图和稀疏张量 workload 中的负载不平衡。
- 背景：图形处理行从 2016 年开始出现； HMC/HBM 和近内存设计表明内存层次结构是核心。
- 当前状态：证据包括图框架、HMC 图分析、SpMM、ACTS 近内存图处理和稀疏注意力。
- 方法谱系：图处理框架 -> HMC/HBM 图访问协同优化 -> 流式 SpMM -> 近内存图 -> 稀疏注意力块聚合。
- 代表论文：[FPGA-2016-P0012](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0012)、[FPGA-2018-P0024](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0024)、[FPGA-2022-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0007)、[FPGA-2023-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2023-P0007)、[FPGA-2026-P0006](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0006)。
- 团队线索：仅作者字符串信号包括清华图框架线和近内存图处理线。
- workload/artifact 信号：FPGP 和 ACTS 是框架信号，但执行/重用未经过审核。
- 开放问题：cross-venue综合应决定 DNN 稀疏性、图和稀疏注意力是否共享足够的机制以保持在一起。

### [FPGA-SF07](#FPGA-SF07)。 FPGA/HLS 的基准/分析/再现性

- 研究问题：如何使FPGA/HLS的评价具有可比性和可重复性。
- 背景：Rosetta 于 2018 年推出基准套件系列；后面的行添加了可综合数据集、内存微基准、hls4ml 代理建模、RISC-V 编排和分层 HPC 比较。
- 本 venue 的当前状态：基准/分析的行数很少，但作为其他子领域的证据标准很重要。
- 方法谱系：HLS 基准测试套件 -> 可综合的 HLS 数据集 -> 内存系统微基准测试 -> 资源/延迟估计基准测试 -> RISC-V 编排和 HPC 比较方法。
- 代表论文：[FPGA-2018-P0027](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0027)、[FPGA-2020-P0035](../../10_corpus/FPGA/id_index.md#FPGA-2020-P0035)、[FPGA-2021-P0009](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0009)、[FPGA-2025-P0022](../../10_corpus/FPGA/id_index.md#FPGA-2025-P0022)、[FPGA-2026-P0044](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0044)、[FPGA-2026-P0050](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0050)。
- 团队线索：仅限作者字符串；没有排名。
- workload/artifact 信号：Rosetta 代码记录为 runnable_unchecked；其他基准 artifact 需要跟进。
- 开放问题：基准测试/代码重用需要单独的 artifact 清单，不应仅从标题推断。

### [FPGA-SF08](#FPGA-SF08)。物理感知 FPGA 架构/CAD

- 研究问题：如何探索 FPGA 结构并关闭路由、时序和频率约束。
- 背景：FPRESSO 是 2016 年最佳论文anchor；后来的物理感知 HLS 和 RapidStream 显示了进入 HLS 级别叙述的 CAD 约束。
- 本 venue 的当前状态：architecture/CAD 线仍然是基础线，并与 HLS 闭包重叠。
- 方法谱系：晶体管/结构探索 -> 布局规划/流水线 -> 并行物理实现。
- 代表论文：[FPGA-2016-P0009](../../10_corpus/FPGA/id_index.md#FPGA-2016-P0009)、[FPGA-2021-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0007)、[FPGA-2022-P0001](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0001)。
- 团队线索：仅包含作者字符串的信号包括 EPFL/Paolo Ienne 和 UCLA-VAST/Cornell 线路。
- workload/artifact 信号：AutoBridge 和 RapidStream 代码信号记录为 runnable_unchecked。
- 开放问题：在全局分类法更改之前需要进行 DAC/ICCAD/DATE 比较。

### [FPGA-SF09](#FPGA-SF09)。云/数据中心 FPGA 和多租户系统

- 研究问题：如何在具有集成、隔离和验证约束的云/数据中心环境中部署FPGA加速。
- 背景：Cloud-DNN 和数据中心内存系统微基准测试显示部署问题； 2026 年云原生验证继续从系统角度进行。
- 此venue的当前状态：此行与部署上下文相关，而不是用户 3DGS/FPGA 方向的主要技术路线。
- 方法谱系：DNN 映射到云 FPGA -> 数据中心内存分析 -> 云原生硬件验证。
- 代表论文：[FPGA-2019-P0006](../../10_corpus/FPGA/id_index.md#FPGA-2019-P0006)、[FPGA-2021-P0009](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0009)、[FPGA-2026-P0038](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0038)。
- 团队线索：仅限作者字符串。
- workload/artifact 信号：Cloud-DNN 是一个框架信号； 2026 验证行是partial且未经影响审计。
- 开放问题：需要 cross-venue 挂钩系统和架构venue。

### [FPGA-SF10](#FPGA-SF10)。机器人/事件视觉边缘加速

- 研究问题：如何在FPGA/SoC平台上满足实时感知和操控约束。
- 背景：这是 FPGA 中较小的一行，但可直接用作相邻边缘实时 workload 系列。
- 本 venue 的现状：选定的证据包括视觉 SLAM、机器人操作和基于事件的视觉稀疏数据流。
- 方法谱系：视觉 SLAM 加速 -> 用于操作的非参数置信传播 -> 用于事件视觉的可组合动态稀疏数据流。
- 代表论文：[FPGA-2022-P0023](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0023)、[FPGA-2022-P0024](../../10_corpus/FPGA/id_index.md#FPGA-2022-P0024)、[FPGA-2024-P0022](../../10_corpus/FPGA/id_index.md#FPGA-2024-P0022)。
- 团队线索：仅限作者字符串。
- workload/artifact 信号：artifact/代码重用未审核。
- 开放问题：仅在 FPGA 中，机器人技术还不够占主导地位；它应该在以后的综合中与建筑/系统/机器人venue联系起来。

## 4. 发展趋势

- HLS/toolflow 在基准测试/DSL 阶段后成为强大的 FPGA venue线：Rosetta (2018)、HeteroCL (2019)、AutoBridge (2021)、RapidStream (2022)、DONGLE (2023)、HLS (2024) 的形式验证、而2026年的dynamic-HLS亚军则共同支持了这一趋势。
- 神经推理从 CNN/LSTM/BNN 锚点演变为 LUT 原生和 Transformer 相邻 workload：2016 年 CNN 行、2017 年 FINN/ESE、2024 年 FlightLLM、2025 年 FlightVGM 和 Transformer 推理行，以及2026 年的 KANELÉ/TeLLMe/CXL-SpecKV/FlashAttention。2026 年部分仅为前沿，而非长期影响证据。
- 内存和数据移动仍然是各个子领域反复出现的瓶颈：LMC (2016)、HMC 图形分析 (2018)、内存微基准测试和 HBM Connect (2021)、DONGLE (2023) 和 CXL-SpecKV (2026) 在不同年份和 workload 中显示了这一点。
- 基准/分析证据从 HLS 基准套件成熟到更广泛的方法：Rosetta (2018)、MLSBench (2020)、数据中心内存微基准测试 (2021)、wa-hls4ml/lui-gnn (2025)、RISCBench 和 HPC 比较方法 (2026)。

## 5. 方法变化

- 评估从应用程序加速和资源使用转向选定行中的基准测试、微基准测试和分析方法。
- HLS 论文越来越多地包含物理、正确性、存储或动态调度约束，而不仅仅是源级综合。
- ML 加速器论文从 CNN/RNN/BNN 映射转向 LLM/生成推理、KV 缓存、稀疏注意力以及最近行中的查表/三元设计。
- 以内存为中心的方法从分区/存储转移到 HBM/HMC、NVMe 和 CXL 式系统集成。

## 6. 缺失来源

- 完整 ACM DL 每篇论文 DOI/摘要/关键字批量导出所有 409 篇论文。
- 规范官方 FPGA 来源，提供超出当前最佳论文/亚军记录的最佳学生论文、时间测试、杰出论文或荣誉奖类别。
- 代码仓库和受限 artifact 的 artifact 执行状态。
- FCCM/FPL/FPT 和建筑/system venues的cross-venue evidence。
