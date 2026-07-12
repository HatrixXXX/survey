# ISCA 论文图谱分析

## 1. 会议定位

本报告中的 `ISCA` 指 International Symposium on Computer Architecture。本项目把它作为计算机体系结构核心来源，覆盖 processors、memory systems、accelerators、datacenter architecture、architecture evaluation、security/correctness 和 emerging architectures。这里的 architecture 是来源边界，不是最终 topic 标签。对应 claim <a id="ISCA-001-C001"></a>[ISCA-001-C001](#ISCA-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。2016-2025 主体来自 DBLP/proceedings metadata，并按 Crossref、DOI、官方 award 页面做 targeted backfill；2026 来自 ISCA 2026 官方 program，仍是 pre-proceedings partial。当前 `papers.csv` 有 957 行，`awards.csv` 有 24 行，`ISCA_screening_matrix.csv` 有 981 行，`ISCA_paper_evidence_matrix.csv` 有 40 行。

| 年份 | papers.csv 记录数 | 状态 |
|---|---:|---|
| 2016 | 58 | 完全的 |
| 2017 | 54 | 完全的 |
| 2018 | 65 | 完全的 |
| 2019 | 62 | 完全的 |
| 2020 | 83 | 完全的 |
| 2021 | 82 | 完全的 |
| 2022 | 74 | 完全的 |
| 2023 | 84 | 完全的 |
| 2024 | 88 | 完全的 |
| 2025 | 135 | 完全的 |
| 2026 | 172 | partial |

本轮修正了三个数据问题：2017 年若干 DOI 由 Crossref backfill；6 条 proceedings/front-matter volume row 改为 `front_matter` 并在 screening 中排除；[ISCA-2019-P0062](../../10_corpus/ISCA/id_index.md#ISCA-2019-P0062) 补作者，同时记录 Crossref retraction 风险。对应 claim <a id="ISCA-001-C065"></a>[ISCA-001-C065](#ISCA-001-C065) 和 <a id="ISCA-001-C066"></a>[ISCA-001-C066](#ISCA-001-C066)。

## 3. Awards 复核

`awards.csv` 保留 2016-2025 的 SIGARCH/TCCA Influential ISCA Paper Award 行；这些多为历史 test-of-time 论文，不属于 2016-2026 accepted-paper corpus，因此不硬填 `paper_id`。ISCA Best Paper Award 使用 SIGARCH/ISCA 官方 source：2022 NvMR、2023 Contiguitas/SCALO、2024 Constable、2025 Precise exceptions 和 H2-LLM。2025 honorable mentions 保留 XOR Cache 与 Rethinking Prefetching。

本轮新增两条 2023 artifact award 行：RowPress 和 RoSE。来源是 SIGARCH 的 2023 ISCA awards-recipient post；RoSE 的作者字符串在 official page 与 DBLP/papers.csv 之间有 Chris/Kris 变体，已标为 minor conflict。对应 claim <a id="ISCA-001-C064"></a>[ISCA-001-C064](#ISCA-001-C064)。

2016-2021 Best Paper 不再作为缺失 winner rows 继续推进：官方 Best Paper Award page 的 past winners 从 2022 开始，2022 SIGARCH trip report 也把 2022 称为 inaugural ISCA Best Paper Award。当前处理是不补猜测行，只在 缺失来源 中保留“若后续发现更早官方 list，再复核”。对应 claim <a id="ISCA-001-C063"></a>[ISCA-001-C063](#ISCA-001-C063)。

## 4. Venue 内小领域

| 子领域 | 代表问题 | 代表论文 |
|---|---|---|
| 稀疏/空间 DNN 数据流 | CNN/DNN 中稀疏性、数据复用、PE 利用率和片上存储如何共同决定能效 | Cnvlutin；艾里斯； EIE； SCNN |
| 生产张量加速器 | 生产级 ML accelerator 如何处理服务延迟、互连、embedding、TCO 和部署约束 | TPU； TPUv4i 课程； TPU v4； TSP |
| 编译器/模拟器/artifact 评估 | 架构主张如何通过 compiler、simulator、DSE 和 artifact 复核 | 橡皮泥；火模拟； Accel-Sim； AIO；火斧； DAM； CODO; RoSE |
| NeRF/3DGS/神经渲染 | neural rendering、NeRF、3DGS 和 scene representation 的实时/端侧瓶颈如何被硬件支持 | NeuRex；神经图形的硬件加速；卢米娜； FlexNeRFer； NeRAch-Sim；高追踪器； 3DGS 行 |
| LLM/基础模型内存和执行 | LLM/RAG 的 state、PIM、quantization、low-batch 和 FPGA mixed precision 如何协同优化 | H2-LLM；异构体；显微镜； MLX； COSM; XtraMAC |
| 内存可靠性/缓存/间歇 | DRAM disturbance、物理连续性、cache compression 和 intermittent NVM/prefetch 如何影响性能与正确性 | RowPress；连续性； XOR 缓存；核磁共振；重新思考预取 |
| 正确性/语义/专业系统 | 架构优化如何处理语义、安全边界、quantum/VQA 或 BCI 等专用系统约束 | 警员；精确的例外情况；俄罗斯方块； SCALO |

详细 WHY/HOW/WHAT/IMPACT/EVIDENCE 见 `ISCA_paper_evidence_matrix.csv`，小领域 deep dive 见 `subfields.md`。

## 5. 代表性论文和影响力初审

本轮只把 citation/adoption/artifact 当影响力线索，不把 citation count 直接写成里程碑结论。检索日期均为 2026-06-27。

- TPU production line：In-Datacenter TPU 的 OpenAlex `cited_by_count=4424`，并与 TPUv4i lessons、TPU v4 构成生产系统 evidence chain。对应 claim <a id="ISCA-001-C067"></a>[ISCA-001-C067](#ISCA-001-C067)。
- FireSim 与 Accel-Sim：两者都有公开 project/GitHub 信号，适合作为 artifact-backed evaluation 入口。对应 claim <a id="ISCA-001-C068"></a>[ISCA-001-C068](#ISCA-001-C068) 和 <a id="ISCA-001-C069"></a>[ISCA-001-C069](#ISCA-001-C069)。
- Neural rendering/3DGS：2023 NeuRex/Hardware Acceleration of Neural Graphics、2025 Lumina/FlexNeRFer/Cambricon-SR、2026 NeRArch-Sim/GauTracer/3DGS official-program rows 支撑“ISCA 内出现连续前沿信号”，但 2026 仍 partial。对应 claim <a id="ISCA-001-C070"></a>[ISCA-001-C070](#ISCA-001-C070)。
- LLM/GenAI：H2-LLM 有 official Best Paper 和 GitHub repo；CODO、XtraMAC 作为 2026 official-program/arXiv/repo 信号记录，不写 final proceedings 事实。对应 claim <a id="ISCA-001-C071"></a>[ISCA-001-C071](#ISCA-001-C071) 到 <a id="ISCA-001-C073"></a>[ISCA-001-C073](#ISCA-001-C073)。
- Artifact award：2024 Tetris、FireAxe、DACAPO、DAM 由 ISCA 2024 official page 确认；2023 RowPress/RoSE 由 SIGARCH 2023 post 确认。artifact award 不等于已复现。

## 6. 与用户方向的连接点

对 3DGS、neural rendering、FPGA 和 accelerator 方向，ISCA 的价值主要有三类：

1. 方法迁移：Eyeriss、SCNN、TPU、TSP、H2-LLM 等论文提供从 workload profiling 到 dataflow、memory、precision 和 evaluation 的写作/实验框架。
2. 直接技术线：NeuRex、Hardware Acceleration of Neural Graphics、Lumina、FlexNeRFer、NeRArch-Sim、GauTracer 和 2026 3DGS row 形成 neural rendering/3DGS 的 ISCA 内部线索。
3. 工具和可复核性：FireSim、Accel-Sim、FireAxe、DAM、CODO、RoSE 提醒后续 3DGS/FPGA 工作需要同时记录 simulator、artifact、baseline 公平性和可运行状态。

## 7. 团队线索

只记录线索，不做排名。所有团队线索都需要后续 author entity 和 affiliation timeline 消歧。

| 团队/机构线索 | 关联方向 | 证据状态 | 使用限制 |
|---|---|---|---|
| Google TPU | production tensor accelerator、datacenter ML system | team_signal | 需要 author entity 和 affiliation timeline 消歧；不做排名 |
| MIT / Sze / Emer | accelerator dataflow、edge/efficient ML hardware | team_signal | 需要 author entity 和 affiliation timeline 消歧；只作为阅读入口 |
| Stanford / Olukotun | architecture、parallel systems、accelerator-adjacent work | team_signal | 需要 author entity 和 affiliation timeline 消歧；不写成强弱判断 |
| UC Berkeley FireSim / FireAxe | simulation、FPGA-accelerated architecture research | project/team_signal | 需要 author entity 和 affiliation timeline 消歧；不做排名 |
| UBC / Purdue Accel-Sim | GPU simulation、accelerator simulation | project/team_signal | 需要 author entity 和 affiliation timeline 消歧；只作为论文入口 |
| CAS / Cambricon | accelerator architecture、AI hardware | institution/team_signal | 需要 author entity 和 affiliation timeline 消歧；不写成团队排名 |
| SJTU / Yuhao Zhu / CODO / H2-LLM / Lumina 相关作者集群 | graphics/vision/LLM accelerator-adjacent work | author cluster signal | 需要 author entity 和 affiliation timeline 消歧；只作为阅读入口 |
| Onur Mutlu-linked line | DRAM、memory reliability | author-linked signal | 需要 author entity 和 affiliation timeline 消歧；不做排名 |
| Cambridge / Edinburgh / Aarhus | architecture semantics | institution-string signal | 需要 author entity 和 affiliation timeline 消歧；只作为方向入口 |

## 8. 缺失来源

- 2026 final proceedings、ACM/IEEE DOI、official award outcome 和 artifact outcome。
- ACM DL/IEEE Xplore 批量 abstract、keywords、PDF、artifact badge metadata。
- RoSE、Tetris、DACAPO、DAM、FireAxe 的 artifact package 精确 URL、版本和可运行状态。
- Contiguitas Linux upstream、FireAxe upstream 到 FireSim、Precise exceptions 工具/规范采纳等后续 adoption 证据。
- MICRO/HPCA/ASPLOS/FPGA/FCCM/FPL/graphics venues 的跨会议对照矩阵。
