# FPL 论文图谱分析

## 1. 会议定位

本报告中的 `FPL` 指 International Conference on Field-Programmable Logic and Applications。在本项目中，FPL 作为 FPGA、reconfigurable computing、HLS/CAD、FPGA systems、软硬协同应用加速和开放工具生态的 P1 venue 处理。该定位由 FPL 官方 prior-editions 页面和项目 `VENUE_REGISTRY.csv` 支撑，对应 claim <a id="FPL-001-C001"></a>[FPL-001-C001](#FPL-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 现有 754 行，覆盖 2016-2025 FPL proceedings/DBLP row；`awards.csv` 现有 26 行，覆盖 2016-2025 official FPL award rows。2026 官方站点存在，但截至 2026-06-27 未找到 accepted/proceedings/award 静态来源，因此 2026 记为 `normal_2026_partial`，不作为缺陷处理。

第二次补充已写入：screening matrix 780 rows，paper evidence matrix 62 rows，subfield deep dive、issue audit、claim ledger 和 run card 均已更新。

## 3. 主题分类

FPL 的主线不应写成“FPGA/EDA/ML systems”这类大词。本轮按具体研究问题重写为 venue-local subfields：CAD/architecture/QoR、HLS-to-routed-circuit automation、low-precision neural and Transformer mapping、host/network/storage/HBM streaming systems、cloud virtualization/overlays、open tooling/benchmarks/artifacts、security/bitstream trust、vision/SLAM/NeRF adjacency。

## 4. Accepted Papers 聚类结果

全量 screening 对 `papers.csv` 和 `awards.csv` 每一行给出 decision：`deep_read` 86、`index_only` 460、`needs_review` 199、`exclude_non_main` 35。`needs_review` 主要来自 title-level 信息不足或 topic bucket 仍过宽的 rows；`exclude_non_main` 主要用于 preface/demo/支持性 proceedings row。

`deep_read` evidence matrix 记录 WHY/HOW/WHAT/IMPACT/EVIDENCE。A/C deep-read agents 返回了 partial 结果；B 组因并发限制失败，因此 ML/Transformer 相关 rows 没有被写成 PDF-level 确定事实。没有 citation、artifact、benchmark 标准化或 adoption 来源的行保留 `impact_unverified`。

## 5. Award Papers 分析

`awards.csv` 中 2016-2025 奖项均有 canonical official FPL awards page 支撑；2025 award details 也有 FPL 2025 best-paper-awards page 支撑。Community award 与 paper award 已区分：FloPoCo、FGPU、Artifact Evaluation Initiative、Koios 等不能自动当作同年 FPL proceedings paper row。

已保留的 source/metadata variants：[FPL-2022-A16](../../10_corpus/FPL/id_index.md#FPL-2022-A16) Bitfiltrator title singular/plural variant；[FPL-2023-A20](../../10_corpus/FPL/id_index.md#FPL-2023-A20) Co-Visu author spelling variant；[FPL-2025-A26](../../10_corpus/FPL/id_index.md#FPL-2025-A26) Double Duty author order variant；[FPL-2025-A24](../../10_corpus/FPL/id_index.md#FPL-2025-A24) Koios cross-year alignment to [FPL-2021-P0060](../../10_corpus/FPL/id_index.md#FPL-2021-P0060)。

## 6. 代表性论文清单

| 论文/成果 | 角色 | WHY/HOW/WHAT/IMPACT 边界 | claim |
|---|---|---|---|
| JetStream | tool_benchmark | PCIe/FPGA-FPGA 通信瓶颈；流媒体库；采用未经审核。 | <a id="FPL-001-C032"></a>[FPL-001-C032](#FPL-001-C032) |
| 基于电压下降的故障攻击 | milestone_candidate | 作为故障向量的有效比特流；仅引文信号，后续结构未经审核。 | <a id="FPL-001-C035"></a>[FPL-001-C035](#FPL-001-C035) |
| FPGA 虚拟化调查 | formation_paper | 虚拟化分类锚；采用未经审核。 | <a id="FPL-001-C038"></a>[FPL-001-C038](#FPL-001-C038) |
| LogicNets | milestone_candidate | 低精度 ML/电路协同设计；仓库信号，重用未经审核。 | <a id="FPL-001-C048"></a>[FPL-001-C048](#FPL-001-C048) |
| Koios | tool_benchmark | FPGA 架构/CAD 基准测试套件；标准化未经过充分审核。 | <a id="FPL-001-C052"></a>[FPL-001-C052](#FPL-001-C052) |
| Bitfiltrator | milestone_candidate | Xilinx 比特流逆向工程；仓库/引用信号需要进一步审核。 | <a id="FPL-001-C053"></a>[FPL-001-C053](#FPL-001-C053) |
| 编译器发现动态调度 | milestone_candidate | 不规则 HLS 和选择性动态调度；后续候选人需要验证。 | <a id="FPL-001-C056"></a>[FPL-001-C056](#FPL-001-C056) |
| DynaRapid | 前沿 | 使用 Dynamatic/RapidWright 的快速 C 到路由电路路径；最近的，partial。 | <a id="FPL-001-C060"></a>[FPL-001-C060](#FPL-001-C060) |
| SERI | milestone_candidate | HBM 量子化学流；仓库/引用信号，采用未经审核。 | <a id="FPL-001-C061"></a>[FPL-001-C061](#FPL-001-C061) |
| 从错误到解决方案 | 前沿 | VPR-LLM 用于 FPGA CAD 工具的命令修复； 2025 年，太近了。 | <a id="FPL-001-C063"></a>[FPL-001-C063](#FPL-001-C063) |
| 双任务 | 前沿 | LUT/ML 算术压力下的加法器链并发； 2025 年的奖项，太新了。 | <a id="FPL-001-C062"></a>[FPL-001-C062](#FPL-001-C062) |
| NeRF/神经渲染行 | 起源/形成 | [FPL-2023-P0028](../../10_corpus/FPL/id_index.md#FPL-2023-P0028) 和 [FPL-2024-P0045](../../10_corpus/FPL/id_index.md#FPL-2024-P0045)； impact_unverified。 | FPL-001-SW-C010 |

## 7. 发展脉络

- 2016-2018：FPL 同时出现 CAD/architecture modeling、cloud/runtime、security/reliability、HLS memory banking、low-precision ML 和 system interface。
- 2019-2021：Fletcher、Limago、LogicNets、Koios、X-Attack、PathFinder switch-block work 把 FPL 从单 kernel datapath 推向 data interface、networking、benchmark infrastructure、security 和 physical QoR。
- 2022-2023：TRAC、Bitfiltrator、Compiler Discovered Dynamic Scheduling、GNNBuilder、Co-Visu 和 DiAD 显示 Transformer/HLS/bitstream/tooling/video/datacenter signals 同时活跃。
- 2024-2025：DynaRapid、SERI、Kratos、CFSA、Double Duty、From Errors to Solutions、ReconFormer、EQViTA、FPGA Stereo Visual SLAM、DMA Calypte 显示 rapid HLS backend、HBM/domain streaming、AI-for-CAD、vision/NeRF 和 Transformer/ViT 前沿。2025 impact 仍早，2026 不写趋势。

## 8. 团队线索

团队线索只作为 author-string/institution hints，不做排名，也不写成跨会议实力判断。所有 affiliation/entity 仍需人工消歧。

| 团队/机构线索 | 关联方向 | 证据状态 | 使用限制 |
|---|---|---|---|
| Toronto / Betz-Boutros-Abdelfattah | CAD、architecture、Koios、Double Duty | author-string/institution hint | 需要 affiliation/entity 人工消歧；不做排名 |
| EPFL / Ienne-Josipovic-Nikolic | HLS、routing、architecture、virtualization | author-string/institution hint | 需要 affiliation/entity 人工消歧；不写成跨会议实力判断 |
| Manchester / Koch / Fahmy | JetStream、virtualization、open infrastructure | author-string/institution hint | 需要 affiliation/entity 人工消歧；只作为阅读入口 |
| KIT / Tahoori-Gnad | FPGA security、fault line | author-string/institution hint | 需要 affiliation/entity 人工消歧；不做排名 |
| TU Delft / UAM / ETH / TU Darmstadt / SFU / Paderborn | system-interface、HBM rows | author-string/institution hint | 需要 affiliation/entity 人工消歧；不写成强弱判断 |
| Imperial / Sun Yat-sen / Xidian / NTU / Fudan | SLAM、vision、neural-rendering adjacency | author-string/institution hint | 需要 affiliation/entity 人工消歧；只作为邻近方向入口 |

## 9. 对博士入门者的阅读路线

先读 JetStream/Fletcher/Limago 理解 FPGA system interface；再读 LogicNets/Koios/TRAC/ReconFormer 理解 ML workload mapping；再读 Bitfiltrator/Compiler Discovered Dynamic Scheduling/DynaRapid/From Errors to Solutions 理解 toolchain/CAD route；最后读 Co-Visu、[FPL-2023-P0028](../../10_corpus/FPL/id_index.md#FPL-2023-P0028)、CFSA、FPGA Stereo Visual SLAM 看 vision/neural rendering/SLAM 信号。

## 10. 与我的方向的连接点

3DGS/神经渲染/FPGA 方向在 FPL 里目前应写成“NeRF/neural-rendering emerging signal + vision/SLAM adjacency + transferable FPGA system/CAD methods”。本轮确认到 [FPL-2023-P0028](../../10_corpus/FPL/id_index.md#FPL-2023-P0028) NeRF accelerator 和 [FPL-2024-P0045](../../10_corpus/FPL/id_index.md#FPL-2024-P0045) neural radiation field rendering；没有确认到 2016-2025 FPL 3DGS row。可迁移方法包括：HLS/CAD closure、host/HBM/DMA streaming、low-precision/Transformer/ViT mapping、CPU-FPGA partitioning、stereo/SLAM/event-camera evaluation。不要把这些证据升级成成熟 3DGS 加速方向。

## 11. 缺失来源

- FPL 2026年官方录用/论文集/获奖来源。
- IEEE/proceedings/official abstract、keywords、session 和 PDF 批量导出。
- ML/Transformer B-list 的 abstract/PDF 级补跑 deep-read。
- Repository health、artifact reproduction、citation-neighborhood、benchmark standardization、industry/toolchain adoption 审计。
- 针对 FPGA/FCCM/FPT/DAC/ICCAD/DATE/architecture/system/graphics venue的cross-venue综合。
