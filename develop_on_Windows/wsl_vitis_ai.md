# 利用 WSL 运行 Xilinx Vitis AI

本页将介绍使用适用于 Linux 的 Windows 子系统（WSL）部署 Xilinx Vitis AI 运行环境的相关配置和步骤。部分步骤可能省略，你或许可以在页面最后的相关文档中查看更加具体的内容。

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
然后你需要重启 Docker，可使用下述命令：
```
>> sudo snap restart docker /
>> sudo service docker restart /
>> sudo /etc/init.d/docker restart
```
重启会话后，必须通过 `newgrp-docker` 从当前用户组切换到 Docker 用户组。

## 拉取 Vitis-AI 仓库

一般情况下，WSL 发行版中已经安装了 Git，但你可能需要通过 `sudo apt upgrade git` 将其更新到最新版。若要了解如何配置 Git 中的信息，你可以在相关文档 2 中查阅。

如果你在 WSL 中使用 `mkdir` 命令创建了一个文件夹，并且你不能确认文件或者文件夹的存放位置，则你可以在 Windows 资源管理器中的 `\\wsl.localhost\Ubuntu\home\<USER>\<NEW DIR>` 下看到该文件夹。也就是说 WSL 挂载的工作目录为 `\\wsl.localhost\Ubuntu\home\<USER>\`，在 WSL 中可键入 `cd /home/<USER>` 回到主工作目录。

Vitis-AI 的 GitHub 仓库位置在 `https://github.com/Xilinx/Vitis-AI`，你可以直接拉取最新版，也可以拉取早期版本。你可以查看仓库分支选择合适的版本，**下述步骤只适用于 `3.5` 或更新版本**。

如果发现 WSL 的网络流量不使用本机的代理端口，可以尝试使用 `cat /etc/resolv.conf` 命令获取 WSL 的 DNS 服务器位置，然后通过环境变量 `ALL_PROXY` 配置代理：
```
export ALL_PROXY="http://<DNS IP>:<proxy port>"
```
注意需要在本机的代理软件中设置允许来自局域网的流量（ALLOW LAN）。

## 安装 Vitis-AI

除非没有可用的 Nvidia GPU，否则不推荐安装 CPU 版本的 Vitis-AI。

### 安装 CPU 或 AMD ROCm 版本的 Vitis-AI

使用下述命令直接下载并安装适用于 CPU 和 AMD ROCm 的 Vitis-AI 最新版：
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
>> cd <vitis-ai install path>/Vitis-AI/
>> docker pull xilinx/vitis-ai-tensorflow2-cpu:latest
```

### 安装 Nvidia GPU (CUDA) 版本的 Vitis-AI

你需要运行下述指令，以部署 Cuda 运行环境：
```bash
>> sudo apt purge nvidia* libnvidia*
>> sudo apt install nvidia-driver-<VERSION>
>> sudo apt install nvidia-container-toolkit
```
在 `<VERSION>` 处填写 Nvidia GPU 的驱动程序版本号，例如指定 `530` 将下载驱动程序 530-539 之间最新的驱动程序。

如果安装无误，你将在输入 `nvidia-smi` 后看到驱动程序版本号和硬件的相关信息。

由于统一脚本不支持 Nvidia GPU，因此你需要在 `Vitis-AI/docker/` 路径下找到 `docker_build.sh`，并从源代码构建 Nvidia GPU 版本的 Vitis-AI。执行命令如下：
```bash
./docker_build.sh -t <DOCKER_TYPE> -f <FRAMEWORK>
```

你需要按照下述表格按需填入参数。

| `<DOCKER_TYPE>` | `<FRAMEWORK>` |说明|
| :---: | :---: | :--- |
| cpu | pytorch | CPU 版本的 pytorch |
|| tf2 | CPU 版本的 TensorFlow2 |
|| tf1 | CPU 版本的 TensorFlow1.15 |
| gpu | pytorch | CUDA GPU 版本的 pytorch |
|| tf2 | CUDA GPU 版本的 TensorFlow2 |
|| tf1 | CUDA GPU 版本的 TensorFlow1.15 |
| rocm | pytorch | ROCm GPU 版本的 pytorch |
|| tf2 | ROCm GPU 版本的 TensorFlow2 |

建议使用 `tf2` 作为目标安装框架，命令为：
```bash
>> cd <vitis-ai install path>/Vitis-AI/docker
>> ./docker_build.sh -t gpu -f tf2
```

下载可能需要几个小时的时间，请坐和放宽。如果出现无法找到特定包的情况，可以尝试重新运行构建脚本。



## 相关文档

  1. 如需了解使用 VS Code 在远程容器中开发，请[点此](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-containers)访问；
  2. 如需了解如何在每个 WSL 发行版中安装和配置 Git，请[点此](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-git)访问；
  3. 如需了解在 WSL 和 Windows 之间的跨文件操作，请[点此](https://learn.microsoft.com/zh-cn/windows/wsl/filesystems)访问；
  4. 如需了解在 Docker 中使用 Nvidia GPU 加速，请[点此](https://xilinx.github.io/Vitis-AI/3.5/html/docs/install/install.html)访问；