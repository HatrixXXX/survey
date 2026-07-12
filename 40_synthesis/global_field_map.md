# 硬件加速研究课题关系图谱

日期：2026-06-25  

## 0. 读法和证据状态

本图谱是全局 seed map，用于给后续 venue reports 和 subfield reports 提供统一标注入口。它不把“体系结构、FPGA、EDA、IC、ML systems、HPC、机器人”写成主分类；这些词只用于定位会议来源、平台上下文或应用边界。主分类对象是更小的研究问题：某类负载在某个瓶颈上形成的稳定问题、对应机制、映射方式和评价口径。

证据状态分三类：

| 状态 | 含义 | 本文件用法 |
|---|---|---|
| `project_rule` | 来自项目控制文件的已确认规则 | 可作为后续 worker 的约束 |
| `seed_from_taxonomy` | 来自 `TOPIC_TAXONOMY.md` 的 seed topic | 可用于初始标注，但不能当成稳定领域结论 |
| `hypothesis` | 从 seed topic 之间的重叠关系推出 | 必须由 venue reports 或 subfield reports 复核 |

本文件不列代表论文、作者、奖项、DOI 或团队排名。当前仓库还没有 venue reports 和 subfield reports，因此所有研究关系都是 `seed_from_taxonomy` 或 `hypothesis`，没有 `stable` 关系。

## 1. 六个分析层，不混成一棵树

后续所有聚类建议按六层拆开记录。一个论文或 topic 可以同时命中多层。

| 层 | 记录什么 | 示例标签 |
|---|---|---|
| 负载 | 计算对象或系统对象 | `transformer_decode`、`3dgs_rendering`、`robot_edge_control`、`graph_spmm` |
| 瓶颈 | 主要受限环节 | `kv_cache_capacity`、`memory_bandwidth`、`sorting_visibility`、`tail_latency`、`noc_contention` |
| 加速机制 | 具体减少开销的手段 | `tiling`、`kernel_fusion`、`low_precision`、`zero_skipping`、`runtime_scheduling` |
| 平台映射 | 落到哪类执行载体或存储层次 | `gpu_kernel`、`fpga_dataflow`、`asic_systolic`、`near_memory`、`chiplet_interconnect` |
| 编译/runtime | 配置、生成、调度和适配 | `hls_schedule`、`dsl_codegen`、`autotuning`、`dynamic_batching`、`memory_planning` |
| 评价方法 | 如何证明有效 | `roofline`、`memory_traffic_model`、`ppa`、`tokens_per_second`、`fps`、`tail_latency` |

这样拆分的原因很直接：同一个负载可能有多个瓶颈；同一个机制可以服务多个负载；同一个平台也可以承载不同技术路线。如果把它们压成单一 topic tree，后续 venue worker 很容易把论文标成“FPGA”或“LLM 加速”，但漏掉真正可复核的问题关系。

## 2. Topic 节点：按研究问题命名

下表把当前 `TOPIC_TAXONOMY.md` 的 12 个 seed topic 放进全局图谱。这里保留 topic id，方便后续 claim ledger、venue reports 和 papers.csv 对齐。

