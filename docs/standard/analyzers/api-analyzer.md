---
title: .NET API 分析器
description: 了解「.NET API 分析器」如何協助偵測已被取代的 API 及平台相容性問題。
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 8da4b2add206daa431124a7d24efc2676cbcaa69
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598090"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="ba4fc-103">.NET API 分析器</span><span class="sxs-lookup"><span data-stu-id="ba4fc-103">.NET API analyzer</span></span>

<span data-ttu-id="ba4fc-104">「.NET API 分析器」是一個 Roslyn 分析器，可探索不同平台上 C# API 的潛在相容性風險，並偵測對已被取代之 API 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="ba4fc-105">對於任何開發階段的所有 C# 開發人員來說，都是相當實用的工具。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="ba4fc-106">「API 分析器」是以 NuGet 套件 [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/) 的形式提供。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="ba4fc-107">在您於專案中參考它之後，它就會自動監視程式碼並指出有問題的 API 使用情況。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="ba4fc-108">您也可以按一下燈泡圖示來取得可能之修正的相關建議。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="ba4fc-109">下拉式功能表中有包含隱藏警告的選項。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="ba4fc-110">.NET API 分析器目前仍然是發行前版本。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba4fc-111">先決條件</span><span class="sxs-lookup"><span data-stu-id="ba4fc-111">Prerequisites</span></span>

- <span data-ttu-id="ba4fc-112">Visual Studio 2017 及更新版本，或 Visual Studio for Mac (所有版本)。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discover-deprecated-apis"></a><span data-ttu-id="ba4fc-113">探索已淘汰的 Api</span><span class="sxs-lookup"><span data-stu-id="ba4fc-113">Discover deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="ba4fc-114">什麼是已被取代的 API？</span><span class="sxs-lookup"><span data-stu-id="ba4fc-114">What are deprecated APIs?</span></span>

