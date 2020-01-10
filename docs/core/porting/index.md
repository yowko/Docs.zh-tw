---
title: 從 .NET Framework 到 .NET Core 的埠
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: b5b010acbccf134afe800aa5bb98a0ae6e9ffa25
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777363"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a><span data-ttu-id="5732a-103">從 .NET Framework 移植到 .NET Core 的總覽</span><span class="sxs-lookup"><span data-stu-id="5732a-103">Overview of porting from .NET Framework to .NET Core</span></span>

<span data-ttu-id="5732a-104">您的程式碼可能目前是在您想要移植到 .NET Core 的 .NET Framework 上執行。</span><span class="sxs-lookup"><span data-stu-id="5732a-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="5732a-105">本文提供：</span><span class="sxs-lookup"><span data-stu-id="5732a-105">This article provides:</span></span>

* <span data-ttu-id="5732a-106">移植程式的總覽。</span><span class="sxs-lookup"><span data-stu-id="5732a-106">An overview of the porting process.</span></span>
* <span data-ttu-id="5732a-107">當您將程式碼移植到 .NET Core 時，您可能會覺得有用的工具清單。</span><span class="sxs-lookup"><span data-stu-id="5732a-107">A list of tools that you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="5732a-108">移轉程序概觀</span><span class="sxs-lookup"><span data-stu-id="5732a-108">Overview of the porting process</span></span>

<span data-ttu-id="5732a-109">將您的專案移植到 .NET Core 時，建議您使用下列進程：</span><span class="sxs-lookup"><span data-stu-id="5732a-109">We recommend you use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="5732a-110">將您想要移植到 .NET Framework 目標的所有專案，都設為4.7.2 或更高。</span><span class="sxs-lookup"><span data-stu-id="5732a-110">Retarget all projects you wish to port to target .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="5732a-111">此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。</span><span class="sxs-lookup"><span data-stu-id="5732a-111">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

2. <span data-ttu-id="5732a-112">使用[.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)來分析您的元件，並查看它們是否可移植到 .net Core。</span><span class="sxs-lookup"><span data-stu-id="5732a-112">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="5732a-113">API 可攜性分析器工具會分析已編譯的元件，並產生報表。</span><span class="sxs-lookup"><span data-stu-id="5732a-113">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="5732a-114">此報告會顯示高階的可攜性摘要，以及您所使用的每個 API 在 NET Core 上無法取得的明細。</span><span class="sxs-lookup"><span data-stu-id="5732a-114">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span>

3. <span data-ttu-id="5732a-115">將[.NET API 分析器](../../standard/analyzers/api-analyzer.md)安裝到您的專案，以識別在某些平臺上擲回 <xref:System.PlatformNotSupportedException> 的 api，以及一些其他潛在的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="5732a-115">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs throwing <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="5732a-116">這項工具與可攜性分析器類似，但不會分析是否可以在 .NET Core 上建立，而是會分析您是否以在執行時間擲回 <xref:System.PlatformNotSupportedException> 的方式來使用 API。</span><span class="sxs-lookup"><span data-stu-id="5732a-116">This tool is similar to the portability analyzer, but instead of analyzing if things can build on .NET Core, it analyzes if you're using an API in a way that will throw the <xref:System.PlatformNotSupportedException> at run time.</span></span> <span data-ttu-id="5732a-117">雖然這在您從 .NET Framework 4.7.2 或更高版本中移動時並不常見，但仍可進行檢查。</span><span class="sxs-lookup"><span data-stu-id="5732a-117">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span>

4. <span data-ttu-id="5732a-118">使用[Visual Studio 中的轉換工具](/nuget/consume-packages/migrate-packages-config-to-package-reference)，將所有 `packages.config` 相依性轉換為[PackageReference](/nuget/consume-packages/package-references-in-project-files)格式。</span><span class="sxs-lookup"><span data-stu-id="5732a-118">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="5732a-119">此步驟牽涉到從舊版 `packages.config` 格式轉換相依性。</span><span class="sxs-lookup"><span data-stu-id="5732a-119">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="5732a-120">`packages.config` 無法在 .NET Core 上執行，因此如果您有封裝相依性，就需要進行這項轉換。</span><span class="sxs-lookup"><span data-stu-id="5732a-120">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span>

5. <span data-ttu-id="5732a-121">為 .NET Core 建立新的專案，並複製原始程式檔，或嘗試使用工具轉換現有的專案檔。</span><span class="sxs-lookup"><span data-stu-id="5732a-121">Create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="5732a-122">.NET Core 使用簡化的（和不同的）[專案檔案格式](../tools/csproj.md)，而不是 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="5732a-122">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="5732a-123">您必須將專案檔轉換成此格式才能繼續。</span><span class="sxs-lookup"><span data-stu-id="5732a-123">You'll need to convert your project files into this format to continue.</span></span>

6. <span data-ttu-id="5732a-124">移植您的測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="5732a-124">Port your test code.</span></span>

   <span data-ttu-id="5732a-125">由於移植到 .NET Core 是您程式碼基底的重大變更，因此強烈建議您移植測試專案，讓您可以在將程式碼移植到時執行測試。</span><span class="sxs-lookup"><span data-stu-id="5732a-125">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to port your test projects so that you can run tests as you port your code over.</span></span> <span data-ttu-id="5732a-126">MSTest、xUnit 和 NUnit 全都適用于 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="5732a-126">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

<span data-ttu-id="5732a-127">此外，您可以使用 dotnet 的 [[嘗試轉換](https://github.com/dotnet/try-convert)] 工具，嘗試將一項作業中較小的方案或個別專案移植到 .net Core 專案檔案格式。</span><span class="sxs-lookup"><span data-stu-id="5732a-127">Additionally, you can attempt to port smaller solutions or individual projects in one operation to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool.</span></span> <span data-ttu-id="5732a-128">`dotnet try-convert` 不保證適用于您所有的專案，而且可能會對您所依賴的行為造成細微的變更。</span><span class="sxs-lookup"><span data-stu-id="5732a-128">`dotnet try-convert` is not guaranteed to work for all your projects, and it may cause subtle changes in behavior that you depended on.</span></span> <span data-ttu-id="5732a-129">使用它做為自動化可自動化之基本事項的_起點_。</span><span class="sxs-lookup"><span data-stu-id="5732a-129">Use it as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="5732a-130">它不是可移轉專案的保證解決方案。</span><span class="sxs-lookup"><span data-stu-id="5732a-130">It isn't a guaranteed solution to migrating a project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5732a-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5732a-131">Next steps</span></span>

>[!div class="nextstepaction"]
>[<span data-ttu-id="5732a-132">.NET Core 上的無法使用技術</span><span class="sxs-lookup"><span data-stu-id="5732a-132">Unavailable technologies on .NET Core</span></span>](net-framework-tech-unavailable.md)
