---
title: 衛星程式集載入演算法 - .NET 核心
description: .NET Core 中衛星程式集載入演算法的詳細資訊說明
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "70234624"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="f5e2f-103">衛星程式集載入演算法</span><span class="sxs-lookup"><span data-stu-id="f5e2f-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="f5e2f-104">附屬程式集用於存儲為語言和文化定制的當地語系化資源。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="f5e2f-105">附屬程式集使用的載入演算法與常規託管程式集不同。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="f5e2f-106">何時載入附屬程式集？</span><span class="sxs-lookup"><span data-stu-id="f5e2f-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="f5e2f-107">載入當地語系化資源時載入附屬程式集。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="f5e2f-108">載入當地語系化資源的基本 API 是類<xref:System.Resources.ResourceManager?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="f5e2f-109">最終，<xref:System.Resources.ResourceManager>類將為每個<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType><xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>調用 方法。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f5e2f-110">更高級別 API 可能會抽象低級 API。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="f5e2f-111">演算法</span><span class="sxs-lookup"><span data-stu-id="f5e2f-111">Algorithm</span></span>

<span data-ttu-id="f5e2f-112">.NET Core 資源後援處理序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f5e2f-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="f5e2f-113">確定`active`<xref:System.Runtime.Loader.AssemblyLoadContext>實例。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="f5e2f-114">在所有情況下，`active`實例都是執行程式集的<xref:System.Runtime.Loader.AssemblyLoadContext>。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="f5e2f-115">實例`active`嘗試按優先順序順序載入請求的區域性的附屬程式集，其順序包括：</span><span class="sxs-lookup"><span data-stu-id="f5e2f-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="f5e2f-116">檢查其緩存。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-116">Checking its cache.</span></span>
    - <span data-ttu-id="f5e2f-117">檢查當前正在執行程式集的目錄，以執行與請求<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>匹配的子目錄（例如`es-MX`）。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="f5e2f-118">此功能在 3.0 之前未在 .NET Core 中實現。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="f5e2f-119">在 Linux 和 macOS 上，子目錄區分大小寫，必須：</span><span class="sxs-lookup"><span data-stu-id="f5e2f-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="f5e2f-120">完全符合的情況下。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-120">Exactly match case.</span></span>
        > - <span data-ttu-id="f5e2f-121">處於小寫字母中。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-121">Be in lower case.</span></span>

    - <span data-ttu-id="f5e2f-122">如果是`active`實例，<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>則通過運行[預設的衛星（資源）程式集探測](default-probing.md#satellite-resource-assembly-probing)邏輯。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="f5e2f-123">調用函數<xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="f5e2f-124">引發事件<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="f5e2f-125">引發事件<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="f5e2f-126">如果載入了附屬程式集：</span><span class="sxs-lookup"><span data-stu-id="f5e2f-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="f5e2f-127">便會引發 <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="f5e2f-128">將程式集搜索為請求的資源。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="f5e2f-129">如果運行時在程式集中找到資源，則使用它。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="f5e2f-130">如果找不到資源，會繼續搜尋。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f5e2f-131">為了在附屬組件內尋找資源，執行階段會搜尋目前 <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 的 <xref:System.Resources.ResourceManager> 所要求的資源檔。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5e2f-132">在資源檔中，它搜索請求的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="f5e2f-133">如果找不到任一個，就會將資源視為找不到。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="f5e2f-134">接下來運行時通過許多潛在級別搜索父區域性程式集，每次重複步驟 2 & 3。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="f5e2f-135">每個區域性只有一個父級，由<xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>屬性定義。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="f5e2f-136">當區域性的屬性為<xref:System.Globalization.CultureInfo.Parent%2A><xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>時，對父區域性的搜索將停止。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="f5e2f-137">對於<xref:System.Globalization.CultureInfo.InvariantCulture>，我們不會返回到步驟 2 & 3，而是繼續步驟 5。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="f5e2f-138">如果仍未找到資源，則使用預設（回退）區域性的資源。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="f5e2f-139">通常，主要應用程式組件中會包含預設文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="f5e2f-140">但是，您可以為<xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType><xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType>屬性指定。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f5e2f-141">此值表示資源的最終回退位置是附屬程式集，而不是主程式集。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f5e2f-142">預設區域性是最終的回退。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="f5e2f-143">因此，我們建議您始終在預設資源檔中包含一組詳盡的資源。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="f5e2f-144">這樣有助於防止擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="f5e2f-145">通過擁有詳盡集，您可以為所有資源提供回退，並確保使用者始終存在至少一個資源，即使它不是特定于區域性的資源。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="f5e2f-146">最後</span><span class="sxs-lookup"><span data-stu-id="f5e2f-146">Finally,</span></span>
   - <span data-ttu-id="f5e2f-147">如果運行時找不到預設（回退）區域性的資源檔，則引發 或<xref:System.Resources.MissingManifestResourceException><xref:System.Resources.MissingSatelliteAssemblyException>異常。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="f5e2f-148">如果找到資源檔但請求的資源不存在，則請求將返回`null`。</span><span class="sxs-lookup"><span data-stu-id="f5e2f-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
