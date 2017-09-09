---
title: "從 DNX 移轉到 .NET Core CLI"
description: "從 DNX 移轉到 .NET Core CLI"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c0d70120-78c8-4d26-bb3c-801f42fc2366
translationtype: Human Translation
ms.sourcegitcommit: 4a1f0c88fb1ccd6694f8d4f5687431646adbe000
ms.openlocfilehash: d32c73ac3a724d4701b7f6c1d548aedb3fb00c56
ms.lasthandoff: 03/22/2017

---

# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>從 DNX 移轉到 .NET Core CLI (project.json)

## <a name="overview"></a>概觀
.NET Core 的 RC1 版本與 ASP.NET Core 1.0 引進了 DNX 工具。 .NET Core 的 RC2 版本與 ASP.NET Core 1.0 則從 DNX 進展到了 .NET Core CLI。

現在，讓我們稍微複習一下什麼是 DNX。 DNX 是一種執行階段和工具組，可用來建置 .NET Core 和 ASP.NET Core 1.0 應用程式。 它由 3 個主要部分所組成：

1. DNVM - 可取得 DNX 的安裝指令碼
2. DNX (Dotnet 執行階段) - 執行程式碼的執行階段
3. DNU (Dotnet 開發人員公用程式) - 可管理相依性、建置並發佈應用程式的工具

現在，引進 CLI 之後，單一工具組即包含上述所有項目。 不過，由於 DNX 是在 RC1 時間範圍內可供使用，因此您可能會想將使用它所建置的專案移出至新的 CLI 工具。 

本移轉指南說明如何將專案從 DNX 移轉至 .NET Core CLI 的基本資訊。 如果您一開始就是從 .NET Core 開始專案，可放心略過這份文件。 

## <a name="main-changes-in-the-tooling"></a>工具的主要變更
首先，我們必須先概述這項工具的幾個一般變更。 

### <a name="no-more-dnvm"></a>不再有 DNVM
DNVM 是「DotNet 版本管理員」的簡稱，其為一種可用來在電腦上安裝 DNX 的 Bash/PowerShell 指令碼。 它可幫助使用者從其指定的摘要 (或預設摘要) 取得所需的 DNX，並將特定 DNX 標示為「作用中」，以將它放在指定工作階段的 $PATH 中。 這樣一來，您就可以使用各種工具。

DNVM 已停用，因為其功能集與 .NET Core CLI 工具引入的變更重複。

CLI 工具已透過兩種主要方式進行封裝：

1. 適用於指定平台的原生安裝程式
2. 適用於其他情況的安裝指令碼 (例如 CI 伺服器)

基於此，即不需要 DNVM 安裝功能。 那麼執行階段選取功能呢？ 

您可在相依性中新增特定版本的套件，以參考 `project.json` 中的執行階段。 這項變更可讓您的應用程式使用新的執行階段位元。 若要讓您的電腦具有這些位元，其方式與 CLI 相同︰您可透過執行階段支援的其中一個原生安裝程式，或是執行階段的安裝指令碼，來安裝執行階段。 

### <a name="different-commands"></a>不同的命令
如果您以前使用 DNX，您應該從其中的三個組件之一 (DNX、DNU 或 DNVM) 使用過一些命令。 使用 CLI 時，其中某些命令已變更，某些可能無法使用，某些雖然相同但有稍微不同的語意。 

下表顯示 DNX/DNU 命令和 CLI 對應項目之間的對應。


