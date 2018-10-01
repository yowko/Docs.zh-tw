---
title: Windows 上 .NET Core 的必要條件
description: 了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。
author: mairaw
ms.author: mairaw
ms.date: 08/31/2018
ms.openlocfilehash: 477d303b50495070ba3a3540188deb274dd9f510
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44179490"
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
* Windows Server 2016 或更新版本 (完整伺服器、Server Core 或 Nano Server)

## <a name="net-core-supported-operating-systems"></a>.NET core 支援的作業系統

以下文件有 .NET Core 所支援每個版本作業系統的完整清單：

* [.NET core 2.1 - 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) \(英文\)
* [.NET core 2.0 - 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) \(英文\)
* [.NET core 1.x - 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) \(英文\)

## <a name="net-core-dependencies"></a>.NET Core 的相依性

在 Windows 10 和 Windows Server 2016 之前的 Windows 版本上執行時，.NET Core 1.1 和舊版本需要 Visual C++ 可轉散發套件。 .NET Core 安裝程式會自動安裝此相依性。

必須手動安裝 [Microsoft Visual C++ 2015 可轉散發套件 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) 的時機：

* 使用[安裝程式指令碼](./tools/dotnet-install-script.md)安裝 .NET Core。
* 部署獨立的 .NET Core 應用程式。
* 從來源建置產品。
* 透過 *.zip* 檔案安裝 .NET Core。 這可以包含組建/CI/CD 伺服器。

> [!NOTE]
> **適用於 Windows 8.1 和更早版本，或 Windows Server 2012 R2 和更早版本：**
>
> 請確定您的 Windows 安裝處於最新狀態，且包含 [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) \(機器翻譯\) (可透過 Windows Update 安裝)。 如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **適用於 Windows 7 或 Windows Server 2008 R2：**
>
> 除了 KB2999226，請確定您也已經安裝 [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)。 如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`。

## <a name="prerequisites-with-visual-studio-2017"></a>使用 Visual Studio 2017 的必要條件

您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。 [Visual Studio 2017](#visual-studio-2017) 為 Windows 上的 .NET Core 應用程式提供整合式開發環境。

您可以在[版本資訊](/visualstudio/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 的變更。

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

若要在 Visual Studio 2017 中開發 .NET Core 2.1 應用程式：

 1. [下載並安裝 Visual Studio 2017 15.7.0 版本或更新版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-15-8-workloads.jpg)

安裝 [.NET Core 跨平台開發] 工具組之後，根據預設，Visual Studio 2017 15.7 會使用 .NET Core 2.0 SDK，而 Visual Studio 2017 15.8 會使用 2.1 SDK。

 2. 如果您使用 Visual Studio 2017 15.7，請安裝 [.NET Core 2.1 SDK](https://www.microsoft.com/net/download/core) 或升級為 Visual Studio 2017 15.8。

 3. 使用下列指示，將現有或新的 .NET Core 專案目標重定為 .NET Core 2.1：
    * 在 [專案] 功能表上，選擇 [屬性]。
    * 在 [目標 Framework] 選取功能表中，將值設為 **.NET Core 2.1**。

![螢幕擷取畫面：選取 ".NET Core 2.0" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/Targeting-dotnetCore2.png)

一旦使用 .NET Core 2.1 SDK 設定 Visual Studio，您可以執行下列動作：

* 開啟、建置及執行現有的 .NET Core 1.x 和 2.x 專案。
* 將 .NET Core 1.x 和 2.0 專案目標重定為 .NET Core 2.1、建置和執行。
* 建立新的 .NET Core 2.1 專案。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

若要在 Visual Studio 2017 中開發 .NET Core 2.0 應用程式：

 1. [下載並安裝 Visual Studio 2017 15.3.0 版本或更高版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-15-3-workloads.jpg)

安裝 **.NET Core 跨平台開發**工具集之後，Visual Studio 2017 預設使用 .NET Core 1.x。 安裝 .NET Core 2.0 SDK 以取得 Visual Studio 2017 中的 .NET Core 2.0 支援。

 2. 安裝 [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0)。
 3. 使用下列指示將現有或新的 .NET Core 1.x 專案目標重定為 .NET Core 2.0：
    * 在 [專案] 功能表上，選擇 [屬性]。
    * 在 [目標 Framework] 選取功能表中，將值設為 **.NET Core 2.0**。

![螢幕擷取畫面：選取 ".NET Core 2.0" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/Targeting-dotnetCore2.png)

一旦安裝 .NET Core 2.0 SDK，Visual Studio 2017 預設會使用 .NET Core SDK 2.0，而且支援下列動作：

* 開啟、建置及執行現有的 .NET Core 1.x 專案。
* 將 .NET Core 1.x 專案目標重定為 .NET Core 2.0、建置和執行。
* 建立新的 .NET Core 2.0 專案。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

若要使用 Visual Studio 開發 .NET Core 1.x 應用程式，請[下載並安裝 Visual Studio 2017](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> 有可能使用 Visual Studio 2015 開發 .NET Core 1.x，但不建議為下列原因而如此做：
  > * .NET Core 工具是預覽版本，不受支援。
  > * 專案是以 project.json 為基礎，已被取代。
>
> 如需專案格式變更的詳細資訊，請參閱[變更的高階概觀](./tools/cli-msbuild-architecture.md)。
---

<a name="vs-mapping"></a>

> [!TIP]
> 確認 Visual Studio 2017 版本：
>
> * 在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]**。
> * 在 [關於 Microsoft Visual Studio] 對話方塊中，確認版本號碼。
>   * 若為 .NET Core 2.2 Preview 1 應用程式，需要 Visual Studio 2017 15.9 版 (目前處於預覽版) 或更新版本。
>   * 若為 .NET Core 2.1 應用程式，需要 Visual Studio 2017 15.7 版或更新版本。
>   * 若為 .NET Core 2.0 應用程式，需要 Visual Studio 2017 版本 15.3 或更高版本。
>   * 若為 .NET Core 1.x 應用程式，需要 Visual Studio 2017 版本 15.0 或更高版本。
