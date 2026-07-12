# ICCD 小领域深读

## 1. 范围与语料

- Venue：`ICCD`
- Corpus: `papers.csv` 有 1016 条 DOI-backed proceedings rows，年份为 2016-2025；`awards.csv` 有 17 条官方 Best Paper winner/candidate rows。
- Screening: `ICCD_screening_matrix.csv` 覆盖 1033 行，其中 deep_read=46、index_only=808、needs_review=144、exclude_non_main=35。deep_read 包含 29 篇 P0 paper 和 17 条 award source row。
- Evidence: `ICCD_paper_evidence_matrix.csv` 写入 29 篇 P0 paper 的 WHY/HOW/WHAT/IMPACT/EVIDENCE。影响力初审使用 OpenAlex/Semantic Scholar/Crossref/官方页/作者页/GitHub 可见信息；citation/adoption/artifact 信号均写了检索日期。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="ICCD-SF01"></a>[ICCD-SF01](#ICCD-SF01) | 用于不规则/有状态 workload 的近内存和 PIM | 把 pointer chasing、GNN/PIM、persistent-memory index 等数据移动问题移近 memory 或存储层处理 | 链接结构、DBx1000、GNN、PM 哈希索引 | 内存延迟、随机访问、调整大小/索引元数据 | 3D 堆栈内存逻辑、地址访问解耦、数字 PIM、持久内存散列 | 2016, 2023, 2025 | partial |
| <a id="ICCD-SF02"></a>[ICCD-SF02](#ICCD-SF02) | FPGA/HLS/可重新配置加速和 RTL 生成 | 把 CNN/LDPC/Transformer/streaming/RTL generation 变成可综合、可调度、可扩展的硬件实现 | CNN、QNN、 LDPC、Transformer、Verilog 生成、流式传输 CGRA | 片外带宽、HLS QoR、重新配置开销、非线性操作 | HLS 数据流、部分重新配置、成本模型、NAS、LLM 微调/RAG | 2016-2025 | partial |
| <a id="ICCD-SF03"></a>[ICCD-SF03](#ICCD-SF03) | 新兴记忆神经加速器和可靠性 | 用 ReRAM/SOT-MRAM/CIM 降低 neural workload 数据移动，同时处理 fault、bit sparsity 和 attention/GNN irregularity | BNN、TGAN、DNN、注意力、GNN | 模拟/设备故障、稀疏利用率、外设成本 | SOT-MRAM PIM、位切片、挤出、冗余、故障检测/再训练 | 2017-2023 | partial |
| <a id="ICCD-SF04"></a>[ICCD-SF04](#ICCD-SF04) | 神经/注意力/LLM 执行和运行时内存 | 训练和推理阶段的 memory capacity、checkpoint I/O、micro-batch overlap、swapping 和 NPU allocator 问题 | ResNet、稀疏 DNN 训练、注意力、LLM 训练、Ascend/MindSpeed | GPU/NPU 内存、通信重叠、页面错误、碎片 | 交换、稀疏拓扑协同设计、按元素量化、基于路径的检查点、微批量协同执行 | 2019-2025 | partial |
| <a id="ICCD-SF05"></a>[ICCD-SF05](#ICCD-SF05) | 存储/文件系统元数据和内核 I/O 路径 | 分布式文件系统、buffered I/O 和 persistent-memory index 的 metadata/path bottleneck | DFS 元数据、Linux 缓冲 I/O、PM 哈希表 | 尾部延迟、权限检查、页面回收、调整 | 大小全路径索引、权限服务器、脏节流更改、拆分顺序调整大小 | 2023-2025 | partial |
| <a id="ICCD-SF06"></a>[ICCD-SF06](#ICCD-SF06) | 工具、基准测试和设计自动化 artifact | 给硬件生成、yield analysis 和 attention quantization 提供可复查工具或 benchmark | Verilog 生成、SRAM 产量、注意力量化 | 数据稀缺性、再现性、基准真实性 | 数据集生成、LLM 微调/RAG、SRAM 生成器、公开仓库 | 2023-2025 | partial |
| <a id="ICCD-SF07"></a>[ICCD-SF07](#ICCD-SF07) | 安全性/可靠性/测试边界 | 把 hardware implementation 的 fault、side-channel、privacy boundary 写清楚 | Kyber、 FHE 基因组匹配、ReRAM 故障 | 泄漏、故障恢复、加密域成本 | 旁路攻击、FHE 友好哈希、故障测试 | 2019-2025 | partial |
| <a id="ICCD-SF08"></a>[ICCD-SF08](#ICCD-SF08) | 近似/新兴硬件权衡 | 在 approximate arithmetic 和 emerging devices 中平衡 quality、PPA 和 application error | 近似 Booth 乘数、语料库中的量子/神经形态行 | 质量损失、设备约束 | 近似编码、OpenROAD 综合、应用程序级质量检查 | 2025加上标题级语料库 | needs_review |
| <a id="ICCD-SF09"></a>[ICCD-SF09](#ICCD-SF09) | 边缘/自主嵌入式能源/运行时 | 自动驾驶/自治嵌入式系统在运行时处理能耗和资源波动 | Jetson Orin，自主嵌入式 workload | 随机运行时方差，资源未充分利用 | 影子循环，持续优化 | 2024 | 单纸前沿 |

## 3. 小领域深读

### [ICCD-SF01](#ICCD-SF01)：用于不规则/有状态 workload 的近内存和 PIM

ICCD 的 memory/PIM 线不是一个单一问题。P0 证据把它拆成三类：2016 IMPICA 解决 pointer chasing 的 memory-side execution 和地址转换，2023 GIM 把 GNN 的 operand/bit sparsity 放进 compact digital PIM，2025 R2Hash 处理 persistent-memory hash index 的 read/resize tradeoff。共同瓶颈是数据搬运和随机访问，而不是“memory”这个大标签。

代表工作：[ICCD-2016-P0004](../../10_corpus/ICCD/id_index.md#ICCD-2016-P0004)、[ICCD-2023-P0073](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0073)、[ICCD-2025-P0026](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0026)。IMPICA 有较强 citation signal（OpenAlex cited_by_count=181，检索日期 2026-06-27），但 artifact/code 和产业采用没有验证。GIM 与 R2Hash 都太新，影响力写 `impact_unverified` 或 `partial`。

团队线索只作为活动信号：IMPICA 的 PDF 显示 CMU/UVA/ETH Zurich 与 SAFARI/Mutlu group；R2Hash 是 HUST/WNLO storage systems 信号；GIM 与 Zhezhi He/SJTU-Qi Zhi 活动线索有关，但需要 affiliation disambiguation。

跨会议 hook：这条线应和 MICRO/HPCA/ISCA 的 near-data/PIM、FAST/OSDI/SOSP 的 storage metadata、DATE/DAC 的 emerging-memory implementation 交叉看。

### [ICCD-SF02](#ICCD-SF02)：FPGA/HLS/可重构加速和 RTL 生成

这条线从 CNN accelerator 的手工 dataflow，走到 QNN/FINN 式成本模型、FPGA-aware NAS、dynamic CGRA、HLS-friendly LDPC，再到 Transformer FPGA 和 LLM-assisted Verilog generation。它的核心不是“FPGA”，而是如何在资源、时序、吞吐和可维护性之间找到可综合实现。

代表工作：[ICCD-2016-P0043](../../10_corpus/ICCD/id_index.md#ICCD-2016-P0043)、[ICCD-2017-P0086](../../10_corpus/ICCD/id_index.md#ICCD-2017-P0086)、[ICCD-2020-P0076](../../10_corpus/ICCD/id_index.md#ICCD-2020-P0076)、[ICCD-2021-P0010](../../10_corpus/ICCD/id_index.md#ICCD-2021-P0010)、[ICCD-2023-P0081](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0081)、[ICCD-2024-P0023](../../10_corpus/ICCD/id_index.md#ICCD-2024-P0023)、[ICCD-2025-P0013](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0013)。DynPaC 和 HF-LDPC 是官方 Best Paper；AutoVCoder 是官方 2024 candidate，且有公开 GitHub repo。AutoVCoder 的 early citation signal 强，但只能写成 `partial`，因为工业 toolchain adoption 没有验证。

技术路线：manual/reconfigurable CNN processor -> FINN/QNN scaling model -> DNAS/DSE -> dynamic CGRA reconfiguration -> HLS-friendly domain decoder -> LLM-assisted RTL generation -> FPGA Transformer fusion/integer-only quantization。

团队线索：Xilinx Research Labs/FINN、PNNL ACMD/DMC、HUST/WNLO + UT Arlington、SJTU/SYSU/Fudan 等。这里只写 activity signal，不做排名。

跨会议 hook：FCCM/FPL/FPGA 对 HLS/FPGA dataflow 更深；DAC/ICCAD/DATE 对 LLM-for-RTL、HLS、verification 和 physical closure 更强；MLSys/SC 适合追 Transformer/LLM execution。

### [ICCD-SF03](#ICCD-SF03)：新兴内存神经加速器和可靠性

这条线把 neural accelerator 的数据移动问题和 emerging-memory 的 device fault 绑在一起。2017 SOT-MRAM BNN、2018 PIM-TGAN、2019 RRAMedy、2020 ATT、2021 SME、2023 GIM 组成跨年证据。趋势可以说成立：CIM/PIM 从 binary/CNN/GAN 扩展到 attention/GNN，同时 fault tolerance 和 bit sparsity 成为核心机制。

代表工作：[ICCD-2017-P0009](../../10_corpus/ICCD/id_index.md#ICCD-2017-P0009)、[ICCD-2018-P0040](../../10_corpus/ICCD/id_index.md#ICCD-2018-P0040)、[ICCD-2019-P0012](../../10_corpus/ICCD/id_index.md#ICCD-2019-P0012)、[ICCD-2020-P0038](../../10_corpus/ICCD/id_index.md#ICCD-2020-P0038)、[ICCD-2021-P0064](../../10_corpus/ICCD/id_index.md#ICCD-2021-P0064)、[ICCD-2023-P0073](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0073)。RRAMedy 是官方 2019 Best Paper，适合作为 reliability subline 的 anchor；SME 有 author PDF/arXiv 证据；ATT 和 PIM-TGAN 仍主要是 abstract/citation-level。

影响力：多篇有 citation signal，但 artifact/code reuse 和 benchmark standardization 都未验证。报告中只能写 partial 或 impact_unverified。

跨会议 hook：与 DAC/ICCAD/DATE 的 CIM/EDA、ISCA/HPCA/MICRO 的 architecture、ISSCC/VLSI 的 device/circuit 实现需要并读。

### [ICCD-SF04](#ICCD-SF04)：神经/注意力/LLM 执行和运行时内存

这条线在 2019 AccUDNN 还只是 GPU training memory；2023 DEQ 转向 attention quantization；2024 ParaCkpt 处理 training checkpoint I/O；2025 DHeLlam、Repo 和 Dynamic VM 把问题扩展到 distributed LLM training、proactive swapping 和 Ascend/NPU allocator。趋势由多篇跨年论文支撑，但后两年太新，不能写成稳定影响。

代表工作：[ICCD-2019-P0009](../../10_corpus/ICCD/id_index.md#ICCD-2019-P0009)、[ICCD-2022-P0079](../../10_corpus/ICCD/id_index.md#ICCD-2022-P0079)、[ICCD-2023-P0088](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0088)、[ICCD-2024-P0026](../../10_corpus/ICCD/id_index.md#ICCD-2024-P0026)、[ICCD-2025-P0010](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0010)、[ICCD-2025-P0018](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0018)、[ICCD-2025-P0055](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0055)。DHeLlam 是官方 2025 Best Paper；DEQ 有公开 repo；其余多为 abstract/PDF-level evidence。

研究问题：如何在 memory capacity、communication overlap、checkpoint I/O、page faults 和 allocator fragmentation 之间做系统级优化。对用户的 3DGS/神经渲染方向，直接启发是把显存、tile/binning/sort、streaming 和 fallback storage 问题拆成可测系统瓶颈，而不是泛泛说“加速渲染”。

跨会议 hook：MLSys、OSDI/SOSP、SC、PPoPP 更适合追 LLM training runtime；FPGA/FCCM/FPL 适合追 Transformer inference on FPGA；MICRO/HPCA/ISCA 适合追 memory hierarchy 和 accelerator system。

### [ICCD-SF05](#ICCD-SF05)：存储/文件系统元数据和内核 I/O 路径

ICCD 中 storage 不只是外围主题。2023 Duplex 和 Buffered I/O 候选、2025 R2Hash 都围绕 metadata、kernel path 和 persistent memory 的 tail latency/resize 问题。它和 accelerator 的关系在于数据供给、metadata indexing 和 memory system，而不是计算核本身。

代表工作：[ICCD-2023-P0042](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0042)、[ICCD-2023-P0068](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0068)、[ICCD-2025-P0026](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0026)。Duplex 和 Buffered I/O 是 2023 official candidates；R2Hash 是 2025 official candidate。三者影响力都不能写实锤 adoption：Duplex/R2Hash 没有 code，Buffered I/O 没有 kernel upstream 证据。

跨会议 hook：FAST、USENIX ATC、OSDI/SOSP 和 PPoPP/SC 的 memory/runtime 会提供更强系统证据。

### [ICCD-SF06](#ICCD-SF06)：工具、基准测试和设计自动化 artifact

这里不能把“tool”当作成功事实，只能写 artifact visibility。DEQ、AutoVCoder、OpenYield 都有公开 GitHub 链接，分别对应 attention quantization software、LLM-assisted Verilog generation、SRAM yield benchmark suite。OpenYield 的 artifact signal 最清楚，但 runnability 没有检查；AutoVCoder 的 early citation signal 强，但 adoption 不等于 citation。

代表工作：[ICCD-2023-P0088](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0088)、[ICCD-2024-P0023](../../10_corpus/ICCD/id_index.md#ICCD-2024-P0023)、[ICCD-2025-P0023](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0023)。可见 repo：DEQ、AutoVCoder、OpenYield。benchmark standardization 仍是 needs_review。

跨会议 hook：DATE/DAC/ICCAD 对 EDA tool/benchmark adoption 更关键；MLSys/NeurIPS datasets/tools 经验也可借鉴 LLM-for-RTL 的评测设计。

### [ICCD-SF07](#ICCD-SF07)：安全性/可靠性/测试边界

Blink 和 HElix 是边界类证据。Blink 说明并行 Kyber 硬件实现仍可能被 side-channel 攻击；HElix 把 encrypted-domain genome similarity 放在 FHE-friendly hashing 上。这些不是 accelerator 性能里程碑，但能提醒 hardware/software co-design 必须把安全边界纳入系统设计。

代表工作：[ICCD-2024-P0016](../../10_corpus/ICCD/id_index.md#ICCD-2024-P0016)、[ICCD-2025-P0001](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0001)，再加上 [ICCD-2019-P0012](../../10_corpus/ICCD/id_index.md#ICCD-2019-P0012) 的 ReRAM fault reliability。HElix 的 IACR preprint 和 ICCD abstract 范围不完全一致，细节必须保留 needs_review。

跨会议 hook：CHES、HOST、USENIX Security、DATE/DAC/ICCAD 的 security/test track。

### [ICCD-SF08](#ICCD-SF08)：近似/新兴硬件权衡

P0 里只有 2025 approximate Booth multiplier，因此不能把它单独写成成熟 ICCD subfield。它更适合作为 existing approximate/quantum/neuromorphic corpus 的入口：问题是 application quality、PPA 和 design automation 的 tradeoff。直接 artifact URL 未找到，保持 needs_review。

### [ICCD-SF09](#ICCD-SF09)：边缘/自主嵌入式能源/运行时

SHEEO 是 2024 official candidate，作者 PDF 可读，问题是 autonomous embedded system 在 runtime variance 下的 continuous energy optimization。单篇不足以形成稳定子领域，但能作为 edge runtime hook，连接 EMSOFT/RTSS、DATE、embedded ML systems。

## 4. 发展趋势

1. Memory-centric design 从 2016 IMPICA 的 pointer chasing，延伸到 2023 GIM 的 GNN PIM 和 2025 R2Hash 的 persistent-memory index。证据来自 [ICCD-2016-P0004](../../10_corpus/ICCD/id_index.md#ICCD-2016-P0004)、[ICCD-2023-P0073](../../10_corpus/ICCD/id_index.md#ICCD-2023-P0073)、[ICCD-2025-P0026](../../10_corpus/ICCD/id_index.md#ICCD-2025-P0026)。
2. FPGA/HLS/reconfigurable line 从 CNN-MERP、QNN scaling 和 FPGA-aware NAS，走到 DynPaC、HF-LDPC、AutoVCoder 和 Transformer FPGA inference。证据跨 2016-2025，多篇支撑。
3. Emerging-memory neural acceleration 从 SOT-MRAM BNN 和 PIM-TGAN，进入 ReRAM fault reliability、attention accelerator、bit-sparsity 和 GNN PIM。证据来自 2017-2023 六篇 P0。
4. LLM/attention/runtime memory 是近年 frontier：DEQ、ParaCkpt、DHeLlam、Repo、Dynamic VM 共同说明 ICCD 开始收录训练/runtime/memory 管理问题。由于 2024-2025 太新，影响力不能写成 verified。
5. Tool/benchmark artifact 有明确可见 repo 的是 DEQ、AutoVCoder、OpenYield。OpenYield 和 AutoVCoder 有较强后续引用线索，但 runnable/adoption 未验证。

## 5. 方法变化

- 从 title-level clustering 进入 paper-level evidence 后，topic 应写成具体瓶颈：pointer chasing translation、HLS-friendly LDPC dataflow、LLM micro-batch co-execution、Linux buffered-I/O page reclaim、LLM-for-RTL generation，而不是 FPGA、EDA、ML systems 这类大词。
- 评价维度也更具体：memory latency、tail latency、PPA、throughput、MFU、fragmentation、fault recovery、side-channel trace count、benchmark reproducibility。
- 影响力初审要分开写：citation signal、follow-on citation、artifact visibility、benchmark standardization、toolchain/industry adoption。没有证据的字段写 impact_unverified。

## 6. 缺失来源

- ICCD 2016、2017、2018、2020、2022 canonical Best Paper winner sources。已有 Best Papers Session/official program 不能自动写成 winner。
- ICCD 2026 accepted papers、program、award list。按 CFP 时间线，2026-06-27 尚未到 acceptance notification。
- 2016-2025 official program/session 的全量结构化解析。
- 多数 P0 paper 的 camera-ready PDF、artifact/code URL 和 runnable 状态。
- 团队 affiliation disambiguation 和跨 venue 影响力审计。
