# 在 Windows 中实现整个工作流
自 Windows10 的第一个正式版本 1507 发布已经过去了 8 年。还记得 2014 年，所有媒体都在疯狂尝鲜、报导新的 Windows 操作系统，那个时候我拿着 Surface Pro3，还在写 c 的 `Hello world` 程序。<br><br>
事实上，与 Windows11 发布前夕泄露 22000 版本后我立即尝试安装不同，以前我花了 2 年时间才最终决定从 Windows8 更新到 Windows10。Windows8.1 始终不能令我割舍的是**开始菜单**功能，不得不说时至今日我仍然还是会说 Win8 的**开始**设计很前卫。当然，UWP 和 Fluent Design 也一直在吸引着我。很可惜的是，我最终错过了 UWP 最繁荣的时期。<br><br>
废话不多说，毋庸置疑的是 Windows11 现在有非常完备的开发工具链，当然也有非常好的兼容性（其实我并不喜欢这个历史包袱）。导师建议我可以尝试在 Linux 上运行某些负载，而我觉得 Windows 足以胜任，这也是我决定写这个文档的源动力。

## 本页内容
  * 使用 Windows 本地运行 Linux 负载和 Android 应用程序
  * 部署紫光同创 FPGA 开发工具链
  * 在 Windows 配置 TensorFlow-GPU 版本

