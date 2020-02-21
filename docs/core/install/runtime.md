---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core 執行時間-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索執行 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ba50eb222d9eab6bffbb8ebfdf0ecf47951ce719
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543517"
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

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>使用套件管理員進行安裝

您可以使用許多常見的 Linux 封裝管理員來安裝 .NET Core 執行時間。 如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-managers.md)。

只有在 x64 架構上才支援使用套件管理員進行安裝。 如果您要使用不同的架構（例如 ARM）來安裝 .NET Core 執行時間，請遵循[下載並手動安裝](#download-and-manually-install)一節中的指示。 如需有關支援哪些架構的詳細資訊，請參閱[.Net Core 相依性和需求](dependencies.md)。

## <a name="download-and-manually-install"></a>下載並手動安裝

若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。 然後，開啟終端機並執行下列命令。

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 上述 `export` 命令只會將 .NET Core CLI 命令提供給執行它的終端機會話。
>
> 您可以編輯您的 shell 設定檔，以永久新增命令。 有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。 例如：
>
> - **Bash Shell**： *~/. bash_profile*， *~/.bashrc*
> - **Korn Shell**： *~/.kshrc*或 *. profile*
> - **Z Shell**： *~/.zshrc*或 *. zprofile*
> 
> 為您的 shell 編輯適當的原始程式檔，並將 `:$HOME/dotnet` 新增至現有 `PATH` 語句的結尾。 如果未包含任何 `PATH` 語句，請加入具有 `export PATH=$PATH:$HOME/dotnet`的新行。
>
> 此外，將 `export DOTNET_ROOT=$HOME/dotnet` 新增至檔案結尾。

這種方法可讓您將不同的版本安裝到不同的位置，並明確選擇哪一個應用程式要使用哪一個。

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>使用 PowerShell 自動化進行安裝

[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。 您可以藉由指定 `Channel` 參數來選擇特定版本。 包含 `Runtime` 參數，以安裝執行時間。 否則，腳本會安裝[SDK](sdk.md)。

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> 上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。 ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。

## <a name="download-and-manually-install"></a>下載並手動安裝

若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。 然後，建立要安裝的目錄，例如 `%USERPROFILE%\dotnet`。 最後，將下載的 zip 檔案解壓縮至該目錄。

根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core。 您必須明確地選擇使用它。 若要這麼做，請變更應用程式啟動時所使用的環境變數：

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

這種方法可讓您將多個版本安裝到不同的位置，然後明確地選擇應用程式應該使用的安裝位置，方法是以指向該位置的環境變數執行應用程式。

即使已設定這些環境變數，在選取最佳架構來執行應用程式時，.NET Core 仍然會考慮預設的全域安裝位置。 預設值通常是 `C:\Program Files\dotnet`，這是安裝程式所使用的。 您也可以藉由設定此環境變數，指示執行時間只使用自訂安裝位置：

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>使用 bash automation 進行安裝

[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。 您可以藉由指定 `current` 參數來選擇特定版本。 包含 `runtime` 參數，以安裝執行時間。 否則，腳本會安裝[SDK](sdk.md)。

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> 上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。 ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。

::: zone-end

## <a name="all-net-core-downloads"></a>所有 .NET Core 下載

您可以使用下列其中一個連結直接下載並安裝 .NET Core：

- [.NET Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 3.0 下載](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET Core 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。 相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。

.NET Core 可以在 Docker 容器中執行。 官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>後續步驟

- [如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。
