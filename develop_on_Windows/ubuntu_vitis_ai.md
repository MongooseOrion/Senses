# �� Ubuntu �²��� Xilinx Vitis-AI ���㻷��

## �Ⱦ�����

*��Щ�������������Բ��ԣ�������˵��������Щ�����²ſ������У������������в������������л�����*

  * Ubuntu �汾 20.04
  * �ڴ棺4GB
  * ���ÿռ䣺60GB
  * ���������ģ�4 �ˣ�ÿ�������߳���Ϊ 1
  * Vitis-AI �汾 2.5

�����ϣ��ʹ��[������ Linux �� Windows ��ϵͳ](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/WSL.md)��WSL�������� Vitis-AI ���л�������[���](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/wsl_vitis_ai.md)���ʡ�

## ��ҳ����

  * ��ȡ Vitis-AI �ֿ�
  * ��װ Docker Container
  * ��װ Anaconda
  * ���� Vitis-AI Docker ����

*ע�⣺�״������ն�ʱ������ͨ�����������������ϵͳ������*
```bash
>> sudo apt update
>> sudo apt upgrade
```

## �����Թ����ų�

�ڴ˴��г���һЩʹ��Ԥ�õ����⾵����ܳ��ֵ�����Ͷ�Ӧ�Ľ������������Գ����Ų���ϡ�

### ��ʾ������̲����ݣ��޷���Ԥ�õ��������

��������Ԥ�õ� Ubuntu20.04 �����ǻ��� VMware17.0.2 �����ġ���������е� VMware �����ڰ汾���������ͨ����� `�����` - `����` - `����Ӳ��������`�������������ʹ�ü���ģʽ���С�

### �������������磬��������޷����ʻ�����

����������ھ������ڴ��ڶ����ͬ�������ַ���������������ֹ���ʻ���������Ҫ��������⣬����ѭ���²��裺
  1. ȷ�������Ϊ�ػ�״̬��
  1. ȷ���� VMware ����������е�����������ģʽΪ `NAT` ģʽ��
  2. �� `����������ѡ��` �ж�Ӧ������������������������һ�� MAC ��ַ������ IP ��ַ��
  3. �� Windows �����е�������������ԣ�Ȼ�����ù����������ӵ�ָ��������������
  4. ����������������նˣ������������

```bash
>> sudo service network-manager stop
>> sudo rm /var/lib/NetworkManager/NetworkManager.state
>> sudo service network-manager start
```

��Ӧ�ÿ�����ִ����������������������Ͻǿ��������������ӵı�ʶ��

## ��ȡ Vitis-AI �ֿ�

### ��װ Git

����Ҫʹ�� Git ��ȡλ�� GitHub �� Vitis-AI Զ�ֿ̲⡣ͨ�����������������԰�װ Git��
```bash
>> sudo apt install git
```

### ��ȡ�ֿ�

Vitis-AI �� GitHub �ֿ�λ���� `https://github.com/Xilinx/Vitis-AI`�������ֱ����ȡ���°棬Ҳ������ȡ���ڰ汾������Բ鿴�ֿ��֧ѡ����ʵİ汾��**���ĵ�ʹ�� 2.5 �汾**��ʹ��������������ȡ�÷�֧��

```bash
>> git clone -b 2.5 https://github.com/Xilinx/Vitis-AI
```

## ���� Docker Container Ӧ�ó���

### ��װ Docker Container
���ȣ�ͨ���������������������������Ұ�װ��Ҫ�����������
```bash
>> sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```

Ȼ��ʹ�� `curl` ����Դ�ֿ�� GPG key��
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

�� Docker APT ���Դ��ӵ�ϵͳ�У�
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

�������������ֱ�Ӱ�װ���°� Docker Container Ӧ�ó���
```bash
sudo apt install docker-ce docker-ce-cli containerd.io
```

### ��֤ Docker Container ����״̬

ͨ������ `sudo systemctl status docker`���㽫���Կ��� Docker ����״̬������������У�������ʾ��������������Ϣ��
```bash
�� docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset>
     Active: active (running) since Tue 2023-10-10 20:41:02 CST; 13min ago
TriggeredBy: �� docker.socket
       Docs: https://docs.docker.com
   Main PID: 1086 (dockerd)
      Tasks: 13
     Memory: 98.7M
     CGroup: /system.slice/docker.service
             ����1086 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/cont>

10�� 10 20:40:57 ubuntu dockerd[1086]: time="2023-10-10T20:40:57.190108404+08:0>
10�� 10 20:40:57 ubuntu dockerd[1086]: time="2023-10-10T20:40:57.234916952+08:0>
10�� 10 20:40:58 ubuntu dockerd[1086]: time="2023-10-10T20:40:58.196150681+08:0>
10�� 10 20:40:58 ubuntu dockerd[1086]: time="2023-10-10T20:40:58.287704676+08:0>
10�� 10 20:41:01 ubuntu dockerd[1086]: time="2023-10-10T20:41:01.138433753+08:0>
10�� 10 20:41:01 ubuntu dockerd[1086]: time="2023-10-10T20:41:01.750789042+08:0>
10�� 10 20:41:02 ubuntu dockerd[1086]: time="2023-10-10T20:41:02.299463077+08:0>
10�� 10 20:41:02 ubuntu dockerd[1086]: time="2023-10-10T20:41:02.300051177+08:0>
10�� 10 20:41:02 ubuntu dockerd[1086]: time="2023-10-10T20:41:02.649779318+08:0>
10�� 10 20:41:02 ubuntu systemd[1]: Started Docker Application Container Engine.
lines 1-21/21 (END)
```
*ע�⣺����Ҫ���� `:q` �ſ��Լ����������*

