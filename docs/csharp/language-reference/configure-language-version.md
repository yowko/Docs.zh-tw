---
title: C# 語言版本控制 - C# 指南
description: '瞭解如何根據您的專案以及該選項背後的原因來決定 c # 語言版本。 瞭解如何手動覆寫預設值。'
ms.custom: updateeachrelease
ms.date: 08/11/2020
ms.openlocfilehash: b022b726861bd6ea45b188df44549dc279d34a74
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96598925"
---
# <a name="c-language-versioning"></a><span data-ttu-id="4afb3-104">C# 語言版本控制</span><span class="sxs-lookup"><span data-stu-id="4afb3-104">C# language versioning</span></span>

<span data-ttu-id="4afb3-105">最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。</span><span class="sxs-lookup"><span data-stu-id="4afb3-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="4afb3-106">Visual Studio 不會提供 UI 來變更值，但您可以編輯 *.csproj* 檔案來變更該值。</span><span class="sxs-lookup"><span data-stu-id="4afb3-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="4afb3-107">選擇預設值可確保您使用與目標 framework 相容的最新語言版本。</span><span class="sxs-lookup"><span data-stu-id="4afb3-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="4afb3-108">您可以從與專案目標相容的最新語言功能存取中獲益。</span><span class="sxs-lookup"><span data-stu-id="4afb3-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="4afb3-109">此預設選項也可確保您不會使用需要類型或執行時間行為的語言，而無法在您的目標 framework 中使用。</span><span class="sxs-lookup"><span data-stu-id="4afb3-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="4afb3-110">選擇比預設版本新的語言版本，可能會導致難以診斷編譯時期和執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="4afb3-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="4afb3-111">本文中的規則適用于使用 Visual Studio 2019 或 .NET SDK 提供的編譯器。</span><span class="sxs-lookup"><span data-stu-id="4afb3-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET SDK.</span></span> <span data-ttu-id="4afb3-112">屬於 Visual Studio 2017 安裝或舊版 .NET Core SDK 一部分的 C# 編譯器預設會以 C# 7.0 為目標。</span><span class="sxs-lookup"><span data-stu-id="4afb3-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="4afb3-113">只有 .NET Core 3.x 和更新版本才支援 c # 8.0。</span><span class="sxs-lookup"><span data-stu-id="4afb3-113">C# 8.0 is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="4afb3-114">許多最新功能都需要 .NET Core 3.x 所引進的程式庫和執行時間功能：</span><span class="sxs-lookup"><span data-stu-id="4afb3-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="4afb3-115">[預設介面執行](../whats-new/csharp-8.md#default-interface-methods) 需要 .net CORE 3.0 CLR 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="4afb3-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="4afb3-116">[非同步資料流程](../whats-new/csharp-8.md#asynchronous-streams) 需要新的類型 <xref:System.IAsyncDisposable?displayProperty=nameWithType> 、 <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4afb3-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="4afb3-117">[索引和範圍](../whats-new/csharp-8.md#indices-and-ranges) 需要新的類型 <xref:System.Index?displayProperty=nameWithType> 和 <xref:System.Range?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4afb3-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="4afb3-118">[可為 null 的參考型別](../whats-new/csharp-8.md#nullable-reference-types) 會使用數個 [屬性](attributes/nullable-analysis.md) ，以提供更好的警告。</span><span class="sxs-lookup"><span data-stu-id="4afb3-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="4afb3-119">這些屬性已在 .NET Core 3.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4afb3-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="4afb3-120">其他目標 framework 尚未以上述任何屬性標注。</span><span class="sxs-lookup"><span data-stu-id="4afb3-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="4afb3-121">這表示可為 null 的警告可能無法精確反映潛在問題。</span><span class="sxs-lookup"><span data-stu-id="4afb3-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

<span data-ttu-id="4afb3-122">只有在 .NET 5 和更新版本上才支援 c # 9.0。</span><span class="sxs-lookup"><span data-stu-id="4afb3-122">C# 9.0 is supported only on .NET 5 and newer versions.</span></span>

## <a name="defaults"></a><span data-ttu-id="4afb3-123">Defaults</span><span class="sxs-lookup"><span data-stu-id="4afb3-123">Defaults</span></span>