| topic id | 研究课题节点 | 主负载或系统 | 主瓶颈 | 典型机制 | 评价入口 | 状态 |
|---|---|---|---|---|---|---|
| T01 | Transformer 推理的存储与状态管理 | LLM/Transformer inference | KV cache、权重和中间状态的容量、带宽、时延 | 缓存分层、压缩、低精度存储、prefetch、数据搬运优化 | tokens/s、首 token 时延、decode 时延、显存占用 | `seed_from_taxonomy` |
| T02 | Transformer 算子、kernel 融合与低精度执行 | GEMM、attention、norm、MoE routing | 算子利用率、访存开销、layout 和 dispatch 开销 | kernel fusion、tiling、mixed precision、quantization、persistent kernel | 算子吞吐、end-to-end latency、roofline、occupancy | `seed_from_taxonomy` |
| T03 | 3DGS、神经渲染与 3D 视觉加速 | 3DGS、NeRF、3D vision pipeline | 渲染、排序、采样、体积积分、梯度计算 | 空间分块、排序优化、专用 pipeline、稀疏结构、近似表示 | FPS、训练时间、渲染时延、质量指标、能耗 | `seed_from_taxonomy` |
| T04 | 机器人和具身智能的端侧实时计算 | sensor-policy-control loop、VLA、world model | 低 batch、低时延、功耗、确定性和 tail latency | pipeline scheduling、heterogeneous execution、operator placement、model compression | end-to-end latency、tail latency、control frequency、success rate | `seed_from_taxonomy` |
| T05 | 低精度、稀疏和近似计算的硬件-算法协同 | DNN、Transformer、稀疏/近似负载 | 数值质量与计算/搬运成本之间的冲突 | low precision、quantization、sparsity、zero skipping、近似单元 | accuracy/quality drop、speedup、energy、area、compression ratio | `seed_from_taxonomy` |
| T06 | 空间数据流架构与片上存储组织 | systolic、streaming、spatial、CGRA、定制数据流 | PE、buffer、NoC 和 DMA 的共同利用率 | data reuse、spatial mapping、tiling、double buffering、banking | utilization、memory traffic、NoC contention、area/frequency | `seed_from_taxonomy` |
| T07 | 编译、HLS、DSL 与自动映射 | 算法、计算图、DSL 到硬件或 kernel | 可移植性、QoR、搜索成本、资源约束 | schedule search、loop transform、memory planning、resource binding、codegen | QoR、compile/search time、Pareto frontier、resource utilization | `seed_from_taxonomy` |
| T08 | Runtime 调度、autotuning 与动态适配 | dynamic shape、serving、异构执行 | 负载波动、多 kernel 组合、配置选择和调度稳定性 | offline tuning、online adaptation、cost model、dynamic batching、queue scheduling | steady-state latency、tail latency、throughput、robustness | `seed_from_taxonomy` |
| T09 | 不规则、动态图和稀疏控制流加速 | graph traversal、SpMM/SpMV、routing、动态任务 | 负载不均、分支、随机访存、格式转换 | workload partitioning、hardware queue、prefetch、format transform、dynamic scheduling | load balance、memory divergence、latency distribution、scalability | `seed_from_taxonomy` |
| T10 | 存储中心、近存和互连受限计算 | HBM、PIM/near-memory、chiplet、NoC | 片外带宽、数据搬运能耗、互连通信和容量 | near-data processing、communication avoidance、compression、prefetch、placement | bandwidth utilization、energy/byte、NoC contention、capacity hit rate | `seed_from_taxonomy` |
| T11 | Benchmark、profiling 与性能模型 | benchmark、profiler、PMU、性能模型 | 结果可解释性、可复现性和 baseline 公平性 | roofline、traffic model、microbenchmark、artifact evaluation | coverage、measurement accuracy、repeatability、ablation | `seed_from_taxonomy` |
| T12 | EDA、物理约束与可实现性闭环 | RTL/HLS flow、synthesis、P&R、verification | 面积、频率、功耗、布线、时序和验证闭环 | physical-aware mapping、timing-aware scheduling、DSE pruning、verification-aware design | post-synthesis/post-layout PPA、timing slack、resource utilization | `seed_from_taxonomy` |

## 3. 关系图：从负载到证据闭环

下面是当前 seed map 的主干。箭头表示“需要一起复核的关系”，不是已经稳定的历史演化结论。

```text
负载层
  T01 Transformer state/memory
  T02 Transformer kernels
  T03 3DGS/neural rendering
  T04 embodied edge compute
  T09 irregular graph/sparse control

瓶颈层
  memory/capacity/bandwidth: T01 -> T10
  operator utilization/layout: T02 -> T06
  visibility/sorting/sampling: T03 -> T06/T08
  realtime/tail latency: T04 -> T08/T11
  load imbalance/random access: T09 -> T10/T11

机制层
  low precision/sparsity/approximation: T05 <-> T02/T03/T09
  spatial dataflow/buffering: T06 <-> T02/T03/T10/T12
  compiler/HLS/DSL mapping: T07 <-> T06/T12
  runtime/autotuning/adaptation: T08 <-> T01/T04/T07/T11

证据层
  measurement/model/artifact: T11 -> all topics
  physical closure/PPA: T12 -> T06/T07 and accelerator implementation claims
```

## 4. 关系矩阵

### 4.1 已由项目规则支撑的关系

这些关系来自项目章程、source policy、venue schema 或 taxonomy 使用原则。它们是工作规则，不是论文趋势。

| 关系 | 说明 | 证据状态 |
|---|---|---|
| 大领域标签不能作为主分类边界 | FPGA、EDA、IC、ML systems、HPC、机器人等只作为检索入口、会议来源和上下文边界 | `project_rule` |
| 正式报告必须配套 claim ledger | 报告事实、趋势判断和综合判断必须能回到 claim ledger | `project_rule` |
| topic 标注要拆成研究课题、机制、谱系、评价方法 | venue worker 不能只填一个 topic 名 | `project_rule` |
| 代表论文不能按名气或引用量直接排序 | 候选必须有来源、topic 归属和入选理由 | `project_rule` |
| 当前 taxonomy 没有 stable topic | 所有 topic 都要等待 venue/subfield reports 复核 | `project_rule` |

