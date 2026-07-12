# PACT 小领域深读

## 1. 范围与语料

- Venue：`PACT`（并行架构和编译技术国际会议）。
- 语料库：2016-2026 年 `423` paper rows和 `5` award rows；截至 2026 年 6 月 27 日，2026 仍然是正常的部分标记。
- 筛选：`428` 行；决策计数 `{'deep_read': 111, 'needs_review': 103, 'index_only': 145, 'exclude_non_main': 69}`。
- 证据矩阵：`108` 接受的paper rows；读取深度计数 `{'title': 24, 'artifact_docs': 1, 'pdf_section': 26, 'abstract+artifact_docs': 1, 'full_pdf': 2, 'abstract': 13, 'official_page': 41}`。
- 通过从现有 DOI 解析器 `source_url` 值中提取 DOI 值，DOI 覆盖范围从 0 行提高到 422 行。这是元数据回填，而不是新技术解释。
- 引用/采用信号是初步的。 Crossref 和Semantic Scholar计数用 `checked_date=2026-06-27` 记录，并不证明采用或里程碑状态。

## 2. 小领域图谱

| subfield_id | 子领域 | 核心问题 | workload | 瓶颈 | 机制 | 活跃年数 | 证据状态 |
|---|---|---|---|---|---|---|---|
| <a id="PACT-SF01"></a>[PACT-SF01](#PACT-SF01) | 调度/代码生成/自动调整 | 减少调度搜索和手动编译器调整成本 | 编译器、MLIR、多面体、张量代码生成 | 搜索成本和可移植性 | 降低、自动调整、程序合成 | 2016-2025 | venue_provisional |
| <a id="PACT-SF02"></a>[PACT-SF02](#PACT-SF02) | GPU 内存/运行时利用率 | 保持 GPU 内存、TLB、扭曲和共享行为不受运行时支配 | GPU 内核和 CPU-GPU workload | 延迟、地址转换、争用 | 扭曲调度、页表、运行时共享 | 2016-2024 | venue_provisional |
| <a id="PACT-SF03"></a>[PACT-SF03](#PACT-SF03) | 稀疏图和不规则计算 | 使稀疏/图形/GNN 足够规律地工作，以利用并行硬件 | 图形分析、稀疏矩阵、GNN | 负载不平衡和不规则内存 | 格式转换、分区、缓存使用 | 2016-2025 | venue_provisional |
| <a id="PACT-SF04"></a>[PACT-SF04](#PACT-SF04) | DNN/GNN/LLM 张量执行 | 提高模型执行、服务、训练和张量代码效率 | DNN、GNN、LLM、MoE、张量程序 | 内存占用、通信、张量利用率 | 稀疏性、量化、缓存、并行性 | 2018-2025 | venue_provisional |
| <a id="PACT-SF05"></a>[PACT-SF05](#PACT-SF05) | PIM/CXL/近内存数据移动 | 通过移动降低带宽/容量成本内存计算或管理 | PIM、CXL、NVM、KV 缓存、指针密集型 workload | 数据移动、容量、持久性开销 | 近内存处理、CXL 分层、负载重新平衡 | 2016-2025 | venue_provisional |
| <a id="PACT-SF06"></a>[PACT-SF06](#PACT-SF06) | FPGA/空间/异构映射 | 将应用程序映射到具有资源和可移植性限制的空间或异构硬件 | FPGA、空间加速器、CPU-FPGA、异构系统 | 资源利用、分区、主机设备移动 | HLS、源到源编译、加速器调度 | 2016-2025 | venue_provisional |
| <a id="PACT-SF07"></a>[PACT-SF07](#PACT-SF07) | 可靠性/安全性/加密加速 | 加速或强化可靠性/安全性/加密 workload | GPU 可靠性、FHE、ZKP、PQC | 吞吐量、能源、可靠性开销 | 专业加速、容错 | 2016-2025 | venue_provisional |
| <a id="PACT-SF08"></a>[PACT-SF08](#PACT-SF08) | 域 3D/视觉/机器人/基因组学/科学管道 | 优化数据移动和延迟占主导地位的域管道 | 3D 重建、SLAM、3DGS、基因组学、科学求解器 | 管道延迟、内存占用、实时吞吐量 | DSL、近似、平铺、移动GPU 映射 | 2016-2025 | venue_provisional |
| <a id="PACT-SF09"></a>[PACT-SF09](#PACT-SF09) | 基准测试/分析/建模 | 使评估和性能预测更加可靠 | 基准、分析、模拟器、性能模型 | 代表性、预测误差、采样成本 | 基准生成、建模、模拟 | 2016-2022 | venue_provisional |
| <a id="PACT-SF99"></a>[PACT-SF99](#PACT-SF99) | 残差 PACT 分类 | 行太宽，无法单独从标题/会话进行稳定的主题分配 | 混合 | 不确定 | 手动源浓缩 | 2016-2025 | insufficient_evidence |

## 3. 小领域深读

### [PACT-SF01](#PACT-SF01)。调度/代码生成/自动调优

- 研究问题：减少调度搜索和手动编译器调优成本。
- 背景/当前状态：PACT 中的 `13` evidence rows，跨越 2016 年至 2025 年。代表行：[PACT-2016-P0004](../../10_corpus/PACT/id_index.md#PACT-2016-P0004) 在 POWER8 上自动调整 Spark 大数据 workload：基于预测的动态 SMT 线程； [PACT-2017-P0002](../../10_corpus/PACT/id_index.md#PACT-2017-P0002) 自动脚本语言并行化的通用框架； [PACT-2017-P0012](../../10_corpus/PACT/id_index.md#PACT-2017-P0012) 优化启发式端到端深度学习； [PACT-2019-P0009](../../10_corpus/PACT/id_index.md#PACT-2019-P0009) BOLT：使用用户级线程优化 OpenMP 并行区域。
- 方法谱系：降低、自动调整、程序综合。平台标签仍然是实现上下文，而不是主要主题边界。
- 更强的evidence rows：[PACT-2017-P0002](../../10_corpus/PACT/id_index.md#PACT-2017-P0002) (pdf_section)； [PACT-2017-P0012](../../10_corpus/PACT/id_index.md#PACT-2017-P0012) (artifact_docs); [PACT-2019-P0009](../../10_corpus/PACT/id_index.md#PACT-2019-P0009) (pdf_section); [PACT-2025-P0024](../../10_corpus/PACT/id_index.md#PACT-2025-P0024) (pdf_section)。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF02](#PACT-SF02)。 GPU 内存/运行时利用率

- 研究问题：保持 GPU 内存、TLB、扭曲和共享行为不控制运行时。
- 背景/当前状态：PACT 中的 `5` evidence rows，跨越 2016 年至 2024 年。代表行： [PACT-2016-P0007](../../10_corpus/PACT/id_index.md#PACT-2016-P0007) 弥合 GPU 的语义差距 加速基于 CNN 的横向扩展大数据处理：大处着眼，小处着眼； [PACT-2018-P0023](../../10_corpus/PACT/id_index.md#PACT-2018-P0023) Mage：多尺度异构系统的在线和干扰感知调度； [PACT-2020-P0024](../../10_corpus/PACT/id_index.md#PACT-2020-P0024) GOPipe：用于 GPU 上流水线模板执行的粒度无关的编程框架； [PACT-2023-P0024](../../10_corpus/PACT/id_index.md#PACT-2023-P0024) SDM：具有缓存一致性计算 Express 链路的支持共享的分解内存系统。
- 方法谱系：warp 调度、页表、运行时共享。平台标签仍然是实现上下文，而不是主要主题边界。
- 更有力的evidence rows：[PACT-2018-P0023](../../10_corpus/PACT/id_index.md#PACT-2018-P0023) (pdf_section)。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF03](#PACT-SF03)。稀疏图和不规则计算

- 研究问题：使稀疏/图/GNN 工作足够规律以利用并行硬件。
- 背景/当前状态：PACT 中的 `8` evidence rows，跨越 2016 年至 2025 年。代表行：[PACT-2016-P0043](../../10_corpus/PACT/id_index.md#PACT-2016-P0043) Sparso：稀疏线性代数的上下文驱动优化； [PACT-2018-P0003](../../10_corpus/PACT/id_index.md#PACT-2018-P0003) 具有并行数据冲突管理功能的高效图形加速器； [PACT-2018-P0008](../../10_corpus/PACT/id_index.md#PACT-2018-P0008) Cimple：指令和内存级并行性：用于发现 ILP 和 MLP 的 DSL； [PACT-2019-P0016](../../10_corpus/PACT/id_index.md#PACT-2019-P0016) 数据记录编译器中的快速并行等价关系。
- 方法谱系：格式转换、分区、缓存使用。平台标签仍然是实现上下文，而不是主要主题边界。
- 更强的evidence rows：[PACT-2018-P0008](../../10_corpus/PACT/id_index.md#PACT-2018-P0008) (pdf_section)； [PACT-2019-P0016](../../10_corpus/PACT/id_index.md#PACT-2019-P0016) (pdf_section); [PACT-2025-P0025](../../10_corpus/PACT/id_index.md#PACT-2025-P0025) (pdf_section)。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF04](#PACT-SF04)。 DNN/GNN/LLM 张量执行

- 研究问题：提高模型执行、服务、训练和张量代码效率。
- 背景/当前状态：PACT 中的 `23` evidence rows，跨越 2018 年至 2025 年。代表行：[PACT-2018-P0002](../../10_corpus/PACT/id_index.md#PACT-2018-P0002) 用于深度神经网络的便携式自动数据量化器； [PACT-2019-P0006](../../10_corpus/PACT/id_index.md#PACT-2019-P0006) Acorns：用于加速具有输入稀疏性的深度神经网络的框架； [PACT-2019-P0023](../../10_corpus/PACT/id_index.md#PACT-2019-P0023) MASR：稀疏 RNN 的模块化加速器； [PACT-2020-P0042](../../10_corpus/PACT/id_index.md#PACT-2020-P0042) SparseRT：加速 GPU 上的非结构化稀疏性以进行深度学习推理。
- 方法谱系：稀疏性、量化、缓存、并行性。平台标签仍然是实现上下文，而不是主要主题边界。
- 更强的evidence rows：[PACT-2019-P0006](../../10_corpus/PACT/id_index.md#PACT-2019-P0006) (pdf_section)； [PACT-2019-P0023](../../10_corpus/PACT/id_index.md#PACT-2019-P0023) (pdf_section); [PACT-2025-P0013](../../10_corpus/PACT/id_index.md#PACT-2025-P0013) (pdf_section); [PACT-2025-P0017](../../10_corpus/PACT/id_index.md#PACT-2025-P0017) (pdf_section); [PACT-2025-P0021](../../10_corpus/PACT/id_index.md#PACT-2025-P0021) (pdf_section); [PACT-2025-P0022](../../10_corpus/PACT/id_index.md#PACT-2025-P0022) (pdf_section)。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF05](#PACT-SF05)。 PIM/CXL/近内存数据移动

- 研究问题：通过将计算或管理移至内存来降低带宽/容量成本。
- 背景/当前状态：PACT 中的 `10` evidence rows，跨越 2016 年至 2025 年。代表行：[PACT-2016-P0003](../../10_corpus/PACT/id_index.md#PACT-2016-P0003) 通过近数据处理加速链表遍历； [PACT-2016-P0042](../../10_corpus/PACT/id_index.md#PACT-2016-P0042) 具有内存处理功能的 GPU 架构的调度技术； [PACT-2021-P0013](../../10_corpus/PACT/id_index.md#PACT-2021-P0013) PIM-DL：通过数据布局优化增强 DNN 对内存中数字处理架构的推理； [PACT-2022-P0022](../../10_corpus/PACT/id_index.md#PACT-2022-P0022) GNNear：通过近内存处理加速图神经网络的全批量训练。
- 方法谱系：近内存处理、CXL 分层、负载重新平衡。平台标签仍然是实现上下文，而不是主要主题边界。
- 更有力的evidence rows：[PACT-2021-P0013](../../10_corpus/PACT/id_index.md#PACT-2021-P0013)（摘要）； [PACT-2025-P0016](../../10_corpus/PACT/id_index.md#PACT-2025-P0016) (pdf_section); [PACT-2025-P0023](../../10_corpus/PACT/id_index.md#PACT-2025-P0023) (pdf_section); [PACT-2025-P0034](../../10_corpus/PACT/id_index.md#PACT-2025-P0034) (pdf_section)。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF06](#PACT-SF06)。 FPGA/空间/异构映射

- 研究问题：将应用程序映射到具有资源和可移植性限制的空间或异构硬件。
- 背景/当前状态：PACT 中的 `20` evidence rows，跨越 2016 年至 2025 年。代表行：[PACT-2016-P0006](../../10_corpus/PACT/id_index.md#PACT-2016-P0006) 使用加速器对闪存进行大数据分析； [PACT-2016-P0039](../../10_corpus/PACT/id_index.md#PACT-2016-P0039) Rinnegan：异构架构中的高效资源利用； [PACT-2017-P0004](../../10_corpus/PACT/id_index.md#PACT-2017-P0004) 用于语音识别中声学评分的超低功耗硬件加速器； [PACT-2018-P0019](../../10_corpus/PACT/id_index.md#PACT-2018-P0019) 用于可编程加速器协同设计的混合优化/启发式指令调度。
- 方法谱系：HLS、源到源编译、加速器调度。平台标签仍然是实现上下文，而不是主要主题边界。
- 更强的evidence rows：[PACT-2019-P0011](../../10_corpus/PACT/id_index.md#PACT-2019-P0011) (pdf_section)； [PACT-2019-P0022](../../10_corpus/PACT/id_index.md#PACT-2019-P0022) (pdf_section); [PACT-2021-P0023](../../10_corpus/PACT/id_index.md#PACT-2021-P0023)（摘要）； [PACT-2025-P0005](../../10_corpus/PACT/id_index.md#PACT-2025-P0005)（摘要）； [PACT-2025-P0038](../../10_corpus/PACT/id_index.md#PACT-2025-P0038)（摘要）； [PACT-2025-P0039](../../10_corpus/PACT/id_index.md#PACT-2025-P0039) (pdf_section)。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF07](#PACT-SF07)。可靠性/安全性/加密加速

- 研究问题：加速或强化可靠性/安全/加密 workload。
- 背景/当前状态：PACT 中的 `4` evidence rows，跨越 2016 年至 2025 年。代表行：[PACT-2016-P0010](../../10_corpus/PACT/id_index.md#PACT-2016-P0010) 在低电源电压下应对 GPU 寄存器文件的可靠性挑战； [PACT-2023-P0029](../../10_corpus/PACT/id_index.md#PACT-2023-P0029) SpecCheck：系统识别gem5中易受攻击的瞬态执行的工具； [PACT-2024-P0023](../../10_corpus/PACT/id_index.md#PACT-2024-P0023) SZKP：用于零知识证明的可扩展加速器架构； [PACT-2025-P0036](../../10_corpus/PACT/id_index.md#PACT-2025-P0036) SCREME：弹性内存设计的可扩展框架。
- 方法谱系：专门加速、容错。平台标签仍然是实现上下文，而不是主要主题边界。
- 更有力的evidence rows：[PACT-2023-P0029](../../10_corpus/PACT/id_index.md#PACT-2023-P0029)（pdf_section）； [PACT-2024-P0023](../../10_corpus/PACT/id_index.md#PACT-2024-P0023)（摘要）； [PACT-2025-P0036](../../10_corpus/PACT/id_index.md#PACT-2025-P0036)（pdf_section）。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF08](#PACT-SF08)。领域 3D/视觉/机器人/基因组学/科学管道

- 研究问题：优化数据移动和延迟占主导地位的领域管道。
- 背景/当前状态：PACT 中的 `14` evidence rows，跨越 2016 年至 2025 年。代表行：[PACT-2016-P0001](../../10_corpus/PACT/id_index.md#PACT-2016-P0001) 用于加速 FPGA 上图像处理管道的 DSL 编译器； [PACT-2019-P0004](../../10_corpus/PACT/id_index.md#PACT-2019-P0004) 加速 DCA++（动态簇逼近）在 Summit 超级计算机上的科学应用； [PACT-2019-P0017](../../10_corpus/PACT/id_index.md#PACT-2019-P0017) FindeR：通过 ReRAM 技术加速基因组序列中基于 FM 索引的精确模式匹配； [PACT-2019-P0052](../../10_corpus/PACT/id_index.md#PACT-2019-P0052) SLAMBooster：用于密集 SLAM 近似的应用程序感知在线控制器。
- 方法谱系：DSL、近似、平铺、移动 GPU 映射。平台标签仍然是实现上下文，而不是主要主题边界。
- 更强的evidence rows：[PACT-2019-P0004](../../10_corpus/PACT/id_index.md#PACT-2019-P0004) (pdf_section)； [PACT-2019-P0017](../../10_corpus/PACT/id_index.md#PACT-2019-P0017) (pdf_section); [PACT-2019-P0052](../../10_corpus/PACT/id_index.md#PACT-2019-P0052) (full_pdf); [PACT-2020-P0001](../../10_corpus/PACT/id_index.md#PACT-2020-P0001)（摘要）； [PACT-2020-P0014](../../10_corpus/PACT/id_index.md#PACT-2020-P0014)（摘要）； [PACT-2020-P0031](../../10_corpus/PACT/id_index.md#PACT-2020-P0031)（摘要）。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF09](#PACT-SF09)。 benchmark/profiling/modeling

- 研究问题：使评估和性能预测更加可靠。
- 背景/当前状态：PACT 中的 `6` evidence rows，跨越 2016 年至 2022 年。代表行：[PACT-2016-P0016](../../10_corpus/PACT/id_index.md#PACT-2016-P0016) 将算法参数集成到 3D 场景理解中的基准测试和设计空间探索中； [PACT-2016-P0019](../../10_corpus/PACT/id_index.md#PACT-2016-P0019) 多核上数据并行程序的在线可扩展性表征； [PACT-2017-P0043](../../10_corpus/PACT/id_index.md#PACT-2017-P0043) 新兴大数据 workload 的代理基准； [PACT-2021-P0003](../../10_corpus/PACT/id_index.md#PACT-2021-P0003) AIBench 场景：场景蒸馏 AI 基准测试。
- 方法谱系：基准生成、建模、模拟。平台标签仍然是实现上下文，而不是主要主题边界。
- 更强的evidence rows：[PACT-2016-P0019](../../10_corpus/PACT/id_index.md#PACT-2016-P0019) (artifact_docs)； [PACT-2022-P0009](../../10_corpus/PACT/id_index.md#PACT-2022-P0009)（摘要）； [PACT-2022-P0032](../../10_corpus/PACT/id_index.md#PACT-2022-P0032)（摘要）。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

### [PACT-SF99](#PACT-SF99)。残余 PACT 分类

- 研究问题：行太宽，无法单独从标题/会话进行稳定的主题分配。
- 背景/当前状态：PACT 中的 `5` evidence rows，跨越 2016 年至 2025 年。代表行：[PACT-2016-P0008](../../10_corpus/PACT/id_index.md#PACT-2016-P0008) CAF：核心到核心通信加速框架； [PACT-2017-P0001](../../10_corpus/PACT/id_index.md#PACT-2017-P0001) 用于表演编排的 DSL； [PACT-2020-P0011](../../10_corpus/PACT/id_index.md#PACT-2020-P0011) 清除阴影：通过 HW/SW 协同设计恢复隐形推测执行的性能损失； [PACT-2022-P0031](../../10_corpus/PACT/id_index.md#PACT-2022-P0031) mu-grind：动态检测 HLS 生成的 RTL 的框架。
- 方法谱系：手动源丰富。平台标签仍然是实现上下文，而不是主要主题边界。
- 更有力的evidence rows：[PACT-2025-P0033](../../10_corpus/PACT/id_index.md#PACT-2025-P0033) (pdf_section)。
- 团队线索：仅限作者字符串；不存在任何entity disambiguation、排名或领导地位 claim。
- 开放问题：在全球分类法推广之前，仍然需要完整的 PDF 覆盖、artifact 重用、引文结构和cross-venue比较。

## 4. 发展趋势

- 编译器/自动调整仍然是长期运行的 PACT 系列，从早期的运行时/DSL/自动调整工作到 MLIR、学习和代理调度搜索。证据包括 [PACT-2016-P0004](../../10_corpus/PACT/id_index.md#PACT-2016-P0004)、[PACT-2017-P0012](../../10_corpus/PACT/id_index.md#PACT-2017-P0012)、[PACT-2021-P0014](../../10_corpus/PACT/id_index.md#PACT-2021-P0014)、[PACT-2023-P0017](../../10_corpus/PACT/id_index.md#PACT-2023-P0017)、[PACT-2025-P0003](../../10_corpus/PACT/id_index.md#PACT-2025-P0003) 和 [PACT-2025-P0024](../../10_corpus/PACT/id_index.md#PACT-2025-P0024)。
- 以内存为中心的工作从近数据/GPU-PIM 调度转向 DPIM 布局、PIM 框架、CXL 分层和 LLM KV-cache/PNM。证据包括 [PACT-2016-P0003](../../10_corpus/PACT/id_index.md#PACT-2016-P0003)、[PACT-2016-P0042](../../10_corpus/PACT/id_index.md#PACT-2016-P0042)、[PACT-2021-P0013](../../10_corpus/PACT/id_index.md#PACT-2021-P0013)、[PACT-2023-P0026](../../10_corpus/PACT/id_index.md#PACT-2023-P0026)、[PACT-2025-P0016](../../10_corpus/PACT/id_index.md#PACT-2025-P0016) 和 [PACT-2025-P0034](../../10_corpus/PACT/id_index.md#PACT-2025-P0034)。
- 稀疏/图形工作涵盖稀疏线性代数、图形加速器、GNN 缓存/使用和广义稀疏 ML 计算。证据包括 [PACT-2016-P0043](../../10_corpus/PACT/id_index.md#PACT-2016-P0043)、[PACT-2018-P0003](../../10_corpus/PACT/id_index.md#PACT-2018-P0003)、[PACT-2022-P0041](../../10_corpus/PACT/id_index.md#PACT-2022-P0041)、[PACT-2023-P0012](../../10_corpus/PACT/id_index.md#PACT-2023-P0012)、[PACT-2024-P0027](../../10_corpus/PACT/id_index.md#PACT-2024-P0027) 和 [PACT-2025-P0025](../../10_corpus/PACT/id_index.md#PACT-2025-P0025)。
- 视觉/机器人/3D 是一个反复出现但尚未稳定的 3DGS 子领域：SLAMBooster、Visual SLAM 近似、VoxelCache、SLIDEX 和一个移动 3DGS 行提供了跨年度证据。证据包括 [PACT-2019-P0052](../../10_corpus/PACT/id_index.md#PACT-2019-P0052)、[PACT-2020-P0001](../../10_corpus/PACT/id_index.md#PACT-2020-P0001)、[PACT-2022-P0049](../../10_corpus/PACT/id_index.md#PACT-2022-P0049)、[PACT-2023-P0027](../../10_corpus/PACT/id_index.md#PACT-2023-P0027) 和 [PACT-2025-P0027](../../10_corpus/PACT/id_index.md#PACT-2025-P0027)。
- 基准/分析/建模出现在 3D 场景 DSE、代理大数据基准、AIBench Scenario、BenchPress、NaviSim 和 XPU-Point 中。证据包括 [PACT-2016-P0016](../../10_corpus/PACT/id_index.md#PACT-2016-P0016)、[PACT-2017-P0043](../../10_corpus/PACT/id_index.md#PACT-2017-P0043)、[PACT-2021-P0003](../../10_corpus/PACT/id_index.md#PACT-2021-P0003)、[PACT-2022-P0009](../../10_corpus/PACT/id_index.md#PACT-2022-P0009)、[PACT-2022-P0032](../../10_corpus/PACT/id_index.md#PACT-2022-P0032) 和 [PACT-2025-P0039](../../10_corpus/PACT/id_index.md#PACT-2025-P0039)。

## 5. 方法变化

- 前面的行通常将问题描述为 GPU 调度、DSL/代码生成、近数据处理或基准测试。后面的行将编译器/运行时选择绑定到 LLM 服务、CXL、PIM、FPGA 模拟、移动 GPU 渲染和专门的加密/可靠性约束。
- 评估信号从广泛的加速和微基准测试转向特定于 workload 的指标：服务延迟、内存压力、缓存/KV 容量、图/GNN 吞吐量、SLAM/3D 映射质量和模拟器/样本选择代表性。
- 工具和 artifact 信号被记录为 `code_available_unchecked`、`artifact_mentioned` 或基准方法信号。没有运行或复制任何 artifact。

## 6. 缺失来源

- 统一官方 PACT 奖项注册表或 2016-2026 年最佳论文列表。
- 2016-2018 年和 2021 年的官方计划/会议页面。
- 所有已接受论文的批量摘要、关键字、artifact 徽章、代码 URL 和数据集 URL。
- PDF 级别读取所有 108 个evidence rows，对 3DGS、VoxelCache、SLAMBooster、PIM/CXL/KV-cache 和剩余 [PACT-SF99](#PACT-SF99) 行具有特殊优先级。
- 针对 MICRO、HPCA、ISCA、ASPLOS、PPoPP、SC 和 FPGA 系列venue的cross-venue主题矩阵。
