# ASPLOS 论文图谱分析

第二轮写入日期：`2026-06-27`

## 1. 会议定位

本报告中的 `ASPLOS` 指 ACM International Conference on Architectural Support for Programming Languages and Operating Systems。本项目把它作为 architecture、OS、compiler 和 systems 交叉 venue 处理，而不是把 `architecture`、`OS`、`compiler` 或 `ML systems` 当成主 topic。第二轮重点改为小领域证据：具体 workload、瓶颈、技术路线、代表论文、artifact/code 和影响力线索。

## 2. 数据来源与覆盖范围

覆盖年份仍为 2016-2026。`papers.csv` 有 1161 行，`awards.csv` 有 40 行；2026 保持 `partial`，因为官方 program/awards 可验证，但长期影响无法在 2026-06-27 判断。第二轮新增输出：

- `ASPLOS_screening_matrix.csv`：1201 行，覆盖 papers 和 awards 全量筛选。
- `ASPLOS_paper_evidence_matrix.csv`：103 行 deep_read evidence，包含 WHY/HOW/WHAT/IMPACT/EVIDENCE。
- `subfields.md`：按小领域写研究问题、背景、路线、代表工作、团队线索、趋势和跨会议 hook。

| 年份 | papers.csv 记录数 | 状态 |
|---|---:|---|
| 2016 | 56 | 完全的 |
| 2017 | 57 | 完全的 |
| 2018 | 57 | 完全的 |
| 2019 | 71 | 完全的 |
| 2020 | 88 | 完全的 |
| 2021 | 73 | 完全的 |
| 2022 | 79 | 完全的 |
| 2023 | 140 | 完全的 |
| 2024 | 172 | 完全的 |
| 2025 | 190 | 完全的 |
| 2026 | 178 | partial |

## 3. 第二轮 Issue 处理

