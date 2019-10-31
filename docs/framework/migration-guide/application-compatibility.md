---
title: 執行時間和重定變更-.NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196693"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="6fbcb-102">.NET Framework 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="6fbcb-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="6fbcb-103">相容性是每個 .NET 版本的重要目標。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="6fbcb-104">相容性可確保每個版本都是附加的，因此舊版會繼續工作。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="6fbcb-105">另一方面，對先前的功能所做的變更（例如，為了改善效能、解決安全性問題或修正錯誤）可能會導致現有程式碼中的相容性問題，或在更新版本下執行的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="6fbcb-106">每個應用程式都是以特定版本的 .NET Framework 為目標，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6fbcb-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="6fbcb-107">在 Visual Studio 中定義目標架構。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="6fbcb-108">在專案檔中指定目標架構。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="6fbcb-109">將 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> 套用至原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="6fbcb-110">從 .NET Framework 的某個版本遷移至另一個版本時，需要考慮兩種類型的變更：</span><span class="sxs-lookup"><span data-stu-id="6fbcb-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="6fbcb-111">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="6fbcb-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="6fbcb-112">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="6fbcb-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="6fbcb-113">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="6fbcb-113">Runtime changes</span></span>

<span data-ttu-id="6fbcb-114">執行時間問題是在電腦上放置新的執行時間，以及應用程式的行為變更時所發生的問題。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="6fbcb-115">當在比目標較新的版本上執行時，.NET Framework 會使用*quirked*行為來模擬較舊的目標版本。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="6fbcb-116">應用程式會在較新的版本上執行，但會如同在較舊的版本上執行一樣。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="6fbcb-117">.NET Framework 版本間的許多相容性問題是透過這種古怪的模型而降低。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="6fbcb-118">例如，如果二進位檔是針對 .NET Framework 4.0 編譯，但在具有 .NET Framework 4.5 或更新版本的電腦上執行，則會在 .NET Framework 4.0 相容性模式下執行。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="6fbcb-119">這表示，較新版本中的許多變更不會影響二進位檔。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="6fbcb-120">應用程式目標的 .NET Framework 版本是由程式碼執行所在之應用程式域的專案元件目標版本所決定。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="6fbcb-121">載入該應用程式域中的所有其他元件都會以該版本為目標。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="6fbcb-122">例如，如果是可執行檔，則可執行檔目標的版本是該應用程式域中的所有元件在其下執行的相容性模式。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="6fbcb-123">若要查看適用于您環境的執行時間變更清單，請選取您目前設為目標的 .NET Framework 版本，然後選擇您想要遷移到的版本：</span><span class="sxs-lookup"><span data-stu-id="6fbcb-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="6fbcb-124">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="6fbcb-124">Retargeting changes</span></span>

<span data-ttu-id="6fbcb-125">重定變更是元件重新編譯成以較新版本為目標時所發生的變更。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="6fbcb-126">以較新的版本為目標，表示元件會加入宣告新功能，以及舊功能的潛在相容性問題。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="6fbcb-127">若要查看適用于您環境的重定變更清單，請選取您目前設為目標的 .NET Framework 版本，然後選擇您想要遷移到的版本：</span><span class="sxs-lookup"><span data-stu-id="6fbcb-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="6fbcb-128">影響分類</span><span class="sxs-lookup"><span data-stu-id="6fbcb-128">Impact classification</span></span>

<span data-ttu-id="6fbcb-129">在描述執行時間和重定變更的主題中（例如，[重定從4.7.2 遷移到4.8 的變更](retargeting/4.7.2-4.8.md)），個別專案會依其預期的影響分類，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6fbcb-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="6fbcb-130">**Major**</span><span class="sxs-lookup"><span data-stu-id="6fbcb-130">**Major**</span></span>\
<span data-ttu-id="6fbcb-131">影響大量應用程式或需要大幅修改程式碼的重大變更。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="6fbcb-132">**Minor**</span><span class="sxs-lookup"><span data-stu-id="6fbcb-132">**Minor**</span></span>\
<span data-ttu-id="6fbcb-133">影響少量應用程式或需要稍微修改程式碼的變更。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="6fbcb-134">**Edge 案例**</span><span class="sxs-lookup"><span data-stu-id="6fbcb-134">**Edge case**</span></span>\
<span data-ttu-id="6fbcb-135">在非常特定 (罕見) 的情況下影響應用程式的變更。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="6fbcb-136">**透明**</span><span class="sxs-lookup"><span data-stu-id="6fbcb-136">**Transparent**</span></span>\
<span data-ttu-id="6fbcb-137">此變更對應用程式的開發人員或使用者的影響不明顯。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="6fbcb-138">發生此變更的應用程式應該不需要修改。</span><span class="sxs-lookup"><span data-stu-id="6fbcb-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fbcb-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="6fbcb-139">See also</span></span>

- [<span data-ttu-id="6fbcb-140">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="6fbcb-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="6fbcb-141">新增功能</span><span class="sxs-lookup"><span data-stu-id="6fbcb-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="6fbcb-142">過時功能</span><span class="sxs-lookup"><span data-stu-id="6fbcb-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
