# 利用 WSL 运行 Xilinx Vitis AI

本页将介绍使用适用于 Linux 的 Windows 子系统（WSL）部署 CPU 版本的 Xilinx Vitis AI 主机运行环境的相关配置和步骤。部分步骤可能省略，你或许可以在页面最后的相关文档中查看更加具体的内容。

在主机上安装 Vitis AI 的主要作用是提供一个方便的开发和测试环境，使开发者能够在本地进行模型的开发、调试和验证。经过验证的模型最终会部署到开发板上运行，以利用硬件加速的优势。这样可以提高开发效率，减少在硬件上调试的时间和复杂度。

## 先决条件

  * Windows10 版本 18362 或更高版本
  * [已安装 WSL2](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/WSL.md)，发行版本为 [Ubuntu 22.04](https://www.microsoft.com/store/productid/9PDXGNCFSCZV?ocid=pdpshare)（可选）
  * [已安装 Docker Desktop for Windows](https://docs.docker.com/desktop/wsl/#download)

在运行任何负载前，建议你首先在 WSL 发行版中键入下述命令：

```
>> sudo apt-get update
>> sudo apt-get upgrade
```

以确保 `apt install` 命令可以工作。

## 本页内容

  * 配置 Docker Desktop
  * 拉取 Vitis-AI 仓库
  * 安装 Vitis-AI Docker 镜像
  * 部署交叉编译工具链
  * 运行深度学习项目示例

## 配置 Docker Desktop

在安装 Docker Desktop for Windows 后，你需要确保在 “设置”>“常规” 中选中 “使用基于 WSL2 的引擎”，然后转到 “设置”>“资源”>“WSL 集成”，选择要启用 Docker 集成的已安装 WSL2 发行版。

如果配置无误，你将可以在 WSL 发行版中通过输入 `docker --version` 看到版本和内部版本号。

通过使用 `docker run hello-world` 运行简单的内置 Docker 映像，可测试安装是否正常工作。

<div align='center'><img src = '../Picture\vit\屏幕截图 2023-08-31 142420.png' height='300' title='运行 Hello world Docker 映像应该出现的结果'></div>

### 非管理员用户管理 Docker

Docker 允许多用户访问同一映像，如果需要，你可以通过 `sudo groupadd docker` 创建群组。如需加入新的协作用户，你可以使用下述命令：
```
>> sudo usermod -aG docker <USER>
```
然后你需要重启 Docker，可使用下述命令中的任意一个：
```
>> sudo snap restart docker /
>> sudo service docker restart /
>> sudo /etc/init.d/docker restart
```
重启会话后，必须通过 `newgrp-docker` 从当前用户组切换到 Docker 用户组。

## 拉取 Vitis-AI 仓库

一般情况下，WSL 发行版中已经安装了 Git，但你可能需要通过 `sudo apt upgrade git` 将其更新到最新版。若要了解如何配置 Git 中的信息，你可以在相关文档 2 中查阅。

如果你在 WSL 中使用 `mkdir` 命令创建了一个文件夹，并且你不能确认文件或者文件夹的存放位置，则你可以在 Windows 资源管理器中的 `\\wsl.localhost\Ubuntu\home\<USER>\<NEW DIR>` 下看到该文件夹。也就是说 WSL 挂载的工作目录为 `\\wsl.localhost\Ubuntu\home\<USER>\`，在 WSL 中可键入 `cd /home/<USER>` 回到主工作目录。

Vitis-AI 的 GitHub 仓库位置在 `https://github.com/Xilinx/Vitis-AI`，你可以直接拉取最新版，也可以拉取早期版本。你可以查看仓库分支选择合适的版本，此文档使用 2.5 版本，使用下述命令以拉取该分支：

```bash
>> git clone -b 2.5 https://github.com/Xilinx/Vitis-AI
```

如果发现 WSL 的网络流量不使用本机的代理端口，可以尝试使用 `cat /etc/resolv.conf` 命令获取 WSL 的 DNS 服务器位置，然后通过环境变量 `ALL_PROXY` 配置代理：
```
export ALL_PROXY="http://<DNS IP>:<proxy port>"
```
注意需要在本机的代理软件中设置允许来自局域网的流量（ALLOW LAN）。

## 安装 Vitis-AI-CPU Docker 镜像

使用下述命令直接下载并安装适用于 CPU 的 Vitis-AI 最新版：
```bash
>> cd Vitis-AI
>> docker pull xilinx/vitis-ai-<Framework>-<Arch>:latest
```

你需要按照下表按需填入参数：
| `<Framework>` | `<Arch>` | 描述 |
| :---: | :---: | :--- |
| pytorch | cpu | CPU 版本的 pytorch |
| tensorflow2 | cpu | CPU 版本的 tensorflow2 |
| tensorflow | cpu | CPU 版本的 tensorflow1.15 |
| pytorch | rocm | ROCm 版本的 pytorch |
| tensorflow | rocm | ROCm 版本的 tensorflow2 |

例如，如果你想要下载 CPU 版本的 TensorFlow2 docker 镜像，可以使用命令：

```bash
>> cd <VITIS-AI INSTALL PATH>/Vitis-AI/
>> docker pull xilinx/vitis-ai-tensorflow2-cpu:latest
```

下载可能需要一段时间，请坐和放宽。如果出现无法找到特定包的情况，可以尝试重新运行该脚本。

## 部署交叉编译工具链

运行下述命令：

```bash
>> cd <VITIS-AI INSTALL PATH>/Vitis-AI/setup/mpsoc
>> bash host_cross_compiler_setup.sh
```

应该会开始下载 petalinux_sdk_2022.1_sdk。

<div align='center'><img src='../Picture\vit\屏幕截图 2023-09-03 145630.png' height='250'></div>

在下载完成后，按照提示键入：

```bash
>> source ~/petalinux_sdk_2022.1/environment-setup-cortexa72-cortexa53-xilinx-linux
```

即可配置交叉编译环境。

你可以测试编译功能，在输入下述命令后，你应该可以在同一子文件夹下看到名为 `resnet50` 的文件：

```bash
>> cd <VITIS-AI INSTALL PATH>/Vitis-AI/examples/VART/resnet50
>> bash -x build.sh
```

### 搭建工作环境

*请确认 Docker Desktop for Windows 已经运行。*

使用下述命令启动适用于 Vitis-AI 的 Docker：
```bash
>> cd <Vitis-AI install path>/Vitis-AI
>> ./docker_run.sh xilinx/vitis-ai-tensorflow2-cpu:latest
```

<div align='center'><img src='../Picture\vit\屏幕截图 2023-09-03 183820.png' height='250'></div>

如果没有问题，你应该可以在 Docker Desktop for Windows 应用中看到正在运行的 Vitis-AI 容器。

在使用统一脚本部署 Vitis-AI-CPU 时，已经自动下载了包含开发需要使用包的 conda 虚拟环境，你可以使用命令 `conda activate vitis-ai-tensorflow2` 激活该虚拟环境。

如需退出虚拟环境，可键入 `conda deactivate`，如需退出容器，可键入 `exit`。如需关闭容器，可键入 `docker stop <CONTAINER_ID>`。

## 在主机和开发板上运行模型

### 在主机上评估标准模型



### 在开发板上运行转译、量化后的模型

你可以[点此](https://xilinx.github.io/Vitis-AI/3.0/html/docs/workflow-model-zoo.html)了解 Vitis-AI 存储库中的预构建模型库如何使用。

同时，你可以[点此](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/run_kv260.md)了解如何在 KV260 板上运行模型。

## 相关文档

  1. 如需了解使用 VS Code 在远程容器中开发，请[点此](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-containers)访问；
  2. 如需了解如何在每个 WSL 发行版中安装和配置 Git，请[点此](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-git)访问；
  3. 如需了解在 WSL 和 Windows 之间的跨文件操作，请[点此](https://learn.microsoft.com/zh-cn/windows/wsl/filesystems)访问；
  4. 如需了解在 Docker 中使用 Nvidia GPU 加速，请[点此](https://xilinx.github.io/Vitis-AI/3.5/html/docs/install/install.html)访问；