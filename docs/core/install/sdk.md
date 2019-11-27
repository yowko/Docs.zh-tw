---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core SDK-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索開發 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2f65e9dc39a4cd1076af1a70dfedfa671f20b42d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450874"
---
# <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

在本文中，您將瞭解如何安裝 .NET Core SDK。 .NET Core SDK 可用來建立 .NET Core 應用程式和程式庫。 .NET Core 執行時間一律會與 SDK 一起安裝。

您可以使用下列其中一個連結直接下載並安裝 .NET Core：

- [.NET Core 3.1 Preview 3 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 3.0 下載](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET Core 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)

您也可以將 .NET Core 安裝為整合式開發環境（IDE）的一部分，如下節所述。

## <a name="install-with-an-installer"></a>使用安裝程式安裝

Windows 和 macOS 都有獨立的安裝程式，可以用來安裝 .NET Core 3.0 SDK。

- Windows [X64 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)
- macOS [X64 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>使用套件管理員進行安裝

您可以使用許多常見的 Linux 套件管理員來安裝 .NET Core SDK。 如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-manager-rhel7.md)。

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>使用 Visual Studio 安裝

如果您使用 Visual Studio 開發 .NET Core 應用程式，下表將根據目標 .NET Core SDK 版本描述 Visual Studio 的最低必要版本。

| .NET Core SDK 版本 | Visual Studio 版本                      |
| --------------------- | ------------------------------------------ |
| 3.0                   | Visual Studio 2019 16.3 或更高版本。 |
| 2.2                   | Visual Studio 2017 15.9 或更高版本。 |
| 2.1                   | Visual Studio 2017 15.7 或更高版本。 |

如果您已安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。

01. 開啟 Visual Studio。
01. 選取 **[** 說明] > **關於 Microsoft Visual Studio**。
01. 閱讀 [**關於**] 對話方塊中的版本號碼。

Visual Studio 可以安裝最新的 .NET Core SDK 和執行時間。

- [下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。

### <a name="select-a-workload"></a>選取工作負載

安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列其中一個工作負載：

- [**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。
- **Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。
- **Web & 雲端**一節中的**Azure 開發**工作負載。
- **桌上型電腦 & Mobile**一節中的 **.net 桌面開發**工作負載。

[使用 .NET Core 工作負載 ![Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>使用 Visual Studio for Mac 安裝

Visual Studio for Mac 在選取 [ **.Net Core** ] 工作負載時安裝 .NET Core SDK。 若要開始在 macOS 上使用 .NET Core 開發，請參閱[安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。

[使用 .NET Core 工作負載功能 ![macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-from-visual-studio-code"></a>從 Visual Studio Code 安裝

Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。 Visual Studio Code 適用于 Windows、macOS 和 Linux。

雖然 Visual Studio Code 不隨附 .NET Core 支援，但新增 .NET Core 支援很簡單。

01. [下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。
01. [下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0)。
01. [從 Visual Studio Code C# marketplace 安裝延伸](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)模組。

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>使用 PowerShell 自動化進行安裝

[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 2.1。 若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>使用 bash automation 進行安裝

[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 2.1。 若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a>Docker

容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。 相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。

.NET Core 可以在 Docker 容器中執行。 官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>後續步驟

::: zone pivot="os-windows"

- [教學課程C# ： Hello World 教學](../tutorials/with-visual-studio.md)課程。
- [教學課程： Visual Basic Hello World 教學](../tutorials/vb-with-visual-studio.md)課程。
- [教學課程：使用 Visual Studio Code 建立新的應用程式](https://code.visualstudio.com/docs/languages/dotnet)。
- [教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。

::: zone-end

::: zone pivot="os-macos"

- [教學課程：開始使用 macOS](../tutorials/using-on-mac-vs.md)。
- [教學課程：使用 Visual Studio Code 建立新的應用程式](https://code.visualstudio.com/docs/languages/dotnet)。
- [教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。

::: zone-end
