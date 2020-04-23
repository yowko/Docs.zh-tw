---
title: C# 語言版本控制 - C# 指南
description: 瞭解如何根據項目確定 C# 語言版本以及該選擇背後的原因。 瞭解如何手動覆蓋預設值。
ms.date: 02/21/2020
ms.openlocfilehash: 850c4a860878593d80aaa3b7b38efaff9e003f43
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102654"
---
# <a name="c-language-versioning"></a><span data-ttu-id="7b45c-104">C# 語言版本控制</span><span class="sxs-lookup"><span data-stu-id="7b45c-104">C# language versioning</span></span>

<span data-ttu-id="7b45c-105">最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。</span><span class="sxs-lookup"><span data-stu-id="7b45c-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="7b45c-106">Visual Studio 不提供更改值的 UI,但您可以通過編輯*csproj*檔來更改該值。</span><span class="sxs-lookup"><span data-stu-id="7b45c-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="7b45c-107">選擇預設值可確保使用與目標框架相容的最新語言版本。</span><span class="sxs-lookup"><span data-stu-id="7b45c-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="7b45c-108">您可以造訪與項目目標相容的最新語言功能。</span><span class="sxs-lookup"><span data-stu-id="7b45c-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="7b45c-109">此預設選擇還可確保不使用需要目標框架中不可用的類型或運行時行為的語言。</span><span class="sxs-lookup"><span data-stu-id="7b45c-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="7b45c-110">選擇比預設值更新的語言版本可能會導致難以診斷編譯時間和運行時錯誤。</span><span class="sxs-lookup"><span data-stu-id="7b45c-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="7b45c-111">本文中的規則適用於使用 Visual Studio 2019 或 .NET Core 3.0 SDK 提供的編譯器。</span><span class="sxs-lookup"><span data-stu-id="7b45c-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="7b45c-112">屬於 Visual Studio 2017 安裝或舊版 .NET Core SDK 一部分的 C# 編譯器預設會以 C# 7.0 為目標。</span><span class="sxs-lookup"><span data-stu-id="7b45c-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="7b45c-113">C# 8.0(更高版本)僅在 .NET Core 3.x 和較新版本上受支援。</span><span class="sxs-lookup"><span data-stu-id="7b45c-113">C# 8.0 (and higher) is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="7b45c-114">許多最新的功能需要 .NET Core 3.x 中引入的庫和運行時功能:</span><span class="sxs-lookup"><span data-stu-id="7b45c-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="7b45c-115">默認介面成員實現需要 .NET Core 3.0 CLR 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="7b45c-115">Default interface member implementation requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="7b45c-116">非同步需要新類型<xref:System.IAsyncDisposable?displayProperty=nameWithType>,<xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType><xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>與 。</span><span class="sxs-lookup"><span data-stu-id="7b45c-116">Async streams require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="7b45c-117">索引和範圍需要新類型<xref:System.Index?displayProperty=nameWithType>和<xref:System.Range?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7b45c-117">Indexes and Ranges require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="7b45c-118">空引用類型使用多個[屬性](attributes/nullable-analysis.md)來提供更好的警告。</span><span class="sxs-lookup"><span data-stu-id="7b45c-118">Nullable reference types make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="7b45c-119">這些屬性在 .NET Core 3.0 中添加。</span><span class="sxs-lookup"><span data-stu-id="7b45c-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="7b45c-120">其他目標框架尚未使用任何這些屬性進行批文。</span><span class="sxs-lookup"><span data-stu-id="7b45c-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="7b45c-121">這意味著無效警告可能無法準確反映潛在問題。</span><span class="sxs-lookup"><span data-stu-id="7b45c-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

## <a name="defaults"></a><span data-ttu-id="7b45c-122">Defaults</span><span class="sxs-lookup"><span data-stu-id="7b45c-122">Defaults</span></span>

