---
title: C# 語言版本控制 - C# 指南
description: 了解如何根據您的專案決定 C# 語言版本，以及您可以手動調整的不同值。
ms.date: 07/10/2019
ms.openlocfilehash: 2d593ca0588f291c61cdf52fbc1eb60a1f3f7ecb
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859608"
---
# <a name="c-language-versioning"></a><span data-ttu-id="ccc69-103">C# 語言版本控制</span><span class="sxs-lookup"><span data-stu-id="ccc69-103">C# language versioning</span></span>

<span data-ttu-id="ccc69-104">C# 編譯器會根據您專案的目標架構判斷預設語言版本。</span><span class="sxs-lookup"><span data-stu-id="ccc69-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="ccc69-105">這是因為 C# 語言可能具有依賴於型別或執行階段元件的功能，而並非每個 .NET 實作都提供。</span><span class="sxs-lookup"><span data-stu-id="ccc69-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="ccc69-106">這也可確保建置專案的任何目標，您可以根據預設獲得最相容的語言版本。</span><span class="sxs-lookup"><span data-stu-id="ccc69-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="ccc69-107">預設值</span><span class="sxs-lookup"><span data-stu-id="ccc69-107">Defaults</span></span>

<span data-ttu-id="ccc69-108">編譯器會根據下列規則決定預設值：</span><span class="sxs-lookup"><span data-stu-id="ccc69-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="ccc69-109">目標架構</span><span class="sxs-lookup"><span data-stu-id="ccc69-109">Target framework</span></span>|<span data-ttu-id="ccc69-110">版本</span><span class="sxs-lookup"><span data-stu-id="ccc69-110">version</span></span>|<span data-ttu-id="ccc69-111">C# 語言版本預設值</span><span class="sxs-lookup"><span data-stu-id="ccc69-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="ccc69-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="ccc69-112">.NET Core</span></span>|<span data-ttu-id="ccc69-113">3.x</span><span class="sxs-lookup"><span data-stu-id="ccc69-113">3.x</span></span>|<span data-ttu-id="ccc69-114">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="ccc69-114">C# 8.0</span></span>|
|<span data-ttu-id="ccc69-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="ccc69-115">.NET Core</span></span>|<span data-ttu-id="ccc69-116">2.x</span><span class="sxs-lookup"><span data-stu-id="ccc69-116">2.x</span></span>|<span data-ttu-id="ccc69-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="ccc69-117">C# 7.3</span></span>|
|<span data-ttu-id="ccc69-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="ccc69-118">.NET Standard</span></span>|<span data-ttu-id="ccc69-119">all</span><span class="sxs-lookup"><span data-stu-id="ccc69-119">all</span></span>|<span data-ttu-id="ccc69-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="ccc69-120">C# 7.3</span></span>|
|<span data-ttu-id="ccc69-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ccc69-121">.NET Framework</span></span>|<span data-ttu-id="ccc69-122">all</span><span class="sxs-lookup"><span data-stu-id="ccc69-122">all</span></span>|<span data-ttu-id="ccc69-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="ccc69-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="ccc69-124">預設為預覽</span><span class="sxs-lookup"><span data-stu-id="ccc69-124">Default for previews</span></span>

<span data-ttu-id="ccc69-125">當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。</span><span class="sxs-lookup"><span data-stu-id="ccc69-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="ccc69-126">這能確保可讓您利用最新功能，保證可在任何環境中使用該預覽，而不會影響對已發行之 .NET Core 版本為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="ccc69-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="overriding-a-default"></a><span data-ttu-id="ccc69-127">覆寫預設值</span><span class="sxs-lookup"><span data-stu-id="ccc69-127">Overriding a default</span></span>

<span data-ttu-id="ccc69-128">如果您必須明確指定您的 C# 版本，您可以透過數種方式進行：</span><span class="sxs-lookup"><span data-stu-id="ccc69-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="ccc69-129">手動編輯您的[專案檔](#edit-the-project-file)。</span><span class="sxs-lookup"><span data-stu-id="ccc69-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="ccc69-130">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="ccc69-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="ccc69-131">設定 [`-langversion`編譯器選項](#set-the-langversion-compiler-option)。</span><span class="sxs-lookup"><span data-stu-id="ccc69-131">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="ccc69-132">編輯專案檔</span><span class="sxs-lookup"><span data-stu-id="ccc69-132">Edit the project file</span></span>

