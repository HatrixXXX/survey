# DATE 论文图谱分析

## 1. 会议定位

DATE 是 Design, Automation and Test in Europe Conference。2026 官方页给出的会期是 2026 年 4 月 20-22 日，地点是意大利 Verona <a id="DATE-001-C001"></a>[DATE-001-C001](#DATE-001-C001)。对本项目来说，DATE 是一个交叉入口：EDA、test、embedded systems、SoC、FPGA/HLS、AI accelerator、PIM/CIM、CPS/robotics 和安全可靠性会在同一技术程序里相遇 <a id="DATE-001-C030"></a>[DATE-001-C030](#DATE-001-C030)。

和 DAC/ICCAD 相比，DATE 的欧洲嵌入式系统、CPS 和 automotive 比重更明显。和 FPGA/FCCM/FPL 相比，它不会只围绕可重构计算，而是把 HLS、系统建模、低功耗、测试可靠性和应用系统放在一起看。这个特性让 DATE 适合追踪“软硬件协同设计如何进入真实应用约束”，但不适合单独判断某个 accelerator 子领域的完整影响力。

## 2. 数据来源与覆盖范围

- 年份范围：2016-2026。`papers.csv` 有 4057 行。第二轮 后的 paper_type 计数是 accepted_paper=3439、invited_talk=478、other=140 <a id="DATE-001-C002"></a>[DATE-001-C002](#DATE-001-C002)。
- 年度行数：2016: 308, 2017: 336, 2018: 309, 2019: 331, 2020: 344, 2021: 348, 2022: 276, 2023: 385, 2024: 422, 2025: 507, 2026: 491。
- 2016-2022 使用官方 DATE proceedings archive 的 technical-program TOC 和 best-paper 页面 <a id="DATE-001-C004"></a>[DATE-001-C004](#DATE-001-C004)。
- 2023 使用官方 detailed programme。缓存 HTML 给出标题、作者和摘要，但没有稳定暴露每篇论文 PDF 链接，所以 2023 的批量 `pdf_url` 仍留空 <a id="DATE-001-C005"></a>[DATE-001-C005](#DATE-001-C005)。
- 2024-2026 使用官方 detailed programme。2026 的 programme 和 awards 可见，但 DOI/DBLP/publisher URL 没有批量复核，所以 2026 仍是 `partial`；这部分正常缺口标为 normal_2026_partial <a id="DATE-001-C003"></a>[DATE-001-C003](#DATE-001-C003)。
- `awards.csv` 记录 45 条 DATE Best Paper Award winner。第二轮 已把 45 条都对齐到官方 awards/best-paper 页面和 corpus paper_id <a id="DATE-001-C006"></a>[DATE-001-C006](#DATE-001-C006)。
- 本轮只补了可靠的 DOI、DBLP、code URL 和 arXiv URL。没有来源的字段继续保留 missing/needs_review，不用标题猜 DOI 或 artifact 状态 <a id="DATE-001-C026"></a>[DATE-001-C026](#DATE-001-C026)。

## 3. 主题分类

| 小领域 | 核心问题 | 代表论文 | 活跃年份 | 证据状态 |
| --- | --- | --- | --- | --- |
| 边缘神经渲染和3DGS加速 | 边缘实时渲染下的显存、带宽、FPS 和质量约束 | FAMERS； PS-GS； SpNeRF； FLICKER | 2025-2026 | DATE-本地集群；仍然需要cross-venue <a id="DATE-001-C027"></a>[DATE-001-C027](#DATE-001-C027) |
| 点云和 3D 感知加速 | 点云/深度感知的不规则访问和算子融合 | 深度立体激光雷达融合； PRADA; FusionArch | 2021-2024 | 多论文 DATE 证据 |
| 边缘/移动 DNN 和传感器内推理 | 模型部署到移动、传感器和实时边缘平台 | MoDNN；跌倒检测CNN； INSPIRE;机器人扩散加速器 | 2017-2026 | 选定的影响证据部分 |
| LLM 序列模型部署和量化 | 长上下文、MoE、Mamba、softmax、fault assessment 的内存/精度/可靠性瓶颈 | Cocktail; DAOP； DOTS；FineQ；LightMamba； RIFT | 2021, 2025-2026 | 多纸趋势；采用大多未 verified <a id="DATE-001-C033"></a>[DATE-001-C033](#DATE-001-C033) |
| PIM/CIM/NVM 内存端 AI 计算 | 减少 AI compute 与 memory hierarchy 间的数据搬移 | GenPIM； TDO-CIM； FSDB; STT-MRAM/ReRAM 行 | 2018-2026 | 多年venue evidence |
| HDC 和类脑边缘计算 | 低能耗、鲁棒、隐私友好的边缘学习 | HDC 边缘协同设计；DropDim；CafeHD； EcoFlex-HDP | 2022-2024 | 多论文venue evidence |
| 物理设计封装和小芯片热建模 | routing、placement、extraction、thermal closure 的 PPA 约束 | 电容提取；快速GR； SAGE路线；高效-TDP； 3D-ICE 4.0 | 2016-2026 | 多年venue evidence |
| HLS、EDA-AI、形式验证和 DSE | 降低 HLS/verification/EDA iteration 成本，同时保留 QoR 和 correctness 证据 | Sensei；利用处理器建模；锚定和适应；工作台4HLS；覆盖断言 | 2018-2026 | 基准测试/候选工具，临时 <a id="DATE-001-C016"></a>[DATE-001-C016](#DATE-001-C016) |
| 可靠的硬件、安全性和故障感知执行 | fault、side-channel、soft error、robustness 和 embedded intrusion detection | MATIC；定时通道； DEFCON; SELCC； RIFT | 2016-2026 | 多年venue evidence |

## 4. 筛选和证据

第二轮 写入了全量 screening matrix：paper rows=4057，award rows=45，总计 4102 行。筛选决定只使用 deep_read、index_only、exclude_non_main、needs_review <a id="DATE-001-C031"></a>[DATE-001-C031](#DATE-001-C031)。

Screening 计数：deep_read=120，index_only=2951，exclude_non_main=618，needs_review=413。

Evidence matrix 包含 75 篇 deep_read 论文，每行都有 WHY、HOW、WHAT、IMPACT 和 EVIDENCE 字段 <a id="DATE-001-C032"></a>[DATE-001-C032](#DATE-001-C032)。impact 字段没有证据时写 `impact_unverified`；citation、artifact、benchmark 信号写入检索日期。

## 5. Award Papers 分析

第二轮 复核后，45 条 Best Paper Award row 都有 canonical official source。若旧 `awards.csv` 的标题、作者或 paper_id 与官方 award/proceedings 对不上，已按官方来源和匹配 paper row 修正。奖项只能证明 DATE 认可这篇工作，不能证明长期采用或引用影响。

| 年份 | 论文 | 为什么重要 | impact 状态 | 证据状态 |
| --- | --- | --- | --- | --- |
| 2017 | MoDNN | 早期 mobile/distributed DNN system award node | OpenAlex 306 / Semantic Scholar 295, 2026-06-27；adoption not_audited | 已验证 <a id="DATE-001-C035"></a>[DATE-001-C035](#DATE-001-C035) |
| 2018 | MATIC | 低电压 neural accelerator 可靠性/近似计算 award node | OpenAlex 67, 2026-06-27；adoption not_audited | 已验证 <a id="DATE-001-C036"></a>[DATE-001-C036](#DATE-001-C036) |
| 2024 | FusionArch | 点云神经网络 accelerator award node | impact_unverified | 已验证 <a id="DATE-001-C024"></a>[DATE-001-C024](#DATE-001-C024) |
| 2025 | Cocktail | 长上下文 LLM KV-cache mixed precision award node | Crossref 3, 2026-06-27；code URL 有冲突 | 已验证 <a id="DATE-001-C038"></a>[DATE-001-C038](#DATE-001-C038) |
| 2026 | FSDB | 混合计算-in-ROM/SRAM DNN 片上奖励节点 | impact_unverified | 已验证 [DATE-001-C006](#DATE-001-C006) |
| 2026 | RIFT | LLM 加速器故障评估奖励节点 | Crossref 0, 2026-06-27；太新的 | 已验证 <a id="DATE-001-C040"></a>[DATE-001-C040](#DATE-001-C040) |

## 6. 代表性论文清单

- MoDNN (2017): 关注 mobile devices 上的本地 DNN 计算和分布式执行。citation 信号强，但本轮没有追引用结构或系统复用 [DATE-001-C035](#DATE-001-C035)。
- MATIC (2018): 关注低电压 neural accelerator 中的错误容忍和准确率保持。citation 信号可见，但不能直接写成产业采用 [DATE-001-C036](#DATE-001-C036)。
- GenPIM / TDO-CIM / FSDB: 组成 DATE 中 memory-side AI compute 的多年份线索，覆盖 generalized PIM、transparent offload 和 hybrid ROM/SRAM compute。
- HDC edge co-design / DropDim / CafeHD / EcoFlex-HDP: 组成 HDC 和 brain-inspired edge computing 线索，重点是能耗、鲁棒性和 memory-centric platformization。
- FastGR / SAGERoute / Efficient-TDP / 3D-ICE 4.0: 组成 physical-design closure 线索，覆盖 global routing、analog routing、critical path extraction 和 2.5D/3D thermal modeling。
- FusionArch / PRADA: 是 point-cloud neural network acceleration 的 DATE-local 主线。
- FAMERS / PS-GS / SpNeRF / FLICKER: 是 2025-2026 3DGS/neural rendering hardware 的 DATE-local cluster [DATE-001-C027](#DATE-001-C027)。
- Cocktail / DAOP / FineQ / DOTS / LightMamba / RIFT: 是 2025-2026 LLM/sequence-model deployment 的主要入口 [DATE-001-C033](#DATE-001-C033)。
- Bench4HLS / Anchor-and-Adapt / CoverAssert / Chip-Map: 是 2026 LLM-for-HLS、LLM-for-EDA 和 coverage-guided verification 的入口；Bench4HLS 只写 benchmark candidate，不写成 standardized benchmark <a id="DATE-001-C034"></a>[DATE-001-C034](#DATE-001-C034)。

## 7. 发展脉络

- 2016-2018：DATE 的硬件加速相关内容贴着低功耗、嵌入式系统、HLS、NVM/存储和早期 DNN accelerator 走。MoDNN、MATIC、Sensei 和若干 CPS/NoC/可靠性论文说明当时关注点是把模型或系统放进受限平台。
- 2019-2021：安全、可靠性和边缘 AI 变重。硬件安全、timing channel、statistical fault injection、Transformer IMC、ROS/robotics verification 把“加速器能不能可信部署”拉进同一张图 <a id="DATE-001-C011"></a>[DATE-001-C011](#DATE-001-C011)。
- 2022-2024：PIM/CIM、HDC、routing/physical design 和 point-cloud neural network acceleration 更醒目。FusionArch 是这段时间和 3D perception 关系最直接的 award node <a id="DATE-001-C012"></a>[DATE-001-C012](#DATE-001-C012)。
- 2025-2026：DATE 出现多个 LLM/Mamba/MoE、3DGS/neural rendering、robotic diffusion、LLM-for-EDA 和 chiplet/thermal 信号 <a id="DATE-001-C013"></a>[DATE-001-C013](#DATE-001-C013)。这些是 early-warning feed，不替代 ASPLOS/ISCA/HPCA/MICRO/FPGA/FPL 或图形学会议的影响力判断。

## 8. 团队线索

本节只写 team_signal，不做排名。

| 团队/机构线索 | 关联方向 | 代表线索 | 复核状态 | claim |
|---|---|---|---|---|
| ETH Zurich / University of Bologna / PULP-adjacent author strings | 低功耗嵌入式、edge AI、MCU Transformer inference | 多次出现在相关 rows | 仍需 author disambiguation | <a id="DATE-001-C021"></a>[DATE-001-C021](#DATE-001-C021) |
| UCSD / UCI / HDC / memory-centric ML author strings | HDC、memory-centric ML | Mohsen Imani、Tajana Rosing、Yeseong Kim 等相关 rows | 团队线索，不是实力排名 | <a id="DATE-001-C022"></a>[DATE-001-C022](#DATE-001-C022) |
| CUHK / Peking / Bei Yu / Yibo Lin related author strings | routing、physical design、SAGERoute、LLM-for-EDA、macro placement | 多条可追踪结果 | 仍需 affiliation/name 清洗 | <a id="DATE-001-C023"></a>[DATE-001-C023](#DATE-001-C023) |
| Shanghai Jiao Tong / Sanechips style point-cloud accelerator line | point-cloud acceleration | FusionArch、PRADA | 只作为 team_signal | [DATE-001-C024](#DATE-001-C024) |
| Bremen / JKU / TUM formal-verification and quantum design automation line | formal verification、quantum design automation | DATE 中长期 presence | 团队级结论继续 `needs_review` | <a id="DATE-001-C025"></a>[DATE-001-C025](#DATE-001-C025) |

## 9. 对博士入门者的阅读路线

先按问题链路读，而不是按年份读：MoDNN、MATIC、HDC edge co-design、FastGR、SAGERoute、FusionArch、Cocktail、Bench4HLS、FSDB、RIFT，再补 FAMERS/PS-GS/SpNeRF/Flicker。读每篇时先问瓶颈是什么，再看它把瓶颈归给模型、存储、互连、编译器、EDA tool 还是可靠性。

对 3DGS/neural rendering/FPGA/accelerator/软硬协同方向，优先从 screening matrix 的 `deep_read` 行开始，再按 `topic_hint` 过滤 `3DGS`、`neural rendering`、`point cloud`、`robotic diffusion`、`FPGA`、`HLS`、`LLM inference`、`PIM/CIM`。

## 10. 与用户方向的连接点

- 3DGS / Neural Rendering：DATE 2025-2026 有 FAMERS、PS-GS、SpNeRF、FLICKER 和 2026 neural rendering accelerator。它们适合补硬件实现和设计方法视角，但不替代图形学主会的算法谱系 [DATE-001-C027](#DATE-001-C027)。
- FPGA / accelerator / soft-hardware co-design：DATE 强项是把 accelerator 放进 HLS、runtime、verification、memory hierarchy、low-power 和 test 中一起讨论。LightMamba、Bench4HLS、Sensei、Anchor-and-Adapt 适合作为工具链线索 [DATE-001-C016](#DATE-001-C016)[DATE-001-C034](#DATE-001-C034)。
- 机器人 / 具身智能边缘计算：DATE 从 automotive/CPS/ROS verification 延伸到 3D perception 和 robotic diffusion policy accelerator。2026 robotic diffusion policy accelerator 是需要继续追的近年信号 <a id="DATE-001-C018"></a>[DATE-001-C018](#DATE-001-C018)。
- LLM inference：Cocktail、DAOP、FineQ、DOTS、LightMamba、SegTransformer 和 RIFT 说明 DATE 已覆盖低 batch、长上下文、PIM/FPGA/MCU 和可靠性问题 [DATE-001-C033](#DATE-001-C033)。
- AI-for-EDA：Chip-Map、Bench4HLS、CoverAssert、MAEDA/VeriRepair 等行适合和 DAC/ICCAD 的 AI-for-EDA 报告合并看 [DATE-001-C023](#DATE-001-C023)。

## 11. 缺失来源

- Taxonomy 仍是 venue_provisional。趋势判断已经要求多篇或跨年份证据，但稳定 subfield 要等跨会议 synthesis。
- 2026 仍是 `partial`：official programme/awards 已用，DOI/DBLP/publisher URL 未批量复核。纯 2026 metadata partial 是 normal_2026_partial [DATE-001-C003](#DATE-001-C003)。
- 2023 per-paper PDF gap 仍在。没有按 URL pattern 猜 PDF [DATE-001-C005](#DATE-001-C005)。
- author/team disambiguation 仍未做。所有团队内容只作为 team_signal，不做排名。
- artifact/code 只记录 verified URL 或冲突状态；没有运行仓库，也没有把 repository 写成 adoption proof。
- citation/adoption 只是初审。写了检索日期的 citation count 不等于长期采用；后续需要检查 citing-paper structure、benchmark reuse、toolchain adoption 和产业采用。
- 当前 `awards.csv` 只覆盖 Best Paper Award rows。2023-2026 官方页面上的其他 award 类型没有扩展进表。
