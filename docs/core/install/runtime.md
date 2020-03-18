---
title: 在 Windows、Linux 和 macOS 上安裝 .NET 核心運行時 - .NET 內核
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 瞭解運行 .NET 核心應用所需的依賴項。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399011"
---
# <a name="install-the-net-core-runtime"></a>安裝 .NET 核心運行時

在本文中，您將學習如何下載和安裝 .NET Core 運行時。 .NET 核心運行時用於運行使用 .NET Core 創建的應用。

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>使用安裝程式安裝

Windows 具有可用於安裝 .NET Core 3.1 運行時的獨立安裝程式：

- [x64 （64 位） CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 （32 位） CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>使用安裝程式安裝

macOS 具有可用於安裝 .NET Core 3.1 運行時的獨立安裝程式：

- [x64 （64 位） CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>下載並手動安裝

作為 .NET Core 的 macOS 安裝程式的替代方法，您可以下載並手動安裝運行時。

要安裝運行時並啟用終端上可用的 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).NET Core 二進位版本。 然後，打開一個終端並運行以下命令。 假定運行時將下載到`~/Downloads/dotnet-runtime.pkg`檔中。

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>使用包管理器安裝

您可以使用許多常見的 Linux 套裝程式管理器安裝 .NET 核心運行時。 有關詳細資訊，請參閱[Linux 套裝軟體管理器 - 安裝 .NET 核心](linux-package-managers.md)。

僅在 x64 體系結構上支援使用包管理器安裝它。 如果要使用其他體系結構（如 ARM）安裝 .NET 核心運行時，請按照["下載"部分的說明進行手動安裝](#download-and-manually-install)。 有關支援哪些體系結構的詳細資訊，請參閱[.NET Core 依賴項和要求](dependencies.md)。

## <a name="download-and-manually-install"></a>下載並手動安裝

要提取運行時並使 .NET Core CLI 命令在終端上可用，請首先[下載](#all-net-core-downloads).NET Core 二進位版本。 然後，打開一個終端並運行以下命令。

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
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

此方法允許您將不同版本安裝到不同的位置，並明確選取要使用哪個應用程式的版本。

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>使用 PowerShell 自動化安裝

[dotnet 安裝腳本](../tools/dotnet-install-script.md)用於運行時的自動化和非管理員安裝。 可以從[dotnet 安裝腳本引用頁](../tools/dotnet-install-script.md)下載腳本。

該腳本預設安裝最新的[長期支援 （LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，即 .NET Core 3.1。 您可以通過指定`Channel`交換器來選擇特定版本。 包括`Runtime`用於安裝運行時的交換器。 否則，腳本將安裝[SDK](sdk.md)。

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> 上述命令安裝ASP.NET核心運行時以實現最大的相容性。 ASP.NET核心運行時還包括標準的 .NET 核心運行時。

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

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>使用 bash 自動化安裝

[dotnet 安裝腳本](../tools/dotnet-install-script.md)用於運行時的自動化和非管理員安裝。 可以從[dotnet 安裝腳本引用頁](../tools/dotnet-install-script.md)下載腳本。

該腳本預設安裝最新的[長期支援 （LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，即 .NET Core 3.1。 您可以通過指定`current`交換器來選擇特定版本。 包括`runtime`用於安裝運行時的交換器。 否則，腳本將安裝[SDK](sdk.md)。

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> 上述命令安裝ASP.NET核心運行時以實現最大的相容性。 ASP.NET核心運行時還包括標準的 .NET 核心運行時。

::: zone-end

## <a name="all-net-core-downloads"></a>所有 .NET 核心下載

您可以使用以下連結之一直接下載和安裝 .NET Core：

- [.NET 核心 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET 核心 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

容器提供了將應用程式與主機系統的其餘部分隔離的羽量級方法。 同一台電腦上的容器僅共用內核並使用提供給應用程式的資源。

.NET Core 可以在 Docker 容器中運行。 官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

有關在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.NET 和 Docker 和](../docker/introduction.md)[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)簡介。

## <a name="next-steps"></a>後續步驟

- [如何檢查是否已安裝 .NET Core。](how-to-detect-installed-versions.md)
