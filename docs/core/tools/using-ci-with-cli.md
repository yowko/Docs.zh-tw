---
title: "在持續整合 (CI) 中使用 .NET Core SDK 和工具 | Microsoft Docs"
description: "在持續整合 (CI) 中使用 .NET Core SDK 和工具"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5fb15297-a276-417f-8c4f-267281357769
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: dc68271dcca6a64bbcbeb487050e809fae40c8aa

---

# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>在持續整合 (CI) 中使用 .NET Core SDK 和工具

> [!WARNING]
> 本主題適用於 .NET Core 工具 Preview 2。 Visual Studio 2017 RC - .NET Core 工具 Preview 4 版本，請參閱[在持續整合 (CI) 中使用 .NET Core SDK 和工具 (工具 Preview 4)](../preview3/tools/using-ci-with-cli.md) 主題。

## <a name="overview"></a>概觀
本文件概述如何在組建伺服器上使用 .NET Core SDK 和其工具。 一般而言，在 CI 組建伺服器上，您會想要透過某種方式自動化安裝。 在理想狀況下，自動化應該不需要系統管理權限。 

SaaS CI 方案有數個選項。 本文件涵蓋兩個極常用的選項：[TravisCI](https://travis-ci.org/) 和 [AppVeyor](https://www.appveyor.com/)。 當然會有許多其他服務，但是安裝和使用機制應該類似。

## <a name="installation-options-for-ci-build-servers"></a>CI 組建伺服器的安裝選項

## <a name="using-the-native-installers"></a>使用原生安裝程式
如果使用需要系統管理權限的安裝程式不會造成問題，則可以使用每個平台的原生安裝程式來設定組建伺服器。 尤其是在 Linux 組建伺服器的情況下，這種方式有一個優勢就是自動安裝 SDK 執行所需的相依性。 原生安裝程式也會安裝整個系統版本的 SDK (這可能是所需的版本)；否則，您應該查看下面所述的[安裝程式指令碼用法](#using-the-installer-script)。 

這種方式的使用十分簡單。 針對 Linux，您可以選擇使用摘要套件管理員 (例如適用於 Ubuntu 的 `apt-get` 或適用於 CentOS 的 `yum`)，或使用套件本身 (即 DEB 或 RPM)。 前者需要設定包含套件的摘要。

針對 Windows 平台，您可以使用 MSI。 

您可以在指向最新穩定版本的 [.NET Core 入門頁面](https://aka.ms/dotnetcoregs)中找到所有二進位檔。 如果您想要使用較新 (但可能不穩定) 版本或最新版本，則可以使用 [CLI 存放庫](https://github.com/dotnet/cli)中的連結。 

## <a name="using-the-installer-script"></a>使用安裝程式指令碼
使用安裝程式指令碼可以在您的組建伺服器上進行非系統管理安裝。 它也可以極為輕鬆地自動化。 指令碼本身將會下載所需的 ZIP/tarball 檔案，並將其解壓縮；它也會將本機電腦上的安裝位置新增至 PATH，因此可在安裝後立即叫用工具。 

在建置開頭，可以輕鬆地自動化安裝程式指令碼，以擷取和安裝所需的 SDK 版本。 「所需版本」就是正在建置的應用程式所需的版本。 您可以選擇安裝路徑，以在本機安裝 SDK，然後在建置完成後清除。 這會將其他封裝和不可部分完成性帶到建置流程。 

安裝指令碼參考位於 [dotnet-install](dotnet-install-script.md) 文件中。 

### <a name="dealing-with-the-dependencies"></a>處理相依性
使用安裝程式指令碼即表示不會自動安裝原生相依性，而且您必須在正在安裝的作業系統上還未安裝它們時進行安裝。 您可以在 [CLI 存放庫](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)中看到必要條件清單。 

## <a name="ci-services-setup-examples"></a>CI 服務設定範例
下列各節顯示使用所提及 CI SaaS 供應項目之組態的範例。 

### <a name="travisci"></a>TravisCI

[travis-ci](https://travis-ci.org/) 可以設定成使用 `csharp` 語言和 `dotnet` 索引鍵來安裝 .NET Core SDK。

只要使用：

```yaml
dotnet: 1.0.0-preview2-003121
```

Travis 可以在建置矩陣中執行 `osx` (OS X 10.11) 和 `linux` (Ubuntu 14.04) 工作，如需詳細資訊，請參閱[範例 .travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml)。

### <a name="appveyor"></a>AppVeyor

[appveyor.com ci](https://www.appveyor.com/) 已將 .NET Core SDK preview2 安裝在建置背景工作映像 `Visual Studio 2015` 中。

只要使用：

```yaml
os: Visual Studio 2015
```

可以安裝特定版本的 .NET Core SDK，如需詳細資訊，請參閱[範例 appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml)。 

在範例中，會下載 .NET Core SDK 二進位檔，並在子目錄中進行解壓縮，然後將其新增至 `PATH` 環境變數。

可以新增建置矩陣，以執行與多個 .NET Core SDK 版本的整合測試。

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.0-preview2-003121
    - CLI_VERSION: Latest

install:
  # .NET Core SDK binaries
  - ps: $url = "https://dotnetcli.blob.core.windows.net/dotnet/preview/Binaries/$($env:CLI_VERSION)/dotnet-dev-win-x64.$($env:CLI_VERSION.ToLower()).zip"
  # follow normal installation from binaries
```




<!--HONumber=Jan17_HO3-->


