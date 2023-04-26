# �����Ϲ�ͬ�� FPGA ����������

�Ϲ�ͬ�����ֳ��ɱ༭�߼������У�FPGA���������߰��� Pango Design Suite �� Pango Design Suite Lite��PDS�����ڴ��½ڽ��������ʹ�� PDS ���ߡ�

## �Ⱦ�����

  1. �Ѱ�װ Altera ModelSim Ӧ�ó���
  2. �߱��Ϲ� FPGA Ӳ������ƽ̨��

## ����ͱ���
��Ҫʹ�� ModelSim ����������ļ�����֤������Ҫ�� `Project - Project Settings - Simulation - Target Simulator` ��ѡ�� `ModelSim Simulator`��

����Խ� `Compiled Libarary Location` ������ Modelsim Ӧ�ó���װ��Ŀ¼�£��Ա� ModelSim �ɿ��ر��� PDS ��������Ͳ鿴��Ȼ������Ҫ���� `Simulator Executable Path` �� Modelsim ������ĸ��ļ���·���£������Ĭ�����ã���Ӧ���� `C:\altera\13.1\modelsim_ase\win32aloem`��

���������ȷ����Ӧ�ÿ����ڱ�д�����ļ���������Ϊ������ʱ�ܹ����� Modelsim �Զ��򿪲����в��η��档

## ��� IP �ļ�

�����Ԥ�õ� IP �ˣ������ֱ�������� `source` �����л�ȡ�����ģ�飬����ʱ�ӷ�Ƶ�����߼������ǡ�

����ǵ����� IP �ˣ���������Ҫ��װ���������ϲ��� `Tools - IP Compiler`��Ȼ���� IP Compiler ���ϲ��� `Files - update` ���ܣ���� `Add packedge` ����� IP �����ڵ�·��������Ҫȷ������һ�� `iar` �ļ���

## ��ԭ��ͼ

ԭ��ͼ�ǰ��������Ա�Ӵ��뼶ת�Ƶ���·������Ҫ���ߣ�����Է���ؼ��ʹ��Ӳ���������ԣ�HDL����д�Ĵ������߼���ϵ�����˽��������������ӹ�ϵ��

��Ҫʹ��ԭ��ͼ���ܣ�����Ҫȷ��ͨ�����η���ͱ��롣��� `Tools - Schematic Viwer` ���ɲ鿴��

## �ۺ�

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

### ��ʾ

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

## ���ֲ���

�ڴ˲����£���Ӧ�ô���ʱ��Լ�����⡣

### ���Ե������ŵ�ʱ��Լ������

ĳЩʱ���ź�����һЩԭ��û�б����ŵ� FPGA ������ʱ��ר�������ϣ���ͻᵼ�´�������

��������Ϊ��
```
Place-0084: GLOBAL_CLOCK: the driver [port] fixed at [position] is unreasonable. Sub-optimal placement for a clock source and a clock buffer.
```

��������ǣ��� `Pre Synthesize UCE` ������ѡ�� `Attributes` ѡ�Ȼ��������������������磨Nets�����ƣ���ѡ�� `PAP_CLOCK_DEDICATED_ROUTE` ��ֵΪ `FALSE`��

## ������������

�����ɱ������ļ��󣬵�� `Tools - Configuration` ���豸�����ܡ�

������������������ȷ����Ӧ�ÿ����ڵ�� `File - Connect To Server` ���� `Device Properties` �����п�������豸��Ϣ��

�����İ��Ӳ�֧�� SPI Flash����ѡ�� `Boundary Scan` �����Ҳര�����Ҽ�ѡ�� `Add Pango Device` ����ӱ������ļ���Ȼ���㽫���� `Program Device`��