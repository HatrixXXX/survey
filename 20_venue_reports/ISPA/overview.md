# ISPA 论文图谱分析（第二轮 回写）

## 1. 会议定位

本报告中的 `ISPA` 指 IEEE International Symposium/Conference on Parallel and Distributed Processing with Applications，不是 ISPASS。项目 registry 把它放在体系结构补充批次。ISPA 对本项目的作用是补充 parallel/distributed systems、edge/cloud、GPU/FPGA/PIM、memory/storage、graph/irregular workload 和应用型 accelerator 线索；它不单独定义全局 taxonomy。

## 2. 数据范围与来源状态

本轮仍覆盖 2016-2026。`papers.csv` 当前有 1437 行；`awards.csv` 从 6 行扩展到 10 行，新增 2023 官方 award certificate page 中的 4 条 award rows。2026 截至 2026-06-27 没有找到 accepted papers/proceedings/awards，按 `normal_2026_partial` 处理。

| 年份 | papers.csv 记录数 | 当前状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 69 | 完整/元数据部分 | Proceedings.com TOC |
| 2017 | 175 | 完整/元数据部分 | Proceedings.com TOC |
| 2018 | 139 | 完整/元数据部分 | Proceedings.com TOC |
| 2019 | 6 | still_open 部分 | 损坏 Proceedings.com TOC 提取 |
| 2020 | 90 | 完整/元数据部分 | Proceedings.com TOC |
| 2021 | 185 | 完整/元数据部分 | 官方程序 + 会议记录 TOC |
| 2022 | 104 | 完整/元数据部分 | Proceedings.com TOC |
| 2023 | 118 | 完整/元数据部分 | Proceedings.com TOC + 官方奖项页面 |
| 2024 | 335 | 官方接受列表基础 | 官方接受论文列表 |
| 2025 | 216 | 基于程序的部分 | Proceedings.com TOC |
| 2026 | 0 | normal_2026_partial | 官方路径不可用 |

第二轮 写入结果：

- `ISPA_screening_matrix.csv` 覆盖 1437 paper rows 和 10 award rows。
- `ISPA_paper_evidence_matrix.csv` 包含 49 篇 parent-selected deep-read rows。
- `subfields.md` 建立 10 个 venue-local subfields。
- targeted DOI backfill 已写入代表论文和 selected deep-read rows；bulk abstract/keywords/PDF metadata 仍缺。

## 3. 小领域图谱

| 子领域 | 研究问题 | 代表 evidence rows | 状态 |
|---|---|---|---|
| 分析和性能表征 | 如何解释 workload/system/accelerator 性能瓶颈 | P0003、P0417、P0534、P0758、P1142、P1339 | venue_provisional |
| FPGA/HLS DNN 实现 | 如何把 CNN/RNN/NAS 落到 FPGA/HLS/cluster | P0172、P0435、P0561、P0617、 P0956 | venue_provisional |
| 以内存为中心的 PIM 和混合内存 | 如何降低 PMem/PIM/CXL/hybrid memory 数据搬运 | P0118、P0587、P0713、P0908、P1363、P1401 | needs_review 用于 P0587 标题冲突 |
| GPU 运行时调度和卸载 | 如何调度 GPU kernel、DMA 和 GPU cluster | P0210、P0662、P0716、P1327、 P1424 | venue_provisional |
| DNN 算子编译器、低精度和数据流 | 如何做 fusion、layout、quantization、sparsity 和 DSA mapping | P0428、P0504、P0872、P1052、P1098、P1128、P1220、P1268、P1399 | venue_provisional |
| graph/GNN 不规则缓存 | 如何缓解 GNN/graph 不规则访存和 feature cache 压力 | P0627、P0750 | 小样本临时 |
| 图形/3DGS/Web3D 系统 | 如何处理 3D Gaussian/Web3D/3DGS 的 cache、precision、atomic 和 load balance | P0372、P0942、P1278、P1323 | 直接用户相关边界 |
| 边缘/自治/应用程序运行时边界 | 哪些应用运行时行只提供部署约束 | P0500、P0533、P0802、P0876、P1073 | 边界 |
| 安全/区块链/网络边界 | 哪些 award/network/security 行不支撑 accelerator 趋势 | P0480, P0551, P0841, P0870 | negative_boundary |
| 字符串 workload 加速 | 如何加速 string matching/string operations | P0059, P0379 | venue_provisional |

## 4. 奖项审核

