---
title: 將程式庫移植到 .NET Core
description: 了解如何將程式庫專案從 .NET Framework 移植到 .NET Core。
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: c7a770ba2da8c245ba9140852fc7c2a33a55f7a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660704"
---
# <a name="port-net-framework-libraries-to-net-core"></a><span data-ttu-id="bf2da-103">將 .NET Framework 程式庫移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="bf2da-103">Port .NET Framework libraries to .NET Core</span></span>

<span data-ttu-id="bf2da-104">了解如何將.NET Framework 程式庫程式碼移植到 .NET Core，以執行跨平台並擴展使用它的應用程式的範圍。</span><span class="sxs-lookup"><span data-stu-id="bf2da-104">Learn how to port .NET Framework library code to .NET Core, to run cross-platform and expand the reach of the apps that use it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bf2da-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="bf2da-105">Prerequisites</span></span>

<span data-ttu-id="bf2da-106">本文假設您已具備下列條件：</span><span class="sxs-lookup"><span data-stu-id="bf2da-106">This article assumes that you:</span></span>

- <span data-ttu-id="bf2da-107">使用 Visual Studio 2017 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="bf2da-107">Are using Visual Studio 2017 or later.</span></span>
  - <span data-ttu-id="bf2da-108">舊版 Visual Studio 不支援 .NET Core</span><span class="sxs-lookup"><span data-stu-id="bf2da-108">.NET Core isn't supported on earlier versions of Visual Studio</span></span>
- <span data-ttu-id="bf2da-109">了解[建議的移植程序](index.md)。</span><span class="sxs-lookup"><span data-stu-id="bf2da-109">Understand the [recommended porting process](index.md).</span></span>
- <span data-ttu-id="bf2da-110">已解決任何[協力廠商相依性](third-party-deps.md)問題。</span><span class="sxs-lookup"><span data-stu-id="bf2da-110">Have resolved any issues with [third-party dependencies](third-party-deps.md).</span></span>

<span data-ttu-id="bf2da-111">您也應該進一步熟悉下列主題的內容：</span><span class="sxs-lookup"><span data-stu-id="bf2da-111">You should also become familiar with the content of the following topics:</span></span>

<span data-ttu-id="bf2da-112">[.NET Standard](../../standard/net-standard.md)</span><span class="sxs-lookup"><span data-stu-id="bf2da-112">[.NET Standard](../../standard/net-standard.md)</span></span>\
<span data-ttu-id="bf2da-113">本主題描述計畫在所有 .NET 實作上提供的正式 .NET API 規格。</span><span class="sxs-lookup"><span data-stu-id="bf2da-113">This topic describes the formal specification of .NET APIs that are intended to be available on all .NET implementations.</span></span>

<span data-ttu-id="bf2da-114">[套件、中繼套件和架構](../packages.md) </span><span class="sxs-lookup"><span data-stu-id="bf2da-114">[Packages, Metapackages and Frameworks](../packages.md) </span></span>  
<span data-ttu-id="bf2da-115">本文討論 .NET Core 如何定義及使用套件，以及套件如何支援在多個 .NET 實作上執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2da-115">This article discusses how .NET Core defines and uses packages and how packages support code running on multiple .NET implementations.</span></span>

<span data-ttu-id="bf2da-116">[使用跨平台工具開發程式庫](../tutorials/libraries.md) </span><span class="sxs-lookup"><span data-stu-id="bf2da-116">[Developing Libraries with Cross Platform Tools](../tutorials/libraries.md) </span></span>  
<span data-ttu-id="bf2da-117">本主題說明如何使用跨平台 CLI 工具撰寫 .NET 的程式庫。</span><span class="sxs-lookup"><span data-stu-id="bf2da-117">This topic explains how to write libraries for .NET using cross-platform CLI tools.</span></span>

