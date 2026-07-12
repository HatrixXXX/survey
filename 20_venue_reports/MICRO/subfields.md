# MICRO 小领域深读

检索日期：2026-06-27  
范围：MICRO 2016-2025 accepted-paper corpus；2026 保持 partial。

## 1. 范围与语料

- `papers.csv`：890 行，2016-2025 为 complete；2026 没有 accepted-paper 行。
- `awards.csv`：61 行；本轮补入 SIGMICRO Test-of-Time 2016-2025 结构化行，并修正 2016/2018 若干 award/session 缺口。
- `MICRO_screening_matrix.csv`：951 行，覆盖 papers 和 awards。decision 计数：{'index_only': 659, 'deep_read': 144, 'needs_review': 135, 'exclude_non_main': 13}。
- `MICRO_paper_evidence_matrix.csv`：101 行。证据深度主要是 official program / DOI / title-session level；没有把未读 PDF 的内容写成确定事实。
- 2026：MICRO-59 在 2026-06-27 尚无 accepted-paper 或 award 完整列表，作为 `normal_2026_partial`。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="MICRO-SF01"></a>[MICRO-SF01](#MICRO-SF01) | 3D/神经场景加速 | 3D 重建、神经场景、点云、渲染或 SLAM workload 遇到延迟、可见性、排序和内存移动瓶颈。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2016-2025 | venue_provisional； 22个evidence rows：[MICRO-2016-P0051](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0051)； [MICRO-2017-P0044](../../10_corpus/MICRO/id_index.md#MICRO-2017-P0044); [MICRO-2019-P0047](../../10_corpus/MICRO/id_index.md#MICRO-2019-P0047)； [MICRO-2020-P0074](../../10_corpus/MICRO/id_index.md#MICRO-2020-P0074); [MICRO-2021-P0033](../../10_corpus/MICRO/id_index.md#MICRO-2021-P0033)；... |
| <a id="MICRO-SF02"></a>[MICRO-SF02](#MICRO-SF02) | LLM/Transformer 服务内存架构 | Transformer/LLM/MoE 执行强调 KV/状态容量、内存带宽和数据流利用率。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2016-2025 | venue_provisional; 24个evidence rows：[MICRO-2016-P0017](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0017)； [MICRO-2016-P0020](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0020); [MICRO-2017-P0032](../../10_corpus/MICRO/id_index.md#MICRO-2017-P0032)； [MICRO-2018-P0003](../../10_corpus/MICRO/id_index.md#MICRO-2018-P0003); [MICRO-2019-P0003](../../10_corpus/MICRO/id_index.md#MICRO-2019-P0003)；... |
| <a id="MICRO-SF03"></a>[MICRO-SF03](#MICRO-SF03) | 稀疏张量和 DNN 加速器建模 | 稀疏张量和 DNN 加速器必须处理元数据、负载平衡和数据流建模，而不仅仅是密集算术。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2016-2023 | venue_provisional; 9 个evidence rows：[MICRO-2016-P0056](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0056)； [MICRO-2016-P0057](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0057); [MICRO-2016-P0058](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0058)； [MICRO-2019-P0015](../../10_corpus/MICRO/id_index.md#MICRO-2019-P0015); [MICRO-2020-P0034](../../10_corpus/MICRO/id_index.md#MICRO-2020-P0034)；... |
| <a id="MICRO-SF04"></a>[MICRO-SF04](#MICRO-SF04) | PIM/CXL/近内存系统 | 内存层次结构、PIM、CXL、DRAM 可靠性和处理器内存接口决定性能或正确性。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2016-2025 | venue_provisional; 20 个evidence rows：[MICRO-2016-P0060](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0060)； [MICRO-2016-P0061](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0061); [MICRO-2017-P0025](../../10_corpus/MICRO/id_index.md#MICRO-2017-P0025)； [MICRO-2018-P0059](../../10_corpus/MICRO/id_index.md#MICRO-2018-P0059); [MICRO-2018-P0060](../../10_corpus/MICRO/id_index.md#MICRO-2018-P0060)；... |
| <a id="MICRO-SF05"></a>[MICRO-SF05](#MICRO-SF05) | FPGA/生成器和加速器可用性 | 高级程序、覆盖、HLS/生成器流和多 FPGA 设备减少了加速器实施工作。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2016-2022 | venue_provisional; 5 个evidence rows：[MICRO-2016-P0048](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0048)； [MICRO-2018-P0018](../../10_corpus/MICRO/id_index.md#MICRO-2018-P0018); [MICRO-2021-P0035](../../10_corpus/MICRO/id_index.md#MICRO-2021-P0035)； [MICRO-2022-P0003](../../10_corpus/MICRO/id_index.md#MICRO-2022-P0003); [MICRO-2022-P0073](../../10_corpus/MICRO/id_index.md#MICRO-2022-P0073) |
| <a id="MICRO-SF06"></a>[MICRO-SF06](#MICRO-SF06) | 基准/分析/模型有效性 | 分析、模拟、功率/建模和基准决定架构 claim 是否具有可比性。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2016-2022 | venue_provisional; 9 个evidence rows：[MICRO-2016-P0059](../../10_corpus/MICRO/id_index.md#MICRO-2016-P0059)； [MICRO-2018-P0068](../../10_corpus/MICRO/id_index.md#MICRO-2018-P0068)； [MICRO-2019-P0028](../../10_corpus/MICRO/id_index.md#MICRO-2019-P0028); [MICRO-2019-P0077](../../10_corpus/MICRO/id_index.md#MICRO-2019-P0077); [MICRO-2020-P0063](../../10_corpus/MICRO/id_index.md#MICRO-2020-P0063);... |
| <a id="MICRO-SF07"></a>[MICRO-SF07](#MICRO-SF07) | 安全/正确的加速器和推测设计 | 推测、侧通道、加速器访问控制和证明义务约束优化。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2017-2025 | venue_provisional; 10 个evidence rows：[MICRO-2017-P0063](../../10_corpus/MICRO/id_index.md#MICRO-2017-P0063)； [MICRO-2019-P0071](../../10_corpus/MICRO/id_index.md#MICRO-2019-P0071)； [MICRO-2020-P0001](../../10_corpus/MICRO/id_index.md#MICRO-2020-P0001); [MICRO-2022-P0001](../../10_corpus/MICRO/id_index.md#MICRO-2022-P0001); [MICRO-2023-P0001](../../10_corpus/MICRO/id_index.md#MICRO-2023-P0001);... |
| <a id="MICRO-SF08"></a>[MICRO-SF08](#MICRO-SF08) | 核心预测和指令效率 | 分支、负载、指令和边缘核心机制攻击通用核心内的延迟和利用率。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2023-2023 | venue_provisional; 1 个evidence rows：[MICRO-2023-P0002](../../10_corpus/MICRO/id_index.md#MICRO-2023-P0002) |
| <a id="MICRO-SF09"></a>[MICRO-SF09](#MICRO-SF09) | 量子/非常规计算架构 | 量子、超导或非常规设备需要架构级资源和错误管理选择。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 2020-2020 | venue_provisional; 1 个evidence rows：[MICRO-2020-P0015](../../10_corpus/MICRO/id_index.md#MICRO-2020-P0015) |
| <a id="MICRO-SF10"></a>[MICRO-SF10](#MICRO-SF10) | 历史 MICRO 时间测试锚点 | 较旧的 MICRO 论文被 SIGMICRO 认可为长期存在的架构贡献。 | 查看evidence rows | 查看evidence rows | 查看evidence rows | 历史/外部语料库 | venue_provisional； 0 个evidence rows： |

## 3. 小领域深读

### [MICRO-SF01](#MICRO-SF01)。 3D/神经场景加速

研究问题：3D 感知、神经场景、点云和 3DGS workload 需要实时或近实时执行，但数据路径由可见性、排序、平铺/分箱、内存流量和增量 SLAM/训练循环决定。
背景：MICRO 首先在直接 3DGS 行之前显示点云和 3D 相邻加速器信号。 `Tigris` 和点云行是较早的锚点； 2024-2025 行添加即时 3D 重建、3D 高斯分布、SLAM 和点云 ISA 证据。
本 venue 的当前状态：这是最近的 MICRO 线程，而不是成熟的长期运行的 MICRO 子域。evidence rows包括 [MICRO-2019-P0047](../../10_corpus/MICRO/id_index.md#MICRO-2019-P0047)、[MICRO-2024-P0006](../../10_corpus/MICRO/id_index.md#MICRO-2024-P0006)、[MICRO-2024-P0115](../../10_corpus/MICRO/id_index.md#MICRO-2024-P0115)、[MICRO-2025-P0120](../../10_corpus/MICRO/id_index.md#MICRO-2025-P0120)、[MICRO-2025-P0121](../../10_corpus/MICRO/id_index.md#MICRO-2025-P0121)、[MICRO-2025-P0122](../../10_corpus/MICRO/id_index.md#MICRO-2025-P0122) 和 [MICRO-2025-P0123](../../10_corpus/MICRO/id_index.md#MICRO-2025-P0123)。
方法谱系：点云加速和渲染/光线追踪支持出现在直接 3DGS 之前。最近的产品线转向端到端 3D 重建/渲染、高斯智能处理、冗余减少、边缘增量训练和点云 ISA 扩展。
代表论文：Tigris；融合3D；高SPU； GCC; RTGS;反应3D；点ISA。
团队线索：作者字符串包括 Yingyan Lin-linked Fusion-3D、Fudan GauSPU、Tsinghua/HKUST REACT3D 和 Tsinghua/Beihang PointISA。这些只是语料库信号；不进行排名或作者实体合并。
workload/artifact 信号：从官方标题和会议中可以清楚地看出 workload 证据。artifact/代码重用未 verified。
开放问题：3DGS 加速是否应该与点云/神经场景加速合并，还是在cross-venue evidence到达后分开。

### [MICRO-SF02](#MICRO-SF02)。 LLM/Transformer 服务内存架构

研究问题：现代 LLM 和 Transformer 服务强调状态容量、KV 缓存放置、MoE 路由、稀疏注意力、张量格式转换和加速器内存移动。
本 venue 的当前状态：MICRO 有较旧的 DNN/稀疏加速器系列和最近的 2022-2025 年 LLM/Transformer 系列。 `DFX`是早期的多FPGATransformer电器信号； 2025 年有 Stratum、Kelle、LongSight、DECA、StreamTensor 和 LLM.265。
方法谱系：该线路从密集/稀疏 DNN 加速器转向服务状态和内存系统协同设计。评估语言也从单一加速器加速转向内存层次结构、数据流和系统级服务约束。
代表论文：Cambricon-X；辛巴； DFX;闪存LLM；地层;凯勒；远视； DECA;流张量； LLM.265。
团队线索：作者字符串包括 Cambricon/ICT-CAS、MIT/NVIDIA、Georgia Tech 和最近的 systems/LLM 组。这些信号不是排名。
开放问题：此处未收集大多数行的引用/采用证据； `impact_unverified` 仍用于长期 claim。

### [MICRO-SF03](#MICRO-SF03)。稀疏张量和 DNN 加速器建模

研究问题：稀疏神经/张量 workload 暴露了密集加速器模型隐藏的元数据移动、不规则负载平衡和数据流选择。
本 venue 的现状：证据跨越 2016 年至 2025 年。 Cambricon-X 和 Addressing Irregularity 是早期的稀疏-NN 锚； ExTensor和Sparse Tensor Core拓宽了张量路线； Sparseloop 和 TeAAL 将部分问题转化为分析/建模基础设施。
代表论文：Cambricon-X；解决违规行为；外张量；稀疏张量核心；普罗克拉斯特斯；稀疏循环；茶碱。
方法谱系：加速器设计和建模论文共同发展。有用的阅读路径不仅是硬件数据路径，还包括论文如何建模稀疏性和验证加速。

### [MICRO-SF04](#MICRO-SF04)。 PIM/CXL/近内存系统

研究问题：内存带宽、容量、局部性、可靠性和处理器内存接口限制了经典 workload 和较新的 AI/3D workload。
该venue的现状：路线广泛且持久。 Ambit 是一款commodity-DRAM 计算锚； BEER 和 DStress 是 DRAM 可靠性锚； TRiM 和 PyPIM 显示处理器-内存接口和可编程性；最近的 CXL 和处理器-PIM 行转向可部署接口。
代表论文：Ambit； BEER; D压力；修剪;揭秘 CXL 内存； PyPIM；罗盘;超越页面迁移；代表。
方法谱系：路线从证明内存可以计算转向使内存端计算与系统软件、一致性、调度和测量兼容。

### [MICRO-SF05](#MICRO-SF05)。 FPGA/生成器和加速器可用性

研究问题：高级 workload 需要加速器实现路径，而不需要每篇论文都手工设计新的 RTL 堆栈。
本 venue 的当前状态：MICRO 包含直接 FPGA 和生成器信号：高级 DNN-to-FPGA、gem5-Aladdin SoC 接口建模、TAPAS、OverGen 和 DFX。这些应该稍后与 FPGA/FCCM/FPL/FPT 进行比较，而不是被视为这些venue的替代品。
代表论文：From High-Level Deep Neural Models to FPGAs；使用 gem5-Aladdin 共同设计加速器和 SoC 接口； TAPAS;超根； DFX。

### [MICRO-SF06](#MICRO-SF06)。基准/分析/模型有效性

研究问题：加速 claim 需要分析、模拟、功率模型和基准有效性检查，特别是当 workload 和内存系统变得更加复杂时。
此venue的当前状态：NVBit、APOLLO、TIP、Sparseloop、TeAAL、内存系统基准测试的混乱和相关行显示了测量/方法线。
代表论文：NVBit； APOLLO; TIP;稀疏循环；茶碱；混乱的内存系统基准测试。
开放问题：artifact 可用性未通过运行代码进行验证。仅当标题/会话暗示工具/框架时，行才标记为 `artifact_mentioned`。

### [MICRO-SF07](#MICRO-SF07)。安全/正确加速器和推测设计

研究问题：推测、侧通道和第三方加速器改变了优化的正确性和隔离边界。
本 venue 的当前状态：STT 是有奖支持的推测性污点跟踪证据； CEASER、Graphene、SecureLoop、CryptoMMU、推测性 GPU 地址转换和 ZKP 协同设计显示了跨核心、内存和加速器设计的安全性/正确性压力。
代表论文：STT； CEASER;Graphene；SecureLoop；CryptoMMU；通过硬件算法协同设计加速零知识证明。

### [MICRO-SF08](#MICRO-SF08)。核心预测和指令效率

研究问题：分支/负载预测、指令分析和边缘核心指令子集仍然很重要，因为加速器系统不断与通用核心交互。
代表论文：TIP；爱马仕；耳语;钟针；解耦矢量超前运行；将 RISC-V 指令子集处理器灵活运用到 Extreme Edge。

## 4. 发展趋势

- 3D/神经场景加速是最近但显而易见的：2019 年的 `Tigris`，2020-2024 年的点云行，然后 2024-2025 年的 Fusion-3D/GauSPU/GCC/RTGS/REACT3D/PointISA。这支持了venue-level的边界主张，而不是成熟的长期血统主张。
- AI 加速从稀疏/CNN 加速器转向 LLM 服务状态和内存协同设计。证据包括 Cambricon-X、Simba、DFX、FlashLLM、Stratum、Kelle、LongSight、DECA、StreamTensor 和 LLM.265。
- 以记忆为中心的工作仍然是整个时期的支柱。 Ambit、BEER、TRiM、Demystifying CXL Memory、PyPIM、ComPASS、Beyond Page Migration 和 Delegato 表明问题从 DRAM/缓存优化转变为可部署的接口和协议。
- 评估方法在 2019 年之后变得更加明确：NVBit、APOLLO、TIP、Sparseloop、TeAAL 和 A Mess of Memory System Benchmarking 都认为测量基础设施是架构结果的一部分。

## 5. 方法变化

- Sparse/DNN 工作从自定义加速器数据路径转向稀疏张量建模、DSE 和 LLM 服务状态放置。
- PIM 工作从 in-DRAM 操作建议转向 CXL、处理器-PIM 兼容性、面向 Python 的接口和调度/协议问题。
- 视觉/3D 工作从点云和图形相邻行转向显式 3DGS 和 SLAM 加速器。
- Generator/FPGA 作品似乎是architecture venues和 FPGA venue之间的桥梁：对于阅读 MICRO 很有用，但最终的分类应该等待 FPGA/FCCM/FPL/FPT 比较。

## 6. 缺失来源

- ACM DL / IEEE Xplore 摘要、关键字和 PDF 导出 2016-2025 年完整语料库。
- 工具和基准行的 artifact/代码/项目页面。
- 与 ISCA、HPCA、ASPLOS、FPGA/FCCM/FPL/FPT、DAC/ICCAD 和 MLSys 的cross-venue比较。
- 作者和隶属entity disambiguation，用于团队线索整合。
