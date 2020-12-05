---
title: .NET 中的程式碼分析
titleSuffix: ''
description: 瞭解 .NET SDK 中的原始程式碼分析。
ms.date: 08/22/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 8efac4d5e3fddcb9fdc6e08bcc933f2776420ced
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739970"
---
# <a name="overview-of-net-source-code-analysis"></a><span data-ttu-id="4da3d-103">.NET source 程式碼分析總覽</span><span class="sxs-lookup"><span data-stu-id="4da3d-103">Overview of .NET source code analysis</span></span>

<span data-ttu-id="4da3d-104">.NET 編譯器平台 (Roslyn) 分析器會檢查 C# 或 Visual Basic 程式碼以找出程式碼品質與程式碼樣式問題。</span><span class="sxs-lookup"><span data-stu-id="4da3d-104">.NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and code style issues.</span></span> <span data-ttu-id="4da3d-105">從 .NET 5.0 開始，這些分析器即隨附於 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="4da3d-105">Starting in .NET 5.0, these analyzers are included with the .NET SDK.</span></span> <span data-ttu-id="4da3d-106">如果您不想要移至 .NET 5 + SDK，或您偏好以 NuGet 套件為基礎的模型，則 `Microsoft.CodeAnalysis.NetAnalyzers` [nuget 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)中也會提供分析器。</span><span class="sxs-lookup"><span data-stu-id="4da3d-106">If you don't want to move to the .NET 5+ SDK or if you prefer a NuGet package-based model, the analyzers are also available in the `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers).</span></span> <span data-ttu-id="4da3d-107">您可能偏好以套件為基礎的模型來進行隨選版本更新。</span><span class="sxs-lookup"><span data-stu-id="4da3d-107">You might prefer a package-based model for on-demand version updates.</span></span>

> [!NOTE]
> <span data-ttu-id="4da3d-108">.NET 分析器與目標平臺無關。</span><span class="sxs-lookup"><span data-stu-id="4da3d-108">.NET analyzers are target-platform agnostic.</span></span> <span data-ttu-id="4da3d-109">也就是說，您的專案不需要以特定的 .NET 平臺為目標。</span><span class="sxs-lookup"><span data-stu-id="4da3d-109">That is, your project does not need to target a specific .NET platform.</span></span> <span data-ttu-id="4da3d-110">分析器適用于以和舊版 .NET 版本為目標的專案 `net5.0` ，例如 `netcoreapp` 、 `netstandard` 和 `net472` 。</span><span class="sxs-lookup"><span data-stu-id="4da3d-110">The analyzers work for projects that target `net5.0` as well as earlier .NET versions, such as `netcoreapp`, `netstandard`, and `net472`.</span></span>

