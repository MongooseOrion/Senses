# 微软开发者大会 2022（Microsoft Build 2022）会议记录
  * 时间：2022 年 5 月 25 日 -- 2022 年 5 月 27 日
  * 关键词：Windows, Github, Azure, 低代码

## 重要议题
  * 使用 Windows 创建混合工作流
  * 利用 GitHub 为项目赋能
  * 低代码平台助力更高效能
  * 利用 Azure 加速云原生应用现代化

## 使用 Windows 创建混合工作流
### WSL GUI 原生应用支持，以及 WSA 正式发布
在今年早些时候，Windows11 预览版推出 WSA（适用于 Android 的 Windows 子系统）的系统支持，这意味着现在 Windows 上原生支持 Android 应用程序的运行。

同时，WSL（适用于 Linux 的 Windows 子系统）取得新的进展。目前，WSL 已经作为单独的应用程序在 Microsoft Store 中可供下载，用户可按需独立下载包括 Debian、Ubuntu 在内的任一 Linux 子系统。另外，WSL2 已支持独立运行 Linux GUI 应用程序，这使得在 Linux 环境下进行完整、持续的项目开发成为可能。

所有的 Android 和 Linux 应用程序将独立显示在**开始**菜单中。

### Visual Studio 2022
全新的 Visual Studio 2022 现在是 64 位应用程序。这意味着，可以在不耗尽内存的情况下打开、编辑、运行和调试最大且最复杂的解决方案。重要更新如下述所示：
  * 原生支持 ARM64，可在 Windows on ARM 设备中运行
  * 集成了一个名为提交图的相对新的 Git 功能，可查看 Git 项目的**树状图**
  * 完全支持 .NET 6
  * Git 多存储库支持和行暂存支持

### Microsoft Store
Mcirosoft Store 已经删除所有转制应用等待名单，面向所有开发者开放，这意味着 Microsoft Store 现可接收包括 win32、PWA、UWP 在内的多种应用，并且**开发者收益 100% 归开发者**。

### PowerShell 7
PowerShell 7.x 是 PowerShell 的最新主版本，与 PowerShell 5 是并行版本，是跨平台、开源和 Windows 管理的完整工具，汇集了 Windows PowerShell 和 PowerShell Core。

## 利用 GitHub 为项目赋能
GitHub 面向企业用户和个人用户分别推出了几项功能，如下述所示：
  * GitHub Codespaces 和 github.dev
  * GitHub Copilot

### GitHub Codespaces 和 github.dev
Codespaces 现在已经开放给 GitHub Teams 和 GitHub Enterprise Cloud 上的所有人使用，可以为团队快速获得即用即付的托管开发环境。如果满足资格的用户，可以在仓库的首页的 Code 按钮，看到提示。遗憾的是，此功能暂未对个人用户的仓库开放。

对于个人用户，现在使用浏览器打开任意一个仓库，将链接中 github.com 的 com 替换为 dev，即可开启一个在线的 VSCode 编辑器，可以对工程代码进行查看和编辑。

### GitHub Copilot

## 相关文档
  1. 有关 WSL 运行 Linux GUI 应用的更多信息，可[点此](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps)了解。
  2. 有关 WSA 与 Visual Studio 2022 实现 Android 应用程序联合开发的更多信息，可[点此](https://learn.microsoft.com/zh-cn/shows/on-net/debug-android-apps-with-wsa-and-visual-studio-2022)了解。
  3. 有关 Microsoft Store 更新的更多细节，可[点此](https://blogs.windows.com/windowsdeveloper/2022/05/24/microsoft-store-grows-with-the-developer-community/)了解。
  4. 有关 PowerShell 7 的更多更新内容，可[点此](https://www.thomasmaurer.ch/2020/03/whats-new-in-powershell-7-check-it-out/)了解。
  5. 了解 GitHub 是什么？以及如何使用 GitHub 创建可溯源的项目工作流？可[点此](https://learn.microsoft.com/zh-cn/training/modules/introduction-to-github/)访问。
  6. 了解更多使用 GitHub Codespaces 进行开发的信息，可[点此](https://learn.microsoft.com/zh-cn/azure-sphere/app-development/container-codespaces)访问。