2021 award rows 保留 `needs_review`：`https://www.cloud-conf.net/ispa2021/award.html` 是官方 ISPA 2021 URL，正文写 ISPA 2021，但页面 heading 写 KSEM 2021。A02 还有 author-list conflict，A04 有 author-order conflict。因此本轮只把它作为 partial canonical source，不把 2021 awards 写成无冲突 verified。

2023 award rows 已新增并标 verified：官方页面 `http://ieee-hust-ncc.org/2023/ISPA/bestpaper.html` 列出 4 个 certificate-based award papers，并和现有 `papers.csv` 行对齐：[ISPA-2023-P0841](../../10_corpus/ISPA/id_index.md#ISPA-2023-P0841)、[ISPA-2023-P0870](../../10_corpus/ISPA/id_index.md#ISPA-2023-P0870)、[ISPA-2023-P0876](../../10_corpus/ISPA/id_index.md#ISPA-2023-P0876)、[ISPA-2023-P0802](../../10_corpus/ISPA/id_index.md#ISPA-2023-P0802)。

2022、2024、2025 仍未找到 canonical award pages。2026 按 normal partial 处理。

## 5. 代表性论文与 Evidence 状态

Second wave 选出 49 篇 evidence rows。进入 evidence matrix 的论文均有 WHY/HOW/WHAT/IMPACT/EVIDENCE 字段；read_depth 多数为 `title`，并明确标注 PDF 未完全读取。Crossref citation count 只作为弱 impact signal，检索日期统一为 2026-06-27。

直接相关线索：

- 3DGS/Web3D：`AMQGaussian`、`Dependency-Aware Edge Caching for Web3D`、`GSGPU`。
- FPGA/HLS：FPGA LSTM、MobileNetV2 FPGA、CNN FPGA 存储/数据流、FPGA NAS、HLS4ML FPGA 集群。
- DNN/加速器数据流：DLFusion、SCRA、Funnel、Low-bit CUTLASS GEMM、ViTa、CRSPU、QVU。
- 内存/运行时：Racetrack PIM CNN、HyperKV、EPGraph、LLM 检查点混合内存、CXL热点页调度、GPU集群调度。

## 6. 发展趋势

趋势只在 venue-local、title/DOI/proceedings metadata 层成立：

1. Accelerator 线从早期 FPGA/PIM/string accelerator 扩展到 compiler、systolic/sparse、GEMM/ViT/quantization 和 3DGS。支撑论文集合：P0059、P0118、P0428、P0872、P1052、P1220、P1268、P1323、P1399。
2. GPU runtime 线从 kernel scheduling 扩展到 distributed DL sharing、DMA offloading 和 GPU cluster scheduling。支撑论文集合：P0210、P0662、P0716、P1327、P1424。
3. Memory-centric 线从 racetrack/PIM 与 PMem 扩展到 LLM checkpointing、CXL 和 racetrack remapping。支撑论文集合：P0118、P0587、P0713、P0908、P1363、P1401。
4. 3DGS/Web3D 是近年 frontier。支撑论文集合：P0942、P1278、P1323；P0372 是 graphics cache bridge。

## 7. 团队线索

本轮不做团队排名。团队相关内容只写 `author_string_only` 或 `needs_review`。

| 作者/团队线索 | 信号类型 | 证据状态 | 使用限制 |
|---|---|---|---|
| Hongxu Jiang / Yonghua Zhang | author-string activity signal | `author_string_only` 或 `needs_review` | 不能写成团队领先性 |
| Quan Chen / Minyi Guo | author-string activity signal | `author_string_only` 或 `needs_review` | 不能写成团队领先性 |
| Xuehai Zhou / Lei Gong | author-string activity signal | `author_string_only` 或 `needs_review` | 不能写成团队领先性 |
| Dongrui Fan / Xiaochun Ye | author-string activity signal | `author_string_only` 或 `needs_review` | 不能写成团队领先性 |

## 8. 缺失来源

- 缺 ISPA 2016-2025 IEEE Xplore/DBLP 批量 abstract、keywords、PDF-level metadata。
- 缺 ISPA 2019 可解析 TOC 或官方 program。
- 缺 ISPA 2022、2024、2025 official award pages。
- 缺 ISPA 2026 official accepted papers/proceedings/awards；当前只按 normal partial 处理。
- 缺重点论文的 PDF/artifact/code audit：GSGPU、AMQGaussian、DLFusion、HLS4ML FPGA cluster、Funnel、QVU、CXL hot-page scheduling。
- 缺作者entity disambiguation和跨会议 team/entity 对照。
