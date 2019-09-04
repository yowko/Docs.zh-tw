---
title: dotnet-install 指令碼
description: 了解如何使用 dotnet-install 指令碼來安裝 .NET Core CLI 工具和共用執行階段。
ms.date: 01/16/2019
ms.openlocfilehash: ed1a3341e678b405ae4aca35e3b49ada89eb069a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253903"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet-install 指令碼參考

## <a name="name"></a>名稱

`dotnet-install.ps1` | `dotnet-install.sh` - 用來安裝 .NET Core CLI 工具和共用執行階段的指令碼。

## <a name="synopsis"></a>概要

Windows：

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

macOS/Linux：

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>描述

`dotnet-install` 指令碼可用來執行 .NET Core SDK 的非系統管理安裝，其中包含了 .NET Core CLI 工具和共用執行階段。

建議您使用 [.NET Core 主網站](https://dot.net) \(英文\) 所提供的穩定版本。 指令碼的直接路徑如下：

- <https://dot.net/v1/dotnet-install.sh> (bash、UNIX)
- <https://dot.net/v1/dotnet-install.ps1> (Powershell、Windows)

這些指令碼對於自動化案例和非系統管理員安裝非常有幫助。 有兩個指令碼：一個是在 Windows 上運作的 PowerShell 指令碼，另一個是在 Linux/macOS 上運作的 Bash 指令碼。 這兩個指令碼有相同的行為。 Bash 指令碼也能讀取 PowerShell 參數，因此您可以搭配 PowerShell 參數使用 Linux/macOS 系統上的指令碼。

安裝指令碼會從 CLI 組建放置區下載 ZIP/tarball 檔案，並且繼續將它安裝在預設位置或 `-InstallDir|--install-dir` 所指定的位置。 根據預設，安裝指令碼會下載並安裝 SDK。 如果您想要只取得共用執行階段，請指定 `--runtime` 引數。

根據預設，指令碼會將安裝位置新增到目前工作階段的 $PATH。 指定 `--no-path` 引數可以覆寫此預設行為。

執行指令碼之前，請安裝所有必要的[相依性 (英文)](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。

您可以使用 `--version` 引數安裝特定版本。 指定版本時，必須以三段式版本格式指定 (例如 1.0.0-13232)。 如果未提供，就會使用 `latest` 版本。

## <a name="options"></a>選項

- **`-Channel <CHANNEL>`**

  指定安裝的來源通道。 可能值為：

  - `Current` - 最新版本。
  - `LTS` - 長期支援通道 (最新的支援版本)。
  - 代表特定版本的 X.Y 格式兩段式版本 (例如 `2.0` 或 `1.0`)。
  - 分支名稱。 例如 `release/2.0.0`、`release/2.0.0-preview2` 或 `master` (適用於夜間版本)。

  預設值為 `LTS`。 如需有關 .NET 支援通道的詳細資訊，請參閱 [.NET Core 支援政策](https://www.microsoft.com/net/platform/support-policy#dotnet-core) \(英文\) 頁面。

- **`-Version <VERSION>`**

  代表特定的組建版本。 可能值為：

  - `latest` - 通道上的最新組建 (與 `-Channel` 選項搭配使用)。
  - `coherent` - 通道上的最新一致性組建；使用最新的穩定套件組合 (與分支名稱 `-Channel` 選項搭配使用)。
  - 代表特定組建版本的 X.Y.Z 格式三段式版本；取代 `-Channel` 選項。 例如：`2.0.0-preview2-006120`。

  如果未指定，`-Version` 會預設為 `latest`。

- **`-InstallDir <DIRECTORY>`**

  指定安裝路徑。 如果目錄不存在，則會建立它。 預設值是 *%LocalAppData%\Microsoft\dotnet*。 二進位檔會直接放在此目錄中。

- **`-Architecture <ARCHITECTURE>`**

  要安裝的 .NET Core 二進位檔的架構。 可能的值為 `<auto>`、`amd64`、`x64`、`x86`、`arm64` 和 `arm`。 預設值為 `<auto>`，代表目前正在執行的 OS 架構。

- **`-SharedRuntime`**

  > [!NOTE]
  > 此參數已被淘汰，在未來的指令碼版本中可能會將其移除。 建議的替代方案是 `Runtime` 選項。

  只安裝共用執行階段位元，而不是整個 SDK。 這相當於指定 `-Runtime dotnet`。

- **`-Runtime <RUNTIME>`**

  只安裝共用執行階段，而不是整個 SDK。 可能值為：

  - `dotnet` - `Microsoft.NETCore.App` 共用執行階段。
  - `aspnetcore` - `Microsoft.AspNetCore.App` 共用執行階段。

- **`-DryRun`**

  如果設定，指令碼將不會執行安裝。 取而代之的是，會顯示以一致方式安裝目前所要求的 .NET Core CLI 版本時，所要使用的命令列。 例如，如果您指定 `latest` 版本，就會顯示特定版本的連結，以便在建置指令碼中以決定性方式使用此命令。 如果您想要自行進行安裝或下載，它也會顯示二進位檔位置。

- **`-NoPath`**

  如果設定，就不會將安裝資料夾匯出至目前工作階段的路徑。 指令碼預設會修改此路徑，以讓 CLI 工具在安裝後立即可供使用。

- **`-Verbose`**

  顯示診斷資訊。

- **`-AzureFeed`**

  指定給安裝程式的 Azure 摘要 URL。 建議您不要變更這個值。 預設值為 `https://dotnetcli.azureedge.net/dotnet`。

- **`-UncachedFeed`**

  允許變更此安裝程式所使用之未快取摘要的 URL。 建議您不要變更這個值。

- **`-NoCdn`**

  不允許從 [Azure 內容傳遞網路 (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) 下載，而直接使用未快取的摘要。

- **`-FeedCredential`**

  用來作為要附加至 Azure 摘要的查詢字串。 這可允許變更 URL 以使用非公用 Blob 儲存體帳戶。

- **`-ProxyAddress`**

  如果設定，安裝程式會使用此 Proxy 進行 Web 要求。 (只適用於 Windows)

- **`ProxyUseDefaultCredentials`**

  如果設定，當使用 Proxy 位址時，安裝程式會使用目前使用者的認證。 (只適用於 Windows)

- **`-SkipNonVersionedFiles`**

  如果已經有非版本控制的檔案 (例如 *dotnet.exe*) 存在，便略過其安裝。

- **`-Help`**

  印出指令碼的說明。

## <a name="examples"></a>範例

- 將最新的長期支援 (LTS) 版本安裝至預設位置︰

  Windows：

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux：

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- 將來自 2.0 通道的最新版本安裝至指定的位置︰

  Windows：

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  macOS/Linux：

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- 安裝共用執行階段 1.1.0 版本：

  Windows：

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  macOS/Linux：

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- 取得指令碼並在公司 Proxy 後方安裝 2.1.2 版本 (僅適用於 Windows)：

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- 取得指令碼並安裝 .NET Core CLI 單行範例：

  Windows：

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux：

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>另請參閱

- [.NET Core 版本](https://github.com/dotnet/core/releases)
- [.NET Core 執行階段和 SDK 下載封存](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
