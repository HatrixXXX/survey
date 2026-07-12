# ICCAD 论文图谱分析

## 1. 会议定位

本报告中的 `ICCAD` 指 IEEE/ACM International Conference on Computer-Aided Design。ICCAD 在本项目中作为 EDA 顶级来源处理，覆盖从 device/circuit 到 system level、post-CMOS、实现闭环、验证、安全、HLS/架构 DSE、AI for EDA 等设计自动化问题。该定位来自 ICCAD 官方页面和项目 `VENUE_REGISTRY.csv`，对应 claim <a id="ICCAD-001-C001"></a>[ICCAD-001-C001](#ICCAD-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 使用 DBLP ICCAD proceedings TOC/API 生成 2016-2025 行；其中 `paper_type=accepted_paper` 用于第 4 节聚类，`paper_type=invited_talk` 单独保留但不计入 accepted-paper 聚类。每行保留 DOI/ACM/IEEE URL 或 DBLP URL。2024/2025 官方 accepted/program 页面、IEEE CEDA William J. McCalla 奖项页和 ICCAD 2022 history 页用于补强 coverage 和 award 证据。2026 官方站点只确认会议计划信息，未找到完整 accepted-paper/award list，因此 2026 标记为 `partial`，不生成 accepted-paper 行。对应 claim <a id="ICCAD-001-C002"></a>[ICCAD-001-C002](#ICCAD-001-C002) 到 <a id="ICCAD-001-C004"></a>[ICCAD-001-C004](#ICCAD-001-C004)。

| 年份 | paper.csv 总行数 | accepted_paper 行数 | invited_talk 行数 | 状态 | 主要来源 |
|---|---:|---:|---:|---|---|
| 2016 | 133 | 131 | 2 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2017 | 143 | 124 | 19 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2018 | 135 | 135 | 0 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2019 | 133 | 113 | 20 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2020 | 169 | 156 | 13 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2021 | 152 | 145 | 7 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2022 | 164 | 159 | 5 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2023 | 200 | 200 | 0 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2024 | 239 | 239 | 0 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2025 | 311 | 304 | 7 | 完全的 | DBLP ICCAD 会议记录 TOC |
| 2026 | 0 | 0 | 0 | partial | ICCAD 2026 官方网站；尚无接受的列表 |

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型方法 | 代表论文 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|---|---|
| T07/T06 | HLS、FPGA、可重新配置编译和 DSE | 从算法/架构描述到可实现硬件和系统设计空间 | HLS 建模、DSE、生成器、FPGA/加速器框架 | COMBA； DNN构建器； BOOM-资源管理器； LaZagna | 2017-2025 | 直接连接 FPGA/3DGS 加速器从算法到硬件落地 | 已验证论文，临时集群 |
| T03/T07 | INR、NeRF、神经渲染和 3DGS 加速 | 神经场/神经渲染负载如何映射到端侧或流式硬件 | 渲染引擎、数据流架构、编译器、workload 调度 | RT-NeRF； INR-拱门；高普雷；无冗余、无停顿 | 2022-2025 | 与 3DGS/FPGA 加速方向直接相关，但目前只是 emerging signal | 标题级已验证，主题成熟度未验证 |
| T02/T07 | AI 模型加速器和软硬件协同设计 | DNN/Transformer/LLM 等负载如何进入加速器和软硬协同设计 | 数据流模板、量化、PIM/CIM、LLM 服务/调度 | 咖啡因； DNN构建器；敏捷LLM加速器； FlexLLM | 2016-2025 | 对端侧智能、LLM 和相邻神经渲染负载的加速叙事有参考 | 已验证对于行，临时用于集群 |
| T12/T10 | 物理设计、时序、布线、可靠性 | 如何让芯片实现满足 timing/power/reliability/placement/routing 约束 | 布局、布线、STA、EM/IR、decap、DTCO | SALT；打开定时器；规格部分； EM/power-grid 获奖论文 | 2016-2025 | 连接 PPA、时序收敛、EDA 闭环和真实可实现性 | 已验证论文，临时集群 |
| T07/T11 | EDA AI 代理、基准测试和电路表示 | 用 ML/LLM/统计模型预测或优化设计流程，或把硬件设计变成可学习表示 | GNN、RL、LLM、基准测试、电路表示 | VerilogEval； HLS 飞行员；分析流；开放定时器 | 2020-2025 | 对“AI 写硬件/工具链自动化”有方法论参考 | 标题级验证，摘要缺失 |
| T10/T05 | Memory/CIM/PIM/post-CMOS 加速器感知设计 | 存储和新器件如何改变计算位置、能效和可靠性 | PIM、CIM、NVCiM、SRAM/NAND、神经形态、近似设计 | NVCiM 奖； LLM-在-掌上； TP-DCIM | 2016-2025 | 连接 LLM/Transformer 低能耗推理和端侧部署 | 已验证对于行，临时用于集群 |
| T12/T11 | 验证、安全、测试、基准测试/工具 | 设计正确性、安全性、测试和可复现工具如何进入 EDA 主线 | 正式、模糊测试、特洛伊木马/安全验证、SAT/SMT、基准测试/工具 | 恶意 LUT；HyperFuzzing； PolyCleaner | 2016-2025 | 对硬件 IP 正确性、安全验证和 benchmark 可信度有参考 | 已验证对于行，临时用于集群 |

## 4. Accepted Papers 聚类结果

本节只统计 `paper_type=accepted_paper` 的 1706 行；`invited_talk` 行保留在 `papers.csv` 中，但不计入 accepted-paper 聚类。`topic_cluster_label` 是标题关键词加人工规则的 provisional 标注，适合做 venue 内部浏览，不应直接升级为全局 taxonomy。`Other or needs-review` 是 unresolved/proceedings-row residue，不作为 coherent dominant topic 解读。对应 claim <a id="ICCAD-001-C005"></a>[ICCAD-001-C005](#ICCAD-001-C005) 和 <a id="ICCAD-001-C010"></a>[ICCAD-001-C010](#ICCAD-001-C010)。

| 序号 | 簇 | accepted_paper 记录数 | 状态 |
|---:|---|---:|---|
| 1 | AI 模型加速器和软硬件协同设计 | 303 | 临时 |
| 2 | HLS、FPGA、可重新配置编译和 DSE | 187 | 临时 |
| 3 | CIM、PIM、新兴存储器和非常规加速器 | 126 | 临时 |
| 4 | EDA AI 代理、基准测试和电路表示 | 118 | 临时 |
| 5 | 布局、布线、布局规划和时钟设计 | 116 | 临时 |
| 6 | 硬件安全、隐私和信任 | 114 | 临时 |
| 7 | 时序、功耗、散热、可靠性和签核 | 105 | 临时 |
| 8 | 量子、低温、微流体和生物芯片设计自动化 | 68 | 临时 |
| 9 | 逻辑综合、映射、SAT 和形式方法 | 61 | 临时 |
| 10 | 模拟、RF 和混合信号自动化 | 33 | 临时 |
| 11 | 内存、存储和数据密集型系统 | 26 | 临时 |
| 12 | INR、NeRF、神经渲染和 3DGS 加速 | 7 | 临时 |
| 13 | 其他或需求审查 ICCAD 程序行 | 442 | 临时 |

| 时间段 | 主导主题 | 代表论文/信号 | 备注 |
|---|---|---|---|
| 2016-2018 | 硬件安全、隐私和信任；时序、功率、热量、可靠性和签核； HLS、FPGA、可重新配置编译和 DSE | 针对片上电网的基于物理的快速电迁移检查 | 临时标题级聚类 |
| 2019-2021 | AI 模型加速器和软硬件协同设计； HLS、FPGA、可重新配置编译和 DSE；布局、布线、布局规划和时钟设计 | 针对电迁移引起的电压故障的电网修复 | 临时标题级聚类 |
| 2022-2023 | AI 模型加速器和软硬件协同设计； HLS、FPGA、可重新配置编译和 DSE； CIM、PIM、新兴内存和非常规加速器 | SpecPart：用于超图分区解决方案改进的监督频谱框架 | 临时标题级聚类 |
| 2024-2025 | AI 模型加速器和软硬件协同设计； HLS、FPGA、可重新配置编译和 DSE； EDA AI 代理、基准测试和电路表示 | 高效敏捷框架 LLM 加速器开发和模型推理 | 临时标题级聚类 |

## 5. Award Papers 分析

| 年份 | 奖项类型 | 论文 | 作者/团队 | 主题 | 是否纳入里程碑 | 证据状态 |
|---|---|---|---|---|---|---|
| 2025 | 前端奖 | LaZagna：灵活 3D 的开源框架 FPGA 架构探索 | Ismael Youssef|Hang Yang|丛浩 | hls_fpga_reconfigurable_compilation | yes | 已验证 |
| 2025 | 后端奖 | 基于半定编程的配电网优化去耦电容器布置 | 蔡宗英|毛伟汉|Yao-Wen Chang|Yang Lu|Jerry Bai|Bin-Chyi Tseng | placement_routing_floorplan_clock | yes | 已验证 |
| 2025 | 十年回顾最具影响力论文 | Caffeine：走向深度卷积神经网络的统一表示和加速 | 张晨|方振曼|周佩佩|潘沛辰|Jason Cong | ai_model_accelerator_hw_sw_codesign | yes | 已验证 |
| 2024 | 前端奖 | 高效敏捷框架 LLM 加速器开发和模型推理 | 陈吕程|吴英|文晨怡|王世章|张莉|贝宇|孙琪|Cheng Zhuo | ai_model_accelerator_hw_sw_codesign | yes | 已验证 |
| 2024 | 后端奖 | DTCO 中基于神经常微分方程的过程建模通用方法：化学机械平坦化和镀铜案例研究 | Yue Qi|Lan Chen | timing_power_thermal_reliability_signoff | yes | 已验证 |
| 2024 | 十年回顾最具影响力论文 | OpenTimer：高性能时序分析工具 | Tsung-Wei Huang|Martin D. F. Wong | timing_power_thermal_reliability_signoff | yes | 已验证 |
| 2023 | 前端类别 | 追求质量和速度：实用乱码电路的逻辑综合 | Mingfei Yu|Giovanni De Micheli | hardware_security_privacy_trust | yes | 已验证 |
| 2023 | 后端类别 | 提高现实NVCiM DNN 加速器通过右删失高斯噪声训练的最坏情况性能 | Zheyu Yan|Yifanqin|Wujie Wen|X. Sharon Hu|Yiyu Shi | ai_model_accelerator_hw_sw_codesign | yes | 已验证 |
| 2023 | 十年回顾最具影响力论文 | 可靠神经形态计算系统的缩减和 IR-drop 补偿技术 | Beiye Liu|Hai Li|Yiran Chen|Xin Li|Tingwen Huang|Qing Wu|Mark Barnell | cim_pim_emerging_memory_unconventional_accel | yes | 已验证 |
| 2022 | 前端奖 | Attack Directories on ARM big.LITTLE Processors | Zili Kou|Sharad Sinha|Wenjian He|Wei Zhang | hardware_security_privacy_trust | yes | 已验证 |
| 2022 | 后端奖 | SpecPart：用于超图分区解决方案改进的监督频谱框架 | Ismail Bustany|Andrew B. Kahng|Ioannis Koutis|Bodhisatta Pramanik|Ziang Wang | placement_routing_floorplan_clock | yes | 已验证 |
| 2022 | 十年回顾最具影响力论文 | 面向重构的近似加法器设计及其应用 | 叶荣|王庭奇|冯远|Rakesh Kumar|徐强 | cim_pim_emerging_memory_unconventional_accel | yes | 已验证 |
| 2021 | 前端奖 | BOOM-Explorer: RISC-V BOOM 微架构设计空间探索框架 | 陈白|孙琪|翟建旺|马玉哲|贝宇|Martin D. F. Wong | hls_fpga_reconfigurable_compilation | yes | 已验证 |
| 2021 | 后端奖 | 基于边界反射的瞬态电迁移应力分析建模 | Mohammad Abdullah Al Shohel|Vidya A. Chhabria|Nestor Evmorfopoulos|Sachin S. Sapatnekar | timing_power_thermal_reliability_signoff | yes | 已验证 |
| 2021 | 十年回顾最具影响力论文 | MACACO：近似计算电路的建模和分析 | Rangharajan Venkatesan|Amit Agarwal|Kaushik Roy|Anand Raghunathan | cim_pim_emerging_memory_unconventional_accel | yes | 已验证 |
| 2020 | 前端奖 | 用于 SoC 安全验证的 HyperFuzzing | Sujit Kumar Muduli|Gourav Takhar|Pramod Subramanayan | hardware_security_privacy_trust | yes | 已验证 |
| 2020 | 后端奖 | 使用随机有效电流模型进行电迁移检查 | Adam Issa|Valeriy Sukharev|Farid N. Najm | timing_power_thermal_reliability_signoff | yes | 已验证 |
| 2020 | 十年回顾最具影响力论文 | 3D-ICE：具有层间液体冷却功能的 3D IC 的快速紧凑瞬态热建模 | A. Sridhar|A. Vincenzi|M. Ruggiero|T. Brunschwiler|D. Atienza | timing_power_thermal_reliability_signoff | yes | 已验证 |
| 2019 | 前端奖 | 对 EISC 上的存储内计算 workload 进行分析和建模 - 基于 FPGA 的系统级仿真平台 | Zhunyuan Ruan|Tong He|Jason Cong | hls_fpga_reconfigurable_compilation | yes | 已验证 |
| 2019 | 后端奖 | 针对电迁移引起的电压故障的电网修复 | Zahi Moudallal|Valeriy Sukharev|Farid N. Najm | timing_power_thermal_reliability_signoff | yes | 已验证 |
| 2019 | 十年回顾最具影响力论文 | 非易失性忆阻器存储器：器件特性和设计含义 | Yenpo Ho|Garng M. Huang|Peng Li | cim_pim_emerging_memory_unconventional_accel | yes | 已验证 |
| 2018 | 前端奖 | DNNBuilder：用于构建高性能 DNN FPGA 硬件加速器的自动化工具 | Xiaofan 张|Junsong Wang|Chao Zhu|Yonghua Lin|Jinjun Xiong|Wen-Mei Hwu|Deming Chen | hls_fpga_reconfigurable_compilation | yes | 已验证 |
| 2018 | 后端奖 | PolyCleaner：在向后重写以验证百万门乘数之前清理多项式 | Alireza Mahzoon|Daniel Grosse|Rolf Drechsler | logic_synthesis_mapping_sat_formal | yes | 已验证 |
| 2018 | 十年回顾最具影响力论文 | 基于 TSV 的 3D 片上网络链路的低开销容错方案 | Igor Loi|Luca Benini|Subhasish Mitra|Thomas H. Lee|Shinobu Fujita | other_needs_review | yes | 已验证 |
| 2017 | 前端奖 | COMBA：基于模型的综合分析框架，用于实际应用的高级综合 | Jieru Zhu|Liang Feng|Wei Zhang|Sharad Sinha|Yun Liang|Bingsheng He | hls_fpga_reconfigurable_compilation | yes | 已验证 |
| 2017 | 后端奖 | SALT：通过新颖的 steiner 浅光树算法证明良好的路由拓扑 | Gengjie Chen|Peishan Tu|Evangeline F. Y. Young | placement_routing_floorplan_clock | yes | 已验证 |
| 2017 | 十年回顾最具影响力论文 | 轻量级安全 PUF | Mehrdad Majzoobi|Farinaz Koushanfar|Miodrag Potkonjak | other_needs_review | yes | 已验证 |
| 2016 | 前端奖 | 恶意 LUT：由设计流程注入并触发的隐形 FPGA 特洛伊木马 | Christian Krieg|Clifford Wolf|Axel Jantsch | hls_fpga_reconfigurable_compilation | yes | 已验证 |
| 2016 | 后端奖 | 针对片上电网的基于物理的快速电迁移检查 | Sandeep Chatterjee|Valeriy Sukharev|Farid N. Najm | timing_power_thermal_reliability_signoff | yes | 已验证 |
| 2016 | 十年回顾最具影响力论文 | 负偏压温度不稳定性分析模型 | Sanjay V. Kumar|Chris H. Kim|Sachin S. Sapatnekar | other_needs_review | yes | 已验证 |

奖项事实优先使用 IEEE CEDA William J. McCalla 官方奖项页；2016-2021 的历史奖项同时使用 ICCAD 2022 history 页复核。奖项只说明本 venue 的正式认可，不自动证明长期影响；除 ten-year retrospective 的“十年影响”奖项名称本身外，其他 impact 均保留 `impact_unverified`，需要后续 citation、artifact、工具链复用或跨 venue 证据补齐。

## 6. 代表论文清单

| 论文 | 角色 | WHY / HOW / WHAT / IMPACT | claim |
|---|---|---|---|
| 针对片上电网的基于物理的快速电迁移检查 | 里程碑 | WHY：William J. McCalla ICCAD 获奖行；影响需要后续审计。 HOW/WHAT：请参阅标题级源和簇 `Timing, power, thermal, reliability, and signoff`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C018"></a>[ICCAD-001-C018](#ICCAD-001-C018) |
| 恶意 LUT：由设计流程注入并触发的隐形 FPGA 木马 | 里程碑 | WHY：William J. McCalla ICCAD 奖行；影响需要后续审计。 HOW/WHAT：请参阅标题级源和簇 `HLS, FPGA, reconfigurable compilation, and DSE`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C019"></a>[ICCAD-001-C019](#ICCAD-001-C019) |
| Caffeine：致力于深度卷积神经网络的统一表示和加速 | 里程碑 | WHY：William J. McCalla ICCAD 奖行；影响需要后续审计。 HOW/WHAT：请参阅标题级源和簇 `AI model accelerators and hardware-software co-design`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C020"></a>[ICCAD-001-C020](#ICCAD-001-C020) |
| SALT：通过新颖的 steiner 浅光树算法证明良好的路由拓扑 | 里程碑 | WHY：William J. McCalla ICCAD 奖行；影响需要后续审计。 HOW/WHAT：请参阅标题级源和簇 `Placement, routing, floorplanning, and clock design`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C021"></a>[ICCAD-001-C021](#ICCAD-001-C021) |
| COMBA：基于模型的综合分析框架，用于实际应用的高级综合 | 里程碑 | WHY：2017年前端奖； HLS 基于模型的分析路线。 HOW/WHAT：请参阅标题级源和簇 `HLS, FPGA, reconfigurable compilation, and DSE`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C022"></a>[ICCAD-001-C022](#ICCAD-001-C022) |
| PolyCleaner：在向后重写之前清理多项式以验证百万门乘数 | 里程碑 | WHY：William J. McCalla ICCAD 奖行；影响需要后续审计。 HOW/WHAT：请参阅标题级源和簇 `Logic synthesis, mapping, SAT, and formal methods`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C023"></a>[ICCAD-001-C023](#ICCAD-001-C023) |
| DNNBuilder：用于为 FPGA 构建高性能 DNN 硬件加速器的自动化工具 | 里程碑 | WHY：William J. McCalla ICCAD 奖行；影响需要后续审计。 HOW/WHAT：请参阅标题级源和簇 `HLS, FPGA, reconfigurable compilation, and DSE`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C024"></a>[ICCAD-001-C024](#ICCAD-001-C024) |
| 针对电迁移引起的电压故障的电网修复 | 里程碑 | WHY：2019 年后端奖；电网修复路线。 HOW/WHAT：请参阅标题级源和簇 `Timing, power, thermal, reliability, and signoff`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C025"></a>[ICCAD-001-C025](#ICCAD-001-C025) |
| 对 EISC 上的存储内计算 workload 进行分析和建模 - 基于 FPGA 的系统级仿真平台 | 里程碑 | WHY：2019年前端奖； storage/FPGA 系统级模拟路由。 HOW/WHAT：请参阅标题级源和簇 `HLS, FPGA, reconfigurable compilation, and DSE`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C026"></a>[ICCAD-001-C026](#ICCAD-001-C026) |
| 使用随机有效电流模型进行电迁移检查 | 里程碑 | WHY：2020后端奖； EM可靠性分析路线。 HOW/WHAT：请参阅标题级源和簇 `Timing, power, thermal, reliability, and signoff`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C027"></a>[ICCAD-001-C027](#ICCAD-001-C027) |
| 用于 SoC 安全验证的 HyperFuzzing | 里程碑 | WHY：2020年前端奖； SoC安全验证Pathways。 HOW/WHAT：请参阅标题级源和簇 `Hardware security, privacy, and trust`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C028"></a>[ICCAD-001-C028](#ICCAD-001-C028) |
| BOOM-Explorer: RISC-V BOOM 微架构设计空间探索框架 | 里程碑 | WHY：2021年前端奖；微架构DSE路线。 HOW/WHAT：请参阅标题级源和簇 `HLS, FPGA, reconfigurable compilation, and DSE`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C029"></a>[ICCAD-001-C029](#ICCAD-001-C029) |
| 基于边界反射的瞬态电迁移应力分析建模 | 里程碑 | WHY：William J. McCalla ICCAD 获奖行；影响需要后续审计。 HOW/WHAT：请参阅标题级源和簇 `Timing, power, thermal, reliability, and signoff`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C030"></a>[ICCAD-001-C030](#ICCAD-001-C030) |
| SpecPart：用于超图分区解决方案改进的监督频谱框架 | 里程碑 | WHY：2022年后端奖；分区/物理设计路线。 HOW/WHAT：请参阅标题级源和簇 `Placement, routing, floorplanning, and clock design`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C031"></a>[ICCAD-001-C031](#ICCAD-001-C031) |
| Attack Directories on ARM big.LITTLE Processors | 里程碑 | WHY：2022年前端奖；微架构攻击/安全路线。 HOW/WHAT：请参阅标题级源和簇 `Hardware security, privacy, and trust`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C032"></a>[ICCAD-001-C032](#ICCAD-001-C032) |
| RT-NeRF：实现沉浸式 AR/VR 渲染的实时设备上神经辐射场 | 前沿 | WHY：用于设备上神经辐射场加速的 2022 程序信号。 HOW/WHAT：请参阅标题级源和簇 `INR, NeRF, neural rendering, and 3DGS acceleration`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C033"></a>[ICCAD-001-C033](#ICCAD-001-C033) |
| INR-Arch：用于隐式神经表示处理中任意阶梯度计算的数据流架构和编译器 | 前沿 | WHY：用于隐式神经表示架构/编译器工作的 2023 程序信号。 HOW/WHAT：请参阅标题级源和簇 `INR, NeRF, neural rendering, and 3DGS acceleration`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C034"></a>[ICCAD-001-C034](#ICCAD-001-C034) |
| 提高现实NVCiM DNN 加速器通过右删失高斯噪声训练的最坏情况性能 | 前沿 | WHY：2023后端奖；非易失性内存计算加速器的可靠性。 HOW/WHAT：请参阅标题级源和簇 `AI model accelerators and hardware-software co-design`。 IMPACT：impact_unverified 超出奖励/工具状态。 | <a id="ICCAD-001-C035"></a>[ICCAD-001-C035](#ICCAD-001-C035) |

扩展阅读建议：Caffeine、DNNBuilder、COMBA、EISC in-storage computing、3D-ICE、MACACO、BOOM-Explorer、HyperFuzzing、SpecPart、OpenTimer、NVCiM DNN accelerator training、2024 LLM accelerator framework、LaZagna、LLM-on-the-Palm、TP-DCIM。

## 7. 发展脉络

- 2016-2018：ICCAD 的前后端奖项分别覆盖 FPGA Trojan/security、HLS model analysis、DNN/FPGA accelerator generation，以及 EM、routing、multiplier verification 等实现闭环问题。这一阶段已经能看到 HLS/FPGA/accelerator 和物理实现/验证两条线并行。
- 2019-2021：system-level emulation、SoC security validation、RISC-V microarchitecture DSE、3D thermal modeling、approximate-computing modeling 与 power-grid/EM reliability 同时进入奖项层。对硬件加速方向来说，这说明 ICCAD 不只关注传统后端，也接收可解释的架构探索、系统建模和验证方法。
- 2022-2023：security、hypergraph partitioning、logic synthesis for garbled circuits、NVCiM accelerator worst-case performance 等主题强化了“特定新计算/安全/存储负载出现后，EDA 方法随之更新”的路线。
- 2024-2025：LLM accelerator framework、3D FPGA architecture exploration、PIM/NAND mobile LLM、digital SRAM CIM for Transformer 等标题信号说明 AI/LLM 负载开始进入 ICCAD；同时 2022-2025 已出现 RT-NeRF、INR-Arch、Rapid-INR、Residual-INR、SLTarch、GauPRE、No Redundancy, No Stall 等少量 neural rendering/INR/3DGS 标题信号。目前只能写作 emerging signal，不能写成成熟稳定 topic。

| 技术路线 | 核心问题 | 代表论文 | 活跃年份 | 转折点 |
|---|---|---|---|---|
| HLS / 架构 DSE / 加速器生成 | 怎样从算法和微架构描述稳定生成可评估硬件 | COMBA、DNNBuilder、BOOM-Explorer、LaZagna | 2017-2025 | 从 HLS 分析到 DNN/LLM/FPGA architecture exploration |
| 物理实现闭包 | timing/routing/placement/EM/IR/thermal 如何决定设计能否实现 | SALT、SpecPart、OpenTimer、 3D-ICE、EM 获奖论文 | 2016-2025 | 从单点后端算法到 ML/optimization-assisted closure |
| 安全与验证 | 硬件安全、形式验证、fuzzing、Trojan/test 如何进入 CAD 主线 | 恶意 LUT、HyperFuzzing、PolyCleaner | 2016-2023 | 从传统 test/verification 扩展到 SoC/security validation |
| Memory/CIM/PIM 和 post-CMOS | 存储、新器件和 compute-in-memory 如何改变加速器设计 | NVCiM、LLM-on-the-Palm、TP-DCIM | 2016-2025 | 从 device implication 到 Transformer/LLM memory-centric acceleration |
| AI/ML 用于 EDA | ML/LLM 是否能预测或优化 EDA 流程中的困难步骤 | 时序/布局预测、RL/LLM rows | 2020-2025 | 从局部预测走向工具链 assistant 和 design automation |

## 8. 领跑团队和代表成果

这里的“领跑”只表示 2016-2025 ICCAD corpus 内反复出现，并且与某条技术路线绑定；不等同于跨会议或 citation 影响力排名。作者实体和机构归属没有做全量消歧。

| 团队/机构线索 | 主要路线 | 代表成果 | claim |
|---|---|---|---|
| Bei Yu / CUHK-adjacent rows | 微架构 DSE、LLM 加速器框架、物理设计 | BOOM-Explorer； 2024 LLM加速器框架；多个语料库行 | <a id="ICCAD-001-C011"></a>[ICCAD-001-C011](#ICCAD-001-C011) |
| Jason Cong / UCLA-相邻行 | DNN 加速器表示、存储内计算、HLS 传输/DSE、LLM 加速器库 | Caffeine； EISC；高效的任务转移； FlexLLM | <a id="ICCAD-001-C012"></a>[ICCAD-001-C012](#ICCAD-001-C012) |
| David Atienza / 3D 热建模线 | 3D IC 紧凑型热建模 | 3D-ICE 回顾奖 | needs_review 直至cross-venue团队审核 |
| Kaushik Roy / Anand Raghunathan 近似计算线 | 近似计算模型和电路 | MACACO 回顾奖 | needs_review 直至cross-venue团队审核 |
| Farid Najm / Valeriy Sukharev 可靠性线 | EM，电网可靠性，PDN 修复/检查 | 基于物理的快速 EM；电网固定；随机有效电流 | <a id="ICCAD-001-C013"></a>[ICCAD-001-C013](#ICCAD-001-C013) |
| Andrew B. Kahng / 物理设计优化线 | 分区、布局、布局和物理设计优化 | SpecPart 和重复语料库行 | <a id="ICCAD-001-C014"></a>[ICCAD-001-C014](#ICCAD-001-C014) |
| Giovanni De Micheli / EPFL 逻辑综合线 | 逻辑综合，安全/乱码电路，新兴计算 | 追求质量和速度；相关语料库行 | <a id="ICCAD-001-C015"></a>[ICCAD-001-C015](#ICCAD-001-C015) |
| Deming Chen / FPGA-HLS-DNN line | FPGA DNN 加速器生成和 HLS-adjacent 方法 | DNNBuilder 和相关语料库行 | <a id="ICCAD-001-C016"></a>[ICCAD-001-C016](#ICCAD-001-C016) |
| 佐治亚理工学院SHARC / 丛浩行 | FPGA 架构探索、INR 加速器、边缘 AI 加速器设计 | LaZagna； INR-拱门；边缘-MoE | <a id="ICCAD-001-C017"></a>[ICCAD-001-C017](#ICCAD-001-C017) |

## 9. 对博士入门者的阅读路线

必读 10 篇：Caffeine、DNNBuilder、COMBA、EISC in-storage computing、BOOM-Explorer、3D-ICE、HyperFuzzing、SpecPart、OpenTimer、LaZagna。

扩展 20 篇：Malicious LUT、Fast physics-based electromigration checking、SALT、PolyCleaner、Power Grid Fixing、Electromigration Checking Using a Stochastic Effective Current Model、MACACO、Attack Directories、Striving for Both Quality and Speed、NVCiM DNN Accelerator、An Agile Framework for Efficient LLM Accelerator Development and Model Inference、Semidefinite Programming-Based Decoupling Capacitor Placement、LLM-on-the-Palm、TP-DCIM，以及 `papers.csv` 中 ICCAD-C02/C03/C05 的近年代表行。

适合跟踪的近年方向：AI/LLM for EDA、LLM/Transformer accelerator design automation、PIM/CIM 和 memory-centric inference、FPGA architecture exploration、security validation、physical-design closure 的 ML/optimization 方法。

## 10. 与我的方向的连接点

你的 3DGS/神经渲染/FPGA 加速方向在 ICCAD 里有一条 venue-local 直接证据线，但还不是全局稳定 topic。第二轮 deep read 已确认 7 个直接锚点：RT-NeRF (2022)、INR-Arch 和 Rapid-INR (2023)、Residual-INR (2024)、SLTarch、GauPRE、No Redundancy, No Stall (2025)。这条线的技术对象从 NeRF on-device rendering，转向 INR dataflow/compiler 和 INR compression，再到 2025 的 point-based rendering 与 3DGS streaming/rasterization bottleneck。对应 claim <a id="ICCAD-001-C100"></a>[ICCAD-001-C100](#ICCAD-001-C100)、<a id="ICCAD-001-C114"></a>[ICCAD-001-C114](#ICCAD-001-C114) 和 <a id="ICCAD-001-C115"></a>[ICCAD-001-C115](#ICCAD-001-C115)。

更稳的阅读路径是三条。第一，HLS/FPGA architecture exploration 解释算法如何走向可实现硬件，代表行包括 COMBA、DNNBuilder、BOOM-Explorer、RapidStream IR、TransLib 和 LaZagna。第二，PIM/CIM 与 memory-centric inference 给出新负载进入存储侧/近存侧计算的方法迁移，代表行包括 EISC、ReTransformer、TP-DCIM、LP-Spec、SAGE、HD-MoE、LLM-on-the-Palm 和 LEAP。第三，physical design / reliability closure 说明 accelerator 方案最终仍要面对 timing、routing、PDN、EM/IR、DTCO 和 decap 约束。

## 11. 缺失来源

- 2016-2025 每年 official final program / accepted list 与 DBLP/proceedings 的结构化 crosswalk。
- ACM DL / IEEE Xplore abstract、keywords、PDF-level metadata 和 artifact badges 的批量导出。
- 2026 accepted papers、final proceedings、award outcome 和 artifact outcome。
- 对 53 个 evidence anchors 的 citation-structure audit、follow-on paper sampling、artifact fork/reuse audit 和 benchmark standardization audit。
- Artifact/code runnable status：DNNBuilder/AccDNN、BOOM-Explorer、EISC、HD-MoE、LaZagna、VerilogEval、HLSPilot、Golden Gate/MIDAS、Accelergy 和 LLM4HWDesign Toolkit 都只是 `runnable_unchecked`。
- 官方 artifact/dataset URL：OpenLLM-RTL、EDALearn、LLM4Verilog、SLTarch、GauPRE 和 No Redundancy, No Stall 仍需后续确认。
- 跨 DAC/DATE/ASP-DAC/TCAD、FPGA/FCCM/FPL/FPT 和 architecture venues 的同题对照矩阵。
- 作者、机构和团队线索的entity disambiguation。
