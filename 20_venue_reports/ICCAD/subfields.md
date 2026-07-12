# ICCAD 小领域深读

## 1. 范围与语料

- Venue：`ICCAD` / IEEE/ACM 国际计算机辅助设计会议。
- 语料库：`10_corpus/venues/ICCAD/papers.csv` 中的 `1779` 行和 `10_corpus/venues/ICCAD/awards.csv` 中的 `30` 行。
- 筛选矩阵：`1809` 行。决策：`deep_read=74`、`index_only=1211`、`needs_review=451`、`exclude_non_main=73`。
- 论文证据矩阵：`53` 独特的论文锚点。其余的 `21` deep-read奖励行是 2016-2025 本地语料库之外的paper evidence rows或十年奖励行的重复奖励链接。
- 源深度：DBLP/proceedings DOI 元数据、官方 ICCAD/CEDA 页面、选定的 arXiv/作者 PDF、项目页面、GitHub 仓库、OpenAlex 引文快照和subagent PDF/abstract 读取。
- 引用/采用/artifact 数据仅是首次通过信号。计数使用 OpenAlex，除非该行另有说明，并且 `ICCAD_paper_evidence_matrix.csv` 中的每个计数都在 `2026-06-27` 上检查。
- `papers.csv` 没有 2026 行接受的论文。 2026 年仍然是 `normal_2026_partial`，因为完整的官方接受论文和获奖结果在此阶段并未公开。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="ICCAD-SF01"></a>[ICCAD-SF01](#ICCAD-SF01) | HLS/FPGA 架构探索和加速器生成 | 将算法、运算符或微架构描述转化为可评估和可实现的 FPGA/微架构设计。 | HLS 内核、CNN/Transformer 运算符、RISC-V BOOM、FPGA 架构 | DSE/搜索成本、QoR 可预测性、定时/路由/资源关闭 | 基于模型的 HLS 分析、生成器、贝叶斯DSE、物理综合感知 IR、Transformer 运算符库、3D FPGA 探索 | 2017;2018;2021;2024;2025 | venue_provisional； 6 个evidence rows |
| <a id="ICCAD-SF02"></a>[ICCAD-SF02](#ICCAD-SF02) | AI/LLM 加速器硬件-软件协同设计 | 针对延迟、能量、带宽和 PPA 共同优化模型表示、精度、软件堆栈和硬件映射。 | CNN、DNN 鲁棒性、LLM、二值化 Transformer、边缘 FPGA | 内存流量、精度质量权衡、框架迭代成本、边缘延迟 | 统一表示、Caffe/HLS 集成、对抗鲁棒性边界、二进制 LLM 框架、面向 BiT 的 compiler/ISA | 2016;2018;2024 | venue_provisional；4 个 evidence rows |
| <a id="ICCAD-SF03"></a>[ICCAD-SF03](#ICCAD-SF03) | PIM/CIM 和以内存为中心的推理 | 当数据移动、容量、带宽或内存设备非理想性占主导地位时，在内存附近移动或调度计算。 | ReRAM 逻辑、ISC workload、Transformer/LLM、NVCiM、SRAM/NAND/LPDDR PIM、MoE | 片外流量、ADC/DAC 和存储器非理想性、移动容量、MoE 通信 | ReRAM 映射、ISC 仿真、ReRAM Transformer PIM、右删失噪声训练、数字 SRAM CIM、LPDDR/NAND/PIM-NoC/3D-NMP LLM 推理 | 2016;2019;2020;2023;2024;2025 | venue_provisional； 11 个evidence rows |
| <a id="ICCAD-SF04"></a>[ICCAD-SF04](#ICCAD-SF04) | 物理设计、时序、功耗和可靠性收敛 | 在布线、时序、PDN、EM/IR、工艺和可靠性约束下闭合设计。 | 电网、路由树、超图分区、DTCO 过程数据、PDN decaps | 签核运行时间、悲观主义、电压/可靠性裕度、分区质量、过程模型成本 | 基于物理的 EM、EM 感知修复、随机/瞬态 EM、 Steiner 浅光树、监督光谱分区、神经 ODE 过程建模、SDP 开盖放置 | 2016;2017;2019;2020;2021;2022;2024;2025 | venue_provisional; 8 个evidence rows |
| <a id="ICCAD-SF05"></a>[ICCAD-SF05](#ICCAD-SF05) | 硬件安全、验证和信任 | 围绕木马、SoC、微架构侧通道和安全计算风险进行暴露、验证或优化。 | FPGA 设计流程、SoC 固件/硬件验证、ARM big.LITTLE 攻击、乱码电路 | 隐藏攻击面、验证覆盖范围、模糊测试可扩展性、安全逻辑 QoR | design-flow Trojan 模型、HyperPLTL 模糊测试、attack directories、乱码电路逻辑综合 | 2016;2020;2022;2023 | venue_provisional；4 个 evidence rows |
| <a id="ICCAD-SF06"></a>[ICCAD-SF06](#ICCAD-SF06) | AI-for-EDA 代理、电路表示和基准 | 使用可重现的数据集和基准测试工具生成、评估或支持 Verilog/RTL/HLS/EDA 工作流程。 | Verilog 生成、RTL 生成、HLS、RTL-to-signoff ML-EDA、硬件代码竞赛 | 正确性、数据集泄漏、基准质量、PPA 意识、再现性 | 基于模拟的评估、打开 RTL/断言数据集、 RTL-to-signoff 基准、LLM-HLS、社区数据集构建 | 2023;2024;2025 | venue_provisional； 6 个evidence rows |
| <a id="ICCAD-SF07"></a>[ICCAD-SF07](#ICCAD-SF07) | 神经渲染、INR 和 3DGS 加速 | 满足 NeRF/INR/PBNR/3DGS 的边缘/移动实时、通信、内存和 workload 平衡限制。 | NeRF、INR 编辑/训练、设备上学习、基于点的神经渲染、3D 高斯分布 | 渲染延迟、密集嵌入访问、无线传输、LoD 搜索、光栅化冗余、图块不平衡 | NeRF 算法-硬件协同设计、INR 数据流/编译器、INR 压缩、残差INR、SLTree/LTcore、模式光栅化、流 workload 感知映射 | 2022;2023;2024;2025 | venue_provisional； 7 个evidence rows |
| <a id="ICCAD-SF08"></a>[ICCAD-SF08](#ICCAD-SF08) | 逻辑综合、映射和形式推理 | 缩放符号、代数和布尔推理以进行综合和形式验证。 | 乘数验证、多项式重写、乱码电路逻辑 | 证明可扩展性、多项式爆炸、乱码成本 | 向后重写之前的多项式清理； X1G/XAG 安全逻辑综合桥 | 2018；2023 桥 | 不足以满足独立趋势； 1 个直接evidence rows加 1 个方法桥 |
| <a id="ICCAD-SF10"></a>[ICCAD-SF10](#ICCAD-SF10) | 用于加速器研究的基准/分析/仿真工具 | 通过全系统仿真、原型设计、能源模型、屋顶线分析、开放 EDA 平台和验证框架使加速器 claim 具有可比性。 | HLS SoC 仿真、FPGA 原型、加速器能量估算、HLS 屋顶线、3D 芯片 EDA、缓存一致性 RTL 验证 | 基线公平性、全系统保真度、模拟器资源成本、artifact 出处 | 基于 FireSim 的全系统评估、Golden Gate/MIDAS 模拟编译器、Accelergy 插件、Roofline-HLS、Open3DFlow 候选者、Rhea gem5-Verilator 流程 | 2019;2020;2025 | venue_provisional； 6 个evidence rows |

## 3. 小领域深读

### [ICCAD-SF01](#ICCAD-SF01)。 HLS/FPGA 架构探索和加速器生成

- 研究问题：如何从算法、运算符或微架构参数转向可搜索、评估和实现的 FPGA/微架构设计。
- 背景：这是一个venue-local路线，而不是全球分类 claim。证据来自与奖项相关的行和最近的 HLS/FPGA 基础设施行。
- 本 venue 的现状：6 个evidence rows跨越 2017 年至 2025 年。 COMBA 和 DNNBuilder 是早期的 HLS/DNN-generator 锚点； BOOM-Explorer 将 DSE 扩展到 RISC-V 微架构； RapidStream IR 和 TransLib 进入物理综合感知和 Transformer 算子生成阶段； LaZagna 添加了 3D FPGA 架构探索。
- 方法谱系：基于模型的 pragma/DSE 分析 -> FPGA DNN 生成器 -> 贝叶斯微架构 DSE -> 高级物理综合 IR 和 Transformer 运算符库 -> 开源 3D FPGA 架构探索。
- 代表论文：[ICCAD-2017-P0137](../../10_corpus/ICCAD/id_index.md#ICCAD-2017-P0137)、[ICCAD-2018-P0129](../../10_corpus/ICCAD/id_index.md#ICCAD-2018-P0129)、[ICCAD-2021-P0017](../../10_corpus/ICCAD/id_index.md#ICCAD-2021-P0017)、[ICCAD-2024-P0099](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0099)、[ICCAD-2024-P0121](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0121)、[ICCAD-2025-P0280](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0280)。
- 团队线索：Jason Cong/UCLA-adjacent、CUHK/Tsinghua BOOM-Explorer 和佐治亚理工学院 SHARC/Conghao 仅是有用的线索。不进行排名或实体消除歧义的团队 claim。
- workload/artifact 信号：DNNBuilder/AccDNN、BOOM-Explorer 和 LaZagna 在 `papers.csv` 中有公共代码信号；都是`runnable_unchecked`。 RapidStream IR 和 TransLib 代码/artifact 仍未得到验证。
- 开放问题：DNNBuilder/TransLib/LaZagna 需要完整的 PDF/artifact 审查。 LaZagna 有奖励/代码信号，但采用率仍然是 `needs_review`。

### [ICCAD-SF02](#ICCAD-SF02)。 AI/LLM 加速器软硬件协同设计

- 研究问题：如何在延迟、带宽、能耗和 PPA 约束下协同设计模型表示、精度、软件堆栈和硬件映射。
- 背景：Caffeine 锚定了旧的 CNN/FPGA 路线，而 2024 行则转向 LLM 加速器框架和二值化 Transformer 推理。
- 本 venue 的当前状态：四个evidence rows支持临时路线。咖啡因具有经过验证的十年回顾奖信号；保留 Defective Dropout 作为负边界，因为它的影响主要是鲁棒性/安全性； 2024 LLM 行是尚未验证采用的前沿信号。
- 方法谱系：统一 CNN 表示和 Caffe/HLS 集成 -> 鲁棒性/安全边界 -> 二进制 LLM/RISC-V 加速器框架 -> 二值化 Transformer edge-FPGA 编译器/ISA。
- 代表论文：[ICCAD-2016-P0129](../../10_corpus/ICCAD/id_index.md#ICCAD-2016-P0129)、[ICCAD-2018-P0116](../../10_corpus/ICCAD/id_index.md#ICCAD-2018-P0116)、[ICCAD-2024-P0035](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0035)、[ICCAD-2024-P0234](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0234)。
- 团队线索：PKU/UCLA/Falcon、Northeastern/FIU/BU、Zhejiang/CUHK 和 Fudan 仅是作者字符串或隶属关系线索。
- workload/artifact 信号：Caffeine 通过十年奖和高 OpenAlex 引用计数具有强大的正式影响力。 Edge-BiT 和 2024 LLM 加速器框架需要 PDF/artifact 检查。
- 开放问题：原始 Caffeine 代码、Edge-BiT artifact 和 2024 LLM 框架 artifact 未 verified。

### [ICCAD-SF03](#ICCAD-SF03)。 PIM/CIM 和以内存为中心的推理

- 研究问题：如何减少 DNN/Transformer/LLM workload 的内存移动并处理内存设备非理想性。
- 背景：ICCAD 证据从 ReRAM 逻辑映射和存储内仿真到 ReRAM/SRAM/NAND/LPDDR/PIM-NoC/3D 近内存 LLM 推理。
- 此venue的当前状态：十一个evidence rows涵盖 2016 年、2019 年、2020 年、2023 年、2024 年和 2025 年。路线广泛但围绕数据移动和内存端计算是一致的。
- 方法谱系：ReRAM 技术映射 -> ISC 仿真 -> ReRAM Transformer PIM -> NVCiM 右删失噪声训练 -> SRAM/NAND/LPDDR/PIM-NoC/3D-NMP LLM 推理。
- 代表论文：[ICCAD-2016-P0012](../../10_corpus/ICCAD/id_index.md#ICCAD-2016-P0012)、[ICCAD-2019-P0094](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0094)、[ICCAD-2020-P0153](../../10_corpus/ICCAD/id_index.md#ICCAD-2020-P0153)、[ICCAD-2023-P0176](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0176)、[ICCAD-2024-P0150](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0150)、[ICCAD-2024-P0208](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0208)、[ICCAD-2025-P0068](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0068)、[ICCAD-2025-P0073](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0073)、[ICCAD-2025-P0080](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0080)、[ICCAD-2025-P0101](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0101)、[ICCAD-2025-P0243](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0243)。
- 团队线索：UCLA VAST、杜克大学、圣母大学/NCSU、高丽大学、UCSD/英特尔、北京大学、RPI/IBM、SNU 和 NUS 显示为仅字符串领先。这些不是排名。
- workload/artifact 信号：EISC 和 HD-MoE 的公开仓库记录为 `runnable_unchecked`。 2025 LP-Spec/SAGE/LLM-on-the-Palm/LEAP 大部分仍然是abstract/program-level证据。
- 开放问题：许多 2024/2025 行需要完整的 PDF、artifact 出处和引文结构审核。

### [ICCAD-SF04](#ICCAD-SF04)。物理设计、时序、功耗和可靠性收敛

- 研究问题：如何在时序、布线、PDN、EM/IR、可靠性和工艺约束下收敛可实现的设计。
- 背景：ICCAD 后端奖项多次选择这条线，这解释了为什么加速器或电路想法仍然需要签核和物理闭合。
- 本 venue 的当前状态：八个evidence rows形成从 2016 年到 2025 年的跨年序列。
- 方法谱系：基于物理的 EM 检查 -> 路由拓扑保证 -> EM 感知修复 -> 随机/workload 感知 EM -> 分析瞬态 EM -> 监督频谱分区 -> neural-ODE DTCO 流程建模 -> SDP 基于 decap 放置。
- 代表论文：[ICCAD-2016-P0018](../../10_corpus/ICCAD/id_index.md#ICCAD-2016-P0018)、[ICCAD-2017-P0022](../../10_corpus/ICCAD/id_index.md#ICCAD-2017-P0022)、[ICCAD-2019-P0078](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0078)、[ICCAD-2020-P0064](../../10_corpus/ICCAD/id_index.md#ICCAD-2020-P0064)、[ICCAD-2021-P0110](../../10_corpus/ICCAD/id_index.md#ICCAD-2021-P0110)、[ICCAD-2022-P0021](../../10_corpus/ICCAD/id_index.md#ICCAD-2022-P0021)、[ICCAD-2024-P0152](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0152)、[ICCAD-2025-P0012](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0012)。
- 团队线索：Najm/Sukharev EM 线路、CUHK 路由、UCSD/Kahng 物理设计和 Yao-Wen Chang PDN/decap 仅是团队领导。
- workload/artifact 信号：EM 行使用电网基准； SpecPart 使用 ISPD98/Titan23/工业 FPGA 基准； neural-ODE DTCO 和 SDP decap 行在abstract-level证据中引用了硅/工业基准设置。没有运行任何 artifact。
- 开放问题：2019/2020/2021/2024/2025 的几行仍需要完整的 PDF。商业工具比较和工业基准细节不应该从摘要中被过度解读。

### [ICCAD-SF05](#ICCAD-SF05)。硬件安全、验证和信任

- 研究问题：CAD/安全方法如何公开、验证或优化隐藏的硬件漏洞和安全计算成本。
- 背景：所选行不是一个狭窄的方法系列，但它们形成了跨设计流程、SoC 验证、处理器攻击和安全逻辑综合的venue-local安全/信任路线。
- 本 venue 的当前状态：四行证据涵盖 2016-2023 年。
- 方法谱系：FPGA 设计流程木马 -> SoC 超属性模糊测试 -> ARM 目录/snoop-filter side-channel -> 实用乱码电路的逻辑综合。
- 代表论文：[ICCAD-2016-P0054](../../10_corpus/ICCAD/id_index.md#ICCAD-2016-P0054)、[ICCAD-2020-P0111](../../10_corpus/ICCAD/id_index.md#ICCAD-2020-P0111)、[ICCAD-2022-P0067](../../10_corpus/ICCAD/id_index.md#ICCAD-2022-P0067)、[ICCAD-2023-P0185](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0185)。
- 团队线索：IIT Kanpur HyperFuzzing、EPFL/De Micheli 安全逻辑综合和 Sinha/Zhang ARM 安全仅是领先者。
- workload/artifact 信号：HyperFuzzing 具有 PDF 级别的证据；其他范围从标题/摘要到 PDF。没有验证公共代码重用。
- 开放问题：恶意 LUT 在详细机制 claim 之前需要abstract/PDF 访问权限。在超出abstract-level别措辞的平台特定 claim 之前，攻击目录需要完整的 PDF。

### [ICCAD-SF06](#ICCAD-SF06)。 AI-for-EDA 代理、电路表示和基准

- 研究问题：LLM/ML 系统如何使用可重现的基准生成、评估或支持 Verilog/RTL/HLS/EDA 工作流程。
- 背景：该系列从 2023 年的 VerilogEval 开始，并在 2024-2025 年扩展到 RTL 数据集、HLS 代理、竞赛和 ML-for-EDA 基准测试。
- 本 venue 的当前状态：六个evidence rows涵盖 2023-2025 年。 VerilogEval 目前拥有最强的已验证影响信号：OpenAlex 引用计数以及活跃的公开仓库和repository README 中的基准修订证据。
- 方法谱系：基于模拟的 Verilog 基准测试 -> 打开 RTL/assertion/data 基准测试 -> RTL-to-signoff ML-EDA 基准测试 -> LLM 辅助的 HLS 工作流程 -> 社区 Verilog 数据基础设施。
- 代表论文：[ICCAD-2023-P0106](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0106)、[ICCAD-2024-P0118](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0118)、[ICCAD-2024-P0148](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0148)、[ICCAD-2024-P0200](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0200)、[ICCAD-2024-P0213](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0213)、[ICCAD-2025-P0281](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0281)。
- 球队信号：NVIDIA、HKUST、Duke/HKUST、CAS/ICT/UCAS 和佐治亚理工学院 EIC + NVIDIA 仅为领先。
- workload/artifact 信号：VerilogEval、HLSPilot 和 LLM4HWDesign 工具包的公开仓库记录为 `runnable_unchecked`； OpenLLM-RTL、EDALearn 和 LLM4Verilog 官方 artifact 仍然缺失或未 verified。
- 开放问题：在调用这些社区标准之前，需要官方数据集 URL、基准许可证、泄漏控制和引用论文结构。

### [ICCAD-SF07](#ICCAD-SF07)。神经渲染、INR 和 3DGS 加速

- 研究问题：NeRF、INR、基于点的神经渲染和 3D Gaussian Splatting 如何满足边缘/移动实时、通信、内存和 workload 平衡约束。
- 背景：在 ICCAD 中，这是一条新兴的 2022-2025 年venue-local 线路。如果没有cross-venue比较，它不应该被提升为全球稳定的话题。
- 本 venue 的当前状态：七个evidence rows：RT-NeRF (2022)、INR-Arch/Rapid-INR (2023)、Residual-INR (2024) 和 SLTarch/GauPRE/No Redundancy, No Stall (2025)。
- 方法谱系：NeRF 算法-硬件协同设计 -> 用于训练/设备上学习的 INR 数据流/HLS/编译器和 INR 压缩 -> 针对 LoD 搜索、光栅化冗余和图块不平衡的基于点的神经渲染和 3DGS 设计。
- 代表论文：[ICCAD-2022-P0076](../../10_corpus/ICCAD/id_index.md#ICCAD-2022-P0076)、[ICCAD-2023-P0001](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0001)、[ICCAD-2023-P0024](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0024)、[ICCAD-2024-P0037](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0037)、[ICCAD-2025-P0118](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0118)、[ICCAD-2025-P0132](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0132)、[ICCAD-2025-P0252](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0252)。
- 团队线索：Rice/Georgia Tech EIC、Georgia Tech SHARC/Conghao、上海交通大学、复旦大学和 Peking/BAAI 仅是作者/项目负责人。
- workload/artifact 信号：INR-Arch、Rapid-INR 和 Residual-INR 具有公开仓库，但重用信号较低且未运行。 RT-NeRF 有一个项目页面。 2025年的3DGS论文大多缺乏这关的验证代码。
- 开放问题：验证 3DGS artifact/代码版本、2025 年论文的官方 PDF，以及后来的神经渲染加速器论文是否引用或重复使用 2022-2024 年 ICCAD INR/NeRF 工作。

### [ICCAD-SF08](#ICCAD-SF08)。逻辑综合、映射和形式推理

- 研究问题：如何进行符号、代数和布尔推理的尺度综合和形式验证。
- 背景：只有一个直接深读行分配给该小领域，因此不将其视为独立趋势。 [ICCAD-2023-P0185](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0185) 是安全逻辑综合的方法桥。
- 本 venue 的当前状态：PolyCleaner 受到奖励并具有很强的引用信号，但在选定的 ICCAD 证据集中，该子领域仍然很薄弱。
- 方法谱系：在向后重写之前基于 SCA 的算术验证和多项式清理，并桥接到用于乱码电路的 X1G/XAG 安全逻辑综合。
- 代表论文：[ICCAD-2018-P0080](../../10_corpus/ICCAD/id_index.md#ICCAD-2018-P0080)；桥：[ICCAD-2023-P0185](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0185)。
- 团队线索：Bremen/Drechsler 形式验证和 EPFL 逻辑综合线仅是线索。
- workload/artifact 信号：百万门乘法器验证基准和乱码电路基准套件是证据信号；artifact 重用未 verified。
- 开放问题：完整的 PDF/artifact 检查以及与 FMCAD、DAC 和 DATE 形式方法行的cross-venue比较。

### [ICCAD-SF10](#ICCAD-SF10)。用于加速器研究的基准/分析/仿真工具

- 研究问题：如何通过全系统仿真、能源模型、屋顶线分析、开放平台和验证框架使加速器和 CAD-flow claim 具有可比性。
- 背景：这是一个工具/评估小领域。它不应与加速机制本身相混淆。
- 本 venue 的当前状态：六个evidence rows涵盖 2019 年、2020 年和 2025 年。
- 方法谱系：离心机全系统 HLS SoC 评估 -> Golden Gate/MIDAS 模拟编译器 -> Accelergy 架构级能源估计 -> Roofline-HLS 瓶颈诊断 -> Open3DFlow 3D 芯片EDA 候选 -> Rhea 缓存一致性内存子系统验证。
- 代表论文：[ICCAD-2019-P0045](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0045)、[ICCAD-2019-P0076](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0076)、[ICCAD-2019-P0121](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0121)、[ICCAD-2020-P0129](../../10_corpus/ICCAD/id_index.md#ICCAD-2020-P0129)、[ICCAD-2025-P0308](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0308)、[ICCAD-2025-P0311](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0311)。
- 团队线索：Berkeley FireSim/Golden Gate 和 MIT/Sze/Emer Accelergy 仅是工具链领先者；没有排名。
- workload/artifact 信号：Golden Gate/MIDAS 和 Accelergy/Timeloop 具有强大的公开仓库信号。 Open3DFlow 仓库匹配仍然是 `needs_review`；未找到瑞亚代码。
- 开放问题：artifact 来源、可运行状态和基准重用仍然悬而未决。 Roofline-HLS和Open3DFlow需要abstract/PDF级别的验证。

## 4. 发展趋势

- HLS/FPGA 路线：[ICCAD-2017-P0137](../../10_corpus/ICCAD/id_index.md#ICCAD-2017-P0137)、[ICCAD-2018-P0129](../../10_corpus/ICCAD/id_index.md#ICCAD-2018-P0129)、[ICCAD-2021-P0017](../../10_corpus/ICCAD/id_index.md#ICCAD-2021-P0017)、[ICCAD-2024-P0099](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0099)、[ICCAD-2024-P0121](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0121)、[ICCAD-2025-P0280](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0280) 支持venue-local从基于模型的 HLS 分析转向算子库、物理综合感知基础设施和 3D FPGA 架构探索。
- 以内存为中心的推理路线：[ICCAD-2016-P0012](../../10_corpus/ICCAD/id_index.md#ICCAD-2016-P0012)、[ICCAD-2019-P0094](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0094)、[ICCAD-2020-P0153](../../10_corpus/ICCAD/id_index.md#ICCAD-2020-P0153)、[ICCAD-2023-P0176](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0176)、[ICCAD-2024-P0150](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0150)、[ICCAD-2024-P0208](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0208)、[ICCAD-2025-P0068](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0068)、[ICCAD-2025-P0073](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0073)、[ICCAD-2025-P0080](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0080)、[ICCAD-2025-P0101](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0101)、[ICCAD-2025-P0243](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0243) 支持ICCAD 内的 ReRAM/ISC/PIM-to-LLM 进程。
- 神经渲染/3DGS 路线：[ICCAD-2022-P0076](../../10_corpus/ICCAD/id_index.md#ICCAD-2022-P0076)、[ICCAD-2023-P0001](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0001)、[ICCAD-2023-P0024](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0024)、[ICCAD-2024-P0037](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0037)、[ICCAD-2025-P0118](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0118)、[ICCAD-2025-P0132](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0132)、[ICCAD-2025-P0252](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0252) 支持从 NeRF/INR 到基于点的渲染和 3DGS 加速器的新兴venue-local序列。
- AI-for-EDA 基准路线：[ICCAD-2023-P0106](../../10_corpus/ICCAD/id_index.md#ICCAD-2023-P0106)、[ICCAD-2024-P0118](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0118)、[ICCAD-2024-P0148](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0148)、[ICCAD-2024-P0200](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0200)、[ICCAD-2024-P0213](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0213)、[ICCAD-2025-P0281](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0281) 支持围绕 Verilog/RTL/HLS 生成和基准基础设施的 2023-2025 年序列。
- 物理闭合路线：[ICCAD-2016-P0018](../../10_corpus/ICCAD/id_index.md#ICCAD-2016-P0018)、[ICCAD-2017-P0022](../../10_corpus/ICCAD/id_index.md#ICCAD-2017-P0022)、[ICCAD-2019-P0078](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0078)、[ICCAD-2020-P0064](../../10_corpus/ICCAD/id_index.md#ICCAD-2020-P0064)、[ICCAD-2021-P0110](../../10_corpus/ICCAD/id_index.md#ICCAD-2021-P0110)、[ICCAD-2022-P0021](../../10_corpus/ICCAD/id_index.md#ICCAD-2022-P0021)、[ICCAD-2024-P0152](../../10_corpus/ICCAD/id_index.md#ICCAD-2024-P0152)、[ICCAD-2025-P0012](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0012) 支持单独的签核/闭合线，用于约束设计是否可实现。
- 工具/分析路线：[ICCAD-2019-P0045](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0045)、[ICCAD-2019-P0076](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0076)、[ICCAD-2019-P0121](../../10_corpus/ICCAD/id_index.md#ICCAD-2019-P0121)、[ICCAD-2020-P0129](../../10_corpus/ICCAD/id_index.md#ICCAD-2020-P0129)、[ICCAD-2025-P0308](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0308)、[ICCAD-2025-P0311](../../10_corpus/ICCAD/id_index.md#ICCAD-2025-P0311) 将评估基础设施作为自己的研究对象。

## 5. 方法变化

- HLS/FPGA 工作从分析/生成器行转移到在设计流程早期承载物理和架构约束的基础设施。
- PIM/CIM 工作从设备级映射和存储端仿真转向 Transformer/LLM 推理，包括移动、MoE 和 PIM-NoC 数据流。
- 神经渲染出现晚于 HLS/PIM 路线。 ICCAD 证据从 RT-NeRF 开始，然后使用 INR 作为数据流/编译器或压缩底层，然后转向 2025 基于点的渲染和 3DGS 加速器瓶颈。
- AI-for-EDA 基准测试工作从单一基准测试工具转向更广泛的数据基础设施和竞赛，但目前只有 VerilogEval 拥有经过明确验证的仓库加引用信号。
- 物理封闭仍然是一个约束层，而不是应用程序 workload：EM、路由、分区、DTCO 和 decap 行解释了加速器或芯片创意在何处满足签核现实。

## 6. 缺失来源

- 结构化 2016-2025 年官方最终节目/会议/曲目提取超出 DBLP/会议记录元数据。
- 批量 ACM DL / IEEE Xplore 摘要、关键字、PDF 和 artifact 徽章导出。
- 2026 年官方接受论文和奖项名单一旦公开。
- DNNBuilder/AccDNN、BOOM-Explorer、EISC、HD-MoE、LaZagna、VerilogEval、HLSPilot、Golden Gate/MIDAS、Accelergy 和 LLM4HWDesign 工具包的 artifact/代码可运行状态。
- OpenLLM-RTL、EDALearn 和 LLM4Verilog 的官方 artifact/数据集 URL。
- SLTarch、GauPRE 和无冗余、无停顿的代码/artifact 版本。
- OpenAlex/Semantic Scholar/施引论文的引文结构和后续采用审核。
- 针对 DAC、DATE、ASP-DAC、TCAD、FPGA/FCCM/FPL/FPT 和architecture venues 的 cross-venue evidence matrix。
