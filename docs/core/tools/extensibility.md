---
title: ".NET Core CLI 擴充性模型"
description: ".NET Core CLI 擴充性模型"
keywords: "CLI, 擴充性, 自訂命令, .NET Core"
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 1bebd25a-120f-48d3-8c25-c89965afcbcd
translationtype: Human Translation
ms.sourcegitcommit: aeb199a9aeb1584570ad2a2942e2f22c75a59616
ms.openlocfilehash: 4223f296224c9b62c88b72f0f643c8b8b6fc9f6b

---

# <a name="net-core-cli-extensibility-model"></a>.NET Core CLI 擴充性模型 

## <a name="overview"></a>概觀
本文件將涵蓋如何擴充 CLI 工具的主要方法，並說明驅動所有項目的案例。 它將會概述如何使用這些工具，以及提供如何建置這兩種工具的簡短附註。 

## <a name="how-to-extend-cli-tools"></a>如何擴充 CLI 工具
CLI 工具可以透過兩種主要方式進行擴充︰

1. 透過個別專案的 NuGet 套件
2. 透過系統的 PATH

上述這兩種擴充性機制都不是專用的；您可以使用兩者或其中一個。 選擇哪一個主要取決於您嘗試使用擴充功能達成的目標。

## <a name="perproject-based-extensibility"></a>個別專案擴充性
個別專案工具是散發為 NuGet 套件的[可攜式主控台應用程式](../deploying/index.md)。 工具僅適用於參考它們以及還原它們的專案內容；因為將會找不到命令，所以專案內容外部的叫用 (例如，包含專案的目錄外部) 會失敗。

