# HLS、编译器、自动调整和硬件生成闭包

<a id="FIELD-HLS-COMPILER-001-C015"></a>
对应 global_subfield_id：[GSF-04](../40_synthesis/third_wave_field_synthesis.md#GSF-04)  
证据规则：正文中的论文、工具、趋势、边界和团队线索均回到 `FIELD-HLS-COMPILER-001_paper_evidence_matrix.csv` 或 `FIELD-HLS-COMPILER-001_claim_ledger.csv`；未运行 artifact 或 benchmark 的项目只写 `runnable_unchecked`、`needs_review` 或 `impact_unverified` <a id="FIELD-HLS-COMPILER-001-C005"></a>[FIELD-HLS-COMPILER-001-C005](#FIELD-HLS-COMPILER-001-C005)<a id="FIELD-HLS-COMPILER-001-C017"></a>[FIELD-HLS-COMPILER-001-C017](#FIELD-HLS-COMPILER-001-C017)。

## 研究背景

这个 field 从跨 venue 证据中浮现，是因为同一类失败反复出现：高层描述能生成硬件，但生成结果未必能达到可用的 fmax、II、latency、resource、stall、power 或 correctness 目标。项目的 profiling inventory 明确把 resource utilization、fmax/timing slack、initiation interval、kernel latency、external memory bandwidth、pipeline stall/backpressure 和 board power/energy 作为 FPGA/HLS 解释变量 <a id="FIELD-HLS-COMPILER-001-C016"></a>[FIELD-HLS-COMPILER-001-C016](#FIELD-HLS-COMPILER-001-C016)。

和“大 FPGA”或“大 EDA”标签相比，[GSF-04](../40_synthesis/third_wave_field_synthesis.md#GSF-04) 的对象更窄：它关心算法到硬件实现之间的闭环，而不是所有 FPGA 论文、所有 placement/routing 论文或所有 AI for EDA 论文。Rosetta、Spector、HeteroCL、AutoBridge 和 LightningSim 是 cross-venue representative matrix 中直接归入 `fpga_hls_compiler_closure` 的阅读锚点；RTLLM 和 BENCH4HLS 则是相邻的 AI-for-EDA / HLS benchmark 前沿路线 <a id="FIELD-HLS-COMPILER-001-C003"></a>[FIELD-HLS-COMPILER-001-C003](#FIELD-HLS-COMPILER-001-C003)。

## 核心问题

1. 工具比较和 benchmark 公平性：HLS 工具报告、真实 board 行为和 benchmark 输入之间经常不一致。TCAD HLS tool survey、Spector 和 Rosetta 给出这一问题的早期工具/benchmark锚点 <a id="FIELD-HLS-COMPILER-001-C006"></a>[FIELD-HLS-COMPILER-001-C006](#FIELD-HLS-COMPILER-001-C006)。
2. Search cost 和 QoR predictability：DSE 不能只枚举 pragma 或 architecture choice，还要面对昂贵的 synthesis/implementation loop。HLS DSE survey、state-of-HLS study 和 GNN QoR prediction 构成方法桥 <a id="FIELD-HLS-COMPILER-001-C007"></a>[FIELD-HLS-COMPILER-001-C007](#FIELD-HLS-COMPILER-001-C007)。
3. 高层 DSL/IR 到硬件结构的表达：HeteroCL、AutoSA、Calyx 和 HIDA 说明 field 内部从 HLS pragma 走向 DSL、polyhedral/dataflow compiler 和 accelerator-generator IR <a id="FIELD-HLS-COMPILER-001-C008"></a>[FIELD-HLS-COMPILER-001-C008](#FIELD-HLS-COMPILER-001-C008)。
4. Physical/timing closure：AutoBridge、DREAMPlaceFPGA、RapidStream IR、LaZagna、HLS-Timer 和 FESTAL 都把生成后的 physical/timing/routing/fabric constraint 拉回高层设计空间 <a id="FIELD-HLS-COMPILER-001-C009"></a>[FIELD-HLS-COMPILER-001-C009](#FIELD-HLS-COMPILER-001-C009)。
5. Correctness and verification closure：HLS source-to-source transformation 可能在优化时破坏语义，因此 formal verification 也进入 closure 问题，而不只是性能附属项 <a id="FIELD-HLS-COMPILER-001-C011"></a>[FIELD-HLS-COMPILER-001-C011](#FIELD-HLS-COMPILER-001-C011)。
6. LLM-assisted generation 的评价污染：RTLLM、OpenLLM-RTL、HLS code-generation benchmark 和 BENCH4HLS 显示 LLM 设计路线正在扩展，但 benchmark contamination、QoR comparability 和 runnable status 仍是 caveat <a id="FIELD-HLS-COMPILER-001-C012"></a>[FIELD-HLS-COMPILER-001-C012](#FIELD-HLS-COMPILER-001-C012)。

## 发展脉络

**阶段 A：HLS 工具比较和 benchmark 化。** 2016 年 TCAD 的 `A Survey and Evaluation of FPGA High-Level Synthesis Tools` 是 HLS tool evaluation 的 origin anchor <a id="FIELD-HLS-COMPILER-001-E001"></a>[FIELD-HLS-COMPILER-001-E001](#FIELD-HLS-COMPILER-001-E001)<a id="FIELD-HLS-COMPILER-001-C101"></a>[FIELD-HLS-COMPILER-001-C101](#FIELD-HLS-COMPILER-001-C101)。同年 FPT 的 `Spector: An OpenCL FPGA benchmark suite` 提供 OpenCL FPGA benchmark suite 和 public result/code signal <a id="FIELD-HLS-COMPILER-001-E002"></a>[FIELD-HLS-COMPILER-001-E002](#FIELD-HLS-COMPILER-001-E002)<a id="FIELD-HLS-COMPILER-001-C102"></a>[FIELD-HLS-COMPILER-001-C102](#FIELD-HLS-COMPILER-001-C102)。2018 年 FPGA 的 `Rosetta` 将 HLS benchmark discipline 推向 software-programmable FPGA workloads <a id="FIELD-HLS-COMPILER-001-E003"></a>[FIELD-HLS-COMPILER-001-E003](#FIELD-HLS-COMPILER-001-E003)<a id="FIELD-HLS-COMPILER-001-C103"></a>[FIELD-HLS-COMPILER-001-C103](#FIELD-HLS-COMPILER-001-C103)。

**阶段 B：方法状态、DSE 和 QoR 预测。** 2019 年 TCAD 的 `Are We There Yet?` 和 2020 年 TCAD 的 HLS DSE survey 把 HLS 的成熟度、限制和 design-space automation 系统化 <a id="FIELD-HLS-COMPILER-001-E004"></a>[FIELD-HLS-COMPILER-001-E004](#FIELD-HLS-COMPILER-001-E004)<a id="FIELD-HLS-COMPILER-001-E006"></a>[FIELD-HLS-COMPILER-001-E006](#FIELD-HLS-COMPILER-001-E006)<a id="FIELD-HLS-COMPILER-001-C104"></a>[FIELD-HLS-COMPILER-001-C104](#FIELD-HLS-COMPILER-001-C104)<a id="FIELD-HLS-COMPILER-001-C106"></a>[FIELD-HLS-COMPILER-001-C106](#FIELD-HLS-COMPILER-001-C106)。2022 年 DAC 的 `High-Level Synthesis Performance Prediction using GNNs` 是 QoR prediction 路线的代表，但当前证据仍是 `needs_review`，不能写成已验证 benchmark 标准 <a id="FIELD-HLS-COMPILER-001-E011"></a>[FIELD-HLS-COMPILER-001-E011](#FIELD-HLS-COMPILER-001-E011)<a id="FIELD-HLS-COMPILER-001-C111"></a>[FIELD-HLS-COMPILER-001-C111](#FIELD-HLS-COMPILER-001-C111)。

**阶段 C：DSL、IR 和 generator compiler。** 2019 年 FPGA 的 `HeteroCL` 将 algorithm、schedule 和 customization 分层，代表 DSL/programming-infrastructure 路线 <a id="FIELD-HLS-COMPILER-001-E005"></a>[FIELD-HLS-COMPILER-001-E005](#FIELD-HLS-COMPILER-001-E005)<a id="FIELD-HLS-COMPILER-001-C105"></a>[FIELD-HLS-COMPILER-001-C105](#FIELD-HLS-COMPILER-001-C105)。2021 年 FPGA 的 `AutoSA` 把 polyhedral compilation 用于 FPGA systolic array generation <a id="FIELD-HLS-COMPILER-001-E008"></a>[FIELD-HLS-COMPILER-001-E008](#FIELD-HLS-COMPILER-001-E008)<a id="FIELD-HLS-COMPILER-001-C108"></a>[FIELD-HLS-COMPILER-001-C108](#FIELD-HLS-COMPILER-001-C108)。同年 ASPLOS 的 Calyx paper 建立 accelerator-generator compiler infrastructure，用结构与控制分离的 IR 支撑硬件生成器 <a id="FIELD-HLS-COMPILER-001-E009"></a>[FIELD-HLS-COMPILER-001-E009](#FIELD-HLS-COMPILER-001-E009)<a id="FIELD-HLS-COMPILER-001-C109"></a>[FIELD-HLS-COMPILER-001-C109](#FIELD-HLS-COMPILER-001-C109)。2024 年 ASPLOS 的 `HIDA` 则沿 hierarchical dataflow compiler 继续推进 HLS/dataflow generation <a id="FIELD-HLS-COMPILER-001-E013"></a>[FIELD-HLS-COMPILER-001-E013](#FIELD-HLS-COMPILER-001-E013)<a id="FIELD-HLS-COMPILER-001-C113"></a>[FIELD-HLS-COMPILER-001-C113](#FIELD-HLS-COMPILER-001-C113)。

**阶段 D：Physical-aware and timing-aware closure。** 2021 年 FPGA 的 `AutoBridge` 把 coarse-grained floorplanning 和 pipelining 接入 high-frequency multi-die FPGA HLS closure <a id="FIELD-HLS-COMPILER-001-E007"></a>[FIELD-HLS-COMPILER-001-E007](#FIELD-HLS-COMPILER-001-E007)<a id="FIELD-HLS-COMPILER-001-C107"></a>[FIELD-HLS-COMPILER-001-C107](#FIELD-HLS-COMPILER-001-C107)。2022 年 ASP-DAC 的 `DREAMPlaceFPGA` 是 open-source FPGA placement/physical closure 工具锚点 <a id="FIELD-HLS-COMPILER-001-E010"></a>[FIELD-HLS-COMPILER-001-E010](#FIELD-HLS-COMPILER-001-E010)<a id="FIELD-HLS-COMPILER-001-C110"></a>[FIELD-HLS-COMPILER-001-C110](#FIELD-HLS-COMPILER-001-C110)。2024 年 ICCAD 的 `RapidStream IR` 把 hierarchy、interconnect、protocol、pipelining 和 spatial information 放进 high-level physical synthesis IR <a id="FIELD-HLS-COMPILER-001-E014"></a>[FIELD-HLS-COMPILER-001-E014](#FIELD-HLS-COMPILER-001-E014)<a id="FIELD-HLS-COMPILER-001-C114"></a>[FIELD-HLS-COMPILER-001-C114](#FIELD-HLS-COMPILER-001-C114)。2025 年 ICCAD 的 `LaZagna` 将 architecture generation 和 3D FPGA physical-flow validation 作为 frontier/boundary <a id="FIELD-HLS-COMPILER-001-E020"></a>[FIELD-HLS-COMPILER-001-E020](#FIELD-HLS-COMPILER-001-E020)<a id="FIELD-HLS-COMPILER-001-C120"></a>[FIELD-HLS-COMPILER-001-C120](#FIELD-HLS-COMPILER-001-C120)。2026 年 ASP-DAC 的 FIFOAdvisor、HLS-Timer 和 FESTAL 显示 frontier 正在聚焦 FIFO sizing、path-level timing estimation 和 MLIR/dataflow synthesis <a id="FIELD-HLS-COMPILER-001-E022"></a>[FIELD-HLS-COMPILER-001-E022](#FIELD-HLS-COMPILER-001-E022)<a id="FIELD-HLS-COMPILER-001-E023"></a>[FIELD-HLS-COMPILER-001-E023](#FIELD-HLS-COMPILER-001-E023)<a id="FIELD-HLS-COMPILER-001-E024"></a>[FIELD-HLS-COMPILER-001-E024](#FIELD-HLS-COMPILER-001-E024)。

**阶段 E：Simulation/profiling feedback loop。** FCCM 2023 的 `LightningSim` 通过 LLVM trace generation 和 trace analysis 加速 HLS simulation feedback <a id="FIELD-HLS-COMPILER-001-E012"></a>[FIELD-HLS-COMPILER-001-E012](#FIELD-HLS-COMPILER-001-E012)<a id="FIELD-HLS-COMPILER-001-C112"></a>[FIELD-HLS-COMPILER-001-C112](#FIELD-HLS-COMPILER-001-C112)。FCCM 2025 的 `RealProbe` 把 profiling 进一步推到 in-FPGA execution，避免只依赖 HLS C synthesis 或 C/RTL co-simulation <a id="FIELD-HLS-COMPILER-001-E018"></a>[FIELD-HLS-COMPILER-001-E018](#FIELD-HLS-COMPILER-001-E018)<a id="FIELD-HLS-COMPILER-001-C118"></a>[FIELD-HLS-COMPILER-001-C118](#FIELD-HLS-COMPILER-001-C118)。FIFOAdvisor 则把 LightningSim-style feedback 用于 dataflow FIFO sizing [FIELD-HLS-COMPILER-001-E022](#FIELD-HLS-COMPILER-001-E022)<a id="FIELD-HLS-COMPILER-001-C122"></a>[FIELD-HLS-COMPILER-001-C122](#FIELD-HLS-COMPILER-001-C122)。

**阶段 F：LLM-assisted RTL/HLS generation。** ASP-DAC 2024 `RTLLM` 形成 LLM-assisted RTL-generation benchmark anchor <a id="FIELD-HLS-COMPILER-001-E015"></a>[FIELD-HLS-COMPILER-001-E015](#FIELD-HLS-COMPILER-001-E015)<a id="FIELD-HLS-COMPILER-001-C115"></a>[FIELD-HLS-COMPILER-001-C115](#FIELD-HLS-COMPILER-001-C115)。ICCAD 2024 `OpenLLM-RTL` 扩展到 RTLLM 2.0、AssertEval 和 RTLCoder-Data，但 repo 状态仍需复核 <a id="FIELD-HLS-COMPILER-001-E016"></a>[FIELD-HLS-COMPILER-001-E016](#FIELD-HLS-COMPILER-001-E016)<a id="FIELD-HLS-COMPILER-001-C116"></a>[FIELD-HLS-COMPILER-001-C116](#FIELD-HLS-COMPILER-001-C116)。ASP-DAC 2025 的 HLS code-generation benchmark 和 DATE 2026 `BENCH4HLS` 把 LLM 评价进一步推到 HLS compile/simulation/synthesis/PPA hooks <a id="FIELD-HLS-COMPILER-001-E019"></a>[FIELD-HLS-COMPILER-001-E019](#FIELD-HLS-COMPILER-001-E019)<a id="FIELD-HLS-COMPILER-001-E021"></a>[FIELD-HLS-COMPILER-001-E021](#FIELD-HLS-COMPILER-001-E021)<a id="FIELD-HLS-COMPILER-001-C119"></a>[FIELD-HLS-COMPILER-001-C119](#FIELD-HLS-COMPILER-001-C119)<a id="FIELD-HLS-COMPILER-001-C121"></a>[FIELD-HLS-COMPILER-001-C121](#FIELD-HLS-COMPILER-001-C121)。

## 研究方法

本 field 的方法族可以按闭环位置划分：

- Benchmark and corpus：Spector、Rosetta、RTLLM、OpenLLM-RTL、BENCH4HLS 提供 workload or task suites，但除已有 second-wave 验证的 source-backed artifact 外，不能推断社区标准化或已复现 [FIELD-HLS-COMPILER-001-C006](#FIELD-HLS-COMPILER-001-C006)[FIELD-HLS-COMPILER-001-C012](#FIELD-HLS-COMPILER-001-C012)。
- DSL/IR/compiler generation：HeteroCL、AutoSA、Calyx 和 HIDA 用 DSL、polyhedral/dataflow compiler 或 accelerator-generator IR 把算法/结构/控制分层 [FIELD-HLS-COMPILER-001-C008](#FIELD-HLS-COMPILER-001-C008)。
- DSE/QoR prediction：HLS DSE survey、GNN QoR prediction、Anchor-and-Adapt 和 HLS-Timer 指向 search cost、predictability 和 timing estimation，但部分 rows 仍需要 PDF/full artifact audit [FIELD-HLS-COMPILER-001-C007](#FIELD-HLS-COMPILER-001-C007)[FIELD-HLS-COMPILER-001-C009](#FIELD-HLS-COMPILER-001-C009)。
- Physical-aware implementation：AutoBridge、DREAMPlaceFPGA、RapidStream IR 和 LaZagna 把 floorplanning、placement、spatial information 或 fabric architecture 带入高层生成流程 [FIELD-HLS-COMPILER-001-C009](#FIELD-HLS-COMPILER-001-C009)。
- Profiling/simulation：LightningSim、RealProbe 和 FIFOAdvisor 形成从 trace simulation 到 board-side profiling 再到 FIFO sizing 的反馈路线 <a id="FIELD-HLS-COMPILER-001-C010"></a>[FIELD-HLS-COMPILER-001-C010](#FIELD-HLS-COMPILER-001-C010)。
- Correctness：Formal Verification of Source-to-Source Transformations for HLS 将 transformation correctness 纳入 HLS closure [FIELD-HLS-COMPILER-001-C011](#FIELD-HLS-COMPILER-001-C011)。

## 代表性论文与系统

| 角色 | 证据 | paper/system | 为什么它代表这个领域 |
|---|---|---|---|
| origin_anchor | [FIELD-HLS-COMPILER-001-E001](#FIELD-HLS-COMPILER-001-E001) | TCAD 2016 `A Survey and Evaluation of FPGA High-Level Synthesis Tools` | HLS 工具评估基线 [FIELD-HLS-COMPILER-001-C101](#FIELD-HLS-COMPILER-001-C101) |
| tool_benchmark | [FIELD-HLS-COMPILER-001-E002](#FIELD-HLS-COMPILER-001-E002) | FPT 2016 `Spector` | OpenCL FPGA benchmark测试套件和结果数据artifact [FIELD-HLS-COMPILER-001-C102](#FIELD-HLS-COMPILER-001-C102) |
| tool_benchmark | [FIELD-HLS-COMPILER-001-E003](#FIELD-HLS-COMPILER-001-E003) | FPGA 2018 `Rosetta` | 适用于软件可编程 FPGA [FIELD-HLS-COMPILER-001-C103](#FIELD-HLS-COMPILER-001-C103) 的真实 HLS benchmark测试套件 |
| milestone_candidate | [FIELD-HLS-COMPILER-001-E005](#FIELD-HLS-COMPILER-001-E005) | FPGA 2019 `HeteroCL` | DSL/编程-基础设施路线[FIELD-HLS-COMPILER-001-C105](#FIELD-HLS-COMPILER-001-C105) |
| milestone_candidate | [FIELD-HLS-COMPILER-001-E007](#FIELD-HLS-COMPILER-001-E007) | FPGA 2021 `AutoBridge` | 物理感知高频 HLS 闭合 [FIELD-HLS-COMPILER-001-C107](#FIELD-HLS-COMPILER-001-C107) |
| formation_paper | [FIELD-HLS-COMPILER-001-E009](#FIELD-HLS-COMPILER-001-E009) | ASPLOS 2021 萼纸 | 用于加速器生成器 [FIELD-HLS-COMPILER-001-C109](#FIELD-HLS-COMPILER-001-C109) 的编译器 IR |
| tool_benchmark | [FIELD-HLS-COMPILER-001-E012](#FIELD-HLS-COMPILER-001-E012) | FCCM 2023 `LightningSim` | 基于迹线的 HLS 模拟反馈 [FIELD-HLS-COMPILER-001-C112](#FIELD-HLS-COMPILER-001-C112) |
| method_bridge | [FIELD-HLS-COMPILER-001-E014](#FIELD-HLS-COMPILER-001-E014) | ICCAD 2024 `RapidStream IR` | 高级物理综合桥[FIELD-HLS-COMPILER-001-C114](#FIELD-HLS-COMPILER-001-C114) |
| formation_paper | [FIELD-HLS-COMPILER-001-E015](#FIELD-HLS-COMPILER-001-E015) | ASP-DAC 2024 `RTLLM` | LLM辅助RTL一代benchmark形成[FIELD-HLS-COMPILER-001-C115](#FIELD-HLS-COMPILER-001-C115) |
| milestone_candidate | <a id="FIELD-HLS-COMPILER-001-E017"></a>[FIELD-HLS-COMPILER-001-E017](#FIELD-HLS-COMPILER-001-E017) | FPGA 2024 `Formal Verification of Source-to-Source Transformations for HLS` | HLS 变换 <a id="FIELD-HLS-COMPILER-001-C117"></a>[FIELD-HLS-COMPILER-001-C117](#FIELD-HLS-COMPILER-001-C117) 的正确性闭包 |
| frontier | [FIELD-HLS-COMPILER-001-E018](#FIELD-HLS-COMPILER-001-E018) | FCCM 2025 `RealProbe` | in-FPGA HLS 分析 [FIELD-HLS-COMPILER-001-C118](#FIELD-HLS-COMPILER-001-C118) |
| tool_benchmark | [FIELD-HLS-COMPILER-001-E021](#FIELD-HLS-COMPILER-001-E021) | DATE 2026 `BENCH4HLS` | 端到端 LLM-HLS 评估候选 [FIELD-HLS-COMPILER-001-C121](#FIELD-HLS-COMPILER-001-C121) |
| frontier | [FIELD-HLS-COMPILER-001-E022](#FIELD-HLS-COMPILER-001-E022) | ASP-DAC 2026 `FIFOAdvisor` | 模拟引导 FIFO 尺寸调整 [FIELD-HLS-COMPILER-001-C122](#FIELD-HLS-COMPILER-001-C122) |
| frontier | [FIELD-HLS-COMPILER-001-E023](#FIELD-HLS-COMPILER-001-E023) | ASP-DAC 2026 `HLS-Timer` | 路径级时序估计 <a id="FIELD-HLS-COMPILER-001-C123"></a>[FIELD-HLS-COMPILER-001-C123](#FIELD-HLS-COMPILER-001-C123) |
| frontier | [FIELD-HLS-COMPILER-001-E024](#FIELD-HLS-COMPILER-001-E024) | ASP-DAC 2026 `FESTAL` | MLIR/数据流综合前沿，仍需奖励/档案审查 <a id="FIELD-HLS-COMPILER-001-C124"></a>[FIELD-HLS-COMPILER-001-C124](#FIELD-HLS-COMPILER-001-C124) |
| negative_boundary | <a id="FIELD-HLS-COMPILER-001-E026"></a>[FIELD-HLS-COMPILER-001-E026](#FIELD-HLS-COMPILER-001-E026) | FPT 2024 `FINN-T` | 特定于workload的 Transformer FPGA 数据流主要属于 LLM/低精度边界 <a id="FIELD-HLS-COMPILER-001-C126"></a>[FIELD-HLS-COMPILER-001-C126](#FIELD-HLS-COMPILER-001-C126) |
| negative_boundary | <a id="FIELD-HLS-COMPILER-001-E027"></a>[FIELD-HLS-COMPILER-001-E027](#FIELD-HLS-COMPILER-001-E027) | VLSI 2026数字CIM编译器行 | `compiler` 内部的命名 CIM/PIM 并不使其成为 HLS/编译器关闭 <a id="FIELD-HLS-COMPILER-001-C127"></a>[FIELD-HLS-COMPILER-001-C127](#FIELD-HLS-COMPILER-001-C127) |

## 团队与会议线索

Venue activity 广泛但不统一。 FPGA/FCCM/FPT/FPL 供应核心 FPGA/HLS 和benchmark/工具行； DAC/ICCAD/ASP-DAC/DATE/TCAD贡献EDA、HLS、DSE、LLM-设计和物理闭合行； ASPLOS/MLSys/PACT/SC 贡献编译器/runtime/codegen 桥； CICC/VLSI/Hot Chips主要提供端点或边界信号<a id="FIELD-HLS-COMPILER-001-C001"></a>[FIELD-HLS-COMPILER-001-C001](#FIELD-HLS-COMPILER-001-C001)。

团队信号仅作为源支持的活动线索包含在内。cross-venue团队矩阵标记了诸如佐治亚理工学院SHARC/丛浩、微软Catapult、EPFL/AMD路由以及几个部分FPGA/HLS或LLM设计项目信号等行，但项目规则禁止将这些转化为排名或“领先团队”claim<a id="FIELD-HLS-COMPILER-001-C013"></a>[FIELD-HLS-COMPILER-001-C013](#FIELD-HLS-COMPILER-001-C013)。在论文证据矩阵中，团队字符串保留为 `author_string`、`project signal` 或 `lab line`；未解决的实体边界仍然需要注意。

## 开放问题

1. QoR 可预测性仍然存在阶段不匹配：HLS 估计、综合报告、实施时序和电路板测量不能互换 [FIELD-HLS-COMPILER-001-C016](#FIELD-HLS-COMPILER-001-C016)。
2. benchmark套件是可用的，但标准化和独立重用并不均衡。 Rosetta、Spector、RTLLM 和 BENCH4HLS 是有用的锚点，而不是自动证明全场再现性 [FIELD-HLS-COMPILER-001-C005](#FIELD-HLS-COMPILER-001-C005)[FIELD-HLS-COMPILER-001-C006](#FIELD-HLS-COMPILER-001-C006)[FIELD-HLS-COMPILER-001-C012](#FIELD-HLS-COMPILER-001-C012)。
3. 物理感知 HLS 内部仍然分为布局规划/流水线、布局、高级物理综合 IR、时序估计和结构架构探索 [FIELD-HLS-COMPILER-001-C009](#FIELD-HLS-COMPILER-001-C009)。
4. LLM辅助设计需要抗污染任务和端到端编译/模拟/综合/PPA检查；当前行属于前沿行，许多artifact status仍为 `runnable_unchecked` 或 `needs_review` [FIELD-HLS-COMPILER-001-C012](#FIELD-HLS-COMPILER-001-C012)。
5. 与性能收敛相比，正确性收敛的代表性不足；正式的 HLS 转换行显示了该问题，但其本身并未建立成熟的验证子字段 [FIELD-HLS-COMPILER-001-C011](#FIELD-HLS-COMPILER-001-C011)。

## 连接到用户方向

对于 FPGA 研究，[GSF-04](../40_synthesis/third_wave_field_synthesis.md#GSF-04) 是直接方法层：它告诉设计claim的哪些部分必须通过资源、II、时序、延迟、停顿、电路板测量或artifact evidence来关闭，而不是在算法级加速 <a id="FIELD-HLS-COMPILER-001-C014"></a>[FIELD-HLS-COMPILER-001-C014](#FIELD-HLS-COMPILER-001-C014)[FIELD-HLS-COMPILER-001-C016](#FIELD-HLS-COMPILER-001-C016) 上停止。

对于 3DGS 和神经渲染来说，这个领域并不是视觉workload本身。它的相关性在于将排序/bin/混合/光栅化子图映射到HLS/数据流kernel，选择FIFO和存储器，并证明FPGA或加速器实现实际上满足fmax和延迟约束[FIELD-HLS-COMPILER-001-C014](#FIELD-HLS-COMPILER-001-C014)。

对于机器人和嵌入式边缘计算，该字段是低延迟 FPGA/SoC 实现的闭合层：明确报告 II、fmax、延迟、内存带宽、失速/背压和电路板功率边界，并避免将工具估计与系统内测量 [FIELD-HLS-COMPILER-001-C016](#FIELD-HLS-COMPILER-001-C016) 混合。

## 缺失来源

- 对于几个仅元数据/摘要的行，仍然需要完整的 PDF 级技术提取，特别是 DAC 2022 HLS GNN 预测和一些 2026 前沿行 [FIELD-HLS-COMPILER-001-C111](#FIELD-HLS-COMPILER-001-C111)[FIELD-HLS-COMPILER-001-C123](#FIELD-HLS-COMPILER-001-C123)。
- 部分 2026 ASP-DAC 信号仍需要规范授予/存档确认；本报告将它们保留为前沿或 needs_review，而不是长期里程碑 [FIELD-HLS-COMPILER-001-C124](#FIELD-HLS-COMPILER-001-C124)。
- 此处列出的所有公共存储库均不执行artifact，包括 Spector、Rosetta、HeteroCL、AutoBridge、AutoSA、Calyx、HIDA、LightningSim、RealProbe、FIFOAdvisor 和 BENCH4HLS [FIELD-HLS-COMPILER-001-C017](#FIELD-HLS-COMPILER-001-C017)。
- LLM 辅助设计benchmark 污染和隐藏测试重叠需要在使用benchmark 分数作为稳定证据 [FIELD-HLS-COMPILER-001-C012](#FIELD-HLS-COMPILER-001-C012) 之前进行单独审核。
- 作者、实验室和公司团队的实体消歧仍然不完整；不应推断出任何排名或强度claim [FIELD-HLS-COMPILER-001-C013](#FIELD-HLS-COMPILER-001-C013)。