<span data-ttu-id="ccc69-133">您可以在專案檔中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="ccc69-133">You can set the language version in your project file.</span></span> <span data-ttu-id="ccc69-134">舉例而言，如果您明確希望存取預覽功能，您可以新增像這樣的項目：</span><span class="sxs-lookup"><span data-stu-id="ccc69-134">For example, if you explicitly wanted access to preview features, you could do add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="ccc69-135">`preview` 值會使用編譯器支援的最新預覽 C# 語言。</span><span class="sxs-lookup"><span data-stu-id="ccc69-135">The value `preview` uses the latest available preview C# language that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="ccc69-136">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="ccc69-136">Configure multiple projects</span></span>

<span data-ttu-id="ccc69-137">您可以建立 **Directory.Build.props** 檔案，其中包含 `<LangVersion>` 元素來設定多個目錄。</span><span class="sxs-lookup"><span data-stu-id="ccc69-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="ccc69-138">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="ccc69-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="ccc69-139">將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="ccc69-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="ccc69-140">現在，包含該檔案之目錄中每個子目錄的組建，將會使用預覽 C# 版本。</span><span class="sxs-lookup"><span data-stu-id="ccc69-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="ccc69-141">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="ccc69-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="ccc69-142">C# 語言版本參考</span><span class="sxs-lookup"><span data-stu-id="ccc69-142">C# language version reference</span></span>

<span data-ttu-id="ccc69-143">下表顯示所有目前的 C# 語言版本。</span><span class="sxs-lookup"><span data-stu-id="ccc69-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="ccc69-144">如果您的編譯器版本較舊，可能不一定了解每個值。</span><span class="sxs-lookup"><span data-stu-id="ccc69-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="ccc69-145">如果您安裝 .NET Core 3.0，您將能存取所列的所有項目。</span><span class="sxs-lookup"><span data-stu-id="ccc69-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="ccc69-146">值</span><span class="sxs-lookup"><span data-stu-id="ccc69-146">Value</span></span>|<span data-ttu-id="ccc69-147">意義</span><span class="sxs-lookup"><span data-stu-id="ccc69-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="ccc69-148">preview</span><span class="sxs-lookup"><span data-stu-id="ccc69-148">preview</span></span>|<span data-ttu-id="ccc69-149">編譯器會接受最新預覽版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="ccc69-150">latest</span><span class="sxs-lookup"><span data-stu-id="ccc69-150">latest</span></span>|<span data-ttu-id="ccc69-151">編譯器會接受編譯器最新已發行版本 (包括次要版本) 的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="ccc69-152">latestMajor</span><span class="sxs-lookup"><span data-stu-id="ccc69-152">latestMajor</span></span>|<span data-ttu-id="ccc69-153">編譯器會接受編譯器最新已發行主要版本的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="ccc69-154">8.0</span><span class="sxs-lookup"><span data-stu-id="ccc69-154">8.0</span></span>|<span data-ttu-id="ccc69-155">編譯器只會接受 C# 8.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="ccc69-156">7.3</span><span class="sxs-lookup"><span data-stu-id="ccc69-156">7.3</span></span>|<span data-ttu-id="ccc69-157">編譯器只會接受 C# 7.3 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="ccc69-158">7.2</span><span class="sxs-lookup"><span data-stu-id="ccc69-158">7.2</span></span>|<span data-ttu-id="ccc69-159">編譯器只會接受 C# 7.2 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="ccc69-160">7.1</span><span class="sxs-lookup"><span data-stu-id="ccc69-160">7.1</span></span>|<span data-ttu-id="ccc69-161">編譯器只會接受 C# 7.1 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="ccc69-162">7</span><span class="sxs-lookup"><span data-stu-id="ccc69-162">7</span></span>|<span data-ttu-id="ccc69-163">編譯器只會接受 C# 7.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="ccc69-164">6</span><span class="sxs-lookup"><span data-stu-id="ccc69-164">6</span></span>|<span data-ttu-id="ccc69-165">編譯器只會接受 C# 6.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="ccc69-166">5</span><span class="sxs-lookup"><span data-stu-id="ccc69-166">5</span></span>|<span data-ttu-id="ccc69-167">編譯器只會接受 C# 5.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="ccc69-168">4</span><span class="sxs-lookup"><span data-stu-id="ccc69-168">4</span></span>|<span data-ttu-id="ccc69-169">編譯器只會接受 C# 4.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="ccc69-170">3</span><span class="sxs-lookup"><span data-stu-id="ccc69-170">3</span></span>|<span data-ttu-id="ccc69-171">編譯器只會接受 C# 3.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="ccc69-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="ccc69-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="ccc69-172">ISO-2</span></span>|<span data-ttu-id="ccc69-173">編譯器只會接受 ISO/IEC 23270:2006 C# (2.0) 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="ccc69-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="ccc69-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="ccc69-174">ISO-1</span></span>|<span data-ttu-id="ccc69-175">編譯器只會接受 ISO/IEC 23270:2003 C# (1.0/1.2) 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="ccc69-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
