---
title: .NET Framework 的版本相容性
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8db23f8e670406faff01644e751a948096f5fc7c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592888"
---
# <a name="version-compatibility-in-the-net-framework"></a><span data-ttu-id="6a874-102">.NET Framework 的版本相容性</span><span class="sxs-lookup"><span data-stu-id="6a874-102">Version compatibility in the .NET Framework</span></span>

<span data-ttu-id="6a874-103">回溯相容性表示針對特定平台版本開發的應用程式將會在該平台的較新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="6a874-103">Backward compatibility means that an app that was developed for a particular version of a platform will run on later versions of that platform.</span></span> <span data-ttu-id="6a874-104">.NET Framework 嘗試最大化回溯相容性：針對某一個 .NET Framework 版本撰寫的原始程式碼應該在較新版本的 .NET Framework 上編譯，且在某一個 .NET Framework 版本上執行的二進位檔行為應該與較新版本 .NET Framework 相同。</span><span class="sxs-lookup"><span data-stu-id="6a874-104">The .NET Framework tries to maximize backward compatibility: Source code written for one version of the .NET Framework should compile on later versions of the .NET Framework, and binaries that run on one version of the .NET Framework should behave identically on later versions of the .NET Framework.</span></span>

## <a name="Apps"></a> <span data-ttu-id="6a874-105">應用程式的版本相容性</span><span class="sxs-lookup"><span data-stu-id="6a874-105">Version compatibility for apps</span></span>

<span data-ttu-id="6a874-106">根據預設，應用程式會在其建置所針對的 .NET Framework 版本上執行。</span><span class="sxs-lookup"><span data-stu-id="6a874-106">By default, an app runs on the version of the .NET Framework that it was built for.</span></span> <span data-ttu-id="6a874-107">如果該版本不存在，且應用程式組態檔不會定義支援的版本，則可能會發生 .NET Framework 初始化錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a874-107">If that version isn't present and the app configuration file doesn't define supported versions, a .NET Framework initialization error may occur.</span></span> <span data-ttu-id="6a874-108">在此例中，嘗試執行應用程式的作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="6a874-108">In this case, the attempt to run the app will fail.</span></span>

<span data-ttu-id="6a874-109">若要定義應用程式執行所在的特定版本，請將一個或多個 [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) 項目新增至應用程式的組態檔。</span><span class="sxs-lookup"><span data-stu-id="6a874-109">To define the specific versions on which your app runs, add one or more [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) elements to your app's configuration file.</span></span> <span data-ttu-id="6a874-110">每一個 `<supportedRuntime>` 項目都會列出支援的執行階段版本，最先指定的是最優先的版本，而最後指定的則是優先順序最低的版本。</span><span class="sxs-lookup"><span data-stu-id="6a874-110">Each `<supportedRuntime>` element lists a supported version of the runtime, with the first specifying the most preferred version and the last specifying the least preferred version.</span></span>

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

<span data-ttu-id="6a874-111">如需詳細資訊，請參閱[如何：設定應用程式以支援 .NET Framework 4 或 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)。</span><span class="sxs-lookup"><span data-stu-id="6a874-111">For more information, see [How to: Configure an App to Support .NET Framework 4 or 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).</span></span>

## <a name="version-compatibility-for-components"></a><span data-ttu-id="6a874-112">元件的版本相容性</span><span class="sxs-lookup"><span data-stu-id="6a874-112">Version compatibility for components</span></span>

<span data-ttu-id="6a874-113">應用程式可以控制其執行的 .NET Framework 版本，元件則不能。</span><span class="sxs-lookup"><span data-stu-id="6a874-113">An app can control the version of the .NET Framework on which it runs, but a component can't.</span></span> <span data-ttu-id="6a874-114">元件和類別庫會載入至特定應用程式的內容中，這就是為什麼它們會自動執行應用程式所執行的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="6a874-114">Components and class libraries are loaded in the context of a particular app, and that's why they automatically run on the version of the .NET Framework that the app runs on.</span></span>

<span data-ttu-id="6a874-115">由於這項限制，所以相容性保證對於元件特別重要。</span><span class="sxs-lookup"><span data-stu-id="6a874-115">Because of this restriction, compatibility guarantees are especially important for components.</span></span> <span data-ttu-id="6a874-116">從 .NET Framework 4 開始，您可以指定元件在多個版本中維持相容所需的程度，方法是將 <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> 屬性套用至該元件。</span><span class="sxs-lookup"><span data-stu-id="6a874-116">Starting with the .NET Framework 4, you can specify the degree to which a component is expected to remain compatible across multiple versions by applying the <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> attribute to that component.</span></span> <span data-ttu-id="6a874-117">工具可以使用這個屬性來偵測將來的元件版本中，是否有可能違反相容性保證的狀況。</span><span class="sxs-lookup"><span data-stu-id="6a874-117">Tools can use this attribute to detect potential violations of the compatibility guarantee in future versions of a component.</span></span>

