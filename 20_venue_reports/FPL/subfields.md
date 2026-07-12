# FPL 小领域深读

## 1. 范围与语料

- Venue：`FPL`
- 语料库：`papers.csv` 754 行，`awards.csv` 26 行。
- 筛选矩阵：780 行（`deep_read` 86、`index_only` 460、`needs_review` 199、`exclude_non_main` 35）。
- 证据矩阵：62 行。没有引用/采用/人工证据的行保留 `impact_unverified` 或 `needs_review`。
- 2026 处理：截至 2026 年 6 月 27 日，尚无接受/proceedings/获奖名单；这是`normal_2026_partial`，不是venue issue。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="FPL-SF01"></a>[FPL-SF01](#FPL-SF01) | FPGA CAD、架构和物理 QoR 建模 | FPGA 架构/CAD 选择必须转化为可路由、定时、区域高效的实现 | CAD 基准、架构模型、路由/布局 workload | 可路由性、定时、区域模型错误，CAD 运行时/内存 | 区域模型验证； ML 拥塞/可路由性预测；布局/布线算法； LLM 脚本 | 2016-2025 | partial |
| <a id="FPL-SF02"></a>[FPL-SF02](#FPL-SF02) | HLS 至路由电路自动化 | 高级程序需要 FPGA 上可预测的内存、调度和后端关闭 | HLS 内核、不规则循环、C 到电路流程 | 内存银行、不规则控制、编译/后端延迟 | 跟踪引导银行；选择性动态调度；动态/RapidWright 路由重用 | 2017-2024 | partial |
| <a id="FPL-SF03"></a>[FPL-SF03](#FPL-SF03) | 低精度神经和 Transformer FPGA 映射 | 神经 workload 必须符合 FPGA 精度、内存和管道约束 | BNN/CNN/GNN/Transformer/ViT/GPT/Diffusion | 注意力成本、低精度、稀疏性、缓冲、通信 | 覆盖；量化；运行时重新配置；生成加速器；分析缓冲 | 2018-2025 | partial |
| <a id="FPL-SF04"></a>[FPL-SF04](#FPL-SF04) | 主机-FPGA、网络、存储和 HBM 流系统 | 如果主机/网络/存储/HBM 路径成为主导瓶颈，应用加速收益会失效 | PCIe、Arrow、100GbE、block I/O、SVM、DMA、scientific HBM kernels | 数据移动、接口延迟、网络协议栈、内存带宽 | streaming libraries；TCP/IP stack；block-I/O framework；SVM；低延迟 DMA；HBM pipelines | 2016-2025 | partial |
| <a id="FPL-SF05"></a>[FPL-SF05](#FPL-SF05) | 云 FPGA 虚拟化、覆盖和运行时共享 | FPGA 资源需要抽象、共享、隔离和可编程覆盖 | 云 FPGA、软 SIMT、覆盖加速器、运行时可重新配置 SoC | 利用率、隔离、DSE 成本、重新配置开销 | 运行时 API；内存虚拟化；调查分类；软SIMT；贝叶斯叠加 DSE | 2016-2025 | partial |
| <a id="FPL-SF06"></a>[FPL-SF06](#FPL-SF06) | 开放工具、基准测试和 artifact 基础设施 | FPL 结果需要可重用工具、基准测试和 artifact 流程 | FloPoCo、Koios、GNNBuilder、LogicNets、artifact 评估 | 再现性、基准测试覆盖率、代码可用性、重用证明 | 生成器；基准套件；开放框架；官方 artifact 评估计划 | 2017-2025 | partial |
| <a id="FPL-SF07"></a>[FPL-SF07](#FPL-SF07) | FPGA 安全性、可靠性和比特流信任 | 共享和不透明 FPGA 结构会产生信任、攻击和逆向工程风险 | 故障攻击、比特流、侧通道、供应链诊断 | 有效比特流攻击、电压行为、不透明比特流格式 | 环形振荡器；电压故障实验；比特流逆向工程 | 2016-2022 | partial |
| <a id="FPL-SF08"></a>[FPL-SF08](#FPL-SF08) | 不规则图、稀疏和科学流内核 | 数据相关和域内核需要内存感知 FPGA 映射 | 图分析、ERI 量子化学、稀疏/科学内核 | HBM 压力、不规则访问、内存不足处理 | HBM 流；活动子图调度；特定领域的数据流 | 2024 | partial |
| <a id="FPL-SF09"></a>[FPL-SF09](#FPL-SF09) | 视觉、视频、SLAM、3D 和神经渲染管道 | 实时视觉/3D workload 需要低延迟、资源感知的 FPGA 管道 | SLAM、立体视觉、视频 SR、事件摄像机、NeRF/神经渲染 | 特征匹配、渲染吞吐量、编解码器重用、边缘功率 | 立体匹配；屋顶线建模；编解码器重用； NeRF 数据路径； CPU-FPGA 调度 | 2016-2025 | partial/needs_review |

## 3. 小领域深读

### [FPL-SF01](#FPL-SF01)：FPGA CAD、架构和物理 QoR 建模

研究问题是架构和 CAD 判断怎样落到可布线、可计时、可解释的 FPGA 实现。证据从 [FPL-2016-P0028](../../10_corpus/FPL/id_index.md#FPL-2016-P0028) 的面积模型校验，到 [FPL-2018-P0072](../../10_corpus/FPL/id_index.md#FPL-2018-P0072)、[FPL-2019-P0050](../../10_corpus/FPL/id_index.md#FPL-2019-P0050) 的 ML congestion/routability 预测，再到 [FPL-2020-P0023](../../10_corpus/FPL/id_index.md#FPL-2020-P0023)、[FPL-2021-P0036](../../10_corpus/FPL/id_index.md#FPL-2021-P0036) 的 placement/switch-block 路线，最后延伸到 2025 的 routing runtime/memory、[FPL-2025-P0021](../../10_corpus/FPL/id_index.md#FPL-2025-P0021) Double Duty 和 [FPL-2025-P0027](../../10_corpus/FPL/id_index.md#FPL-2025-P0027) VPR-LLM。这个趋势有跨年份证据，但 2025 论文影响力仍是早期信号。团队线索只记录 author-string 层面的 Toronto/Betz-Boutros-Abdelfattah、EPFL/Ienne-Nikolic、Areibi/Grewal/Vannelli、Wilton/Gunter 等，不做排名。

### [FPL-SF02](#FPL-SF02)：HLS 到路由电路自动化

这条线关注 HLS 从“能综合”到“能按预期布线和运行”。[FPL-2017-P0087](../../10_corpus/FPL/id_index.md#FPL-2017-P0087) 处理 multi-threaded HLS 的 banked memory，[FPL-2023-P0002](../../10_corpus/FPL/id_index.md#FPL-2023-P0002) 处理 irregular code 的 selective dynamic scheduling，[FPL-2024-P0004](../../10_corpus/FPL/id_index.md#FPL-2024-P0004) DynaRapid 把 C-to-routed-circuit 的后端延迟作为核心问题。趋势判断来自 2017、2023、2024 三个节点；代码和 follow-on adoption 仍需后续核查。

### [FPL-SF03](#FPL-SF03)：低精度神经和 Transformer FPGA 映射

FPL 的 ML 线不是单纯“AI 加速”，而是低精度、overlay/compiler、Transformer/ViT/GPT/Diffusion、buffer sizing 与资源约束之间的映射问题。代表节点包括 [FPL-2018-P0052](../../10_corpus/FPL/id_index.md#FPL-2018-P0052) BISMO、[FPL-2018-P0070](../../10_corpus/FPL/id_index.md#FPL-2018-P0070) DLA、[FPL-2020-P0043](../../10_corpus/FPL/id_index.md#FPL-2020-P0043) LogicNets、[FPL-2022-P0007](../../10_corpus/FPL/id_index.md#FPL-2022-P0007) TRAC、[FPL-2023-P0030](../../10_corpus/FPL/id_index.md#FPL-2023-P0030) GNNBuilder、[FPL-2024-P0020](../../10_corpus/FPL/id_index.md#FPL-2024-P0020) Kratos、[FPL-2025-P0019](../../10_corpus/FPL/id_index.md#FPL-2025-P0019) ReconFormer、[FPL-2025-P0039](../../10_corpus/FPL/id_index.md#FPL-2025-P0039) EQViTA 和 [FPL-2025-P0055](../../10_corpus/FPL/id_index.md#FPL-2025-P0055) buffer sizing。B 组 deep-read 失败，因此这部分多数是 metadata/index-level；不能写成已完成影响力审计。

### [FPL-SF04](#FPL-SF04)：主机 FPGA、网络、存储和 HBM 流系统

这条线把 bottleneck 从 kernel datapath 推到系统接口。[FPL-2016-P0037](../../10_corpus/FPL/id_index.md#FPL-2016-P0037) JetStream 处理 PCIe/multi-FPGA streaming，[FPL-2019-P0041](../../10_corpus/FPL/id_index.md#FPL-2019-P0041) Fletcher 处理 Apache Arrow 到 FPGA 的数据接口，[FPL-2019-P0043](../../10_corpus/FPL/id_index.md#FPL-2019-P0043) Limago 处理 100GbE TCP/IP，[FPL-2022-P0030](../../10_corpus/FPL/id_index.md#FPL-2022-P0030) DeLiBA 处理 Linux block I/O，[FPL-2024-P0010](../../10_corpus/FPL/id_index.md#FPL-2024-P0010) FlexiMem 处理 PCIe-attached FPGA 的 shared virtual memory，[FPL-2025-P0046](../../10_corpus/FPL/id_index.md#FPL-2025-P0046) DMA Calypte 处理低延迟 DMA。C 组给 Fletcher、Limago 等记录了 citation 和 repository 信号，但 adoption/reuse 没有完成结构化审计。

### [FPL-SF05](#FPL-SF05)：云 FPGA 虚拟化、覆盖和运行时共享

FPL 在 cloud/runtime 上的证据包括 [FPL-2016-P0092](../../10_corpus/FPL/id_index.md#FPL-2016-P0092) virtual runtime 和 [FPL-2018-P0024](../../10_corpus/FPL/id_index.md#FPL-2018-P0024) FPGA virtualization survey。overlay/soft architecture 则有 [FPL-2021-A13](../../10_corpus/FPL/id_index.md#FPL-2021-A13) FGPU community award 和 [FPL-2025-P0022](../../10_corpus/FPL/id_index.md#FPL-2025-P0022) DEFA。这里可以写 formation line，但不能把它扩展成跨会议强弱结论；industry/cloud adoption source 仍缺。

### [FPL-SF06](#FPL-SF06)：开放工具、基准测试和 artifact 基础设施

FPL 的工具/benchmark 证据包括 [FPL-2017-A04](../../10_corpus/FPL/id_index.md#FPL-2017-A04) FloPoCo、[FPL-2021-P0060](../../10_corpus/FPL/id_index.md#FPL-2021-P0060) Koios、[FPL-2023-P0030](../../10_corpus/FPL/id_index.md#FPL-2023-P0030) GNNBuilder、[FPL-2024-A21](../../10_corpus/FPL/id_index.md#FPL-2024-A21) Artifact Evaluation Initiative 和多个 repository-backed rows。这里的核心问题是可复现、可复用和可比较，而不是把“有 GitHub”当作影响力。Koios、LogicNets、GNNBuilder、Fletcher、Limago 等只记录 repository signal；是否被后续论文或工具链复用仍需单独审计。

### [FPL-SF07](#FPL-SF07)：FPGA 安全性、可靠性和比特流信任

这条线从 [FPL-2016-P0038](../../10_corpus/FPL/id_index.md#FPL-2016-P0038) supply-chain analyzer，到 [FPL-2017-P0086](../../10_corpus/FPL/id_index.md#FPL-2017-P0086) valid-bitstream voltage-drop attacks，再到 [FPL-2022-P0001](../../10_corpus/FPL/id_index.md#FPL-2022-P0001) Bitfiltrator。A 组记录了 [FPL-2017-P0086](../../10_corpus/FPL/id_index.md#FPL-2017-P0086) 的高 citation signal，但也明确 citation 只是影响力线索，不等于 adoption 或标准化。后续需要检查 security follow-on papers、artifact/code 和工具链采纳。

### [FPL-SF08](#FPL-SF08)：不规则图、稀疏和科学流内核

目前证据更像候选子领域：[FPL-2024-P0008](../../10_corpus/FPL/id_index.md#FPL-2024-P0008) SERI 针对 HBM quantum chemistry streaming，[FPL-2024-P0011](../../10_corpus/FPL/id_index.md#FPL-2024-P0011) SoGraph 针对 out-of-memory graph processing。它们共同指向 memory-aware FPGA mapping，但还缺多年份深读和 cross-venue 对照。

### [FPL-SF09](#FPL-SF09)：视觉、视频、SLAM、3D 和神经渲染pipelines

这条线与用户方向最直接，但边界必须写清楚：FPL 2016-2025 没有在本轮确认到 3DGS paper row；确认到的是 SLAM、stereo vision、video SR、event-camera tracking、NeRF/neural radiation field 等邻近证据。[FPL-2016-P0068](../../10_corpus/FPL/id_index.md#FPL-2016-P0068) 和 [FPL-2017-P0077](../../10_corpus/FPL/id_index.md#FPL-2017-P0077) 是 SLAM 早期 anchor，但 PDF 级信息不足；[FPL-2020-P0040](../../10_corpus/FPL/id_index.md#FPL-2020-P0040)、[FPL-2020-P0045](../../10_corpus/FPL/id_index.md#FPL-2020-P0045) 覆盖 stereo vision；[FPL-2023-P0014](../../10_corpus/FPL/id_index.md#FPL-2023-P0014) Co-Visu 覆盖 video SR；[FPL-2023-P0028](../../10_corpus/FPL/id_index.md#FPL-2023-P0028) 和 [FPL-2024-P0045](../../10_corpus/FPL/id_index.md#FPL-2024-P0045) 是 NeRF/neural rendering 直接信号；[FPL-2025-P0040](../../10_corpus/FPL/id_index.md#FPL-2025-P0040)、[FPL-2025-P0041](../../10_corpus/FPL/id_index.md#FPL-2025-P0041) 是较新的 SLAM/event-camera 前沿。趋势只能表述为“NeRF/neural rendering emerging signal + vision/SLAM adjacency”，不能升级成成熟 3DGS 子领域。

## 4. 发展趋势

- CAD/architecture/QoR 从 2016 的面积模型校验，发展到 2018-2019 的 ML congestion/routability，再到 2025 的 routing runtime/memory、logic-block arithmetic 和 LLM-assisted CAD scripting。
- HLS automation 从 memory banking，发展到 irregular-code dynamic scheduling 和 C-to-routed-circuit 快速后端闭环。
- ML accelerator 线从低精度/overlay，扩展到 Transformer、ViT、GPT、Diffusion、buffer sizing 和 runtime reconfiguration；这部分需要后续补 B 组 PDF/abstract 级深读。
- System-interface 线跨 PCIe、Arrow、100GbE、block I/O、SVM、DMA 和 HBM；趋势由多篇论文和跨年份证据支撑，但 reuse/adoption 未完成。
- Vision/3D 线在 FPL 内是相邻和新兴信号，尤其是 NeRF/neural rendering；3DGS 直接证据未验证。

## 5. 方法变化

方法变化主要体现在四类：第一，CAD/QoR 从手工模型走向 ML/LLM 辅助判断；第二，HLS 从静态综合走向 selective dynamic scheduling 和 routed-circuit reuse；第三，ML workloads 从 CNN/BNN 走向 Transformer/ViT/GPT/Diffusion，并更强调 buffer、precision 和 runtime reconfiguration；第四，系统论文从单 kernel speedup 转向 host/network/storage/HBM/DMA 的端到端瓶颈。

## 6. 缺失来源

- FPL 2026 接受/论文集/奖项来源。
- IEEE/proceedings/official abstract、keywords、session 和 PDF 批量导出。
- ML/Transformer B-list paper 的 abstract/PDF 级 deep-read 补跑。
- Repository health、artifact reproducibility、citation-neighborhood、benchmark standardization 和 industry/toolchain adoption 审计。
- 针对 FPGA/FCCM/FPT/DAC/ICCAD/DATE/architecture/system/graphics venue的cross-venue综合。
