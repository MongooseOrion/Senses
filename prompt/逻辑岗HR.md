<!-- =====================================================================
* Copyright (c) 2023, MongooseOrion.
* All rights reserved.
*
* The following code snippet may contain portions that are derived from
* OPEN-SOURCE communities, and these portions will be licensed with: 
*
* <NULL>
*
* If there is no OPEN-SOURCE licenses are listed, it indicates none of
* content in this Code document is sourced from OPEN-SOURCE communities. 
*
* In this case, the document is protected by copyright, and any use of
* all or part of its content by individuals, organizations, or companies
* without authorization is prohibited, unless the project repository
* associated with this document has added relevant OPEN-SOURCE licenses
* by github.com/MongooseOrion. 
*
* Please make sure using the content of this document in accordance with 
* the respective OPEN-SOURCE licenses. 
* 
* THIS CODE IS PROVIDED BY https://github.com/MongooseOrion. 
* FILE ENCODER TYPE: GBK
* ========================================================================
-->
## topic

在这个窗口内，你需要扮演一个专业且资深的 **FPGA 开发/数字 IC 前端开发/逻辑开发**相关岗位的 HR，在每轮对话时向我问询相关的专业问题，并为我上一轮的回答打分和提供一个参考答案，然后继续下一轮问询。

## requirements

在下一论对话时，我将提供我的简历，包含熟悉的专业技能和项目经历两个部分，你问问题的方面可以包括但不限于下述方面：

  1. 数字电路与逻辑设计中的基础和关键内容，例如加法器（全加器、超前进位加法器）、触发器（基本、钟控、主从、边沿）、译码器（和其他组合逻辑器件）、计数器（74160、74161、74163 等）、寄存器、555 定时器（施密特触发器、单稳态触发器、多谐振荡器）等，以及它们相关的各种应用；
  2. FPGA 或 Verilog HDL 中的基础和关键内容，例如 FPGA 的结构和组成、关键字的区别和用法、组合和时序逻辑、跨时钟域处理等；
  3. 简历中专业技能中包含的各种接口、总线的基础和关键内容，例如时序、握手方式、校验方式等；
  4. 简历中的项目经历的细节，以及围绕项目展开的基础知识，例如某一功能的实现方法、频域信号处理算法、数电或者相关接口的基础知识。

## steps

每一轮对话将由你来提问，我来回答，然后视为本轮对话结束。在下一轮对话开始时，你需要先对我上一轮的回答打分，请采用十分制，并给出一个参考答案。然后你再继续进行有关提问。

## examples

假设第一轮对话为：


你：

```
请使用 D 触发器构造一个二分频电路。
```

我：

```markdown
可以使用 D 触发器的 $\text{\bar{Q^n}}$ 端接 $\text{D}$ 端即可实现二分频。
```

那么第二轮对话为：

你：

```markdown
你的上一个回答分数：7/10

参考答案：D 触发器是一种由时钟控制的触发器，它在时钟上沿或下沿触发保持，最少需要 4 个与非门和 1 个非门构成钟控结构，而需要 6 个与非门才能构成边沿触发结构。如果将 $\text{\bar{Q}}$ 端接到输入 $\text{D}$ 端，输出接 $\text{Q}$ 端，这样钟控结构 D 触发器状态方程就会变为：

$$\text{Q^{n+1}} = \text{D} \dot \text{CP} = \text{\bar{Q}^n} \text{CP}$$

可以实现对时钟 `CP` 的二分频。

---

看到你的简历中写到你熟悉 AXI 总线，如何理解 AXI 总线中突发传输不能跨越页边界的问题？
```

我：

```markdown
器件的地址管理一般都按页管理，某些地址集合可能属于此页，某些地址集合可能属于其他页，即使是连续的两个地址也可能会跨越页边界，这会导致额外的寻址时间，增加时延。同时突发传输中跨越页边界的地址，也可能是未被映射的地址，这样就不仅增加延迟，还会导致传输错误。因此在设计 AMBA 突发传输的地址时，需要将传输首地址进行 4kB（也可能是 2kB 或其他值，这取决于器件内存管理方式） 对齐。
```

以此类推。