<span data-ttu-id="bf2da-118">[適用於 .NET Core 之 *csproj* 格式的新增項目](../tools/csproj.md) </span><span class="sxs-lookup"><span data-stu-id="bf2da-118">[Additions to the *csproj* format for .NET Core](../tools/csproj.md) </span></span>  
<span data-ttu-id="bf2da-119">本文概述從改為使用 *csproj* 和 MSBuild 時，新增至專案檔的變更。</span><span class="sxs-lookup"><span data-stu-id="bf2da-119">This article outlines the changes that were added to the project file as part of the move to *csproj* and MSBuild.</span></span>

<span data-ttu-id="bf2da-120">[移植到 .NET Core - 分析協力廠商相依性](third-party-deps.md) </span><span class="sxs-lookup"><span data-stu-id="bf2da-120">[Porting to .NET Core - Analyzing your Third-Party Party Dependencies](third-party-deps.md) </span></span>  
<span data-ttu-id="bf2da-121">本主題討論協力廠商相依性的可攜性，以及當某個 NuGet 套件相依性無法在 .NET Core 上執行時的解決方法。</span><span class="sxs-lookup"><span data-stu-id="bf2da-121">This topic discusses the portability of third-party dependencies and what to do when a NuGet package dependency doesn't run on .NET Core.</span></span>

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a><span data-ttu-id="bf2da-122">將您的 .NET Framework 程式碼目標重新設定為 .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="bf2da-122">Retargeting your .NET Framework code to .NET Framework 4.7.2</span></span>

<span data-ttu-id="bf2da-123">如果您的程式碼目標不是 .NET Framework 4.7.2，建議您將目標重新設定為 .NET Framework 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="bf2da-123">If your code isn't targeting .NET Framework 4.7.2, we recommended that you retarget to .NET Framework 4.7.2.</span></span> <span data-ttu-id="bf2da-124">這可確保在 .NET Standard 不支援現有 API 的情況下，仍可以使用最新的 API 替代項目。</span><span class="sxs-lookup"><span data-stu-id="bf2da-124">This ensures the availability of the latest API alternatives for cases where the .NET Standard doesn't support existing APIs.</span></span>

<span data-ttu-id="bf2da-125">針對您想要移轉的每個 Visual Studio 專案，執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="bf2da-125">For each of your projects in Visual Studio you wish to port, do the following:</span></span>

1. <span data-ttu-id="bf2da-126">以滑鼠右鍵按一下專案並選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="bf2da-126">Right-click on the project and select **Properties**.</span></span>
1. <span data-ttu-id="bf2da-127">在 [目標 Framework]  下拉式清單中，選取 [.NET Framework 4.7.2]  。</span><span class="sxs-lookup"><span data-stu-id="bf2da-127">In the **Target Framework** dropdown, select **.NET Framework 4.7.2**.</span></span>
1. <span data-ttu-id="bf2da-128">重新編譯您的專案。</span><span class="sxs-lookup"><span data-stu-id="bf2da-128">Recompile your projects.</span></span>

<span data-ttu-id="bf2da-129">因為您的專案現在是以 .NET Framework 4.7.2 為目標，請使用該版本的 .NET Framework 作為基礎移植程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2da-129">Because your projects now target .NET Framework 4.7.2, use that version of the .NET Framework as your base for porting code.</span></span>

## <a name="determining-the-portability-of-your-code"></a><span data-ttu-id="bf2da-130">判斷程式碼的可攜性</span><span class="sxs-lookup"><span data-stu-id="bf2da-130">Determining the portability of your code</span></span>

<span data-ttu-id="bf2da-131">下一個步驟是執行 API 可攜性分析器 (ApiPort)，以產生可用於分析的可攜性報告。</span><span class="sxs-lookup"><span data-stu-id="bf2da-131">The next step is to run the API Portability Analyzer (ApiPort) to generate a portability report for analysis.</span></span>

