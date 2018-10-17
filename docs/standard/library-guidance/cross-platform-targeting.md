---
title: 跨平台為目標
description: 建立跨平台.NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 72fa891d5b1054af485a98d89b4efb11d6b0018b
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374884"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="b2e4c-103">跨平台為目標</span><span class="sxs-lookup"><span data-stu-id="b2e4c-103">Cross-platform targeting</span></span>

<span data-ttu-id="b2e4c-104">新式的.NET 支援多個作業系統和裝置。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="b2e4c-105">務必.NET 開放原始碼程式庫，才支援多個開發人員盡可能的情況下，不論它們要建置的 ASP.NET 網站裝載於 Azure 或在 Unity 中的進行.NET 遊戲。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="b2e4c-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="b2e4c-106">.NET Standard</span></span>

<span data-ttu-id="b2e4c-107">.NET standard 是跨平台支援加入.NET 程式庫的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="b2e4c-108">[.NET standard](../net-standard.md)是可在所有.NET 實作的.NET Api 的規格。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="b2e4c-109">目標.NET Standard，可讓您產生限制為使用中指定版本的.NET Standard，這表示它是使用會實作.NET Standard 版本的所有平台 Api 的程式庫。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="b2e4c-110">![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="b2e4c-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="b2e4c-111">目標.NET Standard，並成功地編譯您的專案，並不保證程式庫會在所有平台上順利執行：</span><span class="sxs-lookup"><span data-stu-id="b2e4c-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="b2e4c-112">其他平台上，將會失敗的平台專屬的 Api。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="b2e4c-113">例如，<xref:Microsoft.Win32.Registry?displayProperty=nameWithType>會在 Windows 上成功，則擲回<xref:System.PlatformNotSupportedException>使用任何其他作業系統上時。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="b2e4c-114">Api 的行為。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-114">APIs can behave differently.</span></span> <span data-ttu-id="b2e4c-115">例如，反映 Api 時，有不同的效能特性應用程式在 iOS 或 UWP 上使用預先 just-in-time 編譯。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="b2e4c-116">.NET 小組[提供一個 Roslyn 分析器](../analyzers/api-analyzer.md)可協助您找出可能的問題。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="b2e4c-117">**請勿 ✔️**開頭包括`netstandard2.0`目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-117">**✔️ DO** start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="b2e4c-118">一般用途的文件庫應該不需要外部.NET Standard 2.0 的 Api。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="b2e4c-119">.NET standard 2.0 支援所有新型平台，而且是建議用來支援多個目標平台。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="b2e4c-120">**請避免 ❌**包括`netstandard1.x`目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-120">**❌ AVOID** including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="b2e4c-121">.NET standard 1.x 分散會建立大型的套件相依性圖形，並導致下載的封裝時建置的開發人員的 NuGet 套件的細微設定。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="b2e4c-122">新式的.NET 平台，包括.NET Framework 4.6.1、 UWP 和 Xamarin，所有支援.NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="b2e4c-123">您只應該以目標為.NET Standard 1.x，如果您特別需要較舊的平台為目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="b2e4c-124">**請勿 ✔️**包括`netstandard2.0`如果您需要為目標`netstandard1.x`目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-124">**✔️ DO** include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="b2e4c-125">將所有的平台支援.NET Standard 2.0`netstandard2.0`為目標，並受益於具有較小的套件圖形，而較舊的平台仍會運作，並改為使用`netstandard1.x`目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="b2e4c-126">**不這麼做 ❌**包含.NET Standard 的目標，如果程式庫依賴平台專屬的應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-126">**❌ DO NOT** include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="b2e4c-127">例如，UWP 控制項工具組程式庫才可以使用 UWP 應用程式模型而定。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="b2e4c-128">應用程式模型特定的 Api 不是在.NET Standard 中，您可以使用的狀態。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="b2e4c-129">多目標</span><span class="sxs-lookup"><span data-stu-id="b2e4c-129">Multi-targeting</span></span>

<span data-ttu-id="b2e4c-130">有時候您需要存取特定架構的 Api，從您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="b2e4c-131">呼叫架構特定 Api 的最佳方式使用多目標，建置您的專案提供了許多[目標的.NET frameworks](../frameworks.md)而不是其中一個。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="b2e4c-132">若要防護您的取用者不必建立個別的架構，您應該盡量有.NET Standard 的輸出，再加上一個或多個架構特定輸出。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="b2e4c-133">使用多目標會將所有組件封裝內單一 NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="b2e4c-134">取用者可以參考相同的套件，NuGet 會挑選適當的實作。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="b2e4c-135">後援文件庫會使用所有位置，其中您的 NuGet 套件提供的架構特定實作的案例除外，就會作為您的.NET Standard 程式庫。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="b2e4c-136">多目標可讓您在程式碼中使用條件式編譯，並呼叫特定架構的 Api。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="b2e4c-137">![具有多個組件的 NuGet 封裝](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "具有多個組件的 NuGet 封裝")</span><span class="sxs-lookup"><span data-stu-id="b2e4c-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="b2e4c-138">**請考慮 ✔️**目標除了.NET Standard 的.NET 實作。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-138">**✔️ CONSIDER** targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="b2e4c-139">目標為.NET 實作，可讓您呼叫外部.NET Standard 平台專屬 Api。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="b2e4c-140">當您執行此動作不捨棄.NET Standard 的支援。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="b2e4c-141">相反地，從實作擲回，並提供功能的 Api。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="b2e4c-142">如此一來，您的程式庫可用於任何地方，並支援執行階段啟動的功能。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

<span data-ttu-id="b2e4c-143">**請避免 ❌**使用多目標的.NET Standard 與您的程式碼是否適用於所有目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-143">**❌ AVOID** using multi-targeting with .NET Standard if your source code is the same for all targets.</span></span>

> <span data-ttu-id="b2e4c-144">NuGet 會自動使用.NET Standard 的組件。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="b2e4c-145">目標為個別的.NET 實作會增加`*.nupkg`大小沒有任何好處。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="b2e4c-146">**請考慮 ✔️**新增的目標`net461`當您提供`netstandard2.0`目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-146">**✔️ CONSIDER** adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span> 

> <span data-ttu-id="b2e4c-147">使用.NET Standard 2.0，從.NET Framework 有一些.NET Framework 4.7.2 中已解決的問題。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="b2e4c-148">您可以改善仍在使用.NET Framework 4.6.1-藉由提供他們建置適用於.NET Framework 4.6.1 的二進位檔 4.7.1 的開發人員的體驗。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="b2e4c-149">**請勿 ✔️**散發您的程式庫使用 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-149">**✔️ DO** distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="b2e4c-150">NuGet 會選取最佳的目標，開發人員，並避免它們需要挑選適當的實作。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="b2e4c-151">**請勿 ✔️**使用專案檔的`TargetFrameworks`多目標時的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-151">**✔️ DO** use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b2e4c-152">**請考慮 ✔️**使用[MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras)時多目標的 UWP 和 Xamarin，它可大幅簡化您的專案檔。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-152">**✔️ CONSIDER** using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="b2e4c-153">較舊的目標</span><span class="sxs-lookup"><span data-stu-id="b2e4c-153">Older targets</span></span>

<span data-ttu-id="b2e4c-154">.NET 支援的.NET framework 是長時間不支援，以及不再常用的平台的目標版本。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="b2e4c-155">雖然沒有在進行您的程式庫工作上需要解決遺失的 Api 越好，許多的目標可以新增重大額外負荷的值。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="b2e4c-156">我們相信特定架構已不再值得目標，考量其觸達和限制。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="b2e4c-157">**不這麼做 ❌**包含可攜式類別庫 (PCL) 目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-157">**❌ DO NOT** include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="b2e4c-158">例如，`portable-net45+win8+wpa81+wp8`。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="b2e4c-159">.NET standard 是現代化的方式，以支援跨平台.NET 程式庫，並取代 Pcl。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="b2e4c-160">**不這麼做 ❌**包含不受支援的.NET 平台的目標。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-160">**❌ DO NOT** include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="b2e4c-161">例如，`SL4`、`WP`。</span><span class="sxs-lookup"><span data-stu-id="b2e4c-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b2e4c-162">[上一頁](./get-started.md)
[下一頁](./strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="b2e4c-162">[Previous](./get-started.md)
[Next](./strong-naming.md)</span></span>
