# ISCA 小领域深读

## 1. 范围与语料

本轮只处理 ISCA。输入 corpus 覆盖 2016-2026：`papers.csv` 有 957 行，`awards.csv` 回写后有 24 行。2026 年仍按官方 program 的 pre-proceedings 信号处理，共 172 条，保持 `partial`。本轮生成 screening matrix 981 行，其中 40 个 current-corpus paper 进入 evidence matrix；6 条 DBLP proceedings/front-matter 行标为 `exclude_non_main`。

来源口径：2016-2025 主体仍以 DBLP/DOI/ACM/IEEE metadata 为准；2022-2025 Best Paper、2024 artifact、2025 honorable mention 和 2023 新补 artifact award 使用 SIGARCH 或 ISCA 官方页面；citation 只作为 OpenAlex 检索日为 2026-06-27 的影响力线索。

## 2. 小领域图谱

| subfield_id | 子领域 | evidence rows | 代表性 ids |
|---|---|---:|---|
| <a id="ISCA-SF01"></a>[ISCA-SF01](#ISCA-SF01) | 稀疏和空间 DNN 加速器数据流 | 4 个evidence rows | [ISCA-2016-P0003](../../10_corpus/ISCA/id_index.md#ISCA-2016-P0003)、[ISCA-2016-P0005](../../10_corpus/ISCA/id_index.md#ISCA-2016-P0005)、[ISCA-2016-P0015](../../10_corpus/ISCA/id_index.md#ISCA-2016-P0015)、[ISCA-2017-P0030](../../10_corpus/ISCA/id_index.md#ISCA-2017-P0030) |
| <a id="ISCA-SF02"></a>[ISCA-SF02](#ISCA-SF02) | 生产张量加速器和数据中心ML 系统 | 4 个evidence rows | [ISCA-2017-P0018](../../10_corpus/ISCA/id_index.md#ISCA-2017-P0018)、[ISCA-2020-P0005](../../10_corpus/ISCA/id_index.md#ISCA-2020-P0005)、[ISCA-2021-P0029](../../10_corpus/ISCA/id_index.md#ISCA-2021-P0029)、[ISCA-2023-P0032](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0032) |
| <a id="ISCA-SF03"></a>[ISCA-SF03](#ISCA-SF03) | 架构编译器、模拟器和 artifact 支持的评估 | 7 个evidence rows | [ISCA-2017-P0034](../../10_corpus/ISCA/id_index.md#ISCA-2017-P0034)、[ISCA-2018-P0023](../../10_corpus/ISCA/id_index.md#ISCA-2018-P0023)、 [ISCA-2020-P0045](../../10_corpus/ISCA/id_index.md#ISCA-2020-P0045)、[ISCA-2024-P0059](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0059)、[ISCA-2026-P0002](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0002)、[ISCA-2024-P0078](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0078)... |
| <a id="ISCA-SF04"></a>[ISCA-SF04](#ISCA-SF04) | NeRF、3DGS 和神经渲染加速 | 10 个evidence rows | [ISCA-2023-P0038](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0038)、[ISCA-2023-P0054](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0054)、[ISCA-2025-P0010](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0010)、 [ISCA-2025-P0011](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0011)、[ISCA-2025-P0086](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0086)、[ISCA-2026-P0108](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0108)... |
| <a id="ISCA-SF05"></a>[ISCA-SF05](#ISCA-SF05) | LLM 和基础模型内存、量化、PIM 和 FPGA 执行 | 6 个evidence rows | [ISCA-2025-P0073](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0073)、[ISCA-2025-P0093](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0093)、 [ISCA-2026-P0001](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0001)、[ISCA-2026-P0003](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0003)、[ISCA-2026-P0161](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0161)、[ISCA-2025-P0069](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0069) |
| <a id="ISCA-SF06"></a>[ISCA-SF06](#ISCA-SF06) | 内存可靠性、缓存压缩和间歇性进度 | 5 个evidence rows | [ISCA-2022-P0010](../../10_corpus/ISCA/id_index.md#ISCA-2022-P0010)、[ISCA-2023-P0046](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0046)、[ISCA-2023-P0084](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0084)、[ISCA-2025-P0002](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0002)、[ISCA-2025-P0031](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0031) |
| <a id="ISCA-SF07"></a>[ISCA-SF07](#ISCA-SF07) | 架构正确性、语义和专业系统 | 4 个evidence rows | [ISCA-2023-P0069](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0069)、[ISCA-2024-P0006](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0006)、[ISCA-2024-P0032](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0032)、[ISCA-2025-P0098](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0098) |

## 3. 小领域深读

### [ISCA-SF01](#ISCA-SF01)。稀疏和空间 DNN 加速器数据流

- 研究问题： DNN/CNN 的核心瓶颈不是单个算子标签，而是稀疏性、数据复用、片上存储和 PE 利用率如何共同决定能效。
- 背景： 2016-2017 的 Cnvlutin、Eyeriss、EIE、SCNN 构成早期硬件加速锚点，分别强调跳过无效神经元、row-stationary dataflow、压缩权重/激活和 compressed-sparse dataflow。
- 本 venue 的当前状态： 这条线在 ISCA 中已转为方法模板，后续 neural rendering 和 LLM accelerator 论文反复借用“负载剖析 -> 数据流 -> 存储/精度 -> 评价”的叙事方式。
- 代表论文：[ISCA-2016-P0003](../../10_corpus/ISCA/id_index.md#ISCA-2016-P0003)、[ISCA-2016-P0005](../../10_corpus/ISCA/id_index.md#ISCA-2016-P0005)、[ISCA-2016-P0015](../../10_corpus/ISCA/id_index.md#ISCA-2016-P0015)、[ISCA-2017-P0030](../../10_corpus/ISCA/id_index.md#ISCA-2017-P0030)。
- 团队线索： MIT/Sze/Emer、Stanford/Dally/Horowitz、Toronto/UBC 等作者集群只作为线索，不做排名。
- workload/artifact 信号： Eyeriss 有项目页；多数早期 artifact/code 状态未复核。
- 开放问题： 需要 citation-structure audit 区分“高引用背景论文”和“真正被作为 baseline 或方法模板复用”的论文。

### [ISCA-SF02](#ISCA-SF02)。生产张量加速器和数据中心 ML 系统

- 研究问题： 生产级 ML accelerator 的约束来自部署环境：服务延迟、编译栈、互连、embedding 支持、多租户、功耗和 TCO。
- 背景： TPU v1 论文把真实 datacenter inference 评价带入 ISCA；TPUv4i lessons 和 TPU v4 继续补上产品迭代、部署经验和 supercomputer 级互连。
- 本 venue 的当前状态： 这条线是 ISCA 中影响力最稳的加速器证据链之一，citation 与连续论文都较强，但公开 artifact 通常不可用。
- 代表论文：[ISCA-2017-P0018](../../10_corpus/ISCA/id_index.md#ISCA-2017-P0018)、[ISCA-2020-P0005](../../10_corpus/ISCA/id_index.md#ISCA-2020-P0005)、[ISCA-2021-P0029](../../10_corpus/ISCA/id_index.md#ISCA-2021-P0029)、[ISCA-2023-P0032](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0032)。
- 团队线索： Google TPU 团队线索明确；TSP/Groq-like company author cluster 需要实体复核。
- workload/artifact 信号： 以 production disclosure 和论文指标为主，不写 runnable。
- 开放问题： 需要跨 MLSys/SC/ASPLOS 对照，把产品论文和学术 simulator 论文分开比较。

### [ISCA-SF03](#ISCA-SF03)。架构编译器、模拟器和 artifact 支持的评估

- 研究问题： 加速器主张如何变成可复核的模拟、DSE、编译和 artifact，而不是只给单点 speedup。
- 背景： Plasticine、FireSim、Accel-Sim、AIO、FireAxe、DAM、CODO 和 RoSE 覆盖 spatial architecture、cloud-FPGA simulation、GPU simulator、性能抽象、RTL partitioning、dataflow simulation 和 HLS dataflow compiler。
- 本 venue 的当前状态： FireSim、Accel-Sim 和 CODO 有公开 repo；FireAxe、DAM、RoSE 等需要进一步确认 artifact package 或 upstream 状态。
- 代表论文：[ISCA-2017-P0034](../../10_corpus/ISCA/id_index.md#ISCA-2017-P0034)、[ISCA-2018-P0023](../../10_corpus/ISCA/id_index.md#ISCA-2018-P0023)、[ISCA-2020-P0045](../../10_corpus/ISCA/id_index.md#ISCA-2020-P0045)、[ISCA-2023-P0058](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0058)、[ISCA-2024-P0059](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0059)、[ISCA-2024-P0078](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0078)、[ISCA-2024-P0083](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0083)、[ISCA-2026-P0002](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0002)。
- 团队线索： Stanford/Olukotun、UC Berkeley FireSim、UBC/Purdue Accel-Sim、SJTU Zhao lab 等是团队线索，不做排名。
- workload/artifact 信号： FireSim、Accel-Sim、CODO 记为 `code_available; runnable_unchecked`；未本地运行。
- 开放问题： 需要后续 workload/artifact inventory 统一记录 artifact package、依赖、版本和可运行状态。

### [ISCA-SF04](#ISCA-SF04)。 NeRF、3DGS 和神经渲染加速

- 研究问题： NeRF、neural graphics、3DGS 和机器人/视觉场景表示的瓶颈集中在 irregular scene memory、hash/encoding、排序、rasterization、实时延迟和画质/能耗权衡。
- 背景： 2023 年 NeuRex 和 Hardware Acceleration of Neural Graphics 给出 neural rendering 的早期体系结构锚点；2025 年 Cambricon-SR、Lumina、FlexNeRFer 扩展到 neural scene representation、3DGS redundancy/radiance caching 和多数据流 NeRF；2026 program 出现 NeRArch-Sim、GauTracer 和直接 3DGS 优化行。
- 本 venue 的当前状态： 这条线与用户方向最直接，但 2026 仍是 partial。能确认的是 ISCA 已有多篇跨年份论文围绕 neural rendering/scene representation 形成小领域线索，不能把 2026 title-only 行写成成熟趋势。
- 代表论文：[ISCA-2023-P0038](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0038)、[ISCA-2023-P0054](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0054)、[ISCA-2024-P0037](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0037)、[ISCA-2025-P0010](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0010)、[ISCA-2025-P0011](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0011)、[ISCA-2025-P0086](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0086)、[ISCA-2026-P0108](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0108)、[ISCA-2026-P0126](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0126)、[ISCA-2026-P0128](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0128)。
- 团队线索： SNU/Jaewoong Sim、UIUC/Rakesh Kumar、CAS/Cambricon、SJTU/Yuhao Zhu、Fudan/Haozhe Zhu 等只作为线索。
- workload/artifact 信号： Lumina 有项目页；NeRArch-Sim、GauTracer、3DGS 2026 行需要 final PDF 和 artifact 复核。
- 开放问题： 需要和图形学/视觉会议、FPGA/FCCM/FPL、MICRO/HPCA 对照，确认 3DGS 硬件加速是否已形成跨 venue topic。

### [ISCA-SF05](#ISCA-SF05)。 LLM 和基础模型内存、量化、PIM 和 FPGA 执行

- 研究问题： LLM/RAG/foundation workloads 的主瓶颈来自 KV/state、attention/MoE 数据移动、低 batch、量化 outlier、PIM/CPU 协同和 FPGA mixed precision 原语。
- 背景： 2025 的 HeterRAG、MicroScopiQ、H2-LLM 已经把 RAG/PIM、outlier-aware microscaling 和 hybrid-bonding low-batch inference 带入 ISCA；2026 program 继续出现 MLX、COSM、XtraMAC 等 spatial/PIM/FPGA 行。
- 本 venue 的当前状态： 这条线是 2025-2026 的前沿信号。H2-LLM 和 XtraMAC 有公开 repo；2026 其他行仍缺 final DOI/PDF。
- 代表论文：[ISCA-2025-P0069](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0069)、[ISCA-2025-P0073](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0073)、[ISCA-2025-P0093](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0093)、[ISCA-2026-P0001](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0001)、[ISCA-2026-P0003](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0003)、[ISCA-2026-P0161](../../10_corpus/ISCA/id_index.md#ISCA-2026-P0161)。
- 团队线索： PKU/SJTU/Alibaba/HKUST/Southeast、HUST/Hai Jin、Georgia Tech/Tushar Krishna、NUS/Xtra-Computing 等均需entity disambiguation。
- workload/artifact 信号： H2-LLM、XtraMAC repo 已记录为 `code_available; runnable_unchecked`。
- 开放问题： 需要把 RAG、MoE、KV compression、mixed precision 和 FPGA MAC primitives 拆开做跨 venue 对照，不能都写成一个泛泛的 LLM topic。

### [ISCA-SF06](#ISCA-SF06)。内存可靠性、缓存压缩和间歇性进展

- 研究问题： memory-system 类论文的共同问题是数据移动、地址转换、物理连续性、可靠性和 intermittent 能量约束如何影响性能与正确性。
- 背景： NvMR、RowPress、Contiguitas、XOR Cache、Rethinking Prefetching 分别覆盖 intermittent NVM、DRAM read-disturbance、datacenter physical contiguity、cache compression 和 intermittent prefetching。
- 本 venue 的当前状态： 这是 ISCA 最持续的来源线之一，但内部问题分化很大，不能合成一个稳定 global topic。
- 代表论文：[ISCA-2022-P0010](../../10_corpus/ISCA/id_index.md#ISCA-2022-P0010)、[ISCA-2023-P0046](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0046)、[ISCA-2023-P0084](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0084)、[ISCA-2025-P0002](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0002)、[ISCA-2025-P0031](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0031)。
- 团队线索： CMU/Meta、ETH/CMU-SAFARI/Onur Mutlu、Wisconsin/Joshua San Miguel 等只作为线索。
- workload/artifact 信号： RowPress repo 已记录；Contiguitas 有 production evaluation 信号但 Linux upstream 未核验。
- 开放问题： 后续需要把 security/reliability、datacenter memory、intermittent computing 和 cache compression 拆开。

### [ISCA-SF07](#ISCA-SF07)。架构正确性、语义和专业系统

- 研究问题： 架构优化不能只看速度，还必须处理 load elimination 安全、relaxed exception 语义、quantum compilation、BCI 等专用系统的正确性和边界条件。
- 背景： Constable 和 Precise exceptions 从 CPU/memory semantics 方向进入，Tetris 代表 quantum VQA compilation artifact，SCALO 代表 accelerator-rich BCI system。
- 本 venue 的当前状态： 这组更像边界集合，提醒后续 synthesis 不要把所有 award paper 都归入“加速器性能”主线。
- 代表论文：[ISCA-2023-P0069](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0069)、[ISCA-2024-P0006](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0006)、[ISCA-2024-P0032](../../10_corpus/ISCA/id_index.md#ISCA-2024-P0032)、[ISCA-2025-P0098](../../10_corpus/ISCA/id_index.md#ISCA-2025-P0098)。
- 团队线索： Yale BCI/system、Intel/Mutlu-linked、Rutgers/UW-Madison/NC State、Cambridge/Edinburgh/Aarhus formal semantics 等均需复核。
- workload/artifact 信号： Tetris 有官方 artifact award；Precise exceptions 只记录 PDF 和相关 herdtools7 生态线索，不写标准采纳。
- 开放问题： 需要区分 formal semantics、security/reliability 和 domain-specific accelerator。

## 4. 发展趋势

- Sparse/CNN dataflow 的早期锚点集中在 2016-2017，支撑论文为 Cnvlutin、Eyeriss、EIE 和 SCNN。这个趋势有多篇论文支撑，但本轮只写为 ISCA 内部历史线索。
- Production ML accelerator 从 2017 TPU 到 2021 TPUv4i lessons 再到 2023 TPU v4，构成跨年份生产系统线索。它和普通 simulator paper 的证据类型不同。
- Artifact-backed evaluation 从 FireSim、Accel-Sim 发展到 FireAxe、DAM、RoSE 和 CODO，逐步覆盖 cloud-FPGA、GPU simulation、RTL partitioning、dataflow simulation、robotics SoC co-simulation 和 HLS dataflow compiler。
- Neural rendering/3DGS 在 2023-2026 出现连续信号：NeuRex、Hardware Acceleration of Neural Graphics、Lumina、FlexNeRFer、NeRArch-Sim、GauTracer 和 3DGS official program row。2026 仍 partial，趋势只写成“活跃前沿信号”。
- LLM/GenAI 在 2025-2026 分成低 batch/hybrid bonding、RAG/PIM、outlier quantization、spatial execution、PIM/CPU scheduling 和 FPGA MAC primitive，多篇证据支持“正在分化”，但 final proceedings 不完整。

## 5. 方法变化

- 评价方法从早期 cycle-level/simulator + CNN benchmark，扩展到 production trace、cloud FPGA artifact、validated GPU simulator、artifact award 和 OpenAlex citation/adoption 初审。
- 加速机制从固定 CNN dataflow、compressed sparse execution，转向 workload-specific memory state、hybrid bonding、PIM scheduling、FPGA mixed precision、scene rendering pipeline 和 full-stack co-simulation。
- artifact 信号更重要，但本轮没有搭环境，不写“已复现”。公开 repo 只记为 `code_available` 或 `runnable_unchecked`。

## 6. 缺失来源

- 2026 final proceedings、ACM/IEEE DOI、artifact outcome 和 award outcome。
- ACM DL/IEEE Xplore 批量 abstract、keywords、PDF 和 artifact badge metadata。
- RoSE、Tetris、DACAPO、DAM、FireAxe 等 artifact package 的精确 URL 与 runnable 状态。
- Contiguitas Linux upstream、FireAxe upstream 到 FireSim、Precise exceptions 进入工具或规范的后续采纳证据。
- MICRO/HPCA/ASPLOS/FPGA/FCCM/FPL/graphics venues 的对照矩阵。