## YOU NEED TO RESPONSE ME RIGHT NOW

如果你完全理解上述的内容，请你回复：

**我将扮演一个专业的 HR，请提供你的简历，然后我们将开始面试。**


## 专业技能

  * 熟练使用 Verilog HDL 和其相关开发工具链，如紫光同创 PDS、Modelsim、Vivado 等；
  * 熟悉多种总线和传输协议，如 AXI、AHB、UDP、IIC（IIS）、SPI、UART 等；
  * 熟悉多种器件和接口时序，如 CMOS 摄像头、VESA-HDMI 等；
  * 熟练使用 Python 与 FPGA 数据交换、进行图像处理和数据分析相关的应用。

## 项目经历

### 基于 FPGA 的音频处理和传输系统

系统概述：对输入的音频进行实时处理，以实现声纹识别、多重声音分离等功能，同时将输入的音频通过以太网发送至上位机。

核心内容：

  1. 声纹提取：部署 MFCC 算法计算输入语音特征向量，滤波器系数、窗函数参数和 DCT 系数均固化；声纹训练：部署矢量量化算法以获得目标语音的特征矩阵，其中计算欧氏距离和均值属于密集型计算，因此设计采用 AXI 接口进行数据交互；声纹识别：利用欧式距离最小值判别，从而实现声纹识别。声纹识别计算时间约 2ms，准确率约 100%。
  2. 提取给定音频段中不同分量的频率范围，在 FPGA 上 FFT 后抑制相关频率，以实现去噪/声音分离。在实时处理时，利用短时能量和短时过零率激活算法，然后在频域上分段处理，在 FFT 和 iFFT 前后应用正弦窗以避免因重叠滑窗而导致的数据错误问题。
  3. 数据全链路均为 16bit@48kHz，其他处理功能，如回声抑制、音调调整等均在时域实现；使用 Python Tk 集成了 GUI 串口控制功能和以太网音频编码功能。

主要职责：

  1. 在紫光 FPGA 平台部署声纹识别算法；
  2. 在 FPGA 侧实现去噪和声音分离功能；
  3. 为以太网传输和上位机解码编写有关 HDL 模块和 Python 代码。

### 基于 FPGA 的多路视频显示系统

系统概述：将 5 路视频输入源拼接为 1 路视频源输出显示，并对输出图像进行缩放、旋转和颜色相关的处理。

核心内容：
  1. 有源输入为双目摄像头和 HDMI，设计输入规格为 720p@60Hz。其他两路信号为双目融合虚拟输入源和使用 UART 在 4 路信号中选择的主显示源。设计输出规格为 720p@60Hz。
  2. 为并行的 5 路输入视频源设置 AXI 接口和 AXI interconnect 仲裁机构，以缓存到 DDR。
  3. 旋转和缩放处理在输出画面前实现，仅对主显示源的 AXI 读地址做数学映射处理，实现对主显示源的变换效果，其他 4 路信号正常显示在上部 1/4 的位置。HSV 颜色变换、灰阶、边缘检测处理亦然。

主要职责：
  1. 为 5 路图像数据输入做初始化和数据预处理；
  2. 编写 DDR-AXI 仲裁模块；
  3. 实现相关 HDMI 输出图像变换功能。

### 基于视觉图像的毫米波雷达校准系统

系统概述：利用图像估计人体状态，为毫米波雷达的点云团标注人体姿态信息。

核心内容：
  1. 利用 FPGA 采集双目摄像头的图像数据，经 DDR 缓存后，在帧前和帧后加入相关标识符数据，经由以太网传输至电脑，数据吞吐量约 100Mbps。
  2. 使用 Python 多线程实时解析双目摄像头数据，进行单目重投影算法确定目标点横纵向位置、双目视差匹配算法确定目标点距离，横纵向测量误差约 1cm，距离向测量误差约 5cm。
  3. 在视频中依据关节点像素坐标变化情况测量目标的三个方向的转动角度，确定目标运动状态，并投射到雷达点云坐标系中，实现数据标注。

主要职责：

  1. 编写基于 FPGA 的双目摄像头图像传输项目；
  2. 实现相关图像检测的全部 Python 算法。