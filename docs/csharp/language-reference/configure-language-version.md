---
title: C# 語言版本控制 - C# 指南
description: '瞭解如何根據您的專案以及該選項背後的原因來決定 c # 語言版本。 瞭解如何手動覆寫預設值。'
ms.custom: updateeachrelease
ms.date: 05/20/2020
ms.openlocfilehash: a27f3210f399f1bed190c18d778cf3824772d576
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656846"
---
# <a name="c-language-versioning"></a><span data-ttu-id="5d8a7-104">C# 語言版本控制</span><span class="sxs-lookup"><span data-stu-id="5d8a7-104">C# language versioning</span></span>

<span data-ttu-id="5d8a7-105">最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="5d8a7-106">Visual Studio 不會提供 UI 來變更值，但您可以編輯 *.csproj* 檔案來變更該值。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="5d8a7-107">選擇預設值可確保您使用與目標 framework 相容的最新語言版本。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="5d8a7-108">您可以從與專案目標相容的最新語言功能存取中獲益。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="5d8a7-109">此預設選項也可確保您不會使用需要類型或執行時間行為的語言，而無法在您的目標 framework 中使用。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="5d8a7-110">選擇比預設版本新的語言版本，可能會導致難以診斷編譯時期和執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="5d8a7-111">本文中的規則適用于使用 Visual Studio 2019 或 .NET Core 3.0 SDK 提供的編譯器。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="5d8a7-112">屬於 Visual Studio 2017 安裝或舊版 .NET Core SDK 一部分的 C# 編譯器預設會以 C# 7.0 為目標。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="5d8a7-113">只有 .NET Core 3.x 和更新版本才支援 c # 8.0 (和更高版本的) 。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-113">C# 8.0 (and higher) is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="5d8a7-114">許多最新功能都需要 .NET Core 3.x 所引進的程式庫和執行時間功能：</span><span class="sxs-lookup"><span data-stu-id="5d8a7-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="5d8a7-115">[預設介面執行](../whats-new/csharp-8.md#default-interface-methods) 需要 .net CORE 3.0 CLR 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="5d8a7-116">[非同步資料流程](../whats-new/csharp-8.md#asynchronous-streams) 需要新的類型 <xref:System.IAsyncDisposable?displayProperty=nameWithType> 、 <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="5d8a7-117">[索引和範圍](../whats-new/csharp-8.md#indices-and-ranges) 需要新的類型 <xref:System.Index?displayProperty=nameWithType> 和 <xref:System.Range?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="5d8a7-118">[可為 null 的參考型別](../whats-new/csharp-8.md#nullable-reference-types) 會使用數個 [屬性](attributes/nullable-analysis.md) ，以提供更好的警告。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="5d8a7-119">這些屬性已在 .NET Core 3.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="5d8a7-120">其他目標 framework 尚未以上述任何屬性標注。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="5d8a7-121">這表示可為 null 的警告可能無法精確反映潛在問題。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

## <a name="defaults"></a><span data-ttu-id="5d8a7-122">Defaults</span><span class="sxs-lookup"><span data-stu-id="5d8a7-122">Defaults</span></span>

