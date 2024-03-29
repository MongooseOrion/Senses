# 在紫光 FPGA 环境下移植开源项目

与 Xilinx 不同，紫光 FPGA 开发平台并不完善，这体现在各个方面，例如原语和 IP 核。因此，许多的开源项目需要重新编写或修改某些部分才能通过紫光 PDS 开发工具的编译及后续的验证。该文档将总结我适配紫光的所有开源 RTL 项目。

## 重新编写的 IP 核

由于紫光缺少 IP 核，可能需要手动编写 RTL 代码，目前包括下述内容：
  * [AHB Lite 转 AXI4 Lite 桥](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/system/ahb_to_axi_bridge.v)
  * [IOBUF](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/logic_primitive/IOBUF.v)
  * [逻辑上拉 PULLUP](https://github.com/MongooseOrion/MyVerilogLearning/blob/master/logic_primitive/PULLUP.v)

## 无剑 100 开源 RISC-V SoC

这是一个由阿里平头哥开发的 RISC-V 处理器。[点此](https://github.com/MongooseOrion/wujian100_open)访问。