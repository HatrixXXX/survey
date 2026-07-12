# DAC 论文图谱分析

## 1. 会议定位

本报告中的 `DAC` 指 Design Automation Conference。它在本项目中作为 EDA、芯片到系统设计自动化、HLS/硬件生成、physical design、verification、hardware security、AI for EDA、PIM/near-memory、chiplet/3DIC 和软硬协同设计的重要来源处理。项目不把 DAC 简化成一个大领域标签，而是把它拆成若干具体问题线索，对应 claim <a id="DAC-001-C001"></a>[DAC-001-C001](#DAC-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 的主体来自 DAC 2021-2026 官方 Linklings search program 中的 `Research Manuscript` 条目；2016-2020 因 DBLP/ACM 批量导出在本轮受到限流，只放入少量代表性 anchor rows 并标记 `partial`。2026 是会前 program 状态，也标记 `partial`。对应 claim <a id="DAC-001-C002"></a>[DAC-001-C002](#DAC-001-C002) 到 <a id="DAC-001-C006"></a>[DAC-001-C006](#DAC-001-C006)。

| 年份 | papers.csv 记录数 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 1 | partial | https://archive.dac.com/about/conference-archive/53rd-dac-2016.html |
| 2017 | 1 | partial | https://archive.dac.com/about/conference-archive/54th-dac-2017.html |
| 2018 | 1 | partial | https://archive.dac.com/about/conference-archive/55th-dac-2018.html |
| 2019 | 1 | partial | https://archive.dac.com/about/conference-archive/56th-dac-2019.html |
| 2020 | 1 | partial | https://archive.dac.com/about/conference-archive/57th-dac-2020.html |
| 2021 | 215 | 完全的 | https://58dac.conference-program.com/search-program/ |
| 2022 | 221 | 完全的 | https://59dac.conference-program.com/search-program/ |
| 2023 | 263 | 完全的 | https://60dac.conference-program.com/search-program/ |
| 2024 | 337 | 完全的 | https://61dac.conference-program.com/search-program/ |
| 2025 | 419 | 完全的 | https://62dac.conference-program.com/search-program/ |
| 2026 | 544 | partial | https://63dac.conference-program.com/search-program/ |

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型方法 | 代表论文/信号 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|---|---|
| T12/T07 | AI-for-EDA 预测设计收敛 | 用 ML/GNN/RL/LLM 预测或优化 timing、power、routing、layout、verification | GNN/RL/LLM、QoR 预测、路由/时序/功耗模型 | Gamora、LHNN、RTLFixer、验证 RL rows | 2018-2026 | 帮助理解 AI 辅助 EDA 与硬件生成闭环 | 已验证对于行，临时用于集群 |
| T02/T05 | AI/ML 加速器，量化，稀疏性，数据流 | DNN/Transformer/LLM 加速中的精度、稀疏、数据流和平台映射 | 微缩放、混合精度、稀疏注意力、FPGA/ASIC 映射 | DeepBurning、APTQ、OPAL、2025/2026 LLM 加速器rows | 2016-2026 | 和神经渲染/端侧推理的算子、数据流和低精度设计相邻 | 已验证对于行，临时用于集群 |
| T10/T06 | PIM，近内存和以内存为中心的加速 | 带宽/能耗受限负载如何通过 PIM、near-memory、HBM-PIM 或 storage-side compute 缓解数据搬运 | SRAM/ReRAM/DRAM PIM、3D 绑定、存储内计算 | CMP-PIM、近内存LLM、McPAL、SpecANNS | 2018-2026 | 直接连接 3DGS 的 tile/binning、sorting、alpha blending 与显存/带宽瓶颈 | 已验证对于行，临时用于集群 |
| T02/T06 | NeRF/3DGS 渲染加速 | 神经渲染中的训练、rasterization、sorting、blending 和 streaming 如何映射到硬件 | 近内存 NeRF、GPU 光栅扩展、图块分组、深度推测、GEMM 兼容混合 | Instant-NeRF、GauRast、GS-TG、GSAcc、Local-GS、Adagscale、GEMM-GS、Pipegs、Relay-GS | 2023-2026 | 这是 title-level / program-level 信号，影响证据仍短 | 已验证对于行，临时用于集群 |
| T07/T12 | HLS/DSL/硬件生成和 DSE | 如何把高层算法、IR 或 DSL 变成可综合、可布线、可评价的硬件实现 | HLS、推测 HLS、GNN 成本模型、DSE、生成器 | DeepBurning、HLS GNN 预测、推测HLS 行 | 2016-2026 | 直接关联 FPGA/ASIC 加速器从算法到实现的路线选择 | 已验证对于行，临时用于集群 |
| T12 | 物理设计、布局、布线、时序收敛 | 布局布线、timing、congestion、DFM/signoff 如何闭合 | 分析布局、可微布局、布线优化、时序预测 | SkyPlace、可微布局、布线/时序行 | 2016-2026 | 帮助区分 paper simulator claim 与真实 PPA closure | 已验证对于行，临时用于集群 |
| T12/T10 | Chiplet、2.5D/3DIC 和异构集成 | chiplet/封装/3D 集成中的 cost、thermal、EM、placement 与 architecture co-design | Chiplet 成本模型、3D 布局、混合键合、EM签核 | Chiplet Actuary、ChipletEM、Hydra | 2022-2026 | 对多 die、HBM、近存和高带宽系统设计有参考价值 | 已验证对于行，临时用于集群 |
| T11/T12 | 验证、验证、测试和芯片生命周期 | RTL/formal/DFT/silicon lifecycle 如何减少 bug、test cost 和 bring-up 风险 | 正式+ML、断言分类、测试生成、调试 | ChatCPU、RTLFixer、断言失败 LLM 行 | 2016-2026 | 关系到加速器设计可验证性和工具链可信度 | 已验证对于行，临时用于集群 |

## 4. Accepted Papers 聚类结果

`papers.csv` 目前是 Linklings title/session/topic 级聚类，不是 citation graph 或 full abstract 聚类。cluster 状态全部保留为 provisional。

| 簇 | papers.csv 记录数 | 状态 |
|---|---:|---|
| AI/ML 加速器 量化-稀疏-数据流 | 428 | 临时 |
| PIM 近内存和以内存为中心的加速 | 258 | 临时 |
| 一般 DAC 研究手稿 | 241 | 临时 |
| 验证测试和芯片生命周期 | 187 | 临时 |
| 自主嵌入式 CPS 实时系统 | 129 | 临时 |
| LLM 辅助芯片设计和验证 | 127 | 临时 |
| Chiplet 2.5D 3DIC 异构集成 | 113 | 临时 |
| AI-for-EDA 预测设计收敛 | 111 | 临时 |
| 硬件安全信任和隐私 | 110 | 临时 |
| 新兴器件量子神经拟态计算 | 108 | 临时 |
| 物理设计布局布线时序收敛 | 108 | 临时 |
| HLS DSL 硬件生成和 DSE | 83 | 临时 |
| 基准分析和性能模型 | 1 | 临时 |

时间趋势：

| 时间段 | 主导主题 | 新兴主题 | 下降/不太明显的主题 | 备注 |
|---|---|---|---|---|
| 2016-2018 | 物理设计、HLS、验证/安全 | ML 加速器、PIM、AI-for-EDA | 传统 approximate computing 开始并入 AI/accelerator co-design | 受限于本轮 2016-2020 只抽 anchor rows，需 DBLP/ACM 全量复核 |
| 2019-2020 | AI/ML 加速器、PIM、HLS、安全 | AI-for-EDA、嵌入式系统 | 不明确 | clustering worker 根据 DBLP title anchors 指出 PIM/near-memory 与 ML 加速开始变显眼 |
| 2021-2022 | HLS、PIM、安全性、物理设计 | 小芯片成本/DSE、Transformer 加速器 | generic low-power 单独叙事较弱 | Linklings program 支持 session/topic 级读取 |
| 2023-2024 | AI-for-EDA、LLM 用于设计、物理设计、安全、加速器设计 | 3DIC/chiplet、LLM 辅助 RTL/验证 | DNN-only accelerator 标签被 LLM/PIM/chiplet 细分 | 2024 press release 提供 337 accepted / 29 tracks 的覆盖背景 |
| 2025-2026 | LLM 加速器、LLM for EDA、PIM/近内存、chiplet、验证/安全 | chiplet 作为 2026 top-level program axis | 2026 影响不能判断 | 2026 为会前 partial，不能写长期趋势 |

## 5. Award Papers 分析

| 年份 | 奖项类型 | 论文 | 主题 | 是否纳入里程碑 | 证据状态 |
|---|---|---|---|---|---|
| 2021 | 获胜者 | Gemmini：通过全栈集成实现系统化深度学习架构评估 | 全栈 DNN 加速器生成器/评估 | yes | 奖项已验证；作者跟踪的拼写变体 |
| 2022 | 获胜者 | 面向数据遗忘计算的正式验证硬件信任根 | 安全性、形式验证和芯片生命周期 | 可能已验证 | 奖项；作者元数据冲突跟踪 |
| 2023 | 获胜者 | Gamora：基于图学习的大规模布尔网络符号推理 | AI-for-EDA 收敛预测和优化 | yes | 已验证 |
| 2023 | 获胜者 | RL-CCD：使用基于注意力的自监督强化学习进行并发时钟和数据优化 | AI-for-EDA 时钟/数据优化 | yes | 已验证 |
| 2024 | 获胜者 | Token-Picker：加速文本生成中的注意力通过概率估计实现最小化内存传输 | Transformer/LLM 注意力加速 | yes | 奖项已验证；标题/作者元数据冲突跟踪 |
| 2024 | 提名者 | LLM-HD：使用 GDS 语义编码进行热点检测的布局语言模型 | LLM 辅助设计和验证工作流程 | 可能已验证 | 提名者标题已验证；元数据 needs_review |
| 2024 | 提名者 | ChatCPU：采用 LLM 的敏捷 CPU 设计和验证平台 | LLM 辅助 CPU 设计和验证 | 可能已验证 | 提名者标题已验证；元数据 needs_review |

奖项只说明 DAC 当年的正式认可或 nominee 信号，不自动证明长期影响。2021-2024 的现有 award rows 已用官方 DAC 页面或 DAC press release 复核；2021、2022 和 2024 的作者或题名变体已在 `awards.csv` 中保留 `conflict_status`，不把冲突来源静默合并成单一事实。2025 只找到二级 nominee 线索，未找到 canonical DAC/IEEE/ACM award source；2026 奖项属于正常 partial。

## 6. 代表性论文清单

| 论文 | 角色 | WHY / HOW / WHAT / IMPACT | claim |
|---|---|---|---|
| DeepBurning：为神经网络系列自动生成基于 FPGA 的学习加速器 | 里程碑 | WHY: DAC 2016 中把 neural-network accelerator generation 和 FPGA/HLS 连接。HOW: 自动生成 FPGA 学习加速器。WHAT: title-level DBLP anchor。IMPACT: impact_unverified。 | DAC-001-R001 |
| TIME：基于忆阻器的深度神经网络的内存训练架构 | 里程碑 | WHY: 把 DNN training 和 in-memory architecture 放进同一问题线。HOW: memristor-based training-in-memory。WHAT: title-level DBLP anchor。IMPACT: impact_unverified。 | DAC-001-R002 |
| CMP-PIM：一种节能的基于比较器的内存处理神经网络加速器 | 里程碑 | WHY: PIM+NN accelerator 的早期 DAC anchor。HOW: comparator-based PIM。WHAT: title-level DBLP anchor。IMPACT: impact_unverified。 | DAC-001-R003 |
| Gemmini：通过全栈集成实现系统化深度学习架构评估 | 里程碑 | WHY: DAC 2021 Best Paper Research，代表 full-stack architecture evaluation。HOW/WHAT: 官方 award 页面给出题名、作者和奖项类别。IMPACT: venue_award_verified, long-term impact not separately claimed。 | DAC-001-R004 |
| Gamora：基于图学习的大规模布尔网络符号推理 | 里程碑 | WHY: DAC 2023 Research Track Best Paper row，连接 graph learning 和 Boolean-network reasoning。HOW/WHAT: 官方 award 页面给出题名和作者。IMPACT: venue_award_verified, long-term impact not separately claimed。 | DAC-001-R005 |
| RL-CCD：使用基于注意力的自监督强化学习进行并发时钟和数据优化 | 里程碑 | WHY: DAC 2023 Research Track award row，代表 RL/attention 用于 clock/data optimization。HOW/WHAT: 官方 award 页面给出题名和作者。IMPACT: venue_award_verified, long-term impact not separately claimed。 | DAC-001-R006 |
| RTLFixer：自动修复RTL 大型语言模型的语法错误 | 前沿 | WHY: LLM-assisted RTL repair 方向的 2024 anchor。HOW: LLM 修复 RTL syntax errors。WHAT: Linklings title anchor。IMPACT: new, impact_unverified。 | DAC-001-R007 |
| Token-Picker：加速文本生成中的注意力通过概率估计实现最小化内存传输 | 里程碑 | WHY: DAC 2024 Best Paper Research，直接落在 attention acceleration 与 memory transfer minimization。HOW/WHAT: 官方 press release 给出题名、作者和奖项类别。IMPACT: venue_award_verified, long-term impact not separately claimed。 | DAC-001-R008 |
| 近内存 LLM 基于 3D DRAM 到逻辑混合绑定的推理处理器 | 前沿 | WHY: 2025 把 LLM inference、near-memory 和 3D bonding 合到同一硬件路线。HOW: 3D DRAM-to-logic hybrid bonding。WHAT: title/session anchor。IMPACT: new, impact_unverified。 | DAC-001-R009 |
| SpecANNS：通过推测加速基于图的近似最近邻搜索存储内计算 | 前沿 | WHY: 2026 会前 program 中的 storage-side acceleration 代表信号。HOW: speculative in-storage computing。WHAT: 官方 Linklings title/abstract。IMPACT: too early。 | DAC-001-R010 |

## 7. 发展脉络

| 技术路线 | 核心问题 | 方法变化 | 代表题名/信号 | 活跃年份 | 证据 |
|---|---|---|---|---|---|
| AI-for-EDA 预测设计收敛 | timing、logic、clock/data、layout hotspot 等 EDA 闭环预测和优化 | 从预布线 timing prediction、GNN slack prediction、graph/RL optimization，走到 LLM-assisted layout/standard-cell flows | 基于机器学习的预路由时序预测、Gamora、RL-CCD、LLM-HD、TOPCELL | 2019、2021-2026 部分 | DAC-001-L001 |
| LLM-芯片设计/验证 | 把 LLM 放进 RTL repair、CPU design verification、SVA/assertion、DSE 和 layout 自动化 | 从 2024 nominee/frontier rows 扩展到 2026 verification/HLS/DSE program rows | ChatCPU、LLM-HD、Svacoder、PRO-V-R1、Paretopilot、CHiRM-DSE | 2024-2026 部分 | DAC-001-L002 |
| AI/ML 加速器和全栈生成器 | DNN/Transformer/LLM accelerator 如何生成、评估和映射 | 从 FPGA generator 和 full-stack evaluation，转到 LLM attention、KV cache、memory-transfer 优化 | DeepBurning、Gemmini、Token-Picker、AttenPIM、Crystal-KV | 2016、2021-2026 部分 | DAC-001-L003 |
| PIM / 近内存 / 以内存为中心 AI | 权重、KV cache、embedding、graph/search 的数据搬运瓶颈 | 从 ReRAM/memristor NN PIM，转到 LLM attention、KV/MoE/RAG、HBM-PIM 和 3D memory | TIME、CMP-PIM、AttenPIM、BlockPIM、NVLLM、McPAL | 2017-2018、2021-2026 部分 | DAC-001-L004 |
| HLS / 硬件生成 / DSE | 从 C/C++、IR、DSL 或模型图生成硬件并搜索 PPA/资源 Pareto | 从 HLS/memory-system synthesis，转到 LLM-guided HLS DSE 和 FPGA accelerator exploration | Cayman、Paretopilot、CHiRM-DSE、LLM-Based Automatic Architecture Optimization for AI Model HLS Implementation on FPGA | 2021-2026 partial | DAC-001-L005 |
| 物理设计/时序/布线加速 | placement、routing、timing、3D floorplan 和 signoff bottleneck | 从 GPU/path-based timing、GNN slack prediction，转到 differentiable GPU STA 和 3D floorplanning | GPU-accelerated Path-based Timing Analysis、A Timing Engine Inspired GNN、Warp-STAR、POLT | 2021-2026 partial | DAC-001-L006 |
| Chiplet / 2.5D / 3DIC / 晶圆级 | chiplet、3D memory、wafer-scale system 的 cost/PPA/floorplan/interconnect co-design | 从集成/PPA 研究，转到 chiplet-CIM LLM inference、wafer-scale cost model 和 3D floorplan | Network-on-Interposer、3D-CIMlet、WSC-Cost、POLT | 2021-2026 partial | DAC-001-L007 |

简单按时间看：

2016-2018：DAC 的稳定底盘仍是 physical design、timing、routing、verification、security 和 HLS。AI/ML accelerator 与 PIM 已出现，但多是 anchor signal，本轮 2016-2020 没有全量抽取，不能把比例写死。

2019-2022：AI/ML 与 EDA 的关系变成双向。一条线是 AI/ML accelerator、PIM、near-memory、Transformer/ViT/FPGA-aware quantization；另一条线是 ML/GNN/RL 用于 timing、congestion、HLS performance prediction 和 design closure。Gemmini 的 2021 Best Paper Research 信号说明 DAC 已把 full-stack architecture evaluation 当成重要议题；2022 Root-of-Trust award row 说明 security/formal verification 仍是 DAC 的硬核主线之一，但姓名编码需要复核。

2023-2024：LLM 开始进入 chip design workflow。ChatCPU、LLM-HD、RTL/verification rows 把“生成/修复/验证设计”推到 DAC 前台；同一时期 3D placement、chiplet、near-memory 和 LLM accelerator 也更常一起出现。

2025-2026：LLM、PIM/HBM-PIM、chiplet、3D bonding、LLM-assisted verification/design 和 3DGS/NeRF acceleration 同时升温。2026 只可当 program frontier signal，不能当成熟趋势结论。

## 8. 团队线索和代表成果

本节只写 corpus 内能被 award/corpus 支撑的团队线索，不等同于跨会议排名或团队实力判断。作者消歧、机构变更追踪和跨会议验证仍需后续实体审计；single-paper signal 只能当跟踪对象。

| 团队/机构线索 | 主要路线 | 代表成果 | 证据状态 | claim |
|---|---|---|---|---|
| UC Berkeley / MIT Gemmini line | 全栈加速器生成器、RISC-V/Chipyard-相邻评估堆栈 | Gemmini DAC 2021 年最佳论文研究 | 已验证奖项/隶属关系行；多年 DAC 连续性 needs_review | DAC-001-T001 |
| KAIST / Lee-Sup Kim line | 注意力加速、内存传输减少、LLM/文本生成硬件 | Token-Picker DAC 2024 年最佳论文研究 | 已验证获奖行；更广泛的 DAC 连续性 needs_review | DAC-001-T002 |
| Georgia Tech / Sung Kyu Lim 线 | 物理设计、3D IC、RL/注意力优化、GNN 辅助路由 | RL-CCD、DCO-3D、GNN-MLS | 已验证语料行；隶属关系/日期处理 needs_review | DAC-001-T003 |
| 元谢线 | 布尔网络推理图学习、量子编译信号 | Gamora、Phoenix | 验证列出的行；更广泛的 PIM/AI-硬件连续性 needs_review | DAC-001-T004 |
| 2025 PIM/LLM 单paper rows | 3D-CIM/chiplet、token-stationary CIM、PIM 注意力、长上下文 PIM 内存布局 | 3D-CIMlet、3D-TokSIM、AttenPIM、BlockPIM | 已验证单纸信号，而非比较 claim | DAC-001-T005 |
| 2026 台湾物理设计/chiplet 活动信号 | 小芯片 DSE、PCB 轨道/信号协同设计、GPU STA、布局/尺寸调整、封装 PG 综合 | ChiSER、统一轨道信号协同设计、Warp-STAR、HyPAS、BLADE | 部分活性信号，非比较性 claim | DAC-001-T006 |
| EDA 供应商和行业实验室 | 生产 EDA、AI/EDA、物理实现、验证/工程跟踪 | Synopsys 链接的 RL-CCD 行、Cadence/Siemens 工程和事件信号 | 在切片中验证存在；更广泛的连续性 needs_review | needs_review |

## 9. 对博士入门者的阅读路线

必读 10 篇：DeepBurning、TIME、CMP-PIM、Gemmini、Machine Learning-Based Pre-Routing Timing Prediction、AHEC、Gamora、RL-CCD、Token-Picker、Near-Memory LLM Inference Processor based on 3D DRAM-to-logic Hybrid Bonding。

扩展 20 篇：Compensated-DNN、BitBlade、HybridDNN、NN-LUT、FPGA-aware ViT acceleration、Chiplet Actuary、High-level synthesis performance prediction using GNNs、LHNN、APTQ、OPAL、SkyPlace、Mixed-Size 3D Analytical Placement、Insights from Rights and Wrongs、Hydra、McPAL、SpecANNS、3D-DuRA、RTLFixer、ChatCPU、LLM_HD。

适合跟踪的近年方向：LLM-assisted design/verification、PIM/HBM-PIM/near-storage for LLM、chiplet/3DIC signoff、AI-for-EDA closure prediction、HLS performance models、security and confidential-computing side channels。

## 10. 与我的方向的连接点

DAC 已经出现直接的 NeRF/3DGS/4DGS 官方 Linklings 题名：2023 的 Instant-NeRF；2025 的 GauRast、GS-TG、GSAcc、Local-GS、StreamingGS；2026 会前 program 里的 Adagscale、GEMM-GS、Is 2D Gaussian Enough?、Pipegs、Relay-GS。现阶段只能把它们视为 title-level / program-level 信号，还不能据此判断 3DGS 已形成稳定长期谱系或影响链。2026 相关条目全部保持 `partial`。

对你的 FPGA/神经渲染加速方向，最值得跟的不是泛泛的 graphics 标签，而是几个具体问题：tile/binning 和 sorting 能否硬件化，alpha blending 能否改写成更适合 Tensor Core/GEMM 或流水并行的形式，Gaussian locality 能否减少访存，训练和推理是否适合 near-memory 或 streaming 架构。对应 claim <a id="DAC-001-C008"></a>[DAC-001-C008](#DAC-001-C008)。

## 11. 缺失来源

- 缺少 DAC 2016-2020 的 ACM DL/DBLP/官方 program 全量 title、author、DOI export。
- 缺少 2025 DAC award outcomes 的 canonical source；本轮只找到 SIGDA 二级 nominee 线索，未写成确定 award fact。
- 2026 rows 的 final proceedings、DOI、award outcomes 和后续影响证据需等 DAC 2026 结束后补。
- NeRF/3DGS/4DGS 相关题名已进入 screening/evidence matrix，部分 2025 DOI/作者已回填，但仍缺逐篇 PDF、artifact/code、citation structure 和 adoption 证据；2026 相关条目保持 partial program signal。
- 缺少 artifact/code checks for Gemmini、RTLFixer、ChatCPU、3DGS accelerators、PIM/LLM systems 和 HLS/DSE frameworks。
- 缺少跨 ICCAD/DATE/ASP-DAC/FPGA/FCCM/FPL/FPT/architecture venue 的对照矩阵。
