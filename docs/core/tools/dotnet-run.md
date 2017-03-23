---
title: "dotnet-run 命令 | Microsoft Docs"
description: "dotnet-run 命令提供方便的選項，以透過原始程式碼來執行應用程式。"
keywords: "dotnet-run, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 60bb9160e43788539b0dc6bcf1372bb925e9ba22
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-run"></a>dotnet-run

## <a name="name"></a>名稱 

`dotnet-run` - 「就地」執行原始程式碼，而不需要有任何明確的編譯或啟動命令。

## <a name="synopsis"></a>概要

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a>描述

`dotnet run` 命令提供方便的選項，以使用一個命令透過原始程式碼來執行應用程式。 可用於在命令列中快速進行反覆開發。 此命令需要 [`dotnet build`](dotnet-build.md) 命令以建置程式碼，因此組建的任何需求 (例如必須先還原專案) 也適用於 `dotnet run`。 

輸出檔會寫入至預設位置，也就是 `bin/<configuration>/<target>`。 例如，如果您有 `netcoreapp1.0` 應用程式並執行 `dotnet run`，輸出將會放置在 `bin/Debug/netcoreapp1.0` 中； 而且會視需要覆寫檔案。 暫存檔案會放置在 `obj` 目錄中。 

如果有指定多個架構的專案，除非使用 `--framework` 選項指定要執行應用程式的架構，否則 `dotnet run` 會顯示錯誤。

`dotnet run` 命令必須用於專案內容中，而非已建置的組件。 如果您嘗試改為執行可攜式應用程式 DLL，則應該會使用未含任何命令的 [dotnet](dotnet.md)，如下列範例中所示：
 
`dotnet myapp.dll`

如需 `dotnet` 驅動程式的詳細資訊，請參閱 [.NET Core 命令列工具 (CLI)](index.md) 主題。

為了執行應用程式，`dotnet run` 命令會從 NuGet 快取解析共用執行階段之外的應用程式相依性。 在此情況下，不建議在生產環境中使用此命令來執行應用程式。 相反地，您應該使用 [`dotnet publish`](dotnet-publish.md) 命令[建立部署](../deploying/index.md)，再於生產環境中使用該部署。 

## <a name="options"></a>選項

`--`

分隔 `dotnet run` 的引數與執行中應用程式的引數。 這個項目後面的所有引數將會傳遞至執行中應用程式。 

`-h|--help`

印出命令的簡短說明。

`-c|--configuration {Debug|Release}`

要用於建置專案的組態。 預設值是 `Debug`。

`-f|--framework <FRAMEWORK_IDENTIFIER>`

使用指定的架構建置並執行應用程式。 必須在專案檔中指定此架構。

`-p|--project <PATH>`

指定要執行之專案檔的路徑。 它可以是 [csproj](csproj.md) 檔案的路徑，或包含 [csproj](csproj.md) 檔案之目錄的路徑。 如果未指定，則會預設為目前目錄。 

## <a name="examples"></a>範例

執行目前目錄中的專案：

`dotnet run` 

執行指定的專案：

`dotnet run --project /projects/proj1/proj1.csproj`

執行目前目錄中的專案 (因為已使用 `--` 引數，所以這個範例中的 `--help` 引數會傳遞給正在執行的應用程式)：

`dotnet run --configuration Release -- --help`
