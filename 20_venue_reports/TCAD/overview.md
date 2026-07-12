# TCAD 论文图谱分析

## 1. Venue 定位和数据范围

`TCAD` 在本项目中指 IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems。它是 journal，不是会议 accepted-paper venue。本轮仍把它作为 EDA、硬件加速、软硬协同和设计闭环成熟成果来源处理。

本 第二轮 pass 覆盖 2016-2026。`papers.csv` 有 3329 条 journal_article rows，主要来自 DBLP TCAD volume metadata；`awards.csv` 有 14 条 IEEE CEDA Donald O. Pederson Best Paper Award rows。2026 年仍是 partial。

## 2. 第二轮 处理结果

- 写入 `TCAD_screening_matrix.csv`：3343 行，覆盖全部 papers 和 awards。
- 写入 `TCAD_paper_evidence_matrix.csv`：35 条 parent-selected deep-read evidence rows。
- 写入 `subfields.md`：按小领域整理研究问题、路线、代表工作、团队线索和跨会议 hook。
- Targeted metadata backfill：为代表论文补可靠 IEEE URL（能解析处），为 DREAMPlace、DNN+NeuroSim、CircuitNet 补 code/dataset URL；为 2016/2017 Pederson award rows 补 2015 DOI/IEEE URL，但不造 2016-2026 corpus 外的 `paper_id`。

## 3. 主题分类

