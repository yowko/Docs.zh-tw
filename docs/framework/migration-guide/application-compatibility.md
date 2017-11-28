---
title: ".NET Framework 中的應用程式相容性"
ms.custom: 
ms.date: 05/19/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
- app-compat
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
caps.latest.revision: "19"
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e67fff19c4b187010b35519081f46e11effbad6c
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2017
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="a05db-102">.NET Framework 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="a05db-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="a05db-103">簡介</span><span class="sxs-lookup"><span data-stu-id="a05db-103">Introduction</span></span>
<span data-ttu-id="a05db-104">相容性是每個 .NET 版本都極為重視的目標。</span><span class="sxs-lookup"><span data-stu-id="a05db-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="a05db-105">相容性可確保每個版本都能累加，讓舊版仍能運作。</span><span class="sxs-lookup"><span data-stu-id="a05db-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="a05db-106">另一方面，舊版功能的變更 (為改善效能、處理安全性問題，或修正 Bug) 會造成現有程式碼或現有應用程式中在更新版本下執行的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="a05db-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="a05db-107">.NET Framework 可辨識重定目標變更及執行階段變更。</span><span class="sxs-lookup"><span data-stu-id="a05db-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="a05db-108">重定目標變更會影響以 .NET Framework 特定版本為目標，但在更新版本上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a05db-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="a05db-109">執行階段變更會影響在特定版本上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a05db-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="a05db-110">每個應用程式都有特定版本的 .NET Framework 目標，可以下列方式指定：</span><span class="sxs-lookup"><span data-stu-id="a05db-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="a05db-111">在 Visual Studio 中定義目標架構。</span><span class="sxs-lookup"><span data-stu-id="a05db-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="a05db-112">在專案檔中指定目標架構。</span><span class="sxs-lookup"><span data-stu-id="a05db-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="a05db-113">將 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 套用至原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="a05db-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="a05db-114">在比目標版本更新的版本上執行時，.NET Framework 會使用古怪的行為，模擬較舊的目標版本。</span><span class="sxs-lookup"><span data-stu-id="a05db-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="a05db-115">換句話說，應用程式會在較新的 Framework 版本上執行，但表現出的行為如同在較舊的版本上執行。</span><span class="sxs-lookup"><span data-stu-id="a05db-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="a05db-116">.NET Framework 版本間的許多相容性問題是透過這種古怪的模型而降低。</span><span class="sxs-lookup"><span data-stu-id="a05db-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="a05db-117">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="a05db-117">Runtime changes</span></span>

<span data-ttu-id="a05db-118">執行階段問題是在電腦上進行新的執行階段，而相同的二進位檔案也在執行時，會看到不同的行為。</span><span class="sxs-lookup"><span data-stu-id="a05db-118">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="a05db-119">如果二進位檔已針對 .NET Framework 4.0 編譯，它就可以在 4.5 或更新版本中以 .NET Framework 4.0 相容性模式執行。</span><span class="sxs-lookup"><span data-stu-id="a05db-119">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="a05db-120">許多影響 4.5 的變更不會影響針對 4.0 所編譯的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="a05db-120">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="a05db-121">這是 AppDomain 特有的功能，視項目組件的設定而定。</span><span class="sxs-lookup"><span data-stu-id="a05db-121">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="a05db-122">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="a05db-122">Retargeting changes</span></span>

<span data-ttu-id="a05db-123">重定目標問題，是當以 4.0 為目標的組件現在設定為以 4.5 為目標時發生的問題。</span><span class="sxs-lookup"><span data-stu-id="a05db-123">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="a05db-124">現在，組件選擇加入新功能並成為可能的舊功能相容性問題。</span><span class="sxs-lookup"><span data-stu-id="a05db-124">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="a05db-125">這同樣受項目組件支配，所以主控台應用程式會使用組件，或網站會參考組件。</span><span class="sxs-lookup"><span data-stu-id="a05db-125">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="a05db-126">.NET 相容性診斷</span><span class="sxs-lookup"><span data-stu-id="a05db-126">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="a05db-127">.NET 相容性診斷是由 Roslyn 提供的分析器，可協助您識別各版 .NET Framework 之間的應用程式相容性問題。</span><span class="sxs-lookup"><span data-stu-id="a05db-127">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="a05db-128">此清單包含所有可用的分析器，但只有一部分會套用至任何特定的移轉。</span><span class="sxs-lookup"><span data-stu-id="a05db-128">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="a05db-129">分析器會判斷適用於規劃之移轉的問題，並且只會呈現這些問題。</span><span class="sxs-lookup"><span data-stu-id="a05db-129">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="a05db-130">每個問題包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="a05db-130">Each issue includes the following information:</span></span>

