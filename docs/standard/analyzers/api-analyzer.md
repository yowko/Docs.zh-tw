---
title: .NET API 分析器
description: 了解「.NET API 分析器」如何協助偵測已被取代的 API 及平台相容性問題。
author: oliag
ms.author: mairaw
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 2d97921a3e98d85ac1e58c7686eadef3e979211f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107376"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="799ca-103">.NET API 分析器</span><span class="sxs-lookup"><span data-stu-id="799ca-103">.NET API analyzer</span></span>

<span data-ttu-id="799ca-104">「.NET API 分析器」是一個 Roslyn 分析器，可探索不同平台上 C# API 的潛在相容性風險，並偵測對已被取代之 API 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="799ca-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="799ca-105">對於任何開發階段的所有 C# 開發人員來說，都是相當實用的工具。</span><span class="sxs-lookup"><span data-stu-id="799ca-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="799ca-106">「API 分析器」是以 NuGet 套件 [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/) 的形式提供。</span><span class="sxs-lookup"><span data-stu-id="799ca-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="799ca-107">在您於專案中參考它之後，它就會自動監視程式碼並指出有問題的 API 使用情況。</span><span class="sxs-lookup"><span data-stu-id="799ca-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="799ca-108">您也可以按一下燈泡圖示來取得可能之修正的相關建議。</span><span class="sxs-lookup"><span data-stu-id="799ca-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="799ca-109">下拉式功能表中有包含隱藏警告的選項。</span><span class="sxs-lookup"><span data-stu-id="799ca-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="799ca-110">.NET API 分析器目前仍然是發行前版本。</span><span class="sxs-lookup"><span data-stu-id="799ca-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="799ca-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="799ca-111">Prerequisites</span></span>

- <span data-ttu-id="799ca-112">Visual Studio 2017 及更新版本，或 Visual Studio for Mac (所有版本)。</span><span class="sxs-lookup"><span data-stu-id="799ca-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="799ca-113">探索已被取代的 API</span><span class="sxs-lookup"><span data-stu-id="799ca-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="799ca-114">什麼是已被取代的 API？</span><span class="sxs-lookup"><span data-stu-id="799ca-114">What are deprecated APIs?</span></span>

