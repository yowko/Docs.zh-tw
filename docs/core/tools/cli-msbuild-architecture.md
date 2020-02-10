---
title: .NET Core 命令列工具架構
description: 深入了解 .NET Core 工具層級，以及最新版本中已變更的內容。
ms.date: 03/06/2017
ms.openlocfilehash: fde1a0acb6af9dd65aa3466b4ea37473b2eab6fb
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092911"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a><span data-ttu-id="10c0a-103">.NET Core 工具中變更的高階概觀</span><span class="sxs-lookup"><span data-stu-id="10c0a-103">High-level overview of changes in the .NET Core tools</span></span>

<span data-ttu-id="10c0a-104">本文件說明從 *project.json* 移轉至 MSBuild 以及 *csproj* 專案系統相關聯的變更，包含 .NET Core 工具分層與 CLI 命令實作之變更的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="10c0a-104">This document describes the changes associated with moving from *project.json* to MSBuild and the *csproj* project system with information on the changes to the layering of the .NET Core tooling and the implementation of the CLI commands.</span></span> <span data-ttu-id="10c0a-105">2017 年 3 月 7 日發行的 .NET Core SDK 1.0 與 Visual Studio 2017 會進行這些變更 (請參閱[公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/))，但一開始是隨 .NET Core SDK Preview 3 版本實作。</span><span class="sxs-lookup"><span data-stu-id="10c0a-105">These changes occurred with the release of .NET Core SDK 1.0 and Visual Studio 2017 on March 7, 2017 (see the [announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)) but were initially implemented with the release of the .NET Core SDK Preview 3.</span></span>

## <a name="moving-away-from-projectjson"></a><span data-ttu-id="10c0a-106">從 project.json 移開</span><span class="sxs-lookup"><span data-stu-id="10c0a-106">Moving away from project.json</span></span>

<span data-ttu-id="10c0a-107">.NET Core 的工具中最大的變更，絕對是將專案系統[從 project.json 改為使用 csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/)。</span><span class="sxs-lookup"><span data-stu-id="10c0a-107">The biggest change in the tooling for .NET Core is certainly the [move away from project.json to csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) as the project system.</span></span> <span data-ttu-id="10c0a-108">命令列工具的最新版本不支援 *project.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="10c0a-108">The latest versions of the command-line tools don't support *project.json* files.</span></span> <span data-ttu-id="10c0a-109">這表示它無法用來建立、執行或發行以 json 為基礎的應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="10c0a-109">That means that it cannot be used to build, run, or publish project.json based applications and libraries.</span></span> <span data-ttu-id="10c0a-110">若要使用這個版本的工具，請遷移您現有的專案，或啟動新的專案。</span><span class="sxs-lookup"><span data-stu-id="10c0a-110">To use this version of the tools, migrate your existing projects or start new ones.</span></span>

