# ASP-DAC 小领域深读

## 1. 范围与语料

- Venue：`ASP-DAC`
- 语料库：`papers.csv` 2016-2026 年有 1660 行； `awards.csv` 有 31 行。
- 筛选：`ASP-DAC_screening_matrix.csv` 覆盖 1691 行：`{'index_only': 1133, 'needs_review': 444, 'deep_read': 114}`。
- 证据矩阵：`ASP-DAC_paper_evidence_matrix.csv` 有 54 个深读/evidence rows。
- 来源依据：DBLP/DOI 行、ASP-DAC 奖项档案、ASP-DAC 2025/2026 官方计划页面、2026 年 6 月 27 日检查的选定 GitHub/arXiv/OpenAlex 信号。
- 边界：2026年获奖结果由SIGDA电子新闻留在`needs_review`； 2026 年 6 月 27 日检查时，ASP-DAC 官方奖项档案没有 2026 行。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="ASPDAC-SF01"></a>[ASPDAC-SF01](#ASPDAC-SF01) | HLS 缓冲区、时序和内存限制下的 DSE 数据流 | FIFO 大小、路径时序、片上缓冲区容量、HBM 分配 | HLS 内核； FPGA 数据流加速器； HBM 内存管理器 | FIFO 大小、路径时序、片上缓冲区容量、HBM 分配 | HLS DSE、图融合、MLIR、时序估计、内存分配 | 2022, 2025, 2026 | venue_provisional |
| <a id="ASPDAC-SF02"></a>[ASPDAC-SF02](#ASPDAC-SF02) | LLM 辅助 RTL/HLS 生成和断言基准测试 | 功能正确性、度量推理、基准公平性、验证覆盖率 | RTL、Verilog、HLS C/C++、断言 | 功能正确性、度量推理、基准公平性、验证覆盖率 | LLM 工作流程、静态分析、基准数据集、断言生成 | 2024, 2025, 2026 | venue_provisional |
| <a id="ASPDAC-SF03"></a>[ASPDAC-SF03](#ASPDAC-SF03) | DL 模型到 FPGA 编译和架构探索 | 模型到 FPGA 编译、架构搜索、资源/延迟权衡 | DNN，Transformer，深度学习加速器 | 模型到 FPGA 编译、架构搜索、资源/延迟权衡 | 覆盖编译，CAD-循环架构探索，DSE | 2016, 2025, 2026 | venue_provisional |
| <a id="ASPDAC-SF04"></a>[ASPDAC-SF04](#ASPDAC-SF04) | 布局、可布线性、时序和 3D PDN 约束下的实现收敛优化 | 线长、可布线性、时序、IR drop、全流程 PPA | FPGA 布局、全局布局、F2F 3D IC PDN | 线长、可布线性、时序、IR drop、全流程 PPA | GPU/可微优化、分析放置、PDN 建模 | 2016, 2020, 2021, 2022, 2024, 2026 | venue_provisional |
| <a id="ASPDAC-SF05"></a>[ASPDAC-SF05](#ASPDAC-SF05) | 内存和边缘限制下的 3DGS/NeRF 和点云加速 | 渲染/训练内存流量、边缘延迟、量化、光栅化不平衡 | 3D 高斯溅射、NeRF、点云、神经渲染 | 渲染/训练内存流量、边缘延迟、量化、光栅化不平衡 | FPGA/GPU 加速、脉冲编码、ReRAM、剪枝、算法系统协同设计 | 2024, 2025, 2026 | venue_provisional |
| <a id="ASPDAC-SF06"></a>[ASPDAC-SF06](#ASPDAC-SF06) | PIM/CIM 和图、NN 和 LLM workload 的近内存映射 | 数据移动、ADC/DAC 开销、带宽、非易失性内存变化 | 图处理、DNN、Transformer、LLM 解码、KV 缓存 | 数据移动、ADC/DAC 开销、带宽、非易失性内存变化 | ReRAM 交叉开关、DRAM-PIM、CiM、单片 3D 内存、数据分配 | 2017, 2019, 2021, 2022, 2024, 2025, 2026 | venue_provisional |
| <a id="ASPDAC-SF07"></a>[ASPDAC-SF07](#ASPDAC-SF07) | 低功耗、近似和非易失性 AI 架构 | 能源、延迟、精度/资源扩展、设备变化 | NN 推理、光学 NN、FFT、能量收集处理器、神经形态系统 | 能源、延迟、精度/资源扩展、设备变化 | 近似、布尔最小化、光学 FFT、频率缩放、一级突触 | 2017, 2019, 2020, 2023, 2026 | venue_provisional |
| <a id="ASPDAC-SF08"></a>[ASPDAC-SF08](#ASPDAC-SF08) | EDA/网表、模型和新兴存储器的安全性/可靠性 | 逆向工程、模型提取风险、变异、可靠性 | 网表、EDA ML 模型、skyrmion/赛道存储器、物理验证 | 逆向工程、模型提取风险、变异、可靠性 | 逆向工程、提取攻击、变化感知数据管理 | 2018, 2023 | venue_provisional |
| <a id="ASPDAC-SF09"></a>[ASPDAC-SF09](#ASPDAC-SF09) | 电路仿真和模拟/混合信号数值加速 | 求解器运行时间和鲁棒性 | 稀疏线性系统，电路仿真 | 求解器运行时间和鲁棒性 | 随机 GMRES、并行 LU 分解 | 2025 | insufficient_evidence |

## 3. 小领域深读

### [ASPDAC-SF01](#ASPDAC-SF01)。 HLS 缓冲区、时序和内存限制下的 DSE 数据流

- 研究问题：HLS/数据流设计经常在 FIFO 大小、时序估计、内存分配和片外/片内通信方面失败，即使计算内核看起来不错。
- 背景：[ASPDAC-2016-P0078](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2016-P0078)是早期FPGA CNN DSE anchor； 2026 年增加了更严格的实施封闭集群。
- 本 venue 的当前状态：`FIFOAdvisor`、`HLS-Timer`、`UltraMalloc` 和 `FESTAL` 涵盖缓冲区大小、时序估计、HBM 感知内存分配和 MLIR/数据流图融合。
- 方法谱系：DSE/资源建模 -> 数据流 FIFO 搜索 -> 路径级时序预测 -> MLIR/graph-fusion 综合。
- 代表论文：{reps('[ASPDAC-SF01](#ASPDAC-SF01)')}。
- 团队线索：佐治亚理工学院/UCLA HLS、BUPT/SYSU 计时、复旦/Wai-Shing Luk 内存管理、PKU/Yun Liang 数据流综合。这些只是作者字符串信号。
- workload/artifact 信号：FIFOAdvisor 有代码； FESTAL 和 HLS-Timer 需要 PDF/artifact 检查； UltraMalloc 没有经过验证的仓库。
- 开放问题：这些 2026 年工具是否成为可重复使用的基准，以及它们报告的基准集是否涵盖不规则的加速器 workload。

### [ASPDAC-SF02](#ASPDAC-SF02)。 LLM 辅助 RTL/HLS 生成和断言基准测试

- 研究问题：LLM 硬件生成需要公平的基准、度量推理、断言生成和形式工具反馈，而不仅仅是一次性的 Verilog 片段。
- 背景：`RTLLM`是主要基准anchor。它在 RTLLM2.0/OpenLLM-RTL、RTL-Coder 和 VFlow 中有一个公开仓库和强大的后续用途。
- 本 venue 的当前状态：2024-2026 行从 RTL 生成基准转移到 HLS 生成、度量推理、断言生成、模块级挖掘和代理工作流程。
- 方法谱系：`RTLLM` -> `AssertLLM` / `MetRex` / HLS 代码基准 -> `AssertMiner`、`SuperSAGA`、`VFlow`。
- 代表论文：{reps('[ASPDAC-SF02](#ASPDAC-SF02)')}。
- 团队线索：HKUST/谢志耀/张宏策、布朗/Sherief Reda、ICT CAS/Huawei Li、SJTU/EIT 宁波/谢菲尔德。没有暗示排名。
- workload/artifact 信号：RTLLM、AssertLLM 和 MetRex 具有代码/数据集信号； VFlow 和 SuperSAGA 需要 artifact 审查。
- 开放问题：污染控制、基准新鲜度、形式等效覆盖率以及 PPA claim 是否能通过完整的工具流程评估。

### [ASPDAC-SF03](#ASPDAC-SF03)。 DL 模型到 FPGA 编译和架构探索

- 研究问题：将 DNN/Transformer workload 映射到 FPGA 需要编译器和架构决策，而不仅仅是加速器数据路径。
- 本 venue当前状态：2025 行包括基于覆盖的 FPGA 编译和 DL 加速的架构探索。
- 方法谱系：一侧的模型翻译器/指令生成器/覆盖编译器；另一方面是 VTR/Koios 风格的架构探索。
- 代表论文：{reps('[ASPDAC-SF03](#ASPDAC-SF03)')}。
- 团队线索：Fudan/NTU/Kun Wang 和 HKUST(GZ)/Yuzhe Ma/Dongsheng Zuo 作者字符串信号。
- workload/artifact 信号：Xilinx FPGA 推理和 CAD 循环评估可见，但代码可用性大多未 verified。
- 开放问题：模型覆盖率、可重现的编译器堆栈以及与 FPGA/FCCM/FPL 工作的cross-venue比较。

### [ASPDAC-SF04](#ASPDAC-SF04)。布局、可路由性、时序和 3D PDN 约束下的实现闭合优化

- 研究问题：可扩展的布局/路由/PDN 方法必须改进运行时间而不损失全流程 PPA 质量。
- 背景：ASP-DAC 奖励行已经包括虚拟填充、路由树构建、FineMap 和 SPIRAL。第二波添加了 DREAMPlaceFPGA、C3PO 和 DPO-3D 作为以闭包为中心的证据。
- 此venue的当前状态：GPU/可微优化用于 LUT 映射、全局布局和 3D IC PDN/可路由性权衡。
- 方法谱系：分析/开放布局 -> GPU 并行 LUT 映射 -> 商业质量可微布局 -> F2F 3D IC PDN/可布线性协同优化。
- 代表论文：{reps('[ASPDAC-SF04](#ASPDAC-SF04)')}。
- 团队线索：UT Austin/Pan、CUHK/Bei Yu/Evangeline Young、NVIDIA EDA 研究、佐治亚理工学院/Sung Kyu Lim、USC/Tsung-Yi Ho。这些是团队线索，而不是排名。
- workload/artifact 信号：DREAMPlaceFPGA 具有公共代码； FineMap有CULS候选代码； C3PO 和 DPO-3D 需要 artifact/产品采用检查。
- 开放问题：商业工具比较是否可重复，以及 2026 年奖励信号是否得到官方 ASP-DAC 档案确认。

### [ASPDAC-SF05](#ASPDAC-SF05)。内存和边缘约束下的 3DGS/NeRF 和点云加速

- 研究问题：神经渲染和 3D 感知 workload 对内存流量、光栅化平衡、边缘延迟和训练反向传播造成压力。
- 背景：TreeNet 是 2021 年获奖行，使用点云嵌入进行路由树构建。直接渲染线将于 2024-2026 年出现，包括 Booth-NeRF、GSNorm、Spiking-NeRF、BOA-3DGS、BalanceGS 和 HERO。
- 本 venue 的当前状态：ASP-DAC 有直接 3DGS/NeRF 信号，但它们是最近的且是venue-local的。
- 方法谱系：点云嵌入 -> FPGA NeRF 推理 -> 3DGS 渲染归一化 -> 3DGS 训练内存优化 -> NeRF 量化。
- 代表论文：{reps('[ASPDAC-SF05](#ASPDAC-SF05)')}。
- 团队线索：PKU、Sungkyunkwan、Guohao Dai 组和几个点云加速器作者集群。没有进行entity disambiguation。
- workload/artifact 信号：官方program abstract支持 GSNorm/BOA/BalanceGS/Spiking-NeRF。文物状态大多仍未知。
- 开放问题：这些论文是否成为 3DGS 训练/渲染加速器的基线，以及它们与 DAC/ICCAD/FPGA venue工作相比如何。

### [ASPDAC-SF06](#ASPDAC-SF06)。 PIM/CIM 和图、NN 和 LLM workload 的近内存映射

- 研究问题：图形处理、NN 推理/训练、Transformer/LLM 解码和 KV 缓存 workload 受到数据移动和内存带宽的限制。
- 背景：GraphSAR、基于连接的 PIM 和最佳数据分配是 PIM 的 ASP-DAC 奖项锚。 2024-2026 添加了面向 Transformer/LLM 的 PIM/CIM 行。
- 本 venue 的当前状态：产品线从 ReRAM 图形处理和交叉开关引擎转移到 Transformer 令牌修剪、异构 CiM、DRAM-PIM LLM 解码和单片 3D KV 缓存。
- 方法谱系：ReRAM 图 PIM -> 电阻交叉开关 PIM -> 图数据分配 -> 动态令牌修剪 PIM -> CiM Transformer -> LLM 解码/KV-cache 近内存处理。
- 代表论文：{reps('[ASPDAC-SF06](#ASPDAC-SF06)')}。
- 团队线索：清华/杨华中/刘永攀、李海/陈怡然、姜丽、竹内/三泽、塔贾纳·罗辛/纳拉亚南信号。
- workload/artifact 信号：大多数行都有 DOI/官方abstract 证据，但没有可运行的 artifact 状态。
- 开放问题：模拟/CIM 非理想报告、基准可比性以及 LLM/PIM 行是否在 ASP-DAC 之外被引用。

### [ASPDAC-SF07](#ASPDAC-SF07)。低功耗、近似和非易失性 AI 架构

- 研究问题：能量和延迟限制迫使在精度、设备行为和算法映射方面进行权衡。
- 本 venue 的当前状态：Spendthrift、神经形态一级精度、布尔最小化神经网络、光学 NN FFT、近似 FFT 和 ViDA 显示了减少能量/延迟的不同Pathways。
- 代表论文：{reps('[ASPDAC-SF07](#ASPDAC-SF07)')}。
- 开放问题：哪些路线保持活跃，哪些路线变得孤立奖励示例。

### [ASPDAC-SF08](#ASPDAC-SF08)。 EDA/网表、模型和新兴存储器的安全/可靠性

- 研究问题：设计 artifact 和 EDA 模型创建攻击、逆向工程和可靠性表面。
- 本 venue 的当前状态：网表逆向工程、skyrmion 赛道变化管理和 EDA 中的 ML 模型提取提供了安全/可靠性线程。
- 代表论文：{reps('[ASPDAC-SF08](#ASPDAC-SF08)')}。
- 开放问题：这条线如何连接到LLM辅助的EDA安全和cross-venue硬件安全工作。

### [ASPDAC-SF09](#ASPDAC-SF09)。电路仿真和模拟/混合信号数值加速

- 研究问题：模拟/电路仿真花费时间进行稀疏线性求解。
- 当前状态：2025 年随机 GMRES 最佳论文为电路仿真提供了数值方法锚点。
- 代表论文：{reps('[ASPDAC-SF09](#ASPDAC-SF09)')}。
- 开放问题：引用/采用以及集成到模拟器工具链中未 verified。

## 4. 发展趋势

- HLS/dataflow 闭包于 2026 年通过 [ASPDAC-2026-P0002](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0002)、[ASPDAC-2026-P0053](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0053)、[ASPDAC-2026-P0116](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0116) 和 [ASPDAC-2026-P0168](../../10_corpus/ASP-DAC/id_index.md#ASPDAC-2026-P0168) 变得可见。这支持了venue-local趋势，而不是全球分类推广。
- LLM-for-hardware-design 在 2024-2026 年期间扩展：`RTLLM`、`AssertLLM`、`MetRex`、HLS 代码生成基准、`AssertMiner`、`SuperSAGA` 和 `VFlow` 覆盖 RTL、 HLS，度量推理、断言和代理工作流程。
- 神经渲染/3DGS 从稀疏的直接证据转移到最近的集群：`Booth-NeRF`、`GSNorm`、`Spiking-NeRF`、`BOA-3DGS`、`BalanceGS` 和 `HERO`。该信号是最近的，仍需要cross-venue比较。
- PIM/CIM 从图形/ReRAM 和交叉开关引擎转向 Transformer 和 LLM/KV 缓存 workload：`GraphSAR`、`Connection-based PIM`、`Optimal Data Allocation`、`PRIMATE`、`Transformer Hetero-CiM`、`BLADE` 和 `M3DKV` 支持venue-local趋势。
- 实现收敛越来越多地使用 GPU/可微分方法：`DREAMPlaceFPGA`、`FineMap`、`C3PO` 和 `DPO-3D` 提供跨年度证据。

## 5. 方法变化

- 早期的 ASP-DAC 代表行通常是单问题 EDA 或设备/系统设计论文：布尔图、网表逆向工程、能量收集控制、神经形态精度和新兴的存储器可靠性。
- 2019-2022 添加了 PIM 和图形处理锚点，以及光学/近似神经网络路线。
- 2024-2026 将许多论文转向面向工具链的 artifact：开放基准、HLS/DSE 框架、GPU/可微分闭包引擎以及具有可重现钩子的官方program abstract页面。
- 评估对象也发生了变化：较旧的行经常暴露此语料库中的 DOI/标题级证据；最近的行通常包括program abstract、候选代码、基准名称或 GitHub 链接。

## 6. 缺失来源

- 2016-2024 年结构化官方期末课程/曲目/摘要提取。
- 2025 年 10 年 MIP 官方标题。
- 官方 2026 年 ASP-DAC 奖项存档行。
- 批量 ACM/IEEE 摘要、关键字、PDF 链接和 artifact 元数据。
- 完整 2026 年接受论文 ID 至 DBLP DOI 所有 215 行的crosswalk。
- 所有子领域的专用 artifact 执行和引用/采用审核。
