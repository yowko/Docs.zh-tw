---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core 執行時間-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索執行 .NET Core 應用程式所需的相依性。
author: adegeo
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 6a0390ff1db900815628e4c7eb69e7a6c5f148a8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324590"
---
# <a name="install-the-net-core-runtime"></a>安裝 .NET Core 執行時間

在本文中，您將瞭解如何下載並安裝 .NET Core 執行時間。 .NET Core 執行時間是用來執行使用 .NET Core 所建立的應用程式。

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>使用安裝程式安裝

Windows 有獨立的安裝程式，可用於安裝 .NET Core 3.1 執行時間：

- [x64 （64位） Cpu](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 （32位） Cpu](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>使用安裝程式安裝

macOS 具有可用於安裝 .NET Core 3.1 執行時間的獨立安裝程式：

- [x64 （64位） Cpu](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>下載並手動安裝

除了適用于 .NET Core 的 macOS 安裝程式之外，您還可以下載並手動安裝執行時間。

若要安裝執行時間並啟用終端機可用的 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。 然後，開啟終端機並執行下列命令。 假設執行時間已下載至檔案 `~/Downloads/dotnet-runtime.pkg` 。

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a>在 Linux 上安裝

這篇文章很快就會移除。 目前已藉由[在 Linux 上安裝 .Net Core](linux.md)來取代。

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>使用 PowerShell 自動化進行安裝

[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。 您可以藉由指定參數來選擇特定版本 `Channel` 。 包含用 `Runtime` 來安裝執行時間的參數。 否則，腳本會安裝[SDK](sdk.md)。

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> 上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。 ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。

## <a name="download-and-manually-install"></a>下載並手動安裝

若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。 然後，建立要安裝的目錄，例如 `%USERPROFILE%\dotnet` 。 最後，將下載的 zip 檔案解壓縮至該目錄。

根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core，因此您必須明確地選擇使用它。 若要這麼做，請變更應用程式啟動時所使用的環境變數：

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

這種方法可讓您將多個版本安裝到不同的位置，然後明確地選擇應用程式應該使用的安裝位置，方法是以指向該位置的環境變數執行應用程式。

即使已設定這些環境變數，在選取最佳架構來執行應用程式時，.NET Core 仍然會考慮預設的全域安裝位置。 預設值通常是 `C:\Program Files\dotnet` 安裝程式所使用的。 您也可以藉由設定此環境變數，指示執行時間只使用自訂安裝位置：

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a>使用 bash automation 進行安裝

[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。 您可以藉由指定參數來選擇特定版本 `current` 。 包含用 `runtime` 來安裝執行時間的參數。 否則，腳本會安裝[SDK](sdk.md)。

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> 上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。 ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。

::: zone-end

## <a name="all-net-core-downloads"></a>所有 .NET Core 下載

您可以使用下列其中一個連結直接下載並安裝 .NET Core：

- [.NET Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。 相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。

.NET Core 可以在 Docker 容器中執行。 官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>後續步驟

- [如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。
