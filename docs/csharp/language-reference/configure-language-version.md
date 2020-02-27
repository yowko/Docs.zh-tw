---
title: C# 語言版本控制 - C# 指南
description: 瞭解如何根據您C#的專案以及該選擇背後的原因來決定語言版本。 瞭解如何手動覆寫預設值。
ms.date: 02/21/2020
ms.openlocfilehash: 2be76fdac471a7175b661d896b0da2910b3609f3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626760"
---
# <a name="c-language-versioning"></a><span data-ttu-id="7a4bb-104">C# 語言版本控制</span><span class="sxs-lookup"><span data-stu-id="7a4bb-104">C# language versioning</span></span>

<span data-ttu-id="7a4bb-105">最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="7a4bb-106">Visual Studio 不會提供變更值的 UI，但是您可以藉由編輯 *.csproj*檔案來變更它。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="7a4bb-107">選擇預設值可確保您使用的是與目標 framework 相容的最新語言版本。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="7a4bb-108">您可以從存取與您專案的目標相容的最新語言功能中獲益。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="7a4bb-109">此預設選項也可確保您不會使用需要在目標 framework 中提供之類型或執行時間行為的語言。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="7a4bb-110">選擇比預設值新的語言版本可能會導致難以診斷編譯時期和執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="7a4bb-111">C#8.0 （和更新版本）僅在 .NET Core 3.x 和較新版本上受到支援。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-111">C# 8.0 (and higher) is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="7a4bb-112">許多最新的功能都需要 .NET Core 3.x 中引進的程式庫和執行時間功能：</span><span class="sxs-lookup"><span data-stu-id="7a4bb-112">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="7a4bb-113">預設介面成員執行需要 .NET Core 3.0 CLR 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-113">Default interface member implementation requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="7a4bb-114">非同步資料流程需要新的類型 <xref:System.IAsyncDisposable?displayProperty=nameWithType>、<xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>和 <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-114">Async streams require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="7a4bb-115">索引和範圍需要新的類型 <xref:System.Index?displayProperty=nameWithType> 和 <xref:System.Range?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-115">Indexes and Ranges require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="7a4bb-116">可為 null 的參考型別利用數個[屬性](../nullable-attributes.md)來提供更好的警告。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-116">Nullable reference types make use of several [attributes](../nullable-attributes.md) to provide better warnings.</span></span> <span data-ttu-id="7a4bb-117">這些屬性是在 .NET Core 3.0 中新增的。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-117">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="7a4bb-118">其他目標架構尚未使用上述任何屬性來標注。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-118">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="7a4bb-119">這表示可為 null 的警告可能無法正確反映潛在的問題。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-119">That means nullable warnings may not accurately reflect potential issues.</span></span>

## <a name="defaults"></a><span data-ttu-id="7a4bb-120">Defaults</span><span class="sxs-lookup"><span data-stu-id="7a4bb-120">Defaults</span></span>

