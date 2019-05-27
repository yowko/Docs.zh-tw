---
title: dotnet clean 命令
description: dotnet clean 命令會清除目前的目錄。
ms.date: 04/14/2019
ms.openlocfilehash: fa19f1b041e4031082f928135395a5f06ce702e9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631826"
---
# <a name="dotnet-clean"></a>dotnet clean

**本主題適用於：✓** .NET Core 1.x SDK 和更新版本

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>名稱

`dotnet clean` - 清除專案的輸出。

## <a name="synopsis"></a>概要

```
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>說明

`dotnet clean` 命令會清除前一個組建的輸出。 它會實作為 [MSBuild 目標](/visualstudio/msbuild/msbuild-targets)，因此命令在執行的時候會評估專案。 只會清除在建置期間建立的輸出。 中繼 (*obj*) 和最後輸出 (*bin*) 這兩個資料夾都會清除。

## <a name="arguments"></a>引數

`PROJECT | SOLUTION`

要清除的 MSBuild 專案或方案。 MSBuild 會在目前工作目錄中搜尋副檔名以 *proj* 或 *sln* 結尾的檔案，並使用該檔案。

## <a name="options"></a>選項

* **`-c|--configuration {Debug|Release}`**

  定義組建組態。 預設值為 `Debug`。 如果在建置階段指定此選項，清除時才需要使用它。

* **`-f|--framework <FRAMEWORK>`**

  在建置時間指定的[架構](../../standard/frameworks.md)。 架構必須定義於[專案檔](csproj.md)中。 如果在建置階段指定架構，則您必須在清除時指定該架構。

* **`-h|--help`**

  印出命令的簡短說明。

* **`--interactive`**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 自 .NET Core 3.0 SDK 起提供。

* **`-o|--output <OUTPUT_DIRECTORY>`**

  包含要清除組建成品的目錄。 如果您在建置專案時指定架構，請搭配輸出目錄參數來指定 `-f|--framework <FRAMEWORK>` 參數。

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  清除指定執行階段的輸出資料夾。 建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。 自 .NET Core 2.0 SDK 起可用的選項。

* **`-v|--verbosity <LEVEL>`**

  設定 MSBuild 詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設為 `normal`。

## <a name="examples"></a>範例

* 清除專案的預設組建︰

  ```console
  dotnet clean
  ```

* 清除使用發行組態來建置的專案︰

  ```console
  dotnet clean --configuration Release
  ```