| 子领域 | 核心问题 | 证据论文 | 地位 |
|---|---|---|---|
| 物理设计、光刻、热和布局收敛 | 随着设计变得更加复杂，如何关闭布局、布线、光刻、热和布局约束。 | [TCAD-2021-P0047](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0047);[TCAD-2021-P0112](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0112);[TCAD-2022-P0278](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0278);[TCAD-2023-P0049](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0049);[TCAD-2024-P0281](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0281) | venue_provisional |
| HLS、FPGA 和可重构硬件生成 | 算法和系统模型如何成为 FPGA 或具有有用 QoR 的可重构实现。 | [TCAD-2016-P0015](../../10_corpus/TCAD/id_index.md#TCAD-2016-P0015);[TCAD-2019-P0122](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0122);[TCAD-2020-P0076](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0076);[TCAD-2022-P0386](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0386);[TCAD-2023-P0091](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0091) | venue_provisional |
| 神经/边缘加速器和硬件-软件协同设计 | 神经和边缘 workload 如何在内存、延迟和资源限制下映射到硬件。 | [TCAD-2017-P0088](../../10_corpus/TCAD/id_index.md#TCAD-2017-P0088);[TCAD-2018-P0016](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0016);[TCAD-2019-P0039](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0039);[TCAD-2020-P0254](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0254);[TCAD-2022-P0303](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0303);[TCAD-2026-P0201](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0201) | venue_provisional |
| CIM/PIM 和神经形态基准框架 | 以内存为中心的设备和模拟器如何减少数据移动并使比较可重复。 | [TCAD-2018-P0118](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0118);[TCAD-2021-P0045](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0045);[TCAD-2023-P0085](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0085);[TCAD-2026-P0117](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0117) | venue_provisional |
| Transformer 和 LLM 注意力加速 | 注意力和 LLM 推理/训练如何与记忆运动、稀疏性和精度相互作用。 | [TCAD-2022-P0449](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0449);[TCAD-2023-P0003](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0003);[TCAD-2024-P0236](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0236);[TCAD-2024-P0307](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0307);[TCAD-2026-P0161](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0161);[TCAD-2026-P0231](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0231) | cross_venue_candidate |
| Neural rendering and NeRF acceleration | Whether neural rendering appears in TCAD as hardware/software co-design rather than only graphics algorithms. | [TCAD-2024-P0120](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0120);[TCAD-2025-P0308](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0308) | insufficient_evidence_for_stable_trend |
| AI 用于 EDA 和 LLM 辅助 CAD | ML/LLM 如何帮助具体的 EDA 任务，例如热点检测、RTL生成、布局和数据集。 | [TCAD-2023-P0180](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0180);[TCAD-2024-P0281](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0281);[TCAD-2025-P0209](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0209);[TCAD-2025-P0341](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0341) | venue_provisional |
| 3D IC、小芯片、中介层和 NoC 集成约束 | 封装/集成如何改变物理设计、测试、散热和通信约束。 | [TCAD-2020-P0365](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0365);[TCAD-2026-P0117](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0117) | cross_venue_candidate |
| 逻辑、形式和量子 CAD 方法锚 | 表示和映射选择如何控制优化/搜索复杂性。 | [TCAD-2016-P0111](../../10_corpus/TCAD/id_index.md#TCAD-2016-P0111);[TCAD-2019-P0148](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0148) | method_bridge |

这些 label 是 venue 内小领域线索，不是全局 stable taxonomy。大领域词如 EDA、FPGA、accelerator 只作为上下文或平台，不作为主 topic。

## 4. Corpus 和 Screening 概览

| 项目 | count | 注释 |
|---|---:|---|
| 论文.csv 行 | 3329 | DBLP 衍生期刊文章元数据 |
| Awards.csv 行 | 14 | CEDA Pederson 奖来源 |
| 筛选行 | 3343 | 所有论文 + 奖项 |
| 筛选决策`deep_read` | 47 | 允许的决策值 |
| 筛选决策 `index_only` | 2256 | 允许的决策值 |
| 筛选决策 `needs_review` | 1040 | 允许的决策值 |
| 筛选决策 `exclude_non_main` | 0 | 允许的决策值 |

最大的标题级簇对于浏览仍然有用，但不是最终分类：

| 簇 | rows | 地位 |
|---|---:|---|
| 其他需要手动审核的 TCAD 期刊行 | 1038 | 临时 |
| 时序、功耗、散热、可靠性和签核 | 293 | 临时 |
| AI 加速器、FPGA、HLS 和软硬件协同设计 | 244 | 临时 |
| CIM、PIM、新兴存储器和神经形态加速器 | 214 | 临时 |
| 物理设计、布局、光刻、封装和 DTCO | 203 | 临时 |
| HLS、 FPGA，可重构系统和硬件生成 | 196 | 临时 |
| DFT，测试生成、故障诊断和验证 | 156 | 临时 |
| AI for EDA，基于学习的设计自动化和 LLM 辅助 CAD | 152 | 临时 |
| 变化、成品率、近似计算和可靠性建模 | 145 | 临时 |
| 嵌入式， CPS、实时和机器人系统 | 126 | 临时 |

## 5. 奖项来源审计

Pederson award rows使用 IEEE CEDA 官方奖项页面作为规范来源。获奖年份和论文发表年份分开。两行需要显式范围处理：2016 年和 2017 年奖项指向 2015 年 TCAD 出版物，因此 `paper_id` 在当前 2016-2026 年论文语料库中保持空白。 `awards.csv` 中记录了两个较小的元数据冲突：2021 年硬件/软件联合探索作者列表差异和 2019 年 Caffeine 标题变体。

## 6. 代表性evidence rows

| paper_id | 年 | 标题 | 子领域 | 角色 | 影响状态 |
|---|---:|---|---|---|---|
| [TCAD-2016-P0015](../../10_corpus/TCAD/id_index.md#TCAD-2016-P0015) | 2016 | FPGA 高级综合工具的调查和评估 | HLS、FPGA 和可重构硬件生成 | origin_anchor | impact_unverified |
| [TCAD-2016-P0111](../../10_corpus/TCAD/id_index.md#TCAD-2016-P0111) | 2016 | 多数逆变器图：逻辑优化的新范式 | 逻辑、形式和量子 CAD 方法锚 | milestone_candidate | impact_unverified |
| [TCAD-2017-P0088](../../10_corpus/TCAD/id_index.md#TCAD-2017-P0088) | 2017 | DLAU：FPGA | 神经/边缘加速器和硬件-软件协同设计 | origin_anchor | impact_unverified |
| [TCAD-2018-P0016](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0016) | 2018 | YodaNN：超低功耗二进制权重架构的可扩展深度学习加速器单元CNN 加速 | 神经/边缘加速器和硬件-软件协同设计 | milestone_candidate | impact_unverified |
| [TCAD-2018-P0118](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0118) | 2018 | NeuroSim：用于在线学习中神经启发架构基准测试的电路级宏模型 | CIM/PIM 和神经形态基准框架 | tool_benchmark | impact_unverified |
| [TCAD-2019-P0039](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0039) | 2019 | Caffeine：实现深度卷积神经网络的统一表示和加速 | 神经/边缘加速器和硬件-软件协同设计 | milestone_candidate | impact_unverified |
| [TCAD-2019-P0122](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0122) | 2019 | 我们到了吗？高级综合状态研究 | HLS、FPGA 和可重构硬件生成 | method_bridge | impact_unverified |
| [TCAD-2019-P0148](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0148) | 2019 | 将量子电路映射到 IBM QX 架构的有效方法 | 逻辑、形式和量子 CAD 方法锚 | milestone_candidate | impact_unverified |
| [TCAD-2020-P0076](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0076) | 2020 | 高级综合设计空间探索：过去、现在和未来 | HLS、FPGA 和可重构硬件生成 | method_bridge | impact_unverified |
| [TCAD-2020-P0254](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0254) | 2020 | 神经架构的硬件/软件联合探索 | 神经/边缘加速器和硬件-软件协同设计 | milestone_candidate | impact_unverified |
| [TCAD-2020-P0365](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0365) | 2020 | Compact-2D：构建两层门级 3-D IC 的物理设计方法 | 3D IC、小芯片、中介层和 NoC 集成约束 | milestone_candidate | impact_unverified |
| [TCAD-2021-P0045](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0045) | 2021 | DNN+NeuroSim V2.0：端到端基准测试框架用于片上训练的内存计算加速器 | CIM/PIM 和神经形态基准框架 | tool_benchmark | impact_unverified |
| [TCAD-2021-P0047](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0047) | 2021 | OpenMPL：开源布局分解器 | 物理设计、光刻、热和布局收敛 | tool_benchmark | impact_unverified |
| [TCAD-2021-P0112](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0112) | 2021 | DREAMPlace：支持深度学习工具包的 GPU 现代 VLSI 布局加速 | 神经/边缘加速器和硬件-软件协同设计 | milestone_candidate | impact_unverified |
| [TCAD-2022-P0278](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0278) | 2022 | PACT：用于新兴集成和冷却技术的可扩展并行热模拟器 | 物理设计、光刻、热和布局收敛 | tool_benchmark | impact_unverified |
| [TCAD-2022-P0303](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0303) | 2022 | INCAME：用于多机器人探索的可中断 CNN 加速器 | 神经/边缘加速器和硬件-软件协同设计 | 前沿 | impact_unverified |
| [TCAD-2022-P0386](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0386) | 2022 | 用于 FPGA 模拟/混合信号集成电路设计仿真的开源框架 | HLS、FPGA 和可重构硬件生成 | tool_benchmark | impact_unverified |
| [TCAD-2022-P0449](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0449) | 2022 | 用于在基于 ReRAM 的架构上加速基于 Transformer 的语言模型的框架 | Transformer 和 LLM 注意力加速 | 前沿 | impact_unverified |

完整的evidence rows位于 `TCAD_paper_evidence_matrix.csv` 中。每行都有 WHY/HOW/WHAT/IMPACT/EVIDENCE。引用计数是查询日期为 2026-06-27 的 Crossref 和 Semantic Scholar 索引信号；除非存在来源 URL，否则采用不会被视为已验证。

## 7. 开发信号

- HLS/FPGA 和可重构硬件的生成在 2016-2026 年期间通过 HLS 调查/状态/DSE 行、FPGA 仿真和 FPGA 基准或 LLM 推理行可见。
- CIM/PIM 基准测试和神经形态评估出现在 2018 年、2021 年、2023 年和 2026 年的evidence rows中。该 claim 是 TCAD 可见性和基准/工具框架，而不是经过验证的社区标准化。
- Transformer/LLM 加速从 2022 年开始出现。 2026 行仅是前沿/部分信号。
- 神经渲染正好出现在两行中，NeRF-PIM 和神经渲染加速。这是直接与用户相关的证据，但仍不足以形成稳定的 TCAD 趋势。
- AI 为 EDA/LLM 辅助的 CAD 由 CircuitNet、光刻热点检测、RTLCoder 和 LayoutCopilot 表示。共同的问题是设计自动化任务，而不是广泛的 AI 标签。

## 8. 团队线索

团队信息在第二波文件中保留作者字符串级别。该报告不会对团队进行排名，也不会推断隶属时间表。这些是实体审计的指针，而不是团队实力 claim。

| 团队/作者线索 | 关联方向 | 证据状态 | 使用限制 |
|---|---|---|---|
| Pan / Lin 物理设计行 | physical design | 第二波文件中的作者字符串级别信号 | 只作为实体审计指针；不做排名 |
| NeuroSim / SpikeSim CIM 行 | CIM、simulation | 第二波文件中的作者字符串级别信号 | 不推断隶属时间表；不写成团队实力 claim |
| LLM / RTL / layout 行 | LLM-for-EDA、RTL、layout | 第二波文件中的作者字符串级别信号 | 只作为后续信号；需要实体审计 |

## 9. 与用户方向的连接点

TCAD 与 3DGS/神经渲染/FPGA/加速器方向的连接分两类。直接连接是 [TCAD-2024-P0120](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0120) 和 [TCAD-2025-P0308](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0308)，它们说明 neural rendering 已经进入 TCAD 的 hardware/software co-design 语境，但样本只有两篇。方法连接更宽：HLS/FPGA、CIM/PIM benchmarking、Transformer/LLM acceleration、AI for EDA 和 physical-design closure 都能给 3DGS/FPGA 工作提供评价、工具链和设计闭环参照。

## 10. 缺失来源

- IEEE Xplore TCAD 2016-2026 full article export、abstract、author affiliation 和 IEEE terms。
- DBLP stream API / Crossref / IEEE Xplore 三方 reconciled metadata table。
- DAC/ICCAD/DATE/ASP-DAC 与 TCAD 的 topic 对照矩阵。
- 各团队的 paper-time affiliation、DBLP PID disambiguation 和 coauthor graph。
- NeRF/neural rendering/3DGS 相关 rows 的 full-paper audit、artifact/code audit 和 adoption audit。
- AI for EDA / LLM-assisted CAD 的 artifact 运行、benchmark 标准化和真实使用证据。
