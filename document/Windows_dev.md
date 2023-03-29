# �� Windows ��ʵ������������
�� Windows10 �ĵ�һ����ʽ�汾 1507 �����Ѿ���ȥ�� 8 �ꡣ���ǵ� 2014 �꣬����ý�嶼�ڷ���ʡ������µ� Windows ����ϵͳ���Ǹ�ʱ�������� Surface Pro3������д c �� `Hello world` ����<br><br>
��ʵ�ϣ��� Windows11 ����ǰϦй¶ 22000 �汾�����������԰�װ��ͬ����ǰ�һ��� 2 ��ʱ������վ����� Windows8 ���µ� Windows10��Windows8.1 ʼ�ղ������Ҹ������**��ʼ�˵�**���ܣ����ò�˵ʱ����������Ȼ���ǻ�˵ Win8 ��**��ʼ**��ƺ�ǰ������Ȼ��UWP �� Fluent Design Ҳһֱ���������ҡ��ܿ�ϧ���ǣ������մ���� UWP ��ٵ�ʱ�ڡ�<br><br>
�ϻ�����˵����ӹ���ɵ��� Windows11 �����зǳ��걸�Ŀ�������������ȻҲ�зǳ��õļ����ԣ���ʵ�Ҳ���ϲ�������ʷ����������ʦ�����ҿ��Գ����� Linux ������ĳЩ���أ����Ҿ��� Windows ����ʤ�Σ���Ҳ���Ҿ���д����ĵ���Դ������

## ��ҳ����
  * ʹ�� Windows �������� Linux ���غ� Android Ӧ�ó���
  * �����Ϲ�ͬ�� FPGA ����������
  * �� Windows ���� TensorFlow-GPU �汾

