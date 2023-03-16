# �� Windows ��ʵ������������
�� Windows10 �ĵ�һ����ʽ�汾 1507 �����Ѿ���ȥ�� 8 �ꡣ���ǵ� 2014 �꣬����ý�嶼�ڷ���ʡ������µ� Windows ����ϵͳ���Ǹ�ʱ�������� Surface Pro3������д c �� ��Hello world�� ����<br><br>
��ʵ�ϣ��� Windows11 ����ǰϦй¶ 22000 �汾�����������԰�װ��ͬ����ǰ�һ��� 2 ��ʱ������վ����� Windows8 ���µ� Windows10��Windows8.1 ʼ�ղ������Ҹ������**��ʼ�˵�**���ܣ����ò�˵ʱ����������Ȼ���ǻ�˵ Win8 ��**��ʼ**��ƺ�ǰ������Ȼ��UWP �� Fluent Design Ҳһֱ���������ҡ��ܿ�ϧ���ǣ������մ���� UWP ��ٵ�ʱ�ڡ�<br><br>
�ϻ�����˵����ӹ���ɵ��� Windows11 �����зǳ��걸�Ŀ�������������ȻҲ�зǳ��õļ����ԣ���ʵ�Ҳ���ϲ�������ʷ����������ʦ�����ҿ��Գ����� Linux ������ĳЩ���أ����Ҿ��� Windows ����ʤ�Σ���Ҳ���Ҿ���д����ĵ���Դ������

## ��ҳ����
  * ʹ�� Windows �������� Linux ���غ� Android Ӧ�ó���
  * ʹ���Ϲ�ͬ�� FPGA ������������� Xilinx ����
  * �� Windows ���� TensorFlow-GPU �汾

## ʹ�� Windows �������� Linux ���غ� Android Ӧ�ó���
�ڱ��£����������ʹ�� [Windows �ն�](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)���� Python ����������[������ Windows �� Linux ��ϵͳ��WSL2��](https://learn.microsoft.com/zh-cn/windows/wsl/about)��

### �Ⱦ�����
  1. Windows11 ���ڲ��汾���� 22000.194 �����ϣ�
  2. ���� RAM ������ 8GB��

### ���� Python ����

�� Micorsoft store �п���ֱ�Ӱ�װ Python��������Զ��尲װ���������ĺô����� Visual Studio ����ֱ��ʶ�� Python ����������������ã������Է�����Ƴ���

Ҫ���� Python ֮ǰ����ȷ��Դ����򿪷����������� Python �汾��Python3.9 �ɵ��[�˴�](ms-windows-store://pdp/?ProductId=9p7qfqmjrfp7&referrer=bingwebsearch&ocid=bingwebsearch)��װ��

���δ�Զ��尲װĿ¼��������� `C:\Users\ [user] \AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_qbz5n2kfra8p0\LocalCache\local-packages\Python39\Scripts` ·�����ҵ�ʹ�� `pip install` ���װ�ĵ�����ģ�顣

<br>�뽫��·������ `Path` ���������У��Ա�ֱ�Ӵ� Windows �ն��н��� Python ������

### ���� WSL2

���[�˴�](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R)��װ WSL ���ߣ��ù��߿��Թ���ϵͳ�а�װ������ WSL �ַ��汾��



## ʹ���Ϲ�ͬ�� FPGA ������������� Xilinx ����

�Ϲ�ͬ���� FPGA ��������Ϊ Pango Design Suite �� Pango Design Suite Lite��PDS�����ڴ��½ڽ��������ʹ�� PDS ���ߡ�

*�ٶ����Ѿ���װ�� PDS Ӧ�ó���� Modelsim��*

## �� Windows ���� TensorFlow-GPU �汾

### �Ⱦ�����

  1. Windows �汾��Windows 10 1909 �����ϣ�
  2. Nvidia GPU �����Լ�������[֧�� Cuda �� GPU �ͺ�](https://developer.nvidia.com/cuda-gpus)��
  3. Cuda ֧���� cuDNN ֧������� [TensorFlow �������Եļ��ݰ汾](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)��
  4. ȷ�� Nvidia GPU �������������°汾�����豣֤��������ʼ��Ϊ���£��ɲ��� [NVIDIA Geforce experience](https://www.nvidia.cn/geforce/geforce-experience/)��

### ��װ Cuda ������������� cuDNN ������

NVIDIA CUDA��Compute Unified Device Architecture����һ������ GPU ���м����ƽ�м���ƽ̨�ͱ��ģ�ͣ�ּ��Ϊ GPU �ṩһ��ͨ�õı�̽ӿںͱ��ģ�ͣ�ʹ�ÿ�����Ա����ͨ����д CUDA ���������� GPU ���в��м��㡣

���� Cuda ��������� cuDNN ʱ��Ӧ��ȷ����������汾��cuDNN �汾�� [TensorFlow �������Եļ��ݰ汾](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)���г��� TensorFlow �汾����ݡ�

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

#### ���������⻷���в��� TensorFlow-GPU
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

#### ��֤ TensorFlow-GPU �Ƿ�װ�ɹ�

�����⻷���н��� Python �������������������
```
>>> import tensorflow as tf
>>> tf.test.is_gpu_available()
```
���������ȷ��ʾ Nvidia GPU �ͺź��Դ��С��������ĩβ��ʾ `True` �ַ�������� TensorFlow-GPU ��ɲ���