<span data-ttu-id="7a4bb-121">編譯器會根據下列規則決定預設值：</span><span class="sxs-lookup"><span data-stu-id="7a4bb-121">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="7a4bb-122">目標 Framework</span><span class="sxs-lookup"><span data-stu-id="7a4bb-122">Target framework</span></span>|<span data-ttu-id="7a4bb-123">version</span><span class="sxs-lookup"><span data-stu-id="7a4bb-123">version</span></span>|<span data-ttu-id="7a4bb-124">C# 語言版本預設值</span><span class="sxs-lookup"><span data-stu-id="7a4bb-124">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="7a4bb-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="7a4bb-125">.NET Core</span></span>|<span data-ttu-id="7a4bb-126">3.x</span><span class="sxs-lookup"><span data-stu-id="7a4bb-126">3.x</span></span>|<span data-ttu-id="7a4bb-127">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="7a4bb-127">C# 8.0</span></span>|
|<span data-ttu-id="7a4bb-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="7a4bb-128">.NET Core</span></span>|<span data-ttu-id="7a4bb-129">2.x</span><span class="sxs-lookup"><span data-stu-id="7a4bb-129">2.x</span></span>|<span data-ttu-id="7a4bb-130">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="7a4bb-130">C# 7.3</span></span>|
|<span data-ttu-id="7a4bb-131">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7a4bb-131">.NET Standard</span></span>|<span data-ttu-id="7a4bb-132">2.1</span><span class="sxs-lookup"><span data-stu-id="7a4bb-132">2.1</span></span>|<span data-ttu-id="7a4bb-133">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="7a4bb-133">C# 8.0</span></span>|
|<span data-ttu-id="7a4bb-134">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7a4bb-134">.NET Standard</span></span>|<span data-ttu-id="7a4bb-135">2.0</span><span class="sxs-lookup"><span data-stu-id="7a4bb-135">2.0</span></span>|<span data-ttu-id="7a4bb-136">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="7a4bb-136">C# 7.3</span></span>|
|<span data-ttu-id="7a4bb-137">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7a4bb-137">.NET Standard</span></span>|<span data-ttu-id="7a4bb-138">1.x</span><span class="sxs-lookup"><span data-stu-id="7a4bb-138">1.x</span></span>|<span data-ttu-id="7a4bb-139">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="7a4bb-139">C# 7.3</span></span>|
|<span data-ttu-id="7a4bb-140">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7a4bb-140">.NET Framework</span></span>|<span data-ttu-id="7a4bb-141">all</span><span class="sxs-lookup"><span data-stu-id="7a4bb-141">all</span></span>|<span data-ttu-id="7a4bb-142">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="7a4bb-142">C# 7.3</span></span>|

<span data-ttu-id="7a4bb-143">當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-143">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="7a4bb-144">您可在任何環境中使用該預覽的最新功能，而不會影響以發行的 .NET Core 版本為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-144">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="7a4bb-145">覆寫預設</span><span class="sxs-lookup"><span data-stu-id="7a4bb-145">Override a default</span></span>

