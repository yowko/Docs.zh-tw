---
title: dotnet publish 命令
description: dotnet publish 命令會將 .NET Core 專案發行到目錄中。
ms.date: 05/29/2018
ms.openlocfilehash: f9fea1a30e349ef949078e881756e2520d79ccbf
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969833"
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet publish` - 將應用程式與其相依性封裝至資料夾中，以部署至主機系統。

## <a name="synopsis"></a>概要

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>描述

`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。 此輸出包含下列資產：

- 組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。
- *.deps.json* 檔案，其中包含專案的所有相依性。
- 指定應用程式預期之共用執行階段的 *.runtime.config.json* 檔案，以及適用於執行階段的其他設定選項 (例如記憶體回收類型)。
- 應用程式的相依性，這些相依性會從 NuGet 快取複製到輸出資料夾。

`dotnet publish`　命令的輸出已準備好部署到裝載系統 (例如伺服器、電腦、Mac、膝上型電腦) 以供執行。 這是準備應用程式以供部署的唯一正式支援的方法。 根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。 針對已發行應用程式的目錄結構，請參閱[目錄結構 (英文)](/aspnet/core/hosting/directory-structure)。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>引數

`PROJECT`

要發佈的專案。 它是 [C#](csproj.md)、F# 或 Visual Basic 專案檔的路徑與檔案名稱，或包含 C#、F# 或 Visual Basic 專案檔之目錄的路徑。 如果未指定，則會預設為目前目錄。

## <a name="options"></a>選項

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值為 `Debug`。

`-f|--framework <FRAMEWORK>`

發行所指定[目標架構](../../standard/frameworks.md)的應用程式。 您必須在專案檔中指定此目標架構。

`--force`

即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

`-h|--help`

印出命令的簡短說明。

`--manifest <PATH_TO_MANIFEST_FILE>`

指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。 資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。 若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。 自 .NET Core 2.0 SDK 開始提供此選項。

`--no-build`

不會在發佈前建置專案。 選項也會隱含設定 `--no-restore` 旗標。

`--no-dependencies`

忽略專案對專案參考，並且只還原根專案。

`--no-restore`

執行命令時，不會執行隱含還原。

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

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值為 `Debug`。

`-f|--framework <FRAMEWORK>`

發行所指定[目標架構](../../standard/frameworks.md)的應用程式。 您必須在專案檔中指定此目標架構。

`--force`

即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

`-h|--help`

印出命令的簡短說明。

`--manifest <PATH_TO_MANIFEST_FILE>`

指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。 資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。 若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。 自 .NET Core 2.0 SDK 開始提供此選項。

`--no-dependencies`

忽略專案對專案參考，並且只還原根專案。

`--no-restore`

執行命令時，不會執行隱含還原。

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

定義組建組態。 預設值為 `Debug`。

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

- [目標架構](../../standard/frameworks.md)
- [執行階段識別項 (RID) 目錄](../rid-catalog.md)
