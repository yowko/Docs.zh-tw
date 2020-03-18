---
title: 從 .NET 框架到 .NET 核心的埠
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937331"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a><span data-ttu-id="618b2-103">從 .NET 框架移植到 .NET 核心的概述</span><span class="sxs-lookup"><span data-stu-id="618b2-103">Overview of porting from .NET Framework to .NET Core</span></span>

<span data-ttu-id="618b2-104">您可能有當前在 .NET 框架上運行的代碼，您有興趣移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="618b2-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="618b2-105">本文提供：</span><span class="sxs-lookup"><span data-stu-id="618b2-105">This article provides:</span></span>

* <span data-ttu-id="618b2-106">移植過程概述。</span><span class="sxs-lookup"><span data-stu-id="618b2-106">An overview of the porting process.</span></span>
* <span data-ttu-id="618b2-107">在將代碼移植到 .NET Core 時，您可能會發現有用的工具清單。</span><span class="sxs-lookup"><span data-stu-id="618b2-107">A list of tools that you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="618b2-108">移轉程序概觀</span><span class="sxs-lookup"><span data-stu-id="618b2-108">Overview of the porting process</span></span>

<span data-ttu-id="618b2-109">我們建議您在將專案移植到 .NET Core 時使用以下過程：</span><span class="sxs-lookup"><span data-stu-id="618b2-109">We recommend you use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="618b2-110">將要移植的所有專案重新置放為目標 .NET 框架 4.7.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="618b2-110">Retarget all projects you wish to port to target .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="618b2-111">此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。</span><span class="sxs-lookup"><span data-stu-id="618b2-111">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

2. <span data-ttu-id="618b2-112">使用[.NET 可攜性分析器](../../standard/analyzers/portability-analyzer.md)分析程式集，並查看它們是否可移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="618b2-112">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="618b2-113">API 可攜性分析器工具分析已編譯的程式集並生成報告。</span><span class="sxs-lookup"><span data-stu-id="618b2-113">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="618b2-114">此報告顯示高級可攜性摘要以及您正在使用的每個 API 的明細，這些 API 在 NET Core 上不可用。</span><span class="sxs-lookup"><span data-stu-id="618b2-114">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span>

3. <span data-ttu-id="618b2-115">將[.NET API 分析器](../../standard/analyzers/api-analyzer.md)安裝到專案中，以識別<xref:System.PlatformNotSupportedException>某些平臺上的 API 和其他一些潛在的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="618b2-115">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs that throw <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="618b2-116">此工具類似于可攜性分析器，但它不是分析代碼是否可以在 .NET Core 上構建，而是分析您是否以在運行時引發 A<xref:System.PlatformNotSupportedException>的方式使用 API。</span><span class="sxs-lookup"><span data-stu-id="618b2-116">This tool is similar to the portability analyzer, but instead of analyzing if code can build on .NET Core, it analyzes whether you're using an API in a way that will throw a <xref:System.PlatformNotSupportedException> at run time.</span></span> <span data-ttu-id="618b2-117">儘管如果您要從 .NET 框架 4.7.2 或更高版本移動，這種情況並不常見，但最好檢查一下。</span><span class="sxs-lookup"><span data-stu-id="618b2-117">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span> <span data-ttu-id="618b2-118">有關在 .NET Core 上引發異常的 API 的詳細資訊，請參閱[始終在 .NET Core 上引發異常的 API。](../compatibility/unsupported-apis.md)</span><span class="sxs-lookup"><span data-stu-id="618b2-118">For more information about APIs that throw exceptions on .NET Core, see [APIs that always throw exceptions on .NET Core](../compatibility/unsupported-apis.md).</span></span>

4. <span data-ttu-id="618b2-119">使用 Visual `packages.config` [Studio 中的轉換工具](/nuget/consume-packages/migrate-packages-config-to-package-reference)將所有依賴項轉換為[包參考](/nuget/consume-packages/package-references-in-project-files)格式。</span><span class="sxs-lookup"><span data-stu-id="618b2-119">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="618b2-120">此步驟涉及從舊`packages.config`格式轉換依賴項。</span><span class="sxs-lookup"><span data-stu-id="618b2-120">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="618b2-121">`packages.config`在 .NET Core 上不起作用，因此如果您有包依賴項，則需要進行此轉換。</span><span class="sxs-lookup"><span data-stu-id="618b2-121">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span>

5. <span data-ttu-id="618b2-122">為 .NET Core 創建新專案並複製原始檔案，或嘗試使用工具轉換現有專案檔案。</span><span class="sxs-lookup"><span data-stu-id="618b2-122">Create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="618b2-123">.NET Core 使用比 .NET 框架簡化（和不同的）[專案檔案格式](../tools/csproj.md)。</span><span class="sxs-lookup"><span data-stu-id="618b2-123">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="618b2-124">您需要將專案檔案轉換為此格式才能繼續。</span><span class="sxs-lookup"><span data-stu-id="618b2-124">You'll need to convert your project files into this format to continue.</span></span>

6. <span data-ttu-id="618b2-125">移植測試代碼。</span><span class="sxs-lookup"><span data-stu-id="618b2-125">Port your test code.</span></span>

   <span data-ttu-id="618b2-126">由於移植到 .NET Core 是代碼庫的重大更改，因此強烈建議您移植測試專案，以便在移植代碼時運行測試。</span><span class="sxs-lookup"><span data-stu-id="618b2-126">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to port your test projects so that you can run tests as you port your code over.</span></span> <span data-ttu-id="618b2-127">MSTest、xUnit 和 NUnit 都在 .NET Core 上工作。</span><span class="sxs-lookup"><span data-stu-id="618b2-127">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

<span data-ttu-id="618b2-128">此外，您可以使用[dotnet try 轉換](https://github.com/dotnet/try-convert)工具嘗試將較小的解決方案或單個專案移植到 .NET Core 專案檔案格式。</span><span class="sxs-lookup"><span data-stu-id="618b2-128">Additionally, you can attempt to port smaller solutions or individual projects in one operation to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool.</span></span> <span data-ttu-id="618b2-129">`dotnet try-convert`不能保證適用于所有專案，並且可能會導致您所依賴的行為發生細微的變化。</span><span class="sxs-lookup"><span data-stu-id="618b2-129">`dotnet try-convert` is not guaranteed to work for all your projects, and it may cause subtle changes in behavior that you depended on.</span></span> <span data-ttu-id="618b2-130">使用它作為一個_起點_，自動執行可以自動化的基本內容。</span><span class="sxs-lookup"><span data-stu-id="618b2-130">Use it as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="618b2-131">它不是遷移專案的保證解決方案。</span><span class="sxs-lookup"><span data-stu-id="618b2-131">It isn't a guaranteed solution to migrating a project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="618b2-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="618b2-132">Next steps</span></span>

>[!div class="nextstepaction"]
>[<span data-ttu-id="618b2-133">分析依賴項</span><span class="sxs-lookup"><span data-stu-id="618b2-133">Analyze dependencies</span></span>](third-party-deps.md)
