# ISCAS 论文图谱分析

## 1. 会议定位

本报告中的 `ISCAS` 指 IEEE International Symposium on Circuits and Systems。项目 registry 把它放在 IC 组，优先级 P1。和 ISSCC/VLSI/JSSC 这类更强调芯片实作和电路测量的来源相比，ISCAS 更宽：它覆盖模拟/RF、数据转换、DSP、通信、传感、生医、EDA、硬件安全、AI/ML circuit/system、neuromorphic、CIM/PIM、功率与系统理论等 CAS 社区主题。对本项目来说，ISCAS 更适合作为“电路与系统侧约束和早期信号”的补充来源，而不是架构级 accelerator lineage 的主证据。对应 claim <a id="ISCAS-001-C001"></a>[ISCAS-001-C001](#ISCAS-001-C001) 和 <a id="ISCAS-001-C008"></a>[ISCAS-001-C008](#ISCAS-001-C008)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 主体来自 DBLP ISCAS proceedings TOC/API；有 DOI 的行以 DOI/IEEE Xplore 入口作为主要论文级来源。2026 年 DBLP 已有 ISCAS 2026 proceedings metadata，但本轮仍把 2026 标成 `partial`，原因是官方 program PDF 只提供会议日程和总体覆盖信息，paper-award winner outcomes 没有在本轮抽取到稳定公开表。奖项方面，IEEE CASS 的 ISCAS Student Best Paper Award 页面确认 ISCAS 会识别三篇 Student Papers 和最佳 Demos，并能恢复 2018 Student Best Paper rows；2025 官方站点恢复了 Conference Best Paper、Best Live Demo、WiCAS finalist 和 YP finalist rows；2016、2017、2019-2024 的未恢复 winner 级别数据保留 `needs_review` coverage markers。对应 claim <a id="ISCAS-001-C002"></a>[ISCAS-001-C002](#ISCAS-001-C002) 到 <a id="ISCAS-001-C005"></a>[ISCAS-001-C005](#ISCAS-001-C005) 和 <a id="ISCAS-001-C010"></a>[ISCAS-001-C010](#ISCAS-001-C010)。

| 年份 | 论文.csv 行 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 759 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2017 | 716 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2018 | 988 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2019 | 725 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2020 | 916 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2021 | 737 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2022 | 743 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2023 | 631 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2024 | 855 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2025 | 1158 | 完全的 | DBLP ISCAS 程序 TOC/API |
| 2026 | 1009 | partial | DBLP ISCAS 程序 TOC/API 加官方程序 PDF 上下文 |

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型方法 | 代表论文/信号 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|---|---|
| T01/T02/T05/T06 | AI/ML 加速器和软硬件协同设计 | AI/ML workload 如何在 circuit/system 层实现低功耗、稀疏、低精度和专用数据流 | 加速器、量化、稀疏性、张量/数据流、推理/训练 | GASA 和其他标题级加速器行 | 2016-2026 | 间接连接 LLM/Transformer、边缘 AI 和专用加速器 | 验证行、临时簇 |
| T05/T09/T10 | 内存计算、神经形态和新兴内存加速器 | 存储墙、事件驱动和类脑计算如何在阵列/存储器/电路层实现 | RRAM/ReRAM、SRAM-CIM、忆阻器交叉开关、SNN、尖峰/事件处理 | paper.csv 中的 CIM/neuromorphic 行 | 2016-2026 | 连接低精度、稀疏、near-memory 和端侧 AI | 验证行、临时簇 |
| T03/T04/T11 | 视觉、神经渲染、3DGS 和空间智能硬件 | 2D/3D 感知、NeRF/3DGS、SLAM 和空间表示如何落到低功耗硬件或端侧系统 | 图像传感器、事件视觉、NeRF/3DGS 处理器、SLAM 加速、空间压缩 | GNeRF；神经 3DGS 处理器； 3DGS-SLAM 加速器 | 2024-2026 | 直接连接 3DGS/神经渲染和机器人空间感知 | 验证 DOI 行，年轻集群 |
| T03/T04/T11 | 边缘生物医学、机器人和传感系统 | 可穿戴/植入式、生医和机器人输入如何变成低功耗系统 | 雷达/激光雷达、生物医学前端、边缘推理、植入/可穿戴系统 | 2025 WiCAS/YP 入围行；传感器集群 | 2016-2026 | 连接机器人端侧计算和传感闭环 | 验证行、split_candidate |
| T06/T09/T11 | DSP、通信和信号处理架构 | 通信/DSP 算法如何映射到高吞吐、低功耗硬件 | FFT/滤波器、LDPC/极性/维特比、MIMO/波束成形、编解码器、5G/6G | 大型循环 DSP/通信集群 | 2016-2026 | 提供数据流、pipeline、并行译码和定点化方法背景 | 验证行、临时簇 |
| T07/T11/T12 | EDA、VLSI 设计自动化、 FPGA 和硬件安全 | 设计自动化、可重构实现、验证、安全和可靠性如何支撑 CAS 系统 | HLS、FPGA、布局/布线、测试、PUF、旁路、硬件安全 | PCBRouteNet 2025 YP 决赛入围者和 EDA/安全行 | 2016-2026 | 连接 FPGA 工具链、硬件生成和可信实现 | 验证行、临时簇 |
| T10/T12 | 模拟、 RF、电源和数据转换器电路 | 端侧系统的 ADC/DAC/RF/电源/时钟/I/O 如何决定 PPA 和感知链路 | SAR/Delta-Sigma ADC、PLL、DC-DC、RF 前端、LDO、数据转换器 | 主模拟/RF/电源集群 | 2016-2026 | 作为芯片/传感/机器人系统的底层约束 | 验证行，宽CAS 集群 |

## 4. Accepted Papers 聚类结果

本节统计 第二轮 修正后的 `paper_type=accepted_paper` 9226 行；11 行年度 proceedings/container metadata 已改为 `front_matter_or_proceedings_volume` 并排除出 main-paper 趋势判断。`topic_cluster_label` 由 title-keyword rules 得出；没有批量抽取 abstract、keyword 或 session name，因此只能作为 venue-level browsing bucket。`Other ISCAS circuits-and-systems proceedings rows` 是宽泛剩余桶，不能解释为单一 topic。对应 claim <a id="ISCAS-001-C006"></a>[ISCAS-001-C006](#ISCAS-001-C006)、<a id="ISCAS-001-C007"></a>[ISCAS-001-C007](#ISCAS-001-C007)、<a id="ISCAS-001-C009"></a>[ISCAS-001-C009](#ISCAS-001-C009)。

| 序号 | 簇 | accepted_paper 记录数 | 状态 |
|---:|---|---:|---|
| 1 | 其他 ISCAS 电路和系统程序行 | 2959 | 不确定 |
| 2 | 模拟、 RF、电源和数据转换器电路 | 1390 | 临时 |
| 3 | 内存计算、神经形态和新兴内存加速器 | 996 | 临时 |
| 4 | AI/ML 加速器和软硬件协同设计 | 983 | 临时 |
| 5 | DSP、通信和信号处理架构 | 882 | 临时 |
| 6 | EDA、VLSI 设计自动化、 FPGA 和硬件安全 | 661 | 临时 |
| 7 | 边缘生物医学、机器人和传感系统 | 423 | 临时 |
| 8 | 电路和系统理论、非线性系统和优化 | 389 | 临时 |
| 9 | 视觉、视频、神经渲染、3DGS 和空间智能硬件 | 296 | 临时 |
| 10 | 能源、设备、量子和其他新兴 CAS 主题 | 247 | 临时 |

| 时间段 | 主导主题 | 新兴主题 | 代表论文/信号 | 备注 |
|---|---|---|---|---|
| 2016-2018 | 其他ISCAS 电路与系统程序行；模拟、RF、电源和数据转换器电路； DSP、通信和信号处理架构 | 神经形态和早期 DNN/FPGA 加速器信号 | 2 用户高斯 IM-DD 光学多址信道的容量范围； FPGA 大型 MIMO 无线系统中数据检测的近似半定松弛设计；使用神经形态、场景驱动图像传感器的超低带宽视频流；用于神经形态应用的基于 HfO2 的忆阻器 | 标题级 DBLP/会议记录聚类；摘要/会话名称未批量提取。 |
| 2019-2021 | 其他 ISCAS 电路和系统程序行；模拟、RF、电源和数据转换器电路； AI/ML 加速器和软硬件协同设计 | CIM/神经形态、AI 推理、硬件安全、边缘传感 | 20 TOp/s/W 二元神经网络加速器；用于神经形态视觉传感器的基于尖峰神经网络的区域提议网络； 8 通道患者特定神经形态处理器，用于通过情绪检测对自闭症儿童进行早期筛查；用于基于 Lyra2REv2 的加密货币的 Lyra2 FPGA 核心 | 标题级 DBLP/会议记录聚类；摘要/会话名称未批量提取。 |
| 2022-2024 | 其他 ISCAS 电路和系统程序行；模拟、RF、电源和数据转换器电路； AI/ML 加速器和软硬件协同设计 | Transformer/注意力相邻行、稀疏 AI、学习辅助电路 | PRUNIX：忆阻加速器的非理想感知卷积神经网络修剪；使用 6T SRAM 进行内存计算，适用于各种 workload； RemEduLa - FPGA 设计技术远程教育实验室；使用 HLS 在 FPGA 中设计参数化光流分层算法 | 标题级 DBLP/会议记录聚类；摘要/会话名称未批量提取。 |
| 2025-2026 | 其他 ISCAS 电路和系统程序行；模拟、RF、电源和数据转换器电路； AI/ML 加速器和软硬件协同设计 | PEFT/稀疏性、AI 增强电路、现场演示、更广泛的智能社会框架 | GASA：Rank-Sliced GAther-Scatter 激活及其在稀疏性保持参数高效微调中的应用； CROSSCUT：提高资源利用率的多核神经形态加速器；现场演示：用于神经形态硬件上癫痫发作监测的实时事件编码器； STPE：具有多模式数据压缩方案的节能边缘设备Transformer推理处理器 | 2026 行使用 DBLP/DOI 元数据加上官方程序上下文；奖励结果仍然是partial。 |

## 5. Award Papers 分析

| 年份 | 奖项类型 | rank | 论文/条目 | 作者/Presenter | 证据状态 | 备注 |
|---|---|---|---|---|---|---|
| 2018 | student_best_paper | 获胜者 | 用于离子成像的 128x128 电流模式超高帧速率 ISFET 阵列 | Junming Zeng|Nicholas Miscourides|Pantelis Georgiou | 已验证 | IEEE CASS 官方页面第二波修正；与 [ISCAS-2018-P0944](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0944) 对齐。 |
| 2018 | student_best_paper | 获胜者 | FPGA 用于检测线的内存高效霍夫参数空间的实现 | David Northcote|Louise H. Crockett|Paul Murray | 已验证 | 来自 IEEE CASS 官方页面的第二波修正；与 [ISCAS-2018-P0634](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0634) 对齐。 |
| 2018 | student_best_paper | 获胜者 | 一种采用双注入二分频技术的低功耗、宽锁定范围三分频注入锁定分频器 | Alessandro Garghetti|Andrea L. Lacaita|Salvatore Levantino | 已验证 | IEEE CASS 官方页面的第二波修正；与 [ISCAS-2018-P0261](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0261) 对齐。 |
| 2016 | 其他 | 缺失 | ISCAS 2016 年学生论文/演示奖获奖者在此运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2017 | 其他 | 缺失 | ISCAS 2017 年学生论文/演示获奖者在本次运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2018 | 其他 | 缺失 | ISCAS 2018 年完整会议最佳论文/最佳演示获奖者在本次运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2019 | 其他 | 缺失 | ISCAS 2019 年学生论文/演示获奖者在本次运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2020 | 其他 | 缺失 | ISCAS 2020 年学生论文/演示获奖者在本次运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2021 | 其他 | 缺失 | ISCAS 2021 年学生论文/演示获奖者在本次运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2022 | 其他 | 缺失 | ISCAS 2022 年学生论文/演示奖获奖者在本次运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2023 | 其他 | 缺失 | ISCAS 2023 年学生论文/演示奖获奖者在本次运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2024 | 其他 | 缺失 | ISCAS 2024 年学生论文/演示获奖者在此运行中未从稳定来源恢复 | 作者 needs_review | needs_review | CASS 页面指出 ISCAS 认可三篇最佳学生论文和最佳演示，但未列出今年的获奖者。 |
| 2022 | society_award_bundle | 捆绑包 | 多个 IEEE CASS 2022 学会最佳论文奖 | 请参阅源页面 | 已验证 | CASS 协会奖项页面； ISCAS 不一定接受paper award。 |
| 2023 | 其他 | 缺失 | ISCAS 2023 年颁奖典礼获奖者名单未从节目中恢复 PDF | 作者 needs_review | needs_review | 官方节目包括颁奖典礼，但获奖者名单未恢复。 |
| 2024 | student_design_competition | 获胜者 | 多模态生理信号实时监测的可穿戴心肺保健系统 | 石汉宇|龙一辰|黄志宇|李树勋|周家训|梁郑世|杨延昌|Changyan Chen|Yuhang 张 | 已验证 | CASS 公告称决赛于 ISCAS 2024 期间举行。 |
| 2025 | honorable_mention | 入围者 | 工业物联网系统自动渗透测试：提高效率并减少对人类专业知识的依赖 | Fatim Sbai | 已验证 | 官方 ISCAS 2025 入围表行；会议论文ID 1438；会议=工业物联网的挑战与机遇。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 全集成动态电源单元分配 SIDO SC DC-DC 转换器，速度为 263.8mV/Ns DVS 速度和 19.8ns 瞬态恢复时间 | Feiyu Li | 已验证 | 官方 ISCAS 2025 年决赛表行；会议论文ID 1384； session=集成开关电容转换器。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 专用于糖尿病诊断和治疗的植入式闭环神经调节平台 | Razieh Eskandari | 已验证 | 官方 ISCAS 2025 年入围表行；会议论文ID 1592；会议=可穿戴和植入式生物医学电路和系统II。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 用于高 SNR 三倍增益的面积高效读出电路 LOFIC CMOS 图像传感器 | Ai Otani | 已验证 | 官方 ISCAS 2025 年决赛表行；会议论文ID 2170；会话=传感与显示技术。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | A 389um2 26.7nW 8 位 100kS/S SAR ADC 与混合 C-CI DAC | Kyungmin Lee | 已验证 | 官方 ISCAS 2025 年入围表行；会议论文ID 1225；会话=SAR ADC 设计。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 用于双近红外荧光团区分的 1280 x 720 x 3、12 波段多光谱成像仪 | Brianna Hajek | 已验证 | 官方 ISCAS 2025 年入围表行；会议论文ID 2273；会话=图像和视觉传感器。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 一款 14.9uW 准无源误差反馈噪声整形 SAR 转换器，具有 78dB 动态范围，用于音频活动检测 | Marco Tambussi | 已验证 | 官方 ISCAS 2025 年决赛表行；会议论文ID 1139； session=SAR 和流水线 ADC。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 具有动态 PVT 补偿的 550MHz 带宽、40dB 增益范围模拟基带，在 28 nm 中实现 26.1dBm OIP3 CMOS | 郭伟 | 已验证 | 官方 ISCAS 2025 年决赛表行；会议文件ID 1360； session=模拟放大器设计。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 用于增强可再生能源高渗透电力系统瞬态电压稳定性的最佳配置 | Xi 张 | 已验证 | 官方ISCAS 2025决赛入围表行；会议论文ID 2120；会议=从非线性电路和系统的角度来看电力电子渗透绿色电网。获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | PCBRouteNet：基于动态四边形网络流模型的数据集生成工具，用于 ML PCB 路由 | 刘浩 | 已验证 | 官方 ISCAS 2025 年入围表行；会议论文ID 2373； session=电子设计自动化和物理设计 I. 获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 上行链路无细胞 MIMO 网络节能检测器的设计与实现 | Ti-Yu Chen | 已验证 | 官方 ISCAS 2025 年决赛表行；会议论文ID 2452； session=无线通信 I. 获胜者结果未从此页面提取。 |
| 2025 | honorable_mention | 入围者 | 植入式电流耦合身体通道通信收发器，带蛇形互连电极对，用于关节置换术后监测 | Yunchul Chung | 已验证 | 官方 ISCAS 2025 年入围表行；会议论文ID 2527； session=可穿戴和可植入生物医学电路和系统 I. 获胜者结果未从此页面提取。 |
| 2025 | best_paper | 第一名 | 分布式二次控制对孤岛微电网暂态稳定性的影响 | 杨静熙|吴振熙|谢凯|黄孟|赵朝阳|华瀚 | 已验证 | 官方 ISCAS 2025 年授予由元数据代理转录并与书目搜索进行交叉检查的图像支持行。 |
| 2025 | best_paper | 第二名 | PCBRouteNet：基于动态四边形网络流模型的 ML PCB 路由数据集生成工具 | 刘浩|郑杰|王浩|涂俊|白胜龙|刘玉熙|陈杰楠 | 已验证 | 官方ISCAS 2025 奖励由元数据代理转录的图像支持行。 |
| 2025 | best_paper | 第三名 | Transformer非线性函数逼近的低复杂性和可重构设计 | Qi-Xian Wu|Shu-Sian Teng|Ming-Der Shieh|Chih-Tsun Huang|Juin-Ming Lu | 已验证 | 官方ISCAS 2025 奖励由元数据代理转录的图像支持行。 |
| 2025 | best_demo | 获胜者 | 现场演示：用于高速大面积触觉传感的压缩子采样 | Ariel Slepyan|Dian Li|Trac Tran|Nitish Thakor | 已验证 | 官方 ISCAS 2025 奖项图像支持行；元数据代理找到 DOI 10.1109/ISCAS56072.2025.11043348。 |
| 2025 | best_demo | 亚军 | 现场演示：用于辅助中心静脉导管插入术的触觉增强生物阻抗针 | Qingyu Zhang|Ahmed Al-Hindawi|Jiaxing 张|Andreas Demosthenous|Yu Wu | 已验证 | 官方 ISCAS 2025奖项图像支持行；英式拼写遵循奖项图像。 |

奖项partial关键结论是“缺口和局部恢复并存”：2018 Student Best Paper、2025 Conference Best Paper、2025 Best Live Demo、2024 CASS Student Design Competition 和若干 CASS society-award bundle 有官方来源；2025 WiCAS/YP 页面给出的是 finalist table，因此 `awards.csv` 把它们记录为 `honorable_mention` / `Finalist`，不写成 Best Paper winner。没有稳定恢复到的年度保留 `Missing` 或 `Pending` coverage markers，不能用于里程碑判断。

## 6. 代表性论文清单

| 论文 | 年份 | 主题 | 角色 | WHY / HOW / WHAT / IMPACT | claim |
|---|---:|---|---|---|---|
| 2 用户高斯 IM-DD 光多路访问信道的容量范围 | 2016 | 能源、设备、量子和其他新兴 CAS 主题 | reading_route | WHY：集群 `Energy, devices, quantum, and other emerging CAS topics` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`energy_devices_quantum_other` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C020"></a>[ISCAS-001-C020](#ISCAS-001-C020) |
| FPGA 大型 MIMO 无线系统中数据检测的近似半定松弛设计 | 2016 | EDA、VLSI 设计自动化、 FPGA 和硬件安全 | reading_route | WHY：集群 `EDA, VLSI design automation, FPGA, and hardware security` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`eda_vlsi_fpga_security` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C021"></a>[ISCAS-001-C021](#ISCAS-001-C021) |
| 使用神经形态、场景驱动图像传感器的超低带宽视频流 | 2016 | 视觉、视频、神经渲染、3DGS 和空间智能硬件 | reading_route | WHY：集群 `Vision, video, neural rendering, 3DGS, and spatial-intelligence hardware` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`vision_video_3d_spatial_intelligence_hardware` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C022"></a>[ISCAS-001-C022](#ISCAS-001-C022) |
| 用于神经形态应用的基于 HfO2 的忆阻器 | 2016 | 内存计算、神经形态和新兴内存加速器 | reading_route | WHY：集群 `Compute-in-memory, neuromorphic, and emerging memory accelerators` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`cim_neuromorphic_emerging_memory` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C023"></a>[ISCAS-001-C023](#ISCAS-001-C023) |
| 面向基于忆阻器的稀疏矩阵向量乘法加速器 | 2016 | 内存计算、神经形态和新兴内存加速器 | reading_route | WHY：集群 `Compute-in-memory, neuromorphic, and emerging memory accelerators` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`cim_neuromorphic_emerging_memory` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C024"></a>[ISCAS-001-C024](#ISCAS-001-C024) |
| 用于移动机器人的快速鲁棒同伦路径规划方法 | 2016 | 边缘生物医学、机器人和传感系统 | reading_route | WHY：集群 `Edge biomedical, robotics, and sensing systems` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`edge_biomedical_robotics_sensing` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C025"></a>[ISCAS-001-C025](#ISCAS-001-C025) |
| 带有旋转Transformer的感应电力传输系统，用于在旋转应用上进行非接触式能量传输 | 2016 | AI/ML 加速器和软硬件协同设计 | reading_route | WHY：集群 `AI/ML accelerators and hardware-software co-design` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`ai_ml_accelerator_codesign` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C026"></a>[ISCAS-001-C026](#ISCAS-001-C026) |
| FPGA 最小组件 SKAN 用于经典和操作调节的模型 | 2016 | EDA、VLSI 设计自动化、 FPGA 和硬件安全 | reading_route | WHY：集群 `EDA, VLSI design automation, FPGA, and hardware security` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`eda_vlsi_fpga_security` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C027"></a>[ISCAS-001-C027](#ISCAS-001-C027) |
| 带有输出校正的近似加法器，用于容错应用和高斯分布式输入 | 2016 | 其他 ISCAS 电路和系统程序行 | reading_route | WHY：项目相关 ISCAS 标题级集群 `Other ISCAS circuits-and-systems proceedings rows` 中的信号； impact_unverified。 HOW/WHAT：`other_cas_needs_review` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C028"></a>[ISCAS-001-C028](#ISCAS-001-C028) |
| 使用 FPGA 进行自定时处理器原型设计的实用设计方法 | 2016 | EDA、VLSI 设计自动化、 FPGA 和硬件安全 | reading_route | WHY：集群 `EDA, VLSI design automation, FPGA, and hardware security` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`eda_vlsi_fpga_security` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C029"></a>[ISCAS-001-C029](#ISCAS-001-C029) |
| 考虑额外Transformer安装的并网 PV 系统影响分析的初步研究 | 2016 | AI/ML 加速器和软硬件协同设计 | reading_route | WHY：集群 `AI/ML accelerators and hardware-software co-design` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`ai_ml_accelerator_codesign` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C030"></a>[ISCAS-001-C030](#ISCAS-001-C030) |
| 混合神经形态计算memristive/CMOS 用于实时学习的突触 | 2016 | 内存计算、神经形态和新兴内存加速器 | reading_route | WHY：集群 `Compute-in-memory, neuromorphic, and emerging memory accelerators` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`cim_neuromorphic_emerging_memory` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C031"></a>[ISCAS-001-C031](#ISCAS-001-C031) |
| 用于基于忆阻器阵列的神经拟态计算的循环传感集成触发电路 | 2016 | 内存计算、神经形态和新兴内存加速器 | reading_route | WHY：集群 `Compute-in-memory, neuromorphic, and emerging memory accelerators` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`cim_neuromorphic_emerging_memory` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C032"></a>[ISCAS-001-C032](#ISCAS-001-C032) |
| A 43.7 mW 94 fps CMOS 基于图像传感器的立体匹配加速器，具有焦平面校正和模拟功能人口普查转换 | 2016 | 视觉、视频、神经渲染、3DGS 和空间智能硬件 | reading_route | WHY：集群 `Vision, video, neural rendering, 3DGS, and spatial-intelligence hardware` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`vision_video_3d_spatial_intelligence_hardware` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C033"></a>[ISCAS-001-C033](#ISCAS-001-C033) |
| 基于草图的高性能生物医学大数据处理加速器 | 2016 | AI/ML 加速器和软硬件协同设计 | reading_route | WHY：集群 `AI/ML accelerators and hardware-software co-design` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`ai_ml_accelerator_codesign` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C034"></a>[ISCAS-001-C034](#ISCAS-001-C034) |
| 基于块的深度图估计算法，用于 FPGA 上的 2D 到 3D 转换 | 2016 | EDA、VLSI 设计自动化、 FPGA 和硬件安全 | reading_route | WHY：集群 `EDA, VLSI design automation, FPGA, and hardware security` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`eda_vlsi_fpga_security` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C035"></a>[ISCAS-001-C035](#ISCAS-001-C035) |
| 具有可重构神经形态的异构系统计算加速器 | 2016 | 内存计算、神经形态和新兴内存加速器 | reading_route | WHY：集群 `Compute-in-memory, neuromorphic, and emerging memory accelerators` 中与项目相关的 ISCAS 标题级信号； impact_unverified。 HOW/WHAT：`cim_neuromorphic_emerging_memory` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C036"></a>[ISCAS-001-C036](#ISCAS-001-C036) |
| 使用高斯传递函数方法设计高阶 II 延迟锁定环 | 2016 | 其他 ISCAS 电路和系统程序行 | reading_route | WHY：项目相关 ISCAS 标题级集群 `Other ISCAS circuits-and-systems proceedings rows` 中的信号； impact_unverified。 HOW/WHAT：`other_cas_needs_review` 下的标题级源行。 IMPACT：impact_unverified。 | <a id="ISCAS-001-C037"></a>[ISCAS-001-C037](#ISCAS-001-C037) |

必读路线不建议从 ISCAS 直接挑“全领域十大论文”。更合理的读法是按问题取样：CIM/neuromorphic rows 看事件驱动和近存计算；AI/ML accelerator rows 看电路级稀疏/低精度和数据流；edge/vision/biomedical rows 看端侧传感闭环；EDA/FPGA/security rows 看实现和验证；analog/RF/power rows 看真实芯片系统的底层约束。

## 7. 发展脉络

- 2016-2018：ISCAS 的大盘仍由 analog/RF/data converter、DSP/communications、systems theory 和 biomedical/vision sensing 构成。AI/ML、neuromorphic、FPGA/HLS 和 CIM 相关论文已经出现，但更像散点信号，不能据此写成成熟 accelerator 主线。
- 2019-2021：CIM/neuromorphic、edge AI、hardware security、learning-assisted circuit/system design 的标题信号增多。它们和 ISCAS 的传统强项不是替代关系，而是把存储器、传感、低功耗和算法映射问题带进 CAS 语境。
- 2022-2024：Transformer/attention、稀疏、低精度、AI-assisted design 和边缘感知系统开始更频繁出现。2024 的 GNeRF 把 neural radiance fields 明确带进 ISCAS accelerator 语境，但这仍是新线索，不应直接写成成熟谱系。
- 2025-2026：2025 DBLP rows 包含 GASA、Neural-3DGS Processor、3DGS-SLAM Accelerator 等 sparse/PEFT 与 neural-rendering/3DGS title-level signal；2026 DOI rows 包含 LOKI、STEAM-SSM、PRIMAL 等 LLM/KV/PIM/SSM 信号。官方 program 以 “Circuits and Systems for Intelligent Society” 作为主题，并说明有 over a thousand papers、14 regular tracks、special/cross-disciplinary/live-demo sessions。这个阶段的连接点是 AI workload、memory hierarchy、3D/spatial intelligence 和 CAS 的融合，但 award/proceedings post-curation 仍需复核。

| 技术路线 | 核心问题 | 代表信号 | 活跃年份 | 转折点 |
|---|---|---|---|---|
| CIM / 神经形态 / 事件驱动计算 | 数据搬运、事件稀疏和低功耗推理如何靠近存储/传感器 | papers.csv 中 memristor/RRAM/SNN/spiking/CIM rows | 2016-2026 | 从 neuromorphic 电路散点走向 CIM/PIM 和 AI inference 共同问题 |
| AI/ML 加速器和稀疏数据流 | DNN/Transformer/PEFT 等负载如何落到 circuit/system 级数据流 | GASA 和加速器标题行 | 2018-2026 | 从 CNN/DNN 加速扩展到 sparsity、attention/Transformer-adjacent 和 PEFT |
| 神经渲染/3DGS/3D 视觉加速器 | sampling、rendering、sparse 3D primitive、SLAM 和 neural representation 如何加速 | GNeRF；神经 3DGS 处理器； 3DGS-SLAM 加速器； SCAR/SCOPE-3D 候选者 | 2024-2026 | 从 2D image/video accelerator 扩展到 NeRF/3DGS 和空间智能硬件 |
| 边缘传感和生物医学/机器人系统 | sensor-front-end 到低功耗系统闭环如何设计 | WiCAS 入围图像传感器/植入行；视觉/传感器集群 | 2016-2026 | 从单个传感器/前端走向完整 sensing + local compute |
| EDA/FPGA/安全 | CAS 系统如何被生成、验证、测试和保护 | PCBRouteNet YP 入围； HLS/FPGA/安全/测试行 | 2016-2026 | 从传统 VLSI CAD/test 扩展到 ML PCB routing、security 和 reconfigurable design |
| 模拟/RF/电源/数据转换器基板 | 端侧系统如何被 ADC/RF/power/clock/I/O 约束 | 主模拟/RF/电源集群 | 2016-2026 | AI/edge 系统越来越依赖这些底层电路质量，而不是只看数字 accelerator |

## 8. 领跑团队和代表成果

这里不做跨会议“团队排名”。ISCAS 的 corpus 太宽，且本轮没有做完整 affiliation disambiguation。下表只记录 teams agent 从 DOI/Crossref/OpenAlex/官方 program 交叉得到的线索；含 `needs_review` 的团队行不能被改写成“领域领跑”结论。对应 claim <a id="ISCAS-001-C011"></a>[ISCAS-001-C011](#ISCAS-001-C011)。

| 团队/线索 | 主要路线 | 代表成果 | 证据状态 | 备注 |
|---|---|---|---|---|
| KAIST Yoo Lab / 边缘 AI 处理器系列 | 移动/边缘 DNN、ViT/Transformer 处理器、低位推理 | 2018在线DNN训练处理器； 2019 DT-CNN; 2025 ViT处理器； 2026 SeVeDo | DOI 行已验证，领导 needs_review | active-years 信号为 2018-2019 和 2025-2026 部分 |
| Tian-Sheuan Chang 组 | 稀疏/矢量 CNN、SNN、尖峰Transformer、边缘LLM | VSCNN; VSA; 2025 Spiking Transformer 加速器； 2026 维塔LLM | DOI 行已验证，领导 needs_review | 稀疏性/SNN/边缘 LLM |
| 中峰王加速器/VLSI line | FPGA/SoC AI 加速器、EfficientViT、Mamba/SSM、RISC-V Top-K | EfficientViT 的有用谱系信号FPGA加速器； SSMA; 2026 视频插值和 Top-V 行 | DOI/节目行已验证，隶属关系 needs_review | 南京/中山/深圳的隶属关系变化需要手动消歧 |
| INI / Indiveri-Sandamirskaya 线 | 神经形态电路、基于事件的 SNN、在线学习 | LGMD 避障；基于事件的电路；基于尖峰的可塑性； 2025/2026 神经形态行 | DOI 行已验证，从属关系 needs_review | 强神经形态路线，但不是完整的 ISCAS 排名 |
| Arindam Basu 神经形态/CIM 线 | 神经形态视觉，SRAM-CIM， SNN 加速器 | 2019 SNN 区域提案； 2020 SRAM CIM 去噪； 2026 SRAM-CIM SNN 加速器 | DOI 行已验证，从属关系 needs_review | 在来源行中从属关系从 NTU 新加坡更改为香港城市大学 |
| Westlake Sawan-Yang 线 | 神经拟态芯片、尖峰Transformer、边缘/生物医学智能 | 2025 年神经拟态芯片趋势； 2026异构决策尖峰Transformer | DOI 行已验证，领导 needs_review | young 2025-2026 部分信号 |
| KU Leuven MICAS / Verhelst 系列 | BNN 鲁棒性、数字 DNN 加速器芯片、边缘 AI 硬件 | 2018 BNN处理器容错； 2026 16 nm DNN 加速器 | DOI 行已验证，ISCAS 连续性 needs_review | 更宽的边缘-AI 强度应在 ISCAS 之外检查 |
| KAUST CIM / Eltawil-Fouda-Krestinskaya 线 | 数字 CIM、混合精度 CIM、硬件-workload 协同优化 | 2025 INT4-8/FP8 数字 CIM 宏； IMC 加速器设计 | DOI 行经过验证，多年强度 needs_review | 本次运行中的一年 ISCAS 信号 |
| 2025 WiCAS 决赛入围者 | 工业物联网、电源转换器、植入式、图像传感器、SAR ADC、多光谱成像器 | 官方入围表行 | 验证入围者 | finalist 不是 winner；只作读论文入口 |
| 2025 YP 入围者 | ADC、模拟基带、电力系统、PCB 路由数据集、MIMO检测器、生物医学收发器 | 官方入围表行 | 验证入围者 | 包含 EDA/PCB routing 和通信/生医端侧系统信号 |
| CAS 广泛社区 | Analog/RF/power/DSP/sensing/CIM/EDA | 数千个 DBLP/DOI 程序行 | 验证元数据 | 需要后续按 topic 做 author/institution disambiguation |

## 9. 对博士入门者的阅读路线

必读 10 个入口：GASA；2025 WiCAS 的 image sensor/implantable/ADC finalist rows；2025 YP 的 PCBRouteNet、MIMO detector、ADC finalist rows；papers.csv 中 `Compute-in-memory, neuromorphic, and emerging memory accelerators` 的近年代表行；papers.csv 中 `AI/ML accelerators and hardware-software co-design` 的近年代表行；papers.csv 中 `EDA, VLSI design automation, FPGA, and hardware security` 的 HLS/FPGA/security rows。

扩展 20 篇应从 `papers.csv` 过滤：`topic_cluster_id=ISCAS-C01`、`ISCAS-C02`、`ISCAS-C03`、`ISCAS-C06` 且 `include_in_report=maybe/yes`，再按 DOI 页面或 IEEE Xplore 补 abstract/keyword。适合跟踪的近年方向：CIM/PIM and neuromorphic circuits、sparse/low-precision AI dataflow、edge biomedical/vision systems、ML-assisted EDA/PCB routing、hardware security for CAS systems、data-converter/power substrate for AI edge devices。

## 10. 与我的方向的连接点

ISCAS 对你的 3DGS/FPGA/机器人芯片方向有直接但很新的 3D 信号：2024 的 GNeRF、2025 的 Neural-3DGS Processor 和 3DGS-SLAM Accelerator，以及 2026 neural rendering / implicit 3D 方向的候选 DOI 行。它们说明 3DGS/NeRF 已经进入 CAS 硬件讨论，但目前活跃年份短，不能写成稳定成熟谱系。更稳的连接点有五个。第一，CIM/neuromorphic rows 帮你理解 Gaussian primitive、feature/cache、排序和 alpha blending 背后的存储墙与事件稀疏问题。第二，edge vision/sensor rows 对机器人端侧感知和 3D reconstruction 前端有价值。第三，DSP/communications architectures 提供 pipeline、定点、并行译码和流式处理方法。第四，EDA/FPGA/security rows 对 HLS、FPGA mapping、PCB/physical design 和可信硬件有连接。第五，analog/RF/power/data-converter rows 提醒你端侧 3D/机器人系统不是纯数字加速器，传感器、ADC、供电和热设计会塑造系统边界。

## 11. 第二轮 Outputs

第二波在 `20_venue_reports/ISCAS/` 下添加了三个小领域 artifact：

- `ISCAS_screening_matrix.csv`：9273行，涵盖所有论文和奖项。决策为 121 `deep_read`、7785 `index_only`、1356 `needs_review` 和 11 `exclude_non_main`。
- `ISCAS_paper_evidence_matrix.csv`：101 个paper evidence rows，包含 WHY/HOW/WHAT/IMPACT/EVIDENCE、引用信号、artifact/代码状态和​​ team_signal。引文/采用/artifact 字段使用检索日期 `2026-06-27`。
- `subfields.md`：venue-local小领域深读 CIM/PIM、FPGA/HLS、开源硬件基准测试、Transformer/LLM/Mamba、NeRF/3DGS/SLAM、边缘传感、模拟/电源/数据转换器基板和边界主题。

此通道中的parent agent更正：

- 11 个年度会议记录/容器行从已接受的paper rows更改为 `front_matter_or_proceedings_volume`，并从主要论文趋势中排除。
- 2018 年学生最佳paper rows已根据 IEEE CASS 官方页面进行更正，并与 [ISCAS-2018-P0944](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0944)、[ISCAS-2018-P0634](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0634) 和 [ISCAS-2018-P0261](../../10_corpus/ISCAS/id_index.md#ISCAS-2018-P0261) 对齐。
- [ISCAS-2025-A022](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-A022) 与 [ISCAS-2025-P0901](../../10_corpus/ISCAS/id_index.md#ISCAS-2025-P0901) 对齐； [ISCAS-2024-A015](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-A015) 与 [ISCAS-2024-P0098](../../10_corpus/ISCAS/id_index.md#ISCAS-2024-P0098) 模糊对齐，并带有标题不同的注释。
- 2026年会议论文获奖结果仍为`normal_2026_partial`； CASS 社会奖页面不能替代 ISCAS 会议论文获奖者。

第二波子领域的发现是保守的。最强的venue-local方向是 CIM/PIM 和以神经形态记忆为中心的 AI； FPGA/HLS 映射和基准测试工作；开源硬件/EDA 基准测试； Transformer/LLM/Mamba内存和低精度加速；以及 2024-2026 NeRF/3DGS/SLAM 集群。 NeRF/3DGS 系列与神经渲染和机器人技术直接相关，但由于时间跨度短且几乎没有经过验证的采用证据，因此仍然处于新兴阶段。

影响审计仍处于初步阶段。记录了 101 个evidence rows的交叉引用引用计数，并且subagent在可访问的地方添加了 OpenAlex/Semantic Scholar/GitHub 信号。引用计数仅用作审核线索，而不用作里程碑状态的证明。

## 12. 缺失来源

- 完整的 2016-2026 年官方最终节目表，包含会议、摘要和关键词。
- IEEE Xplore 大规模摘要、关键字、参考和 PDF 元数据。
- 完整的 ISCAS 2016 年、2017 年和 2019-2024 年年度最佳学生论文/最佳演示获奖者档案。
- 公开ISCAS 2026年会后会议论文获奖者名单。
- PCBRouteNet、PDPU、OpenDPD、SVVHD、AMUSD 和其他工具/基准候选的完整 artifact/代码审核和可运行状态。
- 与 ISSCC、VLSI、JSSC、DAC、ICCAD、DATE、FPGA/FCCM/FPL/FPT 和architecture venues 的 cross-venue comparison。
- 作者/机构/entity disambiguation，以巩固团队线索。
