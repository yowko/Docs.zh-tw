---
title: ".NET Core 的必要條件 (Preview 3 工具)"
description: ".NET Core 的必要條件 (Preview 3 工具)"
keywords: .NET, .NET Core
author: billwagner
ms.author: wiwagn
ms.date: 09/15/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: 07b62bd7163193eff8dc8f61fda7a45a924bba2b
ms.openlocfilehash: ee4ccba7c06f0a7f67e3fe59c885febf895235fd

---

# <a name="prerequisites-for-windows-development-preview-3-tooling"></a>Windows 開發的必要條件 (Preview 3 工具)

使用 Visual Studio 在 Windows 上進行 .NET Core 開發需具備︰

* 支援的 Windows 用戶端或作業系統版本。
* Visual Studio 2017 RC 或更新版本
* .NET Core 工具 Preview 3

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

您可以使用使用 .NET Core 的命令列工具，透過任何編輯器開發 .NET Core 應用程式，但如果您想要使用 Visual Studio 和 .NET Core 工具 Preview 3，就需要 Visual Studio 2017 RC 或更新版本。 您可以免費下載 [Visual Studio Community 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/)。 

確認您執行的是 Visual Studio 2017 RC：

* 在 [說明] 功能表上，選擇 [關於 Microsoft Visual Studio]。
* 在 [關於 Microsoft Visual Studio] 對話方塊中，版本號碼應為 15.0.25831.1 或更高版本。

您可以在[版本資訊](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 RC 的變更。

請確定您已在安裝期間安裝「.NET Core 和 Docker (Preview)」工作負載。 如果未指定，可以再次執行安裝程式並加以選取。



<!--HONumber=Nov16_HO3-->


