---
title: 選取 C# 語言版本 - C# 指南
description: 設定編譯器以特定的編譯器版本執行語法驗證
ms.date: 05/24/2018
ms.openlocfilehash: 2056a99544d0cac94bc7cc79e8cd8793b1bcff78
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34566319"
---
# <a name="select-the-c-language-version"></a><span data-ttu-id="43f23-103">選取 C# 語言版本</span><span class="sxs-lookup"><span data-stu-id="43f23-103">Select the C# language version</span></span>

<span data-ttu-id="43f23-104">C# 編譯器會預設為已發行的語言最新主要版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-104">The C# compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="43f23-105">您可以選擇使用語言的新點發行來編譯任何專案。</span><span class="sxs-lookup"><span data-stu-id="43f23-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="43f23-106">選擇語言的較新版本可讓您的專案利用最新的語言功能。</span><span class="sxs-lookup"><span data-stu-id="43f23-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="43f23-107">在其他情況下，使用較舊版本的語言時，您可能需要驗證專案全新地進行編譯。</span><span class="sxs-lookup"><span data-stu-id="43f23-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="43f23-108">此功能可讓在您開發環境中決定安裝新版本的 SDK 和工具，與在專案中決定納入新語言功能這兩件事分開。</span><span class="sxs-lookup"><span data-stu-id="43f23-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="43f23-109">您可以在組建電腦上安裝最新的 SDK 和工具。</span><span class="sxs-lookup"><span data-stu-id="43f23-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="43f23-110">每個專案可以設定為針對其組建使用特定版本的語言。</span><span class="sxs-lookup"><span data-stu-id="43f23-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="43f23-111">有數種方法可以設定語言版本：</span><span class="sxs-lookup"><span data-stu-id="43f23-111">There are several ways to set the language version:</span></span>

