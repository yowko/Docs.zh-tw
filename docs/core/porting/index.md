---
title: 將程式碼從 .NET Framework 移植到 .NET Core
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 09/13/2019
ms.custom: seodec18
ms.openlocfilehash: b6c02932b5d9c7ccc2743dd38dddf2904f9c24e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039655"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a><span data-ttu-id="29e25-103">將您的程式碼從 .NET Framework 移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="29e25-103">Port your code from .NET Framework to .NET Core</span></span>

<span data-ttu-id="29e25-104">如果您有在 .NET Framework 上執行的程式碼，您可能也想要在 .NET Core 上執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="29e25-104">If you've got code that runs on the .NET Framework, you may be interested in running your code on .NET Core, too.</span></span> <span data-ttu-id="29e25-105">此處提供移轉程序的概觀，以及將您的程式碼移轉到 .NET Core 時可能覺得有用的工具清單。</span><span class="sxs-lookup"><span data-stu-id="29e25-105">Here's an overview of the porting process and a list of the tools you may find helpful when porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="29e25-106">移轉程序概觀</span><span class="sxs-lookup"><span data-stu-id="29e25-106">Overview of the porting process</span></span>

<span data-ttu-id="29e25-107">這是將您的程式碼移植到 .NET Core 的建議程序。</span><span class="sxs-lookup"><span data-stu-id="29e25-107">This is the process we recommend you take when porting your project to .NET Core.</span></span> <span data-ttu-id="29e25-108">此程序的每個步驟未來會在其他文章中進一步討論。</span><span class="sxs-lookup"><span data-stu-id="29e25-108">Each step of the process is covered in more detail in further articles.</span></span>

1. <span data-ttu-id="29e25-109">識別及說明協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="29e25-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="29e25-110">此步驟涉及了解程式協力廠商相依性是什麼、依賴它們的方式、查看它們是否也在 .NET Core 上執行的方式，以及不在 .NET Core 上執行時可以採取的步驟。</span><span class="sxs-lookup"><span data-stu-id="29e25-110">This step involves understanding what your third-party dependencies are, how you depend on them, how to check if they also run on .NET Core, and steps you can take if they don't.</span></span> <span data-ttu-id="29e25-111">它涵蓋將您的相依性移轉到 .NET Core 中使用之 [PackageReference](/nuget/consume-packages/package-references-in-project-files) 格式的方式。</span><span class="sxs-lookup"><span data-stu-id="29e25-111">It also covers how you can migrate your dependencies over to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format that is used in .NET Core.</span></span>

2. <span data-ttu-id="29e25-112">將所有想要移轉到目標 .NET Framework 4.7.2 或更新版本的專案重定為目標。</span><span class="sxs-lookup"><span data-stu-id="29e25-112">Retarget all projects you wish to port to target the .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="29e25-113">此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。</span><span class="sxs-lookup"><span data-stu-id="29e25-113">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

3. <span data-ttu-id="29e25-114">使用 [.NET 可攜性分析工具](../../standard/analyzers/portability-analyzer.md)來分析組件，並且根據結果開發移轉計劃。</span><span class="sxs-lookup"><span data-stu-id="29e25-114">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="29e25-115">API 可攜性分析器工具會分析您已編譯的元件，並產生報表，其中顯示高層級的可攜性摘要，以及您所使用且在目標 .NET Core 平臺公用介面上未提供的每個 API 的細目。</span><span class="sxs-lookup"><span data-stu-id="29e25-115">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report that shows a high-level portability summary and a breakdown of each API you're using that isn't available on targeted .NET Core platform public surface.</span></span> <span data-ttu-id="29e25-116">您可以使用此報告與程式碼基底分析，開發移轉程式碼的計劃。</span><span class="sxs-lookup"><span data-stu-id="29e25-116">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>

4. <span data-ttu-id="29e25-117">將專案檔轉換成目標 .net Core 版本之後，您可以使用 Roslyn 型的[.net API 分析器](../../standard/analyzers/api-analyzer.md)來識別<xref:System.PlatformNotSupportedException>在某些平臺上擲回的 api，以及一些其他潛在的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="29e25-117">Once you have your project file converted to your targeted .NET Core version, you can use Roslyn based [.NET API analyzer](../../standard/analyzers/api-analyzer.md) to identify APIs throwing <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

5. <span data-ttu-id="29e25-118">移轉測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="29e25-118">Port your tests code.</span></span>

   <span data-ttu-id="29e25-119">因為移轉到 .NET Core 對程式碼基底是巨變，所以強烈建議您移轉測試，以便在移轉您的程式碼時執行測試。</span><span class="sxs-lookup"><span data-stu-id="29e25-119">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to get your tests ported, so that you can run tests as you port your code over.</span></span> <span data-ttu-id="29e25-120">MSTest、xUnit 與 NUnit 都支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="29e25-120">MSTest, xUnit, and NUnit all support .NET Core.</span></span>

