---
title: dotnet build 命令
description: dotnet build 命令會建置專案和其所有相依性。
ms.date: 04/24/2019
ms.openlocfilehash: 6564aacbe520797b47095929cfe72c6b180b99a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632127"
---
# <a name="dotnet-build"></a>dotnet build

**本文適用於：✓** .NET Core 1.x SDK 及更新版本

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>名稱

`dotnet build` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>說明

`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。 二進位檔將專案程式碼包含在副檔名為 *.dll* 的中繼語言 (IL) 檔案中，以及副檔名為 *.pdb* 且用於偵錯的符號檔。 產生相依性的 JSON 檔案 ( *\*.deps.json*)，其中列出應用程式的相依性。 產生 *\*.runtimeconfig.json* 檔案，其中指定應用程式的共用執行階段及其版本。

如果專案對於第三方有相依性 (例如來自 NuGet 的程式庫)，這些相依性將會從 NuGet 快取解析，而不會透過專案的建置輸出提供。 因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。 這與 .NET Framework 的行為相反。在 .NET Framework 中，建置可執行檔專案 (應用程式) 所產生的輸出，可在任何已安裝 .NET Framework 的電腦上執行。 若要在 .NET Core 中擁有類似體驗，您需要使用 [dotnet publish](dotnet-publish.md) 命令。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。

建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。 檔案會在 [`dotnet restore`](dotnet-restore.md) 執行時建立。 如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。 以前使用 .NET Core 1.x SDK 時，您需要先明確執行 `dotnet restore` 再執行 `dotnet build`。 自 .NET Core 2.0 SDK 開始，`dotnet restore` 會在您執行 `dotnet build` 時以隱含方式執行。 如果您想要在執行 build 命令時停用隱含還原，您可以跳過 `--no-restore` 選項。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。 下列範例顯示會產生可執行程式碼的專案：

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

若要產生程式庫，只要省略 `<OutputType>` 屬性即可。 建置輸出的主要差別在於，程式庫的 IL DLL 不包含進入點，而且無法執行。

### <a name="msbuild"></a>MSBuild

`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。 如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。

除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `-p`，以及用於定義記錄器的 `-l`。 如需這些選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。 或者，您也可以使用 [dotnet msbuild](dotnet-msbuild.md) 命令。

執行 `dotnet build` 相當於 `dotnet msbuild -restore -target:Build`。

## <a name="arguments"></a>引數

`PROJECT | SOLUTION`

要建置的專案或方案檔。 若未指定專案或解決方案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 或 *sln* 的檔案，並使用該檔案。

## <a name="options"></a>選項

* **`-c|--configuration {Debug|Release}`**

  定義組建組態。 預設值為 `Debug`。

* **`-f|--framework <FRAMEWORK>`**

  針對特定[架構](../../standard/frameworks.md)進行編譯。 架構必須定義於[專案檔](csproj.md)中。

* **`--force`**

  即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。 自 .NET Core 2.0 SDK 起提供使用。

* **`-h|--help`**

  印出命令的簡短說明。

* **`--interactive`**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 自 .NET Core 3.0 SDK 起提供使用。

* **`--no-dependencies`**

  忽略專案對專案 (P2P) 參考，並且只建置指定的根專案。

* **`--no-incremental`**

  針對累加建置，將建置標示為不安全。 此旗標會關閉累加編譯，並強制全新重建專案的相依性關係圖。

* **`--no-logo`**

  不要顯示程式啟始橫幅或著作權訊息。 自 .NET Core 3.0 SDK 起提供使用。

* **`--no-restore`**

  建置期間不會執行隱含還原。 自 .NET Core 2.0 SDK 起提供使用。

* **`-o|--output <OUTPUT_DIRECTORY>`**

  在其中放置已建置的二進位檔的目錄。 當您指定這個選項時，也需要定義 `--framework`。 如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  指定目標執行階段。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

* **`-v|--verbosity <LEVEL>`**

  設定 MSBuild 詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設為 `minimal`。

* **`--version-suffix <VERSION_SUFFIX>`**

  設定要在建置專案時使用的 `$(VersionSuffix)` 屬性值。 這只有在沒有設定 `$(Version)` 屬性時才能運作。 接著，`$(Version)` 會設為 `$(VersionPrefix)` 加上 `$(VersionSuffix)`，並以破折號區隔。

## <a name="examples"></a>範例

* 建置專案和其相依性：

  ```console
  dotnet build
  ```

* 使用發行組態來建置專案和其相依性︰

  ```console
  dotnet build --configuration Release
  ```

* 針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 18.04)：

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* 建置專案，並在還原作業期間使用指定的 NuGet 套件來源 (.NET Core 2.0 SDK 和更新版本)：

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* 建置專案並設定 1.2.3.4 版本作為建置參數：

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
