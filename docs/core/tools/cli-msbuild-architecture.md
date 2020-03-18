---
title: .NET Core 命令列工具架構
description: 深入了解 .NET Core 工具層級，以及最新版本中已變更的內容。
ms.date: 03/06/2017
ms.openlocfilehash: fde1a0acb6af9dd65aa3466b4ea37473b2eab6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092911"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a><span data-ttu-id="4002f-103">.NET Core 工具中變更的高階概觀</span><span class="sxs-lookup"><span data-stu-id="4002f-103">High-level overview of changes in the .NET Core tools</span></span>

<span data-ttu-id="4002f-104">本文件說明從 *project.json* 移轉至 MSBuild 以及 *csproj* 專案系統相關聯的變更，包含 .NET Core 工具分層與 CLI 命令實作之變更的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4002f-104">This document describes the changes associated with moving from *project.json* to MSBuild and the *csproj* project system with information on the changes to the layering of the .NET Core tooling and the implementation of the CLI commands.</span></span> <span data-ttu-id="4002f-105">2017 年 3 月 7 日發行的 .NET Core SDK 1.0 與 Visual Studio 2017 會進行這些變更 (請參閱[公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/))，但一開始是隨 .NET Core SDK Preview 3 版本實作。</span><span class="sxs-lookup"><span data-stu-id="4002f-105">These changes occurred with the release of .NET Core SDK 1.0 and Visual Studio 2017 on March 7, 2017 (see the [announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)) but were initially implemented with the release of the .NET Core SDK Preview 3.</span></span>

## <a name="moving-away-from-projectjson"></a><span data-ttu-id="4002f-106">從 project.json 移開</span><span class="sxs-lookup"><span data-stu-id="4002f-106">Moving away from project.json</span></span>

<span data-ttu-id="4002f-107">.NET Core 的工具中最大的變更，絕對是將專案系統[從 project.json 改為使用 csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/)。</span><span class="sxs-lookup"><span data-stu-id="4002f-107">The biggest change in the tooling for .NET Core is certainly the [move away from project.json to csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) as the project system.</span></span> <span data-ttu-id="4002f-108">命令列工具的最新版本不支援 *project.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="4002f-108">The latest versions of the command-line tools don't support *project.json* files.</span></span> <span data-ttu-id="4002f-109">這意味著它不能用於構建、運行或發佈基於 project.json 的應用程式和庫。</span><span class="sxs-lookup"><span data-stu-id="4002f-109">That means that it cannot be used to build, run, or publish project.json based applications and libraries.</span></span> <span data-ttu-id="4002f-110">要使用此版本的工具，請遷移現有專案或啟動新專案。</span><span class="sxs-lookup"><span data-stu-id="4002f-110">To use this version of the tools, migrate your existing projects or start new ones.</span></span>

