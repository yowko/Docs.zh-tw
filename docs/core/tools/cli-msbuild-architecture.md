---
title: ".NET Core 命令列工具架構"
description: "深入了解 .NET Core 工具層級，以及最新版本中已變更的內容。"
keywords: ".NET Core, MSBuild, 架構"
author: blackdwarf
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 7fff0f61-ac23-42f0-9661-72a7240a4456
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6830cc46994aa44d46a9c862efff525142578003
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>.NET Core 工具中變更的高階概觀

本文件說明從 *project.json* 移轉至 MSBuild 以及 *csproj* 專案系統相關聯的變更，包含 .NET Core 工具分層與 CLI 命令實作之變更的相關資訊。 2017 年 3 月 7 日發行的 .NET Core SDK 1.0 與 Visual Studio 2017 會進行這些變更 (請參閱[公告](https://blogs.msdn.microsoft.com/dotnet/2017/03/07/announcing-net-core-tools-1-0/))，但一開始是隨 .NET Core SDK Preview 3 版本實作。

## <a name="moving-away-from-projectjson"></a>從 project.json 移開
.NET Core 的工具中最大的變更，絕對是將專案系統[從 project.json 改為使用 csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/)。 命令列工具的最新版本不支援 *project.json* 檔案。 這表示它無法用來建置、執行或發佈以 project.json 為基礎的應用程式與程式庫。 若要使用此版本的工具，您必須移轉您現有的專案，或開始新的專案。 

做為移動的一部分，開發用來建置 project.json 專案的自訂建置引擎會以成熟且功能完整、名稱為 [MSBuild](https://github.com/Microsoft/msbuild) 的建置引擎取代。 MSBuild 是 .NET 社群中眾所周知的引擎，因為它從該平台首次發行以來一直就是關鍵技術。 當然，因為它需要建置 .NET Core 應用程式，MSBuild 已經移植到 .NET Core，且可以在執行 .NET Core 的任何平台上使用。 .NET Core 其中一個主要承諾就是跨平台開發堆疊，而我們也以確認此移動不會中斷該承諾。

> [!NOTE]
> 如果您不熟悉 MSBuild 且希望深入了解它，您可以透過閱讀 [MSBuild 概念](/visualstudio/msbuild/msbuild-concepts)一文開始。 

## <a name="the-tooling-layers"></a>工具分層
離開現有的專案系統以及轉換建置引擎，接下來很自然的問題就是這些變更是否會變更完整 .NET Core 工具生態系統的整體「分層」呢？ 有新的項目和元件嗎？

讓我們開始快速複習 Preview 2 分層，如下列圖片所示︰

![Preview 2 工具高階架構](media/cli-msbuild-architecture/p2-arch.png)

這些工具的分層相當簡單。 在底部我們有 .NET Core 命令列工具做為基礎。 所有其他的高階工具 (例如 Visual Studio 或 Visual Studio Code) 則依存並仰賴 CLI 來建置專案、還原相依性等。 舉例來說，這表示如果 Visual Studio 希望執行還原作業，它會呼叫 CLI 中的 `dotnet restore` 命令。 

隨著移動到新的專案系統，之前的圖表有所變更： 

![.NET Core SDK 1.0.0 高階架構](media/cli-msbuild-architecture/p3-arch.png)

主要差異就是 CLI 不再是基本層；此角色現在會填入「共用的 SDK 元件」。 共用的 SDK 元件是負責編譯您的程式碼、發行程式碼，封裝 NuGet 套件等的一組目標和關聯工作。SDK 本身是開放原始碼，而且您可以在 GitHub 的 [SDK 存放庫](https://github.com/dotnet/sdk)上找到它。 

> [!NOTE]
> 「目標」是表示 MSBuild 可叫用之具名作業的 MSBuild 詞彙。 它通常會搭配執行目標應該要執行之某些邏輯的一或多個工作。 MSBuild 支援許多現成的目標，例如 `Copy` 或 `Execute`；它也允許使用者使用受管理程式碼撰寫自己的工作，並定義目標以執行那些工作。 如需詳細資訊，請參閱 [MSBuild 工作](/visualstudio/msbuild/msbuild-tasks)。 

所有工具組現在使用共用的 SDK 元件及其目標，包含 CLI。 例如，下一版 Visual Studio 將不會呼叫 `dotnet restore` 命令來還原 .NET Core 專案的相依性，它會直接使用「還原」目標。 由於這些都是 MSBuild 目標，您也可以使用原始的 MSBuild 來使用 [dotnet msbuild](dotnet-msbuild.md) 命令執行它們。 

### <a name="cli-commands"></a>CLI 命令
共用的 SDK 元件表示大部分現有的 CLI 命令已經重新實作為 MSBuild 工作和目標。 這對 CLI 命令和您的工具組的使用方式有什麼意義？ 

從使用方式觀點來看，它不會變更您使用 CLI 的方式。 CLI 仍然具備存在於 Preview 2 版本中的核心命令：

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

這些命令仍然可以執行您所期望的動作 (新建專案、建置專案、發行專案、封裝專案等)。 大部分的選項都沒有變更，且仍然存在，而您可以查閱命令的說明畫面 (使用 `dotnet <command> --help`) 或此網站上的文件，以熟悉任何變更。 

從執行觀點而言，CLI 命令會接受輸入參數並建構對「原始」MSBuild 的呼叫，這會設定所需的屬性，並執行所需的目標。 為進一步說明這一點，請考慮下列命令︰ 

   `dotnet publish -o pub -c Release`
    
此命令會使用「發行」組態，將應用程式發佈至 `pub` 資料夾中。 就內部而言，此命令會轉譯成下列 MSBuild 引動過程︰ 

   `dotnet msbuild /t:Publish /p:OutputPath=pub /p:Configuration=Release`

此規則值得注意的例外狀況為 `new` 和 `run` 命令，因為它們尚未實作為 MSBuild 目標。

