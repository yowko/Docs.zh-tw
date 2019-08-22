---
title: <relativeBindForResources> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 859e8a12421ea92aa48c54317e052683eb8e83f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663489"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="5d154-102">\<Relativebindforresources> > 元素</span><span class="sxs-lookup"><span data-stu-id="5d154-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="5d154-103">最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="5d154-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="5d154-104">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="5d154-104">\<configuration> Element</span></span>  
<span data-ttu-id="5d154-105">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="5d154-105">\<runtime> Element</span></span>  
<span data-ttu-id="5d154-106">\<Relativebindforresources> > 元素</span><span class="sxs-lookup"><span data-stu-id="5d154-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d154-107">語法</span><span class="sxs-lookup"><span data-stu-id="5d154-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d154-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5d154-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5d154-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5d154-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d154-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5d154-110">Attributes</span></span>  
  
|<span data-ttu-id="5d154-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5d154-111">Attribute</span></span>|<span data-ttu-id="5d154-112">描述</span><span class="sxs-lookup"><span data-stu-id="5d154-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5d154-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5d154-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5d154-114">指定通用語言執行時間是否要優化附屬元件的探查。</span><span class="sxs-lookup"><span data-stu-id="5d154-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5d154-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="5d154-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5d154-116">值</span><span class="sxs-lookup"><span data-stu-id="5d154-116">Value</span></span>|<span data-ttu-id="5d154-117">說明</span><span class="sxs-lookup"><span data-stu-id="5d154-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5d154-118">執行時間不會優化附屬元件的探查。</span><span class="sxs-lookup"><span data-stu-id="5d154-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="5d154-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="5d154-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="5d154-120">執行時間會優化附屬元件的探查。</span><span class="sxs-lookup"><span data-stu-id="5d154-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d154-121">子元素</span><span class="sxs-lookup"><span data-stu-id="5d154-121">Child Elements</span></span>  
 <span data-ttu-id="5d154-122">無。</span><span class="sxs-lookup"><span data-stu-id="5d154-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d154-123">父項目</span><span class="sxs-lookup"><span data-stu-id="5d154-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5d154-124">項目</span><span class="sxs-lookup"><span data-stu-id="5d154-124">Element</span></span>|<span data-ttu-id="5d154-125">描述</span><span class="sxs-lookup"><span data-stu-id="5d154-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5d154-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5d154-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5d154-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d154-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d154-128">備註</span><span class="sxs-lookup"><span data-stu-id="5d154-128">Remarks</span></span>  
 <span data-ttu-id="5d154-129">一般來說, Resource Manager 會探查資源, 如[封裝和部署資源](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)主題中所述。</span><span class="sxs-lookup"><span data-stu-id="5d154-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="5d154-130">這表示當 Resource Manager 探查特定當地語系化版本的資源時, 它可能會查看全域組件快取、在應用程式的程式碼基底中尋找特定文化特性的資料夾、針對附屬元件查詢 Windows Installer, 然後引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="5d154-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="5d154-131">`<relativeBindForResources>`元素會將 Resource Manager 探查附屬元件的方式優化。</span><span class="sxs-lookup"><span data-stu-id="5d154-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="5d154-132">在下列情況下探查資源時, 它可以改善效能:</span><span class="sxs-lookup"><span data-stu-id="5d154-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="5d154-133">當附屬元件部署在與程式碼元件相同的位置時。</span><span class="sxs-lookup"><span data-stu-id="5d154-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="5d154-134">換句話說, 如果程式碼元件安裝在全域組件快取中, 則也必須在該處安裝附屬元件。</span><span class="sxs-lookup"><span data-stu-id="5d154-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="5d154-135">如果程式碼元件安裝在應用程式的程式碼基底中, 則附屬元件也必須安裝在程式碼基底中的文化特性特定資料夾內。</span><span class="sxs-lookup"><span data-stu-id="5d154-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="5d154-136">未使用 Windows Installer, 或只是很少用來視需要安裝附屬元件。</span><span class="sxs-lookup"><span data-stu-id="5d154-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="5d154-137">當應用程式代碼未處理<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件時。</span><span class="sxs-lookup"><span data-stu-id="5d154-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="5d154-138">設定專案的`<relativeBindForResources>` `true`屬性, 以將 Resource Manager 的附屬元件探查優化, 如下所示: `enabled`</span><span class="sxs-lookup"><span data-stu-id="5d154-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="5d154-139">它會使用父程式碼元件的位置來探查附屬元件。</span><span class="sxs-lookup"><span data-stu-id="5d154-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="5d154-140">它不會查詢附屬元件 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="5d154-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="5d154-141">它不會引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="5d154-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d154-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d154-142">See also</span></span>

- [<span data-ttu-id="5d154-143">封裝和部署資源</span><span class="sxs-lookup"><span data-stu-id="5d154-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="5d154-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5d154-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5d154-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5d154-145">Configuration File Schema</span></span>](../index.md)
