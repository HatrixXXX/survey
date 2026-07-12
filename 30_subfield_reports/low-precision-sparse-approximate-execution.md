# 低精度；稀疏性； LUT/原生算术；近似神经执行

对应 global_subfield_id：[GSF-06](../40_synthesis/third_wave_field_synthesis.md#GSF-06)  
证据规则：本报告只使用 cross-venue inventory、third-wave index、representative matrix、second-wave venue evidence matrix、claim ledger、实体/影响力审计和 workload/artifact inventory。正文中的论文、系统、趋势、团队和 artifact 判断均回到本报告 claim ledger 或 paper evidence matrix；未运行的 artifact 不写为已复现。<a id="FIELD-LOWPREC-SPARSE-001-C009"></a>[FIELD-LOWPREC-SPARSE-001-C009](#FIELD-LOWPREC-SPARSE-001-C009)

## 研究背景

低精度和稀疏之所以形成独立 field，是因为它改变的不是单个算子的常数因子，而是执行模型本身。位宽降低会影响乘法器、累加宽度、buffer 容量、带宽、溢出和质量损失；稀疏会引入索引、负载不均、格式转换和不规则累加；LUT/native arithmetic 则把乘加或非线性函数换成可直接映射到 FPGA LUT 或近似表的结构。<a id="FIELD-LOWPREC-SPARSE-001-E002"></a>[FIELD-LOWPREC-SPARSE-001-E002](#FIELD-LOWPREC-SPARSE-001-E002)<a id="FIELD-LOWPREC-SPARSE-001-E004"></a>[FIELD-LOWPREC-SPARSE-001-E004](#FIELD-LOWPREC-SPARSE-001-E004)<a id="FIELD-LOWPREC-SPARSE-001-E008"></a>[FIELD-LOWPREC-SPARSE-001-E008](#FIELD-LOWPREC-SPARSE-001-E008)

跨会议代表矩阵给 [GSF-06](../40_synthesis/third_wave_field_synthesis.md#GSF-06) 的起点和骨架是 fpgaConvNet、Eyeriss、SCNN、LUTNet 和 KANELÉ：它们分别代表 FPGA dataflow mapping、CNN data-movement/dataflow baseline、compressed-sparse CNN dataflow、LUT-native FPGA inference 和 2026 LUT/KAN frontier。<a id="FIELD-LOWPREC-SPARSE-001-C005"></a>[FIELD-LOWPREC-SPARSE-001-C005](#FIELD-LOWPREC-SPARSE-001-C005)

与 [GSF-01](../40_synthesis/third_wave_field_synthesis.md#GSF-01) 的区别是，本报告只在低精度/稀疏机制成为主问题时吸收 LLM/Transformer 行；KV/cache、serving SLO 和 prefill/decode 本身不在本报告中心。与 [GSF-07](../40_synthesis/third_wave_field_synthesis.md#GSF-07) 的区别是，本报告只把 sparse graph/tensor runtime 当边界：Gunrock 和 HiCOO 能说明 “sparse” 不是一个统一问题，但它们不构成 neural low-precision arithmetic 主线。<a id="FIELD-LOWPREC-SPARSE-001-C006"></a>[FIELD-LOWPREC-SPARSE-001-C006](#FIELD-LOWPREC-SPARSE-001-C006)<a id="FIELD-LOWPREC-SPARSE-001-C031"></a>[FIELD-LOWPREC-SPARSE-001-C031](#FIELD-LOWPREC-SPARSE-001-C031)<a id="FIELD-LOWPREC-SPARSE-001-C032"></a>[FIELD-LOWPREC-SPARSE-001-C032](#FIELD-LOWPREC-SPARSE-001-C032)

## 核心问题

1. 数值格式和质量损失：FINN、UNPU、JSSC mixed-precision AI chip、BETA、LiquidGEMM 和 MXBLAS 说明低精度必须同时回答位宽、累加、反量化、精度损失和硬件利用率。<a id="FIELD-LOWPREC-SPARSE-001-E005"></a>[FIELD-LOWPREC-SPARSE-001-E005](#FIELD-LOWPREC-SPARSE-001-E005)<a id="FIELD-LOWPREC-SPARSE-001-E007"></a>[FIELD-LOWPREC-SPARSE-001-E007](#FIELD-LOWPREC-SPARSE-001-E007)<a id="FIELD-LOWPREC-SPARSE-001-E012"></a>[FIELD-LOWPREC-SPARSE-001-E012](#FIELD-LOWPREC-SPARSE-001-E012)<a id="FIELD-LOWPREC-SPARSE-001-E016"></a>[FIELD-LOWPREC-SPARSE-001-E016](#FIELD-LOWPREC-SPARSE-001-E016)<a id="FIELD-LOWPREC-SPARSE-001-E018"></a>[FIELD-LOWPREC-SPARSE-001-E018](#FIELD-LOWPREC-SPARSE-001-E018)<a id="FIELD-LOWPREC-SPARSE-001-E019"></a>[FIELD-LOWPREC-SPARSE-001-E019](#FIELD-LOWPREC-SPARSE-001-E019)
2. 稀疏不是免费加速：Cnvlutin、EIE、SCNN 和 SNAP 都需要处理跳零、压缩格式、稀疏乘积累加、负载均衡和存储延迟。[FIELD-LOWPREC-SPARSE-001-E002](#FIELD-LOWPREC-SPARSE-001-E002)[FIELD-LOWPREC-SPARSE-001-E004](#FIELD-LOWPREC-SPARSE-001-E004)<a id="FIELD-LOWPREC-SPARSE-001-E006"></a>[FIELD-LOWPREC-SPARSE-001-E006](#FIELD-LOWPREC-SPARSE-001-E006)<a id="FIELD-LOWPREC-SPARSE-001-E010"></a>[FIELD-LOWPREC-SPARSE-001-E010](#FIELD-LOWPREC-SPARSE-001-E010)
3. LUT/native arithmetic 的可编程性边界：LUTNet、LogicNets、PolyLUT、TFLOP 和 KANELÉ 都把计算重写成 LUT-friendly 或 native-LUT 表达，但每条路线的 workload、质量指标和工具状态不同。[FIELD-LOWPREC-SPARSE-001-E008](#FIELD-LOWPREC-SPARSE-001-E008)<a id="FIELD-LOWPREC-SPARSE-001-E009"></a>[FIELD-LOWPREC-SPARSE-001-E009](#FIELD-LOWPREC-SPARSE-001-E009)<a id="FIELD-LOWPREC-SPARSE-001-E013"></a>[FIELD-LOWPREC-SPARSE-001-E013](#FIELD-LOWPREC-SPARSE-001-E013)<a id="FIELD-LOWPREC-SPARSE-001-E020"></a>[FIELD-LOWPREC-SPARSE-001-E020](#FIELD-LOWPREC-SPARSE-001-E020)<a id="FIELD-LOWPREC-SPARSE-001-E021"></a>[FIELD-LOWPREC-SPARSE-001-E021](#FIELD-LOWPREC-SPARSE-001-E021)
4. Transformer/LLM 低精度前沿和旧 CNN 低精度不共享完整评价口径：DEQ、Sparse Transformer Processor、BETA、ISCAS 2025 bit-layered quantization、LiquidGEMM 和 MXBLAS 的关键指标开始偏向 attention、token-level silicon、serving GEMM 和 library integration。<a id="FIELD-LOWPREC-SPARSE-001-E014"></a>[FIELD-LOWPREC-SPARSE-001-E014](#FIELD-LOWPREC-SPARSE-001-E014)<a id="FIELD-LOWPREC-SPARSE-001-E015"></a>[FIELD-LOWPREC-SPARSE-001-E015](#FIELD-LOWPREC-SPARSE-001-E015)[FIELD-LOWPREC-SPARSE-001-E016](#FIELD-LOWPREC-SPARSE-001-E016)<a id="FIELD-LOWPREC-SPARSE-001-E017"></a>[FIELD-LOWPREC-SPARSE-001-E017](#FIELD-LOWPREC-SPARSE-001-E017)[FIELD-LOWPREC-SPARSE-001-E018](#FIELD-LOWPREC-SPARSE-001-E018)[FIELD-LOWPREC-SPARSE-001-E019](#FIELD-LOWPREC-SPARSE-001-E019)
5. 评价指标不能跨 workload 混用：workload inventory 把 LLM serving、sparse graph/irregular kernels、dense tensor/fused kernels、FPGA HLS dataflow 和 robotics edge workloads 分成不同 profiling 家族；TOPS/W、tokens/s、p99 jitter、accuracy drop、energy/token、II/resource 和 sparse format overhead 不能互相替代。<a id="FIELD-LOWPREC-SPARSE-001-C007"></a>[FIELD-LOWPREC-SPARSE-001-C007](#FIELD-LOWPREC-SPARSE-001-C007)

## 发展脉络

第一条路线是 spatial dataflow and early neural accelerator baselines。fpgaConvNet 提供 CNN-to-FPGA mapping 的早期 anchor；Eyeriss 把 CNN acceleration 的能效问题放到 data movement 和 reuse pattern 上，成为很多后续低精度/稀疏设计的评价背景。<a id="FIELD-LOWPREC-SPARSE-001-E001"></a>[FIELD-LOWPREC-SPARSE-001-E001](#FIELD-LOWPREC-SPARSE-001-E001)<a id="FIELD-LOWPREC-SPARSE-001-E003"></a>[FIELD-LOWPREC-SPARSE-001-E003](#FIELD-LOWPREC-SPARSE-001-E003)

第二条路线是 sparse execution。Cnvlutin 说明 activation value 可以直接改变执行路径；EIE 和 SCNN 把 compressed sparse weights、sparse activations 和 compressed-sparse dataflow 做成 accelerator 问题；SNAP 把 unstructured sparse DNN inference 推进到 silicon datapath 和 storage latency 层。[FIELD-LOWPREC-SPARSE-001-E002](#FIELD-LOWPREC-SPARSE-001-E002)[FIELD-LOWPREC-SPARSE-001-E004](#FIELD-LOWPREC-SPARSE-001-E004)[FIELD-LOWPREC-SPARSE-001-E006](#FIELD-LOWPREC-SPARSE-001-E006)[FIELD-LOWPREC-SPARSE-001-E010](#FIELD-LOWPREC-SPARSE-001-E010)

第三条路线是 precision-scalable silicon。UNPU 把 1b 到 16b variable weight precision 当成能效/质量旋钮；JSSC 2022 mixed-precision chip 把 FP8 training、INT4 inference、INT2 和 workload-aware throttling 放到 advanced-node chip 中。这里的主线不是 “低比特一定好”，而是如何让位宽选择和硬件工作点对应起来。[FIELD-LOWPREC-SPARSE-001-E007](#FIELD-LOWPREC-SPARSE-001-E007)[FIELD-LOWPREC-SPARSE-001-E012](#FIELD-LOWPREC-SPARSE-001-E012)

第四条路线是 LUT/native arithmetic。FINN 是 binarized neural network FPGA toolflow 的 formation evidence；LUTNet 把 learned K-input Boolean functions 直接映射到 FPGA soft logic；LogicNets 形成 code/tool signal；PolyLUT 把 LUT inference 扩展到 piecewise-polynomial blocks；KANELÉ 则是 2026 KAN/LUT frontier。[FIELD-LOWPREC-SPARSE-001-E005](#FIELD-LOWPREC-SPARSE-001-E005)[FIELD-LOWPREC-SPARSE-001-E008](#FIELD-LOWPREC-SPARSE-001-E008)[FIELD-LOWPREC-SPARSE-001-E009](#FIELD-LOWPREC-SPARSE-001-E009)[FIELD-LOWPREC-SPARSE-001-E013](#FIELD-LOWPREC-SPARSE-001-E013)[FIELD-LOWPREC-SPARSE-001-E021](#FIELD-LOWPREC-SPARSE-001-E021)

第五条路线是 Transformer/LLM low-bit frontier。DEQ 以 element-wise attention precision 控制为入口；ISSCC 2023 Sparse Transformer Processor 把 sparse Transformer、mixed precision 和 token-level chip metrics 放到 measured silicon；BETA、ISCAS 2025 bit-layered quantization、LiquidGEMM、MXBLAS 和 TFLOP 则把 binary/low-bit execution、W4A8/8-bit GEMM、micro-scaled library 和 LUT/product quantization 推向 edge 或 serving 场景。[FIELD-LOWPREC-SPARSE-001-E014](#FIELD-LOWPREC-SPARSE-001-E014)[FIELD-LOWPREC-SPARSE-001-E015](#FIELD-LOWPREC-SPARSE-001-E015)[FIELD-LOWPREC-SPARSE-001-E016](#FIELD-LOWPREC-SPARSE-001-E016)[FIELD-LOWPREC-SPARSE-001-E017](#FIELD-LOWPREC-SPARSE-001-E017)[FIELD-LOWPREC-SPARSE-001-E018](#FIELD-LOWPREC-SPARSE-001-E018)[FIELD-LOWPREC-SPARSE-001-E019](#FIELD-LOWPREC-SPARSE-001-E019)[FIELD-LOWPREC-SPARSE-001-E020](#FIELD-LOWPREC-SPARSE-001-E020)

边界路线是 sparse graph/tensor and CIM。Spike-CIM 可作为 sparsity-adaptive CIM 的 method bridge，但核心归属更靠近 [GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03)；Gunrock 和 HiCOO 证明 sparse/irregular 有独立图和 tensor storage 路线，本报告只把它们列为 negative_boundary。<a id="FIELD-LOWPREC-SPARSE-001-E011"></a>[FIELD-LOWPREC-SPARSE-001-E011](#FIELD-LOWPREC-SPARSE-001-E011)<a id="FIELD-LOWPREC-SPARSE-001-E022"></a>[FIELD-LOWPREC-SPARSE-001-E022](#FIELD-LOWPREC-SPARSE-001-E022)<a id="FIELD-LOWPREC-SPARSE-001-E023"></a>[FIELD-LOWPREC-SPARSE-001-E023](#FIELD-LOWPREC-SPARSE-001-E023)

## 研究方法

Quantization and precision scaling：包括 binary/ternary、1b-16b variable precision、FP8/INT4/INT2、W4A8、8-bit micro-scaled GEMM、bit-layered non-uniform quantization 和 element-wise attention precision。该方法族必须记录量化点、累加位宽、反量化开销、accuracy/quality loss 和真实硬件利用率。[FIELD-LOWPREC-SPARSE-001-E005](#FIELD-LOWPREC-SPARSE-001-E005)[FIELD-LOWPREC-SPARSE-001-E007](#FIELD-LOWPREC-SPARSE-001-E007)[FIELD-LOWPREC-SPARSE-001-E012](#FIELD-LOWPREC-SPARSE-001-E012)[FIELD-LOWPREC-SPARSE-001-E014](#FIELD-LOWPREC-SPARSE-001-E014)[FIELD-LOWPREC-SPARSE-001-E017](#FIELD-LOWPREC-SPARSE-001-E017)[FIELD-LOWPREC-SPARSE-001-E018](#FIELD-LOWPREC-SPARSE-001-E018)[FIELD-LOWPREC-SPARSE-001-E019](#FIELD-LOWPREC-SPARSE-001-E019)

Sparse execution and compressed dataflow：包括 zero/ineffectual-neuron skipping、compressed sparse weights、sparse activations、unstructured sparse silicon、sparse attention 和 sparse product accumulation。核心风险是索引/格式转换抵消乘法减少，或负载不均让 PE 利用率下降。[FIELD-LOWPREC-SPARSE-001-E002](#FIELD-LOWPREC-SPARSE-001-E002)[FIELD-LOWPREC-SPARSE-001-E004](#FIELD-LOWPREC-SPARSE-001-E004)[FIELD-LOWPREC-SPARSE-001-E006](#FIELD-LOWPREC-SPARSE-001-E006)[FIELD-LOWPREC-SPARSE-001-E010](#FIELD-LOWPREC-SPARSE-001-E010)[FIELD-LOWPREC-SPARSE-001-E015](#FIELD-LOWPREC-SPARSE-001-E015)

LUT/native arithmetic：包括 BNN-to-FPGA compilation、learned Boolean LUTs、co-designed neural circuits、piecewise-polynomial LUT blocks、KAN LUT evaluation 和 LUT/product-quantization LLM decoding。它适合 FPGA 和 reconfigurable fabric，但对模型结构、离线训练/编译、可扩展性和质量曲线有更强依赖。[FIELD-LOWPREC-SPARSE-001-E005](#FIELD-LOWPREC-SPARSE-001-E005)[FIELD-LOWPREC-SPARSE-001-E008](#FIELD-LOWPREC-SPARSE-001-E008)[FIELD-LOWPREC-SPARSE-001-E009](#FIELD-LOWPREC-SPARSE-001-E009)[FIELD-LOWPREC-SPARSE-001-E013](#FIELD-LOWPREC-SPARSE-001-E013)[FIELD-LOWPREC-SPARSE-001-E020](#FIELD-LOWPREC-SPARSE-001-E020)[FIELD-LOWPREC-SPARSE-001-E021](#FIELD-LOWPREC-SPARSE-001-E021)

Library/kernel methods：LiquidGEMM 和 MXBLAS 说明低精度也可以作为 reusable GPU/HPC library kernel，而不是必须走专用 ASIC/FPGA。这里需要独立记录 dequantization overhead、layout conversion、kernel fusion、library integration 和 serving workload context。[FIELD-LOWPREC-SPARSE-001-E018](#FIELD-LOWPREC-SPARSE-001-E018)[FIELD-LOWPREC-SPARSE-001-E019](#FIELD-LOWPREC-SPARSE-001-E019)

Evaluation methods：本报告不把 paper-level TOPS/W、TFLOPS/W、throughput、latency、accuracy、resource use 或 ZCU102 对比写成统一 benchmark。benchmark audit 明确 paper-level metrics 不能直接当 community standardization；所有 public code 都停留在 runnable_unchecked 或 needs_review。[FIELD-LOWPREC-SPARSE-001-C007](#FIELD-LOWPREC-SPARSE-001-C007)[FIELD-LOWPREC-SPARSE-001-C009](#FIELD-LOWPREC-SPARSE-001-C009)

## 代表性论文与系统

| 角色 | 证据 | 代表项目 | 路线 |
|---|---|---|---|
| origin_anchor | [FIELD-LOWPREC-SPARSE-001-E001](#FIELD-LOWPREC-SPARSE-001-E001) | fpgaConvNet，FCCM 2016 | FPGA 神经映射 |
| formation_paper | [FIELD-LOWPREC-SPARSE-001-E002](#FIELD-LOWPREC-SPARSE-001-E002) | 环卢汀，ISCA 2016 | 激活稀疏性/零跳跃 |
| milestone_candidate | [FIELD-LOWPREC-SPARSE-001-E003](#FIELD-LOWPREC-SPARSE-001-E003) | 艾里斯，ISCA 2016 | 数据移动和空间数据流基线 |
| milestone_candidate | [FIELD-LOWPREC-SPARSE-001-E004](#FIELD-LOWPREC-SPARSE-001-E004) | EIE, ISCA 2016 | 压缩 DNN 推理 |
| formation_paper | [FIELD-LOWPREC-SPARSE-001-E005](#FIELD-LOWPREC-SPARSE-001-E005) | FINN, FPGA 2017 | 二值化神经 FPGA 工具流程 |
| milestone_candidate | [FIELD-LOWPREC-SPARSE-001-E006](#FIELD-LOWPREC-SPARSE-001-E006) | SCNN, ISCA 2017 | 压缩稀疏 CNN 加速器 |
| formation_paper | [FIELD-LOWPREC-SPARSE-001-E007](#FIELD-LOWPREC-SPARSE-001-E007) | UNPU, ISSCC 2018 | 可变精度硅 |
| formation_paper | [FIELD-LOWPREC-SPARSE-001-E008](#FIELD-LOWPREC-SPARSE-001-E008) | LUTNet，FCCM 2019 | LUT-原生推理 |
| tool_benchmark | [FIELD-LOWPREC-SPARSE-001-E009](#FIELD-LOWPREC-SPARSE-001-E009) | 逻辑网，FPL 2020 | 神经电路协同设计/编码信号 |
| formation_paper | [FIELD-LOWPREC-SPARSE-001-E010](#FIELD-LOWPREC-SPARSE-001-E010) | SNAP, JSSC 2021 | 非结构化稀疏DNN硅 |
| method_bridge | [FIELD-LOWPREC-SPARSE-001-E011](#FIELD-LOWPREC-SPARSE-001-E011) | 穗-CIM，A-SSCC 2022 | 稀疏自适应 CIM 边界 |
| milestone_candidate | [FIELD-LOWPREC-SPARSE-001-E012](#FIELD-LOWPREC-SPARSE-001-E012) | JSSC 2022混合精度AI芯片 | FP8/INT4/INT2 硅 |
| milestone_candidate | [FIELD-LOWPREC-SPARSE-001-E013](#FIELD-LOWPREC-SPARSE-001-E013) | PolyLUT，FPT 2023 | 多项式 LUT 推理 |
| frontier | [FIELD-LOWPREC-SPARSE-001-E014](#FIELD-LOWPREC-SPARSE-001-E014) | DEQ, ICCD 2023 | 注意力量化 |
| frontier | [FIELD-LOWPREC-SPARSE-001-E015](#FIELD-LOWPREC-SPARSE-001-E015) | 稀疏Transformer处理器，ISSCC 2023 | 稀疏/混合精度令牌硅 |
| formation_paper | [FIELD-LOWPREC-SPARSE-001-E016](#FIELD-LOWPREC-SPARSE-001-E016) | BETA, ISCAS 2024 | 二进制Transformer边缘 FPGA |
| frontier | [FIELD-LOWPREC-SPARSE-001-E017](#FIELD-LOWPREC-SPARSE-001-E017) | ISCAS 2025位分层非均匀量化 | LLM 边缘silicon，源深度有限 |
| frontier | [FIELD-LOWPREC-SPARSE-001-E018](#FIELD-LOWPREC-SPARSE-001-E018) | 液体GEMM，SC 2025 | W4A8 GEMM 服务kernel |
| frontier | [FIELD-LOWPREC-SPARSE-001-E019](#FIELD-LOWPREC-SPARSE-001-E019) | MXBLAS, SC 2025 | 微型 8 位 GEMM 库 |
| frontier | [FIELD-LOWPREC-SPARSE-001-E020](#FIELD-LOWPREC-SPARSE-001-E020) | TFLOP、ASP-DAC 2026 | LUT/FPGA-亲和力 LLM 的乘积量化 |
| frontier | [FIELD-LOWPREC-SPARSE-001-E021](#FIELD-LOWPREC-SPARSE-001-E021) | KANELÉ，FPGA 2026 | LUT-原生KAN前沿 |
| negative_boundary | [FIELD-LOWPREC-SPARSE-001-E022](#FIELD-LOWPREC-SPARSE-001-E022) | HiCOO, SC 2018 | 稀疏tensor存储，非神经算术核心 |
| negative_boundary | [FIELD-LOWPREC-SPARSE-001-E023](#FIELD-LOWPREC-SPARSE-001-E023) | 冈洛克，PPoPP 2016 | 图runtime，而不是低精度神经执行 |

## 团队与会议线索

Venue activity 广泛但不统一。 ISCA 提供早期的稀疏/数据流锚点； FCCM、FPGA、FPL、FPT提供FPGA、LUT本地路由； ISSCC、JSSC、A-SSCC、ISCAS和VLSI提供测量的silicon和电路系统证据； SC 提供最新的低精度 GEMM/库前沿； DAC、ASP-DAC 和 ICCD 提供 Transformer/LLM 量化和近似/低功耗设计挂钩。这是活动图，不是排名。<a id="FIELD-LOWPREC-SPARSE-001-C001"></a>[FIELD-LOWPREC-SPARSE-001-C001](#FIELD-LOWPREC-SPARSE-001-C001)<a id="FIELD-LOWPREC-SPARSE-001-C008"></a>[FIELD-LOWPREC-SPARSE-001-C008](#FIELD-LOWPREC-SPARSE-001-C008)

团队信号只是读取线索。cross-venue团队矩阵记录MIT Eyeriss、NVIDIA/MIT/Stanford/UC Berkeley SCNN、KAIST/Yoo-line、Imperial College LUT/fpgaConvNet/PolyLUT 线，以及Xilinx/FINN 风格的机构字符串作为源支持或部分活动信号，但这些都不会转换为领导力claim。[FIELD-LOWPREC-SPARSE-001-C008](#FIELD-LOWPREC-SPARSE-001-C008)<a id="FIELD-LOWPREC-SPARSE-001-C010"></a>[FIELD-LOWPREC-SPARSE-001-C010](#FIELD-LOWPREC-SPARSE-001-C010)<a id="FIELD-LOWPREC-SPARSE-001-C012"></a>[FIELD-LOWPREC-SPARSE-001-C012](#FIELD-LOWPREC-SPARSE-001-C012)<a id="FIELD-LOWPREC-SPARSE-001-C015"></a>[FIELD-LOWPREC-SPARSE-001-C015](#FIELD-LOWPREC-SPARSE-001-C015)<a id="FIELD-LOWPREC-SPARSE-001-C016"></a>[FIELD-LOWPREC-SPARSE-001-C016](#FIELD-LOWPREC-SPARSE-001-C016)<a id="FIELD-LOWPREC-SPARSE-001-C017"></a>[FIELD-LOWPREC-SPARSE-001-C017](#FIELD-LOWPREC-SPARSE-001-C017)<a id="FIELD-LOWPREC-SPARSE-001-C022"></a>[FIELD-LOWPREC-SPARSE-001-C022](#FIELD-LOWPREC-SPARSE-001-C022)

## 开放问题

第一，精度-质量-硬件三者的坐标系还没有统一。CNN 分类、binary Transformer、LLM serving GEMM、edge silicon、CIM macro 和 sparse tensor storage 的质量指标不同，不能用一个 TOPS/W 或 speedup 直接比较。<a id="FIELD-LOWPREC-SPARSE-001-C002"></a>[FIELD-LOWPREC-SPARSE-001-C002](#FIELD-LOWPREC-SPARSE-001-C002)[FIELD-LOWPREC-SPARSE-001-C007](#FIELD-LOWPREC-SPARSE-001-C007)

第二，稀疏的系统成本仍是主问题。EIE/SCNN/SNAP 这类 neural sparse line 和 Gunrock/HiCOO 这类 graph/tensor line 都说明 sparse 会引入格式、索引、调度和负载均衡开销；但它们的 workload 和评价方法不同。[FIELD-LOWPREC-SPARSE-001-E004](#FIELD-LOWPREC-SPARSE-001-E004)[FIELD-LOWPREC-SPARSE-001-E006](#FIELD-LOWPREC-SPARSE-001-E006)[FIELD-LOWPREC-SPARSE-001-E010](#FIELD-LOWPREC-SPARSE-001-E010)[FIELD-LOWPREC-SPARSE-001-E022](#FIELD-LOWPREC-SPARSE-001-E022)[FIELD-LOWPREC-SPARSE-001-E023](#FIELD-LOWPREC-SPARSE-001-E023)

第三，LUT-native route 的泛化边界需要复核。LUTNet、LogicNets、PolyLUT 和 KANELÉ 很适合 FPGA 方向阅读，但代码存在不等于可复现，也不等于对大模型/视觉/机器人 workload 自动有效。[FIELD-LOWPREC-SPARSE-001-E008](#FIELD-LOWPREC-SPARSE-001-E008)[FIELD-LOWPREC-SPARSE-001-E009](#FIELD-LOWPREC-SPARSE-001-E009)[FIELD-LOWPREC-SPARSE-001-E013](#FIELD-LOWPREC-SPARSE-001-E013)[FIELD-LOWPREC-SPARSE-001-E021](#FIELD-LOWPREC-SPARSE-001-E021)[FIELD-LOWPREC-SPARSE-001-C009](#FIELD-LOWPREC-SPARSE-001-C009)

第四，Transformer/LLM low-bit frontier 很活跃，但近期 evidence 很多还处在 2025-2026 abstract/title/project stage。ISCAS 2025 bit-layered quantization、TFLOP、KANELÉ、LiquidGEMM 和 MXBLAS 都适合写 frontier，不适合直接写成长期影响。[FIELD-LOWPREC-SPARSE-001-E017](#FIELD-LOWPREC-SPARSE-001-E017)[FIELD-LOWPREC-SPARSE-001-E018](#FIELD-LOWPREC-SPARSE-001-E018)[FIELD-LOWPREC-SPARSE-001-E019](#FIELD-LOWPREC-SPARSE-001-E019)[FIELD-LOWPREC-SPARSE-001-E020](#FIELD-LOWPREC-SPARSE-001-E020)[FIELD-LOWPREC-SPARSE-001-E021](#FIELD-LOWPREC-SPARSE-001-E021)

## 连接到用户方向

这条 field 与用户方向直接相关，因为个人输入明确关注量化、反量化、位宽、固定点溢出、混合精度、模型剪枝、低精度、FPGA dataflow、profiling 和端侧资源约束。<a id="FIELD-LOWPREC-SPARSE-001-C033"></a>[FIELD-LOWPREC-SPARSE-001-C033](#FIELD-LOWPREC-SPARSE-001-C033)

对 3DGS/神经渲染来说，可迁移的不是某篇 DNN 低精度论文的指标，而是方法学：先把 cov/rgb/alpha/sort 等 pipeline 的数值范围、误差容忍和访存量 profiling 清楚，再判断 Q16、FP16、LUT approximation、剪枝或 sort-free 近似是否真的能降低瓶颈。[FIELD-LOWPREC-SPARSE-001-C033](#FIELD-LOWPREC-SPARSE-001-C033)[FIELD-LOWPREC-SPARSE-001-C007](#FIELD-LOWPREC-SPARSE-001-C007)

对 FPGA 来说，FINN、LUTNet、LogicNets、PolyLUT 和 KANELÉ 给出一条清楚路线：如果模型或子函数能离线重写成低比特、Boolean/LUT 或 piecewise polynomial block，就可以把 DSP 压力转移到 LUT/BRAM/dataflow 上。但是否值得做取决于资源、频率、pipeline II、buffer backpressure、质量损失和工具链可维护性。[FIELD-LOWPREC-SPARSE-001-E005](#FIELD-LOWPREC-SPARSE-001-E005)[FIELD-LOWPREC-SPARSE-001-E008](#FIELD-LOWPREC-SPARSE-001-E008)[FIELD-LOWPREC-SPARSE-001-E009](#FIELD-LOWPREC-SPARSE-001-E009)[FIELD-LOWPREC-SPARSE-001-E013](#FIELD-LOWPREC-SPARSE-001-E013)[FIELD-LOWPREC-SPARSE-001-E021](#FIELD-LOWPREC-SPARSE-001-E021)

对机器人端侧计算来说，低精度/稀疏的关键不是云端吞吐，而是 batch=1、低 jitter、功耗、控制环路质量和模型智能-端侧部署 trade-off。用户输入中对 VLA/World Model、多模型组件、固定延迟和复杂控制流的关注，说明后续应把 precision/sparsity 与 runtime scheduling 和 workload profiling 结合，而不是单独追求低比特指标。[FIELD-LOWPREC-SPARSE-001-C033](#FIELD-LOWPREC-SPARSE-001-C033)[FIELD-LOWPREC-SPARSE-001-C007](#FIELD-LOWPREC-SPARSE-001-C007)

## 缺失来源

- 需要对 FINN、LUTNet、LogicNets、PolyLUT、DEQ、KANELÉ 等代码做独立 install/build/run audit，当前最多是 runnable_unchecked 或 project/code signal。[FIELD-LOWPREC-SPARSE-001-C009](#FIELD-LOWPREC-SPARSE-001-C009)
- 需要补充 LogicNets、ISCAS 2025 bit-layered quantization、TFLOP、LiquidGEMM 和 MXBLAS 的 PDF-level mechanism extraction 与 artifact/adoption audit。[FIELD-LOWPREC-SPARSE-001-E009](#FIELD-LOWPREC-SPARSE-001-E009)[FIELD-LOWPREC-SPARSE-001-E017](#FIELD-LOWPREC-SPARSE-001-E017)[FIELD-LOWPREC-SPARSE-001-E018](#FIELD-LOWPREC-SPARSE-001-E018)[FIELD-LOWPREC-SPARSE-001-E019](#FIELD-LOWPREC-SPARSE-001-E019)[FIELD-LOWPREC-SPARSE-001-E020](#FIELD-LOWPREC-SPARSE-001-E020)
- 需要将 sparse neural execution 与 graph/tensor sparse infrastructure 做更细的 boundary report，避免把 [GSF-06](../40_synthesis/third_wave_field_synthesis.md#GSF-06) 和 [GSF-07](../40_synthesis/third_wave_field_synthesis.md#GSF-07) 混为一类。[FIELD-LOWPREC-SPARSE-001-C006](#FIELD-LOWPREC-SPARSE-001-C006)[FIELD-LOWPREC-SPARSE-001-E022](#FIELD-LOWPREC-SPARSE-001-E022)[FIELD-LOWPREC-SPARSE-001-E023](#FIELD-LOWPREC-SPARSE-001-E023)
- 需要将低精度方法的 accuracy/quality loss、dequantization overhead、format conversion overhead、memory traffic 和 power/area 统一到 workload-specific profiling schema 中。[FIELD-LOWPREC-SPARSE-001-C007](#FIELD-LOWPREC-SPARSE-001-C007)
- 需要做 team/entity paper-time affiliation audit，特别是 Imperial、MIT/Eyeriss、NVIDIA/MIT/Stanford/UC Berkeley SCNN、KAIST/Yoo-line、Xilinx/FINN-style 和 recent LLM low-bit rows。[FIELD-LOWPREC-SPARSE-001-C008](#FIELD-LOWPREC-SPARSE-001-C008)
