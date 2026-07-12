# 分布式训练；加速器编排；集体；数据中心结构瓶颈

<a id="FIELD-DATACENTER-FABRIC-001-C002"></a>
对应 global_subfield_id：[GSF-10](../40_synthesis/third_wave_field_synthesis.md#GSF-10)  
证据规则：论文级事实、团队线索、趋势判断和 artifact 状态均以本报告 claim ledger 与 paper evidence matrix 为准；未运行任何 benchmark、artifact 或代码。

## 研究背景

[GSF-10](../40_synthesis/third_wave_field_synthesis.md#GSF-10) 从跨会议证据中浮现，是因为加速器论文的瓶颈不再只停在单芯片算力或单算子吞吐。MLSys 和 PPoPP 把问题表述为 parallelism、all-reduce、collective synthesis、in-network aggregation 和 asynchronous distributed dataflow；ASPLOS 与 SC 把近期大模型训练中的 communication-computation overlap、MoE、offload、GPU memory wall 和 pipeline parallelism 拉到系统/体系结构层；Hot Chips 和 ISCA 则提供生产 accelerator platform、GPU/TPU supercomputer、SmartNIC/DPU 和 optical interconnect 的产业披露与架构证据 <a id="FIELD-DATACENTER-FABRIC-001-C003"></a>[FIELD-DATACENTER-FABRIC-001-C003](#FIELD-DATACENTER-FABRIC-001-C003).

因此，这个 field 的实际对象是“多 accelerator 组成的训练/推理系统如何被组织、连接、调度和测量”，而不是某一种 accelerator ISA、某一个 GPU SKU，或某一类云平台服务。

## 核心问题

1. Collective 和 topology：All-reduce、sparse allreduce、collective algorithm synthesis、collective compression、GPU-to-GPU communication 和 topology design 是长期反复出现的问题 [<a id="FIELD-DATACENTER-FABRIC-001-C007"></a>[FIELD-DATACENTER-FABRIC-001-C007](#FIELD-DATACENTER-FABRIC-001-C007); <a id="FIELD-DATACENTER-FABRIC-001-C008"></a>[FIELD-DATACENTER-FABRIC-001-C008](#FIELD-DATACENTER-FABRIC-001-C008); <a id="FIELD-DATACENTER-FABRIC-001-C012"></a>[FIELD-DATACENTER-FABRIC-001-C012](#FIELD-DATACENTER-FABRIC-001-C012); <a id="FIELD-DATACENTER-FABRIC-001-C013"></a>[FIELD-DATACENTER-FABRIC-001-C013](#FIELD-DATACENTER-FABRIC-001-C013); <a id="FIELD-DATACENTER-FABRIC-001-C029"></a>[FIELD-DATACENTER-FABRIC-001-C029](#FIELD-DATACENTER-FABRIC-001-C029); <a id="FIELD-DATACENTER-FABRIC-001-C031"></a>[FIELD-DATACENTER-FABRIC-001-C031](#FIELD-DATACENTER-FABRIC-001-C031)].
2. Computation-communication overlap：大模型训练开始显式围绕 overlap、sequence parallelism、MoE communication 和 collective library abstraction 组织系统 [<a id="FIELD-DATACENTER-FABRIC-001-C024"></a>[FIELD-DATACENTER-FABRIC-001-C024](#FIELD-DATACENTER-FABRIC-001-C024); <a id="FIELD-DATACENTER-FABRIC-001-C025"></a>[FIELD-DATACENTER-FABRIC-001-C025](#FIELD-DATACENTER-FABRIC-001-C025); <a id="FIELD-DATACENTER-FABRIC-001-C026"></a>[FIELD-DATACENTER-FABRIC-001-C026](#FIELD-DATACENTER-FABRIC-001-C026)].
3. Memory/offload orchestration：GPU memory wall、multi-level offload、pipeline parallelism 和 superchip offload 说明“内存容量/路径”在本领域中常表现为训练 orchestration 问题，而不是单纯的 CXL/far-memory 题目 [<a id="FIELD-DATACENTER-FABRIC-001-C028"></a>[FIELD-DATACENTER-FABRIC-001-C028](#FIELD-DATACENTER-FABRIC-001-C028); <a id="FIELD-DATACENTER-FABRIC-001-C027"></a>[FIELD-DATACENTER-FABRIC-001-C027](#FIELD-DATACENTER-FABRIC-001-C027); <a id="FIELD-DATACENTER-FABRIC-001-C032"></a>[FIELD-DATACENTER-FABRIC-001-C032](#FIELD-DATACENTER-FABRIC-001-C032)].
4. Production fabric：TPU、NVLink/NVSwitch、optically reconfigurable supercomputer、SmartNIC/DPU、SuperNIC/Ethernet/photonic AI-factory disclosures 把集群 fabric 变成 accelerator platform 的一部分 [<a id="FIELD-DATACENTER-FABRIC-001-C015"></a>[FIELD-DATACENTER-FABRIC-001-C015](#FIELD-DATACENTER-FABRIC-001-C015); <a id="FIELD-DATACENTER-FABRIC-001-C017"></a>[FIELD-DATACENTER-FABRIC-001-C017](#FIELD-DATACENTER-FABRIC-001-C017); <a id="FIELD-DATACENTER-FABRIC-001-C019"></a>[FIELD-DATACENTER-FABRIC-001-C019](#FIELD-DATACENTER-FABRIC-001-C019); <a id="FIELD-DATACENTER-FABRIC-001-C020"></a>[FIELD-DATACENTER-FABRIC-001-C020](#FIELD-DATACENTER-FABRIC-001-C020); <a id="FIELD-DATACENTER-FABRIC-001-C023"></a>[FIELD-DATACENTER-FABRIC-001-C023](#FIELD-DATACENTER-FABRIC-001-C023)].
5. Measurement and artifacts：MLPerf Training、network-latency modeling、GPU-to-GPU communication profiling、SC reproducibility reports 和 collective diagnostics提供评价基础设施，但本报告没有把任何 artifact 写成已复现 [<a id="FIELD-DATACENTER-FABRIC-001-C009"></a>[FIELD-DATACENTER-FABRIC-001-C009](#FIELD-DATACENTER-FABRIC-001-C009); [FIELD-DATACENTER-FABRIC-001-C031](#FIELD-DATACENTER-FABRIC-001-C031); <a id="FIELD-DATACENTER-FABRIC-001-C035"></a>[FIELD-DATACENTER-FABRIC-001-C035](#FIELD-DATACENTER-FABRIC-001-C035); <a id="FIELD-DATACENTER-FABRIC-001-C036"></a>[FIELD-DATACENTER-FABRIC-001-C036](#FIELD-DATACENTER-FABRIC-001-C036)].

## 发展脉络

第一条路线是 distributed training parallelism 和 collectives。MLSys 2019 的 Beyond Data and Model Parallelism 与 BlueConnect，把训练并行和 all-reduce 层次结构作为系统设计对象；MLSys 2020 Blink、PPoPP 2021 Synthesizing Optimal Collective Algorithms 和 PPoPP 2022 Near-Optimal Sparse Allreduce 将 collective algorithm/library 本身变成独立问题 [<a id="FIELD-DATACENTER-FABRIC-001-C006"></a>[FIELD-DATACENTER-FABRIC-001-C006](#FIELD-DATACENTER-FABRIC-001-C006); [FIELD-DATACENTER-FABRIC-001-C007](#FIELD-DATACENTER-FABRIC-001-C007); [FIELD-DATACENTER-FABRIC-001-C008](#FIELD-DATACENTER-FABRIC-001-C008); [FIELD-DATACENTER-FABRIC-001-C012](#FIELD-DATACENTER-FABRIC-001-C012); [FIELD-DATACENTER-FABRIC-001-C013](#FIELD-DATACENTER-FABRIC-001-C013)].

第二条路线是 accelerator orchestration。Pathways 将 distributed dataflow 升级为 ML execution 的 orchestration 问题；后续 ASPLOS 和 SC 的 Centauri、FlexSP、FSMoE、COMET、SlimPipe、X-MoE 等，把 overlap、sequence parallelism、MoE expert routing、pipeline parallelism 和 memory/offload 编进训练系统路线 [<a id="FIELD-DATACENTER-FABRIC-001-C011"></a>[FIELD-DATACENTER-FABRIC-001-C011](#FIELD-DATACENTER-FABRIC-001-C011); [FIELD-DATACENTER-FABRIC-001-C024](#FIELD-DATACENTER-FABRIC-001-C024); [FIELD-DATACENTER-FABRIC-001-C025](#FIELD-DATACENTER-FABRIC-001-C025); [FIELD-DATACENTER-FABRIC-001-C032](#FIELD-DATACENTER-FABRIC-001-C032)].

第三条路线是 production accelerator fabric。ISCA 的 In-Datacenter TPU、TPUv4i lessons 和 TPU v4，以及 Hot Chips 的 Pascal/NVLink、NVSwitch/DGX-2、TPU/ML supercomputer 和 Dojo/Ethernet transport disclosure，显示生产 accelerator 不只是芯片，而是芯片、互连、软件栈和 workload 共同定义的平台 [[FIELD-DATACENTER-FABRIC-001-C015](#FIELD-DATACENTER-FABRIC-001-C015); <a id="FIELD-DATACENTER-FABRIC-001-C016"></a>[FIELD-DATACENTER-FABRIC-001-C016](#FIELD-DATACENTER-FABRIC-001-C016); [FIELD-DATACENTER-FABRIC-001-C017](#FIELD-DATACENTER-FABRIC-001-C017); <a id="FIELD-DATACENTER-FABRIC-001-C018"></a>[FIELD-DATACENTER-FABRIC-001-C018](#FIELD-DATACENTER-FABRIC-001-C018); [FIELD-DATACENTER-FABRIC-001-C019](#FIELD-DATACENTER-FABRIC-001-C019); <a id="FIELD-DATACENTER-FABRIC-001-C022"></a>[FIELD-DATACENTER-FABRIC-001-C022](#FIELD-DATACENTER-FABRIC-001-C022)].

第四条路线是 fabric offload 与 optical frontier。DPU/SmartNIC/SuperNIC/programmable RoCE 和 co-packaged photonics/AI factory disclosures把网络、存储、安全、telemetry 和 collective movement 的一部分推到 fabric-side processors 或 optical switching 路径上。不过 Hot Chips 的这类证据多为 vendor disclosure，必须保留独立验证缺口 [<a id="FIELD-DATACENTER-FABRIC-001-C005"></a>[FIELD-DATACENTER-FABRIC-001-C005](#FIELD-DATACENTER-FABRIC-001-C005); [FIELD-DATACENTER-FABRIC-001-C020](#FIELD-DATACENTER-FABRIC-001-C020); [FIELD-DATACENTER-FABRIC-001-C023](#FIELD-DATACENTER-FABRIC-001-C023)].

## 研究方法

本领域的方法族包括：

- 集体算法和库设计：全归约分解、泛型集体、集体合成、稀疏/压缩集体、自定义GPU通信抽象[[FIELD-DATACENTER-FABRIC-001-C007](#FIELD-DATACENTER-FABRIC-001-C007); [FIELD-DATACENTER-FABRIC-001-C008](#FIELD-DATACENTER-FABRIC-001-C008)； [FIELD-DATACENTER-FABRIC-001-C012](#FIELD-DATACENTER-FABRIC-001-C012)； [FIELD-DATACENTER-FABRIC-001-C013](#FIELD-DATACENTER-FABRIC-001-C013)； [FIELD-DATACENTER-FABRIC-001-C026](#FIELD-DATACENTER-FABRIC-001-C026)]。
- runtime和训练编排：并行搜索、异步数据流、通信分区、序列并行、MoE重叠、管道调度、多路径卸载 [[FIELD-DATACENTER-FABRIC-001-C006](#FIELD-DATACENTER-FABRIC-001-C006); [FIELD-DATACENTER-FABRIC-001-C011](#FIELD-DATACENTER-FABRIC-001-C011)； [FIELD-DATACENTER-FABRIC-001-C024](#FIELD-DATACENTER-FABRIC-001-C024)； [FIELD-DATACENTER-FABRIC-001-C025](#FIELD-DATACENTER-FABRIC-001-C025)； [FIELD-DATACENTER-FABRIC-001-C027](#FIELD-DATACENTER-FABRIC-001-C027)； [FIELD-DATACENTER-FABRIC-001-C032](#FIELD-DATACENTER-FABRIC-001-C032)]。
- Fabric架构：NVLink/NVSwitch、光可重构TPU v4 Fabric、定制AI以太网传输、DPU/SmartNIC/SuperNIC和光子交换机披露[[FIELD-DATACENTER-FABRIC-001-C017](#FIELD-DATACENTER-FABRIC-001-C017); [FIELD-DATACENTER-FABRIC-001-C019](#FIELD-DATACENTER-FABRIC-001-C019)； [FIELD-DATACENTER-FABRIC-001-C020](#FIELD-DATACENTER-FABRIC-001-C020)； [FIELD-DATACENTER-FABRIC-001-C022](#FIELD-DATACENTER-FABRIC-001-C022)； [FIELD-DATACENTER-FABRIC-001-C023](#FIELD-DATACENTER-FABRIC-001-C023)]。
- 评估和分析：MLPerf Training、GPU-to-GPU 通信分析、网络延迟容忍建模、SC 再现性报告和集体诊断 [[FIELD-DATACENTER-FABRIC-001-C009](#FIELD-DATACENTER-FABRIC-001-C009); [FIELD-DATACENTER-FABRIC-001-C031](#FIELD-DATACENTER-FABRIC-001-C031)； [FIELD-DATACENTER-FABRIC-001-C035](#FIELD-DATACENTER-FABRIC-001-C035)； [FIELD-DATACENTER-FABRIC-001-C036](#FIELD-DATACENTER-FABRIC-001-C036)]。

## 代表性论文与系统

| 角色 | 证据行 | 为什么它代表这个领域 |
|---|---|---|
| `origin_anchor` | E001、E002、E003 | 建立分布式训练并行性和全归约/集体通信作为系统问题。 |
| `tool_benchmark` | E004、E013、E035、E040、E041 | 提供benchmark、诊断、延迟建模或artifact evaluation基础设施；没有一个是在本地运行的。 |
| `milestone_candidate` | E006、E010、E014、E016、E026、E029、E032、E039 | Mark 转向异步编排、集体合成、生产 TPU/fabric、通信重叠和 MoE/HPC 扩展。 |
| `method_bridge` | E015、E018、E019、E020、E022、E024、E034 | 将单加速器设计与生产平台/结构/卸载/分析方法联系起来。 |
| `frontier` | E007、E008、E012、E023、E025、E027、E028、E030、E037、E038 | 捕获 2025-2026 年压力点：MoE 重叠、具有集体能力的 NoC、压缩集体、光子 AI 工厂结构、LLM 训练卸载和管道并行性。 |
| `negative_boundary` | E009 | 防止存储/CXL/远内存跟踪被折叠到 [GSF-10](../40_synthesis/third_wave_field_synthesis.md#GSF-10) 中，除非绑定到加速器结构或集合。 |
| `background` | E042, E043 | 提供数据中心分配/QoS 上下文，而无需成为核心结构/集体证据。 |

## 团队与会议线索

venue activity在设计上并不均衡。 MLSys 和 PPoPP 提供训练系统和集体算法证据； SC 提供 HPC 规模的通信、卸载、artifact和再现性证据； ASPLOS 提供围绕重叠、超级芯片卸载和集体抽象的架构/系统行； ISCA 和 Hot Chips 提供生产加速器平台和行业结构披露证据 [<a id="FIELD-DATACENTER-FABRIC-001-C001"></a>[FIELD-DATACENTER-FABRIC-001-C001](#FIELD-DATACENTER-FABRIC-001-C001); [FIELD-DATACENTER-FABRIC-001-C003](#FIELD-DATACENTER-FABRIC-001-C003)]。

这里使用的唯一实体解析团队信号是 ISCA 2017-2023 期间的 Google TPU 团队信号；这是一个活动信号，而不是排名 <a id="FIELD-DATACENTER-FABRIC-001-C004"></a>[FIELD-DATACENTER-FABRIC-001-C004](#FIELD-DATACENTER-FABRIC-001-C004)。 NVIDIA、Intel、AMD、Fungible、Tesla、Microsoft、Cerebras 和其他公司名称在证据行中显示为作者字符串或供应商披露信号，但本报告不会对团队进行排名或根据频率推断团队实力 [[FIELD-DATACENTER-FABRIC-001-C005](#FIELD-DATACENTER-FABRIC-001-C005)； [FIELD-DATACENTER-FABRIC-001-C020](#FIELD-DATACENTER-FABRIC-001-C020)； [FIELD-DATACENTER-FABRIC-001-C023](#FIELD-DATACENTER-FABRIC-001-C023)； [FIELD-DATACENTER-FABRIC-001-C026](#FIELD-DATACENTER-FABRIC-001-C026)]。

## 开放问题

1. 对供应商结构披露的独立验证仍然薄弱。 Hot Chips 行对于路由映射很有用，但性能、采用和workload泛化claim需要单独的benchmark/部署证据 [FIELD-DATACENTER-FABRIC-001-C005](#FIELD-DATACENTER-FABRIC-001-C005)。
2. 内存容量/CXL/存储的边界是脆弱的。当卸载是训练编排的一部分时，它就属于这里；远记忆/存储属于其他地方，除非集体、加速器结构或训练系统证据明确为 <a id="FIELD-DATACENTER-FABRIC-001-C034"></a>[FIELD-DATACENTER-FABRIC-001-C034](#FIELD-DATACENTER-FABRIC-001-C034)。
3. artifact status还浅。 FSMoE、MSCCL++、COMET 和 SC 再现性行包含代码或artifact evaluation 信号，但在此任务中未安装或再现任何信号 [[FIELD-DATACENTER-FABRIC-001-C035](#FIELD-DATACENTER-FABRIC-001-C035)； [FIELD-DATACENTER-FABRIC-001-C036](#FIELD-DATACENTER-FABRIC-001-C036)]。
4. 评估分散在 MLPerf、SC artifact报告、供应商幻灯片、DOI 元数据和每篇论文的benchmark设置中。未来的审计应该将规则集证据、代码可用性、artifact evaluation和实际的本地再现性分开[[FIELD-DATACENTER-FABRIC-001-C009](#FIELD-DATACENTER-FABRIC-001-C009)； [FIELD-DATACENTER-FABRIC-001-C035](#FIELD-DATACENTER-FABRIC-001-C035)]。

## 连接到用户方向

对于 3DGS 来说，这个领域是相邻的而不是中心的：大规模 3DGS 训练可以继承相同的 GPU 内存墙、分布式训练、卸载和集体问题，但 3DGS 渲染/排序/光栅化管道属于神经渲染领域，除非论文明确针对分布式训练/结构瓶颈。

对于 FPGA，直接连接是结构侧卸载、SmartNIC/DPU、支持集合的 NoC 和数据流集合。该报告并未声称 FPGA 是 [GSF-10](../40_synthesis/third_wave_field_synthesis.md#GSF-10) 的核心，但它确定了 FPGA 或可重新配置逻辑可能变得相关的接口：流集合、网络内聚合、NIC 端预处理和通信重叠分析。

对于机器人/嵌入式边缘计算，这种连接主要是方法论上的：在研究边缘队列或多加速器机器人时，编排、多租户调度和通信/分析指标很重要，但低延迟传感器/控制循环仍然是一个单独的领域，除非结构瓶颈占主导地位。

## 缺失来源

- 针对 SmartNIC/DPU、Spectrum-X、光子 AI 工厂和其他供应商结构披露的独立部署或benchmark验证。
- 针对 MSCCL++、FSMoE、COMET、PPoPP 2026 集体artifact、MLP-Offload 和 X-MoE 的完整artifact审核。
- [GSF-10](../40_synthesis/third_wave_field_synthesis.md#GSF-10) 卸载编排和 [GSF-11](../40_synthesis/third_wave_field_synthesis.md#GSF-11) 内存容量/CXL/存储行之间更精确的划分。
- 对当前用作标题/源或幻灯片级证据的仅元数据 SC 和 Hot Chips 行进行全面的 PDF 级审查。
- 针对 Microsoft、NVIDIA、Intel、AMD、Tesla、Cerebras、大学/HPC 组和重复作者字符串进行更深入的实体消歧。
