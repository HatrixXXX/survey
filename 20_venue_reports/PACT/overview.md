# PACT 论文图谱分析

## 1. 会议定位

本报告中的 `PACT` 指 International Conference on Parallel Architectures and Compilation Techniques。项目中把它放在体系结构 P1 来源，重点看 compiler、parallel runtime、GPU/CPU-GPU、memory/PIM/CXL、稀疏/图计算、specialized accelerator 和软硬件协同。这里明确排除 DBLP 的 `conf/pact` Parallel Computing Technologies 系列；本轮只使用 `conf/IEEEpact` 和 PACT 官方页面。对应 claim <a id="PACT-001-C001"></a>[PACT-001-C001](#PACT-001-C001)、<a id="PACT-001-C002"></a>[PACT-001-C002](#PACT-001-C002)。

## 2. 数据来源与覆盖范围

覆盖范围是 2016-2026。`papers.csv` 以 DBLP `conf/IEEEpact` XML 为优先来源；DBLP XML 在本轮对部分早年请求不稳定，所以 2016-2018 和 2021 使用 researchr proceedings index 作为 fallback。2019、2020、2022-2025 使用官方 program 页面补 session、Best Paper Session 和 PDF link。2026 官方 program 仍写着 technical sessions coming soon，submission page 给出的 author notification 是 2026-08-05，因此 2026 标为 `partial`。对应 claim <a id="PACT-001-C003"></a>[PACT-001-C003](#PACT-001-C003)、<a id="PACT-001-C004"></a>[PACT-001-C004](#PACT-001-C004)。

本轮按任务要求先启动 metadata、clustering、lineage、teams 四个 subagents，均使用 `gpt-5.5`、`xhigh`、`priority`。当前报告中的聚类命名主要采用 clustering agent 返回的 PACT-C01 到 PACT-C09 seed；metadata、lineage 和 teams agent 的结果用于后续复核和修订。

| 年份 | 论文.csv 行 | 状态 | 主要来源 |
| --- | --- | --- | --- |
| 2016 | 55 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2017 | 50 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2018 | 36 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2019 | 58 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2020 | 49 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2021 | 25 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2022 | 50 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2023 | 33 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2024 | 27 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2025 | 39 | 完整/部分元数据 | DBLP/researchr 以及可用的官方程序 |
| 2026 | 1 | partial | PACT 2026 官方程序和提交页面 |

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型标签 | 代表论文 | 记录数 | 证据状态 |
| --- | --- | --- | --- | --- | --- | --- |
| T11 | 一般 PACT 需求审查行 | general_needs_review | needs_review | 任务并行程序的静态截止； CAF：核心到核心通信加速框架 | 138 | 临时 |
| T08/T10/T11 | GPU 内存、运行时和微架构 | gpu_memory_runtime_microarchitecture | gpu|运行时|缓存|address_translation|warp|内核 | 桥接基于 CNN 的横向扩展大数据处理的 GPU 加速的语义差距：大处着眼，小处着眼； OAWS：内存遮挡感知扭曲调度 | 61 | 临时 |
| T01/T02/T05 | DNN、GNN、LLM 和模型服务加速 | dnn_gnn_llm_acceleration | dnn|gnn|llm|moe|推理|训练|张量 | POSTER：弥合神经网络和神经形态硬件之间的差距； POSTER：共享内存加速器上深度神经网络性能优化的设计空间探索 | 50 | 临时 |
| T09/T05/T08 | 并行硬件上的图、稀疏图、不规则图和 OLAP | graph_sparse_irregular_gpu | 图|稀疏|不规则|gpu|olap|spmm | Sparso：稀疏线性代数的上下文驱动优化；学生研究海报：用于大规模图形处理的可扩展通用系统 | 44 | 临时 |
| T07/T08/T11 | 编译器、代码生成和自动调优 | compiler_codegen_autotuning | 编译器|code_generation|自动调优|多面体|dsl|mlir|loop_optimization | 自动调整 POWER8 上的 Spark 大数据 workload：基于预测的动态 SMT 线程；自动利用 GPU 多个相关内核的隐式管道并行性 | 40 | 临时 |
| T10/T01/T11 | 内存、PIM、CXL、持久性和数据移动 | memory_pim_cxl_persistence | 内存|pim|near_memory|cxl|nvm|kv_cache|data_movement | 通过近数据处理加速链表遍历；能源感知持久性：减少 NVM 中基于内存的持久性的能源开销 | 29 | 临时 |
| T06/T07/T12 | 空间、FPGA 和异构加速器 | spatial_fpga_heterogeneous_accelerators | fpga|空间|异构|加速器|hls|source_to_source | 使用加速器对闪存进行大数据分析；多核上数据并行程序的在线可扩展性表征 | 26 | 临时 |
| T03/T04/T09/T11 | 领域、视觉、机器人、基因组学和科学 workload | domain_visual_robotics_genomics | 3dgs|机器人学|slam|视觉|基因组学|科学|mobile_gpu | 用于加速图像处理流程的 DSL 编译器在 FPGA 上； POSTER：科学应用数据流架构的优化 | 21 | 临时 |
| T10/T12/T11 | 安全性、可靠性和加密加速器 | security_reliability_specialized_crypto | 安全性|可靠性|side_channel|crypto|fhe|zkp|pqc | 应对 GPU 寄存器文件在低电源电压下的可靠性挑战； POSTER：在支持硬件事务内存的 COTS 多核处理器上进行容错执行 | 7 | 临时 |
| T11 | 分析、基准测试、建模和仿真 | profiling_benchmark_modeling | 分析|基准|建模|模拟|sample_selection | 将算法参数集成到 3D 场景理解中的基准测试和设计空间探索中；新兴大数据 workload 的代理基准 | 6 | 临时 |

这些 topic 是 clustering agent 基于标题和 session 名给出的 provisional seed，不是稳定 taxonomy。对应 claim <a id="PACT-001-C005"></a>[PACT-001-C005](#PACT-001-C005)。

## 4. Accepted Papers 聚类结果

| 年份 | 主导主题 | 新兴主题 | 代表论文 | 证据口径 |
| --- | --- | --- | --- | --- |
| 2016 | 一般 PACT 需求审查行 (25)； GPU 内存、运行时和微架构 (10)；编译器、代码生成和自动调整 (5) | 仅一年内未断言 | 一个 DSL 编译器，用于加速 FPGA 上的图像处理管道；通过近数据处理加速链表遍历；具有内存处理功能的 GPU 架构的调度技术 | 标题/会话级 |
| 2017 | 一般 PACT 需求评审行 (25)； GPU 内存、运行时和微架构 (9)；并行硬件上的图、稀疏、不规则和 OLAP (5) | 仅一年内未断言 | 优化启发式的端到端深度学习 | 标题/会话级 |
| 2018 | 一般 PACT needs_review行 (14)； Spatial、FPGA 和异构加速器 (5)； GPU 内存、运行时和微架构 (5) | 仅一年内未断言 | 3D-Xpath：高密度管理的 DRAM 架构，为内存事务提供经济有效的替代路径；用于深度神经网络的便携式自动数据量化器；具有并行数据冲突管理功能的高效图形加速器 | 标题/会话级 |
| 2019 | 一般 PACT 需求审查行 (18)；并行硬件上的图、稀疏图、不规则图和 OLAP (10)； GPU 内存、运行时和微架构 (10) | 仅一年内未断言 | BOLT：使用用户级线程优化 OpenMP 并行区域； Deepframe：用于空间硬件加速器的配置文件驱动编译器 | 标题/会话级 |
| 2020 | 一般 PACT 需求审查行 (23)； DNN、GNN、LLM 和模型服务加速 (7)； GPU 内存、运行时和微体系结构 (6) | 仅一年内未断言 | cuSZ：一种基于 GPU 的高效科学数据误差界限有损压缩框架； Fireiron：一种用于 GPU 的数据移动感知调度语言； Helix：加速纳米孔基因组碱基识别的算法/架构协同设计； SparseRT：加速 GPU 上的非结构化稀疏性以实现深度学习推理 | 标题/会话级 |
| 2021 | DNN、GNN、LLM 和模型服务加速 (5)； GPU 内存、运行时和微架构 (4)；并行硬件上的图、稀疏、不规则和 OLAP (4) | 仅一年内未断言 | 自动调整多通道机器学习编译器的灵活方法； PIM-DL：通过数据布局优化增强 DNN 对内存中数字处理架构的推理；多灵：将 C 提升为多面体 MLIR；联合：MLIR 中的统一 HW-SW 协同设计生态系统，用于评估空间加速器上的张量运算 | 标题/会话级 |
| 2022 | 一般 PACT 需求审查行 (12)； GPU 内存、运行时和微架构 (8)；编译器、代码生成和自动调优 (8) | 仅一年内未断言 | GNNear：利用近内存处理加速图神经网络的全批量训练； ReACT：张量表达式的冗余感知代码生成； Slice-and-Forge：更好地利用图卷积网络加速器的缓存；传输调优：重用自动调度以实现高效的张量程序代码生成； VoxelCache：加速机器人和 3D 重建任务中的在线绘图 | 标题/会话级 |
| 2023 | DNN、GNN、LLM 和模型服务加速 (9)；一般PACTneeds_review行（5）； GPU 内存、运行时和微架构 (5) | 仅一年内未断言 | G-Sparse：现代 GPU 上图神经网络广义稀疏计算的编译器驱动加速； SDM：具有缓存一致性计算 Express Link 的支持共享的分解内存系统； SimplePIM：用于高效高效内存处理的软件框架；虚拟 PIM：多 DPU PIM 架构的资源感知动态 DPU 分配和 workload 调度框架 | 标题/会话级 |
| 2024 | 一般 PACT 需求审查行 (8)； DNN、GNN、LLM 和模型服务加速 (5)；空间、FPGA 和异构加速器 (3) | 仅一年内未断言 | 激活序列缓存：使用单个 GPU 进行高吞吐量和内存高效的生成推理； PIM-Opt：揭秘现实世界内存处理系统上的分布式优化算法； SZKP：用于零知识证明的可扩展加速器架构 | 标题/会话级 |
| 2025 | DNN、GNN、LLM 和模型服务加速 (8)；内存、PIM、CXL、持久性和数据移动 (7)；并行硬件上的图形、稀疏、不规则和 OLAP (5) | 仅一年内未断言 | 自动代码生成，用于加速 FPGA 上基于结构化网格的显式数值求解器；通过基于 FPGA 的仿真和设备端管理探索 CXL 时代的内存分层系统； LibraPIM：动态负载重新平衡，以最大限度地提高 PIM 辅助 LLM 推理系统的利用率； LOOPer：用于多面体编译器的学习自动代码优化器；优化移动 GPU 的 3D 高斯飞溅； 1M 令牌的可扩展处理-近内存 LLM 推理：CXL-启用 KV-缓存管理超出 GPU 限制； ScaleMoE：用于大规模专家混合模型的快速且可扩展的分布式训练框架； SPipe：用于在内存压力下训练 LLM 的混合 GPU 和 CPU 管道 | 标题/会话级 |
| 2026 | 部分；接受的论文列表未公开 | 待定 | 没有接受的paper rows | 官方计划称技术会议即将推出 |

整体上，PACT 的主线不是单一“体系结构会议”口径，而是编译器/runtime 与并行架构之间的交叉：早年可见 GPU scheduling、PIM、FPGA DSL 和 sparse linear algebra；2019-2023 出现 spatial accelerator compiler、PIM software framework、GNN/graph 和 3D reconstruction/robotics；2024-2025 明显转向 generative inference、LLM/MoE、CXL/KV-cache、specialized crypto accelerator，以及一个直接命中 3D Gaussian mobile GPU 的 2025 row。趋势判断只基于本 corpus 的论文集合和官方 session，不扩展到全领域。

## 5. Award Papers 分析

| 年份 | 奖项/标记 | rank | 论文 | 主题 | 证据状态 | 备注 |
| --- | --- | --- | --- | --- | --- | --- |
| 2017 | PACT 最佳论文 | 获胜者 | DeNovo：重新思考纪律并行的内存层次结构 | general_needs_review | needs_review | 已归档 PACT 2017 官方页面验证了奖项文本，但是DBLP 将此标题映射到 PACT 2011 年论文； paper_id 对齐问题仍未解决。 |
| 2017 | PACT 最佳学生论文 | 获胜者 | Optimizing Data Layouts for Parallel Computation on Multicores | general_needs_review | needs_review | 已归档 PACT 2017 官方页面验证了奖项文本，但是DBLP 将此标题映射到 PACT 2011 年论文； paper_id 对齐问题仍未解决。 |
| 2019 | PACT 最佳论文 | 获胜者 | BOLT: Optimizing OpenMP Parallel Regions with User-Level Threads | general_needs_review | 已验证 | 元数据和团队代理报告 PACT 2019 主页明确指出了这篇最佳论文。 |
| 2020 | PACT 最佳论文 | 获胜者 | 基于模型的扭曲重叠平铺用于 GPU 上的图像处理程序 | domain_visual_robotics_genomics | 已验证 | Teams 代理报告 PACT 2020 官方主页验证了这篇最佳论文；程序页面还公开了最佳论文会议。 |
| 2022 | PACT 最佳论文 | 获胜者 | Slice-and-Forge：更好地利用图卷积网络加速器的缓存 | graph_sparse_irregular_gpu | 已验证 | 元数据、沿袭和团队代理报告 PACT 2022 官方主页验证了这篇最佳论文。 |

本轮没有找到一个跨 2016-2026 的 PACT 官方 award registry。`awards.csv` 记录的是 subagents 找到并可回链的 award rows：2017 保留 archived official page 作为 award-text 证据，但 paper_id 对齐仍是 `needs_review`；2019、2020、2022 依赖官方首页或 program。2016、2018、2021、2023-2026 的 main-paper award 仍按 `needs_review` 处理，不在正文里写成确定事实。奖项只作为代表论文候选，不等于已经做过 citation impact audit。

## 6. 代表性论文清单

| 论文 | 年份 | 角色 | WHY / HOW / WHAT / IMPACT | claim |
| --- | --- | --- | --- | --- |
| 用于加速 FPGA 上图像处理管道的 DSL 编译器 | 2016 | tool_benchmark | WHY: FPGA DSL/与硬件-软件映射相关的编译器路径。 HOW/WHAT：领域、视觉、机器人、基因组学和科学 workload。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C040"></a>[PACT-001-C040](#PACT-001-C040) |
| 通过近数据处理加速链表遍历 | 2016 | 里程碑 | WHY：用于大量指针不规则访问的早期近数据路由。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C041"></a>[PACT-001-C041](#PACT-001-C041) |
| 具有内存处理功能的 GPU 架构的调度技术 | 2016 | 里程碑 | WHY：连接 GPU 调度和 PIM/近内存执行的早期 PACT 行。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C042"></a>[PACT-001-C042](#PACT-001-C042) |
| 优化启发式的端到端深度学习 | 2017 | 里程碑 | WHY：基于学习的编译器启发式和 ML-for-compilers 路线。 HOW/WHAT：一般 PACT needs_review行。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C043"></a>[PACT-001-C043](#PACT-001-C043) |
| BOLT: Optimizing OpenMP Parallel Regions with User-Level Threads | 2019 | 里程碑 | WHY：PACT 2019 年最佳论文和 OpenMP 运行时路线。 HOW/WHAT：一般 PACT needs_review行。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C044"></a>[PACT-001-C044](#PACT-001-C044) |
| Deepframe：用于空间硬件加速器的配置文件驱动编译器 | 2019 | 里程碑 | WHY：用于空间硬件加速器的配置文件驱动编译器路线。 HOW/WHAT：编译器、代码生成和自动调整。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C045"></a>[PACT-001-C045](#PACT-001-C045) |
| cuSZ：一种基于 GPU 的高效科学数据误差有限有损压缩框架 | 2020 | tool_benchmark | WHY：GPU/HPC 数据缩减和压缩路线。 HOW/WHAT：领域、视觉、机器人、基因组学和科学 workload。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C046"></a>[PACT-001-C046](#PACT-001-C046) |
| Fireiron：用于 GPU 的数据移动感知调度语言 | 2020 | tool_benchmark | WHY：数据移动感知 GPU 调度语言。 HOW/WHAT：编译器、代码生成和自动调整。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C047"></a>[PACT-001-C047](#PACT-001-C047) |
| Helix：加速纳米孔基因组碱基识别的算法/架构协同设计 | 2020 | 前沿 | WHY：特定领域的算法/架构协同设计示例。 HOW/WHAT：领域、视觉、机器人、基因组学和科学 workload。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C048"></a>[PACT-001-C048](#PACT-001-C048) |
| SparseRT：加速 GPU 上的非结构化稀疏性以进行深度学习推理 | 2020 | 里程碑 | WHY：GPU 上的稀疏 DNN 推理和不规则执行路线。 HOW/WHAT：DNN、GNN、LLM 和模型服务加速。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C049"></a>[PACT-001-C049](#PACT-001-C049) |
| 自动调整多遍机器学习编译器的灵活方法 | 2021 | tool_benchmark | WHY：ML 编译器自动调整路线。 HOW/WHAT：编译器、代码生成和自动调整。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C050"></a>[PACT-001-C050](#PACT-001-C050) |
| PIM-DL：通过数据布局优化增强 DNN 对数字处理内存架构的推理 | 2021 | 前沿 | WHY：通过布局优化对数字 PIM 进行 DNN 推理。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C051"></a>[PACT-001-C051](#PACT-001-C051) |
| 多灵：将 C 提升为多面体 MLIR | 2021 | tool_benchmark | WHY：MLIR/多面体编译器基础结构路线。 HOW/WHAT：编译器、代码生成和自动调整。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C052"></a>[PACT-001-C052](#PACT-001-C052) |
| 联盟：MLIR 中的统一 HW-SW 协同设计生态系统，用于评估空间加速器上的张量操作 | 2021 | tool_benchmark | WHY：基于 MLIR 的 HW/SW 空间加速器协同设计生态系统。 HOW/WHAT：DNN、GNN、LLM 和模型服务加速。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C053"></a>[PACT-001-C053](#PACT-001-C053) |
| GNNear：通过近内存处理加速图神经网络的全批量训练 | 2022 | 前沿 | WHY：通过近内存处理进行 GNN 训练。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C054"></a>[PACT-001-C054](#PACT-001-C054) |
| ReACT：张量表达式的冗余感知代码生成 | 2022 | tool_benchmark | WHY：张量表达式代码生成路径。 HOW/WHAT：DNN、GNN、LLM 和模型服务加速。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C055"></a>[PACT-001-C055](#PACT-001-C055) |
| Slice-and-Forge：更好地利用图卷积网络加速器的缓存 | 2022 | 里程碑 | WHY：PACT 2022 年最佳论文和以缓存为中心的 GCN 加速器路线。 HOW/WHAT：并行硬件上的图形、稀疏、不规则和 OLAP。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C056"></a>[PACT-001-C056](#PACT-001-C056) |
| 传输调优：重用自动调度以实现高效张量程序代码生成 | 2022 | tool_benchmark | WHY：自动调度重用和张量编译器路径。 HOW/WHAT：DNN、GNN、LLM 和模型服务加速。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C057"></a>[PACT-001-C057](#PACT-001-C057) |
| VoxelCache：加速机器人和 3D 重建任务中的在线映射 | 2022 | 前沿 | WHY：与用户方向相关的机器人和 3D 重建行。 HOW/WHAT：领域、视觉、机器人、基因组学和科学 workload。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C058"></a>[PACT-001-C058](#PACT-001-C058) |
| G-Sparse：现代 GPU 上图神经网络广义稀疏计算的编译器驱动加速 | 2023 | 前沿 | WHY：GPU 上编译器驱动的稀疏 GNN 加速。 HOW/WHAT：DNN、GNN、LLM 和模型服务加速。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C059"></a>[PACT-001-C059](#PACT-001-C059) |
| SDM：具有缓存一致性计算 Express Link 的启用共享的分解内存系统 | 2023 | 前沿 | WHY：CXL/分解内存路由。 HOW/WHAT：GPU 内存、运行时和微体系结构。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C060"></a>[PACT-001-C060](#PACT-001-C060) |
| SimplePIM：用于高效高效内存处理的软件框架 | 2023 | tool_benchmark | WHY：PIM 软件框架路线。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C061"></a>[PACT-001-C061](#PACT-001-C061) |
| 虚拟 PIM：多 DPU PIM 架构的资源感知动态 DPU 分配和 workload 调度框架 | 2023 | 前沿 | WHY：资源感知多 DPU PIM 调度路由。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C062"></a>[PACT-001-C062](#PACT-001-C062) |
| 激活序列缓存：使用单个 GPU 进行高吞吐量和内存高效的生成推理 | 2024 | 前沿 | WHY：生成推理内存/缓存路由。 HOW/WHAT：DNN、GNN、LLM 和模型服务加速。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C063"></a>[PACT-001-C063](#PACT-001-C063) |
| PIM-Opt：揭秘真实世界内存处理系统上的分布式优化算法 | 2024 | tool_benchmark | WHY：真实世界 PIM 系统评估路线。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C064"></a>[PACT-001-C064](#PACT-001-C064) |
| SZKP：用于零知识证明的可扩展加速器架构 | 2024 | 前沿 | WHY：ZKP 的专用加速器路线。 HOW/WHAT：空间、FPGA 和异构加速器。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C065"></a>[PACT-001-C065](#PACT-001-C065) |
| 自动代码生成，用于加速 FPGA 上基于结构化网格的显式数值求解器 | 2025 | tool_benchmark | WHY：结构化网格求解器的 FPGA 代码生成路径。 HOW/WHAT：领域、视觉、机器人、基因组学和科学 workload。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C066"></a>[PACT-001-C066](#PACT-001-C066) |
| 通过基于 FPGA 的仿真和设备端管理探索 CXL 时代的内存分层系统 | 2025 | 前沿 | WHY：使用基于 FPGA 的仿真路由的 CXL 内存分层。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C067"></a>[PACT-001-C067](#PACT-001-C067) |
| LibraPIM：动态负载重新平衡以最大限度地提高 PIM 辅助 LLM 推理系统的利用率 | 2025 | 前沿 | WHY：PIM 辅助 LLM 推理负载平衡路由。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C068"></a>[PACT-001-C068](#PACT-001-C068) |
| LOOPer：多面体编译器的学习自动代码优化器 | 2025 | 前沿 | WHY：多面体编译器的学习代码优化器。 HOW/WHAT：编译器、代码生成和自动调整。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C069"></a>[PACT-001-C069](#PACT-001-C069) |
| 优化移动 GPU 的 3D 高斯飞溅 | 2025 | 前沿 | WHY：直接 PACT 2025 3D 高斯 mobile-GPU 行。 HOW/WHAT：领域、视觉、机器人、基因组学和科学 workload。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C070"></a>[PACT-001-C070](#PACT-001-C070) |
| 可扩展处理 - 1M 令牌的近内存 LLM 推理：CXL-启用 KV-缓存管理超出 GPU 限制 | 2025 | 前沿 | WHY：LLM KV-cache， CXL 和处理近内存路由。 HOW/WHAT：内存、PIM、CXL、持久性和数据移动。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C071"></a>[PACT-001-C071](#PACT-001-C071) |
| ScaleMoE：用于大规模专家混合模型的快速且可扩展的分布式训练框架 | 2025 | 前沿 | WHY：MoE 分布式训练路线。 HOW/WHAT：DNN、GNN、LLM 和模型服务加速。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C072"></a>[PACT-001-C072](#PACT-001-C072) |
| SPipe：用于在内存压力下训练 LLM 的混合 GPU 和 CPU 管道 | 2025 | 前沿 | WHY：在内存压力下混合 GPU/CPU LLM 训练管道。 HOW/WHAT：DNN、GNN、LLM 和模型服务加速。 IMPACT：impact_unverified 超出了源支持的包含范围。 | <a id="PACT-001-C073"></a>[PACT-001-C073](#PACT-001-C073) |

这些代表论文按解释价值和来源可追溯性选，不按引用数排序。读者应把它们当作 PACT 入口：compiler/codegen、PIM/memory、sparse/GNN、FPGA/spatial accelerator、LLM/edge AI 和 3D Gaussian mobile GPU。

## 7. 发展脉络

- 2016-2018：GPU memory/runtime、near-data/PIM、FPGA DSL、sparse linear algebra 和 DNN quantization 已经在 PACT proceedings 中出现。由于 2016-2018 主要依赖 researchr fallback，session-level 结论保守处理。
- 2019-2020：官方 program 显示 PACT 把 sparse RNN、heterogeneous graph analytics、spatial hardware compiler、SLAM approximation、SparseRT、Fireiron、AutoHOOT 和 Helix 放进主程序/Best Paper Session 语境中。这个阶段的核心是编译器/runtime 与专用/异构架构的协同。
- 2021-2023：PIM-DL、Union、GNNear、VoxelCache、SimplePIM、Virtual PIM、SDM、G-Sparse 等标题把 PIM、MLIR/spatial accelerator、near-memory GNN 和 3D reconstruction/robotics 连起来。
- 2024-2025：PACT 的新信号集中在 generative inference、LLM/MoE、CXL/KV-cache、mobile/edge AI、FHE/ZKP/PQC accelerator 和 3D Gaussian mobile GPU。当前只能说“出现直接标题证据”，不能说 PACT 已形成稳定 3DGS 子领域。

## 8. 领跑团队和代表成果

本节只写 PACT corpus 内的 team signal，不做团队排名。SNU 及相关韩国 AI/PIM/GPU 群在 2024-2025 的 graph neural network、LLM inference/training、MoE 和 PIM-assisted LLM rows 中很活跃，但 Jae W. Lee 和 Jaejin Lee 不能混为一人。ETH Zurich / Onur Mutlu / Juan Gómez-Luna 合作者是 PIM 和 memory/data movement 的强入口。University of Edinburgh / Michael O'Boyle / Elizabeth Polgreen / Alexander Brauckmann / Tobias Grosser 是 compiler/program synthesis/IR raising 的清晰线索。University of Georgia/William & Mary 的 2025 3D Gaussian mobile-GPU row 是和用户方向最直接的团队入口，但 PACT 内只有一个直接 3DGS row，不能写成长期领跑团队。对应 claim <a id="PACT-001-C120"></a>[PACT-001-C120](#PACT-001-C120) 到 <a id="PACT-001-C124"></a>[PACT-001-C124](#PACT-001-C124)。这些判断仍需 affiliation disambiguation。

## 9. 对博士入门者的阅读路线

必读 10 篇：Scheduling Techniques for GPU Architectures with Processing-In-Memory Capabilities；A DSL Compiler for Accelerating Image Processing Pipelines on FPGAs；Deepframe；SparseRT；Fireiron；PIM-DL；Union；GNNear；VoxelCache；Optimizing 3D Gaussian Splattering for Mobile GPUs。

扩展 20 篇：从 `papers.csv` 中筛选 `representative_role != none`，再补 PACT-C01、PACT-C03、PACT-C05、PACT-C06 和 PACT-C08 的近年 rows。这样能覆盖 compiler/runtime、graph/sparse、PIM/memory、FPGA/spatial accelerator 和 user-relevant 3D/robotics/vision，而不是只读 LLM。

适合跟踪的近年方向：LLM KV-cache/CXL/PNM，MoE distributed training，agentic/codegen/autoscheduling，GPU irregular/OLAP，specialized crypto accelerator，mobile/edge AI 与 3D Gaussian rendering。

## 10. 与我的方向的连接点

直接连接点是 PACT 2025 的 `Optimizing 3D Gaussian Splattering for Mobile GPUs`，它在官方 program 的 Edge & Mobile AI Systems session 中出现。相邻连接点包括 2022 `VoxelCache: Accelerating Online Mapping in Robotics and 3D Reconstruction Tasks`、2019 `SLAMBooster`、以及 PACT 中持续存在的 GPU/PIM/memory/runtime/compiler 论文。这些论文适合用来拆 3DGS 的 mobile GPU mapping、cache/data movement、kernel/runtime scheduling 和端侧约束，但必须逐篇看 PDF 才能判断技术路线是否能迁移到 FPGA 或专用加速器。

FPGA 连接点来自 2016 FPGA image pipeline DSL、2021/2023 spatial accelerator 和 CPU-FPGA/source-to-source 路线、2025 structured-mesh solver FPGA code-generation。PACT 的价值主要是把“编译/调度/数据搬运”写清楚，而不是直接替代 FPGA/FCCM/FPL 的硬件实现证据。

## 11. 缺失来源

- 统一 PACT 2016-2026 官方奖项登记处或官方最佳论文列表。
- 2016-2018 年和 2021 年可靠的官方会议/程序页面。
- 所有接受的paper rows的批量摘要、关键字、artifact 徽章、代码 URL 和数据集 URL。
- 所有 108 个已接受的paper evidence rows的完整 PDF 级技术细分，特别是 3D 高斯移动 GPU、VoxelCache、SLAMBooster 和剩余 [PACT-SF99](subfields.md#PACT-SF99) 行。
- 针对 MICRO、HPCA、ISCA、ASPLOS、PPoPP、SC 和 FPGA 系列venue的cross-venue主题矩阵。
