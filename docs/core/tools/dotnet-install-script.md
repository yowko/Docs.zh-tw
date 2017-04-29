---
title: "dotnet-install 指令碼 | Microsoft Docs"
description: "了解如何使用 dotnet-install 指令碼來安裝 .NET Core CLI 工具和共用執行階段。"
keywords: "dotnet-install, dotnet-install 指令碼, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
translationtype: Human Translation
ms.sourcegitcommit: 4a1f0c88fb1ccd6694f8d4f5687431646adbe000
ms.openlocfilehash: fbc1ce8d864a5c2150c61f4b8bf7cb8544921634
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-install-scripts-reference"></a>dotnet-install 指令碼參考

## <a name="name"></a>名稱

`dotnet-install.ps1` | `dotnet-install.sh` - 用來安裝 .NET Core 命令列介面 (CLI) 工具和共用執行階段的指令碼。

## <a name="synopsis"></a>概要

Windows：

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DebugSymbols] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress]`

macOS/Linux：

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

## <a name="description"></a>描述

`dotnet-install` 指令碼用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。 您可以從 [CLI GitHub 存放庫 (英文)](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain) 下載指令碼。 

這些指令碼對於自動化案例和非系統管理員安裝非常有幫助。 指令碼有兩種：一種是在 Windows 上使用的 PowerShell 指令碼。 另一種指令碼是在 Linux/OS X 上使用的 Bash 指令碼。兩種指令碼的行為相同。 Bash 指令碼也能讀取 PowerShell 參數，因此您可以搭配 PowerShell 參數使用 Linux/OS X 系統上的指令碼。 

安裝指令碼會從 CLI 組建放置區下載 ZIP/tarball 檔案，並且繼續將它安裝在預設位置或 `-InstallDir|--install-dir` 所指定的位置。 根據預設，安裝指令碼會下載並安裝 SDK。 如果您想要只取得共用執行階段，請指定 `--shared-runtime` 引數。 

根據預設，指令碼會將安裝位置新增到目前工作階段的 $PATH。 指定 `--no-path` 引數可以覆寫此預設行為。 

執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。

您可以使用 `--version` 引數安裝特定版本。 必須以三段式版本的格式指定版本 (例如，1.0.0-13232)。 如果省略，則預設值為在叫用指令碼時，所在資料夾的上層資料夾中找到的第一個包含 `version` 屬性的 [global.json](global-json.md) 檔案。 如果該檔案不存在，則會使用最新版本。

您也可以搭配 `--debug` 引數使用這個指令碼，以取得包含偵錯符號的 SDK 或共用執行階段偵錯二進位檔。 如果您第一次安裝時沒有這麼做，而事後發現需要對符號進行偵錯，則您可以搭配 `--debug` 引數和已安裝的 SDK 版本重新執行指令碼，以取得偵錯符號。 

## <a name="options"></a>選項

注意：指令碼實作之間的選項不同。 

### <a name="powershell-windows"></a>PowerShell (Windows)

`-Channel <CHANNEL>`

指定安裝的來源通道。 這些值為：`future`、`preview` 和 `production`。 預設值是 `production`。

`-Version <VERSION>`

指定要安裝的 CLI 版本。 您必須以三段式版本的格式指定版本 (例如，1.0.0-13232)。 如果省略，則預設值為第一個包含 `version` 屬性的 [global.json](global-json.md) 檔案。 如果該檔案不存在，則會使用最新版本。

`-InstallDir <DIRECTORY>`

指定安裝路徑。 如果目錄不存在，則會建立它。 預設值為 *%LocalAppData%\.dotnet*。

`-Architecture <ARCHITECTURE>`

要安裝的 .NET Core 二進位檔的架構。 可能的值為 `auto`、`x64` 和 `x86`。 預設值為 `auto`，代表目前正在執行的 OS 架構。

`-SharedRuntime`

如果設定，則此參數會限制在共用執行階段的安裝。 尚未安裝整個 SDK。

`-DebugSymbols` (請參閱「注意」)

如果設定，則安裝程式會在安裝中包含偵錯符號。

> [!NOTE]
> 目前還不能使用 `-DebugSymbols` 參數，但已計劃在未來的版本推出。

`-DryRun`

如果設定，指令碼將不會執行安裝，而是會顯示以一致的方式安裝目前要求的 .NET CLI 版本時所要使用的命令列。 例如，如果您指定 `latest` 版本，則會顯示特定版本的連結，以便可在建置指令碼中明確使用此命令。 如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。

`-NoPath`

如果設定，則不會將 prefix/installdir 匯出至目前工作階段的路徑。 根據預設，指令碼將會修改此路徑，以在安裝後立即提供 CLI 工具。

`-AzureFeed`

指定給安裝程式的 Azure 摘要 URL。 不建議您變更這個值。 預設為 `https://dotnetcli.azureedge.net/dotnet`。

`-ProxyAddress`

如果設定，安裝程式會使用此 Proxy 進行 Web 要求。

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

`--channel <CHANNEL>`

指定安裝的來源通道。 這些值為：`future`、`dev` 和 `production`。 預設值是 `production`。

`--version <VERSION>`

指定要安裝的 CLI 版本。 您必須以三段式版本的格式指定版本 (例如，1.0.0-13232)。 如果省略，則預設值為第一個包含 `version` 屬性的 [global.json](global-json.md) 檔案。 如果該檔案不存在，則會使用最新版本。

`--install-dir <DIRECTORY>`

指定安裝路徑。 如果目錄不存在，則會建立它。 預設值是 `$HOME/.dotnet`。

`--architecture <ARCHITECTURE>`

要安裝的 .NET Core 二進位檔的架構。 可能的值為 `auto`、`x64` 和 `amd64`。 預設值為 `auto`，代表目前正在執行的 OS 架構。

`--shared-runtime`

如果設定，則此參數會限制在共用執行階段的安裝。 尚未安裝整個 SDK。

`--debug-symbols`

如果設定，則安裝程式會在安裝中包含偵錯符號。

> [!NOTE]
> 目前還不能使用此參數，但已計劃在未來的版本推出。

`--dry-run`

如果設定，指令碼將不會執行安裝，而是會顯示以一致的方式安裝目前要求的 .NET CLI 版本時所要使用的命令列。 例如，如果您指定 `latest` 版本，則會顯示特定版本的連結，以便可在建置指令碼中明確使用此命令。 如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。

`--no-path`

如果設定，則不會將 prefix/installdir 匯出至目前工作階段的路徑。 根據預設，指令碼將會修改此路徑，以在安裝後立即提供 CLI 工具。

`--verbose`

顯示診斷資訊。

`--azure-feed`

指定給安裝程式的 Azure 摘要 URL。 不建議您變更這個值。 預設為 `https://dotnetcli.azureedge.net/dotnet`。

`--help`

印出指令碼的說明。

## <a name="examples"></a>範例

將最新的開發版本安裝至預設位置︰

Windows：

`./dotnet-install.ps1 -Channel Future`

macOS/Linux：

`./dotnet-install.sh --channel Future`

將最新預覽版本安裝至指定的位置︰

Windows：

`./dotnet-install.ps1 -Channel preview -InstallDir C:\cli`

macOS/Linux：

`./dotnet-install.sh --channel preview --install-dir ~/cli`
