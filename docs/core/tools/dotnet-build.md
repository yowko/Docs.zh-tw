---
title: dotnet build 命令
description: dotnet build 命令會建置專案和其所有相依性。
ms.date: 02/14/2020
ms.openlocfilehash: cc8c6ed30dbf8ff0602fb19e5001f618a8380f16
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189950"
---
# <a name="dotnet-build"></a>dotnet build

本文 **適用于：** ✔️ .net CORE 2.x SDK 和更新版本

## <a name="name"></a>名稱

`dotnet build` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--source <SOURCE>]
    [-v|--verbosity <LEVEL>] [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a>Description

`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。 二進位檔包含中繼語言的專案程式碼 (IL) 檔案，副檔名為 *.dll* 。  視專案類型和設定而定，可能會包含其他檔案，例如：

- 可以用來執行應用程式的可執行檔（如果專案類型是以 .NET Core 3.0 或更新版本為目標的可執行檔）。
- 用來以 *.pdb* 副檔名進行偵錯工具的符號檔。
- 檔案 *上的.deps.js* ，其會列出應用程式或程式庫的相依性。
- 檔案 *上的.runtimeconfig.js* ，可指定共用執行時間及其版本的應用程式。
- 專案相依的其他程式庫 (透過專案參考或 NuGet 套件參考) 。

若是以 .NET Core 3.0 之前的版本為目標的可執行檔專案，來自 NuGet 的程式庫相依性通常不會複製到輸出檔案夾。  它們是在執行時間從 NuGet 全域套件資料夾解析。 因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。 若要建立可部署的應用程式版本，您需要將它發佈 (例如，使用 [dotnet publish](dotnet-publish.md) 命令) 。 如需詳細資訊，請參閱 [.Net 應用程式部署](../deploying/index.md)。

針對以 .NET Core 3.0 和更新版本為目標的可執行檔專案，會將程式庫相依性複製到輸出檔案夾。 這表示，如果沒有任何其他發佈特定邏輯 (例如 Web 專案有) ，則組建輸出應該是可部署的。

### <a name="implicit-restore"></a>隱含還原

建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。 當執行時，就會建立此檔案 [`dotnet restore`](dotnet-restore.md) 。 如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a>可執行檔或程式庫輸出

專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。 下列範例顯示會產生可執行程式碼的專案：

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

若要產生程式庫，請省略 `<OutputType>` 屬性，或將其值變更為 `Library` 。 程式庫的 IL DLL 不包含進入點，而且無法執行。

### <a name="msbuild"></a>MSBuild

`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。 如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。

除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `-p`，以及用於定義記錄器的 `-l`。 如需這些選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。 或者，您也可以使用 [dotnet msbuild](dotnet-msbuild.md) 命令。

執行 `dotnet build` 相當於執行 `dotnet msbuild -restore` ; 不過，輸出的預設詳細程度不同。

## <a name="arguments"></a>引數

`PROJECT | SOLUTION`

要建置的專案或方案檔。 若未指定專案或解決方案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 或 *sln* 的檔案，並使用該檔案。

## <a name="options"></a>選項

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 大部分專案的預設值為 `Debug` ，但您可以覆寫專案中的組建設定。

- **`-f|--framework <FRAMEWORK>`**

  針對特定[架構](../../standard/frameworks.md)進行編譯。 架構必須定義於[專案檔](../project-sdk/overview.md)中。

- **`--force`**

  即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--interactive`**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 自 .NET Core 3.0 SDK 起提供。

- **`--no-dependencies`**

  忽略專案對專案 (P2P) 參考，並且只建置指定的根專案。

- **`--no-incremental`**

  針對累加建置，將建置標示為不安全。 此旗標會關閉累加編譯，並強制全新重建專案的相依性關係圖。

- **`--no-restore`**

  建置期間不會執行隱含還原。

- **`--nologo`**

  不要顯示程式啟始橫幅或著作權訊息。 自 .NET Core 3.0 SDK 起提供。

- **`-o|--output <OUTPUT_DIRECTORY>`**

  在其中放置已建置的二進位檔的目錄。 如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。  針對具有多個目標 framework 的專案 (透過 `TargetFrameworks` 屬性) ，您也需要在 `--framework` 指定此選項時定義。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  指定目標執行階段。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

- **`--source <SOURCE>`**

  要在還原作業期間使用的 NuGet 套件來源 URI。

- **`-v|--verbosity <LEVEL>`**

  設定 MSBuild 詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設為 `minimal`。

- **`--version-suffix <VERSION_SUFFIX>`**

  設定要在建置專案時使用的 `$(VersionSuffix)` 屬性值。 這只有在沒有設定 `$(Version)` 屬性時才能運作。 接著，`$(Version)` 會設為 `$(VersionPrefix)` 加上 `$(VersionSuffix)`，並以破折號區隔。

## <a name="examples"></a>範例

- 建置專案和其相依性：

  ```dotnetcli
  dotnet build
  ```

- 使用發行組態來建置專案和其相依性︰

  ```dotnetcli
  dotnet build --configuration Release
  ```

- 針對特定執行階段，建置專案和其相依性 (在此範例中為 Ubuntu 18.04)：

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- 建立專案，並在還原作業期間使用指定的 NuGet 套件來源：

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- 建置專案並使用 `-p` [MSBuild 選項](#msbuild) 將 1.2.3.4 版設定為組建參數：

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
