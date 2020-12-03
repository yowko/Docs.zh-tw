---
title: 在 Windows 上安裝 .NET
description: 瞭解您可以在哪些版本的 Windows 上安裝 .NET。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 786814549724948fa69b18a05cee966e0940aaf4
ms.sourcegitcommit: c6de55556add9f92af17e0f8d1da8f356a19a03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96549341"
---
# <a name="install-net-on-windows"></a>在 Windows 上安裝 .NET

> [!div class="op_single_selector"]
>
> - [在 Windows 上安裝](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [在 Linux 上安裝](linux.md)

在本文中，您將瞭解如何在 Windows 上安裝 .NET。 .NET 是由執行時間和 SDK 所組成。 執行時間是用來執行 .NET 應用程式，且不一定會包含在應用程式中。 SDK 是用來建立 .NET 應用程式和程式庫。 .NET 執行時間一律會與 SDK 一起安裝。

.NET 的最新版本為5.0。

> [!div class="button"]
> [下載 .NET](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>支援的版本

下表列出目前支援的 .NET 版本，以及支援的 Windows 版本。 這些版本一直受支援，直到 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Windows 版本的 [生命週期結束](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)為止。

Windows 10 版本的服務結束日期會依版本分割。 下表只考慮 **家用** 版、 **專業** 版、 **專業教育** 版和 **工作站版專業** 版。 查看 [Windows 生命週期的工作表](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) 以取得特定詳細資料。

> [!TIP]
> `+`符號表示最小版本。

| 作業系統            | .NET Core 2.1 | .NET Core 3.1 | .NET 5 |
|-----------------------------|---------------|---------------|--------|
| Windows 10，版本2004    | ✔️           | ✔️            | ✔️    |
| Windows 10，版本1909    | ✔️           | ✔️            | ✔️    |
| Windows 10，版本1903    | ✔️           | ✔️            | ✔️    |
| Windows 10，版本1809    | ✔️           | ✔️            | ✔️    |
| Windows 10，版本1803    | ✔️           | ✔️            | ✔️    |
| Windows 10，版本1709    | ✔️           | ✔️            | ✔️    |
| Windows 10，版本 1607    | ✔️           | ✔️            | ✔️    |
| Windows 8.1                 | ✔️           | ✔️            | ✔️    |
| Windows 7 SP1 [ESU][esu]    | ✔️           | ✔️            | ✔️    |
| Windows 10，版本 1607    | ✔️           | ✔️            | ✔️    |
| Windows 10，版本 1607    | ✔️           | ✔️            | ✔️    |
| Windows Server 2012 R2      | ✔️           | ✔️            | ✔️    |
| Windows Server Core 2012 R2 | ✔️           | ✔️            | ✔️    |
| Nano Server、Version 1809 +  | ✔️           | ✔️            | ✔️    |
| Nano Server，版本1803   | ✔️           | ✔️            | ❌    |

## <a name="unsupported-releases"></a>不支援的版本

不再支援下列 .NET 版本 ❌ 。 這些內容的下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="runtime-information"></a>執行時間資訊

執行時間是用來執行以 .NET 建立的應用程式。 當應用程式作者發佈應用程式時，他們可以在其應用程式中包含執行時間。 如果未包含執行時間，則會由使用者自行安裝執行時間。

您可以在 Windows 上安裝三個不同的執行時間：

*ASP.NET Core 執行時間*\
執行 ASP.NET Core 應用程式。 包含 .NET 執行時間。

*桌面執行時間*\
執行適用于 Windows 的 .NET WPF 和 Windows Forms 桌面應用程式。 包含 .NET 執行時間。

*.NET 執行時間*\
此執行時間是最簡單的執行時間，不包含任何其他執行時間。 強烈建議您安裝 *ASP.NET Core 運行* 時間和 *桌面運行* 時間，以獲得與 .net 應用程式的最佳相容性。

> [!div class="button"]
> [下載 .NET 執行時間](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>SDK 資訊

SDK 可用來建立及發佈 .NET 應用程式和程式庫。 安裝 SDK 包含三個 [運行](#runtime-information)時間： ASP.NET Core、Desktop 和 .net。

## <a name="dependencies"></a>相依性

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[.NET 5.0](#tab/net50)

.NET 5.0 支援下列 Windows 版本：

> [!NOTE]
> `+`符號表示最小版本。

| OS                  | 版本       | 架構   |
|---------------------|---------------|-----------------|
| Windows 10 用戶端   | 1607版 + | x64、x86、ARM64 |
| Windows 用戶端      | 7 SP1 +、8。1   | x64、x86        |
| Windows Server      | 2012 R2 +      | x64、x86        |
| Windows 伺服器核心 | 2012 R2 +      | x64、x86        |
| Nano Server         | 版本 1809 + | x64             |

如需 .NET 5.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱 [.net 5.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)。

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 支援下列 Windows 版本：

> [!NOTE]
> `+`符號表示最小版本。

| OS                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8。1                    | x64、x86        |
| Windows 10 用戶端             | 1607版 +                  | x64、x86        |
| Windows Server                | 2012 R2 +                       | x64、x86        |
| Nano Server                   | 版本 1803 +                  | x64、ARM32      |

如需 .NET Core 3.1 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*.NET Core 3.0 目前不 ❌ 支援。如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*

.NET Core 3.0 支援下列 Windows 版本：

> [!NOTE]
> `+`符號表示最小版本。

| OS                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8。1                    | x64、x86        |
| Windows 10 用戶端             | 1607版 +                  | x64、x86        |
| Windows Server                | 2012 R2 +                       | x64、x86        |
| Nano Server                   | 版本 1803 +                  | x64、ARM32      |

如需 .NET Core 3.0 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*.NET Core 2.2 目前不 ❌ 支援。如需詳細資訊，請參閱 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*

.NET Core 2.2 支援下列 Windows 版本：

> [!NOTE]
> `+`符號表示最小版本。

| OS                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8。1                    | x64、x86        |
| Windows 10 用戶端             | 1607版 +                  | x64、x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64、x86        |
| Nano Server                   | 版本 1803 +                   | x64、ARM32      |

如需 .NET Core 2.2 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 支援下列 Windows 版本：

> [!NOTE]
> `+`符號表示最小版本。

| OS                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8。1                    | x64、x86        |
| Windows 10 用戶端             | 1607版 +                  | x64、x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64、x86        |
| Nano Server                   | 版本 1803 +                  | 64            |

如需 .NET Core 2.1 支援的作業系統、散發套件和生命週期原則的詳細資訊，請參閱 [.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> Windows 7/Vista/8.1/Server 2008 R2/Server 2012 R2

如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：

- Windows 7 SP1 [ESU][esu]
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

安裝下列項目：

- [Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件更新3。
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

如果您遇到下列其中一個錯誤，也需要先前的需求：

> 程式無法啟動，因為您的電腦遺漏 *api-ms-win-crt-runtime-l1-1-0.dll* 。 請嘗試重新安裝程式以修正此問題。
>
> \- 或 -
>
> 程式無法啟動，因為您的電腦遺漏 *api-ms-win-cor-timezone-l1-1-0.dll* 。 請嘗試重新安裝程式以修正此問題。
>
> \- 或 -
>
> 找到程式庫 *hostfxr.dll* ，但從 *C： \\ \<path_to_app> \\hostfxr.dll* 載入該程式庫失敗。

## <a name="install-with-powershell-automation"></a>使用 PowerShell 自動化安裝

[Dotnet 安裝腳本](../tools/dotnet-install-script.md)適用于執行時間的 CI 自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載腳本。

腳本預設會安裝最新 [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。 您可以藉由指定參數來選擇特定版本 `Channel` 。 包含 `Runtime` 參數以安裝執行時間。 否則，腳本會安裝 SDK。

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

藉由省略參數來安裝 SDK `-Runtime` 。 `-Channel`此範例會將此參數設定為 `Current` ，以安裝最新支援的版本。

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>使用 Visual Studio 安裝

如果您使用 Visual Studio 開發 .NET 應用程式，下表將根據目標 .NET SDK 版本描述 Visual Studio 所需的最低版本。

| .NET SDK 版本      | Visual Studio 版本                      |
| --------------------- | ------------------------------------------ |
| 5.0                   | Visual Studio 2019 16.8 版或更高版本。 |
| 3.1                   | Visual Studio 2019 16.4 版或更高版本。 |
| 3.0                   | Visual Studio 2019 16.3 版或更高版本。 |
| 2.2                   | Visual Studio 2017 15.9 版或更高版本。 |
| 2.1                   | Visual Studio 2017 15.7 版或更高版本。 |

如果您已經安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。

01. 開啟 Visual Studio。
01. 選取 **Help**  >  **Microsoft Visual Studio** 的 [說明]。
01. 閱讀 [ **關於** ] 對話方塊中的版本號碼。

Visual Studio 可以安裝最新的 .NET SDK 和執行時間。

> [!div class="button"]
> [下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。

### <a name="select-a-workload"></a>選取工作負載

安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列一或多個工作負載：

- [**其他工具** 組] 區段中的 **.net Core 跨平臺開發** 工作負載。
- **Web & Cloud** 區段中的 **ASP.NET 和 網頁程式開發** 工作負載。
- **Web & Cloud** 區段中的 **Azure 開發** 工作負載。
- Desktop 中的 **.net 桌面開發** 工作負載 **& Mobile** 區段。

[![使用 .NET Core 工作負載的 Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>隨 Visual Studio Code 一起安裝

Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。 Visual Studio Code 適用于 Windows、macOS 和 Linux。

雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援很簡單。

01. [下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。
01. [下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。
01. [從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。

## <a name="windows-installer"></a>Windows Installer

.NET 的 [下載頁面](https://dotnet.microsoft.com/download/dotnet-core) 提供 Windows Installer 可執行檔。

當您使用 MSI 檔案來安裝 .NET 時< 您可以藉由設定和參數來自訂安裝路徑 `DOTNETHOME_X64` `DOTNETHOME_X86` ：

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

## <a name="download-and-manually-install"></a>下載並手動安裝

您也可以下載並手動安裝 SDK 或執行時間，以替代適用于 .NET 的 Windows 安裝程式。 手動安裝通常會做為持續整合測試的一部分來執行。 針對開發人員或使用者，通常最好是使用 [安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。

.NET SDK 和 .NET 執行時間都可以在下載之後手動安裝。 如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。 首先，從下列其中一個網站下載 SDK 或執行時間的二進位版本：

- [.NET 5.0 下載](https://dotnet.microsoft.com/download/dotnet/5.0)
- [.NET Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下載](https://dotnet.microsoft.com/download/dotnet-core)

例如，建立用來將 .NET 解壓縮至的目錄 `%USERPROFILE%\dotnet` 。 然後，將下載的 zip 檔案解壓縮到該目錄中。

根據預設，.NET CLI 命令和應用程式不會使用以這種方式安裝的 .NET，因此您必須明確地選擇使用它。 若要這樣做，請變更應用程式啟動所在的環境變數：

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

這種方法可讓您將多個版本安裝到不同的位置，然後使用指向該位置的環境變數來執行應用程式，以明確選擇應用程式應使用的安裝位置。

當 `DOTNET_MULTILEVEL_LOOKUP` 設定為時 `0` ，.net 會忽略任何全域安裝的 .net 版本。 移除該環境設定，讓 .NET 在選取最適合用來執行應用程式的架構時，考慮預設的全域安裝位置。 預設值通常是 `C:\Program Files\dotnet` 安裝程式安裝 .net 的位置。

## <a name="docker"></a>Docker

容器可提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。 相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。

.NET 可以在 Docker 容器中執行。 官方 .NET Docker 映射會發佈至 Microsoft Container Registry (MCR) 並可在 [microsoft .net Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet)中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-aspnet) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

如需在 Docker 容器中使用 .NET 的詳細資訊，請參閱 [.net 和 Docker 簡介](../docker/introduction.md) 和 [範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>後續步驟

- [如何檢查是否已安裝 .net](how-to-detect-installed-versions.md?pivots=os-windows)。
- [教學課程： Hello World 教學](../tutorials/with-visual-studio.md)課程。
- [教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。
- [教學課程：將 .Net Core 應用程式](../docker/build-container.md)。

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
