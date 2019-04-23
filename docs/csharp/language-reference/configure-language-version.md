---
title: 選取 C# 語言版本 - C# 指南
description: 設定編譯器以特定的編譯器版本執行語法驗證
ms.date: 02/28/2019
ms.openlocfilehash: feb3e51a107f9830071b55c7985f202edc842f4a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770876"
---
# <a name="select-the-c-language-version"></a><span data-ttu-id="78b57-103">選取 C# 語言版本</span><span class="sxs-lookup"><span data-stu-id="78b57-103">Select the C# language version</span></span>

<span data-ttu-id="78b57-104">C# 編譯器會根據您專案的目標架構判斷預設語言版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="78b57-105">當您的專案是以具有對應預覽語言版本為目標的預覽架構時，所使用的語言版本將會是預覽語言版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-105">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="78b57-106">當您的專案不以預覽架構作為目標時，所使用的語言版本將會是最新的次要版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-106">When your project doesn't target a preview framework, the language version used is the latest minor version.</span></span>

<span data-ttu-id="78b57-107">例如，在 .NET Core 3.0 的預覽期間，以 `netcoreapp3.0` 或 `netstandard2.1` (兩者皆處於預覽狀態) 為目標的任何物件都將會使用 C# 8.0 語言 (同樣也處於預覽狀態)。</span><span class="sxs-lookup"><span data-stu-id="78b57-107">For example, during the preview period for .NET Core 3.0, any project that targets `netcoreapp3.0` or `netstandard2.1` (both in preview) will use the C# 8.0 language (also in preview).</span></span> <span data-ttu-id="78b57-108">以任何已發行版本為目標的專案將會使用 C# 7.3 (最新的已發行版本)。</span><span class="sxs-lookup"><span data-stu-id="78b57-108">Projects targeting any released version will use C# 7.3 (the latest released version).</span></span> <span data-ttu-id="78b57-109">此行為代表以 .NET Framework 為目標的任何專案都會使用最新版本 (C# 7.3)。</span><span class="sxs-lookup"><span data-stu-id="78b57-109">This behavior means that any project targeting .NET Framework will use latest (C# 7.3).</span></span> 

<span data-ttu-id="78b57-110">此功能可讓在您開發環境中決定安裝新版本的 SDK 和工具，與在專案中決定納入新語言功能這兩件事分開。</span><span class="sxs-lookup"><span data-stu-id="78b57-110">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="78b57-111">您可以在組建電腦上安裝最新的 SDK 和工具。</span><span class="sxs-lookup"><span data-stu-id="78b57-111">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="78b57-112">每個專案可以設定為針對其組建使用特定版本的語言。</span><span class="sxs-lookup"><span data-stu-id="78b57-112">Each project can be configured to use a specific version of the language for its build.</span></span> <span data-ttu-id="78b57-113">預設行為代表仰賴新類型或新 CLR 行為的任何語言功能，都只會在專案以那些架構作為目標時才會啟用。</span><span class="sxs-lookup"><span data-stu-id="78b57-113">The default behavior means that any language features that rely on new types or new CLR behavior are enabled only when projects target those frameworks.</span></span>

<span data-ttu-id="78b57-114">您可以透過指定語言版本來覆寫預設行為。</span><span class="sxs-lookup"><span data-stu-id="78b57-114">You can override the default behavior by specifying a language version.</span></span> <span data-ttu-id="78b57-115">有數種方法可以設定語言版本：</span><span class="sxs-lookup"><span data-stu-id="78b57-115">There are several ways to set the language version:</span></span>

