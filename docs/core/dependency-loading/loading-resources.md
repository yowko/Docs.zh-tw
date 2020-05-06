---
title: 附屬元件載入演算法-.NET Core
description: 描述 .NET Core 中附屬元件載入演算法的詳細資料
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 17f29a9aca79019daa91736e586bf1b6b753a9ec
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859526"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="466ab-103">附屬元件載入演算法</span><span class="sxs-lookup"><span data-stu-id="466ab-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="466ab-104">附屬元件是用來儲存針對語言和文化特性自訂的當地語系化資源。</span><span class="sxs-lookup"><span data-stu-id="466ab-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="466ab-105">附屬元件會使用與一般 managed 元件不同的載入演算法。</span><span class="sxs-lookup"><span data-stu-id="466ab-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="466ab-106">何時會載入附屬元件？</span><span class="sxs-lookup"><span data-stu-id="466ab-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="466ab-107">載入當地語系化資源時，會載入附屬元件。</span><span class="sxs-lookup"><span data-stu-id="466ab-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="466ab-108">用來載入當地語系化資源的基本 API 是<xref:System.Resources.ResourceManager?displayProperty=fullName>類別。</span><span class="sxs-lookup"><span data-stu-id="466ab-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="466ab-109">最後， <xref:System.Resources.ResourceManager>類別會針對每<xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>個<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="466ab-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="466ab-110">較高層級的 Api 可能會抽象化低層級 API。</span><span class="sxs-lookup"><span data-stu-id="466ab-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="466ab-111">演算法</span><span class="sxs-lookup"><span data-stu-id="466ab-111">Algorithm</span></span>

<span data-ttu-id="466ab-112">.NET Core 資源後援處理序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="466ab-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="466ab-113">`active` <xref:System.Runtime.Loader.AssemblyLoadContext>判斷實例。</span><span class="sxs-lookup"><span data-stu-id="466ab-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="466ab-114">在所有情況下， `active`實例都是執行元件的<xref:System.Runtime.Loader.AssemblyLoadContext>。</span><span class="sxs-lookup"><span data-stu-id="466ab-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="466ab-115">`active`實例會嘗試載入所要求文化特性的附屬元件（依優先順序排列）：</span><span class="sxs-lookup"><span data-stu-id="466ab-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="466ab-116">正在檢查其快取。</span><span class="sxs-lookup"><span data-stu-id="466ab-116">Checking its cache.</span></span>
    - <span data-ttu-id="466ab-117">檢查目前執行中元件的目錄中是否有符合要求<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>的子目錄（例如`es-MX`）。</span><span class="sxs-lookup"><span data-stu-id="466ab-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="466ab-118">在3.0 之前，不會在 .NET Core 中實作為這項功能。</span><span class="sxs-lookup"><span data-stu-id="466ab-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="466ab-119">在 Linux 和 macOS 上，子目錄會區分大小寫，而且必須是：</span><span class="sxs-lookup"><span data-stu-id="466ab-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        >
        > - <span data-ttu-id="466ab-120">完全相符的大小寫。</span><span class="sxs-lookup"><span data-stu-id="466ab-120">Exactly match case.</span></span>
        > - <span data-ttu-id="466ab-121">以小寫。</span><span class="sxs-lookup"><span data-stu-id="466ab-121">Be in lower case.</span></span>

    - <span data-ttu-id="466ab-122">如果`active`是<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>實例，則執行預設的[附屬（資源）元件探查](default-probing.md#satellite-resource-assembly-probing)邏輯。</span><span class="sxs-lookup"><span data-stu-id="466ab-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="466ab-123"><xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="466ab-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="466ab-124">引發<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="466ab-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="466ab-125">引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="466ab-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="466ab-126">如果載入附屬元件：</span><span class="sxs-lookup"><span data-stu-id="466ab-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="466ab-127">便會引發 <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="466ab-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="466ab-128">元件會在其中搜尋所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="466ab-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="466ab-129">如果執行時間在元件中找到資源，則會使用它。</span><span class="sxs-lookup"><span data-stu-id="466ab-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="466ab-130">如果找不到資源，會繼續搜尋。</span><span class="sxs-lookup"><span data-stu-id="466ab-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="466ab-131">為了在附屬組件內尋找資源，執行階段會搜尋目前 <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 的 <xref:System.Resources.ResourceManager> 所要求的資源檔。</span><span class="sxs-lookup"><span data-stu-id="466ab-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="466ab-132">在資源檔中，它會搜尋所要求的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="466ab-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="466ab-133">如果找不到任一個，就會將資源視為找不到。</span><span class="sxs-lookup"><span data-stu-id="466ab-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="466ab-134">執行時間接著會透過許多可能的層級來搜尋父文化特性元件，每次重複步驟 2 & 3。</span><span class="sxs-lookup"><span data-stu-id="466ab-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="466ab-135">每個文化<xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>特性都只有一個父系，這是由屬性所定義。</span><span class="sxs-lookup"><span data-stu-id="466ab-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="466ab-136">當文化特性的<xref:System.Globalization.CultureInfo.Parent%2A>屬性為時，會<xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>停止搜尋父文化特性。</span><span class="sxs-lookup"><span data-stu-id="466ab-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="466ab-137">在<xref:System.Globalization.CultureInfo.InvariantCulture>中，我們不會回到步驟 2 & 3，而是繼續執行步驟5。</span><span class="sxs-lookup"><span data-stu-id="466ab-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="466ab-138">如果仍找不到資源，則會使用預設（fallback）文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="466ab-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="466ab-139">通常，主要應用程式組件中會包含預設文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="466ab-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="466ab-140">不過，您可以為<xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType>屬性指定。</span><span class="sxs-lookup"><span data-stu-id="466ab-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="466ab-141">此值表示資源的最終回退位置是附屬元件，而不是主要元件。</span><span class="sxs-lookup"><span data-stu-id="466ab-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="466ab-142">預設的文化特性是最終的回溯。</span><span class="sxs-lookup"><span data-stu-id="466ab-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="466ab-143">因此，我們建議您一律在預設資源檔中包含一組完整的資源。</span><span class="sxs-lookup"><span data-stu-id="466ab-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="466ab-144">這樣有助於防止擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="466ab-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="466ab-145">藉由全面設定，您可以提供所有資源的回復，並確保使用者一律至少有一個資源，即使它不是特定文化特性。</span><span class="sxs-lookup"><span data-stu-id="466ab-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="466ab-146">最後</span><span class="sxs-lookup"><span data-stu-id="466ab-146">Finally,</span></span>
   - <span data-ttu-id="466ab-147">如果執行時間找不到預設（fallback）文化特性的資源檔，則<xref:System.Resources.MissingManifestResourceException>會<xref:System.Resources.MissingSatelliteAssemblyException>擲回或例外狀況。</span><span class="sxs-lookup"><span data-stu-id="466ab-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="466ab-148">如果找到資源檔，但要求的資源不存在，則要求會傳回`null`。</span><span class="sxs-lookup"><span data-stu-id="466ab-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
