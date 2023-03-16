# 在 Windows 中实现整个工作流
自 Windows10 的第一个正式版本 1507 发布已经过去了 8 年。还记得 2014 年，所有媒体都在疯狂尝鲜、报导新的 Windows 操作系统，那个时候我拿着 Surface Pro3，还在写 c 的 “Hello world” 程序。<br><br>
事实上，与 Windows11 发布前夕泄露 22000 版本后我立即尝试安装不同，以前我花了 2 年时间才最终决定从 Windows8 更新到 Windows10。Windows8.1 始终不能令我割舍的是**开始菜单**功能，不得不说时至今日我仍然还是会说 Win8 的**开始**设计很前卫。当然，UWP 和 Fluent Design 也一直在吸引着我。很可惜的是，我最终错过了 UWP 最繁荣的时期。<br><br>
废话不多说，毋庸置疑的是 Windows11 现在有非常完备的开发工具链，当然也有非常好的兼容性（其实我并不喜欢这个历史包袱）。导师建议我可以尝试在 Linux 上运行某些负载，而我觉得 Windows 足以胜任，这也是我决定写这个文档的源动力。

## 本页内容
  * 使用 Windows 本地运行 Linux 负载和 Android 应用程序
  * 使用紫光同创 FPGA 开发工具链替代 Xilinx 工具
  * 在 Windows 配置 TensorFlow-GPU 版本

## 使用 Windows 本地运行 Linux 负载和 Android 应用程序
在本章，将介绍如何使用 [Windows 终端](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)配置 Python 环境和运行[适用于 Windows 的 Linux 子系统（WSL2）](https://learn.microsoft.com/zh-cn/windows/wsl/about)。

### 先决条件
  1. Windows11 且内部版本号在 22000.194 或以上；
  2. 机带 RAM 不少于 8GB。

### 部署 Python 环境

在 Micorsoft store 中可以直接安装 Python，相比于自定义安装，这样做的好处在于 Visual Studio 可以直接识别 Python 环境而无需额外配置，并可以方便地移除。

要构建 Python 之前，请确认源代码或开发工具依赖的 Python 版本，Python3.9 可点击[此处](ms-windows-store://pdp/?ProductId=9p7qfqmjrfp7&referrer=bingwebsearch&ocid=bingwebsearch)安装。

如果未自定义安装目录，你可以在 `C:\Users\ [user] \AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_qbz5n2kfra8p0\LocalCache\local-packages\Python39\Scripts` 路径中找到使用 `pip install` 命令安装的第三方模块。

<br>请将该路径加入 `Path` 环境变量中，以便直接从 Windows 终端中进入 Python 环境。

### 配置 WSL2

点击[此处](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R)安装 WSL 工具，该工具可以管理系统中安装的所有 WSL 分发版本。



## 使用紫光同创 FPGA 开发工具链替代 Xilinx 工具

紫光同创的 FPGA 开发工具为 Pango Design Suite 和 Pango Design Suite Lite（PDS），在此章节将介绍如何使用 PDS 工具。

*假定你已经安装好 PDS 应用程序和 Modelsim。*

## 在 Windows 配置 TensorFlow-GPU 版本

### 先决条件

  1. Windows 版本：Windows 10 1909 或以上；
  2. Nvidia GPU 兼容性检查请参阅[支持 Cuda 的 GPU 型号](https://developer.nvidia.com/cuda-gpus)；
  3. Cuda 支持与 cuDNN 支持请参阅 [TensorFlow 经过测试的兼容版本](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)；
  4. 确保 Nvidia GPU 驱动程序处于最新版本，如需保证驱动程序始终为最新，可参阅 [NVIDIA Geforce experience](https://www.nvidia.cn/geforce/geforce-experience/)。

### 安装 Cuda 计算核心驱动和 cuDNN 依赖库

NVIDIA CUDA（Compute Unified Device Architecture）是一种用于 GPU 并行计算的平行计算平台和编程模型，旨在为 GPU 提供一种通用的编程接口和编程模型，使得开发人员可以通过编写 CUDA 程序来利用 GPU 进行并行计算。

下载 Cuda 驱动程序和 cuDNN 时，应该确保驱动程序版本、cuDNN 版本与 [TensorFlow 经过测试的兼容版本](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)所列出的 TensorFlow 版本相兼容。

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

#### 在上述虚拟环境中部署 TensorFlow-GPU
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

#### 验证 TensorFlow-GPU 是否安装成功

在虚拟环境中进入 Python 环境，并输入下述命令：
```
>>> import tensorflow as tf
>>> tf.test.is_gpu_available()
```
如果可以正确显示 Nvidia GPU 型号和显存大小，或者在末尾显示 `True` 字符，则代表 TensorFlow-GPU 完成部署。