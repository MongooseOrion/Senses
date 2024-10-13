# �� Windows ���� TensorFlow-GPU �汾

## �Ⱦ�����

  1. Windows �汾��Windows10 1909 �����ϣ�
  2. Nvidia GPU �����Լ�������[֧�� Cuda �� GPU �ͺ�](https://developer.nvidia.com/cuda-gpus)��
  3. Cuda ֧���� cuDNN ֧������� [TensorFlow �������Եļ��ݰ汾](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)��
  4. ȷ�� Nvidia GPU �������������°汾�����豣֤��������ʼ��Ϊ���£��ɲ��� [NVIDIA Geforce Experience](https://www.nvidia.cn/geforce/geforce-experience/)��

��ע�⣬���� Tensorflow ֧����վ��������Ϣ��TensorFlow-GPU �汾 2.11 �Ѿ���֧��ԭ�� Windows �� GPU ���С��������Ҫ�� Windows �������� GPU �汾�� TensorFlow����ôֻ��ѡ�� TensorFlow-GPU �汾 2.10������������ Windows ʹ�� 2.11 ����߰汾�� TensorFlow-GPU���뿼�� WSL2 �����[�� Windows �����д�Դ���빹��](https://tensorflow.google.cn/install/source_windows?hl=zh-cn)��

## ��װ Cuda ������������� cuDNN ������

NVIDIA CUDA��Compute Unified Device Architecture����һ������ GPU ���м����ƽ�м���ƽ̨�ͱ��ģ�ͣ�ּ��Ϊ GPU �ṩһ��ͨ�õı�̽ӿںͱ��ģ�ͣ�ʹ�ÿ�����Ա����ͨ����д CUDA ���������� GPU ���в��м��㡣

���� Cuda ��������� cuDNN ʱ����Ӧ��ȷ����������汾��cuDNN �汾�� [TensorFlow �������Եļ��ݰ汾](https://tensorflow.google.cn/install/source?hl=zh-cn#gpu)���г��� TensorFlow �汾����ݡ�

Cuda �����������ص��[�˴�](https://developer.nvidia.com/cuda-toolkit-archive)��cuDNN �����ص��[�˴�](https://developer.nvidia.com/rdp/cudnn-archive)��

�ڰ�װ Cuda ����������ɺ󣬽� cuDNN �����ļ��п����� Cuda �İ�װĿ¼�£��滻�ļ��� `bin`��`include` �� `lib`��

��������������󣬽� Cuda �İ�װ�ļ����ļ�����ӵ� Windows ϵͳ�� `Path` ����������

---

���������ɣ��� [Windows �ն�](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)�����룺

```
nvcc -V
```

Ӧ����� Cuda ��������汾�š�

## ��װ Anaconda Ӧ�ó���

ʹ�� Anaconda Ӧ�ó��������� TensorFlow �����¼����ô���

  1. ����������ϵ��Anaconda Ӧ�ó�������Զ����� TensorFlow �������Ŀ�͹��ߣ�ȷ�� TensorFlow ��������ϵ��ȷ���󣬱��������������⵼�¹���ʧ�ܻ�����ʱ����
  2. ��ƽ̨֧�֣�Anaconda Ӧ�ó���֧�ֶ��ֲ���ϵͳ������ Windows��Linux �� MacOS�������ڲ�ͬƽ̨�Ϲ��������� TensorFlow Ӧ�ó���
  3. �������⻷����Anaconda Ӧ�ó���֧�ִ������⻷���������ڲ�ͬ�Ļ����й��������� TensorFlow Ӧ�ó��򣬱��ⲻͬ��Ŀ֮���������ͻ��
  4. �򻯹������̣�Anaconda Ӧ�ó����ṩ��һ�ּ򵥵ķ�ʽ�������͹��� TensorFlow Ӧ�ó����û�ֻ��Ҫִ��һЩ�򵥵�����Ϳ����Զ������Ͱ�װ TensorFlow�������˷������ֶ����úͰ�װ���̡�
  5. ��װ������͹��ߣ�Anaconda Ӧ�ó����ṩ��һ���㷺�Ŀ�ѧ�����͹��ߵļ��ϣ��û����Է���ذ�װ��ʹ����Щ��͹��ߣ��� NumPy��SciPy��Matplotlib �ȣ����Է���ؽ��п�ѧ��������ݷ�����

���[�˴�](https://www.anaconda.com/)�Է��� Anaconda ��վ��

### ʹ�� `Anaconda Prompt` ���� TensorFlow ���⻷��

�� `Anaconda Prompt` Ӧ�ó�������������������Բ鿴��ǰ�������⻷����
```
conda env list
```

<br>���贴��һ���µ� TensorFlow �������������������
```
conda create -n tensorflow python=3.9
```
���У�`tensorflow` Ϊ�û�ָ�������⻷�����ơ�**��ע��**��������������ָ�������⻷��Ϊ TensorFlow ����������`python=3.9` ����ָ�������⻷��Ϊ Python3.9 �汾����ע�⣬�˴��� Python ֻ�ڴ����⻷����Ψһ��Ч��

## ���������⻷���в��� TensorFlow-GPU

### ʹ�����߰�װ

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

### ʹ�����߰�װ

�����ʹ�� `pip install tensorflow=[version]` ָ�����߰�װָ���汾�� CPU��GPU ���ɰ汾 TensorFlow��

��ע�⣬���ؿ����������������жϣ�����Ը��� Anaconda ������Դ��ȷ����ȷ��װ��

## ��֤ TensorFlow-GPU �Ƿ�װ�ɹ�

�����⻷���н��� Python �������������������
```
>>> import tensorflow as tf
>>> tf.test.is_gpu_available()
```
���������ȷ��ʾ Nvidia GPU �ͺź��Դ��С��������ĩβ��ʾ `True` �ַ�������� TensorFlow-GPU ��ɲ���