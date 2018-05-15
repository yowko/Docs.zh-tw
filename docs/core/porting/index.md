---
title: 從 .NET Framework 移轉到 .NET Core
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: bf4f50ca915f21cdda6b99ae6bdf9e837eca3ae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="bc55b-103">從 .NET Framework 移轉到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="bc55b-103">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="bc55b-104">如果已在 .NET Framework 上執行程式碼，您可能也想要在 .NET Core 1.0 執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="bc55b-104">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core 1.0.</span></span>  <span data-ttu-id="bc55b-105">本文章涵蓋移轉程序的概觀，以及移轉到 .NET Core 時可能覺得有用的工具清單。</span><span class="sxs-lookup"><span data-stu-id="bc55b-105">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="bc55b-106">移轉程序概觀</span><span class="sxs-lookup"><span data-stu-id="bc55b-106">Overview of the Porting Process</span></span>

<span data-ttu-id="bc55b-107">建議的移轉程序會遵循下列一系列步驟。</span><span class="sxs-lookup"><span data-stu-id="bc55b-107">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="bc55b-108">此程序的每個部分未來會在其他文章中進一步討論。</span><span class="sxs-lookup"><span data-stu-id="bc55b-108">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="bc55b-109">識別及說明協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="bc55b-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="bc55b-110">這涉及了解程式協力廠商相依性是什麼、依賴它們的方式、查看它們是否也在 .NET Core 上執行的方式，以及不在 .NET Core 上執行時可以採取的步驟。</span><span class="sxs-lookup"><span data-stu-id="bc55b-110">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="bc55b-111">將所有想要移轉到目標 .NET Framework 4.6.2 的專案重定為目標。</span><span class="sxs-lookup"><span data-stu-id="bc55b-111">Retarget all projects you wish to port to target .NET Framework 4.6.2.</span></span>

   <span data-ttu-id="bc55b-112">這可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。</span><span class="sxs-lookup"><span data-stu-id="bc55b-112">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="bc55b-113">使用 [API 可攜性分析工具](https://github.com/Microsoft/dotnet-apiport/) 分析組件，並且根據結果開發移轉計劃。</span><span class="sxs-lookup"><span data-stu-id="bc55b-113">Use the [API Portability Analyzer tool](https://github.com/Microsoft/dotnet-apiport/) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="bc55b-114">API 可攜性分析工具會分析已編譯的組件並產生報告，顯示高階的可攜性摘要，以及您使用但 .NET Core 不提供的每個 API 分析。</span><span class="sxs-lookup"><span data-stu-id="bc55b-114">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="bc55b-115">您可以使用此報告與程式碼基底分析，開發移轉程式碼的計劃。</span><span class="sxs-lookup"><span data-stu-id="bc55b-115">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="bc55b-116">移轉測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="bc55b-116">Port your tests code.</span></span>

   <span data-ttu-id="bc55b-117">因為移轉到 .NET Core 對程式碼基底是巨變，所以強烈建議您移轉測試，以便在移轉程式碼時執行測試。</span><span class="sxs-lookup"><span data-stu-id="bc55b-117">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="bc55b-118">MSTest、xUnit 和 NUnit 都支援目前的 .NET Core 1.0。</span><span class="sxs-lookup"><span data-stu-id="bc55b-118">MSTest, xUnit, and NUnit all support .NET Core 1.0 today.</span></span>
   
6. <span data-ttu-id="bc55b-119">執行移轉計劃！</span><span class="sxs-lookup"><span data-stu-id="bc55b-119">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="bc55b-120">協助工具</span><span class="sxs-lookup"><span data-stu-id="bc55b-120">Tools to help</span></span>

<span data-ttu-id="bc55b-121">以下是您會發現有幫助的簡短工具清單︰</span><span class="sxs-lookup"><span data-stu-id="bc55b-121">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="bc55b-122">NuGet - [NuGet 用戶端](https://dist.nuget.org/index.html)或 [NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)，適用於 .NET 實作的 Microsoft 封裝管理員。</span><span class="sxs-lookup"><span data-stu-id="bc55b-122">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="bc55b-123">API 可攜性分析器：[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)或 [Visual Studio 擴充功能](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)，一種工具鏈，可以產生一份報表，說明程式碼在 .NET Framework 與 .NET Core 之間的可攜程度，以及逐一分析組件問題。</span><span class="sxs-lookup"><span data-stu-id="bc55b-123">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="bc55b-124">如需詳細資訊，請參閱 [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/)。</span><span class="sxs-lookup"><span data-stu-id="bc55b-124">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="bc55b-125">反向封裝搜尋：[有用的 Web 服務](https://packagesearch.azurewebsites.net)，可讓您搜尋類型，以及尋找包含該類型的封裝。</span><span class="sxs-lookup"><span data-stu-id="bc55b-125">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bc55b-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bc55b-126">Next steps</span></span>

[<span data-ttu-id="bc55b-127">分析協力廠商相依性。</span><span class="sxs-lookup"><span data-stu-id="bc55b-127">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
