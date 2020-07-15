---
title: 在 Windows 上安裝 .NET Core
description: 瞭解您可以在上安裝 .NET Core 的 Windows 版本。
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: 97f67d00b3eb4dafc55256aea51f4295bb0ef06a
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308945"
---
# <a name="install-net-core-on-windows"></a>在 Windows 上安裝 .NET Core

> [!div class="op_single_selector"]
>
> - [安裝在 Windows 上](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [安裝在 Linux 上](linux.md)

在本文中，您將瞭解如何在 Windows 上安裝 .NET Core。 .NET Core 是由執行時間和 SDK 所組成。 執行時間是用來執行 .NET Core 應用程式，且不一定會包含在應用程式中。 SDK 可用來建立 .NET Core 應用程式和程式庫。 .NET Core 執行時間一律會與 SDK 一起安裝。

.NET Core 的最新版本為3.1。

> [!div class="button"]
> [下載 .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>支援的版本

下表列出目前支援的 .NET Core 版本，以及支援的 Windows 版本。 這些版本持續支援，直到[.Net Core 版本達到支援的終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或[Windows 版本達到生命週期的結束](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)為止。

Windows 10 版本的服務結束日期是依版本分割。 下表只會考慮**Home**、 **Pro**、 **Pro 教育**和**適用于工作站**版本的 pro。 如需特定詳細資料，請參閱[Windows 生命週期事實表](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)。

- ✔️表示仍然支援 Windows 或 .NET Core 的版本。
- A ❌ 表示該 windows 版本不支援 windows 或 .Net Core 的版本。
- 當 Windows 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| 作業系統                      | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview |
|-----------------------------|---------------|---------------|----------------|
| ✔️ Windows 10，版本2004 | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ Windows 10，版本1909 | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ Windows 10，版本1903 | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ Windows 10，版本1809 | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ❌Windows 10 版本1803 | ✔️2。1        | ❌3.1        | ❌5.0 預覽 |
| ❌Windows 10 版本1709 | ❌2.1        | ❌3.1        | ❌5.0 預覽 |
| ❌Windows 10 版本1703 | ❌2.1        | ❌3.1        | ❌5.0 預覽 |
| ❌Windows 10 版本1607 | ❌2.1        | ❌3.1        | ❌5.0 預覽 |
| ❌Windows 10 版本1511 | ❌2.1        | ❌3.1        | ❌5.0 預覽 |
| ❌Windows 10 版本1507 | ❌2.1        | ❌3.1        | ❌5.0 預覽 |

## <a name="unsupported-releases"></a>不支援的版本

已不再支援下列 .NET Core 版本 ❌ 。 這些下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="runtime-information"></a>執行時間資訊

執行時間是用來執行使用 .NET Core 所建立的應用程式。 當應用程式作者發行應用程式時，他們可以將執行時間包含在其應用程式中。 如果它們不包含執行時間，則會由使用者自行安裝執行時間。

您可以在 Windows 上安裝三種不同的執行時間：

*ASP.NET Core 執行時間*\
執行 ASP.NET Core 應用程式。 包含 .NET Core 執行時間。

*桌面執行時間*\
執行適用于 Windows 的 .NET Core WPF 和 .NET Core Windows Forms 桌面應用程式。 包含 .NET Core 執行時間。

*.NET Core 執行時間*\
此執行時間是最簡單的執行時間，不包含任何其他執行時間。 強烈建議您同時安裝*ASP.NET Core 運行*時間和*桌面運行*時間，以獲得與 .net Core 應用程式的最佳相容性。

> [!div class="button"]
> [下載 .NET Core 執行時間](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>SDK 資訊

SDK 可用來建立及發佈 .NET Core 應用程式和程式庫。 安裝 SDK 包括三個[運行](#runtime-information)時間： ASP.NET Core、桌面和 .net Core。

> [!div class="button"]
> [下載 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a>相依性

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 支援下列 Windows 版本：

> [!NOTE]
> `+`代表最小版本的符號。

| 作業系統                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 8.1                            | x64、x86        |
| Windows 10 用戶端             | 版本 1609 +                  | x64、x86        |
| Windows Server                | 2012 R2 +                       | x64、x86        |
| Nano Server                   | 版本 1803 +                  | x64、ARM32      |

如需 .NET Core 3.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*.NET Core 3.0 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*

.NET Core 3.0 支援下列 Windows 版本：

> [!NOTE]
> `+`代表最小版本的符號。

| 作業系統                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8。1                    | x64、x86        |
| Windows 10 用戶端             | 版本 1607 +                  | x64、x86        |
| Windows Server                | 2012 R2 +                       | x64、x86        |
| Nano Server                   | 版本 1803 +                  | x64、ARM32      |

如需 .NET Core 3.0 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 3.0 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*.NET Core 2.2 目前不受支援。如需詳細資訊，請參閱[.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。*

.NET Core 2.2 支援下列 Windows 版本：

> [!NOTE]
> `+`代表最小版本的符號。

| 作業系統                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8。1                    | x64、x86        |
| Windows 10 用戶端             | 版本 1607 +                  | x64、x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64、x86        |
| Nano Server                   | 版本 1803 +                   | x64、ARM32      |

如需 .NET Core 2.2 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.2 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 支援下列 Windows 版本：

> [!NOTE]
> `+`代表最小版本的符號。

| 作業系統                            | 版本                        | 架構   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 用戶端                | 7 SP1 +、8。1                    | x64、x86        |
| Windows 10 用戶端             | 版本 1607 +                  | x64、x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64、x86        |
| Nano Server                   | 版本 1803 +                  | x64            |

如需 .NET Core 2.1 支援的作業系統、發行版本和生命週期原則的詳細資訊，請參閱[.Net core 2.1 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a>Windows 7/Vista/8.1/Server 2008 R2/Server 2012 R2

如果您要在下列 Windows 版本上安裝 .NET SDK 或執行時間，則需要額外的相依性：

- ❌Windows 7 SP1
- ❌Windows Vista SP 2
- ✔️ Windows 8。1
- ✔️ Windows Server 2008 R2
- ✔️ Windows Server 2012 R2

安裝下列項目：

- [Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685)可轉散發套件 Update 3。
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

如果您遇到下列其中一個錯誤，也需要上述需求：

> 程式無法啟動，因為電腦中遺失*api-ms-win-crt-runtime-l1-1-0.dll* 。 請嘗試重新安裝程式以修正此問題。
>
> \- 或 -
>
> 程式無法啟動，因為電腦中遺失*api-ms-win-cor-timezone-l1-1-0.dll* 。 請嘗試重新安裝程式以修正此問題。
>
> \- 或 -
>
> 找到程式庫*hostfxr.dll* ，但從*C： \\ \<path_to_app> \\hostfxr.dll*載入它失敗。

## <a name="install-with-powershell-automation"></a>使用 PowerShell 自動化進行安裝

[Dotnet-install 腳本](../tools/dotnet-install-script.md)會用於 CI 自動化，以及非系統管理員的執行時間安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。 您可以藉由指定參數來選擇特定版本 `Channel` 。 包含用 `Runtime` 來安裝執行時間的參數。 否則，腳本會安裝[SDK](sdk.md)。

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

省略參數以安裝 SDK `-Runtime` 。 `-Channel`此範例中的參數設定為 `Current` ，它會安裝最新支援的版本。

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>使用 Visual Studio 安裝

如果您使用 Visual Studio 開發 .NET Core 應用程式，下表將根據目標 .NET Core SDK 版本描述 Visual Studio 的最低必要版本。

| .NET Core SDK 版本 | Visual Studio 版本                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 16.4 或更高版本。 |
| 3.0                   | Visual Studio 2019 16.3 或更高版本。 |
| 2.2                   | Visual Studio 2017 15.9 或更高版本。 |
| 2.1                   | Visual Studio 2017 15.7 或更高版本。 |

如果您已安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。

01. 開啟 Visual Studio。
01. 選取 **[**  >  **關於 Microsoft Visual Studio**的說明]。
01. 閱讀 [**關於**] 對話方塊中的版本號碼。

Visual Studio 可以安裝最新的 .NET Core SDK 和執行時間。

> [!div class="button"]
> [下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。

### <a name="select-a-workload"></a>選取工作負載

安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列其中一個或多個工作負載：

- [**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。
- **Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。
- **Web & 雲端**一節中的**Azure 開發**工作負載。
- **桌上型電腦 & Mobile**一節中的 **.net 桌面開發**工作負載。

[![Windows Visual Studio 2019 與 .NET Core 工作負載](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>與 Visual Studio Code 一起安裝

Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。 Visual Studio Code 適用于 Windows、macOS 和 Linux。

雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援十分簡單。

01. [下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。
01. [下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。
01. [從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。

## <a name="download-and-manually-install"></a>下載並手動安裝

除了適用于 .NET Core 的 Windows 安裝程式之外，您還可以下載並手動安裝 SDK 或執行時間。 手動安裝通常是做為持續整合測試的一部分來執行。 對於開發人員或使用者，通常最好是使用[安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。

.NET Core SDK 和 .NET Core 執行時間都可以在下載之後手動安裝。 如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 首先，從下列其中一個網站下載 SDK 或執行時間的二進位版本：

- ✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下載](https://dotnet.microsoft.com/download/dotnet-core)

建立可將 .NET 解壓縮至的目錄，例如 `%USERPROFILE%\dotnet` 。 然後，將下載的 zip 檔案解壓縮至該目錄。

根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core，因此您必須明確地選擇使用它。 若要這麼做，請變更應用程式啟動時所使用的環境變數：

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

這種方法可讓您將多個版本安裝到不同的位置，然後明確地選擇應用程式應該使用的安裝位置，方法是以指向該位置的環境變數執行應用程式。

當 `DOTNET_MULTILEVEL_LOOKUP` 設定為時 `0` ，.net core 會忽略任何全域安裝的 .net core 版本。 移除該環境設定，讓 .NET Core 在選取最適合執行應用程式的架構時，考慮預設的全域安裝位置。 預設值通常是 `C:\Program Files\dotnet` ，安裝程式會在此安裝 .Net Core。

## <a name="docker"></a>Docker

容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。 相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。

.NET Core 可以在 Docker 容器中執行。 官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>後續步驟

- [如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md?pivots=os-windows)。
- [教學課程： Hello World 教學](../tutorials/with-visual-studio.md)課程。
- [教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。
- [教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。
