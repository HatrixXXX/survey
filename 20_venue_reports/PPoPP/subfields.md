# PPoPP 小领域深读

## 1. 范围与语料

- Venue：`PPoPP`
- 语料库：355 行主会论文，30 行奖项。
- 筛选矩阵：385 行。决策计数：`deep_read` 80、`index_only` 305、`needs_review` 0。
- 证据矩阵：50 个paper evidence rows。所有行都使用 `read_depth=abstract`，因为 ACM PDF 端点在此过程中不完全可读。
- 来源政策：SIGPLAN/Researchr 官方页面、ACM/DOI/Crossref/OpenAlex、DBLP 确切标题元数据、作者 PDF（如果有）以及本地语料库文件。

## 2. 小领域图谱

| subfield_id | 子领域 | evidence rows | 证据论文 ids |
|---|---|---:|---|
| <a id="PPOPP-SF01"></a>[PPOPP-SF01](#PPOPP-SF01) | 同步回收和持久数据结构 | 11 | [PPoPP-2016-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2016-P0023)|[PPoPP-2018-P0001](../../10_corpus/PPoPP/id_index.md#PPoPP-2018-P0001)|[PPoPP-2020-P0020](../../10_corpus/PPoPP/id_index.md#PPoPP-2020-P0020)|[PPoPP-2021-P0013](../../10_corpus/PPoPP/id_index.md#PPoPP-2021-P0013)|[PPoPP-2022-P0018](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0018)|[PPoPP-2022-P0019](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0019)|[PPoPP-2022-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0023)|[PPoPP-2022-P0029](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0029)|[PPoPP-2023-P0018](../../10_corpus/PPoPP/id_index.md#PPoPP-2023-P0018)|[PPoPP-2025-P0010](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0010)|[PPoPP-2026-P0001](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0001) |
| <a id="PPOPP-SF02"></a>[PPOPP-SF02](#PPOPP-SF02) | 任务编译器运行时和编程模型 | 5 | [PPoPP-2017-P0018](../../10_corpus/PPoPP/id_index.md#PPoPP-2017-P0018)|[PPoPP-2019-P0017](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0017)|[PPoPP-2022-P0016](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0016)|[PPoPP-2023-P0015](../../10_corpus/PPoPP/id_index.md#PPoPP-2023-P0015)|[PPoPP-2026-P0005](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0005) |
| <a id="PPOPP-SF03"></a>[PPOPP-SF03](#PPOPP-SF03) | 不规则图搜索和硬件单元映射 | 7 | [PPoPP-2016-P0011](../../10_corpus/PPoPP/id_index.md#PPoPP-2016-P0011)|[PPoPP-2017-P0017](../../10_corpus/PPoPP/id_index.md#PPoPP-2017-P0017)|[PPoPP-2019-P0016](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0016)|[PPoPP-2022-P0006](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0006)|[PPoPP-2023-P0005](../../10_corpus/PPoPP/id_index.md#PPoPP-2023-P0005)|[PPoPP-2025-P0004](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0004)|[PPoPP-2026-P0009](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0009) |
| <a id="PPOPP-SF04"></a>[PPOPP-SF04](#PPOPP-SF04) | 张量核稀疏模板和科学内核 | 9 | [PPoPP-2019-P0018](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0018)|[PPoPP-2019-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0023)|[PPoPP-2021-P0020](../../10_corpus/PPoPP/id_index.md#PPoPP-2021-P0020)|[PPoPP-2022-P0008](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0008)|[PPoPP-2024-P0025](../../10_corpus/PPoPP/id_index.md#PPoPP-2024-P0025)|[PPoPP-2025-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0023)|[PPoPP-2025-P0025](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0025)|[PPoPP-2026-P0024](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0024)|[PPoPP-2026-P0028](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0028) |
| <a id="PPOPP-SF05"></a>[PPOPP-SF05](#PPOPP-SF05) | 分布式培训通信和诊断 | 5 | [PPoPP-2021-P0005](../../10_corpus/PPoPP/id_index.md#PPoPP-2021-P0005)|[PPoPP-2022-P0010](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0010)|[PPoPP-2022-P0011](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0011)|[PPoPP-2026-P0029](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0029)|[PPoPP-2026-P0032](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0032) |
| <a id="PPOPP-SF06"></a>[PPOPP-SF06](#PPOPP-SF06) | LLM 推理状态和注意力内核 | 6 | [PPoPP-2021-P0028](../../10_corpus/PPoPP/id_index.md#PPoPP-2021-P0028)|[PPoPP-2025-P0017](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0017)|[PPoPP-2026-P0023](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0023)|[PPoPP-2026-P0038](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0038)|[PPoPP-2026-P0045](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0045)|[PPoPP-2026-P0047](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0047) |
| <a id="PPOPP-SF07"></a>[PPOPP-SF07](#PPOPP-SF07) | 分析调试能量和证据工具 | 6 | [PPoPP-2018-P0012](../../10_corpus/PPoPP/id_index.md#PPoPP-2018-P0012)|[PPoPP-2019-P0015](../../10_corpus/PPoPP/id_index.md#PPoPP-2019-P0015)|[PPoPP-2022-P0017](../../10_corpus/PPoPP/id_index.md#PPoPP-2022-P0017)|[PPoPP-2025-P0005](../../10_corpus/PPoPP/id_index.md#PPoPP-2025-P0005)|[PPoPP-2026-P0013](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0013)|[PPoPP-2026-P0037](../../10_corpus/PPoPP/id_index.md#PPoPP-2026-P0037) |
| <a id="PPOPP-SF99"></a>[PPOPP-SF99](#PPOPP-SF99) | 领域模拟 artifact 的边界奖励证据 | 1 | [PPoPP-2023-P0014](../../10_corpus/PPoPP/id_index.md#PPoPP-2023-P0014) |

## 3. 小领域深读

### [PPOPP-SF01](#PPOPP-SF01) 同步回收和持久数据结构
研究问题是多核共享对象在高并发下如何兼顾吞吐、进展保证、内存回收和持久化正确性。DomLock、Interval-Based Memory Reclamation、Non-Blocking Interpolation Search Trees、NBR、FliT、Software Combining in Persistence、Lock-Free Locks、PathCAS、Block-STM、Publish on Ping 和 Binary Compatible Critical Section Delegation 构成了从锁粒度、reclamation、durable algorithms 到动态对象/委派的路线。趋势判断基于 2016、2018、2020-2023、2025、2026 多年论文。

Team signal 只写作者字符串线索：Trevor Brown、Dan Alistarh、Guy Blelloch、Naama Ben-David、Ajay Singh 等在并发/持久化对象中多次出现；未做entity disambiguation或排名。Open questions：哪些 artifact 真正被后续并发数据结构论文复用，仍需 artifact/code audit。

### [PPOPP-SF02](#PPOPP-SF02) 任务编译器/运行时和编程模型
核心问题是并行结构如何进入编译器 IR、runtime 和 scheduler。Tapir 把 fork-join 并行嵌入 LLVM IR，granularity control 处理任务粒度，OpenCilk 给出模块化 task-parallel infrastructure，2026 oversubscription scheduler 把多 runtime/多进程协调作为前沿问题。SMT verification 论文作为 method_bridge，说明并发程序验证也依赖对线程干扰关系的建模。

跨会议 hook 是编译器/runtime 和体系结构共同定义可调度的并行粒度。OpenCilk 和 Tapir 的直接实现继承关系需要专门源检查，本轮只写 thematic lineage。

### [PPOPP-SF03](#PPOPP-SF03) 不规则图、搜索和树 workload 映射
这一线处理 graph analytics、GNN、neighbor search、Barnes-Hut、parallel biconnectivity、dynamic trees 这类不规则负载的并行度和访存问题。Gunrock/Groute 是 GPU graph runtime 的早期锚点；Gswitch 处理 GPU graph autotuning；RTNN/RT-BarnesHut 把空间查询映射到 ray-tracing hardware；parallel biconnectivity 和 UFO Trees 体现算法侧的 work/space efficiency。

它和 3DGS/neural rendering 的 hook 不是同一任务本身，而是不规则空间查询、图遍历、树结构和固定功能单元复用的共性瓶颈。

### [PPOPP-SF04](#PPOPP-SF04) 矩阵/张量单元稀疏和科学内核重构
研究问题是 SpMM、stencil、QGNN、BFS、MD、sparse direct solver 等非标准 GEMM 负载如何使用矩阵/张量硬件。Adaptive Sparse Tiling、EGEMM-TC、QGTC、ConvStencil、FlashSparse、BerryBees、HierCut、Trojan Horse 展示了从稀疏 tiling、扩展精度 Tensor Core、stencil-to-matmul、冗余减少、bit Tensor Core 到 GPU cluster batching 的路线。趋势由 2019-2026 多篇证据支撑：PPoPP 越来越常把算法结构重排成矩阵/张量硬件更容易执行的形式。

### [PPOPP-SF05](#PPOPP-SF05) 分布式训练通信和诊断
这一线从 collective algorithm synthesis、sparse allreduce、BAGUALU 到 COCCL/CCL-D，关注大模型训练里的通信、压缩、checkpoint 和慢节点/挂起诊断。这里不能把 “ML systems” 当 topic；主 topic 是 collective 生成、压缩通信库和训练异常诊断。与 MLSys/SC/HPCA 的 hook 是通信库、拓扑、压缩和训练运行时的接口。

### [PPOPP-SF06](#PPOPP-SF06) LLM 推理状态和注意力内核
TurboTransformers 是 Transformer serving 的较早锚点。MARLIN、JanusQuant、Laser、FlashAttention-T、MetaAttention 体现 2025-2026 的前沿：低比特权重/KV、attention tensorization、multi-SLO serving、跨后端 attention framework。由于这些论文很新，影响力不能写成已确定，只能记录 frontier evidence 和 `impact_unverified`。

### [PPOPP-SF07](#PPOPP-SF07) 分析调试能量和证据工具
Featherlight、Lightweight HTM Profiling、PerFlow、EVeREST、PRISM、BEEMS 说明 PPoPP 持续出现“测量/诊断/运行时控制/数据压缩”论文。它们给硬件加速研究的价值在于 workload evidence：定位 false sharing、HTM 行为、parallel performance variance、GPU energy、progressive data retrieval 或 machine-vision memory behavior。citation、artifact/code 复用和产业采纳均未完整审计。

### [PPOPP-SF99](#PPOPP-SF99) 领域仿真 artifact 的边界奖励证据
BioDynaMo 是 2023 Best Artifact，保留为 boundary evidence。它说明 PPoPP 会接收高性能 domain simulation artifact，但本轮不把单篇 agent-based simulation artifact 提升成独立趋势。

## 4. 发展趋势

- Irregular workload mapping 从 GPU graph runtime 走向专门负载/硬件单元：Gunrock、Groute、Gswitch、RTNN、RT-BarnesHut、UFO Trees。
- Task runtime 从 IR/粒度抽象走向多 runtime 协调：Tapir、granularity control、OpenCilk、2026 oversubscription scheduling。
- Matrix/Tensor-unit reformulation 从 sparse tiling 和 GEMM 扩展走向 stencil、QGNN、BFS、MD 和 sparse solver：Adaptive Sparse Tiling、EGEMM-TC、QGTC、ConvStencil、FlashSparse、BerryBees、HierCut、Trojan Horse。
- DNN/LLM 系统线从 Transformer serving 和 distributed training 走向 LLM-specific communication、KV、attention 和 serving scheduler：TurboTransformers、BAGUALU、MARLIN、COCCL、JanusQuant、Laser、FlashAttention-T、MetaAttention。
- Evidence tooling 从单点 profiling 走向 runtime diagnostics、energy control 和 compression：Featherlight、TxSampler、PerFlow、EVeREST、PRISM、BEEMS、CCL-D。

## 5. 方法变化

第二波修正了旧奖项表中的 2019/2020 缺口和 2021/2022/2023 官方奖项冲突；补齐了 residual DOI/title/author/PDF metadata。screening 决策只使用 `deep_read` 和 `index_only`，没有 `needs_review`，也没有 `exclude_non_main`，因为 corpus 已过滤为主会论文。

## 6. 缺失来源

- Full PDF所有 deep_read 行的文本/节级证据。
- artifact/代码可运行状态以及最佳 artifact 和 `artifact_mentioned` 行的重用证据。
- 基准标准化和行业/工具链采用来源。
- 超出 OpenAlex 计数的引文结构审核。
- 实体消除歧义的作者/隶属关系/团队表。
