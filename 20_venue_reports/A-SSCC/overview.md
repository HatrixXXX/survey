# A-SSCC 论文图谱分析

## 1. 会议定位

A-SSCC 是 IEEE Asian Solid-State Circuits Conference。在本项目的 registry 中，正式 `venue_id` 是 `A-SSCC`；本次用户输入的 `ASSCC` 也按这个 venue 处理。它和 ISSCC、VLSI、JSSC、CICC 属于固态电路和芯片实作社区的同一条谱系。

对本项目来说，A-SSCC 的价值不在于重新概括 RF、ADC、PMIC 这类大类，而在于观察 AI 加速器、计算存内（CIM）、FPGA/vision pipeline、3DGS/neural rendering、PQC/security、memory/I/O/system constraints 这些主题进入芯片实现语境后，如何被拆成具体瓶颈。对应 claim <a id="ASSCC-001-C001"></a>[ASSCC-001-C001](#ASSCC-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 目前有 `949` 行，其中 2016-2025 的 accepted/proceedings rows 为 `948` 行，2026 只有 partial marker。按当前日期 `2026-06-27`，2026 录用论文尚未公开，因此 2026 缺论文清单属于 `normal_2026_partial`，不作为真实缺口；混合缺口中，只有 2026 partial 部分按这个状态处理，其余 metadata、award、source 缺口仍保留在 issue audit 中。

第二轮元数据（metadata）回填后，论文 DOI 覆盖为 `909/949`，paper verification status 为 {'needs_review': 40, 'verified': 909}。2025 官方 ePapers 页面覆盖 135/135 行，134 行补到了 track/session/abstract/keywords 级别；[A-SSCC-2025-P0053](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0053) 仍有标题/作者解析污染，保留 `needs_review`。2016 和 2022 DOI 已用严格的 Crossref title/container/year match 部分回填，但仍分别有 21 行和 8 行 DOI 缺口。

| 年份 | rows | DOI rows | official URL rows | 备注 |
|---|---:|---:|---:|---|
| 2016 | 90 | 69 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2017 | 83 | 83 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2018 | 90 | 90 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2019 | 88 | 88 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2020 | 41 | 41 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2021 | 103 | 103 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2022 | 92 | 84 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2023 | 99 | 99 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2024 | 127 | 127 | 0 | proceedings/Researchr/Crossref 混合来源 |
| 2025 | 135 | 125 | 135 | 官方 ePapers 详情页来源 |
| 2026 | 1 | 0 | 1 | 仅 partial marker |

## 3. Topic Taxonomy（主题分类）

第二轮之后，正文不再把 "AI accelerator / CIM / FPGA / security" 这类大领域词当主 topic。它们只作为入口；实际 deep dive 使用更细的研究问题和瓶颈标签。完整筛选见 `A-SSCC_screening_matrix.csv`，深读证据见 `A-SSCC_paper_evidence_matrix.csv`。

| subfield | 研究问题 / 瓶颈 | evidence rows | 证据状态 |
|---|---|---:|---|
| [A-SSCC-SF01](subfields.md#A-SSCC-SF01) 低能耗神经 MAC 与非标准算术原语 | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 3 | venue_provisional |
| [A-SSCC-SF02](subfields.md#A-SSCC-SF02) 端侧学习、自适应与动态 edge AI | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 6 | venue_provisional |
| [A-SSCC-SF03](subfields.md#A-SSCC-SF03) Transformer 与 LLM 状态/数据流加速 | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 4 | venue_provisional |
| [A-SSCC-SF04](subfields.md#A-SSCC-SF04) SRAM 混合信号/数字 CIM macro 演进 | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 4 | venue_provisional |
| [A-SSCC-SF05](subfields.md#A-SSCC-SF05) 时域、脉冲与稀疏自适应 CIM | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 2 | venue_provisional |
| [A-SSCC-SF06](subfields.md#A-SSCC-SF06) NVM/hybrid CIM 可靠性与 fine-tuning | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 3 | venue_provisional |
| [A-SSCC-SF07](subfields.md#A-SSCC-SF07) Transformer、LLM 与生成式 AI CIM | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 3 | venue_provisional |
| [A-SSCC-SF08](subfields.md#A-SSCC-SF08) 具身 edge perception 与 planning | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 2 | frontier_needs_review |
| [A-SSCC-SF09](subfields.md#A-SSCC-SF09) Depth、SLAM、event 与 sensor-near vision | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 12 | venue_provisional |
| [A-SSCC-SF10](subfields.md#A-SSCC-SF10) FPGA vision/DNN pipeline 加速器 | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 7 | venue_provisional |
| [A-SSCC-SF12](subfields.md#A-SSCC-SF12) 神经渲染与 3D Gaussian Splatting 加速 | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 4 | venue_provisional |
| [A-SSCC-SF13](subfields.md#A-SSCC-SF13) 安全与 PQC 算术加速 | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 8 | venue_provisional |
| [A-SSCC-SF14](subfields.md#A-SSCC-SF14) 芯片 memory、I/O 与 SoC 集成约束 | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 5 | venue_provisional |
| [A-SSCC-SF11](subfields.md#A-SSCC-SF11) 可编程/非主流 PIM 与边界行 | 见 subfield deep dive 的 WHY/HOW/WHAT 字段 | 4 | boundary_only |

## 4. Accepted Papers 筛选结果

本轮对 `papers.csv` 和 `awards.csv` 做了全量筛选（screening），共 `954` 行，decision 分布为 {'index_only': 870, 'deep_read': 70, 'needs_review': 10, 'exclude_non_main': 4}。筛选决定只使用 `deep_read`、`index_only`、`exclude_non_main`、`needs_review`。`deep_read` paper 为 67 篇；award rows 中有 3 行因为能对齐 paper，也标为 deep_read，但 award fact 本身不作为 verified impact evidence。

| subfield_id | subfield | evidence rows | active years | representative ids | status |
|---|---|---:|---|---|---|
| [A-SSCC-SF01](subfields.md#A-SSCC-SF01) | 低能耗神经 MAC 与非标准算术原语 | 3 | 2016-2018 | [A-SSCC-2016-P0006](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0006); [A-SSCC-2016-P0007](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0007); [A-SSCC-2018-P0001](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0001) | venue_provisional |
| [A-SSCC-SF02](subfields.md#A-SSCC-SF02) | 端侧学习、自适应与动态 edge AI | 6 | 2017-2025 | [A-SSCC-2017-P0060](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2017-P0060); [A-SSCC-2019-P0017](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0017); [A-SSCC-2020-P0037](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0037); [A-SSCC-2024-P0017](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0017) | venue_provisional |
| [A-SSCC-SF03](subfields.md#A-SSCC-SF03) | Transformer 与 LLM 状态/数据流加速 | 4 | 2023-2025 | [A-SSCC-2023-P0008](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0008); [A-SSCC-2023-P0030](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0030); [A-SSCC-2025-P0090](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0090); [A-SSCC-2025-P0093](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0093) | venue_provisional |
| [A-SSCC-SF04](subfields.md#A-SSCC-SF04) | SRAM 混合信号/数字 CIM macro 演进 | 4 | 2019-2025 | [A-SSCC-2019-P0010](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0010); [A-SSCC-2019-P0061](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0061); [A-SSCC-2023-P0020](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0020); [A-SSCC-2025-P0111](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0111) | venue_provisional |
| [A-SSCC-SF05](subfields.md#A-SSCC-SF05) | 时域、脉冲与稀疏自适应 CIM | 2 | 2020-2022 | [A-SSCC-2020-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0031); [A-SSCC-2022-P0048](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0048) | venue_provisional |
| [A-SSCC-SF06](subfields.md#A-SSCC-SF06) | NVM/hybrid CIM 可靠性与 fine-tuning | 3 | 2021-2025 | [A-SSCC-2021-P0032](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0032); [A-SSCC-2024-P0089](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0089); [A-SSCC-2025-P0065](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0065) | venue_provisional |
| [A-SSCC-SF07](subfields.md#A-SSCC-SF07) | Transformer、LLM 与生成式 AI CIM | 3 | 2022-2025 | [A-SSCC-2022-P0013](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0013); [A-SSCC-2023-P0013](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0013); [A-SSCC-2025-P0045](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0045) | venue_provisional |
| [A-SSCC-SF08](subfields.md#A-SSCC-SF08) | 具身 edge perception 与 planning | 2 | 2025-2025 | [A-SSCC-2025-P0094](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0094); [A-SSCC-2025-P0026](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0026) | frontier_needs_review |
| [A-SSCC-SF09](subfields.md#A-SSCC-SF09) | Depth、SLAM、event 与 sensor-near vision | 12 | 2016-2025 | [A-SSCC-2016-P0065](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0065); [A-SSCC-2018-P0078](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0078); [A-SSCC-2019-P0009](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0009); [A-SSCC-2021-P0042](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0042) | venue_provisional |
| [A-SSCC-SF10](subfields.md#A-SSCC-SF10) | FPGA vision/DNN pipeline 加速器 | 7 | 2018-2025 | [A-SSCC-2018-P0022](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0022); [A-SSCC-2019-P0058](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0058); [A-SSCC-2021-P0021](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0021); [A-SSCC-2021-P0092](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0092) | venue_provisional |
| [A-SSCC-SF12](subfields.md#A-SSCC-SF12) | 神经渲染与 3D Gaussian Splatting 加速 | 4 | 2023-2025 | [A-SSCC-2023-P0046](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0046); [A-SSCC-2024-P0096](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0096); [A-SSCC-2025-P0012](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0012); [A-SSCC-2025-P0027](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0027) | venue_provisional |
| [A-SSCC-SF13](subfields.md#A-SSCC-SF13) | 安全与 PQC 算术加速 | 8 | 2018-2025 | [A-SSCC-2018-P0049](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2018-P0049); [A-SSCC-2022-P0015](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0015); [A-SSCC-2022-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0031); [A-SSCC-2023-P0011](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0011) | venue_provisional |
| [A-SSCC-SF14](subfields.md#A-SSCC-SF14) | 芯片 memory、I/O 与 SoC 集成约束 | 5 | 2016-2025 | [A-SSCC-2016-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0031); [A-SSCC-2019-P0039](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0039); [A-SSCC-2024-P0062](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0062); [A-SSCC-2025-P0002](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0002) | venue_provisional |
| [A-SSCC-SF11](subfields.md#A-SSCC-SF11) | 可编程/非主流 PIM 与边界行 | 4 | 2022-2025 | [A-SSCC-2023-P0072](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0072); [A-SSCC-2024-P0112](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0112); [A-SSCC-2022-P0029](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2022-P0029); [A-SSCC-2025-P0102](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0102) | boundary_only |

旧版 title/session bucket 仍可作为粗检索入口，但不作为主结论。粗 bucket 中 RF/mmWave/wireline、data converters、PMIC 等行大量存在；本报告只在它们直接影响 accelerator、SoC、memory/I/O 或 security constraint 时纳入深读。

## 5. Award Papers（获奖论文）分析

award-source agent 未找到官方 consolidated A-SSCC awards registry。因此 `awards.csv` 的 5 行均按保守方式处理：4 行 `needs_review`，1 行 `conflicting`。官方 ePapers 能确认论文 metadata 和部分 Student Contest flag，但不能替代 award-result registry。[A-SSCC-2025-A04](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-A04) 尤其冲突：lab page 提到 Best Design Award，官方 ePapers 对应 paper page 标为 `Student Contest: No`，所以不能写成确定奖项事实。

| 年份 | 奖项名 | 标题 | paper_id | status | source |
|---|---|---|---|---|---|
| 2020 | Student Design Contest Best Design Award | An Energy-Efficient GAN Accelerator with On-chip Training for Domain Specific Optimization | [A-SSCC-2020-P0037](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0037) | needs_review / source_gap | https://hdh4797.wixsite.com/dhan/conference-1 |
| 2023 | Student Design Contest Distinguished Design Award | SESOMP: A Scalable and Energy-Efficient Self-Organizing Map Processor with Computing-In-Memory and Dead Neuron Pruning | [A-SSCC-2023-P0072](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0072) | needs_review / source_gap | https://epapers2.org/asscc2023/ESR/paper_details.php?paper_id=2105 |
| 2024 | Student Design Contest Distinguished Design Award | A Real-Time Optical-Flow-based SLAM FPGA Accelerator with Inter-Frame Similarity Exploitation and Correlation-Guided Mixed-Precision Flow Update | [A-SSCC-2024-P0021](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0021) | needs_review / source_gap | https://epapers2.org/asscc2024/ESR/paper_details.php?paper_id=8045 |
| 2025 | Student Design Contest Best Design Award | A 250kHz-BW 86.2dB-SNDR 176.7dB-FoMS Fully Dynamic kT/C Noise-Canceled DT DSM with SAR-Assisted Input FF and DNC | [A-SSCC-2025-P0102](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0102) | conflicting / conflicting | https://epapers2.org/asscc2025/ESR/paper_details.php?paper_id=4202 |
| 2025 | Student Design Contest Distinguished Design Award | VLA-Driven Manipulator on FPGA | [A-SSCC-2025-P0026](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0026) | needs_review / unresolved_alias | https://epapers2.org/asscc2025/ESR/paper_details.php?paper_id=4137 |

## 6. 代表性论文清单

- **An 8-bit, 16 input, 3.2 pJ/op switched-capacitor dot product circuit in 28-nm FDSOI CMOS** (2016, [A-SSCC-2016-P0006](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0006)). WHY：这是 A-SSCC 早期的神经 dot-product 电路原语，把模型推理问题表述为 switched-capacitor 能耗问题。HOW：使用 28nm FDSOI switched-capacitor dot-product 电路，支持 8-bit 输入和 16 输入累加。WHAT：面向紧凑 DNN 推理构件的 3.2 pJ/op dot-product circuit。IMPACT：OpenAlex 在 2026-06-27 记录 cited_by_count=48；后续采用未验证。Evidence: https://doi.org/10.1109/asscc.2016.7844125。
- **Time-domain neural network: A 48.5 TSOp/s/W neuromorphic chip optimized for deep learning and CMOS technology** (2016, [A-SSCC-2016-P0007](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0007)). WHY：展示了另一条早期路线，把神经计算映射到时域/类脑电路原语。HOW：实现面向 CMOS 工艺约束优化的 time-domain neural-network computation。WHAT：用于 deep-learning style compute 的 48.5 TSOp/s/W neuromorphic chip。IMPACT：OpenAlex 在 2026-06-27 记录 cited_by_count=25；采用未验证。Evidence: https://doi.org/10.1109/asscc.2016.7844126。
- **A 16K SRAM-Based Mixed-Signal In-Memory Computing Macro Featuring Voltage-Mode Accumulator and Row-by-Row ADC** (2019, [A-SSCC-2019-P0010](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0010)). WHY：这是 A-SSCC 中把 SRAM array 变成 mixed-signal dot-product macro 的早期证据。HOW：使用 6T SRAM、XNOR binary multiplier、pseudo-differential voltage-mode accumulation 和 row-by-row ADC。WHAT：65nm 16K SRAM IMC macro；abstract 级来源记录其在 5b ADC、0.5V 下达到 87 TOPS/W。IMPACT：Crossref 在 2026-06-27 记录 refby=31；采用未验证。Evidence: https://doi.org/10.1109/A-SSCC47793.2019.9056926。
- **A Time-Domain Computing-in-Memory based Processor using Predictable Decomposed Convolution for Arbitrary Quantized DNNs** (2020, [A-SSCC-2020-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0031)). WHY：这篇把 time-domain CIM 推到 processor-level 路线，用于 arbitrary quantized DNN，而不只是 macro。HOW：使用 predictable decomposed convolution 和 time-domain CIM。WHAT：A-SSCC TIMAQ-line processor；JSSC 2021 扩展版本已验证。IMPACT：A-SSCC 版本 Crossref 在 2026-06-27 记录 refby=4，JSSC 2021 版本 Crossref 记录 refby=30；后续扩展发表已验证。Evidence: https://doi.org/10.1109/A-SSCC48613.2020.9336145。
- **CIM-SECDED: A 40nm 64Kb Compute In-Memory RRAM Macro with ECC Enabling Reliable Operation** (2021, [A-SSCC-2021-P0032](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0032)). WHY：这篇把 RRAM CIM 的 reliability/ECC 放在中心，而不是只报 TOPS/W。HOW：使用 40nm 64Kb RRAM CIM macro，在 ADC readout 之后使用 CIM-compatible SECDED。WHAT：公开 PDF 报告最高 69.2x BER reduction，并在 RRAM variation 下恢复 accuracy。IMPACT：Crossref 在 2026-06-27 记录 refby=21；可靠性方法信号已验证，采用仍需审计。Evidence: https://doi.org/10.1109/A-SSCC53895.2021.9634742。
- **A 28nm 49.7TOPS/W Sparse Transformer Processor with Random-Projection-Based Speculation, Multi-Stationary Dataflow, and Redundant Partial Product Elimination** (2023, [A-SSCC-2023-P0008](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0008)). WHY：标志着 Transformer workload 进入 A-SSCC accelerator 证据链，核心瓶颈是 sparse attention/dataflow。HOW：结合 random-projection speculation、multi-stationary dataflow 和 redundant partial-product elimination。WHAT：28nm sparse Transformer processor，报告 49.7 TOPS/W。IMPACT：OpenAlex 在 2026-06-27 记录 cited_by_count=1；现在判断采用还太早。Evidence: https://doi.org/10.1109/A-SSCC58667.2023.10347953。
- **CIMFormer: A 38.9TOPS/W-8b Systolic CIM-Array Based Transformer Processor with Token-Slimmed Attention Reformulating and Principal Possibility Gathering** (2023, [A-SSCC-2023-P0013](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0013)). WHY：这篇明确处理 CIM processor 内的 Transformer attention 数据搬运和 weight reload。HOW：使用 token-slimmed attention reformulation、principal component gathering 和 systolic CIM array。WHAT：CIMFormer 报告 38.9 TOPS/W-8b Transformer processing。IMPACT：2026-06-27 的 Crossref/Semantic Scholar citation signal=4；采用未验证。Evidence: https://doi.org/10.1109/A-SSCC58667.2023.10347930。
- **A 33.6 FPS Embedding based Real-time Neural Rendering Accelerator with Switchable Computation Skipping Architecture on Edge Device** (2023, [A-SSCC-2023-P0046](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0046)). WHY：这是已选 A-SSCC 行中第一条明确把 neural rendering 放入 edge accelerator 场景的论文。HOW：面向 embedding-based neural rendering 使用 switchable computation skipping。WHAT：edge device 上 33.6 FPS real-time neural-rendering accelerator。IMPACT：Crossref 在 2026-06-27 记录 refby=9；存在同主题 follow-on rows，但因果采用未验证。Evidence: https://doi.org/10.1109/A-SSCC58667.2023.10347991。
- **KDA: Kyber and Dilithium Accelerator for CRYSTALS Suite of Post-Quantum Cryptography in Hybrid Multipath Delay Commutator Pipelined Architecture** (2024, [A-SSCC-2024-P0084](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0084)). WHY：从 Kyber-only acceleration 扩展到统一的 CRYSTALS suite accelerator。HOW：使用 hybrid multipath delay-commutator pipeline、switchable parallel/serial NTT、Karatsuba/Barrett reuse 和 cascaded Keccak。WHAT：面向 Kyber 和 Dilithium KEM/signature workloads 的 KDA accelerator。IMPACT：2026-06-27 的 S2 citationCount=1，Crossref refby=2；现在判断采用还太早。Evidence: https://doi.org/10.1109/A-SSCC60305.2024.10848993。
- **A 28nm 76.25TOPS/W RRAM/SRAM-Collaborative CIM Fine-Tuning Accelerator with RRAM-Endurance/Latency-Aware Weight Allocation for CNN and Transformer** (2024, [A-SSCC-2024-P0089](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0089)). WHY：把 CIM 从 inference 推向 fine-tuning，同时处理 RRAM endurance 和 write latency。HOW：使用 RRAM-MSB/SRAM-LSB collaborative macros、sparse/dense update engine 和 row-wise pipelined gradient dataflow。WHAT：28nm CNN/Transformer fine-tuning accelerator；官方 abstract 报告 76.25 TOPS/W macro 和 13.98 TOPS/W system efficiency。IMPACT：Crossref 在 2026-06-27 记录 refby=4；frontier signal 已验证，采用未验证。Evidence: https://doi.org/10.1109/A-SSCC60305.2024.10848596。
- **A 66.6 FPS High Quality Gaussian Splats Rendering FPGA Processor with Reconfigurable Computation Architecture** (2024, [A-SSCC-2024-P0096](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0096)). WHY：把 3D Gaussian Splatting 变成带 FPS、quality、reconfigurability 指标的具体 FPGA processor。HOW：使用 reconfigurable computation architecture 执行 Gaussian splats rendering。WHAT：66.6 FPS high-quality Gaussian Splats rendering FPGA processor。IMPACT：Crossref 在 2026-06-27 记录 refby=9；发现同主题 2025 follow-ons，采用未验证。Evidence: https://doi.org/10.1109/A-SSCC60305.2024.10848911。
- **A 102.5-Hz Real-Time FPGA Robot-Action-Planning Accelerator with Velocity-Estimation-Driven Behavior Prediction for Embodied Artificial Intelligence** (2025, [A-SSCC-2025-P0026](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0026)). WHY：这条 VLA/robot action planning 记录把 visual foundation model workload 连接到 FPGA/embodied edge control。HOW：使用面向 FPGA 的 robot action-planning acceleration；标题来自官方 ePapers，award alias 仍未解决。WHAT：2025 robot action-planning FPGA row；A05 award alias 为 `needs_review`。IMPACT：Crossref 在 2026-06-27 记录 refby=0；award alias 未验证。Evidence: https://epapers2.org/asscc2025/ESR/paper_details.php?paper_id=4137。
- **MobileSplat: A 105 FPS 3D Gaussian Splatting Rendering FPGA Processor with Mixed Precision Computation Path and Pre-Culling Architecture** (2025, [A-SSCC-2025-P0027](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0027)). WHY：MobileSplat 是 2024 A-SSCC 3DGS row 之后，2025 官方记录中的第二个 3DGS FPGA 点。HOW：面向 3DGS rendering 使用 mixed-precision computation path 和 pre-culling architecture。WHAT：105 FPS MobileSplat 3D Gaussian Splatting FPGA processor。IMPACT：Crossref 在 2026-06-27 记录 refby=1；现在判断采用还太早。Evidence: https://epapers2.org/asscc2025/ESR/paper_details.php?paper_id=4018。
- **PDAcc: A 541 Tokens/s@Llama-1.2B Effective Throughput Prefill-Decode Disaggregated MCM-Based Accelerator for Multi-Task Large Language Model Applications** (2025, [A-SSCC-2025-P0090](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0090)). WHY：这是直接的 LLM serving 证据：瓶颈是 prefill/decode disaggregation，而不只是 matrix MAC efficiency。HOW：使用 MCM-based prefill-decode disaggregated accelerator organization。WHAT：官方 2025 row 中，PDAcc 报告 Llama-1.2B 下 541 tokens/s effective throughput。IMPACT：OpenAlex 在 2026-06-27 记录 cited_by_count=0；现在判断采用还太早。Evidence: https://epapers2.org/asscc2025/ESR/paper_details.php?paper_id=4358。
- **FPGA Accelerator for 398bit, (2,2)-Isogeny Based Post-Quantum Cryptography** (2025, [A-SSCC-2025-P0134](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0134)). WHY：这是 Kyber/Dilithium 路线之后的非 lattice PQC 边界样本。HOW：使用 quad-core FPGA、five-stage Montgomery multiplier、lifetime-based temporary remapping 和 parallel schedule。WHAT：Xilinx VU9P 上的 398-bit (2,2)-isogeny accelerator；官方 abstract 报告 59.6 ms 和 87% latency reduction。IMPACT：2026-06-27 的 Crossref/S2 citations=0；现在判断采用还太早。Evidence: https://epapers2.org/asscc2025/ESR/paper_details.php?paper_id=4188。

## 7. 发展脉络

**从低能耗神经计算到动态/生成式 edge AI。** 2016 年的 switched-capacitor dot-product 和 time-domain neural chip，2019-2020 年的 trainable CNN/GAN on-chip training，以及 2023-2025 年的 Transformer/LLM/diffusion rows，共同构成 A-SSCC 内部从电路原语到动态模型负载的跨年线索。该判断由多篇论文支撑，但 adoption 多数仍是 `impact_unverified`。

**CIM / memory-centric AI。** 2019 SRAM mixed-signal/configurable CIM、2020 time-domain CIM、2021 CIM-SECDED、2023 CIMFormer/LOG-CIM、2024 RRAM/SRAM fine-tuning、2025 MIDAS/LoRA-CIM/942-TOPS SRAM CIM 共同说明：A-SSCC 的 CIM 线索从 macro/TOPS/W 走向 reliability、fine-tuning、Transformer/LLM 和 generative-AI workload。

**sensor-near / FPGA vision / neural rendering / 3DGS。** 2016-2025 的 depth、computational CIS、near-sensor SNN、SLAM、LiDAR、optical-flow rows 支撑 sensor-near vision；2018-2025 的 FPGA CNN/NMS/super-resolution/video Transformer 支撑 FPGA pipeline line；2023 neural rendering、2024 Gaussian Splats FPGA、2025 Garnet/MobileSplat 形成对 3DGS/神经渲染方向最直接的跨年 hook。

**Security/PQC 和 system constraints。** 2018 ECDSA 到 2022-2025 Kyber、Dilithium、isogeny、ABE rows 构成 venue-provisional PQC arc；2016 cache Vmin、2019 CGRA/NoC、2024 HBM3 PHY、2025 GPU SRAM 和 embedded-Flash near-memory MCU 显示，真实 accelerator 设计会被 memory/I/O/voltage/persistence 约束重塑。

## 8. 对博士入门者的阅读路线

**第一组：电路原语到 edge AI。** 读 [A-SSCC-2016-P0006](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0006)、[A-SSCC-2016-P0007](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2016-P0007)、[A-SSCC-2017-P0060](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2017-P0060)、[A-SSCC-2019-P0017](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0017)、[A-SSCC-2023-P0008](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0008)、[A-SSCC-2025-P0090](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0090)。重点看 workload 如何从 MAC/RNN 变成 Transformer/LLM prefill-decode。

**第二组：CIM 和 memory-centric AI。** 读 [A-SSCC-2019-P0010](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0010)、[A-SSCC-2020-P0031](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2020-P0031)、[A-SSCC-2021-P0032](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2021-P0032)、[A-SSCC-2023-P0013](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0013)、[A-SSCC-2024-P0089](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0089)、[A-SSCC-2025-P0065](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0065)。重点看 memory wall、可靠性、fine-tuning 和 LLM/LoRA 如何改变 CIM 问题定义。

**第三组：3DGS/FPGA/机器人视觉。** 读 [A-SSCC-2023-P0046](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2023-P0046)、[A-SSCC-2024-P0096](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0096)、[A-SSCC-2025-P0012](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0012)、[A-SSCC-2025-P0027](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0027)，再横向看 [A-SSCC-2024-P0021](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0021) 和 [A-SSCC-2025-P0026](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0026)。重点看 FPS、quality、mixed precision、pre-culling、SLAM/action-planning 这些硬件化瓶颈。

**第四组：系统边界。** 读 [A-SSCC-2019-P0039](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2019-P0039)、[A-SSCC-2024-P0062](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2024-P0062)、[A-SSCC-2025-P0002](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0002)、[A-SSCC-2025-P0066](../../10_corpus/A-SSCC/id_index.md#A-SSCC-2025-P0066) 和 PQC line。它们帮助理解真实芯片里的 memory bandwidth、NoC、HBM、SRAM density、安全加速与 power envelope。

## 9. 团队线索和代表成果

本轮只保留 team_signal，不做排名。证据矩阵中的 team_signal 来自 author line、official paper metadata 或 deep-read subagent 的机构线索。

| 团队/机构线索 | 关联方向 | 证据来源 | 使用限制 |
|---|---|---|---|
| KAIST / Hoi-Jun Yoo 相关 author line | edge AI、neural rendering、3DGS、SNN/DRL | author line、official paper metadata、deep-read 机构线索 | 只作为 activity signal；不表示团队排名或影响力强弱 |
| Tsinghua / Leibo Liu / Shaojun Wei / Shouyi Yin / Yang Hu author line | Transformer、LLM、CIM、AI processor | author line、official paper metadata、deep-read 机构线索 | 只作为 activity signal；需要后续实体边界复核 |
| Meng-Fan Chang / Xin Si / Kea-Tiong Tang 等 author line | SRAM/CIM、sensor-near rows | author line、official paper metadata、deep-read 机构线索 | 只作为 activity signal；不写成跨团队强弱判断 |
| SUTD / Bo Wang line | SESOMP 相关方向 | author line、official paper metadata、deep-read 机构线索 | 只作为 activity signal；不表示团队排名或影响力强弱 |

## 10. 与我的方向的连接点

对 3DGS/神经渲染/FPGA/加速器方向，A-SSCC 的价值在于提供样本：一个新 workload 进入芯片会议后，会怎样被拆成电路和 pipeline 问题。2024 Gaussian Splats FPGA processor 把 3DGS rendering 变成 FPS、quality、reconfigurable computation architecture 的硬件对象；2025 Garnet/MobileSplat 把 mixed precision、pre-culling 和 mobile 3DGS 继续推到官方 program。和 FPGA/FCCM/ASPLOS/MLSys 对照时，A-SSCC 提供的是 silicon/prototype/PPA 视角，可以补系统会议常缺的实现约束。

## 11. Missing Sources（缺失来源）

- 官方跨年 A-SSCC accepted-paper registry。
- 官方 Student Design Contest / Best Paper / Distinguished Paper / Best Design Award registry。
- 剩余 DOI/IEEE/PDF 导出：2016 21 行、2022 8 行、2025 10 行，以及 2026 partial marker。
- 2016-2026 全量 author affiliation、institution 和 author-ID 消歧。
- 全量 abstract/keywords/full text，尤其是旧年份 DOI/title-only rows。
- citation graph、follow-on reuse、artifact/code reuse、benchmark standardization 和 industry/toolchain adoption sources。
