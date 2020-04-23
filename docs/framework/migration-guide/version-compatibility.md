---
title: .NET 架構中的版本相容性
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: 2e268753bf5941e9d28ee2bdd82ce77016ddf01a
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102979"
---
# <a name="version-compatibility"></a><span data-ttu-id="545fe-102">版本相容性</span><span class="sxs-lookup"><span data-stu-id="545fe-102">Version compatibility</span></span>

<span data-ttu-id="545fe-103">回溯相容性表示針對特定平台版本開發的應用程式將會在該平台的較新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="545fe-103">Backward compatibility means that an app that was developed for a particular version of a platform will run on later versions of that platform.</span></span> <span data-ttu-id="545fe-104">.NET Framework 嘗試最大化向後相容性:為 .NET Framework 的一個版本編寫的原始程式碼應編譯於 .NET Framework 的更高版本,而在 .NET Framework 的一個版本上運行的二進位檔案應在 .NET Framework 的更高版本中的行為相同。</span><span class="sxs-lookup"><span data-stu-id="545fe-104">.NET Framework tries to maximize backward compatibility: Source code written for one version of .NET Framework should compile on later versions of .NET Framework, and binaries that run on one version of .NET Framework should behave identically on later versions of .NET Framework.</span></span>

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a><span data-ttu-id="545fe-105">套用的版本相容性</span><span class="sxs-lookup"><span data-stu-id="545fe-105">Version compatibility for apps</span></span>

<span data-ttu-id="545fe-106">默認情況下,應用在為其構建的.NET框架版本上運行。</span><span class="sxs-lookup"><span data-stu-id="545fe-106">By default, an app runs on the version of .NET Framework that it was built for.</span></span> <span data-ttu-id="545fe-107">如果該版本不存在，且應用程式組態檔不會定義支援的版本，則可能會發生 .NET Framework 初始化錯誤。</span><span class="sxs-lookup"><span data-stu-id="545fe-107">If that version isn't present and the app configuration file doesn't define supported versions, a .NET Framework initialization error may occur.</span></span> <span data-ttu-id="545fe-108">在此例中，嘗試執行應用程式的作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="545fe-108">In this case, the attempt to run the app will fail.</span></span>