-   <span data-ttu-id="a05db-131">舊版中已變更的內容描述。</span><span class="sxs-lookup"><span data-stu-id="a05db-131">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="a05db-132">變更如何影響客戶，以及是否有任何因應措施可保留版本間的相容性。</span><span class="sxs-lookup"><span data-stu-id="a05db-132">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="a05db-133">變更的重要性評估。</span><span class="sxs-lookup"><span data-stu-id="a05db-133">An assessment of how important the change is.</span></span> <span data-ttu-id="a05db-134">應用程式相容性問題可分類如下：</span><span class="sxs-lookup"><span data-stu-id="a05db-134">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="a05db-135">主要</span><span class="sxs-lookup"><span data-stu-id="a05db-135">Major</span></span>|<span data-ttu-id="a05db-136">影響大量應用程式或需要大幅修改程式碼的重大變更。</span><span class="sxs-lookup"><span data-stu-id="a05db-136">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="a05db-137">次要</span><span class="sxs-lookup"><span data-stu-id="a05db-137">Minor</span></span>|<span data-ttu-id="a05db-138">影響少量應用程式或需要稍微修改程式碼的變更。</span><span class="sxs-lookup"><span data-stu-id="a05db-138">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="a05db-139">邊緣案例</span><span class="sxs-lookup"><span data-stu-id="a05db-139">Edge case</span></span>|<span data-ttu-id="a05db-140">在非常特定 (罕見) 的情況下影響應用程式的變更。</span><span class="sxs-lookup"><span data-stu-id="a05db-140">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="a05db-141">透明</span><span class="sxs-lookup"><span data-stu-id="a05db-141">Transparent</span></span>|<span data-ttu-id="a05db-142">對應用程式的開發人員或使用者影響的不明顯變更。</span><span class="sxs-lookup"><span data-stu-id="a05db-142">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="a05db-143">第一次出現此變更的 Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a05db-143">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="a05db-144">也指出某些變更會引入到特定版本，然後在更新版本中還原。</span><span class="sxs-lookup"><span data-stu-id="a05db-144">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="a05db-145">變更類型：</span><span class="sxs-lookup"><span data-stu-id="a05db-145">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="a05db-146">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="a05db-146">Retargeting</span></span>|<span data-ttu-id="a05db-147">此變更會影響為了以新版 .NET Framework 為目標而重新編譯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a05db-147">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="a05db-148">執行階段</span><span class="sxs-lookup"><span data-stu-id="a05db-148">Runtime</span></span>|<span data-ttu-id="a05db-149">此變更會影響以舊版 .NET Framework 為目標但在新版上執行的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a05db-149">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="a05db-150">受影響的 API (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="a05db-150">The affected APIS, if any.</span></span>

-   <span data-ttu-id="a05db-151">可用診斷的識別碼</span><span class="sxs-lookup"><span data-stu-id="a05db-151">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="a05db-152">使用方式</span><span class="sxs-lookup"><span data-stu-id="a05db-152">Usage</span></span>
<span data-ttu-id="a05db-153">若要開始，請選取以下的相容性變更類型：</span><span class="sxs-lookup"><span data-stu-id="a05db-153">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="a05db-154">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="a05db-154">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="a05db-155">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="a05db-155">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="a05db-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a05db-156">See Also</span></span>

* [<span data-ttu-id="a05db-157">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="a05db-157">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [<span data-ttu-id="a05db-158">新功能</span><span class="sxs-lookup"><span data-stu-id="a05db-158">What's New</span></span>](../../../docs/framework/whats-new/index.md)
* [<span data-ttu-id="a05db-159">類別庫中已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="a05db-159">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