- <span data-ttu-id="78b57-116">依賴 [Visual Studio 快速動作](#visual-studio-quick-action)。</span><span class="sxs-lookup"><span data-stu-id="78b57-116">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="78b57-117">在 [Visual Studio UI](#set-the-language-version-in-visual-studio) 中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-117">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="78b57-118">手動編輯您的 [**.csproj** 檔案](#edit-the-csproj-file)。</span><span class="sxs-lookup"><span data-stu-id="78b57-118">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="78b57-119">針對[子目錄中的多個專案](#configure-multiple-projects)設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-119">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="78b57-120">設定 [`-langversion`編譯器選項](#set-the-langversion-compiler-option)。</span><span class="sxs-lookup"><span data-stu-id="78b57-120">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="78b57-121">Visual Studio 快速動作</span><span class="sxs-lookup"><span data-stu-id="78b57-121">Visual Studio quick action</span></span>

<span data-ttu-id="78b57-122">Visual Studio 可協助您判斷您需要的語言版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-122">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="78b57-123">如果您使用不適用於目前設定版本的語言功能，Visual Studio 會顯示可能的修正，以更新專案的語言版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-123">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="78b57-124">在 Visual Studio 中設定語言版本</span><span class="sxs-lookup"><span data-stu-id="78b57-124">Set the language version in Visual Studio</span></span>

<span data-ttu-id="78b57-125">您可以在 Visual Studio 中設定版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-125">You can set the version in Visual Studio.</span></span> <span data-ttu-id="78b57-126">以滑鼠右鍵按一下 [方案總管] 的專案節點，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="78b57-126">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="78b57-127">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="78b57-127">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="78b57-128">在下拉式清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-128">In the dropdown, select the version.</span></span> <span data-ttu-id="78b57-129">下圖顯示「最新」設定︰</span><span class="sxs-lookup"><span data-stu-id="78b57-129">The following image shows the "latest" setting:</span></span>

![進階組建設定的螢幕擷取畫面，您可以在其中指定語言版本](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="78b57-131">如果您使用 Visual Studio IDE 來更新 csproj 檔，IDE 會為每個組建組態建立個別的節點。</span><span class="sxs-lookup"><span data-stu-id="78b57-131">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="78b57-132">您一般會在所有組建組態中設定相同的值，但您需要針對每個組建組態明確設定，或在修改此設定時選取 [所有組態]。</span><span class="sxs-lookup"><span data-stu-id="78b57-132">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="78b57-133">您會在 csproj 檔案中看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="78b57-133">You'll see the following in your csproj file:</span></span>
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

## <a name="edit-the-csproj-file"></a><span data-ttu-id="78b57-134">編輯 csproj 檔案</span><span class="sxs-lookup"><span data-stu-id="78b57-134">Edit the csproj file</span></span>

<span data-ttu-id="78b57-135">您可以在 **.csproj** 檔案中設定語言版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-135">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="78b57-136">如下所示新增元素：</span><span class="sxs-lookup"><span data-stu-id="78b57-136">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="78b57-137">`latest` 值使用 C# 語言的最新次要版本。</span><span class="sxs-lookup"><span data-stu-id="78b57-137">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="78b57-138">有效值為：</span><span class="sxs-lookup"><span data-stu-id="78b57-138">Valid values are:</span></span>

|<span data-ttu-id="78b57-139">值</span><span class="sxs-lookup"><span data-stu-id="78b57-139">Value</span></span>|<span data-ttu-id="78b57-140">意義</span><span class="sxs-lookup"><span data-stu-id="78b57-140">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="78b57-141">preview</span><span class="sxs-lookup"><span data-stu-id="78b57-141">preview</span></span>|<span data-ttu-id="78b57-142">編譯器會接受最新預覽版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-142">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="78b57-143">latest</span><span class="sxs-lookup"><span data-stu-id="78b57-143">latest</span></span>|<span data-ttu-id="78b57-144">編譯器會接受編譯器最新已發行版本 (包括次要版本) 的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-144">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="78b57-145">latestMajor</span><span class="sxs-lookup"><span data-stu-id="78b57-145">latestMajor</span></span>|<span data-ttu-id="78b57-146">編譯器會接受編譯器最新已發行主要版本的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-146">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="78b57-147">8.0</span><span class="sxs-lookup"><span data-stu-id="78b57-147">8.0</span></span>|<span data-ttu-id="78b57-148">編譯器只會接受 C# 8.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-148">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="78b57-149">7.3</span><span class="sxs-lookup"><span data-stu-id="78b57-149">7.3</span></span>|<span data-ttu-id="78b57-150">編譯器只會接受 C# 7.3 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-150">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="78b57-151">7.2</span><span class="sxs-lookup"><span data-stu-id="78b57-151">7.2</span></span>|<span data-ttu-id="78b57-152">編譯器只會接受 C# 7.2 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-152">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="78b57-153">7.1</span><span class="sxs-lookup"><span data-stu-id="78b57-153">7.1</span></span>|<span data-ttu-id="78b57-154">編譯器只會接受 C# 7.1 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="78b57-155">7</span><span class="sxs-lookup"><span data-stu-id="78b57-155">7</span></span>|<span data-ttu-id="78b57-156">編譯器只會接受 C# 7.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-156">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="78b57-157">6</span><span class="sxs-lookup"><span data-stu-id="78b57-157">6</span></span>|<span data-ttu-id="78b57-158">編譯器只會接受 C# 6.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-158">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="78b57-159">5</span><span class="sxs-lookup"><span data-stu-id="78b57-159">5</span></span>|<span data-ttu-id="78b57-160">編譯器只會接受 C# 5.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-160">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="78b57-161">4</span><span class="sxs-lookup"><span data-stu-id="78b57-161">4</span></span>|<span data-ttu-id="78b57-162">編譯器只會接受 C# 4.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-162">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="78b57-163">3</span><span class="sxs-lookup"><span data-stu-id="78b57-163">3</span></span>|<span data-ttu-id="78b57-164">編譯器只會接受 C# 3.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-164">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="78b57-165">ISO-2</span><span class="sxs-lookup"><span data-stu-id="78b57-165">ISO-2</span></span>|<span data-ttu-id="78b57-166">編譯器只會接受 ISO/IEC 23270:2006 C# (2.0) 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="78b57-166">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="78b57-167">ISO-1</span><span class="sxs-lookup"><span data-stu-id="78b57-167">ISO-1</span></span>|<span data-ttu-id="78b57-168">編譯器只會接受 ISO/IEC 23270:2003 C# (1.0/1.2) 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="78b57-168">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |

## <a name="configure-multiple-projects"></a><span data-ttu-id="78b57-169">設定多個專案</span><span class="sxs-lookup"><span data-stu-id="78b57-169">Configure multiple projects</span></span>

<span data-ttu-id="78b57-170">您可以建立 **Directory.Build.props** 檔案，其中包含 `<LangVersion>` 元素來設定多個目錄。</span><span class="sxs-lookup"><span data-stu-id="78b57-170">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="78b57-171">您通常會在解決方案目錄中進行。</span><span class="sxs-lookup"><span data-stu-id="78b57-171">You typically do that in your solution directory.</span></span> <span data-ttu-id="78b57-172">將下列內容新增到解決方案目錄中的 **Directory.Build.props** 檔案：</span><span class="sxs-lookup"><span data-stu-id="78b57-172">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="78b57-173">現在，包含該檔案之目錄的每個子目錄中的組建將會使用 C# 版本 7.3 語法。</span><span class="sxs-lookup"><span data-stu-id="78b57-173">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="78b57-174">如需詳細資訊，請參閱[自訂組建](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="78b57-174">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="78b57-175">設定 langversion 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="78b57-175">Set the langversion compiler option</span></span>

<span data-ttu-id="78b57-176">您可以使用 `-langversion` 命令列選項。</span><span class="sxs-lookup"><span data-stu-id="78b57-176">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="78b57-177">如需詳細資訊，請參閱 [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) 編譯器選項的文章。</span><span class="sxs-lookup"><span data-stu-id="78b57-177">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="78b57-178">您可以藉由輸入 `csc -langversion:?`，看到有效值的清單。</span><span class="sxs-lookup"><span data-stu-id="78b57-178">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
