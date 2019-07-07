---
title: Windows 上 .NET Core 的必要條件
description: 了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 9c4c15a08e0988955ecdf442307059868cb377d1
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539360"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows 上 .NET Core 的必要條件

本文會說明支援的 OS 版本，以便在 Windows 上執行 .NET Core 應用程式。 支援的作業系統版本和跟隨的相依性，適用於在 Windows 開發 .NET Core 應用程式的三種方式：

* [命令列](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

此外，如果您正在使用 Visual Studio 2017 在 Windows 上進行開發，則[使用 Visual Studio 2017 的必要條件](#prerequisites-with-visual-studio-2017)一節將詳細介紹 .NET Core 開發支援的最低版本。

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

* [.NET Core 3.0 (預覽)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

如需下載連結和詳細資訊，請參閱 [NET 下載](https://dotnet.microsoft.com/download)以下載最新版本或 [.NET 下載封存](https://dotnet.microsoft.com/download/archives#dotnet-core) (針對舊版本)。

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
> 請確定您的 Windows 安裝處於最新狀態，且包含 [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows) \(機器翻譯\) (可透過 Windows Update 安裝)。 如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **適用於 Windows 7 或 Windows Server 2008 R2：**
>
> 除了 KB2999226，請確定您也已經安裝 [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)。 如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`。

## <a name="prerequisites-for-net-core-30-preview-3"></a>.NET Core 3.0 Preview 3 的先決條件

.NET Core 3.0 Preview 3 與其他版本的 .NET Core 具有相同的先決條件。 不過，如果您想要使用 Visual Studio 建立 .NET Core 3.0 專案，則必須使用 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 Visual Studio 2019 能與其他版本的 Visual Studio 並行安裝，而不會相互衝突。

## <a name="prerequisites-with-visual-studio-2017"></a>使用 Visual Studio 2017 的必要條件
    
您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。 Visual Studio 2017 可為 Windows 上的 .NET Core 應用程式提供整合式開發環境。

您可以在[版本資訊](/visualstudio/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 的變更。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

若要在 Visual Studio 2017 中開發使用 .NET Core 2.2 SDK 的 .NET Core 應用程式：

 1. [下載並安裝 Visual Studio 2017 15.9.0 版本或更新版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發]  工作負載 (在 [其他工具組]  區段)。

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-2017-workloads.jpg)

安裝 **.NET Core 跨平台開發**工具集之後，Visual Studio 通常會安裝舊版的 .NET Core SDK。
例如，安裝工作負載之後，Visual Studio 2017 15.9 預設會使用 .NET Core 2.1 SDK。

若要更新 Visual Studio 以使用 .NET Core 2.2 SDK：

 1. 安裝 [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)。

 1. 如果您希望專案使用最新的 .NET Core 執行階段，請使用下列指示將現有或新的 .NET Core 專案目標重新設定為 .NET Core 2.2：

    * 在 [ **專案** ] 功能表上，選擇 [ **屬性**]。
    * 在 [目標 Framework]  選取功能表中，將值設為 **.NET Core 2.2**。

![螢幕擷取畫面：選取 ".NET Core 2.2" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/targeting-dotnet-core.jpg)

一旦使用 .NET Core 2.2 SDK 設定 Visual Studio，您可以執行下列動作：

* 開啟、建置及執行現有的 .NET Core 1.x 和 2.x 專案。
* 將 .NET Core 1.x 和 2.x 專案目標重新設定為 .NET Core 2.2、建置和執行。
* 建立新的 .NET Core 2.2 專案。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

若要使用 Visual Studio 開發 .NET Core 1.x 應用程式，請[下載並安裝 Visual Studio 2017](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發]  工作負載 (在 [其他工具組]  區段)。

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> 有可能使用 Visual Studio 2015 開發 .NET Core 1.x，但不建議為下列原因而如此做：
  > * .NET Core 工具是預覽版本，不受支援。
  > * 專案是以 project.json 為基礎，已被取代。
>
> 如需專案格式變更的詳細資訊，請參閱[變更的高階概觀](./tools/cli-msbuild-architecture.md)。

---

<a name="vs-mapping"></a>

> [!TIP]
> 確認 Visual Studio 版本：
>
> * 在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]** 。
> * 在 [關於 Microsoft Visual Studio]  對話方塊中，確認版本號碼。
>   * 針對 .NET Core 3.0 Preview 3 應用程式，需要 Visual Studio 2019 16.0 版或更新版本。
>   * 若為 .NET Core 2.2 應用程式，需要 Visual Studio 2017 15.9 版或更新版本。
>   * 若為 .NET Core 2.1 應用程式，需要 Visual Studio 2017 15.7 版或更新版本。
>   * 若為 .NET Core 1.x 應用程式，需要 Visual Studio 2017 版本 15.0 或更高版本。