<span data-ttu-id="bf2da-132">請確定您了解 [API 可攜性分析器 (ApiPort)](../../standard/analyzers/portability-analyzer.md)，以及產生目標 .NET Core 之可攜性報告的方式。</span><span class="sxs-lookup"><span data-stu-id="bf2da-132">Make sure you understand the [API Portability Analyzer (ApiPort)](../../standard/analyzers/portability-analyzer.md) and how to generate portability reports for targeting .NET Core.</span></span> <span data-ttu-id="bf2da-133">作法因個人需求及品味而異。</span><span class="sxs-lookup"><span data-stu-id="bf2da-133">How you do this likely varies based on your needs and personal tastes.</span></span> <span data-ttu-id="bf2da-134">以下是幾種不同的方法。</span><span class="sxs-lookup"><span data-stu-id="bf2da-134">What follows are a few different approaches.</span></span> <span data-ttu-id="bf2da-135">根據您的程式碼架構，可以混合使用這些方法的步驟。</span><span class="sxs-lookup"><span data-stu-id="bf2da-135">You may find yourself mixing steps of these approaches depending on how your code is structured.</span></span>

### <a name="dealing-primarily-with-the-compiler"></a><span data-ttu-id="bf2da-136">主要以編譯器處理</span><span class="sxs-lookup"><span data-stu-id="bf2da-136">Dealing primarily with the compiler</span></span>

<span data-ttu-id="bf2da-137">這個方法大概最適合小型專案或不使用太多 .NET Framework API 的專案。</span><span class="sxs-lookup"><span data-stu-id="bf2da-137">This approach may be the best for small projects or projects which don't use many .NET Framework APIs.</span></span> <span data-ttu-id="bf2da-138">方法相當簡單︰</span><span class="sxs-lookup"><span data-stu-id="bf2da-138">The approach is simple:</span></span>

1. <span data-ttu-id="bf2da-139">對專案選擇性地執行 ApiPort。</span><span class="sxs-lookup"><span data-stu-id="bf2da-139">Optionally, run ApiPort on your project.</span></span> <span data-ttu-id="bf2da-140">如果執行 ApiPort，請透過報告取得需解決問題的相關知識。</span><span class="sxs-lookup"><span data-stu-id="bf2da-140">If you run ApiPort, gain knowledge from the report on issues you'll need to address.</span></span>
1. <span data-ttu-id="bf2da-141">將所有程式碼全部複製到新的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="bf2da-141">Copy all of your code over into a new .NET Core project.</span></span>
1. <span data-ttu-id="bf2da-142">在參考可攜性報告 (若有產生) 的同時，持續解決編譯器錯誤，直到專案可完整編譯為止。</span><span class="sxs-lookup"><span data-stu-id="bf2da-142">While referring to the portability report (if generated), solve compiler errors until the project fully compiles.</span></span>

<span data-ttu-id="bf2da-143">雖然此方法不夠有條理，但以程式碼為主的方法通常可以快速解決問題，而且可能是最適合小型專案或程式庫的方法。</span><span class="sxs-lookup"><span data-stu-id="bf2da-143">Although this approach is unstructured, the code-focused approach often leads to resolving issues quickly and might be the best approach for smaller projects or libraries.</span></span> <span data-ttu-id="bf2da-144">只包含資料模型的專案可能最適合此方法。</span><span class="sxs-lookup"><span data-stu-id="bf2da-144">A project that contains only data models might be an ideal candidate for this approach.</span></span>

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a><span data-ttu-id="bf2da-145">留在 .NET Framework 直到解決可攜性問題</span><span class="sxs-lookup"><span data-stu-id="bf2da-145">Staying on the .NET Framework until portability issues are resolved</span></span>

<span data-ttu-id="bf2da-146">如果您偏好在整個程序期間執行編譯的程式碼，這就是最佳方法。</span><span class="sxs-lookup"><span data-stu-id="bf2da-146">This approach might be the best if you prefer to have code that compiles during the entire process.</span></span> <span data-ttu-id="bf2da-147">方法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="bf2da-147">The approach is as follows:</span></span>

