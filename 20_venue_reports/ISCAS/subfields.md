# ISCAS 小领域深读

## 1. 范围和语料库

本次 第二轮 只处理 ISCAS。输入为 `papers.csv` 9237 行和 `awards.csv` 36 行。父 agent 复核后，`papers.csv` 中 9226 行保留为 `accepted_paper`，11 行改为 `front_matter_or_proceedings_volume`，这些行是年度 proceedings/container metadata，不再作为论文参与 deep read 或主题趋势判断。

筛选矩阵覆盖 9273 行，决策分布为：121 行 `deep_read`，7785 行 `index_only`，1356 行 `needs_review`，11 行 `exclude_non_main`。最终 paper evidence matrix 写入 101 篇 paper-level evidence：96 篇来自父 agent 初始 deep_read 清单，另加 5 篇由 award-source 合并后新增的 award-aligned papers。`read_depth` 分布为 58 行 `abstract`、4 行 `full_pdf`、4 行 `abstract+artifact_metadata`、35 行 `title`。2026 年继续标 `partial`。

主要来源是 DBLP/DOI/IEEE DOI metadata、本地 corpus、IEEE CASS / ISCAS 官方页面、ISCAS 2025/2026 program PDF、Crossref citation count、subagent 能访问到的 arXiv/PDF/GitHub metadata。没有完成 IEEE Xplore 批量 abstract、keyword、reference、artifact extraction；因此正文所有影响力判断只写为 preliminary signal。引用、artifact、code 和 adoption 均按 `2026-06-27` 检索日期记录在 evidence matrix。

