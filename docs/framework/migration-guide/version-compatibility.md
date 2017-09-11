---
title: ".NET Framework 的版本相容性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 741c2d1c49f44a6a7b299845cdc37cc8425c326b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="version-compatibility-in-the-net-framework"></a><span data-ttu-id="e9f20-102">.NET Framework 的版本相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-102">Version Compatibility in the .NET Framework</span></span>
<span data-ttu-id="e9f20-103">回溯相容性表示針對特定平台版本開發的應用程式將會在該平台的較新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="e9f20-103">Backward compatibility means that an app that was developed for a particular version of a platform will run on later versions of that platform.</span></span> <span data-ttu-id="e9f20-104">.NET Framework 嘗試最大化回溯相容性：針對某一個 .NET Framework 版本撰寫的原始程式碼應該在較新版本的 .NET Framework 上編譯，而且在某一個 .NET Framework 版本上執行之二進位檔的行為應該與較新版本的 .NET Framework 相同。</span><span class="sxs-lookup"><span data-stu-id="e9f20-104">The .NET Framework tries to maximize backward compatibility: Source code written for one version of the .NET Framework should compile on later versions of the .NET Framework, and binaries that run on one version of the .NET Framework should behave identically on later versions of the .NET Framework.</span></span>  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a><span data-ttu-id="e9f20-105">應用程式的版本相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-105">Version compatibility for apps</span></span>  
 <span data-ttu-id="e9f20-106">根據預設，應用程式會在其建置所針對的 .NET Framework 版本上執行。</span><span class="sxs-lookup"><span data-stu-id="e9f20-106">By default, an app runs on the version of the .NET Framework that it was built for.</span></span> <span data-ttu-id="e9f20-107">如果該版本不存在，而且應用程式組態檔並未定義支援的版本，則可能會發生 .NET Framework 初始化錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9f20-107">If that version is not present and the app configuration file does not define supported versions, a .NET Framework initialization error may occur.</span></span> <span data-ttu-id="e9f20-108">在此例中，嘗試執行應用程式的作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="e9f20-108">In this case, the attempt to run the app will fail.</span></span>  
  
 <span data-ttu-id="e9f20-109">若要定義應用程式執行所在的特定版本，請將一個或多個 [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) 項目新增至應用程式的組態檔。</span><span class="sxs-lookup"><span data-stu-id="e9f20-109">To define the specific versions on which your app runs, add one or more [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elements to your app's configuration file.</span></span> <span data-ttu-id="e9f20-110">每一個 `<supportedRuntime>` 項目都會列出支援的執行階段版本，最先指定的是最優先的版本，而最後指定的則是優先順序最低的版本。</span><span class="sxs-lookup"><span data-stu-id="e9f20-110">Each `<supportedRuntime>` element lists a supported version of the runtime, with the first specifying the most preferred version and the last specifying the least preferred version.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 <span data-ttu-id="e9f20-111">如需詳細資訊，請參閱[如何：設定應用程式以支援 .NET Framework 4 或 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f20-111">For more information, see [How to: Configure an App to Support .NET Framework 4 or 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).</span></span>  
  
## <a name="version-compatibility-for-components"></a><span data-ttu-id="e9f20-112">元件的版本相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-112">Version compatibility for components</span></span>  
 <span data-ttu-id="e9f20-113">應用程式可以控制其執行所在的 .NET Framework 版本，但是元件則無法控制。</span><span class="sxs-lookup"><span data-stu-id="e9f20-113">An app can control the version of the .NET Framework on which it runs, but a component cannot.</span></span> <span data-ttu-id="e9f20-114">元件和類別庫會在特定應用程式的內容中載入，因此會自動在應用程式執行所在的 .NET Framework 版本上執行。</span><span class="sxs-lookup"><span data-stu-id="e9f20-114">Components and class libraries are loaded in the context of a particular app, and therefore automatically run on the version of the .NET Framework that the app runs on.</span></span>  
  
 <span data-ttu-id="e9f20-115">由於這項限制，所以相容性保證對於元件特別重要。</span><span class="sxs-lookup"><span data-stu-id="e9f20-115">Because of this restriction, compatibility guarantees are especially important for components.</span></span> <span data-ttu-id="e9f20-116">從 .NET Framework 4 開始，您可以指定元件在多個版本中維持相容所需的程度，方法是將 <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=fullName> 屬性套用至該元件。</span><span class="sxs-lookup"><span data-stu-id="e9f20-116">Starting with the .NET Framework 4, you can specify the degree to which a component is expected to remain compatible across multiple versions by applying the <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=fullName> attribute to that component.</span></span> <span data-ttu-id="e9f20-117">工具可以使用這個屬性來偵測將來的元件版本中，是否有可能違反相容性保證的狀況。</span><span class="sxs-lookup"><span data-stu-id="e9f20-117">Tools can use this attribute to detect potential violations of the compatibility guarantee in future versions of a component.</span></span>  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a><span data-ttu-id="e9f20-118">回溯相容性和 .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="e9f20-118">Backward compatibility and the .NET Framework 4.5</span></span>  
 <span data-ttu-id="e9f20-119">.NET Framework 4.5 及其點版本 (4.5.1、4.5.2、4.6、4.6.1、4.6.2 和 4.7) 可與使用舊版 .NET Framework 建置的應用程式回溯相容。</span><span class="sxs-lookup"><span data-stu-id="e9f20-119">The .NET Framework 4.5 and its point releases (4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, and 4.7) are backward-compatible with apps that were built with earlier versions of the .NET Framework.</span></span> <span data-ttu-id="e9f20-120">換句話說，使用舊版建置的應用程式和元件不需經過修改，就可在 .NET Framework 4.5 上運作。</span><span class="sxs-lookup"><span data-stu-id="e9f20-120">In other words, apps and components built with previous versions will work without modification on the .NET Framework 4.5.</span></span> <span data-ttu-id="e9f20-121">不過，應用程式預設會在做為其開發目標的 Common Language Runtime 版本上執行，因此您可能需要提供組態檔，才能讓您的應用程式在 .NET Framework 4.5 上執行。</span><span class="sxs-lookup"><span data-stu-id="e9f20-121">However, by default, apps run on the version of the common language runtime for which they were developed, so you may have to provide a configuration file to enable your app to run on the .NET Framework 4.5.</span></span> <span data-ttu-id="e9f20-122">如需詳細資訊，請參閱本文前面的[應用程式的版本相容性](#Apps)一節。</span><span class="sxs-lookup"><span data-stu-id="e9f20-122">For more information, see the [Version compatibility for apps](#Apps) section earlier in this article.</span></span>  
  
 <span data-ttu-id="e9f20-123">在實際操作中，.NET Framework 中似乎前後不一致的變更以及程式設計技術的變更可能會破壞此相容性。</span><span class="sxs-lookup"><span data-stu-id="e9f20-123">In practice, this compatibility can be broken by seemingly inconsequential changes in the .NET Framework and changes in programming techniques.</span></span> <span data-ttu-id="e9f20-124">例如，.NET Framework 4.5 中的效能改良可能會暴露在舊版不會發生的競爭情況。</span><span class="sxs-lookup"><span data-stu-id="e9f20-124">For example, performance improvements in the .NET Framework 4.5 can expose a race condition that did not occur on earlier versions.</span></span> <span data-ttu-id="e9f20-125">同樣地，使用 .NET Framework 組件的硬式編碼路徑、搭配特定版本的 .NET Framework 執行相等比較以及使用反映來取得私用欄位的值，都不是具有回溯相容性的作法。</span><span class="sxs-lookup"><span data-stu-id="e9f20-125">Similarly, using a hard-coded path to .NET Framework assemblies, performing an equality comparison with a particular version of the .NET Framework, and getting the value of a private field by using reflection are not backward-compatible practices.</span></span> <span data-ttu-id="e9f20-126">此外，每一個 .NET Framework 版本都包含可能會影響某些應用程式與元件之相容性的 Bug 修正和安全性相關的變更。</span><span class="sxs-lookup"><span data-stu-id="e9f20-126">In addition, each version of the .NET Framework includes bug fixes and security-related changes that can affect the compatibility of some apps and components.</span></span>  
  
 <span data-ttu-id="e9f20-127">如果您的應用程式或元件無法依預期的方式在 .NET Framework 4.5 (包括其點版本 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]和 4.5.2)、4.6、4.6.1、4.6.2 或 4.7 上運作，請使用下列檢查清單：</span><span class="sxs-lookup"><span data-stu-id="e9f20-127">If your app or component does not work as expected on the .NET Framework 4.5 (including its point releases, the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, or 4.7, use the following checklists:</span></span>  
  
-   <span data-ttu-id="e9f20-128">檢查下列主題，找出任何可能會影響應用程式的變更，並套用所述的替代解決辦法：</span><span class="sxs-lookup"><span data-stu-id="e9f20-128">Check these topics  for any changes that might affect your app and apply the workaround described:</span></span>  
  
    -   [<span data-ttu-id="e9f20-129">.NET Framework 4 移轉問題</span><span class="sxs-lookup"><span data-stu-id="e9f20-129">.NET Framework 4 Migration Issues</span></span>](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)  
  
    -   [<span data-ttu-id="e9f20-130">4.5 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-130">Application Compatibility in 4.5</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)  
  
    -   [<span data-ttu-id="e9f20-131">4.5.1 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-131">Application Compatibility in 4.5.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)  
  
    -   [<span data-ttu-id="e9f20-132">4.5.2 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-132">Application Compatibility in 4.5.2</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)  
  
    -   [<span data-ttu-id="e9f20-133">4.6 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-133">Application Compatibility in 4.6</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6.md)  
  
    -   [<span data-ttu-id="e9f20-134">4.6.1 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-134">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
    -   [<span data-ttu-id="e9f20-135">4.6.2 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-135">Application Compatibility in 4.6.2</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)  

    - [<span data-ttu-id="e9f20-136">4.7 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="e9f20-136">Application Compatibility in 4.7</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
       
-   <span data-ttu-id="e9f20-137">如果您有 .NET Framework 1.1 應用程式，請同時檢閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="e9f20-137">If you have a .NET Framework 1.1 app, also review these topics:</span></span>  
  
    -   [<span data-ttu-id="e9f20-138">.NET Framework 2.0 的變更</span><span class="sxs-lookup"><span data-stu-id="e9f20-138">Changes in .NET Framework 2.0</span></span>](http://go.microsoft.com/fwlink/?LinkID=125263)  
  
    -   [<span data-ttu-id="e9f20-139">.NET Framework 3.5 SP1 的變更</span><span class="sxs-lookup"><span data-stu-id="e9f20-139">Changes in .NET Framework 3.5 SP1</span></span>](http://go.microsoft.com/fwlink/?LinkId=186989)  
  
-   <span data-ttu-id="e9f20-140">如果您正在重新編譯現有的原始程式碼以便在 .NET Framework 4.5 或其點版本上執行，或者您正從現有的原始程式碼基底開發以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為目標的新版應用程式或元件，請查看[類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)中的過時類型和成員，並套用所述的因應措施</span><span class="sxs-lookup"><span data-stu-id="e9f20-140">If you are recompiling existing source code to run on the .NET Framework 4.5 or its point releases, or if you are developing a new version of an app or component that targets the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] from an existing source code base, check [What's Obsolete in the Class Library](../../../docs/framework/whats-new/whats-obsolete.md) for obsolete types and members, and apply the workaround described.</span></span> <span data-ttu-id="e9f20-141">(之前編譯的程式碼將會針對已標示為過時的型別和成員繼續執行)。</span><span class="sxs-lookup"><span data-stu-id="e9f20-141">(Previously compiled code will continue to run against types and members that have been marked as obsolete.)</span></span>  
  
-   <span data-ttu-id="e9f20-142">如果您判斷 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中的某項變更已經破壞您的應用程式，請查看[執行階段設定結構描述](../../../docs/framework/configure-apps/file-schema/runtime/index.md)來判斷您是否可以在應用程式組態檔中使用執行階段設定，以還原舊版行為。</span><span class="sxs-lookup"><span data-stu-id="e9f20-142">If you determine that a change in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has broken your app, check the [Runtime Settings Schema](../../../docs/framework/configure-apps/file-schema/runtime/index.md) to determine whether you can use a runtime setting in your app's configuration file to restore the previous behavior.</span></span>  
  
-   <span data-ttu-id="e9f20-143">如果您遇到未記載的問題，請記錄 [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) 錯誤 (bug)，然後連絡 [netfxcf@microsoft.com](mailto:netfxcf@microsoft.com) 並提供錯誤 (bug) 編號。</span><span class="sxs-lookup"><span data-stu-id="e9f20-143">If you encounter an issue that is not documented, file a [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) bug and contact [netfxcf@microsoft.com](mailto:netfxcf@microsoft.com) with the bug number.</span></span>  
  
## <a name="compatibility-and-side-by-side-execution"></a><span data-ttu-id="e9f20-144">相容性和並存執行</span><span class="sxs-lookup"><span data-stu-id="e9f20-144">Compatibility and side-by-side execution</span></span>  
 <span data-ttu-id="e9f20-145">如果您找不到問題的適當因應措施，請記得 .NET Framework 4.5 (或其中一個點版本) 會與版本 1.1、2.0 和 3.5 並存執行，而且是取代第 4 版的就地更新。</span><span class="sxs-lookup"><span data-stu-id="e9f20-145">If you cannot find a suitable workaround for your issue, remember that the .NET Framework 4.5 (or one of its point releases) runs side by side with versions 1.1, 2.0, and 3.5, and is an in-place update that replaces version 4.</span></span> <span data-ttu-id="e9f20-146">若是以 1.1、2.0 和 3.5 版為目標的應用程式，您可以在目標電腦上安裝適當的 .NET Framework 版本，以便在最佳環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9f20-146">For apps that target versions 1.1, 2.0, and 3.5, you can install the appropriate version of the .NET Framework on the target machine to run the app in its best environment.</span></span> <span data-ttu-id="e9f20-147">如需並存執行的詳細資訊，請參閱[並存執行](../../../docs/framework/deployment/side-by-side-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f20-147">For more information about side-by-side execution, see [Side-by-Side Execution](../../../docs/framework/deployment/side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f20-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9f20-148">See Also</span></span>  
 <span data-ttu-id="e9f20-149">[新功能](../../../docs/framework/whats-new/index.md) </span><span class="sxs-lookup"><span data-stu-id="e9f20-149">[What's New](../../../docs/framework/whats-new/index.md) </span></span>  
 <span data-ttu-id="e9f20-150">[類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md) </span><span class="sxs-lookup"><span data-stu-id="e9f20-150">[What's Obsolete in the Class Library](../../../docs/framework/whats-new/whats-obsolete.md) </span></span>  
 <span data-ttu-id="e9f20-151">[應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="e9f20-151">[Application Compatibility](../../../docs/framework/migration-guide/application-compatibility.md) </span></span>  
 <span data-ttu-id="e9f20-152">[Microsoft .NET Framework 支援週期原則](http://go.microsoft.com/fwlink/p/?LinkId=248212) </span><span class="sxs-lookup"><span data-stu-id="e9f20-152">[Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/p/?LinkId=248212) </span></span>  
 [<span data-ttu-id="e9f20-153">.NET Framework 4 移轉問題</span><span class="sxs-lookup"><span data-stu-id="e9f20-153">.NET Framework 4 Migration Issues</span></span>](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)

