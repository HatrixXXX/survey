# DAC 小领域深读

## 1. 范围与语料

- Venue：`DAC` /设计自动化会议。
- 语料库：`2004` `papers.csv` 行和 `7` `awards.csv` 行。
- 筛选矩阵行：`2011`（`papers`：2004，`awards`：7）。决策：`deep_read=56`、`index_only=1714`、`needs_review=240`、`exclude_non_main=1`。
- 论文证据矩阵行：`49` 论文级deep-read锚点。奖励行被合并到匹配的paper evidence中，而不是重复。
- 2016-2020 仍然是partial，因为此过程使用代表性的锚行而不是完整的 DAC 接受的论文导出。
- 2026 仍为 `normal_2026_partial`：该活动原定于 2026 年 7 月 26 日至 2026 年 7 月 29 日举行，因此最终程序、DOI 和奖项结果预计不会在 2026 年 6 月 27 日公布。
- 读取深度是保守的。大多数证据是`official_page`或`doi_metadata`； full-PDF 读取未 claim。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="DAC-SF01"></a>[DAC-SF01](#DAC-SF01) | AI-for-EDA 收敛预测和优化 | 预测/优化时序、时钟/数据、逻辑、热点、STA 和设计收敛 | EDA 图、时序路径、布尔网络和物理设计收敛 | QoR 可预测性和收敛搜索 | GNN、强化学习、LLM 辅助推理、符号推理 | 2019,2023 | venue_provisional；evidence rows：3 |
| <a id="DAC-SF02"></a>[DAC-SF02](#DAC-SF02) | LLM 辅助芯片设计和验证工作流程 | 使用 LLM 进行 RTL 修复、CPU 设计、断言、布局/热点检测和 DSE | RTL， SVA/断言、CPU 设计、布局和 HLS 工作流程 | 手动调试、验证和搜索成本 | LLM 修复/生成、RTL 基础数据合成、设计数据提示 | 2024,2026 | venue_provisional；evidence rows：4 |
| <a id="DAC-SF03"></a>[DAC-SF03](#DAC-SF03) | Transformer/LLM 推理量化和注意力加速 | 降低 Transformer/LLM 推理中的精度、softmax、注意力和 KV/内存成本 | Transformer/LLM 推理和注意力内核 | 内存流量、精度质量权衡、KV/注意力状态 | 混合精度、量化、稀疏注意力、softmax 协同设计、概率估计 | 2021,2022,2024,2026 | venue_provisional；evidence rows：9 |
| <a id="DAC-SF04"></a>[DAC-SF04](#DAC-SF04) | PIM 和近内存 AI 数据移动 | 将计算或调度移至更靠近内存的 NN/LLM/搜索 workload | DNN 训练/推理、LLM 注意力/KV、 ANNS/search | 片外带宽、内存管理、数据移动能量 | ReRAM/忆阻器 PIM、HBM-PIM、3D DRAM-逻辑绑定、存储内推测 | 2017,2018,2025,2026 | venue_provisional；evidence rows：8 |
| <a id="DAC-SF05"></a>[DAC-SF05](#DAC-SF05) | NeRF 和高斯渲染加速 | 通过更改数据流、光栅化、排序和混合来加速神经渲染和高斯泼溅训练/渲染 | NeRF、3DGS 和 4DGS | 排序/混合成本、高斯瓦片对增长、内存局部性、流状态 | 近内存训练、光栅化器扩展、瓦片分组、深度推测、GEMM 兼容混合、时间排序重用 | 2023,2025,2026 | venue_provisional；evidence rows：11 |
| <a id="DAC-SF06"></a>[DAC-SF06](#DAC-SF06) | HLS，硬件生成和设计空间探索 | 将高级模型/IR/DSL/HLS 代码转换为 PPA 和资源限制下的加速器实现 | HLS 内核、FPGA 加速器、加速器生成器 | 设计空间大小、综合/搜索成本、QoR 可预测性 | 生成器堆栈、GNN 性能预测、LLM 引导 DSE、控制/数据访问优化 | 2016,2022,2025,2026 | venue_provisional；evidence rows：5 |
| <a id="DAC-SF07"></a>[DAC-SF07](#DAC-SF07) | 物理设计、时序和布局收敛 | 规模和物理约束下的紧密布局、布线、静态时序和 3D 布局规划 | 布局、时序、布线、布局和布局规划 | 时序收敛、拥塞、签核运行时间、3D 约束 | GPU STA，分析/可微布局、图形模型、Laguerre-Voronoi 布局规划 | 2024,2026 | venue_provisional；evidence rows：4 |
| <a id="DAC-SF08"></a>[DAC-SF08](#DAC-SF08) | 小芯片、2.5D/3DIC 和封装感知协同设计 | 设计多芯片/封装系统，同时考虑成本、良率、散热、互连和布局耦合 | 小芯片、3D 存储器、中介层和晶圆级系统 | 成本/良率/热/互连/布局耦合 | 成本模型，3D布局、混合键合、chiplet-CIM、晶圆级建模 | 2022,2025 | venue_provisional；evidence rows：3 |
| <a id="DAC-SF09"></a>[DAC-SF09](#DAC-SF09) | 安全、形式验证和芯片生命周期 | 降低硬件系统中的安全、信任、验证和生命周期风险 | 信任根、RTL/形式验证、机密计算、ML 隐私 | 证明可扩展性、错误暴露、信任和数据遗忘保证 | 形式验证、隐私保护编译器流程、信任根设计 | 2020,2022 | venue_provisional；evidence rows：2 |
| <a id="DAC-SF10"></a>[DAC-SF10](#DAC-SF10) | 自治嵌入式和实时系统 | 跟踪 DAC 内的嵌入式/CPS 实时和边缘系统约束，但尚未选择足够的深读证据 | 嵌入式 CPS、自治系统和边缘 AI | 实时、功率、可靠性和调度约束 | 运行时适应、异构感知调度、模型压缩 | 2021-2026 index_only 信号 | insufficient_evidence；evidence rows：0 |

## 3. 小领域深读

### [DAC-SF01](#DAC-SF01)。 AI-for-EDA 收敛预测和优化

- 研究问题：预测/优化时序、时钟/数据、逻辑、热点、STA 和设计收敛。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：3 个选定的paper evidence rows；活跃年份：2019、2023。
- 方法谱系：GNN、强化学习、LLM 辅助推理、符号推理。
- 代表论文：[DAC-2019-P2003](../../10_corpus/DAC/id_index.md#DAC-2019-P2003) Machine Learning-Based Pre-Routing Timing Prediction with Reduced Pessimism (2019)； [DAC-2023-P0105](../../10_corpus/DAC/id_index.md#DAC-2023-P0105) Gamora：基于图学习的大规模布尔网络符号推理（2023）； [DAC-2023-P0212](../../10_corpus/DAC/id_index.md#DAC-2023-P0212) RL-CCD：使用基于注意力的自监督强化学习进行并发时钟和数据优化（2023）
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 是 EDA 图表、时序路径、布尔网络和物理设计收敛。artifact/代码状态摘要：none_found_in_corpus=3。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF02](#DAC-SF02)。 LLM 辅助芯片设计和验证工作流程

- 研究问题：使用LLM进行 RTL 修复、CPU 设计、断言、布局/热点检测和 DSE。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：4 个选定的paper evidence rows；活跃年份：2024、2026。
- 方法谱系：LLM 修复/生成、RTL 基础数据合成、设计数据提示。
- 代表论文：[DAC-2024-P0037](../../10_corpus/DAC/id_index.md#DAC-2024-P0037) Automatically Fixing RTL Syntax Errors with Large Language Model (2024)； [DAC-2024-P0055](../../10_corpus/DAC/id_index.md#DAC-2024-P0055) ChatCPU：采用 LLM 的敏捷 CPU 设计和验证平台（2024 年）； [DAC-2024-P0194](../../10_corpus/DAC/id_index.md#DAC-2024-P0194) LLM-HD：使用 GDS 语义编码进行热点检测的布局语言模型（2024）； [DAC-2026-P0476](../../10_corpus/DAC/id_index.md#DAC-2026-P0476) Svacoder：通过 RTL 接地双向数据合成训练专门的 LLM 生成硬件断言 (2026)
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 为 RTL、SVA/断言、CPU 设计、布局和 HLS 工作流程。artifact/代码状态摘要：needs_review=3、none_found_in_corpus=1。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF03](#DAC-SF03)。 Transformer/LLM 推理量化和注意力加速

- 研究问题：降低 Transformer/LLM 推理中的精度、softmax、注意力和 KV/内存成本。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：9 个选定的paper evidence rows；活跃年份：2021、2022、2024、2026。
- 方法谱系：混合精度、量化、稀疏注意力、softmax 协同设计、概率估计。
- 代表论文：[DAC-2021-P0056](../../10_corpus/DAC/id_index.md#DAC-2021-P0056) Dancing around Battery: Enabling Transformer with Run-time Reconfigurability on Mobile Devices (2021)； [DAC-2021-P0088](../../10_corpus/DAC/id_index.md#DAC-2021-P0088) Gemmini：通过全栈集成实现系统深度学习架构评估（2021）； [DAC-2021-P0186](../../10_corpus/DAC/id_index.md#DAC-2021-P0186) Softermax：Transformer高效 Softmax 的硬件/软件协同设计（2021）； [DAC-2022-P0132](../../10_corpus/DAC/id_index.md#DAC-2022-P0132) NN-LUT：用于高效Transformer推理的非线性运算的神经逼近（2022）； [DAC-2022-P0170](../../10_corpus/DAC/id_index.md#DAC-2022-P0170) SALO：一种高效的空间加速器，支持长序列的混合稀疏注意力机制（2022）； [DAC-2024-P0032](../../10_corpus/DAC/id_index.md#DAC-2024-P0032) APTQ：大型语言模型的注意感知训练后混合精度量化（2024）； [DAC-2024-P0231](../../10_corpus/DAC/id_index.md#DAC-2024-P0231) OPAL：用于生成大型语言模型的离群值保留微尺度量化加速器（2024）； [DAC-2024-P0308](../../10_corpus/DAC/id_index.md#DAC-2024-P0308) Token-Picker：通过概率估计最小化内存传输加速文本生成中的注意力（2024）； [DAC-2026-P0119](../../10_corpus/DAC/id_index.md#DAC-2026-P0119) Crystal-KV：通过答案优先原则对思想链 LLM 进行高效 KV 缓存管理 (2026)
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 是 Transformer/LLM 推理和注意力内核。artifact/代码状态摘要：none_found_in_corpus=9、code_available_official_claim_needs_reuse_check=1。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF04](#DAC-SF04)。 PIM 和近内存 AI 数据移动

- 研究问题：将 NN/LLM/搜索 workload 的计算或调度移至更靠近内存的位置。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：8 个选定的paper evidence rows；活跃年份：2017、2018、2025、2026。
- 方法谱系：ReRAM/忆阻器 PIM、HBM-PIM、3D DRAM 逻辑绑定、存储内推测。
- 代表论文：[DAC-2017-P2001](../../10_corpus/DAC/id_index.md#DAC-2017-P2001) TIME: A Training-in-memory Architecture for Memristor-based Deep Neural Networks (2017)； [DAC-2018-P2002](../../10_corpus/DAC/id_index.md#DAC-2018-P2002) CMP-PIM：一种基于节能比较器的内存处理神经网络加速器（2018）； [DAC-2025-P0006](../../10_corpus/DAC/id_index.md#DAC-2025-P0006) 3D-TokSIM：使用令牌固定内存计算堆叠 3D 内存，以实现推测性 LLM 推理 (2025)； [DAC-2025-P0056](../../10_corpus/DAC/id_index.md#DAC-2025-P0056) AttenPIM：在内存处理中使用双模式 GEMV 加速 LLM 注意力（2025）； [DAC-2025-P0069](../../10_corpus/DAC/id_index.md#DAC-2025-P0069) BlockPIM：优化支持 PIM 的长上下文 LLM 推理的内存管理 (2025)； [DAC-2025-P0256](../../10_corpus/DAC/id_index.md#DAC-2025-P0256) McPAL：利用适用于LLM的多芯片 HBM-PIM 架构扩展非结构化稀疏推理 (2025)； [DAC-2025-P0281](../../10_corpus/DAC/id_index.md#DAC-2025-P0281) 近内存 LLM 基于 3D DRAM 到逻辑混合接合的推理处理器 (2025)； [DAC-2026-P0459](../../10_corpus/DAC/id_index.md#DAC-2026-P0459) SpecANNS：通过推测存储内计算加速基于图的近似最近邻搜索 (2026)
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 为 DNN 训练/推理、LLM 注意力/KV、ANNS/搜索。artifact/代码状态摘要：none_found_in_corpus=8。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF05](#DAC-SF05)。 NeRF 和高斯渲染加速

- 研究问题：通过改变数据流、光栅化、排序和混合来加速神经渲染和高斯泼溅训练/渲染。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：11 个选定的paper evidence rows；活跃年份：2023、2025、2026。
- 方法谱系：近内存训练、光栅化器扩展、切片分组、深度推测、GEMM 兼容混合、时间排序重用。
- 代表论文：[DAC-2023-P0131](../../10_corpus/DAC/id_index.md#DAC-2023-P0131) Instant-NeRF：通过算法加速器联合设计的近内存处理进行即时设备上神经辐射场训练（2023）； [DAC-2025-P0174](../../10_corpus/DAC/id_index.md#DAC-2025-P0174) GauRast：增强 GPU 三角形光栅器以加速 3D 高斯泼溅 (2025)； [DAC-2025-P0190](../../10_corpus/DAC/id_index.md#DAC-2025-P0190) GS-TG：具有平铺分组功能的 3D 高斯泼溅加速器，可在保持光栅化效率的同时减少冗余排序（2025）； [DAC-2025-P0191](../../10_corpus/DAC/id_index.md#DAC-2025-P0191) GSAcc：通过深度推测和以高斯为中心的光栅化加速 3D 高斯泼溅 (2025)； [DAC-2025-P0242](../../10_corpus/DAC/id_index.md#DAC-2025-P0242) Local-GS：利用 Splat 局部性的与阶数无关的高斯 Splatting 训练加速器（2025）； [DAC-2025-P0378](../../10_corpus/DAC/id_index.md#DAC-2025-P0378) StreamingGS：具有内存优化和架构支持的基于体素的流式 3D 高斯分布（2025）； [DAC-2026-P0023](../../10_corpus/DAC/id_index.md#DAC-2026-P0023) Adagscale：3D 高斯泼溅中的视点自适应高斯缩放以减少高斯平铺对（2026）； [DAC-2026-P0216](../../10_corpus/DAC/id_index.md#DAC-2026-P0216) GEMM-GS：通过 GEMM 兼容混合加速张量核心上的 3D 高斯泼溅 (2026)； [DAC-2026-P0265](../../10_corpus/DAC/id_index.md#DAC-2026-P0265) 2D 高斯足够了吗？具有几何指导的无排序 3D 高斯泼溅推理架构 (2026)； [DAC-2026-P0375](../../10_corpus/DAC/id_index.md#DAC-2026-P0375) Pipegs：通过分层重用和动态分区解锁 3DGS 管道并行性 (2026)； [DAC-2026-P0404](../../10_corpus/DAC/id_index.md#DAC-2026-P0404) Relay-GS：重用时间排序信息进行 4D 高斯泼溅加速 (2026)
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 为 NeRF、3DGS 和 4DGS。artifact/代码状态摘要：none_found_in_corpus=11。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF06](#DAC-SF06)。 HLS，硬件生成和设计空间探索

- 研究问题：在 PPA 和资源限制下将高级模型/IR/DSL/HLS 代码转化为加速器实现。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：5 个选定的paper evidence rows；活跃年份：2016、2022、2025、2026。
- 方法谱系：生成器堆栈、GNN 性能预测、LLM 引导的 DSE、控制/数据访问优化。
- 代表论文：[DAC-2016-P2000](../../10_corpus/DAC/id_index.md#DAC-2016-P2000) DeepBurning：自动生成基于 FPGA 的神经网络家族学习加速器（2016）； [DAC-2022-P0108](../../10_corpus/DAC/id_index.md#DAC-2022-P0108) 使用 GNN 进行高级综合性能预测：基准测试、建模和推进（2022 年）； [DAC-2025-P0077](../../10_corpus/DAC/id_index.md#DAC-2025-P0077) Cayman：具有控制流和数据访问优化的自定义加速器生成（2025）； [DAC-2026-P0093](../../10_corpus/DAC/id_index.md#DAC-2026-P0093) CHiRM-DSE：用于 FPGA 加速器的基于 CodeLLM 的分层和规则挖掘引导的 DSE (2026)； [DAC-2026-P0350](../../10_corpus/DAC/id_index.md#DAC-2026-P0350) Paretopilot：使用LLM进行 HLS 设计空间探索的全局优化推理 (2026)
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 是 HLS 内核、FPGA 加速器、加速器生成器。artifact/代码状态摘要：none_found_in_corpus=2、needs_review=2。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF07](#DAC-SF07)。物理设计、时序和布局收敛

- 研究问题：规模和物理约束下的紧密布局、布线、静态时序和 3D 布局规划。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：4 个选定的paper evidence rows；活跃年份：2024、2026。
- 方法谱系：GPU STA、分析/可微分放置、图形模型、Laguerre-Voronoi 布局规划。
- 代表论文：[DAC-2024-P0211](../../10_corpus/DAC/id_index.md#DAC-2024-P0211) Mixed-Size 3D Analytical Placement with Heterogeneous Technology Nodes (2024)； [DAC-2024-P0282](../../10_corpus/DAC/id_index.md#DAC-2024-P0282) SkyPlace：使用基于模块化的集群和 SDP 松弛的新混合大小放置框架（2024）； [DAC-2026-P0530](../../10_corpus/DAC/id_index.md#DAC-2026-P0530) Warp-STAR：高性能、可微分的 GPU - 通过面向 Warp 的并行编排加速静态时序分析 (2026)； [DAC-2026-P0535](../../10_corpus/DAC/id_index.md#DAC-2026-P0535) 采用压力驱动正交 Laguerre-Voronoi 曲面细分的无空白直线 3D 布局规划 (POLT) (2026)
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 是布局、时序、路由、布局和布局规划。artifact/代码状态摘要：none_found_in_corpus=3、needs_review=1。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF08](#DAC-SF08)。 Chiplet、2.5D/3DIC 和封装感知协同设计

- 研究问题：设计多芯片/封装系统，同时考虑成本、良率、散热、互连和布局耦合。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：3 个选定的paper evidence rows；活跃年份：2022、2025。
- 方法谱系：成本模型、3D 布局、混合键合、chiplet-CIM、晶圆级建模。
- 代表论文：[DAC-2022-P0044](../../10_corpus/DAC/id_index.md#DAC-2022-P0044) Chiplet Actuary: A Quantitative Cost Model and Multi-Chiplet Architecture Exploration (2022)； [DAC-2025-P0003](../../10_corpus/DAC/id_index.md#DAC-2025-P0003) 3D-CIMlet：用于边缘异构内存加速的 Chiplet 协同设计框架 LLM 推理和持续学习（2025）； [DAC-2025-P0211](../../10_corpus/DAC/id_index.md#DAC-2025-P0211) Hydra：利用专家人气在 Chiplet 系统上进行高效的专家混合推理 (2025)
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 是 Chiplet、3D 内存、中介层和晶圆级系统。artifact/代码状态摘要：none_found_in_corpus=2、needs_review=1。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF09](#DAC-SF09)。安全、形式验证和芯片生命周期

- 研究问题：降低硬件系统中的安全、信任、验证和生命周期风险。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：2 个选定的paper evidence rows；活跃年份：2020、2022。
- 方法谱系：形式验证、隐私保护编译器流程、信任根设计。
- 代表论文：[DAC-2020-P2004](../../10_corpus/DAC/id_index.md#DAC-2020-P2004) AHEC: End-to-end Compiler Framework for Privacy-preserving Machine Learning Acceleration (2020)； [DAC-2022-P0202](../../10_corpus/DAC/id_index.md#DAC-2022-P0202) 迈向数据不经意计算的正式验证硬件信任根 (2022)
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 是信任根、RTL/正式验证、机密计算、ML 隐私。artifact/代码状态摘要：needs_review=1、none_found_in_corpus=1。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

### [DAC-SF10](#DAC-SF10)。自主嵌入式和实时系统

- 研究问题：跟踪 DAC 内的嵌入式/CPS 实时和边缘系统约束，但尚未选择足够的深读证据。
- 背景：这是一个 DAC-local 小领域标签。这不是全球分类升级。
- 本 venue 的当前状态：0 个选定的paper evidence rows；活跃年份：仅限指数覆盖。
- 方法谱系：运行时适应、异构感知调度、模型压缩。
- 代表性论文：本次未评选出论文级深读代表性论文。
- 团队线索：作者字符串记录在证据矩阵中，其中 DOI/官方元数据可用；不进行团队排名或实体合并。
- workload/artifact 信号：workload 是嵌入式 CPS、自治系统和边缘 AI。artifact/代码状态摘要：无。
- 开放问题：PDF 级方法提取、artifact/代码重用、引文结构和cross-venue比较仍然开放，除非单独验证。

## 4. 发展趋势

- AI-for-EDA 闭合和 LLM 辅助设计在 [DAC-2019-P2003](../../10_corpus/DAC/id_index.md#DAC-2019-P2003)、[DAC-2023-P0105](../../10_corpus/DAC/id_index.md#DAC-2023-P0105)、[DAC-2023-P0212](../../10_corpus/DAC/id_index.md#DAC-2023-P0212)、[DAC-2024-P0037](../../10_corpus/DAC/id_index.md#DAC-2024-P0037)、[DAC-2024-P0055](../../10_corpus/DAC/id_index.md#DAC-2024-P0055)、[DAC-2024-P0194](../../10_corpus/DAC/id_index.md#DAC-2024-P0194)、[DAC-2026-P0093](../../10_corpus/DAC/id_index.md#DAC-2026-P0093)、[DAC-2026-P0350](../../10_corpus/DAC/id_index.md#DAC-2026-P0350) 上可见， [DAC-2026-P0476](../../10_corpus/DAC/id_index.md#DAC-2026-P0476) 和 [DAC-2026-P0530](../../10_corpus/DAC/id_index.md#DAC-2026-P0530)。这是从预测/图形模型到 LLM 辅助设计和验证的venue级趋势，而不是全球稳定的分类学主张。
- LLM DAC 中的推理加速分为量化/注意力/KV 工作和以内存为中心的 PIM 工作。证据包括 [DAC-2021-P0186](../../10_corpus/DAC/id_index.md#DAC-2021-P0186)、[DAC-2022-P0132](../../10_corpus/DAC/id_index.md#DAC-2022-P0132)、[DAC-2022-P0170](../../10_corpus/DAC/id_index.md#DAC-2022-P0170)、[DAC-2024-P0032](../../10_corpus/DAC/id_index.md#DAC-2024-P0032)、[DAC-2024-P0231](../../10_corpus/DAC/id_index.md#DAC-2024-P0231)、[DAC-2024-P0308](../../10_corpus/DAC/id_index.md#DAC-2024-P0308)、[DAC-2025-P0056](../../10_corpus/DAC/id_index.md#DAC-2025-P0056)、[DAC-2025-P0069](../../10_corpus/DAC/id_index.md#DAC-2025-P0069)、[DAC-2025-P0256](../../10_corpus/DAC/id_index.md#DAC-2025-P0256)、[DAC-2025-P0281](../../10_corpus/DAC/id_index.md#DAC-2025-P0281) 和 [DAC-2026-P0119](../../10_corpus/DAC/id_index.md#DAC-2026-P0119)。
- NeRF/3DGS/4DGS 加速是跨 [DAC-2023-P0131](../../10_corpus/DAC/id_index.md#DAC-2023-P0131)、五个 2025 3DGS 行和五个部分 2026 高斯分布行的直接 DAC 前沿信号。由于引用/采用/人工证据仍然薄弱，而且 2026 年是partial，因此这并没有被写为成熟的影响。
- Chiplet/3DIC 和物理设计行通过 [DAC-2022-P0044](../../10_corpus/DAC/id_index.md#DAC-2022-P0044)、[DAC-2024-P0211](../../10_corpus/DAC/id_index.md#DAC-2024-P0211)、[DAC-2025-P0003](../../10_corpus/DAC/id_index.md#DAC-2025-P0003)、[DAC-2025-P0211](../../10_corpus/DAC/id_index.md#DAC-2025-P0211)、[DAC-2026-P0530](../../10_corpus/DAC/id_index.md#DAC-2026-P0530) 和 [DAC-2026-P0535](../../10_corpus/DAC/id_index.md#DAC-2026-P0535) 将封装约束链接到加速器和内存。

## 5. 方法变化

- 早期的锚点涵盖加速器生成、PIM/内存中神经计算、隐私保护 ML 加速和时序预测。最近的行越来越多地将 LLM/GNN/RL 与设计收敛、验证、HLS/DSE 和加速器映射结合起来。
- 渲染加速从近内存 NeRF 训练转移到显式 3DGS 机制：光栅化器扩展、图块分组、深度推测、位置感知训练、流内存支持、GEMM 兼容混合、管道分区和时间排序重用。
- 以内存为中心的 AI 从忆阻器/ReRAM 和通用 PIM 锚点转向注意力、长上下文内存管理、HBM-PIM、3D DRAM 逻辑绑定和存储内搜索。

## 6. 缺失来源

- 完整的 DAC 2016-2020 标题/作者/DOI 从 ACM DL、DBLP 或官方程序 PDF 导出。
- Canonical 2025 DAC 奖项来源。 SIGDA 辅助材料提供了提名者线索，但在此通行证中未找到官方 DAC/IEEE/ACM 获奖者页面。
- DOI/DAC 2026 结束后部分 2026 行的会议记录元数据。
- PDF 级方法提取和 Gemmini、RTLFixer/ChatCPU 式工具、3DGS 加速器、PIM/LLM 系统和 HLS/DSE 框架的 artifact/代码检查。
- 证据矩阵中记录的所选 OpenAlex 信号之外的引用/采用审核。
- 针对 ICCAD、DATE、ASP-DAC、FPGA/FCCM/FPL/FPT 和architecture venues 的 cross-venue evidence matrix。
