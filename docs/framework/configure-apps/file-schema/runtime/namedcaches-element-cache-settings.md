---
title: "&lt;namedCaches&gt;項目 （快取設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7c25f0039f75ba1c736cff946dbaaff9252dc93e
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="abba7-102">&lt;namedCaches&gt;項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="abba7-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="abba7-103">指定的具名組態設定集合<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="abba7-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="abba7-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>屬性參考的組態設定集合從一或多個`namedCaches`的組態檔項目。</span><span class="sxs-lookup"><span data-stu-id="abba7-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="abba7-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="abba7-105">\<configuration></span></span>  
<span data-ttu-id="abba7-106">\<system.runtime.caching ></span><span class="sxs-lookup"><span data-stu-id="abba7-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="abba7-107">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="abba7-107">\<memoryCache></span></span>  
<span data-ttu-id="abba7-108">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="abba7-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abba7-109">語法</span><span class="sxs-lookup"><span data-stu-id="abba7-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="abba7-110">類型</span><span class="sxs-lookup"><span data-stu-id="abba7-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abba7-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="abba7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="abba7-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="abba7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abba7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="abba7-113">Attributes</span></span>  
  
|<span data-ttu-id="abba7-114">屬性</span><span class="sxs-lookup"><span data-stu-id="abba7-114">Attribute</span></span>|<span data-ttu-id="abba7-115">描述</span><span class="sxs-lookup"><span data-stu-id="abba7-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="abba7-116">整數值，以 mb 為單位，指定最大容許大小的執行個體<xref:System.Runtime.Caching.MemoryCache>可以成長到。</span><span class="sxs-lookup"><span data-stu-id="abba7-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="abba7-117">預設值為 0，這表示的自動調整啟發學習法<xref:System.Runtime.Caching.MemoryCache>預設會使用類別。</span><span class="sxs-lookup"><span data-stu-id="abba7-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="abba7-118">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="abba7-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="abba7-119">整數值 0 和 100 之間，指定可供快取的實際安裝的電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="abba7-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="abba7-120">預設值為 0，這表示的自動調整啟發學習法<xref:System.Runtime.Caching.MemoryCache>預設會使用類別。</span><span class="sxs-lookup"><span data-stu-id="abba7-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="abba7-121">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="abba7-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="abba7-122">這個值是以"Hh: mm:"格式輸入。</span><span class="sxs-lookup"><span data-stu-id="abba7-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abba7-123">子元素</span><span class="sxs-lookup"><span data-stu-id="abba7-123">Child Elements</span></span>  
  
|<span data-ttu-id="abba7-124">項目</span><span class="sxs-lookup"><span data-stu-id="abba7-124">Element</span></span>|<span data-ttu-id="abba7-125">描述</span><span class="sxs-lookup"><span data-stu-id="abba7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abba7-126">\<add></span><span class="sxs-lookup"><span data-stu-id="abba7-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="abba7-127">將具名快取新增到記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="abba7-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="abba7-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="abba7-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="abba7-129">清除記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="abba7-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="abba7-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="abba7-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="abba7-131">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="abba7-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abba7-132">父項目</span><span class="sxs-lookup"><span data-stu-id="abba7-132">Parent Elements</span></span>  
  
|<span data-ttu-id="abba7-133">項目</span><span class="sxs-lookup"><span data-stu-id="abba7-133">Element</span></span>|<span data-ttu-id="abba7-134">描述</span><span class="sxs-lookup"><span data-stu-id="abba7-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abba7-135">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="abba7-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="abba7-136">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="abba7-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abba7-137">備註</span><span class="sxs-lookup"><span data-stu-id="abba7-137">Remarks</span></span>  
 <span data-ttu-id="abba7-138">記憶體快取組態區段位於 Web.config 檔案可以包含`add`， `remove`，和`clear`屬性`namedCaches`集合。</span><span class="sxs-lookup"><span data-stu-id="abba7-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="abba7-139">每個`namedCaches`項目以唯一識別`name`屬性。</span><span class="sxs-lookup"><span data-stu-id="abba7-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="abba7-140">您可以藉由參考應用程式組態檔中的資訊擷取執行個體的記憶體快取項目。</span><span class="sxs-lookup"><span data-stu-id="abba7-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="abba7-141">根據預設，只有預設快取執行個體，請在組態檔中有項目。</span><span class="sxs-lookup"><span data-stu-id="abba7-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="abba7-142">預設快取執行個體是從傳回的執行個體<xref:System.Runtime.Caching.MemoryCache.Default%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="abba7-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="abba7-143">如果您設定 name 屬性為"default"，項目會使用預設的記憶體快取執行個體。</span><span class="sxs-lookup"><span data-stu-id="abba7-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abba7-144">範例</span><span class="sxs-lookup"><span data-stu-id="abba7-144">Example</span></span>  
 <span data-ttu-id="abba7-145">下列範例示範如何設定預設快取項目名稱的快取的名稱，藉由設定`name`「 預設 」 的屬性。</span><span class="sxs-lookup"><span data-stu-id="abba7-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="abba7-146">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="abba7-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="abba7-147">將這些屬性設定為零表示自動調整啟發學習法的<xref:System.Runtime.Caching.MemoryCache>可用類別。</span><span class="sxs-lookup"><span data-stu-id="abba7-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="abba7-148">快取實作比較目前的記憶體負載，對絕對和以百分比為基礎的記憶體限制每兩分鐘。</span><span class="sxs-lookup"><span data-stu-id="abba7-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="abba7-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="abba7-149">See Also</span></span>  
 [<span data-ttu-id="abba7-150">\<memoryCache > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="abba7-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
