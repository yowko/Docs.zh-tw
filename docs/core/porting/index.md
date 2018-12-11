---
title: 將程式碼從 .NET Framework 移植到 .NET Core
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 12/04/2018
ms.custom: seodec18
ms.openlocfilehash: 5c7cd8b01672e71b0db7255dad23d994a95ce532
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170037"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a><span data-ttu-id="27014-103">將您的程式碼從 .NET Framework 移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="27014-103">Port your code from .NET Framework to .NET Core</span></span>

<span data-ttu-id="27014-104">如果您有在 .NET Framework 上執行的程式碼，您可能也想要在 .NET Core 上執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="27014-104">If you've got code that runs on the .NET Framework, you may be interested in running your code on .NET Core, too.</span></span> <span data-ttu-id="27014-105">此處提供移轉程序的概觀，以及將您的程式碼移轉到 .NET Core 時可能覺得有用的工具清單。</span><span class="sxs-lookup"><span data-stu-id="27014-105">Here's an overview of the porting process and a list of the tools you may find helpful when porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="27014-106">移轉程序概觀</span><span class="sxs-lookup"><span data-stu-id="27014-106">Overview of the porting process</span></span>

<span data-ttu-id="27014-107">這是將您的程式碼移植到 .NET Core 的建議程序。</span><span class="sxs-lookup"><span data-stu-id="27014-107">This is the process we recommend you take when porting your project to .NET Core.</span></span> <span data-ttu-id="27014-108">此程序的每個步驟未來會在其他文章中進一步討論。</span><span class="sxs-lookup"><span data-stu-id="27014-108">Each step of the process is covered in more detail in further articles.</span></span>

1. <span data-ttu-id="27014-109">識別及說明協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="27014-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="27014-110">此步驟涉及了解程式協力廠商相依性是什麼、依賴它們的方式、查看它們是否也在 .NET Core 上執行的方式，以及不在 .NET Core 上執行時可以採取的步驟。</span><span class="sxs-lookup"><span data-stu-id="27014-110">This step involves understanding what your third-party dependencies are, how you depend on them, how to check if they also run on .NET Core, and steps you can take if they don't.</span></span> <span data-ttu-id="27014-111">它涵蓋將您的相依性移轉到 .NET Core 中使用之 [PackageReference](/nuget/consume-packages/package-references-in-project-files) 格式的方式。</span><span class="sxs-lookup"><span data-stu-id="27014-111">It also covers how you can migrate your dependencies over to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format that is used in .NET Core.</span></span>

2. <span data-ttu-id="27014-112">將所有想要移轉到目標 .NET Framework 4.7.2 或更新版本的專案重定為目標。</span><span class="sxs-lookup"><span data-stu-id="27014-112">Retarget all projects you wish to port to target the .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="27014-113">此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。</span><span class="sxs-lookup"><span data-stu-id="27014-113">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

3. <span data-ttu-id="27014-114">使用 [.NET 可攜性分析工具](../../standard/analyzers/portability-analyzer.md)來分析組件，並且根據結果開發移轉計劃。</span><span class="sxs-lookup"><span data-stu-id="27014-114">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="27014-115">API 可攜性分析器工具可分析您的設定組件，並產生報告以顯示高階可攜性摘要與您使用但 .NET Core 不提供之每個 API 的明細。</span><span class="sxs-lookup"><span data-stu-id="27014-115">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report that shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span> <span data-ttu-id="27014-116">您可以使用此報告與程式碼基底分析，開發移轉程式碼的計劃。</span><span class="sxs-lookup"><span data-stu-id="27014-116">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>

4. <span data-ttu-id="27014-117">移轉測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="27014-117">Port your tests code.</span></span>

   <span data-ttu-id="27014-118">因為移轉到 .NET Core 對程式碼基底是巨變，所以強烈建議您移轉測試，以便在移轉您的程式碼時執行測試。</span><span class="sxs-lookup"><span data-stu-id="27014-118">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to get your tests ported, so that you can run tests as you port your code over.</span></span> <span data-ttu-id="27014-119">MSTest、xUnit 與 NUnit 都支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="27014-119">MSTest, xUnit, and NUnit all support .NET Core.</span></span>

5. <span data-ttu-id="27014-120">執行移轉計劃！</span><span class="sxs-lookup"><span data-stu-id="27014-120">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="27014-121">協助工具</span><span class="sxs-lookup"><span data-stu-id="27014-121">Tools to help</span></span>

<span data-ttu-id="27014-122">下列清單顯示您在移轉程序期間可能會發現有用的工具：</span><span class="sxs-lookup"><span data-stu-id="27014-122">The following list shows tools you might find helpful to use during the porting process:</span></span>

* <span data-ttu-id="27014-123">.NET 可攜性分析器：[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)或 [Visual Studio 擴充功能](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)，一種工具鏈，可以產生一份報表，說明程式碼在 .NET Framework 與 .NET Core 之間的可攜程度，以及逐一分析組件問題。</span><span class="sxs-lookup"><span data-stu-id="27014-123">.NET Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span> <span data-ttu-id="27014-124">如需詳細資訊，請參閱 [.NET 可攜性分析器](../../standard/analyzers/portability-analyzer.md)。</span><span class="sxs-lookup"><span data-stu-id="27014-124">For more information, see [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md).</span></span>
* <span data-ttu-id="27014-125">.NET API 分析器 - 一個 Roslyn 分析器，可探索不同平台上 C# API 的潛在相容性風險，並偵測對已被取代之 API 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="27014-125">.NET API analyzer - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="27014-126">如需詳細資訊，請參閱 [.NET API 分析器](../../standard/analyzers/api-analyzer.md)。</span><span class="sxs-lookup"><span data-stu-id="27014-126">For more information, see [.NET API analyzer](../../standard/analyzers/api-analyzer.md).</span></span>
* <span data-ttu-id="27014-127">反向封裝搜尋：[有用的 Web 服務](https://packagesearch.azurewebsites.net)，可讓您搜尋類型，以及尋找包含該類型的封裝。</span><span class="sxs-lookup"><span data-stu-id="27014-127">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

<span data-ttu-id="27014-128">此外，您也可以嘗試使用 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 工具將較小的解決方案或個別專案移植到 .NET Core 專案檔案格式。</span><span class="sxs-lookup"><span data-stu-id="27014-128">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="27014-129">CsprojToVs2017 是第三方工具。</span><span class="sxs-lookup"><span data-stu-id="27014-129">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="27014-130">不保證它可搭配您的所有專案運作，而且它可能會導致您所依賴的行為發生些微變更。</span><span class="sxs-lookup"><span data-stu-id="27014-130">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="27014-131">CsprojToVs2017 應該當作將可自動化之基本事項自動化的「起點」使用。</span><span class="sxs-lookup"><span data-stu-id="27014-131">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="27014-132">它不是可以用來移轉專案檔格式保證解決方案。</span><span class="sxs-lookup"><span data-stu-id="27014-132">It is not a guaranteed solution to migrating project file formats.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="27014-133">下一步</span><span class="sxs-lookup"><span data-stu-id="27014-133">Next</span></span>](third-party-deps.md)
