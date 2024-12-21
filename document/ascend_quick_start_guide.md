# ��Ϊ�N��������������ָ��

���ĵ���ͨ��ָ�����м�������ģ�ͣ�������������Ż�Ϊ�N�ڵĿ������̡��������Ҫ��Դ���빹����Ϊ�N�ڿ�����������[���](https://github.com/MongooseOrion/Senses/blob/main/document/ascend_310B4_cann.md)���ʡ�

## ���Ӻ�ȷ��

### ������̫�����������ӷ�ʽ

�㽫ʹ���������ӵķ�ʽ������������£��뽫������Ӧ���ڵ� IP ����Ϊ�������ݣ�

```
IP ��ַ��192.168.0.35
�������룺255.255.255.0
���أ�192.168.0.1
DNS��1.1.1.1
```

Ȼ����� [Windows �ն�](https://apps.microsoft.com/detail/9n0dx20hk701?hl=zh-cn&gl=CN)�����Լ��룺

```bat
ping 192.168.0.19
```

�������Ӧ�ô�ӡ�������������ݣ�

```bat
���� Ping 192.168.0.9 ���� 32 �ֽڵ�����:
���� 192.168.0.9 �Ļظ�: �ֽ�=32 ʱ��=8ms TTL=64
���� 192.168.0.9 �Ļظ�: �ֽ�=32 ʱ��=12ms TTL=64
���� 192.168.0.9 �Ļظ�: �ֽ�=32 ʱ��=15ms TTL=64
���� 192.168.0.9 �Ļظ�: �ֽ�=32 ʱ��=3ms TTL=64

192.168.0.9 �� Ping ͳ����Ϣ:
    ���ݰ�: �ѷ��� = 4���ѽ��� = 4����ʧ = 0 (0% ��ʧ)��
�����г̵Ĺ���ʱ��(�Ժ���Ϊ��λ):
    ��� = 3ms��� = 15ms��ƽ�� = 9ms
```

����˵�������뿪�����ܹ���ͨ��

  * �������������� Windows10 build 19045.5011 ����°汾���������ֱ�Ӽ������������� ssh Զ�����ӿ����壺

      ```bash
      ssh HwHiAiUser@192.168.0.19
      ```

      **��ʹ��ǰ����ȷ�������뿪����������ͬһ��������**��

  * �����ĵ����Ѱ�װ [WSL](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/WSL.md#%E9%85%8D%E7%BD%AE-wsl2) �������� Ubuntu ���°汾���������ʹ�û��� X11 ת���� ssh Զ�����ӣ��⽫���Բ鿴������ı���ͼƬ������ GUI Ӧ�ó���

      ```bash
      ssh -X HwHiAiUser@192.168.0.19
      ```

������󣬽�Ҫ�����������룺

```bash
HwHiAiUser@192.168.0.9's password: Mind@123
```

Linux ����������ʱ���ɼ��������ֻҪ�����밴˳����벢�س����ɣ�������󣬽���ʾ��

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

### ���� UART ���������ӷ�ʽ

����㷢��ֱ�Ӱ��������ķ��������޸����� IP ���߲��� `ping` ͨ�����壬����Կ���ͨ��������ʱ�޸Ŀ����� IP ��ַ��Ȼ��ʹ�� ssh ���ӡ����ȣ���ȷ�������� [MobaXterm](https://mobaxterm.mobatek.net/download.html)��Ȼ��ʹ�ô������ӵ��ԡ��� MobaXterm �е�� `Session` �½�һ�� `Serial` �����뽫�˿ں�����Ϊ��Ӧ���ƣ���������������Ϊ `115200`��Ȼ�󿪻������������壬�㽫���Կ����ڴ����ڴ�ӡ���Լ���־��

��ʱ�����ֱ��ͨ������������ָ��������ϣ������û�д����ļ���������������������ڵĺ������ݡ���������Ȼ��Ҫ ssh ���ӣ�����������£�UART ֻ����һ���޸İ��� IP ��ַ�����á�

��ȷ����ʱ�ѽ������ߡ�����������������Ȼ���������ϴ� Windows �նˣ�������ָ�� `ipconfig`����Ӧ�ÿ��Կ��������̫�����߻����������������ҵ��������ӿ�������������ڵ���������������Ӧ������ `��̫�������� ��̫�� 3:`��Ȼ�����¼������������� IPv4 ��ַ�����أ��ص� `MobaXterm` �����У����룺

```bash
sudo ifconfig eth0 {IP ��ַ} gateway {���ص�ַ}
```

�������õ� IP ��ַӦ����ǰ���� IP ��ַǰ�����ֽ���ͬ�����һ���ֽڿ��������õ���������ԭ IP ��ͬ�����ص�ַӦ����ԭ����һ�¡�

����ɲ���������Լ������³����ܷ������� `ping` ͨ�����壬������[������̫�����������ӷ�ʽ](#������̫�����������ӷ�ʽ)�ĺ������ݡ�

## ���ӹ���

### AclNN ����

��˳���������������۲�ʵ������

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

�������������־���Ӧ���ǣ�

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

### Kernel ֱ������

��˳������������Ȼ��۲�ʵ������

```bash
cd /home/HwHiAiUser/repo/operator/AddCustomSample/KernelLaunch/
cp -r AddKernelInvocationNeo/ test
cd test
bash run.sh -r cpu -v Ascend310B4
```

������󣬽������

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

���ڳ����Զ������ӣ��˴����Զ���һ�� `sinh` ����Ϊ����������������

```bash
cd /home/HwHiAiUser/repo/operator/AddCustomSample/KernelLaunch/test/scripts
vim gen_data.py
```

�ڴ��ļ������ `i` ����༭ģʽ��Ȼ��ע�ͺ������������ݣ�

```python
#input_x = np.random.uniform(1, 100, [8, 2048]).astype(np.float16)
#golden = (input_x + input_y).astype(np.float16)
input_x = np.random.uniform(1,10,[8,2048]).astype(np.float16)
golden = np.sinh(input_x).astype(np.float16)
```

�޸���ɺ�˳����� `esc`��`:w`��`:q`������޸ġ�

Ȼ��������������

```bash
cd ../
vim add_custom.cpp
```

�ڴ��ļ����ҵ� `Compute()` ������Ȼ��ע�ͺ����������䣺

```c
//AscendC::Add(zLocal, xLocal, yLocal, TILE_LENGTH);
Exp(xLocal, xLocal, TILE_LENGTH);
Reciprocal(zLocal, xLocal, TILE_LENGTH);
Sub(zLocal, xLocal, zLocal, TILE_LENGTH);
half scalar = 0.5;
Muls(zLocal, zLocal, scalar, TILE_LENGTH);
```

**���������˼�����ӵ�������ѧԭ��Ϊʲô����ʵ�� `sinh()` ���ܣ�����**

���沢�˳� vim ��������������ִ�����ӱ��룺

```bash
bash run.sh -r cpu -v Ascend310B4
```

������󣬽���ӡ���������ı�����־��

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

��·�� `./output` �µ������ļ���Ϊʹ�� python ���������ֵ���Զ������Ӽ���ֵ�������ʹ�� python ���ն��ж�ȡ����ӡ�����ļ���ֵ�����бȽϡ�����룺

```bash
python
```

Ȼ��˳������������

```python
import numpy as np
golden = np.fromfile('output/golden.bin', dtype=np.float16)
output_z = np.fromfile('output/output_z.bin', dtype=np.float16)
print(f"Golden file content:{golden}")
print(f"Output_z file content:{output_z}")
```

��Ҫ�˳� `python` ����룺

```python
exit()
```

## ���� Resnet50 ͼƬ��������

��������������Խ�����زֿ⣺

```bash
cd /home/HwHiAiUser/repo/EdgeAndRobotics/Samples/ResnetPicture/
```

����Լ��� `ls` �Բ鿴����洢����ļ��нṹ��Ҳ���Լ��� `vim readme.md` ���˽�ô洢����ı�ָʾ���ڸô洢���У����Ѿ�Ԥ�������ͼƬ�� `ATC` ģ�ͣ���Ҫ�˽�ʲô�� `ATC`�������[ʹ�� ATC ���߽���ģ��ת��](https://www.hiascend.com/document/detail/zh/CANNCommunityEdition/80RC1alpha003/devaids/auxiliarydevtool/atlasatc_16_0003.html)����ˣ��㽫����ֱ��ִ���������룺

```bash
cd scripts
bash sample_run.sh
```

ִ�гɹ�������Ļ�ϵĹؼ���ʾ��Ϣʾ�����£���ʾ��Ϣ�е� `top1-5` ��ʾͼƬ���Ŷȵ�ǰ 5 �����index ��ʾ����ʶ��value ��ʾ�÷����������Ŷȣ�class ��ʾ�������

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

�������Ҫ�鿴���������ͼƬ������Լ������������� X11 ת���Ƿ�������

```bash
echo $DISPLAY
```

�����ʾ `localhost:XX.X`���������ͨ������ֱ�Ӳ鿴������룺

```bash
display /home/HwHiAiUser/repo/EdgeAndRobotics/Samples/ResnetPicture/data/dog1_1024_683.jpg
```

����������޷��鿴ͼƬ������������������ͨ�� `scp` ����䴫�䵽�����ϣ��������Ҫ�鿴ͼƬ����ͼƬ����һ���ȸ�Ȯ������Է������Ŷ���ߵı�ǩ��������

## ������д��ʶ������

ģ���ļ�������������ļ����Ѵ洢�����λ�ã���ֱ�������������

```bash
cd /home/HwHiAiUser/repo/EdgeAndRobotics/Samples/HandWritingTrainAndInfer/omInfer/scripts
bash sample_run.sh
```

ִ�гɹ������������Ļ�ϵĿ�����������ͼƬ��ʶ��������Ҫ�������ϲ鿴���������ͼƬ�������ǰ�����ݣ�����һ����д "8" ��ͼƬ��

## �����Զ������д��ʶ������

ͨ�� Tensorflow2�������й�����һ������֪������д��ʶ�������磬��Ҫ�˽��������Ľṹ����[���](https://github.com/MongooseOrion/deep_learn/blob/master/tensorflow_learn/mnist_test.py)�˽⣻��Ҫ�˽��׼ Tensorflow2 ģ�����ת��Ϊ��Ϊ�N��ģ�ͣ���[���](https://github.com/MongooseOrion/Senses/blob/main/document/ascend_310B4_cann.md#%E8%BF%90%E8%A1%8C%E8%87%AA%E5%AE%9A%E4%B9%89%E7%9A%84-tensorflow-%E6%A8%A1%E5%9E%8B)�˽⡣

�ڴ˴���ģ���Ѿ�ת���ɹ����Ѵ�������λ�ã�����������������ο�������ģ��ִ��������������룺

```bash
cd /home/HwHiAiUser/repo/tools/msame/out
./main --model "/home/HwHiAiUser/repo/mnist_recog/model/mnist_pic_classify_mod.om" --input "/home/HwHiAiUser/repo/mnist_recog/data/8.bin" --output "./out/" --outfmt TXT --loop 1
```

Ȼ���������·�� `/home/HwHiAiUser/repo/tools/msame/out/out` �¿���һ�������ɵ��ļ��У����е� TXT ��ָʾ 10 �����������ԵĿ����ԡ�

