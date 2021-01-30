---
title: .NET 中的程式碼分析
titleSuffix: ''
description: 瞭解 .NET SDK 中的原始程式碼分析。
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: efc440adb59da1ef9838ec5445d9c55544c14380
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216469"
---
# <a name="overview-of-net-source-code-analysis"></a><span data-ttu-id="b650b-103">.NET source 程式碼分析總覽</span><span class="sxs-lookup"><span data-stu-id="b650b-103">Overview of .NET source code analysis</span></span>

<span data-ttu-id="b650b-104">.NET 編譯器平台 (Roslyn) 分析器會檢查 C# 或 Visual Basic 程式碼以找出程式碼品質與程式碼樣式問題。</span><span class="sxs-lookup"><span data-stu-id="b650b-104">.NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and code style issues.</span></span> <span data-ttu-id="b650b-105">從 .NET 5.0 開始，這些分析器會隨附于 .NET SDK 中，您不需要個別安裝。</span><span class="sxs-lookup"><span data-stu-id="b650b-105">Starting in .NET 5.0, these analyzers are included with the .NET SDK and you don't need to install them separately.</span></span> <span data-ttu-id="b650b-106">如果您的專案是以 .NET 5 或更新版本為目標，則預設會啟用程式碼分析。</span><span class="sxs-lookup"><span data-stu-id="b650b-106">If your project targets .NET 5 or later, code analysis is enabled by default.</span></span> <span data-ttu-id="b650b-107">如果您的專案以不同的 .NET 執行為目標（例如，.NET Core、.NET Standard 或 .NET Framework），您必須將 [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) 屬性設定為，以手動方式啟用程式碼分析 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b650b-107">If your project target a different .NET implementation, for example, .NET Core, .NET Standard, or .NET Framework, you must manually enable code analysis by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span>

<span data-ttu-id="b650b-108">如果您不想要移至 .NET 5 + SDK，或您偏好以 NuGet 套件為基礎的模型，也可以在 [CodeAnalysis. NetAnalyzers NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)中找到分析器。</span><span class="sxs-lookup"><span data-stu-id="b650b-108">If you don't want to move to the .NET 5+ SDK or if you prefer a NuGet package-based model, the analyzers are also available in the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers).</span></span> <span data-ttu-id="b650b-109">您可能偏好以套件為基礎的模型來進行隨選版本更新。</span><span class="sxs-lookup"><span data-stu-id="b650b-109">You might prefer a package-based model for on-demand version updates.</span></span>

> [!NOTE]
> <span data-ttu-id="b650b-110">.NET 分析器與目標架構無關。</span><span class="sxs-lookup"><span data-stu-id="b650b-110">.NET analyzers are target-framework agnostic.</span></span> <span data-ttu-id="b650b-111">也就是說，您的專案不需要以特定的 .NET 實作為目標。</span><span class="sxs-lookup"><span data-stu-id="b650b-111">That is, your project does not need to target a specific .NET implementation.</span></span> <span data-ttu-id="b650b-112">分析器適用于以 `net5.0` 和舊版 .net 版本為目標的專案，例如 `netcoreapp3.1` 和 `net472` 。</span><span class="sxs-lookup"><span data-stu-id="b650b-112">The analyzers work for projects that target `net5.0` as well as earlier .NET versions, such as `netcoreapp3.1` and `net472`.</span></span>

<span data-ttu-id="b650b-113">如果分析器發現規則違規，就會回報為建議、警告或錯誤，視每個規則的 [設定](configuration-options.md)方式而定。</span><span class="sxs-lookup"><span data-stu-id="b650b-113">If rule violations are found by an analyzer, they're reported as a suggestion, warning, or error, depending on how each rule is [configured](configuration-options.md).</span></span> <span data-ttu-id="b650b-114">程式碼分析違規的開頭會加上 "CA" 或 "IDE" 前置詞，以區別它們與編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="b650b-114">Code analysis violations appear with the prefix "CA" or "IDE" to differentiate them from compiler errors.</span></span>

## <a name="code-quality-analysis"></a><span data-ttu-id="b650b-115">程式碼品質分析</span><span class="sxs-lookup"><span data-stu-id="b650b-115">Code quality analysis</span></span>

<span data-ttu-id="b650b-116">程式 *代碼品質分析* ( "CAxxxx" ) 規則會檢查您的 c # 或 Visual Basic 程式碼，以取得安全性、效能、設計和其他問題。</span><span class="sxs-lookup"><span data-stu-id="b650b-116">*Code quality analysis* ("CAxxxx") rules inspect your C# or Visual Basic code for security, performance, design and other issues.</span></span> <span data-ttu-id="b650b-117">依預設，針對以 .NET 5.0 或更新版本為目標的專案，會啟用分析。</span><span class="sxs-lookup"><span data-stu-id="b650b-117">Analysis is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="b650b-118">您可以藉由將 [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) 屬性設定為，在以較早 .net 版本為目標的專案上啟用程式碼分析 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b650b-118">You can enable code analysis on projects that target earlier .NET versions by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span> <span data-ttu-id="b650b-119">您也可以將設定為，以停用專案的程式碼分析 `EnableNETAnalyzers` `false` 。</span><span class="sxs-lookup"><span data-stu-id="b650b-119">You can also disable code analysis for your project by setting `EnableNETAnalyzers` to `false`.</span></span>

> [!TIP]
> <span data-ttu-id="b650b-120">如果您使用 Visual Studio：</span><span class="sxs-lookup"><span data-stu-id="b650b-120">If you're using Visual Studio:</span></span>
>
> - <span data-ttu-id="b650b-121">許多分析器規則都有相關聯的 *程式碼修正* ，可讓您修正問題。</span><span class="sxs-lookup"><span data-stu-id="b650b-121">Many analyzer rules have associated *code fixes* that you can apply to correct the problem.</span></span> <span data-ttu-id="b650b-122">程式碼修正會顯示在燈泡圖示功能表中。</span><span class="sxs-lookup"><span data-stu-id="b650b-122">Code fixes are shown in the light bulb icon menu.</span></span>
> - <span data-ttu-id="b650b-123">您可以在方案總管中的專案上按一下滑鼠右鍵，然後選取 [**屬性** 程式  >  **代碼分析**] 索引標籤 >**啟用 .net 分析器**，藉以啟用或停用程式碼分析。</span><span class="sxs-lookup"><span data-stu-id="b650b-123">You can enable or disable code analysis by right-clicking on a project in Solution Explorer and selecting **Properties** > **Code Analysis** tab > **Enable .NET analyzers**.</span></span>

### <a name="enabled-rules"></a><span data-ttu-id="b650b-124">啟用的規則</span><span class="sxs-lookup"><span data-stu-id="b650b-124">Enabled rules</span></span>

<span data-ttu-id="b650b-125">依預設，會在 .NET 5.0 中啟用下列規則。</span><span class="sxs-lookup"><span data-stu-id="b650b-125">The following rules are enabled, by default, in .NET 5.0.</span></span>