### 4.2 来自 taxonomy seed 的 topic 相邻关系

这些关系可用于后续聚类，但只能标成初始假设。

| 关系 | 为什么相邻 | 需要后续复核的问题 | 证据状态 |
|---|---|---|---|
| T01 <-> T02 | Transformer 推理同时受状态存储和算子执行影响 | KV/state 管理是否应和 serving runtime 分拆；attention 是否应独立成 topic | `seed_from_taxonomy` |
| T01 <-> T08 | KV cache、batching、paging 和 memory planning 可能由 runtime 共同管理 | 相关论文主要出现在 architecture、MLSys 还是 systems venue | `seed_from_taxonomy` |
| T01 <-> T10 | LLM state 和 weight streaming 常指向容量、带宽和数据搬运瓶颈 | 哪些论文能证明瓶颈确实由数据搬运主导 | `seed_from_taxonomy` |
| T02 <-> T05 | 低精度、量化和稀疏经常用于提升 Transformer 算子效率 | 低精度应作为机制保留，还是形成独立 topic | `seed_from_taxonomy` |
| T02 <-> T07 | 算子融合、layout 和 tiling 既可手写 kernel，也可由 compiler 生成 | 编译器生成 kernel 和算子库优化是否属于同一论文群 | `seed_from_taxonomy` |
| T03 <-> T04 | 3D 视觉负载可能进入机器人端侧感知和控制链路 | 3DGS/NeRF 加速与机器人实时计算是否已有稳定交集 | `seed_from_taxonomy` |
| T03 <-> T06 | 渲染、排序和稀疏 primitive pipeline 可能映射到数据流或专用 pipeline | 3DGS 硬件加速是否已有稳定架构路线 | `seed_from_taxonomy` |
| T03 <-> T11 | 3DGS/NeRF 需要同时报告速度、质量、训练时间和端侧约束 | 图像质量指标和硬件 PPA 指标如何同时记录 | `seed_from_taxonomy` |
| T04 <-> T08 | 机器人端侧系统依赖调度、异构执行和实时 runtime | tail latency、control frequency 和任务成功率如何联合评价 | `seed_from_taxonomy` |
| T05 <-> T06 | 低精度/稀疏会改变 PE、buffer 和数据流设计 | 稀疏索引压缩和低精度格式是否应分拆 | `seed_from_taxonomy` |
| T06 <-> T07 | 空间映射通常需要 HLS、DSL、generator 或 schedule search 支持 | HLS 方法学和 DNN compiler 是否应分开 | `seed_from_taxonomy` |
| T06 <-> T10 | 片上存储组织和近存/互连受限计算都围绕数据搬运 | PIM、chiplet 和 memory hierarchy 是否应拆成独立 topic | `seed_from_taxonomy` |
| T07 <-> T08 | 编译期 schedule、离线 autotune 和在线 runtime 是连续谱系 | autotuning 是机制、runtime 子题，还是独立 topic | `seed_from_taxonomy` |
| T07 <-> T12 | 自动映射需要最终落到 HLS/RTL、P&R、时序和 PPA 约束 | 工具论文和架构论文的评价口径如何统一 | `seed_from_taxonomy` |
| T09 <-> T05 | 图计算、稀疏矩阵和 DNN sparsity 都涉及稀疏表示 | 图计算和 DNN 稀疏是否共享足够机制 | `seed_from_taxonomy` |
| T09 <-> T10 | 不规则访存和动态任务经常触发 memory-centric 设计 | near-memory 是否真正缓解随机访存瓶颈 | `seed_from_taxonomy` |
| T11 <-> all | benchmark/profiling 是所有 topic 的证据标准 | 各 topic 应使用哪些最低评价字段 | `project_rule` + `seed_from_taxonomy` |
| T12 <-> implementation claims | 真实实现、PPA 和物理闭环决定架构结论的可信度 | 模拟、post-synthesis、post-layout 和芯片实测如何分级 | `seed_from_taxonomy` |

### 4.3 待验证假设

这些是假设，不应在后续报告中直接改写成确定结论。

