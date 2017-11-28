---
title: "dotnet clean 命令 - .NET Core CLI"
description: "dotnet clean 命令會清除目前的目錄。"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 4836f07ec1a8b59c343b4d0181587e602f61d45e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-clean"></a>dotnet-clean

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet clean` - 清除專案的輸出。

## <a name="synopsis"></a>概要

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>說明

`dotnet clean` 命令會清除前一個組建的輸出。 它會實作為 [MSBuild 目標](/visualstudio/msbuild/msbuild-targets)，因此命令在執行的時候會評估專案。 只會清除在建置期間建立的輸出。 中繼 (*obj*) 和最後輸出 (*bin*) 這兩個資料夾都會清除。

## <a name="arguments"></a>引數

`PROJECT`

要清除的 MSBuild 專案。 如果未指定專案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 的檔案，並使用該檔案。

## <a name="options"></a>選項

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值是 `Debug`。 如果在建置階段指定此選項，清除時才需要使用它。

`-f|--framework <FRAMEWORK>`

在建置時間指定的[架構](../../standard/frameworks.md)。 架構必須定義於[專案檔](csproj.md)中。 如果在建置階段指定架構，則您必須在清除時指定該架構。

`-h|--help`

印出命令的簡短說明。

`-o|--output <OUTPUT_DIRECTORY>`

在其中放置建置輸出的目錄。 如果您在建置專案時指定架構，請搭配輸出目錄參數來指定 `-f|--framework <FRAMEWORK>` 參數。

`-r|--runtime <RUNTIME_IDENTIFIER>`

清除指定執行階段的輸出資料夾。 建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的層級為 q[uiet]、m[inimal]、n[ormal]、d[etailed] 和 diag[nostic]。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

定義組建組態。 預設值是 `Debug`。 如果在建置階段指定此選項，清除時才需要使用它。

`-f|--framework <FRAMEWORK>`

在建置時間指定的[架構](../../standard/frameworks.md)。 架構必須定義於[專案檔](csproj.md)中。 如果在建置階段指定架構，則您必須在清除時指定該架構。

`-h|--help`

印出命令的簡短說明。

`-o|--output <OUTPUT_DIRECTORY>`

在其中放置建置輸出的目錄。 如果您在建置專案時指定架構，請搭配輸出目錄參數來指定 `-f|--framework <FRAMEWORK>` 參數。

`-v|--verbosity <LEVEL>`

設定命令的詳細資訊層級。 允許的層級為 q[uiet]、m[inimal]、n[ormal]、d[etailed] 和 diag[nostic]。

---

## <a name="examples"></a>範例

清除專案的預設組建︰

`dotnet clean`

清除使用發行組態來建置的專案︰

`dotnet clean --configuration Release`
