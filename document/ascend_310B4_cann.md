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
# 在基于 ARM64 的华为昇腾开发板上部署 CANN 环境和运行模型

本文档基于的硬件平台配置为：

  * 开发板：Orange Pi AI Pro
  * 内存：8GB
  * 昇腾计算平台型号：Ascend310B4
  * Ubuntu 系统版本：Ubuntu 22.04.3 LTS jammy
  * 处理器架构：aarch64 with 4 核 4 线程

这里假设你已经在开发板中正确安装并部署了 Linux 系统，如果没有，请自行访问相关开发板制造商的官方网站。

在开始之前，建议你更新 `apt` 软件包信息：

```bash
sudo apt-get update
```

## 基本依赖的说明

Python 和 cpp 的编译环境版本：

```bash
Python 3.9.2
cmake version 3.29.8
g++ (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
```

你需要与上述的依赖版本保持一致。

Python 包版本：

```bash
Package                   Version
------------------------- ----------------------
absl-py                   2.1.0
aclruntime                0.0.2
ais-bench                 0.0.2
albumentations            1.3.1
annotated-types           0.6.0
anyio                     4.2.0
appdirs                   1.4.4
argon2-cffi               23.1.0
argon2-cffi-bindings      21.2.0
arrow                     1.3.0
ascendebug                0.1.0
asttokens                 2.4.1
astunparse                1.6.3
async-lru                 2.0.4
async-timeout             4.0.3
attrs                     23.2.0
auto_tune                 0.1.0
Babel                     2.14.0
backcall                  0.2.0
beautifulsoup4            4.12.3
bleach                    6.1.0
boltons                   23.0.0
brotlipy                  0.7.0
certifi                   2023.11.17
cffi                      1.15.1
charset-normalizer        2.0.4
click                     8.1.7
comm                      0.2.1
conda                     23.7.4
conda-content-trust       0.1.3
conda-package-handling    2.0.2
conda_package_streaming   0.7.0
construct                 2.10.70
contourpy                 1.2.0
croniter                  2.0.1
cryptography              38.0.4
cycler                    0.12.1
dataflow                  0.0.1
debugpy                   1.8.0
decorator                 5.1.1
defusedxml                0.7.1
exceptiongroup            1.2.0
fastjsonschema            2.19.1
ffmpeg-python             0.2.0
filelock                  3.13.1
fonttools                 4.47.2
fqdn                      1.5.1
fsspec                    2023.12.2
future                    0.18.3
hccl                      0.1.0
hccl_parser               0.1
idna                      3.4
ifaddr                    0.2.0
imageio                   2.33.1
importlib-metadata        7.0.1
importlib-resources       6.1.1
ipykernel                 6.29.0
ipython                   7.34.0
ipywidgets                8.1.1
isoduration               20.11.0
jedi                      0.19.1
Jinja2                    3.1.3
joblib                    1.3.2
json5                     0.9.14
jsonpatch                 1.32
jsonpointer               2.1
jsonschema                4.21.1
jsonschema-specifications 2023.12.1
jupyter_client            8.6.0
jupyter_core              5.7.1
jupyter-events            0.9.0
jupyter-lsp               2.2.2
jupyter_server            2.12.5
jupyter_server_terminals  0.5.2
jupyterlab                4.0.11
jupyterlab_pygments       0.3.0
jupyterlab_server         2.25.2
jupyterlab-widgets        3.0.9
kiwisolver                1.4.5
lazy_loader               0.3
llm_datadist              0.0.1
MarkupSafe                2.1.4
matplotlib                3.8.2
matplotlib-inline         0.1.6
micloud                   0.6
mindspore                 2.2.14
mindspore-lite            2.2.11
mistune                   3.0.2
mpmath                    1.3.0
msadvisor                 1.0.0
msobjdump                 0.1.0
nbclient                  0.9.0
nbconvert                 7.14.2
nbformat                  5.9.2
nest-asyncio              1.6.0
networkx                  3.2.1
notebook_shim             0.2.3
numpy                     1.22.4
op_compile_tool           0.1.0
op_gen                    0.1
op_test_frame             0.1
opc_tool                  0.1.0
opencv-python-headless    4.9.0.80
overrides                 7.6.0
packaging                 23.1
pandocfilters             1.5.1
parso                     0.8.3
pathlib2                  2.3.7.post1
pexpect                   4.9.0
pickleshare               0.7.5
pillow                    10.2.0
pip                       22.3.1
platformdirs              4.1.0
pluggy                    1.0.0
prometheus-client         0.19.0
prompt-toolkit            3.0.43
protobuf                  3.20.0
psutil                    5.9.8
ptyprocess                0.7.0
pycocotools               2.0.7
pycosat                   0.6.4
pycparser                 2.21
pycryptodome              3.20.0
pydantic                  2.5.3
pydantic_core             2.14.6
Pygments                  2.17.2
pyOpenSSL                 22.0.0
pyparsing                 3.1.1
PySocks                   1.7.1
python-dateutil           2.8.2
python-json-logger        2.0.7
python-miio               0.6.0.dev0
pytz                      2023.3.post1
PyYAML                    6.0.1
pyzmq                     25.1.2
qudida                    0.0.4
referencing               0.32.1
requests                  2.31.0
rfc3339-validator         0.1.4
rfc3986-validator         0.1.1
rpds-py                   0.17.1
ruamel.yaml               0.17.21
ruamel.yaml.clib          0.2.6
schedule_search           0.0.1
scikit-image              0.22.0
scikit-learn              1.4.0
scikit-video              1.1.11
scipy                     1.12.0
Send2Trash                1.8.2
setuptools                65.6.3
show_kernel_debug_data    0.1.0
six                       1.16.0
sniffio                   1.3.0
soupsieve                 2.5
sympy                     1.12
te                        0.4.0
terminado                 0.18.0
threadpoolctl             3.2.0
tifffile                  2023.12.9
tinycss2                  1.2.1
tomli                     2.0.1
toolz                     0.12.0
torch                     2.1.0
torch-npu                 2.1.0.post2+git64bdab5
torchaudio                2.1.0
torchvision               0.16.0
tornado                   6.4
tqdm                      4.64.1
traitlets                 5.14.1
types-python-dateutil     2.8.19.20240106
typing_extensions         4.9.0
tzlocal                   5.2
uri-template              1.3.0
urllib3                   1.26.14
wcwidth                   0.2.13
webcolors                 1.13
webencodings              0.5.1
websocket-client          1.7.0
wheel                     0.37.1
widgetsnbextension        4.0.9
zeroconf                  0.131.0
zipp                      3.17.0
zstandard                 0.18.0
```

