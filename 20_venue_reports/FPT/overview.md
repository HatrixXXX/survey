# FPT 论文图谱分析

## 1. 会议定位

本报告的 `FPT` 指 International Conference on Field Programmable Technology，也常在 IEEE/DBLP 元数据中写作 ICFPT。FPT 是亚太地区 field-programmable technology 会议，主题覆盖 field-programmable devices、reconfigurable computing systems、FPGA design tools、architectures、device technology 和应用加速。该定位由 FPT 2025/2026 官方网站和 CFP 支撑，对应 claim <a id="FPT-001-C001"></a>[FPT-001-C001](#FPT-001-C001)、<a id="FPT-001-C016"></a>[FPT-001-C016](#FPT-001-C016)。

FPT 和 FPGA/FCCM/FPL 同属可重构计算核心来源，但调性更宽：除了 HLS、routing、architecture，也持续容纳机器人、视觉、SLAM、量化 DNN、GNN、LLM、security、CGRA、NoC、HPC 和 education/competition 类内容。读 FPT 时不应只把它当作“FPGA 应用列表”，而要看每篇论文解决的瓶颈：编译/映射、片上互连、存储、低精度、实时边缘负载，还是安全/可验证性。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 的 2016-2024 主体来自 Crossref/IEEE ICFPT proceedings metadata，并过滤 author index、table of contents、committee、supporters、title page、preface 等 front matter。2025 同时纳入 Crossref/IEEE rows 和官方 program-only rows；后者用 `source_type=official_page`、空 DOI、具体 `track/paper_type` 标记，避免和 DOI proceedings 主体混淆。2024 和 2025 用官方 program 页面补 session/track；其他年份没有批量补 session。2026 只写一个 partial marker：FPT 2026 官网列出会议时间为 2026-12-07 到 2026-12-10，Conference Track notification 为 2026-08-21；当前日期是 2026-06-27，accepted-paper 和 award list 尚未公开。对应 claim <a id="FPT-001-C002"></a>[FPT-001-C002](#FPT-001-C002)、<a id="FPT-001-C003"></a>[FPT-001-C003](#FPT-001-C003)。

| 年 | 论文.csv 行 | 地位 | 主要来源 |
|---|---:|---|---|
| 2016 | 67 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2017 | 53 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2018 | 83 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2019 | 89 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2020 | 48 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2021 | 51 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2022 | 55 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2023 | 56 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2024 | 35 | 完全的 | Crossref/IEEE 会议记录元数据； DBLP 索引作为辅助锚点 |
| 2025 | 66 | 完全的 | Crossref/IEEE 会议元数据加上 FPT 2025 官方节目专用行 |
| 2026 | 1 | partial | FPT 2026 官方网站和 CFP |

奖项来自 TCFPGA FPT Best Paper Awards 页面。该页覆盖本轮范围内的 2016、2017、2018、2019、2021、2022、2023、2024、2025；未列 2020，本报告在 `awards.csv` 中保留 missing row，不推断 2020 没有奖项。第二波复核后，2024 GraphNoC 和 2025 JEDI-Linear 的 winner 身份由 TCFPGA 官方奖项 ledger 验证，`awards.csv` 标为 `verified`；年度 FPT 官网或 proceedings front matter 的二次确认仍是剩余缺口。2026 奖项未公开，属于 `normal_2026_partial`。对应 claim <a id="FPT-001-C007"></a>[FPT-001-C007](#FPT-001-C007)、<a id="FPT-001-C017"></a>[FPT-001-C017](#FPT-001-C017)、<a id="FPT-001-C018"></a>[FPT-001-C018](#FPT-001-C018)、<a id="FPT-001-C048"></a>[FPT-001-C048](#FPT-001-C048)、<a id="FPT-001-C049"></a>[FPT-001-C049](#FPT-001-C049)。

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型方法 | 代表论文 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|---|---|
| T07/T12 | HLS、CAD、路由、DSE | 如何把算法或设计描述转成可实现、可预测、可调试的 FPGA 实现 | HLS DSE、MLIR、路由预测、重定时、QoR 估计、比特流/等价 | 程序二进制文件综合、GRAFT/AUGER/HGBO-DSE、HBMalloc、HOLMES-HLS、GraphNoC | 2016-2025 | 直接服务 3DGS/机器人负载从算法到 RTL/HLS 的落地 | 验证行、临时簇 |
| T02/T05 | DNN、Transformer、LLM 和低精度执行 | 如何把神经网络负载映射到 LUT/BRAM/DSP/HBM/AIE 等资源 | BNN、低精度、LUT inference、Transformer attention、GNN、LLM nonlinear units | 抖动NN、PolyLUT、FINN-T、FAMOUS、JEDI-Linear、FlightOPU | 2016-2025 | 和端侧推理、VLA、3D/视觉前馈模型强相关 | 验证行、临时簇 |
| T06/T10 | 内存/数据流/NoC/网络 | 数据搬运、NoC、HBM、streaming 和多 FPGA 通信如何限制系统效率 | 脉动/数据流、HBM 内存管理、NoC 预测、多 FPGA 图形分析、流缓冲区 | 分区脉动Arrays、Swift、HBMalloc、TableCache、Fast Multi-Tau | 2016-2025 | 对 3DGS tile/binning/sorting/alpha blending 的数据流分析有迁移价值 | 验证行、临时簇 |
| T03/T04 | 机器人、SLAM、视觉、边缘、3D | 实时视觉和机器人感知管线如何在 FPGA 上低延迟运行 | ORB/SLAM、LiDAR/视觉 SLAM、基于事件的视觉、边缘视觉、点云、遥感 | FPGA ORB、FSLAM、硬件高效关键点选择、FRME、EdgeCT、PointODE | 2017-2025 | 是用户机器人/3D 视觉方向的最直接 FPT 入口 | 验证行、临时簇 |
| T05/T12 | 安全性、PQC、PUF、可靠性 | 如何保护 FPGA bitstream/IP/multi-tenant 系统并实现 crypto workloads | PUF 克隆、网表反向工程、PQC/FHE、CAN 安全、侧通道隔离 | 克隆不可克隆、CAN 不会被黑客攻击、HHEML、IsoFPGA | 2016-2025 | 与可信边缘/多租户 FPGA 平台有关，但不是当前主方向 | 验证行、临时簇 |
| T06/T12 | CGRA、覆盖、可编程结构 | FPGA/CGRA/overlay 的可编程性、拓扑和算术结构如何设计 | CGRA DSE、可编程结构、嵌入式 FPGA、AI 引擎、退火/量子加速器 | Into the Third Dimension、FastCGRA、AUGER、CGRA-HD、MPD | 2018-2025 | 帮助判断“可重构性”何时值得保留 | 验证行、临时簇 |

## 4. Accepted Papers 聚类结果

本节只使用 title/session/track 层面的 provisional clustering。没有批量使用摘要、关键词和引用图，因此不能把这些 cluster 直接当成稳定 taxonomy。对应 claim <a id="FPT-001-C006"></a>[FPT-001-C006](#FPT-001-C006)、<a id="FPT-001-C010"></a>[FPT-001-C010](#FPT-001-C010)。

| 簇 | 论文.csv 行 | 地位 |
|---|---:|---|
| 其他现场可编程技术论文 | 134 | 临时 |
| ML, DNN、Transformer、LLM 和低精度加速器 | 126 | 临时 |
| 以内存为中心、HBM、NoC、流、网络和数据移动 | 91 | 临时 |
| HLS、编译器、CAD、路由和设计空间探索 | 82 | 临时 |
| CGRA、覆盖、FPGA 架构、算术和可编程结构 | 54 | 临时 |
| 机器人、SLAM、视觉、3D、边缘和传感 workload | 41 | 临时 |
| 安全、加密、PUF、FHE 和可靠的 FPGA 系统 | 30 | 临时 |
| 基准、框架、云 FPGA 和虚拟化 | 28 | 临时 |
| HPC、图形、科学、通信和领域加速器 | 17 | 临时 |

| 时间段 | 主导主题 | 新兴主题 | 代表论文 | 备注 |
|---|---|---|---|---|
| 2016-2018 | HLS、NoC/overlay、DNN/BNN、加密、内存丰富 FPGA | ORB/SLAM、OpenCL CNN、低位神经网络 | MTJ BRAM、二进制到加速器综合、Dither NN、PipeCNN | paper rows主要由 IEEE/Crossref 元数据支撑；session 多数缺失 |
| 2019-2021 | 脉动/数据流、DNN 映射、机器人/SLAM、开源/工具流、内存/NoC | 决策林、FPGA 路由/架构建模、HPC 流计算 | 分区脉动数组、决策林加速器、FastCGRA、FLOWER | 2020 award source缺口保留 |
| 2022-2023 | CGRA/HLS DSE、Transformer/GNN、security/PUF、robotics/SLAM、3D可重构架构 | 云 FPGA 租户编译、混合精度 BRAM GEMM、基于事件的视觉 | 克隆不可克隆、PolyLUT、进入三维、FSLAM | 2023 有 journal-track abstract rows，CSV 用 `journal_article` 标注 |
| 2024-2025 | 路由/CAD、HLS DSE、Transformer/LLM/GNN、SLAM/edge 视觉、HBM/内存 | HBMalloc、FINN-T、FAMOUS、FRME、FlightOPU、EdgeCT、LL-ViT | GraphNoC、JEDI-Linear、FINN-T、HBMalloc、FRME | 2024/2025 session 来自官方 program，可作为 stronger source |

## 5. Award Papers 分析

| 年 | 奖项 | 论文 | 作者 | 主题 | 地位 |
|---|---|---|---|---|---|
| 2016 | 获胜者 | 高密度、低能耗、用于内存丰富的 FPGA 的基于磁隧道结的 Block RAM | Kosuke Tatsumura|Sadegh Yazdanshenas|Vaughn Betz | memory_dataflow_network | 已验证 |
| 2017 | 获胜者 | 将程序二进制文件合成为 FPGA 带运行时依赖验证的加速器 | Shaoyi Cheng|Qijing Huang|John Wawrzynek | other_fpt | 已验证 |
| 2018 | 获胜者 | 抖动 NN：用于低位精度硬件的抖动的精确神经网络 | Kota Ando|Kodai Ueyoshi|Yuka Oba|Kazutoshi Hirose|Ryota Uematsu|Takumi Kudo|Masayuki Ikebe|浅井哲也|高前田山崎慎也|Masato Motomura | ml_dnn_transformer_low_precision | 已验证 |
| 2019 | 获胜者 | 分区 FPGA 优化的脉动阵列，带来乐趣和利润 | Long Chung Chan|Gurshaant Malik|Nachiket Kapre | reconfigurable_architecture | 已验证 |
| 2020 | 缺失 | FPT 在此运行期间，在 TCFPGA 奖项分类账中未找到 FPT 2020 年度最佳论文获奖者 |  | coverage_gap | needs_review |
| 2021 | 获胜者 | 基于先验特征空间分区的高性能且灵活的 FPGA 决策森林推理加速器 | Thiem Van Chu|Ryuichi Kitajima|Kazushi Kawamura|Jaehoon Yu|Masato Motomura | ml_dnn_transformer_low_precision | 已验证 |
| 2022 | 获胜者 | 克隆不可克隆：物理克隆 FPGA RO PUF | Hayden Cook|Jonathan Thompson|Zephram Tripp|Brad Hutchings|Jeffrey Goeders | security_crypto_dependability | 已验证 |
| 2023 | 获胜者 | PolyLUT：学习分段多项式以实现超低延迟 FPGA LUT 基于推理 | Marta Andronic|George A. Constantinides | ml_dnn_transformer_low_precision | 已验证 |
| 2023 | 获胜者 | 进入三维：架构探索3D 可重构加速设备工具 | Andrew Boutros|Fatemehsadat Mahmoudi|Amin Mohaghegh|Stephen More|Vaughn Betz | robotics_slam_vision_edge | 已验证 |
| 2024 | 获胜者 | GraphNoC：用于特定应用的图神经网络 FPGA NoC 性能预测 | Gurshaant Malik|Nachiket Kapre | memory_dataflow_network | 已验证 |
| 2025 | 获胜者 | JEDI-Linear：用于 FPGA 上 Jet 标记的快速高效图神经网络 | 阙志强|张孙|Sudarshan Paramesvaran|Emyr Clement|Katerina Karakoulaki|Christopher Brown|Lauri Laatu|Arianna Cox|Alexander Tapper|Wayne Luk|Maria Spiropulu | ml_dnn_transformer_low_precision | 已验证 |
| 2026 | 待定 | FPT 2026 年获奖者截至 2026 年 6 月 27 日尚未公开 |  | coverage_gap | normal_2026_partial |

奖项只能证明 venue-level recognition，不直接证明长期影响。2023 同时有 PolyLUT 和 Into the Third Dimension 两条 Best Paper 记录；它们分别指向低延迟 LUT inference 和 3D reconfigurable architecture exploration。2025 JEDI-Linear 将 GNN/HEP real-time inference 推到 FPT award 层面。2020 award 缺口不能被改写成“无奖项”。

## 6. 代表性论文清单

| 论文 | 角色 | WHY / HOW / WHAT / IMPACT | claim |
|---|---|---|---|
| 高级综合 - 历史的右侧 | 典范 | WHY：2016年HLS定位纸； FPT 工具流历史记录的有用起点。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C030"></a>[FPT-001-C030](#FPT-001-C030) |
| 可配置云 - 使用 FPGA 加速超大规模数据中心服务 | 典范 | WHY：2016 数据中心/云 FPGA 主题演讲风格信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C031"></a>[FPT-001-C031](#FPT-001-C031) |
| 用于存储器丰富的 FPGA 的高密度、低能耗、基于磁性隧道结的 Block RAM | 里程碑 | WHY：2016 年 FPT 最佳论文；内存丰富的 FPGA 架构信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C032"></a>[FPT-001-C032](#FPT-001-C032) |
| 加速二值化神经网络：FPGA、CPU、GPU 和 ASIC 的比较 | 典范 | WHY：与架构权衡相关的跨平台 BNN 加速比较。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C033"></a>[FPT-001-C033](#FPT-001-C033) |
| Spector：OpenCL FPGA 基准测试套件 | tool_benchmark | WHY：OpenCL 时代基准测试套件信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C034"></a>[FPT-001-C034](#FPT-001-C034) |
| 通过运行时依赖性验证将程序二进制文件合成为 FPGA 加速器 | 里程碑 | WHY：2017 年 FPT 最佳论文；二进制到加速器和运行时验证路线。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C035"></a>[FPT-001-C035](#FPT-001-C035) |
| PipeCNN：基于 OpenCL 的卷积神经网络开源 FPGA 加速器 | tool_benchmark | WHY：OpenCL/HLS 时期的开源 CNN 加速器信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C036"></a>[FPT-001-C036](#FPT-001-C036) |
| 抖动 NN：用于低位精度硬件的抖动的精确神经网络 | 里程碑 | WHY：2018 FPT 最佳论文；低位神经网络加速路线。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C037"></a>[FPT-001-C037](#FPT-001-C037) |
| DaCO：用于 FPGA 的高性能令牌数据流协处理器覆盖 | 典范 | WHY：数据流/覆盖谱系中的令牌数据流覆盖信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C038"></a>[FPT-001-C038](#FPT-001-C038) |
| 分区 FPGA 优化的脉动阵列，带来乐趣和利润 | 里程碑 | WHY：2019 FPT 最佳论文；脉动阵列分区路线。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C039"></a>[FPT-001-C039](#FPT-001-C039) |
| 基于先验特征空间分区的高性能且灵活的 FPGA 决策森林推理加速器 | 里程碑 | WHY：2021 FPT 最佳论文；非 DNN ML 推理加速器路线。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C040"></a>[FPT-001-C040](#FPT-001-C040) |
| FLOWER：用于高级综合的综合数据流编译器 | tool_benchmark | WHY：HLS 的 2021 数据流编译器信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C041"></a>[FPT-001-C041](#FPT-001-C041) |
| Hypersort：对启用 HBM 的 FPGA | 前沿 | WHY：启用 HBM 的排序/数据移动信号进行高性能并行排序。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C042"></a>[FPT-001-C042](#FPT-001-C042) |
| 在 FPGA 上加速 Transformer 神经网络以进行高能物理实验 | 前沿 | WHY：HEP workload 线中的早期 Transformer-on-FPGA 信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C043"></a>[FPT-001-C043](#FPT-001-C043) |
| FSLAM：SoC FPGA 上高效、准确的 SLAM 加速器 | 前沿 | WHY：2022 SLAM 加速器信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C044"></a>[FPT-001-C044](#FPT-001-C044) |
| PolyLUT：学习分段多项式以实现超低延迟 FPGA LUT 基于推理 | 里程碑 | WHY：2023 FPT 最佳论文； LUT-原生神经推理路线。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C045"></a>[FPT-001-C045](#FPT-001-C045) |
| 进入三维：架构探索3D 可重构加速设备工具 | 里程碑 | WHY：2023 FPT 最佳论文； 3D可重构架构探索路线。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C046"></a>[FPT-001-C046](#FPT-001-C046) |
| 关于 Xilinx 内部配置访问端口 (ICAP) 的恶意潜力 | 前沿 | WHY：FPGA 安全中的 ICAP 攻击面信号。 HOW/WHAT：源标题和主题行标识机制。 IMPACT: impact_unverified 除非仅说明venue award认可。 | <a id="FPT-001-C047"></a>[FPT-001-C047](#FPT-001-C047) |

扩展阅读建议：PipeCNN、Accelerating Binarized Neural Networks、FSLAM、FINN-T、FAMOUS、HBMalloc、Hardware-Efficient Homogenized Key-Point Selection、FRME、EdgeCT、LL-ViT、FlightOPU、Gluttonous Snake。它们适合作为用户方向的技术迁移入口，但 impact 仍需后续 citation/artifact audit。

## 7. 发展脉络和技术路线变化

2016-2018 年，FPT 的主题从传统 FPGA architecture、NoC、HLS 和 memory-rich fabric，扩展到 CNN/BNN、OpenCL、SLAM 和 crypto。这个阶段的关键问题是：新兴应用能不能映射到 FPGA，映射后是否真的获得性能/能效收益。

2019-2021 年，systolic/dataflow、低精度神经网络、robotics/SLAM、decision forest、CGRA modeling 和 HLS/dataflow compiler 变得更明显。FPT 不只是发表应用加速器，也开始反复出现“怎样让设计空间、数据流和工具链可管理”的方法论文。

2022-2023 年，Transformer、GNN、CGRA、cloud FPGA、安全/PUF、3D reconfigurable architecture 进入核心视野。PolyLUT 和 Into the Third Dimension 的 award 信号说明 FPT 同时关注算法近似/表示和底层 reconfigurable architecture。

2024-2025 年，routing/CAD 的 ML 化、HLS DSE 的自动化、HBM/memory 管理、edge vision/SLAM、LLM/Transformer/GNN 和 AI Engine/overlay 变成近年前沿。FPT 2025 官方 program 还把 artifact、design competition、journal session 和 special session 放进会议结构，说明会议已经不仅是传统 proceedings paper 形态。

| 谱系 | 核心问题 | 代表性论文 | 转折点 |
|---|---|---|---|
| HLS/CAD/DSE | FPGA 工具链如何从手调 pragma 走向预测、搜索、编译和验证 | 二进制到加速器综合、GRAFT/AUGER/HGBO-DSE、HBMalloc、HOLMES-HLS | 2023-2025 出现 GNN/Bayesian/MLIR/HBM-aware HLS 信号 |
| ML/低精度/LLM | 神经网络如何适配 LUT/BRAM/DSP/HBM/AIE | 抖动NN、PolyLUT、FINN-T、FAMOUS、JEDI-Linear、FlightOPU | 从 CNN/BNN 走向 LUT inference、Transformer、LLM nonlinear/overlay |
| OpenCL/基准/云 | FPGA 开发如何从单实验板走向可复用 benchmark、toolkit 和 cloud/datacenter 服务 | Spector、PipeCNN、hCODE/hCODE 2.0、可配置云 | 2016-2017 形成早期可复用平台和云 FPGA 信号 |
| 内存/NoC/multi-FPGA | 数据搬运、排序、graph、NoC 和多 FPGA 通信如何限制吞吐 | Hypersort、GraFF、Swift、HBMalloc、OpenFPGA-NoC、CD-LLM | HBM 和多 FPGA LLM/graph workload 将 memory/network 变成主问题 |
| 视觉/SLAM/机器人 | 低延迟感知管线如何在端侧 FPGA 上运行 | ORB 特征提取、FSLAM、FRME、EdgeCT、PointODE | 从 robot-car demos 走向 SLAM/event-based/edge vision |
| 安全性/可靠性 | FPGA 多租户、PUF、PQC/FHE 和系统安全如何落地 | 克隆不可克隆、malicious ICAP potential、SmartSSD covert channels、HHEML、CAN't Be Hacked | 2022 后安全成为持续主题而非孤立论文 |
| 可重构架构 | 为什么需要可重构、CGRA、3D/eFPGA 或 AI Engine | 进入Third Dimension、FastCGRA、AUGER、MPD、AIE相关行 | 可重构性从平台属性转向设计空间和系统集成问题 |

## 8. 团队线索和代表成果

这里的团队线索只表示 FPT corpus 内反复出现的作者/机构字符串，不是跨会议排名。姓名和机构仍需 DBLP PID、ORCID 或作者主页消歧。对应 claim <a id="FPT-001-C011"></a>[FPT-001-C011](#FPT-001-C011) 到 <a id="FPT-001-C015"></a>[FPT-001-C015](#FPT-001-C015)。

| 团队/机构线 | 主题 | 代表性论文 | 活跃年数 | 注意 |
|---|---|---|---|---|
| 复旦 FPGA 架构 / CGRA / HLS-DSE 集群 | 路由架构、CGRA 映射、HLS 探索、MLIR/HLS、DNN 工具 | FastCGRA、VIB、GRAFT/AUGER/HGBO-DSE、HBMalloc、HOLMES-HLS | 2021-2025 持续出现 | 多个中文姓名需 DBLP PID 消歧 |
| 帝国可重构计算 / FPGA ML 集群 | DNN/Transformer/GNN、低延迟推理、HLS 内存调度、HEP/jet 标记 | PolyLUT、优化 DNN 加速器压缩、JEDI-Linear、da4ml | 2016-2025 | Wayne Luk / Wai-Shing Luk 名称需合并核验 |
| 多伦多大学 FPGA CAD / 架构集群 | 布局/路由/时序 CAD、3D 可重构器件、调试 | MTJ BRAM、StateLink、Into the Third Dimension、routing/CAD rows | 2016-2025 | Betz/Stojilovic/Murray 等存在机构变化 |
| Kapre NoC/脉动/覆盖谱系 | NoC、脉动/数据流、性能预测 | 分区FPGA-优化的脉动阵列、GraphNoC | 2016-2019, 2024 | Waterloo / earlier NTU / industry lineage 不应简单合并 |
| BYU FPGA 安全/逆向工程集群 | PUF 克隆、网表逆向工程、IP 识别 | 克隆不可克隆、确保网表到比特流的等效性、Neurocore | 2022-2025 | security 影响需要更广来源复核 |
| RIKEN 可重构 HPC / 流计算 | FPGA 集群、模板/流计算、ESSPER | Senju、ESSPER 可扩展行 | 2021-2023 | moderate signal；需要补 full affiliation graph |

## 9. 对博士入门者的阅读路线

必读 10 篇：High Density MTJ Block RAMs、Synthesis of Program Binaries into FPGA Accelerators、Dither NN、Partitioning FPGA-Optimized Systolic Arrays、decision-forest accelerator、Cloning the Unclonable、PolyLUT、Into the Third Dimension、GraphNoC、JEDI-Linear。

扩展 20 篇：PipeCNN、Accelerating Binarized Neural Networks、FSLAM、FastCGRA、FLOWER、AUGER、GRAFT、M4BRAM、FINN-T、FAMOUS、HBMalloc、FRME、EdgeCT、LL-ViT、FlightOPU、Gluttonous Snake、HOLMES-HLS、LogicSparse、PointODE、FRME。

适合跟踪的近年方向：HLS DSE 自动化、routing/CAD 的 GNN/ML 方法、LUT-native/low-bit neural inference、Transformer/LLM on FPGA、视觉 SLAM 和 edge vision、HBM/memory management、FPGA security/reverse engineering。

## 10. 与我的方向的连接点

FPT 对你的 3DGS/神经渲染/FPGA 方向有三类连接。第一类是端侧视觉和 SLAM：FSLAM、Hardware-Efficient Key-Point Selection、FRME、PointODE、EdgeCT 这些论文能帮助分析实时视觉 pipeline 中 feature extraction、matching、motion estimation、point cloud 和 edge inference 的数据流。第二类是 HLS/CAD/dataflow：HBMalloc、HOLMES-HLS、FINN-T、FAMOUS、GraphNoC 等论文能提供从算法到 FPGA pipeline 的设计空间、memory hierarchy 和 NoC/BRAM/HBM 管理方法。第三类是低精度/查表/Transformer：PolyLUT、LL-ViT、JEDI-Linear、FlightOPU 等工作能帮助判断什么时候 LUT/低精度/稀疏/近似计算值得做成硬件。

本轮没有找到以 3D Gaussian Splatting 为标题核心对象的 FPT 论文，因此不能把 FPT 写成 3DGS 硬件加速已经成熟的证据。更准确的表述是：FPT 反复提供 3DGS 所需的邻近方法，包括实时视觉、SLAM、dataflow/HLS、低精度 inference、memory/NoC 和 edge deployment。对应 claim <a id="FPT-001-C008"></a>[FPT-001-C008](#FPT-001-C008)、<a id="FPT-001-C009"></a>[FPT-001-C009](#FPT-001-C009)。

## 11. 缺失来源

- 2020 FPT Best Paper 仍缺 canonical official source；TCFPGA ledger 未列 2020，不能推断为无奖项。
- 2024/2025 Best Paper winner 已由 TCFPGA official ledger 验证，但仍缺年度 FPT 官网或 proceedings front matter 的二次确认。
- 2016-2023 官方 program/session 统一抽取仍未完成。
- IEEE Xplore abstract/keyword 批量抽取仍未完成。
- 若干 deep_read 论文仍缺全文、PDF 或 artifact 复核，尤其是 2016 HLS、2017 binary synthesis、2019 systolic partitioning、2024 HBMalloc、2024 GraphNoC、2025 FRME/EdgeCT/FlightOPU 等。
- FPT 与 FPGA/FCCM/FPL/DAC/ICCAD/HOST/CHES/USENIX/体系结构会议的跨 venue 对照仍未做。
- FPT title-level scan 没有找到 3DGS、NeRF、neural rendering 或 splatting 核心论文；SLAM/edge vision/3D reconfigurable architecture 只能作为邻近 hook。abstract-level 和跨 venue 3DGS/NeRF 专门审计仍是剩余缺口。
