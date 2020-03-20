---
title: 運行時和重新置放更改 - .NET 框架
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196693"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="44900-102">.NET 框架中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="44900-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="44900-103">相容性是每個 .NET 版本的一個重要目標。</span><span class="sxs-lookup"><span data-stu-id="44900-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="44900-104">相容性可確保每個版本都是附加版本，因此以前的版本將繼續工作。</span><span class="sxs-lookup"><span data-stu-id="44900-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="44900-105">另一方面，對以前功能的更改（例如，為了提高性能、解決安全問題或修復 Bug）可能會導致現有代碼或在更高版本下運行的現有應用程式中出現相容性問題。</span><span class="sxs-lookup"><span data-stu-id="44900-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="44900-106">每個應用都針對 .NET 框架的特定版本：：</span><span class="sxs-lookup"><span data-stu-id="44900-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="44900-107">在 Visual Studio 中定義目標架構。</span><span class="sxs-lookup"><span data-stu-id="44900-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="44900-108">在專案檔中指定目標架構。</span><span class="sxs-lookup"><span data-stu-id="44900-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="44900-109">將 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 套用至原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="44900-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="44900-110">從 .NET 框架的一個版本遷移到另一個版本時，需要考慮兩種類型的更改：</span><span class="sxs-lookup"><span data-stu-id="44900-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="44900-111">運行時更改</span><span class="sxs-lookup"><span data-stu-id="44900-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="44900-112">重新置放更改</span><span class="sxs-lookup"><span data-stu-id="44900-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="44900-113">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="44900-113">Runtime changes</span></span>

<span data-ttu-id="44900-114">運行時問題是將新運行時放置在電腦上且應用行為發生更改時出現的問題。</span><span class="sxs-lookup"><span data-stu-id="44900-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="44900-115">在比目標版本更新的版本中運行時，.NET Framework 使用*古怪的*行為來類比較舊的目標版本。</span><span class="sxs-lookup"><span data-stu-id="44900-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="44900-116">應用在較新版本上運行，但運行時就像它在舊版本上運行一樣。</span><span class="sxs-lookup"><span data-stu-id="44900-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="44900-117">.NET Framework 版本間的許多相容性問題是透過這種古怪的模型而降低。</span><span class="sxs-lookup"><span data-stu-id="44900-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="44900-118">例如，如果為 .NET Framework 4.0 編譯了二進位檔案，但在具有 .NET Framework 4.5 或更高版本的電腦上運行，則該二進位檔案在 .NET Framework 4.0 相容模式下運行。</span><span class="sxs-lookup"><span data-stu-id="44900-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="44900-119">這意味著更高版本中的許多更改不會影響二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="44900-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="44900-120">應用程式目標 .NET Framework 的版本由代碼運行的應用程式域的入口程式集的目標版本確定。</span><span class="sxs-lookup"><span data-stu-id="44900-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="44900-121">在該應用程式域中載入的所有其他程式集都針對該版本。</span><span class="sxs-lookup"><span data-stu-id="44900-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="44900-122">例如，對於可執行檔，可執行目標的版本是該應用程式域中的所有程式集都運行的相容性模式。</span><span class="sxs-lookup"><span data-stu-id="44900-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="44900-123">要查看適用于環境的運行時更改清單，請選擇當前定位的 .NET Framework 版本，然後選擇要遷移到的版本：</span><span class="sxs-lookup"><span data-stu-id="44900-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="44900-124">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="44900-124">Retargeting changes</span></span>

<span data-ttu-id="44900-125">重新定向更改是在重新編譯程式集以定位較新版本時發生的更改。</span><span class="sxs-lookup"><span data-stu-id="44900-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="44900-126">定位較新版本意味著程式集選擇新功能以及舊功能的潛在相容性問題。</span><span class="sxs-lookup"><span data-stu-id="44900-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="44900-127">要查看適用于環境的重定向更改清單，請選擇當前定位的 .NET Framework 版本，然後選擇要遷移到的版本：</span><span class="sxs-lookup"><span data-stu-id="44900-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="44900-128">影響分類</span><span class="sxs-lookup"><span data-stu-id="44900-128">Impact classification</span></span>

<span data-ttu-id="44900-129">在描述運行時和重定向更改的主題中，例如，[從 4.7.2 遷移到 4.8 的重定向更改](retargeting/4.7.2-4.8.md)，各個項按其預期影響進行分類，如下所示：</span><span class="sxs-lookup"><span data-stu-id="44900-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="44900-130">**主要**</span><span class="sxs-lookup"><span data-stu-id="44900-130">**Major**</span></span>\
<span data-ttu-id="44900-131">影響大量應用程式或需要大幅修改程式碼的重大變更。</span><span class="sxs-lookup"><span data-stu-id="44900-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="44900-132">**小**</span><span class="sxs-lookup"><span data-stu-id="44900-132">**Minor**</span></span>\
<span data-ttu-id="44900-133">影響少量應用程式或需要稍微修改程式碼的變更。</span><span class="sxs-lookup"><span data-stu-id="44900-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="44900-134">**邊緣案例**</span><span class="sxs-lookup"><span data-stu-id="44900-134">**Edge case**</span></span>\
<span data-ttu-id="44900-135">在非常特定 (罕見) 的情況下影響應用程式的變更。</span><span class="sxs-lookup"><span data-stu-id="44900-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="44900-136">**透明**</span><span class="sxs-lookup"><span data-stu-id="44900-136">**Transparent**</span></span>\
<span data-ttu-id="44900-137">此變更對應用程式的開發人員或使用者的影響不明顯。</span><span class="sxs-lookup"><span data-stu-id="44900-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="44900-138">發生此變更的應用程式應該不需要修改。</span><span class="sxs-lookup"><span data-stu-id="44900-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="44900-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44900-139">See also</span></span>

- [<span data-ttu-id="44900-140">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="44900-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="44900-141">新功能</span><span class="sxs-lookup"><span data-stu-id="44900-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="44900-142">過時的內容</span><span class="sxs-lookup"><span data-stu-id="44900-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
