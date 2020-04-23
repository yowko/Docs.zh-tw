---
title: .NET Core 命令列工具架構
description: 深入了解 .NET Core 工具層級，以及最新版本中已變更的內容。
ms.date: 03/06/2017
ms.openlocfilehash: e1a9fe59225c17d54f6e7213d2b3c3fa70ee58e0
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102875"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>.NET Core 工具中變更的高階概觀

本文件說明從 *project.json* 移轉至 MSBuild 以及 *csproj* 專案系統相關聯的變更，包含 .NET Core 工具分層與 CLI 命令實作之變更的相關資訊。 2017 年 3 月 7 日發行的 .NET Core SDK 1.0 與 Visual Studio 2017 會進行這些變更 (請參閱[公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/))，但一開始是隨 .NET Core SDK Preview 3 版本實作。

## <a name="moving-away-from-projectjson"></a>從 project.json 移開

.NET Core 的工具中最大的變更，絕對是將專案系統[從 project.json 改為使用 csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/)。 命令列工具的最新版本不支援 *project.json* 檔案。 這意味著它不能用於構建、運行或發佈基於 project.json 的應用程式和庫。 要使用此版本的工具,請遷移現有專案或啟動新專案。

做為移動的一部分，開發用來建置 project.json 專案的自訂建置引擎會以成熟且功能完整、名稱為 [MSBuild](https://github.com/Microsoft/msbuild) 的建置引擎取代。 MSBuild 是 .NET 社區中的一個眾所周知的引擎。 自該平臺首次發佈以來,它一直是關鍵技術。 由於 MSBuild 需要建構 .NET Core 應用程式,因此 MSBuild 已移植到 .NET Core,可用於 .NET Core 運行的任何平臺上。 .NET Core 其中一個主要承諾就是跨平台開發堆疊，而我們也以確認此移動不會中斷該承諾。

> [!TIP]
> 如果您是 MSBuild 的新增產品,並且希望瞭解有關它的更多內容,則可以從閱讀[MSBuild 概念](/visualstudio/msbuild/msbuild-concepts)文章開始。

## <a name="the-tooling-layers"></a>工具分層

隨著構建引擎的變化和現有項目系統的退出,一些問題自然而然地隨之而來。 這些更改中的任何一項都改變了 .NET Core 工具生態系統的整體「分層」? 有新的項目和元件嗎？

讓我們開始快速複習 Preview 2 分層，如下列圖片所示︰

![Preview 2 工具高階架構](media/cli-msbuild-architecture/p2-arch.png)

預覽 2 中工具的分層非常簡單。 在底部,基礎是 .NET 核心 CLI。 所有其他高級工具(如 Visual Studio 或 Visual Studio 代碼)都依賴於 CLI 來生成專案、還原依賴項等。 例如,如果 Visual Studio 想要執行還原操作,它將調`dotnet restore`用 CLI 中的命令。

隨著移動到新的專案系統，之前的圖表有所變更：

![.NET Core SDK 1.0.0 高階架構](media/cli-msbuild-architecture/p3-arch.png)

主要差異就是 CLI 不再是基本層；此角色現在會填入「共用的 SDK 元件」。 此共用 SDK 元件是一組目標和相關任務,負責編譯代碼、發佈代碼、打包 NuGet 包等。 .NET 核心 SDK 是開源的,可在[GitHub](https://github.com/dotnet/sdk)上獲取 SDK 儲存庫。

> [!NOTE]
> "目標"是一個 MSBuild 術語,指示 MSBuild 可以調用的命名操作。 它通常會搭配執行目標應該要執行之某些邏輯的一或多個工作。 MSBuild 支援許多現成的目標，例如 `Copy` 或 `Execute`；它也允許使用者使用受管理程式碼撰寫自己的工作，並定義目標以執行那些工作。 如需詳細資訊，請參閱 [MSBuild 工作](/visualstudio/msbuild/msbuild-tasks)。

所有工具組現在使用共用的 SDK 元件及其目標，包含 CLI。 例如,Visual Studio 2019`dotnet restore`不會調用 命令來還原 .NET Core 專案的依賴項。 相反,它直接使用"還原"目標。 由於這些都是 MSBuild 目標，您也可以使用原始的 MSBuild 來使用 [dotnet msbuild](dotnet-msbuild.md) 命令執行它們。

### <a name="cli-commands"></a>CLI 命令

共用 SDK 元件意味著大多數現有 CLI 命令已作為 MSBuild 任務和目標重新實現。 這對 CLI 命令和您的工具組的使用方式有什麼意義？

從使用方式的角度來看,它不會更改您使用 CLI 的方式。 CLI 仍然具有 .NET Core 1.0 預覽 2 版本中存在的核心命令:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

這些命令仍然執行您希望它們執行的操作(啟動專案、生成專案、發佈它、打包它們等)。 您可以查閱命令的幫助螢幕(使用`dotnet <command> --help`)或此網站上的文檔,以熟悉其行為。

從執行的角度來看,CLI 命令獲取其參數並建構對「原始」MSBuild 的調用,該調用設置所需的屬性並運行所需的目標。 為進一步說明這一點，請考慮下列命令︰

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

此命令使用"釋放"配置`pub`將應用程式發佈到資料夾中。 就內部而言，此命令會轉譯成下列 MSBuild 引動過程︰

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

此規則的顯著例外是和`new``run`命令。 它們尚未作為 MSBuild 目標實現。

### <a name="implicit-restore"></a>隱式還原

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
