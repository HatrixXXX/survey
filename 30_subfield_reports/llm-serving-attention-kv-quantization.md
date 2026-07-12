# LLM服务状态； KV/缓存；注意力;令牌内存瓶颈

<a id="FIELD-LLM-SERVING-001-C029"></a>
对应 global_subfield_id：[GSF-01](../40_synthesis/third_wave_field_synthesis.md#GSF-01)  
证据规则：本报告只使用 cross-venue inventory、third-wave index、second-wave venue evidence matrix、claim ledger、实体/影响力审计和 workload/artifact inventory。正文中的论文、系统、趋势、团队和 artifact 判断均回到本报告 claim ledger 或 paper evidence matrix；未运行的 artifact 不写为已复现。<a id="FIELD-LLM-SERVING-001-C031"></a>[FIELD-LLM-SERVING-001-C031](#FIELD-LLM-SERVING-001-C031)

## 研究背景

这个领域从跨会议 evidence 中浮现，不是因为 “LLM 很热”，而是因为 serving 的计算形态和传统 DNN 前向传播不同。Prefill 阶段更接近大块矩阵和 attention tile，decode 阶段反复读取权重与历史 K/V，batch 小且受 latency SLO 限制。项目 workload inventory 因此把 LLM serving 的核心指标拆成 TTFT、TPOT、throughput、goodput under SLO、KV peak memory、KV bytes/token、prefix-cache hit ratio 和 energy/token。<a id="FIELD-LLM-SERVING-001-C004"></a>[FIELD-LLM-SERVING-001-C004](#FIELD-LLM-SERVING-001-C004)<a id="FIELD-LLM-SERVING-001-C005"></a>[FIELD-LLM-SERVING-001-C005](#FIELD-LLM-SERVING-001-C005)

跨 venue synthesis 的趋势句也指向同一个变量变化：LLM acceleration 正从泛化 Transformer kernel 走向 state/cache/serving 问题，包括 KV residency、prefill/decode overlap、sparse attention、long-context memory 和 token-level silicon metrics。<a id="FIELD-LLM-SERVING-001-C003"></a>[FIELD-LLM-SERVING-001-C003](#FIELD-LLM-SERVING-001-C003) 这里的 “frontier-heavy” 很关键：2025-2026 rows 很多，说明方向活跃，但不能把近期题名、项目页或厂商 slides 直接写成长期影响。<a id="FIELD-LLM-SERVING-001-C001"></a>[FIELD-LLM-SERVING-001-C001](#FIELD-LLM-SERVING-001-C001)[FIELD-LLM-SERVING-001-C031](#FIELD-LLM-SERVING-001-C031)

## 核心问题

1. Prefill/decode 不对称：prefill 更像 compute/attention-tile 问题，decode 更像 weight/KV bandwidth 和 scheduler 问题。Orca、DistServe、POD-Attention 和 CELLA 都从不同层级支撑了这个拆分。<a id="FIELD-LLM-SERVING-001-C007"></a>[FIELD-LLM-SERVING-001-C007](#FIELD-LLM-SERVING-001-C007)<a id="FIELD-LLM-SERVING-001-C008"></a>[FIELD-LLM-SERVING-001-C008](#FIELD-LLM-SERVING-001-C008)<a id="FIELD-LLM-SERVING-001-C019"></a>[FIELD-LLM-SERVING-001-C019](#FIELD-LLM-SERVING-001-C019)<a id="FIELD-LLM-SERVING-001-C024"></a>[FIELD-LLM-SERVING-001-C024](#FIELD-LLM-SERVING-001-C024)
2. KV/cache 从临时 tensor 变成长期 serving state：vLLM/PagedAttention、Keyformer、Prompt Cache、SLoRA 和 CXL-SpecKV 分别从分页、token selection、prefix reuse、adapter/KV paging 和 disaggregated KV cache 处理状态管理。<a id="FIELD-LLM-SERVING-001-C006"></a>[FIELD-LLM-SERVING-001-C006](#FIELD-LLM-SERVING-001-C006)<a id="FIELD-LLM-SERVING-001-C015"></a>[FIELD-LLM-SERVING-001-C015](#FIELD-LLM-SERVING-001-C015)<a id="FIELD-LLM-SERVING-001-C016"></a>[FIELD-LLM-SERVING-001-C016](#FIELD-LLM-SERVING-001-C016)<a id="FIELD-LLM-SERVING-001-C017"></a>[FIELD-LLM-SERVING-001-C017](#FIELD-LLM-SERVING-001-C017)<a id="FIELD-LLM-SERVING-001-C020"></a>[FIELD-LLM-SERVING-001-C020](#FIELD-LLM-SERVING-001-C020)
3. Attention 不再只是算 FLOPs：A3、SpAtten、FAMOUS、FlashInfer 和 POD-Attention把注意力路线拆成 approximation、sparse token/head pruning、FPGA attention mapping、serving attention engine 和 prefill/decode overlap。<a id="FIELD-LLM-SERVING-001-C010"></a>[FIELD-LLM-SERVING-001-C010](#FIELD-LLM-SERVING-001-C010)<a id="FIELD-LLM-SERVING-001-C011"></a>[FIELD-LLM-SERVING-001-C011](#FIELD-LLM-SERVING-001-C011)<a id="FIELD-LLM-SERVING-001-C018"></a>[FIELD-LLM-SERVING-001-C018](#FIELD-LLM-SERVING-001-C018)[FIELD-LLM-SERVING-001-C019](#FIELD-LLM-SERVING-001-C019)<a id="FIELD-LLM-SERVING-001-C023"></a>[FIELD-LLM-SERVING-001-C023](#FIELD-LLM-SERVING-001-C023)
4. Quantization 是 token-memory 问题，不只是 arithmetic format：AWQ、VLSI 5nm Transformer inference silicon、TeLLMe 和 CELLA 都把低比特与 memory footprint、on-device/edge serving 或 prefill/decode 绑定。<a id="FIELD-LLM-SERVING-001-C013"></a>[FIELD-LLM-SERVING-001-C013](#FIELD-LLM-SERVING-001-C013)<a id="FIELD-LLM-SERVING-001-C014"></a>[FIELD-LLM-SERVING-001-C014](#FIELD-LLM-SERVING-001-C014)<a id="FIELD-LLM-SERVING-001-C021"></a>[FIELD-LLM-SERVING-001-C021](#FIELD-LLM-SERVING-001-C021)[FIELD-LLM-SERVING-001-C024](#FIELD-LLM-SERVING-001-C024)
5. Memory placement 和平台经济性进入主问题：AiM/AiMX、Blackwell 和 CXL-SpecKV 说明 LLM serving state 也被放到 HBM capacity、PIM/CXL、disaggregation 和 cost-per-token 语境里，但这些 platform rows 需要独立 workload validation。[FIELD-LLM-SERVING-001-C020](#FIELD-LLM-SERVING-001-C020)<a id="FIELD-LLM-SERVING-001-C025"></a>[FIELD-LLM-SERVING-001-C025](#FIELD-LLM-SERVING-001-C025)<a id="FIELD-LLM-SERVING-001-C028"></a>[FIELD-LLM-SERVING-001-C028](#FIELD-LLM-SERVING-001-C028)

## 发展脉络

第一条路线是 data-movement and attention-first。`A3: Accelerating Attention Mechanisms in Neural Networks with Approximation` 是 attention acceleration 的较早 architecture anchor。<a id="FIELD-LLM-SERVING-001-E001"></a>[FIELD-LLM-SERVING-001-E001](#FIELD-LLM-SERVING-001-E001)[FIELD-LLM-SERVING-001-C010](#FIELD-LLM-SERVING-001-C010) `Data Movement Is All You Need: A Case Study on Optimizing Transformers` 把 Transformer 优化重新放在 data movement、layout、fusion 和 dataflow 上，是从 operator-level 到 memory-first 思路的形成证据。<a id="FIELD-LLM-SERVING-001-E002"></a>[FIELD-LLM-SERVING-001-E002](#FIELD-LLM-SERVING-001-E002)<a id="FIELD-LLM-SERVING-001-C009"></a>[FIELD-LLM-SERVING-001-C009](#FIELD-LLM-SERVING-001-C009) `SpAtten: Efficient Sparse Attention Architecture with Cascade Token and Head Pruning` 则把 sparse attention 变成硬件路线中的 milestone candidate。<a id="FIELD-LLM-SERVING-001-E003"></a>[FIELD-LLM-SERVING-001-E003](#FIELD-LLM-SERVING-001-E003)[FIELD-LLM-SERVING-001-C011](#FIELD-LLM-SERVING-001-C011)

第二条路线是 serving runtime and state management。workload inventory 中的 Orca、vLLM/PagedAttention 和 DistServe 为 iteration-level scheduling、KV paging 和 prefill/decode disaggregation 提供了系统背景。[FIELD-LLM-SERVING-001-C006](#FIELD-LLM-SERVING-001-C006)[FIELD-LLM-SERVING-001-C007](#FIELD-LLM-SERVING-001-C007)[FIELD-LLM-SERVING-001-C008](#FIELD-LLM-SERVING-001-C008) 进入 venue evidence 后，`Efficiently Scaling Transformer Inference` 把大模型 inference scaling 和分区/低层优化放到同一条线上。<a id="FIELD-LLM-SERVING-001-E004"></a>[FIELD-LLM-SERVING-001-E004](#FIELD-LLM-SERVING-001-E004)<a id="FIELD-LLM-SERVING-001-C012"></a>[FIELD-LLM-SERVING-001-C012](#FIELD-LLM-SERVING-001-C012) `Keyformer`、`Prompt Cache`、`SLoRA` 分别处理 KV reduction、prompt reuse 和 multi-adapter serving paging，说明 KV/cache 不再只是 kernel 局部 buffer。<a id="FIELD-LLM-SERVING-001-E007"></a>[FIELD-LLM-SERVING-001-E007](#FIELD-LLM-SERVING-001-E007)<a id="FIELD-LLM-SERVING-001-E008"></a>[FIELD-LLM-SERVING-001-E008](#FIELD-LLM-SERVING-001-E008)<a id="FIELD-LLM-SERVING-001-E009"></a>[FIELD-LLM-SERVING-001-E009](#FIELD-LLM-SERVING-001-E009)

第三条路线是 attention engines for dynamic serving。`FlashInfer: Efficient and Customizable Attention Engine for LLM Inference Serving` 是本报告的 tool/benchmark role，因为它把 attention kernel 做成可组合、可定制、面向 serving state 的引擎，并且 impact audit 已记录 SGLang backend signal。<a id="FIELD-LLM-SERVING-001-E010"></a>[FIELD-LLM-SERVING-001-E010](#FIELD-LLM-SERVING-001-E010)[FIELD-LLM-SERVING-001-C018](#FIELD-LLM-SERVING-001-C018)<a id="FIELD-LLM-SERVING-001-C027"></a>[FIELD-LLM-SERVING-001-C027](#FIELD-LLM-SERVING-001-C027) `POD-Attention` 进一步把 prefill/decode overlap 放入单个 GPU attention kernel 设计中，保留为 frontier。<a id="FIELD-LLM-SERVING-001-E011"></a>[FIELD-LLM-SERVING-001-E011](#FIELD-LLM-SERVING-001-E011)[FIELD-LLM-SERVING-001-C019](#FIELD-LLM-SERVING-001-C019)

第四条路线是 quantization and token-level silicon。VLSI 2022 的 5nm Transformer inference accelerator 是 low-bit transformer silicon 的 origin anchor。<a id="FIELD-LLM-SERVING-001-E005"></a>[FIELD-LLM-SERVING-001-E005](#FIELD-LLM-SERVING-001-E005)[FIELD-LLM-SERVING-001-C013](#FIELD-LLM-SERVING-001-C013) AWQ 是 on-device LLM weight quantization 的 milestone candidate，并且 impact audit 已验证 TensorRT-LLM precision documentation 的 AWQ support。<a id="FIELD-LLM-SERVING-001-E006"></a>[FIELD-LLM-SERVING-001-E006](#FIELD-LLM-SERVING-001-E006)[FIELD-LLM-SERVING-001-C014](#FIELD-LLM-SERVING-001-C014)<a id="FIELD-LLM-SERVING-001-C026"></a>[FIELD-LLM-SERVING-001-C026](#FIELD-LLM-SERVING-001-C026) TeLLMe 和 CELLA 则把低比特和 prefill/decode token metrics 放到 edge FPGA 和 edge CIM silicon 路线里。<a id="FIELD-LLM-SERVING-001-E013"></a>[FIELD-LLM-SERVING-001-E013](#FIELD-LLM-SERVING-001-E013)<a id="FIELD-LLM-SERVING-001-E016"></a>[FIELD-LLM-SERVING-001-E016](#FIELD-LLM-SERVING-001-E016)[FIELD-LLM-SERVING-001-C021](#FIELD-LLM-SERVING-001-C021)[FIELD-LLM-SERVING-001-C024](#FIELD-LLM-SERVING-001-C024)

第五条路线是 memory placement and platform frontier。FINN-T 和 FAMOUS 是 FPGA 方法桥：一个把 FINN-style custom dataflow 延伸到 quantized Transformers，一个聚焦 UltraScale+ 上的 attention mechanism。<a id="FIELD-LLM-SERVING-001-E014"></a>[FIELD-LLM-SERVING-001-E014](#FIELD-LLM-SERVING-001-E014)<a id="FIELD-LLM-SERVING-001-E015"></a>[FIELD-LLM-SERVING-001-E015](#FIELD-LLM-SERVING-001-E015)<a id="FIELD-LLM-SERVING-001-C022"></a>[FIELD-LLM-SERVING-001-C022](#FIELD-LLM-SERVING-001-C022)[FIELD-LLM-SERVING-001-C023](#FIELD-LLM-SERVING-001-C023) CXL-SpecKV 把 KV cache 放到 disaggregated FPGA/CXL 语境中，是 2026 frontier 而非长期影响证据。<a id="FIELD-LLM-SERVING-001-E012"></a>[FIELD-LLM-SERVING-001-E012](#FIELD-LLM-SERVING-001-E012)[FIELD-LLM-SERVING-001-C020](#FIELD-LLM-SERVING-001-C020) SK Hynix AiM/AiMX 和 NVIDIA Blackwell 是 industry/platform frontier signal，说明 HBM/PIM/platform economics 正在进入 LLM serving 讨论，但不能替代论文级可复核实验。<a id="FIELD-LLM-SERVING-001-E017"></a>[FIELD-LLM-SERVING-001-E017](#FIELD-LLM-SERVING-001-E017)<a id="FIELD-LLM-SERVING-001-E018"></a>[FIELD-LLM-SERVING-001-E018](#FIELD-LLM-SERVING-001-E018)[FIELD-LLM-SERVING-001-C025](#FIELD-LLM-SERVING-001-C025)[FIELD-LLM-SERVING-001-C028](#FIELD-LLM-SERVING-001-C028)

## 研究方法

本领域的方法族可以按 “瓶颈对象” 而不是按平台划分。

Attention kernel and sparse attention：approximation、token/head pruning、MHA/MQA/GQA-like KV reduction、FPGA/HLS tiling、serving-oriented attention templates 和 prefill/decode overlap 都属于这条方法族。A3、SpAtten、FAMOUS、FlashInfer 和 POD-Attention 是当前矩阵中最清楚的 evidence path。[FIELD-LLM-SERVING-001-E001](#FIELD-LLM-SERVING-001-E001)[FIELD-LLM-SERVING-001-E003](#FIELD-LLM-SERVING-001-E003)[FIELD-LLM-SERVING-001-E010](#FIELD-LLM-SERVING-001-E010)[FIELD-LLM-SERVING-001-E011](#FIELD-LLM-SERVING-001-E011)[FIELD-LLM-SERVING-001-E015](#FIELD-LLM-SERVING-001-E015)

State/cache/runtime：KV page/block allocation、prefix reuse、adapter/KV paging、cache hit ratio、goodput under SLO 和 prefill/decode scheduling 是系统侧方法族。vLLM/PagedAttention、Orca、DistServe、Keyformer、Prompt Cache 和 SLoRA 支撑这条线。[FIELD-LLM-SERVING-001-C006](#FIELD-LLM-SERVING-001-C006)[FIELD-LLM-SERVING-001-C007](#FIELD-LLM-SERVING-001-C007)[FIELD-LLM-SERVING-001-C008](#FIELD-LLM-SERVING-001-C008)[FIELD-LLM-SERVING-001-E007](#FIELD-LLM-SERVING-001-E007)[FIELD-LLM-SERVING-001-E008](#FIELD-LLM-SERVING-001-E008)[FIELD-LLM-SERVING-001-E009](#FIELD-LLM-SERVING-001-E009)

Quantization/token-memory：weight-only quantization、KV/token compression、ternary execution、per-vector scaling、CIM/CAM mode switching 和 hash-based KV filtering 是 token-memory 方法族。AWQ、VLSI 5nm transformer chip、TeLLMe 和 CELLA 提供具体 evidence。[FIELD-LLM-SERVING-001-E005](#FIELD-LLM-SERVING-001-E005)[FIELD-LLM-SERVING-001-E006](#FIELD-LLM-SERVING-001-E006)[FIELD-LLM-SERVING-001-E013](#FIELD-LLM-SERVING-001-E013)[FIELD-LLM-SERVING-001-E016](#FIELD-LLM-SERVING-001-E016)

Memory placement/PIM/CXL：PIM/AiM、CXL/disaggregated KV、HBM capacity 和 memory economics 是相邻但重要的方法族。它常和 [GSF-03](../40_synthesis/third_wave_field_synthesis.md#GSF-03)/[GSF-11](../40_synthesis/third_wave_field_synthesis.md#GSF-11) 重叠，因此本报告只使用其服务 LLM serving state 的部分。[FIELD-LLM-SERVING-001-E012](#FIELD-LLM-SERVING-001-E012)[FIELD-LLM-SERVING-001-E017](#FIELD-LLM-SERVING-001-E017)[FIELD-LLM-SERVING-001-E018](#FIELD-LLM-SERVING-001-E018)

Evaluation/profiling：至少要分开 TTFT、TPOT、throughput、goodput-under-SLO、KV bytes/token、KV peak memory、prefix-cache hit ratio 和 energy/token。只写 throughput 或 TOPS/W 会遮蔽 queueing、cache fragmentation、decode bandwidth 和 p99 jitter。[FIELD-LLM-SERVING-001-C004](#FIELD-LLM-SERVING-001-C004)[FIELD-LLM-SERVING-001-C005](#FIELD-LLM-SERVING-001-C005)

## 代表性论文与系统

| 角色 | 证据 | 代表项目 | 路线 |
|---|---|---|---|
| origin_anchor | [FIELD-LLM-SERVING-001-E001](#FIELD-LLM-SERVING-001-E001) | A3, HPCA 2020 | 注意力近似硬件 |
| formation_paper | [FIELD-LLM-SERVING-001-E002](#FIELD-LLM-SERVING-001-E002) | 数据移动就是您所需要的，MLSys 2021 | 数据移动优先 Transformer 优化 |
| milestone_candidate | [FIELD-LLM-SERVING-001-E003](#FIELD-LLM-SERVING-001-E003) | 斯帕滕，HPCA 2021 | 稀疏注意力硬件 |
| milestone_candidate | [FIELD-LLM-SERVING-001-E004](#FIELD-LLM-SERVING-001-E004) | 有效扩展Transformer推理，MLSys 2023 | 服务规模推断 |
| origin_anchor | [FIELD-LLM-SERVING-001-E005](#FIELD-LLM-SERVING-001-E005) | VLSI 2022 5nm Transformer 推理加速器 | 代币级低位硅 |
| milestone_candidate | [FIELD-LLM-SERVING-001-E006](#FIELD-LLM-SERVING-001-E006) | AWQ，MLSys 2024 | 重量量化和设备上服务 |
| formation_paper | [FIELD-LLM-SERVING-001-E007](#FIELD-LLM-SERVING-001-E007) | Keyformer，MLSys 2024 | KV还原 |
| formation_paper | [FIELD-LLM-SERVING-001-E008](#FIELD-LLM-SERVING-001-E008) | 提示缓存，MLSys 2024 | 前缀/提示注意重用 |
| milestone_candidate | [FIELD-LLM-SERVING-001-E009](#FIELD-LLM-SERVING-001-E009) | SLoRA，MLSys 2024 | 适配器/KV 寻呼 |
| tool_benchmark | [FIELD-LLM-SERVING-001-E010](#FIELD-LLM-SERVING-001-E010) | FlashInfer、MLSys 2025 | 服务注意力引擎 |
| frontier | [FIELD-LLM-SERVING-001-E011](#FIELD-LLM-SERVING-001-E011) | POD-注意，ASPLOS 2025 | 预填充/解码重叠 |
| frontier | [FIELD-LLM-SERVING-001-E012](#FIELD-LLM-SERVING-001-E012) | CXL-SpecKV、FPGA 2026 | 分解推测 KV 缓存 |
| frontier | [FIELD-LLM-SERVING-001-E013](#FIELD-LLM-SERVING-001-E013) | TeLLMe，FPGA 2026 | 三进制预填充/边缘解码 FPGA |
| method_bridge | [FIELD-LLM-SERVING-001-E014](#FIELD-LLM-SERVING-001-E014) | FINN-T, FPT 2024 | 量化 Transformer FPGA 数据流 |
| frontier | [FIELD-LLM-SERVING-001-E015](#FIELD-LLM-SERVING-001-E015) | FAMOUS, FPT 2024 | FPGA MHA 加速 |
| milestone_candidate | [FIELD-LLM-SERVING-001-E016](#FIELD-LLM-SERVING-001-E016) | CELLA, VLSI 2025 | 边缘 LLM 预填充/解码 CIM |
| method_bridge | [FIELD-LLM-SERVING-001-E017](#FIELD-LLM-SERVING-001-E017) | SK Hynix AiM/AiMX，2024 年热门芯片 | PIM/内存经济性 |
| frontier | [FIELD-LLM-SERVING-001-E018](#FIELD-LLM-SERVING-001-E018) | NVIDIA Blackwell，Hot Chips 2024 | 产品级内存/状态平台 |
| negative_boundary | <a id="FIELD-LLM-SERVING-001-E019"></a>[FIELD-LLM-SERVING-001-E019](#FIELD-LLM-SERVING-001-E019) | MLP-卸载，SC 2025 | 训练内存墙卸载，不提供解码服务 |
| negative_boundary | <a id="FIELD-LLM-SERVING-001-E020"></a>[FIELD-LLM-SERVING-001-E020](#FIELD-LLM-SERVING-001-E020) | 用于高效 LLM 推理的实用非结构化稀疏性，MLSys 2026 | 仅标题低源深度前沿 |

## 团队与会议线索

MLSys 中的venue信号最强，用于服务状态/runtime/注意力引擎，HPCA 用于注意力架构锚点，VLSI/ISSCC/JSSC 式硅venue用于代币级Transformer加速器，FPGA/FPT/FPL 用于可重新配置数据流和边缘 FPGA 路由，ASPLOS 用于服务kernel/runtime交互，Hot Chips 用于行业平台经济性，以及用于训练/卸载的 SC/PACT 或 CXL/KV 相邻系统。这是活动图，不是排名。[FIELD-LLM-SERVING-001-C001](#FIELD-LLM-SERVING-001-C001)<a id="FIELD-LLM-SERVING-001-C032"></a>[FIELD-LLM-SERVING-001-C032](#FIELD-LLM-SERVING-001-C032)

团队信号的使用是保守的。团队矩阵将 Ajay Tirumala、Raymond Wong 和 NVIDIA 记录为 Blackwell Hot Chips 行的部分公司团队信号；它不支持广泛的排名主张。<a id="FIELD-LLM-SERVING-001-C033"></a>[FIELD-LLM-SERVING-001-C033](#FIELD-LLM-SERVING-001-C033) 实体审计将 Song Han 解析为与 SpAtten/AWQ 样式行相关的策划 MIT/HAN 实验室作者身份，但本报告仍将其视为来源支持的活动信号，而不是团队实力的证据。<a id="FIELD-LLM-SERVING-001-C034"></a>[FIELD-LLM-SERVING-001-C034](#FIELD-LLM-SERVING-001-C034) NVIDIA 机构字符串和VLSI 清华/HKUST/CELLA 信号仍然是有用的阅读线索，但其实体边界对于领导语言来说不够强大。<a id="FIELD-LLM-SERVING-001-C035"></a>[FIELD-LLM-SERVING-001-C035](#FIELD-LLM-SERVING-001-C035)<a id="FIELD-LLM-SERVING-001-C036"></a>[FIELD-LLM-SERVING-001-C036](#FIELD-LLM-SERVING-001-C036)

## 开放问题

第一，metrics 还没有统一。Serving goodput、TTFT、TPOT、KV bytes/token、prefix-cache hit ratio、energy/token、paper-level TOPS/W 和 platform TCO 经常混在一起；后续 deep dive 需要把 workload trace、load level、prompt/output length、model size 和 memory tier 都写清楚。[FIELD-LLM-SERVING-001-C004](#FIELD-LLM-SERVING-001-C004)[FIELD-LLM-SERVING-001-C005](#FIELD-LLM-SERVING-001-C005)

第二，KV/cache 的边界还会继续拆分。Paged KV allocation、KV quantization、prefix reuse、CXL/disaggregated KV、PIM-assisted attention 和 adapter/KV paging 共享 “state management” 这个大问题，但机制、评价指标和硬件边界不同。[FIELD-LLM-SERVING-001-E007](#FIELD-LLM-SERVING-001-E007)[FIELD-LLM-SERVING-001-E008](#FIELD-LLM-SERVING-001-E008)[FIELD-LLM-SERVING-001-E009](#FIELD-LLM-SERVING-001-E009)[FIELD-LLM-SERVING-001-E012](#FIELD-LLM-SERVING-001-E012)[FIELD-LLM-SERVING-001-E017](#FIELD-LLM-SERVING-001-E017)

第三，2025-2026 frontier 很多，但长期影响少。CXL-SpecKV、TeLLMe、POD-Attention、CELLA 和 Blackwell 都适合写前沿，不适合直接写成成熟主线；AWQ 和 FlashInfer 是少数已有 toolchain/backend impact audit 支撑的条目。[FIELD-LLM-SERVING-001-C026](#FIELD-LLM-SERVING-001-C026)[FIELD-LLM-SERVING-001-C027](#FIELD-LLM-SERVING-001-C027)[FIELD-LLM-SERVING-001-C031](#FIELD-LLM-SERVING-001-C031)

第四，artifact/status 需要下一轮复核。公开代码、project page、artifact award 和 benchmark metric 不能等同于可复现；本报告没有本地运行任何代码、simulator 或 benchmark。[FIELD-LLM-SERVING-001-C031](#FIELD-LLM-SERVING-001-C031)

## 连接到用户方向

对用户的 3DGS/FPGA/机器人端侧方向，这个 field 最有用的不是 “LLM 也很火”，而是它提供了一套分析长期状态和内存瓶颈的方法。用户输入里明确关注 FPGA dataflow、3DGS acceleration、robotics batch=1 low-latency inference、KV Cache、attention、quantization、MoE 和 inference engine。<a id="FIELD-LLM-SERVING-001-C037"></a>[FIELD-LLM-SERVING-001-C037](#FIELD-LLM-SERVING-001-C037)

与 3DGS 的直接类比是 stateful rendering/inference：LLM 的 KV cache、prefix cache 和 adapter state，对应 3DGS 中 Gaussian map、tile lists、depth/sort reuse 和 frame-to-frame state。可迁移的问题不是算子名，而是如何把动态状态变成可分页、可复用、可压缩、可预取的硬件对象。[FIELD-LLM-SERVING-001-C005](#FIELD-LLM-SERVING-001-C005)

与 FPGA 的直接关系是 dataflow and memory controller design。FINN-T、FAMOUS、CXL-SpecKV 和 TeLLMe 说明 attention、quantized Transformer、KV cache 和 prefill/decode 都可以被重新组织成 streaming/paged/offload-friendly datapath，但模型迭代、host-device I/O、artifact run status 和 benchmark fairness 是核心风险。[FIELD-LLM-SERVING-001-E012](#FIELD-LLM-SERVING-001-E012)[FIELD-LLM-SERVING-001-E013](#FIELD-LLM-SERVING-001-E013)[FIELD-LLM-SERVING-001-E014](#FIELD-LLM-SERVING-001-E014)[FIELD-LLM-SERVING-001-E015](#FIELD-LLM-SERVING-001-E015)

与机器人端侧计算的关系是 batch=1、low jitter 和 power-bounded inference。workload inventory 把 VLA/action-generation 归为 edge-real-time workload，评价重点不同于云端吞吐：机器人更关心 TTFT/TPOT 的确定性、p99 jitter、功耗和控制环路中的 state reuse。<a id="FIELD-LLM-SERVING-001-C038"></a>[FIELD-LLM-SERVING-001-C038](#FIELD-LLM-SERVING-001-C038)[FIELD-LLM-SERVING-001-C004](#FIELD-LLM-SERVING-001-C004)

## 缺失来源

- 需要对 CXL-SpecKV、TeLLMe、FAMOUS、FINN-T、SLoRA、POD-Attention 和 FlashInfer 做独立 artifact install/build/run audit，当前最多是 runnable_unchecked 或 project/backend signal。[FIELD-LLM-SERVING-001-C031](#FIELD-LLM-SERVING-001-C031)
- 需要补充 vLLM/PagedAttention、Orca、DistServe 与 venue evidence 之间的 citation/context bridge；本报告用 workload inventory 支撑系统背景，但没有把它们当作 GSF venue rows。[FIELD-LLM-SERVING-001-C006](#FIELD-LLM-SERVING-001-C006)[FIELD-LLM-SERVING-001-C007](#FIELD-LLM-SERVING-001-C007)[FIELD-LLM-SERVING-001-C008](#FIELD-LLM-SERVING-001-C008)
- 需要把 2026 MLSys/FPGA/VLSI rows 等 final proceedings、DOI、abstract/PDF 发布后再复核一次。[FIELD-LLM-SERVING-001-C020](#FIELD-LLM-SERVING-001-C020)[FIELD-LLM-SERVING-001-C021](#FIELD-LLM-SERVING-001-C021)<a id="FIELD-LLM-SERVING-001-C030"></a>[FIELD-LLM-SERVING-001-C030](#FIELD-LLM-SERVING-001-C030)
- 需要对 team/entity rows 做更细的 paper-time affiliation 和 project boundary 审计，特别是 NVIDIA、SK Hynix、Tsinghua/HKUST、MIT/HAN Lab、FINN/Xilinx-style author/project signals。[FIELD-LLM-SERVING-001-C032](#FIELD-LLM-SERVING-001-C032)[FIELD-LLM-SERVING-001-C033](#FIELD-LLM-SERVING-001-C033)[FIELD-LLM-SERVING-001-C034](#FIELD-LLM-SERVING-001-C034)[FIELD-LLM-SERVING-001-C035](#FIELD-LLM-SERVING-001-C035)[FIELD-LLM-SERVING-001-C036](#FIELD-LLM-SERVING-001-C036)
- 需要把 attention/KV/cache metrics 与 3DGS/robotics edge metrics 放到共同 profiling framework 中，才能判断哪些方法学可以迁移，哪些只是 LLM serving 的局部工程技巧。[FIELD-LLM-SERVING-001-C037](#FIELD-LLM-SERVING-001-C037)[FIELD-LLM-SERVING-001-C038](#FIELD-LLM-SERVING-001-C038)
