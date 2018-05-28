---
title: dotnet publish 命令 - .NET Core CLI
description: dotnet publish 命令會將 .NET Core 專案發行到目錄中。
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.openlocfilehash: 5e7ce5ce1240f03f53f6e120dfce53d15917425f
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2018
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet publish` - 將應用程式與其相依性封裝至資料夾中，以部署至主機系統。

## <a name="synopsis"></a>概要

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>描述

`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。 輸出會包含下列內容：

* 組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。
* *.deps.json* 檔案，其中包含專案的所有相依性。
* *.runtime.config.json* 檔案，指定應用程式預期的共用執行階段，以及執行階段的其他組態選項 (例如記憶體回收類型)。
* 應用程式的相依性。 這些相依性會從 NuGet 快取複製到輸出資料夾。

`dotnet publish` 命令的輸出已準備好部署至主機系統 (例如，伺服器、電腦、Mac、膝上型電腦) 以執行，且是準備要進行部署之應用程式的唯一正式支援方式。 根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。 針對已發行應用程式的目錄結構，請參閱[目錄結構 (英文)](/aspnet/core/hosting/directory-structure)。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>引數

`PROJECT`

要發行的專案，如果未指定，則預設為目前目錄。

## <a name="options"></a>選項

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值是 `Debug`。

`-f|--framework <FRAMEWORK>`

發行所指定[目標架構](../../standard/frameworks.md)的應用程式。 您必須在專案檔中指定此目標架構。

`--force`

即使最後的還原成功，仍強制解析所有相依性。 這相當於刪除 *project.assets.json* 檔案。

`-h|--help`

印出命令的簡短說明。

`--manifest <PATH_TO_MANIFEST_FILE>`

指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。 資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。 若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。 自 .NET Core 2.0 SDK 開始提供此選項。

`--no-dependencies`

忽略專案對專案參考，並且只還原根專案。

`--no-restore`

執行命令時，不執行隱含的還原。

`-o|--output <OUTPUT_DIRECTORY>`

指定輸出目錄的路徑。 如果未指定，預設為 *./bin/[configuration]/[framework]/publish/* (適用於架構相依的部署) 或 *./bin/[configuration]/[framework]/[runtime]/publish/* (適用於獨立部署)。
如果路徑是相對的，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。

`--self-contained`

使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。 如已指定執行階段識別碼，則其預設值是 `true`。 如需不同部署類型的詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。

`-r|--runtime <RUNTIME_IDENTIFIER>`

發行所指定執行階段的應用程式。 建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 預設值為發行[與 Framework 相依的部署 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

`--version-suffix <VERSION_SUFFIX>`

定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值是 `Debug`。

`-f|--framework <FRAMEWORK>`

發行所指定[目標架構](../../standard/frameworks.md)的應用程式。 您必須在專案檔中指定此目標架構。

`-h|--help`

印出命令的簡短說明。

`--manifest <PATH_TO_MANIFEST_FILE>`

指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。 資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。 若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。 自 .NET Core 2.0 SDK 開始提供此選項。

`-o|--output <OUTPUT_DIRECTORY>`

指定輸出目錄的路徑。 如果未指定，預設為 *./bin/[configuration]/[framework]/publish/* (適用於架構相依的部署) 或 *./bin/[configuration]/[framework]/[runtime]/publish/* (適用於獨立部署)。
如果路徑是相對的，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。

`-r|--runtime <RUNTIME_IDENTIFIER>`

發行所指定執行階段的應用程式。 建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 預設值為發行[與 Framework 相依的部署 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd)。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

`--version-suffix <VERSION_SUFFIX>`

定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。

---

## <a name="examples"></a>範例

發行目前目錄中的專案：

`dotnet publish`

使用指定的專案檔發行應用程式：

`dotnet publish ~/projects/app1/app1.csproj`

使用 `netcoreapp1.1` 架構發行目前目錄中的專案：

`dotnet publish --framework netcoreapp1.1`

使用 `netcoreapp1.1` 架構和 `OS X 10.10` 的執行階段來發行目前應用程式 (您必須在專案檔中列出這個 RID)。

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

發行目前的應用程式，但不還原專案對專案 (P2P) 的參考，還原作業期間只有根專案 (.NET Core SDK 2.0 及更新版本)：

`dotnet publish --no-dependencies`

## <a name="see-also"></a>另請參閱

* [目標架構](../../standard/frameworks.md)
* [執行階段識別項 (RID) 目錄](../rid-catalog.md)
