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
# �ڻ��� ARM64 �Ļ�Ϊ�N�ڿ������ϲ��� CANN ����������ģ��

���ĵ����ڵ�Ӳ��ƽ̨����Ϊ��

  * �����壺Orange Pi AI Pro
  * �ڴ棺8GB
  * �N�ڼ���ƽ̨�ͺţ�Ascend310B4
  * Ubuntu ϵͳ�汾��Ubuntu 22.04.3 LTS jammy
  * �������ܹ���aarch64 with 4 �� 4 �߳�

����������Ѿ��ڿ���������ȷ��װ�������� Linux ϵͳ�����û�У������з�����ؿ����������̵Ĺٷ���վ��

�ڿ�ʼ֮ǰ����������� `apt` �������Ϣ��

```bash
sudo apt-get update
```

## ����������˵��

Python �� cpp �ı��뻷���汾��

```bash
Python 3.9.2
cmake version 3.29.8
g++ (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
```

����Ҫ�������������汾����һ�¡�

Python ���汾��

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

## ��װ CANN ������

������ԣ������㴴��һ���µ��û� `HwHiAiUser` ��������صĕN�ڼ���ģ�ͣ�

```bash
groupadd -g 1000 HwHiAiUser
useradd -g HwHiAiUser -u 1000 -d /home/HwHiAiUser -m HwHiAiUser -s /bin/bash
```

���������ݽ��ڴ��˻���˵������Ҳ����ʹ�� `root` �û���ִ�������İ�װ������������£��������滻��ص�·����

����Ҫͨ���������װ����ĵ�����������

```bash
apt-get install -y gcc g++ make cmake zlib1g zlib1g-dev openssl libsqlite3-dev libssl-dev libffi-dev unzip pciutils net-tools libblas-dev gfortran libblas3
```

�����[���](https://www.hiascend.com/zh/developer/download/community/result?module=cann)���� CANN-toolkit ��**���°汾**��

�����ʹ�õ��� [WSL](https://learn.microsoft.com/zh-cn/windows/wsl/install)���������ʹ������������ص� CANN-toolkit `run` �ļ��ϴ��������壺

```bash
scp ./Downloads/{�ļ�����} HwHiAiUser@{������� IP ��ַ}:Downloads
```

�����ʹ�� WSL �� SSH Զ�����ӵ������壺

```bash
ssh HwHiAiUser@{������� IP ��ַ}
```

��ʱ��Ӧ�ÿ����� `Downloads` �ļ����п��� CANN �� `run` �ļ�������Ҫ�������������������Ȩ�޺ͽ��������Լ�飺

```bash
chmod +x {�ļ�����}.run
./{�ļ�����}.run --check
```

Ȼ��ִ���������װ��

```bash
./{�ļ�����}.run --install
```

���ڰ�װ�û�Ϊ `HwHiAiUser`�������������� CANN-toolkit ��װ������·����

```bash
/home/HwHiAiUser/Ascend/ascend-toolkit/
```

�������ȷ����װ·�������������ָ�������İ�װ����Ϊ��

```bash
./{�ļ�����}.run --install-path=/home/HwHiAiUser/Ascend/
```

��������� root �û��°�װ�ģ������[��װ CANN �׼����ٷ��ĵ�](#����ĵ�)��

Ȼ������Ҫ����ص�·��ȫ�����뻷�������У��������������

```bash
vim ~/.bashrc
```

�ڴ򿪵��ļ�ĩβ�����������ݣ�

```bash
# config CANN platform
. /home/HwHiAiUser/Ascend/ascend-toolkit/set_env.sh
```

Ȼ����� `source ~/.bashrc` ��ʹ��������������Ч��

## ������ӣ���֤ CANN ��װ��

����Ҫʹ�� `git` ������ȡ�洢�� `https://gitee.com/ascend/samples/tree/master/operator`��������Ҳ����ͨ�� WSL ����ѹ�������ϴ��������壬�������ͨ�����������ѹ����

```bash
cd /home/HwHiAiUser/ && mkdir ./custom
cd ./custom
mkdir operator && unzip operator.zip -d ./operator/*
```

�ٶ����ŵ�λ���� `~/custom/operator/`���������������

```bash
cd ./AddCustomSample/FrameworkLaunch/AddCustom
bash build.sh

cd build_out
./custom_opp_ubuntu_aarch64.run

cd ../../AclNNInvocation
bash run.sh
```

��Ӧ�ÿ��Կ��� `test pass` ������

��ע�⣬����洢���������ʹ��Ԥ�õ����ӻ�����Զ������ӣ�����ܻᾭ���õ��������Ӧ�ü�ס�òֿ��λ�á�

## ��װ ACLLite ��

Ϊ������һЩ������ģ�ͣ����� `ResNet50` �� `Yolo`������Ҫ��װ `ACLLite` �⡣

�����ʹ�� git ������ȡ�洢�� `https://gitee.com/ascend/ACLLite`������ʹ�� WSL ����ѹ�������䵽�������ϡ�

Ȼ������Ҫ��ӻ����������밴�������������´򿪻��������ļ���

```bash
vim ~/.bashrc
```

����ĩβ��������������

```bash
# config ACLLite
export DDK_PATH=/home/HwHiAiUser/Ascend/ascend-toolkit/latest
export NPU_HOST_LIB=$DDK_PATH/runtime/lib64/stub
```

������ CANN-toolkit û�а�װ�ڴ�·���£��������޸ġ�

���� `source ~/.bashrc` ��ʹ��������������Ч��

���ڣ�����Ҫ�л��� `ACLLite` �Ĵ洢·���£�

```bash
cd ~/repo/ACLLite
bash build_so.sh
```

���й����п�����Ҫ�������Ա���룬�ȴ���ɡ�

## ��������ģ��

����ȡ����λ�õĲֿ⣺

```
https://gitee.com/ascend/EdgeAndRobotics/tree/master/Samples
```

�����Ŀ������ڴ�ֻ�� 8GB ���С���뽫���������������뵽 `.bashrc` �ļ��У�

```bash
# atc transfer setting (solving OOM)
export TE_PARALLEL_COMPILER=1
export MAX_COMPILE_CORE_NUMBER=1
```

Ȼ������԰��ղֿ�����һģ�͵� `readme` �ļ��е�ָʾ���С�

## ����ĵ�

  1. [��װ CANN �׼���](https://www.hiascend.com/document/detail/zh/CANNCommunityEdition/80RC3alpha001/softwareinst/instg/instg_0038.html)��
  2. [ʹ�� ATC ���߽���ģ��ת��](https://www.hiascend.com/document/detail/zh/CANNCommunityEdition/80RC1alpha003/devaids/auxiliarydevtool/atlasatc_16_0003.html)��