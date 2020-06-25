---
title: dotnet publish 命令
description: Dotnet publish 命令會將 .NET Core 專案或方案發行至目錄。
ms.date: 02/24/2020
ms.openlocfilehash: 61cfcf06586f3ac66526de69a17b8aef3cf0c795
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365579"
---
# <a name="dotnet-publish"></a>dotnet publish

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="name"></a>Name

`dotnet publish`-將應用程式及其相依性發佈至資料夾，以部署至主控系統。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a>描述

`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。 此輸出包含下列資產：

- 組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。
- 檔案*上的.deps.js* ，其中包含專案的所有相依性。
- .runtimeconfig.js檔案，指定應用程式預期的共用執行時間，以及運行*時間*的其他設定選項（例如垃圾收集類型）。
- 應用程式的相依性，這些相依性會從 NuGet 快取複製到輸出資料夾。

`dotnet publish`　命令的輸出已準備好部署到裝載系統 (例如伺服器、電腦、Mac、膝上型電腦) 以供執行。 這是準備應用程式以供部署的唯一正式支援的方法。 根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。 如需詳細資訊，請參閱[使用 .NET Core CLI 發佈 .Net Core 應用程式](../deploying/deploy-with-cli.md)。

### <a name="implicit-restore"></a>隱含還原

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a>MSBuild

`dotnet publish` 命令會呼叫 MSBuild，這會叫用 `Publish` 目標。 所有傳遞給 `dotnet publish` 的參數都會傳遞給 MSBuild。 `-c` 和 `-o` 參數會分別對應至 MSBuild 的 `Configuration` 和 `PublishDir` 屬性。

此 `dotnet publish` 命令接受 MSBuild 選項，例如 `-p` 用於設定屬性和 `-l` 定義記錄器。 例如，您可以使用下列格式來設定 MSBuild 屬性： `-p:<NAME>=<VALUE>` 。 您也可以參考 *.pubxml*檔案來設定發行相關屬性，例如：

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

如需詳細資訊，請參閱下列資源：

- [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)
- [Visual Studio ASP.NET Core 應用程式部署的發行設定檔（. .pubxml）](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>引數

- **`PROJECT|SOLUTION`**

  要發行的專案或方案。
  
  * `PROJECT`是[c #](csproj.md)、f # 或 Visual Basic 專案檔的路徑和檔案名，或是包含 c #、f # 或 Visual Basic 專案檔之目錄的路徑。 如果未指定目錄，則會預設為目前目錄。

  * `SOLUTION`是方案檔（*.sln*副檔名）的路徑和檔案名，或包含方案檔之目錄的路徑。 如果未指定目錄，則會預設為目前目錄。 自 .NET Core 3.0 SDK 起提供。

## <a name="options"></a>選項

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 大部分專案的預設值為 `Debug` ，但您可以覆寫專案中的組建設定。

- **`-f|--framework <FRAMEWORK>`**

  發行所指定[目標架構](../../standard/frameworks.md)的應用程式。 您必須在專案檔中指定此目標架構。

- **`--force`**

  即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--interactive`**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 自 .NET Core 3.0 SDK 起提供。

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。 資訊清單檔案是[ `dotnet store` 命令](dotnet-store.md)輸出的一部分。 若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。

- **`--no-build`**

  不會在發佈前建置專案。 選項也會隱含設定 `--no-restore` 旗標。

- **`--no-dependencies`**

  忽略專案對專案參考，並且只還原根專案。

- **`--nologo`**

  不要顯示程式啟始橫幅或著作權訊息。 自 .NET Core 3.0 SDK 起提供。

- **`--no-restore`**

  執行命令時，不會執行隱含還原。

