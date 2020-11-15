---
title: dotnet restore 命令
description: 了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。
ms.date: 02/27/2020
ms.openlocfilehash: dcb68d6c690f2e12b61cfdfa6dc288bd474721c1
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634399"
---
# <a name="dotnet-restore"></a>dotnet restore

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet restore` - 還原專案的相依性和工具。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a>描述

`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。  在大部分情況下，您不需要明確地使用 `dotnet restore` 命令，因為當您執行下列命令時，會隱含地執行 NuGet 還原：

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

有時候，使用這些命令執行隱含的 NuGet 還原可能很不方便。 例如，某些自動化系統，像是建置系統，必須明確呼叫 `dotnet restore` 以控制還原發生的時間，進而控制網路使用量。 若要防止隱含的 NuGet 還原，您可以使用 `--no-restore` 旗標搭配任何這些命令來停用隱含還原。

### <a name="specify-feeds"></a>指定摘要

若要還原相依性，NuGet 需要套件所在的摘要。 摘要通常透過 *nuget.config* 組態檔提供。 安裝 .NET SDK 時，會提供預設的設定檔案。 若要指定其他摘要，請執行下列其中一項：

- 在專案目錄中建立您自己的 *nuget.config* 檔案。 如需詳細資訊，請參閱本文稍後的 [一般 NuGet](/nuget/consume-packages/configuring-nuget-behavior) 設定和 [nuget.config 差異](#nugetconfig-differences) 。
- 使用 `dotnet nuget` 像這樣的命令 [`dotnet nuget add source`](dotnet-nuget-add-source.md) 。

您可以使用選項覆寫 *nuget.config* 摘要 `-s` 。

如需如何使用已驗證摘要的詳細資訊，請參閱使用 [已驗證摘要中的套件](/nuget/consume-packages/consuming-packages-authenticated-feeds)。

### <a name="global-packages-folder"></a>全域套件資料夾

針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。 如果未指定，則會使用預設的 NuGet 套件快取，它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中。 例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1* 。

### <a name="project-specific-tooling"></a>專案特定工具

針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。

### <a name="nugetconfig-differences"></a>nuget.config 差異

*nuget.config* 檔案中設定 (如果有的話) 會影響 `dotnet restore` 命令的行為。 例如，在 *nuget.config* 中設定 `globalPackagesFolder` 會將還原的 NuGet 套件置於所指定資料夾。 這是在 `dotnet restore` 命令上指定 `--packages` 選項的替代方式。 如需詳細資訊，請參閱 [nuget.config 參考](/nuget/schema/nuget-config-file)。

`dotnet restore` 會忽略三個特定設定：

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  系結重新導向無法使用 `<PackageReference>` 元素，而且 .net 只支援 `<PackageReference>` NuGet 套件的元素。

- [解決方案](/nuget/schema/nuget-config-file#solution-section)

  這項設定是 Visual Studio 特定的，不適用於 .NET。 .NET 不會使用檔案 `packages.config` ，而是會使用 `<PackageReference>` NuGet 套件的元素。

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  此設定不適用，因為 [NuGet 尚未支援信任套件的跨平臺驗證](https://github.com/NuGet/Home/issues/7939)。

## <a name="arguments"></a>引數

- **`ROOT`**

  要還原之專案檔的選用路徑。

## <a name="options"></a>選項

- **`--configfile <FILE>`**

  要用於還原作業的 NuGet 組態檔 ( *nuget.config* )。

- **`--disable-parallel`**

  停用平行還原多個專案。

- **`--force`**

  即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

- **`--force-evaluate`**

  強制還原重新評估所有的相依性，即使鎖定檔案已存在也一樣。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--ignore-failed-sources`**

  如果有套件符合版本需求，則只會警告有關失敗的來源。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作 (例如完成驗證)。 自 .NET Core 2.1.400 起。

- **`--lock-file-path <LOCK_FILE_PATH>`**

  寫入專案鎖定檔案的輸出位置。 根據預設，這會 *PROJECT_ROOT\packages.lock.js開啟* 。

- **`--locked-mode`**

  不允許更新專案鎖定檔案。

- **`--no-cache`**

  指定不快取 HTTP 要求。

- **`--no-dependencies`**

  在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。

- **`--packages <PACKAGES_DIRECTORY>`**

  指定已還原套件的目錄。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  指定套件還原的執行階段。 這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 多次指定這個選項來提供多個 RID。

- **`-s|--source <SOURCE>`**

  指定要在還原作業期間使用的 NuGet 套件來源 URI。 這項設定會覆寫 *nuget.config* 檔案中指定的所有來源。 多次指定這個選項，即可提供多個來源。

- **`--use-lock-file`**

  可產生專案鎖定檔案並與還原一起使用。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值為 `minimal`。

## <a name="examples"></a>範例

- 還原目前目錄中專案的相依性和工具︰

  ```dotnetcli
  dotnet restore
  ```

- 還原在指定路徑中找到之 `app1` 專案的相依性和工具︰

  ```dotnetcli
  dotnet restore ./projects/app1/app1.csproj
  ```

- 使用提供作為來源的檔案路徑，還原目前目錄中專案的相依性和工具：

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- 使用提供作為來源的兩個檔案路徑，還原目前目錄中專案的相依性和工具：

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- 還原目前目錄中專案的相依性和工具，以顯示詳細的輸出：

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