<span data-ttu-id="ba4fc-115">.NET 系列是一組不斷升級來更加滿足客戶需求的大型產品。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="ba4fc-116">很自然地會淘汰一些 API 並以新的 API 取而代之。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="ba4fc-117">當一個 API 有更好的替代方案存在時，即可視為被取代。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="ba4fc-118">其中一個通知使用者某個 API 已被取代而不應使用的方式，就是使用 <xref:System.ObsoleteAttribute> 屬性來標示它。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="ba4fc-119">此方法的缺點是所有已淘汰的 API 只有一個診斷識別碼 (就 C# 而言為 [CS0612](../../csharp/misc/cs0612.md))。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="ba4fc-120">這表示：</span><span class="sxs-lookup"><span data-stu-id="ba4fc-120">This means that:</span></span>

- <span data-ttu-id="ba4fc-121">無法讓每個案例都有專用的文件。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="ba4fc-122">無法隱藏特定類別的警告。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="ba4fc-123">您可以隱藏所有警告或全部不隱藏。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="ba4fc-124">若要通知使用者有新的取代項目，就必須更新參考的組件或目標套件。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="ba4fc-125">「API 分析器」會使用 API 特定的錯誤碼，其開頭為 DE (代表 Deprecation Error，即「取代錯誤」)，可用來控制個別警示的顯示。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="ba4fc-126">[dotnet/platform-compat](https://github.com/dotnet/platform-compat) \(英文\) 存放庫中定義了分析器所識別的已被取代 API。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="add-the-api-analyzer-to-your-project"></a><span data-ttu-id="ba4fc-127">將 API 分析器新增至您的專案</span><span class="sxs-lookup"><span data-stu-id="ba4fc-127">Add the API Analyzer to your project</span></span>

1. <span data-ttu-id="ba4fc-128">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-128">Open Visual Studio.</span></span>
2. <span data-ttu-id="ba4fc-129">開啟您想要執行分析器的專案。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-129">Open the project you want to run the analyzer on.</span></span>
3. <span data-ttu-id="ba4fc-130">在 **方案總管**中，以滑鼠右鍵按一下您的專案，然後選擇 [ **管理 NuGet 套件**]。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-130">In **Solution Explorer**, right-click on your project and choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="ba4fc-131">(這個選項也可以在 [專案]\*\*\*\* 功能表中取得)。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-131">(This option is also available from the **Project** menu.)</span></span>
4. <span data-ttu-id="ba4fc-132">在 [NuGet 封裝管理員] 索引標籤上：</span><span class="sxs-lookup"><span data-stu-id="ba4fc-132">On the NuGet Package Manager tab:</span></span>
   1. <span data-ttu-id="ba4fc-133">選取 "nuget.org" 作為套件來源。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-133">Select "nuget.org" as the Package source.</span></span>
   2. <span data-ttu-id="ba4fc-134">移至 [ **流覽** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-134">Go to the **Browse** tab.</span></span>
   3. <span data-ttu-id="ba4fc-135">選取 [包括發行前版本]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-135">Select **Include prerelease**.</span></span>
   4. <span data-ttu-id="ba4fc-136">搜尋 **DotNet 的相容性**。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-136">Search for **Microsoft.DotNet.Analyzers.Compatibility**.</span></span>
   5. <span data-ttu-id="ba4fc-137">在清單中選取該套件。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-137">Select that package in the list.</span></span>
   6. <span data-ttu-id="ba4fc-138">選取 [安裝]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-138">Select the **Install** button.</span></span>
   7. <span data-ttu-id="ba4fc-139">在 [預覽變更]\*\*\*\* 對話方塊上，選取 [確定]\*\*\*\* 按鈕，然後在 [授權接受]\*\*\*\* 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="use-the-api-analyzer"></a><span data-ttu-id="ba4fc-140">使用 API 分析器</span><span class="sxs-lookup"><span data-stu-id="ba4fc-140">Use the API Analyzer</span></span>

<span data-ttu-id="ba4fc-141">當程式碼中使用已被取代的 API (例如 <xref:System.Net.WebClient>) 時，「API 分析器」會使用綠色曲線來醒目標示它。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-141">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="ba4fc-142">當您將滑鼠游標暫留在該 API 呼叫上時，會顯示燈泡圖示及有關該 API 取代的資訊，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="ba4fc-142">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

![以綠色波浪線和左邊燈泡的 WebClient API 螢幕擷取畫面。](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="ba4fc-144">[錯誤清單]\*\*\*\* 視窗會包含警告，其中每個已被取代的 API 都會有一個唯一識別碼 ，如以下範例所示 (`DE004`)：</span><span class="sxs-lookup"><span data-stu-id="ba4fc-144">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span>

<span data-ttu-id="ba4fc-145">![顯示警告識別碼和描述的 [錯誤清單] 視窗螢幕擷取畫面。](media/api-analyzer/warnings-id-and-descriptions.jpg "包含警告的 [錯誤清單] 視窗。")</span><span class="sxs-lookup"><span data-stu-id="ba4fc-145">![Screenshot of the Error List window showing warning's ID and description.](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="ba4fc-146">藉由按一下識別碼，您便可以前往含有詳細資訊的網頁，當中會說明 API 被取代的原因，並提供有關可使用之替代 API 的建議。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-146">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="ba4fc-147">以滑鼠右鍵按一下反白顯示的成員，然後選取 [\*\*隱藏 \<diagnostic ID> \*\*]，即可隱藏任何警告。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-147">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="ba4fc-148">有兩種隱藏警告的方式：</span><span class="sxs-lookup"><span data-stu-id="ba4fc-148">There are two ways to suppress warnings:</span></span>

- [<span data-ttu-id="ba4fc-149">本機 (在原始程式檔中)</span><span class="sxs-lookup"><span data-stu-id="ba4fc-149">locally (in source)</span></span>](#suppress-warnings-locally)
- <span data-ttu-id="ba4fc-150">[全域 (在隱藏項目檔中)](#suppress-warnings-globally) - 建議使用</span><span class="sxs-lookup"><span data-stu-id="ba4fc-150">[globally (in a suppression file)](#suppress-warnings-globally) - recommended</span></span>

### <a name="suppress-warnings-locally"></a><span data-ttu-id="ba4fc-151">在本機隱藏警告</span><span class="sxs-lookup"><span data-stu-id="ba4fc-151">Suppress warnings locally</span></span>

<span data-ttu-id="ba4fc-152">若要在本機隱藏警告，請在您想要隱藏警告的成員上按一下滑鼠右鍵，然後選取 [**快速動作] 和 [重構**  >  隱藏來源中的\*\**診斷識別碼* \<diagnostic ID> \*\*]  >  \*\* \*\*。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-152">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="ba4fc-153">[#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)警告預處理器指示詞會新增至您在定義範圍中的原始程式碼：已 ![ 停用 #pragma 警告的程式碼螢幕擷取畫面。](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba4fc-153">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: ![Screenshot of code framed with #pragma warning disable.](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppress-warnings-globally"></a><span data-ttu-id="ba4fc-154">全域隱藏警告</span><span class="sxs-lookup"><span data-stu-id="ba4fc-154">Suppress warnings globally</span></span>

<span data-ttu-id="ba4fc-155">若要全域隱藏警告，請在您想要隱藏警告的成員上按一下滑鼠右鍵，然後選取 [**快速動作] 和 [重構**隱藏隱藏專案檔中的  >  \*\**診斷識別碼* \<diagnostic ID> \*\*]  >  \*\* \*\*。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-155">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

![滑鼠右鍵功能表的螢幕擷取畫面，其中顯示在 Visual Studio 中隱藏警告的選項。](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="ba4fc-157">*GlobalSuppressions.cs* 檔案會在第一次隱藏之後新增到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-157">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="ba4fc-158">新的全域隱藏會附加到這個檔案。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-158">New global suppressions are appended to this file.</span></span>

![方案總管中 GlobalSuppressions.cs 檔案的螢幕擷取畫面。](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="ba4fc-160">全域隱藏式建議的使用方式，可確保所有專案的 API 使用方式一致。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-160">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discover-cross-platform-issues"></a><span data-ttu-id="ba4fc-161">探索跨平臺問題</span><span class="sxs-lookup"><span data-stu-id="ba4fc-161">Discover cross-platform issues</span></span>

<span data-ttu-id="ba4fc-162">與已被取代的 API 類似，分析器會識別所有不是跨平台的 API。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-162">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="ba4fc-163">例如，<xref:System.Console.WindowWidth?displayProperty=nameWithType>可在 Windows 上運作，但無法在 Linux 和 macOS 上運作。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-163">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="ba4fc-164">診斷識別碼會顯示在 [錯誤清單]\*\*\*\* 視窗中。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-164">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="ba4fc-165">您可以按一下滑鼠右鍵並選取 [快速動作與重構]\*\*\*\* 來隱藏該警示。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-165">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="ba4fc-166">與有兩個選項 (繼續使用已被取代的成員並隱藏警告，或完全不使用它) 的取代案例不同，在這裡，如果您僅針對特定平台來開發程式碼，就可以隱藏您不打算用來執行程式碼之所有其他平台的所有警告。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-166">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="ba4fc-167">若要這樣做，您只需編輯專案檔，然後新增 `PlatformCompatIgnore` 屬性來列出所有要忽略的平台即可。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-167">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="ba4fc-168">接受的值包括：`Linux`、`macOS` 及 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-168">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="ba4fc-169">如果您的程式碼以多個平台為目標，而您想要利用其中某些平台所不支援的 API，就可以使用 `if` 陳述式來保護該部分的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ba4fc-169">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="ba4fc-170">您也可以有條件地依目標架構/作業系統進行編譯，但目前必須以[手動方式](../frameworks.md#how-to-specify-a-target-framework)執行。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-170">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-a-target-framework).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="ba4fc-171">支援的診斷</span><span class="sxs-lookup"><span data-stu-id="ba4fc-171">Supported diagnostics</span></span>

<span data-ttu-id="ba4fc-172">目前，分析器可處理下列情況：</span><span class="sxs-lookup"><span data-stu-id="ba4fc-172">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="ba4fc-173">使用擲回 <xref:System.PlatformNotSupportedException> 的 .NET Standard API (PC001)。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-173">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="ba4fc-174">使用 .NET Framework 4.6.1 上未提供的.NET Standard API (PC002)。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-174">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="ba4fc-175">使用 UWP 中不存在的原生 API (PC003) 。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-175">Usage of a native API that doesn't exist in UWP (PC003).</span></span>
- <span data-ttu-id="ba4fc-176">Delegate.BeginInvoke 及 EndInvoke API 的使用方式 (PC004)。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-176">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="ba4fc-177">使用標示為已被取代的 API (DEXXXX)。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-177">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="ba4fc-178">CI 電腦</span><span class="sxs-lookup"><span data-stu-id="ba4fc-178">CI machine</span></span>

<span data-ttu-id="ba4fc-179">所有這些診斷不僅在 IDE 中有提供，在組建專案過程中的命令列上也有提供，其中包括 CI 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-179">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="ba4fc-180">設定</span><span class="sxs-lookup"><span data-stu-id="ba4fc-180">Configuration</span></span>

<span data-ttu-id="ba4fc-181">使用者可決定診斷的處理方式：視為警告、錯誤、建議，或將其關閉。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-181">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="ba4fc-182">例如，如果您是架構設計人員，就可以決定應將相容性問題視為錯誤，讓對一些已被取代之 API 的呼叫產生警告，而其他則只產生建議。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-182">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="ba4fc-183">您可以依診斷識別碼及依專案分別進行此設定。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-183">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="ba4fc-184">若要這樣做，請在 [方案總管]\*\*\*\* 中，瀏覽至您專案底下的 [相依性]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-184">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="ba4fc-185">展開 [節點**Dependencies**相依  >  性**分析器**]  >  **DotNet**。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-185">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="ba4fc-186">在診斷識別碼上按一下滑鼠右鍵，選取 [設定規則集合嚴重性]\*\*\*\*，然後挑選想要的選項。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-186">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

![方案總管的螢幕擷取畫面，顯示具有規則集嚴重性的診斷和快顯對話方塊。](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="ba4fc-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba4fc-188">See also</span></span>

- <span data-ttu-id="ba4fc-189">[API 分析器簡介](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) \(英文\) 部落格文章。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-189">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="ba4fc-190">YouTube 上的 [API 分析器](https://youtu.be/eeBEahYXGd0)示範影片。</span><span class="sxs-lookup"><span data-stu-id="ba4fc-190">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