<span data-ttu-id="5d8a7-123">編譯器會根據下列規則決定預設值：</span><span class="sxs-lookup"><span data-stu-id="5d8a7-123">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="5d8a7-124">目標架構</span><span class="sxs-lookup"><span data-stu-id="5d8a7-124">Target framework</span></span> | <span data-ttu-id="5d8a7-125">version</span><span class="sxs-lookup"><span data-stu-id="5d8a7-125">version</span></span> | <span data-ttu-id="5d8a7-126">C# 語言版本預設值</span><span class="sxs-lookup"><span data-stu-id="5d8a7-126">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="5d8a7-127">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5d8a7-127">.NET Core</span></span>        | <span data-ttu-id="5d8a7-128">3.x</span><span class="sxs-lookup"><span data-stu-id="5d8a7-128">3.x</span></span>     | <span data-ttu-id="5d8a7-129">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="5d8a7-129">C# 8.0</span></span>                      |
| <span data-ttu-id="5d8a7-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5d8a7-130">.NET Core</span></span>        | <span data-ttu-id="5d8a7-131">2.x</span><span class="sxs-lookup"><span data-stu-id="5d8a7-131">2.x</span></span>     | <span data-ttu-id="5d8a7-132">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="5d8a7-132">C# 7.3</span></span>                      |
| <span data-ttu-id="5d8a7-133">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="5d8a7-133">.NET Standard</span></span>    | <span data-ttu-id="5d8a7-134">2.1</span><span class="sxs-lookup"><span data-stu-id="5d8a7-134">2.1</span></span>     | <span data-ttu-id="5d8a7-135">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="5d8a7-135">C# 8.0</span></span>                      |
| <span data-ttu-id="5d8a7-136">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="5d8a7-136">.NET Standard</span></span>    | <span data-ttu-id="5d8a7-137">2.0</span><span class="sxs-lookup"><span data-stu-id="5d8a7-137">2.0</span></span>     | <span data-ttu-id="5d8a7-138">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="5d8a7-138">C# 7.3</span></span>                      |
| <span data-ttu-id="5d8a7-139">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="5d8a7-139">.NET Standard</span></span>    | <span data-ttu-id="5d8a7-140">1.x</span><span class="sxs-lookup"><span data-stu-id="5d8a7-140">1.x</span></span>     | <span data-ttu-id="5d8a7-141">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="5d8a7-141">C# 7.3</span></span>                      |
| <span data-ttu-id="5d8a7-142">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d8a7-142">.NET Framework</span></span>   | <span data-ttu-id="5d8a7-143">all</span><span class="sxs-lookup"><span data-stu-id="5d8a7-143">all</span></span>     | <span data-ttu-id="5d8a7-144">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="5d8a7-144">C# 7.3</span></span>                      |

<span data-ttu-id="5d8a7-145">當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-145">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="5d8a7-146">您可以在任何環境中使用該預覽版的最新功能，而不會影響以發行之 .NET Core 版本為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-146">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="5d8a7-147">覆寫預設</span><span class="sxs-lookup"><span data-stu-id="5d8a7-147">Override a default</span></span>

<span data-ttu-id="5d8a7-148">如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：</span><span class="sxs-lookup"><span data-stu-id="5d8a7-148">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="5d8a7-149">手動編輯您的[專案檔](#edit-the-project-file)。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-149">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="5d8a7-150">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-150">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="5d8a7-151">設定[ `-langversion` 編譯器選項](compiler-options/langversion-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-151">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="5d8a7-152">編輯專案檔</span><span class="sxs-lookup"><span data-stu-id="5d8a7-152">Edit the project file</span></span>

<span data-ttu-id="5d8a7-153">您可以在專案檔中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-153">You can set the language version in your project file.</span></span> <span data-ttu-id="5d8a7-154">例如，如果您明確希望存取預覽功能，您可以新增如下元素：</span><span class="sxs-lookup"><span data-stu-id="5d8a7-154">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="5d8a7-155">`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-155">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="5d8a7-156">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="5d8a7-156">Configure multiple projects</span></span>

<span data-ttu-id="5d8a7-157">若要設定多個專案，您可以建立包含元素的 **.props**檔案。 `<LangVersion>`</span><span class="sxs-lookup"><span data-stu-id="5d8a7-157">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="5d8a7-158">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-158">You typically do that in your solution directory.</span></span> <span data-ttu-id="5d8a7-159">將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="5d8a7-159">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="5d8a7-160">在包含該檔案之目錄的所有子目錄中建立的組建都會使用 preview c # 版本。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-160">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="5d8a7-161">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-161">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="5d8a7-162">C# 語言版本參考</span><span class="sxs-lookup"><span data-stu-id="5d8a7-162">C# language version reference</span></span>

<span data-ttu-id="5d8a7-163">下表顯示所有目前的 C# 語言版本。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-163">The following table shows all current C# language versions.</span></span> <span data-ttu-id="5d8a7-164">如果您的編譯器較舊，您的編譯器可能不一定會瞭解每一個值。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-164">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="5d8a7-165">如果您安裝的是 .NET Core 3.0 或更新版本，則可以存取所列的所有專案。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-165">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="5d8a7-166">開啟 [Visual Studio 的開發人員命令提示字元](../../framework/tools/developer-command-prompt-for-vs.md)，然後執行下列命令，以查看您電腦上可用的語言版本清單。</span><span class="sxs-lookup"><span data-stu-id="5d8a7-166">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="5d8a7-167">質疑這類 [langversion](compiler-options/langversion-compiler-option.md) 編譯選項，將會列印如下所示的內容：</span><span class="sxs-lookup"><span data-stu-id="5d8a7-167">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
