---
title: '&lt;新增&gt;元素&lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d65dfd9a1560f2657f48b327277b64ab77014b47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="cacb2-102">&lt;新增&gt;元素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="cacb2-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="cacb2-103">新增`namedCache`進入`namedCaches`記憶體快取的集合。</span><span class="sxs-lookup"><span data-stu-id="cacb2-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="cacb2-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="cacb2-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="cacb2-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="cacb2-105">\<memoryCache></span></span>  
<span data-ttu-id="cacb2-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="cacb2-106">\<namedCaches></span></span>  
<span data-ttu-id="cacb2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="cacb2-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cacb2-108">語法</span><span class="sxs-lookup"><span data-stu-id="cacb2-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="cacb2-109">類型</span><span class="sxs-lookup"><span data-stu-id="cacb2-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cacb2-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cacb2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cacb2-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cacb2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cacb2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="cacb2-112">Attributes</span></span>  
  
|<span data-ttu-id="cacb2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cacb2-113">Attribute</span></span>|<span data-ttu-id="cacb2-114">描述</span><span class="sxs-lookup"><span data-stu-id="cacb2-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="cacb2-115">整數值，指定允許的最大大小 （mb) 的執行個體<xref:System.Runtime.Caching.MemoryCache>可以成長到。</span><span class="sxs-lookup"><span data-stu-id="cacb2-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="cacb2-116">預設值為 0，這表示<xref:System.Runtime.Caching.MemoryCache>預設會使用類別的自動調整啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="cacb2-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="cacb2-117">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="cacb2-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="cacb2-118">整數值 0 和 100 之間，指定可供快取的實際安裝的電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="cacb2-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="cacb2-119">預設值為 0，這表示<xref:System.Runtime.Caching.MemoryCache>預設會使用類別的自動調整啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="cacb2-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="cacb2-120">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="cacb2-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="cacb2-121">這個值是以"Hh: mm:"格式輸入。</span><span class="sxs-lookup"><span data-stu-id="cacb2-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cacb2-122">子項目</span><span class="sxs-lookup"><span data-stu-id="cacb2-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="cacb2-123">父項目</span><span class="sxs-lookup"><span data-stu-id="cacb2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cacb2-124">項目</span><span class="sxs-lookup"><span data-stu-id="cacb2-124">Element</span></span>|<span data-ttu-id="cacb2-125">描述</span><span class="sxs-lookup"><span data-stu-id="cacb2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cacb2-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="cacb2-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="cacb2-127">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="cacb2-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cacb2-128">備註</span><span class="sxs-lookup"><span data-stu-id="cacb2-128">Remarks</span></span>  
 <span data-ttu-id="cacb2-129">`add`項目加入至項目的`namedCaches`記憶體快取的集合。</span><span class="sxs-lookup"><span data-stu-id="cacb2-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="cacb2-130">您可以使用[清除](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)使用之前的項目`add`項目，以確定有沒有其他具名快取，在集合中的。</span><span class="sxs-lookup"><span data-stu-id="cacb2-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="cacb2-131">這個項目可以用於 machine.config 檔案中，並在 Web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="cacb2-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cacb2-132">範例</span><span class="sxs-lookup"><span data-stu-id="cacb2-132">Example</span></span>  
 <span data-ttu-id="cacb2-133">下列範例示範如何定義預設的設定`namedCache`進入`namedCaches`記憶體快取的集合。</span><span class="sxs-lookup"><span data-stu-id="cacb2-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cacb2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cacb2-134">See Also</span></span>  
 [<span data-ttu-id="cacb2-135">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="cacb2-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