| 发出 | 地位 | 当前处理 |
|---|---|---|
| <a id="ASPLOS-SW-I001"></a>[ASPLOS-SW-I001](#ASPLOS-SW-I001) | partially_resolved | 第二波回填目标行的可靠 DOI/URL/code/artifact 元数据； paper.csv 缺少摘要/关键字列，因此缺少摘要/关键字覆盖范围仍然没有架构更改。 |
| <a id="ASPLOS-SW-I002"></a>[ASPLOS-SW-I002](#ASPLOS-SW-I002) | partially_resolved | 官方 2024 年计划/摘要/奖项页面经过检查并用作证据； 2024 年Distinguished Artifact Award页面是规范的，但其行尚未标准化为 Awards.csv。 |
| <a id="ASPLOS-SW-I003"></a>[ASPLOS-SW-I003](#ASPLOS-SW-I003) | partially_resolved | 已知程序/会议记录标题变体已注释并验证 DOI 候选者回填可靠的地方；完整的重复合并仍然被推迟。 |
| <a id="ASPLOS-SW-I004"></a>[ASPLOS-SW-I004](#ASPLOS-SW-I004) | normal_2026_partial | 2026年计划/奖项可以验证，但长期影响通常在2026-06-27无法获得；evidence rows使用 impact_unverified/partial。 |
| <a id="ASPLOS-SW-I005"></a>[ASPLOS-SW-I005](#ASPLOS-SW-I005) | partially_resolved | 编写了完整的筛选矩阵和 103 篇论文的证据矩阵；完整的摘要嵌入和引用图仍然是未来的工作。 |
| <a id="ASPLOS-SW-I006"></a>[ASPLOS-SW-I006](#ASPLOS-SW-I006) | still_open | 团队线索仅是作者/隶属关系字符串；没有进行entity disambiguation或排名。 |
| <a id="ASPLOS-SW-I007"></a>[ASPLOS-SW-I007](#ASPLOS-SW-I007) | partially_resolved | DBLP 仅通过源提示有选择地使用；没有进行稳定的散装 DBLP 回填。 |
| <a id="ASPLOS-SW-I008"></a>[ASPLOS-SW-I008](#ASPLOS-SW-I008) | partially_resolved | 2024-2026 award rows已更正，规范页面已验证； 2016-2023 年历史奖励扩展和 2024 年artifact award rows仍然开放。 |
| <a id="ASPLOS-SW-I009"></a>[ASPLOS-SW-I009](#ASPLOS-SW-I009) | partially_resolved | DOI/proceedings/PDF/arXiv/代码源已在可靠的地方添加； ACM DL 主体解析仍然被阻止/不可用。 |
| <a id="ASPLOS-SW-I010"></a>[ASPLOS-SW-I010](#ASPLOS-SW-I010) | still_open | cross-venue ISCA/MICRO/HPCA/ASPLOS 矩阵位于 ASPLOS 仅限写入范围之外；仅深潜记录挂钩。 |
| <a id="ASPLOS-SW-I011"></a>[ASPLOS-SW-I011](#ASPLOS-SW-I011) | partially_resolved | 证据矩阵记录 deep_read 论文的引用/采用/artifact/基准信号以及检索日期；全面的引用/采用审计仍然是未来的综合工作。 |

## 4. Screening 结果

筛选决定只使用 `deep_read`、`index_only`、`exclude_non_main`、`needs_review`。本轮没有把非 main track 行强行排除；historical award 缺少 local paper_id 的行保留 `needs_review`。

| 决策 | rows |
|---|---:|
| deep_read | 135 |
| index_only | 685 |
| exclude_non_main | 0 |
| needs_review | 381 |

## 5. 小领域图谱

| 子领域 | deep_read rows | 研究问题 |
|---|---:|---|
| [ASPLOS-SF01](subfields.md#ASPLOS-SF01)：3DGS 和神经渲染加速 | 7 | 3DGS/neural rendering 的渲染核心、训练内存和 VR/on-device 管线加速。 |
| [ASPLOS-SF02](subfields.md#ASPLOS-SF02)：SLAM、机器人与具身 AI 极端边缘 | 7 | SLAM、机器人优化、embodied AI、item-level intelligence 的低时延、可靠性和生命周期约束。 |
| [ASPLOS-SF03](subfields.md#ASPLOS-SF03)：LLM 服务、注意力和以记忆为中心的推理 | 25 | LLM/Transformer attention、PIM/NPU/CXL、speculative decoding、KV/cache 和 serving runtime。 |
| [ASPLOS-SF04](subfields.md#ASPLOS-SF04)：分布式 LLM 训练和 GPU 通信 | 8 | 大模型训练并行、通信重叠、MoE、heterogeneous GPU/network 和 collective abstraction。 |
| [ASPLOS-SF05](subfields.md#ASPLOS-SF05)：持久、分层、远端和 CXL 内存系统 | 11 | 持久内存安全、tiered/far/disaggregated memory、CXL fabric 与 bridge synthesis。 |
| [ASPLOS-SF06](subfields.md#ASPLOS-SF06)：编译器 IR、HLS/dataflow 和张量代码生成 | 14 | accelerator generator IR、HLS/dataflow、MLIR/tensor compiler、e-graph 和 operator fusion。 |
| [ASPLOS-SF07](subfields.md#ASPLOS-SF07)：FPGA/云虚拟化和可重构平台 | 6 | cloud FPGA virtualization、CPU/FPGA research platforms、CGRA realization 和 FPGA compile/runtime。 |
| [ASPLOS-SF08](subfields.md#ASPLOS-SF08)：稀疏且不规则的加速器数据流 | 7 | SpGEMM/sparse attention/automata/dynamic orchestration 等不规则数据流。 |
| [ASPLOS-SF09](subfields.md#ASPLOS-SF09)：硬件正确性、安全性和验证 | 11 | MCM/接口验证、侧通道/消毒器、正式 HLS/系统软件、DRAM/CXL 安全。 |
| [ASPLOS-SF10](subfields.md#ASPLOS-SF10)：内存分析、预取和基准基础架构 | 4 | PM/cache/prefetch/profiling 的 workload、benchmark、measurement artifact。 |
| [ASPLOS-SF11](subfields.md#ASPLOS-SF11)：FHE 和新兴安全/模拟 workload | 2 | FHE deep learning、tensor-algebra RTL simulation 等新 workload 的 compiler/runtime 加速。 |
| [ASPLOS-SF12](subfields.md#ASPLOS-SF12)：用户级异步通知和内核绕过运行时 | 1 | 用户级中断、内核绕过 I/O/存储/加速器通知。 |

## 6. Award Source 复核

2024-2026 best paper / honorable mention / artifact / influential award 的 canonical source 优先使用官方会议 award 页。第二轮完成的修正：

- [ASPLOS-2025-A11](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-A11) xUI 对齐到 [ASPLOS-2025-P0058](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0058)，补 DOI `10.1145/3676641.3716028`。
- [ASPLOS-2025-A13](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-A13) MetaSapiens 标题按 DOI/papers.csv 全称规范化。
- [ASPLOS-2025-A21](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-A21) 奖项名改为官方页口径 `Artifact Evaluation Award`，不再写未找到 canonical source 的 `Distinguished Artifact Award`。
- [ASPLOS-2026-A27](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-A27) 到 [ASPLOS-2026-A37](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2026-A37) 的 authors 从匹配 paper row 回填；官方 awards 页本身仍是 title-only source。
- historical influential award 行补 DOI，但不新增本地 paper_id。

仍保留的缺口：ASPLOS 2024 官方 Distinguished Artifact Evaluation Awards 页面列出 10 个 artifact award 条目，但当前 `awards.csv` 未把这些 row 正规化；2016-2023 历史 award 扩表也未完成。

## 7. 影响力初审

影响力状态来自 evidence matrix，不把 citation count 直接当强弱判断依据。citation/adoption/artifact/benchmark 信号均写检索日期。代表性结论如下：

- `MSCCL++` 有 Microsoft Research 页面支撑的 Azure/AMD RCCL 采纳线索，标为 `verified` adoption signal。
- `Relax` 有 Apache TVM 文档支撑的 toolchain signal，标为 `verified`。
- `GSCore` 有 AGS/Nebula follow-on 信号，标为 `partial`，不是长期产业采纳证明。
- `POD-Attention` 有 ASPLOS artifact award 和 FlashInfer/POD-Attention 线索，标为 `partial`。
- `WHISPER` 和 CTVS 是 benchmark/workload 信号；artifact/code 均未运行。
- 2026 论文即便获奖，也统一保守处理长期影响：多数为 `impact_unverified` 或 `partial`。

## 8. 团队线索

本轮只写 team_signal，不做强弱排序。这些都是论文集合中的作者/机构字符串线索，仍需 entity audit。

| 团队/机构线索 | 关联方向 | 证据状态 | 使用限制 |
|---|---|---|---|
| SNU / SJTU / NYU / SNU ARC | 3DGS、neural rendering | 作者/机构字符串线索 | 仍需 entity audit；不做强弱排序 |
| PKU / CMU / Microsoft / SJTU / Tsinghua / UIUC | LLM systems | 作者/机构字符串线索 | 仍需 entity audit；只作为论文集合入口 |
| UCSD / Wisconsin / Yale / Google / UIUC / TUM | memory、CXL | 作者/机构字符串线索 | 仍需 entity audit；不写成团队排名 |
| Cornell / UIUC / UT Austin / Stanford / Alibaba / Peking | compiler、HLS、dataflow | 作者/机构字符串线索 | 仍需 entity audit；只作为阅读入口 |
| Princeton / Yale / EPFL / Columbia / TUM | correctness、security、verification | 作者/机构字符串线索 | 仍需 entity audit；不做强弱排序 |

## 9. 与个人方向的连接点

对 3DGS/神经渲染，ASPLOS 内已有清晰证据：`GSCore`、`MetaSapiens`、`AGS`、`CLM`、`GS-Scale`、`Nebula`、`Neo` 覆盖 rendering core、mobile/foveated rendering、SLAM、large-scene training、VR collaboration 和 on-device sorting。对 FPGA/加速器，`Enzian`、`ViTAL`、`SYNERGY`、`HIDA`、`Calyx`、`RedFuser`、`vCXLGen` 等给出 platform、compiler、verification 和 bridge synthesis 的软硬协同路线。对 LLM systems，ASPLOS 的切口集中在 serving/runtime、PIM/NPU/GPU、communication、KV/cache、thermal/power、low-bit/edge 和 accelerator interface。

## 10. 阅读路线

- 3DGS/神经渲染：GSCore -> MetaSapiens -> AGS -> CLM/GS-Scale -> Nebula/Neo。
- LLM服务/推理：DOTA -> AttAcc/NeuPIMs -> SpecInfer/SpotServe -> POD-Attention/CENT -> DFVG/MSCCL++。
- Memory/CXL：JUSTDO/HPTPM/WHISPER -> Nimble/SDFM/Mitosis -> Clio -> CXLfork/PACT/vCXLGen。
- 编译器/HLS/dataflow：Calyx -> HeteroGen/HIR/Sigma -> HIDA/Isaria -> Relax/SmoothE/ISAMORE/RedFuser/STeP。
- 正确性/安全性：COATCheck/TriCheck -> CTVS -> GIANTSAN/H-Houdini -> Graphiti/Spoq2/vCXLGen。

## 11. 缺失来源

- 缺少 2024 Distinguished Artifact Evaluation Awards 的结构化 row 正规化，以及 2016-2023 历史 award 全量扩表。
- 缺少稳定 DBLP bulk key/URL 回填；ACM DL body 页面仍不作为正文抽取来源。
- 缺少完整 citation graph、adoption graph 和 artifact runnable audit。
- 缺少跨 ISCA/MICRO/HPCA/ASPLOS 的同主题矩阵；本报告只写 ASPLOS 内部 hook。