<span data-ttu-id="7b45c-123">編譯器會根據下列規則決定預設值：</span><span class="sxs-lookup"><span data-stu-id="7b45c-123">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="7b45c-124">目標架構</span><span class="sxs-lookup"><span data-stu-id="7b45c-124">Target framework</span></span>|<span data-ttu-id="7b45c-125">version</span><span class="sxs-lookup"><span data-stu-id="7b45c-125">version</span></span>|<span data-ttu-id="7b45c-126">C# 語言版本預設值</span><span class="sxs-lookup"><span data-stu-id="7b45c-126">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="7b45c-127">.NET Core</span><span class="sxs-lookup"><span data-stu-id="7b45c-127">.NET Core</span></span>|<span data-ttu-id="7b45c-128">3.x</span><span class="sxs-lookup"><span data-stu-id="7b45c-128">3.x</span></span>|<span data-ttu-id="7b45c-129">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="7b45c-129">C# 8.0</span></span>|
|<span data-ttu-id="7b45c-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="7b45c-130">.NET Core</span></span>|<span data-ttu-id="7b45c-131">2.x</span><span class="sxs-lookup"><span data-stu-id="7b45c-131">2.x</span></span>|<span data-ttu-id="7b45c-132">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="7b45c-132">C# 7.3</span></span>|
|<span data-ttu-id="7b45c-133">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7b45c-133">.NET Standard</span></span>|<span data-ttu-id="7b45c-134">2.1</span><span class="sxs-lookup"><span data-stu-id="7b45c-134">2.1</span></span>|<span data-ttu-id="7b45c-135">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="7b45c-135">C# 8.0</span></span>|
|<span data-ttu-id="7b45c-136">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7b45c-136">.NET Standard</span></span>|<span data-ttu-id="7b45c-137">2.0</span><span class="sxs-lookup"><span data-stu-id="7b45c-137">2.0</span></span>|<span data-ttu-id="7b45c-138">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="7b45c-138">C# 7.3</span></span>|
|<span data-ttu-id="7b45c-139">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7b45c-139">.NET Standard</span></span>|<span data-ttu-id="7b45c-140">1.x</span><span class="sxs-lookup"><span data-stu-id="7b45c-140">1.x</span></span>|<span data-ttu-id="7b45c-141">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="7b45c-141">C# 7.3</span></span>|
|<span data-ttu-id="7b45c-142">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b45c-142">.NET Framework</span></span>|<span data-ttu-id="7b45c-143">all</span><span class="sxs-lookup"><span data-stu-id="7b45c-143">all</span></span>|<span data-ttu-id="7b45c-144">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="7b45c-144">C# 7.3</span></span>|

<span data-ttu-id="7b45c-145">當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。</span><span class="sxs-lookup"><span data-stu-id="7b45c-145">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="7b45c-146">您可以在任何環境中將最新的功能與預覽一起使用,而不會影響針對已發佈的 .NET Core 版本的專案。</span><span class="sxs-lookup"><span data-stu-id="7b45c-146">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="7b45c-147">覆寫預設</span><span class="sxs-lookup"><span data-stu-id="7b45c-147">Override a default</span></span>

