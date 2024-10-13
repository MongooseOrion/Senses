# 在 Ubuntu 下部署 Xilinx Vitis-AI 计算环境

## 先决条件

*这些条件经过可用性测试，但并不说明仅在这些条件下才可以运行，你或许可以自行测试其他的运行环境。*

  * Ubuntu 版本 20.04
  * 内存：4GB
  * 可用空间：60GB
  * 处理器核心：4 核，每个核心线程数为 1
  * Vitis-AI 版本 2.5

如果你希望使用[适用于 Linux 的 Windows 子系统](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/WSL.md)（WSL）来构建 Vitis-AI 运行环境，请[点此](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/wsl_vitis_ai.md)访问。

## 本页内容

  * 拉取 Vitis-AI 仓库
  * 安装 Docker Container
  * 安装 Anaconda
  * 配置 Vitis-AI Docker 环境

*注意：首次运行终端时，建议通过如下命令更新所有系统依赖。*
```bash
>> sudo apt update
>> sudo apt upgrade
```

## 兼容性故障排除

在此处列出了一些使用预置的虚拟镜像可能出现的问题和对应的解决方案，你可以尝试排查故障。

### 提示虚拟磁盘不兼容，无法打开预置的虚拟磁盘

这是由于预置的 Ubuntu20.04 镜像是基于 VMware17.0.2 制作的。如果你运行的 VMware 是早期版本，则你可以通过点击 `虚拟机` - `管理` - `更改硬件兼容性`，将该虚拟磁盘使用兼容模式运行。

### 主机已连接网络，但虚拟机无法访问互联网

这可能是由于局域网内存在多个相同的物理地址而导致虚拟机被阻止访问互联网。若要解决此问题，请遵循如下步骤：
  1. 确认虚拟机为关机状态；
  1. 确认在 VMware 虚拟机设置中的网络适配器模式为 `NAT` 模式；
  2. 在 `虚拟网络首选项` 中对应的虚拟网卡处设置重新生成一个 MAC 地址和子网 IP 地址；
  3. 在 Windows 设置中点击物理网卡属性，然后设置共享互联网连接到指定的虚拟网卡；
  4. 开启虚拟机，并打开终端，输入如下命令：

```bash
>> sudo service network-manager stop
>> sudo rm /var/lib/NetworkManager/NetworkManager.state
>> sudo service network-manager start
```

你应该可以在执行上述操作后，在虚拟机右上角看到网络有线连接的标识。

## 拉取 Vitis-AI 仓库

### 安装 Git

你需要使用 Git 拉取位于 GitHub 的 Vitis-AI 远程仓库。通过输入以下命令，你可以安装 Git：
```bash
>> sudo apt install git
```

### 拉取仓库

Vitis-AI 的 GitHub 仓库位置在 `https://github.com/Xilinx/Vitis-AI`，你可以直接拉取最新版，也可以拉取早期版本。你可以查看仓库分支选择合适的版本，**此文档使用 2.5 版本**。使用下述命令以拉取该分支：

```bash
>> git clone -b 2.5 https://github.com/Xilinx/Vitis-AI
```

## 配置 Docker Container 应用程序

### 安装 Docker Container
首先，通过下述命令更新软件包索引，并且安装必要的依赖软件：
```bash
>> sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```

然后，使用 `curl` 导入源仓库的 GPG key：
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

将 Docker APT 软件源添加到系统中：
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

运行下述命令可直接安装最新版 Docker Container 应用程序：
```bash
sudo apt install docker-ce docker-ce-cli containerd.io
```

### 验证 Docker Container 运行状态

通过运行 `sudo systemctl status docker`，你将可以看到 Docker 运行状态，如果正常运行，它将显示类似于下述的信息：
```bash
● docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset>
     Active: active (running) since Tue 2023-10-10 20:41:02 CST; 13min ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
   Main PID: 1086 (dockerd)
      Tasks: 13
     Memory: 98.7M
     CGroup: /system.slice/docker.service
             └─1086 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/cont>

10月 10 20:40:57 ubuntu dockerd[1086]: time="2023-10-10T20:40:57.190108404+08:0>
10月 10 20:40:57 ubuntu dockerd[1086]: time="2023-10-10T20:40:57.234916952+08:0>
10月 10 20:40:58 ubuntu dockerd[1086]: time="2023-10-10T20:40:58.196150681+08:0>
10月 10 20:40:58 ubuntu dockerd[1086]: time="2023-10-10T20:40:58.287704676+08:0>
10月 10 20:41:01 ubuntu dockerd[1086]: time="2023-10-10T20:41:01.138433753+08:0>
10月 10 20:41:01 ubuntu dockerd[1086]: time="2023-10-10T20:41:01.750789042+08:0>
10月 10 20:41:02 ubuntu dockerd[1086]: time="2023-10-10T20:41:02.299463077+08:0>
10月 10 20:41:02 ubuntu dockerd[1086]: time="2023-10-10T20:41:02.300051177+08:0>
10月 10 20:41:02 ubuntu dockerd[1086]: time="2023-10-10T20:41:02.649779318+08:0>
10月 10 20:41:02 ubuntu systemd[1]: Started Docker Application Container Engine.
lines 1-21/21 (END)
```
*注意：你需要键入 `:q` 才可以继续键入命令。*

