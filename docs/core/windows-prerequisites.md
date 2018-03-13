---
title: "Windows 上 .NET Core 的必要條件"
description: "了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。"
author: JRAlexander
ms.author: johalex
ms.date: 03/02/2018
ms.topic: article
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 48102f3fb7fa6e93238eefff0e7f1ecbed4d8409
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows 上 .NET Core 的必要條件

本文會說明在 Windows 開發 .NET Core 應用程式所需的相依性。 支援的作業系統版本和跟隨的相依性，適用於在 Windows 開發 .NET Core 應用程式的三種方式：

* [命令列](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>.NET Core 支援的 Windows 版本

下列版本支援 .NET Core：

* Windows 7 SP1
* Windows 8.1
* Windows 10 年度更新 (1607 版) 或更新版本
* Windows Server 2008 R2 SP1 (完整伺服器或 Server Core)
* Windows Server 2012 SP1 (完整伺服器或 Server Core)
* Windows Server 2012 R2 (完整伺服器或 Server Core)
* Windows Server 2016 (完整伺服器、Server Core 或 Nano Server)

如需 .NET Core 2.x 支援的作業系統完整清單，請參閱 [.NET Core 2.x - 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。

如需 .NET Core 1.x 支援的作業系統完整清單，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。

## <a name="net-core-dependencies"></a>.NET Core 的相依性

在 Windows 10 和 Windows Server 2016 之前的 Windows 版本上執行時，.NET Core 1.1 和舊版本需要 Visual C++ 可轉散發套件。 .NET Core 安裝程式會自動安裝此相依性。

必須手動安裝 [Microsoft Visual C++ 2015 可轉散發套件 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) 的時機：

* 使用[安裝程式指令碼](./tools/dotnet-install-script.md)安裝 .NET Core。
* 部署獨立的 .NET Core 應用程式。
* 從來源建置產品。
* 透過 *.zip* 檔案安裝 .NET Core。 這可以包含組建/CI/CD 伺服器。

> [!NOTE]
> *僅針對 Windows 7 和 Windows Server 2008 電腦：*：確定您的 Windows 安裝為最新狀態，而且包含已透過 Windows Update 安裝的 Hotfix [KB2533623](https://support.microsoft.com/help/2533623)。

## <a name="prerequisites-with-visual-studio-2017"></a>使用 Visual Studio 2017 的必要條件

您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。 [Visual Studio 2017](#visual-studio-2017) 為 Windows 上的 .NET Core 應用程式提供整合式開發環境。

您可以在[版本資訊](/visualstudio/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 的變更。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

若要在 Visual Studio 2017 中開發 .NET Core 2.x 應用程式：

 1. [下載並安裝 Visual Studio 2017 15.3.0 版本或更高版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-15-3-workloads.jpg)

安裝 **.NET Core 跨平台開發**工具集之後，Visual Studio 2017 預設使用 .NET Core 1.x。 安裝 .NET Core 2.x SDK 以取得 Visual Studio 2017 中的 .NET Core 2.x 支援。

 2. 安裝 [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core)。
 3. 使用下列指示將現有或新的 .NET Core 1.x 專案目標重定到 .NET Core 2.x：
    * 在 [專案] 功能表上，選擇 [屬性]。
    * 在 [目標 Framework] 選取功能表中，將值設為 **.NET Core 2.0**。

![螢幕擷取畫面：選取 ".NET Core 2.0" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/Targeting-dotnetCore2.png)

一旦安裝 .NET Core 2.x SDK，Visual Studio 2017 預設會使用 .NET Core SDK 2.x，而且支援下列動作：

* 開啟、建置及執行現有的 .NET Core 1.x 專案。
* 將 .NET Core 1.x 專案重定目標至 .NET Core 2.x、建置和執行。
* 建立新的 .NET Core 2.x 專案。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

若要使用 Visual Studio 開發 .NET Core 1.x 應用程式，請[下載並安裝 Visual Studio 2017 RTM (版本 15.0.26228.4) 或更高版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> 有可能使用 Visual Studio 2015 開發 .NET Core 1.x，但不建議為下列原因而如此做：
  > * .NET Core 工具是預覽版本，不受支援。
  > * 專案是以 project.json 為基礎，已被取代。
>
> 如需專案格式變更的詳細資訊，請參閱[變更的高階概觀](./tools/cli-msbuild-architecture.md)。
---

> [!TIP]
> 確認 Visual Studio 2017 版本：
>
> * 在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]**。
> * 在 [關於 Microsoft Visual Studio] 對話方塊中，確認版本號碼。
>   * 若為 .NET Core 2.1 預覽 1 應用程式，需要 Visual Studio 2017 版本 15.6 預覽 6 或更高版本。
>   * 若為 .NET Core 2.0 應用程式，需要 Visual Studio 2017 版本 15.3 或更高版本。
>   * 若為 .NET Core 1.x 應用程式，需要 Visual Studio 2017 版本 15.0 或更高版本。
