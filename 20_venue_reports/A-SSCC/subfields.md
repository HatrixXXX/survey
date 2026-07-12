# A-SSCC 小领域深读

## 1. 范围与语料

- Venue/task：`A-SSCC`，ASSCC 第二轮。
- 第二轮后的 corpus：`949` 条 paper rows，其中包括 2016-2025 的 `948` 条 accepted/proceedings rows，以及一个 2026 partial marker。
- targeted Crossref 回填后的 DOI 覆盖：`909/949` 条 paper rows。按年份统计的 DOI 数量为 {'2016': 69, '2017': 83, '2018': 90, '2019': 88, '2020': 41, '2021': 103, '2022': 84, '2023': 99, '2024': 127, '2025': 125, '2026': 0}。
- 2025 官方 ePapers metadata：`135/135` 条 official URLs；其中 `134` 条有 track/session detail。
- 筛选矩阵（screening matrix）覆盖：`954` 行（`949` papers + `5` awards），decision 分布为 {'index_only': 870, 'deep_read': 70, 'needs_review': 10, 'exclude_non_main': 4}。
- 深读证据矩阵（deep-read evidence matrix）：`67` 条 paper rows。由于 canonical award sources 仍缺失，award-only rows 不作为 verified paper-impact evidence。
- 证据行中的 citation/adoption/artifact 检查在记录 count 或 adoption statement 时使用查询日期 `2026-06-27`。

## 2. Subfield Map（小领域图谱）

