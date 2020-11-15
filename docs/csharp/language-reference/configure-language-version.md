---
title: C# 語言版本控制 - C# 指南
description: '瞭解如何根據您的專案以及該選項背後的原因來決定 c # 語言版本。 瞭解如何手動覆寫預設值。'
ms.custom: updateeachrelease
ms.date: 08/11/2020
ms.openlocfilehash: a06aa8812dad6f4b9a9254eef9f7c678c22af860
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634493"
---
# <a name="c-language-versioning"></a><span data-ttu-id="41292-104">C# 語言版本控制</span><span class="sxs-lookup"><span data-stu-id="41292-104">C# language versioning</span></span>

<span data-ttu-id="41292-105">最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。</span><span class="sxs-lookup"><span data-stu-id="41292-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="41292-106">Visual Studio 不會提供 UI 來變更值，但您可以編輯 *.csproj* 檔案來變更該值。</span><span class="sxs-lookup"><span data-stu-id="41292-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="41292-107">選擇預設值可確保您使用與目標 framework 相容的最新語言版本。</span><span class="sxs-lookup"><span data-stu-id="41292-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="41292-108">您可以從與專案目標相容的最新語言功能存取中獲益。</span><span class="sxs-lookup"><span data-stu-id="41292-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="41292-109">此預設選項也可確保您不會使用需要類型或執行時間行為的語言，而無法在您的目標 framework 中使用。</span><span class="sxs-lookup"><span data-stu-id="41292-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="41292-110">選擇比預設版本新的語言版本，可能會導致難以診斷編譯時期和執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="41292-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="41292-111">本文中的規則適用于使用 Visual Studio 2019 或 .NET SDK 提供的編譯器。</span><span class="sxs-lookup"><span data-stu-id="41292-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET SDK.</span></span> <span data-ttu-id="41292-112">屬於 Visual Studio 2017 安裝或舊版 .NET Core SDK 一部分的 C# 編譯器預設會以 C# 7.0 為目標。</span><span class="sxs-lookup"><span data-stu-id="41292-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="41292-113">只有 .NET Core 3.x 和更新版本才支援 c # 8.0。</span><span class="sxs-lookup"><span data-stu-id="41292-113">C# 8.0 is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="41292-114">許多最新功能都需要 .NET Core 3.x 所引進的程式庫和執行時間功能：</span><span class="sxs-lookup"><span data-stu-id="41292-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="41292-115">[預設介面執行](../whats-new/csharp-8.md#default-interface-methods) 需要 .net CORE 3.0 CLR 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="41292-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="41292-116">[非同步資料流程](../whats-new/csharp-8.md#asynchronous-streams) 需要新的類型 <xref:System.IAsyncDisposable?displayProperty=nameWithType> 、 <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="41292-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="41292-117">[索引和範圍](../whats-new/csharp-8.md#indices-and-ranges) 需要新的類型 <xref:System.Index?displayProperty=nameWithType> 和 <xref:System.Range?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="41292-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="41292-118">[可為 null 的參考型別](../whats-new/csharp-8.md#nullable-reference-types) 會使用數個 [屬性](attributes/nullable-analysis.md) ，以提供更好的警告。</span><span class="sxs-lookup"><span data-stu-id="41292-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="41292-119">這些屬性已在 .NET Core 3.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="41292-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="41292-120">其他目標 framework 尚未以上述任何屬性標注。</span><span class="sxs-lookup"><span data-stu-id="41292-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="41292-121">這表示可為 null 的警告可能無法精確反映潛在問題。</span><span class="sxs-lookup"><span data-stu-id="41292-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

<span data-ttu-id="41292-122">只有在 .NET 5 和更新版本上才支援 c # 9.0。</span><span class="sxs-lookup"><span data-stu-id="41292-122">C# 9.0 is supported only on .NET 5 and newer versions.</span></span>

## <a name="defaults"></a><span data-ttu-id="41292-123">Defaults</span><span class="sxs-lookup"><span data-stu-id="41292-123">Defaults</span></span>

