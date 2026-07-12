# FPGA 论文图谱分析

## 1. 会议定位

本报告中的 `FPGA` 指 ACM/SIGDA International Symposium on Field-Programmable Gate Arrays，也就是 ISFPGA/FPGA。它在本项目中作为可重构计算、FPGA architecture、CAD、HLS、工具链和 FPGA 加速器工作的核心 venue 处理。该定位来自项目 `VENUE_REGISTRY.csv` 和 ISFPGA 官方 archive 页面，对应 claim <a id="FPGA-001-C001"></a>[FPGA-001-C001](#FPGA-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 从官方 ISFPGA technical program 页面生成，`awards.csv` 以 TCFPGA Best Paper Awards 页面为主，并补充 2026 technical program 中的 runner-up 条目。共生成 accepted / industry / poster 相关记录 409 条。2026 按项目的当前年份约定标记为 `partial`；官方 program 行和 Best Paper/runner-up 事实可访问，但 DOI、citation 和后续影响尚不能完整确认，对应 claim <a id="FPGA-001-C003"></a>[FPGA-001-C003](#FPGA-001-C003)。

| 年份 | papers.csv 记录数 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 36 | 完全的 | https://isfpga.org/past/fpga2016/index_files/FPGA2016FinalProgram2_withSlides.htm |
| 2017 | 14 | 完全的 | https://isfpga.org/past/fpga2017/program.html |
| 2018 | 28 | 完全的 | https://isfpga.org/past/fpga2018/program.html |
| 2019 | 27 | 完全的 | https://isfpga.org/past/fpga2019/program.html |
| 2020 | 55 | 完全的 | https://isfpga.org/past/fpga2020/program.html |
| 2021 | 47 | 完全的 | https://isfpga.org/past/fpga2021/program/ |
| 2022 | 36 | 完全的 | https://isfpga.org/past/fpga2022/program/ |
| 2023 | 46 | 完全的 | https://isfpga.org/past/fpga2023/program/ |
| 2024 | 34 | 完全的 | https://isfpga.org/past/fpga2024/program/ |
| 2025 | 36 | 完全的 | https://isfpga.org/past/fpga2025/program/ |
| 2026 | 50 | partial | https://www.isfpga.org/program/ |

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型方法 | 代表论文 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|---|---|
| T07 | HLS/DSL/编译流程 | 从算法/IR 到可收敛 FPGA 实现 | HLS、MLIR、DSL、源到源变换、平面图感知实现 | HeteroCL、AutoBridge、RapidStream、DONGLE、HLS 的形式验证 | 2019-2026 | 直接关联算法到 RTL/HLS/工具链和 3DGS 加速落地 | 已验证论文，临时集群 |
| T02/T05 | ML/AI 加速器 | CNN/LSTM/GNN/LLM/generative model 在 FPGA 上的算子、精度和数据流映射 | 低精度、稀疏、LUT-native inference、streaming architecture | ESE、FINN、FlightLLM、FlightVGM、KANELÉ | 2016-2026 | 连接 Transformer、端侧推理、机器人 batch=1 和神经渲染邻近负载 | 已验证论文，临时集群 |
| T12 | FPGA 架构/CAD/物理封闭 | FPGA 结构、路由、布局、布局规划、时序/物理约束 | 布局/路由、架构探索、多芯片物理感知映射 | FPRESSO、AutoBridge、RapidStream | 2016-2026 | 帮助判断 FPGA 论文中的落地证据是否可信 | 已验证论文，临时集群 |
| T06/T10 | 数据流、流、内存/存储 | 数据搬运、buffer、HBM/NVMe/CXL/cache 与 streaming pipeline 的瓶颈 | 缓冲区大小调整、近内存/存储编排、收缩/流管道 | Buffer Placement、DONGLE、HBM 连接、CXL-SpecKV | 2020-2026 | 直接连接 3DGS 的排序、tile/binning、alpha blending、burst/DDR 问题 | 已验证论文，临时集群 |
| T11 | 基准测试/分析/评估 | 如何避免只用单点 speedup，建立可比较的 HLS/FPGA 评价 | 基准测试套件、微基准测试、功耗/面积估计、artifact evidence | Rosetta、Demystifying the Memory System、RISCBench | 2018-2026 | 对 profiling、PPA breakdown 和 CPU/GPU 对照直接相关 | needs_review 以确保完整性 |

## 4. Accepted Papers 聚类结果

`papers.csv` 里的 `topic_cluster_label` 是关键词加人工规则的粗标注，适合做 venue 内部浏览，不应直接当成最终 taxonomy。cluster 状态对应 claim <a id="FPGA-001-C010"></a>[FPGA-001-C010](#FPGA-001-C010)。

| 簇 | papers.csv 记录数 | 状态 |
|---|---:|---|
| 应用程序和特定领域加速器 | 107 | 临时 |
| ML/AI 加速器和低精度推理 | 99 | 临时 |
| FPGA 架构、CAD 和实现闭包 | 75 | 临时 |
| HLS、DSL 和物理感知工具流 | 56 | 临时 |
| 数据流、流和计算引擎 | 23 | 临时 |
| 内存、存储和数据移动 | 21 | 临时 |
| 云 FPGA 系统、虚拟化和安全 | 18 | 临时 |
| 稀疏和不规则 workload | 8 | 临时 |
| 基准、分析和评估 | 2 | 临时 |

subagent 聚类给出的 10 个研究簇更接近报告层面的读法，保留为 provisional：

| 集群 ID | 主题 | 活跃年份 | 代表论文/信号 | 状态 |
|---|---|---|---|---|
| FPGA-C01 | AI 模型加速器： CNN/RNN/GNN/Transformer/LLM/VGM | 2016-2026 | ESE; FINN；FlightLLM；FlightVGM；KANELÉ | 临时 |
| FPGA-C02 | LUT/量化/低精度神经计算 | 2017-2026 | FINN;逻辑收缩；树查找表； AmigoLUT | 临时 |
| FPGA-C03 | HLS/DSL/编译器/数据流生成 | 2018-2026 | Rosetta；异质CL；汽车SA； ARIES | 临时 |
| FPGA-C04 | 物理感知 HLS/时序收敛/实现扩展 | 2021-2026 | AutoBridge；快速流； Stream-HLS | 临时 |
| FPGA-C05 | 以内存为中心、HBM、近存储、分解内存 | 2020-2026 | HBM 连接； DONGLE； CXL-SpecKV | 临时 |
| FPGA-C06 | 稀疏/图/不规则/HPC 内核 | 2016-2026 | FASTCF;六分仪； HP-GNN； ACTS | 临时 |
| FPGA-C07 | FPGA 架构/结构/CAD/eFPGA | 2016-2026 | FPRESSO;路径查找器； PRGA; FABulous | 临时 |
| FPGA-C08 | 云/数据中心/SmartNIC/多租户系统 | 2018-2026 | Cloud-DNN；超级网卡；超大规模 FPGA 工程系统 | 临时 |
| FPGA-C09 | 安全/信任/侧通道/FHE | 2019-2026 | FPGA 安全行； FAST; OLA | 临时 |
| FPGA-C10 | 超越主流 AI | 2016-2026 | 基因组学的特定领域应用引擎；信号处理；机器人相邻行 | 临时 |

| 时间段 | 主导主题 | 新兴主题 | 下降/不太明显的主题 | 代表论文 | 备注 |
|---|---|---|---|---|---|
| 2016-2018 | CNN/LSTM/低精度 ML、FPGA architecture/CAD、graph/memory applications | HLS benchmark 和 cloud/datacenter signals | 传统 standalone OpenCL demo 逐步让位给更系统化 toolflow | ESE、FINN、FASTCF、Rosetta | ML 加速出现但还以 CNN/RNN/推荐系统为主 |
| 2019-2022 | HLS/DSL/物理感知实现、数据流缓冲、DNN 加速器生成器 | 多芯片/HBM/物理感知 HLS、artifact/基准规程 | 单纯把一个 kernel 搬上 FPGA 的叙事变弱 | HeteroCL、Buffer Placement、AutoBridge、RapidStream | Best Paper 序列支撑 HLS/toolflow 主线 |
| 2023-2024 | HLS 与 storage/correctness/verification 结合，LLM/Transformer 和 sparse/event vision 出现 | NVMe/HLS、形式验证、LLM 映射 | 经典 CNN 退到低精度/边缘/benchmark 场景 | DONGLE、HLS 的形式验证、FlightLLM | 数据搬运和可验证 toolflow 更突出 |
| 2025-2026 | AI for FPGA、LLM/生成推理、LUT-native ML、CXL/KV 缓存、边缘 LLM | KAN/LUT 评估、三元/查表 LLM、推测 KV 缓存 | 2026 影响尚不可判断 | FlightVGM、KANELÉ、CXL-SpecKV、TeLLMe | 2026 只作 partial 和 frontier signal |

## 5. Award Papers 分析

| 年份 | 奖项 | 论文 | 主题 | 是否里程碑候选 | 来源 |
|---|---|---|---|---|---|
| 2026 | 获胜者 | KANELÉ：基于 Kolmogorov-Arnold 网络的高效基于 LUT 的评估 | FPGA 上的 ML/AI 加速器 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2026 | 亚军 | 凭借 LSQ 出局：动态 HLS 中内存访问重新排序的定制电路 | HLS/DSL/编译流程 | yes | https://www.isfpga.org/program/ |
| 2025 | 获胜者 | FlightVGM: Efficient Video Generation Model Inference with Online Sparsification and Hybrid Precision on FPGAs | FPGA 上的 ML/AI 加速器 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2024 | 获胜者 | HLS 源到源转换的形式验证 | HLS/DSL/编译流程 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2023 | 获胜者 | DONGLE: Direct FPGA-Orchestrated NVMe Storage for HLS | HLS/DSL/编译流程 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2022 | 获胜者 | RapidStream: Parallel Physical Implementation of FPGA HLS Designs | HLS/DSL/编译流程 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2021 | 获胜者 | AutoBridge: Coupling Coarse-Grained Floorplanning and Pipelining for High-Frequency HLS Design on Multi-Die FPGAs | HLS/DSL/编译流程 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2020 | 获胜者 | Buffer Placement and Sizing for High-Performance Dataflow Circuits | FPGA 架构、CAD 和物理设计 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2019 | 获胜者 | HeteroCL: A Multi-Paradigm Programming Infrastructure for Software-Defined Reconfigurable Computing | HLS/DSL/编译流程 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2018 | 获胜者 | FASTCF：基于 FPGA 的加速器基于随机梯度下降的协同过滤 | 特定于应用的 FPGA 加速 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2017 | 获胜者 | ESE：在 FPGA 上使用压缩 LSTM 的高效语音识别引擎 | FPGA 上的 ML/AI 加速器 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |
| 2016 | 获胜者 | FPRESSO：启用 FPGA 架构的快速晶体管级探索 | FPGA 架构、CAD 和物理设计 | yes | https://tcfpga.org/books/community-awards/page/fpga-best-paper-awards |

奖项事实来自 TCFPGA 或 ISFPGA official program。奖项只说明本 venue 的正式认可，不自动证明长期影响；所有 impact 均保留 `impact_unverified`，除非后续 citation/code/toolchain 审计补证。

## 6. 代表性论文清单

| 简称 | 论文 | 为什么放入阅读路线 | impact 状态 | claim |
|---|---|---|---|---|
| ESE | ESE: Efficient Speech Recognition Engine with Sparse LSTM on FPGA | 稀疏/低精度循环推理 | Best Paper; impact_unverified | <a id="FPGA-001-C018"></a>[FPGA-001-C018](#FPGA-001-C018) |
| FINN | FINN：快速、可扩展的二值化神经网络推理框架 | 低位神经推理框架 | impact_unverified | <a id="FPGA-001-C019"></a>[FPGA-001-C019](#FPGA-001-C019) |
| Rosetta | Rosetta：现实的软件可编程 FPGA 高级综合基准套件 | HLS 评估基准 | impact_unverified | <a id="FPGA-001-C020"></a>[FPGA-001-C020](#FPGA-001-C020) |
| HeteroCL | HeteroCL: A Multi-Paradigm Programming Infrastructure for Software-Defined Reconfigurable Computing | DSL/编程基础设施路线 | Best Paper; impact_unverified | <a id="FPGA-001-C021"></a>[FPGA-001-C021](#FPGA-001-C021) |
| Buffer Placement | Buffer Placement and Sizing for High-Performance Dataflow Circuits | 数据流吞吐量和缓冲 | Best Paper; impact_unverified | <a id="FPGA-001-C022"></a>[FPGA-001-C022](#FPGA-001-C022) |
| AutoBridge | AutoBridge: Coupling Coarse-Grained Floorplanning and Pipelining for High-Frequency HLS Design on Multi-Die FPGAs | 物理感知 HLS | Best Paper; impact_unverified | <a id="FPGA-001-C023"></a>[FPGA-001-C023](#FPGA-001-C023) |
| AutoSA | AutoSA: A Polyhedral Compiler for High-Performance Systolic Arrays on FPGA | 编译器生成的脉动数组 | impact_unverified | <a id="FPGA-001-C024"></a>[FPGA-001-C024](#FPGA-001-C024) |
| RapidStream | RapidStream: Parallel Physical Implementation of FPGA HLS Designs | 并行物理实现 | Best Paper; impact_unverified | <a id="FPGA-001-C025"></a>[FPGA-001-C025](#FPGA-001-C025) |
| DONGLE | DONGLE: Direct FPGA-Orchestrated NVMe Storage for HLS | 存储/HLS 协同设计 | Best Paper; impact_unverified | <a id="FPGA-001-C026"></a>[FPGA-001-C026](#FPGA-001-C026) |
| FlightVGM | FlightVGM: Efficient Video Generation Model Inference with Online Sparsification and Hybrid Precision on FPGAs | 生成视频推理前沿 | Best Paper; new, impact_unverified | <a id="FPGA-001-C027"></a>[FPGA-001-C027](#FPGA-001-C027) |

扩展阅读建议：`Throughput-Optimized OpenCL-based FPGA Accelerator for Large-Scale CNNs`、`Can FPGAs Beat GPUs in Accelerating Next-Generation Deep Neural Networks?`、`Cloud-DNN`、`AutoDNNchip`、`HeteroHalide`、`Tensor Slices to the Rescue`、`Demystifying the Memory System of Modern Datacenter FPGAs`、`Hardware Acceleration of Nonparametric Belief Propagation for Efficient Robot Manipulation`、`FlightLLM`、`CXL-SpecKV`、`TeLLMe`。

## 7. 发展脉络

- 2016-2018：ML 加速和 FPGA architecture/CAD 并行。2016 program 中 CNN/OpenCL 与 FPRESSO 并存；2017 的 ESE/FINN 把 sparse/low-bit neural inference 推到显眼位置；2018 的 FASTCF 和 Rosetta 分别代表应用加速和 HLS benchmark 口径。
- 2019-2022：HLS/DSL/physical-aware route 成为主线。HeteroCL、Buffer Placement、AutoBridge、RapidStream 连续说明 FPGA 论文开始更强调从抽象、dataflow、buffer 到 floorplan/physical implementation 的闭环。
- 2023-2024：数据搬运和正确性进入 HLS 叙事。DONGLE 把 NVMe/storage 和 HLS 连接，Formal Verification of HLS 把 source-to-source transformation correctness 推到 Best Paper 层级。
- 2025-2026：生成式/LLM/LUT-native ML 进入前沿。FlightVGM、KANELÉ、CXL-SpecKV、Hummingbird+、TeLLMe 等说明 FPGA venue 已经开始接收 generative/video/LLM inference 负载，但长期路线仍需后续年份验证。

## 8. 领跑团队和代表成果

这里的“领跑”只表示 2016-2026 FPGA corpus 内反复出现，并且与某条技术路线绑定；不等同于跨会议或 citation 影响力排名。

| 团队/机构线索 | 主要路线 | 代表成果 | claim |
|---|---|---|---|
| UCLA/Cornell/Jason Cong/Zhiru Zhang | HLS/DSL/物理感知工具流 | HeteroCL、AutoBridge、AutoSA、RapidStream、Stream-HLS/ARIES 相邻行 | <a id="FPGA-001-C011"></a>[FPGA-001-C011](#FPGA-001-C011) |
| EPFL/ETH/Paolo Ienne/Lana Josipović | 数据流 HLS，动态 HLS，FPGA 架构 | FPRESSO，Buffer Placement，LSQ/数据流论文，DynaRapid，2026 dynamic-HLS rows | <a id="FPGA-001-C012"></a>[FPGA-001-C012](#FPGA-001-C012) |
| Tsinghua/SJTU/Infinigence/Yu Wang/Guohao Dai | 最近的 LLM 和视频生成推理 | FlightLLM、FlightVGM、早期的清华 FPGA ML rows | <a id="FPGA-001-C013"></a>[FPGA-001-C013](#FPGA-001-C013) |
| USC/Viktor Prasanna | 推荐器、图表、安全/FHE、应用程序加速 | FASTCF、HP-GNN、FHE/安全行 | <a id="FPGA-001-C014"></a>[FPGA-001-C014](#FPGA-001-C014) |
| 宾夕法尼亚大学/Andre DeHon/Jing Li | CAD/路由、存储/HLS、文件系统/页面放置系统 | DONGLE、 HiLFS、页面布局/路由行 | <a id="FPGA-001-C016"></a>[FPGA-001-C016](#FPGA-001-C016) |
| Imperial/Constantinides/Wickerson | HLS 正确性、综合错误、方法 | HLS 工具错误论文、源到源验证、2026 P&R 错误 | <a id="FPGA-001-C017"></a>[FPGA-001-C017](#FPGA-001-C017) |

## 9. 对博士入门者的阅读路线

必读 10 篇：ESE、FINN、Rosetta、HeteroCL、Buffer Placement、AutoBridge、AutoSA、RapidStream、DONGLE、Formal Verification of HLS。

扩展 20 篇：Throughput-Optimized OpenCL CNN、Going Deeper with Embedded FPGA CNN、Can FPGAs Beat GPUs、FASTCF、Cloud-DNN、AutoDNNchip、HeteroHalide、Light-OPU、Tensor Slices、NetCracker、Logic Shrinkage、robot manipulation accelerator、ACTS、FlightLLM、FlightVGM、KANELÉ、CXL-SpecKV、Hummingbird+、TeLLMe、RISCBench。

适合跟踪的近年方向：LLM/Transformer 的 KV cache 与低精度执行、LUT-native ML、HLS correctness、physical-aware HLS、HBM/NVMe/CXL 数据搬运、artifact/benchmark/profiling。

## 10. 与我的方向的连接点

你的 3DGS/神经渲染/FPGA 方向更接近 FPGA venue 中的三条线：HLS/DSL/physical-aware toolflow 负责回答算法如何稳定落到 FPGA；dataflow、buffer 和 memory-centric route 对应排序、tile/binning、alpha blending、DDR/AXI burst 这些瓶颈；ML/AI accelerator route 提供新负载从 demo 走向低延迟部署时的算子、精度和数据流定制经验。本轮未找到直接以 3DGS 为核心的 ACM/SIGDA FPGA 论文，因此 3DGS 连接应写作邻近负载迁移，而不是既有成熟 topic。对应 claim <a id="FPGA-001-C008"></a>[FPGA-001-C008](#FPGA-001-C008)。

## 11. 第二轮 Additions

第二波通行证在 `20_venue_reports/FPGA/` 下添加了venue-internal部小领域 artifact：

- `FPGA_screening_matrix.csv`：421 个源行，涵盖 409 个paper rows和 12 个奖项源行。
- `FPGA_paper_evidence_matrix.csv`：44 个选定的带有 WHY/HOW/WHAT/IMPACT/EVIDENCE 字段的paper evidence rows。
- `subfields.md`：10 个venue-provisional 小领域、趋势证据、方法变化和cross-venue 挂钩。

有针对性的元数据回填添加了经过验证的 ACM DOI/acm_url 值以及所选的奖项、代表性和前沿论文的 code/PDF/artifact URL。这不是一个完整的 409 论文 ACM DL 导出。

FPGA-内部第二波映射保持 HLS/DSL/编译器到硬件闭包、神经/低精度推理、LLM/生成推理、以内存/存储为中心的系统、数据流/流、稀疏/图/张量加速、基准/分析、物理感知 CAD、云/数据中心FPGA 系统和机器人/事件视觉边缘加速作为 `venue_provisional` 子领域。这些没有在这里被提升为全球稳定分类法。

对于 3DGS/NeRF/神经渲染，第二波筛选仍然没有发现直接围绕该主题的 ACM/SIGDA FPGA 2016-2026 论文。连接仍然是通过数据流/内存、稀疏/事件视觉、基准/分析和最近的生成/LLM 推理行的相邻cross-venue 挂钩，而不是已建立的 FPGA 内部成熟主题。

## 12. 缺失来源

- 完整 ACM DL 每篇论文 DOI/摘要/关键字导出所有 409 行论文。
- Canonical 官方 FPGA 来源提供除当前最佳论文获奖者和 2026 年亚军记录之外的最佳学生论文、时间测试、杰出论文或荣誉奖类别。
- 记录仓库的 artifact 执行状态和代码重用证据；所有代码/artifact URL 均保留 `runnable_unchecked` 或 `access_restricted`。
- 在进行任何全球分类推广之前，与 FCCM、FPL、FPT、DAC、ICCAD、DATE、ISCA、MICRO、HPCA、ASPLOS 和 MLSys 进行cross-venue比较。
- 专用的cross-venue 3DGS/NeRF/神经渲染硬件加速审核。