| <span data-ttu-id="b650b-126">診斷識別碼</span><span class="sxs-lookup"><span data-stu-id="b650b-126">Diagnostic ID</span></span> | <span data-ttu-id="b650b-127">類別</span><span class="sxs-lookup"><span data-stu-id="b650b-127">Category</span></span> | <span data-ttu-id="b650b-128">嚴重性</span><span class="sxs-lookup"><span data-stu-id="b650b-128">Severity</span></span> | <span data-ttu-id="b650b-129">描述</span><span class="sxs-lookup"><span data-stu-id="b650b-129">Description</span></span> |
| - | - | - | - |
| [<span data-ttu-id="b650b-130">CA1416</span><span class="sxs-lookup"><span data-stu-id="b650b-130">CA1416</span></span>](/visualstudio/code-quality/ca1416) | <span data-ttu-id="b650b-131">互通性</span><span class="sxs-lookup"><span data-stu-id="b650b-131">Interoperability</span></span> | <span data-ttu-id="b650b-132">警告</span><span class="sxs-lookup"><span data-stu-id="b650b-132">Warning</span></span> | <span data-ttu-id="b650b-133">平台相容性分析器</span><span class="sxs-lookup"><span data-stu-id="b650b-133">Platform compatibility analyzer</span></span> |
| [<span data-ttu-id="b650b-134">CA1417</span><span class="sxs-lookup"><span data-stu-id="b650b-134">CA1417</span></span>](/visualstudio/code-quality/ca1417) | <span data-ttu-id="b650b-135">互通性</span><span class="sxs-lookup"><span data-stu-id="b650b-135">Interoperability</span></span> | <span data-ttu-id="b650b-136">警告</span><span class="sxs-lookup"><span data-stu-id="b650b-136">Warning</span></span> | <span data-ttu-id="b650b-137">請勿 `OutAttribute` 在 P/invoke 的字串參數上使用</span><span class="sxs-lookup"><span data-stu-id="b650b-137">Do not use `OutAttribute` on string parameters for P/Invokes</span></span> |
| [<span data-ttu-id="b650b-138">CA1831</span><span class="sxs-lookup"><span data-stu-id="b650b-138">CA1831</span></span>](/visualstudio/code-quality/ca1831) | <span data-ttu-id="b650b-139">效能</span><span class="sxs-lookup"><span data-stu-id="b650b-139">Performance</span></span> | <span data-ttu-id="b650b-140">警告</span><span class="sxs-lookup"><span data-stu-id="b650b-140">Warning</span></span> | <span data-ttu-id="b650b-141">`AsSpan`適當時，請使用而不是字串以範圍為基礎的索引子</span><span class="sxs-lookup"><span data-stu-id="b650b-141">Use `AsSpan` instead of range-based indexers for string when appropriate</span></span> |
| [<span data-ttu-id="b650b-142">CA2013</span><span class="sxs-lookup"><span data-stu-id="b650b-142">CA2013</span></span>](/visualstudio/code-quality/ca2013) | <span data-ttu-id="b650b-143">可靠性</span><span class="sxs-lookup"><span data-stu-id="b650b-143">Reliability</span></span> | <span data-ttu-id="b650b-144">警告</span><span class="sxs-lookup"><span data-stu-id="b650b-144">Warning</span></span> | <span data-ttu-id="b650b-145">請勿搭配實 `ReferenceEquals` 數值型別使用</span><span class="sxs-lookup"><span data-stu-id="b650b-145">Do not use `ReferenceEquals` with value types</span></span> |
| [<span data-ttu-id="b650b-146">CA2014</span><span class="sxs-lookup"><span data-stu-id="b650b-146">CA2014</span></span>](/visualstudio/code-quality/ca2014) | <span data-ttu-id="b650b-147">可靠性</span><span class="sxs-lookup"><span data-stu-id="b650b-147">Reliability</span></span> | <span data-ttu-id="b650b-148">警告</span><span class="sxs-lookup"><span data-stu-id="b650b-148">Warning</span></span> | <span data-ttu-id="b650b-149">不要 `stackalloc` 在迴圈中使用</span><span class="sxs-lookup"><span data-stu-id="b650b-149">Do not use `stackalloc` in loops</span></span> |
| [<span data-ttu-id="b650b-150">CA2015</span><span class="sxs-lookup"><span data-stu-id="b650b-150">CA2015</span></span>](/visualstudio/code-quality/ca2015) | <span data-ttu-id="b650b-151">可靠性</span><span class="sxs-lookup"><span data-stu-id="b650b-151">Reliability</span></span> | <span data-ttu-id="b650b-152">警告</span><span class="sxs-lookup"><span data-stu-id="b650b-152">Warning</span></span> | <span data-ttu-id="b650b-153">請勿針對衍生自的類型定義完成項 <xref:System.Buffers.MemoryManager%601></span><span class="sxs-lookup"><span data-stu-id="b650b-153">Do not define finalizers for types derived from <xref:System.Buffers.MemoryManager%601></span></span> |
| [<span data-ttu-id="b650b-154">CA2200</span><span class="sxs-lookup"><span data-stu-id="b650b-154">CA2200</span></span>](/visualstudio/code-quality/ca2200) | <span data-ttu-id="b650b-155">使用方式</span><span class="sxs-lookup"><span data-stu-id="b650b-155">Usage</span></span> | <span data-ttu-id="b650b-156">警告</span><span class="sxs-lookup"><span data-stu-id="b650b-156">Warning</span></span> | <span data-ttu-id="b650b-157">必須重新擲回以保存堆疊詳細資料</span><span class="sxs-lookup"><span data-stu-id="b650b-157">Rethrow to preserve stack details</span></span>
| [<span data-ttu-id="b650b-158">CA2247</span><span class="sxs-lookup"><span data-stu-id="b650b-158">CA2247</span></span>](/visualstudio/code-quality/ca2247) | <span data-ttu-id="b650b-159">使用方式</span><span class="sxs-lookup"><span data-stu-id="b650b-159">Usage</span></span> | <span data-ttu-id="b650b-160">警告</span><span class="sxs-lookup"><span data-stu-id="b650b-160">Warning</span></span> | <span data-ttu-id="b650b-161">傳遞至 >taskcompletionsource 函式的引數應該是 <xref:System.Threading.Tasks.TaskCreationOptions> 列舉，而不是 <xref:System.Threading.Tasks.TaskContinuationOptions></span><span class="sxs-lookup"><span data-stu-id="b650b-161">Argument passed to TaskCompletionSource constructor should be <xref:System.Threading.Tasks.TaskCreationOptions> enum instead of <xref:System.Threading.Tasks.TaskContinuationOptions></span></span> |

