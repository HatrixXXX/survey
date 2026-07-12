# VLSI 第二轮小领域深读

检索/写入日期：`2026-06-27`  
输入范围：`10_corpus/venues/VLSI/` 与 `20_venue_reports/VLSI/`。本文件只讨论 VLSI venue 内部信号。

## 1. 范围与语料

第二轮筛选覆盖 `papers.csv` 2291 行和 `awards.csv` 50 行，写入 `VLSI_screening_matrix.csv` 2341 行。父 agent 最终把 112 篇论文纳入 evidence matrix，包括官方奖项论文、首轮代表论文、CIM/PIM、Transformer/LLM、3DGS/neural rendering、edge robotics、in-sensor perception、chiplet/3D integration 和低精度/稀疏 neural SoC 线索。

`VLSI_paper_evidence_matrix.csv` 对这些论文记录 WHY/HOW/WHAT/IMPACT/EVIDENCE。citation、adoption、artifact 和 benchmark 信号均写检索日期；没有可靠证据的长期影响写为 `impact_unverified` 或 `needs_review`。2026 年论文仍按 `normal_2026_partial` 处理。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="VLSI-SF01"></a>[VLSI-SF01](#VLSI-SF01) | 神经渲染和 3D 高斯映射芯片 | 神经渲染、NeRF/3DGS 式映射和占用 workload 如何成为可测量的 SoC/PIM 芯片，而不仅仅是 GPU 软件。 | NeRF、神经渲染、3D 高斯占用映射、高斯排序 | 帧能量、占用图更新延迟、移动内存流量和实时吞吐量 | PIM 映射、特定 workload SoC、低功耗排序/映射引擎 | 2023-2026 | cross_venue_candidate； evidence_rows=4 |
| <a id="VLSI-SF02"></a>[VLSI-SF02](#VLSI-SF02) | 机器人技术和嵌入式边缘 SoC | 导航、VIO、SLAM/路径规划和嵌入式 AI 如何适应严格的边缘功耗、延迟和小芯片/内存预算。 | VIO、微型机器人视觉、路径规划、体现多模式 AI、代理动作循环 | 批量 1 延迟、传感器融合带宽、功耗、稀疏/密集混合计算 | 视觉惯性管道、异构 SoC、RVV/chiplet 集成、路径规划加速器 | 2018-2026 | cross_venue_candidate； evidence_rows=10 |
| <a id="VLSI-SF03"></a>[VLSI-SF03](#VLSI-SF03) | Transformer 和 LLM 令牌级加速器 | 注意力、SoftMax、KV 缓存、推测性解码、令牌生成和片上学习如何映射到硅能量和延迟限制。 | BERT、MobileBERT、LLM 推理/训练、Qwen 风格推理/RLFT、多模态 AR 生成 | 内存带宽、KV 缓存大小、预填充/解码不平衡、梯度/更新成本 | 低位量化、近似 SoftMax、推测性解码、 CIM/CAM 模式、RRAM/FP8 宏 | 2022-2026 | venue_provisional； evidence_rows=17 |
| <a id="VLSI-SF04"></a>[VLSI-SF04](#VLSI-SF04) | CIM/PIM 和内存墙加速器 | SRAM/RRAM/PCM/MRAM/FeFET 阵列如何减少数据移动，同时保持准确性、可编程性和测量的 PPA。 | ML 分类器、CNN/DNN 推理/训练、边缘 AI、科学计算、Transformer宏 | 权重/数据移动、ADC/DAC 开销、设备变化、保留、阵列利用率、精度 | SRAM CIM、RRAM/PCM/MRAM 模拟CIM、数字 CIM、PIM 架构、单片 3D 内存计算 | 2016-2026 | venue_split_candidate； evidence_rows=23 |
| <a id="VLSI-SF05"></a>[VLSI-SF05](#VLSI-SF05) | 边缘视觉和传感器内感知 | 图像传感器、SPAD/时间选通传感器和像素内/传感器内计算如何减少感知数据移动和前端延迟。 | ToF、SPAD/LiDAR、人脸分析、像素内计算、事件/视觉传感 | 传感器带宽、SNR/动态范围、读出能量、本地预处理延迟 | 堆叠图像传感器、SPAD 门控、像素内 FDSOI 计算、传感器 SoC | 2017-2026 | venue_provisional； evidence_rows=15 |
| <a id="VLSI-SF06"></a>[VLSI-SF06](#VLSI-SF06) | 小芯片、3D 集成和加速器扩展 | 小芯片、HBM、CoWoS/SoIC、3DIC 和芯片到芯片链接如何支持更大的加速器系统和内存带宽。 | RISC-V/HBM 计算、AI/HPC 小芯片、3D 内存/逻辑集成、高带宽互连 | 片外带宽、封装布线、热/功率密度、小芯片通信 | CoWoS、SoIC、UCIe/die-to-die IO、HBM 集成、3D 堆叠 | 2016-2026 | venue_provisional； evidence_rows=13 |
| <a id="VLSI-SF07"></a>[VLSI-SF07](#VLSI-SF07) | 低精度和稀疏神经 SoC | 精确缩放、稀疏性和可重构数据流如何在边缘和加速器约束下改进测量的 TOPS/W。 | CNN/DNN 处理器、稀疏神经网络、癫痫预测、精确可扩展推理 | 计算能量、利用率、SRAM 带宽、数据流灵活性和准确性损失 | 二进制/三进制/4 位格式、稀疏引擎、可重新配置处理器、在线学习 | 2016-2025 | venue_provisional； evidence_rows=15 |
| <a id="VLSI-SF08"></a>[VLSI-SF08](#VLSI-SF08) | 实现桥、编译器和可基准测试芯片 | 如何电路/架构思想通过编译器、CGRA、基准测试或 DTCO 挂钩变成可编程或类似芯片。 | 密集线性代数、CGRA、硅编译器/IP、DTCO 和可重现加速器评估 | 映射工作、利用率、测量的 PPA 闭包、基准可比性 | CGRA、编译器生成的 CIM、设计空间/DTCO 流程、面向基准的芯片评估 | 2018-2026 | venue_provisional； evidence_rows=4 |
| <a id="VLSI-SF09"></a>[VLSI-SF09](#VLSI-SF09) | 奖励边界和非主行 | 奖励或源完整性行，这些行对出处有价值，但不作为加速器小领域证据进行推广。 | 历史 ToT 或非主要/会议记录材料 | 源对齐和范围控制 | 奖励源验证和行排除 | 2016-2025 | insufficient_evidence； evidence_rows=11 |

## 3. 小领域深读

### [VLSI-SF01](#VLSI-SF01)：神经渲染和 3D 高斯映射芯片

- 研究问题：神经渲染、NeRF/3DGS 式映射和占用 workload 如何成为可测量的 SoC/PIM 芯片，而不仅仅是 GPU 软件。
- 背景：VLSI 强调测量的silicon、器件/电路/工艺证据和 PPA 闭包，因此该小领域是通过芯片、宏、传感器、封装或官方程序行而不是通过宽泛的标签来跟踪的。
- VLSI 的当前状态：evidence rows涵盖 2023-2026 年，有 4 篇 deep_read 论文。状态为`cross_venue_candidate`； 2026 篇来自官方项目的论文仍然是 `partial`。
- 方法谱系：PIM 映射、特定于 workload 的 SoC、低功耗排序/映射引擎。
- 代表论文：[VLSI-2023-P0154](../../10_corpus/VLSI/id_index.md#VLSI-2023-P0154) NeRPIM: A 4.2 mJ/frame Neural Rendering Handling-in-Memory Processor with Space Encoding； [VLSI-2026-P0069](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0069) C23.2 Spectre：376 fps 2.67 nJ/像素 4DGS 处理器，用于时空重建； [VLSI-2026-P0099](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0099) C3.1 Gleanmer：用于实时 3D 高斯占用映射的 6 mW SoC，Zih-Sing Fu1，Peter； [VLSI-2026-P0103](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0103) C3.5 Uni4D：具有统一功能的 12nm 0.16mJ/帧 4D 高斯空间视频渲染处理器。
- 团队线索：KAIST/Hoi-Jun Yoo 作者字符串出现在 NeRPIM/NOVA 风格的神经渲染行中； MIT/Sze-Karaman 字符串出现在 Gleamer 中。这些只是团队线索。
- workload/artifact 信号：NeRF、神经渲染、3D 高斯占用映射、高斯排序。除非在 `VLSI_paper_evidence_matrix.csv` 中明确列出，否则不会验证 artifact/代码重用；大多数行仍为 `none_found_in_corpus` 或 `needs_review`。
- 开放问题：在将本 venue-local信号提升为cross-venue稳定主题之前，仍然需要完整的 IEEE PDF/摘要提取、entity disambiguation和引用/采用图审计。

### [VLSI-SF02](#VLSI-SF02)：机器人技术和嵌入式边缘 SoC

- 研究问题：导航、VIO、SLAM/路径规划和嵌入式 AI 如何适应严格的边缘功耗、延迟和小芯片/内存预算。
- 背景：VLSI 强调测量的silicon、器件/电路/工艺证据和 PPA 闭包，因此该小领域是通过芯片、宏、传感器、封装或官方程序行而不是通过宽泛的标签来跟踪的。
- VLSI 的当前状态：evidence rows涵盖 2018-2026 年，有 10 篇 deep_read 论文。状态为`cross_venue_candidate`； 2026 篇来自官方项目的论文仍然是 `partial`。
- 方法谱系：视觉惯性管道、异构 SoC、RVV/chiplet 集成、路径规划加速器。
- 代表论文：[VLSI-2018-P0104](../../10_corpus/VLSI/id_index.md#VLSI-2018-P0104) Navion: A Excellent Integrated Energy-Efficient Visual-Inertial Odometry Accelerator for Auton； [VLSI-2020-P0085](../../10_corpus/VLSI/id_index.md#VLSI-2020-P0085) 10nm 光线投射加速器 CMOS 用于边缘机器人中的高效 3D 场景重建； [VLSI-2022-P0036](../../10_corpus/VLSI/id_index.md#VLSI-2022-P0036) 一款 22nm 3.5TOPS/W 灵活微型机器人视觉 SoC，具有 2MB eMRAM，用于全片上 Intel； [VLSI-2023-P0132](../../10_corpus/VLSI/id_index.md#VLSI-2023-P0132) GPPU：330.4μJ/任务神经路径规划处理器，具有混合 GNN 自动加速功能； [VLSI-2025-P0172](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0172) MAVERIC：16nm 72 FPS、10 mJ/帧异构机器人 SoC，具有 4 核和 13 个 INT8/FP； [VLSI-2026-P0062](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0062) C21.3 Sirius：用于多模式体现 AI 的双芯片系统，具有异构 RVV 核心； [VLSI-2026-P0063](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0063) C21.4 具有令牌过滤和 Hybrid Pro 的可扩展视觉-语言-动作边缘处理器； [VLSI-2026-P0101](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0101) C3.3 SR-VLNA：5.0-23.9 mJ/米基于空间推理的视觉语言导航加速器。
- 团队线索：MIT/Sze-Karaman、密歇根低功耗 SoC、KAIST 路径规划/机器人、Berkeley/Shao 和斯坦福/TSMC 字符串跨行出现；没有断言排名或实体合并。
- workload/artifact 信号：VIO、微型机器人视觉、路径规划、体现多模式 AI、代理动作循环。除非在 `VLSI_paper_evidence_matrix.csv` 中明确列出，否则不会验证 artifact/代码重用；大多数行仍为 `none_found_in_corpus` 或 `needs_review`。
- 开放问题：在将本 venue-local信号提升为cross-venue稳定主题之前，仍然需要完整的 IEEE PDF/摘要提取、entity disambiguation和引用/采用图审计。

### [VLSI-SF03](#VLSI-SF03)：Transformer 和 LLM 令牌级加速器

- 研究问题：注意力、SoftMax、KV 缓存、推测性解码、令牌生成和片上学习如何映射到硅能量和延迟限制。
- 背景：VLSI 强调测量的silicon、器件/电路/工艺证据和 PPA 闭包，因此该小领域是通过芯片、宏、传感器、封装或官方程序行而不是通过宽泛的标签来跟踪的。
- VLSI 的当前状态：evidence rows涵盖 2022-2026 年，有 17 篇 deep_read 论文。状态为`venue_provisional`； 2026 篇来自官方项目的论文仍然是 `partial`。
- 方法谱系：低位量化、近似 SoftMax、推测性解码、CIM/CAM 模式、RRAM/FP8 宏。
- 代表论文：[VLSI-2022-P0031](../../10_corpus/VLSI/id_index.md#VLSI-2022-P0031) A 17-95.6 TOPS/W Deep Learning Inference Accelerator with Per-Vector Scaled 4-bit Quantiza； [VLSI-2024-P0076](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0076) 具有近似注意力分数梯度 Com 的 99.2TOPS/W Transformer学习处理器； [VLSI-2024-P0125](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0125) 采用内存技术处理的经济高效的 LLM 加速器； [VLSI-2024-P0168](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0168) MINOTAUR：具有 12 MB 片上 Re 的边缘Transformer推理和训练加速器； [VLSI-2025-P0003](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0003) 1.536TB/s/mm2 带宽可扩展注意力加速器，具有 22.5GOPS 高速吞吐量； [VLSI-2025-P0040](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0040) 使用 QKV-Softmax-Layer- 的 22nm 41.8TFLOPS/W AI-Edge Transformer/CNN 非易失性处理器； [VLSI-2025-P0100](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0100) Adelia：4nm LLM 加速器，具有简化的数据流和双模式并行化； [VLSI-2025-P0103](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0103) 157TOPS/W Transformer学习处理器，仅支持零阶前向传递。
- 团队线索：NVIDIA、NTU 台湾、SK hynix、Stanford/TSMC、Intel、KAIST/HyperAccel、清华/HKUST、Cornell Tech 和北大字符串出现；没有断言排名。
- workload/artifact 信号： BERT, MobileBERT, LLM inference/training, Qwen-style reasoning/RLFT, multimodal AR generation.除非在 `VLSI_paper_evidence_matrix.csv` 中明确列出，否则不会验证 artifact/代码重用；大多数行仍为 `none_found_in_corpus` 或 `needs_review`。
- 开放问题：在将本 venue-local信号提升为cross-venue稳定主题之前，仍然需要完整的 IEEE PDF/摘要提取、entity disambiguation和引用/采用图审计。

### [VLSI-SF04](#VLSI-SF04)：CIM/PIM 和内存墙加速器

- 研究问题：SRAM/RRAM/PCM/MRAM/FeFET 阵列如何减少数据移动，同时保持准确性、可编程性和测量的 PPA。
- 背景：VLSI 强调测量的silicon、器件/电路/工艺证据和 PPA 闭包，因此该小领域是通过芯片、宏、传感器、封装或官方程序行而不是通过宽泛的标签来跟踪的。
- VLSI 的当前状态：evidence rows涵盖 2016-2026 年，有 23 篇 deep_read 论文。状态为`venue_split_candidate`； 2026 篇来自官方项目的论文仍然是 `partial`。
- 方法谱系：SRAM CIM、RRAM/PCM/MRAM 模拟 CIM、数字 CIM、PIM 架构、单片 3D 内存计算。
- 代表论文：[VLSI-2016-P0076](../../10_corpus/VLSI/id_index.md#VLSI-2016-P0076) 在标准 6T SRAM 数组中实现的机器学习分类器； [VLSI-2016-P0144](../../10_corpus/VLSI/id_index.md#VLSI-2016-P0144) 首次演示 InGaAs/SiGe CMOS 逆变器和使用 select 的 Si 上密集 SRAM 阵列； [VLSI-2017-P0014](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0014) A 0.3V VDDmin 4+2T SRAM，用于使用 55nm DDC 技术进行搜索和内存计算； [VLSI-2017-P0065](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0065) 一款基于 RRAM 的 462GOPs/J 的非易失性智能处理器，用于能量收集 IoE 系统； [VLSI-2017-P0116](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0116) BRein 内存：13 层 4.2 K 神经元/0.8 M 突触二元/三元可重构内存； [VLSI-2019-P0114](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0114) 基于计算记忆的深度神经网络推理和训练； [VLSI-2019-P0178](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0178) 混合监督-无监督神经网络中的节能持续学习； [VLSI-2019-P0188](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0188) 首次展示具有超低开关的柔性基板上的全印刷 Mos2Rram。
- 团队线索： Princeton/Verma, Michigan/Blaauw/Sylvester, IBM analog AI, Polimi+IBM, Stanford/TSMC, KAIST, ASU/Columbia/Samsung, TSMC and HKUST/CAS strings appear;没有断言排名。
- workload/artifact 信号： ML classifiers, CNN/DNN inference/training, edge AI, scientific computing, transformer macros.除非在 `VLSI_paper_evidence_matrix.csv` 中明确列出，否则不会验证 artifact/代码重用；大多数行仍为 `none_found_in_corpus` 或 `needs_review`。
- 开放问题：在将本 venue-local信号提升为cross-venue稳定主题之前，仍然需要完整的 IEEE PDF/摘要提取、entity disambiguation和引用/采用图审计。

### [VLSI-SF05](#VLSI-SF05)：边缘视觉和传感器内感知

- 研究问题：图像传感器、SPAD/时间选通传感器和像素内/传感器内计算如何减少感知数据移动和前端延迟。
- 背景：VLSI 强调测量的silicon、器件/电路/工艺证据和 PPA 闭包，因此该小领域是通过芯片、宏、传感器、封装或官方程序行而不是通过宽泛的标签来跟踪的。
- VLSI 的当前状态：evidence rows涵盖 2017-2026 年，有 15 篇 deep_read 论文。状态为`venue_provisional`； 2026 篇来自官方项目的论文仍然是 `partial`。
- 方法谱系：堆叠图像传感器、SPAD 门控、像素内 FDSOI 计算、传感器 SoC。
- 代表论文：[VLSI-2017-P0005](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0005) 320×240 背照式10μm CAPD 像素用于高速调制飞行时间CMOS im； [VLSI-2017-P0022](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0022) 一款 10.1" 56 通道、183 uW/电极、0.73 mm2/传感器高 SNR 3D 悬停传感器，基于 en；[VLSI-2017-P0051](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0051) 一款 272.49 pJ/像素 CMOS 图像传感器，具有嵌入式物体检测和仿生 2D opt；[VLSI-2018-P0173](../../10_corpus/VLSI/id_index.md#VLSI-2018-P0173) 下一代眼底相机在 0-lx 可见光下采集全彩色图像；[VLSI-2019-P0086](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0086) A CMOS 具有 11 位分辨率的温度稳定二维机械应力传感器；[VLSI-2021-P0078](../../10_corpus/VLSI/id_index.md#VLSI-2021-P0078) 亚毫瓦双引擎 ML 片上推理系统，可在 ; [VLSI-2023-P0047](../../10_corpus/VLSI/id_index.md#VLSI-2023-P0047) 适用于低功耗视觉应用的 320 x 320 1/5” BSI-CMOS 堆叠式事件传感器； [VLSI-2024-P0004](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0004) 3D 堆叠 1 兆像素时间选通 SPAD 图像传感器，具有 2D 交互式选通网络，适用于.
- 团队线索：Sony/image-sensor、北京大学 in-pixel、VLSI 演示获胜者和边缘传感器 SoC 作者字符串出现；没有断言排名。
- workload/artifact signal：ToF、SPAD/LiDAR、面部分析、像素内计算、事件/视觉传感。除非在 `VLSI_paper_evidence_matrix.csv` 中明确列出，否则不会验证 artifact/代码重用；大多数行仍为 `none_found_in_corpus` 或 `needs_review`。
- 开放问题：在将本 venue-local信号提升为cross-venue稳定主题之前，仍然需要完整的 IEEE PDF/摘要提取、entity disambiguation和引用/采用图审计。

### [VLSI-SF06](#VLSI-SF06)：chiplet、3D 集成和加速器扩展

- 研究问题：chiplet、HBM、CoWoS/SoIC、3DIC 和芯片到芯片链接如何支持更大的加速器系统和内存带宽。
- 背景：VLSI 强调测量的silicon、器件/电路/工艺证据和 PPA 闭包，因此该小领域是通过芯片、宏、传感器、封装或官方程序行而不是通过宽泛的标签来跟踪的。
- VLSI 的当前状态：evidence rows涵盖 2016-2026 年，有 13 篇 deep_read 论文。状态为`venue_provisional`； 2026 篇来自官方项目的论文仍然是 `partial`。
- 方法谱系：CoWoS、SoIC、UCIe/die-to-die IO、HBM 集成、3D 堆叠。
- 代表性论文： [VLSI-2016-P0143](../../10_corpus/VLSI/id_index.md#VLSI-2016-P0143) 首次演示 CMOS 与 CMOS 3D VLSI CoolCube™ 在 300mm 晶圆上的集成； [VLSI-2016-P0173](../../10_corpus/VLSI/id_index.md#VLSI-2016-P0173) 适合量产的 WOW 采用无凸点互连和超薄的 3D 集成技术； [VLSI-2017-P0128](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0128) 用于异构集成的高密度 3D 扇出封装； [VLSI-2019-P0081](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0081) 用于高性能计算的基于 7nm 4GHz Arm® 内核的 CoWoS® 小芯片设计； [VLSI-2024-P0143](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0143) 超高密度混合体单片三维集成首次演示； [VLSI-2024-P0174](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0174) Occamy：432 核 28.1 DP-GFLOP/s/W 83% FPU 利用率双芯片、双 HBM2E RISC-V-B； [VLSI-2025-P0021](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0021) 具有低延迟的 0.52pJ/位 0.448Tbps/mm UCIe 标准封装芯片间收发器 TX； [VLSI-2026-P0142](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0142) Chiplet 计算时代的 JFS4.1 架构划分与优化，Vamsi K.
- 团队线索：TSMC Packaging/3DIC、ETH/Occamy、Berkeley/Shao/Sirius 和imec/Sony/advanced 集成串出现；没有断言排名。
- workload/artifact 信号：RISC-V/HBM 计算、AI/HPC 小芯片、3D 内存/逻辑集成、高带宽互连。除非在 `VLSI_paper_evidence_matrix.csv` 中明确列出，否则不会验证 artifact/代码重用；大多数行仍为 `none_found_in_corpus` 或 `needs_review`。
- 开放问题：在将本 venue-local信号提升为cross-venue稳定主题之前，仍然需要完整的 IEEE PDF/摘要提取、entity disambiguation和引用/采用图审计。

### [VLSI-SF07](#VLSI-SF07)：低精度和稀疏神经 SoC

- 研究问题：精确缩放、稀疏性和可重构数据流如何在边缘和加速器约束下改进测量的 TOPS/W。
- 背景：VLSI 强调测量的silicon、器件/电路/工艺证据和 PPA 闭包，因此该小领域是通过芯片、宏、传感器、封装或官方程序行而不是通过宽泛的标签来跟踪的。
- VLSI 的当前状态：evidence rows涵盖 2016-2025 年，有 15 篇 deep_read 论文。状态为`venue_provisional`； 2026 篇来自官方项目的论文仍然是 `partial`。
- 方法谱系：二进制/三进制/4 位格式、稀疏引擎、可重构处理器、在线学习。
- 代表论文：[VLSI-2016-P0011](../../10_corpus/VLSI/id_index.md#VLSI-2016-P0011) A 0.3-2.6 TOPS/W 用于实时大规模ConvNets的精度可扩展处理器； [VLSI-2016-P0016](../../10_corpus/VLSI/id_index.md#VLSI-2016-P0016) 40nm 1.40mm2141mW 898GOPS 稀疏神经拟态处理器 CMOS； [VLSI-2017-P0019](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0019) 用于深度学习应用程序的 1.06 至 5.09 TOPS/W 可重构混合神经网络处理器； [VLSI-2017-P0028](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0028) 用于动作分类和运动的 127mW 1.63TOPS 稀疏时空认知 SoC； [VLSI-2018-P0112](../../10_corpus/VLSI/id_index.md#VLSI-2018-P0112) 贴纸：0.41-62.1 TOPS/W 8 位神经网络处理器，具有多稀疏性兼容 C； [VLSI-2019-P0077](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0077) 使用内存 Re 的 7.3 M 输出非零/J 稀疏矩阵-矩阵乘法加速器； [VLSI-2019-P0127](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0127) SNAP：用于非结构化稀疏德的 1.67 - 21.55TOPS/W 稀疏神经加速处理器； [VLSI-2020-P0028](../../10_corpus/VLSI/id_index.md#VLSI-2020-P0028) A 146.52 TOPS/W 具有随机粗精修剪功能的深度神经网络学习处理器。
- 团队线索：KU Leuven/MICAS、Tsinghua/HKUST、Berkeley/SPIRIT 以及早期低精度处理器作者字符串出现；没有断言排名。
- workload/artifact 信号：CNN/DNN 处理器、稀疏神经网络、癫痫预测、精确可扩展推理。除非在 `VLSI_paper_evidence_matrix.csv` 中明确列出，否则不会验证 artifact/代码重用；大多数行仍为 `none_found_in_corpus` 或 `needs_review`。
- 开放问题：在将本 venue-local信号提升为cross-venue稳定主题之前，仍然需要完整的 IEEE PDF/摘要提取、entity disambiguation和引用/采用图审计。

### [VLSI-SF08](#VLSI-SF08)：实现桥、编译器和可基准测试的硅

- 研究问题：电路/架构思想如何通过编译器、CGRA、基准测试或 DTCO 挂钩变成可编程或可比较的芯片。
- 背景：VLSI 强调测量的silicon、器件/电路/工艺证据和 PPA 闭包，因此该小领域是通过芯片、宏、传感器、封装或官方程序行而不是通过宽泛的标签来跟踪的。
- VLSI 的当前状态：evidence rows涵盖 2018-2026 年，有 4 篇 deep_read 论文。状态为`venue_provisional`； 2026 篇来自官方项目的论文仍然是 `partial`。
- 方法谱系：CGRA、编译器生成的 CIM、设计空间/DTCO 流程、面向基准的芯片评估。
- 代表论文：[VLSI-2018-P0044](../../10_corpus/VLSI/id_index.md#VLSI-2018-P0044) A 290MV 超低电压单端口 SRAM Compiler Design using a 12T Write Contention and R； [VLSI-2019-P0144](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0144) 2nm 节点：人工智能 FinFET 与纳米板晶体管架构的基准测试； [VLSI-2022-P0097](../../10_corpus/VLSI/id_index.md#VLSI-2022-P0097) 琥珀色：367 GOPS、538 GOPS/W 16nm SoC，带有适用于 Flex 的粗粒度可重构阵列； [VLSI-2026-P0146](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0146) JFS4.5 使用 2D 晶体管的单片 3D FPGA 的设备到架构协同设计，Hung-。
- 团队线索：出现 CGRA/Amber、编译器可配置的 CIM 和 DTCO 面向作者字符串；没有断言排名。
- workload/artifact 信号：密集线性代数、CGRA、硅编译器/IP、DTCO 和可重现加速器评估。除非在 `VLSI_paper_evidence_matrix.csv` 中明确列出，否则不会验证 artifact/代码重用；大多数行仍为 `none_found_in_corpus` 或 `needs_review`。
- 开放问题：在将本 venue-local信号提升为cross-venue稳定主题之前，仍然需要完整的 IEEE PDF/摘要提取、entity disambiguation和引用/采用图审计。

## 4. 发展趋势

- CIM/PIM 是 VLSI 内证据最密的加速方向之一，支撑论文集合包括 [VLSI-2016-P0076](../../10_corpus/VLSI/id_index.md#VLSI-2016-P0076), [VLSI-2017-P0065](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0065), [VLSI-2019-P0114](../../10_corpus/VLSI/id_index.md#VLSI-2019-P0114), [VLSI-2021-P0093](../../10_corpus/VLSI/id_index.md#VLSI-2021-P0093), [VLSI-2022-P0027](../../10_corpus/VLSI/id_index.md#VLSI-2022-P0027), [VLSI-2023-P0055](../../10_corpus/VLSI/id_index.md#VLSI-2023-P0055), [VLSI-2026-P0120](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0120)。趋势只说明 venue 内持续出现，不等同于跨会议稳定分类。
- Transformer/LLM silicon 在 2022-2026 形成前沿线索，支撑论文集合包括 [VLSI-2022-P0031](../../10_corpus/VLSI/id_index.md#VLSI-2022-P0031), [VLSI-2024-P0076](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0076), [VLSI-2024-P0125](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0125), [VLSI-2025-P0100](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0100), [VLSI-2025-P0116](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0116), [VLSI-2026-P0117](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0117), [VLSI-2026-P0119](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0119)。2026 仍是 official-program partial。
- Edge robotics 与 embodied AI 从 Navion 到 micro-robotic vision、MAVERIC/Sirius/uAgent 类 program rows，支撑论文集合包括 [VLSI-2018-P0104](../../10_corpus/VLSI/id_index.md#VLSI-2018-P0104), [VLSI-2020-P0085](../../10_corpus/VLSI/id_index.md#VLSI-2020-P0085), [VLSI-2025-P0172](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0172), [VLSI-2026-P0061](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0061), [VLSI-2026-P0062](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0062)。该趋势需要与 robotics/MLSys/architecture venue 对照。
- Neural rendering / 3D Gaussian 目前是跨 venue candidate，支撑论文集合包括 [VLSI-2023-P0154](../../10_corpus/VLSI/id_index.md#VLSI-2023-P0154), [VLSI-2026-P0069](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0069), [VLSI-2026-P0099](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0099), [VLSI-2026-P0103](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0103)。这说明 VLSI 出现 silicon/program-level 入口，但不能证明已成熟。
- Chiplet/3D integration 在 VLSI 中主要是 accelerator-scaling 支持线，支撑论文集合包括 [VLSI-2017-P0128](../../10_corpus/VLSI/id_index.md#VLSI-2017-P0128), [VLSI-2024-P0174](../../10_corpus/VLSI/id_index.md#VLSI-2024-P0174), [VLSI-2025-P0021](../../10_corpus/VLSI/id_index.md#VLSI-2025-P0021), [VLSI-2026-P0062](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0062), [VLSI-2026-P0142](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0142), [VLSI-2026-P0238](../../10_corpus/VLSI/id_index.md#VLSI-2026-P0238)。

## 5. 方法变化

- 2016-2018：以 SRAM/low-power neural processors、视觉导航和早期 memory-centric classifiers 为主，评价多是 chip PPA、能效和 demo workload。
- 2019-2021：CIM/PIM 和 NVM computational memory 变成更明确的系统问题，award/follow-on 信号开始出现，但 adoption 仍需审计。
- 2022-2024：foundry SRAM/RRAM CIM、Transformer inference/learning、chiplet/HBM 和 edge SoC 信号增多，评价从单一 TOPS/W 扩展到 frame/token/action latency、memory bandwidth 和 utilization。
- 2025-2026：LLM token、speculative decoding、reasoning/RLFT、3D Gaussian occupancy、embodied-AI chiplets、2nm CIM compiler 和 photonic/3D memory compute 进入 official program；这些都按 frontier 和 partial 处理。

## 6. 缺失来源

- IEEE Xplore abstract、affiliation、keywords、PDF 首页的批量抽取。
- 2016-2025 官方 program/session 页级来源与 session/track 回填。
- VLSI 与 JSSC/ISSCC/CICC/A-SSCC/Hot Chips 的 same-chip follow-on 对照。
- Artifact/code 复用、benchmark 标准化和产业/toolchain adoption 的系统审计。
- 2026年期末论文集DOI元数据。
