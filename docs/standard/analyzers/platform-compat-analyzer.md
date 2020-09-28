---
title: 平臺相容性分析器
description: Roslyn 分析器，可協助偵測跨平臺應用程式和程式庫中的平臺相容性問題。
author: buyaa-n
ms.date: 09/17/2020
ms.openlocfilehash: 4e842e5bbe90dd5006d9b27d0365f908b6441997
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406598"
---
# <a name="platform-compatibility-analyzer"></a><span data-ttu-id="81b3d-103">平臺相容性分析器</span><span class="sxs-lookup"><span data-stu-id="81b3d-103">Platform compatibility analyzer</span></span>

<span data-ttu-id="81b3d-104">您可能聽過「單一 .NET」的格言：單一、統一的平臺，可用於建立任何類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="81b3d-104">You've probably heard the motto of "One .NET": a single, unified platform for building any type of application.</span></span> <span data-ttu-id="81b3d-105">.NET 5.0 SDK 包含 ASP.NET Core、Entity Framework Core、WinForms、WPF、Xamarin 和 ML.NET，並且會隨著時間增加更多平臺的支援。</span><span class="sxs-lookup"><span data-stu-id="81b3d-105">The .NET 5.0 SDK includes ASP.NET Core, Entity Framework Core, WinForms, WPF, Xamarin, and ML.NET, and will add support for more platforms over time.</span></span> <span data-ttu-id="81b3d-106">.NET 5.0 致力於提供一種體驗，讓您不必擔心不同的 .NET 種類，但也不會嘗試完全抽象化基礎作業系統)  (作業系統。</span><span class="sxs-lookup"><span data-stu-id="81b3d-106">.NET 5.0 strives to provide an experience where you don't have to reason about the different flavors of .NET, but doesn't attempt to fully abstract away the underlying operating system (OS).</span></span> <span data-ttu-id="81b3d-107">您將繼續能夠呼叫平臺專屬的 Api，例如 P/Invoke、WinRT 或適用于 iOS 和 Android 的 Xamarin 系結。</span><span class="sxs-lookup"><span data-stu-id="81b3d-107">You'll continue to be able to call platform-specific APIs, for example, P/Invokes, WinRT, or the Xamarin bindings for iOS and Android.</span></span>

<span data-ttu-id="81b3d-108">但是，在元件上使用平臺特定的 Api，表示程式碼無法在所有平臺上運作。</span><span class="sxs-lookup"><span data-stu-id="81b3d-108">But using platform-specific APIs on a component means the code no longer works across all platforms.</span></span> <span data-ttu-id="81b3d-109">我們需要在設計階段偵測到此情況的方法，讓開發人員在不小心使用平臺特定 Api 時取得診斷。</span><span class="sxs-lookup"><span data-stu-id="81b3d-109">We needed a way to detect this at design time so developers get diagnostics when they inadvertently use platform-specific APIs.</span></span> <span data-ttu-id="81b3d-110">為了達成此目標，.NET 5.0 引進了 [平臺相容性分析器](/visualstudio/code-quality/ca1416) 和互補的 api，協助開發人員在適當的情況下識別及使用平臺特定的 api。</span><span class="sxs-lookup"><span data-stu-id="81b3d-110">To achieve this goal, .NET 5.0 introduces the [platform compatibility analyzer](/visualstudio/code-quality/ca1416) and complementary APIs to help developers identify and use platform-specific APIs where appropriate.</span></span>
<span data-ttu-id="81b3d-111">新的 Api 包括：</span><span class="sxs-lookup"><span data-stu-id="81b3d-111">The new APIs include:</span></span>