<span data-ttu-id="4afb3-124">編譯器會根據下列規則決定預設值：</span><span class="sxs-lookup"><span data-stu-id="4afb3-124">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="4afb3-125">目標架構</span><span class="sxs-lookup"><span data-stu-id="4afb3-125">Target framework</span></span> | <span data-ttu-id="4afb3-126">version</span><span class="sxs-lookup"><span data-stu-id="4afb3-126">version</span></span> | <span data-ttu-id="4afb3-127">C# 語言版本預設值</span><span class="sxs-lookup"><span data-stu-id="4afb3-127">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="4afb3-128">.NET</span><span class="sxs-lookup"><span data-stu-id="4afb3-128">.NET</span></span>             | <span data-ttu-id="4afb3-129">版</span><span class="sxs-lookup"><span data-stu-id="4afb3-129">5.x</span></span>     | <span data-ttu-id="4afb3-130">C# 9.0</span><span class="sxs-lookup"><span data-stu-id="4afb3-130">C# 9.0</span></span>                      |
| <span data-ttu-id="4afb3-131">.NET Core</span><span class="sxs-lookup"><span data-stu-id="4afb3-131">.NET Core</span></span>        | <span data-ttu-id="4afb3-132">3.x</span><span class="sxs-lookup"><span data-stu-id="4afb3-132">3.x</span></span>     | <span data-ttu-id="4afb3-133">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="4afb3-133">C# 8.0</span></span>                      |
| <span data-ttu-id="4afb3-134">.NET Core</span><span class="sxs-lookup"><span data-stu-id="4afb3-134">.NET Core</span></span>        | <span data-ttu-id="4afb3-135">2.x</span><span class="sxs-lookup"><span data-stu-id="4afb3-135">2.x</span></span>     | <span data-ttu-id="4afb3-136">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="4afb3-136">C# 7.3</span></span>                      |
| <span data-ttu-id="4afb3-137">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="4afb3-137">.NET Standard</span></span>    | <span data-ttu-id="4afb3-138">2.1</span><span class="sxs-lookup"><span data-stu-id="4afb3-138">2.1</span></span>     | <span data-ttu-id="4afb3-139">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="4afb3-139">C# 8.0</span></span>                      |
| <span data-ttu-id="4afb3-140">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="4afb3-140">.NET Standard</span></span>    | <span data-ttu-id="4afb3-141">2.0</span><span class="sxs-lookup"><span data-stu-id="4afb3-141">2.0</span></span>     | <span data-ttu-id="4afb3-142">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="4afb3-142">C# 7.3</span></span>                      |
| <span data-ttu-id="4afb3-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="4afb3-143">.NET Standard</span></span>    | <span data-ttu-id="4afb3-144">1.x</span><span class="sxs-lookup"><span data-stu-id="4afb3-144">1.x</span></span>     | <span data-ttu-id="4afb3-145">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="4afb3-145">C# 7.3</span></span>                      |
| <span data-ttu-id="4afb3-146">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="4afb3-146">.NET Framework</span></span>   | <span data-ttu-id="4afb3-147">all</span><span class="sxs-lookup"><span data-stu-id="4afb3-147">all</span></span>     | <span data-ttu-id="4afb3-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="4afb3-148">C# 7.3</span></span>                      |

<span data-ttu-id="4afb3-149">當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。</span><span class="sxs-lookup"><span data-stu-id="4afb3-149">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="4afb3-150">您可以在任何環境中使用該預覽版的最新功能，而不會影響以發行之 .NET Core 版本為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="4afb3-150">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4afb3-151">Visual Studio 2017 已將專案新增 `<LangVersion>latest</LangVersion>` 至它所建立的任何專案檔。</span><span class="sxs-lookup"><span data-stu-id="4afb3-151">Visual Studio 2017 added a `<LangVersion>latest</LangVersion>` entry to any project files it created.</span></span> <span data-ttu-id="4afb3-152">這表示在加入 *c # 7.0* 時。</span><span class="sxs-lookup"><span data-stu-id="4afb3-152">That meant *C# 7.0* when it was added.</span></span> <span data-ttu-id="4afb3-153">不過，一旦您升級至 Visual Studio 2019，這就表示最新發行的版本，而不論目標 framework 為何。</span><span class="sxs-lookup"><span data-stu-id="4afb3-153">However, once you upgrade to Visual Studio 2019, that means the latest released version, regardless of the target framework.</span></span> <span data-ttu-id="4afb3-154">這些專案現在會覆 [寫預設行為](#override-a-default)。</span><span class="sxs-lookup"><span data-stu-id="4afb3-154">These projects now [override the default behavior](#override-a-default).</span></span> <span data-ttu-id="4afb3-155">您應該編輯專案檔，並移除該節點。</span><span class="sxs-lookup"><span data-stu-id="4afb3-155">You should edit the project file and remove that node.</span></span> <span data-ttu-id="4afb3-156">然後，您的專案將會使用針對您的目標架構所建議的編譯器版本。</span><span class="sxs-lookup"><span data-stu-id="4afb3-156">Then, your project will use the compiler version recommended for your target framework.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="4afb3-157">覆寫預設</span><span class="sxs-lookup"><span data-stu-id="4afb3-157">Override a default</span></span>

