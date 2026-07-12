# FCCM 论文图谱分析

## 1. 会议定位

本报告中的 `FCCM` 指 IEEE International Symposium on Field-Programmable Custom Computing Machines。它在本项目中作为 custom computing、reconfigurable accelerators、FPGA/HLS/CAD、软硬协同系统和应用专用数据通路的核心 venue 处理。该定位来自 FCCM 官方页面和项目 `VENUE_REGISTRY.csv`，对应 claim <a id="FCCM-001-C001"></a>[FCCM-001-C001](#FCCM-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。第二次补充后，`papers.csv` 有 302 条记录：300 条首轮 accepted/program paper 记录、1 条 2019 award paper 回补记录、1 条 2026 Reconfigurable Computing Challenge / proceedings boundary 记录。`awards.csv` 有 17 条记录。2026 仍标记为 `partial`，因为最终 award text、per-paper abstract 和 artifact ledger 没有完全核验。对应 claim <a id="FCCM-001-C002"></a>[FCCM-001-C002](#FCCM-001-C002)、<a id="FCCM-001-C003"></a>[FCCM-001-C003](#FCCM-001-C003)、<a id="FCCM-001-C036"></a>[FCCM-001-C036](#FCCM-001-C036)。

| 年份 | papers.csv 记录数 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 31 | 完全的 | https://www.fccm.org/past/2016/programme.html |
| 2017 | 29 | 完全的 | https://www.fccm.org/past/2017/programme.html |
| 2018 | 29 | 完全的 | https://www.fccm.org/past/2018/program.html |
| 2019 | 37 | 完全的 | https://www.fccm.org/past/2019/home/program/ |
| 2020 | 25 | 完全的 | https://www.fccm.org/past/2020/home/program/ |
| 2021 | 30 | 完全的 | https://www.fccm.org/past/2021/programs-/ |
| 2022 | 24 | 完全的 | https://www.fccm.org/past/2022/technical-program-2022/ |
| 2023 | 20 | 完全的 | https://www.fccm.org/past/2023/technical-program-2023/ |
| 2024 | 21 | 完全的 | https://www.fccm.org/past/2024/technical-program-2024/ |
| 2025 | 26 | 完全的 | https://www.fccm.org/accepted-paper-list-2025/ |
| 2026 | 30 | partial | https://www.wp.fccm.org/accepted-paper-list-2026/ |

第二轮 新增和修正点：[FCCM-2019-P0037](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0037) 回补了 2019 Best Long Paper `Templatised Soft Floating-Point for High-Level Synthesis`，DOI 为 `10.1109/FCCM.2019.00038`；[FCCM-2026-P0025](../../10_corpus/FCCM/id_index.md#FCCM-2026-P0025) TransDot 回补 DOI `10.1109/FCCM68464.2026.00034`；[FCCM-2026-X0001](subfields.md#FCCM-2026-X0001) 记录 2026 3DGS Reconfigurable Computing Challenge/proceedings item，但筛选为 `exclude_non_main`，不并入主论文趋势。对应 claim <a id="FCCM-001-C037"></a>[FCCM-001-C037](#FCCM-001-C037) 到 <a id="FCCM-001-C039"></a>[FCCM-001-C039](#FCCM-001-C039)。

## 3. 主题分类

这里的 topic 是 FCCM venue 内部工作标签，不是全局 taxonomy。大领域词只作为上下文，主 topic 写成具体研究问题。

| 本地主题 | 核心问题 | 代表证据 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|
| HLS 反馈、数值库、实施可预测性 | HLS 设计如何在综合前后获得可靠反馈 | AutoSLIDE、QuickEst、Clockwork、LightningSim、RealProbe、template-hls-float | 2016-2025 | 直接关联 FPGA/加速器工程落地和 3DGS pipeline 的 HLS/RTL 取舍 | 验证行，影响部分 |
| FPGA CAD 路由、布局、开放实现闭包 | 真实 FPGA placement/routing/timing/bitstream flow 如何可复现、可诊断 | Yosys+nextpnr、ML 路由难度、GPU placer、路由收敛、DiffRouter、PathSteiner | 2019-2026 | 决定复杂 pipeline 能否稳定收敛到可布线实现 | 已验证行数，2026 前沿 |
| 神经推理精度、LUT、内存、AIE 映射 | CNN/BNN/LUT/Transformer/LLM/Mamba/AIE workload 如何映射到 FPGA/AIE | fpgaConvNet、ReBNet、LUTNet、ViT 剪枝、ITERA-LLM、LUT-LLM、AIE4ML、ViM-Q | 2016-2026 | 与端侧推理、VLA/机器人、神经渲染近邻负载相关 | 已验证行数，前沿影响未验证 |
| 内存/HBM/PIM/存储/网络数据路径 | 数据搬运、HBM、PIM、SmartNIC、CXL 如何限制系统吞吐 | Terabyte Sort、Corundum、Shuhai、CoMeFa、HBMex、SPAC | 2017-2026 | 连接 tile/binning、排序、alpha blending、DDR/AXI/HBM 数据搬运 | artifact evidence 部分 |
| 视觉/3D/机器人/不规则空间管道 | SLAM、bundle adjustment、tomography、3D CNN、robotics middleware 如何上 FPGA | 主动立体、π-BA、Visual SLAM、GAME、HARFLOW3D、3D 图像配准 | 2019-2026 | 是 3D/机器人/端侧实时方向的邻近证据源 | 重复局部证据 |
| 基准测试、分析、功率、再现性 | 如何测量 power、memory、tool behavior 和真实 FPGA execution | KAPow、Shuhai、LightningSim、RealProbe、Chronbench | 2016-2025 | 对 PPA breakdown 和论证可信度直接相关 | 部分； Chronbench needs_review |
| 安全/FHE/PQC 数据路径 | 加密和安全 workload 如何处理 bandwidth 与 arithmetic bottleneck | 同态 DFT、RefFHE-NTT | 2024-2026 | 可作为 NTT/FHE/PQC 加速邻近路线 | impact_unverified |

## 4. Accepted Papers 聚类结果

`papers.csv` 的 cluster 是 title/session/track 关键词加人工规则的 provisional 标注，服务于 venue 内部浏览，不应直接升级为全局 taxonomy。对应 claim <a id="FCCM-001-C005"></a>[FCCM-001-C005](#FCCM-001-C005) 和 <a id="FCCM-001-C010"></a>[FCCM-001-C010](#FCCM-001-C010)。

| 簇 | papers.csv 记录数 | 状态 |
|---|---:|---|
| 其他自定义计算应用程序和系统 | 91 | 临时 |
| HLS、编译器、CAD 和实现闭包 | 64 | 临时 |
| ML、DNN、LLM 和低精度推理 | 56 | 临时 |
| 数据流、内存、存储和网络数据路径 | 39 | 临时 |
| 科学、图形、机器人和不规则应用加速器 | 22 | 临时 |
| FPGA 结构、覆盖、CGRA、软处理器和算术 | 14 | 临时 |
| 安全、加密、隐私和算法FHE/PQC | 11 | 临时 |
| 基准测试、分析、电源、调试和评估 | 5 | 临时 |

第二轮 screening 结果写入 `FCCM_screening_matrix.csv`：319 行、76 个 `deep_read` screening rows、242 个 `index_only` rows、1 个 `exclude_non_main` row。76 个 `deep_read` rows 中，59 个是唯一 paper_id，17 个是 awards 表重复行。对应 claim <a id="FCCM-001-C040"></a>[FCCM-001-C040](#FCCM-001-C040)。

## 5. Award Papers 分析

| 年份 | 奖项类型 | 论文 | 主题 | 是否纳入里程碑 | 证据状态 |
|---|---|---|---|---|---|
| 2016 | 最佳论文 | KAPow | 电源/分析 | yes | 已验证 |
| 2016 | 最佳短论文 | GRVI Phalanx | 软处理器/覆盖 | yes | 已验证 |
| 2017 | 最佳论文 | 高性能硬件合并排序器 | 排序数据路径 | yes | 已验证 |
| 2017 | 最佳短论文 | 使用 Python 评估基于异构处理器的 FPGA 的 RAD | 编程工作流程 | yes | 已验证 |
| 2018 | 最佳论文 | ReBNet | 低精度神经推理 | yes | 已验证 |
| 2018 | 最佳短论文 | 快速准确的 HLS 使用 ML 进行快速准确的 QoR 估计 | HLS 反馈 | yes | 已验证 |
| 2019 | 最佳长论文 | HLS 的模板化软浮点 | HLS 数字库 | yes | 已验证 |
| 2020 | 最佳论文 | SPN 的算术数字格式比较 推理 | 算术/精度 | yes | 已验证 |
| 2020 | 最佳短论文 | Yosys+nextpnr | open FPGA CAD | yes | needs_review |
| 2021 | 最佳长论文 | Clockwork | 图像管道调度 | yes | 已验证 |
| 2021 | 最佳短论文 | ESCA | 事件/拆分 CNN | yes | 已验证 |
| 2022 | 最佳论文 | CoMeFa | 内存计算 FPGA 块 | yes | 已验证 |
| 2023 | 最佳论文 | ML 路由难度预测 | 路由诊断 | yes | needs_review |
| 2023 | 最佳论文亚军 | LightningSim | HLS 模拟 | yes | needs_review |
| 2024 | 最佳论文 | GPU 时序驱动 FPGA 布局器 | 布局/时序收敛 | yes | needs_review |
| 2024 | 最佳短论文 | LUT 用于密集函数的网络 | LUT 综合/类似 ML 的逻辑 | yes | needs_review |
| 2025 | 最佳论文 | 有保证但很难找到 | 路由收敛 | yes | 已验证 |

2019 award gap已解决：[FCCM-2019-A07](../../10_corpus/FCCM/id_index.md#FCCM-2019-A07) now aligns to [FCCM-2019-P0037](../../10_corpus/FCCM/id_index.md#FCCM-2019-P0037)。2020 Best Short、2023、2024 等补充奖项仍主要依赖 TCFPGA ledger，保留 `needs_review`。2026 award winner 没有 canonical text ledger；HGQ-LUT 的 image/homepage 信号不写成 verified award。对应 claim <a id="FCCM-001-C048"></a>[FCCM-001-C048](#FCCM-001-C048)。

## 6. 第二轮 Evidence Matrix

`FCCM_paper_evidence_matrix.csv` 写入 60 行，每行包含 WHY、HOW、WHAT、IMPACT、evidence_type、evidence_url、citation/adoption/artifact/benchmark/team signals、read_depth 和 verification status。

| 证据组 | 代表论文 | 影响力初审 |
|---|---|---|
| HLS 反馈和实现的可预测性 | QuickEst、LightningSim、RealProbe、Clockwork、template-hls-float | QuickEst/LightningSim/RealProbe/template-hls-float 有 artifact signal；长期复用仍需 citation graph |
| CAD 布线/布局/开放实现 | Yosys+nextpnr、路由预测、GPU 布局器、路由汇聚、DiffRouter、PathSteiner | Yosys+nextpnr artifact/adoption signal最强；2026 routing rows 是 frontier |
| 神经推理 | fpgaConvNet、ReBNet、LUTNet、LUT-LLM、AIE4ML、ViM-Q | fpgaConvNet/LUTNet 影响力信号较强；2025-2026 LLM/Mamba/AIE 不写长期影响 |
| 内存/网络/存储 | Corundum、Shuhai、CoMeFa、HBMex、SPAC | Corundum 有 adoption/artifact signal；Shuhai 是 HBM benchmark candidate；HBMex/SPAC 太新 |
| 视觉/3D/机器人 | π-BA、Visual SLAM、GAME、HARFLOW3D、机器人中间件、3D 图像配准 | 作为邻近 workload evidence；3DGS 只作为 non-main boundary |
| 基准/安全/底层 | KAPow、Chronbench、同态 DFT、ReFHE-NTT、GRVI、AIE 阵列论文 | 多数 impact_unverified；Chronbench artifact/source 仍需查证 |

## 7. 发展脉络

- 2016-2018：FCCM 同时覆盖 overlay/soft processor、power/debug、storage/sorting、早期 BNN/低精度和 HLS feedback。KAPow、GRVI、High-Performance Hardware Merge Sorter、QuickEst 和 ReBNet 说明 venue 早期已经把测量、编程效率、数据密集应用和 neural inference 放在同一 custom-computing 框架下。
- 2019-2021：open-source CAD、HLS numeric libraries、HBM/Optane benchmarking、SLAM/3D/robotics、compute-in-memory 和 image-pipeline scheduling 变得更显眼。Yosys+nextpnr、template-hls-float、Visual SLAM、GAME、Clockwork、CoMeFa 是这一段的锚点。
- 2022-2024：工具链和 memory-centric 主题继续加重。LightningSim、routing difficulty prediction、GPU-accelerated timing-driven placer、Shuhai/HBM follow-ons、HBM2-PIM、HiHiSpMV、ViT pruning 和 homomorphic DFT 表明 FCCM 在工具链、memory bottleneck、edge/ML/security workload 之间反复切换。
- 2025-2026：LLM/Mamba/AIE、SmartNIC/cache/protocol-adaptive switches、robotics middleware、PQC/FHE、AIE-PL 3D image registration 和 differentiable/Steiner routing 进入前沿。2026 论文只作为 frontier/partial signal 使用。

| 技术路线 | 核心问题 | 代表论文 | 活跃年份 | 转折点 |
|---|---|---|---|---|
| HLS 反馈和分析 | 高级程序如何获得可预测、可调试、可测的实现反馈 | AutoSLIDE、QuickEst、LightningSim、RealProbe、Clockwork | 2016-2025 | 仪器 -> QoR 预测 -> 迹线仿真 -> 板载分析 |
| 开放 FPGA CAD 及路由闭包 | placement/routing/timing/bitstream flow 如何可复现 | Yosys+nextpnr、ML 路由、GPU placer、路由收敛、DiffRouter、PathSteiner | 2019-2026 | 开放实器流程 -> 数据驱动/可微分路由与布局 |
| 神经推理与LUT/内存/AIE 映射 | NN workload 如何适配精度、LUT、memory、AIE constraints | fpgaConvNet、ReBNet、LUTNet、ViT 剪枝、LUT-LLM、AIE4ML、ViM-Q | 2016-2026 | CNN -> BNN/LUT -> Transformer/LLM/Mamba -> AIE 映射 |
| 内存/HBM/PIM/网络数据路径 | 数据搬运和 memory/network hierarchy 如何约束吞吐 | Terabyte Sort、Corundum、Shuhai、CoMeFa、HBMex、SPAC | 2017-2026 | 存储排序 -> 打开 NIC/HBM 基准测试 -> PIM/CXL/HBM 机制 -> 协议自适应开关 |
| 视觉/3D/机器人 | perception/registration/mapping pipeline 如何上 FPGA | π-BA、Visual SLAM、GAME、HARFLOW3D、机器人中间件、3D 图像配准 | 2019-2026 | 隔离视觉加速器 ->机器人中间件和 AIE-PL 3D 注册 |
| 安全/FHE/PQC | 加密 workload 的 bandwidth 和 arithmetic bottleneck 如何处理 | 同态 DFT、RefFHE-NTT | 2024-2026 | 应用程序加速 -> 受保护计算数据路径 |

## 8. 团队和机构线索

这里的团队线索只表示 FCCM 2016-2026 corpus 内反复出现，并且与某条技术路线绑定；不等同于跨会议影响力排名。

| 团队/机构线索 | 主要路线 | 代表成果 | claim |
|---|---|---|---|
| UCLA/丛线 | HLS/dataflow、LLM/AIE、网络相邻工作 | LUT-LLM、AIE/收缩行、旧 HLS/数据流行 | <a id="FCCM-001-C011"></a>[FCCM-001-C011](#FCCM-001-C011) |
| USC/Prasanna 线 | graph/GNN、vision/SAR、HE/security/HBM 稀疏 workload | ViT 剪枝、HiHiSpMV、同态 DFT | <a id="FCCM-001-C012"></a>[FCCM-001-C012](#FCCM-001-C012) |
| 伦敦帝国学院 | HLS、DNN/LLM、LUT-原生推理、网络 | fpgaConvNet、LUTNet、ITERA-LLM、SPAC、KAPow | <a id="FCCM-001-C013"></a>[FCCM-001-C013](#FCCM-001-C013) |
| 多伦多/滑铁卢/Betz-Anderson-Kapre 线路 | 覆盖、NoC、路由/CAD、AIE 映射 | 路由预测、HBM NoC、AIE 布局/路由 | <a id="FCCM-001-C014"></a>[FCCM-001-C014](#FCCM-001-C014) |
| EPFL/Ienne-Stojilovic 线 | 数据流、路由汇聚、HBM 接入 | 保证但难找、PathSteiner、HBMex | <a id="FCCM-001-C015"></a>[FCCM-001-C015](#FCCM-001-C015) |
| Georgia Tech/丛浩线 | HLS 仿真/分析工具 | LightningSim、RealProbe | <a id="FCCM-001-C016"></a>[FCCM-001-C016](#FCCM-001-C016) |
| UT Austin 机构级线路 | 内存计算、布局/布线、波形仿真 | CoMeFa、GPU 布局器、布线相关行 | <a id="FCCM-001-C017"></a>[FCCM-001-C017](#FCCM-001-C017) |
| UCSD SysNet 信号 | 开放 SmartNIC/NIC 平台 | Corundum | <a id="FCCM-001-C045"></a>[FCCM-001-C045](#FCCM-001-C045) |

## 9. 对博士入门者的阅读路线

必读 12 篇：KAPow、High-Performance Hardware Merge Sorter、QuickEst、ReBNet、Yosys+nextpnr、LUTNet、Comparison of Arithmetic Number Formats、Clockwork、CoMeFa、LightningSim、A Machine Learning Approach for Predicting Routing Difficulty、Guaranteed Yet Hard to Find。

扩展 25 篇：GRVI Phalanx、Terabyte Sort、template-hls-float、Corundum、Shuhai、3D-VNPU、ESCA、GAME、Visual SLAM feature extraction、π-BA、CXL over Ethernet、GPU timing-driven placer、ViT pruning、HiHiSpMV、homomorphic DFT、HBMex、ITERA-LLM、RealProbe、AIE4ML、HGQ-LUT、LUT-LLM、SPAC、robotics middleware、AIE-PL 3D image registration、ViM-Q。

适合跟踪的近年方向：LUT-native and memory-based inference、AIE compiler/PnR、SmartNIC state and protocol-adaptive switches、HLS simulation/profiling、HBM irregular-access mechanisms、robotics middleware、PQC/FHE datapaths、routing convergence and differentiable routing。

## 10. 与我的方向的连接点

你的 3DGS/神经渲染/FPGA 方向在 FCCM 里更接近四条邻近路线：第一，HLS feedback、CAD routing/placement 和 implementation closure，回答算法如何稳定落到 FPGA/AIE；第二，memory/HBM/storage/network datapaths，对应 tile/binning、排序、alpha blending、buffer、AXI/DDR/HBM 数据搬运；第三，vision/SLAM/tomography/3D image-registration/robotics middleware，提供实时端侧 pipeline 的邻近 workload 证据；第四，LUT/LLM/AIE/Mamba 等 neural inference 前沿，提示模型和空间架构映射的约束。

本轮找到一个 2026 3DGS Reconfigurable Computing Challenge/proceedings item，但没有核验为 FCCM main accepted paper。因此 3DGS 连接点应写为邻近负载、数据通路迁移和 non-main boundary，不应写成 FCCM 已形成成熟 3DGS hardware subfield。对应 claim <a id="FCCM-001-C046"></a>[FCCM-001-C046](#FCCM-001-C046)。

## 11. 缺失来源

- 2026 官方 award text ledger；HGQ-LUT 只保留 needs_review，不写成 verified award。
- IEEE Xplore per-paper pages、abstracts、keywords 和 artifact badges 的批量导出。
- 2020 Best Short、2023、2024 TCFPGA supplemental award rows 的年度页面 canonical confirmation。
- Chronbench artifact/benchmark package源码。
- 3DGS challenge item 的作者、artifact、main-track status 和官方 machine-readable source。
- 跨 FPGA/FPL/FPT/DAC/ICCAD/体系结构/robotics/graphics venues 的对照证据。
