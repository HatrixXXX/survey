# 跨会议小领域综合报告

日期：`2026-06-28`

## 1. 范围和输入

本报告整合 26 个 venue 的第二轮 subfield deep dive、paper evidence matrix、实体消歧、影响力深审和 workload/artifact inventory。主分类按具体研究问题组织，不按 FPGA、EDA、HPC、IC、ML systems 这类大领域词组织。

主要输入：

- `20_venue_reports/*/overview.md`
- `20_venue_reports/*/subfields.md`
- `10_corpus/*/papers.csv`
- `10_corpus/*/awards.csv`
- `40_synthesis/workload_artifact_inventory/*.csv`

配套输出：

- `cross_venue_subfield_inventory.csv`
- `representative_paper_matrix.csv`
- `trend_claims.csv`

## 2. 全局小领域图谱

| id | 小领域 | 证据行数 | venue 数 | 状态 |
|---|---|---:|---:|---|
| [GSF-01](../third_wave_field_synthesis.md#GSF-01) | LLM serving state、KV/cache、attention 与 token-memory bottleneck | 309 | 22 | strong, frontier-heavy |
| [GSF-02](../third_wave_field_synthesis.md#GSF-02) | 神经渲染、NeRF、3DGS 与场景重建 pipeline 瓶颈 | 168 | 20 | strong emerging |
| [GSF-03](../third_wave_field_synthesis.md#GSF-03) | 面向 memory-wall workload 的 CIM/PIM/near-memory execution | 230 | 20 | strong |
| [GSF-04](../third_wave_field_synthesis.md#GSF-04) | HLS、compiler、autotuning 与 hardware-generation closure | 186 | 20 | strong |
| [GSF-05](../third_wave_field_synthesis.md#GSF-05) | 物理/PPA、routing、timing、chiplet、3DIC 与 package closure | 81 | 11 | moderate-strong |
| [GSF-06](../third_wave_field_synthesis.md#GSF-06) | 低精度、稀疏、LUT/native arithmetic 与近似神经执行 | 160 | 16 | strong |
| [GSF-07](../third_wave_field_synthesis.md#GSF-07) | 不规则图、稀疏张量、点云与数据依赖 workload mapping | 112 | 12 | moderate-strong |
| [GSF-08](../third_wave_field_synthesis.md#GSF-08) | Benchmark、profiling、simulator、artifact 与证据有效性基础设施 | 111 | 19 | strong as methodology |
| [GSF-09](../third_wave_field_synthesis.md#GSF-09) | 边缘机器人、sensor-near vision、SLAM 与具身低时延感知 | 172 | 17 | moderate-strong |
| [GSF-10](../third_wave_field_synthesis.md#GSF-10) | 分布式训练、加速器编排、collectives 与数据中心 fabric 瓶颈 | 109 | 7 | moderate-strong |
| [GSF-11](../third_wave_field_synthesis.md#GSF-11) | 内存容量、CXL/far-memory、storage、I/O 与 NoC/data-movement 瓶颈 | 144 | 14 | strong |
| [GSF-12](../third_wave_field_synthesis.md#GSF-12) | 加速系统的安全性、正确性、可靠性与验证约束 | 83 | 18 | moderate |

完整字段、local subfield 对应关系、role mix 和限制见 `cross_venue_subfield_inventory.csv`。

## 3. 主要结论

LLM 推理已经分化为状态与存储问题，而不只是 kernel 问题。最强的跨 venue 信号是 [GSF-01](../third_wave_field_synthesis.md#GSF-01)：KV/cache 驻留、prefill/decode 重叠、attention 数据搬运、量化压力和 token 级时延同时出现在 systems、architecture、FPGA、EDA 和 silicon venues 中。该方向不应被简单并入 T02 operator fusion 或 T08 runtime。相关记录仍然偏前沿，尤其集中在 2025-2026 年。

神经渲染和 3DGS 已经出现在图形学 venue 之外。证据覆盖 DAC、DATE、ISCA、MICRO、HPCA、ASPLOS、ISCAS、VLSI、JSSC、MLSys 和 PACT。反复出现的瓶颈包括排序、光栅化、Gaussian/ray traversal、cache reuse、移动端帧时延和训练内存。这是一个实际存在的新兴小领域，但还不能标为 stable，因为许多 3DGS 记录很新，部分证据仍停留在 program 或 abstract 层级。

PIM/CIM 与 memory-side execution 需要拆分。SRAM/RRAM/analog CIM macros、HBM/DRAM PIM、near-storage/near-memory systems 和 CXL/NDP platforms 都以 memory wall 为共同动机，但它们的 artifact、指标和物理约束不同。本次综合只把 [GSF-03](../third_wave_field_synthesis.md#GSF-03) 保留为父类。

HLS/compiler/EDA 证据已经不再只是传统 HLS DSE。第二轮记录加入了 LLM-assisted Verilog/RTL/HLS generation、assertion generation、RTL benchmarks、agentic optimization 和 QoR prediction。这支持把 T07 拆为 HLS/DSE、tensor/compiler codegen，以及 LLM-assisted hardware design/verification benchmark 几条线索。

Benchmark/profiling/artifact infrastructure 是唯一被升级为 stable 的 topic，且仅作为跨领域评价轴。它具有跨 venue 证据、workload/profiling inventory 支撑，以及代表性工具和 benchmark 记录。这并不表示任何 workload family 已经 stable。

团队证据只能作为线索使用。已解析的 team signal、部分项目/团队信号和冲突说明不用于团队排名，也不从发表频次或 citation count 推断团队领先性。

## 4. 代表性阅读路线

`representative_paper_matrix.csv` 为每个小领域提供了一条压缩阅读路线。表中区分 origin/formation、milestone、tool/benchmark 和 frontier 等角色。例如：

- LLM serving 路线：[MLSys-2021-P0016](../../10_corpus/MLSys/id_index.md#MLSys-2021-P0016)、[HPCA-2021-P0061](../../10_corpus/HPCA/id_index.md#HPCA-2021-P0061)、[MLSys-2024-P0005](../../10_corpus/MLSys/id_index.md#MLSys-2024-P0005)、[MLSys-2025-P0015](../../10_corpus/MLSys/id_index.md#MLSys-2025-P0015)、[FPGA-2026-P0005](../../10_corpus/FPGA/id_index.md#FPGA-2026-P0005)。
- 3D/neural rendering 路线：[HOTCHIPS-2018-P0013](../../10_corpus/HOTCHIPS/id_index.md#HOTCHIPS-2018-P0013)、[FPT-2022-P0050](../../10_corpus/FPT/id_index.md#FPT-2022-P0050)、[ISCA-2023-P0038](../../10_corpus/ISCA/id_index.md#ISCA-2023-P0038)、[ASPLOS-2025-P0097](../../10_corpus/ASPLOS/id_index.md#ASPLOS-2025-P0097)、[MLSys-2026-P0150](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0150)。
- FPGA/HLS closure 路线：[FPT-2016-P0021](../../10_corpus/FPT/id_index.md#FPT-2016-P0021)、[FPGA-2018-P0027](../../10_corpus/FPGA/id_index.md#FPGA-2018-P0027)、[FPGA-2019-P0027](../../10_corpus/FPGA/id_index.md#FPGA-2019-P0027)、[FPGA-2021-P0007](../../10_corpus/FPGA/id_index.md#FPGA-2021-P0007)、[FCCM-2023-P0010](../../10_corpus/FCCM/id_index.md#FCCM-2023-P0010)。
- Evaluation infrastructure 路线：[ISCA-2018-P0023](../../10_corpus/ISCA/id_index.md#ISCA-2018-P0023)、[ISCA-2020-P0045](../../10_corpus/ISCA/id_index.md#ISCA-2020-P0045)、[TCAD-2018-P0118](../../10_corpus/TCAD/id_index.md#TCAD-2018-P0118)、[MICRO-2022-P0086](../../10_corpus/MICRO/id_index.md#MICRO-2022-P0086)、[MLSys-2026-P0099](../../10_corpus/MLSys/id_index.md#MLSys-2026-P0099)。

带有 recent/frontier、program-only 或 audit-status mismatch caveat 的记录已在矩阵中标注。它们应被视为候选项，而不是已经定型的经典文献。

## 5. 趋势判断

趋势判断存放在 `trend_claims.csv` 中，并包含支撑 venue 和 evidence ID。主要判断如下：

1. LLM acceleration 正在从通用 Transformer kernels 转向 state/cache/serving bottlenecks。
2. 神经渲染和 3DGS 已成为跨 venue 的 accelerator frontier。
3. PIM/CIM work 越来越多地面向 Transformer/LLM attention 和 memory state，而不只面向 CNN macros。
4. HLS/compiler/EDA work 正在转向 LLM-assisted code、assertions 和 benchmarks。
5. 物理实现和封装约束已经成为 accelerator maps 的一部分。
6. Benchmark/profiling/artifact infrastructure 本身就是一个证据问题。
7. Sparse/irregular workloads 需要拆分为 neural sparse/tensor、graph/GNN/recommendation 和 scientific sparse kernel 几条线。
8. Edge robotics 与 sensor-near perception 和 neural rendering/3DGS 相邻，但并不相同。
9. Datacenter accelerator research 越来越受 fabric 和 orchestration 限制。
10. Security、correctness 和 dependability 是跨领域约束，而不是单独一条性能谱系。

## 6. Taxonomy 修订

`01_control/TOPIC_TAXONOMY.md` 只在状态层面更新；证据细节仍以本综合报告和趋势表为准。

建议状态如下：

- T01：`provisional`, `split_candidate`
- T02：`provisional`, `split_candidate`
- T03：`provisional`, `split_candidate`
- T04：`provisional`, `split_candidate`
- T05：`provisional`, `split_candidate`
- T06：`provisional`
- T07：`provisional`, `split_candidate`
- T08：`provisional`, `merge_candidate`
- T09：`provisional`, `split_candidate`
- T10：`provisional`, `split_candidate`
- T11：`stable`，仅作为跨领域 evaluation/profiling/artifact evidence infrastructure
- T12：`provisional`, `split_candidate`

## 7. 团队线索使用规则

可以使用的表述：

- 将 `resolved_team_signal` 作为有来源支撑的团队、项目、实验室或公司线索。
- 将 `partial_team_signal` 仅作为带 caveat 的论文或项目级信号。
- 将 author-cluster 或 institution-cluster 证据只作为阅读线索。
- 除非已有官方 proceedings 和更强的实体证据，否则将 2026 年记录视为 frontier/emerging。

不安全的表述：

- 不对团队排名。
- 不写“leading team”或“strongest group”。
- 不把机构字符串直接合并成同一个实验室或公司团队。
- 不用当前 affiliation 改写历史论文发表时的 affiliation。
- 不用 citation count 或 row frequency 表示团队实力。

## 8. 缺失来源（Missing Sources）

- 若干 frontier rows 的 2026 年最终 proceedings、DOI 和 artifact pages。
- Frontier-heavy subfields 的 citation-context sampling。
- 3DGS/neural rendering 的直接 graphics/vision venue evidence。
- 在 T04 能够稳定之前，还需要更多 robotics/VLA/world-model hardware evidence。
- 主要工具和 benchmark 的 runnable status checks。
- 对 `representative_paper_matrix.csv` 中 audit/status mismatches 的人工校对。

## 9. AI 辅助说明（AI Assistance Disclosure）

本报告由 AI 基于本地项目证据文件辅助生成。所有判断均限制在上文列出的矩阵、审计表和 inventory 范围内。