�㻹����ͨ������ `docker run hello-world` ���������� Docker Hello world ��������� Docker �������У�Ӧ�ó���������Ϣ��
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

�����ʾ�û���Ȩ���� Docker ����������������������������ݡ�

### ������Ȩ�û���ӵ��û���

���ȣ�����Ҫ����һ�������� Docker ��Ⱥ�飺
```bash
>> sudo groupadd docker
```

Ȼ�󣬽��û�������Ⱥ�飺
```
>> sudo usermod -aG docker <USER_NAME>
```
���У�`<USER_NAME>` �������û����ơ�

������ Docker Container��
```bash
>> sudo systemctl restart docker
```

��ʱ�����û�Ӧ�þ߱����� Docker ��Ȩ�ޡ�

### ���� Docker ����ԴΪ����Դ

���ȣ�����Ҫ���� Vim�������ֱ���� Ubuntu Ӧ���̵����أ��������ն��м����������

```bash
>> sudo apt install vim
```

һ��������ɣ������ն˼��룺
```bash
>> vim /etc/docker/daemon.json
```

Ȼ������ `i` ����༭ģʽ������������ݣ�
```bash
{
    "registry-mirrors": [ 
        "https://docker.mirrors.ustc.edu.cn"    // ����Ϊ�廪Դ
    ]
}
```

���� `ESC` ���˳��༭ģʽ������ `:wq` ���沢�˳���

Ȼ������Ҫ���� Docker Container ����Ч��

## ��װ Anaconda

### ���ذ�װ�ļ������� Anaconda

�������[�廪Դ](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)�����غ��ʵ� Anaconda �����ļ������� AMD64���밲װ x86-x64������ ARM64���밲װ aarch64��

�л�������Ŀ¼��Ȼ��ִ�� bash ��װ��

```bash
>> cd <ANACONDA_DOWNLOAD_PATH>
>> bash <FILE_NAME>
```

��װ��ɺ󣬽���ע�������������նˣ���ȷ�� Anaconda ��Ч��

��Ҫ��֤ Anaconda �Ƿ�װ�ɹ��������ʹ�� `conda list` �� `conda --version` ����顣

### ���� Anaconda ���⻷��

ʹ��������������⻷����
```bash
>> conda create --name <ENV_NAME> <PACKEDGE_NAME>
```
���У�`<EVN_NAME>` �������⻷�����ƣ�`<PACKEDGE_NAME>` ����ָ�����⻷���е� Python �汾���������봴��һ�� Python �汾Ϊ 3.9 ��Ϊ tensorflow �����⻷������Ӧ�����룺
```bash
>> conda create --name tensorflow python=3.9
```

��Ҫ����ָ�����⻷���������룺
```bash
>> conda activate <ENV_NAME>
```

��Ҫͣ��ָ�����⻷���������룺
```bash
>> conda deactivate <ENV_NAME>
```

�򷵻���������
```bash
>> conda activate base
```

### �����⻷���а�װ python ��

����Խ���ָ��������Ȼ��ʹ�� `pip install` �����غͰ�װ python ��������Ҫ��װ�İ������������ڣ�

  * tensorflow==2.7
  * opencv_python
  * matplot
  * notebook

**ע�⣺Ԥ�õľ������Ѿ���������Ϊ `tensorflow` �����⻷�����Ѿ������������������ֱ�Ӽ���û�����**

## ��װ Vitis-AI-CPU Docker ����

����Ҫ�����л��� Vitis-AI ���زֿ⣬�������������

```bash
>> cd Vitis-AI
>> docker pull xilinx/vitis-ai-cpu:latest
```
*ע�⣺�������ҪһЩʱ�䡣*

## ���𽻲���빤����

���ｫʹ�� VART ��Եƽ̨���𽻲���뻷����
```bash
>> cd <VITIS-AI INSTALL PATH>/Vitis-AI/setup/mpsoc
>> bash host_cross_compiler_setup.sh
```

Ӧ�ûῪʼ���� petalinux_sdk_2022.1_sdk��

��������ɺ󣬰�����ʾ���룺
```bash
>> source ~/petalinux_sdk_2022.1/environment-setup-cortexa72-cortexa53-xilinx-linux
```
�������ý�����뻷����

����Բ��Ա��빦�ܣ������������������Ӧ�ÿ�����ͬһ���ļ����¿�����Ϊ `resnet50` ���ļ���
```bash
>> cd <VITIS-AI INSTALL PATH>/Vitis-AI/examples/VART/resnet50
>> bash -x build.sh
```

**ע�⣺�������Ҫ�������� `resnet50` �ļ��Բ��Ա��빦�ܣ�������Ҫ����ִ���������**

```bash
>> source ~/petalinux_sdk_2022.1/environment-setup-cortexa72-cortexa53-xilinx-linux
```

## �������ѧϰ��Ŀʾ��

### ���������

ʹ�������������������� Vitis-AI �� Docker��
```bash
>> cd <Vitis-AI install path>/Vitis-AI
>> ./docker_run.sh xilinx/vitis-ai-cpu:latest
```

���������ڿ���̨���� Vitis-AI �ı�ʶ����˵������������������

### �������ѧϰ��Ŀʾ��

���ڣ������[���](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/run_kv260.md)���˽��� KV260 ���Ͽ��������ݡ