- **`-o|--output <OUTPUT_DIRECTORY>`**

  指定輸出目錄的路徑。
  
  如果未指定，則預設為 *[project_file_folder]./bin/[configuration]/[framework]/publish/(適用*，適用于執行時間相依的可執行檔和跨平臺二進位檔。 針對獨立可執行檔，其預設為 *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/(適用*。

  在 Web 專案中，如果輸出檔案夾位於專案資料夾中，後續 `dotnet publish` 的命令會產生嵌套的輸出檔案夾。 例如，如果專案資料夾是*myproject*，且發行輸出檔案夾為*myproject/publish*，而您執行了 `dotnet publish` 兩次，則第二個執行會將內容檔案（例如 *.config*和*json*檔案）放在*myproject/publish/publish*中。 若要避免建立發行資料夾的嵌套，請指定不是**直接**在專案資料夾底下的 publish 資料夾，或是從專案中排除 publish 資料夾。 若要排除名為*publishoutput*的發行資料夾，請將下列元素新增至 `PropertyGroup` *.csproj*檔案中的專案：

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - .NET Core 3.x SDK 和更新版本
  
    如果在發行專案時指定相對路徑，則產生的輸出目錄會相對於目前的工作目錄，而不是專案檔位置。

    如果在發行方案時指定相對路徑，所有專案的所有輸出都會進入相對於目前工作目錄的指定資料夾。 若要讓 [發行輸出] 移至每個專案的個別資料夾，請使用 msbuild `PublishDir` 屬性（而非選項）來指定相對路徑 `--output` 。 例如， `dotnet publish -p:PublishDir=.\publish` 會將每個專案的發行輸出傳送至 `publish` 包含專案檔之資料夾下的資料夾。

  - .NET Core 2.x SDK
  
    如果在發行專案時指定相對路徑，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。

    如果在發行方案時指定相對路徑，則每個專案的輸出都會進入與專案檔位置相對的個別資料夾。 如果在發行方案時指定了絕對路徑，所有專案的所有發行輸出都會進入指定的資料夾。

- **`-p:PublishReadyToRun=true`**

  將應用程式元件編譯為 ReadyToRun （R2R）格式。 R2R 是一種預先(AOT) 編譯。 如需詳細資訊，請參閱[ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images)。 自 .NET Core 3.0 SDK 起提供。

  我們建議您在發行設定檔中指定這個選項，而不是在命令列上。 如需詳細資訊，請參閱[MSBuild](#msbuild)。

- **`-p:PublishSingleFile=true`**

  將應用程式封裝成平臺特定的單一檔案可執行檔。 可執行檔會自我解壓縮，並包含執行應用程式所需的所有相依性（包括原生）。 第一次執行應用程式時，系統會將應用程式解壓縮到以應用程式名稱和組建識別碼為基礎的目錄。 再次執行應用程式時的啟動速度會更快。 除非使用新版本，否則應用程式不需要第二次解壓縮。 自 .NET Core 3.0 SDK 起提供。

  如需單一檔案發佈的詳細資訊，請參閱[單一檔案搭配程式設計文件](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md)。

  我們建議您在發行設定檔中指定這個選項，而不是在命令列上。 如需詳細資訊，請參閱[MSBuild](#msbuild)。

- **`-p:PublishTrimmed=true`**

  在發行獨立的可執行檔時，修剪未使用的程式庫，以減少應用程式的部署大小。 如需詳細資訊，請參閱[修剪獨立部署和可執行檔](../deploying/trim-self-contained.md)。 自 .NET Core 3.0 SDK 起提供。

  我們建議您在發行設定檔中指定這個選項，而不是在命令列上。 如需詳細資訊，請參閱[MSBuild](#msbuild)。

- **`--self-contained [true|false]`**

  使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。 如果已 `true` 指定執行時間識別碼，而且專案是可執行檔專案（而不是程式庫專案），則預設值為。 如需詳細資訊，請參閱[.Net core 應用程式](../deploying/index.md)[使用 .NET Core CLI 發佈和發行 .net core](../deploying/deploy-with-cli.md)應用程式。

  如果在不指定或的情況下使用此選項 `true` `false` ，則預設值為 `true` 。 在此情況下，請不要在之後立即放置方案或專案引數 `--self-contained` ，因為 `true` `false` 在該位置中必須有或。

- **`--no-self-contained`**

  相當於 `--self-contained false`。 自 .NET Core 3.0 SDK 起提供。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  發行所指定執行階段的應用程式。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 如需詳細資訊，請參閱[.Net core 應用程式](../deploying/index.md)[使用 .NET Core CLI 發佈和發行 .net core](../deploying/deploy-with-cli.md)應用程式。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值為 `minimal`。

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
- [執行時間識別碼（RID）目錄](../rid-catalog.md)
- [使用 macOS Catalina Notarization](../install/macos-notarization-issues.md)
- [已發行應用程式的目錄結構](/aspnet/core/hosting/directory-structure)
- [MSBuild 命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)
- [Visual Studio ASP.NET Core 應用程式部署的發行設定檔（. .pubxml）](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
- [ILLInk。工作](https://aka.ms/dotnet-illink)
