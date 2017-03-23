---
title: "dotnet-install 指令碼 | Microsoft Docs"
description: "了解如何使用 dotnet-install 指令碼來安裝 .NET Core CLI 工具和共用執行階段。"
keywords: "dotnet-install, dotnet-install 指令碼, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
translationtype: Human Translation
ms.sourcegitcommit: 99254f84873003496ee00214d55ff908f9fd47d3
ms.openlocfilehash: 6301fb61be27d7dac6ead57159c0d9461b3eacb5
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-install-scripts-reference"></a>dotnet-install 指令碼參考

## <a name="name"></a>名稱

`dotnet-install.ps1` | `dotnet-install.sh` - 用來安裝 .NET Core 命令列介面 (CLI) 工具和共用執行階段的指令碼。

## <a name="synopsis"></a>概要
Windows：

```
dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture]
    [-SharedRuntime] [-DebugSymbols] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress]
```

macOS/Linux：

```
dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture]
    [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]
```

## <a name="description"></a>描述
`dotnet-install` 指令碼用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。 您可以從 [CLI GitHub 存放庫](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain)下載指令碼。 

其主要使用案例是要協助自動化案例和非 Admin 安裝。 有兩個指令碼，一個適用於在 Windows 上運作的 PowerShell，以及在 Linux/OS X 上運作的 Bash 指令碼。兩者的行為相同。 Bash 指令碼也會「了解」PowerShell 參數，讓您可以跨面板使用它們。 

安裝指令碼將會從 CLI 組建置放下載 ZIP/tarball 檔案，並且繼續將它安裝在預設位置或 `--install-dir` 所指定的位置。 安裝指令碼預設將會下載並安裝 SDK；如果您只想要取得共用執行階段，則可以指定 `--shared-runtime` 引數。 

指令碼預設會將安裝位置新增至目前工作階段的 $PATH。 如果使用 `--no-path` 引數，則可能會覆寫這項作業。 

執行指令碼之前，請安裝所有必要的[相依性](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。

您可以使用 `--version` 引數安裝特定版本。 版本必須指定為 3 部分的版本 (例如，1.0.0-13232)。 省略時，會預設為在階層的資料夾上方找到的第一個 [global.json](global-json.md) 檔案，在這個資料夾中，會叫用包含 `version` 屬性的指令碼。 如果不存在，則會使用最新版本。

您也可以搭配使用這個指令碼，以使用 `--debug` 引數與偵錯符號來取得 SDK 或共用執行階段偵錯二進位檔。 如果您未在第一次安裝時執行這項作業，並且了解稍後確實需要偵錯符號，則可以使用這個引數和所安裝位元的版本來重新執行指令碼。 

## <a name="options"></a>選項
指令碼實作之間的選項不同。 

### <a name="powershell-windows"></a>PowerShell (Windows)
`-Channel [CHANNEL]`

從中安裝的通道 (例如，`future`、`preview`、`production`)。 預設值是 `production`。

`-Version [VERSION]`

要安裝的 CLI 版本。 您需要將版本指定為 3 部分的版本 (例如 1.0.0-13232)。 省略時，將預設為包含 `version` 屬性的第一個 [global.json](global-json.md)。 如果不存在，則會使用最新版本。

`-InstallDir [DIR]`

要在其中安裝的路徑。 如果目錄不存在，則會建立它。 預設值為 *%LocalAppData%\.dotnet*。

`-Architecture [ARCH]`

要安裝的 .NET Core 二進位檔架構。 可能的值為 &lt;auto&gt;、x64 和 x86。 預設值為 &lt;auto&gt;，代表目前正在執行的 OS 架構。

`-SharedRuntime`

如果設定，則僅安裝共用執行階段位元，而不是整個 SDK。

`-DebugSymbols`

如果設定，安裝程式會在安裝中包含偵錯符號。

> [!NOTE]
> 此參數目前沒有作用。

`-DryRun`

如果設定，指令碼將不會執行安裝，而是會顯示以一致的方式安裝目前要求的 .NET CLI 版本時所要使用的命令列。 例如，如果您指定 `latest` 版本，則會顯示特定版本的連結，以便可在建置指令碼中明確使用此命令。
如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。

`-NoPath`

如果設定，則不會將 prefix/installdir 匯出至目前工作階段的路徑。 根據預設，指令碼將會修改此路徑，以在安裝後立即提供 CLI 工具。

`-AzureFeed`

可供此安裝程式使用的 Azure 摘要 URL。 不建議變更。 預設為 `https://dotnetcli.azureedge.net/dotnet`。

`-ProxyAddress`

如果設定，安裝程式將會使用此 Proxy 進行 Web 要求。

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture]
    [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]
`

`--channel [CHANNEL]`

從中安裝的通道 (例如 "future"、"dev"、"production")。 預設值是 "Production"。

`--version [VERSION]`

要安裝的 CLI 版本。 您需要將版本指定為 3 部分的版本 (例如 1.0.0-13232)。 省略時，將預設為包含 `version` 屬性的第一個 [global.json](global-json.md)。 如果不存在，則會使用最新版本。

`--install-dir [DIR]`

要在其中安裝的路徑。 如果目錄不存在，則會建立它。 預設值是 `$HOME/.dotnet`。

`--architecture [ARCH]`

要安裝的 .NET 二進位檔架構。 可能的值為 &lt;auto&gt;、x64 和 amd64。 預設值為 &lt;auto&gt;，代表目前正在執行的 OS 架構。

`--shared-runtime`

如果設定，則僅安裝共用執行階段位元，而不是整個 SDK。

`--debug-symbols`

如果設定，安裝程式會在安裝中包含偵錯符號。

> [!NOTE]
> 此參數目前沒有作用。

`--dry-run`

如果設定，指令碼將不會執行安裝，而是會顯示以一致的方式安裝目前要求的 .NET CLI 版本時所要使用的命令列。 例如，如果您指定 `latest` 版本，則會顯示特定版本的連結，以便可在建置指令碼中明確使用此命令。
如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。

`--no-path`

如果設定，則不會將 prefix/installdir 匯出至目前工作階段的路徑。 根據預設，指令碼將會修改此路徑，以在安裝後立即提供 CLI 工具。

`--verbose`

顯示診斷資訊。

`--azure-feed`

可供此安裝程式使用的 Azure 摘要 URL。 不建議變更。 預設為 `https://dotnetcli.azureedge.net/dotnet`。

`--help`

印出指令碼的說明。

## <a name="examples"></a>範例

將開發最新版本安裝至預設位置︰

Windows：

`./dotnet-install.ps1 -Channel Future`

macOS/Linux：

`./dotnet-install.sh --channel Future`

將最新預覽版本安裝至指定的位置︰

Windows：

`./dotnet-install.ps1 -Channel preview -InstallDir C:\cli`

macOS/Linux：

`./dotnet-install.sh --channel preview --install-dir ~/cli`
