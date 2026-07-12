# CICC 论文图谱分析

## 1. 会议定位

`CICC` 指 IEEE Custom Integrated Circuits Conference。本项目把它作为 custom IC、AMS、SoC、wireline/RF、power、sensor、CIM 和小型加速器硅实现的来源。它不替代 ISCA/MICRO/HPCA 这类体系结构会议；它提供的是电路实现、测量指标和芯片边界条件 <a id="CICC-001-C001"></a>[CICC-001-C001](#CICC-001-C001)。

## 2. 数据来源与 第二轮 覆盖

本轮仍覆盖 2016-2026。`papers.csv` 有 `1232` 行，其中 `1231` 行带 DOI。唯一不带 DOI 的行是 2016 coverage marker；2016 accepted-paper title list 仍未找到可靠来源 <a id="CICC-001-SW004"></a>[CICC-001-SW004](#CICC-001-SW004)。2017-2026 主体来自 DOI/Crossref/IEEE proceedings metadata，官方 program 和 CICC 页面只在可核验处作为锚点使用。

第二轮 新增或重写了三类输出：全量 screening matrix、paper evidence matrix 和 subfield deep dive <a id="CICC-001-SW001"></a>[CICC-001-SW001](#CICC-001-SW001)<a id="CICC-001-SW005"></a>[CICC-001-SW005](#CICC-001-SW005)。所有 CSV 的不确定事实保留 `needs_review`、`conflicting` 或 `impact_unverified`。

| 年 | paper rows |
| --- | --- |
| 2016 | 1 |
| 2017 | 130 |
| 2018 | 112 |
| 2019 | 126 |
| 2020 | 84 |
| 2021 | 90 |
| 2022 | 98 |
| 2023 | 122 |
| 2024 | 144 |
| 2025 | 154 |
| 2026 | 171 |

## 3. 全量筛选结果

筛选覆盖 papers 和 awards 两张表，共 `1251` 行。决定只使用四个值：`deep_read`、`index_only`、`exclude_non_main`、`needs_review`。

| 决策 | rows |
| --- | --- |
| deep_read | 70 |
| exclude_non_main | 24 |
| index_only | 1136 |
| needs_review | 21 |

`exclude_non_main` 主要是 2016 marker、Program-at-a-Glance/front-matter 和 2017 session-heading 行。`needs_review` 包括重复标题候选、award coverage marker 和 [CICC-2019-A005](../../10_corpus/CICC/id_index.md#CICC-2019-A005) 的标题指标冲突。

## 4. 主题和 subfield

第一轮大类聚类仍只作为索引入口。不能把 RF、EDA、IC、FPGA、HPC 这类大领域词直接写成主 topic。第二轮 后的分析转向更窄的研究问题：CIM/LLM memory-centric execution、edge AI processors、eFPGA/chiplet silicon endpoint、3D vision/rendering accelerators、compute-load power delivery、wireline/RF/clocking、biomedical interfaces、PQC/ZKP/security，以及 data converter / CIM benchmarking。

| 簇 | rows | 地位 |
| --- | --- | --- |
| CICC-C02 | 258 | 临时 |
| CICC-C03 | 190 | 临时 |
| CICC-C01 | 165 | 临时 |
| CICC-C10 | 149 | 临时 |
| CICC-C04 | 136 | 临时 |
| CICC-C05 | 97 | 临时 |
| CICC-C07 | 92 | split_candidate |
| CICC-C06 | 60 | split_candidate |
| CICC-C08 | 43 | 临时 |
| CICC-C11 | 28 | 临时 |
| CICC-C12 | 7 | 临时 |
| CICC-C09 | 6 | 临时 |
| 空白 | 1 | coverage_marker |

更细的路线见 `20_venue_reports/CICC/subfields.md`。这些 subfields 是 title、metadata、abstract、PDF 和 artifact-docs 混合深度；除单独标注外不写成 adoption 或 full-text lineage。

## 5. Awards 复核

Canonical award sources 目前只确认 2019 和 2026：CICC 2019 Award Winners archive 和 CICC 2026 Award Winners 页面 [CICC-001-A001..CICC-001-A010]<a id="CICC-001-SW003"></a>[CICC-001-SW003](#CICC-001-SW003)。2020-2025 没有找到稳定公开的官方 award-winner 页面，coverage marker 仍是 `needs_review`，不能解读成那些年份没有奖项。

第二轮 已把 2019 和 2026 可对齐奖项回填到 paper_id/DOI。[CICC-2019-A005](../../10_corpus/CICC/id_index.md#CICC-2019-A005) 仍为 `conflicting`：官方 award title 写 97.7dB SNDR，DOI paper title 写 79.7dB SNDR。这个冲突没有裁决，等待官方 program/PDF 或 IEEE 详情页复核。

| 年 | 奖项 | 标题 | paper_id | doi | 地位 | 冲突 |
| --- | --- | --- | --- | --- | --- | --- |
| 2016 | 奖项/来源覆盖范围标记 | 在本次运行中找到可靠的 CICC 2016 年获奖者来源 | needs_review | needs_review | needs_review | 无 |
| 2017 | 奖项/来源覆盖范围标记 | 没有可靠的 CICC 在本次运行中找到 2017 年获奖者来源 | needs_review | needs_review | needs_review | 无 |
| 2018 | 奖项/来源覆盖范围标记 | 无可靠CICC 2018 年获奖者来源在此运行中找到 | needs_review | needs_review | needs_review | 无 |
| 2019 | 杰出普通纸 | A 20.1 -uW 1.8 GHz 近场电介质体积描记法 (NF-DPG) 带时间 B 的心率传感器 | [CICC-2019-P0029](../../10_corpus/CICC/id_index.md#CICC-2019-P0029) | 10.1109/cicc.2019.8780179 | 已验证 | 无 |
| 2019 | 杰出邀请论文 | 高分辨率太赫兹成像全集成解决方案 | [CICC-2019-P0102](../../10_corpus/CICC/id_index.md#CICC-2019-P0102) | 10.1109/cicc.2019.8780262 | 已验证 | author_spelling_variant |
| 2019 | 优秀学生论文奖 | A 具有嵌入式可调谐 IIR 均衡滤波器的基于 12.8-Gbaud ADC 的 NRZ/PAM4 接收器实现 | [CICC-2019-P0018](../../10_corpus/CICC/id_index.md#CICC-2019-P0018) | 10.1109/cicc.2019.8780118 | 已验证 | 无 |
| 2019 | 优秀学生论文奖 | A 1.2 V Single Supply Hybrid Current-/Voltage-Mode Three-Way Digital Doherty PA with Built-In Large-Signal Phase Compensation Achieving Less-Than 5 AM-PM | [CICC-2019-P0011](../../10_corpus/CICC/id_index.md#CICC-2019-P0011) | 10.1109/cicc.2019.8780290 | 已验证 | author_spelling_variant |
| 2019 | 优秀学生论文奖 | A 0.9V，97.7dB SNDR， 2MHZ-BW，高度线性 OTA-less 1-1 MASH VCO 基于 ADC，具有新颖的相位 | [CICC-2019-P0001](../../10_corpus/CICC/id_index.md#CICC-2019-P0001) | 10.1109/cicc.2019.8780126 | 冲突 | title_metric_conflict |
| 2019 | 最佳论文奖 | 具有集成零偏置浮栅传感器和 861nW 的可穿戴实时 CMOS 剂量计 | [CICC-2019-P0074](../../10_corpus/CICC/id_index.md#CICC-2019-P0074) | 10.1109/cicc.2019.8780182 | 已验证 | 无 |
| 2020 | 奖项/来源覆盖范围标记 | 在此运行中未找到可靠的 CICC 2020 获奖者来源 | needs_review | needs_review | needs_review | 无 |
| 2021 | 奖项/来源覆盖范围标记 | 在此运行中未找到可靠的 CICC 2021 获奖者来源 | needs_review | needs_review | needs_review | 无 |
| 2022 | 奖项/来源覆盖范围标记 | 在此运行中未找到可靠的 CICC 2022 获奖者来源这次跑步 | needs_review | needs_review | needs_review | 无 |
| 2023 | 奖项/来源覆盖范围标记 | 本次运行中未找到可靠的 CICC 2023 年获奖者源 | needs_review | needs_review | needs_review | 无 |
| 2024 | 奖项/来源覆盖范围标记 | 本次运行中未发现可靠的 CICC 2024 年获奖者源 | needs_review | needs_review | needs_review | 无 |
| 2025 | 奖项/来源覆盖范围标记 | 本次运行中未发现可靠的 CICC 2025 年获奖者源 | needs_review | needs_review | needs_review | 无 |
| 2026 | 最佳论文奖 | A 3-4.2V-to-Sub-1V双相多路径-NLDO Sigma 转换器实现 | [CICC-2026-P0062](../../10_corpus/CICC/id_index.md#CICC-2026-P0062) | 10.1109/cicc65509.2026.11509495 | 已验证 | 无 |
| 2026 | 优秀学生论文奖 | A 14GHz 16 相免校准小数 N 环-PLL 的 50ns 恢复时间使用相位和电压的 118fs 抖动 | [CICC-2026-P0029](../../10_corpus/CICC/id_index.md#CICC-2026-P0029) | 10.1109/cicc65509.2026.11509515 | 已验证 | 无 |
| 2026 | 优秀学生论文奖 | A 16nm 0.67pJ/bit 80Mb/s 电路系统协同优化时域脑通道接收器 | [CICC-2026-P0032](../../10_corpus/CICC/id_index.md#CICC-2026-P0032) | 10.1109/cicc65509.2026.11509547 | 已验证 | 无 |
| 2026 | 优秀学生论文奖 | 刺激器效率为 87.4% 的同步 16 通道绝热电荷跟踪刺激器 | [CICC-2026-P0119](../../10_corpus/CICC/id_index.md#CICC-2026-P0119) | 10.1109/cicc65509.2026.11509506 | 已验证 | 无 |

## 6. Deep-read evidence 和影响力初审

Evidence matrix 有 `61` 篇 paper-level deep_read 行。每行包含 WHY/HOW/WHAT/IMPACT/EVIDENCE。当前 read depth 分布为 `4` 行 full_pdf、`25` 行 abstract、`2` 行 pdf_section、`1` 行 abstract+artifact_docs、`1` 行 artifact_docs、`5` 行 abstract_metadata、`15` 行 title_metadata 和 `8` 行 title [CICC-001-SW005](#CICC-001-SW005)。

影响力初审仍是保守状态：`59/61` 行记录了 Crossref 或 Semantic Scholar citation signal，检索日期均写为 `2026-06-27`，但 citation structure、artifact/code reuse、benchmark standardization 和 industry/toolchain adoption 大多没有完成 <a id="CICC-001-SW006"></a>[CICC-001-SW006](#CICC-001-SW006)。因此 citation 只作为初审信号，不写成确定影响力。

## 7. 发展脉络

- CIM/analog-AI 线：2017 analog in-memory DNN、2022 DCT-RAM、2024 Quartet、2025 FlashAttention/DCIM、2026 D2CIM/TOKCIM 给出一条 mixed title/abstract/PDF evidence 的 CIM-to-LLM 线索 <a id="CICC-001-SW007"></a>[CICC-001-SW007](#CICC-001-SW007)<a id="CICC-001-SW008"></a>[CICC-001-SW008](#CICC-001-SW008)。
- Edge AI processor 线：BinarEye、sparsity-adaptive CNN/Transformer processor、BF16 LLM fine-tuning processor、edge SLM decoder 和 TACC 支撑一个 processor 变化；BinarEye 有 full-PDF evidence，edge SLM decoder 有 public slides signal <a id="CICC-001-SW009"></a>[CICC-001-SW009](#CICC-001-SW009)。
- HLS/eFPGA/chiplet 线：HL5、AIB/Stratix chiplet、CIFER/DECADES、synthesized-eFPGA RISC-V SoC 和 Occamy/open-source chiplet discussion 是 FPGA/HLS 方向的 silicon-endpoint hook；HL5 有 open-PDF evidence，但 artifact reuse 仍未验证 <a id="CICC-001-SW010"></a>[CICC-001-SW010](#CICC-001-SW010)。
- 3D vision/neural rendering/robotics 线：FPGA stereo、FPGA neural volume rendering、BEV/point-cloud processors、BEE-SLAM、optical flow 和 chiplet rendering processor 是低覆盖但直接相关的 cross-venue hook；其中 [CICC-2024-P0007](../../10_corpus/CICC/id_index.md#CICC-2024-P0007) 有 open-PDF FPGA neural volume rendering evidence <a id="CICC-001-SW011"></a>[CICC-001-SW011](#CICC-001-SW011)。
- Power 线：2017 integrated transformer converter 到 2025/2026 point-of-load、HBM jitter 和 Unicorn clock/power SoC，显示 compute-load constraints 进入 CICC power titles/abstracts；2026 Best Paper power row 有官方奖项来源和 abstract-level evidence <a id="CICC-001-SW012"></a>[CICC-001-SW012](#CICC-001-SW012)。

这些都是多篇论文或跨年份 evidence。它们不是 citation/adoption 结论。

## 8. 团队线索

第二轮保留团队线索但不排名。

| 线索范围 | 信号类型 | 当前缺口 | 使用限制 | claim |
|---|---|---|---|---|
| CICC report 中的 team signals | author-string 或 prior-report hints | 未做 affiliation disambiguation；未核验当前机构迁移 | 只能作为后续人工核查入口，不能写成团队排名 | <a id="CICC-001-C014"></a>[CICC-001-C014](#CICC-001-C014)；[CICC-001-SW005](#CICC-001-SW005) |

## 9. Issue audit 状态

| 发出 | 地位 | 决议 |
| --- | --- | --- |
| <a id="CICC-SW-I001"></a>[CICC-SW-I001](#CICC-SW-I001) | still_open | 2016 接受论文标题列表仍未解决；找不到可靠的官方/proceedings标题来源。parent agent 保留标记并将其排除在技术筛选之外。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I002"></a>[CICC-SW-I002](#CICC-SW-I002) | partially_resolved | DOI 覆盖范围、目标会话/源回填、筛选矩阵和证据矩阵已更新；选定的行现在具有摘要/PDF/artifact-doc 深度，但 IEEE 批次摘要、关键字、PDF、从属关系和团队消歧仍然开放。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I003"></a>[CICC-SW-I003](#CICC-SW-I003) | partially_resolved | 官方节目anchor和选定的会议/奖项页面来源被记录为 18 个选定的paper rows；在线proceedings仍然受到访问限制，并且没有被绕过。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I004"></a>[CICC-SW-I004](#CICC-SW-I004) | partially_resolved | 编写了全面筛选和论文级证据矩阵； 61 deep_read paper rows现在包括 WHY/HOW/WHAT/IMPACT/EVIDENCE 以及混合的 title_metadata、摘要、PDF 和 artifact 文档深度。全文聚类仍然开放。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I005"></a>[CICC-SW-I005](#CICC-SW-I005) | partially_resolved | 2019/2026 奖项尽可能与 paper_id/DOI 保持一致； 2020-2025 年规范获奖者页面仍未解决，[CICC-2019-A005](../../10_corpus/CICC/id_index.md#CICC-2019-A005) 保留标题度量冲突。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I006"></a>[CICC-SW-I006](#CICC-SW-I006) | still_open | 团队线索仅保留为 needs_review/字符串级音符；没有进行姓名或隶属关系消歧。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I007"></a>[CICC-SW-I007](#CICC-SW-I007) | still_open | 2016 年可靠的接受论文/会议录标题列表仍然缺失。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I008"></a>[CICC-SW-I008](#CICC-SW-I008) | partially_resolved | 为 2019/2020/2021/2022/2025/2026 代表行添加了选定的官方计划/会议回填；完整的 2017-2026 年页面级会话提取仍然开放。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I009"></a>[CICC-SW-I009](#CICC-SW-I009) | still_open | 2020-2025 官方获奖者/会议记录获奖页面未恢复；覆盖标记仍为 needs_review。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I010"></a>[CICC-SW-I010](#CICC-SW-I010) | partially_resolved | DOI、选定的官方/会话元数据以及 deep_read 行的尽力而为的摘要/PDF/artifact 证据均经过审计； IEEE 批量摘要、隶属关系和 PDF 页面提取保持开放状态。没有发现 CICC 的纯 normal_2026_partial 问题。 |
| <a id="CICC-SW-I011"></a>[CICC-SW-I011](#CICC-SW-I011) | still_open | cross-venue同筹扩展仅被认为是一个钩子；没有完成 ISSCC/JSSC/VLSI/CICC 沿袭审计。没有发现 CICC 的纯 normal_2026_partial 问题。 |

没有纯 `normal_2026_partial` issue。2026 相关条目要么已有 DOI/官方页，要么是 access-restricted、impact_unverified 或 source-audit gap。

## 10. 缺少来源

- 2016 CICC 可靠的已接受论文/会议论文集标题列表。
- 2020-2025 官方 award winners 页面或 proceedings award page。
- IEEE Xplore abstract/PDF/affiliation 批量来源。
- 2017-2026 官方 program PDF 的完整 session extraction 与 Crossref matching。
- Deep_read 论文的 citation-structure、artifact/code reuse、benchmark standardization 和 industry/toolchain adoption sources；目前 citation count 多数已记录但未做结构化引用链审计。

## 11. 与用户方向的连接点

CICC 对 FPGA/加速器方向的价值主要是 silicon endpoint：CIM macro、edge AI processors、chiplet/eFPGA SoC、wireline/optical I/O、compute-load power delivery、sensor interface 和 security processors。对 3DGS/neural rendering，目前有 [CICC-2024-P0007](../../10_corpus/CICC/id_index.md#CICC-2024-P0007) 的 FPGA neural volume rendering open-PDF evidence，以及 optical flow、BEV/point-cloud 和 chiplet rendering rows；这适合进入跨会议 hook，不适合写成 CICC 主线。