- <span data-ttu-id="43f23-112">依賴 [Visual Studio 快速動作](#visual-studio-quick-action)。</span><span class="sxs-lookup"><span data-stu-id="43f23-112">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="43f23-113">在 [Visual Studio UI](#set-the-language-version-in-visual-studio) 中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-113">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="43f23-114">手動編輯您的 [**.csproj** 檔案](#edit-the-csproj-file)。</span><span class="sxs-lookup"><span data-stu-id="43f23-114">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="43f23-115">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-115">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="43f23-116">設定 [`-langversion`編譯器選項](#set-the-langversion-compiler-option)。</span><span class="sxs-lookup"><span data-stu-id="43f23-116">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="43f23-117">Visual Studio 快速動作</span><span class="sxs-lookup"><span data-stu-id="43f23-117">Visual Studio quick action</span></span>

<span data-ttu-id="43f23-118">Visual Studio 可協助您判斷您需要的語言版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-118">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="43f23-119">如果您使用不適用於目前設定版本的語言功能，Visual Studio 會顯示可能的修正，以更新專案的語言版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-119">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="43f23-120">在 Visual Studio 中設定語言版本</span><span class="sxs-lookup"><span data-stu-id="43f23-120">Set the language version in Visual Studio</span></span>

<span data-ttu-id="43f23-121">您可以在 Visual Studio 中設定版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-121">You can set the version in Visual Studio.</span></span> <span data-ttu-id="43f23-122">以滑鼠右鍵按一下 [方案總管] 的專案節點，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="43f23-122">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="43f23-123">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="43f23-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="43f23-124">在下拉式清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-124">In the dropdown, select the version.</span></span> <span data-ttu-id="43f23-125">下圖顯示「最新」設定︰</span><span class="sxs-lookup"><span data-stu-id="43f23-125">The following image shows the "latest" setting:</span></span>

![進階組建設定的螢幕擷取畫面，您可以在其中指定語言版本](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="43f23-127">如果您使用 Visual Studio IDE 來更新 csproj 檔，IDE 會為每個組建組態建立個別的節點。</span><span class="sxs-lookup"><span data-stu-id="43f23-127">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="43f23-128">您一般會在所有組建組態中設定相同的值，但您需要針對每個組建組態明確設定，或在修改此設定時選取 [所有組態]。</span><span class="sxs-lookup"><span data-stu-id="43f23-128">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="43f23-129">您會在 csproj 檔案中看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="43f23-129">You'll see the following in your csproj file:</span></span>
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a><span data-ttu-id="43f23-130">編輯 csproj 檔案</span><span class="sxs-lookup"><span data-stu-id="43f23-130">Edit the csproj file</span></span>

<span data-ttu-id="43f23-131">您可以在 **.csproj** 檔案中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-131">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="43f23-132">如下所示新增元素：</span><span class="sxs-lookup"><span data-stu-id="43f23-132">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="43f23-133">`latest` 值使用 C# 語言的最新次要版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-133">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="43f23-134">有效值為：</span><span class="sxs-lookup"><span data-stu-id="43f23-134">Valid values are:</span></span>

|<span data-ttu-id="43f23-135">值</span><span class="sxs-lookup"><span data-stu-id="43f23-135">Value</span></span>|<span data-ttu-id="43f23-136">意義</span><span class="sxs-lookup"><span data-stu-id="43f23-136">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="43f23-137">default</span><span class="sxs-lookup"><span data-stu-id="43f23-137">default</span></span>|<span data-ttu-id="43f23-138">編譯器會接受它可支援之最新主要版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-138">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="43f23-139">ISO-1</span><span class="sxs-lookup"><span data-stu-id="43f23-139">ISO-1</span></span>|<span data-ttu-id="43f23-140">編譯器只會接受 ISO/IEC 23270:2003 C# (1.0/1.2) 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="43f23-140">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
|<span data-ttu-id="43f23-141">ISO-2</span><span class="sxs-lookup"><span data-stu-id="43f23-141">ISO-2</span></span>|<span data-ttu-id="43f23-142">編譯器只會接受 ISO/IEC 23270:2006 C# (2.0) 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="43f23-142">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="43f23-143">3</span><span class="sxs-lookup"><span data-stu-id="43f23-143">3</span></span>|<span data-ttu-id="43f23-144">編譯器只會接受 C# 3.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-144">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="43f23-145">4</span><span class="sxs-lookup"><span data-stu-id="43f23-145">4</span></span>|<span data-ttu-id="43f23-146">編譯器只會接受 C# 4.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-146">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="43f23-147">5</span><span class="sxs-lookup"><span data-stu-id="43f23-147">5</span></span>|<span data-ttu-id="43f23-148">編譯器只會接受 C# 5.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-148">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="43f23-149">6</span><span class="sxs-lookup"><span data-stu-id="43f23-149">6</span></span>|<span data-ttu-id="43f23-150">編譯器只會接受 C# 6.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-150">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="43f23-151">7</span><span class="sxs-lookup"><span data-stu-id="43f23-151">7</span></span>|<span data-ttu-id="43f23-152">編譯器只會接受 C# 7.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-152">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="43f23-153">7.1</span><span class="sxs-lookup"><span data-stu-id="43f23-153">7.1</span></span>|<span data-ttu-id="43f23-154">編譯器只會接受 C# 7.1 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="43f23-155">7.2</span><span class="sxs-lookup"><span data-stu-id="43f23-155">7.2</span></span>|<span data-ttu-id="43f23-156">編譯器只會接受 C# 7.2 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-156">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="43f23-157">7.3</span><span class="sxs-lookup"><span data-stu-id="43f23-157">7.3</span></span>|<span data-ttu-id="43f23-158">編譯器只會接受 C# 7.3 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-158">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="43f23-159">latest</span><span class="sxs-lookup"><span data-stu-id="43f23-159">latest</span></span>|<span data-ttu-id="43f23-160">編譯器會接受它可支援的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-160">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="43f23-161">特殊字串 `default` 和 `latest` 會分別解析成安裝在組建電腦上的最新主要 (C# 7.0) 和次要 (C# 7.3) 語言版本。</span><span class="sxs-lookup"><span data-stu-id="43f23-161">The special strings `default` and `latest` resolve to the latest major (C# 7.0) and minor (C# 7.3) language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="43f23-162">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="43f23-162">Configure multiple projects</span></span>

<span data-ttu-id="43f23-163">您可以建立 **Directory.build.props** 檔案，其中包含 `<LangVersion>` 元素來設定多個目錄。</span><span class="sxs-lookup"><span data-stu-id="43f23-163">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="43f23-164">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="43f23-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="43f23-165">將下列內容新增到解決方案目錄中的 **Directory.build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="43f23-165">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="43f23-166">現在，包含該檔案之目錄的每個子目錄中的組建將會使用 C# 版本 7.3 語法。</span><span class="sxs-lookup"><span data-stu-id="43f23-166">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="43f23-167">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build.md)。</span><span class="sxs-lookup"><span data-stu-id="43f23-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build.md).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="43f23-168">設定 langversion 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="43f23-168">Set the langversion compiler option</span></span>

<span data-ttu-id="43f23-169">您可以使用 `-langversion` 命令列選項。</span><span class="sxs-lookup"><span data-stu-id="43f23-169">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="43f23-170">如需詳細資訊，請參閱 [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) 編譯器選項的文章。</span><span class="sxs-lookup"><span data-stu-id="43f23-170">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="43f23-171">您可以藉由輸入 `csc -langversion:?`，看到有效值的清單。</span><span class="sxs-lookup"><span data-stu-id="43f23-171">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