<span data-ttu-id="b650b-162">您可以變更這些規則的嚴重性來停用它們，或將它們提升為錯誤。</span><span class="sxs-lookup"><span data-stu-id="b650b-162">You can change the severity of these rules to disable them or elevate them to errors.</span></span> <span data-ttu-id="b650b-163">您也可以 [啟用更多規則](#enable-additional-rules)。</span><span class="sxs-lookup"><span data-stu-id="b650b-163">You can also [enable more rules](#enable-additional-rules).</span></span>

- <span data-ttu-id="b650b-164">如需每個 .NET SDK 版本所包含的規則清單，請參閱 [分析器版本](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)。</span><span class="sxs-lookup"><span data-stu-id="b650b-164">For a list of rules that are included with each .NET SDK version, see [Analyzer releases](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>
- <span data-ttu-id="b650b-165">如需所有程式碼品質規則的清單，請參閱程式 [代碼品質規則](quality-rules/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b650b-165">For a list of all the code quality rules, see [Code quality rules](quality-rules/index.md).</span></span>

### <a name="enable-additional-rules"></a><span data-ttu-id="b650b-166">啟用其他規則</span><span class="sxs-lookup"><span data-stu-id="b650b-166">Enable additional rules</span></span>

<span data-ttu-id="b650b-167">*分析模式* 指的是預先定義的程式碼分析設定，其中未啟用任何、部分或所有規則。</span><span class="sxs-lookup"><span data-stu-id="b650b-167">*Analysis mode* refers to a predefined code analysis configuration where none, some, or all rules are enabled.</span></span> <span data-ttu-id="b650b-168">在預設的分析模式中，只會啟用少量的規則 [作為組建警告](#enabled-rules)。</span><span class="sxs-lookup"><span data-stu-id="b650b-168">In the default analysis mode, only a small number of rules are [enabled as build warnings](#enabled-rules).</span></span> <span data-ttu-id="b650b-169">您可以藉由在專案檔中設定 [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) 屬性，來變更專案的分析模式。</span><span class="sxs-lookup"><span data-stu-id="b650b-169">You can change the analysis mode for your project by setting the [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) property in the project file.</span></span> <span data-ttu-id="b650b-170">允許的值為：</span><span class="sxs-lookup"><span data-stu-id="b650b-170">The allowable values are:</span></span>

| <span data-ttu-id="b650b-171">值</span><span class="sxs-lookup"><span data-stu-id="b650b-171">Value</span></span> | <span data-ttu-id="b650b-172">描述</span><span class="sxs-lookup"><span data-stu-id="b650b-172">Description</span></span> |
| - | - |
| `AllDisabledByDefault` | <span data-ttu-id="b650b-173">這是最保守的模式。</span><span class="sxs-lookup"><span data-stu-id="b650b-173">This is the most conservative mode.</span></span> <span data-ttu-id="b650b-174">預設會停用所有規則。</span><span class="sxs-lookup"><span data-stu-id="b650b-174">All rules are disabled by default.</span></span> <span data-ttu-id="b650b-175">您可以選擇性地 [選擇](configuration-options.md) 加入個別規則來啟用它們。</span><span class="sxs-lookup"><span data-stu-id="b650b-175">You can selectively [opt into](configuration-options.md) individual rules to enable them.</span></span><br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | <span data-ttu-id="b650b-176">這是最積極的模式。</span><span class="sxs-lookup"><span data-stu-id="b650b-176">This is the most aggressive mode.</span></span> <span data-ttu-id="b650b-177">所有規則都會啟用為組建警告。</span><span class="sxs-lookup"><span data-stu-id="b650b-177">All rules are enabled as build warnings.</span></span> <span data-ttu-id="b650b-178">您可以選擇性地 [退出宣告](configuration-options.md) 個別規則來停用它們。</span><span class="sxs-lookup"><span data-stu-id="b650b-178">You can selectively [opt out of](configuration-options.md) individual rules to disable them.</span></span><br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | <span data-ttu-id="b650b-179">預設模式會啟用數個規則做為警告，其他則只會啟用為具有對應程式碼修正的 Visual Studio IDE 建議，其餘部分則會完全停用。</span><span class="sxs-lookup"><span data-stu-id="b650b-179">The default mode, where a handful of rules are enabled as warnings, others are enabled only as Visual Studio IDE suggestions with corresponding code fixes, and the rest are disabled completely.</span></span> <span data-ttu-id="b650b-180">您可以選擇性地 [加入宣告或退出](configuration-options.md) 個別規則來停用它們。</span><span class="sxs-lookup"><span data-stu-id="b650b-180">You can selectively [opt into or out of](configuration-options.md) individual rules to disable them.</span></span><br /><br />`<AnalysisMode>Default</AnalysisMode>` |

<span data-ttu-id="b650b-181">若要尋找每個可用規則的預設嚴重性，以及是否在預設分析模式中啟用規則，請參閱 [完整的規則清單](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)。</span><span class="sxs-lookup"><span data-stu-id="b650b-181">To find the default severity for each available rule and whether or not the rule is enabled in the default analysis mode, see the [full list of rules](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>

### <a name="treat-warnings-as-errors"></a><span data-ttu-id="b650b-182">將警告視為錯誤</span><span class="sxs-lookup"><span data-stu-id="b650b-182">Treat warnings as errors</span></span>

<span data-ttu-id="b650b-183">如果您在 `-warnaserror` 建立專案時使用旗標，則也會將所有程式碼分析警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="b650b-183">If you use the `-warnaserror` flag when you build your projects, all code analysis warnings are also treated as errors.</span></span> <span data-ttu-id="b650b-184">如果您不想要將程式碼品質警告 (CAxxxx) 要被視為存在的錯誤 `-warnaserror` ，您可以 `CodeAnalysisTreatWarningsAsErrors` 在專案檔中將 MSBuild 屬性設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="b650b-184">If you do not want code quality warnings (CAxxxx) to be treated as errors in presence of `-warnaserror`, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="b650b-185">您仍然會看到任何程式碼分析警告，但不會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="b650b-185">You'll still see any code analysis warnings, but they won't break your build.</span></span>

### <a name="latest-updates"></a><span data-ttu-id="b650b-186">最新的更新</span><span class="sxs-lookup"><span data-stu-id="b650b-186">Latest updates</span></span>

<span data-ttu-id="b650b-187">依預設，當您升級至較新版本的 .NET SDK 時，您將會取得最新的程式碼分析規則和預設規則嚴重性。</span><span class="sxs-lookup"><span data-stu-id="b650b-187">By default, you'll get the latest code analysis rules and default rule severities as you upgrade to newer versions of the .NET SDK.</span></span> <span data-ttu-id="b650b-188">如果您不想要此行為，例如，如果您想要確保沒有啟用或停用任何新規則，您可以透過下列其中一種方式來覆寫它：</span><span class="sxs-lookup"><span data-stu-id="b650b-188">If you don't want this behavior, for example, if you want to ensure that no new rules are enabled or disabled, you can override it in one of the following ways:</span></span>

- <span data-ttu-id="b650b-189">將 `AnalysisLevel` MSBuild 屬性設定為特定值，以將警告鎖定至該集合。</span><span class="sxs-lookup"><span data-stu-id="b650b-189">Set the `AnalysisLevel` MSBuild property to a specific value to lock the warnings to that set.</span></span> <span data-ttu-id="b650b-190">當您升級至較新的 SDK 時，仍會收到這些警告的錯誤修正，但不會啟用任何新的警告，也不會停用任何現有的警告。</span><span class="sxs-lookup"><span data-stu-id="b650b-190">When you upgrade to a newer SDK, you'll still get bug fixes for those warnings, but no new warnings will be enabled and no existing warnings will be disabled.</span></span> <span data-ttu-id="b650b-191">例如，若要將規則集鎖定為 .NET SDK 5.0 版隨附的規則，請將下列專案新增至您的專案檔。</span><span class="sxs-lookup"><span data-stu-id="b650b-191">For example, to lock the set of rules to those that ship with version 5.0 of the .NET SDK, add the following entry to your project file.</span></span>

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > <span data-ttu-id="b650b-192">屬性的預設值 `AnalysisLevel` 是 `latest` ，這表示當您移至較新版本的 .net SDK 時，一律會取得最新的程式碼分析規則。</span><span class="sxs-lookup"><span data-stu-id="b650b-192">The default value for the `AnalysisLevel` property is `latest`, which means you always get the latest code analysis rules as you move to newer versions of the .NET SDK.</span></span>

  <span data-ttu-id="b650b-193">如需詳細資訊，以及查看可能值的清單，請參閱 [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)。</span><span class="sxs-lookup"><span data-stu-id="b650b-193">For more information, and to see a list of possible values, see [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel).</span></span>

- <span data-ttu-id="b650b-194">安裝 [CodeAnalysis NetAnalyzers NuGet 套件](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) ，以從 .net SDK 更新分離規則更新。</span><span class="sxs-lookup"><span data-stu-id="b650b-194">Install the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) to decouple rule updates from .NET SDK updates.</span></span> <span data-ttu-id="b650b-195">如果 SDK 包含的分析器元件版本比 NuGet 套件還新，則安裝套件會關閉內建的 SDK 分析器，並產生組建警告。</span><span class="sxs-lookup"><span data-stu-id="b650b-195">Installing the package turns off the built-in SDK analyzers and generates a build warning if the SDK contains a newer analyzer assembly version than that of the NuGet package.</span></span>

## <a name="code-style-analysis"></a><span data-ttu-id="b650b-196">程式碼樣式分析</span><span class="sxs-lookup"><span data-stu-id="b650b-196">Code-style analysis</span></span>

<span data-ttu-id="b650b-197">程式 *代碼樣式分析* ( "IDExxxx" ) 規則可讓您在程式碼基底中定義和維護一致的程式碼樣式。</span><span class="sxs-lookup"><span data-stu-id="b650b-197">*Code-style analysis* ("IDExxxx") rules enable you to define and maintain consistent code style in your codebase.</span></span> <span data-ttu-id="b650b-198">預設啟用設定為：</span><span class="sxs-lookup"><span data-stu-id="b650b-198">The default enablement settings are:</span></span>

- <span data-ttu-id="b650b-199">命令列組建：針對命令列組建上的所有 .NET 專案，預設會停用程式碼樣式分析。</span><span class="sxs-lookup"><span data-stu-id="b650b-199">Command-line build: Code-style analysis is disabled, by default, for all .NET projects on command-line builds.</span></span>

  <span data-ttu-id="b650b-200">從 .NET 5.0 開始，您可以在命令列和 Visual Studio 內 [啟用組建的程式碼樣式分析](#enable-on-build)。</span><span class="sxs-lookup"><span data-stu-id="b650b-200">Starting in .NET 5.0, you can [enable code-style analysis on build](#enable-on-build), both at the command line and inside Visual Studio.</span></span> <span data-ttu-id="b650b-201">程式碼樣式違規會顯示為「IDE」前置詞的警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="b650b-201">Code style violations appear as warnings or errors with an "IDE" prefix.</span></span> <span data-ttu-id="b650b-202">這可讓您在組建階段強制執行一致的程式碼樣式。</span><span class="sxs-lookup"><span data-stu-id="b650b-202">This enables you to enforce consistent code styles at build time.</span></span>

- <span data-ttu-id="b650b-203">Visual Studio：程式碼樣式分析預設會針對 Visual Studio 中的所有 .NET 專案啟用，因為程式 [代碼會重構快速動作](/visualstudio/ide/code-generation-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="b650b-203">Visual Studio: Code-style analysis is enabled, by default, for all .NET projects inside Visual Studio as [code refactoring quick actions](/visualstudio/ide/code-generation-in-visual-studio).</span></span>

<span data-ttu-id="b650b-204">如需程式碼樣式分析規則的完整清單，請參閱程式 [代碼樣式規則](style-rules/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b650b-204">For a full list of code-style analysis rules, see [Code style rules](style-rules/index.md).</span></span>

### <a name="enable-on-build"></a><span data-ttu-id="b650b-205">在組建時啟用</span><span class="sxs-lookup"><span data-stu-id="b650b-205">Enable on build</span></span>

<span data-ttu-id="b650b-206">使用 .NET 5.0 SDK 和更新版本時，您可以在從命令列和 Visual Studio 中建立時啟用程式碼樣式分析。</span><span class="sxs-lookup"><span data-stu-id="b650b-206">With the .NET 5.0 SDK and later versions, you can enable code-style analysis when building from the command-line and in Visual Studio.</span></span> <span data-ttu-id="b650b-207"> (不過，基於效能的考慮， [少數的程式碼樣式規則](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) 仍只適用于 Visual Studio IDE。 ) </span><span class="sxs-lookup"><span data-stu-id="b650b-207">(However, for performance reasons, [a handful of code-style rules](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) will still apply only in the Visual Studio IDE.)</span></span>

<span data-ttu-id="b650b-208">遵循下列步驟來啟用組建的程式碼樣式分析：</span><span class="sxs-lookup"><span data-stu-id="b650b-208">Follow these steps to enable code-style analysis on build:</span></span>

1. <span data-ttu-id="b650b-209">將 MSBuild 屬性 [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) 設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b650b-209">Set the MSBuild property [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) to `true`.</span></span>

1. <span data-ttu-id="b650b-210">在 *editorconfig* 檔案中，將您想要在組建上執行的每個「IDE」程式碼樣式規則 [設定](configuration-options.md) 為警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="b650b-210">In an *.editorconfig* file, [configure](configuration-options.md) each "IDE" code style rule that you wish to run on build as a warning or an error.</span></span> <span data-ttu-id="b650b-211">例如：</span><span class="sxs-lookup"><span data-stu-id="b650b-211">For example:</span></span>

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   <span data-ttu-id="b650b-212">或者，您也可以將整個類別設定為警告或錯誤，依預設，然後選擇性地關閉該類別中不想要在組建上執行的規則。</span><span class="sxs-lookup"><span data-stu-id="b650b-212">Alternatively, you can configure an entire category to be a warning or error, by default, and then selectively turn off rules in that category that you don't want to run on build.</span></span> <span data-ttu-id="b650b-213">例如：</span><span class="sxs-lookup"><span data-stu-id="b650b-213">For example:</span></span>

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

> [!NOTE]
> <span data-ttu-id="b650b-214">程式碼樣式分析功能是實驗性，而且在 .NET 5 和 .NET 6 版本之間可能會變更。</span><span class="sxs-lookup"><span data-stu-id="b650b-214">The code-style analysis feature is experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

## <a name="suppress-a-warning"></a><span data-ttu-id="b650b-215">隱藏警告</span><span class="sxs-lookup"><span data-stu-id="b650b-215">Suppress a warning</span></span>

<span data-ttu-id="b650b-216">若要隱藏規則違規，請在 EditorConfig 檔案中將該規則識別碼的嚴重性選項設定為 `none` 。</span><span class="sxs-lookup"><span data-stu-id="b650b-216">To suppress a rule violation, set the severity option for that rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="b650b-217">例如：</span><span class="sxs-lookup"><span data-stu-id="b650b-217">For example:</span></span>

```ini
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="b650b-218">Visual Studio 提供其他方式來隱藏程式碼分析規則的警告。</span><span class="sxs-lookup"><span data-stu-id="b650b-218">Visual Studio provides additional ways to suppress warnings from code analysis rules.</span></span> <span data-ttu-id="b650b-219">如需詳細資訊，請參閱 [隱藏違規](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)。</span><span class="sxs-lookup"><span data-stu-id="b650b-219">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span></span>

<span data-ttu-id="b650b-220">如需有關規則嚴重性的詳細資訊，請參閱 [設定規則嚴重性](configuration-options.md#severity-level)。</span><span class="sxs-lookup"><span data-stu-id="b650b-220">For more information about rule severities, see [Configure rule severity](configuration-options.md#severity-level).</span></span>

## <a name="third-party-analyzers"></a><span data-ttu-id="b650b-221">第三方分析器</span><span class="sxs-lookup"><span data-stu-id="b650b-221">Third-party analyzers</span></span>

<span data-ttu-id="b650b-222">除了正式的 .NET 分析器，您也可以安裝協力廠商分析器，例如 [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [XUnit 分析器](https://www.nuget.org/packages/xunit.analyzers/)和 [聲納 Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)。</span><span class="sxs-lookup"><span data-stu-id="b650b-222">In addition to the official .NET analyzers, you can also install third party analyzers, such as [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), and [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).</span></span>

## <a name="see-also"></a><span data-ttu-id="b650b-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b650b-223">See also</span></span>

- [<span data-ttu-id="b650b-224">程式碼品質分析規則參考</span><span class="sxs-lookup"><span data-stu-id="b650b-224">Code quality analysis rule reference</span></span>](quality-rules/index.md)
- [<span data-ttu-id="b650b-225">程式碼樣式分析規則參考</span><span class="sxs-lookup"><span data-stu-id="b650b-225">Code style analysis rule reference</span></span>](style-rules/index.md)
- [<span data-ttu-id="b650b-226">Visual Studio 中的程式碼分析</span><span class="sxs-lookup"><span data-stu-id="b650b-226">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="b650b-227">.NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="b650b-227">.NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="b650b-228">教學課程：撰寫您的第一個分析器和程式碼修正</span><span class="sxs-lookup"><span data-stu-id="b650b-228">Tutorial: Write your first analyzer and code fix</span></span>](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
