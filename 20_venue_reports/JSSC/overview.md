# JSSC 论文图谱分析

<a id="JSSC-SW-I001"></a>
<a id="JSSC-SW-I006"></a>
## 1. 会议定位和数据覆盖范围

JSSC 是 journal，不是会议 accepted-paper venue。本报告中的 `JSSC` 指 IEEE Journal of Solid-State Circuits，按项目 registry 归入 IC 组；它主要提供已经落到 silicon/circuit/system 实现的证据，而不是会议投稿 accepted list。对本项目来说，JSSC 的价值在于校准“论文里的加速器/芯片主张是否走到真实电路和系统实现”，覆盖 AI accelerator、CIM/IMC/PIM、vision sensor、RF/mixed-signal、memory macro、power-management 和 biomedical/edge SoC 等路线。对应 claim <a id="JSSC-001-C001"></a>[JSSC-001-C001](#JSSC-001-C001)。

## 2. 数据来源与覆盖范围

本轮覆盖 2016-2026。`papers.csv` 使用 DBLP JSSC volume XML/TOC 生成 DBLP-derived journal article rows，并过滤 obvious editorial、introduction、erratum 和 correction rows；它不是 IEEE Xplore full article export。由于 2026 年仍在进行，所有 2026 行标记为 `partial`。奖项使用 IEEE SSCS 官方页面作为 primary source：Best Paper 覆盖 2016-2024，Best Student Paper 目前有 2024 官方 row，Test-of-Time 目前有 2025 官方 row；其中 Test-of-Time 获奖论文发表于 1992，超出本轮 paper corpus 的发表年份范围，因此 `paper_id` 留空并在 notes 说明。对应 claim <a id="JSSC-001-C002"></a>[JSSC-001-C002](#JSSC-001-C002) 到 <a id="JSSC-001-C004"></a>[JSSC-001-C004](#JSSC-001-C004)。

| 年份 | journal_article 行 | 状态 | 主要来源 |
|---|---:|---|---|
| 2016 | 266 | 完全的 | DBLP JSSC 第 51 卷元数据 |
| 2017 | 267 | 完全的 | DBLP JSSC 第 52 卷元数据 |
| 2018 | 300 | 完全的 | DBLP JSSC 第 53 卷元数据 |
| 2019 | 299 | 完全的 | DBLP JSSC 第 54 卷元数据 |
| 2020 | 276 | 完全的 | DBLP JSSC 第 55 卷元数据 |
| 2021 | 309 | 完全的 | DBLP JSSC 第 56 卷元数据 |
| 2022 | 304 | 完全的 | DBLP JSSC 第 57 卷元数据 |
| 2023 | 283 | 完全的 | DBLP JSSC 第 58 卷元数据 |
| 2024 | 333 | 完全的 | DBLP JSSC 第 59 卷元数据 |
| 2025 | 359 | 完全的 | DBLP JSSC 第 60 卷元数据 |
| 2026 | 235 | partial | DBLP JSSC 第 61 卷元数据 |

## 3. 主题分类

| 一级领域 | 二级 topic | 核心问题 | 典型方法 | 代表论文 | 活跃年份 | 与用户方向的相关性 | 证据状态 |
|---|---|---|---|---|---|---|---|
| JSSC-T01 | CNN/DNN 空间数据流和加速器芯片 | CNN/DNN silicon accelerator 如何闭合数据流、片上复用和能效 | 空间数据流、PE 阵列、推理加速器、AI 芯片 | Eyeriss； UNPU； MCM DNN | 2017-2022 | 为 FPGA/ASIC 加速器报告提供能效、片上存储和数据流叙事模板 | DBLP 标题级，needs_review 与 IEEE 完全导出 |
| JSSC-T02 | 精度自适应 AI 执行 | 可变精度、混合精度、posit/microscaling 如何服务训练/推理 | 可变精度、混合 FP8/INT4、正值、量化 | UNPU； IBM 7 纳米 AI 芯片； MINOTAUR | 2019-2026 | 对低延迟端侧模型和可配置数值格式有直接参考价值 | 标题级，影响未验证 |
| JSSC-T03 | CIM/IMC/PIM 和近内存 AI 计算 | 矩阵向量乘和权重/激活搬运如何向 memory macro 或 near-memory 转移 | 6T SRAM IMC，电荷域 IMC，ReRAM/RRAM，可编程IMC，Transformer-CIM | 6T SRAM IMC； 64瓦电荷域IMC； TranCIM； CIMFormer | 2018-2026 | 对 3DGS tile/binning、sorting、alpha blending 的数据搬运瓶颈有方法迁移价值 | 标题级、集群临时 |
| JSSC-T04 | Transformer/attention/LLM 硅 | Transformer 的 attention、token、外存访问和端侧训练如何进入硅实现 | 注意力稀疏性、CIM、全片内存、外部内存缩减 | 动态弱相关性； TranCIM； CIM前任； T-REX； Adelia | 2023-2026 | 连接端侧智能、LLM/VLA、batch=1 低延迟和 memory residency 问题 | 标题级，2026 部分 |
| JSSC-T05 | 稀疏性和结构化加速 | 稀疏、block-circulant、SNN、outlier-aware 和低秩近似如何进入硬件数据流 | 零跳跃、块循环、令牌剪枝、稀疏/密集核心 | SNAP； STICKER-T；多TCIM； DPIM | 2021-2026 | 对 point cloud/3DGS/attention 稀疏结构的硬件化有迁移价值 | 标题级，影响未验证 |
| JSSC-T06 | 内存驻留和多芯片 AI 缩放 | all-on-chip memory、MCM/chiplet、external-memory reduction 如何支撑模型扩大 | MCM DNN、所有片上内存、近内存加速器、减少外部内存 | MCM DNN； MINOTAUR; T-REX | 2020-2026 | 对外存访问主导的渲染/机器人负载尤其相关 | 标题级，2026 部分 |
| JSSC-T07 | 计算成像和传感器前端 | 图像传感、depth/ToF/event camera 和 LiDAR 如何在 sensor/SoC 侧处理 | CMOS 图像传感器、SPAD、ToF、LiDAR、事件相机 | 查看 JSSC-C07 行 | 2016-2026 | 和相机输入、机器人视觉、端侧 3D 感知前端连接直接 | DBLP 标题级 |
| JSSC-T09 | 神经渲染、NeRF/3DGS、SLAM 和空间计算 | neural rendering、NeRF、3DGS、SLAM 如何作为 JSSC processor/SoC 标题对象出现 | NeRF、3D 高斯 Splatting、渲染处理器、NeRF-SLAM | 神经SLAM；MetaVRain； NeRF-Navi； IRIS；边缘 3DGS；Space-Mate； NeRF-Learner | SLAM/空间前兆：2021-2025； NeRF/3DGS：2024-2026 | 与用户 3DGS/FPGA/加速器方向直接相连，但长期影响仍未验证 | 标题级 needs_review，影响未验证，2026 部分 |
| JSSC-T10 | 特定于域的非 DNN 加速器 | Ising、SAT、PDE、genomics、baseband/security 等非 DNN 负载如何在定制硬件上实现 | 可重配置计算、PE 数组、位串行算术、特定于域的数据路径 | Ising-CIM； PDE 加速器；泛基因组加速器； HMAC-SHA256 加速器 | 2020-2026 | 提供“什么负载值得定制”的反例和参照，不直接等同于 AI accelerator | 标题级 needs_review |
| JSSC-T11 | 计算机视觉、机器人和信号处理加速器 | 图像增强、检测、跟踪、点云和机器人 SoC 负载如何进入 JSSC silicon | 视觉加速器、对象跟踪、点云、机器人 SoC、信号处理管道 | Navion； VOTA;鹰眼； MAVERIC;去模糊加速器 | 2017-2026 | 和 3D/机器人端侧计算直接相邻，但需和 sensor-front-end 区分 | 标题级 needs_review |
| JSSC-B01/B02 | RF/混合信号、内存、转换器和电源管理背景 | 支撑芯片系统的基础电路如何闭合 PPA、IO、时钟和供电 | RF/mmWave、光子/有线、ADC/DAC、PLL、SRAM/DRAM、 DC-DC/LDO | 奖励行和大背景簇 | 2016-2026 | 帮助理解加速器最终落到芯片时的 PPA 和外围系统约束 | 后台集群，非加速器路线 |

## 4. Accepted Papers 聚类结果

严格说 JSSC 没有会议式 accepted papers。本节把 `paper_type=journal_article` 的 JSSC research corpus 当作 journal accepted corpus 来做聚类，不把它等同于会议 accepted list。`topic_cluster_label` 是经返工 subagent 审查后的 title-level provisional 标注：AI Transformer 已和 RF/power transformer 分开，CIM/IMC 只按 compute semantics 归类，NeRF/3DGS/neural-rendering processor rows 单独成簇。由于没有批量 abstract、keywords、affiliation 和 citation graph，这些标签仍不能直接升级为全局 taxonomy。对应 claim <a id="JSSC-001-C005"></a>[JSSC-001-C005](#JSSC-001-C005) 和 <a id="JSSC-001-C010"></a>[JSSC-001-C010](#JSSC-001-C010)。

| 序号 | 簇 | journal_article 记录数 | 状态 |
|---:|---|---:|---|
| 1 | RF、毫米波、光子、有线和时钟 后台 | 1560 | 临时 |
| 2 | 通用固态电路和系统 | 915 | 临时 |
| 3 | 转换器、内存、电源管理和存储 IP 后台 | 232 | 临时 |
| 4 | 计算成像、LiDAR、事件和视觉传感器前端 | 118 | 临时 |
| 5 | TinyML、音频、生物医学、传感器接口和边缘嵌入式 SoC | 107 | 临时 |
| 6 | CIM、IMC、PIM 和近内存 AI 计算宏 | 105 | 临时 |
| 7 | CNN/DNN 空间数据流和神经网络加速器芯片 | 67 | 临时 |
| 8 | 精度自适应 AI 执行和训练/推理芯片 | 31 | 临时 |
| 9 | 稀疏性、结构化压缩、SNN 和事件式加速 | 31 | 临时 |
| 10 | 特定领域的非 DNN 加速器和计算机 | 21 | 临时 |
| 11 | Transformer、注意力、LLM 和边缘 AI 处理器 | 15 | 临时 |
| 12 | 神经渲染、NeRF、 3D 高斯 Splatting、SLAM 和空间计算处理器 | 12 | 临时 |
| 13 | 计算机视觉、机器人和信号处理加速器 | 9 | 临时 |
| 14 | 内存驻留、多芯片和近内存 AI 缩放 | 8 | 临时 |

| 时间段 | 主导主题 | 代表论文/信号 | 备注 |
|---|---|---|---|
| 2016-2018 | RF、毫米波、光子、有线和时钟背景；通用固态电路和系统；转换器、内存、电源管理和存储 IP 背景 | Eyeriss：用于深度卷积神经网络的节能可重构加速器 | subagent审查的标题级聚类；影响未验证 |
| 2019-2021 | RF、毫米波、光子、有线和时钟背景；通用固态电路和系统；转换器、内存、电源管理和存储 IP 背景 | UNPU：具有完全可变权重位精度的节能深度神经网络加速器 | subagent审查的标题级聚类；影响未验证 |
| 2022-2023 | RF、毫米波、光子、有线和时钟背景；通用固态电路和系统；转换器、内存、电源管理和存储 IP 背景 | 7 nm 四核混合精度 AI 芯片，具有 26.2-TFLOPS Hybrid-FP8 训练、104.9-TOPS INT4 推理和 workload 感知节流 | subagent审查的标题级聚类；影响未验证 |
| 2024-2026 | RF、毫米波、光子、有线和时钟背景；通用固态电路和系统；转换器、内存、电源管理和存储 IP 背景 | MetaVRain：一款移动神经 3D 渲染处理器，具有基于捆绑帧熟悉性的 NeRF 加速和混合 DNN 计算 | subagent审查的标题级聚类；影响未验证 |

## 5. Award Papers 分析

| 年份 | 奖项类型 | 论文 | 作者/团队 | 主题 | 是否纳入里程碑 | 证据状态 |
|---|---|---|---|---|---|---|
| 2025 | JSSC 时间考验奖 | 低功耗 CMOS 数字设计 | Anantha P. Chandrakasan|Sam Shen|Robert W. Brodersen | 通用固态电路 | 可能已验证 | 已验证 |
| 2024 | JSSC 最佳论文奖 | 8-λ × 50 Gbps/λ 异构集成 Si-Ph DWDM 发射机 | Cooper S. Levy|哲轩|Jahnavi Sharma|Duanni Huang|Ranjeet Kumar|马超轩|苏冠林|Songtao Liu|Jinyong Kim|Xinru Wu|Tolga Acikalin|Haisheng Rong|Ganesh Balamurugan|James E. Jaussi | rf/mmWave/photonic/wireline background | 可能已验证 | 已验证 |
| 2024 | JSSC 最佳学生论文奖 | A Wireless,用于癌症治疗中实时监测的多色荧光图像传感器植入物 | Micah Roschelle|Rozhan Rabbani|Surin Gweon|Rohan Kumar|Alec Vercruysse|Nam Woo Cho|Matthew H. Spitzer|Ali M. Niknejad|Vladimir M. Stojanović|Mekhail Anwar | 视觉传感器和成像管道 | 可能已验证 | 已验证 |
| 2023 | JSSC 最佳论文奖 | 基于深度学习的逆向设计毫米波无源器件和功率放大器 | Emir Ali Karahan|Cheng Liu|Kaushik Sengupta | rf/mmWave/photonic/wireline background | 可能已验证 | 已验证 |
| 2022 | JSSC 最佳论文奖 | 用于毫米波应用的谐波混合 PLL 架构 | Dihang Yang|David Murphy|Hooman Darabi|Arya Behzad|Asad A. Abidi|Stephen C. Au|Sraavan R. Mundlapudi|Kejian Shi|冷伟宇 | rf/mmWave/photonic/wireline background | 可能已验证 | 已验证 |
| 2021 | JSSC 最佳论文奖 | 具有非线性均衡和热控制功能的基于 3D 集成硅光子微环的 112 Gb/s PAM-4 发射机 | 李浩|Ganesh Balamurugan|Taehwan Kim|Meer N. Sakib|Ranjeet Kumar|Haisheng Rong|James Jaussi|Bryan Casper | rf/mmWave/photonic/wireline background | 可能已验证 | 已验证 |
| 2020 | JSSC 最佳论文奖 | A 0.32-128 TOPS，可扩展的基于多芯片模块的深度神经网络推理加速器，具有 16 nm 中的地面参考信号 | Brian Zimmer|Rangharajan Venkatesan|Yakun Sophia Shao|Jason Clemons|Matthew Fojtik|南江|Ben Keller|Alicia Klinefelter|Nathaniel Pinckney|Priyanka Raina|Stephen G. Tell|张彦青|William J. Dally|Joel S. Emer|C. Thomas Gray|Stephen W. Keckler|Brucek Khailany | 内存驻留和多芯片 AI 缩放 | 可能已验证 | 已验证 |
| 2019 | JSSC 最佳论文奖 | A 具有 12-b/符号极化的 42.2-Gb/s 4.3-pJ/b 60-GHz 数字发射机 MIMO | Chintan Thakkar|Anandaroop Chakrabarti|Shuhei Yamada|Debabani Choudhury|James Jaussi|Bryan Casper | rf/mmWave/photonic/wireline background | 可能已验证 | 已验证 |
| 2018 | JSSC 最佳论文奖 | 具有像素并行 14 位亚阈值的 6.9μm 像素间距背照式全局快门 CMOS 图像传感器 ADC | Masaki Sakakibara|Koji Okawa|Shin Sakai|Yasuhisa栃木|本田胜美|菊池英和|和田拓哉|上久保康信|三浦司|中沟正彦|城直树|林原亮|宫田慎也|中志山本|太田由之|Hirotsugu Takahashi|Tadayuki Taura|Yusuke Oike|Keiji Tatani|Takayuki Ezaki|Teruo Hirayama | 视觉传感器和成像管道 | 可能已验证 | 已验证 |
| 2017 | JSSC 最佳论文奖 | A 28-GHz 32 元件 TRX 相控阵 IC 具有并行双偏振操作和正交相位和增益5G 通信控制 | Bodhisatwa Sadhu|Yahya Tousi|Joakim Hallin|Stefan Sahl|Scott K. Reynolds|Örjan Renström|Kristoffer Sjögren|Olov Haapalahti|Nadav Mazor|Bo Bokinge|Gustaf Weibull|Håkan Bengtsson|Anders Carlinger|Eric Westesson|Jan-Erik Thillberg|Leonard Rexberg|Mark Yeck|顾晓雄|Mark Ferriss|Duixian Liu|Daniel Friedman|Alberto Valdes-Garcia | 通用固态电路 | 可能已验证 | 已验证 |
| 2016 | JSSC 最佳论文奖 | A 2.2 GHz 连续时间 Δ Σ ADC，具有 −102 dBc THD 和 25 MHz 带宽 | Lucien Breems|Muhammed Bolatkale|Hans Brekelmans|Shagun Bajoria|Jan Niehof|Robert Rutten|Bert Oude-Essink|Franco Fritschij|Jagdip Singh|Gerard Lassache | rf/mmWave/photonic/wireline background | 可能已验证 | 已验证 |

奖项只说明 IEEE SSCS/JSSC 对论文的正式认可，不自动证明长期学术影响。按 `VENUE_SCHEMA.md`，award papers 是 priority candidates，不是自动里程碑；本轮将 `milestone_candidate` 标为 `maybe`。Best Paper、Best Student Paper 和 Test-of-Time 获奖事实来自 SSCS 官方页；其中 2018 和 2016 Best Paper 与 corpus 的对齐依赖 DOI 和规范化后的题名排版差异。Test-of-Time 的 2025 award winner 是 1992 年论文，`paper_id` 留空不是缺失匹配错误，而是发表年份超出本轮 2016-2026 corpus。

## 6. 代表论文清单

| 论文 | 角色 | WHY / HOW / WHAT / IMPACT | claim |
|---|---|---|---|
| Eyeriss：用于深度卷积神经网络的节能可重构加速器 | reading_route | WHY：用于能量感知 CNN 数据流的 JSSC 硅文章候选数据移动。 HOW/WHAT：源行属于 `CNN/DNN spatial dataflow and neural-network accelerator silicon`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C016"></a>[JSSC-001-C016](#JSSC-001-C016) |
| 使用标准 6T SRAM 阵列的多功能内存推理处理器 | reading_route | WHY：标准 6T SRAM 内存推理处理器候选路由。 HOW/WHAT：源行属于 `CIM, IMC, PIM, and near-memory AI compute macros`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C017"></a>[JSSC-001-C017](#JSSC-001-C017) |
| 采用电荷域计算的 64-Tile 2.4-Mb 内存计算 CNN 加速器 | reading_route | WHY: tiled charge-domain IMC CNN accelerator route candidate. HOW/WHAT：源行属于 `CIM, IMC, PIM, and near-memory AI compute macros`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C019"></a>[JSSC-001-C019](#JSSC-001-C019) |
| A 0.32-128 TOPS，可扩展的基于多芯片模块的深度神经网络推理加速器，具有 16 nm 中的地面参考信号 | reading_route | WHY: MCM-based DNN inference accelerator and JSSC Best Paper signal candidate. HOW/WHAT：源行属于 `Memory-residency, multichip, and near-memory AI scaling`。 IMPACT: impact_unverified beyond journal publication/award status. | <a id="JSSC-001-C020"></a>[JSSC-001-C020](#JSSC-001-C020) |
| SNAP：用于非结构化稀疏深度神经网络推理的高效稀疏神经加速处理器 | reading_route | WHY：非结构化稀疏 DNN 推理硅路线候选。 HOW/WHAT：源行属于 `Sparsity, structured compression, SNN, and event-style acceleration`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C021"></a>[JSSC-001-C021](#JSSC-001-C021) |
| 7 nm 四核混合精度 AI 芯片，具有 26.2-TFLOPS Hybrid-FP8 训练、104.9-TOPS INT4 推理和 workload 感知节流 | reading_route | WHY：混合精度训练/推理 AI 芯片路线候选。 HOW/WHAT：源行属于 `Precision-adaptive AI execution and training/inference silicon`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C023"></a>[JSSC-001-C023](#JSSC-001-C023) |
| 一种利用全局注意力动态弱相关性的节能Transformer处理器 | 前沿 | WHY：Transformer特定的注意力相关性/稀疏性路线。 HOW/WHAT：源行属于 `Transformer, attention, LLM, and edge AI processors`。 IMPACT: impact_unverified beyond journal publication/award status. | <a id="JSSC-001-C024"></a>[JSSC-001-C024](#JSSC-001-C024) |
| MetaVRain：一款移动神经 3D 渲染处理器，具有基于捆绑帧熟悉性的 NeRF 加速和混合 DNN 计算 | 前沿 | WHY：移动神经3D渲染和NeRF加速路线。 HOW/WHAT：源行属于 `Neural rendering, NeRF, 3D Gaussian Splatting, SLAM, and spatial-computing processors`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C026"></a>[JSSC-001-C026](#JSSC-001-C026) |
| MINOTAUR：基于位置的 0.42-0.50-TOPS/W Edge Transformer 推理和训练加速器 | 前沿 | WHY：使用片上所有内存进行边缘 Transformer 推理和微调。 HOW/WHAT：源行属于 `Transformer, attention, LLM, and edge AI processors`。 IMPACT: impact_unverified beyond journal publication/award status. | <a id="JSSC-001-C033"></a>[JSSC-001-C033](#JSSC-001-C033) |
| NeRF-Navi：具有可重新配置近似/精确位卸载核心的节能 NeRF 3-D 路径规划处理器 | 前沿 | WHY：NeRF 路径规划处理器路线。 HOW/WHAT：源行属于 `Neural rendering, NeRF, 3D Gaussian Splatting, SLAM, and spatial-computing processors`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C032"></a>[JSSC-001-C032](#JSSC-001-C032) |
| 基于形状感知计算架构和时空高斯缓存的边缘 3D 高斯 Splatting 处理器 | 前沿 | WHY：边缘 3D 高斯 Splatting 处理器路线。 HOW/WHAT：源行属于 `Neural rendering, NeRF, 3D Gaussian Splatting, SLAM, and spatial-computing processors`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C036"></a>[JSSC-001-C036](#JSSC-001-C036) |
| IRIS：一种节能空间计算 SoC，用于通过表面感知 3D 高斯 Splatting 进行实时交互式渲染和建模 | 前沿 | WHY：表面感知 3D 高斯 Splatting 空间计算 SoC 路线。 HOW/WHAT：源行属于 `Neural rendering, NeRF, 3D Gaussian Splatting, SLAM, and spatial-computing processors`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C035"></a>[JSSC-001-C035](#JSSC-001-C035) |
| NeRF-Learner：具有统一推理和内存中训练计算功能的 NeRF-SLAM 加速器，用于同时神经渲染和 SLAM | 前沿 | WHY：具有内存计算训练/推理路线的 NeRF-SLAM 加速器。 HOW/WHAT：源行属于 `Neural rendering, NeRF, 3D Gaussian Splatting, SLAM, and spatial-computing processors`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C042"></a>[JSSC-001-C042](#JSSC-001-C042) |
| Space-Mate：用于移动空间计算的 303.5mW 实时稀疏专家混合 NeRF-SLAM 处理器 | 前沿 | WHY：移动 NeRF-SLAM 空间计算处理器路线。 HOW/WHAT：源行属于 `Neural rendering, NeRF, 3D Gaussian Splatting, SLAM, and spatial-computing processors`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C041"></a>[JSSC-001-C041](#JSSC-001-C041) |
| T-REX：硬件-软件协同优化的 Transformer 加速器，减少外部内存访问并增强硬件利用率 | 前沿 | WHY：Transformer 外部内存访问减少路线。 HOW/WHAT：源行属于 `Transformer, attention, LLM, and edge AI processors`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C034"></a>[JSSC-001-C034](#JSSC-001-C034) |
| UNPU：具有完全可变权重位精度的节能深度神经网络加速器 | reading_route | WHY：完全可变精度 DNN 加速器路线候选。 HOW/WHAT：源行属于 `CNN/DNN spatial dataflow and neural-network accelerator silicon`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C018"></a>[JSSC-001-C018](#JSSC-001-C018) |
| STICKER-T：使用块循环算法和统一频域加速的节能神经网络处理器 | reading_route | WHY：块循环和统一频域 CNN/FC/RNN 路由候选。 HOW/WHAT：源行属于 `Sparsity, structured compression, SNN, and event-style acceleration`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C022"></a>[JSSC-001-C022](#JSSC-001-C022) |
| TranCIM：具有管道/并行可重配置模式的基于 CIM 的全数字位线转置稀疏 Transformer 加速器 | 前沿 | WHY：稀疏 Transformer 和 CIM 路由。 HOW/WHAT：源行属于 `Transformer, attention, LLM, and edge AI processors`。 IMPACT：impact_unverified 超出期刊出版/奖励状态。 | <a id="JSSC-001-C025"></a>[JSSC-001-C025](#JSSC-001-C025) |

扩展阅读建议：先读 Eyeriss、6T SRAM IMC、64-tile charge-domain IMC、UNPU、MCM DNN、SNAP、programmable IMC、IBM 7-nm mixed precision AI chip，再读 Transformer 相关的 Dynamic Weak Relevances、TranCIM、MulTCIM、CIMFormer、MINOTAUR、T-REX、Adelia、HyAtt 和 DPIM，最后读 MetaVRain、NeRF-Navi、IRIS、Edge 3DGS、Space-Mate 和 NeRF-Learner。这里的 `reading_route` 是入门阅读候选，不等同于已完成引用影响审计的里程碑。

## 7. 发展脉络和技术路线变化

- 2016-2018：JSSC 的主线仍由 RF/mixed-signal、memory、power-management、sensor 和基础电路构成；AI accelerator 以 Eyeriss、binary/ternary IMC、6T SRAM IMC 等 silicon article 形式进入期刊。
- 2019-2021：title-level rows 显示 DNN accelerator 相关候选路线包括 variable precision、charge-domain IMC、MCM scaling、unstructured sparsity 和 block-circulant/频域加速。这里的重点不是“算法新”，而是算法、存储、数据流、电路实现共同闭合；具体方法变迁需要 full-paper audit。
- 2022-2023：programmable IMC、mixed-precision AI chip 和 Transformer-specific processor 出现为题名信号，提示 JSSC 中可编程、训练/推理混合和 attention/Transformer 负载开始变得可见；这仍是 `needs_review` 的路线判断。
- 2024-2026 partial：TranCIM、MulTCIM、CIMFormer、MINOTAUR、T-REX、Adelia、HyAtt、DPIM 等题名信号指向 Transformer/attention、all-on-chip memory、external-memory-access reduction、precision adaptation 和 sparsity；MetaVRain、NeRF-Navi、IRIS、Edge 3DGS、Space-Mate、NeRF-Learner 指向 neural rendering、NeRF/SLAM 和 3DGS processor；Occamy、Cache-PIM、MAVERIC、PDE/Ising/SAT/genomics 等行说明 JSSC 也有非 DNN 或系统级加速器信号。由于这些 paper 很新，且 2026 仍是 partial，impact 应保持 `impact_unverified`。

| 技术路线 | 核心问题 | 代表论文 | 活跃年份 | 候选转折/待复核点 |
|---|---|---|---|---|
| 空间 CNN 数据流 | 用 silicon 论文候选说明 CNN 数据搬运和片上复用的重要性 | Eyeriss | 2017 | data movement/energy-aware framing 需要 full-paper evidence 支撑 |
| IMC/CIM/PIM 加速器 | 把 MVM 和权重访问移向 memory macro 或 near-memory | 6T SRAM IMC; B莱因；瓦拉维；可编程 IMC | 2018-2024 | macro-level IMC 到 programmable accelerator 是候选解释，需要 abstract/full-paper audit |
| 精密可扩展 AI 芯片 | 用可变精度、混合精度、posit/microscaling 支撑不同模型和训练/推理 | UNPU； IBM 7 纳米芯片； MINOTAUR; Adelia | 2019-2026 | fixed/low-bit inference 到 adaptive training/fine-tuning 是候选解释 |
| 稀疏/结构化协同设计 | 让稀疏、block-circulant、attention relevance 成为硬件数据流的一部分 | SNAP； STICKER-T；动态弱相关性 | 2021-2024 | generic sparsity 到 workload-specific sparsity 是候选解释 |
| Transformer内存路由 | Transformer 的外存访问、token/attention 和端侧 memory residency 成为瓶颈 | 动态弱相关性； TranCIM；多TCIM； CIM前任； MINOTAUR； T-REX； Adelia | 2023-2026 | Transformer 特定的 JSSC 标题簇可见；影响尚未验证 |
| 神经渲染/空间计算路线 | NeRF、3DGS、SLAM 和 photorealistic rendering 成为 processor/SoC 标题对象 | 神经SLAM；MetaVRain； NeRF-Navi； IRIS；边缘 3DGS；Space-Mate； NeRF-Learner | SLAM/空间前兆：2021-2025； NeRF/3DGS：2024-2026 | 标题级存在可见；路线成熟度仍未验证 |
| 特定领域和视觉/机器人加速器 | 非 DNN 负载、视觉处理和机器人 SoC 如何在 silicon 中闭合 | Ising-CIM； PDE 加速器；导航； VOTA;鹰眼； MAVERIC | 2017-2026 | 有用的比较集；需要按 workload 和评估方法手动拆分 |

## 8. 领跑团队和代表成果（JSSC 可见作者簇）

本节只写 JSSC corpus 内可见的 author-cluster 和 collaboration 线索，用来回答“哪些团队值得后续跟踪”。它不是跨会议排名，也不把作者簇直接写成 verified institution/lab。DBLP rows 不提供稳定 affiliation，作者重名、机构变化和产业团队归属需要后续人工消歧。

| 团队/机构线索 | 主要路线 | 代表成果 | claim | 备注 |
|---|---|---|---|---|
| Eyeriss 链接作者集群 | 能源感知 CNN 数据流和加速器评估 | Eyeriss | JSSC-001-T001 | 单个代表行； institution_needs_review |
| Naveen Verma 链接的 IMC 作者集群 | 电荷域、6T SRAM 和可编程 IMC 加速器 | 6T SRAM IMC； 64瓦电荷域IMC；可编程 IMC | JSSC-001-T002 | 作者重复可见； institution_needs_review |
| Hoi-Jun Yoo 移动 AI / 空间计算作者集群 | UNPU、移动 AI、Transformer、NeRF/SLAM 和 3DGS 处理器 | UNPU；MetaVRain； C-Transformer； NeRF-Navi； IRIS； Space-Mate | JSSC-001-T003 | 作者集群可见；完整的隶属关系时间表needs_review |
| Leibo Liu / Shaojun Wei / Shouyi Yin Transformer-CIM 集群 | Transformer 加速，数字 CIM，注意力稀疏 | 动态弱相关性； TranCIM；多TCIM； CIM前任； Ayaka | JSSC-001-T005 | 作者集群可见； institution_needs_review |
| Yongpan Liu / Jinshan Yue稀疏-CIM和3DGS集群 | 稀疏NN、STICKER线、CIM、点云、边缘3DGS | STICKER-T； STICKER-IM; Edge 3-D 高斯溅射处理器 | JSSC-001-T006 | 作者集群可见； institution_needs_review |
| Chang 孟凡链接内存/CIM 合著者集群 | SRAM/RRAM/MRAM CIM、edge AI 内存宏 | ReRAM/SRAM CIM 行； STICKER-T 共同作者； MINOTAUR 协作 | JSSC-001-T007 | 补充候选；隶属关系时间表needs_review |
| Joo-Young Kim-linked PIM/设备上 AI 集群 | PIM、设备上训练、点云、LLM/Transformer 处理器 | Z-PIM； T-PIM; SP-PIM；鹰眼；阿德莉亚； DPIM | JSSC-001-T008 | 补充候选； 2026 行部分 |
| Dally / Keckler / Shao 协作 | MCM DNN 推理和稀疏 DNN 推理 | 2020 MCM DNN 最佳论文； SNAP | JSSC-001-T004 | 足以用于协作注释，没有一个经过验证的机构声称 |
| Jaussi / Balamurugan / Rong / Kumar 光子 I/O 集群 | 硅光子 I/O、PAM-4、DWDM、共同封装光链路 | 2021 光子发射器奖项； 2024 DWDM 发射器奖 | [JSSC-001-C004](#JSSC-001-C004) | 奖支持的作者集群； institution_needs_review |

## 9. 与我的方向的连接点

返工后的聚类显示：JSSC 2016-2026 corpus 中已有 2024-2026 title-level NeRF、neural rendering、SLAM 和 3D Gaussian Splatting processor signals，对应 claim <a id="JSSC-001-C009"></a>[JSSC-001-C009](#JSSC-001-C009)。这不能写成“JSSC 已形成成熟 3DGS 子领域”，因为 2026 是 partial，影响力和引用/采用尚not_audited；但它说明 JSSC 与你的 3DGS/FPGA/加速器方向不只是方法迁移，也已经出现直接相关的 silicon/SoC 题名信号。连接点包括：第一，Eyeriss/IMC/Transformer silicon 这条线提示新负载进入芯片论文时要回答数据流、片上存储、精度、能耗和系统接口；第二，CIM/PIM/near-memory 路线能帮助分析 Gaussian sorting、tile/binning、alpha blending 和 streaming rendering 的数据搬运瓶颈；第三，MetaVRain、NeRF-Navi、IRIS、Edge 3DGS、Space-Mate、NeRF-Learner 可作为后续 deep dive 的直接读 paper 入口；第四，JSSC 的 PPA/measurement 口径能约束 FPGA demo 走向 ASIC/SoC 时需要补哪些真实测量。

## 10. 第二轮 Outputs

本轮 第二轮 已补齐三个 venue 内产物：

- `JSSC_screening_matrix.csv` 覆盖 `papers.csv` 的 3231 行和 `awards.csv` 的 11 行，共 3242 行；筛选状态为 `deep_read` 55 行、`needs_review` 294 行、`index_only` 2881 行、`exclude_non_main` 12 行。`deep_read` 中 45 行来自 paper corpus，10 行来自 award rows。
- `JSSC_paper_evidence_matrix.csv` 收录 45 篇 paper evidence rows，包含 WHY/HOW/WHAT/IMPACT/EVIDENCE 字段；其中 10 行达到 abstract 级，35 行保留 title/official-page/Crossref 级。所有 citation/adoption/artifact/benchmark/team signal 均写入 2026-06-27 检索日期。
- `subfields.md` 把 JSSC 内部小领域拆成 DNN silicon dataflow、precision-adaptive AI execution、CIM/PIM、sparsity、Transformer/LLM silicon、NeRF/3DGS/SLAM/spatial computing、vision/robotics、memory-resident multichip scaling、domain-specific non-DNN compute、computational imaging/sensor front-end、award-linked RF/photonic circuit context。

本轮 issue audit 的处理结果是：<a id="JSSC-SW-I002"></a>[JSSC-SW-I002](#JSSC-SW-I002) 标为 `normal_2026_partial`；`JSSC-SW-I001/I003/I004/I005/I007/I008/I010` 标为 `partially_resolved`；`JSSC-SW-I006/I009/I011` 仍为 `still_open`。2026 partial 是正常当前年状态，不作为缺陷；但 full IEEE export、PDF/abstract、team/entity disambiguation、cross-venue mapping 和 full impact audit 仍未完成。

## 11. 缺失来源

- 缺少 IEEE Xplore 对 JSSC 2016-2026 的全量 article export、abstract、IEEE terms、PDF URL 和 affiliation。
- 缺少 ISSCC/VLSI/CICC 到 JSSC extended journal version 的系统映射。
- 缺少 Transformer/LLM 与 3DGS/NeRF/neural rendering + JSSC/solid-state-circuits 的 PDF-level deep dive、citation/adoption audit 和 cross-venue 对照。
- 缺少 artifact/code repository、benchmark reuse、citation graph 和 industry/toolchain adoption sources。
- 缺少 affiliation disambiguation 和 cross-venue team comparison。