| 假设 | 为什么值得查 | 复核入口 |
|---|---|---|
| LLM 推理可能需要拆成 `kv_cache_memory`、`weight_streaming`、`attention_kernel`、`serving_runtime` 四个聚类 | T01 和 T02 当前边界较宽，且 memory、kernel、runtime 的评价指标不同 | MLSys、ASPLOS、ISCA、MICRO、HPCA venue reports |
| 3DGS 加速可能会形成独立 topic，但也可能只是 3D 视觉/图形 pipeline 的新负载 | T03 与用户方向相关，但 taxonomy 明确不能绕过证据要求 | 3DGS subfield report，必要时补图形学 venue 或作者项目来源 |
| 低精度和稀疏应拆开，而近似计算可能只作为机制标签 | T05 覆盖的数值判据、硬件结构和评价指标可能不同 | MICRO、ISCA、HPCA、ISSCC、VLSI、MLSys |
| HLS/DSL 和 DNN compiler 可能需要两套标签 | HLS 面向硬件生成和资源绑定，DNN compiler 更常处理图优化和 kernel 调度 | FPGA、FCCM、DAC、ICCAD、ASPLOS、PACT |
| Runtime/autotuning 可能跨越编译器、serving 系统和嵌入式实时系统 | T08 同时连接 T01、T04、T07 和 T11 | MLSys、ASPLOS、SC、PACT、robot edge subfield |
| Benchmark/profiling 应作为独立方法 topic 保留 | T11 不加速负载，但决定所有 speedup、PPA 和趋势判断的可信度 | METHOD-002、METHOD-003、所有 venue reports |
| EDA/physical closure 应作为架构可信度过滤器，而不是只作为 EDA 子领域 | T12 决定模拟结论和可实现芯片/FPGA 结果之间的距离 | DAC、ICCAD、FPGA、FCCM、ISSCC、VLSI |

## 5. 给 venue reports 的聚类标签建议

Venue worker 标注论文时，建议先填开放标签，再在一批论文上归纳 `topic_cluster_label`。下面标签只是 seed，不要求一次性固定。

### 5.1 负载标签

| 标签 | 对应 topic | 说明 |
|---|---|---|
| `transformer_decode` | T01/T02/T08 | decode 阶段的状态、算子和 serving 行为 |
| `kv_cache_memory` | T01/T10 | KV cache 的容量、带宽、压缩、paging 或 eviction |
| `attention_kernel` | T02/T07 | attention、softmax、layout、tiling、fusion |
| `moe_routing` | T02/T09/T08 | MoE dispatch/combine、load balance、动态 routing |
| `3dgs_rendering` | T03/T06 | Gaussian primitive、visibility、sorting、rasterization-like pipeline |
| `nerf_sampling` | T03/T05 | ray marching、采样、体积积分、近似表示 |
| `robot_edge_loop` | T04/T08 | sensor-policy-control 的端侧闭环 |
| `graph_sparse_compute` | T09/T10 | graph traversal、SpMM/SpMV、gather/scatter |
| `eda_physical_closure` | T12/T07 | timing、P&R、post-synthesis/post-layout 约束 |

### 5.2 瓶颈标签

| 标签 | 建议使用场景 |
|---|---|
| `memory_capacity` | 显存、HBM、cache、on-chip buffer 容量限制 |
| `memory_bandwidth` | 片外带宽、memory traffic 或 weight/state streaming 主导 |
| `data_movement_energy` | 论文以能耗或 energy/byte 为核心论点 |
| `operator_utilization` | PE、tensor core、SIMD、array 或 pipeline 利用率不足 |
| `layout_overhead` | layout transform、format conversion、dispatch/combine 影响性能 |
| `load_imbalance` | 稀疏、不规则、MoE 或动态图导致 work imbalance |
| `tail_latency` | serving 或实时系统关注 p95/p99 或 deadline miss |
| `physical_timing` | 时序、频率、布线或面积成为可实现性瓶颈 |
| `evaluation_gap` | 论文主要讨论 benchmark、公平比较、profiling 或模型解释 |

### 5.3 加速机制标签

| 标签 | 说明 |
|---|---|
| `tiling` | 多级 tile、block、warp 或 PE array 映射 |
| `data_reuse` | reuse pattern、scratchpad、buffer hierarchy |
| `kernel_fusion` | 融合多个算子、减少启动或中间数据搬运 |
| `layout_transform` | tensor/layout/format 转换或避免转换 |
| `streaming_pipeline` | pipeline 化的数据流或 producer-consumer 执行 |
| `double_buffering` | 计算和搬运重叠 |
| `low_precision` | 低比特、mixed precision、block floating point |
| `quantization` | 量化格式、校准、质量-性能曲线 |
| `sparsity` | structured/unstructured sparsity |
| `compression` | 权重、激活、KV、稀疏索引或数据流压缩 |
| `zero_skipping` | 跳零或动态跳过无效计算 |
| `runtime_scheduling` | queue、batching、placement、work stealing |
| `autotuning` | offline/online tuning、cost model、配置搜索 |
| `memory_planning` | buffer allocation、lifetime、paging、eviction |
| `near_memory` | PIM、near-data 或 memory-side compute |
| `interconnect_aware_mapping` | NoC、chiplet、communication-aware placement |
| `physical_aware_mapping` | floorplan、timing、routing、PPA 约束进入映射 |

