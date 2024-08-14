# ���Ϲ� FPGA ��������ֲ��Դ��Ŀ

�� Xilinx ��ͬ���Ϲ� FPGA ����ƽ̨�������ƣ��������ڸ������棬����ԭ��� IP �ˡ���ˣ����Ŀ�Դ��Ŀ��Ҫ���±�д���޸�ĳЩ���ֲ���ͨ���Ϲ� PDS �������ߵı��뼰��������֤�����ĵ����ܽ��������Ϲ�����п�Դ RTL ��Ŀ��

## �Ϲ� PDS ��� IP ��ע������

PDS ������ĵ�д�ò�����ϸ���ܶ๦�ܺ����Ը�����Ҫ�Լ���������ʹ���߼����������ߵ����źŲ���Ū������������ƪ�ĵ����� PDS ��ĳЩ IP ��ע���������˵����

### DRM based FIFO

| �ź����� | ˵�� |
| :---: | :--- |
| wr_en��rd_en | �����ߺ���һ��ʱ�����ڣ�д����ʱ���򣩲Ż�д�����ݻ��߶������� |
| almost_full��almost_empty | �ڵ������õ�ֵʱͬʱ���ߣ���������һ��ʱ������ |
| wr_full��rd_empty | ��д�����һ�����ݣ����߶������һ�����ݺ�����ߣ����������һ������ͬʱ���� |
| almost_full_water_level | ��дʱ���¶� FIFO �е����ݸ����������������趨ֵʱ������У������� almost_full �źţ��������ߣ�����һ��ʱ�����ڣ� |
| almost_empty_water_level | �ڶ�ʱ���¶� FIFO �е����ݸ����������������趨ֵʱ������У������� almost_empty �źţ��������ߣ�����һ��ʱ�����ڣ� |

### FFT IP

  1. ���ٸ���Ҷ�任��FFT��IP �����������Ϊ 32 λ�����и� 16 λΪ�鲿���� 16 λΪʵ�������������Ϊ 64 λ�����и� 32 λΪ�鲿���� 32 λΪʵ��������Ľ���ֱ�ֻ�� 25 λΪ��Ч����λ���� 7 λΪ����λ��
  2. ��ʹ�÷�����Ҷ�任���ܣ��������������� 256 ����Ҳ���� 8 λ���Բ�Ҫ��

## ���±�д�� IP ��

�����Ϲ�ȱ�� IP �ˣ�������Ҫ�ֶ���д RTL ���룬Ŀǰ�����������ݣ�
  * [AHB Lite ת AXI4 Lite ��](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/system/ahb_to_axi_bridge.v)
  * [IOBUF](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/logic_primitive/IOBUF.v)
  * [�߼����� PULLUP](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/logic_primitive/PULLUP.v)

## �޽� 100 ��Դ RISC-V SoC

����һ���ɰ���ƽͷ�翪���� RISC-V ��������[���](https://github.com/MongooseOrion/wujian100_open)���ʡ