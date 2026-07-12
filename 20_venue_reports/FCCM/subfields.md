# FCCM 第二轮小领域深读

Venue：FCCM
日期：2026-06-27

## 1. 范围和证据

本文件只使用 FCCM 范围内的 corpus、报告和外部来源。第二轮后，`papers.csv` 有 302 条记录，`awards.csv` 有 17 条记录。`FCCM_screening_matrix.csv` 覆盖 319 个 source rows：302 个 paper rows 和 17 个 award rows。筛选结果是 242 个 `index_only`、76 个 `deep_read`、1 个 `exclude_non_main`。76 个 `deep_read` rows 对应 59 个唯一 paper_id，另有 17 个 award duplicate rows。`FCCM_paper_evidence_matrix.csv` 有 60 行：59 个 deep-read 主论文 paper_id，加 1 个 2026 3DGS Reconfigurable Computing Challenge/proceedings negative-boundary row。

引用、adoption、artifact、benchmark 信号的检索日期写在 evidence matrix 中。只有 title、官方 program、DOI 或 abstract 级证据的行，已经在 `read_depth` 和 `impact_verification_status` 标明。2026 论文只作为 frontier signal，除非证据 URL 明确支持 artifact、award 或 adoption。

## 2. 小领域地图

| subfield_id | 本地小领域 | 核心研究问题 | 证据状态 |
|---|---|---|---|
| <a id="FCCM-SF01"></a>[FCCM-SF01](#FCCM-SF01) | HLS 反馈、数值库、实施可预测性 | HLS 和 high-level programming 如何在综合前后得到可解释、可验证的反馈。 | 多年证据；QuickEst、LightningSim、RealProbe、template-hls-float 有 artifact signal |
| <a id="FCCM-SF02"></a>[FCCM-SF02](#FCCM-SF02) | FPGA CAD 路由、布局、开放实现闭包 | placement、routing、timing 和 bitstream-oriented flow 如何可复现、可诊断。 | 多年证据；Yosys+nextpnr artifact signal 强；2026 routing rows 只作 frontier |
| <a id="FCCM-SF03"></a>[FCCM-SF03](#FCCM-SF03) | 神经推理精度、LUT、内存、AIE 映射 | CNN、BNN、LUT-native、Transformer、LLM/VLM、Mamba、AIE workload 如何在 precision、memory 和 spatial constraints 下映射。 | 多年证据；fpgaConvNet/LUTNet artifact signal 强；近年影响力未验证 |
| <a id="FCCM-SF04"></a>[FCCM-SF04](#FCCM-SF04) | 内存、HBM、PIM、存储、网络数据路径 | 数据搬运、memory hierarchy 和 network/storage datapath 如何限制 FPGA accelerator throughput。 | 多年证据；Corundum、Shuhai artifact/adoption signal 较强 |
| <a id="FCCM-SF05"></a>[FCCM-SF05](#FCCM-SF05) | 视觉、3D、机器人、不规则空间管道 | SLAM、bundle adjustment、tomography、3D CNN、robotics middleware、3D registration 如何上 FPGA/AIE。 | 多次出现；main-track 3DGS 未验证 |
| <a id="FCCM-SF06"></a>[FCCM-SF06](#FCCM-SF06) | 基准测试、分析、功率、再现性 | power、memory、tool behavior 和真实 FPGA execution 如何可测、可复核。 | 部分 artifact 已找到；benchmark standardization 仍需审计 |
| <a id="FCCM-SF07"></a>[FCCM-SF07](#FCCM-SF07) | 安全性、FHE/PQC、受保护的计算数据路径 | FHE/PQC/security workload 的 arithmetic 和 bandwidth bottleneck 如何处理。 | 近年证据；adoption 未验证 |
| <a id="FCCM-SF08"></a>[FCCM-SF08](#FCCM-SF08) | 可重构基板、软处理器、算术、AIE 阵列 | soft processor、overlay、custom arithmetic、systolic/AIE mapping fabric 的约束是什么。 | 由 award rows 和 2026 AIE frontier rows 支撑 |

## 3. [FCCM-SF01](#FCCM-SF01): HLS 反馈、数值库、实施可预测性

研究问题：HLS workflow 需要比最终 implementation 更早的反馈。C simulation、C/RTL co-simulation 和 synthesis report 各自只能看到一部分行为，因此调试、QoR 估计、profiling 和 numeric library 都成为独立问题。

背景和现状：[FCCM-2016-P0004](../../10_corpus/FCCM/id_index.md#FCCM-2016-P0004) 从 source-level instrumentation 切入；[FCCM-2017-P0015](../../10_corpus/FCCM/id_index.md#FCCM-2017-P0015) 关注 Python/RAD workflow；[FCCM-2018-P0008](../../10_corpus/FCCM/id_index.md#FCCM-2018-P0008) 做 ML-based QoR estimation；[FCCM-2023-P0010](../../10_corpus/FCCM/id_index.md#FCCM-2023-P0010) 做 trace-based simulation；[FCCM-2025-P0023](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0023) 做 on-board profiling；[FCCM-2021-P0005](../../10_corpus/FCCM/id_index.md#FCCM-2021-P0005) 用 static scheduling 处理 multi-rate image pipeline；[FCCM-2019-P0037](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0037) 则把 custom floating point 做成 HLS numeric library。这个小领域的主线是 implementation feedback，不是泛泛的 HLS 标签。

技术路线：source instrumentation；从 HLS report 提取特征做 QoR prediction；LLVM trace simulation；通过 pragma 插入 profiling logic；multi-rate static scheduling；C++ template + arbitrary-width integer 生成 custom floating-point operator。

代表工作：[FCCM-2018-P0008](../../10_corpus/FCCM/id_index.md#FCCM-2018-P0008) 有 QuickEst code 和较高 citation signal；[FCCM-2023-P0010](../../10_corpus/FCCM/id_index.md#FCCM-2023-P0010)、[FCCM-2025-P0023](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0023) 有 LightningSim/RealProbe artifact；[FCCM-2019-P0037](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0037) 有 `template-hls-float` repository。[FCCM-2016-P0004](../../10_corpus/FCCM/id_index.md#FCCM-2016-P0004)、[FCCM-2017-P0015](../../10_corpus/FCCM/id_index.md#FCCM-2017-P0015)、[FCCM-2021-P0005](../../10_corpus/FCCM/id_index.md#FCCM-2021-P0005) 是 anchor，但还需要 PDF 和 citation graph 才能写成强影响力结论。

团队线索：Cornell/Zhiru Zhang 出现在 QoR estimation；Georgia Tech SHARC/Cong Hao 出现在 LightningSim/RealProbe；Imperial 出现在 templated floating point 和相关 HLS/numeric work。这里只是 corpus-local signal，不是排名。

未解问题：QuickEst、LightningSim、RealProbe、template-hls-float 是否被作者团队之外复用；2025 profiling workflow 是否会进入 artifact evaluation 或 HLS toolchain practice。

## 4. [FCCM-SF02](#FCCM-SF02): FPGA CAD 路由、布局、开放实现闭包

研究问题：FPGA 研究需要 placement、routing、timing 和 bitstream-level closure，但 vendor tool 可见性有限，research flow 又不一定匹配 commercial fabric。

背景和现状：[FCCM-2019-P0036](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0036) 是 open real-device flow anchor。之后的工作从 tool availability 转向 routing prediction ([FCCM-2023-P0001](../../10_corpus/FCCM/id_index.md#FCCM-2023-P0001))、open timing-driven GPU placement ([FCCM-2024-P0001](../../10_corpus/FCCM/id_index.md#FCCM-2024-P0001))、PathFinder convergence diagnosis ([FCCM-2025-P0010](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0010))、differentiable routing ([FCCM-2026-P0007](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0007))、Steiner initialization ([FCCM-2026-P0020](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0020)) 和 AIE array PnR ([FCCM-2026-P0024](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0024))。

技术路线：open synthesis/place/route；routing difficulty prediction；data-driven timing/congestion model；GPU placement；constrained routing case；differentiable relaxation；Steiner-tree initialization；AIE placement/routing algorithm。

代表工作：Yosys+nextpnr 的 artifact/toolchain signal 最强，因为 YosysHQ repositories 仍活跃。DREAMPlaceFPGA 是公开 artifact candidate，但 paper release mapping 仍需复核。DiffRouter、PathSteiner 和 AIE PnR 都是 2026 frontier，不能写成已验证影响。

团队线索：Symbiotic/YosysHQ/Imperial/UBC 出现在 open FPGA CAD；Wilton/Betz/Toronto-Waterloo 出现在 routing/AIE mapping；UT Austin/Pan 出现在 placement/routing；EPFL/Stojilovic/Ienne 出现在 routing convergence。这里只写路线绑定，不做排名。

未解问题：2026 routing/AIE papers 是否发布 code；differentiable 或 Steiner-based routing 是否成为 reusable baseline；AIE PnR 是否进入 MLIR-AIE upstream。

## 5. [FCCM-SF03](#FCCM-SF03): 神经推理精度、LUT、内存、AIE 映射

研究问题：neural workload 从 CNN 到 BNN、LUT-native network、ViT/LLM/VLM、Mamba/SSM 和 AIE execution 后，瓶颈会在 arithmetic precision、LUT/distributed memory、model compression、table lookup、sequence recurrence、AIE data movement 之间切换。

背景和现状：[FCCM-2016-P0010](../../10_corpus/FCCM/id_index.md#FCCM-2016-P0010) 是 CNN-to-FPGA mapping anchor。[FCCM-2018-P0027](../../10_corpus/FCCM/id_index.md#FCCM-2018-P0027) 和 [FCCM-2020-P0006](../../10_corpus/FCCM/id_index.md#FCCM-2020-P0006) 代表 low-precision 和 number-format work。[FCCM-2019-P0022](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0022) 把 LUT 作为 learned inference operator。[FCCM-2024-P0004](../../10_corpus/FCCM/id_index.md#FCCM-2024-P0004)、[FCCM-2025-P0017](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0017)、[FCCM-2026-P0018](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0018)、[FCCM-2026-P0021](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0021) 代表 Transformer/LLM/VLM frontier。[FCCM-2025-P0002](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0002) 与 [FCCM-2026-P0027](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0027) 形成 Mamba/SSM frontier。[FCCM-2026-P0005](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0005)、[FCCM-2026-P0017](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0017)、[FCCM-2026-P0029](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0029) 把 neural inference 连接到 AMD AIE。

技术路线：SDF and graph transformations for CNN；residual binarization；arithmetic-format DSE；LUT-native Boolean functions；ViT static/dynamic pruning；sub-8-bit LLM decomposition；table-lookup LLM inference；FPGA-GPU VLM partitioning；Vision Mamba dynamic quantization；AIE compiler and Transformer mapping。

代表工作：fpgaConvNet 同时有高 citation 和 maintained project signal。LUTNet 是 LUT-native neural inference 的 formation-paper candidate。HGQ-LUT 和 LUT-LLM 是 2026 frontier extensions，impact 太新。AIE4ML 有公开 artifact；LegoMap 仍缺 full PDF 和 artifact check。

团队线索：Imperial 出现在 fpgaConvNet/LUTNet/ITERA-LLM 相关路线；UCLA/Cong 出现在 LUT-LLM 和 AIE-adjacent rows；USC/Prasanna 出现在 ViT；Sun Yat-sen 与 CityU Hong Kong 出现在 Mamba/ViM rows。这些都是 corpus-local signal。

未解问题：LUTNet 到 HGQ-LUT/LUT-LLM 的直接 citation lineage 还需审计；LLM/VLM/Mamba 的 FPGA/GPU comparison 需要统一 benchmark normalization；AIE frameworks 是否会被作者团队之外复用还未知。

## 6. [FCCM-SF04](#FCCM-SF04):内存、HBM、PIM、存储、网络数据路径

研究问题：很多 FPGA accelerator 的瓶颈不是 arithmetic，而是 data movement。FCCM 里的证据可以拆成 sorting/storage、open NIC、HBM characterization、PIM/CIM、HBM access mechanisms、CXL/disaggregation 和 protocol-adaptive switching。

背景和现状：2017 同时出现 sorter microarchitecture ([FCCM-2017-P0019](../../10_corpus/FCCM/id_index.md#FCCM-2017-P0019)) 和 flash-attached Terabyte Sort ([FCCM-2017-P0026](../../10_corpus/FCCM/id_index.md#FCCM-2017-P0026))。[FCCM-2020-P0007](../../10_corpus/FCCM/id_index.md#FCCM-2020-P0007) 给出 reusable 100G NIC platform。[FCCM-2020-P0025](../../10_corpus/FCCM/id_index.md#FCCM-2020-P0025) 与 [FCCM-2021-P0015](../../10_corpus/FCCM/id_index.md#FCCM-2021-P0015) 做 HBM/Optane benchmarking。[FCCM-2022-P0008](../../10_corpus/FCCM/id_index.md#FCCM-2022-P0008) 与 [FCCM-2024-P0017](../../10_corpus/FCCM/id_index.md#FCCM-2024-P0017) 覆盖 compute-in-memory/PIM。[FCCM-2022-P0018](../../10_corpus/FCCM/id_index.md#FCCM-2022-P0018)、[FCCM-2024-P0012](../../10_corpus/FCCM/id_index.md#FCCM-2024-P0012)、[FCCM-2025-P0011](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0011)、[FCCM-2025-P0012](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0012) 把 HBM 问题分成 NoC distribution、irregular/nonbursting access、sparse kernel 和 layout transform。[FCCM-2023-P0005](../../10_corpus/FCCM/id_index.md#FCCM-2023-P0005)、[FCCM-2026-P0010](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0010)、[FCCM-2026-P0023](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0023) 把路线延伸到 CXL、SmartNIC state 和 protocol-adaptive switch。

技术路线：constant-depth merge logic；flash/DRAM/BRAM sort hierarchy；modular 100G NIC；HBM benchmark suite；BRAM compute-in-memory block；HBM2-PIM wrapper；overlay NoC；nonbursting request distribution；matrix-transpose layout scheduling；CXL-over-Ethernet prototype；action-enabled cache；protocol-specific switch generation。

代表工作：Corundum 的 adoption/artifact signal 最强，有 code、docs 和 downstream references。Shuhai 是最清楚的 HBM benchmark candidate。CoMeFa 有 award 和 follow-on evidence，但不能推断 vendor adoption。HBMex 和 SPAC 有公开 code，但太新。

团队线索：UCSD SysNet 出现在 Corundum；Zhejiang/ETH 出现在 Shuhai；UT Austin 出现在 CoMeFa；Waterloo/Kapre 和 EPFL/Ienne 出现在 HBM mechanisms；USC/Prasanna 出现在 HBM sparse kernels；Imperial/Southampton/MIT 出现在 SPAC。

未解问题：HBM benchmark/access-mechanism work 是否被其他 venues 复用；Corundum 是否通过 citation structure 成为 later FCCM network papers 的 baseline，而不仅是 topic 相似。

## 7. [FCCM-SF05](#FCCM-SF05)：视觉、3D、机器人、不规则空间管道

研究问题：实时 perception 和 spatial workload 同时有 irregular memory access、streaming、latency target 和动态 sensor/model structure。对本项目来说，关键是用 FCCM 证据支持 3DGS/robotics/edge pipeline reasoning，而不是虚构 main-track 3DGS 历史。

背景和现状：FCCM 有 active stereo ([FCCM-2019-P0001](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0001))、bundle adjustment ([FCCM-2019-P0004](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0004))、Visual SLAM feature extraction ([FCCM-2020-P0005](../../10_corpus/FCCM/id_index.md#FCCM-2020-P0005))、3D tomography alignment ([FCCM-2020-P0014](../../10_corpus/FCCM/id_index.md#FCCM-2020-P0014))、Gaussian-mixture mapping/navigation ([FCCM-2021-P0014](../../10_corpus/FCCM/id_index.md#FCCM-2021-P0014))、3D-CNN HAR ([FCCM-2023-P0008](../../10_corpus/FCCM/id_index.md#FCCM-2023-P0008))、robotics middleware ([FCCM-2026-P0002](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0002)) 和 AIE-PL 3D image registration ([FCCM-2026-P0004](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0004))。Graph processing ([FCCM-2016-P0013](../../10_corpus/FCCM/id_index.md#FCCM-2016-P0013)) 与 HiHiSpMV ([FCCM-2024-P0012](../../10_corpus/FCCM/id_index.md#FCCM-2024-P0012)) 是 irregular workload 邻近证据。

3DGS 边界：第二轮审计找到 <a id="FCCM-2026-X0001"></a>[FCCM-2026-X0001](#FCCM-2026-X0001)，题名为 `A High-Throughput FPGA Accelerator for Real-Time 3D Gaussian Splatting` 的 Reconfigurable Computing Challenge/proceedings item。它被标为 `exclude_non_main`，因为 authors 和 main-track status 仍是 `needs_review`。它只能作为 boundary signal，不能证明 FCCM 已形成成熟 main-track 3DGS subfield。

技术路线：stereo pipeline；bundle adjustment；CNN feature extraction for SLAM；tomography alignment；Gaussian-mixture mapping；3D CNN toolflow；streaming robotics middleware；AIE-PL image registration；graph/SpMV irregular memory management。

团队线索：Tsinghua/Yu Wang/Huazhong Yang 出现在 Visual SLAM/GAME；Paderborn/Platzner 出现在 robotics middleware；Conficconi/Di Salvo/Galfano 出现在 3D registration/FHE rows；USC/Prasanna 出现在 irregular/HBM/security-adjacent rows。

未解问题：2026 3DGS challenge item 是否有 public artifact 或 main-track equivalent；如何把这些 FCCM workloads 和 FPGA/FPL/FPT、graphics/neural-rendering venues 连接起来，而不越界声称成熟 3DGS topic。

## 8. [FCCM-SF06](#FCCM-SF06)：基准测试、分析、功耗、再现性

研究问题：FPGA 论文需要可复核的证据，包括 power estimation、memory characterization、profiling、HLS simulation 和 benchmark suite。

证据：KAPow ([FCCM-2016-P0016](../../10_corpus/FCCM/id_index.md#FCCM-2016-P0016)) 是 online power estimation anchor。Shuhai ([FCCM-2020-P0025](../../10_corpus/FCCM/id_index.md#FCCM-2020-P0025)) 有公开 HBM benchmark code 和 follow-on signal。LightningSim ([FCCM-2023-P0010](../../10_corpus/FCCM/id_index.md#FCCM-2023-P0010)) 与 RealProbe ([FCCM-2025-P0023](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0023)) 有 HLS simulation/profiling code。Chronbench ([FCCM-2025-P0005](../../10_corpus/FCCM/id_index.md#FCCM-2025-P0005)) 只是 benchmark-suite candidate；在找到 artifact URL 或 benchmark package 之前保持 `needs_review`。

影响力口径：Shuhai、LightningSim、RealProbe 可以写成 artifact candidates。只有 Shuhai 在本轮有 partial benchmark-standardization evidence。Chronbench 不写成 benchmark standard。

## 9. [FCCM-SF07](#FCCM-SF07)：安全、FHE/PQC、受保护的计算数据路径

研究问题：FHE/PQC/security workloads 会同时压到 arithmetic throughput、memory bandwidth 和验证需求。

证据：[FCCM-2024-P0005](../../10_corpus/FCCM/id_index.md#FCCM-2024-P0005) 处理 bandwidth-efficient homomorphic encrypted DFT acceleration。[FCCM-2026-P0022](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0022) 处理 resource-driven NTT architecture for FHE。这说明 security/FHE/PQC 在近年 FCCM 中可见，但 adoption 和 benchmark standardization 均未验证。

未解问题：需要 full PDF 才能写 method-level claim；cross-venue hooks 应包括 CHES、HOST、DAC/ICCAD security tracks 和 architecture/security accelerator venues。

## 10. [FCCM-SF08](#FCCM-SF08)：可重新配置的基板、软处理器、算术、AIE 数组

研究问题：FCCM 也研究 substrate 本身，包括 soft processor、overlay、custom arithmetic、systolic mapping 和 AIE-array constraints。

证据：GRVI Phalanx ([FCCM-2016-P0011](../../10_corpus/FCCM/id_index.md#FCCM-2016-P0011)) 是 soft-processor overlay award anchor。Templated soft floating point ([FCCM-2019-P0037](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0037)) 提供公开 HLS numeric library。2026 AIE PnR ([FCCM-2026-P0024](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0024)) 和 systolic/AIE constraint ([FCCM-2026-P0029](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0029)) 是新的 substrate-mapping frontier。

影响力口径：GRVI 有 citation signal，但本轮没有验证 artifact/adoption。`template-hls-float` 有公开 repository。2026 AIE rows 只写成 frontier，等待 full PDF、code 或 upstream evidence。

## 11. 影响力初审

| 项目 | 信号 | 地位 |
|---|---|---|
| fpgaConvNet | OpenAlex cited_by_count=268 checked 2026-06-27；project site 和 GitHub 存在 | verified impact candidate，不等于 benchmark standardization |
| Yosys+nextpnr | Semantic Scholar citationCount=116 checked 2026-06-27；YosysHQ repositories 活跃 | 已验证的 artifact/工具候选 |
| Corundum | OpenAlex cited_by_count=99 checked 2026-06-27；public repo/docs 和 downstream references | 部分采用候选 |
| Shuhai | OpenAlex cited_by_count=89 检查于 2026-06-27；公共 HBM 基准仓库 | 部分基准标准化候选 |
| LightningSim / RealProbe | 公开仓库；已检查引用信号 2026-06-27 | artifact candidates，adoption 未充分审计 |
| LUTNet / HGQ-LUT / LUT-LLM | LUTNet/HGQ2/LUT-LLM 有公开 code；counts checked 2026-06-27 | 行合理，直接引用谱系需要审核 |
| AIE4ML / ViM-Q / SPAC / HBMex | 公开仓库；2025-2026 行 | frontier artifacts，不写长期影响 |
| Chronbench | 基准套件标题和 DOI | needs_review，等待 artifact/source |

## 12. 剩余缺口

- 2026 仍是 partial：final award text、per-paper abstracts 和 canonical artifact ledger 未完全验证。
- 多个 evidence rows 只有 abstract/title/official-page depth，因为本轮无法访问 IEEE 或作者 PDF。
- Team signals 不是 author disambiguation，也不是排名。
- Citation counts 使用 evidence matrix 中记录的 OpenAlex 或 Semantic Scholar 数值；未使用 Google Scholar。
- 3DGS item 是 non-main challenge/proceedings boundary row，除非后续找到 official main-track source 和作者信息。
