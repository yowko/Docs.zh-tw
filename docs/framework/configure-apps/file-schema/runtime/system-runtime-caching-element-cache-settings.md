---
title: '&lt;system.runtime.caching&gt;項目 （快取設定）'
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 659a168f6c0bcb459bcfbdb247a9959c61c9c996
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a><span data-ttu-id="37c05-102">&lt;system.runtime.caching&gt;項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="37c05-102">&lt;system.runtime.caching&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="37c05-103">透過組態檔中的 <xref:System.Runtime.Caching.ObjectCache> 項目，提供預設記憶體內 `memoryCache` 實作的組態。</span><span class="sxs-lookup"><span data-stu-id="37c05-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="37c05-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="37c05-104">\<configuration></span></span>  
<span data-ttu-id="37c05-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="37c05-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c05-106">語法</span><span class="sxs-lookup"><span data-stu-id="37c05-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37c05-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="37c05-107">Attributes and Elements</span></span>  
 <span data-ttu-id="37c05-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="37c05-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37c05-109">屬性</span><span class="sxs-lookup"><span data-stu-id="37c05-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="37c05-110">子項目</span><span class="sxs-lookup"><span data-stu-id="37c05-110">Child Elements</span></span>  
  
|<span data-ttu-id="37c05-111">項目</span><span class="sxs-lookup"><span data-stu-id="37c05-111">Element</span></span>|<span data-ttu-id="37c05-112">描述</span><span class="sxs-lookup"><span data-stu-id="37c05-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37c05-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="37c05-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="37c05-114">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="37c05-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37c05-115">父項目</span><span class="sxs-lookup"><span data-stu-id="37c05-115">Parent Elements</span></span>  
  
|<span data-ttu-id="37c05-116">項目</span><span class="sxs-lookup"><span data-stu-id="37c05-116">Element</span></span>|<span data-ttu-id="37c05-117">描述</span><span class="sxs-lookup"><span data-stu-id="37c05-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37c05-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="37c05-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="37c05-119">指定通用語言執行平台和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="37c05-119">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37c05-120">備註</span><span class="sxs-lookup"><span data-stu-id="37c05-120">Remarks</span></span>  
 <span data-ttu-id="37c05-121">這個命名空間中的類別提供如同在 ASP.NET 中使用快取設備的方式，但是不需要在 `System.Web` 組件上的相依性。</span><span class="sxs-lookup"><span data-stu-id="37c05-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="37c05-122">如需詳細資訊，請參閱 [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="37c05-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37c05-123">輸出快取功能，以及 <xref:System.Runtime.Caching> 命名空間中的類型是 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]中的新功能。</span><span class="sxs-lookup"><span data-stu-id="37c05-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="37c05-124">範例</span><span class="sxs-lookup"><span data-stu-id="37c05-124">Example</span></span>  
 <span data-ttu-id="37c05-125">下列範例示範如何設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取，</span><span class="sxs-lookup"><span data-stu-id="37c05-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="37c05-126">並示範如何設定記憶體快取之 `namedCaches` 項目的執行個體。</span><span class="sxs-lookup"><span data-stu-id="37c05-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="37c05-127">您可將 `name` 屬性設為 "default"，以將快取的名稱設定為預設快取項目。</span><span class="sxs-lookup"><span data-stu-id="37c05-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="37c05-128">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="37c05-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="37c05-129">將這些屬性設定為零表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 自動調整啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="37c05-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="37c05-130">快取實作應該會每隔兩分鐘即比較目前的記憶體負載與絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="37c05-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37c05-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37c05-131">See Also</span></span>  
 [<span data-ttu-id="37c05-132">\<memoryCache > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="37c05-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
