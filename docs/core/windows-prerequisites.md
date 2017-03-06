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
ms.sourcegitcommit: a8019c9fc25ef458aa555743e61cd83a3beb11ed
ms.openlocfilehash: b5c088da7d1155414a08995ae0d72154af891190
ms.lasthandoff: 01/24/2017

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

## <a name="prerequisites-with-visual-studio"></a>使用 Visual Studio 的必要條件

您可以使用 .NET Core SDK 以使用您選擇的任何編輯器來開發 .NET Core 應用程式。 不過，如果您想要使用 Visual Studio 在 Windows 上開發 .NET Core 應用程式，您可以使用下列兩種版本：

* [Visual Studio 2015](#visual-studio-2015)
* [Visual Studio 2017 RC](#visual-studio-2017-rc)

根據預設，使用 Visual Studio 2015 建立的專案會是 project.json 架構， 而以 Visual Studio 2017 RC 建立的專案則一律為 MSBuild 架構。 如需格式變更的詳細資訊，請參閱[變更的高階概觀](./preview3/tools/layering.md)。

### <a name="visual-studio-2015"></a>Visual Studio 2015

如果您想要使用 Visual Studio 2015 開發 .NET Core 應用程式，您將需要︰

* Visual Studio 2015 Update 3.3 或更新版本。

   Visual Studio 2015 有許多種[版本 (英文)](https://www.visualstudio.com/vs/compare)。 您可以免費下載 [Visual Studio Community 2015](https://www.visualstudio.com/downloads/) 開始使用。 

   若要確認您是否正在執行 [Visual Studio 2015 Update 3.3](https://msdn.microsoft.com/library/mt752379.aspx)，請執行下列動作︰

   * 在 [說明] 功能表上，選擇 [關於 Microsoft Visual Studio]。
   * 在 [關於 Microsoft Visual Studio] 對話方塊中，版本號碼應為 14.0.25424.00 或更高版本，並包含 "Update 3"。
   * 如果您沒有 Update 3，則必須先下載並安裝 [Visual Studio 2015 Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)。
   * 如果您有 Update 3，但版本號碼小於 14.0.25424.00，則必須下載並安裝 [Visual Studio 2015 Update 3.3](https://msdn.microsoft.com/library/mt752379.aspx)。

   您可以在[版本資訊](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)中，進一步了解 Update 3 的變更。

* Visual Studio 的 NuGet 管理員擴充功能

   NuGet 是 Microsoft 開發平台 (包括 .NET Core) 的封裝管理員。 您需要 [NuGet 3.5.0-beta](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) 或更高版本來建置 .NET Core 應用程式。

* .NET Core 工具 Preview 2

   下載並安裝 [.NET Core 1.0.1 - VS 2015 工具 Preview 2][sdk]。 

   .NET Core 工具套件會安裝 .NET Core、專案範本和其他適用於 Visual Studio 2015 的工具。

   > [!NOTE]
   > 目前，您無法下載適用於 [.NET Core 1.0.1 - VS 2015 工具 Preview 2][sdk] 的離線安裝程式。 因此，您必須改為下載[一般啟動載入器][sdk]並使用命令列選項 (例如 `/layout c:\path`) 來執行，以取得離線的版面配置。 之後，您只要從本機路徑執行可執行檔，即可將它做為離線安裝程式。 請注意，由於它是完整的版面配置，因此這個程序會下載所有支援的語言套件，大小約 1 GB。

### <a name="visual-studio-2017-rc"></a>Visual Studio 2017 RC

如果您想要使用 Visual Studio 2017 RC 開發 .NET Core 應用程式，您必須安裝最新版本的 Visual Studio RC 並選取 [.NET Core 和 Docker (預覽)] 工作負載。 

Visual Studio 2017 RC 有許多種版本。 您可以免費下載 [Visual Studio Community 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/#downloadvs) 來開始使用。  若要深入了解 Visual Studio 安裝程序，請參閱[安裝 Visual Studio 2017 RC (英文)](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio)。

若要確認您是否正在執行最新版本的 Visual Studio 2017 RC，請執行下列動作︰

* 在 [說明] 功能表上，選擇 [關於 Microsoft Visual Studio]。
* 在 [關於 Microsoft Visual Studio] 對話方塊中，版本號碼應為 15.0.26020.0 或更高版本。

您可以在[版本資訊](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 RC 的變更。

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546

