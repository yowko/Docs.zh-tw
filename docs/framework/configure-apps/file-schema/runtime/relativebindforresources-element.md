---
title: <relativeBindForResources> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51129f9bb3a278d32a5da723dcc339f5e918c0f4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289805"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="38bb3-102">\<Relativebindforresources> > 項目</span><span class="sxs-lookup"><span data-stu-id="38bb3-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="38bb3-103">最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="38bb3-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="38bb3-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="38bb3-104">\<configuration> Element</span></span>  
<span data-ttu-id="38bb3-105">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="38bb3-105">\<runtime> Element</span></span>  
<span data-ttu-id="38bb3-106">\<Relativebindforresources> > 項目</span><span class="sxs-lookup"><span data-stu-id="38bb3-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38bb3-107">語法</span><span class="sxs-lookup"><span data-stu-id="38bb3-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38bb3-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38bb3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="38bb3-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="38bb3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38bb3-110">屬性</span><span class="sxs-lookup"><span data-stu-id="38bb3-110">Attributes</span></span>  
  
|<span data-ttu-id="38bb3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="38bb3-111">Attribute</span></span>|<span data-ttu-id="38bb3-112">描述</span><span class="sxs-lookup"><span data-stu-id="38bb3-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="38bb3-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="38bb3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="38bb3-114">指定 common language runtime 是否最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="38bb3-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="38bb3-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="38bb3-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="38bb3-116">值</span><span class="sxs-lookup"><span data-stu-id="38bb3-116">Value</span></span>|<span data-ttu-id="38bb3-117">描述</span><span class="sxs-lookup"><span data-stu-id="38bb3-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="38bb3-118">執行階段不會最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="38bb3-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="38bb3-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="38bb3-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="38bb3-120">執行階段最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="38bb3-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38bb3-121">子元素</span><span class="sxs-lookup"><span data-stu-id="38bb3-121">Child Elements</span></span>  
 <span data-ttu-id="38bb3-122">無。</span><span class="sxs-lookup"><span data-stu-id="38bb3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38bb3-123">父項目</span><span class="sxs-lookup"><span data-stu-id="38bb3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="38bb3-124">項目</span><span class="sxs-lookup"><span data-stu-id="38bb3-124">Element</span></span>|<span data-ttu-id="38bb3-125">描述</span><span class="sxs-lookup"><span data-stu-id="38bb3-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="38bb3-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="38bb3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="38bb3-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="38bb3-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38bb3-128">備註</span><span class="sxs-lookup"><span data-stu-id="38bb3-128">Remarks</span></span>  
 <span data-ttu-id="38bb3-129">一般情況下，Resource Manager 來探查資源，如中所述[封裝和部署資源](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)主題。</span><span class="sxs-lookup"><span data-stu-id="38bb3-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="38bb3-130">這表示當資源管理員會探查特定資源的當地語系化版本，它可能在全域組件快取中尋找、 附屬組件，尋找應用程式的程式碼基底，查詢 Windows 安裝程式中的特定文化特性資料夾中，會引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="38bb3-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="38bb3-131">`<relativeBindForResources>`項目最佳化資源管理員探查附屬組件的方式。</span><span class="sxs-lookup"><span data-stu-id="38bb3-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="38bb3-132">當探查資源在下列情況下，它可以改善效能：</span><span class="sxs-lookup"><span data-stu-id="38bb3-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
-   <span data-ttu-id="38bb3-133">當附屬組件會部署在與程式碼組件相同的位置。</span><span class="sxs-lookup"><span data-stu-id="38bb3-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="38bb3-134">換句話說，如果程式碼組件會安裝在全域組件快取，附屬組件也必須安裝那里。</span><span class="sxs-lookup"><span data-stu-id="38bb3-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="38bb3-135">如果程式碼組件會安裝在應用程式的程式碼基底，也必須安裝附屬組件中的程式碼基底中的特定文化特性資料夾。</span><span class="sxs-lookup"><span data-stu-id="38bb3-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
-   <span data-ttu-id="38bb3-136">當 Windows 安裝程式未使用或很少使用依需求安裝附屬組件。</span><span class="sxs-lookup"><span data-stu-id="38bb3-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
-   <span data-ttu-id="38bb3-137">應用程式程式碼未處理的當<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="38bb3-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="38bb3-138">設定`enabled`的屬性`<relativeBindForResources>`項目`true`Resource Manager 的探查最佳化附屬組件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="38bb3-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
-   <span data-ttu-id="38bb3-139">它會使用父程式碼組件的位置來探查附屬組件。</span><span class="sxs-lookup"><span data-stu-id="38bb3-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
-   <span data-ttu-id="38bb3-140">它不會查詢 Windows Installer 附屬組件。</span><span class="sxs-lookup"><span data-stu-id="38bb3-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
-   <span data-ttu-id="38bb3-141">它不會引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="38bb3-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bb3-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38bb3-142">See also</span></span>
- [<span data-ttu-id="38bb3-143">封裝和部署資源</span><span class="sxs-lookup"><span data-stu-id="38bb3-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="38bb3-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="38bb3-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="38bb3-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="38bb3-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