## 2. 小领域映射

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="ISCAS-SF01"></a>[ISCAS-SF01](#ISCAS-SF01) | CIM/PIM 和以神经形态记忆为中心的 AI | 把 ML/SNN/linear algebra 的计算靠近存储或器件阵列，降低数据搬运和能耗 | SpMV、在线学习、SNN、ViT、点云 VFE、通用 IMC | 记忆墙、ADC/数组非理想、状态更新、精确缩放 | RRAM/忆阻器交叉开关、SRAM-CIM、SOT-MRAM、数字 CIM、事件驱动 SNN | 2016-2026 | venue_provisional |
| <a id="ISCAS-SF02"></a>[ISCAS-SF02](#ISCAS-SF02) | FPGA/HLS 加速器映射和硬件基准测试 | 把 CNN/vision/point-cloud 和 memory workloads 映射到可复现 FPGA 系统 | ResNet、QNN、CNN、光学流、DDR4、点云 ICP | 资源/时序收敛、内存流量、实时 I/O | 位切片、向量稀疏性、HLS DSE、生成器、模拟器 | 2017-2026 | cross_venue_candidate |
| <a id="ISCAS-SF03"></a>[ISCAS-SF03](#ISCAS-SF03) | 开源 EDA/硬件基准测试 artifact | 用公开数据、RTL/IP、PDK、framework 改善硬件设计可复现性 | PCB 路由、VHDL 生成、位置算术、DPD、CGRA、PDK | 基准覆盖范围、可重用 artifact、验证 | 数据集生成、开源仓库、RTL 生成器、基准框架 | 2023-2026 | venue_provisional |
| <a id="ISCAS-SF04"></a>[ISCAS-SF04](#ISCAS-SF04) | Transformer/LLM 稀疏性和低精度边缘加速 | 降低 Transformer/LLM inference 的 compute 和 memory cost | 稀疏 Transformer、二进制 Transformer、LLM 量化、边缘 LLM | 稀疏性开销、激活精度、非线性函数逼近 | N:M 稀疏性、二值化、混合 INT4/INT8、位分层量化 | 2022-2026 | venue_provisional |
| <a id="ISCAS-SF05"></a>[ISCAS-SF05](#ISCAS-SF05) | Vision Transformer 边缘推理加速器 | 把 ViT/MobileViT 放进 edge FPGA/resource constraints | ViT、MobileViT | 注意力/MLP 数据流、边缘资源限制 | 头级管道、可配置计算 | 2023-2024 | insufficient_evidence 用于稳定趋势 |
| <a id="ISCAS-SF06"></a>[ISCAS-SF06](#ISCAS-SF06) | Mamba/SSM内存状态加速器 | 加速 state-space model 的 state update 和 memory movement | Mamba、Video Mamba、Mamba-2 | 状态内存、循环数据流、流式切片 | 内存高效型 SSM、冗余消除、流式平铺 FPGA | 2025-2026 | 前沿 |
| <a id="ISCAS-SF07"></a>[ISCAS-SF07](#ISCAS-SF07) | LLM KV/状态内存、CIM/PIM 和 NoC 加速 | 处理 KV cache、LoRA、LLM state 和多核数据流 | LLM 推理、KV 缓存、LoRA、尖峰Transformer | 缓存移动、PIM/NoC 流量、热/数据流映射 | PIM/CIM、KV 压缩/卸载、NoC/拓扑协同设计 | 2024-2026 | 前沿、2026 部分重载 |
| <a id="ISCAS-SF08"></a>[ISCAS-SF08](#ISCAS-SF08) | LLM 解码和运行时加速 | 通过 runtime scheduling 降低 token generation latency | 推测解码、块扩散 LLM | 草稿/验证同步、激活重用 | 异步多设备解码、块扩散重用 | 2025-2026 | insufficient_evidence |
| <a id="ISCAS-SF09"></a>[ISCAS-SF09](#ISCAS-SF09) | NeRF/神经渲染采样加速 | 降低 NeRF/neural rendering 的 ray sampling、MLP 和 volume-rendering cost | NeRF,神经渲染 | 采样成本、占用访问、体积渲染 | 自适应门控、密度估计采样、ConvNeRF 硬件渲染器 | 2024-2026 | 新兴 cross_venue_candidate |
| <a id="ISCAS-SF10"></a>[ISCAS-SF10](#ISCAS-SF10) | 3DGS 场景表示、渲染和压缩 | 让 3DGS/4DGS 在实时、能耗和压缩约束下运行 | 3DGS-SLAM、Neural-3DGS、HyperGS、 GS 视频压缩 | 排序、Alpha 混合、缓存重用、压缩artifact | 对角线馈送、Alpha 重用、体素缓存、分层排序、扩散增强 | 2025-2026 | 新兴 cross_venue_candidate |
| <a id="ISCAS-SF11"></a>[ISCAS-SF11](#ISCAS-SF11) | 空间视觉、SLAM 传感和机器人加速器 | 把 stereo/depth/SLAM front-end 放进低功耗 sensor/SoC/FPGA | 立体匹配、NeuroSLAM、EKF-SLAM、 ORB、LiDAR SLAM | 传感器读数、定位延迟、特征提取 | 焦平面校正、VCO 空间单元、FPGA SoC、ORB/LiDAR 加速器 | 2016-2026 | venue_provisional |
| <a id="ISCAS-SF12"></a>[ISCAS-SF12](#ISCAS-SF12) | 边缘传感、生物医学、可穿戴和触觉系统 | 端侧 sensing 到本地 compute / closed-loop system 的电路系统实现 | 可植入、触觉、图像传感器、可穿戴、触觉 | 功率、读出、闭环延迟、外形尺寸 | CMOS 传感器、BCC、神经调节 SoC、压缩二次采样 | 2018-2025 | venue_provisional |
| <a id="ISCAS-SF13"></a>[ISCAS-SF13](#ISCAS-SF13) | DSP/通信硬件架构 | 通信 workload 的低能耗 detector/architecture 实现 | CF MIMO | 矩阵运算、定点、探测器吞吐量 | EVD/CORDIC/重用/管道 | 2025 | 单行上下文 |
| <a id="ISCAS-SF14"></a>[ISCAS-SF14](#ISCAS-SF14) | 边缘系统的模拟/电源/数据转换器基板 | ADC/RF/power/clocking 对端侧系统的底层约束 | SAR ADC, DC-DC、图像传感器读出、模拟基带、分频器 | 噪声、瞬态响应、动态范围、锁定范围 | 准无源 NS SAR、SIDO SC DC-DC、LOFIC 读出、注入锁定 | 2018-2025 | venue_provisional 作为基底 |
| <a id="ISCAS-SF15"></a>[ISCAS-SF15](#ISCAS-SF15) | CAS 理论和电力系统奖励边界 | 记录 ISCAS broad CAS 的 award boundary，避免混入 accelerator lineage | 微电网，电力系统稳定性 | 控制稳定性，可再生能源渗透 | 同步动态，稳定流域度量，优化 | 2025 | negative_boundary |
| <a id="ISCAS-SF16"></a>[ISCAS-SF16](#ISCAS-SF16) | 工业物联网安全/工具边界 | 记录 security/tooling 作为边界而非 accelerator 主线 | IIoT 渗透测试 | 自动化和验证 | Nessus/PostgreSQL/Metasploit 工作流程 | 2025 | negative_boundary |

## 3. 小领域深读

### [ISCAS-SF01](#ISCAS-SF01)。 CIM/PIM 和以神经形态记忆为中心的 AI

研究问题： 这一组论文处理的是 memory-centric compute：把向量乘、在线学习、SNN 状态更新、Transformer/ViT 或点云特征编码放到 RRAM、SRAM-CIM、SOT-MRAM 或其他近存/存内结构中，减少数据搬运。它不是单一模型路线，而是一组围绕 memory wall 和器件/阵列约束展开的问题。

背景： 2016-2018 的证据包括 [ISCAS-2016-P0127](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0127)、[ISCAS-2016-P0485](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0485)、[ISCAS-2016-P0544](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0544)、[ISCAS-2017-P0444](../../10_corpus/ISCAS/id_index.md#ISCAS-2017-P0444)、[ISCAS-2017-P0715](../../10_corpus/ISCAS/id_index.md#ISCAS-2017-P0715)、[ISCAS-2018-P0310](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0310)、[ISCAS-2018-P0987](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0987)。这些行覆盖 sparse SpMV、RRAM online learning、analog memristor online training、event-driven random backpropagation、Ziksa on-chip learning、ReRAM ECC 和 memristor SNN on-device learning。

Current state in ISCAS: 到 2025-2026，证据转向 digital CIM macro 和更具体的 AI workload：[ISCAS-2025-P1126](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P1126) 连接 differential frame convolution 与 SNN；[ISCAS-2026-P0219](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0219) 把 RRAM digital CIM 指向 BF16 x 1-bit ViT；[ISCAS-2026-P0524](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0524) 把 CIM 用到 large-scale point-cloud VFE；[ISCAS-2026-P0649](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0649) 处理 linear-decay SNN state update；[ISCAS-2026-P0809](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0809) 处理 SRAM-CIM multi-precision AI inference；[ISCAS-2026-P0884](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0884) 转向 SOT-MRAM spiking CIM；[ISCAS-2026-P0925](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0925) 尝试 general-purpose IMC。

方法谱系： sparse matrix mapping and online learning -> analog/on-chip memristor learning -> SRAM in/near-memory arithmetic -> digital CIM for ViT, point clouds, SNN state update and general IMC. 这条线有跨年份支撑，但 2026 paper 仍是 partial frontier，不能写成已验证长期影响。

代表论文：[ISCAS-2016-P0127](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0127)、[ISCAS-2016-P0544](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0544)、[ISCAS-2017-P0444](../../10_corpus/ISCAS/id_index.md#ISCAS-2017-P0444)、[ISCAS-2020-P0784](../../10_corpus/ISCAS/id_index.md#ISCAS-2020-P0784)、[ISCAS-2025-P1126](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P1126)、[ISCAS-2026-P0219](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0219)、[ISCAS-2026-P0524](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0524)、[ISCAS-2026-P0925](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0925)。

团队线索： evidence matrix 只记录 author-string 信号，如 NTU/Hao Yu、Technion/Kvatinsky、UC Irvine + Intel、RIT/Sandia/Kudithipudi、Peking University、CityU HK/Basu、SUSTech/Xidian、USTC、ICT CAS + CUHK。这些不是团队排名，也没有做 affiliation timeline 消歧。

workload/artifact 信号： SpMV、PCA、ViT、point-cloud VFE、SNN state update、multi-precision AI inference 有 benchmark 信号；artifact/code 复用大多没有证据，保留 `artifact_unverified` 或 `none found`。

开放问题： 需要把 analog/memristor CIM、digital SRAM-CIM、PIM for LLM、SNN neuromorphic 分开做 PDF 级阅读；需要跨 ISSCC/JSSC/VLSI/architecture venues 对照，避免把 ISCAS 的 title-level frontier 误写成全领域主线。

### [ISCAS-SF02](#ISCAS-SF02)。 FPGA/HLS 加速器映射和硬件基准

研究问题： 这一组看的是算法到 FPGA/HLS/benchmark 的映射，不是传统 FPGA venue 的完整谱系。核心问题是如何在 resource/timing/memory constraints 下完成可复现的 accelerator implementation。

Background and current state: [ISCAS-2017-P0370](../../10_corpus/ISCAS/id_index.md#ISCAS-2017-P0370) 是 end-to-end ResNet on Arria-10 的早期锚点；[ISCAS-2019-P0060](../../10_corpus/ISCAS/id_index.md#ISCAS-2019-P0060) 和 [ISCAS-2019-P0082](../../10_corpus/ISCAS/id_index.md#ISCAS-2019-P0082) 分别处理 bit-slicing QNN 和 vector sparsity CNN；[ISCAS-2019-P0193](../../10_corpus/ISCAS/id_index.md#ISCAS-2019-P0193) 是 CNN processor generator / DSE 信号；[ISCAS-2022-P0068](../../10_corpus/ISCAS/id_index.md#ISCAS-2022-P0068) 是 optical-flow HLS DSE；[ISCAS-2022-P0489](../../10_corpus/ISCAS/id_index.md#ISCAS-2022-P0489) 是 real-time HD video CNN benchmark framework；[ISCAS-2025-P0290](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0290) 转向 data-center FPGA DDR4 memory performance；[ISCAS-2026-P0892](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0892) 和 [ISCAS-2026-P0984](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0984) 分别是 systolic CNN simulator 和 point-cloud ICP system。

方法谱系：端到端 CNN 映射 -> 低精度/稀疏数据流 -> 生成器/DSE -> HLS/视频基准 -> 内存微基准 -> 模拟器和点云前沿。

代表论文：[ISCAS-2017-P0370](../../10_corpus/ISCAS/id_index.md#ISCAS-2017-P0370)、[ISCAS-2019-P0060](../../10_corpus/ISCAS/id_index.md#ISCAS-2019-P0060)、[ISCAS-2019-P0082](../../10_corpus/ISCAS/id_index.md#ISCAS-2019-P0082)、[ISCAS-2022-P0068](../../10_corpus/ISCAS/id_index.md#ISCAS-2022-P0068)、[ISCAS-2022-P0489](../../10_corpus/ISCAS/id_index.md#ISCAS-2022-P0489)、[ISCAS-2025-P0290](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0290)、[ISCAS-2026-P0984](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0984)。

团队线索：Arizona State/Seo-Cao-Vrudhula、NYCU/Tian-Sheuan Chang、Tennessee Tech/Hasan、 LIP6/Sorbonne/CNRS/Analog Devices、Politecnico di Milano/Zoni、TU Dresden/Goehringer、HKUST/HKU/Wei Zhang 仅是作者字符串信号。

workload/artifact 信号：ResNet/ImageNet、QNN、矢量稀疏性、光流、720p 视频、DDR4 流量、KITTI/ICP。 MulMapper/FaBCNN/MoSim 代码未验证；报告应将它们视为工具/基准候选者，而不是可重用的 artifact。

开放问题： 需要和 FCCM/FPL/FPT/FPGA 做 cross-venue comparison；需要 PDF 级确认 resource utilization、timing closure、evaluation platform 和 code availability。

### [ISCAS-SF03](#ISCAS-SF03)。开源 EDA/硬件基准测试 artifact

研究问题： 这组不是单一 accelerator workload，而是硬件设计可复现性问题：公开数据集、RTL/IP、benchmark framework、PDK 和 code repository 是否能让后续研究可比较。

Current state: 证据从 2023 开始集中出现。[ISCAS-2023-P0105](../../10_corpus/ISCAS/id_index.md#ISCAS-2023-P0105) 是 open-source CGRA / SkyWater 130 nm / agile hardware flow；[ISCAS-2023-P0307](../../10_corpus/ISCAS/id_index.md#ISCAS-2023-P0307) 是 PDPU open-source posit dot-product unit；[ISCAS-2024-P0350](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0350) 是 systolic tensor array RTL generator；[ISCAS-2024-P0734](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0734) 是 OpenDPD；[ISCAS-2025-P0594](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0594) 是 PCBRouteNet，并且在 `awards.csv` 中同时连接 YP finalist 和 ISCAS 2025 Conference Best Paper second place；[ISCAS-2026-P0923](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0923) 是 SVVHD LLM-to-VHDL benchmark；[ISCAS-2026-P0311](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0311) 是 GT2N 2 nm nanosheet PDK benchmark signal。

Artifact signals: subagent 找到并记录了 `qleenju/PDPU`、`lab-emi/OpenDPD`、`GN-KK233/SVVHD`、`CharonRen/PCBRouteNet-Simulation-Environment-for-PCB-Routing-Dataset`。这些只说明 code/repo exists，状态是 `runnable_unchecked`，没有运行或复现。

代表论文：[ISCAS-2023-P0307](../../10_corpus/ISCAS/id_index.md#ISCAS-2023-P0307)、[ISCAS-2024-P0734](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0734)、[ISCAS-2025-P0594](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0594)、[ISCAS-2026-P0923](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0923)、[ISCAS-2026-P0311](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0311)。

团队线索：Stanford/Raina、Nanjing/Zhongfeng Wang、TU Delft/lab-emi、UESTC、SCUT/深圳理工大学、Georgia Tech/Synopsys 仅是作者字符串信号。

开放问题： 需要从 PDF 或官方 artifact 页确认 repository 是否由作者 claim；需要做 benchmark adoption audit，尤其是 OpenDPD 和 PCBRouteNet 是否被后续论文作为 baseline/dataset。

### [ISCAS-SF04](#ISCAS-SF04) 至 SF08。 Transformer、LLM、Mamba/SSM 和运行时加速

研究问题： 这些小领域共同面对 Transformer/LLM/SSM 的 compute/memory/state 问题，但机制不同，不能合并成一个大 topic。SF04 侧重 sparsity / low precision / edge Transformer；SF05 是 ViT edge inference；SF06 是 Mamba/SSM state；SF07 是 LLM KV/state memory、CIM/PIM 和 NoC；SF08 是 decoding/runtime。

证据：

- SF04: [ISCAS-2022-P0163](../../10_corpus/ISCAS/id_index.md#ISCAS-2022-P0163) 是 sparse Transformer FPGA accelerator，subagent 读到 full PDF；[ISCAS-2024-P0274](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0274) 是 BETA binary Transformer accelerator，full PDF；[ISCAS-2024-P0147](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0147)、[ISCAS-2024-P0218](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0218)、[ISCAS-2025-P0456](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0456)、[ISCAS-2025-P0461](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0461)、[ISCAS-2025-P1001](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P1001)、[ISCAS-2026-P0461](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0461)、[ISCAS-2026-P0976](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0976)、[ISCAS-2026-P0980](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0980) 构成 low-precision / quantization / edge LLM frontier。
- SF05: [ISCAS-2023-P0388](../../10_corpus/ISCAS/id_index.md#ISCAS-2023-P0388) ViTA 有 full PDF，[ISCAS-2024-P0239](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0239) 是 MobileViT accelerator title-level follow-up。
- SF06: [ISCAS-2025-P0236](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0236)、[ISCAS-2025-P0673](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0673)、[ISCAS-2026-P0123](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0123) 支撑 Mamba/SSM memory-state frontier。
- SF07: [ISCAS-2024-P0066](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0066)、[ISCAS-2026-P0124](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0124)、[ISCAS-2026-P0262](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0262)、[ISCAS-2026-P0050](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0050)、[ISCAS-2026-P0077](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0077)、[ISCAS-2026-P0228](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0228)、[ISCAS-2026-P0652](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0652)、[ISCAS-2026-P0678](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0678)、[ISCAS-2026-P0748](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0748)、[ISCAS-2026-P0804](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0804)、[ISCAS-2026-P0920](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0920) 支撑 KV/cache/CIM/PIM/NoC frontier。
- SF08: [ISCAS-2025-P0652](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0652) AMUSD 有 full PDF 和 code claimed，[ISCAS-2026-P0548](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0548) 是 block diffusion LLM processor title-level row。

Trends: 这里能支撑的趋势是“2022 sparse Transformer FPGA -> 2024 binary/ViT edge accelerators -> 2025-2026 LLM/Mamba/KV/PIM/NoC frontier”，但 2026 evidence 多为 title/abstract-level partial rows，不能推断长期 adoption。

团队线索：Zhongfeng Wang/NJU/SYSU、Seok-Bum Ko/Hao Zhang、Hoi-Jun Yoo/KAIST、Tian-Sheuan Chang、Hyuk-Jae Lee、Xuanyao Fong 相关集群、Westlake/Sa​​wan-Yang、IIT Madras/USC/Intel Labs、Bradley McDanel 仅是作者字符串信号。

开放问题： 需要 PDF 级区分真正硬件实现、模拟架构、runtime system、algorithm compression；需要统一比较 benchmarks、models、precision、latency/energy 指标。

### [ISCAS-SF09](#ISCAS-SF09) 和 [ISCAS-SF10](#ISCAS-SF10)。 NeRF、神经渲染和 3DGS

研究问题： ISCAS 里与用户方向最直接的信号来自 2024-2026：NeRF/neural rendering 的 sampling/volume-rendering cost，以及 3DGS 的 sorting、alpha blending、voxel cache、compression 和 SLAM integration。

SF09 证据：[ISCAS-2024-P0204](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0204) GNeRF、[ISCAS-2024-P0229](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0229) 密度估计采样、[ISCAS-2024-P0689](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0689) ConvNeRF 硬件体积渲染器、[ISCAS-2026-P0028](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0028) Stereo-NeRF、[ISCAS-2026-P0269](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0269) SCAR。

SF10证据：[ISCAS-2025-P0322](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0322) AquaNeRF、[ISCAS-2025-P0371](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0371) ScatterSplatting、[ISCAS-2025-P0420](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0420) 3DGS-SLAM加速器、[ISCAS-2025-P0513](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0513) Neural-3DGS处理器、[ISCAS-2025-P0703](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0703) HyperGS、[ISCAS-2026-P0208](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0208) Res-P4DGS、[ISCAS-2026-P0419](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0419)时空高斯泼溅系统、[ISCAS-2026-P0714](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0714) GFix、[ISCAS-2026-P0767](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0767) 融合 3DGS 解决方案分析、[ISCAS-2026-P0999](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0999) 双希尔伯特视频 GS 压缩。

方法谱系：2024 年 NeRF 采样/门控和硬件体绘制 -> 2025 年直接 3DGS-SLAM / Neural-3DGS / HyperGS 处理器 -> 2026 年部分有关立体声 NeRF、稀疏感知神经渲染、时空 GS、压缩和分析的行。

团队线索：上海交通大学、上海科技大学/Xin Lou/Pingqiang Zhou、KAIST/Hoi-Jun Yoo、清华大学、布里斯托尔、USTC、浙江大学、圣克拉拉/华为仅是作者字符串信号。

workload/artifact 信号：指标包括 FLOP、PSNR、FPS、mJ/帧、排序/光栅化、压缩质量。没有验证代码/artifact 的重用。 3DGS 系列是真实且直接相关的，但仍然年轻；在推广到新兴信号之外之前，应该与图形、建筑、FPGA 和机器人venue进行交叉检查。

### [ISCAS-SF11](#ISCAS-SF11)。空间视觉、SLAM 传感和机器人加速器

研究问题： 这一组连接 3D/spatial workloads 的前端：stereo matching、NeuroSLAM、EKF-SLAM、ORB feature extraction、2D-LiDAR scan matching。它提供 3DGS/robotics 方向的 sensor/SLAM substrate，而不是直接等同于 3DGS accelerator。

证据：[ISCAS-2016-P0323](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0323) 立体匹配 CMOS 图像传感器加速器；[ISCAS-2020-P0563](../../10_corpus/ISCAS/id_index.md#ISCAS-2020-P0563) NeuroSLAM / 空间导航 VCO；[ISCAS-2024-P0277](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0277) EKF-SLAM FPGA SoC 现场演示；[ISCAS-2026-P0472](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0472) FPGA ORB特征提取；[ISCAS-2026-P0701](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0701) 2D-LiDAR SLAM SoC现场演示。

开放问题： 需要 PDF 区分 algorithm demo、FPGA prototype、measured chip/SoC。2026 rows 仍是 partial frontier。

### [ISCAS-SF12](#ISCAS-SF12) 至 SF16。获奖背景和边界

ISCAS 是 broad CAS venue，award-backed rows 不能全部纳入 accelerator 主线。第二轮将它们分为 sensing/biomedical/wearable、DSP/communications、analog/power/data converter、power-system boundary 和 security/tooling boundary。

SF12 evidence: [ISCAS-2018-P0944](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0944), [ISCAS-2024-P0098](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0098), [ISCAS-2025-P0188](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0188), [ISCAS-2025-P0248](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0248), [ISCAS-2025-P0278](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0278), [ISCAS-2025-P0342](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0342), [ISCAS-2025-P0873](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0873), [ISCAS-2025-P1083](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P1083)。它们支撑 edge sensing / biomedical / wearable / tactile context。

SF13 evidence: [ISCAS-2025-P0148](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0148) 是 CF MIMO detector YP finalist，作为 DSP/communications hardware architecture context。

SF14 evidence: [ISCAS-2018-P0261](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0261), [ISCAS-2025-P0515](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0515), [ISCAS-2025-P0536](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0536), [ISCAS-2025-P0720](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0720), [ISCAS-2025-P0901](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0901), [ISCAS-2025-P0981](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0981)。这些行说明端侧系统受 ADC、电源、image-sensor readout、analog baseband、RF clocking 约束。

SF15 evidence: [ISCAS-2025-P1044](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P1044) 是 ISCAS 2025 Conference Best Paper first place，但它是 microgrid stability，不应纳入 accelerator lineage。

SF16 evidence: [ISCAS-2025-P0830](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0830) 是 Industrial IoT penetration testing WiCAS finalist，是 security/tooling boundary。

Award caveats: 2018 Student Best Paper 三行已按 IEEE CASS official page 修正为 [ISCAS-2018-P0944](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0944)、[ISCAS-2018-P0634](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0634)、[ISCAS-2018-P0261](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0261)。2025 Conference Best Paper / Best Demo rows 可按 official `conference-awards` page 和本地 awards.csv 写为 verified。2025 WiCAS/YP standalone pages是 finalist 表；父 agent没有把 conference-awards 图片页中未能机器解析的 WiCAS/YP certificate细节改写成 winner事实。2026 conference paper-award winner list 仍是 normal partial。

## 4. 发展趋势

1. CIM/neuromorphic 从早期 memristor/RRAM training 和 sparse linear algebra，转向 digital CIM、ViT、point-cloud VFE、SNN state update 和 general-purpose IMC。证据集合：[ISCAS-2016-P0127](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0127), [ISCAS-2016-P0485](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0485), [ISCAS-2016-P0544](../../10_corpus/ISCAS/id_index.md#ISCAS-2016-P0544), [ISCAS-2017-P0715](../../10_corpus/ISCAS/id_index.md#ISCAS-2017-P0715), [ISCAS-2020-P0784](../../10_corpus/ISCAS/id_index.md#ISCAS-2020-P0784), [ISCAS-2025-P1126](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P1126), [ISCAS-2026-P0219](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0219), [ISCAS-2026-P0524](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0524), [ISCAS-2026-P0925](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0925)。
2. FPGA/HLS 在 ISCAS 中更多作为 method bridge 和 benchmark/source of constraints，而不是完整 FPGA community 主线。证据集合：[ISCAS-2017-P0370](../../10_corpus/ISCAS/id_index.md#ISCAS-2017-P0370), [ISCAS-2019-P0060](../../10_corpus/ISCAS/id_index.md#ISCAS-2019-P0060), [ISCAS-2019-P0082](../../10_corpus/ISCAS/id_index.md#ISCAS-2019-P0082), [ISCAS-2022-P0068](../../10_corpus/ISCAS/id_index.md#ISCAS-2022-P0068), [ISCAS-2022-P0489](../../10_corpus/ISCAS/id_index.md#ISCAS-2022-P0489), [ISCAS-2025-P0290](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0290), [ISCAS-2026-P0984](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0984)。
3. Transformer/LLM/Mamba 从 2022 sparse Transformer FPGA，走向 2024 binary/ViT edge acceleration，再到 2025-2026 LLM quantization、Mamba/SSM、KV/cache/CIM/NoC frontier。证据集合：[ISCAS-2022-P0163](../../10_corpus/ISCAS/id_index.md#ISCAS-2022-P0163), [ISCAS-2023-P0388](../../10_corpus/ISCAS/id_index.md#ISCAS-2023-P0388), [ISCAS-2024-P0274](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0274), [ISCAS-2025-P0236](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0236), [ISCAS-2025-P0456](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0456), [ISCAS-2025-P0673](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0673), [ISCAS-2026-P0123](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0123), [ISCAS-2026-P0124](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0124), [ISCAS-2026-P0262](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0262)。
4. NeRF/3DGS 是 2024-2026 的 emerging cluster，不是成熟长期谱系。证据集合：[ISCAS-2024-P0204](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0204), [ISCAS-2024-P0229](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0229), [ISCAS-2024-P0689](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0689), [ISCAS-2025-P0420](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0420), [ISCAS-2025-P0513](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0513), [ISCAS-2025-P0703](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0703), [ISCAS-2026-P0269](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0269), [ISCAS-2026-P0714](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0714), [ISCAS-2026-P0999](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0999)。
5. Open-source artifact / benchmark signal 在 2023-2026 更清晰，尤其是 OpenDPD、PDPU、PCBRouteNet、SVVHD。证据集合：[ISCAS-2023-P0307](../../10_corpus/ISCAS/id_index.md#ISCAS-2023-P0307), [ISCAS-2024-P0734](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0734), [ISCAS-2025-P0594](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0594), [ISCAS-2026-P0923](../../10_corpus/ISCAS/id_index.md#ISCAS-2026-P0923)。
6. Award-backed sensing/analog/power rows 说明 ISCAS 对端侧系统 substrate 的覆盖很强，但这些 rows 多数不是 accelerator lineage。证据集合：[ISCAS-2025-P0248](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0248), [ISCAS-2025-P0342](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0342), [ISCAS-2025-P0515](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0515), [ISCAS-2025-P0536](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0536), [ISCAS-2025-P0720](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0720), [ISCAS-2025-P0901](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0901), [ISCAS-2025-P0981](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0981)。

## 5. 方法将

早期证据更多是 device/circuit-level prototype、FPGA-specific mapping 和 sensing front-end。2022 以后，paper titles 和 subagent abstract evidence 显示评价对象更靠近 workload：Transformer、ViT、Mamba、LLM KV/cache、3DGS、point-cloud VFE、PCB routing dataset、LLM-HDL benchmark。方法也从单个电路/模块，逐步转向 algorithm-hardware co-design、runtime scheduling、benchmark/framework 和 open-source artifact。

这个变化不能解释为 ISCAS “转型为 accelerator conference”。更准确的说法是：CAS venue 的 circuit/system substrate、EDA/tooling 和 edge workload 正在被 AI/3D/spatial/LLM 负载牵引，形成若干 venue-local frontier signals。

## 6. 缺少来源

- 2016-2026 每年官方 final program 的结构化 session、abstract、keyword 表。
- IEEE Xplore 批量 abstract、keyword、references、PDF metadata。
- 2016、2017、2019-2024 的完整 ISCAS Student Best Paper / Best Demo winner archive。
- 2026 会后 ISCAS 会议论文奖获奖者名单。
- artifact/code 的官方链接、可运行性和复用证据。
- Cross-venue cluster comparison 与 author/institution/entity disambiguation。
