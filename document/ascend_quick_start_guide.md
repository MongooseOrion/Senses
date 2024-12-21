# 华为昇腾样例快速入门指南

本文档将通过指导运行几个样例模型，帮助你快速入门华为昇腾的开发流程。如果你需要从源代码构建华为昇腾开发环境，请[点此](https://github.com/MongooseOrion/Senses/blob/main/document/ascend_310B4_cann.md)访问。

## 连接和确认

### 基于以太网的有线连接方式

你将使用有线连接的方式，在这种情况下，请将主机对应网口的 IP 设置为如下内容：

```
IP 地址：192.168.0.35
子网掩码：255.255.255.0
网关：192.168.0.1
DNS：1.1.1.1
```

然后请打开 [Windows 终端](https://apps.microsoft.com/detail/9n0dx20hk701?hl=zh-cn&gl=CN)并尝试键入：

```bat
ping 192.168.0.19
```

如果无误，应该打印形如下述的内容：

```bat
正在 Ping 192.168.0.9 具有 32 字节的数据:
来自 192.168.0.9 的回复: 字节=32 时间=8ms TTL=64
来自 192.168.0.9 的回复: 字节=32 时间=12ms TTL=64
来自 192.168.0.9 的回复: 字节=32 时间=15ms TTL=64
来自 192.168.0.9 的回复: 字节=32 时间=3ms TTL=64

192.168.0.9 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 3ms，最长 = 15ms，平均 = 9ms
```

现在说明主机与开发板能够连通。

  * 如果你的主机运行 Windows10 build 19045.5011 或更新版本，则你可以直接键入下述命令以 ssh 远程连接开发板：

      ```bash
      ssh HwHiAiUser@192.168.0.19
      ```

      **在使用前，请确认主机与开发板连接在同一局域网下**。

  * 如果你的电脑已安装 [WSL](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/WSL.md#%E9%85%8D%E7%BD%AE-wsl2) 或者运行 Ubuntu 较新版本，则你可以使用基于 X11 转发的 ssh 远程连接，这将可以查看开发板的本地图片或运行 GUI 应用程序。

      ```bash
      ssh -X HwHiAiUser@192.168.0.19
      ```

如果无误，将要求你输入密码：

```bash
HwHiAiUser@192.168.0.9's password: Mind@123
```

Linux 在输入密码时不可见，因此你只要将密码按顺序键入并回车即可，如果无误，将显示：

```bash
  ___                                    ____   _
 / _ \  _ __  __ _  _ __    __ _   ___  |  _ \ (_)
| | | || '__|/ _` || '_ \  / _` | / _ \ | |_) || |
| |_| || |  | (_| || | | || (_| ||  __/ |  __/ | |
 \___/ |_|   \__,_||_| |_| \__, | \___| |_|    |_|
                           |___/
Welcome to Orange Pi Ai Pro
This system is based on Ubuntu 22.04.3 LTS (GNU/Linux 5.10.0+ aarch64)

This system is only applicable to individual developers and cannot be used for commercial purposes.

By using this system, you have agreed to the Huawei Software License Agreement.
Please refer to the agreement for details on https://www.hiascend.com/software/protocol

(base) HwHiAiUser@orangepiaipro:~$
```

### 基于 UART 的有线连接方式

如果你发现直接按照上述的方法不能修改主机 IP 或者不能 `ping` 通开发板，则可以考虑通过串口临时修改开发板 IP 地址，然后使用 ssh 连接。首先，请确保已下载 [MobaXterm](https://mobaxterm.mobatek.net/download.html)，然后使用串口连接电脑。在 MobaXterm 中点击 `Session` 新建一个 `Serial` 事务，请将端口号设置为对应名称，并将波特率设置为 `115200`，然后开机或重启开发板，你将可以看到在窗口内打印出自检日志。

此时你可以直接通过串口来输入指令到开发板上，如果你没有传输文件的需求，则你可以跳过本节的后续内容。否则，你仍然需要 ssh 连接，在这种情况下，UART 只是起到一个修改板上 IP 地址的作用。

请确保此时已将串口线、网线连接至主机，然后在主机上打开 Windows 终端，并输入指令 `ipconfig`，你应该可以看到多个以太网有线或无线适配器，请找到用于连接开发板的有线网口的网卡，它的名称应该形如 `以太网适配器 以太网 3:`。然后请记录下这个适配器的 IPv4 地址和网关，回到 `MobaXterm` 窗口中，键入：

```bash
sudo ifconfig eth0 {IP 地址} gateway {网关地址}
```

其中设置的 IP 地址应该与前述的 IP 地址前三个字节相同，最后一个字节可任意设置但不可以与原 IP 相同；网关地址应该与原网关一致。

在完成操作后，你可以继续重新尝试能否在主机 `ping` 通开发板，并继续[基于以太网的有线连接方式](#基于以太网的有线连接方式)的后续内容。

## 算子构建

### AclNN 调用

按顺序键入下述命令，并观察实验结果：

```bash
cd /home/HwHiAiUser/repo/operator/AddCustomSample/FrameworkLaunch/AddCustom
bash build.sh
```

```bash
cd build_out
./custom_opp_ubuntu_aarch64.run
```

```bash
cd /home/HwHiAiUser/repo/operator/AddCustomSample/FrameworkLaunch/AclNNInvocation
bash run.sh
```

如果无误，最后的日志输出应该是：

```bash
INFO: make success!
INFO: execute op!
[INFO]  Set device[0] success
[INFO]  Get RunMode[0] success
[INFO]  Init resource success
[INFO]  Set input success
[INFO]  Copy input[0] success
[INFO]  Copy input[1] success
[INFO]  Create stream success
[INFO]  Execute aclnnAddCustomGetWorkspaceSize success, workspace size 0
[INFO]  Execute aclnnAddCustom success
[INFO]  Synchronize stream success
[INFO]  Copy output[0] success
[INFO]  Write output success
[INFO]  Run op success
[INFO]  Reset Device success
[INFO]  Destroy resource success
INFO: acl executable run success!
error ratio: 0.0000, tolrence: 0.0010
test pass
```

### Kernel 直调工程

按顺序键入下述命令，然后观察实验结果：

```bash
cd /home/HwHiAiUser/repo/operator/AddCustomSample/KernelLaunch/
cp -r AddKernelInvocationNeo/ test
cd test
bash run.sh -r cpu -v Ascend310B4
```

如果无误，将输出：

```bash
[SUCCESS][CORE_0][pid 94783] exit success!
[SUCCESS][CORE_1][pid 94784] exit success!
[SUCCESS][CORE_2][pid 94785] exit success!
[SUCCESS][CORE_3][pid 94786] exit success!
[SUCCESS][CORE_4][pid 94787] exit success!
[SUCCESS][CORE_5][pid 94788] exit success!
[SUCCESS][CORE_6][pid 94789] exit success!
[SUCCESS][CORE_7][pid 94790] exit success!
cf92b9644dd972ded46f49bdb896cea1  output/golden.bin
cf92b9644dd972ded46f49bdb896cea1  output/output_z.bin
error ratio: 0.0000, tolrence: 0.0010
test pass
```

---

现在尝试自定义算子，此处以自定义一个 `sinh` 算子为例，请键入下述命令：

```bash
cd /home/HwHiAiUser/repo/operator/AddCustomSample/KernelLaunch/test/scripts
vim gen_data.py
```

在打开文件后键入 `i` 进入编辑模式，然后注释和增加下述内容：

```python
#input_x = np.random.uniform(1, 100, [8, 2048]).astype(np.float16)
#golden = (input_x + input_y).astype(np.float16)
input_x = np.random.uniform(1,10,[8,2048]).astype(np.float16)
golden = np.sinh(input_x).astype(np.float16)
```

修改完成后按顺序键入 `esc`、`:w`、`:q`，完成修改。

然后请键入下述命令：

```bash
cd ../
vim add_custom.cpp
```

在打开文件后找到 `Compute()` 函数，然后注释和添加下述语句：

```c
//AscendC::Add(zLocal, xLocal, yLocal, TILE_LENGTH);
Exp(xLocal, xLocal, TILE_LENGTH);
Reciprocal(zLocal, xLocal, TILE_LENGTH);
Sub(zLocal, xLocal, zLocal, TILE_LENGTH);
half scalar = 0.5;
Muls(zLocal, zLocal, scalar, TILE_LENGTH);
```

**请读者自行思考增加的语句的数学原理（为什么可以实现 `sinh()` 功能？）。**

保存并退出 vim 后，运行下述命令执行算子编译：

```bash
bash run.sh -r cpu -v Ascend310B4
```

如果无误，将打印形如下述文本的日志：

```bash
[SUCCESS][CORE_0][pid 105073] exit success!
[SUCCESS][CORE_1][pid 105074] exit success!
[SUCCESS][CORE_2][pid 105075] exit success!
[SUCCESS][CORE_3][pid 105076] exit success!
[SUCCESS][CORE_4][pid 105077] exit success!
[SUCCESS][CORE_5][pid 105078] exit success!
[SUCCESS][CORE_6][pid 105079] exit success!
[SUCCESS][CORE_7][pid 105080] exit success!
dad7f4a4e5d06b0324a4d92e3b3fccf8  output/golden.bin
07d1aaafce266e0779d88c793935f0bb  output/output_z.bin
error ratio: 0.0000, tolrence: 0.0010
test pass
```

在路径 `./output` 下的两个文件即为使用 python 计算的期望值和自定义算子计算值。你可以使用 python 在终端中读取并打印两个文件的值，进行比较。请键入：

```bash
python
```

然后按顺序键入下述命令：

```python
import numpy as np
golden = np.fromfile('output/golden.bin', dtype=np.float16)
output_z = np.fromfile('output/output_z.bin', dtype=np.float16)
print(f"Golden file content:{golden}")
print(f"Output_z file content:{output_z}")
```

若要退出 `python` 请键入：

```python
exit()
```

## 运行 Resnet50 图片分类样例

请键入下述命令以进入相关仓库：

```bash
cd /home/HwHiAiUser/repo/EdgeAndRobotics/Samples/ResnetPicture/
```

你可以键入 `ls` 以查看这个存储库的文件夹结构，也可以键入 `vim readme.md` 来了解该存储库的文本指示。在该存储库中，我已经预置了相关图片和 `ATC` 模型，若要了解什么是 `ATC`，请参阅[使用 ATC 工具进行模型转换](https://www.hiascend.com/document/detail/zh/CANNCommunityEdition/80RC1alpha003/devaids/auxiliarydevtool/atlasatc_16_0003.html)。因此，你将可以直接执行推理，键入：

```bash
cd scripts
bash sample_run.sh
```

执行成功后，在屏幕上的关键提示信息示例如下，提示信息中的 `top1-5` 表示图片置信度的前 5 种类别、index 表示类别标识、value 表示该分类的最大置信度，class 表示所属类别。

```bash
[INFO] The sample starts to run
[INFO] InitACLResource success.
[INFO] Init dvpp resource success.
[INFO] Load model ../model/resnet50.om success
[INFO] top 1: index[162] value[0.905956] class[beagle]
[INFO] top 2: index[161] value[0.092549] class[bassetbasset hound]
[INFO] top 3: index[166] value[0.000758] class[Walker houndWalker foxhound]
[INFO] top 4: index[167] value[0.000559] class[English foxhound]
[INFO] top 5: index[163] value[0.000076] class[bloodhound sleuthhound]
[INFO] Unload model ../model/resnet50.om success
[INFO] The program runs successfully
```

如果你想要查看用于推理的图片，你可以键入下述命令检查 X11 转发是否正常：

```bash
echo $DISPLAY
```

如果显示 `localhost:XX.X`，则你可以通过主机直接查看，请键入：

```bash
display /home/HwHiAiUser/repo/EdgeAndRobotics/Samples/ResnetPicture/data/dog1_1024_683.jpg
```

否则，你可能无法查看图片，在这种情况下你可以通过 `scp` 命令将其传输到主机上（如果你需要查看图片）。图片内是一个比格犬，你可以发现置信度最高的标签就是它。

## 运行手写体识别样例

模型文件和用于推理的文件均已存储在相关位置，请直接运行下述命令：

```bash
cd /home/HwHiAiUser/repo/EdgeAndRobotics/Samples/HandWritingTrainAndInfer/omInfer/scripts
bash sample_run.sh
```

执行成功后，你可以在屏幕上的看到关于这张图片的识别结果。若要在主机上查看用于推理的图片，请参照前述内容，这是一张手写 "8" 的图片。

## 运行自定义的手写体识别网络

通过 Tensorflow2，我自行构建了一个多层感知机的手写体识别神经网络，若要了解相关网络的结构，请[点此](https://github.com/MongooseOrion/deep_learn/blob/master/tensorflow_learn/mnist_test.py)了解；若要了解标准 Tensorflow2 模型如何转换为华为昇腾模型，请[点此](https://github.com/MongooseOrion/Senses/blob/main/document/ascend_310B4_cann.md#%E8%BF%90%E8%A1%8C%E8%87%AA%E5%AE%9A%E4%B9%89%E7%9A%84-tensorflow-%E6%A8%A1%E5%9E%8B)了解。

在此处，模型已经转换成功并已存放至相关位置，我们着重来介绍如何快速运行模型执行推理任务。请键入：

```bash
cd /home/HwHiAiUser/repo/tools/msame/out
./main --model "/home/HwHiAiUser/repo/mnist_recog/model/mnist_pic_classify_mod.om" --input "/home/HwHiAiUser/repo/mnist_recog/data/8.bin" --output "./out/" --outfmt TXT --loop 1
```

然后你可以在路径 `/home/HwHiAiUser/repo/tools/msame/out/out` 下看到一个新生成的文件夹，其中的 TXT 将指示 10 个输出结果各自的可能性。