| DNX 命令                        | CLI 命令        | 描述                                                                                                         |
|--------------------------------    |----------------    |-----------------------------------------------------------------------------------------------------------------    |
| dnx run                            | dotnet run         | 從來源執行程式碼。                                                                                               |
| dnu build                          | dotnet build       | 建置您程式碼的 IL 二進位檔。                                                                                    |
| dnu pack                           | dotnet pack        | 封裝您程式碼的 NuGet 套件。                                                                            |
| dnx \[command] (例如 "dnx web")     | N/A\*              | 在 DNX 環境中，依據 project.json 的定義來執行命令。                                                         |
| dnu install                        | N/A\*              | 在 DNX 環境中，將套件安裝為相依性。                                                                |
| dnu restore                        | dotnet restore     | 還原您在 project.json 中指定的相依性。                                                                |
| dnu publish                        | dotnet publish     | 在可攜式、原生可攜式與獨立式這三種形式中，以其中一種方式來發佈要部署的應用程式。     |
| dnu wrap                           | N/A\*              | 在 DNX 環境中，將 project.json 包裝在 csproj 中。                                                                        |
| dnu 命令                       | N/A\*              | 在 DNX 環境中，管理已全域安裝的命令。                                                               |

(\*) - CLI 的設計並不支援這些功能。 

## <a name="dnx-features-that-are-not-supported"></a>不支援的 DNX 功能
如上表所示，我們決定 CLI 目前不再支援 DNX 環境的部分功能。 本節會探討其中最重要的功能，並簡述不支援的理由，以及在您需要使用這些功能時的因應措施。

### <a name="global-commands"></a>全域命令
DNU 具有「全域命令」的概念。 基本上，這當中包括封裝為 NuGet 套件的主控台應用程式，以及可叫用您指定要執行應用程式之 DNX 的殼層指令碼。 

CLI 不支援此概念。 不過，它支援新增個別專案命令的概念；您可使用熟悉的 `dotnet <command>` 語法叫用這些命令。

### <a name="installing-dependencies"></a>安裝相依性
截至 v1 為止，.NET Core CLI 工具都沒有可安裝相依性的 `install` 命令。 若要從 NuGet 安裝套件，您必須將它以相依性形式新增至 `project.json` 檔，然後執行 `dotnet restore`。 

### <a name="running-your-code"></a>執行您的程式碼
有以下兩種執行程式碼的主要方式。 一個是使用 `dotnet run`，從來源執行。 不同於 `dnx run`，這麼做並不會執行任何記憶體中編譯。 實際上，它會叫用 `dotnet build` 以建置您的程式碼，然後執行建置的二進位檔。 

另一個方法是使用 `dotnet` 本身來執行您的程式碼。 此作業是藉由提供組件的路徑來完成：`dotnet path/to/an/assembly.dll`。 

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>將 DNX 專案移轉至 .NET Core CLI
處理程式碼時，除了要使用新的命令之外，還有下列三個主要項目要從 DNX 移轉過來：

1. 如果您已經可以使用 CLI，請移轉 `global.json` 檔案。
2. 將專案檔 (`project.json`) 本身移轉至 CLI 工具。
3. 將任何 DNX API 移轉至其 BCL 對應項目。 

### <a name="changing-the-globaljson-file"></a>變更 global.json 檔案
`global.json` 檔案的作用如同 RC1 和 RC2 (或更新版本) 專案的方案檔。 為了讓 CLI 工具 (以及 Visual Studio) 區分 RC1 與更新版本的差異，該工具會使用 `"sdk": { "version" }` 屬性來區分哪些專案是 RC1 或更新版本。 如果 `global.json` 完全沒有這個節點，就會假設其為最新版本。 

