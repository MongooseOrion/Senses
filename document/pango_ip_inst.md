<!-- =====================================================================
* Copyright (c) 2023, MongooseOrion.
* All rights reserved.
*
* The following code snippet may contain portions that are derived from
* OPEN-SOURCE communities, and these portions will be licensed with: 
*
* <NULL>
*
* If there is no OPEN-SOURCE licenses are listed, it indicates none of
* content in this Code document is sourced from OPEN-SOURCE communities. 
*
* In this case, the document is protected by copyright, and any use of
* all or part of its content by individuals, organizations, or companies
* without authorization is prohibited, unless the project repository
* associated with this document has added relevant OPEN-SOURCE licenses
* by github.com/MongooseOrion. 
*
* Please make sure using the content of this document in accordance with 
* the respective OPEN-SOURCE licenses. 
* 
* THIS CODE IS PROVIDED BY https://github.com/MongooseOrion. 
* FILE ENCODER TYPE: GBK
* ========================================================================
-->
# 紫光 PDS 软件 IP 核注意事项

PDS 软件的文档写得并不详细，很多功能和特性根本需要自己仿真甚至使用逻辑分析仪在线调试信号才能弄清楚，因此我这篇文档将对 PDS 的某些 IP 核注意事项进行说明。

## DRM based FIFO

| 信号名称 | 说明 |
| :---: | :--- |
| wr_en、rd_en | 在拉高后下一个时钟周期（写、读时钟域）才会写进数据或者读出数据 |
| almost_full、almost_empty | 在到达设置的值时同时拉高，不是在下一个时钟拉高 |
| wr_full、rd_empty | 在写进最后一个数据，或者读空最后一个数据后才拉高，不是与最后一个数据同时拉高 |

## FFT IP

  1. 快速傅里叶变换（FFT）IP 核数据输入端为 32 位，其中高 16 位为虚部，低 16 位为实部；数据输出端为 64 位，其中高 32 位为虚部，低 32 位为实部。输出的结果分别都只有 25 位为有效数据位，高 7 位为保留位。
  2. 若使用反傅里叶变换功能，则输出结果被扩大 256 倍，也即低 8 位可以不要。