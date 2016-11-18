---
title: ".NET Core 的必要條件"
description: ".NET Core 的必要條件"
keywords: .NET, .NET Core
author: billwagner
manager: wpickett
ms.date: 09/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: 130b94a745b0e3222e205d8af26194239130ec9c
ms.openlocfilehash: 2e6483b3f1b8b9e1f36a0f4f7377319871fd5674

---

# <a name="prerequisites-for-windows-development"></a>Windows 開發的必要條件

使用 Visual Studio 在 Windows 上進行 .NET Core 開發需具備︰

* 支援的 Windows 用戶端或作業系統版本。
* Visual Studio 2015 Update 3.3 或更新版
* Visual Studio 的 NuGet 管理員擴充功能
* .NET Core 工具 Preview 2

## <a name="supported-windows-versions"></a>支援的 Windows 版本

.NET Core 支援下列 Windows 版本：

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (完整伺服器或 Server Core)
* Windows Server 2012 SP1 (完整伺服器或 Server Core)
* Windows Server 2012 R2 SP1 (完整伺服器或 Server Core)
* Windows Server 2016 (完整伺服器、Server Core 或 Nano Server)

您可以在 [.NET Core Release Notes](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md) (.NET Core 版本資訊) 中查看完整的[支援作業系統](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md#rtm-platform-support)。

## <a name="net-core-dependencies"></a>.NET Core 的相依性

在 Windows 上執行 .NET Core 時，需要 VC++ 可轉散發套件。 .NET Core 安裝程式會為您進行這項安裝。 如果您要透過安裝程式指令碼 (`dotnet-install.ps1`) 安裝 .NET Core，則必須手動安裝 Visual C++ 可轉散發套件。 

Visual C++ 可轉散發套件的版本與 Windows 版本不同。

* Windows 10
    * [適用於 Visual Studio 2015 的 Visual C++ 可轉散發套件](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
* Windows 7+ (不含 Windows 10)
    * 請確定您的 Windows 安裝為最新狀態，而且包含已透過 Windows Update 安裝的 Hotfix [KB2533623](https://support.microsoft.com/en-us/kb/2533623)。
    * [通用 CRT 更新](https://www.microsoft.com/en-us/download/details.aspx?id=48234) (您可以在[這篇部落格文章](https://blogs.msdn.microsoft.com/vcblog/2015/03/03/introducing-the-universal-crt/)中取得通用 CRT 功能的詳細資訊)

## <a name="visual-studio"></a>Visual Studio

您需具備 Visual Studio 2015 來開發 .NET Core 應用程式。 您可以免費下載 [Visual Studio Community 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs)。 

確認您是執行 [Visual Studio 2015 Update 3.3](https://msdn.microsoft.com/library/mt752379.aspx)：

* 在 [說明] 功能表上，選擇 [關於 Microsoft Visual Studio]。
* 在 [關於 Microsoft Visual Studio] 對話方塊中，版本號碼應為 14.0.25424.00 或更高版本，並包含 "Update 3"。
* 如果您沒有 Update 3，則必須先下載並安裝 [Visual Studio 2015 Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)。
* 如果您有 Update 3，但版本號碼小於 14.0.25424.00，則必須下載並安裝 [Visual Studio 2015 Update 3.3](https://msdn.microsoft.com/library/mt752379.aspx)。

您可以在[版本資訊](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)中，進一步了解 Update 3 的變更。

## <a name="nuget-manager-extension-for-visual-studio"></a>Visual Studio 的 NuGet 管理員擴充功能

NuGet 是 Microsoft 開發平台 (包括 .NET Core) 的封裝管理員。 您需具備 [NuGet 3.5.0](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) 或更高版本，來建置 .NET Core 應用程式。

## <a name="net-core-tools-for-visual-studio-2015"></a>適用於 Visual Studio 2015 的 .NET Core 工具

下載並安裝 [.NET Core 1.0.1 - VS 2015 工具 Preview 2][SDK]。 

.NET Core 工具套件會安裝 .NET Core、專案範本和其他適用於 Visual Studio 2015 的工具。

> [!NOTE]
目前，您無法下載適用於 [.NET Core 1.0.1 - VS 2015 工具 Preview 2][SDK] 的離線安裝程式。 因此，您必須改為下載[一般啟動載入器][SDK]並使用命令列選項 (例如 `/layout c:\path`) 來執行，以取得離線的版面配置。 之後，您只要從本機路徑執行可執行檔，即可將它做為離線安裝程式。 請注意，由於它是完整的版面配置，因此這個程序會下載所有支援的語言套件，大小約 1 GB。

[SDK]: https://go.microsoft.com/fwlink/?LinkID=827546



<!--HONumber=Nov16_HO3-->