若要更新 `global.json` 檔案，可移除該屬性或將它設為您想要使用之工具的正確版本，在此案例中為 **1.0.0-preview2-003121**：

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>移轉專案檔
CLI 和 DNX 都使用以 `project.json` 檔案為基礎的相同基本專案系統。 專案檔語法和語意基本上維持不變，僅有不同案例的小差異。 結構描述也有一些變更；您可在[結構描述檔案](http://json.schemastore.org/project)或更易記的 [project.json 參考](../tools/project-json.md)中查看這些變更。 

如果您要建置主控台應用程式，則需要將下列程式碼片段新增至您的專案檔：

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

這麼做會指示 `dotnet build` 針對您的應用程式發出進入點，以讓程式碼可有效執行。 如果您要建置類別庫，只要省略上一節即可。 當然，一旦將上述程式碼片段新增至 `project.json` 檔案之後，您必須新增靜態進入點。 移出 DNX 時，它所提供的 DI 服務便無法再使用，因此進入點必須是基本 .NET 進入點：`static void Main()`。

如果您的 `project.json` 中有「命令」區段，您可以將它移除。 如果某些命令原本是以 DNU 命令的形式存在 (例如 Entity Framework CLI 命令)，則這些命令會以每個專案擴充功能的形式移植至 CLI。 如果您要自行建立命令以在專案中使用，則需要將其取代為 CLI 擴充功能。 在此情況下，`project.json` 中的 `commands` 節點必須以 `tools` 節點取代，且它需要列出工具相依性。 

完成這些作業之後，您必須決定應用程式要具備哪種類型的可攜性。 我們對 .NET Core 所提供的可攜性選項範圍投注不少心力，以供您選擇。 比方說，您可能需要完全*可攜式*的應用程式，或希望擁有*獨立*的應用程式。 可攜式應用程式選項很像 .NET Framework 應用程式的運作方式：它需要共用元件以在目標電腦 (.NET Core) 上執行。 獨立的應用程式不需要在目標上安裝 .NET Core，但是您必須為每個想要支援的作業系統產生一個應用程式。 bpt id="p1" xmlns="urn:oasis:names:tc:xliff:document:1.2"> [</bpt>應用程式可攜性類型](../deploying/index.md)文件中會說明這些可攜性類型等相關資訊。 

一旦您決定要使用何種可攜性類型時，即需要變更目標架構。 如果您撰寫過 .NET Core 的應用程式，您很可能會使用 `dnxcore50` 做為目標架構。 若要使用 CLI 以及新 [.NET 標準程式庫](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/net-platform-standard.md)帶來的變更 ，架構必須是下列其中之一：

1. `netcoreapp1.0`- 如果您要撰寫的應用程式在 .NET Core (包括 ASP.NET Core 應用程式) 上
2. `netstandard1.6`- 如果您要撰寫 .NET Core 的類別庫

如果您使用其他 `dnx` 目標 (例如 `dnx451`)，也必須變更這些項目。 `net451`應變更為 `dnx451`。 如需詳細資訊，請參閱 [.NET 標準程式庫文件](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/net-platform-standard.md)。 

您的 `project.json` 現已大致就緒。 接著，您必須檢查相依性清單，並將相依性更新為較新版本；如果您是使用 ASP.NET Core 相依性的話，更應注意這項作業。 如果您之前針對 BCL API 使用不同的套件，則可以使用[應用程式可攜性類型](../deploying/index.md)文件中所述的執行階段套件。 

準備好後，您可以嘗試使用 `dotnet restore` 進行還原。 根據您的相依性版本而定，如果 NuGet 無法解析上述其中一個目標架構的相依性，就可能會發生錯誤。 這是「時間點」的問題，因為隨著時間過去，會有越來越多套件支援這些架構。 目前來看，如果您遇到這個問題，可以使用 `framework` 節點內的 `imports` 陳述式，指定 NuGet 可以還原目標為 "imports" 陳述式內之架構的套件。 在此情況下取得的還原錯誤應具有足夠資訊，可讓您知道需要匯入哪些架構。 如果您有點跟不上或對這方面不太熟悉，一般來說，只要在 `imports` 陳述式中指定 `dnxcore50` 和 `portable-net45+win8` 就可以達到目的。 下列 JSON 程式碼片段會示範這個過程：

```json
    "frameworks": {
        "netcoreapp1.0": { 
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

執行 `dotnet build` 時，會將任何最終建置錯誤顯示出來，但不應該有太多錯誤。 建置好程式碼並順利執行後，您可以再使用執行器測試一下。 執行 `dotnet <path-to-your-assembly>`，並查看其執行狀況。
