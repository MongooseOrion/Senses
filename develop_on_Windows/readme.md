# 在 Windows 中实现整个工作流
自 Windows10 的第一个正式版本 1507 发布已经过去了 8 年。还记得 2014 年，所有媒体都在疯狂尝鲜、报导新的 Windows 操作系统，那个时候我拿着 Surface Pro3，还在写 c 的 `Hello world` 程序。<br><br>
事实上，与 Windows11 发布前夕泄露 22000 版本后我立即尝试安装不同，以前我花了 2 年时间才最终决定从 Windows8 更新到 Windows10。Windows8.1 始终不能令我割舍的是**开始菜单**功能，不得不说时至今日我仍然还是会说 Win8 的**开始**设计很前卫。当然，UWP 和 Fluent Design 也一直在吸引着我。很可惜的是，我最终错过了 UWP 最繁荣的时期。<br><br>
废话不多说，毋庸置疑的是 Windows11 现在有非常完备的开发工具链，当然也有非常好的兼容性（其实我并不喜欢这个历史包袱）。导师建议我可以尝试在 Linux 上运行某些负载，而我觉得 Windows 足以胜任，这也是我决定写这个文档的源动力。

## 本页内容

  * 使用 Windows 本地运行 Linux 负载和 Android 应用程序
  * 部署紫光同创 FPGA 开发工具链
  * 在 Windows 配置 TensorFlow-GPU 版本

