# TCAD 小领域深读

## 1. 范围与语料

- 语料库：`papers.csv` 有 2016-2026 年的 3329 行期刊文章； `awards.csv` 有 14 行 Pederson 奖。 2026 有 246 行，仍然是 `partial`。
- 筛选矩阵行：3343。决策：{'needs_review': 1040, 'index_only': 2256, 'deep_read': 47}。
- 证据矩阵行：35 个parent agent选择的deep-read代表。读取深度是每行记录的抽象/元数据/artifact-docs level。没有 claim 完整的 PDF 读取或 artifact 执行。
- 使用的来源：DBLP TCAD 卷页面、DOI 解析器/IEEE Xplore URL、Crossref Works API、Semantic Scholar论文页面、IEEE CEDA Pederson 奖页面以及经过验证的 DREAMPlace GitHub URL， DNN+NeuroSim 和 CircuitNet。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="TCAD-SF01"></a>[TCAD-SF01](#TCAD-SF01) | 物理设计、光刻、热和布局收敛 | 随着设计变得更加复杂，如何关闭布局、布线、光刻、热和布局约束。 | 布局、布线、光刻、热仿真 | 运行时、拥塞、可制造性、热精度 | GPU/工具包加速、ML 热点检测、并行热仿真、时序驱动布局 | 2016-2026 | [TCAD-2021-P0047](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0047);[TCAD-2021-P0112](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0112);[TCAD-2022-P0278](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0278);[TCAD-2023-P0049](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0049);[TCAD-2024-P0281](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0281) |
| <a id="TCAD-SF02"></a>[TCAD-SF02](#TCAD-SF02) | HLS、FPGA 和可重构硬件生成 | 算法和系统模型如何成为 FPGA 或具有有用 QoR 的可重构实现。 | HLS 内核、FPGA 加速器、AMS 仿真 | 资源绑定、时序收敛、DSE、工具成熟度 | 工具调查、HLS DSE、FPGA 仿真、基准套件 | 2016-2026 | [TCAD-2016-P0015](../../10_corpus/TCAD/id_index.md#TCAD-2016-P0015);[TCAD-2019-P0122](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0122);[TCAD-2020-P0076](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0076);[TCAD-2022-P0386](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0386);[TCAD-2023-P0091](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0091) |
| <a id="TCAD-SF03"></a>[TCAD-SF03](#TCAD-SF03) | 神经/边缘加速器和硬件-软件协同设计 | 神经和边缘 workload 如何在内存、延迟和资源限制下映射到硬件。 | CNN、DNN、ViT、机器人、LLM 推理 | 内存流量、利用率、延迟、能源、协同探索成本 | 量化、稀疏性、数据流、HLS、FPGA/ASIC 协同设计 | 2017-2026 | [TCAD-2017-P0088](../../10_corpus/TCAD/id_index.md#TCAD-2017-P0088);[TCAD-2018-P0016](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0016);[TCAD-2019-P0039](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0039);[TCAD-2020-P0254](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0254);[TCAD-2022-P0303](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0303);[TCAD-2026-P0201](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0201) |
| <a id="TCAD-SF04"></a>[TCAD-SF04](#TCAD-SF04) | CIM/PIM 和神经形态基准框架 | 以内存为中心的设备和模拟器如何减少数据移动并使比较可重复。 | CIM/PIM、SNN、神经形态、Transformer/PIM | 数据移动、设备变化、基准保真度 | NeuroSim、DNN+NeuroSim、SpikeSim、ReRAM/PIM 映射 | 2018-2026 | [TCAD-2018-P0118](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0118);[TCAD-2021-P0045](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0045);[TCAD-2023-P0085](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0085);[TCAD-2026-P0117](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0117) |
| <a id="TCAD-SF05"></a>[TCAD-SF05](#TCAD-SF05) | Transformer 和 LLM 注意力加速 | 注意力和 LLM 推理/训练如何与记忆运动、稀疏性和精度相互作用。 | Transformer、ViT、LLM、长序列注意力 | KV/激活内存、稀疏 softmax、精度、并行性 | ReRAM/PIM、稀疏注意力、量化、FPGA、张量核心和异步并行 | 2022-2026 | [TCAD-2022-P0449](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0449);[TCAD-2023-P0003](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0003);[TCAD-2024-P0236](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0236);[TCAD-2024-P0307](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0307);[TCAD-2026-P0161](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0161);[TCAD-2026-P0231](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0231) |
| <a id="TCAD-SF06"></a>[TCAD-SF06](#TCAD-SF06) | Neural rendering and NeRF acceleration | Whether neural rendering appears in TCAD as hardware/software co-design rather than only graphics algorithms. | NeRF 和神经渲染 | 体素/射线/解码数据移动和延迟 | PIM，延迟神经解码，以体素为中心的数据流 | 2024-2025 | [TCAD-2024-P0120](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0120);[TCAD-2025-P0308](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0308) |
| <a id="TCAD-SF07"></a>[TCAD-SF07](#TCAD-SF07) | AI 用于 EDA 和 LLM 辅助 CAD | ML/LLM 如何帮助具体的 EDA 任务，例如热点检测、RTL生成、布局和数据集。 | 光刻热点、RTL 生成、模拟布局、VLSI CAD 数据集 | 泛化、数据稀缺性、验证、人机循环生产力 | 联邦学习、开放数据集、LLM 辅助生成、多智能体布局 | 2023-2025 | [TCAD-2023-P0180](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0180);[TCAD-2024-P0281](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0281);[TCAD-2025-P0209](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0209);[TCAD-2025-P0341](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0341) |
| <a id="TCAD-SF08"></a>[TCAD-SF08](#TCAD-SF08) | 3D IC、小芯片、中介层和 NoC 集成约束 | 封装/集成如何改变物理设计、测试、散热和通信约束。 | 3D IC、2.5D、chiplet、NoC | 散热、布线、TSV/中介层、成品率/安全性 | 两层物理设计、分区、NoC/中介层方法 | 2016-2026 | [TCAD-2020-P0365](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0365);[TCAD-2026-P0117](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0117) |
| <a id="TCAD-SF09"></a>[TCAD-SF09](#TCAD-SF09) | 逻辑、形式和量子 CAD 方法锚 | 表示和映射选择如何控制优化/搜索复杂性。 | 逻辑综合、形式化检查、量子映射 | 表示大小、映射深度、证明/搜索成本 | MIG、SAT/形式化方法、量子映射启发式 | 2016-2026 | [TCAD-2016-P0111](../../10_corpus/TCAD/id_index.md#TCAD-2016-P0111);[TCAD-2019-P0148](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0148) |

## 3. 小领域深读

### [TCAD-SF01](#TCAD-SF01)。物理设计、光刻、热和布局封闭
- 研究问题：随着设计变得更加复杂，如何封闭布局、布线、光刻、热和布局约束。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2016-2026 年 `venue_provisional`。支持集是`TCAD-2021-P0047;TCAD-2021-P0112;TCAD-2022-P0278;TCAD-2023-P0049;TCAD-2024-P0281`。
- 方法谱系：GPU/工具包加速、ML 热点检测、并行热模拟、时序驱动布局。
- 代表论文：OpenMPL: An Open-Source Layout Decomposer； DREAMPlace：支持深度学习工具包的 GPU 加速，用于现代 VLSI 放置； PACT：用于新兴集成和冷却技术的可扩展并行热模拟器； DREAMPlace 4.0：基于动量的净权重和基于拉格朗日的细化的时序驱动布局；基于具有局部适应和特征选择的异构联邦学习的光刻热点检测。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：布局、布线、光刻、热模拟；瓶颈：运行时间、拥塞、可制造性、热精度。仅在检查 URL 时记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

### [TCAD-SF02](#TCAD-SF02)。 HLS、FPGA 和可重构硬件生成
- 研究问题：算法和系统模型如何成为 FPGA 或具有有用 QoR 的可重构实现。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2016-2026 年 `venue_provisional`。支持集是`TCAD-2016-P0015;TCAD-2019-P0122;TCAD-2020-P0076;TCAD-2022-P0386;TCAD-2023-P0091`。
- 方法谱系：工具调查、HLS DSE、FPGA 模拟、基准测试套件。
- 代表论文：FPGA高级综合工具的调查与评估；我们到了吗？高水平合成现状研究；高级综合设计空间探索：过去、现在和未来；用于 FPGA 模拟/混合信号集成电路设计仿真的开源框架； Koios 2.0：FPGA 架构和 CAD 研究的开源深度学习基准。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：HLS 内核、FPGA 加速器、AMS 仿真；瓶颈：资源绑定、时序收敛、DSE、工具成熟度。仅在检查 URL 时记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

### [TCAD-SF03](#TCAD-SF03)。神经/边缘加速器和硬件-软件协同设计
- 研究问题：神经和边缘 workload 如何在内存、延迟和资源限制下映射到硬件。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2017-2026 年 `venue_provisional`。支持集是`TCAD-2017-P0088;TCAD-2018-P0016;TCAD-2019-P0039;TCAD-2020-P0254;TCAD-2022-P0303;TCAD-2026-P0201`。
- 方法谱系：量化、稀疏性、数据流、HLS、FPGA/ASIC 协同设计。
- 代表论文：DLAU: A Scalable Deep Learning Accelerator Unit on FPGA； YodaNN：超低功耗二进制权重 CNN 加速架构；咖啡因：深度卷积神经网络的统一表示和加速；神经架构的硬件/软件协同探索； INCAME：用于多机器人探索的可中断 CNN 加速器； Terafly：基于多节点 FPGA 的加速器设计，用于LLM中的高效协作推理。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：CNN、DNN、ViT、机器人、LLM 推理；瓶颈：内存流量、利用率、延迟、能源、协同探索成本。仅在检查了 URL 的情况下记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

### [TCAD-SF04](#TCAD-SF04)。 CIM/PIM 和神经形态基准框架
- 研究问题：以内存为中心的设备和模拟器如何减少数据移动并使比较可重复。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2018-2026 年 `venue_provisional`。支持集是`TCAD-2018-P0118;TCAD-2021-P0045;TCAD-2023-P0085;TCAD-2026-P0117`。
- 方法谱系：NeuroSim、DNN+NeuroSim、SpikeSim、ReRAM/PIM 映射。
- 代表论文：NeuroSim: A Circuit-Level Macro Model for Benchmarking Neuro-Inspired Architectures in Online Learning； DNN+NeuroSim V2.0：用于片上训练的内存计算加速器的端到端基准测试框架； SpikeSim：一种用于对尖峰神经网络进行基准测试的端到端内存计算硬件评估工具； COMET-3D：具有优化管道和 3D 异构集成的基于内存计算的 Transformer 加速器。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：CIM/PIM、SNN、神经形态、Transformer/PIM；瓶颈：数据移动、设备变化、基准保真度。仅在检查了 URL 的情况下记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

### [TCAD-SF05](#TCAD-SF05)。 Transformer 和 LLM 注意力加速
- 研究问题：注意力和 LLM 推理/训练如何与记忆运动、稀疏性和精度相互作用。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2022-2026 年 `cross_venue_candidate`。支持集是`TCAD-2022-P0449;TCAD-2023-P0003;TCAD-2024-P0236;TCAD-2024-P0307;TCAD-2026-P0161;TCAD-2026-P0231`。
- 方法谱系：ReRAM/PIM、稀疏注意力、量化、FPGA、张量核心和异步并行。
- 代表论文：A Framework for Accelerating Transformer-Based Language Model on ReRAM-Based Architecture； Energon：利用动态稀疏注意力实现Transformer的高效加速； ULSeq-TA：支持分组稀疏Softmax和双路径稀疏LayerNorm的超长序列注意力融合Transformer加速器；利用各种线路稀疏性和基于瓦片的动态量化的移动Transformer加速器； APT-LLM：利用任意精度张量核心计算实现 LLM 加速； AsyncGrid：用于响应式边缘 LLM 推理的层内和层间异步混合并行系统。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：Transformer、ViT、LLM、长序列注意力；瓶颈：KV/激活内存、稀疏softmax、精度、并行性。仅在检查 URL 时记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

### [TCAD-SF06](#TCAD-SF06)。神经渲染和 NeRF 加速
- 研究问题：神经渲染是否以硬件/软件协同设计的形式出现在 TCAD 中，而不仅仅是图形算法。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2024-2025 年 `insufficient_evidence_for_stable_trend`。支持集是`TCAD-2024-P0120;TCAD-2025-P0308`。
- 方法谱系：PIM，延迟神经解码，以体素为中心的数据流。
- 代表论文：NeRF-PIM：PIM Hardware-Software Co-Design of Neural Rendering Networks；通过延迟神经解码和以体素为中心的数据流进行神经渲染加速。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：NeRF 和神经渲染；瓶颈：体素/射线/解码数据移动和延迟。仅在检查 URL 时记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

### [TCAD-SF07](#TCAD-SF07)。 AI 用于 EDA 和 LLM 辅助 CAD
- 研究问题：ML/LLM 如何帮助具体的 EDA 任务，例如热点检测、RTL 生成、布局和数据集。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2023-2025 年 `venue_provisional`。支持集是`TCAD-2023-P0180;TCAD-2024-P0281;TCAD-2025-P0209;TCAD-2025-P0341`。
- 方法谱系：联合学习、开放数据集、LLM 辅助生成、多智能体布局。
- 代表论文：CircuitNet：用于 VLSI CAD 应用程序中机器学习的开源数据集，具有改进的领域特定评估指标和学习策略；基于具有局部适应和特征选择的异构联邦学习的光刻热点检测； RTLCoder：完全开源、高效的LLM辅助RTL代码生成技术； LayoutCopilot：由 LLM 支持的多代理协作框架，用于交互式模拟布局设计。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：光刻热点、RTL 生成、模拟布局、VLSI CAD 数据集；瓶颈：泛化、数据稀缺、验证、人机循环生产力。仅在检查了 URL 的情况下记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

### [TCAD-SF08](#TCAD-SF08)。 3D IC、小芯片、中介层和 NoC 集成限制
- 研究问题：封装/集成如何改变物理设计、测试、热和通信限制。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2016-2026 年 `cross_venue_candidate`。支持集是`TCAD-2020-P0365;TCAD-2026-P0117`。
- 方法谱系：两层物理设计、分区、NoC/中介层方法。
- 代表论文：Compact-2D：构建两层门级 3-D IC 的物理设计方法； COMET-3D：具有优化管道和 3D 异构集成的基于内存计算的 Transformer 加速器。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：3D IC、2.5D、chiplet、NoC；瓶颈：散热、布线、TSV/中介层、产量/安全性。仅在检查 URL 时记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

### [TCAD-SF09](#TCAD-SF09)。逻辑、形式和量子 CAD 方法锚定
- 研究问题：表示和映射选择如何控制优化/搜索复杂性。
- 背景：TCAD 将此视为设计方法或评估问题，而不仅仅是平台标签。evidence rows显示了期刊语料库中可见的 workload 和约束。
- TCAD 的当前状态：2016-2026 年 `method_bridge`。支持集是`TCAD-2016-P0111;TCAD-2019-P0148`。
- 方法谱系：MIG、SAT/形式方法、量子映射启发法。
- 代表论文：Majority-Inverter Graph: A New Paradigm for Logic Optimization；将量子电路映射到 IBM QX 架构的有效方法。
- 团队线索：仅限作者字符串信号；此通行证中不提出任何排名或隶属时间要求。
- workload/artifact 信号：逻辑综合、形式检查、量子映射；瓶颈：表示大小、映射深度、证明/搜索成本。仅在检查 URL 时记录代码/数据集信号。
- 开放问题：完整的 IEEE 术语、隶属时间数据、artifact 执行和cross-venue比较仍然开放，除非一行明确说明不然。

## 4. 发展趋势

- HLS/FPGA 作品显示在整个窗口中，并得到 [TCAD-2016-P0015](../../10_corpus/TCAD/id_index.md#TCAD-2016-P0015)、[TCAD-2019-P0122](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0122)、[TCAD-2020-P0076](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0076)、[TCAD-2022-P0386](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0386) 和 [TCAD-2023-P0091](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0091) 的支持。这是一个持续的 TCAD 方法行，而不仅仅是一个 FPGA 标题。
- 神经加速器和硬件/软件协同设计行从早期的 FPGA/DNN 加速器（[TCAD-2017-P0088](../../10_corpus/TCAD/id_index.md#TCAD-2017-P0088)、[TCAD-2018-P0016](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0016)、[TCAD-2019-P0039](../../10_corpus/TCAD/id_index.md#TCAD-2019-P0039)）转移到协同探索和边缘/LLM 行（[TCAD-2020-P0254](../../10_corpus/TCAD/id_index.md#TCAD-2020-P0254)、[TCAD-2022-P0303](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0303)、[TCAD-2026-P0201](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0201)）。 2026年的证据是不完整的。
- CIM/PIM 基准测试受 [TCAD-2018-P0118](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0118)、[TCAD-2021-P0045](../../10_corpus/TCAD/id_index.md#TCAD-2021-P0045)、[TCAD-2023-P0085](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0085) 和 [TCAD-2026-P0117](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0117) 支持。趋势 claim 仅限于 TCAD 可见性和基准/工具框架；是否采用尚未得到证实。
- Transformer/LLM 加速从 2022 年起变得可见：[TCAD-2022-P0449](../../10_corpus/TCAD/id_index.md#TCAD-2022-P0449)、[TCAD-2023-P0003](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0003)、[TCAD-2024-P0236](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0236)、[TCAD-2024-P0307](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0307)、[TCAD-2026-P0161](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0161) 和 [TCAD-2026-P0231](../../10_corpus/TCAD/id_index.md#TCAD-2026-P0231)。 2026 年以来的行仅是前沿信号。
- 神经渲染在本轮中恰好有两个 TCAD 行，[TCAD-2024-P0120](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0120) 和 [TCAD-2025-P0308](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0308)。这是与用户相关的直接证据，但不足以形成稳定的 venue 趋势。
- AI for EDA/LLM-assisted CAD 由 [TCAD-2023-P0180](../../10_corpus/TCAD/id_index.md#TCAD-2023-P0180)、[TCAD-2024-P0281](../../10_corpus/TCAD/id_index.md#TCAD-2024-P0281)、[TCAD-2025-P0209](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0209) 和 [TCAD-2025-P0341](../../10_corpus/TCAD/id_index.md#TCAD-2025-P0341) 支撑。共同问题是具体的设计自动化任务，而不是通用 AI 标签。

## 5. 方法变化

- 前几行强调工具评估、架构模板和表示选择：HLS 调查、MIG、DLAU 和 YodaNN。
- 中间窗口行添加基准框架和加速的 CAD 工具：Caffeine、HLS DSE、NeuroSim/DNN+NeuroSim、DREAMPlace 和 Compact-2D。
- 最近的行转向数据/模型协同设计和工作流程自动化：Transformer 稀疏性/量化、神经渲染数据流、联合热点检测、RTLCoder 和 LayoutCopilot。
- 评估语言也发生变化。较老的行通常关注 QoR、运行时间、资源或能源；较新的行添加了基准可重复性、数据可用性、模型泛化和面向用户的工作流程指标。

## 6. 缺失来源

- IEEE Xplore 完整导出 TCAD 2016-2026 的摘要、IEEE 术语和从属关系。
- DBLP/Crossref/IEEE 协调元数据表。
- DREAMPlace、DNN+NeuroSim、CircuitNet、RTLCoder、SpikeSim、Koios 和 PACT 类工具的 artifact 执行或重用审核。
- DAC、ICCAD、DATE、ASP-DAC 和 FPGA 的cross-venue主题矩阵。
- 超出 Crossref/Semantic Scholar计数的引用/采用结构审核。
