---
title: dotnet publish 命令
description: dotnet 發佈命令將 .NET Core 專案或解決方案發佈到目錄。
ms.date: 02/24/2020
ms.openlocfilehash: c34618409c9a539043c84c7e03daa8aa249d64f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146551"
---
# <a name="dotnet-publish"></a>dotnet publish

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

## <a name="name"></a>名稱

`dotnet publish`- 將應用程式及其依賴項發佈到資料夾以部署到託管系統。

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
- 包含專案的所有依賴項的 *.deps.json*檔。
- 一個 *.runtimeconfig.json*檔，用於指定應用程式期望的共用運行時以及運行時的其他配置選項（例如，垃圾回收類型）。
- 應用程式的相依性，這些相依性會從 NuGet 快取複製到輸出資料夾。

`dotnet publish`　命令的輸出已準備好部署到裝載系統 (例如伺服器、電腦、Mac、膝上型電腦) 以供執行。 這是準備應用程式以供部署的唯一正式支援的方法。 根據專案指定的部署類型，主機系統上可能會安裝 (或不安裝) .NET Core 共用執行階段。

## <a name="arguments"></a>引數

- **`PROJECT|SOLUTION`**

  要發佈的專案或解決方案。
  
  * `PROJECT`是[C#、F#](csproj.md)或 Visual Basic 專案檔案的路徑和檔案名，或包含 C#、F# 或 Visual Basic 專案檔案的目錄的路徑。 如果未指定目錄，則預設為目前的目錄。

  * `SOLUTION`是解決方案檔 *（.sln*副檔名） 的路徑和檔案名，或包含解決方案檔的目錄的路徑。 如果未指定目錄，則預設為目前的目錄。 自 .NET Core 3.0 SDK 起提供。

## <a name="options"></a>選項。

- **`-c|--configuration <CONFIGURATION>`**

  定義組建組態。 大多數專案的預設值為 ，`Debug`但您可以覆蓋專案中的組建組態設置。

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

  指定輸出目錄的路徑。 如果未指定，它預設為 *./bin/[配置]/[框架]/發佈/* 對於與運行時相關的可執行和跨平臺二進位檔案。 它預設為 *./bin/[配置]/[框架]/[運行時]/發佈/* 對於自包含可執行檔。

  如果路徑是相對的，則產生的輸出目錄會相對於專案檔案位置，而不是目前的工作目錄。

- **`--self-contained [true|false]`**

  使用您的應用程式發行 .NET Core 執行階段，讓目標電腦不需要安裝執行階段。 預設值為`true`指定運行時識別碼。 有關詳細資訊，請參閱[.NET 核心應用程式發佈](../deploying/index.md)和[發佈 .NET 核心應用程式與 .NET 核心 CLI](../deploying/deploy-with-cli.md)。

- **`--no-self-contained`**

  相當於 `--self-contained false`。 自 .NET Core 3.0 SDK 起提供。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  發行所指定執行階段的應用程式。 如需執行階段識別項 (RID) 清單，請參閱 [RID 目錄](../rid-catalog.md)。 有關詳細資訊，請參閱[.NET 核心應用程式發佈](../deploying/index.md)和[發佈 .NET 核心應用程式與 .NET 核心 CLI](../deploying/deploy-with-cli.md)。

- **`-v|--verbosity <LEVEL>`**

  設定命令的詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值為 `minimal`。

- **`--version-suffix <VERSION_SUFFIX>`**

  定義要取代專案檔案的版本欄位中之星號 (`*`) 的版本尾碼。

## <a name="examples"></a>範例

- 為目前的目錄中的專案創建[與運行時相關的跨平臺二進位檔案](../deploying/index.md#produce-a-cross-platform-binary)：

  ```dotnetcli
  dotnet publish
  ```

  從 .NET Core 3.0 SDK 開始，此示例還會為當前平臺創建[與運行時相關的可執行檔](../deploying/index.md#publish-runtime-dependent)。

- 為目前的目錄中的專案為特定運行時創建[自包含可執行檔](../deploying/index.md#publish-self-contained)：

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  RID 必須位於專案檔案中。

- 為目前的目錄中的專案為特定平臺創建[與運行時相關的可執行檔](../deploying/index.md#publish-runtime-dependent)：

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  RID 必須位於專案檔案中。 此示例適用于 .NET Core 3.0 SDK 和更高版本。

- 在目前的目錄中發佈專案，用於特定運行時和目標框架：

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- 發佈指定的專案檔案：

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- 發佈當前應用程式，但不還原專案到專案 （P2P） 引用，只是還原操作期間的根專案：

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>另請參閱

- [.NET 核心應用程式發佈概述](../deploying/index.md)
- [使用 .NET 核心 CLI 發佈 .NET 核心應用](../deploying/deploy-with-cli.md)
- [目標框架](../../standard/frameworks.md)
- [執行階段識別項 (RID) 目錄](../rid-catalog.md)
- [使用 macOS Catalina 公證](../install/macos-notarization-issues.md)有關詳細資訊，請參閱他關注以下資源：
- [已發佈應用程式的目錄結構](/aspnet/core/hosting/directory-structure)
