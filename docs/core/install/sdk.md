---
title: 在 Windows、Linux 和 macOS 上安裝 .NET 核心 SDK - .NET 核心
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 瞭解開發 .NET Core 應用所需的依賴項。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399004"
---
# <a name="install-the-net-core-sdk"></a>安裝 .NET Core SDK

在本文中，您將學習如何安裝 .NET 核心 SDK。 .NET 核心 SDK 用於創建 .NET 核心應用和庫。 .NET 核心運行時始終與 SDK 一起安裝。

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>使用安裝程式安裝

Windows 具有可用於安裝 .NET Core 3.1 SDK 的獨立安裝程式：

- [x64 （64 位） CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 （32 位） CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>使用安裝程式安裝

macOS 具有可用於安裝 .NET Core 3.1 SDK 的獨立安裝程式：

- [x64 （64 位） CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>下載並手動安裝

作為 .NET Core 的 macOS 安裝程式的替代方法，您可以下載並手動安裝 SDK。

要提取 SDK 並使 .NET 核心 CLI 命令在終端上可用，請先[下載](#all-net-core-downloads).NET Core 二進位版本。 然後，打開一個終端並運行以下命令。 假定運行時將下載到`~/Downloads/dotnet-sdk.pkg`檔中。

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>使用包管理器安裝

您可以使用許多常見的 Linux 套裝程式管理器安裝 .NET 核心 SDK。 有關詳細資訊，請參閱[Linux 套裝軟體管理器 - 安裝 .NET 核心](linux-package-managers.md)。

僅支援使用包管理器進行安裝。 如果要安裝具有其他體系結構（如 ARM）的 .NET 核心 SDK，請按照下面的[下載並手動安裝](#download-and-manually-install)說明進行操作。 有關支援哪些體系結構的詳細資訊，請參閱[.NET Core 依賴項和要求](dependencies.md)。

## <a name="download-and-manually-install"></a>下載並手動安裝

要提取 SDK 並使 .NET 核心 CLI 命令在終端上可用，請先[下載](#all-net-core-downloads).NET Core 二進位版本。 然後，打開一個終端並運行以下命令。

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 前面的`export`命令僅使 .NET Core CLI 命令可用於運行它的終端會話。
>
> 您可以編輯 shell 設定檔以永久添加命令。 Linux 有許多不同的外殼，每個外殼都有不同的設定檔。 例如：
>
> - **巴什外殼**： **/.bash_profile* *，*/.bashrc*
> - **科恩殼牌**： **/.kshrc*或 *. profile*
> - **Z 外殼**： **/.zshrc*或 *.zprofile*
>
> 編輯 shell 的相應原始檔案，並`:$HOME/dotnet`添加到現有`PATH`語句的末尾。 如果未`PATH`包含語句，則使用`export PATH=$PATH:$HOME/dotnet`添加新行。
>
> 此外，添加到`export DOTNET_ROOT=$HOME/dotnet`檔的末尾。

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>使用視覺工作室安裝

如果您使用 Visual Studio 開發 .NET Core 應用，下表將基於目標 .NET Core SDK 版本描述視覺化工作室的最低要求版本。

| .NET 核心 SDK 版本 | Visual Studio 版本                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 版本 16.4 或更高版本。 |
| 3.0                   | Visual Studio 2019 版本 16.3 或更高版本。 |
| 2.2                   | Visual Studio 2017 版本 15.9 或更高版本。 |
| 2.1                   | Visual Studio 2017 版本 15.7 或更高版本。 |

如果您已經安裝了 Visual Studio，您可以使用以下步驟檢查您的版本。

01. 開啟 Visual Studio。
01. 選擇**關於** > **微軟視覺工作室的説明**。
01. 從 **"關於"** 對話方塊中讀取版本號。

Visual Studio 可以安裝最新的 .NET 核心 SDK 和運行時。

- [下載視覺工作室](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。

### <a name="select-a-workload"></a>選擇工作負荷

安裝或修改 Visual Studio 時，根據要構建的應用程式類型選擇以下一個或多個工作負載：

- **"其他工具集**"部分中的 **.NET 核心跨平臺開發**工作負載。
- **Web &雲**部分中的**ASP.NET和 Web 開發**工作負載。
- **Web &雲**部分中的**Azure 開發**工作負荷。
- **桌面&移動**部分中的 **.NET 桌面開發**工作負荷。

[![Windows 視覺化工作室 2019 與 .NET 核心工作負載](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="download-and-manually-install"></a>下載並手動安裝

要提取運行時並使 .NET Core CLI 命令在終端上可用，請首先[下載](#all-net-core-downloads).NET Core 二進位版本。 然後，創建要安裝到的目錄，例如`%USERPROFILE%\dotnet`。 最後，將下載的 ZIP 檔案提取到該目錄中。

預設情況下，.NET 核心 CLI 命令和應用不會以這種方式使用 .NET Core 安裝。 您必須明確選取使用它。 為此，請更改啟動應用程式的環境變數：

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

此方法允許您將多個版本安裝到單獨的位置，然後通過運行應用程式的環境變數指向該位置來明確選取應用程式應使用哪個安裝位置。

即使設置了這些環境變數，.NET Core 在選擇運行應用程式的最佳框架時仍會考慮預設的全域安裝位置。 預設值通常是`C:\Program Files\dotnet`安裝程式使用的 。 也可以通過設置此環境變數來指示運行時僅使用自訂安裝位置：

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>安裝與 Mac 視覺工作室

選擇 **.NET 核心**工作負載時，適用于 Mac 的視覺化工作室將安裝 .NET 核心 SDK。 要開始在 macOS 上使用 .NET 核心開發，請參閱[為 Mac 安裝視覺化工作室 2019](/visualstudio/mac/installation)。 對於最新版本 .NET Core 3.1，您必須使用 Visual Studio 進行 Mac 8.4 預覽。

[![macOS 視覺化工作室 2019 適用于具有 .NET 核心工作負載功能的 Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>與視覺工作室代碼一起安裝

Visual Studio Code 是一款功能強大且羽量級的原始程式碼編輯器，在桌面上運行。 視覺化工作室代碼可用於 Windows、macOS 和 Linux。

雖然 Visual Studio 代碼沒有像 Visual Studio 那樣具有自動化的 .NET 核心安裝程式，但添加 .NET Core 支援非常簡單。

01. [下載並安裝視覺工作室代碼](https://code.visualstudio.com/Download)。
01. [下載並安裝 .NET 核心 SDK](https://dotnet.microsoft.com/download/dotnet-core)。
01. [從視覺化工作室代碼市場安裝 C# 擴展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>使用 PowerShell 自動化安裝

[點網安裝腳本](../tools/dotnet-install-script.md)用於 SDK 的自動化和非管理員安裝。 可以從[dotnet 安裝腳本引用頁](../tools/dotnet-install-script.md)下載腳本。

該腳本預設安裝最新的[長期支援 （LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，即 .NET Core 3.1。 要安裝 .NET Core 的當前版本，請使用以下開關運行腳本。

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>使用 bash 自動化安裝

[點網安裝腳本](../tools/dotnet-install-script.md)用於 SDK 的自動化和非管理員安裝。 可以從[dotnet 安裝腳本引用頁](../tools/dotnet-install-script.md)下載腳本。

該腳本預設安裝最新的[長期支援 （LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，即 .NET Core 3.1。 要安裝 .NET Core 的當前版本，請使用以下開關運行腳本。

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>所有 .NET 核心下載

您可以使用以下連結之一直接下載和安裝 .NET Core：

- [.NET 核心 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET 核心 3.0 下載](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET 核心 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET 核心 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

容器提供了將應用程式與主機系統的其餘部分隔離的羽量級方法。 同一台電腦上的容器僅共用內核並使用提供給應用程式的資源。

.NET Core 可以在 Docker 容器中運行。 官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

有關在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.NET 和 Docker 和](../docker/introduction.md)[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)簡介。

## <a name="next-steps"></a>後續步驟

::: zone pivot="os-windows"

- [教程：你好世界教程](../tutorials/with-visual-studio.md)。
- [教程：使用視覺化工作室代碼創建新應用程式](../tutorials/with-visual-studio-code.md)。
- [教程： 容器化 .NET 核心應用程式](../docker/build-container.md)。

::: zone-end

::: zone pivot="os-macos"

- [與macOS卡塔琳娜公證](macos-notarization-issues.md)工作。
- [教程： 開始在 macOS](../tutorials/using-on-mac-vs.md).
- [教程：使用視覺化工作室代碼創建新應用程式](../tutorials/with-visual-studio-code.md)。
- [教程： 容器化 .NET 核心應用程式](../docker/build-container.md)。

::: zone-end

::: zone pivot="os-linux"

- [教程：使用視覺化工作室代碼創建新應用程式](../tutorials/with-visual-studio-code.md)。
- [教程： 容器化 .NET 核心應用程式](../docker/build-container.md)。

::: zone-end