## 安装 CANN 计算框架

如果可以，建议你创建一个新的用户 `HwHiAiUser` 来运行相关的昇腾计算模型：

```bash
groupadd -g 1000 HwHiAiUser
useradd -g HwHiAiUser -u 1000 -d /home/HwHiAiUser -m HwHiAiUser -s /bin/bash
```

后续的内容将在此账户下说明，你也可以使用 `root` 用户来执行下述的安装，在这种情况下，请自行替换相关的路径。

你需要通过下述命令安装必需的第三方依赖：

```bash
apt-get install -y gcc g++ make cmake zlib1g zlib1g-dev openssl libsqlite3-dev libssl-dev libffi-dev unzip pciutils net-tools libblas-dev gfortran libblas3
```

你可以[点此](https://www.hiascend.com/zh/developer/download/community/result?module=cann)下载 CANN-toolkit 的**最新版本**。

如果你使用的是 [WSL](https://learn.microsoft.com/zh-cn/windows/wsl/install)，则你可以使用下述命令将下载的 CANN-toolkit `run` 文件上传至开发板：

```bash
scp ./Downloads/{文件名称} HwHiAiUser@{开发板的 IP 地址}:Downloads
```

你可以使用 WSL 来 SSH 远程连接到开发板：

```bash
ssh HwHiAiUser@{开发板的 IP 地址}
```

此时你应该可以在 `Downloads` 文件夹中看到 CANN 的 `run` 文件，你需要运行下面的命令来增加权限和进行完整性检查：

```bash
chmod +x {文件名称}.run
./{文件名称}.run --check
```

然后执行下述命令安装：

```bash
./{文件名称}.run --install
```

由于安装用户为 `HwHiAiUser`，则上述命令将会把 CANN-toolkit 安装到下述路径：

```bash
/home/HwHiAiUser/Ascend/ascend-toolkit/
```

如果你想确保安装路径无误，则你可以指定上述的安装命令为：

```bash
./{文件名称}.run --install-path=/home/HwHiAiUser/Ascend/
```

如果你是在 root 用户下安装的，请参阅[安装 CANN 套件包官方文档](#相关文档)。

然后你需要将相关的路径全部加入环境变量中，请运行下述命令：

```bash
vim ~/.bashrc
```

在打开的文件末尾加入下述内容：

```bash
# config CANN platform
. /home/HwHiAiUser/Ascend/ascend-toolkit/set_env.sh
```

然后键入 `source ~/.bashrc` 以使环境变量立即生效。

## 添加算子（验证 CANN 安装）

你需要使用 `git` 工具拉取存储库 `https://gitee.com/ascend/samples/tree/master/operator`，或者你也可以通过 WSL 下载压缩包并上传至开发板，则你可以通过下述命令解压缩：

```bash
cd /home/HwHiAiUser/ && mkdir ./custom
cd ./custom
mkdir operator && unzip operator.zip -d ./operator/*
```

假定你存放的位置是 `~/custom/operator/`，则运行下述命令：

```bash
cd ./AddCustomSample/FrameworkLaunch/AddCustom
bash build.sh

cd build_out
./custom_opp_ubuntu_aarch64.run

cd ../../AclNNInvocation
bash run.sh
```

你应该可以看到 `test pass` 字样。

请注意，这个存储库的作用是使用预置的算子或添加自定义算子，这可能会经常用到，因此你应该记住该仓库的位置。

## 安装 ACLLite 库

为了运行一些常见的模型，例如 `ResNet50` 和 `Yolo`，你需要安装 `ACLLite` 库。

你可以使用 git 工具拉取存储库 `https://gitee.com/ascend/ACLLite`，或者使用 WSL 下载压缩包后传输到开发板上。

然后，你需要添加环境变量，请按照下述命令重新打开环境变量文件：

```bash
vim ~/.bashrc
```

并在末尾处加入下述内容

```bash
# config ACLLite
export DDK_PATH=/home/HwHiAiUser/Ascend/ascend-toolkit/latest
export NPU_HOST_LIB=$DDK_PATH/runtime/lib64/stub
```

如果你的 CANN-toolkit 没有安装在此路径下，请自行修改。

键入 `source ~/.bashrc` 以使环境变量立即生效。

现在，你需要切换到 `ACLLite` 的存储路径下：

```bash
cd ~/repo/ACLLite
bash build_so.sh
```

运行过程中可能需要输入管理员密码，等待完成。

## 尝试运行模型

请拉取下述位置的仓库：

```
https://gitee.com/ascend/EdgeAndRobotics/tree/master/Samples
```

如果你的开发板内存只有 8GB 或更小，请将下述环境变量加入到 `.bashrc` 文件中：

```bash
# atc transfer setting (solving OOM)
export TE_PARALLEL_COMPILER=1
export MAX_COMPILE_CORE_NUMBER=1
```

然后，你可以按照仓库中任一模型的 `readme` 文件中的指示运行。

## 相关文档

  1. [安装 CANN 套件包](https://www.hiascend.com/document/detail/zh/CANNCommunityEdition/80RC3alpha001/softwareinst/instg/instg_0038.html)；
  2. [使用 ATC 工具进行模型转换](https://www.hiascend.com/document/detail/zh/CANNCommunityEdition/80RC1alpha003/devaids/auxiliarydevtool/atlasatc_16_0003.html)；