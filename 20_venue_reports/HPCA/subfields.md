# HPCA 小领域深读

## 1. 范围与语料

- Venue：`HPCA` / IEEE 高性能计算机体系结构国际研讨会。
- 语料库：`876` `papers.csv` 行和 `23` `awards.csv` 行。
- 筛选矩阵：`899` 行。决策：`deep_read=100`、`index_only=658`、`needs_review=141`。
- 论文证据矩阵：`77` 已接受的论文锚点。 23 个award rows仍在筛选中作为源证据； 11 个时间测试行是历史/超出范围的，不被视为 2016-2026 年论文deep-read。
- 来源深度：DBLP/DOI/IEEE URL、HPCA 官方程序、TCCA/TCCA 博客/SIGARCH 奖项来源、subagent和parent agent检查提供的精选 arXiv/Semantic Scholar/OpenAlex/Crossref 信号。
- 引用/采用/artifact 数据仅是首次通过信号。证据矩阵中的计数包括检索日期 `2026-06-27`。引用计数并不单独用作影响力证明。
- 2026 仍然是 `partial`：官方计划行已存在，但许多 DOI/proceedings/PDF/artifact/award 结果仍然不完整。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="HPCA-SF01"></a>[HPCA-SF01](#HPCA-SF01) | PIM/NDP 用于图形和不规则数据移动 | 通过将图形、GNN 或不规则执行移动到更靠近内存/存储的位置来减少随机访问和通信成本。 | 图、GNN、稀疏和数据间接 workload | 间接延迟、通信量、负载不平衡、存储/内存移动 | 指令级 PIM 卸载、图分区、in-SSD 训练、硬件/软件协同设计 | 2017;2018;2021;2024;2026 | venue_provisional；evidence rows：5 |
| <a id="HPCA-SF02"></a>[HPCA-SF02](#HPCA-SF02) | 注意力和LLM 服务/状态加速 | 管理 Transformer/LLM workload 的注意力、KV/状态流量、长上下文、批处理和服务能量。 | 注意力、Transformer、LLM 推理/训练、RAG、视频 LLM、无服务器服务 | KV 缓存、内存容量、长上下文带宽、尾部延迟、调度、能量 | 近似/稀疏注意力、PIM/PNM/存储卸载、调度、量化、资源分区 | 2020;2021;2022;2023;2024;2025;2026 | venue_provisional；evidence rows：23 |
| <a id="HPCA-SF03"></a>[HPCA-SF03](#HPCA-SF03) | 异构内存带宽和 CXL/一致性 | 协调异构内存带宽、DIMM 间通信、CXL 一致性和安全/可靠 CXL 内存。 | 服务器/内存密集型 workload、近内存系统、CXL 异构内存 | 带宽分区、内存容量、一致性、扩展内存的安全性/可靠性 | 访问分区、DIMM 链路、CXL 一致性控制器、全系统模拟、安全 CXL 内存 | 2017;2023;2025;2026 | venue_provisional；evidence rows：5 |
| <a id="HPCA-SF04"></a>[HPCA-SF04](#HPCA-SF04) | 内存系统工具和 PIM/NDP 基础设施 | 为 DRAM/PIM/NDP 研究提供可重用平台、模拟器、分配器或接口。 | DRAM 实验、商业 PIM、近 DRAM 处理、PIM 运行时、内存中执行 | 工具可用性、实验保真度、运行时分配、可重复评估 | 开源 DRAM 基础设施、商业 PIM 表征、编译器/模拟器、 PIM 分配器、MPU 接口 | 2017;2024;2025;2026 | venue_provisional；evidence rows：5 |
| <a id="HPCA-SF05"></a>[HPCA-SF05](#HPCA-SF05) | 早期 ML 加速器和加速器模板 | 将 Transformer 之前的机器学习内核映射到专用加速器或模板框架。 | 玻尔兹曼机、统计 ML、早期 DNN/稀疏 GEMM 加速器 | 数据流模板选择、稀疏执行、ML 内核的硬件专业化 | 忆阻加速器、基于模板的框架、稀疏 GEMM 灵活互连 | 2016;2020 | venue_provisional；evidence rows：3 |
| <a id="HPCA-SF06"></a>[HPCA-SF06](#HPCA-SF06) | 图形、VR、3DGS 和神经渲染加速 | 减少实时图形和神经渲染管道的渲染/SLAM/3DGS 延迟和内存流量。 | 3D 渲染，VR，基于高斯的渲染，3DGS 训练/渲染/SLAM | 纹理/内存流量、冗余图块、混合不平衡、光线遍历、移动 SLAM 延迟 | PIM 图形、可见性分辨率、图块消除、高斯混合单元、混合并行、稀疏处理 | 2017;2018;2019;2023;2025;2026 | venue_provisional；evidence rows：14 |
| <a id="HPCA-SF07"></a>[HPCA-SF07](#HPCA-SF07) | FPGA/HLS 映射和软硬件协同设计 | 使用 FPGA/HLS/可重新配置的硬件来消除特定于 workload 的性能、资源和验证瓶颈。 | OpenCL FPGA、RNN/DNN 量化、稀疏 GEMM、FHE、图形随机游走、硬件模糊 | 资源利用率、管道平衡、云部署、加密计算成本、验证吞吐量 | OpenCL 性能分析、FPGA 加速器数据路径、MLIR/HLS 框架、流式处理管道、FPGA 模糊测试 | 2016;2019;2021;2023;2024;2026 | venue_provisional；evidence rows：11 |
| <a id="HPCA-SF08"></a>[HPCA-SF08](#HPCA-SF08) | 数据中心 QoS、分配和无服务器控制 | 平衡共享数据中心/无服务器系统中的公平性、吞吐量、尾部延迟和能源。 | 数据中心分配、共置 SMT workload、无服务器 LLM 推理 | 公平分配、QoS 干扰、尾部延迟、资源分区、能源 | 市场分配、QoS/吞吐量控制、节流、阶段感知调度、无服务器分区 | 2018;2019 | venue_provisional；evidence rows：2 |
| <a id="HPCA-SF09"></a>[HPCA-SF09](#HPCA-SF09) | 安全性、RowHammer、可靠性和正确性 | 暴露或减轻架构漏洞、RowHammer 效应、CXL 内存风险和验证瓶颈。 | RowHammer、微架构漏洞、安全内存、硬件模糊测试 | 攻击面、缓解开销、完整性、可靠的扩展内存、验证覆盖率 | 行交换缓解、漏洞分析、安全 CXL 内存、FPGA 加速模糊测试 | 2023;2024;2026 | venue_provisional；evidence rows：4 |
| <a id="HPCA-SF10"></a>[HPCA-SF10](#HPCA-SF10) | 基准测试、分析和模拟方法 | 通过模拟器、基准测试套件、功率测量和 workload 表征使架构 claim 具有可比性。 | 微架构模拟、量子基准测试、MLPerf Power、量子模拟、云原生 LLM 表征 | 测量保真度、workload 代表性、再现性、功耗规模、模拟成本 | 实时模拟、基准测试套件、能源基准测试、全栈加速方法、workload 表征 | 2016;2022;2025;2026 | venue_provisional；evidence rows：5 |

## 3. 小领域深读

### [HPCA-SF01](#HPCA-SF01)。 PIM/NDP 用于图形和不规则数据移动

- 研究问题：通过将图形、GNN 或不规则执行移动到更靠近内存/存储的位置来减少随机访问和通信成本。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`5` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：指令级 PIM 卸载、图形分区、in-SSD 训练、硬件/软件协同设计。
- 代表论文：[HPCA-2017-P0026](../../10_corpus/HPCA/id_index.md#HPCA-2017-P0026) GraphPIM: Enabling instructions-Level PIM Offloading in GraphComputing Frameworks (2017)； [HPCA-2018-P0028](../../10_corpus/HPCA/id_index.md#HPCA-2018-P0028) GraphP：通过高效数据分区减少基于 PIM 的图形处理的通信（2018）； [HPCA-2021-P0053](../../10_corpus/HPCA/id_index.md#HPCA-2021-P0053) Prodigy：使用硬件-软件协同设计改善数据间接不规则 workload 的内存延迟（2021）； [HPCA-2024-P0030](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0030) FlashGNN：用于 GNN 训练的 In-SSD 加速器（2024 年）； [HPCA-2026-P0013](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0013) AutoGNN：用于增强 GNN 性能的端到端硬件驱动图形预处理 (2026)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF02](#HPCA-SF02)。注意力和 LLM 服务/状态加速

- 研究问题：管理注意力、KV/状态流量、长上下文、Transformer/LLM workload 的批处理和服务能量。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`23` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：近似/稀疏注意力、PIM/PNM/存储卸载、调度、量化、资源分区。
- 代表论文：[HPCA-2020-P0004](../../10_corpus/HPCA/id_index.md#HPCA-2020-P0004) A3：Accelerate Attention Mechanisms in Neural Networks with Approximation (2020)； [HPCA-2020-P0044](../../10_corpus/HPCA/id_index.md#HPCA-2020-P0044) PREMA：可抢占式神经处理单元的预测多任务调度算法（2020）； [HPCA-2021-P0061](../../10_corpus/HPCA/id_index.md#HPCA-2021-P0061) SpAtten：具有级联令牌和头部修剪的高效稀疏注意力架构（2021）； [HPCA-2022-P0083](../../10_corpus/HPCA/id_index.md#HPCA-2022-P0083) TransPIM：通过软硬件协同设计为 Transformer 实现基于内存的加速（2022 年）； [HPCA-2023-P0023](../../10_corpus/HPCA/id_index.md#HPCA-2023-P0023) CTA：压缩令牌注意力机制的软硬件协同设计（2023）； [HPCA-2024-P0005](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0005) 一个基于 LPDDR 的 CXL-PNM 平台，用于基于 Transformer 的大型语言模型的 TCO 高效推理（2024）； [HPCA-2024-P0008](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0008) ASADI：使用基于对角线的原位计算加速稀疏注意力（2024）； [HPCA-2024-P0066](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0066) Smart-Infinity：在真实系统上使用近存储处理进行快速大型语言模型训练（2024）； [HPCA-2024-P0080](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0080) 释放 PIM 的潜力：加速基于 Transformer 的生成模型的大批量推理（2024）； [HPCA-2025-P0031](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0031) DynamoLLM：设计 LLM 推理集群以提高性能和能源效率（2025 年）； [HPCA-2025-P0044](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0044) FACIL：用于 SoC-PIM 协作式设备上 LLM 推理的灵活 DRAM 地址映射 (2025)； [HPCA-2025-P0059](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0059) InstAttention：存储内注意力卸载，实现经济高效的长上下文 LLM 推理 (2025)； [HPCA-2025-P0067](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0067) Lincoln：使用 LPDDR 接口、支持计算的闪存对消费设备进行实时 50~100B LLM 推理 (2025)； [HPCA-2025-P0085](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0085) PAISE：PIM-基于 Transformer 的加速推理调度引擎 LLM (2025)；加上证据矩阵
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF03](#HPCA-SF03) 中的 9 行。异构内存带宽和 CXL/coherence

- 研究问题：协调异构内存带宽、DIMM 间通信、CXL 一致性和安全/可靠的 CXL 内存。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`5` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：访问分区、DIMM 链接、CXL 一致性控制器、全系统模拟、安全 CXL 内存。
- 代表论文：[HPCA-2017-P0034](../../10_corpus/HPCA/id_index.md#HPCA-2017-P0034) Near-Optimal Access Partitioning for Memory Hierarchies with Multiple Heterogeneous Bandwidth Sources (2017)； [HPCA-2023-P0027](../../10_corpus/HPCA/id_index.md#HPCA-2023-P0027) DIMM-Link：为近内存处理实现高效的 DIMM 间通信（2023）； [HPCA-2025-P0010](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0010) AsyncDIMM：在基于 DIMM 的近内存处理中实现异步执行 (2025)； [HPCA-2026-P0001](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0001) $C^3$：CXL 异构架构一致性控制器（2026）； [HPCA-2026-P0022](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0022) Cohet：具有硬件校准全系统模拟的 CXL 驱动的一致性异构计算框架 (2026)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF04](#HPCA-SF04)。内存系统工具和 PIM/NDP 基础设施

- 研究问题：为 DRAM/PIM/NDP 研究提供可重用平台、模拟器、分配器或接口。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`5` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：开源 DRAM 基础设施、商业 PIM 表征、编译器/模拟器、PIM 分配器、MPU 接口。
- 代表论文：[HPCA-2017-P0046](../../10_corpus/HPCA/id_index.md#HPCA-2017-P0046) SoftMC：一种灵活实用的开源基础设施，用于实现实验性 DRAM 研究（2017）； [HPCA-2024-P0055](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0055) 通过揭秘商业 PIM 技术探路未来 PIM 架构 (2024)； [HPCA-2025-P0114](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0114) UniNDP：用于近 DRAM 处理架构的统一编译和仿真工具（2025）； [HPCA-2026-P0076](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0076) PIM-malloc：用于内存处理 (PIM) 架构的快速且可扩展的动态内存分配器 (2026)； [HPCA-2026-P0110](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0110) 内存处理单元：用于端到端内存执行的通用接口 (2026)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF05](#HPCA-SF05)。早期 ML 加速器和加速器模板

- 研究问题：将 Transformer 之前的机器学习内核映射到专用加速器或模板框架。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`3` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：忆阻加速器、基于模板的框架、稀疏 GEMM 灵活互连。
- 代表论文：[HPCA-2016-P0034](../../10_corpus/HPCA/id_index.md#HPCA-2016-P0034) 忆阻玻尔兹曼机：用于组合优化和深度学习的硬件加速器（2016）； [HPCA-2016-P0053](../../10_corpus/HPCA/id_index.md#HPCA-2016-P0053) TABLA：用于加速统计机器学习的基于统一模板的框架（2016）； [HPCA-2020-P0048](../../10_corpus/HPCA/id_index.md#HPCA-2020-P0048) SIGMA：具有灵活互连的稀疏且不规则的 GEMM 加速器，用于 DNN 训练 (2020)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF06](#HPCA-SF06)。图形、VR、3DGS 和神经渲染加速

- 研究问题：减少实时图形和神经渲染管道的渲染/SLAM/3DGS 延迟和内存流量。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`14` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：PIM 图形、可见性分辨率、平铺消除、高斯混合单元、混合并行、稀疏处理。
- 代表论文：[HPCA-2017-P0040](../../10_corpus/HPCA/id_index.md#HPCA-2017-P0040) Processing-in-Memory Enabled Graphics Processors for 3D Rendering (2017)； [HPCA-2018-P0042](../../10_corpus/HPCA/id_index.md#HPCA-2018-P0042) 现代图形处理器的面向感知的 3D 渲染近似（2018）； [HPCA-2019-P0016](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0016) 用于删除图形管道中无效计算的早期可见性解决方案 (2019)； [HPCA-2019-P0036](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0036) PIM-VR：使用定制内存立方体消除高交互虚拟现实世界中的运动异常（2019）； [HPCA-2019-P0045](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0045) 渲染消除：图形管道中冗余图块的早期丢弃（2019）； [HPCA-2023-P0072](../../10_corpus/HPCA/id_index.md#HPCA-2023-P0072) Post0-VR：通过利用架构相似性和数据共享为现代 VR 启用通用逼真渲染（2023）； [HPCA-2025-P0048](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0048) 高斯混合单元：GPU 边缘插件，用于 AR/VR (2025) 中基于实时高斯的渲染； [HPCA-2025-P0053](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0053) GSArch：通过架构支持打破 3D Guassian Splatting 训练中的内存障碍 (2025)； [HPCA-2025-P0113](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0113) Uni-Render：跨不同神经渲染器实时渲染的统一加速器（2025）； [HPCA-2025-P0118](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0118) VR-Pipe：简化体积渲染的硬件图形管道（2025）； [HPCA-2026-P0018](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0018) Cambricon-GS：具有高斯像素混合并行性的 3D 高斯泼溅训练加速器（2026）； [HPCA-2026-P0047](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0047) GRTX：基于 3D 高斯渲染的高效光线追踪 (2026)； [HPCA-2026-P0070](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0070) ORANGE：通过使用 GEMM 友好的混合和平衡 workload 在 NPU 上加速 3DGS，探索 Ockham 剃刀神经渲染（2026 年）； [HPCA-2026-P0099](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0099) Splatonic：通过稀疏处理对 3D 高斯分布 SLAM 的架构支持 (2026)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF07](#HPCA-SF07)。 FPGA/HLS 映射和软硬件协同设计

- 研究问题：使用 FPGA/HLS/可重新配置的硬件来关闭特定于 workload 的性能、资源和验证瓶颈。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`11` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：OpenCL 性能分析、FPGA 加速器数据路径、MLIR/HLS 框架、流管道、FPGA 模糊测试。
- 代表论文：[HPCA-2016-P0007](../../10_corpus/HPCA/id_index.md#HPCA-2016-P0007) A Performance Analysis Framework for Optimization OpenCL applications on FPGAs (2016)； [HPCA-2019-P0015](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0015) E-RNN：FPGA 中高效循环神经网络的设计优化 (2019)； [HPCA-2019-P0024](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0024) FPGA 加速 INDEL 云端调整（2019 年）； [HPCA-2019-P0025](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0025) FPGA 基于加密数据同态计算的高性能并行架构（2019）； [HPCA-2021-P0043](../../10_corpus/HPCA/id_index.md#HPCA-2021-P0043) 混合搭配：一种新颖的 FPGA 以深度神经网络量化框架（2021）； [HPCA-2021-P0057](../../10_corpus/HPCA/id_index.md#HPCA-2021-P0057) 重新审视 FPGA 和低功耗架构的超维度学习 (2021)； [HPCA-2021-P0060](../../10_corpus/HPCA/id_index.md#HPCA-2021-P0060) SPAGHETTI：FPGA 上高度稀疏的流加速器 GEMM (2021)； [HPCA-2023-P0034](../../10_corpus/HPCA/id_index.md#HPCA-2023-P0034) FAB：基于 FPGA 的可引导全同态加密加速器（2023）； [HPCA-2023-P0037](../../10_corpus/HPCA/id_index.md#HPCA-2023-P0037) FxHENN：基于 FPGA 的同态加密 CNN 推理加速框架（2023）； [HPCA-2024-P0006](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0006) MLIR 上的优化框架，用于高效生成基于 FPGA 的加速器（2024 年）； [HPCA-2026-P0088](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0088) RidgeWalker：FPGA 上的完美流水线图随机游走 (2026)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF08](#HPCA-SF08)。数据中心 QoS、分配和无服务器控制

- 研究问题：在共享数据中心/无服务器系统中平衡公平性、吞吐量、尾部延迟和能量。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue当前状态：`2` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：市场分配、QoS/吞吐量控制、节流、阶段感知调度、无服务器分区。
- 代表论文：[HPCA-2018-P0007](../../10_corpus/HPCA/id_index.md#HPCA-2018-P0007) Amdahl's Law in the Datacenter Era: A Market for Fair Processor Allocation (2018)； [HPCA-2019-P0048](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0048) 延伸：平衡 SMT 核心上共置服务器 workload 的 QoS 和吞吐量 (2019)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF09](#HPCA-SF09)。安全性、RowHammer、可靠性和正确性

- 研究问题：暴露或减轻架构漏洞、RowHammer 效应、CXL 内存风险和验证瓶颈。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`4` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：行交换缓解、漏洞分析、安全 CXL 内存、FPGA 加速模糊测试。
- 代表论文：[HPCA-2023-P0078](../../10_corpus/HPCA/id_index.md#HPCA-2023-P0078) Scalable and Secure Row-Swap: Efficient and Safe Row Hammer Mitigation in Memory Systems (2023)； [HPCA-2024-P0028](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0028) 退休安全漏洞利用（2024）； [HPCA-2026-P0086](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0086) ReScue：可靠且安全的 CXL 内存 (2026)； [HPCA-2026-P0116](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0116) TurboFuzz：FPGA 用于处理器敏捷验证的加速硬件模糊测试 (2026)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

### [HPCA-SF10](#HPCA-SF10)。基准、分析和模拟方法

- 研究问题：通过模拟器、基准套件、功率测量和 workload 特征使架构 claim 具有可比性。
- 背景：这是 HPCA 第二波审核的venue-local分组。这不是一个全球稳定的分类学主张。
- 本 venue 的当前状态：`5` 已接受paper evidence rows；未选择的行保留在筛选矩阵中。
- 方法谱系：实时模拟、基准测试套件、能源基准测试、全栈加速方法、workload 特征。
- 代表论文：[HPCA-2016-P0030](../../10_corpus/HPCA/id_index.md#HPCA-2016-P0030) LiveSim: Going live with microarchitecture optimization (2016)； [HPCA-2022-P0077](../../10_corpus/HPCA/id_index.md#HPCA-2022-P0077) SupermarQ：可扩展的量子基准套件（2022）； [HPCA-2025-P0077](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0077) MLPerf Power：对机器学习系统从微瓦到兆瓦的能源效率进行基准测试，以实现可持续发展 AI (2025)； [HPCA-2026-P0005](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0005) 推进薛定谔式量子模拟的全栈加速（2026）； [HPCA-2026-P0019](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0019) 描述字节跳动的云原生 LLM 推理并揭示未来 AI 加速器的优化挑战和机遇 (2026)
- 团队线索：作者字符串和已知项目/实验室名称仅是阅读线索；不进行任何排名或消除实体歧义的团队 claim。
- workload/artifact 信号：artifact/代码/工具提示记录为 `runnable_unchecked` 或 `needs_review`；没有运行任何代码、基准测试或 artifact。
- 开放问题：完整的 PDF 阅读、artifact/代码可用性、引文结构和cross-venue比较在证据矩阵中注明的地方仍然开放。

## 4. 发展趋势

- 图形/VR 到 3DGS/神经渲染加速：由 [HPCA-2017-P0040](../../10_corpus/HPCA/id_index.md#HPCA-2017-P0040)、[HPCA-2019-P0016](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0016)、[HPCA-2019-P0045](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0045) 支持[HPCA-2025-P0048](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0048)、[HPCA-2025-P0053](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0053)、[HPCA-2026-P0018](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0018)、[HPCA-2026-P0047](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0047)、[HPCA-2026-P0070](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0070)、[HPCA-2026-P0099](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0099)。这是多论文/跨年度 HPCA 信号，仍为 `venue_provisional`。
- LLM 服务/状态系统的注意力加速器：受 [HPCA-2020-P0004](../../10_corpus/HPCA/id_index.md#HPCA-2020-P0004)、[HPCA-2021-P0061](../../10_corpus/HPCA/id_index.md#HPCA-2021-P0061)、[HPCA-2022-P0083](../../10_corpus/HPCA/id_index.md#HPCA-2022-P0083)、[HPCA-2025-P0031](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0031)、[HPCA-2025-P0085](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0085)、[HPCA-2026-P0072](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0072)、[HPCA-2026-P0113](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0113)、[HPCA-2026-P0119](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0119)、[HPCA-2026-P0121](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0121) 支持。这是多论文/跨年度 HPCA 信号，仍为 `venue_provisional`。
- PIM/NDP/CXL 和内存端执行：受 [HPCA-2017-P0026](../../10_corpus/HPCA/id_index.md#HPCA-2017-P0026)、[HPCA-2018-P0028](../../10_corpus/HPCA/id_index.md#HPCA-2018-P0028)、[HPCA-2023-P0027](../../10_corpus/HPCA/id_index.md#HPCA-2023-P0027)、[HPCA-2024-P0055](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0055)、[HPCA-2025-P0010](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0010)、[HPCA-2026-P0001](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0001)、[HPCA-2026-P0076](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0076)、[HPCA-2026-P0110](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0110) 支持。这是一个多论文/跨年度 HPCA 信号，并且仍然是 `venue_provisional`。
- FPGA/HLS 和软硬件协同设计：受 [HPCA-2016-P0007](../../10_corpus/HPCA/id_index.md#HPCA-2016-P0007)、[HPCA-2019-P0015](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0015)、[HPCA-2019-P0025](../../10_corpus/HPCA/id_index.md#HPCA-2019-P0025)、[HPCA-2021-P0060](../../10_corpus/HPCA/id_index.md#HPCA-2021-P0060)、[HPCA-2024-P0006](../../10_corpus/HPCA/id_index.md#HPCA-2024-P0006)、[HPCA-2026-P0088](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0088)、[HPCA-2026-P0116](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0116) 支持。这是一个多论文/跨年度 HPCA 信号，并且仍然是 `venue_provisional`。
- 基准/分析/评估基础设施：由 [HPCA-2016-P0030](../../10_corpus/HPCA/id_index.md#HPCA-2016-P0030)、[HPCA-2017-P0046](../../10_corpus/HPCA/id_index.md#HPCA-2017-P0046)、[HPCA-2022-P0077](../../10_corpus/HPCA/id_index.md#HPCA-2022-P0077)、[HPCA-2025-P0077](../../10_corpus/HPCA/id_index.md#HPCA-2025-P0077)、[HPCA-2026-P0019](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0019)、[HPCA-2026-P0022](../../10_corpus/HPCA/id_index.md#HPCA-2026-P0022) 支持。这是一个多论文/跨年度 HPCA 信号，并且仍然是 `venue_provisional`。

## 5. 方法变化

- HPCA 内存工作从缓存/DRAM 和异构带宽策略转向 PIM/NDP、CXL/coherence 和内存端运行时/工具。
- AI 加速从早期的 ML 模板和稀疏 GEMM 转向特定于注意力的加速器、LLM 服务、KV/状态管理、长上下文调度和 workload 表征。
- 图形工作从传统的 VR/渲染管道优化转向 2025-2026 高斯渲染、3DGS 训练/渲染/SLAM 和 NPU 友好混合。
- FPGA/HLS 行在这里并不是一个广泛的 FPGA 主题；他们确定了 OpenCL 分析、加密计算、稀疏 GEMM、图随机游走、MLIR 生成和硬件模糊测试中的具体瓶颈。
- 评估基础设施作为其自己的研究对象出现：模拟、DRAM 实验工具、量子基准、MLPerf Power 和云原生 LLM 表征。

## 6. 缺失来源

- 统一 HPCA 2016-2026 官方会议记录/session/DOI 源码；当前数据结合了 DBLP/proceedings 行和官方程序。
- 批量 IEEE/ACM 摘要、关键字、PDF 和 artifact 徽章导出。
- HPCA 2022 年和 2025 年最佳论文的 Canonical 奖项来源； 2021 年改进为 TCCA 博客，但仍保留 `needs_review`； 2026 年最佳论文获奖者仍未获得。
- SoftMC、POM、RidgeWalker、UniNDP、Cohet、PIM-malloc、MPU、3DGS 论文和 LLM/PIM 系统的 artifact/代码可运行状态。
- 所有证据锚点的引文结构、后续采用、基准标准化和行业/工具链采用审核。
- 作者/所属机构/团队entity disambiguation和cross-venue比较矩阵。
