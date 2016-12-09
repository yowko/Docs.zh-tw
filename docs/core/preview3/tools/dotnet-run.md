---
title: "dotnet-run 命令 | .NET Core SDK"
description: "dotnet-run 命令提供方便的選項，以透過原始程式碼來執行應用程式。"
keywords: "dotnet-run, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 495ff50b-cb30-4d30-8f20-beb3d5e7c31f
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 6f95125640e7341426c3a019771a6b8595d10e73

---

#<a name="dotnet-run"></a>dotnet-run

## <a name="name"></a>名稱 

dotnet-run --「就地」執行原始程式碼，而不需要有任何明確的編譯或啟動命令

## <a name="synopsis"></a>概要

`dotnet run [--help] [--framework] [--configuration]
    [--project] [[--] [application arguments]]`

## <a name="description"></a>描述
`dotnet run` 命令提供方便的選項，以使用一個命令透過原始程式碼來執行應用程式。 它會編譯原始程式碼，並產生輸出程式，然後執行該程式。 這個命令適用於快速反覆開發，也用來執行來源分散式程式 (例如網站)。

這個命令依賴 [dotnet build](dotnet-build.md) 先將來源輸入建置到 .NET 組件，再啟動程式。 這個命令以及處理來源輸入的需求全部繼承自 build 命令。 build 命令的文件會提供這些需求的詳細資訊。

輸出檔案會寫入至子系 *bin* 資料夾 (如果不存在，則會予以建立)。 將會視需要覆寫檔案。 暫存檔案會寫入至子系 *obj* 資料夾。  

如果專案有多個指定的架構，`dotnet run` 會先選取 .NET Core 架構。 如果這些不存在，則會發生錯誤。 若要指定其他架構，請使用 `--framework` 引數。

`dotnet run` 命令必須用於專案內容中，而非已建置的組件。 如果您嘗試改為執行可攜式應用程式 DLL，則應該會使用未含任何命令的 [dotnet](dotnet.md)，如下列範例中所示：
 
`dotnet myapp.dll`

如需 `dotnet` 驅動程式的詳細資訊，請參閱 [.NET Core 命令列工具 (CLI)](index.md) 主題。

## <a name="options"></a>選項

`--`

分隔 `dotnet run` 的引數與執行中應用程式的引數。 這個項目後面的所有引數將會傳遞至執行中應用程式。 

`-h|--help`

印出命令的簡短說明。

`-f`, `--framework <FRAMEWORK_IDENTIFIER>`

執行所指定架構識別項 (FID) 的應用程式。 

`-c`, `--configuration <Debug|Release>`

要在發行時使用的組態。 預設值是 `Debug`。

`-p`, `--project [PATH]`

指定要執行的專案。 它可以是 [csproj](csproj.md) 檔案的路徑，或包含 [csproj](csproj.md) 檔案之目錄的路徑。 如果未指定，則會預設為目前目錄。 

## <a name="examples"></a>範例

執行目前目錄中的專案：`dotnet run` 

執行指定的專案：

`dotnet run --project /projects/proj1/proj1.csproj`

執行目前目錄中的專案 (因為已使用 `--` 引數，所以這個範例中的 `--help` 引數會傳遞給正在執行的應用程式)：

`dotnet run --configuration Release -- --help`


<!--HONumber=Nov16_HO3-->


