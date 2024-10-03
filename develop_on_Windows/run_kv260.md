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
# 在 Xilinx KV260 上部署开发环境和运行模型

在[利用 WSL 运行 Xilinx Vitis AI](https://github.com/MongooseOrion/Senses/blob/main/develop_on_Windows/wsl_vitis_ai.md)中，已经介绍了如何在主机上部署 Vitis-AI 工作环境。在本文中，将主要介绍如何使用 KV260 运行常见的模型和自定义模型。

## 部署环境和快速验证

你可以[点此](https://xilinx.github.io/Vitis-AI/3.0/html/docs/quickstart/mpsoc.html#setup-the-target)查看下载和烧录 KV260 的 Linux 镜像教程。

通过上述文档，你应该可以通过运行 ResNet50 示例模型来确保环境已经部署完成。