## <a name="backward-compatibility-and-the-net-framework"></a><span data-ttu-id="6a874-118">回溯相容性和 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6a874-118">Backward compatibility and the .NET Framework</span></span>

<span data-ttu-id="6a874-119">.NET Framework 4.5 和更新版本可以與使用舊版 .NET Framework 所建置的應用程式回溯相容。</span><span class="sxs-lookup"><span data-stu-id="6a874-119">The .NET Framework 4.5 and later versions are backward-compatible with apps that were built with earlier versions of the .NET Framework.</span></span> <span data-ttu-id="6a874-120">換句話說，使用舊版所建置的應用程式和元件不需經過修改，就可在 .NET Framework 4.5 和更新版本上運作。</span><span class="sxs-lookup"><span data-stu-id="6a874-120">In other words, apps and components built with previous versions will work without modification on the .NET Framework 4.5 and later versions.</span></span> <span data-ttu-id="6a874-121">不過，應用程式預設會在作為其開發目標的通用語言執行平台版本上執行，因此您可能需要提供組態檔，才能讓您的應用程式在 .NET Framework 4.5 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="6a874-121">However, by default, apps run on the version of the common language runtime for which they were developed, so you may have to provide a configuration file to enable your app to run on the .NET Framework 4.5 or later versions.</span></span> <span data-ttu-id="6a874-122">如需詳細資訊，請參閱本文前面的[應用程式的版本相容性](#Apps)一節。</span><span class="sxs-lookup"><span data-stu-id="6a874-122">For more information, see the [Version compatibility for apps](#Apps) section earlier in this article.</span></span>

<span data-ttu-id="6a874-123">在實際操作中，.NET Framework 中似乎前後不一致的變更以及程式設計技術的變更可能會破壞此相容性。</span><span class="sxs-lookup"><span data-stu-id="6a874-123">In practice, this compatibility can be broken by seemingly inconsequential changes in the .NET Framework and changes in programming techniques.</span></span> <span data-ttu-id="6a874-124">例如，.NET Framework 4.5 中的效能改良可能會暴露在舊版不會發生的競爭情況。</span><span class="sxs-lookup"><span data-stu-id="6a874-124">For example, performance improvements in the .NET Framework 4.5 can expose a race condition that did not occur on earlier versions.</span></span> <span data-ttu-id="6a874-125">同樣地，使用 .NET Framework 組件的硬式編碼路徑、搭配特定版本的 .NET Framework 執行相等比較以及使用反映來取得私用欄位的值，都不是具有回溯相容性的作法。</span><span class="sxs-lookup"><span data-stu-id="6a874-125">Similarly, using a hard-coded path to .NET Framework assemblies, performing an equality comparison with a particular version of the .NET Framework, and getting the value of a private field by using reflection are not backward-compatible practices.</span></span> <span data-ttu-id="6a874-126">此外，每一個 .NET Framework 版本都包含可能會影響某些應用程式與元件之相容性的 Bug 修正和安全性相關的變更。</span><span class="sxs-lookup"><span data-stu-id="6a874-126">In addition, each version of the .NET Framework includes bug fixes and security-related changes that can affect the compatibility of some apps and components.</span></span>

<span data-ttu-id="6a874-127">如果您的應用程式或元件在 .NET Framework 4.5 (包括其點版本，.NET Framework 4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8) 上無法如預期運作，請使用下列檢查清單：</span><span class="sxs-lookup"><span data-stu-id="6a874-127">If your app or component doesn't work as expected on the .NET Framework 4.5 (including its point releases, the .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8), use the following checklists:</span></span>

- <span data-ttu-id="6a874-128">如果您應用程式的開發目的是在開頭為 .NET Framework 4.0 之任何版本的 .NET Framework 上執行，請參閱 [.NET Framework 中的應用程式相容性](application-compatibility.md)，以產生目標 .NET Framework 版本與您應用程式所執行版本之間的變更清單。</span><span class="sxs-lookup"><span data-stu-id="6a874-128">If your app was developed to run on any version of the .NET Framework starting with the .NET Framework 4.0, see [Application Compatibility in the .NET Framework](application-compatibility.md) to generate lists of changes between your targeted .NET Framework version and the version on which your app is running.</span></span>

- <span data-ttu-id="6a874-129">如果您有 .NET Framework 3.5 應用程式，另請參閱 [.NET Framework 4 移轉問題](../migration-guide/net-framework-4-migration-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="6a874-129">If you have a .NET Framework 3.5 app, also see [.NET Framework 4 Migration Issues](../migration-guide/net-framework-4-migration-issues.md).</span></span>

- <span data-ttu-id="6a874-130">如果您有 .NET Framework 2.0 應用程式，另請參閱 [.NET Framework 3.5 SP1 中的變更](https://go.microsoft.com/fwlink/?LinkId=186989)。</span><span class="sxs-lookup"><span data-stu-id="6a874-130">If you have a .NET Framework 2.0 app, also see [Changes in .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkId=186989).</span></span>

- <span data-ttu-id="6a874-131">如果您有 .NET Framework 1.1 應用程式，另請參閱 [.NET Framework 2.0 中的變更](https://go.microsoft.com/fwlink/?LinkID=125263)。</span><span class="sxs-lookup"><span data-stu-id="6a874-131">If you have a .NET Framework 1.1 app, also see [Changes in .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkID=125263).</span></span>

- <span data-ttu-id="6a874-132">如果您正在重新編譯現有原始程式碼以便在 .NET Framework 4.5 或其點版本執行，或如果您正在開發的新版本應用程式或元件針對 .NET Framework 4.5，或針對來自其現有原始程式碼基底的點版本，請檢查 [.NET Framework 類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)中已淘汰類型和成員，並套用所述的因應措施。</span><span class="sxs-lookup"><span data-stu-id="6a874-132">If you're recompiling existing source code to run on the .NET Framework 4.5 or its point releases, or if you're developing a new version of an app or component that targets the .NET Framework 4.5 or its point releases from an existing source code base, check [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) for obsolete types and members, and apply the workaround described.</span></span> <span data-ttu-id="6a874-133">(之前編譯的程式碼將會針對已標示為過時的型別和成員繼續執行)。</span><span class="sxs-lookup"><span data-stu-id="6a874-133">(Previously compiled code will continue to run against types and members that have been marked as obsolete.)</span></span>

- <span data-ttu-id="6a874-134">如果您認為 .NET Framework 4.5 中的變更已破壞您的應用程式，請檢查[執行階段設定結構描述](../configure-apps/file-schema/runtime/index.md)，特別是 [\<Appcontextswitchoverrides > 項目](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，以判斷您是否可以在您的應用程式組態檔中使用執行階段設定來還原先前行為。</span><span class="sxs-lookup"><span data-stu-id="6a874-134">If you determine that a change in the .NET Framework 4.5 has broken your app, check the [Runtime Settings Schema](../configure-apps/file-schema/runtime/index.md), and particularly the [\<AppContextSwitchOverrides> Element](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), to determine whether you can use a runtime setting in your app's configuration file to restore the previous behavior.</span></span>

- <span data-ttu-id="6a874-135">如果您遇到未記載的問題，請在 [.NET 開發人員社群網站](https://developercommunity.visualstudio.com/spaces/61/index.html)或 [Microsoft/dotnet GitHub 存放庫](https://github.com/microsoft/dotnet/issues)中開啟問題。</span><span class="sxs-lookup"><span data-stu-id="6a874-135">If you come across an issue that isn't documented, open a problem on the [Developer Community site for .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) or open an issue in the [Microsoft/dotnet GitHub repo](https://github.com/microsoft/dotnet/issues).</span></span>

## <a name="compatibility-and-side-by-side-execution"></a><span data-ttu-id="6a874-136">相容性和並存執行</span><span class="sxs-lookup"><span data-stu-id="6a874-136">Compatibility and side-by-side execution</span></span>

<span data-ttu-id="6a874-137">如果您找不到適當的因應措施來解決問題，請記得 .NET Framework 4.5 (或其點版本其中之一) 與版本 1.1、2.0 和 3.5 並存執行，且是取代第 4 版的就地更新。</span><span class="sxs-lookup"><span data-stu-id="6a874-137">If you can't find a suitable workaround for your issue, remember that the .NET Framework 4.5 (or one of its point releases) runs side by side with versions 1.1, 2.0, and 3.5, and is an in-place update that replaces version 4.</span></span> <span data-ttu-id="6a874-138">若是以 1.1、2.0 和 3.5 版為目標的應用程式，您可以在目標電腦上安裝適當的 .NET Framework 版本，以便在最佳環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a874-138">For apps that target versions 1.1, 2.0, and 3.5, you can install the appropriate version of the .NET Framework on the target machine to run the app in its best environment.</span></span> <span data-ttu-id="6a874-139">如需並存執行的詳細資訊，請參閱[並存執行](../deployment/side-by-side-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="6a874-139">For more information about side-by-side execution, see [Side-by-Side Execution](../deployment/side-by-side-execution.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a874-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a874-140">See also</span></span>

- [<span data-ttu-id="6a874-141">新功能</span><span class="sxs-lookup"><span data-stu-id="6a874-141">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="6a874-142">類別庫中已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="6a874-142">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="6a874-143">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="6a874-143">Application Compatibility</span></span>](../migration-guide/application-compatibility.md)
- [<span data-ttu-id="6a874-144">Microsoft .NET Framework 支援週期原則</span><span class="sxs-lookup"><span data-stu-id="6a874-144">Microsoft .NET Framework Support Lifecycle Policy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [<span data-ttu-id="6a874-145">.NET Framework 4 移轉問題</span><span class="sxs-lookup"><span data-stu-id="6a874-145">.NET Framework 4 Migration Issues</span></span>](../migration-guide/net-framework-4-migration-issues.md)
