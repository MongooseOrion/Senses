# 在 Windows 配置 TensorFlow-GPU 版本

## 先决条件

  1. Windows 版本：Windows10 1909 或以上；
  2. Nvidia GPU 兼容性检查请参阅[支持 Cuda 的 GPU 型号](https://developer.nvidia.com/cuda-gpus)；
  3. Cuda 支持与 cuDNN 支持请参阅 [TensorFlow 经过测试的兼容版本](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)；
  4. 确保 Nvidia GPU 驱动程序处于最新版本，如需保证驱动程序始终为最新，可参阅 [NVIDIA Geforce Experience](https://www.nvidia.cn/geforce/geforce-experience/)。

请注意，根据 Tensorflow 支持网站给出的信息，TensorFlow-GPU 版本 2.11 已经不支持原生 Windows 的 GPU 运行。如果你需要在 Windows 本地运行 GPU 版本的 TensorFlow，那么只能选择 TensorFlow-GPU 版本 2.10。如果你必须在 Windows 使用 2.11 或更高版本的 TensorFlow-GPU，请考虑 WSL2 或参阅[在 Windows 环境中从源代码构建](https://tensorflow.google.cn/install/source_windows?hl=zh-cn)。

## 安装 Cuda 计算核心驱动和 cuDNN 依赖库

NVIDIA CUDA（Compute Unified Device Architecture）是一种用于 GPU 并行计算的平行计算平台和编程模型，旨在为 GPU 提供一种通用的编程接口和编程模型，使得开发人员可以通过编写 CUDA 程序来利用 GPU 进行并行计算。

下载 Cuda 驱动程序和 cuDNN 时，你应该确保驱动程序版本、cuDNN 版本与 [TensorFlow 经过测试的兼容版本](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)所列出的 TensorFlow 版本相兼容。

Cuda 驱动程序下载点击[此处](https://developer.nvidia.com/cuda-toolkit-archive)，cuDNN 库下载点击[此处](https://developer.nvidia.com/rdp/cudnn-archive)。

在安装 Cuda 驱动程序完成后，将 cuDNN 包的文件夹拷贝到 Cuda 的安装目录下，替换文件夹 `bin`、`include` 和 `lib`。

在完成上述操作后，将 Cuda 的安装文件父文件夹添加到 Windows 系统的 `Path` 环境变量。

---

如果部署完成，在 [Windows 终端](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)中输入：

```
nvcc -V
```

应当输出 Cuda 驱动程序版本号。

## 安装 Anaconda 应用程序

使用 Anaconda 应用程序来构建 TensorFlow 有以下几个好处：

  1. 管理依赖关系：Anaconda 应用程序可以自动管理 TensorFlow 所依赖的库和工具，确保 TensorFlow 的依赖关系正确无误，避免由于依赖问题导致构建失败或运行时出错。
  2. 跨平台支持：Anaconda 应用程序支持多种操作系统，包括 Windows、Linux 和 MacOS，可以在不同平台上构建和运行 TensorFlow 应用程序。
  3. 创建虚拟环境：Anaconda 应用程序支持创建虚拟环境，可以在不同的环境中构建和运行 TensorFlow 应用程序，避免不同项目之间的依赖冲突。
  4. 简化构建过程：Anaconda 应用程序提供了一种简单的方式来构建和管理 TensorFlow 应用程序，用户只需要执行一些简单的命令，就可以自动构建和安装 TensorFlow，避免了繁琐的手动配置和安装过程。
  5. 安装其他库和工具：Anaconda 应用程序还提供了一个广泛的科学计算库和工具的集合，用户可以方便地安装和使用这些库和工具，如 NumPy、SciPy、Matplotlib 等，可以方便地进行科学计算和数据分析。

点击[此处](https://www.anaconda.com/)以访问 Anaconda 网站。

### 使用 `Anaconda Prompt` 构建 TensorFlow 虚拟环境

在 `Anaconda Prompt` 应用程序中输入下述命令可以查看当前所有虚拟环境。
```
conda env list
```

<br>如需创建一个新的 TensorFlow 环境，可输入下述命令。
```
conda create -n tensorflow python=3.9
```
其中，`tensorflow` 为用户指定的虚拟环境名称。**请注意**，此命名不代表指定该虚拟环境为 TensorFlow 依赖环境。`python=3.9` 代表指定该虚拟环境为 Python3.9 版本，请注意，此处的 Python 只在此虚拟环境中唯一生效。

## 在上述虚拟环境中部署 TensorFlow-GPU

### 使用离线安装

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

### 使用在线安装

你可以使用 `pip install tensorflow=[version]` 指令在线安装指定版本的 CPU、GPU 集成版本 TensorFlow。

请注意，下载可能由于网络问题中断，你可以更换 Anaconda 的下载源来确保正确安装。

## 验证 TensorFlow-GPU 是否安装成功

在虚拟环境中进入 Python 环境，并输入下述命令：
```
>>> import tensorflow as tf
>>> tf.test.is_gpu_available()
```
如果可以正确显示 Nvidia GPU 型号和显存大小，或者在末尾显示 `True` 字符，则代表 TensorFlow-GPU 完成部署。