- [<span data-ttu-id="4da3d-111">程式碼品質分析 ( "CAxxxx" 規則) </span><span class="sxs-lookup"><span data-stu-id="4da3d-111">Code quality analysis ("CAxxxx" rules)</span></span>](#code-quality-analysis)
- [<span data-ttu-id="4da3d-112">程式碼樣式分析 ( "IDExxxx" 規則) </span><span class="sxs-lookup"><span data-stu-id="4da3d-112">Code style analysis ("IDExxxx" rules)</span></span>](#code-style-analysis)

<span data-ttu-id="4da3d-113">如果分析器發現規則違規，就會回報為建議、警告或錯誤，視每個規則的 [設定](configuration-options.md)方式而定。</span><span class="sxs-lookup"><span data-stu-id="4da3d-113">If rule violations are found by an analyzer, they're reported as a suggestion, warning, or error, depending on how each rule is [configured](configuration-options.md).</span></span> <span data-ttu-id="4da3d-114">程式碼分析違規的開頭會加上 "CA" 或 "IDE" 前置詞，以區別它們與編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4da3d-114">Code analysis violations appear with the prefix "CA" or "IDE" to differentiate them from compiler errors.</span></span>

> [!TIP]
>
> - <span data-ttu-id="4da3d-115">您也可以安裝協力廠商分析器，例如 [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [XUnit 分析器](https://www.nuget.org/packages/xunit.analyzers/)和 [聲納 Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-115">You can also install third party analyzers, such as [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), and [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).</span></span>
> - <span data-ttu-id="4da3d-116">如果您使用 Visual Studio，許多分析器規則都有相關聯的 *程式碼修正* ，可讓您套用以修正問題。</span><span class="sxs-lookup"><span data-stu-id="4da3d-116">If you're using Visual Studio, many analyzer rules have associated *code fixes* that you can apply to correct the problem.</span></span> <span data-ttu-id="4da3d-117">程式碼修正會顯示在燈泡圖示功能表中。</span><span class="sxs-lookup"><span data-stu-id="4da3d-117">Code fixes are shown in the light bulb icon menu.</span></span>

## <a name="code-quality-analysis"></a><span data-ttu-id="4da3d-118">程式碼品質分析</span><span class="sxs-lookup"><span data-stu-id="4da3d-118">Code quality analysis</span></span>

<span data-ttu-id="4da3d-119">程式 _代碼品質分析 ( 「CA」 ) 規則_ 會檢查您的 c # 或 Visual Basic 的程式碼，以取得安全性、效能、設計和其他問題。</span><span class="sxs-lookup"><span data-stu-id="4da3d-119">_Code quality analysis ("CA") rules_ inspect your C# or Visual Basic code for security, performance, design and other issues.</span></span> <span data-ttu-id="4da3d-120">依預設，針對以 .NET 5.0 或更新版本為目標的專案，會啟用分析。</span><span class="sxs-lookup"><span data-stu-id="4da3d-120">Analysis is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="4da3d-121">您可以藉由將 [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) 屬性設定為，在以較早 .net 版本為目標的專案上啟用程式碼分析 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4da3d-121">You can enable code analysis on projects that target earlier .NET versions by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span> <span data-ttu-id="4da3d-122">您也可以將設定為，以停用專案的程式碼分析 `EnableNETAnalyzers` `false` 。</span><span class="sxs-lookup"><span data-stu-id="4da3d-122">You can also disable code analysis for your project by setting `EnableNETAnalyzers` to `false`.</span></span>

> [!TIP]
> <span data-ttu-id="4da3d-123">在 Visual Studio 中，您可以使用 [專案屬性視窗] 來啟用或停用程式碼分析。</span><span class="sxs-lookup"><span data-stu-id="4da3d-123">In Visual Studio, you can enable or disable code analysis using the Project Properties window.</span></span> <span data-ttu-id="4da3d-124">若要屬性視窗存取專案，請以滑鼠右鍵按一下方案總管內的專案，然後選取 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4da3d-124">To access the Project Properties window, right-click on a project within Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="4da3d-125">接下來，選取 [程式 **代碼分析** ] 索引標籤，然後選取或清除核取方塊以 **啟用 .net 分析器**。</span><span class="sxs-lookup"><span data-stu-id="4da3d-125">Next, select the **Code Analysis** tab, and then either select or clear the checkbox to **Enable .NET analyzers**.</span></span>

### <a name="enabled-rules"></a><span data-ttu-id="4da3d-126">啟用的規則</span><span class="sxs-lookup"><span data-stu-id="4da3d-126">Enabled rules</span></span>

<span data-ttu-id="4da3d-127">依預設，會在 .NET 5.0 Preview 8 中啟用下列規則。</span><span class="sxs-lookup"><span data-stu-id="4da3d-127">The following rules are enabled, by default, in .NET 5.0 Preview 8.</span></span>

| <span data-ttu-id="4da3d-128">診斷識別碼</span><span class="sxs-lookup"><span data-stu-id="4da3d-128">Diagnostic ID</span></span> | <span data-ttu-id="4da3d-129">類別</span><span class="sxs-lookup"><span data-stu-id="4da3d-129">Category</span></span> | <span data-ttu-id="4da3d-130">嚴重性</span><span class="sxs-lookup"><span data-stu-id="4da3d-130">Severity</span></span> | <span data-ttu-id="4da3d-131">描述</span><span class="sxs-lookup"><span data-stu-id="4da3d-131">Description</span></span> |
| - | - | - | - |
| [<span data-ttu-id="4da3d-132">CA1416</span><span class="sxs-lookup"><span data-stu-id="4da3d-132">CA1416</span></span>](/visualstudio/code-quality/ca1416) | <span data-ttu-id="4da3d-133">互通性</span><span class="sxs-lookup"><span data-stu-id="4da3d-133">Interoperability</span></span> | <span data-ttu-id="4da3d-134">警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-134">Warning</span></span> | <span data-ttu-id="4da3d-135">平台相容性分析器</span><span class="sxs-lookup"><span data-stu-id="4da3d-135">Platform compatibility analyzer</span></span> |
| [<span data-ttu-id="4da3d-136">CA1417</span><span class="sxs-lookup"><span data-stu-id="4da3d-136">CA1417</span></span>](/visualstudio/code-quality/ca1417) | <span data-ttu-id="4da3d-137">互通性</span><span class="sxs-lookup"><span data-stu-id="4da3d-137">Interoperability</span></span> | <span data-ttu-id="4da3d-138">警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-138">Warning</span></span> | <span data-ttu-id="4da3d-139">請勿 `OutAttribute` 在 P/invoke 的字串參數上使用</span><span class="sxs-lookup"><span data-stu-id="4da3d-139">Do not use `OutAttribute` on string parameters for P/Invokes</span></span> |
| [<span data-ttu-id="4da3d-140">CA1831</span><span class="sxs-lookup"><span data-stu-id="4da3d-140">CA1831</span></span>](/visualstudio/code-quality/ca1831) | <span data-ttu-id="4da3d-141">效能</span><span class="sxs-lookup"><span data-stu-id="4da3d-141">Performance</span></span> | <span data-ttu-id="4da3d-142">警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-142">Warning</span></span> | <span data-ttu-id="4da3d-143">`AsSpan`適當時，請使用而不是字串以範圍為基礎的索引子</span><span class="sxs-lookup"><span data-stu-id="4da3d-143">Use `AsSpan` instead of range-based indexers for string when appropriate</span></span> |
| [<span data-ttu-id="4da3d-144">CA2013</span><span class="sxs-lookup"><span data-stu-id="4da3d-144">CA2013</span></span>](/visualstudio/code-quality/ca2013) | <span data-ttu-id="4da3d-145">可靠性</span><span class="sxs-lookup"><span data-stu-id="4da3d-145">Reliability</span></span> | <span data-ttu-id="4da3d-146">警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-146">Warning</span></span> | <span data-ttu-id="4da3d-147">請勿搭配實 `ReferenceEquals` 數值型別使用</span><span class="sxs-lookup"><span data-stu-id="4da3d-147">Do not use `ReferenceEquals` with value types</span></span> |
| [<span data-ttu-id="4da3d-148">CA2014</span><span class="sxs-lookup"><span data-stu-id="4da3d-148">CA2014</span></span>](/visualstudio/code-quality/ca2014) | <span data-ttu-id="4da3d-149">可靠性</span><span class="sxs-lookup"><span data-stu-id="4da3d-149">Reliability</span></span> | <span data-ttu-id="4da3d-150">警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-150">Warning</span></span> | <span data-ttu-id="4da3d-151">不要 `stackalloc` 在迴圈中使用</span><span class="sxs-lookup"><span data-stu-id="4da3d-151">Do not use `stackalloc` in loops</span></span> |
| [<span data-ttu-id="4da3d-152">CA2015</span><span class="sxs-lookup"><span data-stu-id="4da3d-152">CA2015</span></span>](/visualstudio/code-quality/ca2015) | <span data-ttu-id="4da3d-153">可靠性</span><span class="sxs-lookup"><span data-stu-id="4da3d-153">Reliability</span></span> | <span data-ttu-id="4da3d-154">警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-154">Warning</span></span> | <span data-ttu-id="4da3d-155">請勿針對衍生自的類型定義完成項 <xref:System.Buffers.MemoryManager%601></span><span class="sxs-lookup"><span data-stu-id="4da3d-155">Do not define finalizers for types derived from <xref:System.Buffers.MemoryManager%601></span></span> |
| [<span data-ttu-id="4da3d-156">CA2200</span><span class="sxs-lookup"><span data-stu-id="4da3d-156">CA2200</span></span>](/visualstudio/code-quality/ca2200) | <span data-ttu-id="4da3d-157">使用方式</span><span class="sxs-lookup"><span data-stu-id="4da3d-157">Usage</span></span> | <span data-ttu-id="4da3d-158">警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-158">Warning</span></span> | <span data-ttu-id="4da3d-159">必須重新擲回以保存堆疊詳細資料</span><span class="sxs-lookup"><span data-stu-id="4da3d-159">Rethrow to preserve stack details</span></span>
| [<span data-ttu-id="4da3d-160">CA2247</span><span class="sxs-lookup"><span data-stu-id="4da3d-160">CA2247</span></span>](/visualstudio/code-quality/ca2247) | <span data-ttu-id="4da3d-161">使用方式</span><span class="sxs-lookup"><span data-stu-id="4da3d-161">Usage</span></span> | <span data-ttu-id="4da3d-162">警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-162">Warning</span></span> | <span data-ttu-id="4da3d-163">傳遞至 >taskcompletionsource 函式的引數應該是 <xref:System.Threading.Tasks.TaskCreationOptions> 列舉，而不是 <xref:System.Threading.Tasks.TaskContinuationOptions></span><span class="sxs-lookup"><span data-stu-id="4da3d-163">Argument passed to TaskCompletionSource constructor should be <xref:System.Threading.Tasks.TaskCreationOptions> enum instead of <xref:System.Threading.Tasks.TaskContinuationOptions></span></span> |

<span data-ttu-id="4da3d-164">您可以變更這些規則的嚴重性來停用它們，或將它們提升為錯誤。</span><span class="sxs-lookup"><span data-stu-id="4da3d-164">You can change the severity of these rules to disable them or elevate them to errors.</span></span>

<span data-ttu-id="4da3d-165">如需可用程式碼品質規則的完整清單，請參閱程式 [代碼品質規則](quality-rules/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-165">For a full list of available code quality rules, see [Code quality rules](quality-rules/index.md).</span></span>

### <a name="enable-additional-rules"></a><span data-ttu-id="4da3d-166">啟用其他規則</span><span class="sxs-lookup"><span data-stu-id="4da3d-166">Enable additional rules</span></span>

<span data-ttu-id="4da3d-167">從 .NET 5.0 RC2 開始，.NET SDK 隨附所有「CA」程式 [代碼品質規則](/visualstudio/code-quality/code-analysis-for-managed-code-warnings)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-167">Starting with .NET 5.0 RC2, the .NET SDK ships with all of the ["CA" code quality rules](/visualstudio/code-quality/code-analysis-for-managed-code-warnings).</span></span> <span data-ttu-id="4da3d-168">如需每個 .NET SDK 版本所包含之規則的完整清單，請參閱 [分析器版本](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-168">For a full list of rules that are included with each .NET SDK version, see [analyzer releases](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>

#### <a name="default-analysis-mode"></a><span data-ttu-id="4da3d-169">預設分析模式</span><span class="sxs-lookup"><span data-stu-id="4da3d-169">Default analysis mode</span></span>

<span data-ttu-id="4da3d-170">在預設的分析模式中，有些規則 [預設會啟用](#enabled-rules) 為組建警告。</span><span class="sxs-lookup"><span data-stu-id="4da3d-170">In the default analysis mode, some rules are [enabled by default](#enabled-rules) as build warnings.</span></span> <span data-ttu-id="4da3d-171">某些其他規則預設為啟用，但 Visual Studio IDE 建議的對應程式碼修正。</span><span class="sxs-lookup"><span data-stu-id="4da3d-171">Some other rules are enabled by default only as Visual Studio IDE suggestions with corresponding code fixes.</span></span> <span data-ttu-id="4da3d-172">其餘規則預設為停用。</span><span class="sxs-lookup"><span data-stu-id="4da3d-172">The remaining rules are disabled by default.</span></span> <span data-ttu-id="4da3d-173">[規則的完整清單](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)包含每個規則的預設嚴重性，以及預設的分析模式是否啟用規則。</span><span class="sxs-lookup"><span data-stu-id="4da3d-173">The [full list of rules](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md) includes each rule's default severity and whether or not the rule is enabled by default in the default analysis mode.</span></span>

#### <a name="custom-analysis-mode"></a><span data-ttu-id="4da3d-174">自訂分析模式</span><span class="sxs-lookup"><span data-stu-id="4da3d-174">Custom analysis mode</span></span>

<span data-ttu-id="4da3d-175">您可以 [設定程式碼分析規則](configuration-options.md) ，以啟用或停用個別規則或規則類別。</span><span class="sxs-lookup"><span data-stu-id="4da3d-175">You can [configure code analysis rules](configuration-options.md) to enable or disable an individual rule or a category of rules.</span></span> <span data-ttu-id="4da3d-176">此外，您可以使用 [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) 屬性來切換至下列其中一個自訂分析模式：</span><span class="sxs-lookup"><span data-stu-id="4da3d-176">Additionally, you can use the [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) property to switch to one of the following custom analysis modes:</span></span>

- <span data-ttu-id="4da3d-177">_積極_ 或 _退出_ 模式：依預設會啟用所有規則作為組建警告。</span><span class="sxs-lookup"><span data-stu-id="4da3d-177">_Aggressive_ or _Opt-out_ mode: All rules are enabled by default as build warnings.</span></span> <span data-ttu-id="4da3d-178">您可以選擇性地 [退出宣告](configuration-options.md) 個別規則來停用它們。</span><span class="sxs-lookup"><span data-stu-id="4da3d-178">You can selectively [opt out](configuration-options.md) of individual rules to disable them.</span></span>
- <span data-ttu-id="4da3d-179">_保守_ 或 _加入宣告_ 模式：預設會停用所有規則。</span><span class="sxs-lookup"><span data-stu-id="4da3d-179">_Conservative_ or _Opt-in_ mode: All rules are disabled by default.</span></span> <span data-ttu-id="4da3d-180">您可以選擇性地 [選擇](configuration-options.md) 加入個別規則來啟用它們。</span><span class="sxs-lookup"><span data-stu-id="4da3d-180">You can selectively [opt into](configuration-options.md) individual rules to enable them.</span></span>

### <a name="treat-warnings-as-errors"></a><span data-ttu-id="4da3d-181">將警告視為錯誤</span><span class="sxs-lookup"><span data-stu-id="4da3d-181">Treat warnings as errors</span></span>

<span data-ttu-id="4da3d-182">如果您在 `-warnaserror` 建立專案時使用旗標，則也會將所有程式碼分析警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="4da3d-182">If you use the `-warnaserror` flag when you build your projects, all code analysis warnings are also treated as errors.</span></span> <span data-ttu-id="4da3d-183">如果您不想要將程式碼品質警告 (CAxxxx) 要被視為存在的錯誤 `-warnaserror` ，您可以 `CodeAnalysisTreatWarningsAsErrors` 在專案檔中將 MSBuild 屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4da3d-183">If you do not want code quality warnings (CAxxxx) to be treated as errors in presence of `-warnaserror`, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="4da3d-184">您仍然會看到任何程式碼分析警告，但不會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="4da3d-184">You'll still see any code analysis warnings, but they won't break your build.</span></span>

### <a name="latest-updates"></a><span data-ttu-id="4da3d-185">最新的更新</span><span class="sxs-lookup"><span data-stu-id="4da3d-185">Latest updates</span></span>

<span data-ttu-id="4da3d-186">依預設，當您升級至較新版本的 .NET SDK 時，您將會取得最新的程式碼分析規則和預設規則嚴重性。</span><span class="sxs-lookup"><span data-stu-id="4da3d-186">By default, you'll get the latest code analysis rules and default rule severities as you upgrade to newer versions of the .NET SDK.</span></span> <span data-ttu-id="4da3d-187">如果您不想要此行為，例如，如果您想要確保沒有啟用或停用任何新規則，您可以透過下列其中一種方式來覆寫它：</span><span class="sxs-lookup"><span data-stu-id="4da3d-187">If you don't want this behavior, for example, if you want to ensure that no new rules are enabled or disabled, you can override it in one of the following ways:</span></span>

- <span data-ttu-id="4da3d-188">將 `AnalysisLevel` MSBuild 屬性設定為特定值，以將警告鎖定至該集合。</span><span class="sxs-lookup"><span data-stu-id="4da3d-188">Set the `AnalysisLevel` MSBuild property to a specific value to lock the warnings to that set.</span></span> <span data-ttu-id="4da3d-189">當您升級至較新的 SDK 時，仍會收到這些警告的錯誤修正，但不會啟用任何新的警告，也不會停用任何現有的警告。</span><span class="sxs-lookup"><span data-stu-id="4da3d-189">When you upgrade to a newer SDK, you'll still get bug fixes for those warnings, but no new warnings will be enabled and no existing warnings will be disabled.</span></span> <span data-ttu-id="4da3d-190">例如，若要將規則集鎖定為 .NET SDK 5.0 版隨附的規則，請將下列專案新增至您的專案檔。</span><span class="sxs-lookup"><span data-stu-id="4da3d-190">For example, to lock the set of rules to those that ship with version 5.0 of the .NET SDK, add the following entry to your project file.</span></span>

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > <span data-ttu-id="4da3d-191">屬性的預設值 `AnalysisLevel` 是 `latest` ，這表示當您移至較新版本的 .net SDK 時，一律會取得最新的程式碼分析規則。</span><span class="sxs-lookup"><span data-stu-id="4da3d-191">The default value for the `AnalysisLevel` property is `latest`, which means you always get the latest code analysis rules as you move to newer versions of the .NET SDK.</span></span>

  <span data-ttu-id="4da3d-192">如需詳細資訊，以及查看可能值的清單，請參閱 [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-192">For more information, and to see a list of possible values, see [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel).</span></span>

- <span data-ttu-id="4da3d-193">安裝 [CodeAnalysis NetAnalyzers NuGet 套件](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) ，以從 .net SDK 更新分離規則更新。</span><span class="sxs-lookup"><span data-stu-id="4da3d-193">Install the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) to decouple rule updates from .NET SDK updates.</span></span> <span data-ttu-id="4da3d-194">如果 SDK 包含的分析器元件版本比 NuGet 套件還新，則安裝套件會關閉內建的 SDK 分析器，並產生組建警告。</span><span class="sxs-lookup"><span data-stu-id="4da3d-194">Installing the package turns off the built-in SDK analyzers and generates a build warning if the SDK contains a newer analyzer assembly version than that of the NuGet package.</span></span>

## <a name="code-style-analysis"></a><span data-ttu-id="4da3d-195">程式碼樣式分析</span><span class="sxs-lookup"><span data-stu-id="4da3d-195">Code style analysis</span></span>

<span data-ttu-id="4da3d-196">程式[代碼樣式分析](/visualstudio/ide/editorconfig-code-style-settings-reference) ( "IDExxxx" 規則) 可讓您在程式碼基底中定義和維護一致的程式碼樣式。</span><span class="sxs-lookup"><span data-stu-id="4da3d-196">[Code style analysis](/visualstudio/ide/editorconfig-code-style-settings-reference) ("IDExxxx" rules) enables you to define and maintain consistent code style in your codebase.</span></span> <span data-ttu-id="4da3d-197">以下是預設設定：</span><span class="sxs-lookup"><span data-stu-id="4da3d-197">Following are the default settings:</span></span>

- <span data-ttu-id="4da3d-198">命令列組建：針對命令列組建上的所有 .NET 專案，預設會停用程式碼樣式分析。</span><span class="sxs-lookup"><span data-stu-id="4da3d-198">Command line build: Code style analysis is disabled, by default, for all .NET projects on command-line builds.</span></span>
- <span data-ttu-id="4da3d-199">Visual Studio：程式碼樣式分析預設會針對 Visual Studio 中的所有 .NET 專案啟用，因為程式 [代碼會重構快速動作](/visualstudio/ide/code-generation-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-199">Visual Studio: Code style analysis is enabled, by default, for all .NET projects inside Visual Studio as [code refactoring quick actions](/visualstudio/ide/code-generation-in-visual-studio).</span></span>

<span data-ttu-id="4da3d-200">從 .NET 5.0 RC2 開始，您可以在命令列和 Visual Studio 內啟用組建的程式碼樣式分析。</span><span class="sxs-lookup"><span data-stu-id="4da3d-200">Starting .NET 5.0 RC2, you can enable code style analysis on build, both at the command line and inside Visual Studio.</span></span> <span data-ttu-id="4da3d-201">程式碼樣式違規會顯示為「IDE」前置詞的警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="4da3d-201">Code style violations appear as warnings or errors with an "IDE" prefix.</span></span> <span data-ttu-id="4da3d-202">這可讓您在組建階段強制執行一致的程式碼樣式。</span><span class="sxs-lookup"><span data-stu-id="4da3d-202">This enables you to enforce consistent code styles at build time.</span></span>

> [!NOTE]
> <span data-ttu-id="4da3d-203">程式碼樣式分析功能是實驗性，而且在 .NET 5 和 .NET 6 版本之間可能會變更。</span><span class="sxs-lookup"><span data-stu-id="4da3d-203">The code style analysis feature is experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="4da3d-204">在組建上啟用程式碼樣式分析的步驟：</span><span class="sxs-lookup"><span data-stu-id="4da3d-204">Steps to enable code style analysis on build:</span></span>

1. <span data-ttu-id="4da3d-205">將 MSBuild 屬性 [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) 設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4da3d-205">Set the MSBuild property [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) to `true`.</span></span>

1. <span data-ttu-id="4da3d-206">在 *editorconfig* 檔案中，將您想要在組建上執行的每個「IDE」程式碼樣式規則 [設定](configuration-options.md) 為警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="4da3d-206">In an *.editorconfig* file, [configure](configuration-options.md) each "IDE" code style rule that you wish to run on build as a warning or an error.</span></span> <span data-ttu-id="4da3d-207">例如：</span><span class="sxs-lookup"><span data-stu-id="4da3d-207">For example:</span></span>

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   <span data-ttu-id="4da3d-208">或者，您可以將整個「樣式」類別設定為警告或錯誤（依預設，），然後選擇性地關閉您不想在組建上執行的規則。</span><span class="sxs-lookup"><span data-stu-id="4da3d-208">Alternatively, you can configure the entire "Style" category to be a warning or error, by default, and then selectively turn off rules that you don't want to run on build.</span></span> <span data-ttu-id="4da3d-209">例如：</span><span class="sxs-lookup"><span data-stu-id="4da3d-209">For example:</span></span>

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

## <a name="suppress-a-warning"></a><span data-ttu-id="4da3d-210">隱藏警告</span><span class="sxs-lookup"><span data-stu-id="4da3d-210">Suppress a warning</span></span>

<span data-ttu-id="4da3d-211">若要隱藏規則違規，請在 EditorConfig 檔案中將該規則識別碼的嚴重性選項設定為 `none` 。</span><span class="sxs-lookup"><span data-stu-id="4da3d-211">To suppress a rule violation, set the severity option for that rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="4da3d-212">例如：</span><span class="sxs-lookup"><span data-stu-id="4da3d-212">For example:</span></span>

```ini
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="4da3d-213">Visual Studio 提供其他方式來隱藏程式碼分析規則的警告。</span><span class="sxs-lookup"><span data-stu-id="4da3d-213">Visual Studio provides additional ways to suppress warnings from code analysis rules.</span></span> <span data-ttu-id="4da3d-214">如需詳細資訊，請參閱 [隱藏違規](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-214">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span></span>

<span data-ttu-id="4da3d-215">如需有關規則嚴重性的詳細資訊，請參閱 [設定規則嚴重性](configuration-options.md#severity-level)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-215">For more information about rule severities, see [Configure rule severity](configuration-options.md#severity-level).</span></span>

## <a name="see-also"></a><span data-ttu-id="4da3d-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4da3d-216">See also</span></span>

- [<span data-ttu-id="4da3d-217">程式碼品質分析規則參考</span><span class="sxs-lookup"><span data-stu-id="4da3d-217">Code quality analysis rule reference</span></span>](quality-rules/index.md)
- [<span data-ttu-id="4da3d-218">程式碼樣式分析規則參考</span><span class="sxs-lookup"><span data-stu-id="4da3d-218">Code style analysis rule reference</span></span>](style-rules/index.md)
- [<span data-ttu-id="4da3d-219">Visual Studio 中的程式碼分析</span><span class="sxs-lookup"><span data-stu-id="4da3d-219">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="4da3d-220">.NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="4da3d-220">.NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="4da3d-221">教學課程：撰寫您的第一個分析器和程式碼修正</span><span class="sxs-lookup"><span data-stu-id="4da3d-221">Tutorial: Write your first analyzer and code fix</span></span>](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
