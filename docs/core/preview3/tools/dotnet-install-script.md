---
title: "dotnet-install 指令碼 | Microsoft Docs"
description: "了解如何使用 dotnet-install 指令碼來安裝 .NET Core CLI 工具和共用執行階段。"
keywords: "dotnet-install, dotnet-install 指令碼, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 0063ac1220a1f01eef6e7300b0907518863ee01e

---

#<a name="dotnet-install-scripts-reference-net-core-tools-rc4"></a>dotnet-install 指令碼參考 (.NET Core 工具 RC4)

> [!WARNING]
> 本主題適用於 .NET Core 工具 RC4。 .NET Core 工具 Preview 2 版本，請參閱 [dotnet-install 指令碼參考](../../tools/dotnet-install-script.md)主題。

## <a name="name"></a>名稱
dotnet-install.ps1 | dotnet-install.sh - 用來安裝命令列介面 (CLI) 工具和共用執行階段的指令碼

## <a name="synopsis"></a>概要
Windows：

`dotnet-install.ps1 [-Channel] [-Version]
    [-InstallDir] [-Debug] [-NoPath] 
    [-SharedRuntime]`

macOS/Linux：

`dotnet-install.sh [--channel] [--version]
    [--install-dir] [--debug] [--no-path] 
    [--shared-runtime]`

## <a name="description"></a>描述
`dotnet-install` 指令碼用來執行 CLI 工具鏈和共用執行階段的非 Admin 安裝。 您可以從 [CLI GitHub 存放庫](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/scripts/obtain)下載指令碼。 

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

要安裝的 CLI 版本；您需要將版本指定為 3 部分的版本 (例如，1.0.0-13232)。 省略時，將預設為包含 `version` 屬性的第一個 [global.json](global-json.md)；如果不存在，則會使用最新版本。     

`-InstallDir [DIR]`

要在其中安裝的路徑。 如果目錄不存在，則會建立它。 預設值為 *%LocalAppData%\.dotnet*。

`-Debug`

`true` 表示應該使用包含偵錯符號的較大套件；否則為 `false`。 預設值是 `false`。

`-NoPath`

`true` 表示 prefix/installdir 未匯出至目前工作階段的路徑；否則為 `false`。 預設值是 `false`，即已修改 PATH。 如此可讓 CLI 工具在安裝之後立即可用。 

`-SharedRuntime`

`true` 僅安裝共用執行階段位元；`false` 則安裝整個 SDK。 預設值是 `false`。

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)
`--channel [CHANNEL]`

從中安裝的通道 (例如 "future"、"preview"、"production")。 預設值是 "Production"。

`--version [VERSION]`

要安裝的 CLI 版本；您需要將版本指定為 3 部分的版本 (例如，1.0.0-13232)。 省略時，將預設為包含 `version` 屬性的第一個 [global.json](global-json.md)；如果不存在，則會使用最新版本。     

`--install-dir [DIR]`

要在其中安裝的路徑。 如果目錄不存在，則會建立它。 預設值是 `$HOME/.dotnet`。

`--debug`

`true` 表示應該使用包含偵錯符號的較大套件；否則為 `false`。 預設值是 `false`。

`--no-path`

`true` 表示 prefix/installdir 未匯出至目前工作階段的路徑；否則為 `false`。 預設值是 `false`，即已修改 PATH。 如此可讓 CLI 工具在安裝之後立即可用。  

`--shared-runtime`

`true` 僅安裝共用執行階段位元；`false` 則安裝整個 SDK。 預設值是 `false`。

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



<!--HONumber=Feb17_HO2-->


