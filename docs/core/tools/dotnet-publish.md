---
title: dotnet publish 命令
description: dotnet 發佈命令將 .NET Core 專案或解決方案發佈到目錄。
ms.date: 02/24/2020
ms.openlocfilehash: 26dda33d04f3f7a23805627708b55233ef4e87ef
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242838"
---
# <a name="dotnet-publish"></a>dotnet publish

**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet publish`- 將應用程式及其依賴項發佈到資料夾以部署到託管系統。

## <a name="synopsis"></a>概要

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-p:PublishReadyToRun] [-p:PublishSingleFile]
    [-p:PublishTrimmed] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>描述

`dotnet publish` 會編譯應用程式，讀取在其專案檔中指定的相依性，然後將產生的一組檔案發行到目錄中。 此輸出包含下列資產：

- 組件中的中繼語言 (IL) 程式碼，副檔名為 *dll*。
- 包含專案的所有依賴項的 *.deps.json*檔。
- 一個 *.runtimeconfig.json*檔,用於指定應用程式期望的共用運行時以及運行時的其他配置選項(例如,垃圾回收類型)。
- 應用程式的相依性，這些相依性會從 NuGet 快取複製到輸出資料夾。

`dotnet publish`　命令的輸出已準備好部署到裝載系統 (例如伺服器、電腦、Mac、膝上型電腦) 以供執行。 這是準備應用程式以供部署的唯一正式支援的方法。 根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。 有關詳細資訊,請參閱發佈[.NET 核心應用 ,以及 .NET 核心 CLI](../deploying/deploy-with-cli.md)。

### <a name="msbuild"></a>MSBuild

`dotnet publish` 命令會呼叫 MSBuild，這會叫用 `Publish` 目標。 所有傳遞給 `dotnet publish` 的參數都會傳遞給 MSBuild。 `-c` 和 `-o` 參數會分別對應至 MSBuild 的 `Configuration` 和 `OutputPath` 屬性。

該`dotnet publish`指令接受 MSBuild`-p`選項,`-l`例如用於設定屬性 和定義記錄器。 例如,可以使用: 設定 MSBuild 屬性`-p:<NAME>=<VALUE>`。 還可以透過參考 *.pubxml*檔來設定與發佈相關的屬性,例如:

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

如需詳細資訊，請參閱下列資源：

- [MSBuild 指令列參考](/visualstudio/msbuild/msbuild-command-line-reference)
- [視覺化工作室發佈設定檔 (.pubxml) ASP.NET核心應用部署](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>引數

- **`PROJECT|SOLUTION`**

  要發佈的專案或解決方案。
  
  * `PROJECT`是[C#、F#](csproj.md)或 Visual Basic 專案檔的路徑和檔名,或包含 C#、F# 或 Visual Basic 專案檔的目錄的路徑。 如果未指定目錄,則預設為當前目錄。

  * `SOLUTION`是解決方案檔 *(.sln*副檔名) 的路徑和檔名,或包含解決方案檔的目錄的路徑。 如果未指定目錄,則預設為當前目錄。 自 .NET Core 3.0 SDK 起提供。

## <a name="options"></a>選項。

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 大多數項目的預設值為,`Debug`但您可以覆蓋專案中的生成配置設置。

- **`-f|--framework <FRAMEWORK>`**

  發行所指定[目標架構](../../standard/frameworks.md)的應用程式。 您必須在專案檔中指定此目標架構。

- **`--force`**

  即使最後的還原成功，仍強制解析所有相依性。 指定這個旗標等同於刪除 *project.assets.json* 檔案。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--interactive`**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 自 .NET Core 3.0 SDK 起提供。

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  指定一或多個[目標資訊清單](../deploying/runtime-store.md)，用以修剪應用程式發行的套件集。 清單檔是[`dotnet store`命令](dotnet-store.md)的輸出的一部分。 若要指定多個資訊清單，請為每個資訊清單新增 `--manifest` 選項。

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
  
  如果未指定,它預設為 *[project_file_folder]/bin/[配置]/[框架]/發佈/* 對於與運行時相關的可執行檔和跨平臺二進位檔案。 它預設為 *[project_file_folder]/bin/[配置]/[框架]/[運行時]/發佈/* 獨立執行檔。

  在 Web 專案中,如果輸出資料夾位於專案資料夾中,`dotnet publish`則連續 命令會導致嵌套輸出資料夾。 例如,如果項目資料夾是*我的專案*,並且發佈輸出資料夾是我的*專案/發佈*`dotnet publish`, 並且您運行兩次,則第二次運行將內容檔(如 *.config*和 *.json*檔)放入*我的專案/發佈/發佈*中。 為避免嵌套發佈資料夾,請指定不直接位於專案資料夾下的發佈資料夾,或從專案中排除發佈資料夾。 要排除名為 publish*輸出*的發佈資料夾,將以下`PropertyGroup`元素新增到 *.csproj*檔中的元素:

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - .NET 核心 3.x SDK 及更高版本
  
    如果在發佈專案時指定了相對路徑,則生成的輸出目錄與當前工作目錄相關,而不是與專案檔位置相關。

    如果在發佈解決方案時指定了相對路徑,則所有專案的所有輸出都進入相對於當前工作目錄的指定資料夾。 要使發佈輸出轉到每個項目的單獨資料夾,請使用 msbuild`PublishDir`屬性`--output`而不是選項 指定相對路徑。 例如,`dotnet publish -p:PublishDir=.\publish`將每個項目的發佈輸出發送到包含專案檔`publish`的 資料夾下的資料夾。

  - .NET 核心 2.x SDK
  
    如果在發佈專案時指定了相對路徑,則生成的輸出目錄相對於專案檔位置,而不是當前工作目錄。

    如果在發佈解決方案時指定了相對路徑,則每個項目的輸出將相對於專案檔位置進入一個單獨的資料夾。 如果在發佈解決方案時指定了絕對路徑,則所有專案的發佈輸出都將進入指定的資料夾。

- **`-p:PublishReadyToRun`**

  將應用程式程式集編譯為 ReadyToRun (R2R) 格式。 R2R 是一種預先(AOT) 編譯。 有關詳細資訊,請參閱[「準備運行圖像](../whats-new/dotnet-core-3-0.md#readytorun-images)」。。 自 .NET Core 3.0 SDK 起提供。

  我們建議您在發佈設定檔中而不是在命令列中指定此選項。 有關詳細資訊,請參閱[MSBuild](#msbuild)。

- **`-p:PublishSingleFile`**

  將應用打包到特定於平臺的單檔可執行檔中。 可執行檔是自提取的,包含運行應用所需的所有依賴項(包括本機)。 第一次執行應用程式時，系統會將應用程式解壓縮到以應用程式名稱和組建識別碼為基礎的目錄。 再次執行應用程式時的啟動速度會更快。 除非使用新版本,否則應用程式不需要第二次提取自身。 自 .NET Core 3.0 SDK 起提供。

  如需單一檔案發佈的詳細資訊，請參閱[單一檔案搭配程式設計文件](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md)。

  我們建議您在發佈設定檔中而不是在命令列中指定此選項。 有關詳細資訊,請參閱[MSBuild](#msbuild)。

- **`-p:PublishTrimmed`**

  修剪未使用的庫以減小發佈自包含可執行檔時應用的部署大小。 關於詳細資訊,請參考[修剪自包含部署及執行檔](../deploying/trim-self-contained.md)。 自 .NET Core 3.0 SDK 起提供。

  我們建議您在發佈設定檔中而不是在命令列中指定此選項。 有關詳細資訊,請參閱[MSBuild](#msbuild)。

- **`--self-contained [true|false]`**

  使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。 預設值是`true`指定運行時識別碼,並且專案是可執行專案(不是庫專案)。 有關詳細資訊,請參閱[.NET 核心應用程式發佈](../deploying/index.md)和[發佈 .NET 核心應用程式與 .NET 核心 CLI](../deploying/deploy-with-cli.md)。

  如果使用這個選項不指定`true``false`或 ,則預設`true`值為 。 在這種情況下,不要立即將解決方案或專案參數放在`--self-contained`之後,`true`因為`false`或預期處於該位置。

- **`--no-self-contained`**

  相當於 `--self-contained false`。 自 .NET Core 3.0 SDK 起提供。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  發行所指定執行階段的應用程式。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 有關詳細資訊,請參閱[.NET 核心應用程式發佈](../deploying/index.md)和[發佈 .NET 核心應用程式與 .NET 核心 CLI](../deploying/deploy-with-cli.md)。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值為 `minimal`。

- **`--version-suffix <VERSION_SUFFIX>`**

  定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。

## <a name="examples"></a>範例

- 建立目前目錄中的項目建立[與執行時相關的跨平台二進位檔案](../deploying/index.md#produce-a-cross-platform-binary):

  ```dotnetcli
  dotnet publish
  ```

  從 .NET Core 3.0 SDK 開始,此範例還會為目前平台建立[與執行時相關的可執行檔](../deploying/index.md#publish-runtime-dependent)。

- 為目前的目錄中建立的項目為特定執行時建立[自包含可執行檔](../deploying/index.md#publish-self-contained):

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  RID 必須位於項目檔中。

- 為目前目錄中的項目為特定平台建立[與執行時相關的執行檔](../deploying/index.md#publish-runtime-dependent):

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  RID 必須位於項目檔中。 此範例適用於 .NET Core 3.0 SDK 和更高版本。

- 在目前的目錄中發行項目,用於特定執行時和目標框架:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- 發佈指定的項目檔:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- 發佈目前的應用程式,但不還原專案到專案 (P2P) 引用,只是還原操作期間的根專案:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>另請參閱

- [.NET 核心應用程式發佈概述](../deploying/index.md)
- [使用 .NET 核心 CLI 發佈 .NET 核心應用](../deploying/deploy-with-cli.md)
- [目標 Framework](../../standard/frameworks.md)
- [執行時識別器 (RID) 目錄](../rid-catalog.md)
- [使用 macOS Catalina 公證](../install/macos-notarization-issues.md)
- [已發布應用程式的目錄結構](/aspnet/core/hosting/directory-structure)
- [MSBuild 指令列參考](/visualstudio/msbuild/msbuild-command-line-reference)
- [視覺化工作室發佈設定檔 (.pubxml) ASP.NET核心應用部署](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
- [ILLInk.工作](https://aka.ms/dotnet-illink)
