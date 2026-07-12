# DATE 第二轮小领域深读

更新日期：2026-06-27

范围：DATE 2016-2026。`papers.csv` 4057 行，`awards.csv` 45 行。screening matrix 4102 行；paper evidence matrix 75 行。2026 DOI/DBLP/publisher 批量缺口仍按 normal_2026_partial 处理。

## 小领域图谱

| subfield_id | 标签 | 核心问题 | 证据论文 ids | 证据状态 |
| --- | --- | --- | --- | --- |
| <a id="DATE-SF01"></a>[DATE-SF01](#DATE-SF01) | 边缘神经渲染和 3DGS 加速 | 3DGS 和神经渲染 workload 需要实时边缘吞吐量，同时保持视觉质量和内存占用。 | [DATE-2025-P3200](../../10_corpus/DATE/id_index.md#DATE-2025-P3200)； [DATE-2025-P3349](../../10_corpus/DATE/id_index.md#DATE-2025-P3349); [DATE-2025-P3399](../../10_corpus/DATE/id_index.md#DATE-2025-P3399)； [DATE-2026-P3576](../../10_corpus/DATE/id_index.md#DATE-2026-P3576); [DATE-2026-P3743](../../10_corpus/DATE/id_index.md#DATE-2026-P3743) | 多论文venue evidence |
| <a id="DATE-SF02"></a>[DATE-SF02](#DATE-SF02) | 点云和 3D 感知加速 | 点云感知强调不规则数据访问和逐点神经运算符。 | [DATE-2021-P1642](../../10_corpus/DATE/id_index.md#DATE-2021-P1642); [DATE-2023-P2457](../../10_corpus/DATE/id_index.md#DATE-2023-P2457); [DATE-2024-P2793](../../10_corpus/DATE/id_index.md#DATE-2024-P2793) | 多论文venue evidence |
| <a id="DATE-SF03"></a>[DATE-SF03](#DATE-SF03) | 边缘/移动 DNN 和传感器内推理 | 边缘推理必须适应移动、传感器或机器人平台上的延迟、隐私和能源限制。 | [DATE-2017-P0496](../../10_corpus/DATE/id_index.md#DATE-2017-P0496)； [DATE-2024-P2807](../../10_corpus/DATE/id_index.md#DATE-2024-P2807); [DATE-2025-P3068](../../10_corpus/DATE/id_index.md#DATE-2025-P3068)； [DATE-2026-P3582](../../10_corpus/DATE/id_index.md#DATE-2026-P3582); [DATE-2026-P3788](../../10_corpus/DATE/id_index.md#DATE-2026-P3788) | 多论文venue evidence |
| <a id="DATE-SF04"></a>[DATE-SF04](#DATE-SF04) | LLM 序列模型部署和量化 | LLM 和序列模型部署受到 KV 缓存、专家内存、片外流量和特定于模型的运算符的限制。 | [DATE-2021-P1807](../../10_corpus/DATE/id_index.md#DATE-2021-P1807); [DATE-2023-P2287](../../10_corpus/DATE/id_index.md#DATE-2023-P2287); [DATE-2025-P3131](../../10_corpus/DATE/id_index.md#DATE-2025-P3131)； [DATE-2025-P3151](../../10_corpus/DATE/id_index.md#DATE-2025-P3151); [DATE-2025-P3165](../../10_corpus/DATE/id_index.md#DATE-2025-P3165); [DATE-2025-P3166](../../10_corpus/DATE/id_index.md#DATE-2025-P3166)； [DATE-2025-P3207](../../10_corpus/DATE/id_index.md#DATE-2025-P3207); [DATE-2025-P3283](../../10_corpus/DATE/id_index.md#DATE-2025-P3283); [DATE-2025-P3377](../../10_corpus/DATE/id_index.md#DATE-2025-P3377); [DATE-2026-P3908](../../10_corpus/DATE/id_index.md#DATE-2026-P3908) | 多论文venue evidence |
| <a id="DATE-SF05"></a>[DATE-SF05](#DATE-SF05) | PIM/CIM/NVM 内存端 AI 计算 | 内存端 AI 计算尝试减少计算单元和密集内存宏之间的移动。 | [DATE-2018-P0764](../../10_corpus/DATE/id_index.md#DATE-2018-P0764)； [DATE-2019-P1069](../../10_corpus/DATE/id_index.md#DATE-2019-P1069); [DATE-2020-P1416](../../10_corpus/DATE/id_index.md#DATE-2020-P1416)； [DATE-2020-P1441](../../10_corpus/DATE/id_index.md#DATE-2020-P1441); [DATE-2020-P1546](../../10_corpus/DATE/id_index.md#DATE-2020-P1546); [DATE-2021-P1708](../../10_corpus/DATE/id_index.md#DATE-2021-P1708)； [DATE-2022-P2208](../../10_corpus/DATE/id_index.md#DATE-2022-P2208); [DATE-2026-P3752](../../10_corpus/DATE/id_index.md#DATE-2026-P3752) | 多论文venue evidence |
| <a id="DATE-SF06"></a>[DATE-SF06](#DATE-SF06) | HDC 和类脑边缘计算 | HDC 和类脑边缘计算通过紧凑的超向量寻求鲁棒的低能耗学习。 | [DATE-2022-P2011](../../10_corpus/DATE/id_index.md#DATE-2022-P2011); [DATE-2023-P2330](../../10_corpus/DATE/id_index.md#DATE-2023-P2330); [DATE-2023-P2381](../../10_corpus/DATE/id_index.md#DATE-2023-P2381)； [DATE-2024-P2714](../../10_corpus/DATE/id_index.md#DATE-2024-P2714); [DATE-2024-P2758](../../10_corpus/DATE/id_index.md#DATE-2024-P2758)； [DATE-2024-P2764](../../10_corpus/DATE/id_index.md#DATE-2024-P2764); [DATE-2024-P2878](../../10_corpus/DATE/id_index.md#DATE-2024-P2878) | 多论文venue evidence |
| <a id="DATE-SF07"></a>[DATE-SF07](#DATE-SF07) | 物理设计收敛、布线、布局和小芯片热建模 | 物理设计收敛需要在严格的 PPA 约束下进行布线、电容、布局、关键路径和热决策。 | [DATE-2016-P0252](../../10_corpus/DATE/id_index.md#DATE-2016-P0252)； [DATE-2018-P0804](../../10_corpus/DATE/id_index.md#DATE-2018-P0804); [DATE-2022-P2086](../../10_corpus/DATE/id_index.md#DATE-2022-P2086)； [DATE-2023-P2486](../../10_corpus/DATE/id_index.md#DATE-2023-P2486)； [DATE-2024-P2898](../../10_corpus/DATE/id_index.md#DATE-2024-P2898); [DATE-2025-P3417](../../10_corpus/DATE/id_index.md#DATE-2025-P3417); [DATE-2026-P3570](../../10_corpus/DATE/id_index.md#DATE-2026-P3570); [DATE-2026-P3645](../../10_corpus/DATE/id_index.md#DATE-2026-P3645) | 多论文venue evidence |
| <a id="DATE-SF08"></a>[DATE-SF08](#DATE-SF08) | HLS、EDA-AI、形式化验证和设计空间指导 | 设计自动化需要 HLS、形式化和 LLM 辅助流程，以减少手动迭代而不隐藏 QoR/正确性风险。 | [DATE-2018-P0869](../../10_corpus/DATE/id_index.md#DATE-2018-P0869)； [DATE-2018-P0931](../../10_corpus/DATE/id_index.md#DATE-2018-P0931); [DATE-2021-P1816](../../10_corpus/DATE/id_index.md#DATE-2021-P1816)； [DATE-2024-P2766](../../10_corpus/DATE/id_index.md#DATE-2024-P2766); [DATE-2026-P3610](../../10_corpus/DATE/id_index.md#DATE-2026-P3610); [DATE-2026-P3629](../../10_corpus/DATE/id_index.md#DATE-2026-P3629)； [DATE-2026-P3662](../../10_corpus/DATE/id_index.md#DATE-2026-P3662) | 多论文venue evidence |
| <a id="DATE-SF09"></a>[DATE-SF09](#DATE-SF09) | 可靠的硬件、安全性和故障感知执行 | 可靠的执行需要在部署之前量化故障、侧通道、软错误和稳健的 AI 决策。 | [DATE-2016-P0192](../../10_corpus/DATE/id_index.md#DATE-2016-P0192); [DATE-2017-P0441](../../10_corpus/DATE/id_index.md#DATE-2017-P0441); [DATE-2018-P0809](../../10_corpus/DATE/id_index.md#DATE-2018-P0809)； [DATE-2019-P1071](../../10_corpus/DATE/id_index.md#DATE-2019-P1071); [DATE-2019-P1246](../../10_corpus/DATE/id_index.md#DATE-2019-P1246)； [DATE-2020-P1591](../../10_corpus/DATE/id_index.md#DATE-2020-P1591); [DATE-2020-P1623](../../10_corpus/DATE/id_index.md#DATE-2020-P1623); [DATE-2021-P1840](../../10_corpus/DATE/id_index.md#DATE-2021-P1840); [DATE-2022-P2066](../../10_corpus/DATE/id_index.md#DATE-2022-P2066); [DATE-2024-P2908](../../10_corpus/DATE/id_index.md#DATE-2024-P2908); [DATE-2025-P3077](../../10_corpus/DATE/id_index.md#DATE-2025-P3077) | 多论文venue evidence |
| <a id="DATE-SF10"></a>[DATE-SF10](#DATE-SF10) | SoC/NoC 数据移动和实时 CPS 边界 | SoC、NoC 和实时系统需要在嵌入式约束下进行数据移动、热量/能量和时序控制。 | [DATE-2016-P0176](../../10_corpus/DATE/id_index.md#DATE-2016-P0176); [DATE-2016-P0188](../../10_corpus/DATE/id_index.md#DATE-2016-P0188); [DATE-2018-P0701](../../10_corpus/DATE/id_index.md#DATE-2018-P0701)； [DATE-2020-P1296](../../10_corpus/DATE/id_index.md#DATE-2020-P1296); [DATE-2021-P1657](../../10_corpus/DATE/id_index.md#DATE-2021-P1657)； [DATE-2026-P3794](../../10_corpus/DATE/id_index.md#DATE-2026-P3794); [DATE-2026-P3960](../../10_corpus/DATE/id_index.md#DATE-2026-P3960) | 多论文venue evidence |
| <a id="DATE-SF11"></a>[DATE-SF11](#DATE-SF11) | 新兴互连和非加速器边界上下文 | 一些获奖论文是有用的边界标记，因为它们共享设计方法，但不是加速器主线论文。 | [DATE-2016-P0162](../../10_corpus/DATE/id_index.md#DATE-2016-P0162); [DATE-2017-P0369](../../10_corpus/DATE/id_index.md#DATE-2017-P0369); [DATE-2017-P0393](../../10_corpus/DATE/id_index.md#DATE-2017-P0393)； [DATE-2019-P1041](../../10_corpus/DATE/id_index.md#DATE-2019-P1041) | 多论文venue evidence |

## 小领域注释

### [DATE-SF01](#DATE-SF01) 边缘神经渲染和 3DGS 加速

- 研究问题：3DGS 和神经渲染 workload 需要实时边缘吞吐量，同时保持视觉质量和内存占用。
- 背景/当前状态：DATE 证据跨越 2025 年至 2026 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：使用 FPGA/ASIC 管道、稀疏体积解码、光线调度和贡献感知剪枝。
- 代表作品：[DATE-2025-P3200](../../10_corpus/DATE/id_index.md#DATE-2025-P3200)； [DATE-2025-P3349](../../10_corpus/DATE/id_index.md#DATE-2025-P3349)； [DATE-2025-P3399](../../10_corpus/DATE/id_index.md#DATE-2025-P3399); [DATE-2026-P3576](../../10_corpus/DATE/id_index.md#DATE-2026-P3576); [DATE-2026-P3743](../../10_corpus/DATE/id_index.md#DATE-2026-P3743)
- workload/评估：边缘渲染 3DGS、稀疏体积渲染、神经渲染和实时渲染加速器。
- 影响状态：DATE-本地趋势，得到多篇 2025-2026 年论文支持；cross-venue影响尚未得到证实。
- 团队线索：author_string_only：Joongho Jo 和 Jongsun Park|高丽大学； author_string_only: 欧文辉|吴卓宇|张一璞|吴东军|Freddy Hong 和 Chik Yue； author_string_only: 周文凯|张跃峰|郑程|袁斌哲|陈俊生|张伦天|张翔宇|周平强|于静宜和楼鑫|上海科技大学； author_string_only：Yipu Chang|Jiawei Liang|Jian Peng|Jiang Xu 和 Wei Zhang
- artifact/代码信号：除了官方/论文链接之外没有经过验证
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF02](#DATE-SF02) 点云和 3D 感知加速

- 研究问题：点云感知强调不规则数据访问和逐点神经算子。
- 背景/当前状态：DATE 证据跨越 2021-2024 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：采用动态逼近、融合和GPU/加速器协同设计进行密集深度或点云识别。
- 代表作品：[DATE-2021-P1642](../../10_corpus/DATE/id_index.md#DATE-2021-P1642)； [DATE-2023-P2457](../../10_corpus/DATE/id_index.md#DATE-2023-P2457)； [DATE-2024-P2793](../../10_corpus/DATE/id_index.md#DATE-2024-P2793)
- workload/评估：点云神经网络和立体 LiDAR 深度传感。
- 影响状态：里程碑/采用需要cross-venue引用和机器人/视觉比较。
- 团队线索：上海交通/中兴微电子式点云加速器作者专线；没有排名。 author_string_only：孟海涛|钟崇浩|顾建峰和陈刚； author_string_only: Zhuoran Song|Heng Lu|Gang Li|Li Jiang|Nafeng Jing 和 Xiaoyao Liang|上海交通大学
- artifact/代码信号：除了官方/论文链接之外没有经过验证
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF03](#DATE-SF03) 边缘/移动 DNN 和传感器内推理

- 研究问题：边缘推理必须适应移动、传感器或机器人平台上的延迟、隐私和能源限制。
- 背景/当前状态：DATE 证据跨越 2017 年至 2026 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：使用分布式移动执行、压缩传感器内检索、轻量 CNN 和扩散策略加速。
- 代表作品：[DATE-2017-P0496](../../10_corpus/DATE/id_index.md#DATE-2017-P0496)； [DATE-2024-P2807](../../10_corpus/DATE/id_index.md#DATE-2024-P2807)； [DATE-2025-P3068](../../10_corpus/DATE/id_index.md#DATE-2025-P3068); [DATE-2026-P3582](../../10_corpus/DATE/id_index.md#DATE-2026-P3582); [DATE-2026-P3788](../../10_corpus/DATE/id_index.md#DATE-2026-P3788)
- workload/评估：移动 DNN、低分辨率人数统计、跌倒检测、ViT 边缘推断和机器人扩散。
- 影响状态：除了较旧的 MoDNN 引文信号外，影响仍部分得到验证。
- 团队线索：Northeastern/University of Pittsburgh/University of Pittsburgh 作者串：Mao、Chen、Nixon、Krieger、Yiran Chen； author_string_only: 陈博驹|冯晓宇|林俊彦|唐陈|杨华中和刘永攀|清华大学； author_string_only：克里斯蒂安·图雷塔|穆罕默德·阿里|弗洛伦斯·德姆罗齐和格拉齐亚诺·普拉瓦德利； author_string_only: Matteo Risso|谢陈|Francesco Daghero|Alessio Burrello|Seyedmorteza Mollaei|Marco Castellano|Enrico Macii|Massimo Poncino 和 Daniele Jahier Pagliari
- artifact/代码信号：除了官方/论文链接之外没有经过验证
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF04](#DATE-SF04) LLM 序列模型部署和量化

- 研究问题：LLM 和序列模型部署受到 KV 缓存、专家内存、片外流量和特定于模型的算子的限制。
- 背景/当前状态：DATE 证据跨越 2021-2026 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：采用混合精度、MoE offload、MCU 分布、DRAM/ReRAM PIM、低位量化和 Mamba FPGA 映射。
- 代表作品：[DATE-2021-P1807](../../10_corpus/DATE/id_index.md#DATE-2021-P1807)； [DATE-2023-P2287](../../10_corpus/DATE/id_index.md#DATE-2023-P2287)； [DATE-2025-P3131](../../10_corpus/DATE/id_index.md#DATE-2025-P3131); [DATE-2025-P3151](../../10_corpus/DATE/id_index.md#DATE-2025-P3151); [DATE-2025-P3165](../../10_corpus/DATE/id_index.md#DATE-2025-P3165); [DATE-2025-P3166](../../10_corpus/DATE/id_index.md#DATE-2025-P3166); [DATE-2025-P3207](../../10_corpus/DATE/id_index.md#DATE-2025-P3207); [DATE-2025-P3283](../../10_corpus/DATE/id_index.md#DATE-2025-P3283); [DATE-2025-P3377](../../10_corpus/DATE/id_index.md#DATE-2025-P3377); [DATE-2026-P3908](../../10_corpus/DATE/id_index.md#DATE-2026-P3908)
- workload/评估：长上下文 LLM、MoE、Transformer、Mamba 和加速器故障评估。
- 影响状态：2025-2026 年集群是具体的，但对于采用证据来说大多为时过早。
- 团队线索：北航+江苏曙光光电合作； ETH 苏黎世和博洛尼亚大学/PULP-相邻作者字符串； HUST + 平安科技合作； NCKU、中央研究院和 NTU 作者字符串
- artifact/代码信号：artifact_claimed_not_public：声称 UVM artifact 生成，2026 年 6 月 27 日未找到公开仓库； code_available_not_run：https://github.com/ecolab-nus/DAOP于2026年6月27日检查； code_claimed_but_unavailable：https://github.com/Sullivan12138/Cocktail 检查于 2026 年 6 月 27 日
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF05](#DATE-SF05) PIM/CIM/NVM 内存端 AI 计算

- 研究问题：内存端 AI 计算尝试减少计算单元和密集内存宏之间的移动。
- 背景/当前状态：DATE 证据跨越 2018-2026 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：使用PIM/CIM、STT-MRAM/ReRAM、compute-in-ROM/SRAM和透明卸载。
- 代表作品：[DATE-2018-P0764](../../10_corpus/DATE/id_index.md#DATE-2018-P0764)； [DATE-2019-P1069](../../10_corpus/DATE/id_index.md#DATE-2019-P1069); [DATE-2020-P1416](../../10_corpus/DATE/id_index.md#DATE-2020-P1416)； [DATE-2020-P1441](../../10_corpus/DATE/id_index.md#DATE-2020-P1441); [DATE-2020-P1546](../../10_corpus/DATE/id_index.md#DATE-2020-P1546)； [DATE-2021-P1708](../../10_corpus/DATE/id_index.md#DATE-2021-P1708); [DATE-2022-P2208](../../10_corpus/DATE/id_index.md#DATE-2022-P2208); [DATE-2026-P3752](../../10_corpus/DATE/id_index.md#DATE-2026-P3752)
- workload/评估：PIM/CIM/NVM 加速、神经形态内存和片上 DNN 部署。
- 影响状态：多篇多年论文；采用和 artifact 重用大多未 verified。
- 团队线索：author_string_only：Amit Trivedi|Shamma Nasrin|Shruthi Jaisimha 和 Priyesh Shukla； author_string_only：Elham Cheshmikhani |Hamed Farbeh 和 Hossein Asadi； author_string_only：Kamalika Datta|Arko Dutt|Ahmed Zaky|Umesh Chand|Devendra Singh|Yida Li|Jackson Chun-Yang Huang|Aaron Thean 和 Mohamed M Sabry Aly； author_string_only：Kanishkan Vadivel|Lorenzo Chelini|Ali BanaGozar|Gagandeep Singh|Stefano Corda|Roel Jordans 和 Henk 下士
- artifact/代码信号：code_available_not_run：https://github.com/LoopTactics/tdo-cim
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF06](#DATE-SF06) HDC 和类脑边缘计算

- 研究问题：HDC 和类脑边缘计算寻求具有紧凑超向量的鲁棒低能耗学习。
- 背景/当前状态：DATE 证据跨越 2022-2024 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：采用算法-硬件协同设计、不确定性估计、FeFET/NVM CIM 和可编程 HDC 协同处理。
- 代表作品：[DATE-2022-P2011](../../10_corpus/DATE/id_index.md#DATE-2022-P2011)； [DATE-2023-P2330](../../10_corpus/DATE/id_index.md#DATE-2023-P2330); [DATE-2023-P2381](../../10_corpus/DATE/id_index.md#DATE-2023-P2381)； [DATE-2024-P2714](../../10_corpus/DATE/id_index.md#DATE-2024-P2714); [DATE-2024-P2758](../../10_corpus/DATE/id_index.md#DATE-2024-P2758)； [DATE-2024-P2764](../../10_corpus/DATE/id_index.md#DATE-2024-P2764); [DATE-2024-P2878](../../10_corpus/DATE/id_index.md#DATE-2024-P2878)
- workload/评估：HDC 边缘学习、二值化/尖峰神经网络和隐私保护 HDC。
- 影响状态：DATE 证据是多年的，但影响超出venue需要引文图审计。
- 团队线索：author_string_only：Cheng Cheng Tang 和 Jie Han|阿尔伯塔大学； author_string_only：Paul Genssler|Mahta Mayahinia|Simon Thomann|Mehdi Tahoori 和 Hussam Amrouch； author_string_only: 王瑞轩|温文英|Kyle Juretus 和焦迅|维拉诺瓦大学； author_string_only： Taixin Li|hongtaozhong|juejian Wu|Thomas Kämpfe|Kai Ni|Vijaykrishnan Narayanan|Huazhong Yang 和 Xueqing Li
- artifact/代码信号：code_available_not_run：https://github.com/yuya-isaka/EcoFlex-HDP
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF07](#DATE-SF07) 物理设计收敛、布线、布局和小芯片热建模

- 研究问题：物理设计收敛需要在严格的 PPA 约束下进行布线、电容、布局、关键路径和热决策。
- 背景/当前状态：DATE 证据跨越 2016 年至 2026 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：使用宏模型、GPU 任务图路由、模拟路由、LLM 布局和小芯片热建模。
- 代表作品：[DATE-2016-P0252](../../10_corpus/DATE/id_index.md#DATE-2016-P0252)； [DATE-2018-P0804](../../10_corpus/DATE/id_index.md#DATE-2018-P0804); [DATE-2022-P2086](../../10_corpus/DATE/id_index.md#DATE-2022-P2086)； [DATE-2023-P2486](../../10_corpus/DATE/id_index.md#DATE-2023-P2486); [DATE-2024-P2898](../../10_corpus/DATE/id_index.md#DATE-2024-P2898)； [DATE-2025-P3417](../../10_corpus/DATE/id_index.md#DATE-2025-P3417); [DATE-2026-P3570](../../10_corpus/DATE/id_index.md#DATE-2026-P3570); [DATE-2026-P3645](../../10_corpus/DATE/id_index.md#DATE-2026-P3645)
- workload/评估：布线、宏布局、全局布局、2.5D/3D 热建模和电容提取。
- 影响状态：跨年度工具链线可见；工业采用尚未得到证实。
- 团队线索：PKU、UCSB、复旦和 ICT CAS 协作； author_string_only: 张浩一|高晓涵|罗浩阳|宋家豪|唐熙源|刘俊华|林一波|王润生和黄如|北京大学； author_string_only：张浩仪|高晓涵|沉子龙|宋家豪|程晓旭|唐熙媛|林一博|王润生和黄如； author_string_only：Kai Zhu|Darong Huang|Luis Costero 和 David Atienza
- artifact/代码信号：code_available_not_run：https://github.com/lamda-bbo/Efficient-TDP
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF08](#DATE-SF08) HLS、EDA-AI、形式验证和设计空间指导

- 研究问题：设计自动化需要 HLS、形式化和 LLM 辅助流程，以减少手动迭代而不隐藏 QoR/正确性风险。
- 背景/当前状态：DATE 证据跨越 2018-2026 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：使用 HLS 顾问、处理器模型重用、合约/子图搜索、LLM-HLS 基准测试和断言生成。
- 代表作品：[DATE-2018-P0869](../../10_corpus/DATE/id_index.md#DATE-2018-P0869)； [DATE-2018-P0931](../../10_corpus/DATE/id_index.md#DATE-2018-P0931); [DATE-2021-P1816](../../10_corpus/DATE/id_index.md#DATE-2021-P1816)； [DATE-2024-P2766](../../10_corpus/DATE/id_index.md#DATE-2024-P2766); [DATE-2026-P3610](../../10_corpus/DATE/id_index.md#DATE-2026-P3610)； [DATE-2026-P3629](../../10_corpus/DATE/id_index.md#DATE-2026-P3629); [DATE-2026-P3662](../../10_corpus/DATE/id_index.md#DATE-2026-P3662)
- workload/评估：HLS QoR 预测、HLS 代码生成、形式验证和 CPS 架构探索。
- 影响状态：Bench4HLS 是候选基准，尚未成为标准化基准。
- 团队线索：ICT CAS、BNU、CASTEST、UCAS，腾讯与纽卡斯尔联合作； UFRGS + UTFPR 作者字符串；中佛罗里达大学/Hadi Kamali 作者集群； author_string_only：Eugene Goldberg|Matthias Güdemann|Daniel Kroening 和 Rajdeep Mukherjee
- artifact/代码信号：code_available_not_run：https://github.com/yuex1994/DATE2021; code_available_not_run：https://github.com/zfsadik/Bench4HLS 检查于 2026 年 6 月 27 日
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF09](#DATE-SF09) 可靠的硬件、安全性、和故障感知执行

- 研究问题：可靠的执行需要在部署之前量化故障、侧通道、软错误和稳健的 AI 决策。
- 背景/当前状态：DATE 证据跨越 2016 年至 2025 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：采用概率WCET、SAT ATPG、低电压错误学习、故障注入、ECC 和定时通道预防。
- 代表作品：[DATE-2016-P0192](../../10_corpus/DATE/id_index.md#DATE-2016-P0192)； [DATE-2017-P0441](../../10_corpus/DATE/id_index.md#DATE-2017-P0441)； [DATE-2018-P0809](../../10_corpus/DATE/id_index.md#DATE-2018-P0809); [DATE-2019-P1071](../../10_corpus/DATE/id_index.md#DATE-2019-P1071); [DATE-2019-P1246](../../10_corpus/DATE/id_index.md#DATE-2019-P1246); [DATE-2020-P1591](../../10_corpus/DATE/id_index.md#DATE-2020-P1591); [DATE-2020-P1623](../../10_corpus/DATE/id_index.md#DATE-2020-P1623); [DATE-2021-P1840](../../10_corpus/DATE/id_index.md#DATE-2021-P1840); [DATE-2022-P2066](../../10_corpus/DATE/id_index.md#DATE-2022-P2066); [DATE-2024-P2908](../../10_corpus/DATE/id_index.md#DATE-2024-P2908);...
- workload/评估：安全性、可靠性、稳健性认证和 eFPGA 强化。
- 影响状态：所选行存在较旧的引文信号；除非另有说明，否则adoption未 verified。
- 团队线索：华盛顿大学/硅系统作者字符串：Kim、Howe、Moreau、Alaghi、Ceze、Sathe； author_string_only：达米安·哈迪 | 伊莎贝尔·普奥特和雅纳基斯·萨ZeD斯； author_string_only：扬尼斯·齐奥卡诺斯|列夫·穆哈诺夫|吉奥吉斯·乔加库迪斯|迪米特里奥斯·S·尼科洛普洛斯和乔治斯·卡拉康斯坦蒂斯； author_string_only: Jan Burchard|Dominik Erb|Adit D. Singh|Sudhakar M. Reddy 和 Bernd Becker
- artifact/代码信号： code_available_not_run: https://github.com/scalable-arch/DATE_24-SELCC
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF10](#DATE-SF10) SoC/NoC 数据移动和实时 CPS 边界

- 研究问题：SoC， NoC 和实时系统需要在嵌入式约束下进行数据移动、热/能量和时序控制。
- 背景/当前状态：DATE 证据跨越 2016 年至 2026 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：采用流量控制/路由、自适应实时控制、NTT硬件和分布式DMA或CPU内核优化。
- 代表作品：[DATE-2016-P0176](../../10_corpus/DATE/id_index.md#DATE-2016-P0176)； [DATE-2016-P0188](../../10_corpus/DATE/id_index.md#DATE-2016-P0188)； [DATE-2018-P0701](../../10_corpus/DATE/id_index.md#DATE-2018-P0701); [DATE-2020-P1296](../../10_corpus/DATE/id_index.md#DATE-2020-P1296); [DATE-2021-P1657](../../10_corpus/DATE/id_index.md#DATE-2021-P1657); [DATE-2026-P3794](../../10_corpus/DATE/id_index.md#DATE-2026-P3794); [DATE-2026-P3960](../../10_corpus/DATE/id_index.md#DATE-2026-P3960)
- workload/评估：NoC、EV 能源管理、后量子/HE 内核、ARMv9 矩阵乘法和分布式 DMA。
- 影响状态：系统链接的边界小领域；影响大多未 verified。
- 团队线索：KU Leuven 作者字符串；中山大学作者字符串； author_string_only：Ahmet Can Mert|Emre Karabulut|Erdinç Öztürk|Erkay Savas|Michela Becchi 和 Aydin Aysu； author_string_only：Korosh Vatanparvar 和 Mohammad Abdullah Al Faruque
- artifact/代码信号：code_available_not_run：https://github.com/huanglsh/KIRBYMM 检查于 2026 年 6 月 27 日
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

### [DATE-SF11](#DATE-SF11) 新兴互连和非加速器边界上下文

- 研究问题：一些获奖论文是有用的边界标记，因为它们共享设计方法但不是加速器主线论文。
- 背景/当前状态：DATE 证据跨越 2016 年至 2019 年；将其用作venue局部证据，而不是全场覆盖。
- 技术路线：采用光子互连建模、LED驱动的线P&R、微流控单细胞分析或近似计算数据选择。
- 代表作品：[DATE-2016-P0162](../../10_corpus/DATE/id_index.md#DATE-2016-P0162)； [DATE-2017-P0369](../../10_corpus/DATE/id_index.md#DATE-2017-P0369)； [DATE-2017-P0393](../../10_corpus/DATE/id_index.md#DATE-2017-P0393); [DATE-2019-P1041](../../10_corpus/DATE/id_index.md#DATE-2019-P1041)
- workload/评估：新兴互连、微流体和近似数据方法。
- 影响状态：这些保留为 negative_boundary/context，而不是主要加速器主题。
- 团队线索：author_string_only：Mahdi Nikdast|Gabriela Nicolescu|Jelena Trajkovic 和 Odile Liboiron-Ladouceur； author_string_only：穆罕默德·易卜拉欣|Krishnendu Chakrabarty 和 Ulf Schlichtmann； author_string_only：Tushar Krishna|Arya Balachandran|Siau Ben Chiah Li Zhu|Bing Wang|Cong Wang|Kenneth Lee Eng Kian|Jurgen Michel 和 Li-Shiuan Peh； author_string_only：Younghoon Kim|Swagath Venkataramani|Nitin Chandrachoodan 和 Anand Raghunathan
- artifact/代码信号：除了官方/论文链接之外没有经过验证
- 开放问题：cross-venue引用结构、artifact 运行时、基准重用和行业/工具链采用仍需要跟进。

## 跨年度趋势

- 3DGS/神经渲染仅在 2025 年之后才作为 DATE 本地集群出现：FAMERS、PS-GS、SpNeRF、2026 年神经渲染加速器和 FLICKER。这是一个多论文信号，但稳定子领域状态需要图形和架构会议证据。
- 点云加速的 2021-2024 年线较小：立体激光雷达融合、PRADA 和 FusionArch。 FusionArch是官方奖励节点，但长期采用尚未得到验证。
- LLM/序列部署在 2025-2026 年变得密集：Cocktail、DAOP、DOTS、FineQ、LightMamba、SegTransformer、Bench4HLS、Anchor-and-Adapt、Chip-Map、CoverAssert 和 RIFT。这一趋势得到了多篇论文和会议的支持，但大多数行对于采用 claim 来说都太新了。
- PIM/CIM/NVM 和 HDC 是多年以内存为中心的产品线。证据支持从 GenPIM/TDO-CIM 到 HDC/CafeHD/EcoFlex-HDP 到 FSDB 的 DATE venue-local线程。
- 物理设计闭合是多年来真正的 DATE 线程：电容提取、FastGR、SAGERoute/SAGERoute2.0、Efficient-TDP、Chip-Map 和 3D-ICE 4.0。
- 通过 WCET/故障估计、低压神经加速器错误、定时通道、eFPGA 强化和 RIFT，安全性/可靠性与加速器部署保持联系。

## 剩余差距

- 2026 是 DOI/DBLP/publisher 元数据的部分内容。
- 2023 每篇 PDF 仍未批量填充。
- 代码 URL 未经运行时检查；仓库的存在并不意味着采用。
- 引用计数在写入时具有查询日期，但不审核施引论文结构。
- 团队线索仅是作者字符串和隶属关系字符串观察值，而不是排名。
