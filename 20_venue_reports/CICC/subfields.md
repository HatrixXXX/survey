# CICC 小领域小领域深读

## 1. 范围和语料库

Venue：`CICC`
写入后的语料库：`1232` paper rows和 `19` 奖励行。筛选矩阵具有 `1251` 行：`70` `deep_read`、`1136` `index_only`、`24` `exclude_non_main` 和 `21` `needs_review`。证据矩阵有 `61` paper rows。

证据深度有意保守，但现在是混合的：`4` 行是 `full_pdf`，`25` 是 `abstract`，`2` 是 `pdf_section`，`1` 是 `abstract; artifact_docs`，`1` 是 `artifact_docs`，`5` 是`abstract_metadata`、`15` 为 `title_metadata`，`8` 仍为 `title`。使用 Crossref 和/或 Semantic Scholar 对 `2026-06-27` 记录 `61` evidence rows的 `59` 的引文信号；引用计数只是初步的影响信号，而不是采用证明。当未检查采用、artifact 重用、基准标准化或引用结构时，`impact_unverified` 仍然是默认值。

## 2. 小领域映射

| subfield_id | 子领域 | 核心问题 | 活跃年数 | deep_read rows | 证据状态 |
| --- | --- | --- | --- | --- | --- |
| <a id="CICC-SF01"></a>[CICC-SF01](#CICC-SF01) | CIM、模拟 AI 和 LLM 以内存为中心的执行 | AI MAC/attention/LLM 计算如何在处理精度、稀疏性、鲁棒性和数据的同时更接近内存运动。 | 2017-2026 | 13 | full_pdf/抽象/元数据混合；adoption_unverified |
| <a id="CICC-SF02"></a>[CICC-SF02](#CICC-SF02) | 神经形态、循环注意力和优化加速器 | 非标准 AI 或优化 workload 如何映射到电路级加速器。 | 2019-2020 | 3 | 标题/本地元数据； impact_unverified，除非另有说明 |
| <a id="CICC-SF03"></a>[CICC-SF03](#CICC-SF03) | 用于 CNN、Transformer 和 LLM 令牌 workload 的边缘/域 AI 处理器 | 完整处理器如何处理边缘 CNN、Transformer、微调、SLM/LLM 令牌管道、精度格式、稀疏性和压缩。 | 2018-2026 | 6 | 包括 full_pdf/artifact_docs 信号；adoption_unverified |
| <a id="CICC-SF04"></a>[CICC-SF04](#CICC-SF04) | HLS 到芯片 RISC-V、eFPGA、云 FPGA 和小芯片集成 | 可重新配置逻辑、HLS 设计的处理器、小芯片和云部署约束如何出现在 CICC 芯片端点上。 | 2020-2026 | 7 | 一个 full_pdf 加上摘要/元数据；artifact 未 verified |
| <a id="CICC-SF05"></a>[CICC-SF05](#CICC-SF05) | 实时 3D 视觉、神经渲染、BEV 和机器人加速器 | 空间感知和渲染 workload 如何满足实时和能源限制。 | 2022-2026 | 8 | 一种神经渲染 full_pdf 加上元数据组合；稳定谱系未 verified |
| <a id="CICC-SF06"></a>[CICC-SF06](#CICC-SF06) | 计算负载供电和自适应时钟/功率 SoC | 电源和时钟/功率控制如何处理低于 1V 高电流、HBM 和边缘 SoC 瞬态约束。 | 2017-2026 | 7 | 摘要/元数据混合；adoption_unverified |
| <a id="CICC-SF07"></a>[CICC-SF07](#CICC-SF07) | 有线、RF/mmWave/THz 和时钟电路 | 高速链路、RF/THz 系统、PA 和时钟如何处理损耗、线性、抖动和集成约束。 | 2019-2026 | 7 | 摘要/索引证据；adoption_unverified |
| <a id="CICC-SF08"></a>[CICC-SF08](#CICC-SF08) | 生物医学、可穿戴、身体通道和神经接口 | 在严格的功率限制下如何感知或驱动微弱的生理、辐射、身体通道和刺激信号。 | 2019-2026 | 4 | 摘要/索引证据；clinical_adoption_unverified |
| <a id="CICC-SF09"></a>[CICC-SF09](#CICC-SF09) | PQC、ZKP、安全处理器和侧通道弹性硬件 | 加密和 secure-AI workload 如何映射到低功耗或侧通道感知芯片。 | 2022-2026 | 4 | 摘要/索引证据；artifact/adoption_unverified |
| <a id="CICC-SF10"></a>[CICC-SF10](#CICC-SF10) | 数据转换器和 CIM 基准测试方法 | 转换器/量化问题和基准可比性如何影响混合信号和 CIM claim。 | 2019-2022 | 2 | 摘要/artifact 文档加上冲突边界 |

## 3. 小领域深读

### [CICC-SF01](#CICC-SF01)：CIM、模拟 AI 和 LLM 以内存为中心的执行

研究问题：将 AI MAC 移至更接近内存的位置，同时处理精度，稀疏性、转换器成本、PVT 稳健性和数据移动。本地证据是 2017-2026 标题级序列：模拟内存中 DNN ([CICC-2017-P0070](../../10_corpus/CICC/id_index.md#CICC-2017-P0070))、Secure-RRAM ([CICC-2021-P0088](../../10_corpus/CICC/id_index.md#CICC-2021-P0088))、DCT-RAM ([CICC-2022-P0070](../../10_corpus/CICC/id_index.md#CICC-2022-P0070))、Quartet ([CICC-2024-P0137](../../10_corpus/CICC/id_index.md#CICC-2024-P0137))、CIM-utilization-aware 映射 ([CICC-2025-P0041](../../10_corpus/CICC/id_index.md#CICC-2025-P0041))、 FlashAttention/DCIM ([CICC-2025-P0066](../../10_corpus/CICC/id_index.md#CICC-2025-P0066))、用于边缘 LLM 的一次性 FP-CIM ([CICC-2025-P0096](../../10_corpus/CICC/id_index.md#CICC-2025-P0096))、模拟 AI Transformer加速器 ([CICC-2025-P0126](../../10_corpus/CICC/id_index.md#CICC-2025-P0126)) 和 2026 BERT/D2CIM/TOKCIM 行。

当前状态：词汇表从通用 DNN/MVM 和宏观级 CIM 转向命名序列 workload：FlashAttention、FlashMLA、KV-cache、BERT、SoftMax 和 LLM 解码。现在有几行有抽象或完整的 PDF 证据，但这仍然不是采用的证明。

团队线索：本地报告和subagent提及 Le Ye/Tianyu Jia、hongwu Jiang、Hao Yu 和 UM/SKL-AMSV 相关 FP-CIM 作品的作者字符串重叠。这些仍然是 `needs_review`；没有排名。

开放问题：提取剩余的 IEEE PDF 以了解精度模式、宏/系统边界、转换器开销和实际 workload 列表。 [CICC-2022-P0068](../../10_corpus/CICC/id_index.md#CICC-2022-P0068) 有一个公共 UIUC-IMC 仓库和引用信号，但标准化尚未得到验证。

### [CICC-SF02](#CICC-SF02)：神经形态、循环注意力和优化加速器

研究问题：将非标准 AI 和优化 workload 映射到电路加速器中。证据虽小但很明显：2048 个神经元 SNN 加速器 ([CICC-2019-P0031](../../10_corpus/CICC/id_index.md#CICC-2019-P0031))、用于组合优化的 CMOS 退火 ([CICC-2019-P0093](../../10_corpus/CICC/id_index.md#CICC-2019-P0093)) 和用于循环注意力关键字识别的 KeyRAM ([CICC-2020-P0073](../../10_corpus/CICC/id_index.md#CICC-2020-P0073))。

当前状态：这些行位于 CIM 和 AI 处理器附近，但在没有 PDF 证据的情况下，不应将它们折叠到 Transformer/LLM-CIM 行中。它们是边界信号。

### [CICC-SF03](#CICC-SF03)：用于 CNN、Transformer 和 LLM 令牌 workload 的边缘/域 AI 处理器

研究问题：在片上内存、精度、能量和压缩限制下为边缘 CNN、Transformers、LLM 微调和令牌管道构建完整的处理器。本地序列从 BinarEye ([CICC-2018-P0065](../../10_corpus/CICC/id_index.md#CICC-2018-P0065)) 运行到稀疏自适应 CNN/Transformer 处理 ([CICC-2023-P0089](../../10_corpus/CICC/id_index.md#CICC-2023-P0089))、BF16 LLM 微调 ([CICC-2025-P0049](../../10_corpus/CICC/id_index.md#CICC-2025-P0049))、边缘 SLM 解码 ([CICC-2026-P0128](../../10_corpus/CICC/id_index.md#CICC-2026-P0128))、HyperV RISC-V 向量边缘 AI ([CICC-2026-P0154](../../10_corpus/CICC/id_index.md#CICC-2026-P0154)) 和 TACC 混合格式 LLM 加速 ([CICC-2026-P0166](../../10_corpus/CICC/id_index.md#CICC-2026-P0166))。

当前状态：这是更清晰的用户相关 CICC 挂钩之一，因为行命名 workload 和数字格式。 BinarEye 有完整的 PDF 证据，2026 边缘 SLM 解码器有公开幻灯片，但完整处理器、宏和可编程矢量基线之间的划分仍然需要更多 PDF 审查。

### [CICC-SF04](#CICC-SF04)：HLS 到硅 RISC-V、eFPGA、云 FPGA 和小芯片集成

研究问题：了解可重构逻辑和小芯片集成如何显示为测量的硅，而不仅仅是 CAD 或 FPGA 方法。证据包括 HL5 ([CICC-2020-P0071](../../10_corpus/CICC/id_index.md#CICC-2020-P0071))、连接到 Stratix 10 FPGA ([CICC-2021-P0024](../../10_corpus/CICC/id_index.md#CICC-2021-P0024))、CIFER 和 DECADES 缓存一致性/eFPGA SoC ([CICC-2023-P0101](../../10_corpus/CICC/id_index.md#CICC-2023-P0101)/P0104) 的 AIB 兼容小芯片、云 FPGA 部署([CICC-2023-P0120](../../10_corpus/CICC/id_index.md#CICC-2023-P0120))、合成 eFPGA 自定义指令 RISC-V SoC ([CICC-2025-P0074](../../10_corpus/CICC/id_index.md#CICC-2025-P0074)) 以及 Occamy/开源小芯片讨论 ([CICC-2026-P0169](../../10_corpus/CICC/id_index.md#CICC-2026-P0169))。

当前状态：这是 FPGA/HLS/chiplet 工作的cross-venue 挂钩。 HL5有open-PDF证据； DECADES 有abstract-level证据； Occamy 目前仅得到邻近 arXiv 生态系统证据的支持。这还不是 artifact 重用的证据。

### [CICC-SF05](#CICC-SF05)：实时 3D 视觉、神经渲染、BEV 和机器人加速器

研究问题：在帧速率、能量、稀疏性和内存限制下处理立体、渲染、光流、BEV/点云感知、定位和 SLAM。证据包括 FPGA 立体块 PatchMatch ([CICC-2022-P0033](../../10_corpus/CICC/id_index.md#CICC-2022-P0033))、FPGA 机器人定位 ([CICC-2022-P0064](../../10_corpus/CICC/id_index.md#CICC-2022-P0064))、FPGA ([CICC-2024-P0007](../../10_corpus/CICC/id_index.md#CICC-2024-P0007)) 上的神经体积渲染、BEVFusion 和点云处理器 ([CICC-2024-P0038](../../10_corpus/CICC/id_index.md#CICC-2024-P0038)/P0052)、BEE-SLAM ([CICC-2024-P0122](../../10_corpus/CICC/id_index.md#CICC-2024-P0122))、光流加速([CICC-2026-P0056](../../10_corpus/CICC/id_index.md#CICC-2026-P0056)) 和 4 个小芯片渲染处理器 ([CICC-2026-P0081](../../10_corpus/CICC/id_index.md#CICC-2026-P0081))。

当前状态：这与神经渲染和机器人技术相关，但覆盖范围仍然很薄。 2024 年神经体积渲染加速器具有关于 FPGA 实现的 open-PDF 证据； 2026 小芯片渲染行仍然是 title_metadata，不应假定为 3DGS。

### [CICC-SF06](#CICC-SF06)：计算负载供电和自适应时钟/电源 SoC

研究问题：提供高电流或隔离电源轨，同时限制处理器、HBM 和边缘系统的下降、恢复时间、密度和电源引起的抖动。证据涵盖集成磁芯隔离转换器 ([CICC-2017-P0065](../../10_corpus/CICC/id_index.md#CICC-2017-P0065))、SLiMO ([CICC-2023-P0116](../../10_corpus/CICC/id_index.md#CICC-2023-P0116))、2024 隔离 DC-DC 转换 ([CICC-2024-P0037](../../10_corpus/CICC/id_index.md#CICC-2024-P0037))、100A 48-60V 至 1V 转换 ([CICC-2025-P0018](../../10_corpus/CICC/id_index.md#CICC-2025-P0018))、2026 年最佳论文 NLDO 西格玛转换器([CICC-2026-P0062](../../10_corpus/CICC/id_index.md#CICC-2026-P0062))、HBM 抖动缓解 ([CICC-2026-P0097](../../10_corpus/CICC/id_index.md#CICC-2026-P0097)) 和 Unicorn 时钟/电源 SoC ([CICC-2026-P0171](../../10_corpus/CICC/id_index.md#CICC-2026-P0171))。

当前状态：标题和选定的摘要越来越多地编码计算负载约束：70A/20ns、2.5A/20ns、HBM 下降/稳定和 RL 适应控制。 2026 年最佳论文权力行有官方奖项和摘要级证据，但影响力和行业采用率未经审核。

### [CICC-SF07](#CICC-SF07)：有线、RF/mmWave/THz 和时钟电路

研究问题：在损耗、线性、相位噪声、抖动、封装和能量限制下维持高链路速率、RF/mmWave/THz 操作以及时钟质量。 Deep_read 行包括 2019 年基于 ADC 的 NRZ/PAM4 接收器奖行 ([CICC-2019-P0018](../../10_corpus/CICC/id_index.md#CICC-2019-P0018))、Doherty PA 奖行 ([CICC-2019-P0011](../../10_corpus/CICC/id_index.md#CICC-2019-P0011))、太赫兹成像邀请奖行 ([CICC-2019-P0102](../../10_corpus/CICC/id_index.md#CICC-2019-P0102))、224Gb/s DSP/高损耗收发器 ([CICC-2024-P0127](../../10_corpus/CICC/id_index.md#CICC-2024-P0127)) [CICC-2025-P0040](../../10_corpus/CICC/id_index.md#CICC-2025-P0040))、60GHz 相控阵收发器 ([CICC-2025-P0028](../../10_corpus/CICC/id_index.md#CICC-2025-P0028)) 和 2026 年环 PLL 奖 ([CICC-2026-P0029](../../10_corpus/CICC/id_index.md#CICC-2026-P0029))。

目前状态：这个子领域是 CICC 作为巡回赛venue的中心。对于这个项目，它主要作为加速器 I/O 和时钟的硅约束源。记录了引文信号，但没有提出部署或标准化 claim。

### [CICC-SF08](#CICC-SF08)：生物医学、可穿戴、身体通道和神经接口

研究问题：将微弱的生理、辐射、身体通道和神经信号转换为功率和效率预算紧张的数字或刺激接口。证据包括 2019 年 NF-DPG 心率传感器奖行 ([CICC-2019-P0029](../../10_corpus/CICC/id_index.md#CICC-2019-P0029))、2019 年可穿戴剂量计最佳论文奖行 ([CICC-2019-P0074](../../10_corpus/CICC/id_index.md#CICC-2019-P0074))、2026 年脑通道接收器奖行 ([CICC-2026-P0032](../../10_corpus/CICC/id_index.md#CICC-2026-P0032)) 和 2026 年绝热电荷跟踪刺激器奖行 ([CICC-2026-P0119](../../10_corpus/CICC/id_index.md#CICC-2026-P0119))。

当前状态：2019 年和 2026 年的奖励证据有来源支持，所选行现在有摘要/索引证据。不检查临床或产品采用情况。

### [CICC-SF09](#CICC-SF09)：PQC、ZKP、安全处理器和侧通道弹性硬件

研究问题：将加密和 secure-AI workload 映射到低功耗芯片中，同时控制侧通道泄漏和模块化算术成本。证据包括 Saber LWR 加速 ([CICC-2022-P0030](../../10_corpus/CICC/id_index.md#CICC-2022-P0030))、具有侧通道分析/对策的 Kyber ([CICC-2024-P0055](../../10_corpus/CICC/id_index.md#CICC-2024-P0055))、2026 ZKP 处理器 ([CICC-2026-P0059](../../10_corpus/CICC/id_index.md#CICC-2026-P0059)) 以及基于 Transformer 的安全生成 AI 处理器 ([CICC-2026-P0060](../../10_corpus/CICC/id_index.md#CICC-2026-P0060))。

当前状态：路线是抽象/标题支持的并且与加速器安全性相关，但 artifact/代码和基准重用未 verified。

### [CICC-SF10](#CICC-SF10)：数据转换器和 CIM 基准测试方法

研究问题：将转换、量化和基准可比性视为对系统 claim 的约束。 [CICC-2019-P0001](../../10_corpus/CICC/id_index.md#CICC-2019-P0001) 是与奖项相关的 VCO/delta-sigma ADC 行，但 DOI 元数据与官方奖项页面之间存在 79.7dB/97.7dB SNDR 冲突。 [CICC-2022-P0068](../../10_corpus/CICC/id_index.md#CICC-2022-P0068) 是 CIM 基准测试候选者。

目前状态：这个子领域应该保持警惕。 [CICC-2019-P0001](../../10_corpus/CICC/id_index.md#CICC-2019-P0001) 仍然是源冲突边界，直到 SNDR 不匹配得到解决。 [CICC-2022-P0068](../../10_corpus/CICC/id_index.md#CICC-2022-P0068) 通过公开仓库拥有 artifact 文档证据，但下游基准标准化未 verified。

## 4. 发展趋势

- 2017 年至 2026 年间，CIM/analog-AI 标题从 DNN 和 SRAM/RRAM 宏转向 Transformer/LLM 特定术语。证据：[CICC-2017-P0070](../../10_corpus/CICC/id_index.md#CICC-2017-P0070)、[CICC-2022-P0070](../../10_corpus/CICC/id_index.md#CICC-2022-P0070)、[CICC-2024-P0137](../../10_corpus/CICC/id_index.md#CICC-2024-P0137)、[CICC-2025-P0066](../../10_corpus/CICC/id_index.md#CICC-2025-P0066)、 [CICC-2026-P0145](../../10_corpus/CICC/id_index.md#CICC-2026-P0145)、[CICC-2026-P0168](../../10_corpus/CICC/id_index.md#CICC-2026-P0168)。状态：`needs_review`；混合标题/摘要/PDF 证据，采用未验证。
- Edge AI 处理器标题从二进制 CNN 和稀疏自适应 CNN/Transformer 工作转向 BF16 微调和令牌级 SLM/LLM 处理器。证据：[CICC-2018-P0065](../../10_corpus/CICC/id_index.md#CICC-2018-P0065)、[CICC-2023-P0089](../../10_corpus/CICC/id_index.md#CICC-2023-P0089)、[CICC-2025-P0049](../../10_corpus/CICC/id_index.md#CICC-2025-P0049)、[CICC-2026-P0128](../../10_corpus/CICC/id_index.md#CICC-2026-P0128)、[CICC-2026-P0166](../../10_corpus/CICC/id_index.md#CICC-2026-P0166)。状态：`needs_review`；混合标题/摘要/人工证据，采用未验证。
- 电力传输标题越来越多地提及计算负载和内存接口约束。证据：[CICC-2025-P0018](../../10_corpus/CICC/id_index.md#CICC-2025-P0018)、[CICC-2026-P0062](../../10_corpus/CICC/id_index.md#CICC-2026-P0062)、[CICC-2026-P0097](../../10_corpus/CICC/id_index.md#CICC-2026-P0097)、[CICC-2026-P0171](../../10_corpus/CICC/id_index.md#CICC-2026-P0171)，以及早期的隔离转换器锚点。状态：`needs_review` 影响。
- 3D 视觉/神经渲染/机器人行很直接，但覆盖率较低。证据：[CICC-2022-P0033](../../10_corpus/CICC/id_index.md#CICC-2022-P0033)、[CICC-2024-P0007](../../10_corpus/CICC/id_index.md#CICC-2024-P0007)、[CICC-2026-P0056](../../10_corpus/CICC/id_index.md#CICC-2026-P0056)、[CICC-2026-P0081](../../10_corpus/CICC/id_index.md#CICC-2026-P0081)。状态：cross-venue挂机，CICC主线不稳定； [CICC-2024-P0007](../../10_corpus/CICC/id_index.md#CICC-2024-P0007) 有 open-PDF FPGA 证据。
- 在当前语料库中，奖项仅适用于 2019 年和 2026 年。 2020-2025 年覆盖范围标记仍为 `needs_review`。

## 5. 方法将

| 从 | 更改为 | 证据 | 地位 |
| --- | --- | --- | --- |
| 模拟/RRAM/SRAM CIM 原语 | 名为 LLM/Transformer CIM 内核 | [CICC-2017-P0070](../../10_corpus/CICC/id_index.md#CICC-2017-P0070)； [CICC-2025-P0066](../../10_corpus/CICC/id_index.md#CICC-2025-P0066); [CICC-2026-P0145](../../10_corpus/CICC/id_index.md#CICC-2026-P0145)； [CICC-2026-P0168](../../10_corpus/CICC/id_index.md#CICC-2026-P0168) | 标题级 |
| 二进制/量化 CNN 处理器 | BF16、令牌级 SLM/LLM、混合格式 LLM 处理器 | [CICC-2018-P0065](../../10_corpus/CICC/id_index.md#CICC-2018-P0065)； [CICC-2025-P0049](../../10_corpus/CICC/id_index.md#CICC-2025-P0049); [CICC-2026-P0128](../../10_corpus/CICC/id_index.md#CICC-2026-P0128)； [CICC-2026-P0166](../../10_corpus/CICC/id_index.md#CICC-2026-P0166) | 标题级 |
| FPGA/HLS 方法 | 测量 RISC-V/eFPGA/chiplet 芯片端点 | [CICC-2020-P0071](../../10_corpus/CICC/id_index.md#CICC-2020-P0071)； [CICC-2023-P0101](../../10_corpus/CICC/id_index.md#CICC-2023-P0101); [CICC-2023-P0104](../../10_corpus/CICC/id_index.md#CICC-2023-P0104)； [CICC-2025-P0074](../../10_corpus/CICC/id_index.md#CICC-2025-P0074) | artifact_unverified |
| 点转换器 | 计算/HBM 瞬态和抖动感知供电 | [CICC-2025-P0018](../../10_corpus/CICC/id_index.md#CICC-2025-P0018)； [CICC-2026-P0062](../../10_corpus/CICC/id_index.md#CICC-2026-P0062); [CICC-2026-P0097](../../10_corpus/CICC/id_index.md#CICC-2026-P0097) | adoption_unverified |
| 安全原语/PQC | ZKP 和安全 GenAI 处理器 | [CICC-2022-P0030](../../10_corpus/CICC/id_index.md#CICC-2022-P0030)； [CICC-2024-P0055](../../10_corpus/CICC/id_index.md#CICC-2024-P0055); [CICC-2026-P0059](../../10_corpus/CICC/id_index.md#CICC-2026-P0059)； [CICC-2026-P0060](../../10_corpus/CICC/id_index.md#CICC-2026-P0060) | artifact_unverified |

## 6. 缺少来源

- Reliable 2016 CICC 接受的论文/会议论文集标题列表。
- IEEE Xplore 摘要、PDF、作者单位以及 deep_read 行的 artifact/代码链接。
- 2020-2025 年官方获奖者或proceedings奖项页面。
- 完整 2017-2026 计划 PDF 页面级会话提取和 Crossref 匹配。
- CIM、有线、电源和传感器行的cross-venue ISSCC/JSSC/VLSI/CICC 相同芯片系列。
