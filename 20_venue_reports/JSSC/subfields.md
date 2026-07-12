# JSSC 小领域深读

## 1. 范围与语料

本文件基于 `10_corpus/venues/JSSC/papers.csv` 的 2016-2026 DBLP-derived JSSC journal rows、`awards.csv` 的 IEEE SSCS 官方奖项页复核结果、`JSSC_screening_matrix.csv` 的全量筛选，以及 `JSSC_paper_evidence_matrix.csv` 的 45 篇 deep-read/evidence rows。JSSC 是期刊，不是会议 accepted-paper venue；这里把 JSSC 当作 measured silicon、circuit/system implementation 和 award signal 的来源，而不是把它当作算法或体系结构会议的完整替代。

证据深度分层：12 篇 AI/CIM/precision/sparsity/multichip 论文合并了 deep-read A 的 abstract/title 级结果；Transformer/LLM 与 NeRF/3DGS/SLAM 两个 deep-read 子任务因并发限制断开，保留父 agent 的 title/DOI/IEEE/Crossref 级保守 evidence。所有 citation count 仅作为 Crossref/Semantic Scholar 检索信号，检索日期为 2026-06-27；没有做 citation graph、artifact reuse 或产业采用审计。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="JSSC-SF01"></a>[JSSC-SF01](#JSSC-SF01) | 用于 DNN 推理/训练的硅数据流 | CNN/DNN accelerator 如何在真实芯片里降低数据搬运和提高 PE 利用率 | CNN/DNN 推理 | 激活/权重移动，片上复用 | 空间数据流，可重新配置加速器，本地存储 | 2017-2019 | 1 个标题级锚点和 1 个abstract-level精确重叠 |
| <a id="JSSC-SF02"></a>[JSSC-SF02](#JSSC-SF02) | 精度自适应 AI 在硅中执行 | variable/mixed precision 如何成为 silicon-level 能耗、吞吐和精度旋钮 | CNN/DNN 训练和推理、边缘 Transformer | 数字格式成本、准确性/能量权衡 | 1-16b 可变权重、Hybrid-FP8、INT4/INT2、位置/微缩放 | 2019-2026 | 摘要/标题证据；adoption_unverified |
| <a id="JSSC-SF03"></a>[JSSC-SF03](#JSSC-SF03) | 用于 AI 数据移动的内存中计算宏 | 权重/激活搬运能否通过 SRAM/IMC/PIM/near-memory compute 减少 | DNN 推理、设备上学习、Transformer/CIM、超越 NN 稀疏 workload | 内存墙、ADC/AMS/数字 CIM开销、宏可编程性 | 6T SRAM IMC、电荷域 IMC、PIM、可编程 IMC、数字 CIM/MCM | 2018-2026 | 最强的多年证据集； 6 行有摘要/标题详细信息 |
| <a id="JSSC-SF04"></a>[JSSC-SF04](#JSSC-SF04) | 稀疏性和事件驱动的神经加速 | 稀疏或结构化压缩模型怎样避免不规则访存和控制开销 | 稀疏 DNN、块循环 NN、SNN/事件样式路由 | 不规则性、变换开销、低利用率 | 非结构化稀疏核心、块循环/频域加速、稀疏/密集核心 | 2021-2026 | 摘要/标题证据；后续审计缺失 |
| <a id="JSSC-SF05"></a>[JSSC-SF05](#JSSC-SF05) | Transformer 和 LLM 硅内存/注意力瓶颈 | attention/token/LLM 负载怎样在芯片上处理外存访问、动态稀疏和低延迟 | Transformer、LLM、多模态 Transformer、设备上训练 | 注意力内存流量、KV/令牌移动、外部内存 | 注意相关性剪枝、数字/模拟 CIM、全片内存、减少外部内存、双模并行 | 2023-2026 部分 | 12 个标题级前沿行；深读 B 失败、impact_unverified |
| <a id="JSSC-SF06"></a>[JSSC-SF06](#JSSC-SF06) | 神经渲染和空间计算处理器 | NeRF、3DGS、SLAM 和 rendering processor 怎样进入 JSSC silicon/SoC 题名 | NeRF、NeRF-SLAM、3D Gaussian Splatting、移动 AR 渲染、SLAM | 场景表示内存、光线/高斯处理、实时移动能耗 | bundle-frame familiarity、approximate/accurate bit offload、surface-aware 3DGS、Gaussian cache、sparse MoE | 2021-2026 partial | 12 个标题级行；深读 C 失败、impact_unverified |
| <a id="JSSC-SF07"></a>[JSSC-SF07](#JSSC-SF07) | 视觉和机器人边缘加速器管道 | 视觉、点云、机器人与感知 pipeline 如何在端侧芯片中闭合 | SLAM、点云、视觉跟踪、机器人 SoC | 传感器到计算带宽、实时延迟、本地内存 | 视觉惯性里程计、点云推理、机器人 SoC 数据路径 | 2019-2026 | 主要是头衔级别的；重叠 SF06/SF10 |
| <a id="JSSC-SF08"></a>[JSSC-SF08](#JSSC-SF08) | 内存驻留和多芯片 AI 缩放 | 单芯片容量和互连限制下，AI accelerator 如何扩展 | DNN 推理、近内存 AI | 芯片间通信、模型驻留、带宽 | MCM、地面参考信号、近内存加速器 | 2020-2026 | 一项与奖项相关的摘要行以及标题级后续候选人 |
| <a id="JSSC-SF09"></a>[JSSC-SF09](#JSSC-SF09) | 特定于域的非 DNN 计算机 | 非 DNN 负载在 JSSC 中如何用定制硬件论证价值 | Ising、SAT、PDE、基因组学、加密/安全 workload | 不规则计算、延迟、特定于应用程序的数据路径 | 可重配置计算、位串行/数据路径专业化、特定于域的数组 | 2020-2026 | 筛选种子仅；此处未提升为强劲趋势 |
| <a id="JSSC-SF10"></a>[JSSC-SF10](#JSSC-SF10) | 计算成像和传感器前端处理 | image sensor、ToF、LiDAR、event camera 等前端如何做近传感计算 | CMOS 图像传感器、无线图像植入、事件/ToF/LiDAR | 传感器带宽、ADC/读出、边缘预处理 | 像素并行 ADC、植入传感器、本地图像处理 | 2016-2024 | 奖项相关和标题级证据 |
| <a id="JSSC-SF12"></a>[JSSC-SF12](#JSSC-SF12) | 奖项相关RF/毫米波/光子电路背景 | JSSC 官方奖项更多落在 RF、photonic、sensor、ADC 等基础电路，如何约束 accelerator 系统落地 | 毫米波、光子 I/O、ADC、PLL、图像传感器 | PPA、I/O、时钟、测量精度 | DWDM 发射器、光子微环发射器、PLL、 ADC，相控阵 | 2016-2024 | 官方 SSCS 奖项页面已验证；非加速器小领域 |

## 3. 小领域深读

### [JSSC-SF01](#JSSC-SF01)：用于 DNN 推理/训练的硅数据流

研究问题不是“大模型加速”这个大词，而是 CNN/DNN 在真实芯片里怎样把数据搬运、PE array 利用率、片上存储和能效一起闭合。Eyeriss ([JSSC-2017-P0002](../../10_corpus/JSSC/id_index.md#JSSC-2017-P0002)) 是本轮 early anchor，Crossref is-referenced-by-count 为 2531，检索日期 2026-06-27；该数字只能说明 citation signal，不等同于 adoption 或 benchmark 标准化。UNPU ([JSSC-2019-P0006](../../10_corpus/JSSC/id_index.md#JSSC-2019-P0006)) 同时属于 precision route，因为它把 DNN 数据流与 fully variable weight precision 放在同一硅实现里。

当前状态：该子领域在 JSSC 里更像“硅实现证据层”，而不是完整算法路线。后续要读 PDF 才能可靠比较 dataflow、buffering、clock/power、模型覆盖和测量口径。团队线索只可写为 Eyeriss author string、Hoi-Jun Yoo-linked author string；没有做 affiliation disambiguation，不做排名。

### [JSSC-SF02](#JSSC-SF02)：硅中的精度自适应 AI 执行

核心问题是数值格式如何成为芯片级能效/吞吐/精度旋钮。UNPU ([JSSC-2019-P0006](../../10_corpus/JSSC/id_index.md#JSSC-2019-P0006)) 给出 1-16b fully variable weight precision 的 abstract 级证据；7-nm mixed-precision AI chip ([JSSC-2022-P0007](../../10_corpus/JSSC/id_index.md#JSSC-2022-P0007)) 给出 Hybrid-FP8 training、INT4 inference 和 workload-aware throttling 的 abstract 级证据。2025-2026 的 MINOTAUR、Adelia、near-memory variable-precision CNN/Transformer 等行在 screening/evidence matrix 中作为 frontier/title-level 信号保留。

趋势判断只能写成“2019-2026 出现跨年证据”，不能写成某种格式已经成为事实标准。引用和产业/工具链采用仍是 `needs_review` 或 `impact_unverified`。

### [JSSC-SF03](#JSSC-SF03)：用于 AI 数据移动的内存中计算宏

这是本轮 evidence 最稳定的小领域。研究问题是权重/激活搬运能否转移到 memory macro 或 near-memory compute。跨年证据包括：标准 6T SRAM IMC ([JSSC-2018-P0130](../../10_corpus/JSSC/id_index.md#JSSC-2018-P0130))、64-tile charge-domain IMC ([JSSC-2019-P0227](../../10_corpus/JSSC/id_index.md#JSSC-2019-P0227))、Z-PIM ([JSSC-2021-P0164](../../10_corpus/JSSC/id_index.md#JSSC-2021-P0164))、PIMCA ([JSSC-2023-P0188](../../10_corpus/JSSC/id_index.md#JSSC-2023-P0188))、SP-PIM ([JSSC-2024-P0299](../../10_corpus/JSSC/id_index.md#JSSC-2024-P0299)) 和 TensorCIM ([JSSC-2025-P0147](../../10_corpus/JSSC/id_index.md#JSSC-2025-P0147))。deep-read A 对其中 5 篇给出 abstract 级 WHY/HOW/WHAT；Z-PIM 仍是 title/Crossref 级。

可保守写出的路线是：2018-2019 的 SRAM/charge-domain inference macro，逐步连接到 2021 以后 sparsity/variable precision、programmable IMC、on-device learning，以及 2025 的 digital CIM/MCM beyond-NN signal。不能直接声称这些论文构成统一 benchmark 或被产业采用；artifact/code reuse 未找到，benchmark standardization 未验证。

团队线索：Naveen Verma-linked、Joo-Young Kim-linked、Leibo Liu/Shaojun Wei/Shouyi Yin-linked author strings 可作为后续跟踪入口，但仍需要 affiliation/entity audit。

### [JSSC-SF04](#JSSC-SF04)：稀疏性和事件驱动的神经加速

核心问题是稀疏和结构化压缩在芯片中经常被控制流、访存不规则性和 transform overhead 抵消收益。SNAP ([JSSC-2021-P0127](../../10_corpus/JSSC/id_index.md#JSSC-2021-P0127)) 给出 unstructured sparse DNN inference 的 abstract 级证据；STICKER-T ([JSSC-2021-P0233](../../10_corpus/JSSC/id_index.md#JSSC-2021-P0233)) 给出 block-circulant/frequency-domain structured acceleration 的 abstract 级证据。2026 的 DPIM 等 Transformer-in-memory sparse/dense core rows 在 SF05 中作为 frontier title signal 保留。

目前只能写“至少有两条不同稀疏路线”，不能写哪条路线胜出。follow-on citation structure、artifact reuse 和 benchmark 复用都没有完成。

### [JSSC-SF05](#JSSC-SF05)：Transformer 和 LLM 硅内存/注意力瓶颈

JSSC 的 Transformer/LLM 信号集中在 2023-2026 partial：Dynamic Weak Relevances ([JSSC-2023-P0012](../../10_corpus/JSSC/id_index.md#JSSC-2023-P0012))、TranCIM ([JSSC-2023-P0216](../../10_corpus/JSSC/id_index.md#JSSC-2023-P0216))、MulTCIM、CIMFormer、Ayaka、MINOTAUR、C-Transformer、T-REX、Adelia、HyAtt、DPIM 和 variable-precision near-memory CNN/Transformer rows。具体研究问题包括 attention relevance、token-bit sparsity、CIM/Transformer memory mapping、all-on-chip memory、reduced external memory access、dual-mode parallelism 和 sparse/dense core。

这里有跨年多篇 evidence，足以作为 JSSC frontier signal；但 deep-read B 因并发限制未返回，当前保守停在 title/DOI/IEEE/Crossref 级别。2026 年仍 partial，不能用 2026 rows 得出长期影响判断。团队线索包括 Leibo Liu/Shaojun Wei/Shouyi Yin author string、Hoi-Jun Yoo-linked C-Transformer string、Joo-Young Kim-linked Adelia/DPIM strings；都只作为 team_signal，不做排名。

### [JSSC-SF06](#JSSC-SF06)：神经渲染和空间计算处理器

该子领域与用户 3DGS/FPGA/accelerator 方向最直接。JSSC 不是图形/视觉算法会议，所以要关注的是：NeRF、3DGS、SLAM 或 photorealistic rendering 负载怎样被转译成真实处理器/SoC 的数据流、缓存和能耗问题。跨年线索包括 Navion ([JSSC-2019-P0163](../../10_corpus/JSSC/id_index.md#JSSC-2019-P0163)) 和 NeuroSLAM ([JSSC-2021-P0022](../../10_corpus/JSSC/id_index.md#JSSC-2021-P0022)) 作为 SLAM/spatial-computing precursor，MetaVRain ([JSSC-2024-P0022](../../10_corpus/JSSC/id_index.md#JSSC-2024-P0022)) 作为 mobile neural 3-D rendering/NeRF processor，NeRF-Navi ([JSSC-2025-P0002](../../10_corpus/JSSC/id_index.md#JSSC-2025-P0002)) 作为 NeRF path-planning processor，IRIS ([JSSC-2026-P0007](../../10_corpus/JSSC/id_index.md#JSSC-2026-P0007)) 和 Edge 3DGS ([JSSC-2026-P0008](../../10_corpus/JSSC/id_index.md#JSSC-2026-P0008)) 作为 3D Gaussian Splatting processor signals，Space-Mate ([JSSC-2026-P0228](../../10_corpus/JSSC/id_index.md#JSSC-2026-P0228)) 和 NeRF-Learner ([JSSC-2026-P0231](../../10_corpus/JSSC/id_index.md#JSSC-2026-P0231)) 作为 NeRF-SLAM/spatial computing frontier。

可以写出的趋势是：JSSC 已出现从 SLAM/visual-inertial processor 到 NeRF/neural-rendering processor，再到 2026 partial 的 3DGS/NeRF-SLAM processor title signals。不能写成成熟 3DGS 子领域，因为 3DGS rows 主要集中在当前 partial 年份，deep-read C 未返回，影响力仍 `impact_unverified`。

跨会议 hook：CVPR/SIGGRAPH/ICRA 给算法和 workload 定义，MICRO/HPCA/ISCA/ASPLOS 给体系结构对照，FCCM/FPL 给 FPGA prototyping 对照，DAC/ICCAD 给 HLS/EDA/physical closure 对照，ISSCC/VLSI/CICC 给更早或更完整的 silicon presentation 映射。

### [JSSC-SF08](#JSSC-SF08) 和 [JSSC-SF12](#JSSC-SF12)：缩放和电路上下文

MCM DNN accelerator ([JSSC-2020-P0151](../../10_corpus/JSSC/id_index.md#JSSC-2020-P0151)) 是官方 JSSC Best Paper verified row，说明 JSSC 对 multichip AI scaling 和 measured I/O/system integration 有正式认可信号。它不自动证明产业采用，也不能单篇支撑长期趋势；但可作为 chiplet/MCM/near-memory AI scaling 的 anchor。

[JSSC-SF12](#JSSC-SF12) 收录 award-linked RF/mmWave/photonic/ADC/sensor rows。它们不是本项目的加速器主路线，但很重要，因为 accelerator 论文最终落到硅时同样要面对 I/O、clocking、power、sensor front-end 和 measurement rigor。2024 DWDM transmitter、2021 photonic microring transmitter、2022 PLL、2016 ADC 等奖项由 IEEE SSCS 官方页面验证。

## 4. 发展趋势

- 2017-2022：CNN/DNN silicon 从 spatial dataflow、variable precision、charge-domain/6T SRAM IMC、MCM DNN scaling 到 mixed-precision training/inference 逐步展开。证据来自 [JSSC-2017-P0002](../../10_corpus/JSSC/id_index.md#JSSC-2017-P0002)、[JSSC-2018-P0130](../../10_corpus/JSSC/id_index.md#JSSC-2018-P0130)、[JSSC-2019-P0006](../../10_corpus/JSSC/id_index.md#JSSC-2019-P0006)、[JSSC-2019-P0227](../../10_corpus/JSSC/id_index.md#JSSC-2019-P0227)、[JSSC-2020-P0151](../../10_corpus/JSSC/id_index.md#JSSC-2020-P0151)、[JSSC-2022-P0007](../../10_corpus/JSSC/id_index.md#JSSC-2022-P0007)，但影响力审计仍未完成。
- 2018-2025：CIM/PIM line 是 JSSC 内证据最连续的一条：从 SRAM/charge-domain inference macro 到 sparsity-aware PIM、programmable IMC、on-device learning PIM 和 digital CIM/MCM beyond-NN tensor processor。该判断有多篇跨年 evidence 支撑。
- 2023-2026 partial：Transformer/LLM silicon 成为可见 frontier，主题从 attention relevance 和 sparse Transformer CIM 扩展到 all-on-chip memory、external-memory-access reduction、LLM processing unit、analog IMC attention 和 Transformer-in-memory。由于 2026 partial 和 deep-read B 失败，写作时必须保持 `needs_review`。
- 2021-2026 partial：spatial computing line 从 SLAM/visual-inertial processor 到 NeRF/neural rendering，再到 3DGS/NeRF-SLAM processor title signals。该路线与 3DGS/FPGA research hook 直接相关，但成熟度和 adoption 都未验证。

## 5. 方法变化

JSSC 的方法变化体现为“算法名词进入硅实现后，被重新表述为数据搬运、片上存储、数值格式、可测 PPA 和 I/O/系统集成问题”。CNN dataflow 强调 reuse 与 PE utilization；IMC/PIM 把 MVM/weight movement 移到 memory macro 附近；Transformer/LLM rows 把 attention/token movement、external memory 和 on-chip residency 放在中心；NeRF/3DGS rows 把 scene representation、Gaussian/ray processing、cache 和 real-time mobile energy 变成芯片论文问题。

## 6. 缺失来源

- IEEE Xplore 2016-2026 JSSC 全量 article export、abstract、IEEE terms、PDF URL 和 affiliation。
- ISSCC/VLSI/CICC 到 JSSC extended journal version 的结构化映射。
- Transformer/LLM 与 NeRF/3DGS/SLAM 两组 frontier papers 的 PDF-level deep read。
- artifact/code repository、benchmark reuse、citation graph 和 industry/toolchain adoption sources。
- 作者/entity disambiguation和cross-venue团队比较。
