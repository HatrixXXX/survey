# HPCA 论文图谱分析

## 1. 会议定位

本报告中的 `HPCA` 指 IEEE International Symposium on High-Performance Computer Architecture。项目中把它作为体系结构 P0 来源处理，重点观察 high-performance processors、memory hierarchy、accelerator architecture、datacenter/server architecture、PIM/near-memory、security/correctness 和评价方法。这里不把“体系结构”当最终 topic；最终分类仍按具体瓶颈、负载和技术路线来写。对应 claim <a id="HPCA-001-C001"></a>[HPCA-001-C001](#HPCA-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 的 2016-2024 主paper rows以 DBLP HPCA proceedings metadata 为基线；2021-2024 只额外补入官方 program 中的 Best of CAL / Industry 等非主 track 行；2025-2026 使用官方 program 页面。DBLP-backed 行尽量合并官方 session/track，但 abstract、keywords、artifact 仍未批量补齐。2026 已纳入官方 program 上的 Main Conference、Industry Track 和 Best of CAL 条目，但 DOI/proceedings enrichment 与 Best Paper winner 仍缺，所以该年标为 `partial`。`awards.csv` 以 TCCA HPCA Best Paper Award 和 Test-of-Time Award 页面为主；2021、2022、2025 的 Best Paper 是二级来源证据，2023、2024 来自官方 program 标记，2026 winner 仍缺来源。对应 claim <a id="HPCA-001-C002"></a>[HPCA-001-C002](#HPCA-001-C002) 到 <a id="HPCA-001-C019"></a>[HPCA-001-C019](#HPCA-001-C019)。

| 年份 | papers.csv 记录数 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 57 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2017 | 55 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2018 | 62 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2019 | 56 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2020 | 54 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2021 | 76 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2022 | 89 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2023 | 98 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2024 | 83 | 程序完整，元数据部分 | DBLP 程序基线；官方场次/非主轨补充 |
| 2025 | 121 | 节目-完整、DOI-部分 | HPCA 官方节目页面 |
| 2026 | 125 | 节目-部分、DOI-部分 | HPCA 官方节目页面 |

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型方法 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|---|
| T10/T11 | 内存层次结构/DRAM/缓存/预取 | 访存层次、缓存、DRAM、预取和地址转换如何决定系统性能 | 缓存设计； DRAM 表征；预取；带宽分区 | 2016-2026 | 直接连接 3DGS tile/binning/sorting/alpha blending 的带宽和局部性问题 | 行级验证；相关性是推理 |
| T10/T06 | PIM / 近内存 / 存储 / 数据移动 | 当数据搬运支配能耗和时延时，计算应该放到哪里 | PIM；近记忆；存储端计算； CXL/分解 | 2016-2026 | 可迁移到端侧渲染、LLM/视觉状态管理和 FPGA 外存瓶颈分析 | 行级验证；相关性是推理 |
| T02/T06 | DNN / Transformer / AI 加速器 | AI 负载如何映射到专用数据流、稀疏执行和低 batch 推理结构 | DNN 加速器；稀疏GEMM；张量/注意力/LLM 加速 | 2016-2026 | 为神经渲染/3DGS 的算子拆解、数据流和评价提供方法库 | 行级验证；相关性是推理 |
| T03 | 3DGS / 神经渲染 / 图形加速 | Gaussian primitive、ray tracing、rendering pipeline 和 SLAM/ARVR 负载如何落到硬件结构 | 空间分区；稀疏处理；渲染管线；减少内存流量 | 2025-2026 | 这是和用户方向最直接的 HPCA 信号，仍需逐篇读 PDF 后细分 | 行级验证；相关性是推理 |
| T08/T10 | 数据中心/云/QoS | 真实服务中的吞吐、尾延迟、公平性和资源分配如何改变架构问题 | QoS 调度；并置 workload 控制；数据中心分配 | 2016-2026 | 帮助区分论文 demo 和可部署系统约束 | 行级验证；相关性是推理 |
| T11/T12 | 安全性/正确性/评估 | 性能优化如何与安全、隔离、正确性和可复核实验相互制约 | 完整性检查；侧通道防御；建模/分析 | 2016-2026 | 提醒加速器论文不能只报 speedup，也要交代可信评价 | 行级验证；相关性是推理 |

## 4. Accepted Papers 聚类结果

本节只统计 `paper_type=accepted_paper` 的行。`topic_cluster_label` 是标题级 keyword 标注，优先命中会遮住多标签事实，例如 AQPIM 同时涉及 LLM、PIM 和 activation quantization。本轮没有批量 abstract、keyword 或 PDF enrichment，所以这里不能当作 full-text clustering。对应 claim <a id="HPCA-001-C005"></a>[HPCA-001-C005](#HPCA-001-C005) 和 <a id="HPCA-001-C010"></a>[HPCA-001-C010](#HPCA-001-C010)。

| 序号 | 簇 | papers.csv 记录数 | 状态 |
|---:|---|---:|---|
| 1 | 内存层次结构、缓存、预取和 DRAM | 152 | 临时 |
| 2 | DNN/Transformer/AI 加速器和 ML 系统 | 98 | 临时 |
| 3 | 图形、稀疏、不规则和动态 workload | 98 | 临时 |
| 4 | 安全性、侧通道、隔离和正确性 | 71 | 临时 |
| 5 | 数据中心、云、服务器 QoS 和资源分配 | 48 | 临时 |
| 6 | GPU、SIMT、向量和核心微架构 | 46 | 临时 |
| 7 | PIM、近内存、存储和数据移动 | 45 | 临时 |
| 8 | LLM、Transformer、注意力和服务架构 | 45 | 临时 |
| 9 | 基准、分析、建模、模拟和评估 | 42 | 临时 |
| 10 | 可靠性、容错性和错误恢复能力 | 38 | 临时 |
| 11 | 互连、NoC、小芯片和多核系统 | 19 | 临时 |
| 12 | 量子、近似和新兴架构 | 15 | 临时 |
| 13 | 图形、VR、光线追踪和渲染管道 | 9 | 临时 |
| 14 | 3DGS、高斯神经渲染和神经 SLAM | 6 | 临时 |
| - | 一般架构和需求审查行 | 144 | 未解决的存储桶，不是主题 |

| 时间段 | 主导主题 | 新兴主题 | 下降主题 | 备注 |
|---|---|---|---|---|
| 2016-2018 | 内存层次结构、缓存、预取和 DRAM；数据中心、云、服务器 QoS 和资源分配；图形、稀疏、不规则和动态 workload | 无断言 | 无断言 | 标题/会话级元数据集群 |
| 2019-2021 | 内存层次结构、缓存、预取和 DRAM； DNN/Transformer/AI 加速器和 ML 系统；图形、稀疏、不规则和动态 workload | 无断言 | 无断言 | 标题/会话级元数据集群 |
| 2022-2023 | 内存层次结构、缓存、预取和 DRAM； DNN/Transformer/AI 加速器和 ML 系统；图形、稀疏、不规则和动态 workload | 无断言 | 无断言 | 标题/会话级元数据集群 |
| 2024-2026 | 内存层次结构、缓存、预取和 DRAM；图、稀疏、不规则和动态 workload； LLM，Transformer、注意力和服务架构 | LLM/attention/PIM/CXL 信号 | 无断言 | 标题/会话级元数据集群 |

## 5. Award Papers 分析

| 年份 | 奖项类型 | 论文 | 作者/团队 | 主题 | milestone_candidate | 证据状态 |
|---|---|---|---|---|---|---|
| 2016 | HPCA 杰出论文奖/杰出论文 | Memristive Boltzmann Machine：用于组合优化和深度学习的硬件加速器 | Mahdi Nazm Bojnordi|Engin Ipek | dnn_transformer_ai_acceleration | yes | 已验证 |
| 2016 | HPCA 杰出论文奖/杰出论文 | TABLA：用于加速统计机器学习的统一的基于模板的框架 | Divya Mahajan|Jongse Park|Emmanuel Amaro|Hardik Sharma|Amir Yazdanbaksh|Joon Kim|Hadi Esmaeilzadeh | dnn_transformer_ai_acceleration | yes | 已验证 |
| 2017 | HPCA 最佳论文奖/获奖者 | 具有多个异构带宽源的内存层次结构的近乎最优访问分区 | Jayesh Gaur|Mainak Chaudhuri|Pradeep Ramachandran|Sreenivas Subramoney | memory_cache_prefetch_dram | yes | 已验证 |
| 2018 | HPCA 最佳论文奖/获奖者 | 数据中心时代的阿姆达尔定律：公平处理器分配的市场 | Seyed Majid Zahedi|Qiuyun Llull|Benjamin C. Lee | datacenter_cloud_server_qos | yes | 已验证 |
| 2019 | HPCA 最佳论文奖/获奖者 | Stretch：平衡 SMT 核心上的共置服务器 workload 的 QoS 和吞吐量 | Artemiy Margaritov|Siddharth Gupta|Rekai Gonzalez-Alberquilla|Boris Grot | datacenter_cloud_server_qos | yes | 已验证 |
| 2020 | HPCA 最佳论文奖/获奖者 | SIGMA: A Sparse and Irregular GEMM Accelerator with Flexible Interconnects for DNN Training | Eric Qin|Ananda Samajdar|Hyoukjun Kwon|Vineet Nadella|Sudarshan Srinivasan|Dipankar Das|Bharat Kaul|Tushar Krishna | graph_sparse_irregular_workloads | yes | 已验证 |
| 2021 | HPCA 最佳论文奖/获奖者 | Prodigy：使用硬件-软件协同设计改善数据间接不规则 workload 的内存延迟 | Nishil Talati|Kyle May|Armand Behroozi|Yichen Yang|Kuba Kaszyk|Christos Vasiladiotis|Tarunesh Verma|Lu Li|Brandon Nguyen|Jiawen Sun|John Magnus Morton|Agreen Ahmadi|Todd Austin|Michael O'Boyle|Scott Mahlke|Trevor Mudge|Ronald Dreslinski | graph_sparse_irregular_workloads | yes | needs_review |
| 2022 | HPCA 最佳论文奖/获奖者 | SupermarQ：可扩展的量子基准套件 | Teague Tomesh|Pranav Gokhale|Victory Omole|Gokul Subramanian Ravi|Kaitlin N. Smith|Joshua Viszlai|Xin-Chuan Wu|Nikos Hardavellas|Margaret Martonosi|Frederic T. Chong | simulation_profiling_modeling_evaluation | yes | needs_review |
| 2023 | HPCA 最佳论文奖/获奖者 | DIMM-Link：为近内存处理启用高效的 DIMM 间通信 | 周哲|Cong Li|Fan Yang|Opticalyu Sun | pim_near_memory_storage_data_movement | yes | 已验证 |
| 2023 | HPCA 最佳论文奖/获奖者 | 可扩展且安全的行交换：内存系统中高效且安全的行锤缓解 | Jeonghyun Woo|Gururaj Saileshwar|Prashant J. Nair | security_side_channel_correctness | yes | 已验证 |
| 2024 | HPCA 最佳论文奖/获奖者 | Pathfinding Future PIM Architectures by Demystifying a Commercial PIM Technology | Bongjoon Hyun|Taehun Kim|Dongjae Lee|Minsoo Rhu | pim_near_memory_storage_data_movement | yes | 已验证 |
| 2025 | HPCA 最佳论文奖/获奖者 | DynamoLLM：设计 LLM 推理集群以提高性能和能源效率 | Jovan Stojkovic|Chaojie 张|Íñigo Goiri|Josep Torrellas|Esha Choukse | llm_transformer_attention_serving | yes | needs_review |
| 2018 | HPCA 时间考验奖/获奖者 | 动态利用窄宽度操作数以提高处理器能力和性能 | David Brooks|Margaret Martonosi | graph_sparse_irregular_workloads | 可能已验证 | 已验证 |
| 2019 | HPCA 时间考验奖/获奖者 | 带感知器的动态分支预测 | D. A. Jimenez|C. Lin | graph_sparse_irregular_workloads | 可能已验证 | 已验证 |
| 2019 | HPCA 时间测试奖/荣誉奖 | 预测顺序关联缓存 | B. Calder|D. Grunwald|J. Emer | memory_cache_prefetch_dram | 可能已验证 | 已验证 |
| 2020 | HPCA 时间考验奖/获奖者 | A Delay Model and Speculative Architecture for Pipelined Routers | L. S. Peh|W. J. Dally | gpu_simt_core_microarchitecture | 可能已验证 | 已验证 |
| 2021 | HPCA 时间考验奖/获奖者 | 高性能微处理器的动态热管理 | D. M. Brooks|M. Martonosi | reliability_fault_tolerance_resilience | 可能已验证 | 已验证 |
| 2021 | HPCA 时间考验奖/获奖者 | Runahead Execution: An Alternative to Very Large Instruction Windows for Out-of-Order Processors | O. Mutlu|J. Stark|C. Wilkerson|Y. N. Patt | gpu_simt_core_microarchitecture | 可能已验证 | 已验证 |
| 2022 | HPCA 时间考验奖/获奖者 | 使用具有动态电压和频率缩放功能的多个时钟域的节能处理器设计 | Greg Semeraro|Grigorios Magklis|Rajeev Balasubramonian|David H. Albonesi|Sandhya Dwarkadas|Michael L. Scott | graph_sparse_irregular_workloads | 可能已验证 | 已验证 |
| 2023 | HPCA 时间考验奖/获奖者 | 预测芯片多处理器架构上的线程间高速缓存争用 | Dhruba Chandra|FeiGuo|Seongbeom Kim|Yan Solihin | memory_cache_prefetch_dram | 可能已验证 | 已验证 |
| 2024 | HPCA 时间考验奖/获奖者 | 数据使用全局历史缓冲区进行缓存预取 | Kyle J. Nesbit|James E. Smith | memory_cache_prefetch_dram | 可能已验证 | 已验证 |
| 2025 | HPCA 时间考验奖/获奖者 | 用于高效内存完整性验证的缓存和哈希树 | Blaise Gassend|G. Edward Suh|Dwaine Clarke|Marten van Dijk|Srinivas Devadas | security_side_channel_correctness | 可能已验证 | 已验证 |
| 2026 | HPCA 时间考验奖/获奖者 | 评估用于多核和多处理器系统的 MapReduce | Colby Ranger|Ramanan Raghuraman|Arun Penmetsa|Gary Bradski|Christos Kozyrakis | simulation_profiling_modeling_evaluation | 可能已验证 | 已验证 |

奖项只说明 HPCA/TCCA 当年认可或 Test-of-Time 认可，不自动证明本项目里的长期技术影响。2021、2022、2025 Best Paper rows 来自二级来源，`verification_status=needs_review`，`missing_fields` 里保留 `canonical_award_source`。2023 官方 program 同时标出 DIMM-Link 和 Row-Swap 两条 Best Paper；2024 Pathfinding 来自官方 program。2026 Best Paper winner 本轮仍缺可复核来源。

## 6. 代表论文清单

| 论文 | 角色 | WHY / HOW / WHAT / IMPACT | claim |
|---|---|---|---|
| Memristive Boltzmann 机：用于组合优化和深度学习的硬件加速器 | milestone_candidate | WHY: HPCA 2016年杰出论文；组合优化和深度学习的加速器路线。 HOW/WHAT：源行映射到 `DNN/Transformer/AI accelerator and ML systems`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C030"></a>[HPCA-001-C030](#HPCA-001-C030) |
| 具有多个异构带宽源的内存层次结构的近乎最优访问分区 | milestone_candidate | WHY：HPCA 2017 年最佳论文；异构带宽内存层次结构路线。 HOW/WHAT：源行映射到 `Memory hierarchy, cache, prefetching, and DRAM`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C031"></a>[HPCA-001-C031](#HPCA-001-C031) |
| 数据中心时代的阿姆达尔定律：公平处理器分配的市场 | milestone_candidate | WHY：HPCA 2018 年最佳论文；数据中心资源分配和公平路线。 HOW/WHAT：源行映射到 `Datacenter, cloud, server QoS, and resource allocation`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C032"></a>[HPCA-001-C032](#HPCA-001-C032) |
| Stretch：平衡 SMT 核心上的共置服务器 workload 的 QoS 和吞吐量 | milestone_candidate | WHY：HPCA 2019 年最佳论文；共置服务器 QoS/吞吐量路由。 HOW/WHAT：源行映射到 `Datacenter, cloud, server QoS, and resource allocation`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C033"></a>[HPCA-001-C033](#HPCA-001-C033) |
| SIGMA: A Sparse and Irregular GEMM Accelerator with Flexible Interconnects for DNN Training | milestone_candidate | WHY：HPCA 2020 年最佳论文；稀疏且不规则的 GEMM accelerator 路线。 HOW/WHAT：源行映射到 `Graph, sparse, irregular, and dynamic workloads`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C034"></a>[HPCA-001-C034](#HPCA-001-C034) |
| GSArch：通过架构支持打破 3D Guassian Splatting 训练中的内存障碍 | 前沿 | WHY：3DGS/神经渲染加速路线；标题保留源拼写。 HOW/WHAT：源行映射到 `3DGS, Gaussian neural rendering, and neural SLAM`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C035"></a>[HPCA-001-C035](#HPCA-001-C035) |
| AQPIM：通过内存激活量化打破 LLM 的 PIM 容量墙 | 前沿 | WHY：LLM 与 HPCA 相邻行。 HOW/WHAT：源行映射到 `LLM, PIM, and activation quantization`。这是一个多标签行；单个簇只是一个读取句柄。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C036"></a>[HPCA-001-C036](#HPCA-001-C036) |
| Cambricon-GS：具有高斯像素混合并行性的 3D 高斯泼溅训练加速器 | 前沿 | WHY：3DGS/神经渲染加速路线。 HOW/WHAT：源行映射到 `3DGS, Gaussian neural rendering, and neural SLAM`。 IMPACT：impact_unverified 超出记录的奖励/计划状态，除非单独审核。 | <a id="HPCA-001-C037"></a>[HPCA-001-C037](#HPCA-001-C037) |
| GRTX：基于 3D 高斯渲染的高效光线追踪 | 前沿 | WHY：图形/神经渲染加速路线。 HOW/WHAT：源行映射到 `3DGS, Gaussian neural rendering, and neural SLAM`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C038"></a>[HPCA-001-C038](#HPCA-001-C038) |
| Splatonic：通过稀疏处理对 3D 高斯 Splatting SLAM 的架构支持 | 前沿 | WHY：3DGS/神经渲染加速路线。 HOW/WHAT：源行映射到 `3DGS, Gaussian neural rendering, and neural SLAM`。 IMPACT：impact_unverified 超出记录的奖励/计划状态，除非单独审核。 | <a id="HPCA-001-C039"></a>[HPCA-001-C039](#HPCA-001-C039) |
| 退休安全漏洞利用 | milestone_candidate | WHY：安全/正确性路线。 HOW/WHAT：源行映射到 `Security, side channels, isolation, and correctness`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C040"></a>[HPCA-001-C040](#HPCA-001-C040) |
| AsyncDIMM：在基于 DIMM 的近内存处理中实现异步执行 | 前沿 | WHY：PIM/近内存路由。 HOW/WHAT：源行映射到 `PIM, near-memory, storage, and data movement`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C041"></a>[HPCA-001-C041](#HPCA-001-C041) |
| PAISE：PIM - 基于 Transformer 的 LLM | 前沿 | WHY 的加速推理调度引擎：Transformer/attention/LLM - 相邻 HPCA 行。 HOW/WHAT：源行映射到 `LLM, Transformer, attention, and serving architecture`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C042"></a>[HPCA-001-C042](#HPCA-001-C042) |
| $C^3$：CXL 异构架构一致性控制器 | 前沿 | WHY：CXL/分解内存路由。 HOW/WHAT：源行映射到 `PIM, near-memory, storage, and data movement`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C043"></a>[HPCA-001-C043](#HPCA-001-C043) |
| 推进薛定谔式量子模拟的全栈加速 | tool_benchmark | WHY：模拟/建模/评估路线。 HOW/WHAT：源行映射到 `Benchmark, profiling, modeling, simulation, and evaluation`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C044"></a>[HPCA-001-C044](#HPCA-001-C044) |
| AutoGNN：端到端硬件驱动的图形预处理，以增强 GNN 性能 | 前沿 | WHY：图形或不规则 workload 路径。 HOW/WHAT：源行映射到 `Graph, sparse, irregular, and dynamic workloads`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C045"></a>[HPCA-001-C045](#HPCA-001-C045) |
| PIM-malloc：用于内存处理的快速且可扩展的动态内存分配器 (PIM) 架构 | 前沿 | WHY：PIM/近内存路由。 HOW/WHAT：源行映射到 `PIM, near-memory, storage, and data movement`。 IMPACT：impact_unverified 超出记录的奖项/计划状态，除非单独审核。 | <a id="HPCA-001-C046"></a>[HPCA-001-C046](#HPCA-001-C046) |

扩展阅读建议：优先从 `papers.csv` 中 `representative_role != none` 的行开始，再按 HPCA-C01、HPCA-C02、HPCA-C03、HPCA-C04 和 HPCA-C10 过滤近年论文。这个清单按解释价值和来源可追溯性选，不按引用数排序。

## 7. 发展脉络

- 2016-2018：DBLP/title 证据显示 memory/cache、early ML accelerator 和 datacenter allocation 都在主程序里。2016 两个 Distinguished Paper 是 Memristive Boltzmann Machine 和 TABLA；2017/2018 Best Paper 分别落在 heterogeneous bandwidth memory hierarchy 和 datacenter fair allocation。
- 2019-2021：Stretch、SIGMA、Prodigy 这几条 award-backed row 把 server QoS、sparse/irregular GEMM 和 memory-latency hardware/software co-design 放进同一阶段。这里的判断只基于题名、奖项和 session，不包含引用影响。
- 2022-2023：SuperMarQ、DIMM-Link、Row-Swap 这些 award/source-backed row 分别指向 benchmarking、near-memory communication 和 memory-system security。PIM、memory/cache、AI accelerator、security/correctness 仍是主信号；没有 abstract/PDF 批量数据，不能再细分成稳定子学派。
- 2024-2026：LLM/attention、PIM/CXL/near-memory、cloud-native inference、3DGS/graphics acceleration 和 evaluation/modeling 的 title/session 信号增加。直接命中 3DGS/3D Gaussian Splatting 的标题数为 5；长期影响需要 citation/artifact audit。

| 技术路线 | 核心问题 | 方法变化 | 证据 |
|---|---|---|---|
| 内存层次结构/异构带宽 | 容量、带宽、时延、预取、地址转换如何限制系统 | 缓存/DRAM/预取 -> 异构带宽分区 | <a id="HPCA-001-C006"></a>[HPCA-001-C006](#HPCA-001-C006)； <a id="HPCA-001-C012"></a>[HPCA-001-C012](#HPCA-001-C012) |
| PIM / 近内存 / CXL 数据移动 | 当数据搬运支配成本时，计算和控制应放在内存层次的哪个位置 | 近内存/PIM -> inter-DIMM/CXL/分解内存 -> PIM-for-LLM | <a id="HPCA-001-C013"></a>[HPCA-001-C013](#HPCA-001-C013) |
| 神经/张量加速器 | ML/DNN 负载如何在数据流、低精度、片上存储之间取舍 | 统计 ML 加速器 -> 张量/DNN 数据流 | <a id="HPCA-001-C007"></a>[HPCA-001-C007](#HPCA-001-C007) |
| 稀疏/不规则/图形执行 | 稀疏张量、图、间接访存如何避免负载不均和访存发散 | graph/PIM -> 稀疏 GEMM/DNN 训练 -> 数据间接 H/S 协同设计 | <a id="HPCA-001-C017"></a>[HPCA-001-C017](#HPCA-001-C017) |
| LLM /注意力/服务架构 | Transformer/LLM 推理的状态、能耗、集群吞吐和时延如何共同优化 | 注意力/Transformer信号 -> LLM 服务集群和 PIM/量化行 | <a id="HPCA-001-C014"></a>[HPCA-001-C014](#HPCA-001-C014) |
| 3DGS 和图形加速 | 显式 Gaussian primitive、ray tracing、AR/VR rendering 和 SLAM pipeline 如何被硬件化 | 2025 出现 Gaussian rendering/training rows，2026 出现 3D Gaussian Splatting training、rendering 和 SLAM rows | <a id="HPCA-001-C009"></a>[HPCA-001-C009](#HPCA-001-C009); <a id="HPCA-001-C016"></a>[HPCA-001-C016](#HPCA-001-C016) |
| 数据中心 QoS | colocated workloads 如何平衡公平、吞吐和尾延迟 | 资源分配 -> QoS 感知 SMT/服务器控制 -> 云原生推理 | <a id="HPCA-001-C015"></a>[HPCA-001-C015](#HPCA-001-C015) |
| 评估和方法 | 架构主张如何被测量和解释 | 表征/建模/分析/基准行重复出现，但增加需要abstract-level审计 | <a id="HPCA-001-C018"></a>[HPCA-001-C018](#HPCA-001-C018) |

## 8. 作者/团队线索与机构复核点

本节只写 HPCA corpus 内的作者字符串频次，不写团队排名。DBLP 行没有稳定 affiliation 字段，同名作者和机构变化都没有消歧；这些行只能作为后续读论文和查机构的入口。

| 作者字符串 | corpus 内论文数 | 主要 topic | 代表成果 | 证据状态 |
|---|---:|---|---|---|
| Onur Mutlu | 27 | 内存层次结构、缓存、预取和 DRAM；基准测试、分析、建模、模拟和评估；总体架构和需求审查行 | GPU 系统的切换感知压缩案例； ChargeCache：通过利用行访问局部性来减少 DRAM 延迟；低成本互连子阵列 (LISA)：在 DRAM | 验证标题、作者消歧 needs_review |
| Nam Sung Kim | 17 | 中实现快速子阵列间数据移动 内存层次结构、缓存、预取和 DRAM； LLM，Transformer、注意力和服务架构；一般架构和需求审查行 | 通过扭曲内操作数值相似性来近似扭曲； DUANG：非对称内存系统中快速、轻量级的页面迁移； ScalCore：设计电压可扩展性的内核 | 验证标题、作者消歧 needs_review |
| Jung Ho Ahn | 15 | 内存层次结构、缓存、预取和 DRAM； LLM，Transformer、注意力和服务架构；安全性、侧通道、隔离和正确性 | 未来 DRAM 设备的缺陷分析和经济有效的弹性架构； SOUP-N-SALAD：通过非对称 DRAM 微架构减少分配不经意的访问延迟； Web 搜索的内存层次结构 | 验证标题、作者消歧 needs_review |
| Minyi Gui | 15 | LLM，Transformer、注意力和服务架构； DNN/Transformer/AI 加速器和 ML 系统；数据中心、云、服务器 QoS 和资源分配 | 同步多内核 GPU：通过细粒度共享的多任务吞吐量处理器；非对称弹性：利用任务级幂等性实现基于加速器的系统中的瞬态错误恢复； Tacker：Tensor-CUDA 核心内核融合，用于提高 GPU 利用率，同时确保 QoS | 验证标题、作者消歧 needs_review |
| Josep Torrellas | 14 | 内存层次结构、缓存、预取和 DRAM；总体架构和需求审查行；数据中心、云、服务器 QoS 和资源分配 | ScalCore：设计电压可扩展性的核心； SCsafe：连续、精确地记录顺序一致性违规；记录重放架构作为通用安全框架 | 验证标题、作者消歧 needs_review |
| Tushar Krishna | 13 | 图、稀疏、不规则和动态 workload；总体架构和需求审查行；互连、NoC、chiplet 和多核系统 | Static Bubble：无死锁不规则片上拓扑的框架； ALRESCHA：轻量级可重构稀疏计算加速器； DRAIN：任意不规则网络的死锁消除 | 验证标题、作者消歧 needs_review |
| 首医印 | 12 | DNN/Transformer/AI 加速器和 ML 系统； LLM，Transformer、注意力和服务架构；一般架构和需求审查行 | FuseKNA：深度神经网络基于融合内核卷积的加速器；用于可扩展 DNN 加速器的基于原子数据流的图形级 workload 编排；向上数据包弹出可消除基于模块化 Chiplet 的系统中的死锁 | 验证标题、作者消歧 needs_review |
| 钱学海 | 12 | DNN/Transformer/AI 加速器和 ML 系统；图、稀疏、不规则和动态 workload；内存层次结构、缓存、预取和 DRAM | PipeLayer：基于 ReRAM 的流水线深度学习加速器； G-TSC：GPU 的基于时间戳的一致性； GraphP：通过高效数据分区减少基于 PIM 的图形处理的通信 | 验证标题、作者消歧 needs_review |
| 张友涛 | 12 | 内存层次结构、缓存、预取和 DRAM；数据中心、云、服务器 QoS 和资源分配；安全性、侧通道、隔离性和正确性 | 恢复截断以提高未来 DRAM 系统的性能； Simultaneous Multikernel GPU：通过细粒度共享的多任务吞吐量处理器；服务器设置中有效内存带宽共享的协作路径-ORAM | 验证标题、作者消歧 needs_review |
| Carole-Jean Wu | 11 | DNN/Transformer/AI 加速器和 ML 系统；总体架构和需求审查行；数据中心、云、服务器 QoS 和资源分配 | 通过概率 QoS 保证平衡性能和能耗，改善智能手机用户体验； LATTE-CC：针对节能 GPU 的延迟容忍感知自适应缓存压缩管理； Facebook 的机器学习：理解边缘推理 | 验证标题、作者消歧 needs_review |

下面是团队级线索。这里使用“repeated HPCA activity signal”，不是“领跑团队”排名；机构映射只有在有主页或多篇 HPCA 标题共同支撑时才写，仍需 per-paper affiliation 审计。

| 团队/线索 | 机构 | 人员 | 主题 | 代表性论文 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|
| SAFARI 研究小组 signal | ETH 苏黎世；旧行可能包括 CMU 或行业合作者 | Onur Mutlu、Hasan Hassan、Saugata Ghose、Ataberk Olgun、Mohammad Sadrosadati | DRAM/cache、RowHammer、PIM、DRAM 特性 | ChargeCache； LISA；软MC；块锤； CoMeT/MIMDRAM | 2016-2022, 2024-2026 | 已验证信号，从属关系 needs_review；声称 <a id="HPCA-001-C120"></a>[HPCA-001-C120](#HPCA-001-C120) |
| Synergy Lab 信号 | 佐治亚理工学院 | Tushar Krishna、Hyoukjun Kwon、Ananda Samajdar | 稀疏 DNN/GEMM、不规则数据流、NoC | 静态气泡； ALRESCHA； DRAIN； SIGMA; VEGETA | 2017, 2020-2023, 2025-2026 | 已验证信号，从属关系 needs_review；声称 <a id="HPCA-001-C121"></a>[HPCA-001-C121](#HPCA-001-C121) |
| Minsoo Rhu 组信号 | KAIST；早期 NVIDIA/行业关系需要逐篇审核 | Minsoo Rhu、Yujeong Choi、Youngeun Kwon、Bongjoon Hyun、Dongjae Lee | NPU 调度、推荐培训、商业 PIM、PIM 运行时 | PREMA；惰性批处理；张量铸造；寻路PIM； PIM-malloc | 2017-2026 | needs_review；声称 <a id="HPCA-001-C122"></a>[HPCA-001-C122](#HPCA-001-C122) |
| Meta/Facebook AI 基础设施信号 | Meta/Facebook 加学术合作者 | Carole-Jean Wu、Kim Hazelwood、王晓东、David Brooks | ML 推理、推荐系统、边缘/数据中心 AI | Facebook 的应用 ML； Facebook 的机器学习； Facebook DNN 录制；赫拉克勒斯 | 2018-2025 | needs_review;声称<a id="HPCA-001-C123"></a>[HPCA-001-C123](#HPCA-001-C123) |
| SNU/UIUC/韩国内存-PIM信号 | 首尔国立大学，UIUC，三星/行业贡献者；隶属关系需要审核 | Jung Ho Ahn、Nam Sung Kim、Jae W. Lee、Tae Jun Ham | DRAM 可靠性、CXL-PNM、Transformer/LLM PIM、安全 CXL 内存 | 缺陷分析；秘银； SHADOW; LPDDR CXL-PNM; LILo/救援 | 2017-2026 | needs_review；声称 <a id="HPCA-001-C124"></a>[HPCA-001-C124](#HPCA-001-C124) |
| FAST 实验室信号 | 佐治亚理工学院 | Moinuddin K. Qureshi、Anish Saxena、Hritvik Taneja | RowHammer、内存压缩、DDR5/内存系统 | 透明内存压缩； START；自动RFM； BARD/MIRZA/SALT | 2016, 2018-2019, 2022, 2024-2026 | 已验证信号，从属关系 needs_review；claim <a id="HPCA-001-C125"></a>[HPCA-001-C125](#HPCA-001-C125) |
| Prashant Nair 内存安全信号 | 机构映射需要每篇论文审核 | Prashant J. Nair、Gururaj Saileshwar、Jeonghyun Woo、Aamer Jaleel | RowHammer、安全内存、ECC/完整性 | SYNERGY；保障;行交换； DAPPER/QPRAC | 2016, 2018, 2022-2025 | needs_review;声称 <a id="HPCA-001-C126"></a>[HPCA-001-C126](#HPCA-001-C126) |
| SJTU Leng/Guo 集群信号 | 上海交通大学；协作需要审核 | Jingwen Leng、Minyi Gui、Quan Chen、Yu Feng、Zihan Liu | GPU/LLM 内核融合、量化、代码生成、无服务器 LLM、3DGS | 塔克；奇美拉； MANT; VQ-LLM;斯柏拉式 | 2022-2026 | needs_review;声称 <a id="HPCA-001-C127"></a>[HPCA-001-C127](#HPCA-001-C127) |
| 清华 Yin/Wei/Liu/Hu 簇信号 | 清华；密集2026年合着需求审核 | 首医印、Yang Hu、Shaojun Wei、Leibo Liu、Huizheng Wang | DNN 加速器、晶圆级/小芯片、DCIM 可靠性、LLM 训练 | FuseKNA；原子数据流； EFFACT/林肯； PADE/ReThermal/TEMP/WATOS | 2021-2026 | needs_review；声称 <a id="HPCA-001-C128"></a>[HPCA-001-C128](#HPCA-001-C128) |
| HUST 图/GNN 系统信号 | 华中科技大学及合作者；薛静灵隶属需求审核 | 廖晓飞、海金、王清刚、姚鹏程、薛静灵 | 图、超图、GNN 加速、PIM/in-storage | DepGraph；超图；斯卡拉图； FlashGNN； MeHyper | 2021-2026 | needs_review;claim <a id="HPCA-001-C129"></a>[HPCA-001-C129](#HPCA-001-C129) |
| Torrellas 加上 Microsoft/UIUC 信号 | UIUC 加上 Microsoft 和行业合作者；需要从属关系审计 | Josep Torrellas、Jovan Stojkovic、Esha Choukse、Íñigo Goiri | 无服务器、分布式一致性、LLM 集群 | SpecFaaS；和睦;动力LLM； AccelFlow | 2023-2026 以及旧版托雷拉斯行 | needs_review；声称 <a id="HPCA-001-C130"></a>[HPCA-001-C130](#HPCA-001-C130) |

协作模式也只作为读论文入口，不写成团队排名。

| 协作线索 | 连接主题 | 使用方式 | 复核要求 |
|---|---|---|---|
| Mutlu / Ghose / SAFARI 线 | DRAM、PIM、reliability/security | memory-system 论文入口 | 需要作者实体和机构年份复核 |
| Qureshi / Nair 线 | memory movement、RowHammer/security | memory movement 与安全交叉入口 | 需要作者实体和机构年份复核 |
| Ahn / Kim / Lee 线 | DRAM reliability、PIM/CXL、LLM memory | memory reliability 到 LLM memory 的阅读入口 | 需要作者实体和机构年份复核 |
| Qian / Chen / Li 线 | ReRAM/PIM DNN、graph acceleration | PIM DNN 与 graph acceleration 入口 | 需要作者实体和机构年份复核 |
| HUST / Xue 线 | graph、hypergraph、GNN | graph/GNN 系统入口 | 需要作者实体和机构年份复核 |
| SJTU Leng / Guo 线 | 2022-2026 LLM kernel、codegen、3DGS 标题 | LLM kernel/codegen/3DGS 入口 | 需要作者实体和机构年份复核 |
| EPiQC quantum collaboration | benchmark、control | quantum benchmark/control 入口 | 需要作者实体和机构年份复核 |

## 9. 对博士入门者的阅读路线

必读 10 篇：优先读 2016-2020 TCCA Best Paper/Distinguished Paper rows，再补 HPCA-C01/HPCA-C02/HPCA-C03 中近三年的 LLM/PIM/memory rows。

扩展 20 篇：从 `papers.csv` 中筛选 `representative_role != none`、`topic_cluster_id in {HPCA-C01,HPCA-C02,HPCA-C03,HPCA-C04,HPCA-C10}` 的行。这样能覆盖 AI accelerator、memory hierarchy、datacenter QoS、PIM 和评价方法，而不是只沿一个热门方向读。

适合跟踪的近年方向：LLM/attention inference architecture、PIM/CXL/near-memory、cloud-native AI inference characterization、sparse/irregular GEMM、memory integrity/security、profiling/modeling/evaluation。

## 10. 与我的方向的连接点

直接方向：HPCA 2016-2026 中有 5 条标题直接命中 3DGS / 3D Gaussian Splatting，对应 claim [HPCA-001-C009](#HPCA-001-C009)。直接命中行包括：GSArch: Breaking Memory Barriers in 3D Guassian Splatting Training via Architectural Support; Cambricon-GS: An Accelerator for 3D Gaussian Splatting Training with Gaussian-Pixel Hybrid Parallelism; GRTX: Efficient Ray Tracing for 3D Gaussian-Based Rendering; ORANGE: Exploring \underline{O}ckham's \underline{R}azor for Neural Rendering by \underline{A}ccelerating 3DGS on \underline{N}PUs with \underline{GE}MM-Friendly Blending and Balanced Workloads; Splatonic: Architecture Support for 3D Gaussian Splatting SLAM via Sparse Processing。

相邻方向：如果把 Gaussian-based rendering、ray tracing、AR/VR 和 SLAM 也算进来，本轮可追踪到 13 条相关标题，对应 claim [HPCA-001-C016](#HPCA-001-C016)。这些论文适合用来拆 Gaussian 数据结构、tile/binning/sorting、alpha blending、帧间复用、外存带宽和 pipeline bubble，但需要逐篇核对 PDF 和实验设定。

FPGA 连接属于推断，不是 HPCA corpus 直接给出的结论。这里的可迁移价值主要是问题定义和评价口径：bandwidth、latency、utilization、buffering、baseline fairness 和系统集成成本必须写清楚，不能只报相对 CPU/GPU 的 speedup 或能耗比。

## 11. 缺失来源

- 2016-2026 年统一 HPCA 官方会议记录/session/DOI 源。
- 批量 IEEE/ACM 摘要、关键字、PDF 和 artifact 徽章导出。
- 2022 年和 2025 年规范最佳论文来源，以及出现后的 2026 年官方最佳论文获奖者来源。
- 引用结构、后续采用、artifact/代码重用、基准标准化和超越首次引用快照的行业/工具链采用审核。
- 与 ISCA、MICRO、ASPLOS、DAC、ICCAD 和 FPGA/FCCM/FPL/FPT 的cross-venue比较。
- 作者/隶属关系/团队entity disambiguation。