因為不需要 `project.json` 外部的任何項目，所以這些工具也非常適合組建伺服器。 建置流程會執行所建置專案的還原，並且可以使用這些工具。 語言專案 (例如 F#) 也在這個分類中；畢竟，每個專案都只能以一種特定語言撰寫。 

最後，這個擴充性模型支援建立存取專案的已建置輸出所需的工具。 例如，[ASP.NET](https://www.asp.net/) MVC 應用程式中的各種 Razor 檢視工具都會落入這個分類。 

### <a name="consuming-perproject-tools"></a>使用個別專案工具
使用這些工具時，需要您將 `tools` 節點新增至 `project.json`。 在 `tools` 節點內，您參考工具所在的套件。 執行 `dotnet restore` 之後，會還原工具和其相依性。 

針對需要載入專案建置輸出來執行的工具，通常在專案檔中的一般相依性下方會列出另一個相依性。 這表示載入專案程式碼的工具有兩個元件︰ 

1. "tools" 主要叫用者
2. 包含要處理之邏輯的任意數目的其他工具 

為什麼是兩件事呢？ 需要載入專案建置輸出的工具，需要具有含其正在處理之專案的整合相依性圖形。 透過新增相依性位元，可以讓 NuGet 將這些相依性解析為統一圖形。 叫用者的存在原因是需要推論位置以及相依性工具架構。 叫用者可以接受使用者所指定和尋找相依性工具的所有重新導向引數 (`-c`、`-o`、`-b`)；它也可以在多個架構有多個相依性工具時實作任何原則 (亦即，全部執行、只執行一個等)。一般而言，需要時，這兩個工具可以共用邏輯。 

讓我們檢閱在簡單專案中新增僅限簡單工具的工具的範例。 如果具有稱為 `dotnet-api-search` 的範例命令可讓您搜尋所指定 API 的 NuGet 套件，則以下是使用該工具的主控台應用程式 `project.json` 檔案：

```json
{
    "version": "1.0.0",
    "compilationOptions": {
        "emitEntryPoint": true
    },
    "dependencies": {
        "Microsoft.NETCore.App": {
            "type": "platform",
            "version": "1.0.0"
        }
    },
    "tools": {
        "dotnet-api-search": {
            "version": "1.0.0",
            "imports": ["dnxcore50"]
        }
    },
    "frameworks": {
        "netcoreapp1.0": {}
    }
}
```

`tools` 節點的建構方式與 `dependencies` 節點類似。 它需要最少包含工具和其版本的套件的套件識別項。 在上述範例中，我們可以看到有另一個陳述式 ( `imports` 陳述式)。 這會影響工具的還原程序，並且指定工具也與 `dnxcore50` 目標相容 (除了工具所具有的任何目標架構之外)。 如需詳細資訊，您可以查閱 [project.json 參考](project-json.md)。

### <a name="building-tools"></a>建置工具
如前所述，工具只是可攜式主控台應用程式。 在建置任何主控台應用程式時會建立一個。 在您建立它之後，將使用 [`dotnet pack`](dotnet-pack.md) 命令來建立包含您程式碼、其相依性相關資訊等的 NuGet 套件 (nupkg)。 套件名稱可以是作者想要的任何名稱，但在應用程式內，實際工具二進位檔必須符合 `dotnet-<command>` 的慣例，`dotnet` 才能叫用它。 

因為工具是可攜式應用程式，所以使用工具的使用者必須具有用來建置工具的 .NET Core 程式庫版本，才能執行工具。 工具所使用以及 .NET Core 程式庫內未包含的任何其他相依性都會進行還原並放到 NuGet 快取中。 因此，會使用 .NET Core 程式庫中的組件以及 NuGet 快取中的組件來執行整個工具。 

這類工具的相依性圖形必須與使用這些工具之專案的相依性圖形完全分開。 還原程序會先還原專案的相依性，接著還原每個工具和其相依性。 

您可以在 [.NET Core CLI 存放庫](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestProjects)中找到更多範例和這類不同的組合。 您也可以在相同的存放庫中查看[所使用工具的實作](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages)。 

載入專案建置輸出來執行的建置工具會有些許不同。 如所述，這類工具有兩個元件︰

1. 使用者所叫用的發送器工具
2. 架構特有相依性，內含如何尋找組建輸出和其處理方式的邏輯

這個的基本範例是 [Entity Framework (EF)](https://github.com/aspnet/EntityFramework) 命令和 [`dotnet test`](dotnet-test.md) 命令。 在這兩種情況下，於 `project.json` 的 `tools` 節點中會參考一種工具，而有一種工具是主要發送器。 使用者會在命令列上叫用這個工具。 第二個部分是專案主要相依性中指定的相依性 (根相依性或架構特有相依性)。 這個套件包含工具的實際邏輯。 套件是標準相依性，因此它將會還原為專案還原程序的一部分。 

與前一類工具不同，這些工具實際上是使用它們之專案的圖形一部分。 原因是它們需要存取專案的程式碼，也可能需要存取其所有相依性。 例如，EF 工具需要這個項目的原因是需要掃描組件來找出所需的程式碼 (例如移轉)。  

另一個有這兩個尖端方案的原因是允許更乾淨的叫用模型。 在磁碟上放置特定成品的大部分 CLI 命令 (例如，`dotnet build`、`dotnet publish`) 都允許使用者使用 `--output` 引數、`--build-base-path` 引數或 `--configuration` 引數將輸出重新導向至不同路徑。 例如，針對 EF 工具，若要能夠找到您專案的建置輸出，您必須提供 *兩個* `dotnet` 驅動程式和 `ef` 命令具有相同值的相同引數。 使用者可以使用叫用模型將任何引數傳遞給發送器工具，然後使用該發送器工具，在輸出目錄中找到包含邏輯的所需二進位檔。 

這種方式的不錯範例位於 [.NET Core CLI 存放庫](https://github.com/dotnet/cli)中：

* [範例 project.json 檔案](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/TestAssets/DesktopTestProjects/AppWithDirectDependencyDesktopAndPortable/project.json)
* [發送器的實作](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages/dotnet-dependency-tool-invoker)
* [架構特有相依性的實作](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages/dotnet-desktop-and-portable)


### <a name="pathbased-extensibility"></a>PATH 擴充性
PATH 擴充性通常用於開發電腦，而在開發電腦中，您需要有概念上涵蓋多個單一專案的工具。 這個擴充功能機制的主要缺點是繫結至工具所在的電腦。 如果您需要在另一部電腦上使用它，則必須部署它。

這種模式的 CLI 工具組擴充性十分簡單。 如 [.NET Core CLI 概觀](index.md)中所涵蓋，`dotnet` 驅動程式可以執行任何在 `dotnet-<command>` 慣例後面命名的命令。 預設解析邏輯會先探查數個位置，最後再轉到系統 PATH。 如果要求的命令存在於系統 PATH 中，而且是可叫用的二進位檔，`dotnet` 驅動程式將會叫用它。 

二進位檔幾乎是作業系統可以執行的任何項目。 在 Unix 系統上，這表示任何透過 `chmod +x` 設定執行位元的項目。 在 Windows 上，這表示 Windows 知道如何執行的任何項目。 

例如，讓我們查看十分簡單的 `dotnet clean` 命令實作。 我們將使用 `bash` 來實作這個命令。 這個命令只會刪除目前目錄中的 `bin/` 和 `obj/` 目錄。 如果將 `--lock` 引數傳遞給它，則也會刪除 `project.lock.json` 檔案。 這個命令的全部內容如下。 

```bash
#!/bin/bash

# Delete the bin and obj dirs
rm -rf bin/ obj/

LOCK_FILE=$1
if [[ "$LOCK_FILE" = "--lock" ]]; then
    rm project.lock.json
fi


echo "Cleaning complete..."
```

在 macOS 上，我們可以將這個指令碼儲存為 `dotnet-clean`，並使用 `chmod +x dotnet-clean` 設定其可執行位元。 我們接著可以使用 `ln -s dotnet-clean /usr/local/bin/` 命令，以在 `/usr/local/bin` 中建立其符號連結。 這可能會使用 `dotnet clean` 語法來叫用 clean 命令。 測試方式是建立應用程式，並在其上執行 `dotnet build`，然後執行 `dotnet clean`。 

## <a name="conclusion"></a>結論
.NET Core CLI 工具允許兩個主要擴充點。 個別專案工具都包含在專案內容內，但允許透過還原輕鬆地進行安裝。 PATH 工具適用於可在單一電腦上使用的一般跨專案工具。 



<!--HONumber=Nov16_HO3-->


