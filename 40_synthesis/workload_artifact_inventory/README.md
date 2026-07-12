# Workload / Artifact 清单

## 1. 范围

本报告只整理可运行 workload、profiling 字段、benchmark、artifact、代码库、数据集和工具入口；本阶段没有搭环境、没有下载数据集、没有运行 benchmark，也没有复现实验。所有 artifact 状态按 `SOURCE_POLICY.md` 处理：公开仓库只能写成 `runnable_claimed` 或 `runnable_unchecked`，除非本项目实际执行过，否则不写“reproduced”一类结论 <a id="WORKLOAD-ARTIFACT-001-C038"></a>[WORKLOAD-ARTIFACT-001-C038](#WORKLOAD-ARTIFACT-001-C038)<a id="WORKLOAD-ARTIFACT-001-C039"></a>[WORKLOAD-ARTIFACT-001-C039](#WORKLOAD-ARTIFACT-001-C039)。

本目录保留 3 个库存表：

| 文件 | 行数 | 用途 |
| --- | ---: | --- |
| `workload_inventory.csv` | 21 | 记录 3DGS/neural rendering、LLM serving、robotics edge real-time、HPC kernels、FPGA/HLS、PIM/CXL、benchmark/profiling 七类 workload。 |
| `profiling_field_inventory.csv` | 50 | 记录字段定义、单位、采集方式、工具/硬件要求和解释风险。 |
| `benchmark_artifact_inventory.csv` | 71 | 记录公开 benchmark、代码仓库、数据集、工具、规范和访问状态。 |

数量由 CSV 解析检查得到 <a id="WORKLOAD-ARTIFACT-001-C041"></a>[WORKLOAD-ARTIFACT-001-C041](#WORKLOAD-ARTIFACT-001-C041)。

## 2. Workload 家族

| 类别 | Workload ID | 清单重点 |
| --- | --- | --- |
| 3DGS / neural rendering | <a id="WA-WL-3D-001"></a>[WA-WL-3D-001](#WA-WL-3D-001) to <a id="WA-WL-3D-004"></a>[WA-WL-3D-004](#WA-WL-3D-004) | 3DGS 渲染、NeRF/hash-grid 推理、3DGS 训练/大场景 offload、Gaussian-map SLAM。核心字段是 frame latency、Gaussian 数量、tile/bin/sort 阶段、显存、PSNR/SSIM/LPIPS。3DGS 官方实现、gsplat、NerfBaselines 和 SplaTAM 提供可审计入口，但均未运行 <a id="WORKLOAD-ARTIFACT-001-C001"></a>[WORKLOAD-ARTIFACT-001-C001](#WORKLOAD-ARTIFACT-001-C001)<a id="WORKLOAD-ARTIFACT-001-C004"></a>[WORKLOAD-ARTIFACT-001-C004](#WORKLOAD-ARTIFACT-001-C004)<a id="WORKLOAD-ARTIFACT-001-C007"></a>[WORKLOAD-ARTIFACT-001-C007](#WORKLOAD-ARTIFACT-001-C007)。 |
| LLM serving | <a id="WA-WL-LLM-001"></a>[WA-WL-LLM-001](#WA-WL-LLM-001) to <a id="WA-WL-LLM-003"></a>[WA-WL-LLM-003](#WA-WL-LLM-003) | prefill/decode、KV-cache/long-context、MoE/structured/speculative decoding。核心字段是 TTFT、TPOT、throughput、goodput under SLO、KV bytes/token、prefix-cache hit ratio、energy/token。vLLM/PagedAttention、Orca、DistServe、SGLang 等来源支持这些拆分 <a id="WORKLOAD-ARTIFACT-001-C009"></a>[WORKLOAD-ARTIFACT-001-C009](#WORKLOAD-ARTIFACT-001-C009)<a id="WORKLOAD-ARTIFACT-001-C010"></a>[WORKLOAD-ARTIFACT-001-C010](#WORKLOAD-ARTIFACT-001-C010)<a id="WORKLOAD-ARTIFACT-001-C011"></a>[WORKLOAD-ARTIFACT-001-C011](#WORKLOAD-ARTIFACT-001-C011)<a id="WORKLOAD-ARTIFACT-001-C013"></a>[WORKLOAD-ARTIFACT-001-C013](#WORKLOAD-ARTIFACT-001-C013)。 |
| Robotics edge real-time | <a id="WA-WL-ROB-001"></a>[WA-WL-ROB-001](#WA-WL-ROB-001) to <a id="WA-WL-ROB-003"></a>[WA-WL-ROB-003](#WA-WL-ROB-003) | visual/VIO SLAM、LiDAR/map/planning、VLA/action policy inference。平均 FPS 不足以描述实时性；应记录 sensor deadline、p95/p99 tracking latency、map update/query latency、ATE/RPE、action latency 和 power。ORB-SLAM3、SLAMBench、RobotPerf、FAST-LIO 和 OpenVLA 是后续审计入口 <a id="WORKLOAD-ARTIFACT-001-C014"></a>[WORKLOAD-ARTIFACT-001-C014](#WORKLOAD-ARTIFACT-001-C014)<a id="WORKLOAD-ARTIFACT-001-C015"></a>[WORKLOAD-ARTIFACT-001-C015](#WORKLOAD-ARTIFACT-001-C015)<a id="WORKLOAD-ARTIFACT-001-C016"></a>[WORKLOAD-ARTIFACT-001-C016](#WORKLOAD-ARTIFACT-001-C016)<a id="WORKLOAD-ARTIFACT-001-C018"></a>[WORKLOAD-ARTIFACT-001-C018](#WORKLOAD-ARTIFACT-001-C018)。 |
| HPC kernels | <a id="WA-WL-HPC-001"></a>[WA-WL-HPC-001](#WA-WL-HPC-001) to <a id="WA-WL-HPC-003"></a>[WA-WL-HPC-003](#WA-WL-HPC-003) | dense tensor/fused kernels、sparse/graph/irregular kernels、stencil/FFT/scan/sort/reduction motifs。HPL、HPCG、NAS NPB、PolyBench、GAPBS、Graph500 覆盖了 dense、sparse、graph、CFD-derived 和 static-control kernel 入口 <a id="WORKLOAD-ARTIFACT-001-C019"></a>[WORKLOAD-ARTIFACT-001-C019](#WORKLOAD-ARTIFACT-001-C019)<a id="WORKLOAD-ARTIFACT-001-C020"></a>[WORKLOAD-ARTIFACT-001-C020](#WORKLOAD-ARTIFACT-001-C020)<a id="WORKLOAD-ARTIFACT-001-C021"></a>[WORKLOAD-ARTIFACT-001-C021](#WORKLOAD-ARTIFACT-001-C021)<a id="WORKLOAD-ARTIFACT-001-C023"></a>[WORKLOAD-ARTIFACT-001-C023](#WORKLOAD-ARTIFACT-001-C023)。 |
| FPGA / HLS | <a id="WA-WL-FPGA-001"></a>[WA-WL-FPGA-001](#WA-WL-FPGA-001) to <a id="WA-WL-FPGA-003"></a>[WA-WL-FPGA-003](#WA-WL-FPGA-003) | HLS dataflow kernel、accelerator generation/DSE、host/cloud/memory-streaming integration。字段应区分 HLS 估计、implementation report、board counter 和外部功耗测量。Vitis HLS、Rosetta、HeteroCL、AutoSA、Shuhai、LightningSim、RealProbe 是主要入口 <a id="WORKLOAD-ARTIFACT-001-C026"></a>[WORKLOAD-ARTIFACT-001-C026](#WORKLOAD-ARTIFACT-001-C026)<a id="WORKLOAD-ARTIFACT-001-C027"></a>[WORKLOAD-ARTIFACT-001-C027](#WORKLOAD-ARTIFACT-001-C027)<a id="WORKLOAD-ARTIFACT-001-C030"></a>[WORKLOAD-ARTIFACT-001-C030](#WORKLOAD-ARTIFACT-001-C030)<a id="WORKLOAD-ARTIFACT-001-C031"></a>[WORKLOAD-ARTIFACT-001-C031](#WORKLOAD-ARTIFACT-001-C031)。 |
| PIM / CXL memory | <a id="WA-WL-PIM-001"></a>[WA-WL-PIM-001](#WA-WL-PIM-001) to <a id="WA-WL-PIM-003"></a>[WA-WL-PIM-003](#WA-WL-PIM-003) | PIM/CIM Transformer attention、CXL/far-memory/tiered-memory、near-data graph/pointer/sparse workloads。应记录远端内存延迟/带宽、page migration、PIM bank/array utilization、conversion/precision overhead、energy/access 或 energy/token。CXL 规范、Clio、Nimble、AttAcc 是当前入口 <a id="WORKLOAD-ARTIFACT-001-C032"></a>[WORKLOAD-ARTIFACT-001-C032](#WORKLOAD-ARTIFACT-001-C032)<a id="WORKLOAD-ARTIFACT-001-C033"></a>[WORKLOAD-ARTIFACT-001-C033](#WORKLOAD-ARTIFACT-001-C033)<a id="WORKLOAD-ARTIFACT-001-C034"></a>[WORKLOAD-ARTIFACT-001-C034](#WORKLOAD-ARTIFACT-001-C034)。 |
| Benchmark / profiling | <a id="WA-WL-BENCH-001"></a>[WA-WL-BENCH-001](#WA-WL-BENCH-001) to <a id="WA-WL-BENCH-002"></a>[WA-WL-BENCH-002](#WA-WL-BENCH-002) | 将 profiler、benchmark、artifact status 纳入统一审计。必须记录 tool version、input shape、baseline provenance、run count/variance、power boundary 和 artifact access/status。Roofline、MLPerf、ACM artifact policy 和各类 profiler 文档是方法来源 <a id="WORKLOAD-ARTIFACT-001-C025"></a>[WORKLOAD-ARTIFACT-001-C025](#WORKLOAD-ARTIFACT-001-C025)<a id="WORKLOAD-ARTIFACT-001-C035"></a>[WORKLOAD-ARTIFACT-001-C035](#WORKLOAD-ARTIFACT-001-C035)<a id="WORKLOAD-ARTIFACT-001-C036"></a>[WORKLOAD-ARTIFACT-001-C036](#WORKLOAD-ARTIFACT-001-C036)<a id="WORKLOAD-ARTIFACT-001-C037"></a>[WORKLOAD-ARTIFACT-001-C037](#WORKLOAD-ARTIFACT-001-C037)。 |

## 3. Profiling 字段

`profiling_field_inventory.csv` 不是 benchmark 结果表，而是后续实验或 artifact 审计时必须收集的字段目录。每个字段都写了单位、采集方法、需要的硬件/工具和解释风险。

几个需要严格执行的解释规则：

- 3DGS 的 FPS、frame latency、quality metrics 不能脱离 scene、resolution、Gaussian count、pruning/densification policy 单独比较 [WORKLOAD-ARTIFACT-001-C001](#WORKLOAD-ARTIFACT-001-C001)[WORKLOAD-ARTIFACT-001-C004](#WORKLOAD-ARTIFACT-001-C004)。
- LLM serving 的 throughput 不能替代 SLO 内 goodput；prefill、decode、queueing 和 KV-cache 状态必须分开记录 [WORKLOAD-ARTIFACT-001-C009](#WORKLOAD-ARTIFACT-001-C009)[WORKLOAD-ARTIFACT-001-C011](#WORKLOAD-ARTIFACT-001-C011)。
- Robotics workload 要用 deadline miss、tail latency 和任务质量一起看；平均 tracking FPS 不足以判断闭环可用性 [WORKLOAD-ARTIFACT-001-C015](#WORKLOAD-ARTIFACT-001-C015)[WORKLOAD-ARTIFACT-001-C016](#WORKLOAD-ARTIFACT-001-C016)。
- HPC/accelerator 领域可以用 Roofline 的 arithmetic intensity 辅助判断瓶颈，但它不是单独的证明；memory level 和计数来源必须写清楚 [WORKLOAD-ARTIFACT-001-C025](#WORKLOAD-ARTIFACT-001-C025)。
- FPGA/HLS 字段要标注来源是 HLS report、RTL cosim、implementation report 还是 board measurement；II 和 latency 估计不能直接当作板上结果 [WORKLOAD-ARTIFACT-001-C026](#WORKLOAD-ARTIFACT-001-C026)。
- PIM/CXL 的容量扩展、near-memory offload 或 CIM 计算都要同时写延迟、带宽、迁移/同步、精度和能耗边界，避免只记录理想带宽或峰值计算 [WORKLOAD-ARTIFACT-001-C032](#WORKLOAD-ARTIFACT-001-C032)[WORKLOAD-ARTIFACT-001-C033](#WORKLOAD-ARTIFACT-001-C033)。

## 4. Benchmark 与 artifact

`benchmark_artifact_inventory.csv` 记录 71 个条目，类型包括代码仓库、benchmark suite、数据集、profiling tool、simulator、ruleset、official docs 和 specification。状态含义如下：

- `runnable_claimed`：来源页面或 README 提供了运行/安装入口，但本项目没有执行。
- `runnable_unchecked`：公开入口存在，但依赖、硬件、脚本或数据路径还没审完。
- `access_restricted`：数据集、规范或访问条款需要额外下载、注册或许可确认。
- `archived_only`：规范、政策或文档类来源，不是可执行 artifact。
- `needs_review`：来源存在，但 license、硬件需求、依赖或页面可访问性还需要复核。

可优先进入下一轮 artifact audit 的入口：

- 3DGS/neural rendering：`gaussian-splatting`、`gsplat`、`NerfBaselines`、`instant-ngp`、`SplaTAM`、`CLM-GS`、`GS-Scale` <a id="WORKLOAD-ARTIFACT-001-C002"></a>[WORKLOAD-ARTIFACT-001-C002](#WORKLOAD-ARTIFACT-001-C002)<a id="WORKLOAD-ARTIFACT-001-C003"></a>[WORKLOAD-ARTIFACT-001-C003](#WORKLOAD-ARTIFACT-001-C003)[WORKLOAD-ARTIFACT-001-C004](#WORKLOAD-ARTIFACT-001-C004)<a id="WORKLOAD-ARTIFACT-001-C008"></a>[WORKLOAD-ARTIFACT-001-C008](#WORKLOAD-ARTIFACT-001-C008)。
- LLM serving：`vLLM`、`TensorRT-LLM`、`SGLang`、`LLMPerf`、`GenAI-Perf`、`FlexGen`、`KIVI` [WORKLOAD-ARTIFACT-001-C009](#WORKLOAD-ARTIFACT-001-C009)<a id="WORKLOAD-ARTIFACT-001-C012"></a>[WORKLOAD-ARTIFACT-001-C012](#WORKLOAD-ARTIFACT-001-C012)[WORKLOAD-ARTIFACT-001-C013](#WORKLOAD-ARTIFACT-001-C013)。
- Robotics：`ORB-SLAM3`、`SLAMBench`、`RobotPerf`、`FAST-LIO`、`OpenVLA`、EuRoC/KITTI/TUM RGB-D 数据集 [WORKLOAD-ARTIFACT-001-C014](#WORKLOAD-ARTIFACT-001-C014)[WORKLOAD-ARTIFACT-001-C015](#WORKLOAD-ARTIFACT-001-C015)<a id="WORKLOAD-ARTIFACT-001-C017"></a>[WORKLOAD-ARTIFACT-001-C017](#WORKLOAD-ARTIFACT-001-C017)[WORKLOAD-ARTIFACT-001-C018](#WORKLOAD-ARTIFACT-001-C018)。
- HPC/FPGA：HPL、HPCG、NAS NPB、PolyBench、GAPBS、Graph500、MLPerf Inference、Rosetta、TAPA、HeteroCL、AutoSA、Shuhai、LightningSim、RealProbe [WORKLOAD-ARTIFACT-001-C019](#WORKLOAD-ARTIFACT-001-C019)[WORKLOAD-ARTIFACT-001-C020](#WORKLOAD-ARTIFACT-001-C020)[WORKLOAD-ARTIFACT-001-C021](#WORKLOAD-ARTIFACT-001-C021)[WORKLOAD-ARTIFACT-001-C031](#WORKLOAD-ARTIFACT-001-C031)。
- PIM/CXL/profiling：AttAcc、Clio、Nimble、CXL 3.0 spec、Accelergy、Nsight、ROCProfiler、Vitis Analyzer、perf、Perfetto、Timeloop [WORKLOAD-ARTIFACT-001-C032](#WORKLOAD-ARTIFACT-001-C032)[WORKLOAD-ARTIFACT-001-C033](#WORKLOAD-ARTIFACT-001-C033)[WORKLOAD-ARTIFACT-001-C034](#WORKLOAD-ARTIFACT-001-C034)[WORKLOAD-ARTIFACT-001-C035](#WORKLOAD-ARTIFACT-001-C035)。

## 5. 缺口

1. 还没有任何本地执行记录。所有 artifact 状态都停留在来源审计层面，不能用于性能对比。
2. 多数 artifact 还没有逐项核对 license、commit、dependency lockfile、dataset checksum、Docker/Conda 可用性。
3. 3DGS 大场景、2025-2026 venue artifact、PIM/CXL prototype 和部分 FPGA/CAD 工具条目仍需要 PDF/README 深查。
4. Robotics 和 VLA workload 缺真实机器人或回放 trace 的 deadline/tail-latency 证据；公开模型或数据集不能直接推出实时可部署。
5. PIM/CXL 条目中不少属于规范、模拟器或原型系统；没有硬件或仿真执行时，只能作为候选入口。
6. Profiling tool 文档已经入表，但没有采集 tool version，也没有生成 profiler trace。

## 6. 后续行动

1. 对 `benchmark_artifact_inventory.csv` 中 `runnable_claimed` 的条目做只读 artifact audit：记录 license、latest commit/tag、安装说明、数据入口、硬件要求和最小 smoke-test 命令，不运行重型实验。
2. 为每个 workload family 选 2-3 个后续可跑的最小任务，先补齐 input shape、baseline provenance、tool version 和 expected output 字段。
3. 建一个单独的 `artifact_audit_log.csv`，记录 URL 检查日期、commit/tag、README 证据、失败原因和是否需要硬件。
4. 如果进入实际 benchmark 阶段，先写 run protocol，再运行；运行后才能把状态从 `runnable_claimed` 或 `runnable_unchecked` 升级为项目内的执行结果。

## 缺失来源

- 部分 2025-2026 venue 行只完成了来源级定位，没有逐篇打开 PDF 复核全部 metric。
- 部分 GitHub 仓库的 license、commit/tag、issue 状态和安装依赖未审计。
- 部分数据集访问条款、下载链接和 checksum 未确认。
- PIM/CXL 硬件原型、FPGA board flow、robotics trace 和 LLM serving trace 均未本地执行或采集。