<span data-ttu-id="7b45c-148">如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：</span><span class="sxs-lookup"><span data-stu-id="7b45c-148">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="7b45c-149">手動編輯您的[專案檔](#edit-the-project-file)。</span><span class="sxs-lookup"><span data-stu-id="7b45c-149">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="7b45c-150">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="7b45c-150">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="7b45c-151">設定[`-langversion`編譯器選項](compiler-options/langversion-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="7b45c-151">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="7b45c-152">編輯專案檔</span><span class="sxs-lookup"><span data-stu-id="7b45c-152">Edit the project file</span></span>

<span data-ttu-id="7b45c-153">您可以在專案檔中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="7b45c-153">You can set the language version in your project file.</span></span> <span data-ttu-id="7b45c-154">例如，如果您明確希望存取預覽功能，您可以新增如下元素：</span><span class="sxs-lookup"><span data-stu-id="7b45c-154">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="7b45c-155">`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。</span><span class="sxs-lookup"><span data-stu-id="7b45c-155">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="7b45c-156">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="7b45c-156">Configure multiple projects</span></span>

<span data-ttu-id="7b45c-157">要設定多個專案,您可以創建包含該元素的`<LangVersion>` **Directory.Build.props**檔。</span><span class="sxs-lookup"><span data-stu-id="7b45c-157">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="7b45c-158">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="7b45c-158">You typically do that in your solution directory.</span></span> <span data-ttu-id="7b45c-159">將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="7b45c-159">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="7b45c-160">包含該檔的目錄的所有子目錄中的生成將使用預覽 C# 版本。</span><span class="sxs-lookup"><span data-stu-id="7b45c-160">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="7b45c-161">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="7b45c-161">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="7b45c-162">C# 語言版本參考</span><span class="sxs-lookup"><span data-stu-id="7b45c-162">C# language version reference</span></span>

<span data-ttu-id="7b45c-163">下表顯示所有目前的 C# 語言版本。</span><span class="sxs-lookup"><span data-stu-id="7b45c-163">The following table shows all current C# language versions.</span></span> <span data-ttu-id="7b45c-164">如果編譯器較舊,則不一定瞭解每個值。</span><span class="sxs-lookup"><span data-stu-id="7b45c-164">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="7b45c-165">如果安裝 .NET Core 3.0 或更高版本,則可以訪問列出的所有內容。</span><span class="sxs-lookup"><span data-stu-id="7b45c-165">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

|<span data-ttu-id="7b45c-166">值</span><span class="sxs-lookup"><span data-stu-id="7b45c-166">Value</span></span>|<span data-ttu-id="7b45c-167">意義</span><span class="sxs-lookup"><span data-stu-id="7b45c-167">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="7b45c-168">preview</span><span class="sxs-lookup"><span data-stu-id="7b45c-168">preview</span></span>|<span data-ttu-id="7b45c-169">編譯器會接受最新預覽版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-169">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="7b45c-170">最新</span><span class="sxs-lookup"><span data-stu-id="7b45c-170">latest</span></span>|<span data-ttu-id="7b45c-171">編譯器會接受編譯器最新已發行版本 (包括次要版本) 的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-171">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="7b45c-172">latestMajor</span><span class="sxs-lookup"><span data-stu-id="7b45c-172">latestMajor</span></span>|<span data-ttu-id="7b45c-173">編譯器會接受編譯器最新已發行主要版本的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-173">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="7b45c-174">8.0</span><span class="sxs-lookup"><span data-stu-id="7b45c-174">8.0</span></span>|<span data-ttu-id="7b45c-175">編譯器只會接受 C# 8.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-175">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="7b45c-176">7.3</span><span class="sxs-lookup"><span data-stu-id="7b45c-176">7.3</span></span>|<span data-ttu-id="7b45c-177">編譯器只會接受 C# 7.3 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-177">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="7b45c-178">7.2</span><span class="sxs-lookup"><span data-stu-id="7b45c-178">7.2</span></span>|<span data-ttu-id="7b45c-179">編譯器只會接受 C# 7.2 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-179">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="7b45c-180">7.1</span><span class="sxs-lookup"><span data-stu-id="7b45c-180">7.1</span></span>|<span data-ttu-id="7b45c-181">編譯器只會接受 C# 7.1 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-181">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="7b45c-182">7</span><span class="sxs-lookup"><span data-stu-id="7b45c-182">7</span></span>|<span data-ttu-id="7b45c-183">編譯器只會接受 C# 7.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-183">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="7b45c-184">6</span><span class="sxs-lookup"><span data-stu-id="7b45c-184">6</span></span>|<span data-ttu-id="7b45c-185">編譯器只會接受 C# 6.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-185">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="7b45c-186">5</span><span class="sxs-lookup"><span data-stu-id="7b45c-186">5</span></span>|<span data-ttu-id="7b45c-187">編譯器只會接受 C# 5.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-187">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="7b45c-188">4</span><span class="sxs-lookup"><span data-stu-id="7b45c-188">4</span></span>|<span data-ttu-id="7b45c-189">編譯器只會接受 C# 4.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-189">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="7b45c-190">3</span><span class="sxs-lookup"><span data-stu-id="7b45c-190">3</span></span>|<span data-ttu-id="7b45c-191">編譯器只會接受 C# 3.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-191">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="7b45c-192">ISO-2</span><span class="sxs-lookup"><span data-stu-id="7b45c-192">ISO-2</span></span>|<span data-ttu-id="7b45c-193">編譯器僅接受 ISO/IEC 23270:2006 C# (2.0) 中包含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-193">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0).</span></span> |
|<span data-ttu-id="7b45c-194">ISO-1</span><span class="sxs-lookup"><span data-stu-id="7b45c-194">ISO-1</span></span>|<span data-ttu-id="7b45c-195">編譯器僅接受 ISO/IEC 23270:2003 C# (1.0/1.2) 中包含的語法。</span><span class="sxs-lookup"><span data-stu-id="7b45c-195">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2).</span></span> |