你还可以通过运行 `docker run hello-world` 命令来运行 Docker Hello world 容器，如果 Docker 正常运行，应该出现下述信息：
```bash
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

如果显示用户无权访问 Docker 或存在网络错误，请参阅下述两节内容。

### 将非授权用户添加到用户组

首先，你需要创建一个适用于 Docker 的群组：
```bash
>> sudo groupadd docker
```

然后，将用户添加入该群组：
```
>> sudo usermod -aG docker <USER_NAME>
```
其中，`<USER_NAME>` 处填入用户名称。

再重启 Docker Container：
```bash
>> sudo systemctl restart docker
```

此时，该用户应该具备运行 Docker 的权限。

### 更换 Docker 下载源为国内源

首先，你需要下载 Vim，你可以直接在 Ubuntu 应用商店下载，或者在终端中键入下述命令：

```bash
>> sudo apt install vim
```

一旦下载完成，请在终端键入：
```bash
>> vim /etc/docker/daemon.json
```

然后输入 `i` 进入编辑模式，添加如下内容：
```bash
{
    "registry-mirrors": [ 
        "https://docker.mirrors.ustc.edu.cn"    // 更换为清华源
    ]
}
```

按下 `ESC` 可退出编辑模式，按下 `:wq` 保存并退出。

然后，你需要重启 Docker Container 以生效。

## 安装 Anaconda

### 下载安装文件并部署 Anaconda

你可以在[清华源](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)处下载合适的 Anaconda 配置文件，对于 AMD64，请安装 x86-x64，对于 ARM64，请安装 aarch64。

切换到下载目录，然后执行 bash 安装。

```bash
>> cd <ANACONDA_DOWNLOAD_PATH>
>> bash <FILE_NAME>
```

安装完成后，建议注销后重新运行终端，以确保 Anaconda 生效。

若要验证 Anaconda 是否安装成功，你可以使用 `conda list` 或 `conda --version` 来检查。

### 创建 Anaconda 虚拟环境

使用下述命令创建虚拟环境：
```bash
>> conda create --name <ENV_NAME> <PACKEDGE_NAME>
```
其中，`<EVN_NAME>` 填入虚拟环境名称，`<PACKEDGE_NAME>` 用于指定虚拟环境中的 Python 版本，例如你想创建一个 Python 版本为 3.9 名为 tensorflow 的虚拟环境，你应该输入：
```bash
>> conda create --name tensorflow python=3.9
```

若要进入指定虚拟环境，请输入：
```bash
>> conda activate <ENV_NAME>
```

若要停用指定虚拟环境，请输入：
```bash
>> conda deactivate <ENV_NAME>
```

或返回主环境：
```bash
>> conda activate base
```

### 在虚拟环境中安装 python 包

你可以进入指定环境，然后使用 `pip install` 来下载和安装 python 包。你需要安装的包包括但不限于：

  * tensorflow==2.7
  * opencv_python
  * matplot
  * notebook

**注意：预置的镜像中已经创建了名为 `tensorflow` 的虚拟环境，已经包含上述包，你可以直接激活该环境。**

## 安装 Vitis-AI-CPU Docker 镜像

你需要首先切换到 Vitis-AI 本地仓库，你可以输入该命令：

```bash
>> cd Vitis-AI
>> docker pull xilinx/vitis-ai-cpu:latest
```
*注意：这可能需要一些时间。*

## 部署交叉编译工具链

这里将使用 VART 边缘平台部署交叉编译环境。
```bash
>> cd <VITIS-AI INSTALL PATH>/Vitis-AI/setup/mpsoc
>> bash host_cross_compiler_setup.sh
```

应该会开始下载 petalinux_sdk_2022.1_sdk。

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

**注意：如果你想要重新生成 `resnet50` 文件以测试编译功能，则你需要重新执行下述命令：**

```bash
>> source ~/petalinux_sdk_2022.1/environment-setup-cortexa72-cortexa53-xilinx-linux
```

## 运行深度学习项目示例

### 搭建工作环境

使用下述命令启动适用于 Vitis-AI 的 Docker：
```bash
>> cd <Vitis-AI install path>/Vitis-AI
>> ./docker_run.sh xilinx/vitis-ai-cpu:latest
```

如果你可以在控制台看到 Vitis-AI 的标识，则说明它可以正常启动。

### 运行深度学习项目示例

现在，你可以[点此](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/run_kv260.md)来了解在 KV260 板上开发的内容。