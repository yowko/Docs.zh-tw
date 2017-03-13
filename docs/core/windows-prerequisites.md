---
title: "Windows 上 .NET Core 的必要條件 | Microsoft Docs"
description: "了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。"
keywords: ".NET Core, Windows, 必要條件, 相依性, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 01/05/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: e374b924bf78d62227cb9607641130dfd9128186
ms.openlocfilehash: 6383a0ce253f6f7000ed8a81b29b9e1d58914acc
ms.lasthandoff: 03/06/2017

---

# <a name="prerequisites-for-net-core-on-windows"></a>Windows 上 .NET Core 的必要條件

此文章將說明您在 Windows 電腦上部署與執行 .NET Core 應用程式，以及使用 Visual Studio 來開發時，您需要哪些相依性。

## <a name="supported-windows-versions"></a>支援的 Windows 版本

下列 Windows 版本支援 .NET Core：

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (完整伺服器或 Server Core)
* Windows Server 2012 SP1 (完整伺服器或 Server Core)
* Windows Server 2012 R2 SP1 (完整伺服器或 Server Core)
* Windows Server 2016 (完整伺服器、Server Core 或 Nano Server)

您可以在 [.NET Core 1.0.0 版本資訊 (英文)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md) 中查看完整的[支援的作業系統 (英文)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md#rtm-platform-support)。

## <a name="net-core-dependencies"></a>.NET Core 的相依性

在 Windows 10 和 Windows Server 2016 之前的 Windows 版本上執行時，.NET Core 需要 Visual C++ 可轉散發套件。 如果您使用 .NET Core 安裝程式，會自動為您安裝此相依性。 不過，如果您是透過[安裝程式指令碼 (英文)](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/dotnet-install-script)安裝 .NET Core 或者部署獨立的 .NET Core 應用程式，您需要手動安裝[適用於 Visual Studio 2015 的 Visual C++ 可轉散發套件 (英文)](https://www.microsoft.com/en-us/download/details.aspx?id=48145)。

> [!NOTE]
> <em>僅適用於 Windows 7 和 Windows Server 2008 電腦：</em><br>
> 確定您的 Windows 安裝為最新狀態，而且包含已透過 Windows Update 安裝的 Hotfix [KB2533623](https://support.microsoft.com/en-us/kb/2533623)。

## <a name="prerequisites-with-visual-studio-2017"></a>使用 Visual Studio 2017 的必要條件

您可以使用 .NET Core SDK 以使用您選擇的任何編輯器來開發 .NET Core 應用程式。 不過，如果您想要在整合式開發環境中於 Windows 上開發 .NET Core 應用程式，您可以使用 [Visual Studio 2017](#visual-studio-2017)。

若要使用 Visual Studio 2017 開發 .NET Core 應用程式，您必須安裝最新版本的 Visual Studio 並選取 [.NET Core 跨平台開發] 工具組 (在 [其他工具組] 區段中)。

Visual Studio 2017 有許多種版本。 您可以免費下載 [Visual Studio Community 2017](https://www.visualstudio.com/vs/visual-studio-2017/#downloadvs) 開始使用。  若要深入了解 Visual Studio 安裝程序，請參閱 [Install Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio) (安裝 Visual Studio 2017)。

您可以在[版本資訊](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 的變更。

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546
