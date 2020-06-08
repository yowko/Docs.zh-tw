---
title: 從 .NET Framework 移植到 .NET Core
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 74fe4519e41a07bc78a4dc346f8d1b52b5c7d092
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502765"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a><span data-ttu-id="2cbdc-103">從 .NET Framework 移植到 .NET Core 的總覽</span><span class="sxs-lookup"><span data-stu-id="2cbdc-103">Overview of porting from .NET Framework to .NET Core</span></span>

<span data-ttu-id="2cbdc-104">您的程式碼可能目前是在您想要移植到 .NET Core 的 .NET Framework 上執行。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="2cbdc-105">本文提供：</span><span class="sxs-lookup"><span data-stu-id="2cbdc-105">This article provides:</span></span>

* <span data-ttu-id="2cbdc-106">移植程式的總覽。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-106">An overview of the porting process.</span></span>
* <span data-ttu-id="2cbdc-107">當您將程式碼移植到 .NET Core 時，您可能會覺得有用的工具清單。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-107">A list of tools that you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="2cbdc-108">移轉程序概觀</span><span class="sxs-lookup"><span data-stu-id="2cbdc-108">Overview of the porting process</span></span>

<span data-ttu-id="2cbdc-109">從許多專案的 .NET Framework 移植到 .NET Core （或 .NET Standard）相當簡單。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-109">Porting to .NET Core (or .NET Standard) from .NET Framework for many projects is relatively straight forward.</span></span> <span data-ttu-id="2cbdc-110">有一些必要的變更，但其中有許多會遵循下面所述的模式。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-110">There are a number of changes that are required, but many of them follow the patterns outlined below.</span></span> <span data-ttu-id="2cbdc-111">應用程式模型可在 .NET Core 中使用的專案（例如程式庫、主控台應用程式和桌面應用程式）通常只需要少量變更。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-111">Projects where the app-model is available in .NET Core (such as libraries, console apps, and desktop applications) usually require little changes.</span></span> <span data-ttu-id="2cbdc-112">需要新應用程式模型的專案（例如移至 ASP.NET 的 ASP.NET Core）需要更多工作，但許多模式具有可在轉換期間使用的類比。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-112">Projects that require a new app model, such as moving to ASP.NET Core from ASP.NET, require a bit more work, but many patterns have analogs that can be used during the conversion.</span></span> <span data-ttu-id="2cbdc-113">本檔應協助識別使用者所採用的主要策略，以成功地將其程式碼基底轉換成目標 .NET Standard 或 .NET Core，並可解決兩個層級的轉換：整個方案和特定專案。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-113">This document should help with identifying the main strategies that have been employed by users to successfully convert their code bases to target .NET Standard or .NET Core and will address the conversion at two levels: solution-wide and project specific.</span></span> <span data-ttu-id="2cbdc-114">如需應用程式模型特定轉換的指示，請參閱底部的連結。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-114">See the links at the bottom for directions on app-model specific conversions.</span></span>

<span data-ttu-id="2cbdc-115">我們建議您在將專案移植到 .NET Core 時，使用下列進程。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-115">We recommend you use the following process when porting your project to .NET Core.</span></span> <span data-ttu-id="2cbdc-116">每個步驟都會介紹行為變更的可能位置，因此請確定您已充分測試程式庫或應用程式，然後再繼續進行後續步驟。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-116">Each of these steps introduces potential places for behavior changes, so ensure that you adequately test your library or application before continuing on to later steps.</span></span> <span data-ttu-id="2cbdc-117">第一個步驟是讓您的專案準備好切換到 .NET Standard 或 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-117">The first steps are to get your project ready for a switch to .NET Standard or .NET Core.</span></span> <span data-ttu-id="2cbdc-118">如果您有單元測試，最好先進行轉換，讓您可以繼續測試您正在處理的產品中的變更。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-118">If you have unit tests, it's best to convert them first so that you can continue testing changes in the product you're working on.</span></span> <span data-ttu-id="2cbdc-119">由於移植到 .NET Core 是您程式碼基底的重大變更，因此強烈建議您移植測試專案，讓您可以在將程式碼移植到時執行測試。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-119">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to port your test projects so that you can run tests as you port your code over.</span></span> <span data-ttu-id="2cbdc-120">MSTest、xUnit 和 NUnit 全都適用于 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-120">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2cbdc-121">開始使用</span><span class="sxs-lookup"><span data-stu-id="2cbdc-121">Getting started</span></span>

