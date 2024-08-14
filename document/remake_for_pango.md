# 在紫光 FPGA 环境下移植开源项目

与 Xilinx 不同，紫光 FPGA 开发平台并不完善，这体现在各个方面，例如原语和 IP 核。因此，许多的开源项目需要重新编写或修改某些部分才能通过紫光 PDS 开发工具的编译及后续的验证。该文档将总结我适配紫光的所有开源 RTL 项目。

## 紫光 PDS 软件 IP 核注意事项

PDS 软件的文档写得并不详细，很多功能和特性根本需要自己仿真甚至使用逻辑分析仪在线调试信号才能弄清楚，因此我这篇文档将对 PDS 的某些 IP 核注意事项进行说明。

### DRM based FIFO

| 信号名称 | 说明 |
| :---: | :--- |
| wr_en、rd_en | 在拉高后下一个时钟周期（写、读时钟域）才会写进数据或者读出数据 |
| almost_full、almost_empty | 在到达设置的值时同时拉高，不是在下一个时钟拉高 |
| wr_full、rd_empty | 在写进最后一个数据，或者读空最后一个数据后才拉高，不是与最后一个数据同时拉高 |
| almost_full_water_level | 在写时钟下对 FIFO 中的数据个数计数，当到达设定值时（如果有），拉高 almost_full 信号（立即拉高，不等一个时钟周期） |
| almost_empty_water_level | 在读时钟下对 FIFO 中的数据个数计数，当到达设定值时（如果有），拉高 almost_empty 信号（立即拉高，不等一个时钟周期） |

### FFT IP

  1. 快速傅里叶变换（FFT）IP 核数据输入端为 32 位，其中高 16 位为虚部，低 16 位为实部；数据输出端为 64 位，其中高 32 位为虚部，低 32 位为实部。输出的结果分别都只有 25 位为有效数据位，高 7 位为保留位。
  2. 若使用反傅里叶变换功能，则输出结果被扩大 256 倍，也即低 8 位可以不要。

## 重新编写的 IP 核

由于紫光缺少 IP 核，可能需要手动编写 RTL 代码，目前包括下述内容：
  * [AHB Lite 转 AXI4 Lite 桥](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/system/ahb_to_axi_bridge.v)
  * [IOBUF](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/logic_primitive/IOBUF.v)
  * [逻辑上拉 PULLUP](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/logic_primitive/PULLUP.v)

## 无剑 100 开源 RISC-V SoC

这是一个由阿里平头哥开发的 RISC-V 处理器。[点此](https://github.com/MongooseOrion/wujian100_open)访问。