1. <span data-ttu-id="bf2da-148">對專案執行 ApiPort。</span><span class="sxs-lookup"><span data-stu-id="bf2da-148">Run ApiPort on a project.</span></span>
1. <span data-ttu-id="bf2da-149">使用不同的可攜式 API 來解決問題。</span><span class="sxs-lookup"><span data-stu-id="bf2da-149">Address issues by using different APIs that are portable.</span></span>
1. <span data-ttu-id="bf2da-150">記下您無法使用直接替代方法的所有區域。</span><span class="sxs-lookup"><span data-stu-id="bf2da-150">Take note of any areas where you're prevented from using a direct alternative.</span></span>
1. <span data-ttu-id="bf2da-151">為所有要移植的專案重複上述步驟，直到確定每個專案皆已準備好複製到新的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="bf2da-151">Repeat the prior steps for all projects you're porting until you're confident each is ready to be copied over into a new .NET Core project.</span></span>
1. <span data-ttu-id="bf2da-152">將程式碼複製到新的 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="bf2da-152">Copy the code into a new .NET Core project.</span></span>
1. <span data-ttu-id="bf2da-153">解決您先前所記下沒有直接替代方法的問題。</span><span class="sxs-lookup"><span data-stu-id="bf2da-153">Work out any issues where you noted that a direct alternative doesn't exist.</span></span>

<span data-ttu-id="bf2da-154">這個謹慎的方法比處理編譯器錯誤更有條理，但仍相當著重在程式碼，並具備永遠有會執行編譯之程式碼的優點。</span><span class="sxs-lookup"><span data-stu-id="bf2da-154">This careful approach is more structured than simply working out compiler errors, but it's still relatively code-focused and has the benefit of always having code that compiles.</span></span> <span data-ttu-id="bf2da-155">改用其他 API 仍無法解決的問題，其解決方式差異極大。</span><span class="sxs-lookup"><span data-stu-id="bf2da-155">The way you resolve certain issues that couldn't be addressed by just using another API varies greatly.</span></span> <span data-ttu-id="bf2da-156">您可能現某些專案需要開發更完善的方案，下個方法中會加以說明。</span><span class="sxs-lookup"><span data-stu-id="bf2da-156">You may find that you need to develop a more comprehensive plan for certain projects, which is covered as the next approach.</span></span>

### <a name="developing-a-comprehensive-plan-of-attack"></a><span data-ttu-id="bf2da-157">開發全面的攻擊計畫</span><span class="sxs-lookup"><span data-stu-id="bf2da-157">Developing a comprehensive plan of attack</span></span>

<span data-ttu-id="bf2da-158">這個方法可能最適合大型且更複雜的專案，因為可能必須重新建構程式碼或完全重寫特定區域的程式碼才能支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="bf2da-158">This approach might be best for larger and more complex projects, where restructuring code or completely rewriting certain areas of code might be necessary to support .NET Core.</span></span> <span data-ttu-id="bf2da-159">方法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="bf2da-159">The approach is as follows:</span></span>

