---
title: 目標 Framework
description: 了解 .NET Core 應用程式和程式庫的目標 Framework。
author: richlander
ms.author: mairaw
ms.date: 04/02/2019
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: a7005cfe01d168febd97af5f8b41cfff26b2cfc7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641460"
---
# <a name="target-frameworks"></a><span data-ttu-id="2225a-103">目標 Framework</span><span class="sxs-lookup"><span data-stu-id="2225a-103">Target frameworks</span></span>

<span data-ttu-id="2225a-104">當您以應用程式或程式庫中的架構為目標時，您將指定要提供給應用程式或程式庫的一組 API。</span><span class="sxs-lookup"><span data-stu-id="2225a-104">When you target a framework in an app or library, you're specifying the set of APIs that you'd like to make available to the app or library.</span></span> <span data-ttu-id="2225a-105">您可以在專案檔中使用目標 Framework Moniker (TFM) 來指定目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="2225a-105">You specify the target framework in your project file using Target Framework Monikers (TFMs).</span></span>

<span data-ttu-id="2225a-106">應用程式或程式庫可以將目標設為某個版本的 [.NET Standard](~/docs/standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="2225a-106">An app or library can target a version of [.NET Standard](~/docs/standard/net-standard.md).</span></span> <span data-ttu-id="2225a-107">.NET Standard 版本代表跨所有 .NET 實作的標準化 API 集合。</span><span class="sxs-lookup"><span data-stu-id="2225a-107">.NET Standard versions represent standardized sets of APIs across all .NET implementations.</span></span> <span data-ttu-id="2225a-108">例如，程式庫可以將目標設為 .NET Standard 1.6，以存取跨 .NET Core 和 .NET Framework (兩者使用相同的程式碼基底) 運作的 API。</span><span class="sxs-lookup"><span data-stu-id="2225a-108">For example, a library can target .NET Standard 1.6 and gain access to APIs that function across .NET Core and .NET Framework using the same codebase.</span></span>

<span data-ttu-id="2225a-109">應用程式或程式庫也可以將目標設為特定 .NET 實作，以存取實作特定的 API。</span><span class="sxs-lookup"><span data-stu-id="2225a-109">An app or library can also target a specific .NET implementation to gain access to implementation-specific APIs.</span></span> <span data-ttu-id="2225a-110">例如，以 Xamarin.iOS (例如 `Xamarin.iOS10`) 為目標的應用程式可以存取 iOS 10 之 Xamarin 提供的 iOS API 包裝函式；或者，以通用 Windows 平台 (UWP，`uap10.0`) 為目標的應用程式可以存取針對執行 Windows 10 的裝置所編譯的 API。</span><span class="sxs-lookup"><span data-stu-id="2225a-110">For example, an app that targets Xamarin.iOS (for example, `Xamarin.iOS10`) gets access to Xamarin-provided iOS API wrappers for iOS 10, or an app that targets the Universal Windows Platform (UWP, `uap10.0`) has access to APIs that compile for devices that run Windows 10.</span></span>

<span data-ttu-id="2225a-111">針對某些目標 Framework (例如 .NET Framework)，API 是由該架構安裝在系統上的組件所定義，而且可能包含應用程式架構 API (例如 ASP.NET)。</span><span class="sxs-lookup"><span data-stu-id="2225a-111">For some target frameworks (for example, the .NET Framework), the APIs are defined by the assemblies that the framework installs on a system and may include application framework APIs (for example, ASP.NET).</span></span>

<span data-ttu-id="2225a-112">針對以套件為基礎的目標 Framework (例如 .NET Standard 和 .NET Core)，API 是由包含在應用程式或程式庫中的套件所定義。</span><span class="sxs-lookup"><span data-stu-id="2225a-112">For package-based target frameworks (for example, .NET Standard and .NET Core), the APIs are defined by the packages included in the app or library.</span></span> <span data-ttu-id="2225a-113">「中繼套件」是 NuGet 套件，本身沒有任何內容，而是一份相依性 (其他專案) 清單。</span><span class="sxs-lookup"><span data-stu-id="2225a-113">A *metapackage* is a NuGet package that has no content of its own but is a list of dependencies (other packages).</span></span> <span data-ttu-id="2225a-114">以 NuGet 套件為基礎的目標 Framework 會隱含指定一個中繼套件，該套件會參考組成架構的所有套件。</span><span class="sxs-lookup"><span data-stu-id="2225a-114">A NuGet package-based target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

## <a name="latest-target-framework-versions"></a><span data-ttu-id="2225a-115">最新目標 Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2225a-115">Latest target framework versions</span></span>

<span data-ttu-id="2225a-116">下表定義最常用的目標 Framework、其參考方式，以及它們所實作的 [.NET Standard](~/docs/standard/net-standard.md) 版本。</span><span class="sxs-lookup"><span data-stu-id="2225a-116">The following table defines the most common target frameworks, how they're referenced, and which version of the [.NET Standard](~/docs/standard/net-standard.md) they implement.</span></span> <span data-ttu-id="2225a-117">這些目標 Framework 版本是最新穩定版本。</span><span class="sxs-lookup"><span data-stu-id="2225a-117">These target framework versions are the latest stable versions.</span></span> <span data-ttu-id="2225a-118">不顯示發行前版本。</span><span class="sxs-lookup"><span data-stu-id="2225a-118">Pre-release versions aren't shown.</span></span> <span data-ttu-id="2225a-119">目標 Framework Moniker (TFM) 是用於指定 .NET 應用程式或程式庫之目標 Framework 的標準化語彙基元格式。</span><span class="sxs-lookup"><span data-stu-id="2225a-119">A Target Framework Moniker (TFM) is a standardized token format for specifying the target framework of a .NET app or library.</span></span>

| <span data-ttu-id="2225a-120">目標 Framework</span><span class="sxs-lookup"><span data-stu-id="2225a-120">Target Framework</span></span>      | <span data-ttu-id="2225a-121">Latest</span><span class="sxs-lookup"><span data-stu-id="2225a-121">Latest</span></span> <br/> <span data-ttu-id="2225a-122">穩定版本</span><span class="sxs-lookup"><span data-stu-id="2225a-122">Stable Version</span></span> | <span data-ttu-id="2225a-123">Target Framework Moniker (TFM)</span><span class="sxs-lookup"><span data-stu-id="2225a-123">Target Framework Moniker (TFM)</span></span> | <span data-ttu-id="2225a-124">已實作</span><span class="sxs-lookup"><span data-stu-id="2225a-124">Implemented</span></span> <br/> <span data-ttu-id="2225a-125">.NET Standard 版本</span><span class="sxs-lookup"><span data-stu-id="2225a-125">.NET Standard Version</span></span> |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| <span data-ttu-id="2225a-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2225a-126">.NET Standard</span></span>         | <span data-ttu-id="2225a-127">2.0</span><span class="sxs-lookup"><span data-stu-id="2225a-127">2.0</span></span>                         | <span data-ttu-id="2225a-128">netstandard2.0</span><span class="sxs-lookup"><span data-stu-id="2225a-128">netstandard2.0</span></span>                 | <span data-ttu-id="2225a-129">N/A</span><span class="sxs-lookup"><span data-stu-id="2225a-129">N/A</span></span>                                     |
| <span data-ttu-id="2225a-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2225a-130">.NET Core</span></span>             | <span data-ttu-id="2225a-131">2.2</span><span class="sxs-lookup"><span data-stu-id="2225a-131">2.2</span></span>                         | <span data-ttu-id="2225a-132">netcoreapp2.2</span><span class="sxs-lookup"><span data-stu-id="2225a-132">netcoreapp2.2</span></span>                  | <span data-ttu-id="2225a-133">2.0</span><span class="sxs-lookup"><span data-stu-id="2225a-133">2.0</span></span>                                     |
| <span data-ttu-id="2225a-134">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2225a-134">.NET Framework</span></span>        | <span data-ttu-id="2225a-135">4.8</span><span class="sxs-lookup"><span data-stu-id="2225a-135">4.8</span></span>                         | <span data-ttu-id="2225a-136">net48</span><span class="sxs-lookup"><span data-stu-id="2225a-136">net48</span></span>                          | <span data-ttu-id="2225a-137">2.0</span><span class="sxs-lookup"><span data-stu-id="2225a-137">2.0</span></span>                                     |

## <a name="supported-target-framework-versions"></a><span data-ttu-id="2225a-138">支援的目標 Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2225a-138">Supported target framework versions</span></span>

<span data-ttu-id="2225a-139">目標 Framework 通常會由 TFM 參考。</span><span class="sxs-lookup"><span data-stu-id="2225a-139">A target framework is typically referenced by a TFM.</span></span> <span data-ttu-id="2225a-140">下表顯示 .NET Core SDK 和 NuGet 用戶端所支援的目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="2225a-140">The following table shows the target frameworks supported by the .NET Core SDK and the NuGet client.</span></span> <span data-ttu-id="2225a-141">對等項目會顯示在括弧內。</span><span class="sxs-lookup"><span data-stu-id="2225a-141">Equivalents are shown within brackets.</span></span> <span data-ttu-id="2225a-142">例如，`win81` 是 `netcore451` 的對等 TFM。</span><span class="sxs-lookup"><span data-stu-id="2225a-142">For example, `win81` is an equivalent TFM to `netcore451`.</span></span>

| <span data-ttu-id="2225a-143">目標 Framework</span><span class="sxs-lookup"><span data-stu-id="2225a-143">Target Framework</span></span>           | <span data-ttu-id="2225a-144">TFM</span><span class="sxs-lookup"><span data-stu-id="2225a-144">TFM</span></span> |
| -------------------------- | --- |
| <span data-ttu-id="2225a-145">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2225a-145">.NET Standard</span></span>              | <span data-ttu-id="2225a-146">netstandard1.0</span><span class="sxs-lookup"><span data-stu-id="2225a-146">netstandard1.0</span></span><br><span data-ttu-id="2225a-147">netstandard1.1</span><span class="sxs-lookup"><span data-stu-id="2225a-147">netstandard1.1</span></span><br><span data-ttu-id="2225a-148">netstandard1.2</span><span class="sxs-lookup"><span data-stu-id="2225a-148">netstandard1.2</span></span><br><span data-ttu-id="2225a-149">netstandard1.3</span><span class="sxs-lookup"><span data-stu-id="2225a-149">netstandard1.3</span></span><br><span data-ttu-id="2225a-150">netstandard1.4</span><span class="sxs-lookup"><span data-stu-id="2225a-150">netstandard1.4</span></span><br><span data-ttu-id="2225a-151">netstandard1.5</span><span class="sxs-lookup"><span data-stu-id="2225a-151">netstandard1.5</span></span><br><span data-ttu-id="2225a-152">netstandard1.6</span><span class="sxs-lookup"><span data-stu-id="2225a-152">netstandard1.6</span></span><br><span data-ttu-id="2225a-153">netstandard2.0</span><span class="sxs-lookup"><span data-stu-id="2225a-153">netstandard2.0</span></span> |
| <span data-ttu-id="2225a-154">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2225a-154">.NET Core</span></span>                  | <span data-ttu-id="2225a-155">netcoreapp1.0</span><span class="sxs-lookup"><span data-stu-id="2225a-155">netcoreapp1.0</span></span><br><span data-ttu-id="2225a-156">netcoreapp1.1</span><span class="sxs-lookup"><span data-stu-id="2225a-156">netcoreapp1.1</span></span><br><span data-ttu-id="2225a-157">netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="2225a-157">netcoreapp2.0</span></span><br><span data-ttu-id="2225a-158">netcoreapp2.1</span><span class="sxs-lookup"><span data-stu-id="2225a-158">netcoreapp2.1</span></span><br><span data-ttu-id="2225a-159">netcoreapp2.2</span><span class="sxs-lookup"><span data-stu-id="2225a-159">netcoreapp2.2</span></span> |
| <span data-ttu-id="2225a-160">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2225a-160">.NET Framework</span></span>             | <span data-ttu-id="2225a-161">net11</span><span class="sxs-lookup"><span data-stu-id="2225a-161">net11</span></span><br><span data-ttu-id="2225a-162">net20</span><span class="sxs-lookup"><span data-stu-id="2225a-162">net20</span></span><br><span data-ttu-id="2225a-163">net35</span><span class="sxs-lookup"><span data-stu-id="2225a-163">net35</span></span><br><span data-ttu-id="2225a-164">net40</span><span class="sxs-lookup"><span data-stu-id="2225a-164">net40</span></span><br><span data-ttu-id="2225a-165">net403</span><span class="sxs-lookup"><span data-stu-id="2225a-165">net403</span></span><br><span data-ttu-id="2225a-166">net45</span><span class="sxs-lookup"><span data-stu-id="2225a-166">net45</span></span><br><span data-ttu-id="2225a-167">net451</span><span class="sxs-lookup"><span data-stu-id="2225a-167">net451</span></span><br><span data-ttu-id="2225a-168">net452</span><span class="sxs-lookup"><span data-stu-id="2225a-168">net452</span></span><br><span data-ttu-id="2225a-169">net46</span><span class="sxs-lookup"><span data-stu-id="2225a-169">net46</span></span><br><span data-ttu-id="2225a-170">net461</span><span class="sxs-lookup"><span data-stu-id="2225a-170">net461</span></span><br><span data-ttu-id="2225a-171">net462</span><span class="sxs-lookup"><span data-stu-id="2225a-171">net462</span></span><br><span data-ttu-id="2225a-172">net47</span><span class="sxs-lookup"><span data-stu-id="2225a-172">net47</span></span><br><span data-ttu-id="2225a-173">net471</span><span class="sxs-lookup"><span data-stu-id="2225a-173">net471</span></span><br><span data-ttu-id="2225a-174">net472</span><span class="sxs-lookup"><span data-stu-id="2225a-174">net472</span></span><br><span data-ttu-id="2225a-175">net48</span><span class="sxs-lookup"><span data-stu-id="2225a-175">net48</span></span> |
| <span data-ttu-id="2225a-176">Windows 市集</span><span class="sxs-lookup"><span data-stu-id="2225a-176">Windows Store</span></span>              | <span data-ttu-id="2225a-177">netcore [netcore45]</span><span class="sxs-lookup"><span data-stu-id="2225a-177">netcore [netcore45]</span></span><br><span data-ttu-id="2225a-178">netcore45 [win] [win8]</span><span class="sxs-lookup"><span data-stu-id="2225a-178">netcore45 [win] [win8]</span></span><br><span data-ttu-id="2225a-179">netcore451 [win81]</span><span class="sxs-lookup"><span data-stu-id="2225a-179">netcore451 [win81]</span></span> |
| <span data-ttu-id="2225a-180">.NET Micro Framework</span><span class="sxs-lookup"><span data-stu-id="2225a-180">.NET Micro Framework</span></span>       | <span data-ttu-id="2225a-181">netmf</span><span class="sxs-lookup"><span data-stu-id="2225a-181">netmf</span></span> |
| <span data-ttu-id="2225a-182">Silverlight</span><span class="sxs-lookup"><span data-stu-id="2225a-182">Silverlight</span></span>                | <span data-ttu-id="2225a-183">sl4</span><span class="sxs-lookup"><span data-stu-id="2225a-183">sl4</span></span><br><span data-ttu-id="2225a-184">sl5</span><span class="sxs-lookup"><span data-stu-id="2225a-184">sl5</span></span> |
| <span data-ttu-id="2225a-185">Windows Phone</span><span class="sxs-lookup"><span data-stu-id="2225a-185">Windows Phone</span></span>              | <span data-ttu-id="2225a-186">wp [wp7]</span><span class="sxs-lookup"><span data-stu-id="2225a-186">wp [wp7]</span></span><br><span data-ttu-id="2225a-187">wp7</span><span class="sxs-lookup"><span data-stu-id="2225a-187">wp7</span></span><br><span data-ttu-id="2225a-188">wp75</span><span class="sxs-lookup"><span data-stu-id="2225a-188">wp75</span></span><br><span data-ttu-id="2225a-189">wp8</span><span class="sxs-lookup"><span data-stu-id="2225a-189">wp8</span></span><br><span data-ttu-id="2225a-190">wp81</span><span class="sxs-lookup"><span data-stu-id="2225a-190">wp81</span></span><br><span data-ttu-id="2225a-191">wpa81</span><span class="sxs-lookup"><span data-stu-id="2225a-191">wpa81</span></span> |
| <span data-ttu-id="2225a-192">通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="2225a-192">Universal Windows Platform</span></span> | <span data-ttu-id="2225a-193">uap [uap10.0]</span><span class="sxs-lookup"><span data-stu-id="2225a-193">uap [uap10.0]</span></span><br><span data-ttu-id="2225a-194">uap10.0 [win10] [netcore50]</span><span class="sxs-lookup"><span data-stu-id="2225a-194">uap10.0 [win10] [netcore50]</span></span> |

## <a name="how-to-specify-target-frameworks"></a><span data-ttu-id="2225a-195">如何指定目標 Framework</span><span class="sxs-lookup"><span data-stu-id="2225a-195">How to specify target frameworks</span></span>

<span data-ttu-id="2225a-196">目標 Framework 會在專案檔中指定。</span><span class="sxs-lookup"><span data-stu-id="2225a-196">Target frameworks are specified in your project file.</span></span> <span data-ttu-id="2225a-197">指定單一目標 Framework 時，請使用 **TargetFramework** 項目。</span><span class="sxs-lookup"><span data-stu-id="2225a-197">When a single target framework is specified, use the **TargetFramework** element.</span></span> <span data-ttu-id="2225a-198">下列主控台應用程式專案檔會示範如何將目標設為 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="2225a-198">The following console app project file demonstrates how to target .NET Core 2.2:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="2225a-199">當您指定多個目標 Framework 時，您可以有條件地參考每個目標 Framework 的組件。</span><span class="sxs-lookup"><span data-stu-id="2225a-199">When you specify multiple target frameworks, you may conditionally reference assemblies for each target framework.</span></span> <span data-ttu-id="2225a-200">在您的程式碼中，您可以使用前置處理器符號搭配 *if-then-else* 邏輯，有條件地對這些組件進行編譯。</span><span class="sxs-lookup"><span data-stu-id="2225a-200">In your code, you can conditionally compile against those assemblies by using preprocessor symbols with *if-then-else* logic.</span></span>

<span data-ttu-id="2225a-201">下列程式庫專案檔是以 .NET Standard 的 API (`netstandard1.4`) 以及 .NET Framework 的 API (`net40` 和 `net45`) 為目標。</span><span class="sxs-lookup"><span data-stu-id="2225a-201">The following library project file targets APIs of .NET Standard (`netstandard1.4`) and APIs of the .NET Framework (`net40` and `net45`).</span></span> <span data-ttu-id="2225a-202">使用具有多個目標 Framework 的複數 **TargetFrameworks** 項目。</span><span class="sxs-lookup"><span data-stu-id="2225a-202">Use the plural **TargetFrameworks** element with multiple target frameworks.</span></span> <span data-ttu-id="2225a-203">當針對兩個 .NET Framework TFM 編譯程式庫時，注意 `Condition` 屬性如何包含實作特定的套件：</span><span class="sxs-lookup"><span data-stu-id="2225a-203">Note how the `Condition` attributes include implementation-specific packages when the library is compiled for the two .NET Framework TFMs:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.0 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net40' ">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.5 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net45' ">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="2225a-204">您可以在程式庫或應用程式中撰寫條件程式碼，為每個目標 Framework 進行編譯：</span><span class="sxs-lookup"><span data-stu-id="2225a-204">Within your library or app, you write conditional code to compile for each target framework:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

<span data-ttu-id="2225a-205">組建系統知道代表目標 Framework 的前置處理器符號，如[支援的目標 Framework 版本](#supported-target-framework-versions)表格中所示。</span><span class="sxs-lookup"><span data-stu-id="2225a-205">The build system is aware of preprocessor symbols representing the target frameworks shown in the [Supported target framework versions](#supported-target-framework-versions) table.</span></span> <span data-ttu-id="2225a-206">使用代表 .NET Standard 或 .NET Core TFM 的符號時，請以底線取代點，並將小寫字母變更為大寫 (例如 `netstandard1.4` 的符號是 `NETSTANDARD1_4`)。</span><span class="sxs-lookup"><span data-stu-id="2225a-206">When using a symbol that represents a .NET Standard or .NET Core TFM, replace the dot with an underscore and change lowercase letters to uppercase (for example, the symbol for `netstandard1.4` is `NETSTANDARD1_4`).</span></span>

<span data-ttu-id="2225a-207">.NET Core 目標 Framework 之前置處理器符號的完整清單如下：</span><span class="sxs-lookup"><span data-stu-id="2225a-207">The complete list of preprocessor symbols for .NET Core target frameworks is:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a><span data-ttu-id="2225a-208">已被取代的目標 Framework</span><span class="sxs-lookup"><span data-stu-id="2225a-208">Deprecated target frameworks</span></span>

<span data-ttu-id="2225a-209">下列目標 Framework 已被取代。</span><span class="sxs-lookup"><span data-stu-id="2225a-209">The following target frameworks are deprecated.</span></span> <span data-ttu-id="2225a-210">以這些目標 Framework 為目標的套件應該移轉至所指出的取代項目。</span><span class="sxs-lookup"><span data-stu-id="2225a-210">Packages targeting these target frameworks should migrate to the indicated replacements.</span></span>

| <span data-ttu-id="2225a-211">已被取代的 TFM</span><span class="sxs-lookup"><span data-stu-id="2225a-211">Deprecated TFM</span></span>                                                                             | <span data-ttu-id="2225a-212">Replacement</span><span class="sxs-lookup"><span data-stu-id="2225a-212">Replacement</span></span> |
| ------------------------------------------------------------------------------------------ | ----------- |
| <span data-ttu-id="2225a-213">aspnet50</span><span class="sxs-lookup"><span data-stu-id="2225a-213">aspnet50</span></span><br><span data-ttu-id="2225a-214">aspnetcore50</span><span class="sxs-lookup"><span data-stu-id="2225a-214">aspnetcore50</span></span><br><span data-ttu-id="2225a-215">dnxcore50</span><span class="sxs-lookup"><span data-stu-id="2225a-215">dnxcore50</span></span><br><span data-ttu-id="2225a-216">dnx</span><span class="sxs-lookup"><span data-stu-id="2225a-216">dnx</span></span><br><span data-ttu-id="2225a-217">dnx45</span><span class="sxs-lookup"><span data-stu-id="2225a-217">dnx45</span></span><br><span data-ttu-id="2225a-218">dnx451</span><span class="sxs-lookup"><span data-stu-id="2225a-218">dnx451</span></span><br><span data-ttu-id="2225a-219">dnx452</span><span class="sxs-lookup"><span data-stu-id="2225a-219">dnx452</span></span>                  | <span data-ttu-id="2225a-220">netcoreapp</span><span class="sxs-lookup"><span data-stu-id="2225a-220">netcoreapp</span></span>  |
| <span data-ttu-id="2225a-221">dotnet</span><span class="sxs-lookup"><span data-stu-id="2225a-221">dotnet</span></span><br><span data-ttu-id="2225a-222">dotnet50</span><span class="sxs-lookup"><span data-stu-id="2225a-222">dotnet50</span></span><br><span data-ttu-id="2225a-223">dotnet51</span><span class="sxs-lookup"><span data-stu-id="2225a-223">dotnet51</span></span><br><span data-ttu-id="2225a-224">dotnet52</span><span class="sxs-lookup"><span data-stu-id="2225a-224">dotnet52</span></span><br><span data-ttu-id="2225a-225">dotnet53</span><span class="sxs-lookup"><span data-stu-id="2225a-225">dotnet53</span></span><br><span data-ttu-id="2225a-226">dotnet54</span><span class="sxs-lookup"><span data-stu-id="2225a-226">dotnet54</span></span><br><span data-ttu-id="2225a-227">dotnet55</span><span class="sxs-lookup"><span data-stu-id="2225a-227">dotnet55</span></span><br><span data-ttu-id="2225a-228">dotnet56</span><span class="sxs-lookup"><span data-stu-id="2225a-228">dotnet56</span></span> | <span data-ttu-id="2225a-229">netstandard</span><span class="sxs-lookup"><span data-stu-id="2225a-229">netstandard</span></span> |
| <span data-ttu-id="2225a-230">netcore50</span><span class="sxs-lookup"><span data-stu-id="2225a-230">netcore50</span></span>                                                                                  | <span data-ttu-id="2225a-231">uap10.0</span><span class="sxs-lookup"><span data-stu-id="2225a-231">uap10.0</span></span>     |
| <span data-ttu-id="2225a-232">win</span><span class="sxs-lookup"><span data-stu-id="2225a-232">win</span></span>                                                                                        | <span data-ttu-id="2225a-233">netcore45</span><span class="sxs-lookup"><span data-stu-id="2225a-233">netcore45</span></span>   |
| <span data-ttu-id="2225a-234">win8</span><span class="sxs-lookup"><span data-stu-id="2225a-234">win8</span></span>                                                                                       | <span data-ttu-id="2225a-235">netcore45</span><span class="sxs-lookup"><span data-stu-id="2225a-235">netcore45</span></span>   |
| <span data-ttu-id="2225a-236">win81</span><span class="sxs-lookup"><span data-stu-id="2225a-236">win81</span></span>                                                                                      | <span data-ttu-id="2225a-237">netcore451</span><span class="sxs-lookup"><span data-stu-id="2225a-237">netcore451</span></span>  |
| <span data-ttu-id="2225a-238">win10</span><span class="sxs-lookup"><span data-stu-id="2225a-238">win10</span></span>                                                                                      | <span data-ttu-id="2225a-239">uap10.0</span><span class="sxs-lookup"><span data-stu-id="2225a-239">uap10.0</span></span>     |
| <span data-ttu-id="2225a-240">winrt</span><span class="sxs-lookup"><span data-stu-id="2225a-240">winrt</span></span>                                                                                      | <span data-ttu-id="2225a-241">netcore45</span><span class="sxs-lookup"><span data-stu-id="2225a-241">netcore45</span></span>   |

## <a name="see-also"></a><span data-ttu-id="2225a-242">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2225a-242">See also</span></span>

- [<span data-ttu-id="2225a-243">套件、中繼套件和架構</span><span class="sxs-lookup"><span data-stu-id="2225a-243">Packages, Metapackages and Frameworks</span></span>](../core/packages.md)
- [<span data-ttu-id="2225a-244">使用跨平台工具開發程式庫</span><span class="sxs-lookup"><span data-stu-id="2225a-244">Developing Libraries with Cross Platform Tools</span></span>](../core/tutorials/libraries.md)
- [<span data-ttu-id="2225a-245">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2225a-245">.NET Standard</span></span>](net-standard.md)
- [<span data-ttu-id="2225a-246">.NET Core 版本控制</span><span class="sxs-lookup"><span data-stu-id="2225a-246">.NET Core Versioning</span></span>](../core/versions/index.md)
- [<span data-ttu-id="2225a-247">dotnet/standard GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="2225a-247">dotnet/standard GitHub repository</span></span>](https://github.com/dotnet/standard)
- [<span data-ttu-id="2225a-248">NuGet 工具 GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="2225a-248">NuGet Tools GitHub Repository</span></span>](https://github.com/joelverhagen/NuGetTools)
- <span data-ttu-id="2225a-249">[Framework Profiles in .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html) (.NET 中的 Framework 設定檔)</span><span class="sxs-lookup"><span data-stu-id="2225a-249">[Framework Profiles in .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)</span></span>
