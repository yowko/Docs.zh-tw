---
title: dotnet publish 命令
description: Dotnet publish 命令會將 .NET Core 專案或方案發行至目錄。
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156994"
---
# <a name="dotnet-publish"></a>dotnet publish

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>名稱

`dotnet publish`-將應用程式及其相依性發佈至資料夾，以部署至主控系統。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>描述

`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。 此輸出包含下列資產：

- 組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。
- 包含專案所有相依性的 *.deps.json json*檔案。
- *.Runtimeconfig.json json*檔案，指定應用程式預期的共用執行時間，以及執行時間的其他設定選項（例如垃圾收集類型）。
- 應用程式的相依性，這些相依性會從 NuGet 快取複製到輸出資料夾。

`dotnet publish`　命令的輸出已準備好部署到裝載系統 (例如伺服器、電腦、Mac、膝上型電腦) 以供執行。 這是準備應用程式以供部署的唯一正式支援的方法。 根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。

## <a name="arguments"></a>引數

- **`PROJECT|SOLUTION`**

  要發行的專案或方案。
  
  * `PROJECT` 是[C#](csproj.md)、 F#或 Visual Basic 專案檔的路徑和檔案名，或是包含C#、 F#或 Visual Basic 專案檔之目錄的路徑。 如果未指定目錄，則會預設為目前目錄。

  * `SOLUTION` 是方案檔（ *.sln*副檔名）的路徑和檔案名，或包含方案檔之目錄的路徑。 如果未指定目錄，則會預設為目前目錄。 **從 .NET Core 3.0 SDK 開始提供。** 

## <a name="options"></a>選項。

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 大部分專案的預設值都是 `Debug`，但您可以覆寫專案中的組建設定。

- **`-f|--framework <FRAMEWORK>`**

  發行所指定[目標架構](../../standard/frameworks.md)的應用程式。 您必須在專案檔中指定此目標架構。

- **`--force`**

  即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

- **`-h|--help`**

  印出命令的簡短說明。

- **從 .NET Core 3.0 SDK 開始提供`--interactive`。**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。 資訊清單檔是 [`dotnet store` 命令](dotnet-store.md)輸出的一部分。 若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。

- **`--no-build`**

  不會在發佈前建置專案。 選項也會隱含設定 `--no-restore` 旗標。

- **`--no-dependencies`**

  忽略專案對專案參考，並且只還原根專案。

- **從 .NET Core 3.0 SDK 開始提供`--nologo`。**

  不要顯示程式啟始橫幅或著作權訊息。 

- **`--no-restore`**

  執行命令時，不會執行隱含的還原。

- **`-o|--output <OUTPUT_DIRECTORY>`**

  指定輸出目錄的路徑。 如果未指定，則預設為 *./bin/[configuration]/[framework]/publish/(適用*，適用于執行時間相依的可執行檔和跨平臺二進位檔。 它預設為 *./bin/[configuration]/[framework]/[runtime]/publish/(適用*，適用于獨立的可執行檔。

  如果路徑是相對的，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。

- **`--self-contained [true|false]`**

  使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。 如果已指定執行時間識別碼，則預設值為 `true`。 如需詳細資訊，請參閱[.Net core 應用程式](../deploying/index.md)[使用 .NET Core CLI 發佈和發行 .net core](../deploying/deploy-with-cli.md)應用程式。

- **從 .NET Core 3.0 SDK 開始提供`--no-self-contained`。**

  相當於 `--self-contained false`。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  發行所指定執行階段的應用程式。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 如需詳細資訊，請參閱[.Net core 應用程式](../deploying/index.md)[使用 .NET Core CLI 發佈和發行 .net core](../deploying/deploy-with-cli.md)應用程式。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。

- **`--version-suffix <VERSION_SUFFIX>`**

  定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。

## <a name="examples"></a>範例

- 針對目前目錄中的專案建立[執行時間相依的跨平臺二進位](../deploying/index.md#produce-a-cross-platform-binary)檔：

  ```dotnetcli
  dotnet publish
  ```

  從 .NET Core 3.0 SDK 開始，此範例也會建立目前平臺的[執行時間相依可執行檔](../deploying/index.md#publish-runtime-dependent)。

- 針對特定執行時間，為目前目錄中的專案建立[獨立可執行檔](../deploying/index.md#publish-self-contained)：

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  RID 必須在專案檔中。

- 針對特定平臺，為目前目錄中的專案建立[執行時間相依的可執行檔](../deploying/index.md#publish-runtime-dependent)：

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  RID 必須在專案檔中。 這個範例適用于 .NET Core 3.0 SDK 和更新版本。

- 針對特定的執行時間和目標架構，在目前目錄中發佈專案：

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- 發行指定的專案檔：

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- 發行目前的應用程式，但不要在還原作業期間還原專案對專案（P2P）參考，只有根專案：

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>另請參閱

- [.NET Core 應用程式發行總覽](../deploying/index.md)
- [使用 .NET Core CLI 發佈 .NET Core 應用程式](../deploying/deploy-with-cli.md)
- [目標架構](../../standard/frameworks.md)
- [執行階段識別項 (RID) 目錄](../rid-catalog.md)
- 使用[MacOS Catalina Notarization](../install/macos-notarization-issues.md)如需詳細資訊，請參閱下列資源：
- [已發行應用程式的目錄結構](/aspnet/core/hosting/directory-structure)
