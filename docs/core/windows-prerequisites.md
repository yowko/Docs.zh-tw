---
title: Windows 上 .NET Core 的必要條件
description: 了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: b1557e6910cb6d0b6d7e2b3ce2aec97d3715fec7
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591676"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows 上 .NET Core 的必要條件

本文會說明支援的 OS 版本，以便在 Windows 上執行 .NET Core 應用程式。 支援的作業系統版本和跟隨的相依性，適用於在 Windows 開發 .NET Core 應用程式的三種方式：

* [命令列](./tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [Visual Studio Code](https://code.visualstudio.com/)

此外，如果您是使用 Visual Studio 在 Windows 上進行開發，[使用 Visual Studio 一節開發 .Net core 應用程式的必要條件](#prerequisites-to-develop-net-core-apps-with-visual-studio)會更詳細地說明 .net core 開發支援的最低版本。

## <a name="net-core-supported-operating-systems"></a>.NET core 支援的作業系統

以下文件有 .NET Core 所支援每個版本作業系統的完整清單：

* [.NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

如需下載連結和詳細資訊，請參閱 [NET 下載](https://dotnet.microsoft.com/download)以下載最新版本或 [.NET 下載封存](https://dotnet.microsoft.com/download/archives#dotnet-core) (針對舊版本)。

## <a name="net-core-dependencies"></a>.NET Core 的相依性

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

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a>使用 Visual Studio 開發 .NET Core 應用程式的必要條件
    
雖然您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式，但 Visual Studio 2017 和更新版本為 Windows 上的 .NET Core 應用程式提供整合式開發環境。

<a name="vs-mapping"></a>

每個 .NET Core 版本都具有所需 Visual Studio 的最低版本。 確認 Visual Studio 版本：

* 在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]** 。
* 在 [關於 Microsoft Visual Studio] 對話方塊中，確認版本號碼。

下表列出每個 SDK 的最低版本：

| .NET Core SDK 版本 | Visual Studio 版本                      |
| --------------------- | ------------------------------------------ |
| 3.0                   | Visual Studio 2019 16.3 或更高版本。 |
| 2.2                   | Visual Studio 2017 15.9 或更高版本。 |
| 2.1                   | Visual Studio 2017 15.7 或更高版本。 |
| 1.x                   | Visual Studio 2017 15.0 或更高版本。 |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

若要使用 .NET Core 3.0 SDK 在 Visual Studio 2019 中開發 .NET Core 應用程式：

* [下載並安裝 Visual Studio 2019 16.3 版或更新版本](/visualstudio/install/install-visual-studio)，並根據您所建立的應用程式類型，選取包含 .NET Core SDK 的下列其中一個工作負載：

  * [**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。
  * **Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。
  * **Windows**區段中的**NET desktop 開發**工作負載。

下圖顯示在 [Visual Studio] UI 中選取的 [ **.Net Core 跨平臺開發**] 工作負載：

![已選取 [.NET Core 跨平臺開發] 工作負載的 Visual Studio 2019 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-2019-workloads.jpg)

Visual Studio 2019 16.3 在安裝任何這些工作負載之後，預設會使用 .NET Core 3.0 SDK。

如果您想要讓現有的專案使用最新的 .NET Core 執行時間，請使用下列指示，將每個現有的 .NET Core 專案的目標重定為 .NET Core 3.0：

* 在 [ **專案** ] 功能表上，選擇 [ **屬性**]。
* 在 [**目標 framework** ] 選取功能表中，將值設定為 [ **.net Core 3.0**]。

![已選取 ".NET Core 3.0" 目標 framework 功能表項目的 Visual Studio 2019 應用程式專案屬性的螢幕擷取畫面](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

當您使用 .NET Core 3.0 SDK 設定 Visual Studio 之後，就可以執行下列動作：

* 開啟、建置及執行現有的 .NET Core 1.x 和 2.x 專案。
* 將 .NET Core 1.x 和2.x 專案的目標重定為 .NET Core 3.0、組建和執行。
* 建立新的 .NET Core 3.0 專案。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

若要在 Visual Studio 2017 中開發使用 .NET Core 2.2 SDK 的 .NET Core 應用程式：

* 使用已選取的 **.Net Core 跨平臺開發**工作負載（在 [**其他工具**組] 區段），[下載並安裝 Visual Studio 2019 16.3 版或更新版本](/visualstudio/install/install-visual-studio)。
* [下載並安裝 Visual Studio 2017 15.9.0 版本或更新版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-2017-workloads.jpg)

安裝 **.NET Core 跨平台開發**工具集之後，Visual Studio 通常會安裝舊版的 .NET Core SDK。
例如，安裝工作負載之後，Visual Studio 2017 15.9 預設會使用 .NET Core 2.1 SDK。

若要更新 Visual Studio 以使用 .NET Core 2.2 SDK：

 1. 安裝 [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)。

 1. 如果您想要讓專案使用最新的 .NET Core 執行時間，請使用下列指示，將每個現有或新的 .NET Core 專案的目標重定為 .NET Core 2.2：

    * 在 [ **專案** ] 功能表上，選擇 [ **屬性**]。
    * 在 [目標 Framework] 選取功能表中，將值設為 **.NET Core 2.2**。

![螢幕擷取畫面：選取 ".NET Core 2.2" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/targeting-dotnet-core.jpg)

一旦使用 .NET Core 2.2 SDK 設定 Visual Studio，您可以執行下列動作：

* 開啟、建置及執行現有的 .NET Core 1.x 和 2.x 專案。
* 將 .NET Core 1.x 和 2.x 專案目標重新設定為 .NET Core 2.2、建置和執行。
* 建立新的 .NET Core 2.2 專案。

---
