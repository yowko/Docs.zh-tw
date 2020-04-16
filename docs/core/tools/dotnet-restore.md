---
title: dotnet restore 命令
description: 了解如何使用 dotnet restore 命令來還原相依性和專案特有工具。
ms.date: 02/27/2020
ms.openlocfilehash: f49f0cda4424a4cc54ab7d4d4c6f729919dc7e60
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463424"
---
# <a name="dotnet-restore"></a>dotnet restore

**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet restore` - 還原專案的相依性和工具。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a>描述

`dotnet restore` 命令會使用 NuGet 來還原相依性以及專案檔中指定的專案特定工具。 預設會平行執行相依性和工具的還原。

若要還原相依性，NuGet 需要套件所在的摘要。 摘要通常透過 *nuget.config* 組態檔提供。 安裝 .NET 核心 SDK 時提供預設設定檔。 您可以在專案目錄中建立自己的 *nuget.config* 檔案，以指定其他摘要。 您可以使用`-s`- 選項覆*寫 nuget.config*源。

針對相依性，您可以使用 `--packages` 引數指定已還原套件在還原作業期間的放置位置。 如果未指定，則會使用預設的 NuGet 套件快取，它位於所有作業系統上使用者主目錄的 `.nuget/packages` 目錄中。 例如，Linux 上的 */home/user1* 或 Windows 上的 *C:\Users\user1*。

針對專案特定工具，`dotnet restore` 會先還原在其中封裝工具的套件，然後繼續還原其專案檔中所指定的工具相依性。

### <a name="nugetconfig-differences"></a>nuget.config 差異

*nuget.config* 檔案中設定 (如果有的話) 會影響 `dotnet restore` 命令的行為。 例如，在 *nuget.config* 中設定 `globalPackagesFolder` 會將還原的 NuGet 套件置於所指定資料夾。 這是在 `dotnet restore` 命令上指定 `--packages` 選項的替代方式。 如需詳細資訊，請參閱 [nuget.config 參考](/nuget/schema/nuget-config-file)。

`dotnet restore` 會忽略三個特定設定：

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  繫結重新導向不適用於 `<PackageReference>` 元素，且 .NET Core 針對 NuGet 套件僅支援 `<PackageReference>` 元素。

- [解決機制](/nuget/schema/nuget-config-file#solution-section)

  這是 Visual Studio 特定設定，不適用於 .NET Core。 .Net Core 不會使用 `packages.config` 檔案，而是針對 NuGet 套件使用 `<PackageReference>` 元素。

- [受信任的簽名者](/nuget/schema/nuget-config-file#trustedsigners-section)

  此設定不適用，因為 [NuGet 尚未支援信任套件的跨平臺驗證](https://github.com/NuGet/Home/issues/7939)。

## <a name="implicit-restore"></a>隱式還原

如有必要`dotnet restore`,在運行以下命令時,該命令將隱式運行:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

在大多數情況下,不需要顯式使用`dotnet restore`該命令。

有時候，可能不適合隱含執行 `dotnet restore`。 例如，某些自動化系統，像是建置系統，必須明確呼叫 `dotnet restore` 以控制還原發生的時間，進而控制網路使用量。 為避免隱含執行 `dotnet restore`，在使用任一這些命令時，可使用 `--no-restore` 旗標來停用隱含還原。

## <a name="arguments"></a>引數

- **`ROOT`**

  要還原之專案檔的選用路徑。

## <a name="options"></a>選項。

- **`--configfile <FILE>`**

  要用於還原作業的 NuGet 組態檔 (*nuget.config*)。

- **`--disable-parallel`**

  停用平行還原多個專案。

- **`--force`**

  即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

- **`--force-evaluate`**

  強制還原以重新評估所有依賴項,即使鎖檔已存在也是如此。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--ignore-failed-sources`**

  如果有套件符合版本需求，則只會警告有關失敗的來源。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作 (例如完成驗證)。 自 .NET Core 2.1.400 起。

- **`--lock-file-path <LOCK_FILE_PATH>`**

  寫入項目鎖定檔的輸出位置。 預設情況下,這是*PROJECT_ROOT\包.lock.json*。

- **`--locked-mode`**

  不允許更新項目鎖定檔。

- **`--no-cache`**

  指定不要快取套件和 HTTP 要求。

- **`--no-dependencies`**

  在還原包含專案對專案 (P2P) 參考的專案時，會還原根專案，而非參考。

- **`--packages <PACKAGES_DIRECTORY>`**

  指定已還原套件的目錄。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  指定套件還原的執行階段。 這用來針對 *.csproj* 檔案內 `<RuntimeIdentifiers>` 標記中未明確列出的執行階段還原套件。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 多次指定這個選項來提供多個 RID。

- **`-s|--source <SOURCE>`**

  指定要在還原作業期間使用的 NuGet 套件來源。 此設定將覆蓋*nuget.config*檔中指定的所有來源。 多次指定這個選項，即可提供多個來源。

- **`--use-lockfile`**

  使項目鎖定檔能夠生成並與還原一起使用。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值為 `minimal`。

## <a name="examples"></a>範例

- 還原目前目錄中專案的相依性和工具︰

  ```dotnetcli
  dotnet restore
  ```

- 回復指定路徑中找到`app1`的項目的相依項與工具:

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- 使用此檔案路徑回復目前的目錄中項目的相依項與工具:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- 使用為來源的兩個檔案路徑還原目前的目錄中項目的相依項與工具:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- 還原目前的目錄中項目的相依項與工具,顯示詳細輸出:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