<span data-ttu-id="10c0a-111">做為移動的一部分，開發用來建置 project.json 專案的自訂建置引擎會以成熟且功能完整、名稱為 [MSBuild](https://github.com/Microsoft/msbuild) 的建置引擎取代。</span><span class="sxs-lookup"><span data-stu-id="10c0a-111">As part of this move, the custom build engine that was developed to build project.json projects was replaced with a mature and fully capable build engine called [MSBuild](https://github.com/Microsoft/msbuild).</span></span> <span data-ttu-id="10c0a-112">MSBuild 是 .NET 社區中的知名引擎。</span><span class="sxs-lookup"><span data-stu-id="10c0a-112">MSBuild is a well-known engine in the .NET community.</span></span> <span data-ttu-id="10c0a-113">從平臺的第一版開始，這是一項重要的技術。</span><span class="sxs-lookup"><span data-stu-id="10c0a-113">It has been a key technology since the platform's first release.</span></span> <span data-ttu-id="10c0a-114">因為它需要建立 .NET Core 應用程式，所以 MSBuild 已移植到 .NET Core，並可在 .NET Core 執行所在的任何平臺上使用。</span><span class="sxs-lookup"><span data-stu-id="10c0a-114">Because it needs to build .NET Core applications, MSBuild has been ported to .NET Core and can be used on any platform that .NET Core runs on.</span></span> <span data-ttu-id="10c0a-115">.NET Core 其中一個主要承諾就是跨平台開發堆疊，而我們也以確認此移動不會中斷該承諾。</span><span class="sxs-lookup"><span data-stu-id="10c0a-115">One of the main promises of .NET Core is that of a cross-platform development stack, and we have made sure that this move does not break that promise.</span></span>

> [!TIP]
> <span data-ttu-id="10c0a-116">如果您不熟悉 MSBuild，而且想要深入瞭解它，您可以從閱讀[MSBuild 概念](/visualstudio/msbuild/msbuild-concepts)一文開始。</span><span class="sxs-lookup"><span data-stu-id="10c0a-116">If you are new to MSBuild and would like to learn more about it, you can start by reading the [MSBuild concepts](/visualstudio/msbuild/msbuild-concepts) article.</span></span>

## <a name="the-tooling-layers"></a><span data-ttu-id="10c0a-117">工具分層</span><span class="sxs-lookup"><span data-stu-id="10c0a-117">The tooling layers</span></span>

<span data-ttu-id="10c0a-118">隨著組建引擎的變更，以及從現有的專案系統移開，自然會有一些問題。</span><span class="sxs-lookup"><span data-stu-id="10c0a-118">With the change in build engine and the move away from the existing project system, some questions naturally follow.</span></span> <span data-ttu-id="10c0a-119">其中任何一項變更都會變更 .NET Core 工具生態系統的整體「分層」功能嗎？</span><span class="sxs-lookup"><span data-stu-id="10c0a-119">Do any of these changes change the overall "layering" of the .NET Core tooling ecosystem?</span></span> <span data-ttu-id="10c0a-120">有新的項目和元件嗎？</span><span class="sxs-lookup"><span data-stu-id="10c0a-120">Are there new bits and components?</span></span>

<span data-ttu-id="10c0a-121">讓我們開始快速複習 Preview 2 分層，如下列圖片所示︰</span><span class="sxs-lookup"><span data-stu-id="10c0a-121">Let's start with a quick refresher on Preview 2 layering as shown in the following picture:</span></span>

![Preview 2 工具高階架構](media/cli-msbuild-architecture/p2-arch.png)

<span data-ttu-id="10c0a-123">Preview 2 中的工具分層是直接的。</span><span class="sxs-lookup"><span data-stu-id="10c0a-123">The layering of the tools in Preview 2 is straightforward.</span></span> <span data-ttu-id="10c0a-124">在底部，基礎是 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="10c0a-124">At the bottom, the foundation is the .NET Core CLI.</span></span> <span data-ttu-id="10c0a-125">所有其他較高層級的工具，例如 Visual Studio 或 Visual Studio Code，取決於並依賴 CLI 來建立專案、還原相依性等。</span><span class="sxs-lookup"><span data-stu-id="10c0a-125">All other, higher-level tools, such as Visual Studio or Visual Studio Code, depend and rely on the CLI to build projects, restore dependencies, and so on.</span></span> <span data-ttu-id="10c0a-126">例如，如果 Visual Studio 想要執行還原作業，它會呼叫 CLI 中的 `dotnet restore` （[請參閱 note](#dotnet-restore-note)）命令。</span><span class="sxs-lookup"><span data-stu-id="10c0a-126">For example, if Visual Studio wanted to perform a restore operation, it would call into the `dotnet restore` ([see note](#dotnet-restore-note)) command in the CLI.</span></span>

<span data-ttu-id="10c0a-127">隨著移動到新的專案系統，之前的圖表有所變更：</span><span class="sxs-lookup"><span data-stu-id="10c0a-127">With the move to the new project system, the previous diagram changes:</span></span>

![.NET Core SDK 1.0.0 高階架構](media/cli-msbuild-architecture/p3-arch.png)

<span data-ttu-id="10c0a-129">主要差異就是 CLI 不再是基本層；此角色現在會填入「共用的 SDK 元件」。</span><span class="sxs-lookup"><span data-stu-id="10c0a-129">The main difference is that the CLI is not the foundational layer anymore; this role is now filled by the "shared SDK component".</span></span> <span data-ttu-id="10c0a-130">這個共用的 SDK 元件是一組目標和相關聯的工作，負責編譯器代碼、發佈、封裝 NuGet 套件等等。</span><span class="sxs-lookup"><span data-stu-id="10c0a-130">This shared SDK component is a set of targets and associated tasks that are responsible for compiling code, publishing it, packing NuGet packages, and so on.</span></span> <span data-ttu-id="10c0a-131">.NET Core SDK 是開放原始碼，並可在 GitHub 上的[SDK](https://github.com/dotnet/sdk)存放庫中取得。</span><span class="sxs-lookup"><span data-stu-id="10c0a-131">The .NET Core SDK is open-source and is available on GitHub on the [SDK repo](https://github.com/dotnet/sdk).</span></span>

> [!NOTE]
> <span data-ttu-id="10c0a-132">「目標」是一個 MSBuild 詞彙，表示 MSBuild 可以叫用的已命名作業。</span><span class="sxs-lookup"><span data-stu-id="10c0a-132">A "target" is an MSBuild term that indicates a named operation that MSBuild can invoke.</span></span> <span data-ttu-id="10c0a-133">它通常會搭配執行目標應該要執行之某些邏輯的一或多個工作。</span><span class="sxs-lookup"><span data-stu-id="10c0a-133">It is usually coupled with one or more tasks that execute some logic that the target is supposed to do.</span></span> <span data-ttu-id="10c0a-134">MSBuild 支援許多現成的目標，例如 `Copy` 或 `Execute`；它也允許使用者使用受管理程式碼撰寫自己的工作，並定義目標以執行那些工作。</span><span class="sxs-lookup"><span data-stu-id="10c0a-134">MSBuild supports many ready-made targets such as `Copy` or `Execute`; it also allows users to write their own tasks using managed code and define targets to execute those tasks.</span></span> <span data-ttu-id="10c0a-135">如需詳細資訊，請參閱 [MSBuild 工作](/visualstudio/msbuild/msbuild-tasks)。</span><span class="sxs-lookup"><span data-stu-id="10c0a-135">For more information, see [MSBuild tasks](/visualstudio/msbuild/msbuild-tasks).</span></span>

<span data-ttu-id="10c0a-136">所有工具組現在使用共用的 SDK 元件及其目標，包含 CLI。</span><span class="sxs-lookup"><span data-stu-id="10c0a-136">All the toolsets now consume the shared SDK component and its targets, CLI included.</span></span> <span data-ttu-id="10c0a-137">例如，Visual Studio 2019 不會呼叫 `dotnet restore` （[請參閱 note](#dotnet-restore-note)）命令來還原 .net Core 專案的相依性。</span><span class="sxs-lookup"><span data-stu-id="10c0a-137">For example, Visual Studio 2019 doesn't call into the `dotnet restore` ([see note](#dotnet-restore-note)) command to restore dependencies for .NET Core projects.</span></span> <span data-ttu-id="10c0a-138">相反地，它會直接使用「還原」目標。</span><span class="sxs-lookup"><span data-stu-id="10c0a-138">Instead, it uses the "Restore" target directly.</span></span> <span data-ttu-id="10c0a-139">由於這些都是 MSBuild 目標，您也可以使用原始的 MSBuild 來使用 [dotnet msbuild](dotnet-msbuild.md) 命令執行它們。</span><span class="sxs-lookup"><span data-stu-id="10c0a-139">Since these are MSBuild targets, you can also use raw MSBuild to execute them using the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

### <a name="cli-commands"></a><span data-ttu-id="10c0a-140">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="10c0a-140">CLI commands</span></span>

<span data-ttu-id="10c0a-141">共用的 SDK 元件表示大部分現有的 CLI 命令都已根據重新實作為 MSBuild 工作和目標。</span><span class="sxs-lookup"><span data-stu-id="10c0a-141">The shared SDK component means that the majority of existing CLI commands have been reimplemented as MSBuild tasks and targets.</span></span> <span data-ttu-id="10c0a-142">這對 CLI 命令和您的工具組的使用方式有什麼意義？</span><span class="sxs-lookup"><span data-stu-id="10c0a-142">What does this mean for the CLI commands and your usage of the toolset?</span></span>

<span data-ttu-id="10c0a-143">從使用觀點來看，它不會變更您使用 CLI 的方式。</span><span class="sxs-lookup"><span data-stu-id="10c0a-143">From a usage perspective, it doesn't change the way you use the CLI.</span></span> <span data-ttu-id="10c0a-144">CLI 仍然具有 .NET Core 1.0 Preview 2 版本中存在的核心命令：</span><span class="sxs-lookup"><span data-stu-id="10c0a-144">The CLI still has the core commands that existed in the .NET Core 1.0 Preview 2 release:</span></span>

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

<span data-ttu-id="10c0a-145">這些命令仍會執行您預期的動作（新的專案、建立、發行、封裝、封裝等等）。</span><span class="sxs-lookup"><span data-stu-id="10c0a-145">These commands still do what you expect them to do (new up a project, build it, publish it, pack it, and so on).</span></span> <span data-ttu-id="10c0a-146">您可以查閱命令的說明畫面（使用 `dotnet <command> --help`）或此網站上的檔，以瞭解其行為。</span><span class="sxs-lookup"><span data-stu-id="10c0a-146">You can consult either the command's help screen (using `dotnet <command> --help`) or documentation on this site to get familiar with their behavior.</span></span>

<span data-ttu-id="10c0a-147">從執行的觀點來看，CLI 命令會採用其參數，並建立對「原始」 MSBuild 的呼叫，以設定所需的屬性，並執行所需的目標。</span><span class="sxs-lookup"><span data-stu-id="10c0a-147">From an execution perspective, the CLI commands take their parameters and construct a call to "raw" MSBuild that sets the needed properties and runs the desired target.</span></span> <span data-ttu-id="10c0a-148">為進一步說明這一點，請考慮下列命令︰</span><span class="sxs-lookup"><span data-stu-id="10c0a-148">To better illustrate this, consider the following command:</span></span>

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

<span data-ttu-id="10c0a-149">此命令會使用「發行」設定，將應用程式發佈至 `pub` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="10c0a-149">This command publishes an application into a `pub` folder using the "Release" configuration.</span></span> <span data-ttu-id="10c0a-150">就內部而言，此命令會轉譯成下列 MSBuild 引動過程︰</span><span class="sxs-lookup"><span data-stu-id="10c0a-150">Internally, this command gets translated into the following MSBuild invocation:</span></span>

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

<span data-ttu-id="10c0a-151">此規則的值得注意的例外狀況是 `new` 和 `run` 命令。</span><span class="sxs-lookup"><span data-stu-id="10c0a-151">Notable exceptions to this rule are the `new` and `run` commands.</span></span> <span data-ttu-id="10c0a-152">它們尚未實作為 MSBuild 目標。</span><span class="sxs-lookup"><span data-stu-id="10c0a-152">They have not been implemented as MSBuild targets.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