<span data-ttu-id="4002f-111">做為移動的一部分，開發用來建置 project.json 專案的自訂建置引擎會以成熟且功能完整、名稱為 [MSBuild](https://github.com/Microsoft/msbuild) 的建置引擎取代。</span><span class="sxs-lookup"><span data-stu-id="4002f-111">As part of this move, the custom build engine that was developed to build project.json projects was replaced with a mature and fully capable build engine called [MSBuild](https://github.com/Microsoft/msbuild).</span></span> <span data-ttu-id="4002f-112">MSBuild 是 .NET 社區中的一個眾所周知的引擎。</span><span class="sxs-lookup"><span data-stu-id="4002f-112">MSBuild is a well-known engine in the .NET community.</span></span> <span data-ttu-id="4002f-113">自該平臺首次發佈以來，它一直是關鍵技術。</span><span class="sxs-lookup"><span data-stu-id="4002f-113">It has been a key technology since the platform's first release.</span></span> <span data-ttu-id="4002f-114">由於 MSBuild 需要構建 .NET Core 應用程式，因此 MSBuild 已移植到 .NET Core，可用於 .NET Core 運行的任何平臺上。</span><span class="sxs-lookup"><span data-stu-id="4002f-114">Because it needs to build .NET Core applications, MSBuild has been ported to .NET Core and can be used on any platform that .NET Core runs on.</span></span> <span data-ttu-id="4002f-115">.NET Core 其中一個主要承諾就是跨平台開發堆疊，而我們也以確認此移動不會中斷該承諾。</span><span class="sxs-lookup"><span data-stu-id="4002f-115">One of the main promises of .NET Core is that of a cross-platform development stack, and we have made sure that this move does not break that promise.</span></span>

> [!TIP]
> <span data-ttu-id="4002f-116">如果您是 MSBuild 的新增產品，並且希望瞭解有關它的更多內容，則可以從閱讀[MSBuild 概念](/visualstudio/msbuild/msbuild-concepts)文章開始。</span><span class="sxs-lookup"><span data-stu-id="4002f-116">If you are new to MSBuild and would like to learn more about it, you can start by reading the [MSBuild concepts](/visualstudio/msbuild/msbuild-concepts) article.</span></span>

## <a name="the-tooling-layers"></a><span data-ttu-id="4002f-117">工具分層</span><span class="sxs-lookup"><span data-stu-id="4002f-117">The tooling layers</span></span>

<span data-ttu-id="4002f-118">隨著構建引擎的變化和現有專案系統的退出，一些問題自然而然地隨之而來。</span><span class="sxs-lookup"><span data-stu-id="4002f-118">With the change in build engine and the move away from the existing project system, some questions naturally follow.</span></span> <span data-ttu-id="4002f-119">這些更改中的任何一項都改變了 .NET Core 工具生態系統的整體"分層"？</span><span class="sxs-lookup"><span data-stu-id="4002f-119">Do any of these changes change the overall "layering" of the .NET Core tooling ecosystem?</span></span> <span data-ttu-id="4002f-120">有新的項目和元件嗎？</span><span class="sxs-lookup"><span data-stu-id="4002f-120">Are there new bits and components?</span></span>

<span data-ttu-id="4002f-121">讓我們開始快速複習 Preview 2 分層，如下列圖片所示︰</span><span class="sxs-lookup"><span data-stu-id="4002f-121">Let's start with a quick refresher on Preview 2 layering as shown in the following picture:</span></span>

![Preview 2 工具高階架構](media/cli-msbuild-architecture/p2-arch.png)

<span data-ttu-id="4002f-123">預覽 2 中工具的分層非常簡單。</span><span class="sxs-lookup"><span data-stu-id="4002f-123">The layering of the tools in Preview 2 is straightforward.</span></span> <span data-ttu-id="4002f-124">在底部，基礎是 .NET 核心 CLI。</span><span class="sxs-lookup"><span data-stu-id="4002f-124">At the bottom, the foundation is the .NET Core CLI.</span></span> <span data-ttu-id="4002f-125">所有其他高級工具（如 Visual Studio 或 Visual Studio 代碼）都依賴于 CLI 來生成專案、還原依賴項等。</span><span class="sxs-lookup"><span data-stu-id="4002f-125">All other, higher-level tools, such as Visual Studio or Visual Studio Code, depend and rely on the CLI to build projects, restore dependencies, and so on.</span></span> <span data-ttu-id="4002f-126">例如，如果 Visual Studio 想要執行還原操作，它將調用 CLI`dotnet restore`中的 （[請參閱 注釋](#dotnet-restore-note)） 命令。</span><span class="sxs-lookup"><span data-stu-id="4002f-126">For example, if Visual Studio wanted to perform a restore operation, it would call into the `dotnet restore` ([see note](#dotnet-restore-note)) command in the CLI.</span></span>

<span data-ttu-id="4002f-127">隨著移動到新的專案系統，之前的圖表有所變更：</span><span class="sxs-lookup"><span data-stu-id="4002f-127">With the move to the new project system, the previous diagram changes:</span></span>

![.NET Core SDK 1.0.0 高階架構](media/cli-msbuild-architecture/p3-arch.png)

<span data-ttu-id="4002f-129">主要差異就是 CLI 不再是基本層；此角色現在會填入「共用的 SDK 元件」。</span><span class="sxs-lookup"><span data-stu-id="4002f-129">The main difference is that the CLI is not the foundational layer anymore; this role is now filled by the "shared SDK component".</span></span> <span data-ttu-id="4002f-130">此共用 SDK 元件是一組目標和相關任務，負責編譯代碼、發佈代碼、打包 NuGet 包等。</span><span class="sxs-lookup"><span data-stu-id="4002f-130">This shared SDK component is a set of targets and associated tasks that are responsible for compiling code, publishing it, packing NuGet packages, and so on.</span></span> <span data-ttu-id="4002f-131">.NET 核心 SDK 是開源的，可在[GitHub](https://github.com/dotnet/sdk)上獲取 SDK 存儲庫。</span><span class="sxs-lookup"><span data-stu-id="4002f-131">The .NET Core SDK is open-source and is available on GitHub on the [SDK repo](https://github.com/dotnet/sdk).</span></span>

> [!NOTE]
> <span data-ttu-id="4002f-132">"目標"是一個 MSBuild 術語，指示 MSBuild 可以調用的命名操作。</span><span class="sxs-lookup"><span data-stu-id="4002f-132">A "target" is an MSBuild term that indicates a named operation that MSBuild can invoke.</span></span> <span data-ttu-id="4002f-133">它通常會搭配執行目標應該要執行之某些邏輯的一或多個工作。</span><span class="sxs-lookup"><span data-stu-id="4002f-133">It is usually coupled with one or more tasks that execute some logic that the target is supposed to do.</span></span> <span data-ttu-id="4002f-134">MSBuild 支援許多現成的目標，例如 `Copy` 或 `Execute`；它也允許使用者使用受管理程式碼撰寫自己的工作，並定義目標以執行那些工作。</span><span class="sxs-lookup"><span data-stu-id="4002f-134">MSBuild supports many ready-made targets such as `Copy` or `Execute`; it also allows users to write their own tasks using managed code and define targets to execute those tasks.</span></span> <span data-ttu-id="4002f-135">如需詳細資訊，請參閱 [MSBuild 工作](/visualstudio/msbuild/msbuild-tasks)。</span><span class="sxs-lookup"><span data-stu-id="4002f-135">For more information, see [MSBuild tasks](/visualstudio/msbuild/msbuild-tasks).</span></span>

<span data-ttu-id="4002f-136">所有工具組現在使用共用的 SDK 元件及其目標，包含 CLI。</span><span class="sxs-lookup"><span data-stu-id="4002f-136">All the toolsets now consume the shared SDK component and its targets, CLI included.</span></span> <span data-ttu-id="4002f-137">例如，Visual Studio 2019 不會調用`dotnet restore`（請參閱[）](#dotnet-restore-note)命令來還原 .NET Core 專案的依賴項。</span><span class="sxs-lookup"><span data-stu-id="4002f-137">For example, Visual Studio 2019 doesn't call into the `dotnet restore` ([see note](#dotnet-restore-note)) command to restore dependencies for .NET Core projects.</span></span> <span data-ttu-id="4002f-138">相反，它直接使用"還原"目標。</span><span class="sxs-lookup"><span data-stu-id="4002f-138">Instead, it uses the "Restore" target directly.</span></span> <span data-ttu-id="4002f-139">由於這些都是 MSBuild 目標，您也可以使用原始的 MSBuild 來使用 [dotnet msbuild](dotnet-msbuild.md) 命令執行它們。</span><span class="sxs-lookup"><span data-stu-id="4002f-139">Since these are MSBuild targets, you can also use raw MSBuild to execute them using the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

### <a name="cli-commands"></a><span data-ttu-id="4002f-140">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="4002f-140">CLI commands</span></span>

<span data-ttu-id="4002f-141">共用 SDK 元件意味著大多數現有 CLI 命令已作為 MSBuild 任務和目標重新實現。</span><span class="sxs-lookup"><span data-stu-id="4002f-141">The shared SDK component means that the majority of existing CLI commands have been reimplemented as MSBuild tasks and targets.</span></span> <span data-ttu-id="4002f-142">這對 CLI 命令和您的工具組的使用方式有什麼意義？</span><span class="sxs-lookup"><span data-stu-id="4002f-142">What does this mean for the CLI commands and your usage of the toolset?</span></span>

<span data-ttu-id="4002f-143">從使用方式的角度來看，它不會更改您使用 CLI 的方式。</span><span class="sxs-lookup"><span data-stu-id="4002f-143">From a usage perspective, it doesn't change the way you use the CLI.</span></span> <span data-ttu-id="4002f-144">CLI 仍然具有 .NET Core 1.0 預覽 2 版本中存在的核心命令：</span><span class="sxs-lookup"><span data-stu-id="4002f-144">The CLI still has the core commands that existed in the .NET Core 1.0 Preview 2 release:</span></span>

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

<span data-ttu-id="4002f-145">這些命令仍然執行您希望它們執行的操作（啟動專案、生成專案、發佈它、打包它們等）。</span><span class="sxs-lookup"><span data-stu-id="4002f-145">These commands still do what you expect them to do (new up a project, build it, publish it, pack it, and so on).</span></span> <span data-ttu-id="4002f-146">您可以查閱命令的説明螢幕（使用`dotnet <command> --help`）或此網站上的文檔，以熟悉其行為。</span><span class="sxs-lookup"><span data-stu-id="4002f-146">You can consult either the command's help screen (using `dotnet <command> --help`) or documentation on this site to get familiar with their behavior.</span></span>

<span data-ttu-id="4002f-147">從執行的角度來看，CLI 命令獲取其參數並構造對"原始"MSBuild 的調用，該調用設置所需的屬性並運行所需的目標。</span><span class="sxs-lookup"><span data-stu-id="4002f-147">From an execution perspective, the CLI commands take their parameters and construct a call to "raw" MSBuild that sets the needed properties and runs the desired target.</span></span> <span data-ttu-id="4002f-148">為進一步說明這一點，請考慮下列命令︰</span><span class="sxs-lookup"><span data-stu-id="4002f-148">To better illustrate this, consider the following command:</span></span>

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

<span data-ttu-id="4002f-149">此命令使用"釋放"配置`pub`將應用程式發佈到資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4002f-149">This command publishes an application into a `pub` folder using the "Release" configuration.</span></span> <span data-ttu-id="4002f-150">就內部而言，此命令會轉譯成下列 MSBuild 引動過程︰</span><span class="sxs-lookup"><span data-stu-id="4002f-150">Internally, this command gets translated into the following MSBuild invocation:</span></span>

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

<span data-ttu-id="4002f-151">此規則的顯著例外是 和`new``run`命令。</span><span class="sxs-lookup"><span data-stu-id="4002f-151">Notable exceptions to this rule are the `new` and `run` commands.</span></span> <span data-ttu-id="4002f-152">它們尚未作為 MSBuild 目標實現。</span><span class="sxs-lookup"><span data-stu-id="4002f-152">They have not been implemented as MSBuild targets.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
