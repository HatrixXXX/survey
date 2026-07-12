# 硬件加速研究地图跨会议总报告

日期：`2026-06-30`  
范围：2016-2026 年 26 个 venue 的二次补充结果

## 1. 这份报告回答什么问题

这份总报告把 26 个会议、期刊和工业发布型 venue 的报告拉到同一张图里看。它不按 FPGA、EDA、IC、体系结构、HPC、ML systems 这些大标签分类，而是按具体研究问题组织：一个工作负载或系统在什么瓶颈上反复出问题，研究者用什么技术路线解决，哪些论文构成阅读入口，哪些团队线索值得继续追踪。

输入来自已经完成的二次补充产物：26 份 venue report、26 份 venue 内 subfield deep dive、26 份 paper evidence matrix、全局 entity disambiguation audit、impact deep audit、workload/artifact inventory 和 cross-venue subfield synthesis。路径和 CSV 可解析性已经在 <a id="FINAL-AUDIT-SECOND-WAVE-001"></a>[FINAL-AUDIT-SECOND-WAVE-001](#FINAL-AUDIT-SECOND-WAVE-001) 中检查，26 个 venue 的必需文件都存在，CSV 解析错误为 0。`second_wave_issue_audit.csv` 仍有 66 条 `still_open`，但每条都有解释，主要是 2026 proceedings、citation context、artifact runnable status、team/entity disambiguation 和 award canonical source 的后续工作入口。<a id="FR-C001"></a>[FR-C001](#FR-C001)

## 2. 证据读法

报告中的结论分三层使用。

第一层是可以当作当前地图骨架使用的结论。比如全局已经归并出 12 个跨会议研究问题族，T11 作为 benchmark、profiling、artifact 与证据有效性基础设施可以标为 `stable`。注意这里的 stable 只表示“评价基础设施”稳定，不表示某个工作负载方向已经稳定。<a id="FR-C002"></a>[FR-C002](#FR-C002)<a id="FR-C008"></a>[FR-C008](#FR-C008)

第二层是可用但必须带条件的趋势。LLM serving、3DGS/neural rendering、PIM/CIM、HLS/AI-for-EDA、chiplet/physical closure 都有跨 venue 信号，但很多证据集中在 2024-2026 年，影响力、artifact 复用和 citation context 还没有完全审计。<a id="FR-C003"></a>[FR-C003](#FR-C003)<a id="FR-C004"></a>[FR-C004](#FR-C004)<a id="FR-C005"></a>[FR-C005](#FR-C005)<a id="FR-C009"></a>[FR-C009](#FR-C009)

第三层只作为 reading lead。团队线索属于这一层。`team_signal_matrix.csv` 有 11 条 `resolved_team_signal`、109 条 `partial_team_signal` 和 12 条带冲突或需要复核的线索。它们可以帮助定位论文集合、项目或公司路线，但不能写成团队排名，也不能用 paper count、citation count 或作者字符串频次推断“谁最强”。<a id="FR-C006"></a>[FR-C006](#FR-C006)

## 3. 会议族在总图中的位置

| 会议族 | venue | 在总图中的主要作用 | 读法 |
|---|---|---|---|
| FPGA / reconfigurable computing | FPGA, FCCM, FPT, FPL | HLS、dataflow、FPGA benchmark、soft logic、视觉/SLAM/3DGS 原型、cloud FPGA 与 SmartNIC | 更适合看“一个工作负载怎样被拆成 pipeline、buffer、tiling、fixed-point 和 floorplan 问题”。 |
| 体系结构 / systems-architecture | ISCA, MICRO, HPCA, ASPLOS, PACT, ISPA | dataflow、PIM/NDP、LLM serving state、accelerator simulation、sparse/irregular、datacenter orchestration | 更适合看“瓶颈是否真实，体系结构机制是否有跨平台意义”。 |
| EDA / design automation | DAC, ICCAD, ASP-DAC, DATE, TCAD | HLS/DSE、placement/routing/timing、AI-for-EDA、RTL/HLS benchmark、physical-aware closure | 更适合看“工具链和实现闭环是否能把想法落到 QoR、PPA 和可复现流程”。 |
| IC / circuit / silicon | ISSCC, JSSC, VLSI, A-SSCC, CICC, ISCAS | CIM/PIM macros、edge AI chip、3D perception silicon、LLM token-level accelerators、analog/digital circuit constraints | 更适合看“电路、存储阵列、频率、面积、功耗和真实硅验证”。 |
| 工业和系统发布 | Hot Chips, MLSys, SC, PPoPP, ICCD | production AI platforms、GPU/TPU/DPU/CXL、distributed training、runtime、benchmark、parallel programming | 更适合看“系统规模、平台约束、真实部署诉求和社区 benchmark”。 |

这些会议族不是主题分类边界。比如 LLM serving 同时出现在 MLSys、HPCA、ASPLOS、FPGA、DAC、ISSCC、VLSI 和 Hot Chips；3DGS/neural rendering 同时出现在体系结构、EDA、FPGA、MLSys 和 IC 线索里。真正的主分类应当是下面的 12 个问题族。[FR-C002](#FR-C002)

## 4. 跨会议主题分类和聚类结果

### [GSF-01](third_wave_field_synthesis.md#GSF-01). LLM serving state、KV/cache、attention 和 token-memory 瓶颈

这是当前证据行最多的跨会议主题，309 条 evidence rows，覆盖 22 个 venue。它的核心问题不是“Transformer kernel 怎么更快”这么窄，而是 prefill/decode、KV cache 驻留、attention 数据搬运、长上下文显存压力、量化和 serving SLO 怎样共同约束系统。[FR-C003](#FR-C003)

聚类上，这一族应拆成至少三条线：KV/cache 和 serving state 管理；attention/tensor kernel 与低精度执行；面向集群或生产 serving 的 runtime、batching、offload 和 SLO 管理。把它们合成一个 topic 会掩盖评价指标差异：kernel 线看 operator throughput 和精度损失，state 线看 tokens/s、prefill/decode latency、显存占用和带宽，serving 线还要看 tail latency 和负载波动。

发展脉络可以按 2021 年前后切开。早期代表线索包括 `Data Movement Is All You Need` 和 SpAtten，它们把 Transformer 优化从算力问题推向数据移动和 sparse attention。2024 以后，AWQ、FlashInfer、CXL-SpecKV 这类行把问题进一步推到 on-device quantization、attention-engine serving、disaggregated KV cache 和 CXL 方向。近期行很多是 `emerging_signal`，不能直接当作长期影响力。[FR-C009](#FR-C009)

团队和平台线索中，Google TPU 是已解析的 source-backed company-team signal；NVIDIA、AMD、Cerebras、Microsoft Maia 等更多出现在 Hot Chips 或 ISSCC 的平台信号里，主要应当作为产品路线和系统约束入口，不应写成团队强弱比较。[FR-C006](#FR-C006)

对个人研究定位来说，这条线能回答“端侧机器人为什么跑不起大模型”和“云端 serving 与 batch=1、低延迟、确定性边缘推理有什么不同”。如果目标是 3DGS/机器人端侧计算，LLM serving 的 KV/state 方法论可借鉴，但不要直接把云端吞吐指标搬到机器人实时控制场景。

### [GSF-02](third_wave_field_synthesis.md#GSF-02). Neural rendering、NeRF、3DGS 与 scene reconstruction pipeline

这一族有 168 条 evidence rows，覆盖 20 个 venue，是最贴近 3DGS 方向的跨会议新前沿。它的瓶颈集中在 sorting、rasterization、Gaussian/ray traversal、cache reuse、training memory、mobile/edge frame latency 和视觉质量折中。[FR-C004](#FR-C004)

聚类上，需要把 neural rendering/3DGS 和 generic SLAM、BEV、robot perception 分开。前者更像显式 primitive 与渲染 pipeline 的计算图问题，后者更像实时感知和控制系统问题。两者都会涉及 tile、binning、sorting、depth、alpha blending、memory bandwidth 和 frame latency，但评价目标不同：3DGS 要同时看画质、FPS、显存和训练/渲染时间；机器人感知还要看 sensor rate、control loop、tail latency 和功耗。

发展脉络上，Navion 和 FSLAM 可作为 SLAM/视觉惯性方向的前置读物；NeuRex 是 neural rendering acceleration 的体系结构入口；MetaSapiens 和 SwiftGS 代表 2025-2026 年的实时 neural rendering 与 fast 3DGS 系统协同优化前沿。当前证据强，但 frontier-heavy，缺直接 graphics/vision venue 的补充审计。[FR-C009](#FR-C009)

团队线索中，Georgia Tech SHARC/Cong Hao 线在 HLS、INR/3DGS 和 hardware/software co-design 上有多条可追踪 project signal；KAIST/Hoi-Jun Yoo 线在 3D perception、SLAM、NeRF/3DGS 和 sensor-front-end silicon 上有 source-backed 或 partial signals；Tsinghua/Yu Wang/Huazhong Yang 等线索主要还是 partial，需要继续做实体边界和 paper-time affiliation 复核。[FR-C006](#FR-C006)

这条线和用户当前背景最直接。一个可迁移的问题范式是：先把 3DGS pipeline 拆成预处理、排序/分桶、投影、raster/blending、depth/visibility、quality metric 与 host-device 数据流；再用 profiling 判断是数据搬运、排序依赖、DSP/BRAM/DDR、pipeline bubble 还是 fixed-point/FP 精度在限制系统。只有瓶颈定位清楚，FPGA、ASIC、GPU kernel、compiler 或 runtime 才有明确取舍。

### [GSF-03](third_wave_field_synthesis.md#GSF-03). CIM/PIM/near-memory execution for memory-wall workloads

这一族有 230 条 evidence rows，覆盖 20 个 venue。它的共同动机是 memory wall，但内部至少混合了 SRAM/RRAM/analog CIM macro、DRAM/HBM PIM、near-storage/NDP、CXL/far memory 和 LLM memory-state 系统。它们共享“少搬数据”的动机，却不共享同一套 artifact、PPA 和评价指标。[FR-C005](#FR-C005)

发展脉络上，2016-2018 年的 SRAM/Conv-RAM 行更多是 device/circuit macro；2019 年后出现 PCM-synapse、CIM benchmarking 等方法论和可比性问题；2021 年 HBM2 function-in-memory 让 PIM 和产品/内存平台路线更近；2024-2026 年许多行转向 Transformer attention、KV/cache、长上下文和 edge fine-tuning。趋势成立，但不能把 analog CIM、DRAM PIM 和 CXL/NDP 直接合并成一个稳定 topic。[FR-C005](#FR-C005)

团队线索中，KAIST/Yoo-line、Samsung PIM/CXL 相关 partial signals、ASU/Columbia/Samsung 等 memory-computing 线索可作为阅读入口。由于 IC/circuit 和 system PIM 的证据层级差异很大，团队线索只能按具体论文和项目读，不能跨层级排序。[FR-C006](#FR-C006)

这条线对“存储墙、功耗墙具体体现在哪里”最有帮助。它提示：如果一个工作负载的主瓶颈是 off-chip traffic 或容量驻留，优化不一定从算子本身开始，而可能从数据布局、预取、压缩、near-data placement、CXL/HBM 层次和片上 buffer 组织开始。

### [GSF-04](third_wave_field_synthesis.md#GSF-04). HLS、compiler、autotuning 与 hardware-generation closure

这一族有 186 条 evidence rows，覆盖 20 个 venue。它已经不只是经典 HLS DSE。二次补充后，证据中同时出现 HLS benchmark、DSL、tensor compiler/codegen、trace-based simulation、LLM-assisted RTL/HLS/code/assertion generation、QoR prediction 和 agentic optimization。[FR-C005](#FR-C005)

聚类上，至少应拆成三条：FPGA/HLS/DSE 与 implementation predictability；tensor/compiler codegen 与 kernel/runtime 生成；LLM-assisted hardware design/verification benchmark。Spector、Rosetta、HeteroCL、AutoBridge、LightningSim 构成 FPGA/HLS closure 的阅读路线；DREAMPlace、CircuitNet、VerilogEval、RTLLM、BENCH4HLS 构成 AI-for-EDA 和 LLM hardware design benchmark 的阅读路线。[FR-C009](#FR-C009)

团队线索中，Georgia Tech SHARC/Cong Hao 是 resolved signal，NVIDIA VerilogEval 是 resolved company-team/repo signal，EPFL/De Micheli、EPFL Stojilovic/AMD、HKUST/Zhiyao Xie、Tsinghua/Shaojun Wei/Yu Wang/Huazhong Yang 等可作为 partial 或 resolved 线索。使用时要保留 caveat：artifact 多数还是 `runnable_unchecked`，LLM-assisted design 还存在 benchmark contamination、QoR 可比性和真实工具链采用的问题。[FR-C006](#FR-C006)<a id="FR-C007"></a>[FR-C007](#FR-C007)

对 FPGA/3DGS 工程路线，这一族给出的核心判断是：如果要把固定算法翻译成 RTL，单纯“让 AI 写代码”不是完整问题。真正需要闭环的是 workload profiling、IR/DSL 表达、schedule search、buffer sizing、timing/floorplan、simulation、golden model/testbench、QoR prediction 和 artifact 记录。

### [GSF-05](third_wave_field_synthesis.md#GSF-05). Physical/PPA、routing、timing、chiplet、3DIC 与 package closure

这一族有 81 条 evidence rows，覆盖 11 个 venue。它的核心问题不是某个 workload，而是 accelerator idea 怎样落到 timing、routing、thermal、HBM、die-to-die、UCIe、3DIC、package bandwidth 和真实 PPA 约束上。[FR-C005](#FR-C005)

发展脉络上，早期很多工作把 architecture 和 algorithm mapping 停在 simulator 或 pre-layout 层；二次补充看到 EDA、Hot Chips、VLSI、FCCM/FPL 等 venue 中 implementation closure 约束反复出现。这个方向提醒我们：论文里的 speedup 如果没有 post-synthesis、post-layout、frequency、resource utilization、timing slack 或真实 silicon/PPA 证据，不能直接等同于可落地系统。

团队线索中，NVIDIA EDA plus Georgia Tech C3PO collaboration、EPFL Stojilovic FPGA routing line with AMD collaborators 等是 source-backed signal。它们适合作为读 physical-aware accelerator design 的入口，而不是团队排名。[FR-C006](#FR-C006)

这条线对“FPGA 往自研芯片怎么走”很关键。FPGA 原型证明 pipeline 和数据流可行，不等于 ASIC 可闭合。下一步需要把频率、片上 SRAM/BRAM、DSP/乘加树、AXI/DDR/HBM 带宽、floorplan、clock domain、timing closure 和验证成本都放进同一张约束表。

### [GSF-06](third_wave_field_synthesis.md#GSF-06). 低精度、稀疏、LUT/native arithmetic 与近似神经执行

这一族有 160 条 evidence rows，覆盖 16 个 venue。它看似是“量化和稀疏”，实际上包含低 bitwidth、mixed precision、block floating point、LUT/polynomial/native FPGA arithmetic、zero skipping、structured/unstructured sparsity 和 approximate execution。

发展脉络上，fpgaConvNet、Eyeriss、SCNN、LUTNet 是从 CNN/dataflow、sparse CNN 到 FPGA soft logic/native arithmetic 的基础路线；KANELE 等 2026 行体现 LUT/KAN 这类新模型形式对 FPGA/逻辑资源的吸引力，但还只能作为 frontier signal。[FR-C009](#FR-C009)

评价上不能跨工作负载混用指标。LLM quantization 关注 perplexity、accuracy、tokens/s、显存和 serving latency；3DGS 低精度要看 PSNR/SSIM/LPIPS、FPS、画质退化和存储；CIM/analog 还要看噪声、阵列误差和 PPA。把所有“低精度”放到一个 stable topic 会掩盖误差模型差异。

对当前 3DGS/FPGA 研究，这一族提示：fixed-point、FP16、混合精度和 LUT 化不是孤立优化，而是要和 pipeline stage、DSP 使用、BRAM/DDR 带宽、累加位宽、溢出、画质指标一起验证。

### [GSF-07](third_wave_field_synthesis.md#GSF-07). Irregular graph、sparse tensor、point-cloud 与 data-dependent workload mapping

这一族有 112 条 evidence rows，覆盖 12 个 venue。它处理的是 load imbalance、metadata movement、random access、sparse format、dynamic work partitioning 和 data-dependent control。它与 [GSF-06](third_wave_field_synthesis.md#GSF-06) 有交叉，但不是同一个问题。

代表路线包括 Gunrock、FCCM graph processing、HiCOO、RTNN 和 ZeD。这里最容易犯的错误是把 classical graph/HPC irregular、GNN/recommendation、sparse tensor、point-cloud 和 MoE routing 混成一个“稀疏加速”标签。它们的数据结构、可重排空间、locality、同步方式和评价 benchmark 都不同。[FR-C009](#FR-C009)

这条线对 3DGS 也有间接意义。Gaussian sorting、tile binning、visibility、depth ordering 和动态 early-exit 都可能把规则渲染 pipeline 变成不规则数据流问题。是否要硬件化，取决于不规则性是否能被转化成稳定的分块、近似、局部排序或 streaming schedule。

### [GSF-08](third_wave_field_synthesis.md#GSF-08). Benchmark、profiling、simulator、artifact 与证据有效性基础设施

这一族有 111 条 evidence rows，覆盖 19 个 venue，是唯一建议标为 `stable` 的 topic，但它稳定的是“评价基础设施”，不是某个加速工作负载。[FR-C008](#FR-C008)

代表路线包括 FireSim、Accel-Sim、NeuroSim、Sparseloop 和 MLCommons Chakra。它们分别回答不同层级的可比性问题：cycle-exact simulation、GPU modeling、CIM/circuit modeling、sparse tensor analytical modeling、ML execution trace/benchmarking。当前项目也把 workload inventory、profiling field inventory 和 benchmark/artifact inventory 放在这一层，而不是直接把 artifact URL 当作复现实验证据。[FR-C007](#FR-C007)

这条线和用户的“先有足够多的 how，才有 why/what”的判断一致。好的硬件加速问题不是先说“我要做 FPGA/ASIC”，而是先建立 profiling 字段：数据量、运算量、bandwidth、arithmetic intensity、latency breakdown、utilization、PPA、quality drop、artifact status。没有这层，后面的 topic 判断会漂。

### [GSF-09](third_wave_field_synthesis.md#GSF-09). Edge robotics、sensor-near vision、SLAM 与 embodied low-latency perception

这一族有 172 条 evidence rows，覆盖 17 个 venue。它和 [GSF-02](third_wave_field_synthesis.md#GSF-02) 相邻，但重点是低功耗、低延迟、sensor rate、SLAM/depth/event/vision front-end、control loop 和端侧部署约束。

发展脉络上，早期线索包括视觉惯性、SLAM 和 sensor-front-end accelerator；近年出现 NeRF/3DGS、BEV、robotics edge silicon、TinyML runtime 和 embodied perception 的交叉信号。VLA/world model 硬件证据还不充分，目前更多是 workload inventory 或 frontier signal，不能写成已成型的硬件 topic。[FR-C004](#FR-C004)

团队线索中，KAIST/Yoo-line、Tsinghua/Yu Wang/Huazhong Yang line、部分 Google/vision hardware 和 Hot Chips 视觉/robotics 线索值得读，但很多只是 partial signal。对端侧机器人的研究，真正的核心约束是 batch=1、tail latency、功耗、memory residency、控制流复杂性和多模型协同，而不是云端 GPU serving 的平均吞吐。

### [GSF-10](third_wave_field_synthesis.md#GSF-10). Distributed training、accelerator orchestration、collectives 与 datacenter fabric

这一族有 109 条 evidence rows，覆盖 7 个 venue，集中在 systems、Hot Chips、MLSys、SC、ASPLOS、PPoPP 和 ISCA。它的瓶颈是 collectives、topology、offload、GPU sharing、MoE routing、cluster memory pressure 和 datacenter fabric。

代表路线可以从 production AI platforms 读起：In-Datacenter TPU Analysis、NVIDIA A100、TPU v4、Blackwell Platform、Maia。这里的 evidence 很多来自工业平台或 vendor disclosure，因此适合读约束和设计取舍，不适合直接当作独立 benchmark 结论。[FR-C009](#FR-C009)

团队线索中，Google TPU 是 resolved signal；NVIDIA、AMD、Intel、Cerebras、Microsoft 等多是 company/platform partial signals。写作时应区分 product release、official docs、conference talk 和 peer-reviewed system paper。

### [GSF-11](third_wave_field_synthesis.md#GSF-11). Memory capacity、CXL/far-memory、storage、I/O 与 NoC/data movement

这一族有 144 条 evidence rows，覆盖 14 个 venue。它和 [GSF-03](third_wave_field_synthesis.md#GSF-03)、[GSF-10](third_wave_field_synthesis.md#GSF-10)、[GSF-01](third_wave_field_synthesis.md#GSF-01) 都相交，但问题边界更偏系统数据移动：capacity、bandwidth、cache/coherence、host-device transfer、storage、DMA、NoC、CXL/tiered memory、HBM/package bandwidth。

发展脉络上，早期可以从 memory hierarchy、NoC、DMA、FPGA/HBM 和 storage/I/O 优化读起；近年 CXL memory expander、far memory、disaggregated KV cache 和 datacenter fabric 让这条线和 LLM serving 直接相连。后续需要拆成 CXL/far memory、storage/I/O、HBM/package 和 LLM state-memory 四个更窄问题。

对 3DGS/FPGA 实现，这条线最实际的启发是：很多性能问题看似是 arithmetic，不一定真是 compute bottleneck。AXI/DDR burst、host-device copy、frame buffer、tile buffer、sort/depth 中间结果、Gaussian 参数驻留都可能决定上限。

### [GSF-12](third_wave_field_synthesis.md#GSF-12). Security、correctness、reliability 与 verification constraints

这一族有 83 条 evidence rows，覆盖 18 个 venue。它不是一条单一性能 lineage，更像所有加速系统都会遇到的约束层：side-channel、fault tolerance、formal correctness、RowHammer、verification、trust、dependable execution。

当前证据强度是 moderate。很多行属于 boundary evidence 或 negative boundary，说明“这个风险存在”，但不足以构成统一的 accelerator-performance topic。后续如果要深挖，需要引入专门 security/verification venue，而不能只靠硬件加速主会的零散行。

对工程写作，这条线提醒：如果一个加速器要进入真实系统，correctness、testbench、scoreboard、formal/property check、容错和异常控制流不是附录问题。它们会影响可发表性和可转化性。

## 5. 总体发展脉络

### 2016-2018：CNN/dataflow、FPGA/HLS 和基础评价工具成形

这一阶段的代表信号包括 fpgaConvNet、Eyeriss、SCNN、Rosetta、FireSim，以及早期 SRAM/CIM 和 TPU datacenter analysis。主问题是怎样把 CNN、graph、HLS benchmark 和 dataflow accelerator 从“可做”推进到“可比较”。方法上，tile、data reuse、systolic/dataflow、fixed point、benchmark suite 和 simulator 是核心工具。

### 2019-2021：稀疏、低精度、PIM/NDP 和 implementation closure 扩展

这一阶段出现 LUTNet、HeteroCL、AutoBridge、Accel-Sim、HBM2 function-in-memory、persistent memory benchmark 等信号。研究重心从单个 accelerator idea 扩展到工具链、artifact、post-synthesis/post-layout、memory hierarchy 和 benchmark fairness。它也是“只报 speedup 不够”的转折期。

### 2022-2024：LLM serving、AI-for-EDA、CXL/PIM 和 3D/neural rendering 进入硬件地图

这一阶段 Transformer/LLM 把 attention、KV/cache、long-context memory、quantization 和 serving SLO 推到中心；VerilogEval、RTLLM、CircuitNet 等让 LLM-assisted hardware design 形成可评价对象；CXL、PIM、HBM、chiplet 和 package 约束更频繁地进入系统讨论；NeRF/neural rendering 与 SLAM/3D perception 开始跨出图形和视觉语境。

### 2025-2026：前沿信号增多，但长期影响力还不能下结论

SwiftGS、CXL-SpecKV、BENCH4HLS、Blackwell、Maia、更多 3DGS/robotics/edge AI silicon 和 LLM hardware-generation benchmark 让地图明显向 AI workload frontier 移动。但 final audit 已经指出，2024-2026 行大量属于 `emerging_signal`，很多缺 final proceedings、citation context、artifact runnable status 或 adoption evidence。总报告可以把它们写成前沿入口，不能写成已验证影响力。<a id="FR-C010"></a>[FR-C010](#FR-C010)

## 6. 作者和团队线索

下面只列 source-backed 或高价值 partial reading leads，不做排名。

| 线索 | 状态 | 主要关联方向 | 使用方式 |
|---|---|---|---|
| KAIST/Yoo-line author signal | resolved | edge AI silicon、3D perception/SLAM/NeRF/3DGS、Transformer token-processing、AI/HPC processor silicon | 可作为 IC/silicon 与 embodied edge 阅读入口。 |
| Google TPU team signal | resolved | production tensor accelerators、datacenter ML systems | 可作为 production accelerator 系统路线入口。 |
| Georgia Tech SHARC/Cong Hao line | resolved | HLS feedback、numeric libraries、implementation predictability；另有 INR/3DGS partial signals | 可作为 FPGA/HLS/3DGS co-design 阅读入口。 |
| Microsoft Catapult signal | resolved | cloud FPGA platforms、OpenCL tooling | 可作为 datacenter FPGA 早期路线入口。 |
| EPFL LAP/Ienne line | resolved | HBM、PIM、storage、network datapaths | 可作为 memory/datapath 方向入口。 |
| EPFL/De Micheli logic-synthesis signal | resolved | hardware security、validation、logic synthesis | 可作为 EDA/security/verification 入口。 |
| EPFL Stojilovic with AMD collaborators | resolved | FPGA CAD routing、placement、implementation closure | 可作为 FPGA physical-aware closure 入口。 |
| MIT Eyeriss with MIT/NVIDIA author signal | resolved | sparse and spatial DNN accelerator dataflows | 可作为 dataflow accelerator 基础入口。 |
| NVIDIA/MIT/Stanford/UC Berkeley SCNN collaboration | resolved | compressed-sparse CNN accelerator | 可作为 sparse spatial accelerator 入口。 |
| NVIDIA EDA plus Georgia Tech C3PO collaboration | resolved | placement、routability、timing、3D PDN constraints | 可作为 AI-for-EDA/physical closure 入口。 |
| NVIDIA VerilogEval benchmark/repo signal | resolved | LLM Verilog code generation benchmark | 可作为 LLM-assisted hardware design benchmark 入口。 |

其他 partial signals，包括 Samsung PIM/CXL、NVIDIA/AMD/Intel/Cerebras Hot Chips 平台线索、HKUST/Zhiyao Xie、Tsinghua/Shaojun Wei/Yu Wang/Huazhong Yang、Georgia Tech EIC、CUHK Bei Yu 等，适合放进后续专题阅读清单。它们还不适合写成长期团队地位判断。[FR-C006](#FR-C006)

## 7. 对个人研究方向的定位

从当前地图看，用户的 3DGS、FPGA、端侧视觉/机器人和软硬件协同方向位于三条线的交叉处。<a id="FR-C011"></a>[FR-C011](#FR-C011)

第一条是 [GSF-02](third_wave_field_synthesis.md#GSF-02) 的 neural rendering/3DGS pipeline。这里的学术故事最直接：3DGS 的实际瓶颈来自 sorting、rasterization、Gaussian 参数读取、alpha blending、depth/visibility、tile/binning、frame-to-frame reuse 和画质指标。硬件加速的关键不是先选 FPGA 还是 GPU，而是先证明瓶颈在数据流、访存、排序依赖、精度还是 pipeline utilization。

第二条是 [GSF-08](third_wave_field_synthesis.md#GSF-08) 的 profiling/benchmark 证据层。用户当前最需要沉淀的是可复用 profiling 框架：每个 stage 的 latency、throughput、bandwidth、DSP/BRAM/DDR、frame latency、PSNR/SSIM/LPIPS、功耗和 artifact status。它能把“工程工作量”转成论文里的 problem analysis。

第三条是 [GSF-04](third_wave_field_synthesis.md#GSF-04)、[GSF-05](third_wave_field_synthesis.md#GSF-05)、[GSF-06](third_wave_field_synthesis.md#GSF-06)、[GSF-11](third_wave_field_synthesis.md#GSF-11) 组成的实现闭环：HLS/RTL/codegen、timing/floorplan/PPA、fixed-point/FP16/混合精度、host-device/AXI/DDR/HBM 数据流。如果要从 FPGA 原型走向更高层次的体系结构或芯片论文，这些约束必须一起出现。

一个可操作的选题模板是：先跑通完整 3DGS pipeline，再用 profiling 证明通用平台或当前 FPGA 原型的瓶颈；然后提出一个围绕数据流或可实现性约束的具体机制，例如 sort-free/tile-local ordering、frame-to-frame depth/sort reuse、Gaussian 参数驻留、burst-friendly layout、multi-clock pipeline、precision-aware raster/blending、或 host-device dataflow reorganization；最后用 end-to-end latency、FPS、质量指标、资源/PPA、功耗或带宽模型证明它不是孤立优化。

投会议时可以按证据深度选择入口：只有 FPGA/HLS/RTL 与资源指标，优先看 FPGA/FCCM/FPL/FPT；如果有体系结构洞察、瓶颈模型和跨平台意义，去看 ISCA/MICRO/HPCA/ASPLOS/PACT；如果有工具链、代码生成、QoR 或 benchmark，去看 DAC/ICCAD/ASP-DAC/DATE/TCAD；如果有 silicon/PPA 或真实电路实现，去看 ISSCC/VLSI/JSSC/CICC/A-SSCC；如果做到系统、runtime、benchmark 或 ML workload 级别，去看 MLSys/SC/PPoPP/ASPLOS。

## 8. 建议阅读路线

1. 先读方法论和评价：FireSim、Accel-Sim、Rosetta、Sparseloop、NeuroSim、MLCommons Chakra。目标是学会怎样证明一个加速问题真实存在，而不是只看 speedup。
2. 再读 dataflow 和低精度基础：Eyeriss、SCNN、fpgaConvNet、LUTNet、HeteroCL、AutoBridge。目标是建立 pipeline、data reuse、sparse/low-precision、HLS closure 的基本词汇。
3. 再读 3D/视觉线：Navion、FSLAM、NeuRex、MetaSapiens、SwiftGS，并补 graphics/vision venue。目标是把 SLAM、NeRF、3DGS 和 sensor-near perception 的边界分清。
4. 同时读 LLM serving 和 memory 线：Data Movement Is All You Need、SpAtten、AWQ、FlashInfer、HBM/PIM、CXL/KV 相关行。目标是借鉴 state/cache/memory 视角，而不是照搬云端 serving 指标。
5. 最后按投稿目标补实现闭环：VerilogEval、RTLLM、BENCH4HLS、DREAMPlace、CircuitNet、LightningSim、physical-aware placement/routing 和 timing closure。

## 9. 后续任务

最值得继续做的不是再泛泛扩大会议，而是开更窄的专题。

第一，3DGS/neural rendering 专题。补 graphics/vision venue，建立 3DGS pipeline 的 workload/profiling 字段，拆清 sorting、raster/blending、depth/visibility、memory layout、precision 和画质指标。

第二，LLM serving state/KV 专题。把 KV cache、attention engine、prefill/decode、CXL/far memory、quantization 和 batch/tail latency 拆开，避免和普通 Transformer kernel 混在一起。

第三，artifact/citation graph 专题。对 `impact_deep_audit.csv` 中 P0/P1 且 `citation_context_status=needs_review` 的行抽 top citing papers，区分 method reuse、baseline comparison、system extension 和 background-only。[FR-C010](#FR-C010)

第四，团队实体专题。继续处理 `ambiguous`、`split_required` 和高优先级 `string_only` 作者，尤其是 3DGS、FPGA/HLS、AI-for-EDA、PIM/CIM 和 production accelerator 平台相关线索。[FR-C006](#FR-C006)

第五，2026 refresh。等 final proceedings、award、DOI、artifact pages 稳定后刷新 2026 行，避免把正常 partial 当作确定事实。[FR-C010](#FR-C010)<a id="FR-C012"></a>[FR-C012](#FR-C012)

## 10. Missing Sources

- 2026 年多个 venue 的 final proceedings、award、DOI、artifact page 和 PDF。
- 3DGS/neural rendering 的 graphics/vision venue 证据。
- 高优先级论文的 citation-context 语境审计。
- artifact URL 的 license、tag/commit、dependency、hardware requirement 和 runnable status。
- team/entity 的 ORCID、DBLP、主页、实验室页面和 paper-time affiliation 复核。
- same-chip lineage，尤其是 ISSCC、JSSC、VLSI、CICC、A-SSCC、Hot Chips 之间的同一芯片或 journal extension 映射。

## 11. AI Assistance Disclosure

本报告由 AI 辅助生成，但结论限定在本地项目证据文件内。新增综合判断已写入配套 claim ledger；未完成来源复核的内容在正文中保留 caveat。