| subfield_id | subfield | evidence rows | roles | representative paper ids | status |
|---|---|---:|---|---|---|
| <a id="A-SSCC-SF01"></a>[A-SSCC-SF01](#A-SSCC-SF01) | 低能耗神经 MAC 与非标准算术原语 | 3 | origin_anchor:2, method_bridge:1 | [A-SSCC-2016-P0006](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0006) (2016); [A-SSCC-2016-P0007](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0007) (2016); [A-SSCC-2018-P0001](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0001) (2018) | venue_provisional |
| <a id="A-SSCC-SF02"></a>[A-SSCC-SF02](#A-SSCC-SF02) | 端侧学习、自适应与动态 edge AI | 6 | formation_paper:1, milestone_candidate:1, method_bridge:1, frontier:3 | [A-SSCC-2017-P0060](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2017-P0060) (2017); [A-SSCC-2019-P0017](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0017) (2019); [A-SSCC-2020-P0037](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0037) (2020); [A-SSCC-2024-P0017](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0017) (2024); [A-SSCC-2024-P0053](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0053) (2024) | venue_provisional |
| <a id="A-SSCC-SF03"></a>[A-SSCC-SF03](#A-SSCC-SF03) | Transformer 与 LLM 状态/数据流加速 | 4 | milestone_candidate:1, method_bridge:1, frontier:2 | [A-SSCC-2023-P0008](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0008) (2023); [A-SSCC-2023-P0030](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0030) (2023); [A-SSCC-2025-P0090](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0090) (2025); [A-SSCC-2025-P0093](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0093) (2025) | venue_provisional |
| <a id="A-SSCC-SF04"></a>[A-SSCC-SF04](#A-SSCC-SF04) | SRAM 混合信号/数字 CIM macro 演进 | 4 | origin_anchor:1, formation_paper:1, method_bridge:1, frontier:1 | [A-SSCC-2019-P0010](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0010) (2019); [A-SSCC-2019-P0061](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0061) (2019); [A-SSCC-2023-P0020](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0020) (2023); [A-SSCC-2025-P0111](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0111) (2025) | venue_provisional |
| <a id="A-SSCC-SF05"></a>[A-SSCC-SF05](#A-SSCC-SF05) | 时域、脉冲与稀疏自适应 CIM | 2 | milestone_candidate:2 | [A-SSCC-2020-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0031) (2020); [A-SSCC-2022-P0048](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0048) (2022) | venue_provisional |
| <a id="A-SSCC-SF06"></a>[A-SSCC-SF06](#A-SSCC-SF06) | NVM/hybrid CIM 可靠性与 fine-tuning | 3 | milestone_candidate:1, frontier:2 | [A-SSCC-2021-P0032](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0032) (2021); [A-SSCC-2024-P0089](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0089) (2024); [A-SSCC-2025-P0065](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0065) (2025) | venue_provisional |
| <a id="A-SSCC-SF07"></a>[A-SSCC-SF07](#A-SSCC-SF07) | Transformer、LLM 与生成式 AI CIM | 3 | method_bridge:1, milestone_candidate:1, frontier:1 | [A-SSCC-2022-P0013](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0013) (2022); [A-SSCC-2023-P0013](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0013) (2023); [A-SSCC-2025-P0045](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0045) (2025) | venue_provisional |
| <a id="A-SSCC-SF08"></a>[A-SSCC-SF08](#A-SSCC-SF08) | 具身 edge perception 与 planning | 2 | frontier:2 | [A-SSCC-2025-P0094](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0094) (2025); [A-SSCC-2025-P0026](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0026) (2025) | frontier_needs_review |
| <a id="A-SSCC-SF09"></a>[A-SSCC-SF09](#A-SSCC-SF09) | Depth、SLAM、event 与 sensor-near vision | 12 | origin_anchor:1, formation_paper:2, method_bridge:4, milestone_candidate:2, frontier:2, negative_boundary:1 | [A-SSCC-2016-P0065](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0065) (2016); [A-SSCC-2018-P0078](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0078) (2018); [A-SSCC-2019-P0009](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0009) (2019); [A-SSCC-2021-P0042](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0042) (2021); [A-SSCC-2021-P0084](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0084) (2021) | venue_provisional |
| <a id="A-SSCC-SF10"></a>[A-SSCC-SF10](#A-SSCC-SF10) | FPGA vision/DNN pipeline 加速器 | 7 | formation_paper:2, method_bridge:3, frontier:2 | [A-SSCC-2018-P0022](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0022) (2018); [A-SSCC-2019-P0058](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0058) (2019); [A-SSCC-2021-P0021](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0021) (2021); [A-SSCC-2021-P0092](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0092) (2021); [A-SSCC-2023-P0029](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0029) (2023) | venue_provisional |
| <a id="A-SSCC-SF12"></a>[A-SSCC-SF12](#A-SSCC-SF12) | 神经渲染与 3D Gaussian Splatting 加速 | 4 | origin_anchor:1, milestone_candidate:1, frontier:2 | [A-SSCC-2023-P0046](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0046) (2023); [A-SSCC-2024-P0096](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0096) (2024); [A-SSCC-2025-P0012](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0012) (2025); [A-SSCC-2025-P0027](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0027) (2025) | venue_provisional |
| <a id="A-SSCC-SF13"></a>[A-SSCC-SF13](#A-SSCC-SF13) | 安全与 PQC 算术加速 | 8 | origin_anchor:1, formation_paper:1, method_bridge:2, milestone_candidate:2, frontier:2 | [A-SSCC-2018-P0049](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0049) (2018); [A-SSCC-2022-P0015](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0015) (2022); [A-SSCC-2022-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0031) (2022); [A-SSCC-2023-P0011](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0011) (2023); [A-SSCC-2023-P0042](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0042) (2023) | venue_provisional |
| <a id="A-SSCC-SF14"></a>[A-SSCC-SF14](#A-SSCC-SF14) | 芯片 memory、I/O 与 SoC 集成约束 | 5 | origin_anchor:1, formation_paper:1, frontier:3 | [A-SSCC-2016-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0031) (2016); [A-SSCC-2019-P0039](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0039) (2019); [A-SSCC-2024-P0062](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0062) (2024); [A-SSCC-2025-P0002](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0002) (2025); [A-SSCC-2025-P0066](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0066) (2025) | venue_provisional |
| <a id="A-SSCC-SF11"></a>[A-SSCC-SF11](#A-SSCC-SF11) | 可编程/非主流 PIM 与边界行 | 4 | method_bridge:2, negative_boundary:2 | [A-SSCC-2023-P0072](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0072) (2023); [A-SSCC-2024-P0112](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0112) (2024); [A-SSCC-2022-P0029](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0029) (2022); [A-SSCC-2025-P0102](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0102) (2025) | boundary_only |

## 3. Subfield Deep Dives（小领域深读）

### [A-SSCC-SF01](#A-SSCC-SF01). 低能耗神经 MAC 与非标准算术原语

- Research problem：把神经网络计算压到电路原语层，核心问题是 MAC 能耗、表示方式和低电压 CMOS 可实现性。
- Background/current state：证据覆盖 `2016-2018`，共 `3` 条 selected rows。Impact status counts: {'needs_review': 2, 'impact_unverified': 1}。
- Technical route：路线从 switched-capacitor dot product、time-domain neural chip 到 phase-domain MAC；当前只能说明 venue 内出现多种低能耗原语，不声称已经形成统一产业路线。
- Representative work：[A-SSCC-2016-P0006](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0006); [A-SSCC-2016-P0007](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0007); [A-SSCC-2018-P0001](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0001)。
- Team signals：author-line activity signal: Daniel Bankman|Boris Murmann；不做排名或消歧。author-line activity signal: Daisuke Miyashita|Shouhei Kousai|Tomoya Suzuki|Jun Deguchi；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：DNN inference primitive metrics；MNIST / dot-product primitive metrics reported by abstract-level source；paper-level throughput/energy metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF02](#A-SSCC-SF02). 端侧学习、自适应与动态 edge AI

- Research problem：端侧设备不只做固定推理，还要处理 RNN、个性化训练、GAN/domain optimization、DRL、diffusion 和动态网络。
- Background/current state：证据覆盖 `2017-2025`，共 `6` 条 selected rows。Impact status counts: {'needs_review': 3, 'impact_unverified': 3}。
- Technical route：路线从低功耗 RNN、trainable CNN、GAN on-chip training 发展到 DRL/dynamic NN/diffusion；趋势由跨年论文支撑，但后续采用大多未证实。
- Representative work：[A-SSCC-2017-P0060](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2017-P0060); [A-SSCC-2019-P0017](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0017); [A-SSCC-2020-P0037](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0037); [A-SSCC-2025-P0030](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0030)。
- Team signals：author-line activity signal: Jinmook Lee|Dongjoo Shin|Hoi-Jun Yoo；不做排名或消歧。author-line activity signal: Seungkyu Choi|Jaehyeong Sim|Myeonggu Kang|YeongJae Choi et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：DRL SoC paper-level metrics need PDF audit；GAN/domain optimization metrics；diffusion workload metrics from official abstract；embedded RNN evaluation metrics；on-device training/personalization benchmark metrics；paper-level metrics need PDF audit。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF03](#A-SSCC-SF03). Transformer 与 LLM 状态/数据流加速

- Research problem：Transformer/LLM 的瓶颈从单 MAC 能效转向 token/state、prefill/decode、稀疏性和数据流。
- Background/current state：证据覆盖 `2023-2025`，共 `4` 条 selected rows。Impact status counts: {'needs_review': 2, 'impact_unverified': 2}。
- Technical route：路线包括 random projection/speculation、Fourier/linear attention、MCM prefill-decode disaggregation、sparse LLM dataflow。
- Representative work：[A-SSCC-2023-P0008](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0008); [A-SSCC-2023-P0030](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0030); [A-SSCC-2025-P0090](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0090); [A-SSCC-2025-P0093](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0093)。
- Team signals：author-line activity signal: Yubin Qin|Yang Wang 0089|Dazheng Deng|Xiaolong Yang et al.；不做排名或消歧。author-line activity signal: Jingu Lee|Sangjin Kim|Wooyoung Jo|Hoi-Jun Yoo；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：LLM accelerator paper-level metrics；LLM throughput benchmark in title/official abstract；Transformer edge-accelerator metrics；Transformer throughput/energy metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF04](#A-SSCC-SF04). SRAM 混合信号/数字 CIM macro 演进

- Research problem：SRAM CIM 的问题是把 MAC 放进阵列后如何处理 sensing margin、ADC cycle、量化表示和 TOPS/W。
- Background/current state：证据覆盖 `2019-2025`，共 `4` 条 selected rows。Impact status counts: {'needs_review': 2, 'impact_unverified': 2}。
- Technical route：路线从 voltage-mode accumulation、configurable bit-width、logarithmic quantization 到 adaptive sensing/SAR ADC。
- Representative work：[A-SSCC-2019-P0010](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0010); [A-SSCC-2019-P0061](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0061); [A-SSCC-2023-P0020](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0020); [A-SSCC-2025-P0111](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0111)。
- Team signals：author-line activity signal: Hyunjoon Kim|Qian Chen|Bongjin Kim；不做排名或消歧。author-line activity signal: Zhixiao Zhang|Jia-Jing Chen|Xin Si|Yung-Ning Tu et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：CIM macro CNN metrics；CIM macro TOPS/W metrics；CNN/Transformer SRAM CIM metrics；ImageNet ResNet-50 / LOGQ4 INT8 metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF05](#A-SSCC-SF05). 时域、脉冲与稀疏自适应 CIM

- Research problem：time/spike domain CIM 用时间、事件或稀疏性减少数据搬运和 ADC/数字监控成本。
- Background/current state：证据覆盖 `2020-2022`，共 `2` 条 selected rows。Impact status counts: {'verified': 1, 'needs_review': 1}。
- Technical route：路线包括 predictable decomposed convolution、time-domain CIM、spike encoding 和 differential charge-domain integrate-and-fire。
- Representative work：[A-SSCC-2020-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0031); [A-SSCC-2022-P0048](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0048)。
- Team signals：author-line activity signal: Jianxun Yang|Yuyao Kong|Zhao Zhang|Zhuangzhi Liu et al.；不做排名或消歧。author-line activity signal: Jiahao Song|Xiyuan Tang|Haoyang Luo|Kuan Xu et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：quantized-DNN CIM processor metrics；sparsity/CIM macro metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF06](#A-SSCC-SF06). NVM/hybrid CIM 可靠性与 fine-tuning

- Research problem：RRAM/Flash 等 NVM 给容量和静态功耗带来优势，同时引入可靠性、endurance、write latency 和 fine-tuning 更新问题。
- Background/current state：证据覆盖 `2021-2025`，共 `3` 条 selected rows。Impact status counts: {'needs_review': 2, 'impact_unverified': 1}。
- Technical route：路线从 ECC/BER 修复，到 RRAM/SRAM mixed allocation，再到 Flash/SRAM 分工承载 frozen weights 与 LoRA rank matrices。
- Representative work：[A-SSCC-2021-P0032](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0032); [A-SSCC-2024-P0089](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0089); [A-SSCC-2025-P0065](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0065)。
- Team signals：author-line activity signal: Brian Crafton|Samuel Spetalnick|Jong-Hyeok Yoon|Wei Wu et al.；不做排名或消歧。author-line activity signal: Chen Mu|Zhirui Huang|Hao Jiang 0024|Jie Liao et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：CIFAR10/ImageNet variation-recovery metrics；CNN/Transformer fine-tuning metrics；MobileLLM and Llama2-7B decode metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF07](#A-SSCC-SF07). Transformer、LLM 与生成式 AI CIM

- Research problem：CIM 不再只服务 CNN inference，而开始面向 attention、Transformer、LLM/generative inference。
- Background/current state：证据覆盖 `2022-2025`，共 `3` 条 selected rows。Impact status counts: {'impact_unverified': 2, 'needs_review': 1}。
- Technical route：路线包括 correlative CIM ring、token-slimmed attention、systolic CIM array、microscaling/sub-8b digital CIM。
- Representative work：[A-SSCC-2022-P0013](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0013); [A-SSCC-2023-P0013](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0013); [A-SSCC-2025-P0045](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0045)。
- Team signals：author-line activity signal: Ruiqi Guo|Zhiheng Yue|Hao Li|Te Hu et al.；不做排名或消歧。author-line activity signal: Ruiqi Guo|Yang Wang|Xiaofeng Chen|Lei Wang et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：Transformer CIM metrics；attention NN processor metrics；generative-AI CIM efficiency metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF08](#A-SSCC-SF08). 具身 edge perception 与 planning

- Research problem：具身/physical AI 把视觉输入、动作规划和动态神经网络带到低功耗边缘系统。
- Background/current state：证据覆盖 `2025-2025`，共 `2` 条 selected rows。Impact status counts: {'impact_unverified': 1, 'needs_review': 1}。
- Technical route：目前这条路线只是 frontier 信号，不足以做成熟趋势判断；需要跟进 2026 之后的引用和跨会议实现。
- Representative work：[A-SSCC-2025-P0026](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0026); [A-SSCC-2025-P0094](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0094)。
- Team signals：author-line activity signal: Tengyu Zhang|Tong Xie|Haoyang Luo|Yixuan Hu et al.；不做排名或消歧。author-line activity signal: Yujie Ma|Siqi He|Sinong Gong|Linqi Li et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：official abstract-level metrics；robot action-planning official metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF09](#A-SSCC-SF09). Depth、SLAM、event 与 sensor-near vision

- Research problem：把 depth、optical flow、SLAM、event vision 和 sensor-near preprocessing 前移，以降低端侧视觉延迟和能耗。
- Background/current state：证据覆盖 `2016-2025`，共 `12` 条 selected rows。Impact status counts: {'impact_unverified': 7, 'needs_review': 5}。
- Technical route：路线包括 depth/stereo、computational CMOS image sensor、near-sensor SNN、SLAM FPGA、LiDAR point-cloud 和 optical-flow preprocessing。
- Representative work：[A-SSCC-2016-P0065](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0065); [A-SSCC-2019-P0009](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0009); [A-SSCC-2021-P0084](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0084); [A-SSCC-2024-P0021](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0021); [A-SSCC-2025-P0071](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0071)。
- Team signals：author-line activity signal: Sungpill Choi|Seongwook Park|Hoi-Jun Yoo；不做排名或消歧。author-line activity signal: Li-De Chen|Yu-Ta Lu|Yu-Ling Hsiao|Bo-Hsiang Yang et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：3D sensor-near metrics；LiDAR point-cloud metrics；SLAM/optical-flow FPGA metrics；SNN/event vision metrics；always-on feature extraction metrics；depth-estimation processor metrics；event vision detection metrics；learned image compression metrics；light-field/depth FPGA metrics；monocular depth metrics；optical-flow preprocessing sensor metrics；stereo/depth metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF10](#A-SSCC-SF10). FPGA vision/DNN pipeline 加速器

- Research problem：FPGA 在 A-SSCC 中主要用于快速承载视觉/DNN pipeline、后处理、precision tuning 和新 video workload。
- Background/current state：证据覆盖 `2018-2025`，共 `7` 条 selected rows。Impact status counts: {'needs_review': 4, 'impact_unverified': 3}。
- Technical route：路线包括 variable bit precision CNN、sparsity-aware CNN、NMS、tiny NN search、super-resolution 和 video Transformer。
- Representative work：[A-SSCC-2018-P0022](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0022); [A-SSCC-2019-P0058](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0058); [A-SSCC-2021-P0021](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0021); [A-SSCC-2023-P0029](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0029); [A-SSCC-2025-P0029](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0029)。
- Team signals：author-line activity signal: Asuka Maki|Daisuke Miyashita|Kengo Nakata|Fumihiko Tachibana et al.；不做排名或消歧。author-line activity signal: Seungsik Moon|Hyunhoon Lee|Younghoon Byun|Jongmin Park et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：FPGA CNN precision/throughput metrics；NMS/object-detection postprocess metrics；official 2025 visual workload metrics；sparse CNN FPGA metrics；super-resolution FPGA metrics；tiny NN / embedded FPGA metrics；video Transformer metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF12](#A-SSCC-SF12). 神经渲染与 3D Gaussian Splatting 加速

- Research problem：把 neural rendering/3DGS 从算法 pipeline 变成 FPS、quality、mixed precision、pre-culling 和 reconfigurable computation 的硬件对象。
- Background/current state：证据覆盖 `2023-2025`，共 `4` 条 selected rows。Impact status counts: {'needs_review': 2, 'impact_unverified': 2}。
- Technical route：路线从 computation skipping 的 neural rendering，到 3DGS FPGA reconfigurable architecture，再到 mixed precision/pre-culling mobile 3DGS。
- Representative work：[A-SSCC-2023-P0046](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0046); [A-SSCC-2024-P0096](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0096); [A-SSCC-2025-P0012](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0012); [A-SSCC-2025-P0027](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0027)。
- Team signals：author-line activity signal: Jongjun Park|Donghyeon Han|Junha Ryu|Dongseok Im et al.；不做排名或消歧。author-line activity signal: Hongseok Lee|Gwangtae Park|Wonhoon Park|Wooyoung Jo et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：3DGS FPS / mixed precision / pre-culling metrics；3DGS FPS/quality metrics；neural rendering FPS/quality metrics；official 3DGS rendering metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF13](#A-SSCC-SF13). 安全与 PQC 算术加速

- Research problem：边缘/IoT 安全把模乘、NTT、Keccak、Kyber/Dilithium 和非格 PQC 算术带入芯片实现。
- Background/current state：证据覆盖 `2018-2025`，共 `8` 条 selected rows。Impact status counts: {'needs_review': 5, 'impact_unverified': 3}。
- Technical route：路线从可变曲线 ECDSA、Kyber cryptoprocessor、M-LWR/M-LWE reconfigurable arithmetic、RISC-V/vector Kyber 到 fused CRYSTALS 和 isogeny/ABE frontier。
- Representative work：[A-SSCC-2018-P0049](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0049); [A-SSCC-2022-P0015](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0015); [A-SSCC-2022-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0031); [A-SSCC-2024-P0084](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0084); [A-SSCC-2025-P0134](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0134)。
- Team signals：author-line activity signal: Shotaro Sugiyama|Hiromitsu Awano|Makoto Ikeda；不做排名或消歧。author-line activity signal: Taishin Shimada|Makoto Ikeda；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：ABE curve-arithmetic metrics；ECDSA latency/energy metrics；Kyber chip energy metrics；Kyber cryptoprocessor metrics；Kyber implementation metrics need PDF audit；Kyber/Dilithium accelerator metrics；isogeny accelerator latency metrics；lattice-PQC FPGA/prototype metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF14](#A-SSCC-SF14). 芯片 memory、I/O 与 SoC 集成约束

- Research problem：真实 accelerator 的限制常来自 cache Vmin、NoC、HBM PHY、GPU SRAM、NVM weight storage 等 system/circuit boundary。
- Background/current state：证据覆盖 `2016-2025`，共 `5` 条 selected rows。Impact status counts: {'needs_review': 2, 'impact_unverified': 3}。
- Technical route：路线从 SRAM resiliency、buffer-less NoC scheduling 到 chiplet HBM PHY、pseudo-two-port SRAM 和 near-memory NVM microcontroller。
- Representative work：[A-SSCC-2016-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0031); [A-SSCC-2019-P0039](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0039); [A-SSCC-2024-P0062](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0062); [A-SSCC-2025-P0002](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0002); [A-SSCC-2025-P0066](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0066)。
- Team signals：author-line activity signal: Brian Zimmer|Pi-Feng Chiu|Borivoje Nikolic|Krste Asanovic；不做排名或消歧。author-line activity signal: Bo Wang|Manupa Karunarathne|Aditi Kulkarni Mohite|Tulika Mitra et al.；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：CGRA/NoC IoT accelerator metrics；GPU SRAM density/FPS metrics；HBM3 PHY bandwidth/power metrics；Vmin/cache resiliency metrics；edge-AI microcontroller / embedded-flash retention metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

### [A-SSCC-SF11](#A-SSCC-SF11). 可编程/非主流 PIM 与边界行

- Research problem：这个 subfield 用于防止把所有出现 FPGA/PIM/award 的论文都并入主线；边界样本说明哪些证据只能做上下文。
- Background/current state：证据覆盖 `2022-2025`，共 `4` 条 selected rows。Impact status counts: {'needs_review': 2, 'impact_unverified': 2}。
- Technical route：这条路线是分类边界，不是趋势主线；其中 P0102 主要服务 award/source conflict 审计。
- Representative work：[A-SSCC-2023-P0072](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0072); [A-SSCC-2024-P0112](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0112); [A-SSCC-2022-P0029](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0029); [A-SSCC-2025-P0102](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0102)。
- Team signals：author-line activity signal: Yuncheng Lu|Xin Zhang|Zehao Li|Bo Wang 0020 et al.；不做排名或消歧。author-line activity signal: Zhengzhe Wei|Yuqi Su|Tony Tae-Hyoung Kim|Yuanjin Zheng；不做排名或消歧。这些只是 activity signals，不是排名。
- Workload/artifact signals：ADC/DT DSM metrics；not project-main accelerator benchmark；FM-index workload metrics；GCUPS/W and GCPS/W official abstract metrics；PDE/pathfinding/trajectory metrics。
- Open questions：full PDF coverage、citation-structure audit、artifact/code reuse 仍不完整，除非具体行另有说明。

## 4. Development Trends（发展趋势）

- 神经计算从电路原语扩展到动态/生成式 workloads：2016 年的 dot-product/time-domain rows、2019-2020 年的 trainable/GAN rows，以及 2023-2025 年的 Transformer/LLM/diffusion rows 提供跨年证据。这是 venue-local trend，不是 adoption claim。
- CIM 从 SRAM/RRAM macros 走向 reliability、fine-tuning、Transformer/LLM 和 generative-AI CIM：证据来自 2019 SRAM CIM、2020 time-domain CIM、2021 CIM-SECDED、2023 CIMFormer/LOG-CIM，以及 2024-2025 hybrid/LoRA/MIDAS rows。
- Vision acceleration 分成三条线：sensor-near processing、FPGA pipeline acceleration、3DGS/neural rendering。2016-2025 的 depth/event/SLAM rows 支撑第一条，2018-2025 的 FPGA CNN/NMS/video rows 支撑第二条，2023-2025 的 neural rendering/3DGS rows 支撑第三条。
- Security/PQC 是一条跨年但引用信号较轻的线：2018 ECDSA 是 classical public-key arithmetic 的 anchor；2022-2025 的 Kyber、configurable lattice arithmetic、Kyber/Dilithium、isogeny 和 ABE rows 支撑一个 venue-provisional PQC arc。
- System constraints 成为明确的 accelerator context：cache Vmin、NoC、HBM3 PHY、GPU SRAM 和 embedded-Flash near-memory rows 显示，A-SSCC 经常从 memory/I/O/voltage/persistence 瓶颈来处理 accelerator。

## 5. Method Changes（方法变化）

- 从 title/session clustering 转向 full screening：`papers.csv` 和 `awards.csv` 的每一行都进入 `A-SSCC_screening_matrix.csv`，decision 只限 `deep_read`、`index_only`、`exclude_non_main` 和 `needs_review`。
- 从代表论文叙述转向 paper evidence rows：现在有 67 篇 selected papers 在 `A-SSCC_paper_evidence_matrix.csv` 中写入 WHY/HOW/WHAT/IMPACT/EVIDENCE 字段。
- Impact audit 仍是 first-pass：citation counts 使用 OpenAlex、Crossref 或 Semantic Scholar，具体取决于 subagents 找到的来源；adoption/toolchain reuse 除非有明确来源，否则保持 `impact_unverified`。
- Award rows 与 impact claims 分离：官方 ePapers 可以确认 paper metadata 和部分 Student Contest flags，但不能确认 canonical award-result status。

## 6. Missing Sources（缺失来源）

- 官方跨年 A-SSCC accepted-paper 和 award-result registry。
- 剩余 DOI 缺口：2016 年 21 行、2022 年 8 行、2025 年 10 行，以及 2026 partial marker。
- 所有 selected deep_read papers 的完整 IEEE Xplore/PDF 导出，尤其是旧年份 DOI/title-only rows。
- Consolidated Student Design Contest / Best Design / Distinguished Design canonical source；当前 awards 仍是 `needs_review` 或 `conflicting`。
- 用于 impact/team audit 的完整 author affiliation、institution 和 author-ID disambiguation。
- Citation graph structure、downstream reuse、benchmark standardization 和 toolchain/industry adoption sources。
