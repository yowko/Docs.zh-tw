---
title: "dotnet-install 指令碼"
description: "了解如何使用 dotnet-install 指令碼來安裝 .NET Core CLI 工具和共用執行階段。"
keywords: "dotnet-install, dotnet-install 指令碼, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
ms.workload: dotnetcore
ms.openlocfilehash: bc38ca7b9f00c6c252ff4963c42519a64c456b43
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-install-scripts-reference"></a>dotnet-install 指令碼參考

## <a name="name"></a>名稱

`dotnet-install.ps1` | `dotnet-install.sh` - 用來安裝 .NET Core CLI 工具和共用執行階段的指令碼。

## <a name="synopsis"></a>概要

Windows：

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

macOS/Linux：

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>描述

`dotnet-install` 指令碼可用來執行 .NET Core SDK 的非系統管理安裝，其中包含了 .NET Core CLI 工具和共用執行階段。

建議您使用 [.NET Core 主網站](https://dot.net) \(英文\) 所提供的穩定版本。 指令碼的直接路徑如下：

* https://dot.net/v1/dotnet-install.sh (bash, UNIX)
* https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)

這些指令碼對於自動化案例和非系統管理員安裝非常有幫助。 指令碼有兩種：一種是在 Windows 上使用的 PowerShell 指令碼。 另一個指令碼是可在 Linux/macOS 上運作的 bash 指令碼。 這兩個指令碼有相同的行為。 Bash 指令碼也能讀取 PowerShell 參數，因此您可以搭配 PowerShell 參數使用 Linux/macOS 系統上的指令碼。 

安裝指令碼會從 CLI 組建放置區下載 ZIP/tarball 檔案，並且繼續將它安裝在預設位置或 `-InstallDir|--install-dir` 所指定的位置。 根據預設，安裝指令碼會下載並安裝 SDK。 如果您想要只取得共用執行階段，請指定 `--shared-runtime` 引數。 

根據預設，指令碼會將安裝位置新增到目前工作階段的 $PATH。 指定 `--no-path` 引數可以覆寫此預設行為。 

執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。

您可以使用 `--version` 引數安裝特定版本。 必須以三段式版本的格式指定版本 (例如，1.0.0-13232)。 如果省略，就會使用 `latest` 版本。

## <a name="options"></a>選項

`-Channel <CHANNEL>`

指定安裝的來源通道。 可能值為：

- `Current` - 目前的版本
- `LTS` - 長期支援通道 (目前支援的版本)
- X.Y 格式的兩部分版本代表特定版本 (例如 `2.0` 或 `1.0`)
- 分支名稱 [例如 `release/2.0.0`、`release/2.0.0-preview2`，或針對最新 `master` 分支的 `master` (「高度風險」每日更新版)]

預設值是 `LTS`。 如需有關 .NET 支援通道的詳細資訊，請參閱 [.NET Core 支援週期](https://www.microsoft.com/net/core/support) \(英文\) 主題。

`-Version <VERSION>`

代表特定的組建版本。 可能值為：

- `latest` - 通道上的最新組建 (搭配 `-Channel` 選項來使用)
- `coherent` - 通道上的最新一致性組建，使用最新的穩定套件組合 (搭配分支名稱 `-Channel` 選項來使用)
- 代表特定組建版本的 X.Y.Z 格式三段式版本；取代 `-Channel` 選項。 例如：`2.0.0-preview2-006120`

如果省略，`-Version` 預設會設為 `latest`。

`-InstallDir <DIRECTORY>`

指定安裝路徑。 如果目錄不存在，則會建立它。 預設值為 *%LocalAppData%\.dotnet*。 請注意，二進位檔會直接放置在目錄中。

`-Architecture <ARCHITECTURE>`

要安裝的 .NET Core 二進位檔的架構。 可能的值為 `auto`、`x64` 和 `x86`。 預設值為 `auto`，代表目前正在執行的 OS 架構。

`-SharedRuntime`

如果設定，則此參數會限制在共用執行階段的安裝。 尚未安裝整個 SDK。

`-DryRun`

如果設定，指令碼將不會執行安裝，而是會顯示以一致的方式安裝目前要求的 .NET Core CLI 版本時所要使用的命令列。 例如，如果您指定 `latest` 版本，則會顯示特定版本的連結，以便可在建置指令碼中明確使用此命令。 如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。

`-NoPath`

如果設定，則不會將 prefix/installdir 匯出至目前工作階段的路徑。 根據預設，指令碼將會修改此路徑，以在安裝後立即提供 CLI 工具。

`-AzureFeed`

指定給安裝程式的 Azure 摘要 URL。 不建議您變更這個值。 預設為 `https://dotnetcli.azureedge.net/dotnet`。

`-ProxyAddress`

如果設定，安裝程式會使用此 Proxy 進行 Web 要求。 (只適用於 Windows)

`--verbose`

顯示診斷資訊。

`--help`

印出指令碼的說明。

## <a name="examples"></a>範例

將最新的長期支援 (LTS) 版本安裝至預設位置︰

Windows：

`./dotnet-install.ps1 -Channel LTS`

macOS/Linux：

`./dotnet-install.sh --channel LTS`

將來自 2.0 通道的最新版本安裝至指定的位置︰

Windows：

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

macOS/Linux：

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

安裝共用執行階段 1.1.0 版本：

Windows：

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

macOS/Linux：

`./dotnet-install.sh --shared-runtime --version 1.1.0`

取得指令碼並安裝 .NET Core CLI 單行範例：

Windows：

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

macOS/Linux：

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>另請參閱

[.NET Core 版本](https://github.com/dotnet/core/releases)   
[.NET Core 執行階段和 SDK 下載封存](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