1. <span data-ttu-id="bf2da-160">對專案執行 ApiPort。</span><span class="sxs-lookup"><span data-stu-id="bf2da-160">Run ApiPort on a project.</span></span>
1. <span data-ttu-id="bf2da-161">了解每個非可攜式類型是用在程式碼的何處，以及對整體可攜性有何影響。</span><span class="sxs-lookup"><span data-stu-id="bf2da-161">Understand where each non-portable type is used and how that affects overall portability.</span></span>
   - <span data-ttu-id="bf2da-162">了解這些類型的性質。</span><span class="sxs-lookup"><span data-stu-id="bf2da-162">Understand the nature of those types.</span></span> <span data-ttu-id="bf2da-163">它們是否數量很少但使用頻繁？</span><span class="sxs-lookup"><span data-stu-id="bf2da-163">Are they small in number but used frequently?</span></span> <span data-ttu-id="bf2da-164">它們是否數量很大但很少使用？</span><span class="sxs-lookup"><span data-stu-id="bf2da-164">Are they large in number but used infrequently?</span></span> <span data-ttu-id="bf2da-165">使用集中還是分散在整個程式碼？</span><span class="sxs-lookup"><span data-stu-id="bf2da-165">Is their use concentrated, or is it spread throughout your code?</span></span>
   - <span data-ttu-id="bf2da-166">是否容易隔離非可攜式的程式碼，以便更輕鬆地處理它？</span><span class="sxs-lookup"><span data-stu-id="bf2da-166">Is it easy to isolate code that isn't portable so that you can deal with it more effectively?</span></span>
   - <span data-ttu-id="bf2da-167">是否需要重構程式碼？</span><span class="sxs-lookup"><span data-stu-id="bf2da-167">Do you need to refactor your code?</span></span>
   - <span data-ttu-id="bf2da-168">對於非可攜式的類型，是否有替代的 API 可以完成相同的工作？</span><span class="sxs-lookup"><span data-stu-id="bf2da-168">For those types which aren't portable, are there alternative APIs that accomplish the same task?</span></span> <span data-ttu-id="bf2da-169">例如，如果您使用的是 <xref:System.Net.WebClient> 類別，或許可以改用 <xref:System.Net.Http.HttpClient> 類別。</span><span class="sxs-lookup"><span data-stu-id="bf2da-169">For example if you're using the <xref:System.Net.WebClient> class, you might be able to use the <xref:System.Net.Http.HttpClient> class instead.</span></span>
   - <span data-ttu-id="bf2da-170">是否有不同的可攜式 API 可用來完成工作，即使它不是直接替換項目？</span><span class="sxs-lookup"><span data-stu-id="bf2da-170">Are there different portable APIs available to accomplish a task, even if it's not a drop-in replacement?</span></span> <span data-ttu-id="bf2da-171">例如，如果您是使用 <xref:System.Xml.Schema.XmlSchema> 來剖析 XML，但不需要 XML 結構描述探索，則可以使用 <xref:System.Xml.Linq> API 並自行實作剖析，而不需依靠 API。</span><span class="sxs-lookup"><span data-stu-id="bf2da-171">For example if you're using <xref:System.Xml.Schema.XmlSchema> to parse XML but don't require XML schema discovery, you could use <xref:System.Xml.Linq> APIs and implement parsing yourself as opposed to relying on an API.</span></span>
1. <span data-ttu-id="bf2da-172">如果有難以移轉的組件，暫時留在 .NET Framework 是否值得？</span><span class="sxs-lookup"><span data-stu-id="bf2da-172">If you have assemblies that are difficult to port, is it worth leaving them on .NET Framework for now?</span></span> <span data-ttu-id="bf2da-173">以下是要考量的事項：</span><span class="sxs-lookup"><span data-stu-id="bf2da-173">Here are some things to consider:</span></span>
   - <span data-ttu-id="bf2da-174">程式庫中可能有一些功能與 .NET Core 不相容，因為它太過依賴 .NET Framework 或 Windows 特定的功能。</span><span class="sxs-lookup"><span data-stu-id="bf2da-174">You may have some functionality in your library that's incompatible with .NET Core because it relies too heavily on .NET Framework or Windows-specific functionality.</span></span> <span data-ttu-id="bf2da-175">是否值得先不考慮該功能，改為暫時推出功能較少的程式庫 .NET Core 版本，直到有資源可供移植該功能？</span><span class="sxs-lookup"><span data-stu-id="bf2da-175">Is it worth leaving that functionality behind for now and releasing a .NET Core version of your library with less features on a temporary basis until resources are available to port the features?</span></span>
   - <span data-ttu-id="bf2da-176">重構是否會有幫助？</span><span class="sxs-lookup"><span data-stu-id="bf2da-176">Would a refactor help?</span></span>