- <span data-ttu-id="81b3d-112"><xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 將 Api 標注為平臺特定的批註，並 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 將 api 標注為在特定 OS 上不受支援。</span><span class="sxs-lookup"><span data-stu-id="81b3d-112"><xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> to annotate APIs as being platform-specific and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> to annotate APIs as being unsupported on a particular OS.</span></span> <span data-ttu-id="81b3d-113">這些屬性可以選擇性地包含版本號碼，並已套用至核心 .NET 程式庫中的某些平臺特定 Api。</span><span class="sxs-lookup"><span data-stu-id="81b3d-113">These attributes can optionally include the version number, and have already been applied to some platform-specific APIs in the core .NET libraries.</span></span>
- <span data-ttu-id="81b3d-114">`Is<Platform>()` 以及 `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` 類別中的靜態方法，可 <xref:System.OperatingSystem?displayProperty=nameWithType> 安全地呼叫平臺特定的 api。</span><span class="sxs-lookup"><span data-stu-id="81b3d-114">`Is<Platform>()` and `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` static methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class for safely calling platform-specific APIs.</span></span> <span data-ttu-id="81b3d-115">例如， <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> 可以用來保護對 windows 特定 api 的呼叫，而 <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> ( # A1 可以用來保護已建立版本的 WINDOWS 特定 api 呼叫。</span><span class="sxs-lookup"><span data-stu-id="81b3d-115">For example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> can be used to guard a call to a Windows-specific API, and <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>() can be used to guard a versioned Windows-specific API call.</span></span> <span data-ttu-id="81b3d-116">請參閱這些方法的 [範例](#guard-platform-specific-apis-with-guard-methods) ，以瞭解如何使用這些方法來作為平臺特定 API 參考的防護。</span><span class="sxs-lookup"><span data-stu-id="81b3d-116">See these [examples](#guard-platform-specific-apis-with-guard-methods) of how these methods can be used as guards of platform-specific API references.</span></span>

> [!TIP]
> <span data-ttu-id="81b3d-117">平臺相容性分析器會升級並取代[.NET API 分析器](../../standard/analyzers/api-analyzer.md)的[探索跨平臺問題](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues)功能。</span><span class="sxs-lookup"><span data-stu-id="81b3d-117">The platform compatibility analyzer upgrades and replaces the [Discovering cross-platform issues](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues) feature of the [.NET API analyzer](../../standard/analyzers/api-analyzer.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="81b3d-118">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="81b3d-118">Prerequisites</span></span>

<span data-ttu-id="81b3d-119">平臺相容性分析器是 Roslyn 的程式碼品質分析器之一。</span><span class="sxs-lookup"><span data-stu-id="81b3d-119">The platform compatibility analyzer is one of the Roslyn code quality analyzers.</span></span> <span data-ttu-id="81b3d-120">從 .NET 5.0 開始，這些分析器會 [隨附于 .NET SDK](../../fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="81b3d-120">Starting in .NET 5.0, these analyzers are [included with the .NET SDK](../../fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="81b3d-121">根據預設，平臺相容性分析器僅針對以或更新版本為目標的專案啟用 `net5.0` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-121">The platform compatibility analyzer is enabled by default only for projects that target `net5.0` or a later version.</span></span> <span data-ttu-id="81b3d-122">不過，您可以針對以其他架構為目標的專案 [啟用](/visualstudio/code-quality/ca1416.md#configurability) 它。</span><span class="sxs-lookup"><span data-stu-id="81b3d-122">However, you can [enable](/visualstudio/code-quality/ca1416.md#configurability) it for projects that target other frameworks.</span></span>

## <a name="how-the-analyzer-determines-platform-dependency"></a><span data-ttu-id="81b3d-123">分析器如何判斷平臺相關性</span><span class="sxs-lookup"><span data-stu-id="81b3d-123">How the analyzer determines platform dependency</span></span>

- <span data-ttu-id="81b3d-124">**未歸屬 API**會視為在**所有 OS 平臺**上運作。</span><span class="sxs-lookup"><span data-stu-id="81b3d-124">An **unattributed API** is considered to work on **all OS platforms**.</span></span>
- <span data-ttu-id="81b3d-125">標記為的 API `[SupportedOSPlatform("platform")]` 只會被視為可移植到指定的作業系統 `platform` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-125">An API marked with `[SupportedOSPlatform("platform")]` is considered only portable to the specified OS `platform`.</span></span>
  - <span data-ttu-id="81b3d-126">您可以多次套用屬性，以指出 () 的 **多平臺支援** `[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-126">The attribute can be applied multiple times to indicate **multiple platform support** (`[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]`).</span></span>
  - <span data-ttu-id="81b3d-127">如果未使用適當的**平臺內容**參考平臺特定 api，分析器會產生**警告**：</span><span class="sxs-lookup"><span data-stu-id="81b3d-127">The analyzer will produce a **warning** if platform-specific APIs are referenced without a proper **platform context**:</span></span>
    - <span data-ttu-id="81b3d-128">如果專案未以支援的平臺為目標，則會**發出警告** (例如，Windows 特定的 API 呼叫和專案的目標 `<TargetFramework>net5.0-ios14.0</TargetFramework>`) 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-128">**Warns** if the project doesn't target the supported platform (for example, a Windows-specific API call and the project targets `<TargetFramework>net5.0-ios14.0</TargetFramework>`).</span></span>
    - <span data-ttu-id="81b3d-129">如果專案是多目標 () ，則會**發出警告** `<TargetFramework>net5.0</TargetFramework>` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-129">**Warns** if the project is multi-targeted (`<TargetFramework>net5.0</TargetFramework>`).</span></span>
    - <span data-ttu-id="81b3d-130">如果在以任何**指定平臺**為目標的專案中參考平臺特定的 api，則**不會發出警告** (例如，針對 Windows 特定的 api 呼叫和專案的目標 `<TargetFramework>net5.0-windows</TargetFramework>`) 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-130">**Doesn't warn** if the platform-specific API is referenced within a project that targets any of the **specified platforms** (for example, for a Windows-specific API call and the project targets `<TargetFramework>net5.0-windows</TargetFramework>`).</span></span>
    - <span data-ttu-id="81b3d-131">如果平臺特定 API 呼叫受到對應平臺檢查方法的防護，則**不會發出警告** (例如 `if(OperatingSystem.IsWindows())`) 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-131">**Doesn't warn** if the platform-specific API call is guarded by corresponding platform-check methods (for example, `if(OperatingSystem.IsWindows())`).</span></span>
    - <span data-ttu-id="81b3d-132">如果從相同平臺特定的內容參考平臺特定的 API， (**呼叫網站也**以) 進行屬性化，則**不會發出警告** `[SupportedOSPlatform("platform")` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-132">**Doesn't warn** if the platform-specific API is referenced from the same platform-specific context (**call site also attributed** with `[SupportedOSPlatform("platform")`).</span></span>
- <span data-ttu-id="81b3d-133">標記為的 API `[UnsupportedOSPlatform("platform")]` 只會在指定的 OS 上被視為不受支援， `platform` 但所有其他平臺皆支援此 API。</span><span class="sxs-lookup"><span data-stu-id="81b3d-133">An API marked with `[UnsupportedOSPlatform("platform")]` is considered unsupported only on the specified OS `platform` but supported for all other platforms.</span></span>
  - <span data-ttu-id="81b3d-134">您可以使用不同的平臺多次套用屬性，例如 `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-134">The attribute can be applied multiple times with different platforms, for example, `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]`.</span></span>
  - <span data-ttu-id="81b3d-135">只有當對**warning** `platform` 呼叫位置有效時，分析器才會產生警告：</span><span class="sxs-lookup"><span data-stu-id="81b3d-135">The analyzer produces a **warning** only if the `platform` is effective for the call site:</span></span>
    - <span data-ttu-id="81b3d-136">如果專案的目標平臺是以不 (支援的屬性為目標的平臺，例如，如果 API 是以屬性化，而且呼叫位置的目標是) ，則會**發出警告** `[UnsupportedOSPlatform("windows")]` `<TargetFramework>net5.0-windows</TargetFramework>` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-136">**Warns** if the project targets the platform that's attributed as unsupported (for example, if the API is attributed with `[UnsupportedOSPlatform("windows")]` and the call site targets `<TargetFramework>net5.0-windows</TargetFramework>`).</span></span>
    - <span data-ttu-id="81b3d-137">**Warns**如果專案是多目標且 `platform` 包含在預設[MSBuild `<SupportedPlatform>` ](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props)專案群組中，或 `platform` 手動包含在 `MSBuild` items 群組內，則會發出警告 \<SupportedPlatform> ：</span><span class="sxs-lookup"><span data-stu-id="81b3d-137">**Warns** if the project is multi-targeted and the `platform` is included in the default [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) items group, or the `platform` is manually included within the `MSBuild` \<SupportedPlatform> items group:</span></span>

      ```XML
      <ItemGroup>
          <SupportedPlatform Include="platform" />
      </ItemGroup>
      ```

    - <span data-ttu-id="81b3d-138">如果您要建立的應用程式不是以不受支援的平臺為目標，或為多目標，且該平臺未包含在預設的 [ [MSBuild `<SupportedPlatform>` ](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props)專案] 群組中，則**不會發出警告**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-138">**Doesn't warn** if you're building an app that doesn't target the unsupported platform or is multi-targeted and the platform is not included in the default [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) items group.</span></span>
- <span data-ttu-id="81b3d-139">這兩個屬性都可以使用或不含版本號碼作為平臺名稱的一部分來具現化。</span><span class="sxs-lookup"><span data-stu-id="81b3d-139">Both attributes can be instantiated with or without version numbers as part of the platform name.</span></span>
  - <span data-ttu-id="81b3d-140">版本號碼的格式 `major.minor[.build[.revision]]` 為; `major.minor` 是必要的， `build` 而且和 `revision` 部分是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="81b3d-140">Version numbers are in the format of `major.minor[.build[.revision]]`; `major.minor` is required and the `build` and `revision` parts are optional.</span></span> <span data-ttu-id="81b3d-141">例如，「Windows 7.0」表示 Windows 7.0 版，但「Windows」則會被視為 Windows 0.0。</span><span class="sxs-lookup"><span data-stu-id="81b3d-141">For example, "Windows7.0" indicates Windows version 7.0, but "Windows" is interpreted as Windows 0.0.</span></span>

<span data-ttu-id="81b3d-142">如需詳細資訊，請參閱 [屬性如何運作的範例，以及它們所造成的診斷](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce)。</span><span class="sxs-lookup"><span data-stu-id="81b3d-142">For more information, see [examples of how the attributes work and what diagnostics they cause](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce).</span></span>

### <a name="advanced-scenarios-for-combining-attributes"></a><span data-ttu-id="81b3d-143">合併屬性的 Advanced 案例</span><span class="sxs-lookup"><span data-stu-id="81b3d-143">Advanced scenarios for combining attributes</span></span>

- <span data-ttu-id="81b3d-144">如果有 `[SupportedOSPlatform]` 和屬性的組合 `[UnsupportedOSPlatform]` ，則所有屬性都會依作業系統平臺識別碼分組：</span><span class="sxs-lookup"><span data-stu-id="81b3d-144">If a combination of `[SupportedOSPlatform]` and `[UnsupportedOSPlatform]` attributes are present, all attributes are grouped by OS platform identifier:</span></span>
  - <span data-ttu-id="81b3d-145">**僅支援的清單**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-145">**Supported only list**.</span></span> <span data-ttu-id="81b3d-146">如果每個作業系統平臺的最低版本是 `[SupportedOSPlatform]` 屬性，則會將 API 視為僅受列出的平臺支援，而且所有其他平臺都不支援此 API。</span><span class="sxs-lookup"><span data-stu-id="81b3d-146">If the lowest version for each OS platform is a `[SupportedOSPlatform]` attribute, the API is considered to only be supported by the listed platforms and unsupported by all other platforms.</span></span> <span data-ttu-id="81b3d-147">`[UnsupportedOSPlatform]`每個平臺的選擇性屬性只能有較高版本的最低支援版本，表示從指定的版本開始移除 API。</span><span class="sxs-lookup"><span data-stu-id="81b3d-147">The optional `[UnsupportedOSPlatform]` attributes for each platform can only have higher version of the minimum supported version, which denotes that the API is removed starting from the specified version.</span></span>

    ```csharp
    // The API only supported on Windows 8.0 and later, not supported for all other.
    // The API is removed/unsupported from version 10.0.19041.0.
    [SupportedOSPlatform("windows8.0")]
    [UnsupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows80SupportFromCertainVersion();
    ```

  - <span data-ttu-id="81b3d-148">**唯一不支援的清單**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-148">**Unsupported only list**.</span></span> <span data-ttu-id="81b3d-149">如果每個作業系統平臺的最低版本是 `[UnsupportedOSPlatform]` 屬性，則會將 API 視為只有列出的平臺不支援，而且所有其他平臺都支援此 API。</span><span class="sxs-lookup"><span data-stu-id="81b3d-149">If the lowest version for each OS platform is an `[UnsupportedOSPlatform]` attribute, then the API is considered to only be unsupported by the listed platforms and supported by all other platforms.</span></span> <span data-ttu-id="81b3d-150">此清單可能具有 `[SupportedOSPlatform]` 相同平臺但版本較高的屬性，代表從該版本開始支援 API。</span><span class="sxs-lookup"><span data-stu-id="81b3d-150">The list could have `[SupportedOSPlatform]` attribute with the same platform but a higher version, which denotes that the API is supported starting from that version.</span></span>
  
    ```csharp
    // The API was unsupported on Windows until version 10.0.19041.0.
    // The API is considered supported everywhere else without constraints.
    [UnsupportedOSPlatform("windows")]
    [SupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows8UnsupportFromWindows10();
    ```

  - <span data-ttu-id="81b3d-151">**不一致的清單**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-151">**Inconsistent list**.</span></span> <span data-ttu-id="81b3d-152">如果某些平臺的最低版本是 `[SupportedOSPlatform]` 在 `[UnsupportedOSPlatform]` 其他平臺上，則會被視為不一致，分析器不支援此版本。</span><span class="sxs-lookup"><span data-stu-id="81b3d-152">If the lowest version for some platforms is `[SupportedOSPlatform]` while it is `[UnsupportedOSPlatform]` for other platforms, is considered inconsistent, which is not supported for the analyzer.</span></span>
  - <span data-ttu-id="81b3d-153">如果和屬性的最小版本 `[SupportedOSPlatform]` `[UnsupportedOSPlatform]` 相等，分析器會將平臺視為 **支援的唯一清單**的一部分。</span><span class="sxs-lookup"><span data-stu-id="81b3d-153">If the lowest versions of `[SupportedOSPlatform]` and `[UnsupportedOSPlatform]` attributes are equal, the analyzer considers the platform as part of the **Supported only list**.</span></span>
- <span data-ttu-id="81b3d-154">平臺屬性可以套用至類型、成員 (方法、欄位、屬性和事件) 以及具有不同平臺名稱和/或版本的元件。</span><span class="sxs-lookup"><span data-stu-id="81b3d-154">Platform attributes can be applied to types, members (methods, fields, properties, and events) and assemblies with different platform name and / or version.</span></span>
  - <span data-ttu-id="81b3d-155">在最上層套用的屬性 `target` 會影響其所有成員和類型。</span><span class="sxs-lookup"><span data-stu-id="81b3d-155">Attributes applied at the top level `target` affect all of its members and types.</span></span>
  - <span data-ttu-id="81b3d-156">只有當子系層級屬性符合規則「子批註可以縮小平臺支援，但無法將其加寬」時，才適用。</span><span class="sxs-lookup"><span data-stu-id="81b3d-156">Child level attributes only apply if they adhere to the rule "child annotations can narrow the platforms support, but they cannot widen it".</span></span>
    - <span data-ttu-id="81b3d-157">當父系 **僅支援** 清單時，子成員屬性無法加入新的平臺支援，因為它會擴充父系支援，而新的平臺支援只能新增至父系本身。</span><span class="sxs-lookup"><span data-stu-id="81b3d-157">When parent has **Supported only** list, then child member attributes could not add a new platform support as that would be extending parent support, a new platform support can only added to the parent itself.</span></span> <span data-ttu-id="81b3d-158">但是，它可以有 `Supported` 與較新版本相同平臺的屬性，因為這樣會縮小支援範圍。</span><span class="sxs-lookup"><span data-stu-id="81b3d-158">But it can have `Supported` attribute for same platform with later versions as that will narrow the support.</span></span> <span data-ttu-id="81b3d-159">此外，它也可以具有 `Unsupported` 與相同平臺相同的屬性，這樣也會減少父系支援。</span><span class="sxs-lookup"><span data-stu-id="81b3d-159">Also it can have `Unsupported` attribute with same platform as that will also narrow parent support.</span></span>
    - <span data-ttu-id="81b3d-160">當父系有 **不支援** 的清單時，子成員屬性可能會加入新的平臺支援，因為這樣會縮小父項支援，但它不能具有與 `Supported` 父系中相同平臺的屬性，因此會擴充父系支援。</span><span class="sxs-lookup"><span data-stu-id="81b3d-160">When parent has **Unsupported only** list, then child member attributes could add a new platform support as that would be narrowing parent support, but it cannot have `Supported` attribute for same platform as in the parent, that would extend parent support.</span></span> <span data-ttu-id="81b3d-161">相同平臺的支援只能加入至套用原始屬性的父層級 `Unsupported` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-161">Support for the same platform can be added only to parent level where the original `Unsupported` attribute applied.</span></span>
  - <span data-ttu-id="81b3d-162">如果 `[SupportedOSPlatform("platformVersion")]` 針對具有相同名稱的 API 套用了一次以上， `platform` 分析器會考慮最低版本的 API。</span><span class="sxs-lookup"><span data-stu-id="81b3d-162">If `[SupportedOSPlatform("platformVersion")]` is applied more than once for an API with the same `platform` name only the one with minimum version is considered by the analyzer.</span></span>
  - <span data-ttu-id="81b3d-163">如果 `[UnsupportedOSPlatform("platformVersion")]` 為相同名稱的 API 套用了兩次以上 `platform` ，分析器就只會考慮使用最舊版本的兩個。</span><span class="sxs-lookup"><span data-stu-id="81b3d-163">If `[UnsupportedOSPlatform("platformVersion")]` is applied more than twice for an API with the same `platform` name, only the two with earliest versions are considered by the analyzer.</span></span>
  
  > [!NOTE]
  > <span data-ttu-id="81b3d-164">在較新版本中，一開始就支援但不支援 (移除) 的 API，不應該在較新版本中取得 resupported。</span><span class="sxs-lookup"><span data-stu-id="81b3d-164">An API that was supported initially but unsupported (removed) in a later version is not expected to get resupported in an even later version.</span></span>

### <a name="examples-of-how-the-attributes-work-and-what-diagnostics-they-produce"></a><span data-ttu-id="81b3d-165">屬性的運作方式，以及它們所產生之診斷的範例</span><span class="sxs-lookup"><span data-stu-id="81b3d-165">Examples of how the attributes work and what diagnostics they produce</span></span>

  ```csharp
  // An API supported only on Windows.
  [SupportedOSPlatform("Windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  public void Caller()
  {
      WindowsOnlyApi(); // warns: 'WindowsOnlyApi' is supported on 'windows'

      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Windows'
      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Linux'
      SupportedOnWindowsAndLinuxOnly();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 8.0 and later  
      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // for same platform analyzer only warn for the latest version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on android but supported on all other.
  [UnsupportedOSPlatform("android")]  
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  public void Caller2()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'android'

      // warns:'StartedWindowsSupportFromVersion8' is unsupported on 'windows'  
      // warns:'StartedWindowsSupportFromVersion8' is supported on 'windows' 8.0 and later
      StartedWindowsSupportFromVersion8();

      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is unsupported on 'windows'  
      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is supported on 'windows' 8.0 and later
      // even there were 3 diagnostics found analyzer warn only for the first 2.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

## <a name="handle-reported-warnings"></a><span data-ttu-id="81b3d-166">處理回報的警告</span><span class="sxs-lookup"><span data-stu-id="81b3d-166">Handle reported warnings</span></span>

<span data-ttu-id="81b3d-167">處理這些診斷的建議方式是確保您只在適當的平臺上執行時，才呼叫平臺專屬的 Api。</span><span class="sxs-lookup"><span data-stu-id="81b3d-167">The recommended way to deal with these diagnostics is to make sure you only call platform-specific APIs when running on an appropriate platform.</span></span> <span data-ttu-id="81b3d-168">以下是您可以用來解決警告的選項;選擇最適合您情況的哪一種：</span><span class="sxs-lookup"><span data-stu-id="81b3d-168">Following are the options you can use to address the warnings; choose whichever is most appropriate for your situation:</span></span>

- <span data-ttu-id="81b3d-169">**防護通話**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-169">**Guard the call**.</span></span> <span data-ttu-id="81b3d-170">您可以在執行時間依條件呼叫程式碼來達成此目的。</span><span class="sxs-lookup"><span data-stu-id="81b3d-170">You can achieve this by conditionally calling the code at run time.</span></span> <span data-ttu-id="81b3d-171">`Platform`使用其中一個平臺檢查方法（例如或），檢查您是否正在執行 `OperatingSystem.Is<Platform>()` `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-171">Check whether you’re running on a desired `Platform` by using one of platform-check methods, for example, `OperatingSystem.Is<Platform>()` or `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)`.</span></span>

- <span data-ttu-id="81b3d-172">**將呼叫位置標示為平臺特定**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-172">**Mark the call site as platform-specific**.</span></span> <span data-ttu-id="81b3d-173">您也可以選擇將自己的 Api 標記為平臺專屬的 Api，如此一來，就能有效地將需求轉送至您的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="81b3d-173">You can also choose to mark your own APIs as being platform-specific, thus effectively just forwarding the requirements to your callers.</span></span> <span data-ttu-id="81b3d-174">使用與參考的平臺相依呼叫相同的屬性，標記包含方法或類型或整個元件。</span><span class="sxs-lookup"><span data-stu-id="81b3d-174">Mark the containing method or type or the entire assembly with the same attributes as the referenced platform-dependent call.</span></span> <span data-ttu-id="81b3d-175">[範例](#mark-call-site-as-platform-specific)。</span><span class="sxs-lookup"><span data-stu-id="81b3d-175">[Examples](#mark-call-site-as-platform-specific).</span></span>

- <span data-ttu-id="81b3d-176">**使用平臺檢查判斷提示呼叫位置**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-176">**Assert the call site with platform check**.</span></span> <span data-ttu-id="81b3d-177">如果您不想要在執行時間額外負荷額外的 `if` 語句，請使用 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-177">If you don't want the overhead of an additional `if` statement at run time, use <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81b3d-178">[範例](#assert-the-call-site-with-platform-check)。</span><span class="sxs-lookup"><span data-stu-id="81b3d-178">[Example](#assert-the-call-site-with-platform-check).</span></span>

- <span data-ttu-id="81b3d-179">**刪除程式碼**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-179">**Delete the code**.</span></span> <span data-ttu-id="81b3d-180">通常不是您想要的，因為這表示當 Windows 使用者使用您的程式碼時，會喪失精確度。</span><span class="sxs-lookup"><span data-stu-id="81b3d-180">Generally not what you want because it means you lose fidelity when your code is used by Windows users.</span></span> <span data-ttu-id="81b3d-181">如果存在跨平臺的替代方案，您可能會比使用平臺專用的 Api 更好。</span><span class="sxs-lookup"><span data-stu-id="81b3d-181">For cases where a cross-platform alternative exists, you’re likely better off using that over platform-specific APIs.</span></span>

- <span data-ttu-id="81b3d-182">**隱藏警告**。</span><span class="sxs-lookup"><span data-stu-id="81b3d-182">**Suppress the warning**.</span></span> <span data-ttu-id="81b3d-183">您也可以直接透過 editor.config 或隱藏警告 `#pragma warning disable ca1416` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-183">You can also simply suppress the warning, either via editor.config or `#pragma warning disable ca1416`.</span></span> <span data-ttu-id="81b3d-184">不過，此選項應該是使用平臺特定 Api 時的最後手段。</span><span class="sxs-lookup"><span data-stu-id="81b3d-184">However, this option should be a last resort when using platform-specific APIs.</span></span>

### <a name="guard-platform-specific-apis-with-guard-methods"></a><span data-ttu-id="81b3d-185">使用 guard 方法保護平臺特定的 Api</span><span class="sxs-lookup"><span data-stu-id="81b3d-185">Guard platform-specific APIs with guard methods</span></span>

<span data-ttu-id="81b3d-186">Guard 方法的平臺名稱應該與呼叫平臺相依的 API 平臺名稱相符。</span><span class="sxs-lookup"><span data-stu-id="81b3d-186">The guard method's platform name should match with the calling platform-dependent API platform name.</span></span> <span data-ttu-id="81b3d-187">如果呼叫 API 的平臺字串包含版本：</span><span class="sxs-lookup"><span data-stu-id="81b3d-187">If the platform string of the calling API includes the version:</span></span>

- <span data-ttu-id="81b3d-188">若為 `[SupportedOSPlatform("platformVersion")]` 屬性，guard 方法平臺 `version` 應大於或等於呼叫平臺的 `Version` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-188">For the `[SupportedOSPlatform("platformVersion")]` attribute, the guard method platform `version` should be greater than or equal to the calling platform's `Version`.</span></span>
- <span data-ttu-id="81b3d-189">若為 `[UnsupportedOSPlatform("platformVersion")]` 屬性，guard 方法的平臺 `version` 應小於或等於呼叫平臺的 `Version` 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-189">For the `[UnsupportedOSPlatform("platformVersion")]` attribute, the guard method's platform `version` should be less than or equal to the calling platform's `Version`.</span></span>

  ```csharp
  public void CallingSupportedOnlyApis() // Allow list calls
  {
      if (OperatingSystem.IsWindows())
      {
          WindowsOnlyApi(); // will not warn
      }

      if (OperatingSystem.IsLinux())
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn, within one of the supported context
      }

      // Can use &&, || logical operators to guard combined attributes
      if (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10.0.19041)))
      {
          ApiSupportedFromWindows8UnsupportFromWindows10();
      }

      if (OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903))
      {
          AssemblySupportedOnWindowsApiSupportedFromWindows10(); // Only need to check latest supported version
      }
  }

  public void CallingUnsupportedApis()
  {
      if (!OperatingSystem.IsAndroid())
      {
          DoesNotWorkOnAndroid(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || OperatingSystem.IsWindowsVersionAtLeast(8))
      {
          StartedWindowsSupportFromVersion8(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || // supported all other platforms
         (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903)))
      {
          StartedWindowsSupportFrom8UnsupportedFrom10(); // will not warn
      }
  }
  ```

- <span data-ttu-id="81b3d-190">如果您需要保護以 netstandard 或 netcoreapp 為目標的程式碼， <xref:System.OperatingSystem> 但無法使用新的 api <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> ，則可以使用 api 並將由分析器遵循。</span><span class="sxs-lookup"><span data-stu-id="81b3d-190">if you need to guard a code that targets netstandard or netcoreapp where new <xref:System.OperatingSystem> APIs are not available <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API can be used and will be respected by the analyzer.</span></span> <span data-ttu-id="81b3d-191">但是，它並不像新增的 Api 一樣優化 <xref:System.OperatingSystem> 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-191">But it's not as optimized as the new APIs added in <xref:System.OperatingSystem>.</span></span> <span data-ttu-id="81b3d-192">如果結構中不支援該平臺 <xref:System.Runtime.InteropServices.OSPlatform> ，您可以流量分析器也會遵循的 <xref:System.Runtime.InteropServices.OSPlatform.Create%2A?displayProperty=nameWithType> ( 「平臺」 ) 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-192">In case the platform is not supported in <xref:System.Runtime.InteropServices.OSPlatform> struct, you can use <xref:System.Runtime.InteropServices.OSPlatform.Create%2A?displayProperty=nameWithType>("platform") which is also respected by the analyzer.</span></span>

  ```csharp
  public void CallingSupportedOnlyApis()
  {
      if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn
      }

      if (RuntimeInformation.IsOSPlatform(OSPlatform.Create("browser")))
      {
          ApiOnlySupportedOnBrowser(); // call of browser specific API
      }
  }
  ```

### <a name="mark-call-site-as-platform-specific"></a><span data-ttu-id="81b3d-193">將呼叫網站標示為平臺特定</span><span class="sxs-lookup"><span data-stu-id="81b3d-193">Mark call site as platform-specific</span></span>

<span data-ttu-id="81b3d-194">平臺名稱應符合呼叫平臺相依的 API。</span><span class="sxs-lookup"><span data-stu-id="81b3d-194">Platform names should match the calling platform-dependent API.</span></span> <span data-ttu-id="81b3d-195">如果平臺字串包含版本：</span><span class="sxs-lookup"><span data-stu-id="81b3d-195">If the platform string includes a version:</span></span>

- <span data-ttu-id="81b3d-196">若為 `[SupportedOSPlatform("platformVersion")]` 屬性，呼叫位置平臺 `version` 應大於或等於呼叫平臺的 `Version`</span><span class="sxs-lookup"><span data-stu-id="81b3d-196">For the `[SupportedOSPlatform("platformVersion")]` attribute, the call site platform `version` should be greater than or equal to the calling platform's `Version`</span></span>
- <span data-ttu-id="81b3d-197">針對 `[UnsupportedOSPlatform("platformVersion")]` 屬性，呼叫網站平臺 `version` 應小於或等於呼叫平臺的 `Version`</span><span class="sxs-lookup"><span data-stu-id="81b3d-197">For the `[UnsupportedOSPlatform("platformVersion")]` attribute, the call site platform `version` should be less than or equal to the calling platform's `Version`</span></span>

  ```csharp
  // an API supported only on Windows.
  [SupportedOSPlatform("windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  [SupportedOSPlatform("windows8.0")] // call site attributed Windows 8.0 or above.
  public void Caller()
  {
      WindowsOnlyApi(); // will not warn as call site is for Windows.

      // will not warn as call site is for Windows.
      SupportedOnWindowsAndLinuxOnly();

      // will not warn for the API's [SupportedOSPlatform("windows8.0")] attribute.
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // as the call site version is lower than calling version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows11.0")] // call site attributed with windows 11.0 or above.
  public void Caller2()
  {
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // will not warn as call site version higher than calling API.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")] // call site supports Windows from version 8.0 to 10.0.19041.0.
  public void Caller3()
  {
      // will not warn as caller has exact same attributes.
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // As call site stopped support from that version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on Android but supported on all other.
  [UnsupportedOSPlatform("android")]  
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  [UnsupportedOSPlatform("windows")] // Caller no support Windows for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'Android'.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }

  [UnsupportedOSPlatform("windows")]
  [UnsupportedOSPlatform("android")] // Caller not support Windows and Android for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // will not warn as call site not supports Android.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

### <a name="assert-the-call-site-with-platform-check"></a><span data-ttu-id="81b3d-198">使用平臺檢查判斷提示呼叫網站</span><span class="sxs-lookup"><span data-stu-id="81b3d-198">Assert the call-site with platform check</span></span>

<span data-ttu-id="81b3d-199">[平臺防護範例](#guard-platform-specific-apis-with-guard-methods)中使用的所有條件式檢查，也可以當做的條件使用 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="81b3d-199">All the conditional checks used in the [platform guard examples](#guard-platform-specific-apis-with-guard-methods) can also be used as the condition for <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>.</span></span>

  ```csharp
  // An API supported only on Linux.
  [SupportedOSPlatform("linux")]
  public void LinuxOnlyApi() { }

  public void Caller()
  {
      Debug.Assert(OperatingSystem.IsLinux());

      LinuxOnlyApi(); // will not warn
  }
  ```

## <a name="see-also"></a><span data-ttu-id="81b3d-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81b3d-200">See also</span></span>

- [<span data-ttu-id="81b3d-201">.NET 5 中的目標 Framework 名稱</span><span class="sxs-lookup"><span data-stu-id="81b3d-201">Target Framework Names in .NET 5</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [<span data-ttu-id="81b3d-202">標注平臺特定 Api 並偵測其使用</span><span class="sxs-lookup"><span data-stu-id="81b3d-202">Annotating platform-specific APIs and detecting its use</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-checks/platform-checks.md)
- [<span data-ttu-id="81b3d-203">針對特定平臺上不支援的 Api 進行批註</span><span class="sxs-lookup"><span data-stu-id="81b3d-203">Annotating APIs as unsupported on specific platforms</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-exclusion/platform-exclusion.md)
- [<span data-ttu-id="81b3d-204">CA1416 平臺相容性分析器</span><span class="sxs-lookup"><span data-stu-id="81b3d-204">CA1416 Platform compatibility analyzer</span></span>](/visualstudio/code-quality/ca1416)
- [<span data-ttu-id="81b3d-205">.NET API 分析器</span><span class="sxs-lookup"><span data-stu-id="81b3d-205">.NET API analyzer</span></span>](../../standard/analyzers/api-analyzer.md)
