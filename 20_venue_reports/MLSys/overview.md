# MLSys 论文图谱分析

## 1. 会议定位

本报告中的 `MLSys` 指 Conference on Machine Learning and Systems。项目中把它作为 Systems 组 P0 来源处理，重点观察 machine-learning workload 如何从算法、compiler/runtime、训练/推理服务、benchmark、production pipeline 和硬件接口共同形成系统问题。这里不把 “ML systems” 当最终 topic；最终分类仍按具体瓶颈、负载和技术路线来写。对应 claim <a id="MLSYS-001-C001"></a>[MLSYS-001-C001](#MLSYS-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 的 2019-2025 主体来自官方 MLSys Proceedings yearly book pages；2026 来自官方 virtual papers/poster pages，但 proceedings volume 尚未发布，所以 2026 全部标记为 `partial` 和 `needs_review`。2016-2017 没有可复核的 MLSys/SysML archival proceedings；2018 由 metadata agent 标记为 inaugural SysML non-archival talks/posters，本报告不把它写入 accepted proceedings paper rows。2019-2020 未找到公开 official awards detail；2021-2025 awards 来自官方 `virtual/<year>/awards_detail`。对应 claim <a id="MLSYS-001-C002"></a>[MLSYS-001-C002](#MLSYS-001-C002) 到 <a id="MLSYS-001-C014"></a>[MLSYS-001-C014](#MLSYS-001-C014)。

| 年份 | papers.csv 记录数 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 0 | 缺少/out_of_scope | 没有找到 MLSys/SysML 档案程序 |
| 2017 | 0 | 缺少/out_of_scope | 没有找到 MLSys/SysML 档案程序 |
| 2018 | 0 | 非档案 | 就职 SysML 演讲/海报；未加载为已接受的论文集 |
| 2019 | 32 | 完全的 | MLSys 官方论文集 |
| 2020 | 34 | 完全的 | MLSys 官方论文集 |
| 2021 | 52 | 完全的 | MLSys 官方论文集 + 官方 awards_detail |
| 2022 | 51 | 完全的 | MLSys 官方论文集 + 官方 awards_detail |
| 2023 | 46 | 完全的 | MLSys 官方论文集 + 官方 awards_detail |
| 2024 | 37 | 完全的 | MLSys 官方论文集 + 官方 awards_detail |
| 2025 | 61 | 完全的 | MLSys 官方论文集 + 官方 awards_detail |
| 2026 | 173 | partial | 官方虚拟论文/海报页；尚无程序卷 |

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型方法 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
| --- | --- | --- | --- | --- | --- | --- |
| T01/T02/T08 | LLM/Transformer 推理、KV 缓存、注意力服务 | 生成式推理如何在 KV 状态、显存、吞吐和低时延之间取舍 | 权重/KV 量化；寻呼；前缀重用；注意内核；为模拟器 | 2023-2026 | 可迁移到 3DGS/神经渲染的状态缓存、显存布局和 request-level 调度问题 | 验证行提供服务； 2026 部分 |
| T07/T08/T12 | 编译器、图优化、自动调整、协同设计 | Python/model graph 如何转成可优化 kernel、runtime 或硬件友好的执行计划 | 图替换；火炬.fx; DSL；学习成本模型； HLS 阶段排序 | 2019-2026 | 直接连接 FPGA/HLS、kernel 生成和软硬协同设计 | 已验证的行；临时集群 |
| T08/T10/T11 | 分布式训练和加速器编排 | 多 GPU/TPU 训练如何处理 placement、parallelism、memory、communication 和 control plane | SOAP 并行性；再物质化；异步数据流；调度 | 2019-2026 | 为大规模训练/推理系统论文提供系统约束背景 | 已验证的行；临时集群 |
| T11 | 基准测试、分析、模拟、验证 | 如何公平比较 ML 系统，避免单点 speedup 和不可复现实验 | MLPerf；差异会计；模拟器；执行痕迹；分析器 | 2020-2026 | 为硬件加速论文的评价口径提供强约束 | 验证行提供服务； 2026 部分 |
| T04/T07 | Edge、TinyML、设备上运行时 | 模型如何在 MCU、mobile GPU、edge SoC 和碎片化后端上部署 | TinyML 运行时； VM/内存虚拟化；后端集成 | 2021-2026 | 连接端侧 3DGS/机器人感知和部署约束 | 验证行提供服务； 2026 部分 |
| T03/T04 | 3DGS、神经渲染、XR、视觉系统 | 视觉/3D 表示如何被系统化加速和部署 | 分析； GPU 内核协同优化； XR 基准测试；渲染管道 | 2023-2026 | 与用户 3DGS 方向最直接，但证据仍偏近年前沿 | needs_review for 2026 lineage |

## 4. Accepted Papers 聚类结果

本节统计 `paper_type=accepted_paper` 的 486 行。`topic_cluster_label` 是基于 title 和少量 virtual/proceedings metadata 的 provisional 标注，不是 abstract embedding、citation graph 或人工逐篇精读结果。对应 claim <a id="MLSYS-001-C005"></a>[MLSYS-001-C005](#MLSYS-001-C005)。

| 序号 | 簇 | papers.csv 记录数 | 状态 |
| ---: | --- | ---: | --- |
| 1 | LLM/Transformer 推理、KV 缓存、注意力和服务 | 135 | 临时 |
| 2 | 通用 MLSys 系统和需求审查行 | 122 | 临时 |
| 3 | 分布式培训、通信和加速器编排 | 91 | 临时 |
| 4 | 推荐、嵌入、稀疏/MoE 和图学习系统 | 43 | 临时 |
| 5 | 编译器、图优化、自动调整和硬件/软件协同设计 | 35 | 临时 |
| 6 | 3DGS、神经渲染、XR、视频和视觉系统 | 18 | 临时 |
| 7 | 生产 ML 数据、联合学习和生命周期系统 | 17 | 临时 |
| 8 | Edge、TinyML、设备上运行时和部署 | 14 | 临时 |
| 9 | 基准测试、分析、模拟、验证和可靠性 | 11 | 临时 |

| 时间段 | 主导主题 | 新兴主题 | 下降主题 | 备注 |
| --- | --- | --- | --- | --- |
| 2019-2020 | 生产ML/数据验证；分布式训练；图/编译器优化 | MLPerf 风格的基准测试； HLS/自动调谐；重新物化 | 无断言 | 2019/2020 奖项来源缺失，因此仅使用程序支持的行 |
| 2021-2022 | 数据移动；编译器/运行时；边缘/TinyML；分布式编排 | Pathways、torch.fx、TensorFlow Lite Micro、加速器协同设计 | 无断言 | 官方奖项从 2021 年开始提供 |
| 2023-2024 | LLM 推理/服务； MoE/稀疏执行；验证和模拟 | AWQ、SLoRA、提示缓存、VIDUR、高效扩展Transformer推理 | 无断言 | LLM 服务成为可见的 MLSys 重心 |
| 2025-2026 | 注意力引擎；低位服务；基准跟踪；边缘运行时 | FlashInfer、QServe、FlashAttention-4、ExecuTorch、SwiftGS | 无断言 | 2026 是partial，直到程序/奖项公开 |

## 5. Award Papers 分析

| 年份 | 奖项类型 | 论文 | 作者/团队 | 主题 | 是否纳入里程碑 | 证据状态 |
| --- | --- | --- | --- | --- | --- | --- |
| 2021 | 杰出论文奖 | 基于深度学习的自动代码优化成本模型 | Riyadh Baghdadi、Massinissa Merouani、Mohamed-Hicham LEGHETTAS、Kamel Abdous、Taha Arbaoui、Karima BENATCHBA、Saman amar | compiler_graph_autotuning_codesign | yes | 已验证 |
| 2021 | 杰出论文奖 | Cortex：递归深度学习模型的编译器 | Pratik Fegade、Tianqi Chen、Phillip Gibbons、 Todd Mowry | compiler_graph_autotuning_codesign | yes | 已验证 |
| 2021 | 杰出论文奖 | 数据移动就是您所需要的：优化 Transformer 的案例研究 | Andrei Ivanov、Nikoli Dryden、Tal Ben-Nun、Shigang Li、Torsten Hoefler | llm_inference_kv_attention_serving | yes | 已验证 |
| 2021 | 杰出论文奖 | 共享机器学习集群的网络内聚合 | Nadeen Gebara, Manya Ghobadi, Paolo Costa | distributed_training_orchestration | yes | 已验证 |
| 2021 | 杰出论文奖 | TT-Rec：深度学习推荐模型的张量训练压缩 | Chunshing Yin, Bilge Acun, Carole-Jean Wu, Xing Liu | recommendation_sparse_moe_graph | yes | 已验证 |
| 2022 | 杰出论文奖 | GPU 稀疏邻域方法的半环基元 | Corey J. Nolet、Divye Gala、Edward Raff、Joe Eaton、Brad Rees、John Zedlewski、Tim Oates | recommendation_sparse_moe_graph | yes | 已验证 |
| 2022 | 杰出论文奖 | ML-EXray：了解 ML 边缘部署的可见性 | Hang Qiu、Ioanna Vavelidou、Jian Li、Evgenya Pergament、Pete Warden、Sandeep Chinchali、Zain Asgar、Sachin Katti | edge_tinyml_on_device_runtime | yes | 已验证 |
| 2022 | 杰出论文奖 | Pathways: Asynchronous Distributed Dataflow for ML | Paul Barham、Aakanksha Chowdhery、Jeff Dean、Sanjay Ghemawat、Steven Hand、Daniel Hurt、Michael Isard、Hyeontaek Lim、Ruoming Pang、Sudip Roy、Brennan Saeta、Parker Schuh、Ryan Sepassi、Laurent Shafey、Chandu Thekkath、Yonghui Wu | distributed_training_orchestration | yes | 已验证 |
| 2022 | 杰出论文奖 | QuadraLib：用于架构优化和设计探索的高性能二次神经网络库 | Zirui Xu，Fuxun Yu，Jinjun Xiong，Xiang Chen | llm_inference_kv_attention_serving | yes | 已验证 |
| 2022 | 杰出论文奖 | 用于深度学习推荐系统中压缩嵌入表的随机偏移块嵌入 (ROBE) | Aditya Desai，Li Chou， Anshumali Shrivastava | recommendation_sparse_moe_graph | yes | 已验证 |
| 2023 | 杰出论文奖 | 高效扩展 Transformer 推理 | Reiner Pope、Sholto Douglas、Aakanksha Chowdhery、Jacob Devlin、James Bradbury、Jonathan Heek、Kefan Xiao、Shivani Agraw | llm_inference_kv_attention_serving | yes | 已验证 |
| 2023 | 杰出论文奖 | 使用 ReLM 验证大型语言模型 | Michael Kuchnik、Virginia Smith、George Amvrosiadis | llm_inference_kv_attention_serving | yes | 已验证 |
| 2023 | 杰出论文奖 | 具有生命周期预测的虚拟机分配 | Hugo Barbalho, Patricia Kovaleski, Beibin Li, Luke Marshall, Marco Molinaro, Abhisek Pan, Eli Cortez, Matheus Leao, Hars | general_mlsys_needs_review | yes | 已验证 |
| 2024 | 最佳论文奖 | AWQ：设备上的激活感知权重量化LLM 压缩和加速 | Ji Lin、Jiaming Tang、Haotian Tang、Shang Yang、Wei-Ming Chen、Wei-Chen Wang、Guanguan Xu、Xingyu Dang、Chuang Gan、S | llm_inference_kv_attention_serving | yes | 已验证 |
| 2025 | 杰出论文奖 | FlashInfer：用于 LLM 推理服务的高效且可定制的注意力引擎 | Zihao Ye、Lequn Chen、Ruihang Lai， Wuwei Lin, Yineng Zhang, Stephanie Wang, Tianqi Chen, Baris Kasikci, Vinod Grover, Ar | llm_inference_kv_attention_serving | yes | 已验证 |
| 2025 | 杰出论文奖 | 机器学习系统中隐藏的膨胀 | Huaifeng Zhang, Ahmed Ali-Eldin | benchmarking_profiling_evaluation | yes | 已验证 |
| 2025 | 杰出论文荣誉奖 | APOLLO: SGD-like Memory, AdamW 级性能 | Hanqing Zhu, Zhunyu Zhang, Wenyan Cong, Xi Liu, Sem Park, Vikas Chandra, Bo Long, David Z. Pan, Zhuangyang Wang, Jinwon L | general_mlsys_needs_review | yes | 已验证 |
| 2025 | 杰出论文荣誉奖 | COMET: 专家混合的细粒度计算-通信重叠 | Shulai 张, Ningxin Cheng, Haibin Lin, Ziheng Jiang, Wenlei Bao, Chengquan Jiang, Qi Hou, Weihao Cui, Size Cheng, Li-W | recommendation_sparse_moe_graph | yes | 已验证 |
| 2025 | 杰出论文荣誉奖 | LAVA：具有学习分布的终身感知 VM 分配和对错误预测的适应 | Jiangheng Ling, Pratik Worah, Yawen Wang, Yunchuan Kong, Chunlei Wang, Clifford Stein, Diwakar Gupta, Jason Behmer, Logan | general_mlsys_needs_review | yes | 已验证 |
| 2025 | 杰出论文荣誉奖 | Marconi：混合 LLM 时代的前缀缓存 | Rui Pan、Zhuang Wang、Zhen Jia、Can Karakus、Luca Zancato、Tri Dao、Yida Wang、Ravi Netravali | llm_inference_kv_attention_serving | yes | 已验证 |
| 2025 | 杰出论文荣誉奖 | Seesaw：通过模型重新分片进行高吞吐量 LLM 推理 | Qidong Su、Wei Zhao、Xin Li、Muralidhar Andoorveedu, Chenhao Jiang, Zhanda Zhu, Kevin Song, Christina Giannoula, Gennady | llm_inference_kv_attention_serving | yes | 已验证 |

奖项只说明 MLSys 当年的正式认可，不自动证明长期影响。2019-2020 awards 未找到公开官方明细页；2026 awards page 尚未暴露可复核 winner rows，本报告不把 “Best Paper Session” 当成 award winners。

## 6. 代表论文清单

| 论文 | 角色 | WHY / HOW / WHAT / IMPACT | claim |
| --- | --- | --- | --- |
| 使用宽松图替换优化 DNN 计算 | 里程碑 | WHY：搜索等效DNN计算图的图优化路线。 HOW/WHAT：源行映射到 `Compiler, graph optimization, autotuning, and hardware/software co-design`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C030"></a>[MLSYS-001-C030](#MLSYS-001-C030) |
| 机器学习数据验证 | 典范 | WHY：生产 ML 数据验证路线。 HOW/WHAT：源行映射到 `Benchmarking, profiling, simulation, validation, and reliability`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C031"></a>[MLSYS-001-C031](#MLSYS-001-C031) |
| MLPerf 训练基准 | tool_benchmark | WHY：标准化 ML 训练基准路线。 HOW/WHAT：源行映射到 `Distributed training, communication, and accelerator orchestration`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C032"></a>[MLSYS-001-C032](#MLSYS-001-C032) |
| Checkmate: Breaking the Memory Wall with Optimal Tensor Rematerialization | 里程碑 | WHY：激活记忆/重物化优化路线。 HOW/WHAT：源行映射到 `General MLSys systems and needs-review rows`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C033"></a>[MLSYS-001-C033](#MLSYS-001-C033) |
| AutoPhase：使用深度强化学习在随机森林中调整 HLS 相序 | tool_benchmark | WHY：ML 引导的 HLS 编译器相序路线。 HOW/WHAT：源行映射到 `Compiler, graph optimization, autotuning, and hardware/software co-design`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C034"></a>[MLSYS-001-C034](#MLSYS-001-C034) |
| Data Movement Is All You Need: A Case Study on Optimizing Transformers | 里程碑 | WHY：围绕数据移动重新构建Transformer优化。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C035"></a>[MLSYS-001-C035](#MLSYS-001-C035) |
| Pathways: Asynchronous Distributed Dataflow for ML | 里程碑 | WHY：异步分布式加速器编排路线。 HOW/WHAT：源行映射到 `Distributed training, communication, and accelerator orchestration`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C036"></a>[MLSYS-001-C036](#MLSYS-001-C036) |
| torch.fx：Python 中深度学习的实用程序捕获和转换 | tool_benchmark | WHY：用于编译器/运行时集成的 Python 级程序捕获。 HOW/WHAT：源行映射到 `Compiler, graph optimization, autotuning, and hardware/software co-design`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C037"></a>[MLSYS-001-C037](#MLSYS-001-C037) |
| 走向神经网络和加速器的协同设计 | 里程碑 | WHY：加速器感知模型/硬件协同设计路线。 HOW/WHAT：源行映射到 `Compiler, graph optimization, autotuning, and hardware/software co-design`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C038"></a>[MLSYS-001-C038](#MLSYS-001-C038) |
| MegaBlocks：专家混合的高效稀疏训练 | 里程碑 | WHY：块稀疏 MoE 训练路线。 HOW/WHAT：源行映射到 `Recommendation, embeddings, sparse/MoE, and graph learning systems`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C039"></a>[MLSYS-001-C039](#MLSYS-001-C039) |
| 高效扩展 Transformer 推理 | 里程碑 | WHY：大型 Transformer 推理分区和 KV/内存路由。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C040"></a>[MLSYS-001-C040](#MLSYS-001-C040) |
| AWQ：设备上的激活感知权重量化LLM 压缩和加速 | 里程碑 | WHY：MLSys 2024 最佳论文信号，用于硬件友好的 LLM 量化。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C041"></a>[MLSYS-001-C041](#MLSYS-001-C041) |
| SLoRA：数千个 LoRA 适配器的可扩展服务 | 前沿 | WHY：多租户 LoRA 适配器服务路由。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C042"></a>[MLSYS-001-C042](#MLSYS-001-C042) |
| 提示缓存：低延迟推理的模块化注意力重用 | 前沿 | WHY：注意力状态重用和提示缓存路由。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C043"></a>[MLSYS-001-C043](#MLSYS-001-C043) |
| VIDUR：A LARGE-SCALE SIMULATION FRAMEWORK FOR LLM INFERENCE | tool_benchmark | WHY：LLM 推理模拟和配置搜索路径。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C044"></a>[MLSYS-001-C044](#MLSYS-001-C044) |
| FlashInfer：用于 LLM 推理服务的高效且可定制的注意力引擎 | 里程碑 | WHY：MLSys 2025 杰出paper signal可定制关注服务。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C045"></a>[MLSYS-001-C045](#MLSYS-001-C045) |
| QServe:W4A8KV4 量化和系统协同设计，实现高效 LLM 服务 | 前沿 | WHY：低位 LLM 服务协同设计路线。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C046"></a>[MLSYS-001-C046](#MLSYS-001-C046) |
| MLCommons Chakra：使用标准化执行跟踪推进性能基准测试和协同设计 | tool_benchmark | WHY：标准化执行跟踪的 2026 部分信号。 HOW/WHAT：源行映射到 `Compiler, graph optimization, autotuning, and hardware/software co-design`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C047"></a>[MLSYS-001-C047](#MLSYS-001-C047) |
| FlashAttention-4：用于非对称硬件扩展的算法和内核流水线协同设计 | 前沿 | WHY：用于硬件生成特定注意内核的 2026 部分信号。 HOW/WHAT：源行映射到 `LLM/Transformer inference, KV cache, attention, and serving`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C048"></a>[MLSYS-001-C048](#MLSYS-001-C048) |
| ExecuTorch - 用于在设备上运行 ML 模型的统一 PyTorch 解决方案 | tool_benchmark | WHY：PyTorch 原生边缘运行时的 2026 部分信号。 HOW/WHAT：源行映射到 `Edge, TinyML, on-device runtime, and deployment`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C049"></a>[MLSYS-001-C049](#MLSYS-001-C049) |
| SwiftGS：GPU 上快速 3D 高斯泼溅的算法和系统协同优化 | 前沿 | WHY：用于 3DGS 算法/系统协同优化的 2026 部分信号。 HOW/WHAT：源行映射到 `3DGS, neural rendering, XR, video, and vision systems`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C050"></a>[MLSYS-001-C050](#MLSYS-001-C050) |
| 基于深度学习的自动代码优化成本模型 | 里程碑 | WHY：MLSys 官方奖励信号。 HOW/WHAT：源行映射到 `Compiler, graph optimization, autotuning, and hardware/software co-design`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C051"></a>[MLSYS-001-C051](#MLSYS-001-C051) |
| Cortex：递归深度学习模型的编译器 | 里程碑 | WHY：MLSys 官方奖励信号。 HOW/WHAT：源行映射到 `Compiler, graph optimization, autotuning, and hardware/software co-design`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C052"></a>[MLSYS-001-C052](#MLSYS-001-C052) |
| 共享机器学习集群的网络内聚合 | 里程碑 | WHY：官方 MLSys 奖励信号。 HOW/WHAT：源行映射到 `Distributed training, communication, and accelerator orchestration`。 IMPACT：impact_unverified 超出记录的源/奖励信号，除非单独审核。 | <a id="MLSYS-001-C053"></a>[MLSYS-001-C053](#MLSYS-001-C053) |

必读 10 篇建议：Data Validation for Machine Learning、Optimizing DNN Computation with Relaxed Graph Substitutions、MLPerf Training Benchmark、Checkmate、Data Movement Is All You Need、Pathways、torch.fx、Efficiently Scaling Transformer Inference、AWQ、FlashInfer。

## 7. 发展脉络

- 2019-2020：MLSys 的早期 archival proceedings 已经把 production data validation、distributed training、graph rewrite、HLS/autotuning、benchmarking 和 tensor rematerialization 放到同一个 venue 语境中。这个阶段的核心不是单一模型，而是“模型如何变成可部署和可评价的系统”。
- 2021-2022：data movement、compiler/runtime、TinyML、edge deployment 和 asynchronous distributed dataflow 变得显眼。Data Movement Is All You Need、TensorFlow Lite Micro、Pathways、torch.fx 和 neural-network/accelerator co-design 共同把系统瓶颈从算子吞吐扩展到内存、program capture、后端和 control plane。
- 2023-2024：LLM inference、MoE/sparse execution、adapter serving、prompt/KV reuse、simulation 和 validation 成为中心信号。Efficiently Scaling Transformer Inference、MegaBlocks、AWQ、SLoRA、Prompt Cache 和 VIDUR 说明 MLSys 的 LLM 线更关注 serving-time state、memory 和 runtime，而不是只关注模型精度。
- 2025-2026：attention serving engine、low-bit serving、execution traces、edge runtime 和硬件生成相关 kernel co-design 更明显。FlashInfer、QServe、MLCommons Chakra、FlashAttention-4、ExecuTorch 和 SwiftGS 代表近年前沿；其中 2026 全部保持 `partial/needs_review`。

| 技术路线 | 核心问题 | 方法变化 | 代表题名/信号 | 活跃年份 | 证据 |
|---|---|---|---|---|---|
| ML 生产管道 | 数据质量、program capture、monitoring 和 reproducibility 如何进入 ML 系统闭环 | 特别脚本 -> 数据验证和图形捕获 | ML 的数据验证； torch.fx | 2019-2026 | <a id="MLSYS-001-C110"></a>[MLSYS-001-C110](#MLSYS-001-C110) |
| 基准/分析方法 | 如何公平比较训练、推理和系统配置 | 隔离吞吐量 -> 解决方案时间、方差、模拟器、跟踪 | MLPerf 训练； VIDUR; MLCommons Chakra | 2020-2026 | <a id="MLSYS-001-C111"></a>[MLSYS-001-C111](#MLSYS-001-C111) |
| 编译器/自动调整/协同设计 | 动态 Python/model graph 如何变成可优化执行计划 | 贪婪重写 -> 图搜索、等式/超级优化、内核模板 | 宽松图替换；自动相位； FlashAttention-4 | 2019-2026 | <a id="MLSYS-001-C112"></a>[MLSYS-001-C112](#MLSYS-001-C112) |
| 分布式训练/编排 | 规模化训练的 memory、placement、communication 和 control plane 如何协同 | 数据/模型并行 -> 多维和异步编排 | 超越数据和模型并行；Checkmate；Pathways | 2019-2022 | <a id="MLSYS-001-C113"></a>[MLSYS-001-C113](#MLSYS-001-C113) |
| LLM 服务/KV/注意力 | 生成式推理如何被 memory state、prefix reuse 和 attention kernel 支配 | 以计算为中心 -> 内存/KV/缓存/以运行时为中心 | 高效扩展 Transformer 推理； AWQ；提示缓存； FlashInfer | 2023-2026 | <a id="MLSYS-001-C114"></a>[MLSYS-001-C114](#MLSYS-001-C114) |
| 3DGS/神经渲染系统 | 显式 3D 表示和渲染 pipeline 是否进入 MLSys 系统议程 | 通用视觉/XR -> 3DGS 算法/系统协同优化 | XRBench; SwiftGS | 2023-2026 | <a id="MLSYS-001-C115"></a>[MLSYS-001-C115](#MLSYS-001-C115) |

## 8. 领跑团队和代表成果

| 团队/机构谱系 | 主题 | 代表成果 | claim | 备注 |
| --- | --- | --- | --- | --- |
| Google/TPU/生产 ML 系统 | 分布式加速器编排、大型 Transformer 推理 | Pathways；有效扩展 Transformer 推理； MLCommons Chakra 参与 | <a id="MLSYS-001-C121"></a>[MLSYS-001-C121](#MLSYS-001-C121) | needs_review：隶属关系/年份消歧不完整 |
| 伯克利/斯坦福/MIT 系统线 | 图优化、数据验证、编译器/运行时、服务 | 宽松图替换； ML 的数据验证；火炬.fx;提示缓存 | <a id="MLSYS-001-C120"></a>[MLSYS-001-C120](#MLSYS-001-C120) | needs_review：团队边界从论文集推断 |
| MIT HAN 实验室/边缘压缩线 | LLM 量化和服务协同设计 | AWQ； QServe | <a id="MLSYS-001-C122"></a>[MLSYS-001-C122](#MLSYS-001-C122) | 背衬纸套装；更广泛的团队排名未 claim |
| ML 基础设施和服务系统组 | LoRA 服务、注意力内核、前缀缓存、基准测试 | SLoRA；闪存推断；马可尼； VIDUR | <a id="MLSYS-001-C123"></a>[MLSYS-001-C123](#MLSYS-001-C123) | needs_review：作者/entity disambiguation缺失 |
| 3DGS / 神经渲染信号 | 算法/系统协同优化用于渲染 | SwiftGS | [MLSYS-001-C115](#MLSYS-001-C115) | 2026 部分；称稳定的 MLSys 血统为时过早 |

这里的“团队/机构谱系”只作为读论文入口，不是跨会议排名。由于本轮没有完整 affiliation timeline、作者entity disambiguation和跨会议统计，所有团队领先性判断都保持 `needs_review`。

## 9. 对博士入门者的阅读路线

先读系统入口：Data Validation for Machine Learning、MLPerf Training Benchmark、torch.fx。再读 scaling/runtime：Beyond Data and Model Parallelism、Checkmate、Pathways。然后读 LLM serving：Efficiently Scaling Transformer Inference、AWQ、SLoRA、Prompt Cache、FlashInfer、QServe。最后根据个人方向补 SwiftGS、ExecuTorch、MLCommons Chakra 和 FlashAttention-4，但 2026 论文在 proceedings 发布前都应按 partial 处理。

## 10. 与我的方向的连接点

对 3DGS/神经渲染，MLSys 的信号比 ASPLOS/MICRO/HPCA 更晚，也更偏系统实现和算法-系统 co-optimization。2026 的 SwiftGS 直接命中 3D Gaussian Splatting，但目前只是 official virtual/poster row，不能当作稳定 topic。更稳的连接方式是从 MLSys 的 LLM serving 线借方法：把 3DGS 的 Gaussian state、sorting/binning、tile memory、rasterization kernel、frame-level reuse 和 batch/interactive latency 拆成系统瓶颈，再用 profiling/benchmark 和 compiler/runtime co-design 语言表达。

对 FPGA/加速器，MLSys 的 AutoPhase、accelerator co-design、compiler graph optimization、kernel template 和 edge runtime 论文比“芯片结构”更偏方法论。它们适合帮助定义：哪些工作是 kernel/runtime 优化，哪些是硬件映射，哪些需要 HLS/DSL 或 design-space exploration，哪些只是模型压缩。

## 11. 第二轮 Outputs

第二轮补强已写入 `MLSys_screening_matrix.csv`、`MLSys_paper_evidence_matrix.csv` 和 `subfields.md`。筛选矩阵覆盖 `511` 行：`{'index_only': 342, 'deep_read': 134, 'needs_review': 35}`。证据矩阵记录 `109` 篇 bounded deep-read paper，read-depth 统计为 `{'full_pdf': 104, 'title': 3, 'official_page+artifact_docs': 1, 'abstract': 1}`。2019-2025 被选中的 deep-read 论文均由官方 proceedings PDF 支撑；2026 行继续按 partial 处理，少数没有 PDF/abstract 的行保持 `title` 或 `official_page+artifact_docs`。

`papers.csv` 仍保留原 schema，但已从 official proceedings / virtual / OpenReview 页面回填可靠的 `pdf_url`、`openreview_url`、`session` 和少量 `code_url`。没有可靠来源的 DOI、keywords、artifact 状态继续留空或 `needs_review`。

奖项复核新增 4 条 2026 官方 award certificate rows：LEANN、BLASST、StreamDiffusionV2 和 ExecuTorch。2019-2020 官方 award winners 仍未找到 canonical source。2026 proceedings 缺失仍是正常 partial，但 2026 award certificate 已不再作为缺口处理。

## 12. 缺失来源

- MLSys 2026 final proceedings volume、DOI/proceedings metadata 和 post-proceedings artifact badge 信息。
- MLSys 2019-2020 官方获奖者规范来源。
- 2019-2025 全量 keyword、artifact/code badge、citation graph 和 adoption/reuse 证据。
- ForeCache/CacheWise title variant、Practical Unstructured Sparsity 和 ViRuleEval 的 final PDF/abstract。
- SwiftGS / StreamDiffusionV2 / XRBench / TorchSparse 等视觉与 3D 系统方向的跨 venue 对照。
- 隶属关系-消除歧义的作者/团队/机构时间表。
