---
title: .NET 程式庫的跨平台目標設定
description: 建立跨平台 .NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6bd310f2e4b7a9bd7bb550ed9c7da9ebabdf64ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129710"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="90704-103">跨平台目標設定</span><span class="sxs-lookup"><span data-stu-id="90704-103">Cross-platform targeting</span></span>

<span data-ttu-id="90704-104">新式 .NET 支援多種作業系統與裝置。</span><span class="sxs-lookup"><span data-stu-id="90704-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="90704-105">.NET 開放原始碼程式庫要儘可能支援許多開發人員，無論是建置裝載於 Azure 的 ASP.NET 網站，還是 Unity 中的 .NET 遊戲，這一點非常重要。</span><span class="sxs-lookup"><span data-stu-id="90704-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="90704-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="90704-106">.NET Standard</span></span>

<span data-ttu-id="90704-107">.NET Standard 是為 .NET 程式庫新增跨平台支援的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="90704-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="90704-108">[.NET Standard](../net-standard.md) 是在所有 .NET 實作都可以使用的 .NET API 規格。</span><span class="sxs-lookup"><span data-stu-id="90704-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="90704-109">將目標設為 .NET Standard，您可以產生限制為使用給定 .NET Standard 版本中之 API 的程式庫，這表示它可以被實作該 .NET 版本的所有平台使用。</span><span class="sxs-lookup"><span data-stu-id="90704-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="90704-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="90704-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="90704-111">將目標設為 .NET Standard 並成功地編譯您的專案，並不保證程式庫將可在所有平台上順利執行：</span><span class="sxs-lookup"><span data-stu-id="90704-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="90704-112">平台特定 API 將會在其他平台上失敗。</span><span class="sxs-lookup"><span data-stu-id="90704-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="90704-113">例如，<xref:Microsoft.Win32.Registry?displayProperty=nameWithType> 會在 Windows 上成功，並在任何其他 OS 上使用時擲回 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="90704-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="90704-114">API 的行為會不一樣。</span><span class="sxs-lookup"><span data-stu-id="90704-114">APIs can behave differently.</span></span> <span data-ttu-id="90704-115">例如，當應用程式在 iOS 或 UWP 上使用預先編譯時，反映 API 具有不同的效能特性。</span><span class="sxs-lookup"><span data-stu-id="90704-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="90704-116">.NET 小組[提供了一個 Roslyn 分析器](../analyzers/api-analyzer.md)，可協助您找出可能的問題。</span><span class="sxs-lookup"><span data-stu-id="90704-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="90704-117">**✔️ 請務必**開始包括 `netstandard2.0` 目標。</span><span class="sxs-lookup"><span data-stu-id="90704-117">**✔️ DO** start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="90704-118">大部分的一般用途程式庫應該不需要 .NET Standard 2.0 以外的 API。</span><span class="sxs-lookup"><span data-stu-id="90704-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="90704-119">所有新式平台都支援 .NET Standard 2.0，而且是以一個目標支援多個平台的建議方法。</span><span class="sxs-lookup"><span data-stu-id="90704-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="90704-120">**❌ 避免**包含 `netstandard1.x` 目標。</span><span class="sxs-lookup"><span data-stu-id="90704-120">**❌ AVOID** including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="90704-121">.NET standard 1.x 是以一組精細的 NuGet 套件形式發佈，它建立了一個大型的套件相依性圖形，並導致開發人員在建置時下載了大量的套件。</span><span class="sxs-lookup"><span data-stu-id="90704-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="90704-122">新式 .NET 平台，包括 .NET Framework 4.6.1、UWP 與 Xamarin，全都支援 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="90704-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="90704-123">如果您特別需要以較舊的平台為目標，則應僅將目標設為 .NET Standard 1.x。</span><span class="sxs-lookup"><span data-stu-id="90704-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="90704-124">**✔️ 請務必**包含 `netstandard2.0` 目標 (如果您需要 `netstandard1.x` 目標)。</span><span class="sxs-lookup"><span data-stu-id="90704-124">**✔️ DO** include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="90704-125">所有支援 .NET Standard 2.0 的平台都將使用 `netstandard2.0` 目標，並從較小的套件圖形中受益，而較舊的平台仍會運作，並改為使用 `netstandard1.x` 目標。</span><span class="sxs-lookup"><span data-stu-id="90704-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="90704-126">**❌ 請勿**包含 .NET Standard 目標 (如果程式庫依賴平台特定應用程式模型)。</span><span class="sxs-lookup"><span data-stu-id="90704-126">**❌ DO NOT** include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="90704-127">例如，UWP 控制項工具組程式庫相依於只有 UWP 上可用的應用程式模型。</span><span class="sxs-lookup"><span data-stu-id="90704-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="90704-128">.NET Standard 中將不提供應用程式模型特定 API。</span><span class="sxs-lookup"><span data-stu-id="90704-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="90704-129">多目標</span><span class="sxs-lookup"><span data-stu-id="90704-129">Multi-targeting</span></span>

