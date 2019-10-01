---
title: C# 語言版本控制 - C# 指南
description: 了解如何根據您的專案決定 C# 語言版本，以及您可以手動調整的不同值。
ms.date: 07/10/2019
ms.openlocfilehash: aa4f16d91b38fec7f5d4cd0b2632e62552b64eb7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698811"
---
# <a name="c-language-versioning"></a><span data-ttu-id="75650-103">C# 語言版本控制</span><span class="sxs-lookup"><span data-stu-id="75650-103">C# language versioning</span></span>

<span data-ttu-id="75650-104">最新 C# 編譯器會根據您專案的目標 Framework 判斷預設語言版本。</span><span class="sxs-lookup"><span data-stu-id="75650-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="75650-105">這是因為 C# 語言可能具有依賴於型別或執行階段元件的功能，而並非每個 .NET 實作都提供。</span><span class="sxs-lookup"><span data-stu-id="75650-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="75650-106">這也可確保建置專案的任何目標，您可以根據預設獲得最相容的語言版本。</span><span class="sxs-lookup"><span data-stu-id="75650-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="75650-107">本文中規則適用於 Visual Studio 2019 或 .NET Core 3.0 SDK 隨附的編譯器。</span><span class="sxs-lookup"><span data-stu-id="75650-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="75650-108">屬於 Visual Studio 2017 安裝或舊版 .NET Core SDK 一部分的 C# 編譯器預設會以 C# 7.0 為目標。</span><span class="sxs-lookup"><span data-stu-id="75650-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="75650-109">預設值</span><span class="sxs-lookup"><span data-stu-id="75650-109">Defaults</span></span>

<span data-ttu-id="75650-110">編譯器會根據下列規則決定預設值：</span><span class="sxs-lookup"><span data-stu-id="75650-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="75650-111">目標架構</span><span class="sxs-lookup"><span data-stu-id="75650-111">Target framework</span></span>|<span data-ttu-id="75650-112">版本</span><span class="sxs-lookup"><span data-stu-id="75650-112">version</span></span>|<span data-ttu-id="75650-113">C# 語言版本預設值</span><span class="sxs-lookup"><span data-stu-id="75650-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="75650-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="75650-114">.NET Core</span></span>|<span data-ttu-id="75650-115">3.x</span><span class="sxs-lookup"><span data-stu-id="75650-115">3.x</span></span>|<span data-ttu-id="75650-116">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="75650-116">C# 8.0</span></span>|
|<span data-ttu-id="75650-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="75650-117">.NET Core</span></span>|<span data-ttu-id="75650-118">2.x</span><span class="sxs-lookup"><span data-stu-id="75650-118">2.x</span></span>|<span data-ttu-id="75650-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="75650-119">C# 7.3</span></span>|
|<span data-ttu-id="75650-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="75650-120">.NET Standard</span></span>|<span data-ttu-id="75650-121">2.1</span><span class="sxs-lookup"><span data-stu-id="75650-121">2.1</span></span>|<span data-ttu-id="75650-122">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="75650-122">C# 8.0</span></span>|
|<span data-ttu-id="75650-123">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="75650-123">.NET Standard</span></span>|<span data-ttu-id="75650-124">2.0</span><span class="sxs-lookup"><span data-stu-id="75650-124">2.0</span></span>|<span data-ttu-id="75650-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="75650-125">C# 7.3</span></span>|
|<span data-ttu-id="75650-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="75650-126">.NET Standard</span></span>|<span data-ttu-id="75650-127">1.x</span><span class="sxs-lookup"><span data-stu-id="75650-127">1.x</span></span>|<span data-ttu-id="75650-128">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="75650-128">C# 7.3</span></span>|
|<span data-ttu-id="75650-129">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="75650-129">.NET Framework</span></span>|<span data-ttu-id="75650-130">all</span><span class="sxs-lookup"><span data-stu-id="75650-130">all</span></span>|<span data-ttu-id="75650-131">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="75650-131">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="75650-132">預設為預覽</span><span class="sxs-lookup"><span data-stu-id="75650-132">Default for previews</span></span>

<span data-ttu-id="75650-133">當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。</span><span class="sxs-lookup"><span data-stu-id="75650-133">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="75650-134">這能確保可讓您利用最新功能，保證可在任何環境中使用該預覽，而不會影響對已發行之 .NET Core 版本為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="75650-134">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="75650-135">覆寫預設</span><span class="sxs-lookup"><span data-stu-id="75650-135">Override a default</span></span>

