# 部署紫光同创 FPGA 开发工具链

紫光同创的现场可编辑逻辑门阵列（FPGA）开发工具包括 Pango Design Suite 和 Pango Design Suite Lite（PDS），在此章节将介绍如何使用 PDS 工具。

## 先决条件

  1. 已安装 Altera ModelSim 应用程序；
  2. 具备紫光 FPGA 硬件开发平台。

## 仿真和编译
若要使用 ModelSim 来进行设计文件的验证，你需要在 `Project - Project Settings - Simulation - Target Simulator` 中选择 `ModelSim Simulator`。

你可以将 `Compiled Libarary Location` 设置在 Modelsim 应用程序安装根目录下，以便 ModelSim 可靠地编译 PDS 相关器件和查看。然后，你需要设置 `Simulator Executable Path` 在 Modelsim 主程序的父文件夹路径下，如果是默认设置，它应该是 `C:\altera\13.1\modelsim_ase\win32aloem`。

如果设置正确，你应该可以在编写激励文件后运行行为级仿真时能够看到 Modelsim 自动打开并进行波形仿真。

## 添加 IP 文件

如果是预置的 IP 核，你可以直接在左侧的 `source` 窗格中获取所需的模块，例如时钟分频器和逻辑分析仪。

如果是第三方 IP 核，你首先需要安装它。请在上部打开 `Tools - IP Compiler`，然后在 IP Compiler 的上部打开 `Files - update` 功能，点击 `Add packedge` 后添加 IP 核所在的路径。你需要确保它是一个 `iar` 文件。

## 打开原理图

原理图是帮助设计人员从代码级转移到电路级的重要工具，其可以方便地检查使用硬件描述语言（HDL）编写的代码间的逻辑关系，并了解输入和输出的连接关系。

若要使用原理图功能，你需要确认通过波形仿真和编译。点击 `Tools - Schematic Viwer` 即可查看。

## 综合

在此步骤下，需要进行硬件管脚约束，以便 PDS 确认 Verilog 中包含的端口与硬件对应。你可以直接编写管脚约束文件 `.fdc`，其格式如下：
```ruby
define_attribute {p:led[7]} {PAP_IO_DIRECTION} {OUTPUT}
define_attribute {p:led[7]} {PAP_IO_LOC} {F8}
define_attribute {p:led[7]} {PAP_IO_VCCIO} {3.3}
define_attribute {p:led[7]} {PAP_IO_STANDARD} {LVCMOS33}
define_attribute {p:led[7]} {PAP_IO_DRIVE} {8}
define_attribute {p:led[7]} {PAP_IO_NONE} {TRUE}
define_attribute {p:led[7]} {PAP_IO_SLEW} {SLOW}
```

除此之外，PDS 也提供了 GUI 的管脚约束功能，你可以通过点击 `Tools - User Constraint Editer - Pre Synthesize UCE` 打开该功能。点击 `device` 选项，然后在左边二级菜单中点击 `I/O table` 以对系统所有的输入和输出接口进行约束，在选择对应的管脚编号后，其会自动生成管脚电压、驱动等内容。完成编辑后，点击保存按钮，将自动生成 `.fdc` 文件。

**请注意，在约束前你需要确定所采用的芯片部件编号，并仔细对照接口的管脚编号是否正确。**

### 提示

请注意，PDS 不允许设计代码中的 `always` 块引入异步复位但不使用的情况，例如：
```ruby
always@(posedge clk or negedge rst) begin
    key_reg <= key;
end
```
在上述示例代码中，引入了 `negedge rst` 异步复位模式，但是未指定当复位信号变化时，寄存器 `key_reg` 的变化。这样会产生风险：在复位信号来临时，系统仍然在保持运行。应当修改为：

```ruby
always@(posedge clk or negedge rst) begin
    if(!rst) key_reg <= 0;        // PDS 在 rst 为 null 时会对该信号报错
    else key_reg <= key;
end
```

## 布局布线

在此步骤下，你应该处理时钟约束问题。

### 忽略单个引脚的时序约束问题

某些时钟信号由于一些原因，没有被安排到 FPGA 器件的时钟专用引脚上，这就会导致触发错误。

错误内容为：
```
Place-0084: GLOBAL_CLOCK: the driver [port] fixed at [position] is unreasonable. Sub-optimal placement for a clock source and a clock buffer.
```

解决方法是：在 `Pre Synthesize UCE` 功能中选择 `Attributes` 选项，然后在其中添加相关输出网络（Nets）名称，并选择 `PAP_CLOCK_DEDICATED_ROUTE` 的值为 `FALSE`。

## 下载至开发板

在生成比特流文件后，点击 `Tools - Configuration` 打开设备管理功能。

如果板子与电脑连接正确，你应该可以在点击 `File - Connect To Server` 后，在 `Device Properties` 窗格中看到你的设备信息。

如果你的板子不支持 SPI Flash，请选择 `Boundary Scan` 并在右侧窗口中右键选择 `Add Pango Device` 以添加比特流文件。然后你将可以 `Program Device`。