<span data-ttu-id="799ca-115">.NET 系列是一組不斷升級來更加滿足客戶需求的大型產品。</span><span class="sxs-lookup"><span data-stu-id="799ca-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="799ca-116">很自然地會淘汰一些 API 並以新的 API 取而代之。</span><span class="sxs-lookup"><span data-stu-id="799ca-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="799ca-117">當一個 API 有更好的替代方案存在時，即可視為被取代。</span><span class="sxs-lookup"><span data-stu-id="799ca-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="799ca-118">其中一個通知使用者某個 API 已被取代而不應使用的方式，就是使用 <xref:System.ObsoleteAttribute> 屬性來標示它。</span><span class="sxs-lookup"><span data-stu-id="799ca-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="799ca-119">此方法的缺點是所有已淘汰的 API 只有一個診斷識別碼 (就 C# 而言為 [CS0612](../../csharp/misc/cs0612.md))。</span><span class="sxs-lookup"><span data-stu-id="799ca-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="799ca-120">這表示：</span><span class="sxs-lookup"><span data-stu-id="799ca-120">This means that:</span></span>
- <span data-ttu-id="799ca-121">無法讓每個案例都有專用的文件。</span><span class="sxs-lookup"><span data-stu-id="799ca-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="799ca-122">無法隱藏特定類別的警告。</span><span class="sxs-lookup"><span data-stu-id="799ca-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="799ca-123">您可以隱藏所有警告或全部不隱藏。</span><span class="sxs-lookup"><span data-stu-id="799ca-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="799ca-124">若要通知使用者有新的取代項目，就必須更新參考的組件或目標套件。</span><span class="sxs-lookup"><span data-stu-id="799ca-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="799ca-125">「API 分析器」會使用 API 特定的錯誤碼，其開頭為 DE (代表 Deprecation Error，即「取代錯誤」)，可用來控制個別警示的顯示。</span><span class="sxs-lookup"><span data-stu-id="799ca-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="799ca-126">[dotnet/platform-compat](https://github.com/dotnet/platform-compat) \(英文\) 存放庫中定義了分析器所識別的已被取代 API。</span><span class="sxs-lookup"><span data-stu-id="799ca-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="799ca-127">使用 API 分析器</span><span class="sxs-lookup"><span data-stu-id="799ca-127">Using the API Analyzer</span></span>

<span data-ttu-id="799ca-128">當程式碼中使用已被取代的 API (例如 <xref:System.Net.WebClient>) 時，「API 分析器」會使用綠色曲線來醒目標示它。</span><span class="sxs-lookup"><span data-stu-id="799ca-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="799ca-129">當您將滑鼠游標暫留在該 API 呼叫上時，會顯示燈泡圖示及有關該 API 取代的資訊，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="799ca-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

![「帶有綠色曲線的 WebClient API 及左邊有燈泡圖示的螢幕擷取畫面」](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="799ca-131">[錯誤清單]  視窗會包含警告，其中每個已被取代的 API 都會有一個唯一識別碼 ，如以下範例所示 (`DE004`)：</span><span class="sxs-lookup"><span data-stu-id="799ca-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

<span data-ttu-id="799ca-132">![「顯示警告之識別碼和描述的 [錯誤清單] 視窗螢幕擷取畫面」](media/api-analyzer/warnings-id-and-descriptions.jpg "包含警告的 [錯誤清單] 視窗。")</span><span class="sxs-lookup"><span data-stu-id="799ca-132">!["Screenshot of the Error List window showing warning's ID and description"](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="799ca-133">藉由按一下識別碼，您便可以前往含有詳細資訊的網頁，當中會說明 API 被取代的原因，並提供有關可使用之替代 API 的建議。</span><span class="sxs-lookup"><span data-stu-id="799ca-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="799ca-134">若要隱藏任何警告，只要在已醒目標示的成員上按一下滑鼠右鍵，然後選取 [隱藏 \<診斷識別碼>]  即可。</span><span class="sxs-lookup"><span data-stu-id="799ca-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="799ca-135">有兩種隱藏警告的方式：</span><span class="sxs-lookup"><span data-stu-id="799ca-135">There are two ways to suppress warnings:</span></span> 

- [<span data-ttu-id="799ca-136">本機 (在原始程式檔中)</span><span class="sxs-lookup"><span data-stu-id="799ca-136">locally (in source)</span></span>](#suppressing-warnings-locally)
- <span data-ttu-id="799ca-137">[全域 (在隱藏項目檔中)](#suppressing-warnings-globally) - 建議使用</span><span class="sxs-lookup"><span data-stu-id="799ca-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="799ca-138">在本機隱藏警告</span><span class="sxs-lookup"><span data-stu-id="799ca-138">Suppressing warnings locally</span></span>

<span data-ttu-id="799ca-139">若要在本機隱藏警告，請在您想要隱藏警告的成員上按一下滑鼠右鍵，然後選取 [快速動作與重構]   > [隱藏診斷識別碼 \<診斷識別碼>]   > [在原始程式檔中]  。</span><span class="sxs-lookup"><span data-stu-id="799ca-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="799ca-140">[#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) 警告前置處理器指示詞會新增到您所定義範圍中的原始程式碼：![「以 #pragma warning disable 括住之程式碼的螢幕擷取畫面」](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="799ca-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="799ca-141">在全域隱藏警告</span><span class="sxs-lookup"><span data-stu-id="799ca-141">Suppressing warnings globally</span></span>

<span data-ttu-id="799ca-142">若要在全域隱藏警告，請在您想要隱藏警告的成員上按一下滑鼠右鍵，然後選取 [快速動作與重構]   > [隱藏診斷識別碼 \<診斷識別碼>]   > [在隱藏項目檔中]  。</span><span class="sxs-lookup"><span data-stu-id="799ca-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

![「帶有綠色曲線的 WebClient API 及左邊有燈泡圖示的螢幕擷取畫面」](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="799ca-144">*GlobalSuppressions.cs* 檔案會在第一次隱藏之後新增到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="799ca-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="799ca-145">新的全域隱藏會附加到這個檔案。</span><span class="sxs-lookup"><span data-stu-id="799ca-145">New global suppressions are appended to this file.</span></span>

![「帶有綠色曲線的 WebClient API 及左邊有燈泡圖示的螢幕擷取畫面」](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="799ca-147">全域隱藏式建議的使用方式，可確保所有專案的 API 使用方式一致。</span><span class="sxs-lookup"><span data-stu-id="799ca-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="799ca-148">探索跨平台問題</span><span class="sxs-lookup"><span data-stu-id="799ca-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="799ca-149">與已被取代的 API 類似，分析器會識別所有不是跨平台的 API。</span><span class="sxs-lookup"><span data-stu-id="799ca-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="799ca-150">例如，<xref:System.Console.WindowWidth?displayProperty=nameWithType>可在 Windows 上運作，但無法在 Linux 和 macOS 上運作。</span><span class="sxs-lookup"><span data-stu-id="799ca-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="799ca-151">診斷識別碼會顯示在 [錯誤清單]  視窗中。</span><span class="sxs-lookup"><span data-stu-id="799ca-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="799ca-152">您可以按一下滑鼠右鍵並選取 [快速動作與重構]  來隱藏該警示。</span><span class="sxs-lookup"><span data-stu-id="799ca-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="799ca-153">與有兩個選項 (繼續使用已被取代的成員並隱藏警告，或完全不使用它) 的取代案例不同，在這裡，如果您僅針對特定平台來開發程式碼，就可以隱藏您不打算用來執行程式碼之所有其他平台的所有警告。</span><span class="sxs-lookup"><span data-stu-id="799ca-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="799ca-154">若要這樣做，您只需編輯專案檔，然後新增 `PlatformCompatIgnore` 屬性來列出所有要忽略的平台即可。</span><span class="sxs-lookup"><span data-stu-id="799ca-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="799ca-155">接受的值包括：`Linux`、`macOS` 及 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="799ca-155">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="799ca-156">如果您的程式碼以多個平台為目標，而您想要利用其中某些平台所不支援的 API，就可以使用 `if` 陳述式來保護該部分的程式碼：</span><span class="sxs-lookup"><span data-stu-id="799ca-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="799ca-157">您也可以有條件地依目標架構/作業系統進行編譯，但目前必須以[手動方式](../frameworks.md#how-to-specify-target-frameworks)執行。</span><span class="sxs-lookup"><span data-stu-id="799ca-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="799ca-158">支援的診斷</span><span class="sxs-lookup"><span data-stu-id="799ca-158">Supported diagnostics</span></span>

<span data-ttu-id="799ca-159">目前，分析器可處理下列情況：</span><span class="sxs-lookup"><span data-stu-id="799ca-159">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="799ca-160">使用擲回 <xref:System.PlatformNotSupportedException> 的 .NET Standard API (PC001)。</span><span class="sxs-lookup"><span data-stu-id="799ca-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="799ca-161">使用 .NET Framework 4.6.1 上未提供的.NET Standard API (PC002)。</span><span class="sxs-lookup"><span data-stu-id="799ca-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="799ca-162">使用 UWP 中所沒有的原生 API (PC003)。</span><span class="sxs-lookup"><span data-stu-id="799ca-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
- <span data-ttu-id="799ca-163">Delegate.BeginInvoke 及 EndInvoke API 的使用方式 (PC004)。</span><span class="sxs-lookup"><span data-stu-id="799ca-163">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="799ca-164">使用標示為已被取代的 API (DEXXXX)。</span><span class="sxs-lookup"><span data-stu-id="799ca-164">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="799ca-165">CI 電腦</span><span class="sxs-lookup"><span data-stu-id="799ca-165">CI machine</span></span>

<span data-ttu-id="799ca-166">所有這些診斷不僅在 IDE 中有提供，在組建專案過程中的命令列上也有提供，其中包括 CI 伺服器。</span><span class="sxs-lookup"><span data-stu-id="799ca-166">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="799ca-167">Configuration</span><span class="sxs-lookup"><span data-stu-id="799ca-167">Configuration</span></span>

<span data-ttu-id="799ca-168">使用者可決定診斷的處理方式：視為警告、錯誤、建議，或將其關閉。</span><span class="sxs-lookup"><span data-stu-id="799ca-168">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="799ca-169">例如，如果您是架構設計人員，就可以決定應將相容性問題視為錯誤，讓對一些已被取代之 API 的呼叫產生警告，而其他則只產生建議。</span><span class="sxs-lookup"><span data-stu-id="799ca-169">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="799ca-170">您可以依診斷識別碼及依專案分別進行此設定。</span><span class="sxs-lookup"><span data-stu-id="799ca-170">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="799ca-171">若要這樣做，請在 [方案總管]  中，瀏覽至您專案底下的 [相依性]  節點。</span><span class="sxs-lookup"><span data-stu-id="799ca-171">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="799ca-172">展開 [相依性]   > [分析器]   > [Microsoft.DotNet.Analyzers.Compatibility]  節點。</span><span class="sxs-lookup"><span data-stu-id="799ca-172">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="799ca-173">在診斷識別碼上按一下滑鼠右鍵，選取 [設定規則集合嚴重性]  ，然後挑選想要的選項。</span><span class="sxs-lookup"><span data-stu-id="799ca-173">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

![「顯示診斷及含規則集合嚴重性的快顯對話方塊之方案總管的螢幕擷取畫面」](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="799ca-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="799ca-175">See also</span></span>

- <span data-ttu-id="799ca-176">[API 分析器簡介](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) \(英文\) 部落格文章。</span><span class="sxs-lookup"><span data-stu-id="799ca-176">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="799ca-177">YouTube 上的 [API 分析器](https://youtu.be/eeBEahYXGd0)示範影片。</span><span class="sxs-lookup"><span data-stu-id="799ca-177">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