<span data-ttu-id="41292-124">編譯器會根據下列規則決定預設值：</span><span class="sxs-lookup"><span data-stu-id="41292-124">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="41292-125">目標架構</span><span class="sxs-lookup"><span data-stu-id="41292-125">Target framework</span></span> | <span data-ttu-id="41292-126">版本</span><span class="sxs-lookup"><span data-stu-id="41292-126">version</span></span> | <span data-ttu-id="41292-127">C# 語言版本預設值</span><span class="sxs-lookup"><span data-stu-id="41292-127">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="41292-128">.NET</span><span class="sxs-lookup"><span data-stu-id="41292-128">.NET</span></span>             | <span data-ttu-id="41292-129">版</span><span class="sxs-lookup"><span data-stu-id="41292-129">5.x</span></span>     | <span data-ttu-id="41292-130">C# 9.0</span><span class="sxs-lookup"><span data-stu-id="41292-130">C# 9.0</span></span>                      |
| <span data-ttu-id="41292-131">.NET Core</span><span class="sxs-lookup"><span data-stu-id="41292-131">.NET Core</span></span>        | <span data-ttu-id="41292-132">3.x</span><span class="sxs-lookup"><span data-stu-id="41292-132">3.x</span></span>     | <span data-ttu-id="41292-133">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="41292-133">C# 8.0</span></span>                      |
| <span data-ttu-id="41292-134">.NET Core</span><span class="sxs-lookup"><span data-stu-id="41292-134">.NET Core</span></span>        | <span data-ttu-id="41292-135">2.x</span><span class="sxs-lookup"><span data-stu-id="41292-135">2.x</span></span>     | <span data-ttu-id="41292-136">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="41292-136">C# 7.3</span></span>                      |
| <span data-ttu-id="41292-137">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="41292-137">.NET Standard</span></span>    | <span data-ttu-id="41292-138">2.1</span><span class="sxs-lookup"><span data-stu-id="41292-138">2.1</span></span>     | <span data-ttu-id="41292-139">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="41292-139">C# 8.0</span></span>                      |
| <span data-ttu-id="41292-140">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="41292-140">.NET Standard</span></span>    | <span data-ttu-id="41292-141">2.0</span><span class="sxs-lookup"><span data-stu-id="41292-141">2.0</span></span>     | <span data-ttu-id="41292-142">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="41292-142">C# 7.3</span></span>                      |
| <span data-ttu-id="41292-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="41292-143">.NET Standard</span></span>    | <span data-ttu-id="41292-144">1.x</span><span class="sxs-lookup"><span data-stu-id="41292-144">1.x</span></span>     | <span data-ttu-id="41292-145">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="41292-145">C# 7.3</span></span>                      |
| <span data-ttu-id="41292-146">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="41292-146">.NET Framework</span></span>   | <span data-ttu-id="41292-147">all</span><span class="sxs-lookup"><span data-stu-id="41292-147">all</span></span>     | <span data-ttu-id="41292-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="41292-148">C# 7.3</span></span>                      |

<span data-ttu-id="41292-149">當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。</span><span class="sxs-lookup"><span data-stu-id="41292-149">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="41292-150">您可以在任何環境中使用該預覽版的最新功能，而不會影響以發行之 .NET Core 版本為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="41292-150">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

> [!TIP]
> <span data-ttu-id="41292-151">若要瞭解您目前使用的語言版本，請 `#error version` 在您的程式碼中放 (區分大小寫) 。</span><span class="sxs-lookup"><span data-stu-id="41292-151">To know what language version you're currently using, put `#error version` (case sensitive) in your code.</span></span> <span data-ttu-id="41292-152">這會讓編譯器產生診斷（CS8304），其中包含所使用之編譯器版本和目前所選語言版本的訊息。</span><span class="sxs-lookup"><span data-stu-id="41292-152">This makes the compiler produce a diagnostic, CS8304, with a message containing the compiler version being used and the current selected language version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="41292-153">覆寫預設</span><span class="sxs-lookup"><span data-stu-id="41292-153">Override a default</span></span>

<span data-ttu-id="41292-154">如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：</span><span class="sxs-lookup"><span data-stu-id="41292-154">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="41292-155">手動編輯您的[專案檔](#edit-the-project-file)。</span><span class="sxs-lookup"><span data-stu-id="41292-155">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="41292-156">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="41292-156">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="41292-157">設定[ `-langversion` 編譯器選項](compiler-options/langversion-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="41292-157">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="41292-158">編輯專案檔</span><span class="sxs-lookup"><span data-stu-id="41292-158">Edit the project file</span></span>

<span data-ttu-id="41292-159">您可以在專案檔中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="41292-159">You can set the language version in your project file.</span></span> <span data-ttu-id="41292-160">例如，如果您明確希望存取預覽功能，您可以新增如下元素：</span><span class="sxs-lookup"><span data-stu-id="41292-160">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="41292-161">`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。</span><span class="sxs-lookup"><span data-stu-id="41292-161">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="41292-162">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="41292-162">Configure multiple projects</span></span>

<span data-ttu-id="41292-163">若要設定多個專案，您可以建立包含元素的 **.props** 檔案。 `<LangVersion>`</span><span class="sxs-lookup"><span data-stu-id="41292-163">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="41292-164">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="41292-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="41292-165">將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="41292-165">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="41292-166">在包含該檔案之目錄的所有子目錄中建立的組建都會使用 preview c # 版本。</span><span class="sxs-lookup"><span data-stu-id="41292-166">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="41292-167">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="41292-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="41292-168">C# 語言版本參考</span><span class="sxs-lookup"><span data-stu-id="41292-168">C# language version reference</span></span>

<span data-ttu-id="41292-169">下表顯示所有目前的 C# 語言版本。</span><span class="sxs-lookup"><span data-stu-id="41292-169">The following table shows all current C# language versions.</span></span> <span data-ttu-id="41292-170">如果您的編譯器較舊，您的編譯器可能不一定會瞭解每一個值。</span><span class="sxs-lookup"><span data-stu-id="41292-170">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="41292-171">如果您安裝最新的 .NET SDK，則您可以存取所列的所有專案。</span><span class="sxs-lookup"><span data-stu-id="41292-171">If you install the latest .NET SDK, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="41292-172">開啟 [Visual Studio 的開發人員命令提示字元](../../framework/tools/developer-command-prompt-for-vs.md)，然後執行下列命令，以查看您電腦上可用的語言版本清單。</span><span class="sxs-lookup"><span data-stu-id="41292-172">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="41292-173">質疑這類 [langversion](compiler-options/langversion-compiler-option.md) 編譯選項，將會列印如下所示的內容：</span><span class="sxs-lookup"><span data-stu-id="41292-173">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
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
> 8.0
> 9.0 (default)
> latestmajor
> preview
> latest
> ```
