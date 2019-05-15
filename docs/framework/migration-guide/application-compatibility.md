---
title: .NET Framework 中的應用程式相容性
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 154640499e99767f73a148c6980e6a2a4cfbce2f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623781"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="888ba-102">.NET Framework 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="888ba-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="888ba-103">簡介</span><span class="sxs-lookup"><span data-stu-id="888ba-103">Introduction</span></span>
<span data-ttu-id="888ba-104">相容性是每個 .NET 版本都極為重視的目標。</span><span class="sxs-lookup"><span data-stu-id="888ba-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="888ba-105">相容性可確保每個版本都能累加，讓舊版仍能運作。</span><span class="sxs-lookup"><span data-stu-id="888ba-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="888ba-106">另一方面，舊版功能的變更 (為改善效能、處理安全性問題，或修正 Bug) 會造成現有程式碼或現有應用程式中在更新版本下執行的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="888ba-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="888ba-107">.NET Framework 可辨識重定目標變更及執行階段變更。</span><span class="sxs-lookup"><span data-stu-id="888ba-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="888ba-108">重定目標變更會影響以 .NET Framework 特定版本為目標，但在更新版本上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="888ba-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="888ba-109">執行階段變更會影響在特定版本上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="888ba-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="888ba-110">每個應用程式都有特定版本的 .NET Framework 目標，可以下列方式指定：</span><span class="sxs-lookup"><span data-stu-id="888ba-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="888ba-111">在 Visual Studio 中定義目標架構。</span><span class="sxs-lookup"><span data-stu-id="888ba-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="888ba-112">在專案檔中指定目標架構。</span><span class="sxs-lookup"><span data-stu-id="888ba-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="888ba-113">將 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 套用至原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="888ba-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="888ba-114">在比目標版本更新的版本上執行時，.NET Framework 會使用古怪的行為，模擬較舊的目標版本。</span><span class="sxs-lookup"><span data-stu-id="888ba-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="888ba-115">換句話說，應用程式會在較新的 Framework 版本上執行，但表現出的行為如同在較舊的版本上執行。</span><span class="sxs-lookup"><span data-stu-id="888ba-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="888ba-116">.NET Framework 版本間的許多相容性問題是透過這種古怪的模型而降低。</span><span class="sxs-lookup"><span data-stu-id="888ba-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="888ba-117">應用程式的目標 .NET Framework 版本取決於執行程式碼所在之應用程式定義域的項目組件目標版本。</span><span class="sxs-lookup"><span data-stu-id="888ba-117">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code is running in.</span></span> <span data-ttu-id="888ba-118">該應用程式定義域載入的所有其他組件則以該 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="888ba-118">All additional assemblies loaded in that application domain target that .NET Framework version.</span></span> <span data-ttu-id="888ba-119">例如，在可執行檔的情況下，可執行檔的目標架構是該 AppDomain 中的所有組件將在其下運行的相容性模式。</span><span class="sxs-lookup"><span data-stu-id="888ba-119">For example, in the case of an executable, the framework the executable targets is the compatibility mode all assemblies in that AppDomain will run under.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="888ba-120">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="888ba-120">Runtime changes</span></span>

<span data-ttu-id="888ba-121">執行階段問題是在電腦上進行新的執行階段，而相同的二進位檔案也在執行時，會看到不同的行為。</span><span class="sxs-lookup"><span data-stu-id="888ba-121">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="888ba-122">如果二進位檔已針對 .NET Framework 4.0 編譯，它就可以在 4.5 或更新版本中以 .NET Framework 4.0 相容性模式執行。</span><span class="sxs-lookup"><span data-stu-id="888ba-122">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="888ba-123">許多影響 4.5 的變更不會影響針對 4.0 所編譯的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="888ba-123">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="888ba-124">這是 AppDomain 特有的功能，視項目組件的設定而定。</span><span class="sxs-lookup"><span data-stu-id="888ba-124">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="888ba-125">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="888ba-125">Retargeting changes</span></span>

<span data-ttu-id="888ba-126">重定目標問題，是當以 4.0 為目標的組件現在設定為以 4.5 為目標時發生的問題。</span><span class="sxs-lookup"><span data-stu-id="888ba-126">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="888ba-127">現在，組件選擇加入新功能並成為可能的舊功能相容性問題。</span><span class="sxs-lookup"><span data-stu-id="888ba-127">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="888ba-128">這同樣受項目組件支配，所以主控台應用程式會使用組件，或網站會參考組件。</span><span class="sxs-lookup"><span data-stu-id="888ba-128">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="888ba-129">.NET 相容性診斷</span><span class="sxs-lookup"><span data-stu-id="888ba-129">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="888ba-130">.NET 相容性診斷是由 Roslyn 提供的分析器，可協助您識別各版 .NET Framework 之間的應用程式相容性問題。</span><span class="sxs-lookup"><span data-stu-id="888ba-130">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="888ba-131">此清單包含所有可用的分析器，但只有一部分會套用至任何特定的移轉。</span><span class="sxs-lookup"><span data-stu-id="888ba-131">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="888ba-132">分析器會判斷適用於規劃之移轉的問題，並且只會呈現這些問題。</span><span class="sxs-lookup"><span data-stu-id="888ba-132">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="888ba-133">每個問題包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="888ba-133">Each issue includes the following information:</span></span>

