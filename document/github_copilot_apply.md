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
# 在 VS code 上使用 GitHub Copilot Free

GitHub Copilot 是一款用于开发的 AI 工具，其具备聊天、代码自动建议、错误检查和解释等功能，并允许切换包括 GPT-4o、GPT-o1 在内的多个 AI 模型。GiHub Copilot 现已被集成到 Visual Stuio、Visual Studio Code、Xcode、Jetbrain IDEs 等集成开发环境中，你可以按需在受支持的 IDE 扩展应用商店中安装扩展以启用该功能。本文档将介绍如何申请 GitHub Copilot 免费版本，若要比较免费版本和付费版本的区别，请[点此](https://github.com/features/copilot/plans?utm_campaign=launch__reactor_SegmentFault&utm_medium=blog&utm_source=topcopilotfree#)查看。

## 先决条件

  * 已安装 [Visual Studio Code](https://apps.microsoft.com/detail/xp9khm4bk9fz7q?launch=true&mode=full&hl=zh-cn&gl=cn&ocid=bingwebsearch)，免费版本的 Copilot 仅兼容 Visual Studio Code；
  * 已注册的 [GitHub 账户](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)。

## 申请步骤

请访问 [GitHub Copilot](https://github.com/features/copilot?utm_campaign=launch__reactor_SegmentFault&utm_medium=blog&utm_source=topcopilotfree) 支持页面，并登录你的 GitHub 账户。

一旦登录 GitHub 账户，请点击 [Get started for free](https://github.com/copilot?utm_campaign=launch__reactor_SegmentFault&utm_medium=blog&utm_source=topcopilotfree)，并按照指引激活 GitHub Copilot。

在完成激活后，你应该可以在 [GitHub 个人主页设置](https://github.com/settings/profile)中看到 Copilot 的相关设置，如下图所示。

<div align='center'><img src='../Picture\dc\屏幕截图 2024-12-21 124719.png' width='200px'></div>

确保允许 [GitHub Copilot 在 IDE 中提供建议](https://docs.github.com/en/copilot/using-github-copilot/getting-code-suggestions-in-your-ide-with-github-copilot)处于打开状态，如下图所示。

<div align='center'><img src='../Picture\dc\屏幕截图 2024-12-21 125317.png' width='700px'></div>

强烈推荐允许匹配公共代码的建议（可选），并允许 GitHub 使用数据进行产品改进（可选），以便促进开源社区的发展。若你需要 GitHub Copilot 具备联网搜索能力，请启用 Copilot 访问 Bing；若你需要使用最新的 Claude 3.5 Sonnet 模型（早期预览），请打开 “Anthropic Claude 3.5 Sonnet in Copilot”。

一旦完成上述步骤，则 GitHub Copilot 已被激活。你需要在 VS Code 扩展应用商店中搜索并安装 [GitHub Copilot - Your AI pair programmer](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)，如果出现如下图的按钮，则你可以在 VS Code 中使用 Copilot。

<div align='center'><img src='../Picture\dc\屏幕截图 2024-12-21 130658.png' width='600px'></div>

## 相关文档

  * 如要了解如何使用 GitHub Copilot，请[点此](https://docs.github.com/zh/copilot/using-github-copilot/best-practices-for-using-github-copilot)访问；
  * 请[点此](https://docs.github.com/zh/copilot/responsible-use-of-github-copilot-features/responsible-use-of-github-copilot-chat-in-your-ide)参阅使用 GitHub Copilot 聊天功能的安全须知。