<span data-ttu-id="545fe-109">要定義應用運行的特定版本,請向應用的設定檔中添加一個或多個[\<受支援的 Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="545fe-109">To define the specific versions on which your app runs, add one or more [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) elements to your app's configuration file.</span></span> <span data-ttu-id="545fe-110">每一個 `<supportedRuntime>` 項目都會列出支援的執行階段版本，最先指定的是最優先的版本，而最後指定的則是優先順序最低的版本。</span><span class="sxs-lookup"><span data-stu-id="545fe-110">Each `<supportedRuntime>` element lists a supported version of the runtime, with the first specifying the most preferred version and the last specifying the least preferred version.</span></span>

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

<span data-ttu-id="545fe-111">如需詳細資訊，請參閱[如何：設定應用程式以支援 .NET Framework 4 或 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)。</span><span class="sxs-lookup"><span data-stu-id="545fe-111">For more information, see [How to: Configure an App to Support .NET Framework 4 or 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).</span></span>

## <a name="version-compatibility-for-components"></a><span data-ttu-id="545fe-112">元件的版本相容性</span><span class="sxs-lookup"><span data-stu-id="545fe-112">Version compatibility for components</span></span>

<span data-ttu-id="545fe-113">應用程式可以控制其執行的 .NET Framework 版本，元件則不能。</span><span class="sxs-lookup"><span data-stu-id="545fe-113">An app can control the version of the .NET Framework on which it runs, but a component can't.</span></span> <span data-ttu-id="545fe-114">元件和類別庫會載入至特定應用程式的內容中，這就是為什麼它們會自動執行應用程式所執行的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="545fe-114">Components and class libraries are loaded in the context of a particular app, and that's why they automatically run on the version of the .NET Framework that the app runs on.</span></span>

<span data-ttu-id="545fe-115">由於這項限制，所以相容性保證對於元件特別重要。</span><span class="sxs-lookup"><span data-stu-id="545fe-115">Because of this restriction, compatibility guarantees are especially important for components.</span></span> <span data-ttu-id="545fe-116">從 .NET Framework 4 開始，您可以指定元件在多個版本中維持相容所需的程度，方法是將 <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> 屬性套用至該元件。</span><span class="sxs-lookup"><span data-stu-id="545fe-116">Starting with the .NET Framework 4, you can specify the degree to which a component is expected to remain compatible across multiple versions by applying the <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> attribute to that component.</span></span> <span data-ttu-id="545fe-117">工具可以使用這個屬性來偵測將來的元件版本中，是否有可能違反相容性保證的狀況。</span><span class="sxs-lookup"><span data-stu-id="545fe-117">Tools can use this attribute to detect potential violations of the compatibility guarantee in future versions of a component.</span></span>

## <a name="backward-compatibility"></a><span data-ttu-id="545fe-118">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="545fe-118">Backward compatibility</span></span>

<span data-ttu-id="545fe-119">.NET Framework 4.5 和更新版本可以與使用舊版 .NET Framework 所建置的應用程式回溯相容。</span><span class="sxs-lookup"><span data-stu-id="545fe-119">The .NET Framework 4.5 and later versions are backward-compatible with apps that were built with earlier versions of the .NET Framework.</span></span> <span data-ttu-id="545fe-120">換句話說，使用舊版所建置的應用程式和元件不需經過修改，就可在 .NET Framework 4.5 和更新版本上運作。</span><span class="sxs-lookup"><span data-stu-id="545fe-120">In other words, apps and components built with previous versions will work without modification on the .NET Framework 4.5 and later versions.</span></span> <span data-ttu-id="545fe-121">不過，應用程式預設會在作為其開發目標的通用語言執行平台版本上執行，因此您可能需要提供組態檔，才能讓您的應用程式在 .NET Framework 4.5 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="545fe-121">However, by default, apps run on the version of the common language runtime for which they were developed, so you may have to provide a configuration file to enable your app to run on the .NET Framework 4.5 or later versions.</span></span> <span data-ttu-id="545fe-122">如需詳細資訊，請參閱本文前面的[應用程式的版本相容性](#Apps)一節。</span><span class="sxs-lookup"><span data-stu-id="545fe-122">For more information, see the [Version compatibility for apps](#Apps) section earlier in this article.</span></span>

<span data-ttu-id="545fe-123">在實際操作中，.NET Framework 中似乎前後不一致的變更以及程式設計技術的變更可能會破壞此相容性。</span><span class="sxs-lookup"><span data-stu-id="545fe-123">In practice, this compatibility can be broken by seemingly inconsequential changes in the .NET Framework and changes in programming techniques.</span></span> <span data-ttu-id="545fe-124">例如，.NET Framework 4.5 中的效能改良可能會暴露在舊版不會發生的競爭情況。</span><span class="sxs-lookup"><span data-stu-id="545fe-124">For example, performance improvements in the .NET Framework 4.5 can expose a race condition that did not occur on earlier versions.</span></span> <span data-ttu-id="545fe-125">同樣地，使用 .NET Framework 組件的硬式編碼路徑、搭配特定版本的 .NET Framework 執行相等比較以及使用反映來取得私用欄位的值，都不是具有回溯相容性的作法。</span><span class="sxs-lookup"><span data-stu-id="545fe-125">Similarly, using a hard-coded path to .NET Framework assemblies, performing an equality comparison with a particular version of the .NET Framework, and getting the value of a private field by using reflection are not backward-compatible practices.</span></span> <span data-ttu-id="545fe-126">此外，每一個 .NET Framework 版本都包含可能會影響某些應用程式與元件之相容性的 Bug 修正和安全性相關的變更。</span><span class="sxs-lookup"><span data-stu-id="545fe-126">In addition, each version of the .NET Framework includes bug fixes and security-related changes that can affect the compatibility of some apps and components.</span></span>

<span data-ttu-id="545fe-127">如果您的應用程式或元件在 .NET Framework 4.5 (包括其點版本，.NET Framework 4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2 或 4.8) 上無法如預期運作，請使用下列檢查清單：</span><span class="sxs-lookup"><span data-stu-id="545fe-127">If your app or component doesn't work as expected on the .NET Framework 4.5 (including its point releases, the .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8), use the following checklists:</span></span>

- <span data-ttu-id="545fe-128">如果應用已開發為以 .NET 框架 4.0 開頭的任何版本的 .NET Framework 上運行,請參閱[應用程式相容性](application-compatibility.md),以在目標 .NET Framework 版本和應用運行的版本之間生成更改清單。</span><span class="sxs-lookup"><span data-stu-id="545fe-128">If your app was developed to run on any version of the .NET Framework starting with the .NET Framework 4.0, see [Application compatibility](application-compatibility.md) to generate lists of changes between your targeted .NET Framework version and the version on which your app is running.</span></span>

- <span data-ttu-id="545fe-129">如果您有 .NET Framework 3.5 應用程式，另請參閱 [.NET Framework 4 移轉問題](../migration-guide/net-framework-4-migration-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="545fe-129">If you have a .NET Framework 3.5 app, also see [.NET Framework 4 Migration Issues](../migration-guide/net-framework-4-migration-issues.md).</span></span>

- <span data-ttu-id="545fe-130">如果您有 .NET Framework 2.0 應用程式，另請參閱 [.NET Framework 3.5 SP1 中的變更](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="545fe-130">If you have a .NET Framework 2.0 app, also see [Changes in .NET Framework 3.5 SP1](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)).</span></span>

- <span data-ttu-id="545fe-131">如果您有 .NET Framework 1.1 應用程式，另請參閱 [.NET Framework 2.0 中的變更](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="545fe-131">If you have a .NET Framework 1.1 app, also see [Changes in .NET Framework 2.0](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)).</span></span>

- <span data-ttu-id="545fe-132">如果您正在重新編譯現有原始程式碼以便在 .NET Framework 4.5 或其點版本執行，或如果您正在開發的新版本應用程式或元件針對 .NET Framework 4.5，或針對來自其現有原始程式碼基底的點版本，請檢查 [.NET Framework 類別庫中已淘汰的功能](../whats-new/whats-obsolete.md)中已淘汰類型和成員，並套用所述的因應措施。</span><span class="sxs-lookup"><span data-stu-id="545fe-132">If you're recompiling existing source code to run on the .NET Framework 4.5 or its point releases, or if you're developing a new version of an app or component that targets the .NET Framework 4.5 or its point releases from an existing source code base, check [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) for obsolete types and members, and apply the workaround described.</span></span> <span data-ttu-id="545fe-133">(之前編譯的程式碼將會針對已標示為過時的型別和成員繼續執行)。</span><span class="sxs-lookup"><span data-stu-id="545fe-133">(Previously compiled code will continue to run against types and members that have been marked as obsolete.)</span></span>

- <span data-ttu-id="545fe-134">如果您認為 .NET Framework 4.5 中的變更已破壞您的應用程式，請檢查[執行階段設定結構描述](../configure-apps/file-schema/runtime/index.md)，特別是 [\<Appcontextswitchoverrides > 項目](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，以判斷您是否可以在您的應用程式組態檔中使用執行階段設定來還原先前行為。</span><span class="sxs-lookup"><span data-stu-id="545fe-134">If you determine that a change in the .NET Framework 4.5 has broken your app, check the [Runtime Settings Schema](../configure-apps/file-schema/runtime/index.md), and particularly the [\<AppContextSwitchOverrides> Element](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), to determine whether you can use a runtime setting in your app's configuration file to restore the previous behavior.</span></span>

- <span data-ttu-id="545fe-135">如果您遇到未記載的問題，請在 [.NET 開發人員社群網站](https://developercommunity.visualstudio.com/spaces/61/index.html)或 [Microsoft/dotnet GitHub 存放庫](https://github.com/microsoft/dotnet/issues)中開啟問題。</span><span class="sxs-lookup"><span data-stu-id="545fe-135">If you come across an issue that isn't documented, open a problem on the [Developer Community site for .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) or open an issue in the [Microsoft/dotnet GitHub repo](https://github.com/microsoft/dotnet/issues).</span></span>

## <a name="side-by-side-execution"></a><span data-ttu-id="545fe-136">並存執行</span><span class="sxs-lookup"><span data-stu-id="545fe-136">Side-by-side execution</span></span>

<span data-ttu-id="545fe-137">如果找不到適合您的問題的解決方法,請記住.NET Framework 4.5(或其其中一個點版本)與版本 1.1、2.0 和 3.5 並行運行,並且是替換版本 4 的就地更新。</span><span class="sxs-lookup"><span data-stu-id="545fe-137">If you can't find a suitable workaround for your issue, remember that .NET Framework 4.5 (or one of its point releases) runs side by side with versions 1.1, 2.0, and 3.5, and is an in-place update that replaces version 4.</span></span> <span data-ttu-id="545fe-138">對於針對版本 1.1、2.0 和 3.5 的應用,可以在目標電腦上安裝適當的版本 .NET Framework,以在其最佳環境中運行應用。</span><span class="sxs-lookup"><span data-stu-id="545fe-138">For apps that target versions 1.1, 2.0, and 3.5, you can install the appropriate version of .NET Framework on the target machine to run the app in its best environment.</span></span> <span data-ttu-id="545fe-139">如需並存執行的詳細資訊，請參閱[並存執行](../deployment/side-by-side-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="545fe-139">For more information about side-by-side execution, see [Side-by-Side Execution](../deployment/side-by-side-execution.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="545fe-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="545fe-140">See also</span></span>

- [<span data-ttu-id="545fe-141">新功能</span><span class="sxs-lookup"><span data-stu-id="545fe-141">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="545fe-142">類別庫中的過時功能</span><span class="sxs-lookup"><span data-stu-id="545fe-142">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="545fe-143">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="545fe-143">Application Compatibility</span></span>](../migration-guide/application-compatibility.md)
- [<span data-ttu-id="545fe-144">.NET 框架官方支援政策</span><span class="sxs-lookup"><span data-stu-id="545fe-144">.NET Framework official support policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [<span data-ttu-id="545fe-145">.NET 框架 4 移轉問題</span><span class="sxs-lookup"><span data-stu-id="545fe-145">.NET Framework 4 Migration Issues</span></span>](../migration-guide/net-framework-4-migration-issues.md)
