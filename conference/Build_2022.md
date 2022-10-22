# 微软开发者大会 2022（Microsoft Build 2022）会议记录
  * 时间：2022 年 5 月 25 日 -- 2022 年 5 月 27 日
  * 关键词：Windows, Github, Azure, 低代码

## 重点议题
  * 使用 Windows 创建混合工作流
  * 利用 GitHub 为项目赋能
  * 低代码平台助力更高效能
  * 利用 Azure 加速云原生应用现代化

## 使用 Windows 创建混合工作流
### WSL GUI 原生应用支持，以及 WSA 正式发布
在今年早些时候，Windows11 预览版推出 WSA（适用于 Android 的 Windows 子系统）的系统支持，这意味着现在 Windows 上原生支持 Android 应用程序的运行。

同时，WSL（适用于 Linux 的 Windows 子系统）取得新的进展。目前，WSL 已经作为单独的应用程序在 Microsoft Store 中可供下载，用户可按需独立下载包括 Debian、Ubuntu 在内的任一 Linux 子系统。另外，WSL2 已支持独立运行 Linux GUI 应用程序，这使得在 Linux 环境下进行完整、持续的项目开发成为可能。

所有安装的 Android 和 Linux 应用程序将独立显示在**开始**菜单中。

### Visual Studio 2022
全新的 Visual Studio 2022 现在是 **64 位应用程序**。这意味着，可以在不耗尽内存的情况下打开、编辑、运行和调试最大且最复杂的解决方案。重要更新如下述所示：
  * 原生支持 ARM64，可在 Windows on ARM 设备中运行
  * 集成了一个名为提交图的相对新的 Git 功能，可查看 Git 项目的**树状图**
  * 完全支持 .NET 6
  * Git 多存储库支持和行暂存支持

### ARM 设备的通用开发
Windows 现已支持下列应用的本地 ARM 支持和原生应用开发：
  * Visual Studio 2022
  * Visual Studio Code
  * .NET 和 .NET Framework
  * WSA
  * WSL
  * [Windows 终端](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=zh-hk&gl=hk)
  * Git
  * Project Volterra，基于 ARM 的主机，可组成阵列用于深度学习项目的开发

Project Volterra 使开发人员能够利用强大的集成神经处理单元 (NPU) 来构建执行本地 AI 加速工作负载的应用程序。Windows 基于 Project Volterra 通过 Hybrid Loop 模式在客户端和云之间动态转移模型 AI 应用推理时的负载。
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

对于个人用户，现在使用浏览器打开任意一个仓库，将链接中 github.com 的 com 替换为 dev，即可开启一个在线的 **VSCode** 编辑器，可以对工程代码进行查看和编辑。另外也支持快捷键，在 GitHub 仓库页面点击键盘的 “。” 键，可以直接打开。

### GitHub Copilot
Copilot 是一款代码补全工具，它可以根据上下文语意自动生成代码，或者注释，亦可根据注释生成代码。已于目前正式上线，付费，或学生和热门开源项目维护者免费。

## 低代码平台助力更高效能
Microsoft 的低代码平台为 Power 平台，这一平台的出现是为了实现领域专家与开发专家组成的融合团队高效沟通项目开发而设计的。Power 平台的更新包含下述内容：
  * Express Design 应用程序，可将手绘的内容、PPT，自动生成填写应用程序，包含 UI 和后端数据整理功能
  * Power Pages，允许任何人快速构建现代化商业网站，内置模板，构建网页就如同使用 135 编辑器进行微信推送的排版一样简单

## 利用 Azure 加速云原生应用现代化
### Hybrid Loop
Hybrid Loop 允许用户将混合应用程序在云和本地无缝运行，并动态调整在云、本地 CPU、本地 GPU 调整负载。对于混合应用程序而言，云被视为一种额外的计算资源，就像为 PC 赋能的核心除了 CPU 之外还有 GPU 一样。例如，这些类型的应用程序将能够在运行时决定是在客户端设备上还是在 Azure 云上进行 AI 推理。

此外，由于这些新应用程序中的大多数可能会包含一定程度的 AI，因此它们还可能利用 NPU（神经处理单元）或其他类型的 AI 硬件加速器。因此，可以编写混合应用程序，利用 Hybrid Loop 以利用本地设备的 CPU、GPU 和 NPU，并且根据需要或指示，还可以使用基于云的计算资源。

