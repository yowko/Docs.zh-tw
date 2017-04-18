---
title: "Windows 上 .NET Core 的必要條件 | Microsoft Docs"
description: "了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。"
keywords: ".NET Core, Windows, 必要條件, 相依性, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: ff143583ba62fc1d82561e739a75107e50ebee88
ms.openlocfilehash: 13947fd81940c1ccb606cb4cd765dc230fe95c0f
ms.lasthandoff: 03/20/2017

---

# <a name="prerequisites-for-net-core-on-windows"></a>Windows 上 .NET Core 的必要條件

本文將說明您在 Windows 電腦上部署與執行 .NET Core 應用程式，以及使用 Visual Studio 來開發時，您需要哪些相依性。

## <a name="supported-windows-versions"></a>支援的 Windows 版本

下列 Windows 版本支援 .NET Core：

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (完整伺服器或 Server Core)
* Windows Server 2012 SP1 (完整伺服器或 Server Core)
* Windows Server 2012 R2 SP1 (完整伺服器或 Server Core)
* Windows Server 2016 (完整伺服器、Server Core 或 Nano Server)

如需完整的支援作業系統，請參閱 [.NET Core 版本資訊](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md)。

## <a name="net-core-dependencies"></a>.NET Core 的相依性

在 Windows 10 和 Windows Server 2016 之前的 Windows 版本上執行時，.NET Core 需要 Visual C++ 可轉散發套件。 如果您使用 .NET Core 安裝程式，會自動為您安裝此相依性。 不過，如果您是透過[安裝程式指令碼 (英文)](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/dotnet-install-script)安裝 .NET Core 或者部署獨立的 .NET Core 應用程式，您需要手動安裝[適用於 Visual Studio 2015 的 Visual C++ 可轉散發套件 (英文)](https://www.microsoft.com/en-us/download/details.aspx?id=48145)。

> [!NOTE]
> <em>僅適用於 Windows 7 和 Windows Server 2008 電腦：</em><br>
> 確定您的 Windows 安裝為最新狀態，而且包含已透過 Windows Update 安裝的 Hotfix [KB2533623](https://support.microsoft.com/en-us/kb/2533623)。

## <a name="prerequisites-with-visual-studio-2017"></a>使用 Visual Studio 2017 的必要條件

您可以使用 .NET Core SDK 以使用您選擇的任何編輯器來開發 .NET Core 應用程式。 不過，如果您想要在整合式開發環境中於 Windows 上開發 .NET Core 應用程式，您可以使用 [Visual Studio 2017](#visual-studio-2017)。

> [!IMPORTANT]
> 即使如此，您還是可以使用 Visual Studio 2015 搭配預覽版本的 .NET Core 工具來開發，但這些專案將以 *project.json* 為基礎，而這目前已被取代。 Visual Studio 2017 使用以 MSBuild 為基礎的專案檔案。 如需格式變更的詳細資訊，請參閱[變更的高階概觀](./tools/cli-msbuild-architecture.md)。

若要使用 Visual Studio 2017 開發 .NET Core 應用程式，您必須安裝最新版本的 Visual Studio 並選取 [.NET Core 跨平台開發] 工具組 (在 [其他工具組] 區段中)。
![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs_workloads.jpg)

Visual Studio 2017 有許多種版本。 您可以免費下載 [Visual Studio Community 2017](https://www.visualstudio.com/downloads/) 開始使用。  若要深入了解 Visual Studio 安裝程序，請參閱 [Install Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio) (安裝 Visual Studio 2017)。

若要確認您是否正在執行最新版本的 Visual Studio 2017，請執行下列動作︰

* 在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]**。
* 在 **[關於 Microsoft Visual Studio]** 對話方塊中，版本號碼應為 15.0.26228.4 或更高版本。

您可以在[版本資訊](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 的變更。

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546
