---
title: "&lt;relativeBindForResources&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8409b1fe86776397ceb3db5b338fb8aaadef9cbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltrelativebindforresourcesgt-element"></a><span data-ttu-id="2113c-102">&lt;relativeBindForResources&gt;項目</span><span class="sxs-lookup"><span data-stu-id="2113c-102">&lt;relativeBindForResources&gt; Element</span></span>
<span data-ttu-id="2113c-103">最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="2113c-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="2113c-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="2113c-104">\<configuration> Element</span></span>  
<span data-ttu-id="2113c-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="2113c-105">\<runtime> Element</span></span>  
<span data-ttu-id="2113c-106">\<> 項目</span><span class="sxs-lookup"><span data-stu-id="2113c-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2113c-107">語法</span><span class="sxs-lookup"><span data-stu-id="2113c-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2113c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2113c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2113c-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2113c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2113c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2113c-110">Attributes</span></span>  
  
|<span data-ttu-id="2113c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2113c-111">Attribute</span></span>|<span data-ttu-id="2113c-112">描述</span><span class="sxs-lookup"><span data-stu-id="2113c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2113c-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2113c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2113c-114">指定 common language runtime 是否會探查最佳化附屬組件。</span><span class="sxs-lookup"><span data-stu-id="2113c-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2113c-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="2113c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2113c-116">值</span><span class="sxs-lookup"><span data-stu-id="2113c-116">Value</span></span>|<span data-ttu-id="2113c-117">描述</span><span class="sxs-lookup"><span data-stu-id="2113c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2113c-118">執行階段不會最佳化附屬組件探查。</span><span class="sxs-lookup"><span data-stu-id="2113c-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="2113c-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2113c-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="2113c-120">執行階段會探查最佳化附屬組件。</span><span class="sxs-lookup"><span data-stu-id="2113c-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2113c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="2113c-121">Child Elements</span></span>  
 <span data-ttu-id="2113c-122">無。</span><span class="sxs-lookup"><span data-stu-id="2113c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2113c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="2113c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2113c-124">項目</span><span class="sxs-lookup"><span data-stu-id="2113c-124">Element</span></span>|<span data-ttu-id="2113c-125">描述</span><span class="sxs-lookup"><span data-stu-id="2113c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2113c-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2113c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2113c-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="2113c-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2113c-128">備註</span><span class="sxs-lookup"><span data-stu-id="2113c-128">Remarks</span></span>  
 <span data-ttu-id="2113c-129">一般而言，資源管理員來探查資源，如中所述[封裝和部署資源](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)主題。</span><span class="sxs-lookup"><span data-stu-id="2113c-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="2113c-130">這表示，當資源管理員來探查特定資源的當地語系化版本，可能會在全域組件快取中尋找、 尋找應用程式的程式碼基底，查詢 Windows Installer 的特定文化特性資料夾中的附屬組件，並引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="2113c-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="2113c-131">`<relativeBindForResources>`項目最佳化資源管理員探查附屬組件的方式。</span><span class="sxs-lookup"><span data-stu-id="2113c-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="2113c-132">在下列情況下的資源的探查時，它可以改善效能：</span><span class="sxs-lookup"><span data-stu-id="2113c-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
-   <span data-ttu-id="2113c-133">當附屬組件部署在與程式碼組件相同的位置。</span><span class="sxs-lookup"><span data-stu-id="2113c-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="2113c-134">換句話說，如果程式碼組件會安裝在全域組件快取，附屬組件也必須安裝那里。</span><span class="sxs-lookup"><span data-stu-id="2113c-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="2113c-135">如果程式碼組件會安裝在應用程式的程式碼基底，附屬組件也必須安裝的程式碼基底中的特定文化特性資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2113c-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
-   <span data-ttu-id="2113c-136">當 Windows 安裝程式不會使用或很少使用隨安裝的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="2113c-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
-   <span data-ttu-id="2113c-137">當應用程式程式碼未處理<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="2113c-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="2113c-138">設定`enabled`屬性`<relativeBindForResources>`元素`true`資源管理員的探查最佳化附屬組件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2113c-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
-   <span data-ttu-id="2113c-139">它會使用父程式碼組件位置的附屬組件探查。</span><span class="sxs-lookup"><span data-stu-id="2113c-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
-   <span data-ttu-id="2113c-140">它不會查詢 Windows Installer 的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="2113c-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
-   <span data-ttu-id="2113c-141">它不會引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。</span><span class="sxs-lookup"><span data-stu-id="2113c-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2113c-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="2113c-142">See Also</span></span>  
 [<span data-ttu-id="2113c-143">封裝和部署資源</span><span class="sxs-lookup"><span data-stu-id="2113c-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [<span data-ttu-id="2113c-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2113c-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="2113c-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2113c-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