<span data-ttu-id="90704-130">有時您需要從您的程式庫中存取架構特定 API。</span><span class="sxs-lookup"><span data-stu-id="90704-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="90704-131">呼叫架構特定 API 的最佳方法是使用多目標，它為許多 [.NET 目標 Framework](../frameworks.md) 建置專案，而不是僅為一個。</span><span class="sxs-lookup"><span data-stu-id="90704-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="90704-132">為了保護您的取用者不必為個別架構建置，您應該努力獲得 .NET Standard 輸出，加上一或多個架構特定輸出。</span><span class="sxs-lookup"><span data-stu-id="90704-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="90704-133">使用多目標時，所有組件都會封裝在單一 NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="90704-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="90704-134">接著，取用者可以參考相同的套件，NuGet 將挑選適當的實作。</span><span class="sxs-lookup"><span data-stu-id="90704-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="90704-135">您的 .NET Standard 程式庫會作為在任何地方使用的後援程式庫，但您的 NuGet 套件提供架構特定實作的案例除外。</span><span class="sxs-lookup"><span data-stu-id="90704-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="90704-136">多目標可讓您在程式碼中使用條件式編譯，並呼叫架構特定 API。</span><span class="sxs-lookup"><span data-stu-id="90704-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="90704-137">![包含多個組件的 NuGet 套件](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "包含多個組件的 NuGet 套件")</span><span class="sxs-lookup"><span data-stu-id="90704-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="90704-138">**✔️ 考慮**將 .NET 實作設為目標 (除了 .NET Standard 之外)。</span><span class="sxs-lookup"><span data-stu-id="90704-138">**✔️ CONSIDER** targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="90704-139">將 .NET 實作設為目標可讓您呼叫 .NET Standard 之外的平台特定 API。</span><span class="sxs-lookup"><span data-stu-id="90704-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="90704-140">執行此動作時，請不要捨棄 .NET Standard 的支援。</span><span class="sxs-lookup"><span data-stu-id="90704-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="90704-141">相反地，從實作擲回並提供功能API。</span><span class="sxs-lookup"><span data-stu-id="90704-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="90704-142">這樣，您的程式庫便能任何地方使用，並支援執行階段啟動功能。</span><span class="sxs-lookup"><span data-stu-id="90704-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

<span data-ttu-id="90704-143">**❌ 避免**使用多目標以及 .NET Standard 目標設定 (如果您的原始程式碼也適用於所有目標)。</span><span class="sxs-lookup"><span data-stu-id="90704-143">**❌ AVOID** multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="90704-144">NuGet 將自動使用 .NET Standard 組件。</span><span class="sxs-lookup"><span data-stu-id="90704-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="90704-145">將單一 .NET 實作設為目標會增加 `*.nupkg` 大小，沒有任何好處。</span><span class="sxs-lookup"><span data-stu-id="90704-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="90704-146">**✔️ 考慮**針對 `net461` 新增目標 (當您提供 `netstandard2.0` 目標時)。</span><span class="sxs-lookup"><span data-stu-id="90704-146">**✔️ CONSIDER** adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span> 

> <span data-ttu-id="90704-147">使用 .NET Framework 中的 .NET Standard 2.0，會有一些在 .NET Framework 4.7.2 中已經解決的問題。</span><span class="sxs-lookup"><span data-stu-id="90704-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="90704-148">您可以透過為仍在 .NET Framework 4.6.1 - 4.7.1 上的開發人員提供針對 .NET Framework 4.6.1 建置的二進位檔，以改善其體驗。</span><span class="sxs-lookup"><span data-stu-id="90704-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="90704-149">**✔️ 優先**使用 NuGet 套件散發您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="90704-149">**✔️ DO** distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="90704-150">NuGet 將為開發人員選取最佳目標，並讓他們不需要挑選適當的實作。</span><span class="sxs-lookup"><span data-stu-id="90704-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="90704-151">**✔️ 請務必**使用專案檔的 `TargetFrameworks` 屬性 (當使用多目標時)。</span><span class="sxs-lookup"><span data-stu-id="90704-151">**✔️ DO** use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="90704-152">**✔️ 考慮**使用 [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) (當針對 UWP 與 Xamarin 進行多目標時) 因為它可以大幅簡化您的專案檔。</span><span class="sxs-lookup"><span data-stu-id="90704-152">**✔️ CONSIDER** using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="90704-153">較舊的目標</span><span class="sxs-lookup"><span data-stu-id="90704-153">Older targets</span></span>

<span data-ttu-id="90704-154">.NET 支援長期不支援的 .NET Framework 的目標版本，以及不再常用的平台。</span><span class="sxs-lookup"><span data-stu-id="90704-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="90704-155">雖然使您的程式庫在儘可能多的目標上運作是有價值的，但是必須針對 API 遺漏問題找出因應措施會增加重大額外負荷。</span><span class="sxs-lookup"><span data-stu-id="90704-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="90704-156">考慮到其範圍與限制，我們認為特定架構已不再值得設為目標。</span><span class="sxs-lookup"><span data-stu-id="90704-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="90704-157">**❌ 請勿**包含可攜式類別庫 (PCL) 目標。</span><span class="sxs-lookup"><span data-stu-id="90704-157">**❌ DO NOT** include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="90704-158">例如，`portable-net45+win8+wpa81+wp8`。</span><span class="sxs-lookup"><span data-stu-id="90704-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="90704-159">.NET Standard 是支援跨平台 .NET 程式庫並取代 PCL 的新式方法。</span><span class="sxs-lookup"><span data-stu-id="90704-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="90704-160">**❌ 請勿**包含不再支援之 .NET 平台的目標。</span><span class="sxs-lookup"><span data-stu-id="90704-160">**❌ DO NOT** include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="90704-161">例如，`SL4`、`WP`。</span><span class="sxs-lookup"><span data-stu-id="90704-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="90704-162">[上一頁](get-started.md)
>[下一頁](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="90704-162">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