## 使用 Windows 本地运行 Linux 负载和 Android 应用程序
在本章，将介绍如何使用 [Windows 终端](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)配置 Python 环境和运行[适用于 Linux 的 Windows 子系统（WSL2）](https://learn.microsoft.com/zh-cn/windows/wsl/about)。

### 先决条件
  1. Windows11 且内部版本号在 22000.194 或以上；
  2. 机带 RAM 不少于 8GB。

### 部署 Python 环境

在 Micorsoft store 中可以直接安装 Python，相比于自定义安装，这样做的好处在于 Visual Studio 可以直接识别 Python 环境而无需额外配置，并可以方便地移除。

要构建 Python 之前，请确认源代码或开发工具依赖的 Python 版本，Python3.9 可点击[此处](https://apps.microsoft.com/store/detail/python-39/9P7QFQMJRFP7?hl=en-us&gl=us)安装。

如果未自定义安装目录，你可以在 `C:\Users\ [username] \AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_qbz5n2kfra8p0\LocalCache\local-packages\Python39\Scripts` 路径中找到使用 `pip install` 命令安装的第三方模块。

<br>请将该路径加入 `Path` 环境变量中，以便直接从 Windows 终端中进入 Python 环境。

如果部署完成，你应该可以在终端中输入 `python` 后进入 Python 环境。

### 配置 WSL2

WSL2 利用 Hyper-V 虚拟运行 Linux 系统，这与 WSL1 有本质区别。若要比较 WSL1 与 WSL2，请参阅[比较 WSL 版本](https://learn.microsoft.com/zh-cn/windows/wsl/compare-versions)和 [WSL 2 的新增功能](https://learn.microsoft.com/zh-cn/windows/wsl/compare-versions#whats-new-in-wsl-2)。

点击[此处](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R)可安装 WSL 工具，该工具可以管理系统中安装的所有 WSL 分发版本。

对于 WSL 的安装步骤，请参阅[使用 WSL 在 Windows 上安装 Linux](https://learn.microsoft.com/zh-cn/windows/wsl/install)。

在 Microsoft store 中安装特定的 Linux 发行版本后，可以通过在终端键入命令：
```
wsl
```
或者
```
[发行版名称]
```
进入 Linux 环境。

<br>尽管 WSL 没有图形桌面环境，但是 WSL2 允许运行 Linux 图形（GUI）程序，你可以利用使用以往在 Linux 终端环境中安装应用程序的经验，在 Windows 终端中使用指令安装 Linux 应用程序。示例应用程序可参阅[在 WSL2 上运行 Linux GUI 应用](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps)。

如需运行 Docker 远程容器和设置 NVIDIA GPU 加速，请参阅 [Microsoft Learn 相关文档](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gpu-compute)。

### 运行适用于 Android 的 Windows 子系统（WSA）

你可以在 Microsoft store 中搜索 Amazon appstore，下载并安装后，开始菜单中将出现名为 `适用于 Android 的 Windows 子系统设置` 的应用程序。打开 `开发人员 - 开发人员模式`，此时会出现内网 IP 地址，即可使用 Android 调试桥（ADB）旁加载应用程序，或将 WSA 设置为 Android Studio 默认虚拟机。

WSA 可以直接运行基于 ARM64 和 x86 开发的 Android 应用程序，以下功能获得完全支持：
  * 触控，具体取决于本地硬件的触控支持；
  * 扬声器
  * 摄像头
  * 麦克风

以下功能部分支持：
  * 图形处理器，不支持 Vulkan 引擎，推荐 Intel 或 Nvidia 的核芯显卡和独立显卡；

可按需利用 WSA 进行 Android 应用程序开发。

## 部署紫光同创 FPGA 开发工具链

紫光同创的现场可编辑逻辑门阵列（FPGA）开发工具包括 Pango Design Suite 和 Pango Design Suite Lite（PDS），在此章节将介绍如何使用 PDS 工具。

### 先决条件

  1. 已安装 Altera ModelSim 应用程序；
  2. 具备紫光 FPGA 硬件开发平台。

### 仿真和编译
若要使用 ModelSim 来进行设计文件的验证，你需要在 `Project - Project Settings - Simulation - Target Simulator` 中选择 `ModelSim Simulator`。

你可以将 `Compiled Libarary Location` 设置在 Modelsim 应用程序安装根目录下，以便 ModelSim 可靠地编译 PDS 相关器件和查看。然后，你需要设置 `Simulator Executable Path` 在 Modelsim 主程序的父文件夹路径下，如果是默认设置，它应该是 `C:\altera\13.1\modelsim_ase\win32aloem`。

如果设置正确，你应该可以在编写激励文件后运行行为级仿真时能够看到 Modelsim 自动打开并进行波形仿真。

### 添加 IP 文件

如果是预置的 IP 核，你可以在 `Tools - IP Compiler` 中获取所需的模块，例如时钟分频器和逻辑分析仪。

如果是第三方 IP 核，你可以在 `Design` 窗格内添加。

### 打开原理图

原理图是帮助设计人员从代码级转移到电路级的重要工具，其可以方便地检查使用硬件描述语言（HDL）编写的代码间的逻辑关系，并了解输入和输出的连接关系。

若要使用原理图功能，你需要确认通过波形仿真和编译。点击 `Tools - Schematic Viwer` 即可查看。

### 综合

在此步骤下，需要进行硬件管脚约束，以便 PDS 确认 Verilog 中包含的端口与硬件对应。你可以直接编写管脚约束文件 `.fdc`，其格式如下：
```ruby
define_attribute {p:led[7]} {PAP_IO_DIRECTION} {OUTPUT}
define_attribute {p:led[7]} {PAP_IO_LOC} {F8}
define_attribute {p:led[7]} {PAP_IO_VCCIO} {3.3}
define_attribute {p:led[7]} {PAP_IO_STANDARD} {LVCMOS33}
define_attribute {p:led[7]} {PAP_IO_DRIVE} {8}
define_attribute {p:led[7]} {PAP_IO_NONE} {TRUE}
define_attribute {p:led[7]} {PAP_IO_SLEW} {SLOW}
```

除此之外，PDS 也提供了 GUI 的管脚约束功能，你可以通过点击 `Tools - User Constraint Editer - Pre Synthesize UCE` 打开该功能。点击 `device` 选项，然后在左边二级菜单中点击 `I/O table` 以对系统所有的输入和输出接口进行约束，在选择对应的管脚编号后，其会自动生成管脚电压、驱动等内容。完成编辑后，点击保存按钮，将自动生成 `.fdc` 文件。

**请注意，在约束前你需要确定所采用的芯片部件编号，并仔细对照接口的管脚编号是否正确。**

#### 提示

请注意，PDS 不允许设计代码中的 `always` 块引入异步复位但不使用的情况，例如：
```ruby
always@(posedge clk or negedge rst) begin
    key_reg <= key;
end
```
在上述示例代码中，引入了 `negedge rst` 异步复位模式，但是未指定当复位信号变化时，寄存器 `key_reg` 的变化。这样会产生风险：在复位信号来临时，系统仍然在保持运行。应当修改为：

```ruby
always@(posedge clk or negedge rst) begin
    if(!rst) key_reg <= 0;        // PDS 在 rst 为 null 时会对该信号报错
    else key_reg <= key;
end
```

### 布局布线

在此步骤下，你应该处理时钟约束问题。

#### 忽略单个引脚的时序约束问题

某些时钟信号由于一些原因，没有被安排到 FPGA 器件的时钟专用引脚上，这就会导致触发错误。

错误内容为：
```
Place-0084: GLOBAL_CLOCK: the driver [port] fixed at [position] is unreasonable. Sub-optimal placement for a clock source and a clock buffer.
```

解决方法是：在 `Pre Synthesize UCE` 功能中选择 `Attributes` 选项，然后在其中添加相关输出网络（Nets）名称，并选择 `PAP_CLOCK_DEDICATED_ROUTE` 的值为 `FALSE`。

### 下载至开发板

在生成比特流文件后，点击 `Tools - Configuration` 打开设备管理功能。

如果板子与电脑连接正确，你应该可以在点击 `File - Connect To Server` 后，在 `Device Properties` 窗格中看到你的设备信息。

如果你的板子不支持 SPI Flash，请选择 `Boundary Scan` 并在右侧窗口中右键选择 `Add Pango Device` 以添加比特流文件。然后你将可以 `Program Device`。

## 在 Windows 配置 TensorFlow-GPU 版本

### 先决条件

  1. Windows 版本：Windows10 1909 或以上；
  2. Nvidia GPU 兼容性检查请参阅[支持 Cuda 的 GPU 型号](https://developer.nvidia.com/cuda-gpus)；
  3. Cuda 支持与 cuDNN 支持请参阅 [TensorFlow 经过测试的兼容版本](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)；
  4. 确保 Nvidia GPU 驱动程序处于最新版本，如需保证驱动程序始终为最新，可参阅 [NVIDIA Geforce Experience](https://www.nvidia.cn/geforce/geforce-experience/)。

请注意，根据 Tensorflow 支持网站给出的信息，TensorFlow-GPU 版本 2.11 已经不支持原生 Windows 的 GPU 运行。如果你需要在 Windows 本地运行 GPU 版本的 TensorFlow，那么只能选择 TensorFlow-GPU 版本 2.10。如果你必须在 Windows 使用 2.11 或更高版本的 TensorFlow-GPU，请考虑 WSL2 或参阅[在 Windows 环境中从源代码构建](https://tensorflow.google.cn/install/source_windows?hl=zh-cn)。

### 安装 Cuda 计算核心驱动和 cuDNN 依赖库

NVIDIA CUDA（Compute Unified Device Architecture）是一种用于 GPU 并行计算的平行计算平台和编程模型，旨在为 GPU 提供一种通用的编程接口和编程模型，使得开发人员可以通过编写 CUDA 程序来利用 GPU 进行并行计算。

下载 Cuda 驱动程序和 cuDNN 时，你应该确保驱动程序版本、cuDNN 版本与 [TensorFlow 经过测试的兼容版本](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)所列出的 TensorFlow 版本相兼容。

Cuda 驱动程序下载点击[此处](https://developer.nvidia.com/cuda-toolkit-archive)，cuDNN 库下载点击[此处](https://developer.nvidia.com/rdp/cudnn-archive)。

在安装 Cuda 驱动程序完成后，将 cuDNN 包的文件夹拷贝到 Cuda 的安装目录下，替换文件夹 `bin`、`include` 和 `lib`。

在完成上述操作后，将 Cuda 的安装文件父文件夹添加到 Windows 系统的 `Path` 环境变量。

<BR>如果部署完成，在 [Windows 终端](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)中输入：
```
nvcc -V
```
应当输出 Cuda 驱动程序版本号。

### 安装 Anaconda 应用程序

使用 Anaconda 应用程序来构建 TensorFlow 有以下几个好处：

  1. 管理依赖关系：Anaconda 应用程序可以自动管理 TensorFlow 所依赖的库和工具，确保 TensorFlow 的依赖关系正确无误，避免由于依赖问题导致构建失败或运行时出错。
  2. 跨平台支持：Anaconda 应用程序支持多种操作系统，包括 Windows、Linux 和 MacOS，可以在不同平台上构建和运行 TensorFlow 应用程序。
  3. 创建虚拟环境：Anaconda 应用程序支持创建虚拟环境，可以在不同的环境中构建和运行 TensorFlow 应用程序，避免不同项目之间的依赖冲突。
  4. 简化构建过程：Anaconda 应用程序提供了一种简单的方式来构建和管理 TensorFlow 应用程序，用户只需要执行一些简单的命令，就可以自动构建和安装 TensorFlow，避免了繁琐的手动配置和安装过程。
  5. 安装其他库和工具：Anaconda 应用程序还提供了一个广泛的科学计算库和工具的集合，用户可以方便地安装和使用这些库和工具，如 NumPy、SciPy、Matplotlib 等，可以方便地进行科学计算和数据分析。

点击[此处](https://www.anaconda.com/)以访问 Anaconda 网站。

#### 使用 `Anaconda Prompt` 构建 TensorFlow 虚拟环境

在 `Anaconda Prompt` 应用程序中输入下述命令可以查看当前所有虚拟环境。
```
conda env list
```

<br>如需创建一个新的 TensorFlow 环境，可输入下述命令。
```
conda create -n tensorflow python=3.9
```
其中，`tensorflow` 为用户指定的虚拟环境名称。**请注意**，此命名不代表指定该虚拟环境为 TensorFlow 依赖环境。`python=3.9` 代表指定该虚拟环境为 Python3.9 版本，请注意，此处的 Python 只在此虚拟环境中唯一生效。

### 在上述虚拟环境中部署 TensorFlow-GPU

#### 使用离线安装

在虚拟环境中安装 TensorFlow-GPU 版本，请首先参阅[根据 Python 版本指定 whl 的网址](https://tensorflow.google.cn/install/pip?hl=zh-cn#package-location)，并下载指定版本的 `whl` 依赖文件。

如果未自定义设置安装目录，你应该可以在 `C:\Users\ [users] \Downloads` 中找到对应的 `whl` 文件。

然后，请激活名为 `tensorFlow` 的虚拟环境，使用下述命令：
```
activate tensorflow
```
此时根名称应该从 `base` 变为 `tensorflow` 。

<br>输入以下指令，以开始部署 TensorFlow-GPU 版本。
```
pip install C:\Users\ [users] \Downloads\tensorflow_gpu-2.6.0-cp39-cp39-manylinux2010_x86_64.whl
```

#### 使用在线安装

你可以使用 `pip install tensorflow-gpu=[version]` 指令在线安装指定版本的 TensorFlow-GPU。

请注意，下载可能由于网络问题中断，你可以更换 Anaconda 的下载源来确保正确安装。

### 验证 TensorFlow-GPU 是否安装成功

在虚拟环境中进入 Python 环境，并输入下述命令：
```
>>> import tensorflow as tf
>>> tf.test.is_gpu_available()
```
如果可以正确显示 Nvidia GPU 型号和显存大小，或者在末尾显示 `True` 字符，则代表 TensorFlow-GPU 完成部署。