<span data-ttu-id="7a4bb-146">如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：</span><span class="sxs-lookup"><span data-stu-id="7a4bb-146">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="7a4bb-147">手動編輯您的[專案檔](#edit-the-project-file)。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-147">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="7a4bb-148">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-148">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="7a4bb-149">設定 [`-langversion`編譯器選項](compiler-options/langversion-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-149">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="7a4bb-150">編輯專案檔</span><span class="sxs-lookup"><span data-stu-id="7a4bb-150">Edit the project file</span></span>

<span data-ttu-id="7a4bb-151">您可以在專案檔中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-151">You can set the language version in your project file.</span></span> <span data-ttu-id="7a4bb-152">例如，如果您明確希望存取預覽功能，您可以新增如下元素：</span><span class="sxs-lookup"><span data-stu-id="7a4bb-152">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="7a4bb-153">`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-153">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="7a4bb-154">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="7a4bb-154">Configure multiple projects</span></span>

<span data-ttu-id="7a4bb-155">若要設定多個專案，您可以建立包含 `<LangVersion>` 元素的 **.props**檔案。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-155">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="7a4bb-156">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-156">You typically do that in your solution directory.</span></span> <span data-ttu-id="7a4bb-157">將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="7a4bb-157">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="7a4bb-158">包含該檔案之目錄的所有子目錄中的組建都會使用預覽C#版本。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-158">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="7a4bb-159">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-159">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="7a4bb-160">C# 語言版本參考</span><span class="sxs-lookup"><span data-stu-id="7a4bb-160">C# language version reference</span></span>

<span data-ttu-id="7a4bb-161">下表顯示所有目前的 C# 語言版本。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-161">The following table shows all current C# language versions.</span></span> <span data-ttu-id="7a4bb-162">如果您的編譯器較舊，可能不一定要瞭解每個值。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-162">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="7a4bb-163">如果您安裝 .NET Core 3.0 或更新版本，則可以存取列出的所有專案。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-163">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

|<span data-ttu-id="7a4bb-164">值</span><span class="sxs-lookup"><span data-stu-id="7a4bb-164">Value</span></span>|<span data-ttu-id="7a4bb-165">意義</span><span class="sxs-lookup"><span data-stu-id="7a4bb-165">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="7a4bb-166">preview</span><span class="sxs-lookup"><span data-stu-id="7a4bb-166">preview</span></span>|<span data-ttu-id="7a4bb-167">編譯器會接受最新預覽版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-167">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="7a4bb-168">最新</span><span class="sxs-lookup"><span data-stu-id="7a4bb-168">latest</span></span>|<span data-ttu-id="7a4bb-169">編譯器會接受編譯器最新已發行版本 (包括次要版本) 的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-169">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="7a4bb-170">latestMajor</span><span class="sxs-lookup"><span data-stu-id="7a4bb-170">latestMajor</span></span>|<span data-ttu-id="7a4bb-171">編譯器會接受編譯器最新已發行主要版本的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-171">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="7a4bb-172">8.0</span><span class="sxs-lookup"><span data-stu-id="7a4bb-172">8.0</span></span>|<span data-ttu-id="7a4bb-173">編譯器只會接受 C# 8.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-173">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="7a4bb-174">7.3</span><span class="sxs-lookup"><span data-stu-id="7a4bb-174">7.3</span></span>|<span data-ttu-id="7a4bb-175">編譯器只會接受 C# 7.3 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-175">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="7a4bb-176">7.2</span><span class="sxs-lookup"><span data-stu-id="7a4bb-176">7.2</span></span>|<span data-ttu-id="7a4bb-177">編譯器只會接受 C# 7.2 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-177">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="7a4bb-178">7.1</span><span class="sxs-lookup"><span data-stu-id="7a4bb-178">7.1</span></span>|<span data-ttu-id="7a4bb-179">編譯器只會接受 C# 7.1 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-179">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="7a4bb-180">7</span><span class="sxs-lookup"><span data-stu-id="7a4bb-180">7</span></span>|<span data-ttu-id="7a4bb-181">編譯器只會接受 C# 7.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-181">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="7a4bb-182">6</span><span class="sxs-lookup"><span data-stu-id="7a4bb-182">6</span></span>|<span data-ttu-id="7a4bb-183">編譯器只會接受 C# 6.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-183">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="7a4bb-184">5</span><span class="sxs-lookup"><span data-stu-id="7a4bb-184">5</span></span>|<span data-ttu-id="7a4bb-185">編譯器只會接受 C# 5.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-185">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="7a4bb-186">4</span><span class="sxs-lookup"><span data-stu-id="7a4bb-186">4</span></span>|<span data-ttu-id="7a4bb-187">編譯器只會接受 C# 4.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-187">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="7a4bb-188">3</span><span class="sxs-lookup"><span data-stu-id="7a4bb-188">3</span></span>|<span data-ttu-id="7a4bb-189">編譯器只會接受 C# 3.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-189">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="7a4bb-190">ISO-2</span><span class="sxs-lookup"><span data-stu-id="7a4bb-190">ISO-2</span></span>|<span data-ttu-id="7a4bb-191">編譯器只會接受 ISO/IEC 23270:2006 C# （2.0）中所包含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-191">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0).</span></span> |
|<span data-ttu-id="7a4bb-192">ISO-1</span><span class="sxs-lookup"><span data-stu-id="7a4bb-192">ISO-1</span></span>|<span data-ttu-id="7a4bb-193">編譯器只會接受 ISO/IEC 23270:2003 C# （1.0/1.2）中所包含的語法。</span><span class="sxs-lookup"><span data-stu-id="7a4bb-193">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2).</span></span> |