### 5.4 平台映射标签

| 标签 | 使用原则 |
|---|---|
| `gpu_kernel` | 只作为平台载体，必须同时写清负载和瓶颈 |
| `fpga_dataflow` | 只作为实现载体，必须说明 streaming、buffer、HLS/RTL 或 timing 约束 |
| `asic_accelerator` | 需要区分模拟、post-layout、silicon measurement |
| `npu_tensor_array` | 需要说明 array、precision、memory hierarchy 和 workload |
| `near_memory_platform` | 需要说明 memory-side execution 对哪个瓶颈有效 |
| `chiplet_interconnect` | 需要说明 NoC/interposer/link 带来的通信瓶颈和评价口径 |
| `edge_soc` | 需要说明功耗、热、实时性或端侧内存约束 |

### 5.5 编译/runtime 标签

| 标签 | 使用原则 |
|---|---|
| `hls_schedule` | loop pipeline、unroll、resource binding、pragma 或 HLS QoR |
| `dsl_codegen` | DSL、schedule language、generator、template codegen |
| `graph_compiler` | graph rewrite、operator fusion、memory planning |
| `cost_model` | 性能、PPA、搜索或 placement 的预测模型 |
| `design_space_exploration` | DSE、Pareto frontier、search cost |
| `dynamic_batching` | serving 或 runtime 中的 batch/queue 适配 |
| `heterogeneous_placement` | CPU/GPU/NPU/FPGA/SoC 间 placement |
| `profiling_feedback` | profiling 驱动优化或在线适配 |

### 5.6 评价标签

| 标签 | 使用原则 |
|---|---|
| `end_to_end_latency` | 端到端系统时延，必须记录负载和 baseline |
| `tail_latency` | p95/p99、deadline miss 或实时性 |
| `throughput` | 样本、请求、token、frame 或 task throughput |
| `tokens_per_second` | LLM decode 或 serving |
| `fps` | rendering、vision 或 robot perception |
| `energy_efficiency` | TOPS/W、J/token、J/frame、energy/op 等 |
| `power` | 平均、峰值或 thermal envelope |
| `area` | FPGA resource、ASIC area 或 normalized area |
| `frequency` | timing closure 和 clock rate |
| `roofline` | 算力-带宽上限解释 |
| `memory_traffic_model` | byte traffic、reuse、bandwidth utilization |
| `microbenchmark` | 单算子、单 kernel、单模块测试 |
| `application_benchmark` | 应用级 benchmark 或 end-to-end workload |
| `ablation` | 机制贡献拆分 |
| `artifact_available` | 代码、数据、artifact badge 或可复现实验 |
| `post_synthesis` | 综合后结果 |
| `post_layout` | 布局布线后结果 |

## 6. 后续报告如何复核本图谱

1. 每个 venue report 至少记录 `topic_primary`、`topic_secondary`、`topic_tags`、`topic_cluster_label`、`topic_cluster_status` 和 `topic_notes`。
2. 一个 seed topic 只有在至少两个 venue 或一个 venue 的多年论文中反复出现，且核心问题、技术对象和评价方法相对稳定后，才可建议从 `seed` 升级为 `provisional`。
3. 如果一个 topic 内部出现两组互不共享评价方法或技术对象的论文，标记为 `split_candidate`。T02、T05、T10 当前尤其需要注意。
4. 如果两个 topic 经常由同一批论文同时覆盖，且只是机制或平台不同，标记为 `merge_candidate`。T07/T08、T06/T10 当前尤其需要注意。
5. 代表论文、团队、奖项和趋势判断必须进入对应 report 的 claim ledger。本文件的 seed 关系不能替代论文级来源。

## 7. Missing Sources

- 缺少目标会议 2016-2026 年 accepted papers、awards、artifact 和 proceedings 数据。
- 缺少每个 topic 的代表论文集合、工具链、benchmark、代码和团队来源。
- 缺少跨 venue 的趋势证据链，尤其是 LLM inference、3DGS acceleration、runtime/autotuning、memory-centric computing、HLS/DSL 和 physical closure。
- 缺少统一的 benchmark/profiling 报告来校准不同 topic 的评价口径。