<span data-ttu-id="4afb3-158">如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：</span><span class="sxs-lookup"><span data-stu-id="4afb3-158">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="4afb3-159">手動編輯您的[專案檔](#edit-the-project-file)。</span><span class="sxs-lookup"><span data-stu-id="4afb3-159">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="4afb3-160">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="4afb3-160">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="4afb3-161">設定[ `-langversion` 編譯器選項](compiler-options/langversion-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="4afb3-161">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

> [!TIP]
> <span data-ttu-id="4afb3-162">若要瞭解您目前使用的語言版本，請 `#error version` 在您的程式碼中放 (區分大小寫) 。</span><span class="sxs-lookup"><span data-stu-id="4afb3-162">To know what language version you're currently using, put `#error version` (case sensitive) in your code.</span></span> <span data-ttu-id="4afb3-163">這會讓編譯器產生診斷（CS8304），其中包含所使用之編譯器版本和目前所選語言版本的訊息。</span><span class="sxs-lookup"><span data-stu-id="4afb3-163">This makes the compiler produce a diagnostic, CS8304, with a message containing the compiler version being used and the current selected language version.</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="4afb3-164">編輯專案檔</span><span class="sxs-lookup"><span data-stu-id="4afb3-164">Edit the project file</span></span>

<span data-ttu-id="4afb3-165">您可以在專案檔中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="4afb3-165">You can set the language version in your project file.</span></span> <span data-ttu-id="4afb3-166">例如，如果您明確希望存取預覽功能，您可以新增如下元素：</span><span class="sxs-lookup"><span data-stu-id="4afb3-166">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="4afb3-167">`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。</span><span class="sxs-lookup"><span data-stu-id="4afb3-167">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="4afb3-168">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="4afb3-168">Configure multiple projects</span></span>

<span data-ttu-id="4afb3-169">若要設定多個專案，您可以建立包含元素的 **.props** 檔案。 `<LangVersion>`</span><span class="sxs-lookup"><span data-stu-id="4afb3-169">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="4afb3-170">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="4afb3-170">You typically do that in your solution directory.</span></span> <span data-ttu-id="4afb3-171">將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="4afb3-171">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="4afb3-172">在包含該檔案之目錄的所有子目錄中建立的組建都會使用 preview c # 版本。</span><span class="sxs-lookup"><span data-stu-id="4afb3-172">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="4afb3-173">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="4afb3-173">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="4afb3-174">C# 語言版本參考</span><span class="sxs-lookup"><span data-stu-id="4afb3-174">C# language version reference</span></span>

<span data-ttu-id="4afb3-175">下表顯示所有目前的 C# 語言版本。</span><span class="sxs-lookup"><span data-stu-id="4afb3-175">The following table shows all current C# language versions.</span></span> <span data-ttu-id="4afb3-176">如果您的編譯器較舊，您的編譯器可能不一定會瞭解每一個值。</span><span class="sxs-lookup"><span data-stu-id="4afb3-176">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="4afb3-177">如果您安裝最新的 .NET SDK，則您可以存取所列的所有專案。</span><span class="sxs-lookup"><span data-stu-id="4afb3-177">If you install the latest .NET SDK, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="4afb3-178">開啟 [Visual Studio 的開發人員命令提示字元](../../framework/tools/developer-command-prompt-for-vs.md)，然後執行下列命令，以查看您電腦上可用的語言版本清單。</span><span class="sxs-lookup"><span data-stu-id="4afb3-178">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="4afb3-179">質疑這類 [langversion](compiler-options/langversion-compiler-option.md) 編譯選項，將會列印如下所示的內容：</span><span class="sxs-lookup"><span data-stu-id="4afb3-179">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
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
