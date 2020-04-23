---
title: dotnet build 命令
description: dotnet build 命令會建置專案和其所有相依性。
ms.date: 02/14/2020
ms.openlocfilehash: 1022df059493c7e045f81d4be93dff2fdab77eb1
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102836"
---
# <a name="dotnet-build"></a>dotnet build

**本文適用於:✔️** .NET Core 2.x SDK 和更高版本

## <a name="name"></a>名稱

`dotnet build` - 建置專案和其所有相依性。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a>描述

`dotnet build` 命令會將專案及其相依性建置成一組二進位檔。 二進位檔包括專案代碼的中間語言 (IL) 檔案與 *.dll*副檔名。  根據項目類型和設定,可能會包括其他檔,例如:

- 如果項目類型是目標 .NET Core 3.0 或更高版本的可執行檔,則可用於運行應用程式的可執行檔。
- 用於使用 *.pdb*擴展名進行除錯的符號檔。
- *.deps.json*檔,其中列出了應用程式或庫的依賴項。
- *.運行時config.json*檔,該檔指定應用程式的共用運行時及其版本。
- 項目所依賴的其他庫(通過專案引用或 NuGet 包引用)。

對於面向早於 .NET Core 3.0 版本的可執行專案,NuGet 的庫依賴項通常不會複製到輸出資料夾。  它們在運行時從 NuGet 全域包資料夾中解析。 因此，`dotnet build` 產生的結果尚未準備好轉移到另一部電腦來執行。 要建立可部署的應用程式的版本,需要發佈它(例如,使用[dotnet發佈](dotnet-publish.md)命令)。 有關詳細資訊,請參閱[.NET 核心應用程式部署](../deploying/index.md)。

對於針對 .NET Core 3.0 及更高版本的可執行專案,庫依賴項將複製到輸出資料夾。 這意味著,如果沒有任何其他特定於發佈的邏輯(如 Web 專案),則生成輸出應該是可部署的。

### <a name="implicit-restore"></a>隱式還原

建置會需要 *project.assets.json* 檔案，其中列出您應用程式的相依性。 執行時[`dotnet restore`](dotnet-restore.md)將創建該檔。 如果沒有資產檔案，工具就會因為無法解析參考組件而發生錯誤。

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a>執行或函式庫輸出

專案是否為可執行檔可透過專案檔中的 `<OutputType>` 屬性來判斷。 下列範例顯示會產生可執行程式碼的專案：

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

要產生函式庫,`<OutputType>`省略屬性或將其值`Library`變更為 。 庫的 IL DLL 不包含入口點,無法執行。

### <a name="msbuild"></a>MSBuild

`dotnet build` 使用 MSBuild 來建置專案，因此同時支援平行和累加建置。 如需詳細資訊，請參閱[累加建置](/visualstudio/msbuild/incremental-builds)。

除了其選項，`dotnet build` 命令也接受 MSBuild 選項，例如用於設定屬性的 `-p`，以及用於定義記錄器的 `-l`。 如需這些選項的詳細資訊，請參閱 [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)。 或者，您也可以使用 [dotnet msbuild](dotnet-msbuild.md) 命令。

執行`dotnet build`等效於`dotnet msbuild -restore`運行 ;但是,輸出的默認詳細程度是不同的。

## <a name="arguments"></a>引數

`PROJECT | SOLUTION`

要建置的專案或方案檔。 若未指定專案或解決方案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 或 *sln* 的檔案，並使用該檔案。

## <a name="options"></a>選項。

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 大多數項目的預設值為,`Debug`但您可以覆蓋專案中的生成配置設置。

- **`-f|--framework <FRAMEWORK>`**

  針對特定[架構](../../standard/frameworks.md)進行編譯。 架構必須定義於[專案檔](csproj.md)中。

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

  在其中放置已建置的二進位檔的目錄。 如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。  對於具有多個目標框架的專案(通過`TargetFrameworks`屬性),還需要在指定此選項`--framework`時 定義。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  指定目標執行階段。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。

- **`-v|--verbosity <LEVEL>`**

  設定 MSBuild 詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值為 `minimal`。

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

- 建置專案，並在還原作業期間使用指定的 NuGet 套件來源 (.NET Core 2.0 SDK 和更新版本)：

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- 建置專案並使用 `-p` [MSBuild 選項](#msbuild) 將 1.2.3.4 版設定為組建參數：

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
