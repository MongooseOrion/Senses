# ʹ�� Windows �������� Linux ���غ� Android Ӧ�ó���

���Ľ��������ʹ�� [Windows �ն�](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)���� Python ����������[������ Linux �� Windows ��ϵͳ��WSL2��](https://learn.microsoft.com/zh-cn/windows/wsl/about)�������� Android �� Windows ��ϵͳ���ѱ����ã���

## �Ⱦ�����

  1. Windows11 ���ڲ��汾���� 22000.194 �����ϣ�
  2. ���� RAM ������ 8GB��

## ���� Python ����

�� Micorsoft store �п���ֱ�Ӱ�װ Python��������Զ��尲װ���������ĺô����� Visual Studio ����ֱ��ʶ�� Python ����������������ã������Է�����Ƴ���

Ҫ���� Python ֮ǰ����ȷ��Դ����򿪷����������� Python �汾��Python3.9 �ɵ��[�˴�](https://apps.microsoft.com/store/detail/python-39/9P7QFQMJRFP7?hl=en-us&gl=us)��װ��

���δ�Զ��尲װĿ¼��������� `C:\Users\ [username] \AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_qbz5n2kfra8p0\LocalCache\local-packages\Python39\Scripts` ·�����ҵ�ʹ�� `pip install` ���װ�ĵ�����ģ�顣

<br>�뽫��·������ `Path` ���������У��Ա�ֱ�Ӵ� Windows �ն��н��� Python ������

���������ɣ���Ӧ�ÿ������ն������� `python` ����� Python ������

## ���� WSL2

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

## ���������� Android �� Windows ��ϵͳ��WSA��

������� Microsoft store ������ Amazon appstore�����ز���װ�󣬿�ʼ�˵��н�������Ϊ `������ Android �� Windows ��ϵͳ����` ��Ӧ�ó��򡣴� `������Ա - ������Աģʽ`����ʱ��������� IP ��ַ������ʹ�� Android �����ţ�ADB���Լ���Ӧ�ó��򣬻� WSA ����Ϊ Android Studio Ĭ���������

WSA ����ֱ�����л��� ARM64 �� x86 ������ Android Ӧ�ó������¹��ܻ����ȫ֧�֣�
  * ���أ�����ȡ���ڱ���Ӳ���Ĵ���֧�֣�
  * ������
  * ����ͷ
  * ��˷�

���¹��ܲ���֧�֣�
  * ͼ�δ���������֧�� Vulkan ���棬�Ƽ� Intel �� Nvidia �ĺ�о�Կ��Ͷ����Կ���

�ɰ������� WSA ���� Android Ӧ�ó��򿪷���