<span data-ttu-id="2cbdc-122">下列工具將在整個程式中使用：</span><span class="sxs-lookup"><span data-stu-id="2cbdc-122">The following tools will be used throughout the process:</span></span>

- <span data-ttu-id="2cbdc-123">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="2cbdc-123">Visual Studio 2019</span></span>
- <span data-ttu-id="2cbdc-124">下載[.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)</span><span class="sxs-lookup"><span data-stu-id="2cbdc-124">Download [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md)</span></span>
- <span data-ttu-id="2cbdc-125">_選擇性_安裝[dotnet try-convert](https://github.com/dotnet/try-convert)</span><span class="sxs-lookup"><span data-stu-id="2cbdc-125">_Optional_ Install [dotnet try-convert](https://github.com/dotnet/try-convert)</span></span>

## <a name="porting-a-solution"></a><span data-ttu-id="2cbdc-126">移植解決方案</span><span class="sxs-lookup"><span data-stu-id="2cbdc-126">Porting a solution</span></span>

<span data-ttu-id="2cbdc-127">當方案中有多個專案時，移植看起來會比較複雜，因為您必須以特定連續處理專案。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-127">When there are multiple projects in a solution, the porting can seem more complicated because you must address projects in a specific order.</span></span> <span data-ttu-id="2cbdc-128">轉換程式應該是最下層的方法，其中與方案中的其他專案沒有相依性的專案會先轉換，並繼續進行整個解決方案。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-128">The conversion process should be a bottom-up approach, where the projects with no dependencies on other projects in the solution are converted first, and continue up through the whole solution.</span></span>

<span data-ttu-id="2cbdc-129">為了識別應該遷移的訂單專案，您可以使用下列工具：</span><span class="sxs-lookup"><span data-stu-id="2cbdc-129">In order to identify the order projects should be migrated, you can use the following tools:</span></span>

- <span data-ttu-id="2cbdc-130">[Visual Studio 中](/visualstudio/modeling/create-layer-diagrams-from-your-code)的相依性圖表可以在方案中建立程式碼的導向圖形。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-130">[Dependency Diagrams in Visual Studio](/visualstudio/modeling/create-layer-diagrams-from-your-code) can create a directed graph of the code in a solution.</span></span>
- <span data-ttu-id="2cbdc-131">執行 `msbuild _SolutionPath_ /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg.json` 以產生包含專案參考清單的 json 檔。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-131">Run `msbuild _SolutionPath_ /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg.json` to generate a json document that includes list of project references.</span></span>
- <span data-ttu-id="2cbdc-132">使用參數執行[.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md) `-r DGML` ，以取出元件的相依性圖表。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-132">Run [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) with the `-r DGML` switch to retrieve a dependency diagram of the assemblies.</span></span> <span data-ttu-id="2cbdc-133">如需詳細資訊，請參閱[這裡](../../standard/analyzers/portability-analyzer.md#solution-wide-view)。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-133">For more information, see [here](../../standard/analyzers/portability-analyzer.md#solution-wide-view).</span></span>

<span data-ttu-id="2cbdc-134">有了相依性資訊之後，您就可以使用該資訊從分葉節點開始，並在下一節套用步驟的相依性樹狀結構中運作。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-134">Once you have dependency information, you can use that information to start at the leaf nodes and work your way up the dependency tree applying the steps in the next section.</span></span>

## <a name="per-project-steps"></a><span data-ttu-id="2cbdc-135">每個專案步驟</span><span class="sxs-lookup"><span data-stu-id="2cbdc-135">Per project steps</span></span>

<span data-ttu-id="2cbdc-136">將您的專案移植到 .NET Core 時，建議您使用下列進程：</span><span class="sxs-lookup"><span data-stu-id="2cbdc-136">We recommend you use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="2cbdc-137">`packages.config`使用[Visual Studio 中的轉換工具](/nuget/consume-packages/migrate-packages-config-to-package-reference)，將所有相依性轉換為[PackageReference](/nuget/consume-packages/package-references-in-project-files)格式。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-137">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="2cbdc-138">此步驟牽涉到從舊版格式轉換您的相依性 `packages.config` 。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-138">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="2cbdc-139">`packages.config`無法在 .NET Core 上使用，因此如果您有封裝相依性，就需要進行這項轉換。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-139">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span> <span data-ttu-id="2cbdc-140">它也只需要您直接在專案中使用的相依性，藉由減少您必須管理的相依性數目，讓後續步驟更容易。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-140">It also only requires the dependencies you are directly using in a project, which makes later steps easier by reducing the number of dependencies you must manage.</span></span>

1. <span data-ttu-id="2cbdc-141">將您的專案檔案轉換成新的 SDK 樣式檔案結構。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-141">Convert your project file to the new SDK-style files structure.</span></span> <span data-ttu-id="2cbdc-142">您可以為 .NET Core 建立新的專案，並複製原始程式檔，或嘗試使用工具轉換現有的專案檔。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-142">You can create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="2cbdc-143">.NET Core 使用簡化的（和不同的）[專案檔案格式](../tools/csproj.md)，而不是 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-143">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="2cbdc-144">您必須將專案檔轉換成此格式才能繼續。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-144">You'll need to convert your project files into this format to continue.</span></span> <span data-ttu-id="2cbdc-145">此專案樣式可讓您同時以 .NET Framework 為目標，此時您仍會想要鎖定目標。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-145">This project style allows you to also target .NET Framework, which at this point you'll still want to target.</span></span>

   <span data-ttu-id="2cbdc-146">您可以使用 dotnet 的 [[嘗試轉換](https://github.com/dotnet/try-convert)] 工具，嘗試將一個作業中較小的方案或個別專案移植到 .net Core 專案檔案格式。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-146">You can attempt to port smaller solutions or individual projects in one operation to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool.</span></span> <span data-ttu-id="2cbdc-147">`dotnet try-convert`不保證適用于您的所有專案，而且可能會對您所依賴的行為造成細微的變更。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-147">`dotnet try-convert` is not guaranteed to work for all your projects, and it may cause subtle changes in behavior that you depended on.</span></span> <span data-ttu-id="2cbdc-148">使用它做為自動化可自動化之基本事項的_起點_。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-148">Use it as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="2cbdc-149">這不是可供遷移專案的保證解決方案，因為相較于舊樣式的專案檔，SDK 樣式專案所使用的目標有許多差異。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-149">It isn't a guaranteed solution to migrating a project, as there are many differences in the targets used by the SDK style projects compared to the old-style project files.</span></span>

1. <span data-ttu-id="2cbdc-150">將您想要移植到 .NET Framework 目標的所有專案，都設為4.7.2 或更高。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-150">Retarget all projects you wish to port to target .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="2cbdc-151">此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-151">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

1. <span data-ttu-id="2cbdc-152">將所有相依性更新為最新版本。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-152">Update all dependencies to the latest version.</span></span> <span data-ttu-id="2cbdc-153">專案可能使用較舊版本的程式庫，但可能沒有 .NET Standard 支援。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-153">Projects may be using older versions of libraries that may not have .NET Standard support.</span></span> <span data-ttu-id="2cbdc-154">不過，較新的版本可以使用簡單的參數來支援它。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-154">However, later versions may support it with a simple switch.</span></span> <span data-ttu-id="2cbdc-155">如果程式庫中有重大變更，這可能需要變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-155">This may require code changes if there are breaking changes in libraries.</span></span>

1. <span data-ttu-id="2cbdc-156">使用[.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)來分析您的元件，並查看它們是否可移植到 .net Core。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-156">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="2cbdc-157">.NET 可攜性分析器工具會分析已編譯的元件，並產生報表。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-157">The .NET Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="2cbdc-158">此報告會顯示高階的可攜性摘要，以及您所使用的每個 API 在 NET Core 上無法取得的明細。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-158">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span> <span data-ttu-id="2cbdc-159">使用此工具時，只會提交您要轉換的個別專案，以專注于可能需要的 API 變更。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-159">While using the tool, only submit the individual project you are converting to focus on the API changes that are potentially needed.</span></span> <span data-ttu-id="2cbdc-160">許多 Api 在 .NET Core 中都具有對等的可用性，您會想要切換到此功能。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-160">Many of the APIs have equivalent availability in .NET Core, which you'll want to switch to.</span></span>

   <span data-ttu-id="2cbdc-161">讀取分析器所產生的報表時，重要資訊是實際使用的 Api，而不一定是目標平臺支援的百分比。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-161">While reading the reports generated by the analyzer, the important information is the actual APIs that are being used and not necessarily the percentage of support for the target platform.</span></span> <span data-ttu-id="2cbdc-162">許多 Api 在 .NET Standard/核心中都有相同的選項，因此，若要瞭解您的程式庫或應用程式所需的 API，將有助於判斷可攜性的含意。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-162">Many APIs have equivalent options in .NET Standard/Core, and so understanding the scenarios your library or application needs the API for will help determine the implication for portability.</span></span>

   <span data-ttu-id="2cbdc-163">在某些情況下，Api 不是相等的，而且您必須對平臺執行一些編譯器預處理器指示詞（也就是 `#if NET45` ）。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-163">There are some cases where APIs are not equivalent and you'll need to do some compiler preprocessor directives (that is, `#if NET45`) to special case the platforms.</span></span> <span data-ttu-id="2cbdc-164">此時，您的專案仍會以 .NET Framework 為目標。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-164">At this point, your project will still be targeting .NET Framework.</span></span> <span data-ttu-id="2cbdc-165">針對上述每個目標案例，建議使用已知的條件，並可視為案例。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-165">For each of these targeted cases, it is recommended to use well-known conditionals that can be understood as a scenario.</span></span>  <span data-ttu-id="2cbdc-166">例如，.NET Core 中的 AppDomain 支援受到限制，但在載入和卸載元件的案例中，有一個新的 API 無法在 .NET Core 中使用。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-166">For example, AppDomain support in .NET Core is limited, but for the scenario of loading and unloading assemblies, there is a new API that's not available in .NET Core.</span></span> <span data-ttu-id="2cbdc-167">在程式碼中處理這種情況的常見方式如下：</span><span class="sxs-lookup"><span data-stu-id="2cbdc-167">A common way to handle this in code would be something like this:</span></span>

   ```csharp
   #if FEATURE_APPDOMAIN_LOADING
   // Code that uses appdomains
   #elif FEATURE_ASSEMBLY_LOAD_CONTEXT
   // Code that uses assembly load context
   #else
   #error Unsupported platform
   #endif
   ```

1. <span data-ttu-id="2cbdc-168">將[.NET API 分析器](../../standard/analyzers/api-analyzer.md)安裝到您的專案，以識別 <xref:System.PlatformNotSupportedException> 在某些平臺上擲回的 api，以及一些其他潛在的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-168">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs that throw <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="2cbdc-169">這項工具與可攜性分析器類似，但不會分析程式碼是否可以在 .NET Core 上建立，而是會分析您是否使用 API，這種方式會在 <xref:System.PlatformNotSupportedException> 執行時間擲回。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-169">This tool is similar to the portability analyzer, but instead of analyzing if code can build on .NET Core, it analyzes whether you're using an API in a way that will throw a <xref:System.PlatformNotSupportedException> at run time.</span></span> <span data-ttu-id="2cbdc-170">雖然這在您從 .NET Framework 4.7.2 或更高版本中移動時並不常見，但仍可進行檢查。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-170">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span> <span data-ttu-id="2cbdc-171">如需有關在 .NET Core 上擲回例外狀況之 Api 的詳細資訊，請參閱[在 .Net core 上一律會擲回例外狀況的 api](../compatibility/unsupported-apis.md)。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-171">For more information about APIs that throw exceptions on .NET Core, see [APIs that always throw exceptions on .NET Core](../compatibility/unsupported-apis.md).</span></span>

1. <span data-ttu-id="2cbdc-172">此時，您可以切換為以 .NET Core 為目標（通常適用于應用程式）或 .NET Standard （適用于程式庫）。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-172">At this point, you can switch to targeting .NET Core (generally for applications) or .NET Standard (for libraries).</span></span>

   <span data-ttu-id="2cbdc-173">.NET Core 和 .NET Standard 之間的選擇主要取決於專案的執行位置。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-173">The choice between .NET Core and .NET Standard is largely dependent on where the project will be run.</span></span> <span data-ttu-id="2cbdc-174">如果它是其他應用程式所使用或透過 NuGet 散發的程式庫，則喜好設定通常會以 .NET Standard 為目標。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-174">If it is a library that will be consumed by other applications or distributed via NuGet, the preference is usually to target .NET Standard.</span></span> <span data-ttu-id="2cbdc-175">不過，基於效能或其他原因，可能會有僅適用于 .NET Core 的 Api。如果是這種情況，您應該將 .NET Core 的目標設為可用的 .NET Standard 組建，並降低效能或功能。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-175">However, there may be APIs that are only available on .NET Core for performance or other reasons; if that's the case, .NET Core should be targeted with potentially a .NET Standard build available as well with reduced performance or functionality.</span></span> <span data-ttu-id="2cbdc-176">藉由以 .NET Standard 為目標，專案將可在新的平臺上執行（例如 WebAssembly）。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-176">By targeting .NET Standard, the project will be ready to run on new platforms (such as WebAssembly).</span></span> <span data-ttu-id="2cbdc-177">如果專案相依于特定的應用程式架構（例如 ASP.NET Core），則目標會受到相依性支援的限制。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-177">If the project has dependencies on specific app frameworks (such as ASP.NET Core), then the target will be limited by what the dependencies support.</span></span>

   <span data-ttu-id="2cbdc-178">如果 .NET Framework 或 .NET Standard 的條件式編譯器代碼沒有預處理器指示詞，這就像在專案檔中尋找下列簡單：</span><span class="sxs-lookup"><span data-stu-id="2cbdc-178">If there are no preprocessor directives to conditional compile code for .NET Framework or .NET Standard, this will be as simple as finding the following in the project file:</span></span>

   ```xml
   <TargetFramework>net472</TargetFramework>
   ```

   <span data-ttu-id="2cbdc-179">並將它切換到所需的架構。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-179">and switch it to the desired framework.</span></span> <span data-ttu-id="2cbdc-180">針對 .NET Core 3.1，這會是：</span><span class="sxs-lookup"><span data-stu-id="2cbdc-180">For .NET Core 3.1, this would be:</span></span>

   ```xml
   <TargetFramework>netcoreapp3.1</TargetFramework>
   ```

   <span data-ttu-id="2cbdc-181">不過，如果這是您想要繼續支援 .NET Framework 特定組建的程式庫，您可以將它取代為下列內容，藉以[多目標](../../standard/library-guidance/cross-platform-targeting.md)：</span><span class="sxs-lookup"><span data-stu-id="2cbdc-181">However, if this is a library for which you want to continue supporting .NET Framework-specific builds, you can [multi-target](../../standard/library-guidance/cross-platform-targeting.md) by replacing it with the following:</span></span>

   ```xml
   <TargetFrameworks>net472;netstandard2.0</TargetFrameworks>
   ```

   <span data-ttu-id="2cbdc-182">如果您使用 Windows 特定 Api （例如登錄存取），請安裝[Windows 相容性套件](./windows-compat-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="2cbdc-182">If you're using Windows-specific APIs (such as registry access), install the [Windows Compatibility Pack](./windows-compat-pack.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2cbdc-183">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2cbdc-183">Next steps</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="2cbdc-184">[分析相關性](third-party-deps.md) 
> [封裝 NuGet 套件](../deploying/creating-nuget-packages.md) 
> [ASP.NET 至 ASP.NET Core 遷移](/aspnet/core/migration/proper-to-2x)</span><span class="sxs-lookup"><span data-stu-id="2cbdc-184">[Analyze dependencies](third-party-deps.md)
[Package NuGet Package](../deploying/creating-nuget-packages.md)
[ASP.NET to ASP.NET Core Migration](/aspnet/core/migration/proper-to-2x)</span></span>