6. <span data-ttu-id="29e25-121">執行移轉計劃！</span><span class="sxs-lookup"><span data-stu-id="29e25-121">Execute your plan for porting!</span></span>

<span data-ttu-id="29e25-122">下列清單顯示您在移轉程序期間可能會發現有用的工具：</span><span class="sxs-lookup"><span data-stu-id="29e25-122">The following list shows tools you might find helpful to use during the porting process:</span></span>

* <span data-ttu-id="29e25-123">.NET 可移植性分析器：[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)或 [Visual Studio 延伸模組](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)，一種可以產生報表的工具，說明程式碼在 .NET Framework 和目標 .NET Core 平台之間的可移植程度。</span><span class="sxs-lookup"><span data-stu-id="29e25-123">.NET Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), a tool that can generate a report of how portable your code is between .NET Framework and your target .NET Core platform.</span></span> <span data-ttu-id="29e25-124">此報表包含目標 .NET Core 平台上所缺少的類型和 API 各組件細項。</span><span class="sxs-lookup"><span data-stu-id="29e25-124">The report contains an assembly-by-assembly breakdown of the Type and APIs missing on the target .NET Core platform.</span></span> <span data-ttu-id="29e25-125">如需詳細資訊，請參閱 [.NET 可攜性分析器](../../standard/analyzers/portability-analyzer.md)。</span><span class="sxs-lookup"><span data-stu-id="29e25-125">For more information, see [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md).</span></span> <span data-ttu-id="29e25-126">建議您在開始移植之前執行 .NET 可攜性分析器工具，因為它可協助您識別特定目標 .NET 平臺公用介面中遺漏 Api 的任何差距。</span><span class="sxs-lookup"><span data-stu-id="29e25-126">It is recommended to run the .NET Portability Analyzer tool before you start porting, as it will help you identify any gaps in missing APIs in specific targeted .NET platform public surface.</span></span>
* <span data-ttu-id="29e25-127">.NET API 分析器：一種 Roslyn 分析器，可探索在某些平台上擲出 <xref:System.PlatformNotSupportedException> 的 .NET Standard API、偵測對已淘汰 API 的呼叫，以及探索不同平台上 C# API 的其他潛在相容性風險。</span><span class="sxs-lookup"><span data-stu-id="29e25-127">.NET API Analyzer - A Roslyn analyzer that discovers .NET Standard API that throws <xref:System.PlatformNotSupportedException> on some platforms, detects calls to deprecated APIs, and discovers some other potential compatibility risks for C# APIs on different platforms.</span></span> <span data-ttu-id="29e25-128">如需詳細資訊，請參閱 [.NET API 分析器](../../standard/analyzers/api-analyzer.md)。</span><span class="sxs-lookup"><span data-stu-id="29e25-128">For more information, see [.NET API analyzer](../../standard/analyzers/api-analyzer.md).</span></span> <span data-ttu-id="29e25-129">在您已建立 .NET Core 專案後，此分析器有助於找出不同平台上的執行階段行為差異。</span><span class="sxs-lookup"><span data-stu-id="29e25-129">This analyzer is helpful after you already created your .NET Core project to identify runtime behavior differences on different platforms.</span></span>
* <span data-ttu-id="29e25-130">反向封裝搜尋：[有用的 Web 服務](https://packagesearch.azurewebsites.net)，可讓您搜尋類型，以及尋找包含該類型的封裝。</span><span class="sxs-lookup"><span data-stu-id="29e25-130">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

<span data-ttu-id="29e25-131">此外，您也可以嘗試使用 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 工具將較小的解決方案或個別專案移植到 .NET Core 專案檔案格式。</span><span class="sxs-lookup"><span data-stu-id="29e25-131">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING]
> <span data-ttu-id="29e25-132">CsprojToVs2017 是第三方工具。</span><span class="sxs-lookup"><span data-stu-id="29e25-132">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="29e25-133">不保證它可搭配您的所有專案運作，而且它可能會導致您所依賴的行為發生些微變更。</span><span class="sxs-lookup"><span data-stu-id="29e25-133">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="29e25-134">CsprojToVs2017 應該當作將可自動化之基本事項自動化的「起點」使用。</span><span class="sxs-lookup"><span data-stu-id="29e25-134">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="29e25-135">它不是可以用來移轉專案檔格式保證解決方案。</span><span class="sxs-lookup"><span data-stu-id="29e25-135">It is not a guaranteed solution to migrating project file formats.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="29e25-136">下一個</span><span class="sxs-lookup"><span data-stu-id="29e25-136">Next</span></span>](net-framework-tech-unavailable.md)
