# ISSCC 小领域深读

## 1. 范围与语料

本次 第二轮 只处理 ISSCC。`papers.csv` 有 2441 行，`awards.csv` 有 23 行；`ISSCC_screening_matrix.csv` 覆盖 2464 行，筛选决定分布为 `{'index_only': 2362, 'deep_read': 83, 'exclude_non_main': 8, 'needs_review': 11}`。`ISSCC_paper_evidence_matrix.csv` 写入 72 条 evidence rows，包含 WHY/HOW/WHAT/IMPACT/EVIDENCE。

2026 仍按 `normal_2026_partial` 处理。引用、采用和 artifact 信号只作为初审线索；有 citation/adoption 数值时写入检索日期 `2026-06-27`，没有证据时保持 `impact_unverified` 或 `needs_review`。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="ISSCC-SF01"></a>[ISSCC-SF01](#ISSCC-SF01) | CNN/RNN 和低功耗 Edge-AI 加速器硅 | DNN/edge-AI 如何在低功耗芯片中实现数据复用、低电压、精度调节和实测能效 | CNN、RNN、始终在线视觉、微型机器人 AI、SNN | 数据移动、精度、电压、利用率 | 数据流、精确缩放、可重新配置数据路径，神经形态/事件计算 | 2016-2024 | venue_provisional； 6 行 |
| <a id="ISSCC-SF02"></a>[ISSCC-SF02](#ISSCC-SF02) | CIM/PIM 和近内存 MAC | 存储墙如何变成 SRAM/ReRAM/MRAM/DRAM/HBM 阵列、读出、精度和带宽问题 | CNN/DNN 边缘推断、HBM-PIM、内存限制 ML | 带宽、读出、保留、精度 | SRAM/ReRAM/MRAM/DRAM CIM/PIM、数字/模拟 MAC、bank 级并行 | 2018-2026 | venue_split_candidate； 17 行 |
| <a id="ISSCC-SF03"></a>[ISSCC-SF03](#ISSCC-SF03) | Transformer/LLM 令牌处理加速器 | attention、token latency、KV/cache 和低比特 LLM 推理如何落到芯片 | BERT、Transformer、Llama、推测解码、视觉自回归生成 | 令牌内存流量、稀疏性、精度、片上容量 | 稀疏注意力、CIM 令牌管道、量化、近似/乱序计算、推测解码 | 2022-2026 | cross_venue_candidate； 16 行 |
| <a id="ISSCC-SF04"></a>[ISSCC-SF04](#ISSCC-SF04) | 3D 感知、SLAM、NeRF/3DGS 和传感 | 3D sensing、SLAM、NeRF/3DGS 和空间计算如何形成实时低功耗硅流水线 | 立体深度、CNN-SLAM、NeuroSLAM、LiDAR-SLAM、NeRF、3DGS、超声波/SPAD | 帧能量、内存流量、点云/kNN 延迟、传感器前端带宽 | SLAM 加速器、点神经分割、稀疏 MoE NeRF-SLAM、分段哈希、高斯缓存调度 | 2016-2026 | cross_venue_candidate; 11 行 |
| <a id="ISSCC-SF05"></a>[ISSCC-SF05](#ISSCC-SF05) | 产品规模 AI/HPC 平台硅 | 真实 GPU/CPU/chiplet/AI SoC 如何处理 HBM、die-to-die、cache、package 和企业/datacenter workload | 数据中心 GPU、企业 CPU/AI 加速器、百亿亿次处理器、标线/小芯片 AI SoC | HBM 带宽、封装功耗、芯片间链接、存储器层次结构 | Tensor Core/GPU 平台、Telum AI 加速器、Foveros/EMIB、chiplet 封装、UCIe 网格 | 2017-2026 | venue_provisional； 12 行 |
| <a id="ISSCC-SF06"></a>[ISSCC-SF06](#ISSCC-SF06) | 奖励边界电路行 | 保留官方 award 证据但不把非主线电路奖项写成 accelerator trend | 功率、ADC、视频、触摸感应、基因组学、PLL/参考 | 特定领域电路约束 | 奖励来源核实和边界分类 | 2016-2021 | boundary_only； 10 行 |

## 3. 小领域深读

### [ISSCC-SF01](#ISSCC-SF01)。 CNN/RNN 和低功耗 Edge-AI 加速器芯片

- 研究问题： 把 CNN/RNN/edge-AI 负载转成可测的 dataflow、片上存储、低电压、精度和能效指标。
- 背景： ISSCC 的价值在于已流片、可测量的 DNN/edge-AI 处理器，而不是算法首发。
- Current state: 2016-2018 有 Eyeriss、Envision、DNPU、UNPU 等早期线索；2023-2024 又有 neuromorphic/online-learning 边界路线。
- 方法谱系：行固定/数据重用 -> 电压/精度缩放 -> CNN/RNN 可重构性 -> 可变精度 -> 尖峰/在线学习。
- 代表论文：[ISSCC-2016-P0017](../../10_corpus/ISSCC/id_index.md#ISSCC-2016-P0017)； [ISSCC-2016-P0080](../../10_corpus/ISSCC/id_index.md#ISSCC-2016-P0080); [ISSCC-2017-P0137](../../10_corpus/ISSCC/id_index.md#ISSCC-2017-P0137)； [ISSCC-2017-P0172](../../10_corpus/ISSCC/id_index.md#ISSCC-2017-P0172); [ISSCC-2018-P0104](../../10_corpus/ISSCC/id_index.md#ISSCC-2018-P0104)； [ISSCC-2023-P0203](../../10_corpus/ISSCC/id_index.md#ISSCC-2023-P0203)。
- 团队线索： MIT Eyeriss、KAIST edge-AI、KU Leuven/imec、MediaTek/NVE 等仅作为字符串线索，不排名。
- workload/artifact 信号： AlexNet/VGG-16、always-on vision、micro-robot AI、online learning；只有 Eyeriss project/demo 有较强 project signal。
- 开放问题： 需要 PDF 和 citation graph 区分同队扩展、综述引用和跨团队复用。

### [ISSCC-SF02](#ISSCC-SF02)。 CIM/PIM 和近内存 MAC

- 研究问题： 降低数据搬运成本，把 MAC/dot-product/bank-level compute 放进或靠近存储阵列，同时处理精度、读出、retention 和接口成本。
- 背景： 这个小领域应拆成 SRAM-CIM、ReRAM-nvCIM、MRAM/NMC、DRAM/HBM-PIM、analog-vs-digital CIM，而不是只叫“大存内计算”。
- Current state: 2018-2022 有密集 CIM macro 序列；2021 HBM2 FIM/PIM 是系统/产品相邻路线；2026 又出现 3D DRAM-logic PNM 和 ReRAM-on-logic LLM row。
- 方法谱系：SRAM 二进制 -> ReRAM 二进制/多位 -> 6T SRAM 8b/推理训练 -> 全数字全精度 -> MRAM 加密 NMC -> HBM/DRAM PIM 和 3D PNM。
- 代表论文：[ISSCC-2018-P0019](../../10_corpus/ISSCC/id_index.md#ISSCC-2018-P0019)； [ISSCC-2018-P0026](../../10_corpus/ISSCC/id_index.md#ISSCC-2018-P0026)； [ISSCC-2018-P0088](../../10_corpus/ISSCC/id_index.md#ISSCC-2018-P0088); [ISSCC-2019-P0183](../../10_corpus/ISSCC/id_index.md#ISSCC-2019-P0183); [ISSCC-2020-P0002](../../10_corpus/ISSCC/id_index.md#ISSCC-2020-P0002); [ISSCC-2020-P0164](../../10_corpus/ISSCC/id_index.md#ISSCC-2020-P0164); [ISSCC-2020-P0171](../../10_corpus/ISSCC/id_index.md#ISSCC-2020-P0171); [ISSCC-2020-P0196](../../10_corpus/ISSCC/id_index.md#ISSCC-2020-P0196); [ISSCC-2021-P0016](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0016); [ISSCC-2021-P0020](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0020); [ISSCC-2021-P0089](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0089)； [ISSCC-2021-P0193](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0193)；...。
- 团队线索： NTHU/TSMC/Meng-Fan Chang、MIT Chandrakasan、Northwestern Jie Gu、Samsung/Nam Sung Kim、TSMC SRAM-CIM 等为 string-level signal。
- workload/artifact 信号： CNN/BNN/tiny-AI edge、GEMV、speech recognition、LSTM、Transformer simulation；Samsung HBM-PIM 有官方产业/平台线索，大多数 macro 没有公开 artifact/code。
- 开放问题： 需要 cross-venue 对照 MICRO/HPCA/ISCA 的 PIM/CIM 系统论文和 JSSC/VLSI 扩展论文。

### [ISSCC-SF03](#ISSCC-SF03)。 Transformer/LLM 令牌处理加速器

- 研究问题： attention、token latency、KV/cache movement、低比特 GEMM 和 speculative decoding 如何落到真实芯片。
- 背景： 2022 的 TranCIM 和 approximate Transformer processor 是 ISSCC 内较清晰的起点。
- Current state: 2023-2026 出现 sparse Transformer processor、MulTCIM、C-Transformer、Slim-Llama、T-REX、bit-level compressed LLM accelerator、SoulMate、speculative-decoding processor 等路线。
- 方法谱系：近似/稀疏注意力 -> 全数字位线转置 CIM -> 多模/稀疏 Transformer CIM -> 低位 Llama/T-REX -> SoulMate/推测解码/视觉自回归处理器。
- 代表论文：[ISSCC-2022-P0171](../../10_corpus/ISSCC/id_index.md#ISSCC-2022-P0171)； [ISSCC-2022-P0179](../../10_corpus/ISSCC/id_index.md#ISSCC-2022-P0179)； [ISSCC-2023-P0108](../../10_corpus/ISSCC/id_index.md#ISSCC-2023-P0108); [ISSCC-2023-P0153](../../10_corpus/ISSCC/id_index.md#ISSCC-2023-P0153); [ISSCC-2023-P0160](../../10_corpus/ISSCC/id_index.md#ISSCC-2023-P0160); [ISSCC-2024-P0090](../../10_corpus/ISSCC/id_index.md#ISSCC-2024-P0090); [ISSCC-2025-P0096](../../10_corpus/ISSCC/id_index.md#ISSCC-2025-P0096); [ISSCC-2025-P0142](../../10_corpus/ISSCC/id_index.md#ISSCC-2025-P0142); [ISSCC-2025-P0165](../../10_corpus/ISSCC/id_index.md#ISSCC-2025-P0165); [ISSCC-2026-P0009](../../10_corpus/ISSCC/id_index.md#ISSCC-2026-P0009); [ISSCC-2026-P0039](../../10_corpus/ISSCC/id_index.md#ISSCC-2026-P0039)； [ISSCC-2026-P0068](../../10_corpus/ISSCC/id_index.md#ISSCC-2026-P0068)；...。
- 团队线索： Tsinghua/UCSB/Yuan Xie/Shouyi Yin/Leibo Liu、KAIST SSL、Columbia sparse Transformer、Konkuk/T-REX 等只作为 team_signal。
- workload/artifact 信号： BERT-base、Transformer attention、Llama、visual autoregressive generation；SoulMate 有公开 PDF，code/artifact 未验证。
- 开放问题： 需要和 MICRO/ISCA/HPCA/MLSys 的 LLM serving、attention/KV cache、compiler/runtime paper 对齐。

### [ISSCC-SF04](#ISSCC-SF04)。 3D 感知、SLAM、NeRF/3DGS 和传感

- 研究问题： 3D sensing、SLAM、NeRF/3DGS 和空间计算在端侧实时运行时，如何压低 frame energy、点云/kNN latency、渲染内存流量和 sensor-to-compute 开销。
- 背景： ISSCC 从低功耗 3D vision/stereo-depth/ultrasound/SPAD front-end 开始，逐步出现 CNN-SLAM、NeuroSLAM、LiDAR-SLAM、NeRF/NeRF-SLAM、3DGS 和 visual autoregressive silicon。
- Current state: 2019 CNN-SLAM 是较强 citation/lineage 候选；2023 MetaVRain、2024 NeuGPU/Space-Mate、2025 3DGS processor/IRIS、2026 3DGS/VAR rows 构成神经渲染硅化早期序列。
- 方法谱系：3D 视觉/立体深度 -> CNN-SLAM/NeuroSLAM -> LiDAR-SLAM 点神经分割 -> NeRF/NeRF-SLAM 稀疏 MoE -> NeuGPU 分段哈希 -> 3DGS 处理器/SoC -> 视觉自回归加速。
- 代表论文：[ISSCC-2016-P0058](../../10_corpus/ISSCC/id_index.md#ISSCC-2016-P0058)； [ISSCC-2016-P0168](../../10_corpus/ISSCC/id_index.md#ISSCC-2016-P0168)； [ISSCC-2017-P0118](../../10_corpus/ISSCC/id_index.md#ISSCC-2017-P0118); [ISSCC-2019-P0097](../../10_corpus/ISSCC/id_index.md#ISSCC-2019-P0097); [ISSCC-2020-P0202](../../10_corpus/ISSCC/id_index.md#ISSCC-2020-P0202); [ISSCC-2021-P0135](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0135); [ISSCC-2021-P0159](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0159); [ISSCC-2023-P0049](../../10_corpus/ISSCC/id_index.md#ISSCC-2023-P0049); [ISSCC-2024-P0076](../../10_corpus/ISSCC/id_index.md#ISSCC-2024-P0076); [ISSCC-2024-P0156](../../10_corpus/ISSCC/id_index.md#ISSCC-2024-P0156); [ISSCC-2025-P0187](../../10_corpus/ISSCC/id_index.md#ISSCC-2025-P0187)。
- 团队线索： Michigan/Blaauw/Sylvester/Kim、Raychowdhury、Yoo/Han/Kim/Park/Song/Ryu、Tsinghua/3DGS 等均为 string-level signal。
- workload/artifact 信号： stereo depth、VGA CNN-SLAM、LiDAR-SLAM、NeRF、3DGS、ultrasound/SPAD；稳定 code/artifact 复用证据仍缺。
- 开放问题： 必须和 SIGGRAPH/graphics、robotics、FPGA/architecture venue 交叉核对，才能判断 3DGS silicon 是稳定 topic 还是早期 burst。

### [ISSCC-SF05](#ISSCC-SF05)。产品规模 AI/HPC 平台芯片

- 研究问题： GPU/CPU/chiplet/AI SoC 的真实产品硅如何处理 HBM、die-to-die、cache/memory hierarchy、package power 和 enterprise/datacenter workload。
- 背景： ISSCC 这里提供 silicon/PPA/product disclosure，不是算法 benchmark paper。
- Current state: POWER9、A100、Telum/Telum II、Ponte Vecchio、MI300/MI350、Spyre、Maia、Rebellions quad-chiplet SoC 构成平台线索。
- 方法谱系：处理器加速器链接 -> 数据中心 GPU 张量/平台功能 -> CPU 中的企业 AI 加速器 -> 多块 exascale 处理器 ->chiplet/HBM AI 封装 -> reticle/quad-chiplet/UCIe AI推理 SoC。
- 代表论文：[ISSCC-2017-P0059](../../10_corpus/ISSCC/id_index.md#ISSCC-2017-P0059)； [ISSCC-2021-P0026](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0026); [ISSCC-2022-P0042](../../10_corpus/ISSCC/id_index.md#ISSCC-2022-P0042)； [ISSCC-2022-P0043](../../10_corpus/ISSCC/id_index.md#ISSCC-2022-P0043); [ISSCC-2024-P0167](../../10_corpus/ISSCC/id_index.md#ISSCC-2024-P0167)； [ISSCC-2024-P0180](../../10_corpus/ISSCC/id_index.md#ISSCC-2024-P0180); [ISSCC-2025-P0003](../../10_corpus/ISSCC/id_index.md#ISSCC-2025-P0003); [ISSCC-2025-P0191](../../10_corpus/ISSCC/id_index.md#ISSCC-2025-P0191); [ISSCC-2026-P0002](../../10_corpus/ISSCC/id_index.md#ISSCC-2026-P0002); [ISSCC-2026-P0030](../../10_corpus/ISSCC/id_index.md#ISSCC-2026-P0030); [ISSCC-2026-P0223](../../10_corpus/ISSCC/id_index.md#ISSCC-2026-P0223)； [ISSCC-2026-P0244](../../10_corpus/ISSCC/id_index.md#ISSCC-2026-P0244)。
- 团队线索： IBM、NVIDIA、Intel、AMD、Microsoft、Rebellions 等为 company-team signal，不做技术实力排名。
- workload/artifact 信号： datacenter AI/HPC、enterprise inference、large-scale AI serving；官方页面提供部分 product/platform adoption signal。
- 开放问题： 要把 ISSCC silicon disclosure 与 Hot Chips、MLPerf、系统软件/编译器和供应商白皮书分开审计。

### [ISSCC-SF06](#ISSCC-SF06)。奖励边界电路行

- 研究问题： 奖项论文必须筛选，但并非所有 ISSCC award 都服务于本项目主线。
- 背景： 已解析 award paper 包含 power、ADC、video decoder、touch sensor、genomics processor、PLL/frequency reference 等。
- Current state: official award source 可以保留，但在 subfield deep dive 中作为 boundary evidence，不提升为 accelerator trend。
- 代表论文：[ISSCC-2016-P0011](../../10_corpus/ISSCC/id_index.md#ISSCC-2016-P0011)； [ISSCC-2016-P0013](../../10_corpus/ISSCC/id_index.md#ISSCC-2016-P0013)； [ISSCC-2016-P0203](../../10_corpus/ISSCC/id_index.md#ISSCC-2016-P0203); [ISSCC-2017-P0079](../../10_corpus/ISSCC/id_index.md#ISSCC-2017-P0079); [ISSCC-2017-P0190](../../10_corpus/ISSCC/id_index.md#ISSCC-2017-P0190); [ISSCC-2021-P0022](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0022); [ISSCC-2021-P0130](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0130); [ISSCC-2021-P0167](../../10_corpus/ISSCC/id_index.md#ISSCC-2021-P0167); [ISSCC-2025-P0046](../../10_corpus/ISSCC/id_index.md#ISSCC-2025-P0046); [ISSCC-2026-P0199](../../10_corpus/ISSCC/id_index.md#ISSCC-2026-P0199)。
- 开放问题： A13-A23 仍是 handout placeholder，需要人工抽取 paper-title/authors/paper_id。

## 4. 发展趋势

- 2016-2018 CNN/RNN edge-AI silicon: Eyeriss -> Envision -> DNPU -> UNPU，支撑论文 `ISSCC-2016-P0017; ISSCC-2017-P0137; ISSCC-2017-P0172; ISSCC-2018-P0104`。
- 2018-2022 CIM/NMC: SRAM、ReRAM、MRAM、analog/digital、inference/training、HBM-PIM 多条支线并行，支撑论文 `ISSCC-2018-P0019; P0026; P0088; ISSCC-2019-P0183; ISSCC-2020-P0002; P0164; P0171; P0196; ISSCC-2021-P0020; P0089; P0193; ISSCC-2022-P0025`。
- 2022-2026 Transformer/LLM: sparse/approximate attention 和 CIM token pipeline 扩展到 Llama、T-REX、SoulMate、speculative decoding 和 visual autoregressive rows，支撑论文 `ISSCC-2022-P0171; P0179; ISSCC-2023-P0108; P0153; P0160; ISSCC-2025-P0096; P0142; P0165; ISSCC-2026-P0068; P0207`。
- 2019-2026 3D/SLAM/neural-rendering: CNN-SLAM/NeuroSLAM 过渡到 NeRF/NeRF-SLAM/NeuGPU，再到 3DGS 和 visual autoregressive silicon，支撑论文 `ISSCC-2019-P0097; ISSCC-2020-P0202; ISSCC-2023-P0049; ISSCC-2024-P0156; P0167; ISSCC-2025-P0046; P0187; ISSCC-2026-P0199; P0250; P0263`。
- 2021-2026 product-scale AI/HPC platform: HBM/chiplets/interconnect/package 和供应商产品硅，支撑论文 `ISSCC-2021-P0026; ISSCC-2022-P0042; P0043; ISSCC-2024-P0180; ISSCC-2025-P0191; ISSCC-2026-P0002; P0030; P0223; P0244`。

## 5. 方法变化

早期 AI accelerator 关注 CNN/RNN 的 TOPS/W、fps/W、数据复用和低电压。CIM/PIM 把评价对象转向 array capacity、MAC latency、precision、readout 和 memory bandwidth。Transformer/LLM 后，评价对象出现 uJ/token、low-bit LLM、attention sparsity、KV/cache movement 和 speculative decoding。3D/SLAM/neural-rendering 线把 mJ/frame、fps、point-cloud/kNN、Gaussian cache 和 surface-aware modeling 放进 chip PPA。平台线关注 HBM、chiplet、die-to-die、reticle/package 和 enterprise/datacenter deployment。

## 6. 缺失来源

- 2016-2026 official final program 的逐页抽取和完整 session/track/name 回填。
- IEEE Xplore abstracts、affiliations、PDF first page 和 keywords 的批量抽取。
- ISSCC award handout 的 paper-level 人工复核表，特别是 A13-A23 placeholder、2021 link rot 和 2023 redirect/html source。
- ISSCC 与 JSSC/VLSI/CICC/A-SSCC/Hot Chips 的同一芯片后续扩展论文对照。
- Artifact/code reuse 和 benchmark standardization 的系统审计。