1. <span data-ttu-id="bf2da-177">撰寫無法使用的 .NET Framework API 自有實作是否合理？</span><span class="sxs-lookup"><span data-stu-id="bf2da-177">Is it reasonable to write your own implementation of an unavailable .NET Framework API?</span></span>
   <span data-ttu-id="bf2da-178">可以考慮複製、修改及使用來自 [.NET Framework 參考來源](https://github.com/Microsoft/referencesource) \(英文\) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2da-178">You could consider copying, modifying, and using code from the [.NET Framework Reference Source](https://github.com/Microsoft/referencesource).</span></span> <span data-ttu-id="bf2da-179">參考來源程式碼是依據 [MIT 授權條款](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt) \(英文\) 授權，因此您有充分的權限可以將該來源做為自己程式碼的基礎。</span><span class="sxs-lookup"><span data-stu-id="bf2da-179">The reference source code is licensed under the [MIT License](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), so you have significant freedom to use the source as a basis for your own code.</span></span> <span data-ttu-id="bf2da-180">您只需記得在程式碼中適當地將版權歸於 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="bf2da-180">Just be sure to properly attribute Microsoft in your code.</span></span>
1. <span data-ttu-id="bf2da-181">視需要對不同的專案重複此程序。</span><span class="sxs-lookup"><span data-stu-id="bf2da-181">Repeat this process as needed for different projects.</span></span>
 
<span data-ttu-id="bf2da-182">分析階段可能需要一些時間，視您的程式碼基底大小而定。</span><span class="sxs-lookup"><span data-stu-id="bf2da-182">The analysis phase could take some time depending on the size of your codebase.</span></span> <span data-ttu-id="bf2da-183">在這個階段花時間徹底了解所需的變更範圍並開發計畫，通常能為未來省下許多時間，特別是在您程式碼基底較為複雜的情況下。</span><span class="sxs-lookup"><span data-stu-id="bf2da-183">Spending time in this phase to thoroughly understand the scope of changes needed and to develop a plan usually saves you time in the long run, particularly if you have a complex codebase.</span></span>

<span data-ttu-id="bf2da-184">您的計劃可能涉及在對程式碼基底進行重大變更時仍要以 .NET Framework 4.7.2 為目標，讓它成為前一種方法更有條理的版本。</span><span class="sxs-lookup"><span data-stu-id="bf2da-184">Your plan could involve making significant changes to your codebase while still targeting .NET Framework 4.7.2, making this a more structured version of the previous approach.</span></span> <span data-ttu-id="bf2da-185">執行計畫的方式須視程式碼基底而定。</span><span class="sxs-lookup"><span data-stu-id="bf2da-185">How you go about executing your plan is dependent on your codebase.</span></span>

### <a name="mixing-approaches"></a><span data-ttu-id="bf2da-186">混合方法</span><span class="sxs-lookup"><span data-stu-id="bf2da-186">Mixing approaches</span></span>

<span data-ttu-id="bf2da-187">您可能會根據每個專案混用上述各種方法。</span><span class="sxs-lookup"><span data-stu-id="bf2da-187">It's likely that you'll mix the above approaches on a per-project basis.</span></span> <span data-ttu-id="bf2da-188">您應該做對您和程式碼基底而言最有意義的事。</span><span class="sxs-lookup"><span data-stu-id="bf2da-188">You should do what makes the most sense to you and for your codebase.</span></span>

## <a name="porting-your-tests"></a><span data-ttu-id="bf2da-189">移植測試</span><span class="sxs-lookup"><span data-stu-id="bf2da-189">Porting your tests</span></span>

<span data-ttu-id="bf2da-190">移轉程式碼後，確定一切正常運作的最佳方式，是在將程式碼移轉到 .NET Core 時測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2da-190">The best way to make sure everything works when you've ported your code is to test your code as you port it to .NET Core.</span></span> <span data-ttu-id="bf2da-191">若要這樣做，您必須使用能針對 .NET Core 建置並執行測試的測試架構。</span><span class="sxs-lookup"><span data-stu-id="bf2da-191">To do this, you'll need to use a testing framework that builds and runs tests for .NET Core.</span></span> <span data-ttu-id="bf2da-192">目前有三個選項︰</span><span class="sxs-lookup"><span data-stu-id="bf2da-192">Currently, you have three options:</span></span>

- [<span data-ttu-id="bf2da-193">xUnit</span><span class="sxs-lookup"><span data-stu-id="bf2da-193">xUnit</span></span>](https://xunit.github.io/)
  * [<span data-ttu-id="bf2da-194">快速入門</span><span class="sxs-lookup"><span data-stu-id="bf2da-194">Getting Started</span></span>](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [<span data-ttu-id="bf2da-195">將 MSTest 專案轉換成 xUnit 的工具</span><span class="sxs-lookup"><span data-stu-id="bf2da-195">Tool to convert an MSTest project to xUnit</span></span>](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [<span data-ttu-id="bf2da-196">NUnit</span><span class="sxs-lookup"><span data-stu-id="bf2da-196">NUnit</span></span>](https://nunit.org/)
  * [<span data-ttu-id="bf2da-197">快速入門</span><span class="sxs-lookup"><span data-stu-id="bf2da-197">Getting Started</span></span>](https://github.com/nunit/docs/wiki/Installation)
  * [<span data-ttu-id="bf2da-198">關於從 MSTest 移轉至 NUnit 的部落格文章</span><span class="sxs-lookup"><span data-stu-id="bf2da-198">Blog post about migrating from MSTest to NUnit</span></span>](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [<span data-ttu-id="bf2da-199">MSTest</span><span class="sxs-lookup"><span data-stu-id="bf2da-199">MSTest</span></span>](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a><span data-ttu-id="bf2da-200">建議的移植方法</span><span class="sxs-lookup"><span data-stu-id="bf2da-200">Recommended approach to porting</span></span>

<span data-ttu-id="bf2da-201">不管如何，移植工作都會大幅取決於 .NET Framework 程式碼的架構方式。</span><span class="sxs-lookup"><span data-stu-id="bf2da-201">Ultimately, the porting effort depends heavily on how your .NET Framework code is structured.</span></span> <span data-ttu-id="bf2da-202">移植程式碼的良好方式，是從程式庫的「基底」  開始，也就是程式碼的基本元件。</span><span class="sxs-lookup"><span data-stu-id="bf2da-202">A good way to port your code is to begin with the *base* of your library, which are the foundational components of your code.</span></span> <span data-ttu-id="bf2da-203">它可能是資料模型，也可能是所有其他項目會直接或間接使用的基礎類別和方法。</span><span class="sxs-lookup"><span data-stu-id="bf2da-203">This might be data models or some other foundational classes and methods that everything else uses directly or indirectly.</span></span>

1. <span data-ttu-id="bf2da-204">針對測試目前正在移植之程式庫層的測試專案進行移植。</span><span class="sxs-lookup"><span data-stu-id="bf2da-204">Port the test project that tests the layer of your library that you're currently porting.</span></span>
1. <span data-ttu-id="bf2da-205">將程式庫的基底複製到新的 .NET Core 專案，然後選取您想要支援的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="bf2da-205">Copy over the base of your library into a new .NET Core project and select the version of the .NET Standard you wish to support.</span></span>
1. <span data-ttu-id="bf2da-206">進行任何必要的變更，令程式碼執行編譯。</span><span class="sxs-lookup"><span data-stu-id="bf2da-206">Make any changes needed to get the code to compile.</span></span> <span data-ttu-id="bf2da-207">此工作有很大一部分可能會需要將 NuGet 套件相依性新增到 *csproj* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="bf2da-207">Much of this may require adding NuGet package dependencies to your *csproj* file.</span></span>
1. <span data-ttu-id="bf2da-208">執行測試並進行任何必要的調整。</span><span class="sxs-lookup"><span data-stu-id="bf2da-208">Run the tests and make any needed adjustments.</span></span>
1. <span data-ttu-id="bf2da-209">挑選要移植的下一層程式碼，並重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="bf2da-209">Pick the next layer of code to port over and repeat the prior steps.</span></span>

<span data-ttu-id="bf2da-210">如果您是從程式庫基底向外進行移植，並視需要測試每一層，移植將會是個系統化的程序，並將所有問題都隔離在單層的程式碼內。</span><span class="sxs-lookup"><span data-stu-id="bf2da-210">If you start with the base of your library and move outward from the base and test each layer as needed, porting is a systematic process where problems are isolated to one layer of code at a time.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="bf2da-211">下一步</span><span class="sxs-lookup"><span data-stu-id="bf2da-211">Next</span></span>](project-structure.md)
