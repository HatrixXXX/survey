# HOTCHIPS 小领域深读

检查时间：2026-06-27

## 1. 范围与语料

本小领域深读仅涵盖 `HOTCHIPS`。parent agent合并问题元数据、奖励来源、筛选和deep-read影响输出，然后集中编写最终文件。源范围仍然是 Hot Chips 官方计划/存档页面、IEEE/DOI/DBLP（如果有）、官方 TCMM 奖项 PDF、选定的供应商文档、公开仓库和基准页面。 2026 行被视为 `partial`，因为可用源是高级程序。

筛选涵盖 424 个paper rows和 16 个award rows。证据矩阵包含 117 个deep-read行：113 个paper rows和 4 个奖项来源行。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="HOTCHIPS-SF01"></a>[HOTCHIPS-SF01](#HOTCHIPS-SF01) | 数据中心 AI 加速器平台扩展 | 加速器供应商如何将张量吞吐量转变为具有互连、内存层次结构、软件堆栈和机架规模操作约束的可部署数据中心平台。 | AI 数据中心规模的训练和推理 | 集群级带宽、功耗、TCO 和内存容量 | 张量核心/脉动阵列、高带宽内存、一致主机链路、机架规模互连、训练/服务软件堆栈 | 2016-2026 | 12 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF02"></a>[HOTCHIPS-SF02](#HOTCHIPS-SF02) | LLM 内存/状态/推理经济学 | LLM 推理和推理 workload 如何改变围绕模型状态、KV 缓存、带宽和性能/TCO 的加速器设计。 | LLM 训练、预填充/解码、推理服务和边缘 LLM | KV 缓存移动、内存带宽/容量和每个令牌的成本 | HBM 容量扩展、内存分解、量化、稀疏/二进制权重、面向服务的芯片 | 2024-2026 | 16 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF03"></a>[HOTCHIPS-SF03](#HOTCHIPS-SF03) | 空间/数据流和晶圆级 AI 系统 | 空间数据流、晶圆级封装和可重新配置互连如何减少密集张量 workload 的数据移动。 | DNN 训练/推理和大型张量内核 | 不规则模型形状下的片外移动和利用 | 脉动阵列、晶圆级结构、片上 SRAM 局部性、数据流调度、编译器管理的执行 | 2016-2025 | 8 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF04"></a>[HOTCHIPS-SF04](#HOTCHIPS-SF04) | PIM、CXL 和 AI 内存墙的近内存计算 | 内存扩展、CXL 结构和近内存计算攻击能力和带宽压力如何。 | 内存绑定 AI、分析和服务器 workload | 容量扩展和主机设备移动 | CXL 内存池、内存扩展器、AXDIMM/PIM、近内存内核、一致性协议 | 2021-2026 | 9 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF05"></a>[HOTCHIPS-SF05](#HOTCHIPS-SF05) | HBM，小芯片封装和芯片到芯片集成 | HBM、芯片和芯片到芯片标准如何让加速器扩展带宽和封装复杂性。 | AI 加速器、原型设计器件和服务器芯片 | 封装带宽、产量、功率密度和链路互操作性 | HBM 堆栈、2.5D 中介层、小芯片、UCIe 链路、高级封装 | 2016-2026 | 10 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF06"></a>[HOTCHIPS-SF06](#HOTCHIPS-SF06) | 光学 I/O 和光子结构，用于 AI 放大 | 光学连接、共同封装的光学器件和光子开关如何缓解电气放大限制。 | AI 纵向扩展/横向扩展通信 | serdes 功率、范围、基数和带宽密度 | 光学连接、硅光子、共同封装光学、光路交换、光子 NoC/结构 | 2016-2026 | 15 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF07"></a>[HOTCHIPS-SF07](#HOTCHIPS-SF07) | DPU、SmartNIC 和 AI 数据中心结构卸载 | 基础设施处理器和可编程 NIC 如何卸载网络、存储、安全和集体移动。 | AI 数据中心网络、存储和控制平面 workload | 主机 CPU 开销、结构拥塞和安全隔离 | 可编程数据包引擎、RDMA/卸载、NIC 端加速、遥测/安全引擎 | 2018-2026 | 12 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF08"></a>[HOTCHIPS-SF08](#HOTCHIPS-SF08) | 边缘实时 3D 重建和感知 | 边缘 SoC 如何在移动功率限制下支持同步定位、3D 重建和感知。 | SLAM、自主导航、AR/VR 感知和机器人技术 | 边缘延迟、功耗和内存占用 | 视觉惯性处理、神经感知引擎、稀疏性、设备上映射管道 | 2016-2026 | 6 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF09"></a>[HOTCHIPS-SF09](#HOTCHIPS-SF09) | 实时神经渲染和 3DGS 管道硬件 | GPU 和空间 SoC 如何公开对神经渲染和 3D 高斯泼溅风格 workload 的硬件支持。 | 神经渲染、可交互 3D 重建和图形 AI | 实时帧延迟、内存带宽和几何/模型更新成本 | 射线/神经渲染核心、空间高斯管道、渲染/建模 SoC、graphics-AI 协同设计 | 2025 | 3 行证据； 2026 行部分存在 |
| <a id="HOTCHIPS-SF10"></a>[HOTCHIPS-SF10](#HOTCHIPS-SF10) | 开源 EDA 和可重现的 SoC 芯片 | 开源硬件工具链、验证流程和可重现的硅制品如何变得实用。 | SoC 原型设计和硬件研究基础设施 | 验证、物理设计再现性和工具链集成 | Verilator、PULP、Yosys/IceStorm、RISC-V SoC、开放 PDK 流程、可再现流片 | 2021-2026 | 7 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF11"></a>[HOTCHIPS-SF11](#HOTCHIPS-SF11) | FPGA、CGRA 和自适应数据流映射 | FPGA、CGRA 和自适应设备如何映射不规则或快速变化的加速器 workload。 | AI 推理、网络/存储卸载、芯片原型设计和信号处理 | 编译/映射时间、利用率和内存移动 | FPGA 覆盖、CGRA 图块、编译时放置、流数据流、仿真/原型结构 | 2016-2026 | 14 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF12"></a>[HOTCHIPS-SF12](#HOTCHIPS-SF12) | 基准、编译器和内核语言方法 | 基准、编译器抽象和内核语言如何使加速器比较和编程变得可信。 | AI 内核和加速器软件工作流程 | 可移植性、可比性和程序员生产力 | MLPerf、基准测试套件、编译器 IR、内核 DSL、自动调优、软件堆栈 | 2019-2025 | 4 个evidence rows； 2026 行部分存在 |
| <a id="HOTCHIPS-SF13"></a>[HOTCHIPS-SF13](#HOTCHIPS-SF13) | 安全性和信任作为架构约束 | 安全飞地和可信执行如何限制加速器和服务器芯片架构。 | 安全云/服务器执行 | 隔离与性能和可编程性 | 可信执行、飞地隔离、内存保护、旁路边界 | 2018 | 1 个evidence rows； 2026 行部分存在 |

## 3. 小领域深读

### [HOTCHIPS-SF01](#HOTCHIPS-SF01)：数据中心 AI 加速器平台扩展

- 研究问题：加速器供应商如何将张量吞吐量转变为具有互连、内存层次结构、软件堆栈和机架规模操作约束的可部署数据中心平台。
- 背景：Hot Chips 多次将 AI 加速公开为平台披露，而不是孤立的芯片结果。
- 当前状态：到 2024-2026 年，该系列将从单一 GPU/TPU claim 转向 Blackwell、Ironwood、MI350、R200 和 GB300 风格的平台叙述。
- 技术路线：张量核心/脉动阵列、高带宽内存、相干主机链路、机架级互连、训练/服务软件堆栈
- 代表作品：[HOTCHIPS-2017-P0004](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2017-P0004)、[HOTCHIPS-2020-P0025](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2020-P0025)、[HOTCHIPS-2024-P0015](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0015)、[HOTCHIPS-2025-P0018](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0018)、[HOTCHIPS-2026-P0031](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0031)
- 团队线索：NVIDIA、Google、 AMD 和超大规模加速器团队似乎是经常性的披露来源；没有推断排名。
- workload/artifact 信号：workload = AI 数据中心规模的训练和推理；瓶颈=集群级带宽、功耗、TCO 和内存容量；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2016-2026 年 12 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：ISCA/MICRO 加速器论文； MLSys/OSDI 服务系统； ISSCC 芯片披露
- 开放问题：哪些平台披露随后通过基准、部署或独立系统论文进行验证？

### [HOTCHIPS-SF02](#HOTCHIPS-SF02)：LLM 内存/状态/推理经济学

- 研究问题：LLM 推理和推理 workload 如何围绕模型状态、KV 缓存、带宽和性能/TCO 改变加速器设计。
- 背景：2024 年之后，venue从通用深度学习引擎转向明确的 GenAI 和推理模型成本叙述。
- 当前状态：Blackwell、Ironwood、WaferLLM、AXDIMM 和 2026 LLM-serving 行形成连贯但仍部分索引的行。
- 技术路线：HBM 容量扩展、内存分解、量化、稀疏/二进制权重、面向服务的芯片
- 代表作品：[HOTCHIPS-2024-P0016](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0016)、[HOTCHIPS-2025-P0028](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0028)、[HOTCHIPS-2026-P0003](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0003)、[HOTCHIPS-2026-P0032](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0032)
- 团队线索：Google、NVIDIA 和专用 LLM 处理器团队围绕服务经济反复出现；没有推断排名。
- workload/artifact 信号：workload = LLM 训练、预填充/解码、推理服务和边缘 LLM；瓶颈 = KV-缓存移动、内存带宽/容量和每个令牌的成本；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2024-2026 年 16 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：MLSys 推理服务； DAC/FPL 量化加速器工具链
- 开放问题：哪些 LLM 服务 claim 能够超越供应商 perf/TCO 框架，成为可重现的 workload 研究？

### [HOTCHIPS-SF03](#HOTCHIPS-SF03)：空间/数据流和晶圆级 AI 系统

- 研究问题：空间数据流、晶圆级封装和可重构互连如何减少密集张量 workload 的数据移动。
- 背景：DeePhi、TPU 相邻收缩线、Cerebras WSE 和 SambaNova/RDU 行显示长期运行的空间计算主题。
- 当前状态：该系列对于 AI 训练来说已经成熟，并且越来越多地构建为具有编译器/运行时协同设计的完整系统。
- 技术路线：脉动阵列、晶圆级结构、片上 SRAM 局部性、数据流调度、编译器管理执行
- 代表作品：[HOTCHIPS-2017-P0025](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2017-P0025)、[HOTCHIPS-2022-P0019](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0019)、[HOTCHIPS-2023-P0038](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0038)、[HOTCHIPS-2025-P0034](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0034)
- 团队线索：Cerebras、SambaNova/Groq 风格的空间数据流组织和早期的DNN加速器团队提供血统信号；没有推断排名。
- workload/artifact 信号：workload = DNN 训练/推理和大张量内核；瓶颈=不规则模型形状下的片外移动和利用；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2016-2025 年 8 个evidence rows；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：FPL 数据流加速器； MICRO 数据移动研究
- 开放问题：与编译器/运行时控制相比，数据流优势有多少来自架构？

### [HOTCHIPS-SF04](#HOTCHIPS-SF04)：PIM、CXL 和 AI 内存墙的近内存计算

- 研究问题：内存扩展、CXL 如何构造和近内存计算攻击能力和带宽压力。
- 背景：CXL 教程和内存扩展器产品使 Hot Chips 成为内存墙平台化的有用索引。
- 当前状态：CXL/PIM 产品披露和标准方向的证据最强，该语料库内衡量采用的证据较弱。
- 技术路线：CXL 内存池、内存扩展器、AXDIMM/PIM、近内存内核、一致性协议
- 代表作品：[HOTCHIPS-2021-P0039](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2021-P0039)、[HOTCHIPS-2022-P0004](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0004)、[HOTCHIPS-2022-P0029](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0029)、[HOTCHIPS-2026-P0035](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0035)
- 团队线索：三星、CXL 生态系统参与者和内存供应商团队提供信号；没有推断排名。
- workload/artifact 信号：workload = 内存限制 AI、分析和服务器 workload；瓶颈=容量扩展和主机设备移动；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2021-2026 年 9 个evidence rows；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：ISCA/MICRO 内存系统； ASPLOS 系统工作
- 开放问题：哪些 CXL/PIM 机制成为标准平台功能而不是单点产品？

### [HOTCHIPS-SF05](#HOTCHIPS-SF05)：HBM、chiplet 封装和 die-to-die 集成

- 研究问题：HBM、chiplet 和 die-to-die 标准如何让加速器扩展带宽和封装复杂性。
- 背景：HBM 披露、Aquabolt、AMD/Xilinx 2.5D 线路和 UCIe 教程给会场带来了强烈的包装信号。
- 当前状态：到 2023-2026 年，UCIe 和 HBM 将被视为 AI 系统的平台原语，而不是纯组件主题。
- 技术路线：HBM 堆栈、2.5D 中介层、小芯片、UCIe 链路、高级封装
- 代表作品：[HOTCHIPS-2016-P0022](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2016-P0022)、[HOTCHIPS-2022-P0046](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0046)、[HOTCHIPS-2023-P0008](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0008)、[HOTCHIPS-2023-P0009](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0009)
- 团队线索：Samsung、AMD/Xilinx 和 UCIe 生态系统参与者经常出现包装/标准；没有推断排名。
- workload/artifact 信号：workload = AI 加速器、原型设备和服务器芯片；瓶颈=封装带宽、产量、功率密度和链路互操作性；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2016-2026 年 10 个evidence rows；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：ISSCC 封装电路； DAC 小芯片设计流程
- 开放问题：chiplet/HBM 封装选择应如何与架构级 workloadclaim 联系起来？

### [HOTCHIPS-SF06](#HOTCHIPS-SF06)：用于 AI 放大的光学 I/O 和光子结构

- 研究问题：光学连接、共同封装的光学器件和光子开关如何缓解电气放大限制。
- 背景：TeraPHY、Broadcom Optical Attach、Lightmatter、Ayar Labs 和 TPUv4 OCS 形成了跨年度光学结构线。
- 当前状态：存在强有力的产品/披露证据；影响 claim 应与官方产品和paper source保持联系，除非采用经过独立验证。
- 技术路线：optical Attach、硅光子、共封装光学、光路交换、光子 NoC/fabric
- 代表作品：[HOTCHIPS-2019-P0020](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2019-P0020)、[HOTCHIPS-2023-P0027](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0027)、[HOTCHIPS-2024-P0012](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0012)、[HOTCHIPS-2025-P0007](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0007)、[HOTCHIPS-2026-P0037](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0037)
- 团队线索：Google、Broadcom、Lightmatter、Ayar Labs 和硅光子团队再次出现；没有推断排名。
- workload/artifact 信号：workload = AI 纵向扩展/横向扩展通信；瓶颈 = serdes 功率、范围、基数和带宽密度；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2016-2026 年 15 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：SIGCOMM/NSDI 数据中心网络； ISSCC 光子 I/O
- 开放问题：除了产品公告之外，哪些光学结构设计具有独立可观察的部署？

### [HOTCHIPS-SF07](#HOTCHIPS-SF07)：DPU、SmartNIC 和 AI 数据中心结构卸载

- 研究问题：基础设施处理器和可编程 NIC 如何卸载网络、存储、安全和集体移动。
- 背景：Pensando、BlueField、DOJO 网络、DPU/SmartNIC 行公开了 AI 集群的基础设施端。
- 当前状态：随着 AI 平台披露范围从加速器卡扩展到集群结构，该产品线变得越来越重要。
- 技术路线：可编程数据包引擎、RDMA/offload、NIC端加速、遥测/安全引擎
- 代表作品：[HOTCHIPS-2021-P0003](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2021-P0003)、[HOTCHIPS-2024-P0013](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0013)、[HOTCHIPS-2025-P0004](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0004)、[HOTCHIPS-2026-P0038](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0038)
- 团队线索：NVIDIA/Mellanox、 AMD/Pensando、特斯拉和基础设施网络团队再次出现；没有推断排名。
- workload/artifact 信号：workload = AI 数据中心网络、存储和控制平面 workload；瓶颈 = 主机 CPU 开销、结构拥塞和安全隔离；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2018-2026 年 12 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：NSDI/SOSP 系统； ISCA 网络加速
- 开放问题：DPU/SmartNIC 卸载在哪里显着改善 AI 集群操作，而不仅仅是一般基础设施？

### [HOTCHIPS-SF08](#HOTCHIPS-SF08)：边缘实时3D重建和感知

- 研究问题：边缘SoC如何在移动功率限制下支持同时定位、3D重建和感知。
- 背景：Navion、PNNPU 和 DSPU 形成一条较小但直接相关的边缘感知线。
- 当前状态：该行已验证代表性行，但引用/采用数据不均匀，必须保持部分未 verified。
- 技术路线：视觉惯性处理、神经感知引擎、稀疏性、设备端映射管道
- 代表作品：[HOTCHIPS-2018-P0013](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2018-P0013)、[HOTCHIPS-2021-P0024](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2021-P0024)、[HOTCHIPS-2022-P0038](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2022-P0038)、[HOTCHIPS-2026-P0022](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0022)
- 团队线索：MIT/edge-vision 风格的学术团队和工业感知-SoC 团队出现；没有推断排名。
- workload/artifact 信号：workload = SLAM、自主导航、AR/VR 感知和机器人；瓶颈 = 边缘的延迟、功耗和内存占用；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2016-2026 年 6 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：ICRA/IROS 机器人； CVPR/ICCV 3D 感知加速器
- 开放问题：边缘感知 SoC claim 如何直接转移到当前的 3D 重建 workload？

### [HOTCHIPS-SF09](#HOTCHIPS-SF09)：实时神经渲染和 3DGS 管道硬件

- 研究问题：GPU 和空间 SoC 如何公开对神经渲染和 3D 高斯泼溅式 workload 的硬件支持。
- 背景：RTX 神经渲染、Microsoft Maia 100 和 IRIS 3DGS 使其成为 2025 年最清晰的面向用户的新兴主题。
- 当前状态：语料库具有较高的相关性，但早期证据；主张应被视为前沿信号，而不是既定共识。
- 技术路线：光线/神经渲染核心、空间高斯管线、渲染/建模 SoC、图形-AI 协同设计
- 代表作品：[HOTCHIPS-2025-P0014](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0014)、[HOTCHIPS-2025-P0015](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0015)、[HOTCHIPS-2025-P0020](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0020)
- 团队线索：NVIDIA、微软和 KAIST/IRIS 风格的团队提供早期神经渲染信号；没有推断排名。
- workload/artifact signal：workload = 神经渲染、可交互 3D 重建和图形 AI；瓶颈=实时帧延迟、内存带宽和几何/模型更新成本；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2025 年 3 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：SIGGRAPH/TOG 神经渲染； CVPR 3DGS； FPL FPGA 渲染原型
- 开放问题：哪些神经渲染/3DGS 原语足够稳定，足以证明专用硬件的合理性？

### [HOTCHIPS-SF10](#HOTCHIPS-SF10)：开源 EDA 和可复制的 SoC 芯片

- 研究问题：开源硬件工具链、验证流程和可复制的硅 artifact 如何变得实用。
- 背景：TCMM 奖项和蛇怪/柴郡风格的硅排在venue-internal提供了artifact-backed evidence。
- 当前状态：社区/工具链 artifact 的证据很充分，但award rows是社区奖项而不是普通的论文奖项。
- 技术路线：Verilator、PULP、Yosys/IceStorm、RISC-V SoC、开放 PDK 流程、可重现流片
- 代表作品：[HOTCHIPS-2024-P0030](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-P0030)、[HOTCHIPS-2025-P0022](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0022)、[HOTCHIPS-2025-A07](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-A07)、[HOTCHIPS-2024-A03](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2024-A03)、[HOTCHIPS-2025-A05](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-A05)
- 团队线索：PULP、Claire Wolf/开源 EDA、Verilator 和 RISC-V 社区提供 artifact 信号；没有推断排名。
- workload/artifact 信号：workload = SoC 原型设计和硬件研究基础设施；瓶颈=验证、物理设计再现性和工具链集成；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2021-2026 年 7 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：DAC/FPL 打开EDA； CHIPS 联盟/RISC-V 生态系统
- 开放问题：哪些开源硬件 artifact 在其原始团队之外得到重用？

### [HOTCHIPS-SF11](#HOTCHIPS-SF11)：FPGA、CGRA 和自适应数据流映射

- 研究问题：FPGA、CGRA 和自适应设备如何映射不规则或快速变化的加速器 workload。
- 背景：Brainwave、Catapult、Groq/Cerebras 相邻数据流、Versa 和 VP1902 原型行将 Hot Chips 连接到 FPL/DAC。
- 当前状态：生产数据中心卸载和原型/仿真基础设施之间的线路划分。
- 技术路线：FPGA 覆盖、CGRA 磁贴、编译时布局、流数据流、仿真/原型结构
- 代表作品：[HOTCHIPS-2017-P0005](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2017-P0005)、[HOTCHIPS-2017-P0006](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2017-P0006)、[HOTCHIPS-2023-P0039](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0039)、[HOTCHIPS-2026-P0029](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2026-P0029)
- 团队线索：Microsoft Catapult/Brainwave、 AMD/Xilinx 和自适应计算团队再次出现；没有推断排名。
- workload/artifact 信号：workload = AI 推理、网络/存储卸载、芯片原型设计和信号处理；瓶颈=编译/映射时间、利用率和内存移动；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2016-2026 年 14 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：FPL 可重构计算； DAC 仿真/原型
- 开放问题：哪些 FPGA/CGRA 映射流程足以减少生产 workload 的编译摩擦？

### [HOTCHIPS-SF12](#HOTCHIPS-SF12)：基准测试、编译器和内核语言方法

- 研究问题：基准测试、编译器抽象和内核语言如何使加速器比较和编程变得可信。
- 背景：MLPerf 链接的 A100、内核语言和编译器行将方法论显示为反复出现的支持主题。
- 当前状态：这是一个跨领域子领域：作为支持证据比作为独立的 Hot Chips 主题更强大。
- 技术路线：MLPerf、基准测试套件、编译器 IR、内核 DSL、自动调优、软件堆栈
- 代表作品：[HOTCHIPS-2019-P0016](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2019-P0016)、[HOTCHIPS-2019-P0028](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2019-P0028)、[HOTCHIPS-2023-P0005](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2023-P0005)、[HOTCHIPS-2025-P0036](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2025-P0036)
- 团队线索：基准测试/编译器团队表现为横切基础设施；没有推断排名。
- workload/artifact 信号：workload = AI 内核和加速器软件工作流程；瓶颈=可移植性、可比性和程序员生产力；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2019-2025 年 4 行证据；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：MLSys、CGO、PLDI、DAC 编译器流程
- 开放问题：哪些基准测试可以比较高度不同的加速器堆栈？

### [HOTCHIPS-SF13](#HOTCHIPS-SF13)：安全性和信任作为架构约束

- 研究问题：安全飞地和可信执行如何约束加速器和服务器芯片架构。
- 背景：Sanctum 是一个早期的锚点，表明架构披露包括安全约束，而不仅仅是性能。
- 当前状态：该语料库内部稀疏，因此保留为边界主题，而不是占主导地位的 Hot Chips 趋势。
- 技术路线：可信执行、enclave 隔离、内存保护、侧通道边界
- 代表作品：[HOTCHIPS-2018-P0019](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2018-P0019)
- 团队线索：Sanctum 相关架构/安全团队是边界信号；没有推断排名。
- workload/artifact 信号：workload = 安全云/服务器执行；瓶颈=隔离与性能和可编程性；仅当证据矩阵中存在代码或官方奖励来源时，才会记录经过验证的 artifact 信号。
- 趋势证据：2018 年 1 个evidence rows；仅当存在多行或跨年度证据时才使用趋势语言。
- cross-venue 挂钩：IEEE S&P/USENIX 安全； ISCA 安全架构
- 开放问题：架构安全约束是否成为加速器venue的中心，还是仍然是一个边界主题。

## 4. 发展趋势

- AI 加速器披露从单芯片吞吐量转向平台经济性。证据涵盖 2017-2021 年的 TPU/GPU 系列、2020 年的 A100、H100/Dojo 时代的系列、2024 年的 Blackwell、2025 年的 MI350/Ironwood 以及多个 2026 年高级计划系列。这一趋势是跨年度的，但 2026 年的细节仍然是片面的。
- LLM 服务将瓶颈词汇从通用张量吞吐量更改为内存状态、KV/缓存压力、推理性能/TCO 和每个令牌的成本。 2024-2026 年的证据最为有力，因此这是一种前沿趋势，而不是完全成熟的历史趋势。
- 封装、HBM、CXL、UCIe 和光纤 I/O 成为一流的架构主题，因为加速器规模受到内存容量、封装带宽和集群结构功率的限制。证据涵盖 HBM/chiplet 行、CXL 教程/产品、UCIe 教程和光学结构披露。
- 边缘 3D 重建和神经渲染虽小但直接相关的线程。 Navion/PNNPU/DSPU 提供边缘感知锚点； RTX 5090 和 IRIS 提供 2025 个神经渲染/3DGS 前沿信号。影响尚未得到与主要数据中心平台相同级别的验证。
- 开源 EDA 和可复制芯片主要通过 TCMM 奖项和与 artifact 相关的行而不是普通的论文奖项出现。这些信号对于工具轨迹很有用，但不应与最佳论文 claim 混合在一起。

## 5. 方法变化

Hot Chips 行是演示/披露，因此证据方法与传统的会议论文语料库不同。对于主要技术行，矩阵记录`official_program_or_proceedings`或`official_advance_program`。对于奖项，矩阵记录 `award_source`。影响条目使用 `impact_unverified`，除非明确找到带有检索日期的引文、基准、代码/artifact、官方产品堆栈采用或规范奖励证据。

## 6. 缺失来源

- Canonical 2016-2023 Hot Chips 奖励页面未找到占位符最佳/杰出paper rows。
- 一些较旧的行缺少可靠来源中的 DOI、摘要、PDF 或 artifact URL；这些仍然是语料库元数据中的 `needs_review`，而不是猜测。
- 几个影响信号，特别是边缘感知和 3DGS 行，具有冲突或早期引用证据，并保留 `needs_review` 或 `impact_unverified`。
