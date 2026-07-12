# Hot Chips 论文图谱分析

## 1. 会议定位

本报告中的 `HOTCHIPS` 指 Hot Chips: A Symposium on High Performance Chips。它在本项目中不是按传统 peer-reviewed accepted-paper venue 处理，而是作为工业界和研究界公开高性能芯片、系统架构、封装、互连、内存和基础设施路线的 disclosure venue。它适合观察 AI accelerator、GPU/TPU/NPU、server CPU、DPU/SmartNIC、CXL/PIM、chiplet/UCIe、光互连、移动/汽车 SoC、实时 3D/神经渲染和 rack-scale AI infrastructure 如何从单芯片叙事扩展到平台叙事。对应 claim <a id="HOTCHIPS-001-C001"></a>[HOTCHIPS-001-C001](#HOTCHIPS-001-C001)、<a id="HOTCHIPS-001-SW004"></a>[HOTCHIPS-001-SW004](#HOTCHIPS-001-SW004)。

## 2. 数据来源与覆盖范围

覆盖范围是 2016-2026。`papers.csv` 的主来源是 Hot Chips 官方 program/archive 页面；DBLP、DOI/IEEE proceedings index、官方 PDF、官方 TCMM award PDF、公开 repository 和 benchmark 页面只作为补充证据。按照 第二轮 口径，主表聚焦 main conference program presentations/keynotes/memorial items；tutorial、poster 和 award 信号在筛选与 evidence matrix 中单独标注，不强行改写成传统 accepted paper。2026 来源是 advance program，所有 2026 行按 `partial` 处理。对应 claim <a id="HOTCHIPS-001-C002"></a>[HOTCHIPS-001-C002](#HOTCHIPS-001-C002) 到 <a id="HOTCHIPS-001-C004"></a>[HOTCHIPS-001-C004](#HOTCHIPS-001-C004)、<a id="HOTCHIPS-001-SW003"></a>[HOTCHIPS-001-SW003](#HOTCHIPS-001-SW003)。

| 年份 | 论文.csv 行 | 状态 |
| --- | ---: | --- |
| 2016 | 38 | 完全的 |
| 2017 | 30 | 完全的 |
| 2018 | 42 | 完全的 |
| 2019 | 28 | 完全的 |
| 2020 | 33 | 完全的 |
| 2021 | 44 | 完全的 |
| 2022 | 56 | 完全的 |
| 2023 | 47 | 完全的 |
| 2024 | 30 | 完全的 |
| 2025 | 36 | 完全的 |
| 2026 | 40 | partial |

## 3. 第二轮 输出

本轮完成三个层次的补充：metadata/issue 复核、全量 screening、deep-read impact 初审。最终写入：

- `10_corpus/venues/HOTCHIPS/papers.csv`: 保留 424 行，并对若干 2024-2025 IEEE/DOI 可验证行补 DOI、PDF/official URL 和 notes。
- `10_corpus/venues/HOTCHIPS/awards.csv`: 保留 16 行；2024/2025 TCMM award PDF 可验证行标为 `verified`，Basilisk Best Student Poster Award 对齐到 [HOTCHIPS-2025-P0022](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0022)。
- `HOTCHIPS_screening_matrix.csv`: 440 行，覆盖 424 paper rows + 16 award rows。筛选决策分布：`{'needs_review': 57, 'deep_read': 117, 'index_only': 248, 'exclude_non_main': 18}`。对应 claim <a id="HOTCHIPS-001-SW001"></a>[HOTCHIPS-001-SW001](#HOTCHIPS-001-SW001)。
- `HOTCHIPS_paper_evidence_matrix.csv`: 117 行，包含 WHY/HOW/WHAT/IMPACT/EVIDENCE 字段。对应 claim <a id="HOTCHIPS-001-SW002"></a>[HOTCHIPS-001-SW002](#HOTCHIPS-001-SW002)。
- `20_venue_reports/HOTCHIPS/subfields.md`: 写入 13 个 venue-local subfields、趋势证据、团队线索和跨会议 hooks。

Issue audit 处理结果分布：`{'wont_fix': 1, 'partially_resolved': 6, 'normal_2026_partial': 2, 'still_open': 2}`。纯 2026 partial 已标为 `normal_2026_partial`；混合缺口只把 2026 partial 部分视为正常，其余继续保留处理状态。

## 4. Venue-Local 小领域

| subfield_id | 子领域 | evidence rows | 活跃年数 | 代表行 |
| --- | --- | ---: | --- | --- |
| [HOTCHIPS-SF01](subfields.md#HOTCHIPS-SF01) | 数据中心 AI 加速器平台扩展 | 12 | 2016-2026 | [HOTCHIPS-2017-P0004](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2017-P0004)、[HOTCHIPS-2020-P0025](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2020-P0025)、[HOTCHIPS-2024-P0015](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0015)、[HOTCHIPS-2025-P0018](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0018)、[HOTCHIPS-2026-P0031](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0031) |
| [HOTCHIPS-SF02](subfields.md#HOTCHIPS-SF02) | LLM 内存/状态/推理经济学 | 16 | 2024-2026 | [HOTCHIPS-2024-P0016](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0016)、[HOTCHIPS-2025-P0028](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0028)、[HOTCHIPS-2026-P0003](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0003)、[HOTCHIPS-2026-P0032](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0032) |
| [HOTCHIPS-SF03](subfields.md#HOTCHIPS-SF03) | 空间/数据流和晶圆级 AI 系统 | 8 | 2016-2025 | [HOTCHIPS-2017-P0025](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2017-P0025)、 [HOTCHIPS-2022-P0019](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0019)、[HOTCHIPS-2023-P0038](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0038)、[HOTCHIPS-2025-P0034](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0034) |
| [HOTCHIPS-SF04](subfields.md#HOTCHIPS-SF04) | PIM、CXL 和 AI 内存墙的近内存计算 | 9 | 2021-2026 | [HOTCHIPS-2021-P0039](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2021-P0039)、[HOTCHIPS-2022-P0004](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0004)、[HOTCHIPS-2022-P0029](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0029)、[HOTCHIPS-2026-P0035](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0035) |
| [HOTCHIPS-SF05](subfields.md#HOTCHIPS-SF05) | HBM，小芯片封装和芯片到芯片集成 | 10 | 2016-2026 | [HOTCHIPS-2016-P0022](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2016-P0022)、[HOTCHIPS-2022-P0046](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0046)、[HOTCHIPS-2023-P0008](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0008)、[HOTCHIPS-2023-P0009](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0009) |
| [HOTCHIPS-SF06](subfields.md#HOTCHIPS-SF06) | 光学 I/O 和光子结构，用于 AI 放大 | 15 | 2016-2026 | [HOTCHIPS-2019-P0020](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2019-P0020)、[HOTCHIPS-2023-P0027](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0027)、[HOTCHIPS-2024-P0012](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0012)、[HOTCHIPS-2025-P0007](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0007)、[HOTCHIPS-2026-P0037](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0037) |
| [HOTCHIPS-SF07](subfields.md#HOTCHIPS-SF07) | DPU、SmartNIC 和 AI 数据中心结构卸载 | 12 | 2018-2026 | [HOTCHIPS-2021-P0003](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2021-P0003)、[HOTCHIPS-2024-P0013](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0013)、[HOTCHIPS-2025-P0004](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0004)、[HOTCHIPS-2026-P0038](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0038) |
| [HOTCHIPS-SF08](subfields.md#HOTCHIPS-SF08) | 边缘实时 3D 重建和感知 | 6 | 2016-2026 | [HOTCHIPS-2018-P0013](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2018-P0013)、[HOTCHIPS-2021-P0024](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2021-P0024)、[HOTCHIPS-2022-P0038](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0038)、 [HOTCHIPS-2026-P0022](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0022) |
| [HOTCHIPS-SF09](subfields.md#HOTCHIPS-SF09) | 实时神经渲染和 3DGS 管道硬件 | 3 | 2025 | [HOTCHIPS-2025-P0014](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0014)、[HOTCHIPS-2025-P0015](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0015)、[HOTCHIPS-2025-P0020](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0020) |
| [HOTCHIPS-SF10](subfields.md#HOTCHIPS-SF10) | 开源 EDA 和可重现的 SoC 芯片 | 7 | 2021-2026 | [HOTCHIPS-2024-P0030](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0030)、[HOTCHIPS-2025-P0022](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0022)、[HOTCHIPS-2025-A07](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-A07)、[HOTCHIPS-2024-A03](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-A03)、[HOTCHIPS-2025-A05](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-A05) |
| [HOTCHIPS-SF11](subfields.md#HOTCHIPS-SF11) | FPGA、CGRA 和自适应数据流映射 | 14 | 2016-2026 | [HOTCHIPS-2017-P0005](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2017-P0005)、[HOTCHIPS-2017-P0006](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2017-P0006)、 [HOTCHIPS-2023-P0039](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0039), [HOTCHIPS-2026-P0029](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0029) |
| [HOTCHIPS-SF12](subfields.md#HOTCHIPS-SF12) | 基准、编译器和内核语言方法 | 4 | 2019-2025 | [HOTCHIPS-2019-P0016](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2019-P0016), [HOTCHIPS-2019-P0028](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2019-P0028), [HOTCHIPS-2023-P0005](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0005), [HOTCHIPS-2025-P0036](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0036) |
| [HOTCHIPS-SF13](subfields.md#HOTCHIPS-SF13) | 安全性和信任作为架构约束 | 1 | 2018 | [HOTCHIPS-2018-P0019](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2018-P0019) |

## 5. 影响力初审

影响力初审只写有证据的信号；没有 citation、artifact/code、benchmark、adoption 或 canonical award 来源的行，在 evidence matrix 中保持 `impact_unverified`。

- Citation: Blackwell [HOTCHIPS-2024-P0016](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0016) 记录 Semantic Scholar DOI 查询 `citationCount=44`，检索日期 2026-06-27。Navion、PNNPU、DSPU 等边缘感知行存在 citation 信号但来源或版本冲突，保留 `needs_review`。
- Benchmark: A100 [HOTCHIPS-2020-P0025](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2020-P0025) 以 MLPerf v0.7 records 作为 benchmark-standardization 信号，检索日期 2026-06-27。
- Artifact/code: Samsung CXL Memory Expander 对应 OpenMPDK/SMDK repository；Basilisk/Cheshire IHP130 对应 `pulp-platform/cheshire-ihp130-o` repository，检索日期 2026-06-27。
- Adoption/product-stack: Blackwell、Ironwood、RTX 5090、TPUv4 OCS、MI350 等只在有官方产品/benchmark/论文来源时写 adoption signal；没有独立来源时仍不写成确定产业采纳。
- Awards: 2024/2025 TCMM community/open-source award PDF 是 canonical source；2016-2023 placeholder award rows 没有找到稳定官方奖项页，继续 `needs_review`。对应 claim <a id="HOTCHIPS-001-SW009"></a>[HOTCHIPS-001-SW009](#HOTCHIPS-001-SW009) 到 <a id="HOTCHIPS-001-SW012"></a>[HOTCHIPS-001-SW012](#HOTCHIPS-001-SW012)、<a id="HOTCHIPS-001-SW017"></a>[HOTCHIPS-001-SW017](#HOTCHIPS-001-SW017)。

## 6. 与用户方向的相关性

直接相关主题包括实时 3D reconstruction、neural rendering/3DGS、FPGA/CGRA/adaptive mapping、open-source EDA/reproducible silicon、AI accelerator memory/fabric bottleneck。需要注意，HOTCHIPS 的强项是产业 disclosure 和路线早期信号；如果要建立可复现实验链，应回到 ISCA/MICRO/FPL/DAC/ISSCC/MLSys/SIGGRAPH/CVPR 等 venue 寻找 peer-reviewed methods、工具链和 benchmark。

## 7. 缺失来源

- `normal_2026_partial`: 2026 只来自 advance program，属于正常 partial 覆盖，不作为待修复缺口。
- Awards: 2016-2023 placeholder award rows 尚未找到 canonical official source，继续 `needs_review`，不能写成已验证奖项事实。
- Metadata: Hot Chips 不是统一论文 proceedings；部分 older rows 没有可靠 DOI、abstract、keywords、artifact 或 code source，保留空值/`needs_review`，不猜。
- Impact: citation/adoption/artifact 初审不是排名；所有 citation/adoption 数据都写检索日期，且未验证项保留 `impact_unverified` 或 `needs_review`。

## 8. 文件索引

- 筛选矩阵：`HOTCHIPS_screening_matrix.csv`
- 证据矩阵：`HOTCHIPS_paper_evidence_matrix.csv`
- 小领域深度潜水：`20_venue_reports/HOTCHIPS/subfields.md`
- claim 账本：`20_venue_reports/HOTCHIPS/VENUE-HOTCHIPS-001_claim_ledger.csv`