## ʹ�� Windows �������� Linux ���غ� Android Ӧ�ó���
�ڱ��£����������ʹ�� [Windows �ն�](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)���� Python ����������[������ Linux �� Windows ��ϵͳ��WSL2��](https://learn.microsoft.com/zh-cn/windows/wsl/about)��

### �Ⱦ�����
  1. Windows11 ���ڲ��汾���� 22000.194 �����ϣ�
  2. ���� RAM ������ 8GB��

### ���� Python ����

�� Micorsoft store �п���ֱ�Ӱ�װ Python��������Զ��尲װ���������ĺô����� Visual Studio ����ֱ��ʶ�� Python ����������������ã������Է�����Ƴ���

Ҫ���� Python ֮ǰ����ȷ��Դ����򿪷����������� Python �汾��Python3.9 �ɵ��[�˴�](https://apps.microsoft.com/store/detail/python-39/9P7QFQMJRFP7?hl=en-us&gl=us)��װ��

���δ�Զ��尲װĿ¼��������� `C:\Users\ [username] \AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_qbz5n2kfra8p0\LocalCache\local-packages\Python39\Scripts` ·�����ҵ�ʹ�� `pip install` ���װ�ĵ�����ģ�顣

<br>�뽫��·������ `Path` ���������У��Ա�ֱ�Ӵ� Windows �ն��н��� Python ������

���������ɣ���Ӧ�ÿ������ն������� `python` ����� Python ������

### ���� WSL2

WSL2 ���� Hyper-V �������� Linux ϵͳ������ WSL1 �б���������Ҫ�Ƚ� WSL1 �� WSL2�������[�Ƚ� WSL �汾](https://learn.microsoft.com/zh-cn/windows/wsl/compare-versions)�� [WSL 2 ����������](https://learn.microsoft.com/zh-cn/windows/wsl/compare-versions#whats-new-in-wsl-2)��

���[�˴�](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R)�ɰ�װ WSL ���ߣ��ù��߿��Թ���ϵͳ�а�װ������ WSL �ַ��汾��

���� WSL �İ�װ���裬�����[ʹ�� WSL �� Windows �ϰ�װ Linux](https://learn.microsoft.com/zh-cn/windows/wsl/install)��

�� Microsoft store �а�װ�ض��� Linux ���а汾�󣬿���ͨ�����ն˼������
```
wsl
```
����
```
[���а�����]
```
���� Linux ������

<br>���� WSL û��ͼ�����滷�������� WSL2 �������� Linux ͼ�Σ�GUI���������������ʹ�������� Linux �ն˻����а�װӦ�ó���ľ��飬�� Windows �ն���ʹ��ָ�װ Linux Ӧ�ó���ʾ��Ӧ�ó���ɲ���[�� WSL2 ������ Linux GUI Ӧ��](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps)��

�������� Docker Զ������������ NVIDIA GPU ���٣������ [Microsoft Learn ����ĵ�](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gpu-compute)��

### ���������� Android �� Windows ��ϵͳ��WSA��

������� Microsoft store ������ Amazon appstore�����ز���װ�󣬿�ʼ�˵��н�������Ϊ `������ Android �� Windows ��ϵͳ����` ��Ӧ�ó��򡣴� `������Ա - ������Աģʽ`����ʱ��������� IP ��ַ������ʹ�� Android �����ţ�ADB���Լ���Ӧ�ó��򣬻� WSA ����Ϊ Android Studio Ĭ���������

WSA ����ֱ�����л��� ARM64 �� x86 ������ Android Ӧ�ó������¹��ܻ����ȫ֧�֣�
  * ���أ�����ȡ���ڱ���Ӳ���Ĵ���֧�֣�
  * ������
  * ����ͷ
  * ��˷�

���¹��ܲ���֧�֣�
  * ͼ�δ���������֧�� Vulkan ���棬�Ƽ� Intel �� Nvidia �ĺ�о�Կ��Ͷ����Կ���

�ɰ������� WSA ���� Android Ӧ�ó��򿪷���

## �����Ϲ�ͬ�� FPGA ����������

�Ϲ�ͬ�����ֳ��ɱ༭�߼������У�FPGA���������߰��� Pango Design Suite �� Pango Design Suite Lite��PDS�����ڴ��½ڽ��������ʹ�� PDS ���ߡ�

### �Ⱦ�����

  1. �Ѱ�װ Altera ModelSim Ӧ�ó���
  2. �߱��Ϲ� FPGA Ӳ������ƽ̨��

### ����ͱ���
��Ҫʹ�� ModelSim ����������ļ�����֤������Ҫ�� `Project - Project Settings - Simulation - Target Simulator` ��ѡ�� `ModelSim Simulator`��

����Խ� `Compiled Libarary Location` ������ Modelsim Ӧ�ó���װ��Ŀ¼�£��Ա� ModelSim �ɿ��ر��� PDS ��������Ͳ鿴��Ȼ������Ҫ���� `Simulator Executable Path` �� Modelsim ������ĸ��ļ���·���£������Ĭ�����ã���Ӧ���� `C:\altera\13.1\modelsim_ase\win32aloem`��

���������ȷ����Ӧ�ÿ����ڱ�д�����ļ���������Ϊ������ʱ�ܹ����� Modelsim �Զ��򿪲����в��η��档

### ��� IP �ļ�

�����Ԥ�õ� IP �ˣ�������� `Tools - IP Compiler` �л�ȡ�����ģ�飬����ʱ�ӷ�Ƶ�����߼������ǡ�

����ǵ����� IP �ˣ�������� `Design` ��������ӡ�

### ��ԭ��ͼ

ԭ��ͼ�ǰ��������Ա�Ӵ��뼶ת�Ƶ���·������Ҫ���ߣ�����Է���ؼ��ʹ��Ӳ���������ԣ�HDL����д�Ĵ������߼���ϵ�����˽��������������ӹ�ϵ��

��Ҫʹ��ԭ��ͼ���ܣ�����Ҫȷ��ͨ�����η���ͱ��롣��� `Tools - Schematic Viwer` ���ɲ鿴��

### �ۺ�

�ڴ˲����£���Ҫ����Ӳ���ܽ�Լ�����Ա� PDS ȷ�� Verilog �а����Ķ˿���Ӳ����Ӧ�������ֱ�ӱ�д�ܽ�Լ���ļ� `.fdc`�����ʽ���£�
```ruby
define_attribute {p:led[7]} {PAP_IO_DIRECTION} {OUTPUT}
define_attribute {p:led[7]} {PAP_IO_LOC} {F8}
define_attribute {p:led[7]} {PAP_IO_VCCIO} {3.3}
define_attribute {p:led[7]} {PAP_IO_STANDARD} {LVCMOS33}
define_attribute {p:led[7]} {PAP_IO_DRIVE} {8}
define_attribute {p:led[7]} {PAP_IO_NONE} {TRUE}
define_attribute {p:led[7]} {PAP_IO_SLEW} {SLOW}
```

����֮�⣬PDS Ҳ�ṩ�� GUI �Ĺܽ�Լ�����ܣ������ͨ����� `Tools - User Constraint Editer - Pre Synthesize UCE` �򿪸ù��ܡ���� `device` ѡ�Ȼ������߶����˵��е�� `I/O table` �Զ�ϵͳ���е����������ӿڽ���Լ������ѡ���Ӧ�Ĺܽű�ź�����Զ����ɹܽŵ�ѹ�����������ݡ���ɱ༭�󣬵�����水ť�����Զ����� `.fdc` �ļ���

**��ע�⣬��Լ��ǰ����Ҫȷ�������õ�оƬ������ţ�����ϸ���սӿڵĹܽű���Ƿ���ȷ��**

#### ��ʾ

��ע�⣬PDS ��������ƴ����е� `always` �������첽��λ����ʹ�õ���������磺
```ruby
always@(posedge clk or negedge rst) begin
    key_reg <= key;
end
```
������ʾ�������У������� `negedge rst` �첽��λģʽ������δָ������λ�źű仯ʱ���Ĵ��� `key_reg` �ı仯��������������գ��ڸ�λ�ź�����ʱ��ϵͳ��Ȼ�ڱ������С�Ӧ���޸�Ϊ��

```ruby
always@(posedge clk or negedge rst) begin
    if(!rst) key_reg <= 0;        // PDS �� rst Ϊ null ʱ��Ը��źű���
    else key_reg <= key;
end
```

### ���ֲ���

�ڴ˲����£���Ӧ�ô���ʱ��Լ�����⡣

#### ���Ե������ŵ�ʱ��Լ������

ĳЩʱ���ź�����һЩԭ��û�б����ŵ� FPGA ������ʱ��ר�������ϣ���ͻᵼ�´�������

��������Ϊ��
```
Place-0084: GLOBAL_CLOCK: the driver [port] fixed at [position] is unreasonable. Sub-optimal placement for a clock source and a clock buffer.
```

��������ǣ��� `Pre Synthesize UCE` ������ѡ�� `Attributes` ѡ�Ȼ��������������������磨Nets�����ƣ���ѡ�� `PAP_CLOCK_DEDICATED_ROUTE` ��ֵΪ `FALSE`��

### ������������

�����ɱ������ļ��󣬵�� `Tools - Configuration` ���豸�����ܡ�

������������������ȷ����Ӧ�ÿ����ڵ�� `File - Connect To Server` ���� `Device Properties` �����п�������豸��Ϣ��

�����İ��Ӳ�֧�� SPI Flash����ѡ�� `Boundary Scan` �����Ҳര�����Ҽ�ѡ�� `Add Pango Device` ����ӱ������ļ���Ȼ���㽫���� `Program Device`��

## �� Windows ���� TensorFlow-GPU �汾

### �Ⱦ�����

  1. Windows �汾��Windows10 1909 �����ϣ�
  2. Nvidia GPU �����Լ�������[֧�� Cuda �� GPU �ͺ�](https://developer.nvidia.com/cuda-gpus)��
  3. Cuda ֧���� cuDNN ֧������� [TensorFlow �������Եļ��ݰ汾](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)��
  4. ȷ�� Nvidia GPU �������������°汾�����豣֤��������ʼ��Ϊ���£��ɲ��� [NVIDIA Geforce Experience](https://www.nvidia.cn/geforce/geforce-experience/)��

��ע�⣬���� Tensorflow ֧����վ��������Ϣ��TensorFlow-GPU �汾 2.11 �Ѿ���֧��ԭ�� Windows �� GPU ���С��������Ҫ�� Windows �������� GPU �汾�� TensorFlow����ôֻ��ѡ�� TensorFlow-GPU �汾 2.10������������ Windows ʹ�� 2.11 ����߰汾�� TensorFlow-GPU���뿼�� WSL2 �����[�� Windows �����д�Դ���빹��](https://tensorflow.google.cn/install/source_windows?hl=zh-cn)��

### ��װ Cuda ������������� cuDNN ������

NVIDIA CUDA��Compute Unified Device Architecture����һ������ GPU ���м����ƽ�м���ƽ̨�ͱ��ģ�ͣ�ּ��Ϊ GPU �ṩһ��ͨ�õı�̽ӿںͱ��ģ�ͣ�ʹ�ÿ�����Ա����ͨ����д CUDA ���������� GPU ���в��м��㡣

���� Cuda ��������� cuDNN ʱ����Ӧ��ȷ����������汾��cuDNN �汾�� [TensorFlow �������Եļ��ݰ汾](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)���г��� TensorFlow �汾����ݡ�

Cuda �����������ص��[�˴�](https://developer.nvidia.com/cuda-toolkit-archive)��cuDNN �����ص��[�˴�](https://developer.nvidia.com/rdp/cudnn-archive)��

�ڰ�װ Cuda ����������ɺ󣬽� cuDNN �����ļ��п����� Cuda �İ�װĿ¼�£��滻�ļ��� `bin`��`include` �� `lib`��

��������������󣬽� Cuda �İ�װ�ļ����ļ�����ӵ� Windows ϵͳ�� `Path` ����������

<BR>���������ɣ��� [Windows �ն�](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)�����룺
```
nvcc -V
```
Ӧ����� Cuda ��������汾�š�

### ��װ Anaconda Ӧ�ó���

ʹ�� Anaconda Ӧ�ó��������� TensorFlow �����¼����ô���

  1. ����������ϵ��Anaconda Ӧ�ó�������Զ����� TensorFlow �������Ŀ�͹��ߣ�ȷ�� TensorFlow ��������ϵ��ȷ���󣬱��������������⵼�¹���ʧ�ܻ�����ʱ����
  2. ��ƽ̨֧�֣�Anaconda Ӧ�ó���֧�ֶ��ֲ���ϵͳ������ Windows��Linux �� MacOS�������ڲ�ͬƽ̨�Ϲ��������� TensorFlow Ӧ�ó���
  3. �������⻷����Anaconda Ӧ�ó���֧�ִ������⻷���������ڲ�ͬ�Ļ����й��������� TensorFlow Ӧ�ó��򣬱��ⲻͬ��Ŀ֮���������ͻ��
  4. �򻯹������̣�Anaconda Ӧ�ó����ṩ��һ�ּ򵥵ķ�ʽ�������͹��� TensorFlow Ӧ�ó����û�ֻ��Ҫִ��һЩ�򵥵�����Ϳ����Զ������Ͱ�װ TensorFlow�������˷������ֶ����úͰ�װ���̡�
  5. ��װ������͹��ߣ�Anaconda Ӧ�ó����ṩ��һ���㷺�Ŀ�ѧ�����͹��ߵļ��ϣ��û����Է���ذ�װ��ʹ����Щ��͹��ߣ��� NumPy��SciPy��Matplotlib �ȣ����Է���ؽ��п�ѧ��������ݷ�����

���[�˴�](https://www.anaconda.com/)�Է��� Anaconda ��վ��

#### ʹ�� `Anaconda Prompt` ���� TensorFlow ���⻷��

�� `Anaconda Prompt` Ӧ�ó�������������������Բ鿴��ǰ�������⻷����
```
conda env list
```

<br>���贴��һ���µ� TensorFlow �������������������
```
conda create -n tensorflow python=3.9
```
���У�`tensorflow` Ϊ�û�ָ�������⻷�����ơ�**��ע��**��������������ָ�������⻷��Ϊ TensorFlow ����������`python=3.9` ����ָ�������⻷��Ϊ Python3.9 �汾����ע�⣬�˴��� Python ֻ�ڴ����⻷����Ψһ��Ч��

### ���������⻷���в��� TensorFlow-GPU

#### ʹ�����߰�װ

�����⻷���а�װ TensorFlow-GPU �汾�������Ȳ���[���� Python �汾ָ�� whl ����ַ](https://tensorflow.google.cn/install/pip?hl=zh-cn#package-location)��������ָ���汾�� `whl` �����ļ���

���δ�Զ������ð�װĿ¼����Ӧ�ÿ����� `C:\Users\ [users] \Downloads` ���ҵ���Ӧ�� `whl` �ļ���

Ȼ���뼤����Ϊ `tensorFlow` �����⻷����ʹ���������
```
activate tensorflow
```
��ʱ������Ӧ�ô� `base` ��Ϊ `tensorflow` ��

<br>��������ָ��Կ�ʼ���� TensorFlow-GPU �汾��
```
pip install C:\Users\ [users] \Downloads\tensorflow_gpu-2.6.0-cp39-cp39-manylinux2010_x86_64.whl
```

#### ʹ�����߰�װ

�����ʹ�� `pip install tensorflow-gpu=[version]` ָ�����߰�װָ���汾�� TensorFlow-GPU��

��ע�⣬���ؿ����������������жϣ�����Ը��� Anaconda ������Դ��ȷ����ȷ��װ��

### ��֤ TensorFlow-GPU �Ƿ�װ�ɹ�

�����⻷���н��� Python �������������������
```
>>> import tensorflow as tf
>>> tf.test.is_gpu_available()
```
���������ȷ��ʾ Nvidia GPU �ͺź��Դ��С��������ĩβ��ʾ `True` �ַ�������� TensorFlow-GPU ��ɲ���