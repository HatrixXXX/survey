# SC 小领域深读

## 1. 范围与语料

- 语料库：`1014` paper rows和 `22` award rows。
- 筛选矩阵：`1036` 行；决定：`deep_read` 106、`exclude_non_main` 8、`index_only` 876、`needs_review` 46。
- 证据矩阵：`85`行；影响状态：`impact_unverified` 33、`partial` 52。
- 证据深度参差不齐。引用/采用/artifact 字段包括收集的查询日期；否则它们就未 verified。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | evidence rows | 证据状态 |
|---|---|---|---:|---|
| <a id="SC-SF01"></a>[SC-SF01](#SC-SF01) | AI 训练内存/卸载扩展 | 当模型状态、激活、通信和异构内存占主导地位时，扩展科学 DL、推荐器、MoE 和 LLM 训练。 | 8 | abstract_or_source_mixed |
| <a id="SC-SF02"></a>[SC-SF02](#SC-SF02) | LLM 和Transformer服务系统 | 在延迟、吞吐量、异构 GPU 和管道气泡约束下为 Transformer/LLM 模型提供服务。 | 3 | abstract_or_source_mixed |
| <a id="SC-SF03"></a>[SC-SF03](#SC-SF03) | 低精度和融合的 GPU 内核 | 减少 AI 或科学 ML workload 的张量/GEMM/FNO 内核内存流量和反量化开销。 | 6 | abstract_or_source_mixed |
| <a id="SC-SF04"></a>[SC-SF04](#SC-SF04) | 稀疏图、张量和 GNN 系统 | 处理不规则稀疏矩阵、图挖掘、GNN 采样/训练和分布式稀疏求解器。 | 15 | abstract_or_source_mixed |
| <a id="SC-SF05"></a>[SC-SF05](#SC-SF05) | 通信、集合和互连协同设计 | 控制 all-to-all、allreduce、拓扑、集合和通信/压缩瓶颈。 | 14 | abstract_or_source_mixed |
| <a id="SC-SF06"></a>[SC-SF06](#SC-SF06) | 存储、I/O 和数据移动 | 跨文件系统、突发缓冲区、NVMe、GPU 内存和大型科学管道移动数据，而不会停止计算。 | 13 | abstract_or_source_mixed |
| <a id="SC-SF07"></a>[SC-SF07](#SC-SF07) | 运行时调度和资源管理 | 在不断变化的负载和 SLO 下安排工作流、任务、资源、GPU 共享和操作策略。 | 3 | abstract_or_source_mixed |
| <a id="SC-SF08"></a>[SC-SF08](#SC-SF08) | 编译器、AD、DSL 和自动调整 | 生成、转换或调整内核代码、自动微分和性能可移植性。 | 4 | abstract_or_source_mixed |
| <a id="SC-SF09"></a>[SC-SF09](#SC-SF09) | 分析、再现性和基准测试 | 测量性能/数值、评估 artifact 并使基准/再现性证据可重用。 | 7 | abstract_or_source_mixed |
| <a id="SC-SF10"></a>[SC-SF10](#SC-SF10) | 弹性、功率、热和数值正确性 | 检测和管理 HPC 系统中的故障、能量/热行为、浮点错误和可靠性。 | 4 | abstract_or_source_mixed |
| <a id="SC-SF11"></a>[SC-SF11](#SC-SF11) | FPGA、PIM 和近数据加速 | 将 FPGA、PIM、近数据或特定于域的加速器用于内存限制和通信限制的 workload。 | 5 | abstract_or_source_mixed |
| <a id="SC-SF12"></a>[SC-SF12](#SC-SF12) | 3D 重建和视觉科学成像 | 在 GPU/HPC 系统中扩展 3D 图像重建或相邻视觉/科学成像 workload，无需将 3DGS 视为既定的 SC 主题。 | 3 | abstract_or_source_mixed |

## 3. 小领域深读

### [SC-SF01](#SC-SF01) AI 训练内存/卸载扩展

- 研究问题：当模型状态、激活、通信和异构内存占主导地位时，扩展科学 DL、推荐器、MoE 和 LLM 训练。
- 代表作品：[SC-2021-P0115](../../10_corpus/SC/id_index.md#SC-2021-P0115) ZeRO-infinity：打破GPU内存墙，实现超大规模深度学习； [SC-2024-P0017](../../10_corpus/SC/id_index.md#SC-2024-P0017) APTMoE：带宽受限的 GPU 节点上 MoE 模型的亲和感知管道调整； [SC-2024-P0034](../../10_corpus/SC/id_index.md#SC-2024-P0034) 民主化 AI：基于 GPU 的超级计算机上的开源可扩展 LLM 培训； [SC-2024-P0049](../../10_corpus/SC/id_index.md#SC-2024-P0049) Fire-Flyer AI-HPC：一种经济高效的深度学习软硬件协同设计； [SC-2024-P0062](../../10_corpus/SC/id_index.md#SC-2024-P0062) 长曝光：加速阴影稀疏下LLM的参数高效微调； [SC-2025-P0015](../../10_corpus/SC/id_index.md#SC-2025-P0015) 动态LLM的平衡和弹性端到端培训； [SC-2025-P0087](../../10_corpus/SC/id_index.md#SC-2025-P0087) MLP-Offload：针对 LLM 预训练的多级、多路径卸载，以打破 GPU 内存墙
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。
- 趋势证据：科学 DL 和 LLM/MoE 训练行跨越 [SC-2017-P0012](../../10_corpus/SC/id_index.md#SC-2017-P0012)、[SC-2021-P0115](../../10_corpus/SC/id_index.md#SC-2021-P0115)、[SC-2024-P0040](../../10_corpus/SC/id_index.md#SC-2024-P0040)、[SC-2025-P0087](../../10_corpus/SC/id_index.md#SC-2025-P0087) 和 [SC-2025-P0179](../../10_corpus/SC/id_index.md#SC-2025-P0179)。

### [SC-SF02](#SC-SF02) LLM 和Transformer服务系统

- 研究问题：在延迟、吞吐量、异构 GPU 和管道气泡约束下为Transformer/LLM 模型提供服务。
- 代表作品：[SC-2022-P0021](../../10_corpus/SC/id_index.md#SC-2022-P0021) DeepSpeed- Inference：以前所未有的规模实现 Transformer 模型的高效推理； [SC-2025-P0057](../../10_corpus/SC/id_index.md#SC-2025-P0057) gLLM：用于具有令牌限制的分布式 LLM 的全局平衡管道并行系统； [SC-2025-P0063](../../10_corpus/SC/id_index.md#SC-2025-P0063) Hetis：通过细粒度和动态并行性在异构 GPU 集群中为 LLM 提供服务
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。
- 趋势证据：2024-2025 年服务行分为分析、推测性解码、异构服务、管道调度和专家缓存。

### [SC-SF03](#SC-SF03) 低精度和融合的 GPU 内核

- 研究问题：减少 AI 或科学 ML workload 的张量/GEMM/FNO 内核内存流量和反量化开销。
- 代表作品：[SC-2025-P0075](../../10_corpus/SC/id_index.md#SC-2025-P0075) LiquidGEMM：硬件高效的 W4A8 GEMM 高性能 LLM Serving 内核； [SC-2025-P0091](../../10_corpus/SC/id_index.md#SC-2025-P0091) MXBLAS：使用统一的微型 GEMM 库加速 8 位深度学习； [SC-2025-P0171](../../10_corpus/SC/id_index.md#SC-2025-P0171) TurboFNO：在 GPU 上融合 FFT-GEMM-iFFT 的高性能傅立叶神经算子； [SC-2024-P0066](../../10_corpus/SC/id_index.md#SC-2024-P0066) 数据流架构上的无矩阵有限体积内核； [SC-2025-P0065](../../10_corpus/SC/id_index.md#SC-2025-P0065) HP-MDR：使用高级 GPU 进行高性能、便携式数据重构和渐进式检索； [SC-2016-P0019](../../10_corpus/SC/id_index.md#SC-2016-P0019) Daino：GPU 上并行高效 AMR 的高级框架
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。

### [SC-SF04](#SC-SF04) 稀疏图、张量和 GNN 系统

- 研究问题：处理不规则稀疏矩阵、图挖掘、GNN 采样/训练和分布式稀疏求解器。
- 代表作品：[SC-2024-P0040](../../10_corpus/SC/id_index.md#SC-2024-P0040) 基于 Compute Express Link 的高效张量卸载用于大型深度学习模型训练； [SC-2024-P0093](../../10_corpus/SC/id_index.md#SC-2024-P0093) 拓展新高度：用于训练十亿边图的变革性跨 GPU 采样； [SC-2024-P0100](../../10_corpus/SC/id_index.md#SC-2024-P0100) TorchGT：大规模图Transformer训练的整体系统； [SC-2025-P0100](../../10_corpus/SC/id_index.md#SC-2025-P0100) PGT-I：通过内存高效的分布式训练扩展时空 GNN； [SC-2025-P0102](../../10_corpus/SC/id_index.md#SC-2025-P0102) Plexus：通过 3D 并行全图 GNN 训练驯服十亿边缘图； [SC-2025-P0170](../../10_corpus/SC/id_index.md#SC-2025-P0170) TT-LoRA MoE：使用参数高效的微调和稀疏专家混合； [SC-2018-P0043](../../10_corpus/SC/id_index.md#SC-2018-P0043) HiCOO：稀疏张量的分层存储
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。
- 趋势证据：graph/GNN 行跨越稀疏张量存储、图挖掘、分布式共享内存、十亿边采样和全图训练。

### [SC-SF05](#SC-SF05) 通信、集合和互连协同设计

- 研究问题：控制 all-to-all、allreduce、拓扑、集合和通信/压缩瓶颈。
- 代表作品：[SC-2022-P0034](../../10_corpus/SC/id_index.md#SC-2022-P0034) HammingMesh: A Network Topology for Large-Scale Deep Learning； [SC-2022-P0088](../../10_corpus/SC/id_index.md#SC-2022-P0088) WholeGraph：具有多GPU分布式共享内存架构的快速图神经网络训练框架； [SC-2024-P0010](../../10_corpus/SC/id_index.md#SC-2024-P0010) 通过双级自适应有损压缩加速深度学习推荐模型训练中的通信； [SC-2025-P0089](../../10_corpus/SC/id_index.md#SC-2025-P0089) 时刻：针对多 GPU 核外 GNN 训练共同优化物理通信拓扑和数据放置； [SC-2025-P0153](../../10_corpus/SC/id_index.md#SC-2025-P0153) SlimPipe：用于长上下文 LLM 训练的节省内存且高效的管道并行性； [SC-2025-P0167](../../10_corpus/SC/id_index.md#SC-2025-P0167) 通过集体和自适应推测解码实现高效 LLM 推理； [SC-2023-P0053](../../10_corpus/SC/id_index.md#SC-2023-P0053) HEAR：同态加密 Allreduce
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。

### [SC-SF06](#SC-SF06) 存储、I/O 和数据移动

- 研究问题：跨文件系统、突发缓冲区、NVMe、GPU 内存和大型科学管道移动数据，而不停止计算。
- 代表作品：[SC-2017-P0012](../../10_corpus/SC/id_index.md#SC-2017-P0012) 15PF 深度学习：科学数据的监督和半监督分类； [SC-2024-P0083](../../10_corpus/SC/id_index.md#SC-2024-P0083) PipeInfer：使用异步流水线推测加速 LLM 推理； [SC-2025-P0045](../../10_corpus/SC/id_index.md#SC-2025-P0045) Diff-MoE：具有优先级驱动的差分专家缓存的高效批量 MoE 推理； [SC-2018-P0033](../../10_corpus/SC/id_index.md#SC-2018-P0033) 利用高基交换机中的空闲资源进行补充存储； [SC-2019-P0004](../../10_corpus/SC/id_index.md#SC-2019-P0004) 用于自适应多尺度模拟的大规模并行基础设施：对癌症的 RAS 启动Pathways进行建模； [SC-2019-P0066](../../10_corpus/SC/id_index.md#SC-2019-P0066) 红蓝卵石重温：接近最优并行矩阵-矩阵乘法； [SC-2021-P0054](../../10_corpus/SC/id_index.md#SC-2021-P0054) HPAC：评估 HPC OpenMP 应用程序的近似计算技术
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。

### [SC-SF07](#SC-SF07) 运行时调度和资源管理

- 研究问题：在不断变化的负载和 SLO 下调度工作流、任务、资源、GPU 共享和操作策略。
- 代表作品：[SC-2024-P0011](../../10_corpus/SC/id_index.md#SC-2024-P0011) Accelerated Distributed DLRM Training with Optimized TT Decomposition and Micro-Batching； [SC-2024-P0082](../../10_corpus/SC/id_index.md#SC-2024-P0082) ParvaGPU：云环境中大规模 DNN 推理的高效空间 GPU 共享； [SC-2025-P0027](../../10_corpus/SC/id_index.md#SC-2025-P0027) Caracal：具有轻量级细粒度调度的 GPU 常驻稀疏 LU 求解器
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。

### [SC-SF08](#SC-SF08) 编译器、AD、DSL 和自动调优

- 研究问题：生成、转换或调优内核代码、自动微分和性能可移植性。
- 代表作品：[SC-2016-P0050](../../10_corpus/SC/id_index.md#SC-2016-P0050) LIBXSMM：通过运行时代码生成加速小矩阵乘法； [SC-2021-P0093](../../10_corpus/SC/id_index.md#SC-2021-P0093) 通过酶反向模式自动区分和优化 GPU 内核； [SC-2022-P0062](../../10_corpus/SC/id_index.md#SC-2022-P0062) 通过编译器增强可扩展自动区分多个并行范式； [SC-2024-P0056](../../10_corpus/SC/id_index.md#SC-2024-P0056) KaMPIng：MPI 的灵活且（接近）零开销的 C++ 绑定
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。

### [SC-SF09](#SC-SF09) 分析、再现性和基准测试

- 研究问题：测量性能/数值、评估 artifact 并使基准/再现性证据可重用。
- 代表作品：[SC-2024-P0061](../../10_corpus/SC/id_index.md#SC-2024-P0061) LLM-Pilot：表征和优化 LLM 推理服务的性能； [SC-2025-P0016](../../10_corpus/SC/id_index.md#SC-2025-P0016) GPU 加速超级计算的能源分析和归因的基准驱动模型； [SC-2025-P0106](../../10_corpus/SC/id_index.md#SC-2025-P0106) RAPTOR：科学应用的实用数值分析； [SC-2025-P0127](../../10_corpus/SC/id_index.md#SC-2025-P0127) SC25 论文的再现性报告 MLP-Offload：用于 LLM 预训练的多级、多路径卸载，打破 GPU 内存墙； [SC-2025-P0132](../../10_corpus/SC/id_index.md#SC-2025-P0132) SC25 论文的再现性报告 RAPTOR：科学应用的实用数值分析； [SC-2025-P0140](../../10_corpus/SC/id_index.md#SC-2025-P0140) SC25 Paper TurboFNO 的再现性报告：在 GPU 上融合 FFT-GEMM-iFFT 的高性能傅立叶神经算子； [SC-2025-P0142](../../10_corpus/SC/id_index.md#SC-2025-P0142) SC25 论文的可重复性报告 X-MoE：为 HPC 平台上的新兴专家混合架构启用可扩展培训
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。

### [SC-SF10](#SC-SF10) 弹性、功率、热量和数值正确性

- 研究问题：检测和管理 HPC 中的故障、能量/热行为、浮点错误和可靠性系统。
- 代表作品：[SC-2025-P0041](../../10_corpus/SC/id_index.md#SC-2025-P0041) Demystifying the Resilience of Large Language Model Inference: An End-to-End Perspective； [SC-2020-P0082](../../10_corpus/SC/id_index.md#SC-2020-P0082) 可扩展且严格的浮点误差分析； [SC-2021-P0092](../../10_corpus/SC/id_index.md#SC-2021-P0092) 揭示 200PF 百亿亿次级超级计算机的功率、能量和热动态； [SC-2024-P0012](../../10_corpus/SC/id_index.md#SC-2024-P0012) GPU 准确便捷的能耗测量：NVIDIA GPU 内置功率传感器详解
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。

### [SC-SF11](#SC-SF11) FPGA、PIM 和近数据加速

- 研究问题：使用 FPGA、PIM、近数据或适用于内存限制和通信限制 workload 的特定领域加速器。
- 代表作品：[SC-2020-P0040](../../10_corpus/SC/id_index.md#SC-2020-P0040) fBLAS：FPGA 上的流式线性代数； [SC-2023-P0042](../../10_corpus/SC/id_index.md#SC-2023-P0042) FASDA：用于范围有限分子动力学的 FPGA 辅助、可扩展和分布式加速器； [SC-2025-P0048](../../10_corpus/SC/id_index.md#SC-2025-P0048) DRIM-ANN：基于商业 DRAM-PIM 的近似最近邻搜索引擎； [SC-2025-P0118](../../10_corpus/SC/id_index.md#SC-2025-P0118) SC25 论文的再现性报告 DRIM-ANN：基于商业 DRAM-PIM 的近似最近邻搜索引擎； [SC-2025-P0174](../../10_corpus/SC/id_index.md#SC-2025-P0174) UpANNS：利用现实世界的 PIM 架构提高数十亿级 ANNS 效率
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。
- 趋势证据：FPGA/PIM/near-data 行从 fBLAS 和 FASDA 移动到 DRIM-ANN、TaGNN 和 UpANNS；adoption尚未得到验证。

### [SC-SF12](#SC-SF12) 3D 重建和视觉科学成像

- 研究问题：跨 GPU/HPC 系统扩展 3D 图像重建或相邻视觉/科学成像 workload，而不将 3DGS 视为既定的 SC 主题。
- 代表作品：[SC-2018-P0001](../../10_corpus/SC/id_index.md#SC-2018-P0001) 167-PFlops 电子显微镜深度学习：从学习物理到原子操控； [SC-2020-P0067](../../10_corpus/SC/id_index.md#SC-2020-P0067) Petascale XCT：在多个 GPU 节点上进行分层通信的 3D 图像重建； [SC-2025-P0097](../../10_corpus/SC/id_index.md#SC-2025-P0097) ORBIT-2：缩放用于天气和气候的 Exascale 视觉基础模型 缩小
- 团队线索：仅限活动线索；没有排名或作者频率强度 claim。
- 影响状态：每行使用`impact_verification_status`；未经证实的影响仍未得到证实。
- 边界：Petascale XCT 是直接 3D 重建； ORBIT-2 是邻近视觉/科学成像。两者都不能证明 SC 具有直接的 3DGS 主题。

## 4. 发展趋势

- AI 训练内存/卸载：2017-2025 年的多行支持从科学 DL 到内存墙 LLM/MoE 训练的跨年度转变。
- LLM 服务：2024-2025 行显示分析、GPU 共享、推测解码、异构集群和专家缓存方面的单独瓶颈。
- 稀疏图/GNN：2018-2025 年证据将稀疏张量/图奖励与多 GPU 和十亿边 GNN 训练系统联系起来。
- FPGA/PIM/near-data：2020-2025 证据是venue-provisional但具体的；artifact 和采用仍然需要审核。
- 再现性报告：SC25 再现性报告行是 artifact 评估证据，而不是独立的算法里程碑。

## 5. 缺失来源

- 没有摄取带有会话、摘要、关键字和 artifact 徽章的统一 SC 2016-2025 年计划导出。
- 运行时/存储/通信深读分片超时；受影响的行保持保守。
- SC17 规范获奖者页面仍然缺失。
- 截至 2026 年 6 月 27 日，SC26 录用论文名单和获奖者仍保持正常的部分报道。
