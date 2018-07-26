---
title: .NET Core 命令列工具架構
description: 深入了解 .NET Core 工具層級，以及最新版本中已變更的內容。
author: blackdwarf
ms.date: 03/06/2017
ms.openlocfilehash: 1d96a0b1e19bf84af0ab645ebd104afc899ae656
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245125"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a><span data-ttu-id="71359-103">.NET Core 工具中變更的高階概觀</span><span class="sxs-lookup"><span data-stu-id="71359-103">High-level overview of changes in the .NET Core tools</span></span>

<span data-ttu-id="71359-104">本文件說明從 *project.json* 移轉至 MSBuild 以及 *csproj* 專案系統相關聯的變更，包含 .NET Core 工具分層與 CLI 命令實作之變更的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="71359-104">This document describes the changes associated with moving from *project.json* to MSBuild and the *csproj* project system with information on the changes to the layering of the .NET Core tooling and the implementation of the CLI commands.</span></span> <span data-ttu-id="71359-105">2017 年 3 月 7 日發行的 .NET Core SDK 1.0 與 Visual Studio 2017 會進行這些變更 (請參閱[公告](https://blogs.msdn.microsoft.com/dotnet/2017/03/07/announcing-net-core-tools-1-0/))，但一開始是隨 .NET Core SDK Preview 3 版本實作。</span><span class="sxs-lookup"><span data-stu-id="71359-105">These changes occurred with the release of .NET Core SDK 1.0 and Visual Studio 2017 on March 7, 2017 (see the [announcement](https://blogs.msdn.microsoft.com/dotnet/2017/03/07/announcing-net-core-tools-1-0/)) but were initially implemented with the release of the .NET Core SDK Preview 3.</span></span>

## <a name="moving-away-from-projectjson"></a><span data-ttu-id="71359-106">從 project.json 移開</span><span class="sxs-lookup"><span data-stu-id="71359-106">Moving away from project.json</span></span>
<span data-ttu-id="71359-107">.NET Core 的工具中最大的變更，絕對是將專案系統[從 project.json 改為使用 csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/)。</span><span class="sxs-lookup"><span data-stu-id="71359-107">The biggest change in the tooling for .NET Core is certainly the [move away from project.json to csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) as the project system.</span></span> <span data-ttu-id="71359-108">命令列工具的最新版本不支援 *project.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="71359-108">The latest versions of the command-line tools don't support *project.json* files.</span></span> <span data-ttu-id="71359-109">這表示它無法用來建置、執行或發佈以 project.json 為基礎的應用程式與程式庫。</span><span class="sxs-lookup"><span data-stu-id="71359-109">That means that it cannot be used to build, run or publish project.json based applications and libraries.</span></span> <span data-ttu-id="71359-110">若要使用此版本的工具，您必須移轉您現有的專案，或開始新的專案。</span><span class="sxs-lookup"><span data-stu-id="71359-110">In order to use this version of the tools, you will need to migrate your existing projects or start new ones.</span></span> 

<span data-ttu-id="71359-111">做為移動的一部分，開發用來建置 project.json 專案的自訂建置引擎會以成熟且功能完整、名稱為 [MSBuild](https://github.com/Microsoft/msbuild) 的建置引擎取代。</span><span class="sxs-lookup"><span data-stu-id="71359-111">As part of this move, the custom build engine that was developed to build project.json projects was replaced with a mature and fully capable build engine called [MSBuild](https://github.com/Microsoft/msbuild).</span></span> <span data-ttu-id="71359-112">MSBuild 是 .NET 社群中眾所周知的引擎，因為它從該平台首次發行以來一直就是關鍵技術。</span><span class="sxs-lookup"><span data-stu-id="71359-112">MSBuild is a well-known engine in the .NET community, since it has been a key technology since the platform's first release.</span></span> <span data-ttu-id="71359-113">當然，因為它需要建置 .NET Core 應用程式，MSBuild 已經移植到 .NET Core，且可以在執行 .NET Core 的任何平台上使用。</span><span class="sxs-lookup"><span data-stu-id="71359-113">Of course, because it needs to build .NET Core applications, MSBuild has been ported to .NET Core and can be used on any platform that .NET Core runs on.</span></span> <span data-ttu-id="71359-114">.NET Core 其中一個主要承諾就是跨平台開發堆疊，而我們也以確認此移動不會中斷該承諾。</span><span class="sxs-lookup"><span data-stu-id="71359-114">One of the main promises of .NET Core is that of a cross-platform development stack, and we have made sure that this move does not break that promise.</span></span>

> [!NOTE]
> <span data-ttu-id="71359-115">如果您不熟悉 MSBuild 且希望深入了解它，您可以透過閱讀 [MSBuild 概念](/visualstudio/msbuild/msbuild-concepts)一文開始。</span><span class="sxs-lookup"><span data-stu-id="71359-115">If you are new to MSBuild and would like to learn more about it, you can start by reading the [MSBuild Concepts](/visualstudio/msbuild/msbuild-concepts) article.</span></span> 

## <a name="the-tooling-layers"></a><span data-ttu-id="71359-116">工具分層</span><span class="sxs-lookup"><span data-stu-id="71359-116">The tooling layers</span></span>
<span data-ttu-id="71359-117">離開現有的專案系統以及轉換建置引擎，接下來很自然的問題就是這些變更是否會變更完整 .NET Core 工具生態系統的整體「分層」呢？</span><span class="sxs-lookup"><span data-stu-id="71359-117">With the move away from the existing project system as well as with building engine switches, the question that naturally follows is do any of these changes change the overall "layering" of the whole .NET Core tooling ecosystem?</span></span> <span data-ttu-id="71359-118">有新的項目和元件嗎？</span><span class="sxs-lookup"><span data-stu-id="71359-118">Are there new bits and components?</span></span>

<span data-ttu-id="71359-119">讓我們開始快速複習 Preview 2 分層，如下列圖片所示︰</span><span class="sxs-lookup"><span data-stu-id="71359-119">Let's start with a quick refresher on Preview 2 layering as shown in the following picture:</span></span>

![Preview 2 工具高階架構](media/cli-msbuild-architecture/p2-arch.png)

<span data-ttu-id="71359-121">這些工具的分層相當簡單。</span><span class="sxs-lookup"><span data-stu-id="71359-121">The layering of the tools is quite simple.</span></span> <span data-ttu-id="71359-122">在底部我們有 .NET Core 命令列工具做為基礎。</span><span class="sxs-lookup"><span data-stu-id="71359-122">At the bottom we have the .NET Core Command Line tools as a foundation.</span></span> <span data-ttu-id="71359-123">所有其他的高階工具 (例如 Visual Studio 或 Visual Studio Code) 則依存並仰賴 CLI 來建置專案、還原相依性等。</span><span class="sxs-lookup"><span data-stu-id="71359-123">All other, higher-level tools such as Visual Studio or Visual Studio Code, depend and rely on the CLI to build projects, restore dependencies and so on.</span></span> <span data-ttu-id="71359-124">舉例來說，這表示如果 Visual Studio 希望執行還原作業，它會呼叫 CLI 中的 `dotnet restore` ([請參閱附註](#dotnet-restore-note)) 命令。</span><span class="sxs-lookup"><span data-stu-id="71359-124">This meant that, for example, if Visual Studio wanted to perform a restore operation, it would call into `dotnet restore` ([see note](#dotnet-restore-note)) command in the CLI.</span></span> 

<span data-ttu-id="71359-125">隨著移動到新的專案系統，之前的圖表有所變更：</span><span class="sxs-lookup"><span data-stu-id="71359-125">With the move to the new project system, the previous diagram changes:</span></span> 

![.NET Core SDK 1.0.0 高階架構](media/cli-msbuild-architecture/p3-arch.png)

<span data-ttu-id="71359-127">主要差異就是 CLI 不再是基本層；此角色現在會填入「共用的 SDK 元件」。</span><span class="sxs-lookup"><span data-stu-id="71359-127">The main difference is that the CLI is not the foundational layer anymore; this role is now filled by the "shared SDK component".</span></span> <span data-ttu-id="71359-128">共用的 SDK 元件是負責編譯您的程式碼、發行程式碼，封裝 NuGet 套件等的一組目標和關聯工作。SDK 本身是開放原始碼，而且您可以在 GitHub 的 [SDK 存放庫](https://github.com/dotnet/sdk)上找到它。</span><span class="sxs-lookup"><span data-stu-id="71359-128">This shared SDK component is a set of targets and associated tasks that are responsible for compiling your code, publishing it, packing NuGet packages etc. The SDK itself is open-source and is available on GitHub on the [SDK repo](https://github.com/dotnet/sdk).</span></span> 

> [!NOTE]
> <span data-ttu-id="71359-129">「目標」是表示 MSBuild 可叫用之具名作業的 MSBuild 詞彙。</span><span class="sxs-lookup"><span data-stu-id="71359-129">A "target" is a MSBuild term that indicates a named operation that MSBuild can invoke.</span></span> <span data-ttu-id="71359-130">它通常會搭配執行目標應該要執行之某些邏輯的一或多個工作。</span><span class="sxs-lookup"><span data-stu-id="71359-130">It is usually coupled with one or more tasks that execute some logic that the target is supposed to do.</span></span> <span data-ttu-id="71359-131">MSBuild 支援許多現成的目標，例如 `Copy` 或 `Execute`；它也允許使用者使用受管理程式碼撰寫自己的工作，並定義目標以執行那些工作。</span><span class="sxs-lookup"><span data-stu-id="71359-131">MSBuild supports many ready-made targets such as `Copy` or `Execute`; it also allows users to write their own tasks using managed code and define targets to execute those tasks.</span></span> <span data-ttu-id="71359-132">如需詳細資訊，請參閱 [MSBuild 工作](/visualstudio/msbuild/msbuild-tasks)。</span><span class="sxs-lookup"><span data-stu-id="71359-132">For more information, see [MSBuild tasks](/visualstudio/msbuild/msbuild-tasks).</span></span> 

<span data-ttu-id="71359-133">所有工具組現在使用共用的 SDK 元件及其目標，包含 CLI。</span><span class="sxs-lookup"><span data-stu-id="71359-133">All the toolsets now consume the shared SDK component and its targets, CLI included.</span></span> <span data-ttu-id="71359-134">例如，下一版 Visual Studio 將不會呼叫 `dotnet restore` ([請參閱附註](#dotnet-restore-note)) 命令來還原 .NET Core 專案的相依性，它會直接使用「還原」目標。</span><span class="sxs-lookup"><span data-stu-id="71359-134">For example, the next version of Visual Studio will not call into `dotnet restore` ([see note](#dotnet-restore-note)) command to restore dependencies for .NET Core projects, it will use the "Restore" target directly.</span></span> <span data-ttu-id="71359-135">由於這些都是 MSBuild 目標，您也可以使用原始的 MSBuild 來使用 [dotnet msbuild](dotnet-msbuild.md) 命令執行它們。</span><span class="sxs-lookup"><span data-stu-id="71359-135">Since these are MSBuild targets, you can also use raw MSBuild to execute them using the [dotnet msbuild](dotnet-msbuild.md) command.</span></span> 

### <a name="cli-commands"></a><span data-ttu-id="71359-136">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="71359-136">CLI commands</span></span>
<span data-ttu-id="71359-137">共用的 SDK 元件表示大部分現有的 CLI 命令已經重新實作為 MSBuild 工作和目標。</span><span class="sxs-lookup"><span data-stu-id="71359-137">The shared SDK component means that the majority of existing CLI commands have been re-implemented as MSBuild tasks and targets.</span></span> <span data-ttu-id="71359-138">這對 CLI 命令和您的工具組的使用方式有什麼意義？</span><span class="sxs-lookup"><span data-stu-id="71359-138">What does this mean for the CLI commands and your usage of the toolset?</span></span> 

<span data-ttu-id="71359-139">從使用方式觀點來看，它不會變更您使用 CLI 的方式。</span><span class="sxs-lookup"><span data-stu-id="71359-139">From an usage perspective, it doesn't change the way you use the CLI.</span></span> <span data-ttu-id="71359-140">CLI 仍然具備存在於 Preview 2 版本中的核心命令：</span><span class="sxs-lookup"><span data-stu-id="71359-140">The CLI still has the core commands that exist in Preview 2 release:</span></span>

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

<span data-ttu-id="71359-141">這些命令仍然可以執行您所期望的動作 (新建專案、建置專案、發行專案、封裝專案等)。</span><span class="sxs-lookup"><span data-stu-id="71359-141">These commands still do what you expect them to do (new up a project, build it, publish it, pack it and so on).</span></span> <span data-ttu-id="71359-142">大部分的選項都沒有變更，且仍然存在，而您可以查閱命令的說明畫面 (使用 `dotnet <command> --help`) 或此網站上的文件，以熟悉任何變更。</span><span class="sxs-lookup"><span data-stu-id="71359-142">Majority of the options are not changed, and are still there, and you can consult either the commands' help screens (using `dotnet <command> --help`) or documentation on this site to get familiar with any changes.</span></span> 

<span data-ttu-id="71359-143">從執行觀點而言，CLI 命令會接受輸入參數並建構對「原始」MSBuild 的呼叫，這會設定所需的屬性，並執行所需的目標。</span><span class="sxs-lookup"><span data-stu-id="71359-143">From an execution perspective, the CLI commands will take their parameters and construct a call to "raw" MSBuild that will set the needed properties and run the desired target.</span></span> <span data-ttu-id="71359-144">為進一步說明這一點，請考慮下列命令︰</span><span class="sxs-lookup"><span data-stu-id="71359-144">To better illustrate this, consider the following command:</span></span> 

   `dotnet publish -o pub -c Release`
    
<span data-ttu-id="71359-145">此命令會使用「發行」組態，將應用程式發佈至 `pub` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="71359-145">This command is publishing an application into a `pub` folder using the "Release" configuration.</span></span> <span data-ttu-id="71359-146">就內部而言，此命令會轉譯成下列 MSBuild 引動過程︰</span><span class="sxs-lookup"><span data-stu-id="71359-146">Internally, this command gets translated into the following MSBuild invocation:</span></span> 

   `dotnet msbuild /t:Publish /p:OutputPath=pub /p:Configuration=Release`

<span data-ttu-id="71359-147">此規則值得注意的例外狀況為 `new` 和 `run` 命令，因為它們尚未實作為 MSBuild 目標。</span><span class="sxs-lookup"><span data-stu-id="71359-147">The notable exception to this rule are `new` and `run` commands, as they have not been implemented as MSBuild targets.</span></span>

<a name="dotnet-restore-note"></a>  
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
