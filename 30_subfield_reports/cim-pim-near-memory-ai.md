# CIM/PIM/内存墙workload的近内存执行

对应 global_subfield_id：[GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03)  
证据规则：正文中的论文、系统、趋势、边界和团队线索均回到 `FIELD-CIM-PIM-001_paper_evidence_matrix.csv` 或 `FIELD-CIM-PIM-001_claim_ledger.csv`；未运行 artifact、benchmark、simulator 或 chip measurement 的内容只写 `runnable_unchecked`、`needs_review` 或 `impact_unverified` <a id="FIELD-CIM-PIM-001-C016"></a>[FIELD-CIM-PIM-001-C016](#FIELD-CIM-PIM-001-C016)。

## 研究背景

[GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03) 从跨 venue 证据中浮现，是因为 memory-wall 问题在多个层级反复出现：宏单元层面的 bitline/wordline 数据搬运，chip 层面的 SRAM/RRAM/PCM/DRAM/HBM 容量和带宽，系统层面的 host-device movement，以及 LLM/Transformer 中 attention、KV/cache、long-context 和 decode/GEMV 相关的数据流压力 <a id="FIELD-CIM-PIM-001-C001"></a>[FIELD-CIM-PIM-001-C001](#FIELD-CIM-PIM-001-C001)<a id="FIELD-CIM-PIM-001-C007"></a>[FIELD-CIM-PIM-001-C007](#FIELD-CIM-PIM-001-C007)<a id="FIELD-CIM-PIM-001-C008"></a>[FIELD-CIM-PIM-001-C008](#FIELD-CIM-PIM-001-C008)。

和“大 AI accelerator”或“memory system”标签相比，这个 field 更窄。它关心的是计算位置是否被移到 memory array、bank、stack、near-DRAM/NDP runtime 或 PIM software stack 附近，以及这种迁移如何改变能耗、带宽、精度、容量、编程接口和评价方法。它不把所有 memory hierarchy 优化都算作 PIM/CIM，也不把 circuit/device title match 直接写成系统级结论 <a id="FIELD-CIM-PIM-001-C003"></a>[FIELD-CIM-PIM-001-C003](#FIELD-CIM-PIM-001-C003)<a id="FIELD-CIM-PIM-001-C005"></a>[FIELD-CIM-PIM-001-C005](#FIELD-CIM-PIM-001-C005)。

## 核心问题

1. 数据搬运是否真的减少：SRAM-CIM、ReRAM/PCM-CIM、DRAM/HBM-PIM 都以减少 memory-to-compute movement 为目标，但 peripheral、ADC/DAC、bank/array utilization、host synchronization 和 software mapping 可能吃掉收益 [FIELD-CIM-PIM-001-C008](#FIELD-CIM-PIM-001-C008)<a id="FIELD-CIM-PIM-001-C014"></a>[FIELD-CIM-PIM-001-C014](#FIELD-CIM-PIM-001-C014)。
2. 宏单元指标和系统指标不等价：TOPS/W、MAC latency、uJ/token、GB/s/mm2、area efficiency 和 benchmark speedup 不能直接跨 analog CIM、digital CIM、DRAM-PIM 和 software-PIM 比较 [FIELD-CIM-PIM-001-C014](#FIELD-CIM-PIM-001-C014)。
3. 精度、可靠性和器件非理想性：PCM/RRAM/analog CIM 需要同时处理 update、endurance、variation、ECC、ADC/DAC 和 quantization overhead，而不只是报告 compute density <a id="FIELD-CIM-PIM-001-C011"></a>[FIELD-CIM-PIM-001-C011](#FIELD-CIM-PIM-001-C011)。
4. 编程与工具链：如果没有 software framework、compilation/simulation tools 和 profiling/benchmark discipline，PIM/CIM 很难从 single design point 变成可比较系统路线 [FIELD-CIM-PIM-001-C014](#FIELD-CIM-PIM-001-C014)。
5. LLM frontier 的 workload-specific 压力：Transformer attention、softmax、tall-skinny GEMM、KV/cache、long-context 和 LoRA fine-tuning 正在把 CIM/PIM 从 CNN macro line 推到 model/runtime/data-placement line，但很多 2025-2026 rows 仍是 early frontier 或 needs_review [FIELD-CIM-PIM-001-C007](#FIELD-CIM-PIM-001-C007)<a id="FIELD-CIM-PIM-001-C013"></a>[FIELD-CIM-PIM-001-C013](#FIELD-CIM-PIM-001-C013)。

## 发展脉络

**Stage A: SRAM-CIM origin and mixed-signal macro formation.** VLSI 2016 的 `A machine-learning classifier implemented in a standard 6T SRAM array` 是本报告的 SRAM-CIM origin anchor，展示在标准 6T SRAM 内执行 ML classifier 以减少 memory traffic <a id="FIELD-CIM-PIM-001-E001"></a>[FIELD-CIM-PIM-001-E001](#FIELD-CIM-PIM-001-E001)<a id="FIELD-CIM-PIM-001-C101"></a>[FIELD-CIM-PIM-001-C101](#FIELD-CIM-PIM-001-C101)。ISSCC 2018 `Conv-RAM` 将 SRAM embedded compute 推向 convolution/CNN inference chip evidence <a id="FIELD-CIM-PIM-001-E002"></a>[FIELD-CIM-PIM-001-E002](#FIELD-CIM-PIM-001-E002)<a id="FIELD-CIM-PIM-001-C102"></a>[FIELD-CIM-PIM-001-C102](#FIELD-CIM-PIM-001-C102)。A-SSCC 2019 mixed-signal SRAM IMC macro 则把 XNOR、voltage-mode accumulation 和 row-by-row ADC 放入路线中，提示 peripheral cost 是 CIM 的核心问题之一 <a id="FIELD-CIM-PIM-001-E003"></a>[FIELD-CIM-PIM-001-E003](#FIELD-CIM-PIM-001-E003)<a id="FIELD-CIM-PIM-001-C103"></a>[FIELD-CIM-PIM-001-C103](#FIELD-CIM-PIM-001-C103)。

**Stage B: NVM/PCM/RRAM CIM and learning/reliability concerns.** VLSI 2019 PCM synapse continual-learning row 说明 CIM 不只服务 fixed-weight inference，还进入 online/continual learning 和 memory-device update 问题 <a id="FIELD-CIM-PIM-001-E004"></a>[FIELD-CIM-PIM-001-E004](#FIELD-CIM-PIM-001-E004)<a id="FIELD-CIM-PIM-001-C104"></a>[FIELD-CIM-PIM-001-C104](#FIELD-CIM-PIM-001-C104)。这条线在 cross-venue inventory 中和 RRAM、STT-MRAM、FeFET 等 rows 交叉，但本报告只保留能解释 [GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03) 边界的代表 evidence，未把所有 device rows 展开 [FIELD-CIM-PIM-001-C003](#FIELD-CIM-PIM-001-C003)[FIELD-CIM-PIM-001-C011](#FIELD-CIM-PIM-001-C011)。

**Stage C: DRAM/HBM PIM and industry/system disclosure.** ISSCC 2021 `25.4 A 20nm 6GB Function-In-Memory DRAM...` 是 HBM2 Function-In-Memory DRAM milestone candidate，代表从 on-chip SRAM/RRAM macro 转到 stacked memory/bank-level programmable units 的路线 <a id="FIELD-CIM-PIM-001-E005"></a>[FIELD-CIM-PIM-001-E005](#FIELD-CIM-PIM-001-E005)<a id="FIELD-CIM-PIM-001-C105"></a>[FIELD-CIM-PIM-001-C105](#FIELD-CIM-PIM-001-C105)。Hot Chips 2021 Aquabolt-XL 和 Hot Chips 2023 Samsung AI-cluster slide rows 是 source-backed industry activity signals，显示 HBM-PIM、CXL-based processing-near-memory 和 transformer-based LLM memory pressure 的系统化披露，但这些 presentation rows 不能当作 artifact reproduction 或 independent adoption proof <a id="FIELD-CIM-PIM-001-E014"></a>[FIELD-CIM-PIM-001-E014](#FIELD-CIM-PIM-001-E014)<a id="FIELD-CIM-PIM-001-E015"></a>[FIELD-CIM-PIM-001-E015](#FIELD-CIM-PIM-001-E015)<a id="FIELD-CIM-PIM-001-C114"></a>[FIELD-CIM-PIM-001-C114](#FIELD-CIM-PIM-001-C114)<a id="FIELD-CIM-PIM-001-C115"></a>[FIELD-CIM-PIM-001-C115](#FIELD-CIM-PIM-001-C115)。

**Stage D: Transformer and LLM PIM/CIM formation.** ISSCC 2022 sparse Transformer CIM chip、HPCA 2022 `TransPIM` 和 A-SSCC 2023 `CIMFormer` 构成早期 Transformer/attention PIM/CIM formation line <a id="FIELD-CIM-PIM-001-E009"></a>[FIELD-CIM-PIM-001-E009](#FIELD-CIM-PIM-001-E009)<a id="FIELD-CIM-PIM-001-E010"></a>[FIELD-CIM-PIM-001-E010](#FIELD-CIM-PIM-001-E010)<a id="FIELD-CIM-PIM-001-E011"></a>[FIELD-CIM-PIM-001-E011](#FIELD-CIM-PIM-001-E011)。这些 rows 把问题从 CNN convolution MAC 移到 token、attention、weight reload、sparsity、quantization 和 software-hardware co-design [FIELD-CIM-PIM-001-C013](#FIELD-CIM-PIM-001-C013)。

**Stage E: 2024-2026 LLM frontier.** HPCA 2024 large-batched generative model inference, DATE 2025 DOTS, DATE 2025 SEGTRANSFORMER, DAC 2025 AttenPIM, DAC 2025 BlockPIM, CICC 2025 FlashAttention DCIM, A-SSCC 2025 LoRA-CIM, HPCA 2026 PIMphony, ISSCC 2026 3D DRAM-logic PNM, and JSSC 2026 HyAtt/DPIM collectively support the trend that [GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03) is moving into Transformer/LLM attention, KV/cache, long-context, softmax, FlashAttention/FlashMLA, and fine-tuning workloads <a id="FIELD-CIM-PIM-001-E016"></a>[FIELD-CIM-PIM-001-E016](#FIELD-CIM-PIM-001-E016)<a id="FIELD-CIM-PIM-001-E017"></a>[FIELD-CIM-PIM-001-E017](#FIELD-CIM-PIM-001-E017)<a id="FIELD-CIM-PIM-001-E018"></a>[FIELD-CIM-PIM-001-E018](#FIELD-CIM-PIM-001-E018)<a id="FIELD-CIM-PIM-001-E019"></a>[FIELD-CIM-PIM-001-E019](#FIELD-CIM-PIM-001-E019)<a id="FIELD-CIM-PIM-001-E020"></a>[FIELD-CIM-PIM-001-E020](#FIELD-CIM-PIM-001-E020)<a id="FIELD-CIM-PIM-001-E021"></a>[FIELD-CIM-PIM-001-E021](#FIELD-CIM-PIM-001-E021)<a id="FIELD-CIM-PIM-001-E022"></a>[FIELD-CIM-PIM-001-E022](#FIELD-CIM-PIM-001-E022)<a id="FIELD-CIM-PIM-001-E026"></a>[FIELD-CIM-PIM-001-E026](#FIELD-CIM-PIM-001-E026)<a id="FIELD-CIM-PIM-001-E027"></a>[FIELD-CIM-PIM-001-E027](#FIELD-CIM-PIM-001-E027)<a id="FIELD-CIM-PIM-001-E028"></a>[FIELD-CIM-PIM-001-E028](#FIELD-CIM-PIM-001-E028)<a id="FIELD-CIM-PIM-001-E029"></a>[FIELD-CIM-PIM-001-E029](#FIELD-CIM-PIM-001-E029)[FIELD-CIM-PIM-001-C007](#FIELD-CIM-PIM-001-C007)[FIELD-CIM-PIM-001-C013](#FIELD-CIM-PIM-001-C013)。但这条 frontier 很新：多行是 official-page、abstract 或 title-level evidence，不能写成 stable subfield 或 reproduced result。

**Stage F: Tools, software frameworks, and artifact-evaluation.** NeuroSim 和 CICC 2022 IMC benchmarking row 是 circuit/modeling/benchmark methodology anchors <a id="FIELD-CIM-PIM-001-E006"></a>[FIELD-CIM-PIM-001-E006](#FIELD-CIM-PIM-001-E006)<a id="FIELD-CIM-PIM-001-E007"></a>[FIELD-CIM-PIM-001-E007](#FIELD-CIM-PIM-001-E007)。CoMeFa 把 FPGA BRAM 作为 compute substrate，SimplePIM 和 PyPIM 把 PIM 暴露到 software/framework/interface，UniNDP 指向 near-DRAM processing compilation and simulation，DRIM-ANN 和 SC25 reproducibility report 提供 commercial DRAM-PIM application and artifact-evaluation signals <a id="FIELD-CIM-PIM-001-E008"></a>[FIELD-CIM-PIM-001-E008](#FIELD-CIM-PIM-001-E008)<a id="FIELD-CIM-PIM-001-E012"></a>[FIELD-CIM-PIM-001-E012](#FIELD-CIM-PIM-001-E012)<a id="FIELD-CIM-PIM-001-E013"></a>[FIELD-CIM-PIM-001-E013](#FIELD-CIM-PIM-001-E013)<a id="FIELD-CIM-PIM-001-E023"></a>[FIELD-CIM-PIM-001-E023](#FIELD-CIM-PIM-001-E023)<a id="FIELD-CIM-PIM-001-E024"></a>[FIELD-CIM-PIM-001-E024](#FIELD-CIM-PIM-001-E024)<a id="FIELD-CIM-PIM-001-E025"></a>[FIELD-CIM-PIM-001-E025](#FIELD-CIM-PIM-001-E025)[FIELD-CIM-PIM-001-C014](#FIELD-CIM-PIM-001-C014)。

## 研究方法

本 field 的方法族可以按“compute 被放在哪里”和“如何评价”来拆分。

- SRAM/digital/mixed-signal CIM：代表 rows 是 VLSI 2016 SRAM classifier、ISSCC 2018 Conv-RAM、A-SSCC 2019 mixed-signal SRAM macro 和 later Transformer CIM rows。核心指标包括 array utilization、TOPS/W、MAC latency、precision、ADC/accumulation overhead 和 memory traffic <a id="FIELD-CIM-PIM-001-C010"></a>[FIELD-CIM-PIM-001-C010](#FIELD-CIM-PIM-001-C010)。
- NVM/analog CIM：代表 row 是 VLSI 2019 PCM continual learning，相关问题包括 update endurance、analog variation、quantization、accuracy recovery 和 continual/on-chip learning [FIELD-CIM-PIM-001-C011](#FIELD-CIM-PIM-001-C011)。
- DRAM/HBM PIM and PNM：代表 rows 是 ISSCC 2021 HBM2 FIM DRAM、Hot Chips Aquabolt-XL 和 Samsung HBM-PIM/CXL-PNM disclosure。这里的重点从 MAC cell 转向 bank-level parallelism、capacity/bandwidth exposure 和 system integration <a id="FIELD-CIM-PIM-001-C012"></a>[FIELD-CIM-PIM-001-C012](#FIELD-CIM-PIM-001-C012)。
- Transformer/LLM PIM：代表 rows 覆盖 sparse Transformer CIM、TransPIM、CIMFormer、DOTS、SEGTRANSFORMER、AttenPIM、BlockPIM、FlashAttention DCIM、LoRA-CIM、PIMphony、3D DRAM-logic PNM、HyAtt 和 DPIM。评价对象从 CNN accuracy/energy 转到 token、attention、softmax、GEMV/GEMM、KV/cache 和 long-context placement [FIELD-CIM-PIM-001-C013](#FIELD-CIM-PIM-001-C013)。
- Tool and benchmark infrastructure：NeuroSim、CICC IMC benchmarking、SimplePIM、PyPIM、UniNDP 和 DRIM-ANN reproducibility rows 提供 modeling、benchmark methodology、software framework、compiler/simulator 或 artifact-evaluation signals；本任务未执行任何工具或 benchmark [FIELD-CIM-PIM-001-C014](#FIELD-CIM-PIM-001-C014)[FIELD-CIM-PIM-001-C016](#FIELD-CIM-PIM-001-C016)。

## 代表性论文与系统

| 角色 | 证据 | paper/system | 为什么它代表这个领域 |
|---|---|---|---|
| origin_anchor | [FIELD-CIM-PIM-001-E001](#FIELD-CIM-PIM-001-E001) | VLSI 2016 `A machine-learning classifier implemented in a standard 6T SRAM array` | 标准6T SRAM作为计算基板[FIELD-CIM-PIM-001-C101](#FIELD-CIM-PIM-001-C101) |
| origin_anchor | [FIELD-CIM-PIM-001-E002](#FIELD-CIM-PIM-001-E002) | ISSCC 2018 `Conv-RAM` | SRAM 用于 CNN 推理的卷积计算 [FIELD-CIM-PIM-001-C102](#FIELD-CIM-PIM-001-C102) |
| formation_paper | [FIELD-CIM-PIM-001-E003](#FIELD-CIM-PIM-001-E003) | A-SSCC 2019混合信号 SRAM IMC 宏 | ADC/SRAM-CIM [FIELD-CIM-PIM-001-C103](#FIELD-CIM-PIM-001-C103) 中的累积权衡 |
| milestone_candidate | [FIELD-CIM-PIM-001-E004](#FIELD-CIM-PIM-001-E004) | VLSI 2019 PCM 突触持续学习 | NVM/PCM CIM 适合学习，不仅仅是推理 [FIELD-CIM-PIM-001-C104](#FIELD-CIM-PIM-001-C104) |
| milestone_candidate | [FIELD-CIM-PIM-001-E005](#FIELD-CIM-PIM-001-E005) | ISSCC 2021 HBM2 内存中函数 DRAM | DRAM/HBM PIM 里程碑候选者 [FIELD-CIM-PIM-001-C105](#FIELD-CIM-PIM-001-C105) |
| tool_benchmark | [FIELD-CIM-PIM-001-E006](#FIELD-CIM-PIM-001-E006) | TCAD 2018 `NeuroSim` | 电路级benchmark/模型锚点 <a id="FIELD-CIM-PIM-001-C106"></a>[FIELD-CIM-PIM-001-C106](#FIELD-CIM-PIM-001-C106) |
| tool_benchmark | [FIELD-CIM-PIM-001-E007](#FIELD-CIM-PIM-001-E007) | CICC 2022 IMC benchmark测试方法 | IMC 趋势benchmark与未经检查的公共repository <a id="FIELD-CIM-PIM-001-C107"></a>[FIELD-CIM-PIM-001-C107](#FIELD-CIM-PIM-001-C107) |
| method_bridge | [FIELD-CIM-PIM-001-E008](#FIELD-CIM-PIM-001-E008) | FCCM 2022 `CoMeFa` | FPGA BRAM-to-CIM 方法电桥 <a id="FIELD-CIM-PIM-001-C108"></a>[FIELD-CIM-PIM-001-C108](#FIELD-CIM-PIM-001-C108) |
| formation_paper | [FIELD-CIM-PIM-001-E009](#FIELD-CIM-PIM-001-E009) | ISSCC 2022稀疏Transformer CIM芯片 | 令牌/Transformer CIM 硅形成 <a id="FIELD-CIM-PIM-001-C109"></a>[FIELD-CIM-PIM-001-C109](#FIELD-CIM-PIM-001-C109) |
| formation_paper | [FIELD-CIM-PIM-001-E010](#FIELD-CIM-PIM-001-E010) | HPCA 2022 `TransPIM` | 架构侧Transformer PIM 协同设计 <a id="FIELD-CIM-PIM-001-C110"></a>[FIELD-CIM-PIM-001-C110](#FIELD-CIM-PIM-001-C110) |
| milestone_candidate | [FIELD-CIM-PIM-001-E011](#FIELD-CIM-PIM-001-E011) | A-SSCC 2023 `CIMFormer` | CIM <a id="FIELD-CIM-PIM-001-C111"></a>[FIELD-CIM-PIM-001-C111](#FIELD-CIM-PIM-001-C111) 中Transformer注意数据移动 |
| tool_benchmark | [FIELD-CIM-PIM-001-E012](#FIELD-CIM-PIM-001-E012) | PACT 2023 `SimplePIM` | 生产性软件架构路线<a id="FIELD-CIM-PIM-001-C112"></a>[FIELD-CIM-PIM-001-C112](#FIELD-CIM-PIM-001-C112) |
| tool_benchmark | [FIELD-CIM-PIM-001-E013](#FIELD-CIM-PIM-001-E013) | MICRO 2024 `PyPIM` | Python/tensor与数字 PIM 的接口，需要审查 <a id="FIELD-CIM-PIM-001-C113"></a>[FIELD-CIM-PIM-001-C113](#FIELD-CIM-PIM-001-C113) |
| method_bridge | [FIELD-CIM-PIM-001-E014](#FIELD-CIM-PIM-001-E014) | 热门芯片 2021 Aquabolt-XL | HBM2-PIM 行业活动信号 [FIELD-CIM-PIM-001-C114](#FIELD-CIM-PIM-001-C114) |
| method_bridge | [FIELD-CIM-PIM-001-E015](#FIELD-CIM-PIM-001-E015) | 热门芯片 2023 三星 HBM-PIM/CXL-PNM LLM 系统 | HBM-PIM加PNM系统披露[FIELD-CIM-PIM-001-C115](#FIELD-CIM-PIM-001-C115) |
| frontier | [FIELD-CIM-PIM-001-E017](#FIELD-CIM-PIM-001-E017) | DATE 2025 `DOTS` | DRAM-PIM 为高瘦 GEMM 中的 LLM 推理 <a id="FIELD-CIM-PIM-001-C117"></a>[FIELD-CIM-PIM-001-C117](#FIELD-CIM-PIM-001-C117) |
| frontier | [FIELD-CIM-PIM-001-E018](#FIELD-CIM-PIM-001-E018) | DATE 2025 `SEGTRANSFORMER` | ReRAM-PIM 支持 Transformer softmax <a id="FIELD-CIM-PIM-001-C118"></a>[FIELD-CIM-PIM-001-C118](#FIELD-CIM-PIM-001-C118) |
| frontier | [FIELD-CIM-PIM-001-E019](#FIELD-CIM-PIM-001-E019) | DAC 2025 `AttenPIM` | LLM 注意搭配 PIM 双模 GEMV <a id="FIELD-CIM-PIM-001-C119"></a>[FIELD-CIM-PIM-001-C119](#FIELD-CIM-PIM-001-C119) |
| frontier | [FIELD-CIM-PIM-001-E020](#FIELD-CIM-PIM-001-E020) | DAC 2025 `BlockPIM` | 长上下文 PIM 内存管理 <a id="FIELD-CIM-PIM-001-C120"></a>[FIELD-CIM-PIM-001-C120](#FIELD-CIM-PIM-001-C120) |
| frontier | [FIELD-CIM-PIM-001-E021](#FIELD-CIM-PIM-001-E021) | CICC 2025 FlashAttention DCIM 加速器 | 数字 CIM 加 FlashAttention LLM 信号 <a id="FIELD-CIM-PIM-001-C121"></a>[FIELD-CIM-PIM-001-C121](#FIELD-CIM-PIM-001-C121) |
| frontier | [FIELD-CIM-PIM-001-E022](#FIELD-CIM-PIM-001-E022) | A-SSCC 2025 `LoRA-CIM` | 混合闪存-SRAM CIM 边缘 LLM 微调 <a id="FIELD-CIM-PIM-001-C122"></a>[FIELD-CIM-PIM-001-C122](#FIELD-CIM-PIM-001-C122) |
| tool_benchmark | [FIELD-CIM-PIM-001-E023](#FIELD-CIM-PIM-001-E023) | HPCA 2025 `UniNDP` | 近DRAM编译/仿真工具候选<a id="FIELD-CIM-PIM-001-C123"></a>[FIELD-CIM-PIM-001-C123](#FIELD-CIM-PIM-001-C123) |
| frontier | [FIELD-CIM-PIM-001-E024](#FIELD-CIM-PIM-001-E024) | SC 2025 `DRIM-ANN` | 具有repository信号 <a id="FIELD-CIM-PIM-001-C124"></a>[FIELD-CIM-PIM-001-C124](#FIELD-CIM-PIM-001-C124) 的商业 DRAM-PIM 应用 |
| tool_benchmark | [FIELD-CIM-PIM-001-E025](#FIELD-CIM-PIM-001-E025) | SC25 DRIM-ANN 重现性报告 | 文物评估证据，非本地复制 <a id="FIELD-CIM-PIM-001-C125"></a>[FIELD-CIM-PIM-001-C125](#FIELD-CIM-PIM-001-C125) |
| frontier | [FIELD-CIM-PIM-001-E026](#FIELD-CIM-PIM-001-E026) | HPCA 2026 `PIMphony` | 长上下文 LLM PIM 前沿 <a id="FIELD-CIM-PIM-001-C126"></a>[FIELD-CIM-PIM-001-C126](#FIELD-CIM-PIM-001-C126) |
| frontier | [FIELD-CIM-PIM-001-E027](#FIELD-CIM-PIM-001-E027) | ISSCC 2026 3D 二合一 DRAM 一逻辑 PNM 芯片 | 3D DRAM-逻辑 PNM 用于边缘 LLM <a id="FIELD-CIM-PIM-001-C127"></a>[FIELD-CIM-PIM-001-C127](#FIELD-CIM-PIM-001-C127) |
| frontier | [FIELD-CIM-PIM-001-E028](#FIELD-CIM-PIM-001-E028) | JSSC 2026 `HyAtt` | 模拟内存Transformer关注，标题级<a id="FIELD-CIM-PIM-001-C128"></a>[FIELD-CIM-PIM-001-C128](#FIELD-CIM-PIM-001-C128) |
| frontier | [FIELD-CIM-PIM-001-E029](#FIELD-CIM-PIM-001-E029) | JSSC 2026 `DPIM` | eDRAM Transformer-in-Memory芯片，标题级<a id="FIELD-CIM-PIM-001-C129"></a>[FIELD-CIM-PIM-001-C129](#FIELD-CIM-PIM-001-C129) |
| negative_boundary | <a id="FIELD-CIM-PIM-001-E030"></a>[FIELD-CIM-PIM-001-E030](#FIELD-CIM-PIM-001-E030) | 热门芯片 2022 `CXL overview and evolution` | CXL 容量/结构主要属于 [GSF-11](../40_synthesis/third_wave_field_synthesis.md#GSF-11)，除非存在计算端证据 <a id="FIELD-CIM-PIM-001-C130"></a>[FIELD-CIM-PIM-001-C130](#FIELD-CIM-PIM-001-C130) |

## 团队与会议线索

Venue activity 广泛、层次分明。 ISSCC、JSSC、VLSI、A-SSCC 和 CICC 提供电路/芯片和测量的硅或程序/摘要行。 HPCA、MICRO 和 PACT 提供架构、编程和系统/工具行。 DATE、DAC 和 ASP-DAC 显示 EDA/design-automation venues对 LLM/Transformer workload的 PIM/CIM 的采用情况。 FCCM 提供 FPGA 内存块桥。 Hot Chips 为 HBM-PIM、CXL-PNM 和商业内存系统披露 [FIELD-CIM-PIM-001-C001](#FIELD-CIM-PIM-001-C001)[FIELD-CIM-PIM-001-C012](#FIELD-CIM-PIM-001-C012)[FIELD-CIM-PIM-001-C014](#FIELD-CIM-PIM-001-C014) 提供行业演示信号。

团队信号只是有源支持的活动线索。团队矩阵和证据行公开了三星 HBM-PIM/PNM 演示信号、UIUC-IMC benchmark测试、CMU SAFARI SimplePIM 风格的软件框架信号、Princeton/MIT SRAM-CIM 作者字符串、UT Austin/ASU CoMeFa 活动以及多个 2025-2026 LLM-CIM 作者字符串。这些都不被排名或视为团队实力<a id="FIELD-CIM-PIM-001-C015"></a>[FIELD-CIM-PIM-001-C015](#FIELD-CIM-PIM-001-C015)。

## 开放问题

1. 分割边界：模拟/数字 CIM、NVM CIM、SRAM CIM、DRAM/HBM PIM、CXL-PNM 和通用 CXL 内存容量应可能会在后期合成中分离，但目前的cross-venue [GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03) 将它们作为一个强大的场保持在一起，但有局限性 [FIELD-CIM-PIM-001-C003](#FIELD-CIM-PIM-001-C003)<a id="FIELD-CIM-PIM-001-C009"></a>[FIELD-CIM-PIM-001-C009](#FIELD-CIM-PIM-001-C009)。
2. 指标可比性：TOPS/W、uJ/token、GB/s/mm2、系统吞吐量、模型精度和artifact evaluation状态在宏、芯片、模拟器和系统行 [FIELD-CIM-PIM-001-C014](#FIELD-CIM-PIM-001-C014) 之间不可互换。
3. artifact gap：SimplePIM、UIUC-IMC Benchmarking、DRIM-ANN等代码/artifact signal未在本地重现；公开可用性并不证明可运行状态或独立复用[FIELD-CIM-PIM-001-C016](#FIELD-CIM-PIM-001-C016)。
4. LLM 前沿成熟度：许多 2025-2026 行是官方页面、摘要、标题级或部分年份的证据。他们支持一个前沿方向，而不是一个稳定的固定小领域[FIELD-CIM-PIM-001-C013](#FIELD-CIM-PIM-001-C013)。
5. 设备到系统转换：在用作系统级证据 [FIELD-CIM-PIM-001-C008](#FIELD-CIM-PIM-001-C008)[FIELD-CIM-PIM-001-C011](#FIELD-CIM-PIM-001-C011) 之前，必须对照 ADC/DAC、精度损失、耐用性、变化、编译器/runtime映射和主机同步重新检查 RRAM/PCM/模拟 CIM 的优点。

## 连接到用户方向

对于 FPGA 研究，当 BRAM/HBM/PIM 或近存储器布局成为实现基板的一部分时，[GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03) 直接相关。 CoMeFa 是最清晰的 FPGA 内存块桥，而 HBM/PIM 和 NDP 行解释了为什么内存带宽、银行、主机设备移动和模拟器规则需要与计算吞吐量 [FIELD-CIM-PIM-001-E008](#FIELD-CIM-PIM-001-E008)[FIELD-CIM-PIM-001-C014](#FIELD-CIM-PIM-001-C014)<a id="FIELD-CIM-PIM-001-C017"></a>[FIELD-CIM-PIM-001-C017](#FIELD-CIM-PIM-001-C017) 分开报告。

对于 3DGS 和神经渲染，该区域是相邻的而不是中心的。如果高斯排序、图块列表、alpha 混合状态、特征表或神经渲染嵌入受到内存移动限制并映射到 CIM/PIM/NDP 基板上，那么这很重要。该报告并未声称现有的[GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03)行重现3DGS加速[FIELD-CIM-PIM-001-C017](#FIELD-CIM-PIM-001-C017)。

对于机器人和嵌入式边缘计算，[GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03) 通过边缘 LLM、设备上微调、低功耗视觉和内存限制感知workload相关。相关证据不是一般意义上的“CIM 是高效的”，而是workload的数据移动、精度和延迟瓶颈是否与 LoRA-CIM、边缘 LLM PNM、SRAM/RRAM CIM 等行或商业匹配DRAM-PIM应用[FIELD-CIM-PIM-001-E022](#FIELD-CIM-PIM-001-E022)[FIELD-CIM-PIM-001-E027](#FIELD-CIM-PIM-001-E027)[FIELD-CIM-PIM-001-C008](#FIELD-CIM-PIM-001-C008)。

## 缺失来源

- 几个前沿行仍然需要完整的 PDF 级提取，特别是 DAC 2025 AttenPIM/BlockPIM、MICRO 2024 PyPIM、HPCA 2025 UniNDP、HPCA 2026 PIMphony 和 JSSC 2026 凯悦/DPIM [FIELD-CIM-PIM-001-C119](#FIELD-CIM-PIM-001-C119)[FIELD-CIM-PIM-001-C120](#FIELD-CIM-PIM-001-C120)[FIELD-CIM-PIM-001-C123](#FIELD-CIM-PIM-001-C123)[FIELD-CIM-PIM-001-C126](#FIELD-CIM-PIM-001-C126)[FIELD-CIM-PIM-001-C128](#FIELD-CIM-PIM-001-C128)[FIELD-CIM-PIM-001-C129](#FIELD-CIM-PIM-001-C129)。
- UIUC-IMC Benchmarking、SimplePIM、DRIM-ANN 和任何模拟器/工具行 [FIELD-CIM-PIM-001-C016](#FIELD-CIM-PIM-001-C016) 缺少artifact execution。
- 对于HBM-PIM/PNM行业行、商业DRAM-PIM行以及大多数LLM-前沿CIM/PIM论文[FIELD-CIM-PIM-001-C012](#FIELD-CIM-PIM-001-C012)[FIELD-CIM-PIM-001-C013](#FIELD-CIM-PIM-001-C013)，独立采用审核不完整。
- 模拟CIM、数字CIM、DRAM/HBM、PIM、CXL/远存储器、NDP和存储/近数据处理[FIELD-CIM-PIM-001-C003](#FIELD-CIM-PIM-001-C003)[FIELD-CIM-PIM-001-C009](#FIELD-CIM-PIM-001-C009)的边界分割工作仍然开放。
- 作者字符串、实验室、大学和公司团队的实体消歧仍然不完整；不要根据重复的名称或venue数量来推断排名 [FIELD-CIM-PIM-001-C015](#FIELD-CIM-PIM-001-C015)。
