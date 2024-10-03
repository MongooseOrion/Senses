# 使用 Windows 本地运行 Linux 负载和 Android 应用程序

本文将介绍如何使用 [Windows 终端](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)配置 Python 环境、运行[适用于 Linux 的 Windows 子系统（WSL2）](https://learn.microsoft.com/zh-cn/windows/wsl/about)和适用于 Android 的 Windows 子系统（已被弃用）。

## 先决条件

  1. Windows11 且内部版本号在 22000.194 或以上；
  2. 机带 RAM 不少于 8GB。

## 部署 Python 环境

在 Micorsoft store 中可以直接安装 Python，相比于自定义安装，这样做的好处在于 Visual Studio 可以直接识别 Python 环境而无需额外配置，并可以方便地移除。

要构建 Python 之前，请确认源代码或开发工具依赖的 Python 版本，Python3.9 可点击[此处](https://apps.microsoft.com/store/detail/python-39/9P7QFQMJRFP7?hl=en-us&gl=us)安装。

如果未自定义安装目录，你可以在 `C:\Users\ [username] \AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_qbz5n2kfra8p0\LocalCache\local-packages\Python39\Scripts` 路径中找到使用 `pip install` 命令安装的第三方模块。

<br>请将该路径加入 `Path` 环境变量中，以便直接从 Windows 终端中进入 Python 环境。

如果部署完成，你应该可以在终端中输入 `python` 后进入 Python 环境。

## 配置 WSL2

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

## 运行适用于 Android 的 Windows 子系统（WSA）

你可以在 Microsoft store 中搜索 Amazon appstore，下载并安装后，开始菜单中将出现名为 `适用于 Android 的 Windows 子系统设置` 的应用程序。打开 `开发人员 - 开发人员模式`，此时会出现内网 IP 地址，即可使用 Android 调试桥（ADB）旁加载应用程序，或将 WSA 设置为 Android Studio 默认虚拟机。

WSA 可以直接运行基于 ARM64 和 x86 开发的 Android 应用程序，以下功能获得完全支持：
  * 触控，具体取决于本地硬件的触控支持；
  * 扬声器
  * 摄像头
  * 麦克风

以下功能部分支持：
  * 图形处理器，不支持 Vulkan 引擎，推荐 Intel 或 Nvidia 的核芯显卡和独立显卡；

可按需利用 WSA 进行 Android 应用程序开发。