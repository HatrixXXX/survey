# FPT 小领域深读

## 小领域图谱

| subfield_id | 本地标签 | 核心问题 | 活跃年数 | 代表论文 ID | 证据状态 |
|---|---|---|---|---|---|
| <a id="FPT-SF01"></a>[FPT-SF01](#FPT-SF01) | HLS/CAD/DSE 和工具流定位 | 如何把算法、二进制或 HLS 描述变成可预测、可搜索、可维护的 FPGA 实现 | 2016, 2017, 2021, 2024 | [FPT-2016-P0001](../../10_corpus/FPT/id_index.md#FPT-2016-P0001)； [FPT-2017-P0013](../../10_corpus/FPT/id_index.md#FPT-2017-P0013); [FPT-2021-P0042](../../10_corpus/FPT/id_index.md#FPT-2021-P0042) | mixed: FLOWER 有 PDF；2016/2017 多数是 title/metadata |
| <a id="FPT-SF02"></a>[FPT-SF02](#FPT-SF02) | 内存、HBM、NoC 和数据移动 | 容量、带宽、NoC 争用和数据搬运怎样限制吞吐 | 2016, 2022, 2024 | [FPT-2016-P0004](../../10_corpus/FPT/id_index.md#FPT-2016-P0004)； [FPT-2022-P0008](../../10_corpus/FPT/id_index.md#FPT-2022-P0008); [FPT-2024-P0010](../../10_corpus/FPT/id_index.md#FPT-2024-P0010)； [FPT-2024-P0029](../../10_corpus/FPT/id_index.md#FPT-2024-P0029) | mixed: MTJ 有 PDF；HBM/GraphNoC 需补全文 |
| <a id="FPT-SF03"></a>[FPT-SF03](#FPT-SF03) | 数据流叠加和空间结构 | 如何用 spatial/dataflow 结构暴露并行性，同时控制调度、分区和通信成本 | 2018, 2019, 2021 | [FPT-2018-P0024](../../10_corpus/FPT/id_index.md#FPT-2018-P0024); [FPT-2019-P0017](../../10_corpus/FPT/id_index.md#FPT-2019-P0017); [FPT-2021-P0042](../../10_corpus/FPT/id_index.md#FPT-2021-P0042) | DaCO/FLOWER 较强，2019 systolic 仍需 PDF |
| <a id="FPT-SF04"></a>[FPT-SF04](#FPT-SF04) | LUT-本机、低精度、结构化 ML 推理 | 如何把低比特、LUT、多项式近似或非 DNN 模型压到 FPGA 资源内 | 2016, 2018, 2021, 2023, 2025 | [FPT-2016-P0013](../../10_corpus/FPT/id_index.md#FPT-2016-P0013)； [FPT-2018-P0005](../../10_corpus/FPT/id_index.md#FPT-2018-P0005); [FPT-2021-P0001](../../10_corpus/FPT/id_index.md#FPT-2021-P0001)； [FPT-2023-P0007](../../10_corpus/FPT/id_index.md#FPT-2023-P0007); [FPT-2025-P0003](../../10_corpus/FPT/id_index.md#FPT-2025-P0003) | 多篇跨年证据，impact 多数 partial |
| <a id="FPT-SF05"></a>[FPT-SF05](#FPT-SF05) | Transformer、GNN 和 LLM FPGA 推理/编译器数据流 | Attention、GNN 和 LLM 的 latency、memory 和 nonlinear function bottleneck 怎样映射到 FPGA | 2022, 2024, 2025 | [FPT-2022-P0039](../../10_corpus/FPT/id_index.md#FPT-2022-P0039)； [FPT-2024-P0003](../../10_corpus/FPT/id_index.md#FPT-2024-P0003); [FPT-2024-P0014](../../10_corpus/FPT/id_index.md#FPT-2024-P0014)； [FPT-2025-P0020](../../10_corpus/FPT/id_index.md#FPT-2025-P0020); [FPT-2025-P0038](../../10_corpus/FPT/id_index.md#FPT-2025-P0038)； [FPT-2025-P0048](../../10_corpus/FPT/id_index.md#FPT-2025-P0048) | 近年前沿；2025 影响力不稳定 |
| <a id="FPT-SF06"></a>[FPT-SF06](#FPT-SF06) | SLAM、事件视觉和边缘视觉 | 实时视觉/SLAM 前端如何在 SoC FPGA 上低延迟运行 | 2022, 2024, 2025 | [FPT-2022-P0050](../../10_corpus/FPT/id_index.md#FPT-2022-P0050)； [FPT-2024-P0005](../../10_corpus/FPT/id_index.md#FPT-2024-P0005); [FPT-2025-P0015](../../10_corpus/FPT/id_index.md#FPT-2025-P0015)； [FPT-2025-P0029](../../10_corpus/FPT/id_index.md#FPT-2025-P0029) | FSLAM 有 artifact；其他多为早期 frontier |
| <a id="FPT-SF07"></a>[FPT-SF07](#FPT-SF07) | 3D 可重构架构/CAD | 如何建模和探索 stacked-die/3D FPGA 架构及 CAD flow | 2023 | [FPT-2023-P0022](../../10_corpus/FPT/id_index.md#FPT-2023-P0022) | 单篇强证据；不是 3DGS/NeRF 证据 |
| <a id="FPT-SF08"></a>[FPT-SF08](#FPT-SF08) | 云 FPGA、基准测试和 OpenCL 工具 | FPGA 工作怎样从单板实验走向平台、benchmark 和可复用 OpenCL 工具 | 2016, 2017 | [FPT-2016-P0002](../../10_corpus/FPT/id_index.md#FPT-2016-P0002)； [FPT-2016-P0021](../../10_corpus/FPT/id_index.md#FPT-2016-P0021)； [FPT-2017-P0047](../../10_corpus/FPT/id_index.md#FPT-2017-P0047) | Spector/PipeCNN 有公开仓库；标准化需复核 |
| <a id="FPT-SF09"></a>[FPT-SF09](#FPT-SF09) | FPGA 安全性和可靠性攻击面 | PUF、ICAP、SmartSSD 和多租户 FPGA 怎样引入安全风险 | 2022, 2023 | [FPT-2022-P0055](../../10_corpus/FPT/id_index.md#FPT-2022-P0055)； [FPT-2023-P0052](../../10_corpus/FPT/id_index.md#FPT-2023-P0052)； [FPT-2023-P0053](../../10_corpus/FPT/id_index.md#FPT-2023-P0053) | 安全 frontier；full PDF/artifact 不足 |

## 小领域深读

### [FPT-SF01](#FPT-SF01) HLS/CAD/DSE 和工具流定位
研究问题是 FPGA toolflow 怎样从手工 HLS/RTL 调参，走向 binary synthesis、dataflow transformation、memory-aware HLS 和 NoC performance prediction。2016 的 HLS 文章和 2017 的 binary-to-accelerator Best Paper 只能作为定位和里程碑线索；FLOWER 的 PDF 支撑了 dataflow compiler 这一条更具体路线。HBMalloc 和 GraphNoC 被放在相邻 subfield 中，是因为它们的问题核心分别是 HBM 管理和 NoC 预测，而不是泛泛的 HLS。

团队线索只写字符串：University of Toronto、UC Berkeley、Saarland/DFKI、Fudan、Waterloo/Kapre 都出现过，但没有 PID/ORCID 消歧，也不做排名。后续应补 2016/2017/2024 全文与 artifact。

### [FPT-SF02](#FPT-SF02) 内存、HBM、NoC 和数据移动
这一线的共同瓶颈是数据搬运，而不是“加速器应用”本身。MTJ BRAM 处理 memory-rich FPGA 的密度和能耗；Hypersort 把排序搬到 HBM FPGA 上；HBMalloc 处理 HLS 中的 HBM dynamic memory management；GraphNoC 用 GNN 做 application-specific FPGA NoC performance prediction。GraphNoC 因此被重分类为 NoC/CAD 性能预测，GNN 是机制，不是主 topic。

趋势判断有跨年证据：2016 memory fabric、2022 HBM sorting、2024 HBM allocation 和 NoC prediction。影响力仍需谨慎，GraphNoC/HBMalloc 目前主要是 award/title/abstract 证据。

### [FPT-SF03](#FPT-SF03) 数据流叠加和空间结构
DaCO、2019 systolic partitioning 和 FLOWER 共同说明 FPT 中存在 spatial/dataflow 路线。问题不是单个 kernel 怎么快，而是 overlay、systolic partitioning 和 compiler support 怎样让并行结构可管理。DaCO PDF 支撑 out-of-order token dataflow、Hoplite-Q NoC 和 clustering；2019 Best Paper 的机制还需要可读 PDF；FLOWER 则把 dataflow transformation 接到 HLS toolflow。

这一线和 FPGA/FCCM/FPL 的 cross-venue hook 很强，后续需要把 citation graph 和 benchmark reuse 分开看。

### [FPT-SF04](#FPT-SF04) LUT-本机、低精度和结构化 ML 推理
这一线从 BNN 平台比较、Dither NN、decision forest、PolyLUT 到 LL-ViT。共同问题是把模型结构改写成 FPGA 更容易承受的低比特、LUT、多项式或规则化 lookup 形式。BNN 的 OpenAlex citation 信号强；Dither NN、decision forest 和 PolyLUT 有 Best Paper 识别；LL-ViT 是 2025 frontier。

不要把这一线写成“所有 ML 加速”。它只覆盖低精度、LUT-native 或 structured inference 的具体方法。PolyLUT 的 GitHub URL 已补入 corpus，但未运行，状态是 runnable_unchecked。

### [FPT-SF05](#FPT-SF05) Transformer、GNN 和 LLM FPGA 推理
这一线在 2022 后变得清晰：HEP Transformer、FINN-T、FAMOUS、JEDI-Linear、FlightOPU、Gluttonous Snake 都围绕 attention、GNN、LLM nonlinear functions、HBM/overlay 或 strict latency。JEDI-Linear 是 2025 Best Paper；FPT 2025 program 还给出 artifact 状态，但本轮没有运行 artifact。

趋势有多篇跨年证据，但影响力不能提前写死。2025 论文引用低主要是时间窗口问题。JEDI-Linear 的 OpenAlex OA URL 曾出现标题冲突，报告和矩阵均不使用该 OA PDF 作为证据。

### [FPT-SF06](#FPT-SF06) SLAM、事件视觉和边缘视觉
FSLAM、HKPS、FRME 和 EdgeCT 支撑的是邻近视觉/SLAM/edge inference 线。FSLAM 有公开代码仓库，Semantic Scholar 在 2026-06-27 给出 25 citations 和 4 influential citations；HKPS 是 robustness-focused keypoint selection；FRME 是 event-based rotational motion estimation；EdgeCT 是 CNN-Transformer edge vision。

这条线和 3DGS/NeRF 的关系是邻近，不是直接。它能提供 feature extraction、motion estimation、edge inference 和 SoC FPGA 数据流经验，但不能证明 FPT 已经形成 3DGS/neural rendering 硬件加速方向。

### [FPT-SF07](#FPT-SF07) 3D 可重构架构/CAD
Into the Third Dimension 是 2023 FPT Best Paper，问题是 stacked-die/3D FPGA 或 3D RAD 的 architecture exploration，不是三维场景重建。PDF 支撑 RAD-Gen/COFFE/VPR-3D 扩展、inter-die connection、PDN、placement/routing 和 Koios benchmark 使用。

这篇可以作为 3D integration/CAD milestone candidate；不能放进 3DGS/NeRF 证据链。后续要做 VTR/RAD-Gen commit 级 artifact audit。

### [FPT-SF08](#FPT-SF08) 云 FPGA、基准测试和 OpenCL 工具
Configurable Cloud 是 FPT 2016 的平台叙事线索，但该 FPT DOI 在 OpenAlex/Crossref 上没有 citation 信号，本轮不把 Catapult 其他论文的影响力转嫁给它。Spector 和 PipeCNN 更适合写成 artifact/tooling 线索：前者是 OpenCL benchmark suite，后者是 OpenCL CNN accelerator repository。两者都没有本地复现实验。

这一线的 hook 在 HLS DSE、OpenCL toolflow、cloud FPGA 和 reproducibility。Spector 可写作 verified public artifact，但不能写成社区标准 benchmark，除非逐篇审计 citing papers 的实际使用方式。

### [FPT-SF09](#FPT-SF09) FPGA 安全性和可靠性攻击面
2022 的 RO-PUF physical cloning、2023 的 ICAP attack surface 和 SmartSSD covert channel 形成 venue-local security frontier。它们的问题分别是 PUF assumption、dynamic reconfiguration/ICAP、以及 FPGA-enabled storage 里的 covert channel。除 PUF 有 Best Paper 识别外，其他影响多为 early citation signal。

这条线需要 HOST/CHES/USENIX/FPGA security 的跨会议对照，才能判断是否成熟。当前只能写为 FPT 内安全/可靠性前沿，不写成长期主线。

## 趋势证据

- Toolflow 从 HLS 定位、binary synthesis 到 dataflow compiler、HBM-aware HLS 和 NoC prediction，证据来自 [FPT-2016-P0001](../../10_corpus/FPT/id_index.md#FPT-2016-P0001)、[FPT-2017-P0013](../../10_corpus/FPT/id_index.md#FPT-2017-P0013)、[FPT-2021-P0042](../../10_corpus/FPT/id_index.md#FPT-2021-P0042)、[FPT-2024-P0010](../../10_corpus/FPT/id_index.md#FPT-2024-P0010)、[FPT-2024-P0029](../../10_corpus/FPT/id_index.md#FPT-2024-P0029)。
- 数据搬运从 memory-rich BRAM 到 HBM sorting、HBM allocation 和 NoC prediction，证据来自 [FPT-2016-P0004](../../10_corpus/FPT/id_index.md#FPT-2016-P0004)、[FPT-2022-P0008](../../10_corpus/FPT/id_index.md#FPT-2022-P0008)、[FPT-2024-P0010](../../10_corpus/FPT/id_index.md#FPT-2024-P0010)、[FPT-2024-P0029](../../10_corpus/FPT/id_index.md#FPT-2024-P0029)。
- 低精度/LUT inference 不是单篇现象，证据跨 2016、2018、2021、2023、2025。
- Transformer/GNN/LLM 是 2022 后的近年前沿，证据跨 HEP Transformer、FINN-T、FAMOUS、JEDI-Linear、FlightOPU 和 Gluttonous Snake。
- 视觉/SLAM 线从 FSLAM 到 HKPS、FRME、EdgeCT，支持邻近视觉 pipeline hook，但不支持直接 3DGS/NeRF 成熟判断。

## 剩余差距

- 2016-2023 session 仍缺统一 program 抽取。
- IEEE Xplore abstract/keyword 批量抽取未完成。
- 多篇 deep_read 只能到 abstract 或 title metadata，已在 evidence matrix 的 `read_depth` 标出。
- citation/adoption/artifact 信号是 2026-06-27 初审，不等于长期影响结论。
- public code 只标 `runnable_unchecked`，没有本地 build/run。
- team_signal 只保留机构/作者字符串线索，不做排名。