### Azure Kubernetes Service (AKS)
由于应用程序扩展到跨多个服务器部署的多个容器，因此对其进行操作变得更加复杂。为了管理这种复杂性，Kubernetes 提供了一个开放源代码 API，用于控制这些容器的运行方式和位置。

Kubernetes 会根据虚拟机的可用计算资源和每个容器的资源要求，协调一组虚拟机并安排容器在这些虚拟机上运行。负载可根据访问量进行动态的调整，而不必总是启用恒定组服务器资源。

Kubernetes 还会自动管理服务发现、合并负载均衡、跟踪资源分配并根据计算利用率进行缩放。此外，它还会检查单个资源的运行状态，并通过自动重启或复制容器使应用自行修复。这一切要归功于新发布的 Azure Container Apps 功能。

#### Azure Container Apps
Azure Container Apps 使你能够在无服务器平台上运行微服务和容器化应用程序。其常见的用途包括：
  * 部署 API 端点
  * 托管后台处理应用程序
  * 处理事件驱动的处理
  * 运行微服务

基于 Azure Container Apps 构建的应用程序可以根据以下特征动态扩展：
  * HTTP 流量
  * 事件驱动处理
  * CPU 或内存负载
  * 任何 [KEDA](https://keda.sh/docs/2.8/scalers/) 支持的缩放器

### 人工智能模型
利用 Azure 强大的计算能力，训练了 [Florence](https://www.microsoft.com/en-us/research/project/project-florence-vl/)，其具备了突破性的视觉识别能力。而与 OpenAI 合作，推出了：
  * [GPT](https://learn.microsoft.com/zh-cn/azure/cognitive-services/openai/concepts/models#gpt-3-models)，一个类人类语言生成的模型
  * [DALL-E](https://openai.com/blog/dall-e/)，一个对真实图像的生成与编辑的模型
  * [Codex](https://learn.microsoft.com/zh-cn/azure/cognitive-services/openai/how-to/work-with-code)，一个生成代码的模型

通过构建云原生应用程序，使用 AKS 可以用一种非常简单的手法加入这些模型，应用于客户端。

## 相关文档
  1. 有关 Build 2022 大会上对服务更新的更多内容，可[点此](https://news.microsoft.com/build-2022-book-of-news/)了解。
  2. 有关 WSL 运行 Linux GUI 应用的更多信息，可[点此](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps)了解。
  3. 有关 WSA 与 Visual Studio 2022 实现 Android 应用程序联合开发的更多信息，可[点此](https://learn.microsoft.com/zh-cn/shows/on-net/debug-android-apps-with-wsa-and-visual-studio-2022)了解。
  4. 有关 Microsoft Store 更新的更多细节，可[点此](https://blogs.windows.com/windowsdeveloper/2022/05/24/microsoft-store-grows-with-the-developer-community/)了解。
  5. 有关 PowerShell 7 的更多更新内容，可[点此](https://www.thomasmaurer.ch/2020/03/whats-new-in-powershell-7-check-it-out/)了解。
  6. 了解 GitHub 是什么？以及如何使用 GitHub 创建可溯源的项目工作流？可[点此](https://learn.microsoft.com/zh-cn/training/modules/introduction-to-github/)访问。
  7. 了解更多使用 GitHub Codespaces 进行开发的信息，可[点此](https://learn.microsoft.com/zh-cn/azure-sphere/app-development/container-codespaces)访问。
  8. 有关 Github Copilot 的更多消息，可以[点此](https://www.zhihu.com/question/470873369)了解。
  9. 有关 Power Pages 的更多内容，可以[点此](https://learn.microsoft.com/zh-cn/power-pages/introduction)了解。
  10. 有关 AKS 的更多内容，可[点此](https://azure.microsoft.com/zh-cn/topic/what-is-kubernetes/#overview)了解。
  11. 有关 Azure Container Apps 的更多内容，可[点此](https://learn.microsoft.com/en-us/azure/container-apps/overview)了解。
  12. 了解更多 Microsoft 训练的 AI 模型的案例，可[点此](https://learn.microsoft.com/zh-cn/azure/cognitive-services/openai/overview)访问。

