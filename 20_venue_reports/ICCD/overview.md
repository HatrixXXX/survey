# ICCD 论文图谱分析

## 1. 会议定位

ICCD 是 IEEE International Conference on Computer Design。本项目把它放在 computer-design / systems 边界里：它比纯体系结构会议更贴近设计实现、测试、可靠性和电路/系统约束，又比 EDA 顶会更常出现处理器、memory system、accelerator、runtime 和 workload-driven co-design。这个定位见 <a id="ICCD-001-C001"></a>[ICCD-001-C001](#ICCD-001-C001)。

对硬件加速和软硬协同来说，ICCD 的价值在中间层：它经常把一个负载或系统问题落到 memory hierarchy、PIM/CIM、FPGA/HLS、NoC、runtime scheduling、test/reliability 和 security 上。它不是 3DGS 或神经渲染的主会，但能提供把新负载拆成数据搬运、低精度、调度、可靠性和可实现性问题的模板。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 使用 Crossref DOI metadata 生成 2016-2025 的 proceedings rows，共 1016 条，年度计数为：{'2016': 107, '2017': 113, '2018': 88, '2019': 94, '2020': 104, '2021': 90, '2022': 108, '2023': 89, '2024': 101, '2025': 122}。`awards.csv` 收录官方 ICCD 页面能确认的 2019、2021、2023、2025 Best Paper winner，以及 2023-2025 Best Paper Candidate 信息，共 17 条。见 <a id="ICCD-001-C002"></a>[ICCD-001-C002](#ICCD-001-C002) 到 <a id="ICCD-001-C004"></a>[ICCD-001-C004](#ICCD-001-C004)。

第二次补充阶段新增三类文件：`ICCD_screening_matrix.csv`、`ICCD_paper_evidence_matrix.csv`、`subfields.md`。screening matrix 覆盖 papers + awards 共 1033 行，decision 分布为 {'index_only': 808, 'deep_read': 46, 'needs_review': 144, 'exclude_non_main': 35}。evidence matrix 对 29 篇 P0 论文写入 WHY/HOW/WHAT/IMPACT/EVIDENCE，见 <a id="ICCD-001-C047"></a>[ICCD-001-C047](#ICCD-001-C047) 和 <a id="ICCD-001-C048"></a>[ICCD-001-C048](#ICCD-001-C048)。

2026 仍标为 `partial`：官方 CFP 的 acceptance notification 晚于 2026-06-27，本轮没有 accepted-paper、program 或 award list。这个缺口已经在 issue audit 中标为 `normal_2026_partial`。

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 语料库行 | 证据状态 |
| --- | --- | --- | ---: | --- |
| T01/T10 | memory_pim_storage_data_movement | 内存系统、PIM、存储和数据移动 | 244 | 临时 |
| T02/T05/T06 | dnn_transformer_llm_accelerators | DNN、Transformer 和 LLM 加速器 | 185 | 临时 |
| T07/T06/T12 | fpga_hls_reconfigurable_mapping | FPGA、HLS 和可重新配置映射 | 95 | 临时 |
| T11/T12 | reliability_security_test_verification | 可靠性、安全性、测试和验证 | 90 | 临时 |
| T07/T12 | eda_synthesis_timing_physical_design | EDA、综合、时序和物理设计 | 62 | 临时 |
| T08/T09/T11 | runtime_processor_gpu_heterogeneous_systems | 运行时、处理器、GPU 和异构系统 | 49 | 临时 |
| T05/T10/T12 | quantum_approx_neuromorphic_emerging | 量子、近似、神经形态和新兴硬件 | 47 | 临时 |
| T11 | benchmarks_modeling_open_tools | 基准、建模和开放工具 | 42 | 临时 |
| T06/T10 | noc_interconnect_multicore_dataflow | NoC、互连、多核和数据流 | 36 | 临时 |

这些 label 仍是 venue-local provisional label。第二次补充没有把 title-level clustering 改成 stable global taxonomy；具体子领域写在 `subfields.md`。

## 4. 第二轮小领域

第二次补充把 ICCD 的可读路线拆成九个小领域：

1. Near-memory and PIM for irregular/stateful workloads：IMPICA、GIM、R2Hash 等，把 pointer chasing、GNN/PIM、persistent-memory index 作为数据移动和随机访问问题处理。
2. FPGA/HLS/可重构加速和RTL生成：CNN-MERP、QNN缩放、FPGA-aware NAS、DynPaC、HF-LDPC、AutoVCoder、Transformer FPGA推理。
3.新兴记忆神经加速器和可靠性：SOT-MRAM BNN、PIM-TGAN、RRAMedy、ATT、SME、GIM。
4. Neural/attention/LLM 执行和运行时内存：AccUDNN、NeuroFabric、DEQ、ParaCkpt、DHeLlam、Repo、Dynamic VM。
5. 存储/文件系统元数据和内核 I/O 路径：Duplex、Buffered I/O、R2Hash。
6. 工具、基准测试和设计自动化 artifact：DEQ、AutoVCoder、OpenYield。
7. 安全/可靠性/测试边界：BlinK、HElix、RRAMedy。
8. Approximate/emerging hardware tradeoffs：2025 approximate Booth multiplier 仍为 needs_review frontier。
9. Edge/autonomous embedded energy/runtime：SHEEO 是单篇 frontier hook。

趋势判断只在多篇或跨年证据支持时写成趋势。单篇 evidence 只写 frontier、method_bridge 或 needs_review。

## 5. Award Papers 分析

官方可确认的 award/candidate rows 仍为 17 条。2019 RRAMedy、2021 DynPaC、2023 HF-LDPC、2025 DHeLlam 是当前 corpus 中的 winner rows；2023-2025 还有官方 candidate rows。2024 官方 bestpaper 页面只列 candidates，本轮没有找到 winner，所以不写 2024 winner row，见 <a id="ICCD-001-C055"></a>[ICCD-001-C055](#ICCD-001-C055)。

2016、2017、2018、2020、2022 的 official program 中能看到 Best Papers Session 或相关 session，但 award-source agent 没有找到 canonical winner source。本报告不从 session membership 推断 winner。

## 6. 代表论文和影响力初审

P0 evidence matrix 包含 29 篇论文。这里列出阅读路线中的关键锚点：

- [ICCD-2016-P0004](../../10_corpus/ICCD/id_index.md#ICCD-2016-P0004) IMPICA：memory-side pointer chasing，OpenAlex cited_by_count=181（检索日期 2026-06-27），artifact/adoption 未验证。
- [ICCD-2019-P0012](../../10_corpus/ICCD/id_index.md#ICCD-2019-P0012) RRAMedy：官方 2019 Best Paper，ReRAM neural accelerator lifetime fault remedy；citation signal partial，adoption 未验证。
- [ICCD-2021-P0010](../../10_corpus/ICCD/id_index.md#ICCD-2021-P0010) DynPaC：官方 2021 Best Paper，dynamic CGRA reconfiguration；follow-on citations partial，direct artifact 未验证。
- [ICCD-2023-P0081](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0081) HF-LDPC：官方 2023 Best Paper，HLS-friendly QC-LDPC FPGA decoder；author PDF 可读，source code 未找到。
- [ICCD-2024-P0023](../../10_corpus/ICCD/id_index.md#ICCD-2024-P0023) AutoVCoder：官方 2024 candidate，LLM-assisted Verilog generation；GitHub repo 可见，runnability 和 industrial adoption 未验证。
- [ICCD-2025-P0010](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0010) DHeLlam：官方 2025 Best Paper，distributed LLM training micro-batch co-execution；有早期 follow-on citation，public code 未找到。
- [ICCD-2025-P0023](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0023) OpenYield：官方 2025 candidate，SRAM yield benchmark/tool suite；GitHub repo 可见，benchmark standardization 未验证。

影响力初审严格区分 citation、follow-on、artifact、benchmark 和 adoption。没有证据时写 `impact_unverified`。

## 7. 与我的方向的连接点

ICCD 不是 3DGS、NeRF 或 neural rendering 主会。2016-2025 title evidence 没有显示它是成熟 3DGS venue。对 3DGS/神经渲染更有用的是方法模板：把 rendering pipeline 拆成 memory traffic、sort/binning、tile scheduling、precision、FPGA/HLS mapping、runtime memory 和 reliability/security 边界。

如果继续做 FPGA 上的 3DGS，不建议只问“能否写一个专用 IP”。更可验证的问题是：Gaussian primitive 的排序和 streaming 是否能静态化；哪个阶段受显存/带宽限制；低精度会不会破坏画质；buffer/NoC/DRAM 访问是否能用论文级指标解释；系统是否能在端侧功耗和 latency 下闭环。

## 8. 缺失来源

- ICCD 2016、2017、2018、2020、2022 官方最佳论文/获奖者规范页面。
- ICCD 2026 录用论文、项目、奖项列表。
- 2016-2025 official program/session metadata 的全量稳定解析。
- P0 论文的 camera-ready PDF、artifact/code URL、artifact runnability、citation-context 和 adoption audit。
- 团队隶属关系消歧。
- 所有venue报告后与 ICCAD/DAC/FCCM/HPCA/MICRO 的cross-venue比较可用。