- <span data-ttu-id="888ba-134">舊版中已變更的內容描述。</span><span class="sxs-lookup"><span data-stu-id="888ba-134">The description of what has changed from a previous version.</span></span>

- <span data-ttu-id="888ba-135">變更如何影響客戶，以及是否有任何因應措施可保留版本間的相容性。</span><span class="sxs-lookup"><span data-stu-id="888ba-135">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

- <span data-ttu-id="888ba-136">變更的重要性評估。</span><span class="sxs-lookup"><span data-stu-id="888ba-136">An assessment of how important the change is.</span></span> <span data-ttu-id="888ba-137">應用程式相容性問題可分類如下：</span><span class="sxs-lookup"><span data-stu-id="888ba-137">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="888ba-138">主要</span><span class="sxs-lookup"><span data-stu-id="888ba-138">Major</span></span>|<span data-ttu-id="888ba-139">影響大量應用程式或需要大幅修改程式碼的重大變更。</span><span class="sxs-lookup"><span data-stu-id="888ba-139">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="888ba-140">次要</span><span class="sxs-lookup"><span data-stu-id="888ba-140">Minor</span></span>|<span data-ttu-id="888ba-141">影響少量應用程式或需要稍微修改程式碼的變更。</span><span class="sxs-lookup"><span data-stu-id="888ba-141">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="888ba-142">邊緣案例</span><span class="sxs-lookup"><span data-stu-id="888ba-142">Edge case</span></span>|<span data-ttu-id="888ba-143">在非常特定 (罕見) 的情況下影響應用程式的變更。</span><span class="sxs-lookup"><span data-stu-id="888ba-143">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="888ba-144">透明</span><span class="sxs-lookup"><span data-stu-id="888ba-144">Transparent</span></span>|<span data-ttu-id="888ba-145">對應用程式的開發人員或使用者影響的不明顯變更。</span><span class="sxs-lookup"><span data-stu-id="888ba-145">A change with no noticeable effect on the application's developer or user.</span></span>|

- <span data-ttu-id="888ba-146">第一次出現此變更的 Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="888ba-146">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="888ba-147">也指出某些變更會引入到特定版本，然後在更新版本中還原。</span><span class="sxs-lookup"><span data-stu-id="888ba-147">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

- <span data-ttu-id="888ba-148">變更類型：</span><span class="sxs-lookup"><span data-stu-id="888ba-148">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="888ba-149">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="888ba-149">Retargeting</span></span>|<span data-ttu-id="888ba-150">此變更會影響為了以新版 .NET Framework 為目標而重新編譯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="888ba-150">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="888ba-151">執行階段</span><span class="sxs-lookup"><span data-stu-id="888ba-151">Runtime</span></span>|<span data-ttu-id="888ba-152">此變更會影響以舊版 .NET Framework 為目標但在新版上執行的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="888ba-152">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

- <span data-ttu-id="888ba-153">受影響的 API (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="888ba-153">The affected APIS, if any.</span></span>

- <span data-ttu-id="888ba-154">可用診斷的識別碼</span><span class="sxs-lookup"><span data-stu-id="888ba-154">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="888ba-155">使用量</span><span class="sxs-lookup"><span data-stu-id="888ba-155">Usage</span></span>
<span data-ttu-id="888ba-156">若要開始，請選取以下的相容性變更類型：</span><span class="sxs-lookup"><span data-stu-id="888ba-156">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="888ba-157">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="888ba-157">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="888ba-158">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="888ba-158">Runtime Changes</span></span>](./runtime/index.md)

## <a name="see-also"></a><span data-ttu-id="888ba-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="888ba-159">See also</span></span>

- [<span data-ttu-id="888ba-160">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="888ba-160">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
- [<span data-ttu-id="888ba-161">新功能</span><span class="sxs-lookup"><span data-stu-id="888ba-161">What's New</span></span>](../../../docs/framework/whats-new/index.md)
- [<span data-ttu-id="888ba-162">類別庫中已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="888ba-162">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