<span data-ttu-id="75650-136">如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：</span><span class="sxs-lookup"><span data-stu-id="75650-136">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="75650-137">手動編輯您的[專案檔](#edit-the-project-file)。</span><span class="sxs-lookup"><span data-stu-id="75650-137">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="75650-138">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="75650-138">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="75650-139">設定 [`-langversion` 編譯器選項](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="75650-139">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="75650-140">編輯專案檔</span><span class="sxs-lookup"><span data-stu-id="75650-140">Edit the project file</span></span>

<span data-ttu-id="75650-141">您可以在專案檔中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="75650-141">You can set the language version in your project file.</span></span> <span data-ttu-id="75650-142">例如，如果您明確希望存取預覽功能，您可以新增如下元素：</span><span class="sxs-lookup"><span data-stu-id="75650-142">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="75650-143">`preview` 值會使用編譯器支援的最新預覽 C# 語言語言。</span><span class="sxs-lookup"><span data-stu-id="75650-143">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="75650-144">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="75650-144">Configure multiple projects</span></span>

<span data-ttu-id="75650-145">您可以建立 **Directory.Build.props** 檔案，其中包含 `<LangVersion>` 元素來設定多個目錄。</span><span class="sxs-lookup"><span data-stu-id="75650-145">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="75650-146">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="75650-146">You typically do that in your solution directory.</span></span> <span data-ttu-id="75650-147">將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="75650-147">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="75650-148">現在，包含該檔案之目錄中每個子目錄的組建，將會使用預覽 C# 版本。</span><span class="sxs-lookup"><span data-stu-id="75650-148">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="75650-149">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="75650-149">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="75650-150">C# 語言版本參考</span><span class="sxs-lookup"><span data-stu-id="75650-150">C# language version reference</span></span>

<span data-ttu-id="75650-151">下表顯示所有目前的 C# 語言版本。</span><span class="sxs-lookup"><span data-stu-id="75650-151">The following table shows all current C# language versions.</span></span> <span data-ttu-id="75650-152">如果您的編譯器版本較舊，可能不一定了解每個值。</span><span class="sxs-lookup"><span data-stu-id="75650-152">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="75650-153">如果您安裝 .NET Core 3.0，您將能存取所列的所有項目。</span><span class="sxs-lookup"><span data-stu-id="75650-153">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="75650-154">值</span><span class="sxs-lookup"><span data-stu-id="75650-154">Value</span></span>|<span data-ttu-id="75650-155">意義</span><span class="sxs-lookup"><span data-stu-id="75650-155">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="75650-156">preview</span><span class="sxs-lookup"><span data-stu-id="75650-156">preview</span></span>|<span data-ttu-id="75650-157">編譯器會接受最新預覽版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="75650-157">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="75650-158">latest</span><span class="sxs-lookup"><span data-stu-id="75650-158">latest</span></span>|<span data-ttu-id="75650-159">編譯器會接受編譯器最新已發行版本 (包括次要版本) 的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-159">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="75650-160">latestMajor</span><span class="sxs-lookup"><span data-stu-id="75650-160">latestMajor</span></span>|<span data-ttu-id="75650-161">編譯器會接受編譯器最新已發行主要版本的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-161">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="75650-162">8.0</span><span class="sxs-lookup"><span data-stu-id="75650-162">8.0</span></span>|<span data-ttu-id="75650-163">編譯器只會接受 C# 8.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-163">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="75650-164">7.3</span><span class="sxs-lookup"><span data-stu-id="75650-164">7.3</span></span>|<span data-ttu-id="75650-165">編譯器只會接受 C# 7.3 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-165">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="75650-166">7.2</span><span class="sxs-lookup"><span data-stu-id="75650-166">7.2</span></span>|<span data-ttu-id="75650-167">編譯器只會接受 C# 7.2 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-167">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="75650-168">7.1</span><span class="sxs-lookup"><span data-stu-id="75650-168">7.1</span></span>|<span data-ttu-id="75650-169">編譯器只會接受 C# 7.1 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-169">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="75650-170">7</span><span class="sxs-lookup"><span data-stu-id="75650-170">7</span></span>|<span data-ttu-id="75650-171">編譯器只會接受 C# 7.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-171">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="75650-172">6</span><span class="sxs-lookup"><span data-stu-id="75650-172">6</span></span>|<span data-ttu-id="75650-173">編譯器只會接受 C# 6.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-173">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="75650-174">5</span><span class="sxs-lookup"><span data-stu-id="75650-174">5</span></span>|<span data-ttu-id="75650-175">編譯器只會接受 C# 5.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-175">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="75650-176">4</span><span class="sxs-lookup"><span data-stu-id="75650-176">4</span></span>|<span data-ttu-id="75650-177">編譯器只會接受 C# 4.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-177">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="75650-178">3</span><span class="sxs-lookup"><span data-stu-id="75650-178">3</span></span>|<span data-ttu-id="75650-179">編譯器只會接受 C# 3.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="75650-179">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="75650-180">ISO-2</span><span class="sxs-lookup"><span data-stu-id="75650-180">ISO-2</span></span>|<span data-ttu-id="75650-181">編譯器只會接受 ISO/IEC 23270:2006 C# (2.0) 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="75650-181">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="75650-182">ISO-1</span><span class="sxs-lookup"><span data-stu-id="75650-182">ISO-1</span></span>|<span data-ttu-id="75650-183">編譯器只會接受 ISO/IEC 23270:2003 C# (1.0/1.2) 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="75650-183">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
