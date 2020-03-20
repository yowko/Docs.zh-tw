---
title: <namedCaches> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153954"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="fb90d-102">\<具名快取>元素（緩存設置）</span><span class="sxs-lookup"><span data-stu-id="fb90d-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="fb90d-103">指定命名<xref:System.Runtime.Caching.MemoryCache>實例的配置設置集合。</span><span class="sxs-lookup"><span data-stu-id="fb90d-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="fb90d-104">該<xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>屬性引用設定檔的一個或多個`namedCaches`元素的配置設置集合。</span><span class="sxs-lookup"><span data-stu-id="fb90d-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="fb90d-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb90d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fb90d-106">&nbsp;&nbsp;[**\<系統.運行時.緩存>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fb90d-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="fb90d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<記憶體緩存>**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fb90d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="fb90d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<具名快取>**</span><span class="sxs-lookup"><span data-stu-id="fb90d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb90d-109">語法</span><span class="sxs-lookup"><span data-stu-id="fb90d-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="fb90d-110">類型</span><span class="sxs-lookup"><span data-stu-id="fb90d-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb90d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fb90d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fb90d-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fb90d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb90d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fb90d-113">Attributes</span></span>  
  
|<span data-ttu-id="fb90d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fb90d-114">Attribute</span></span>|<span data-ttu-id="fb90d-115">描述</span><span class="sxs-lookup"><span data-stu-id="fb90d-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="fb90d-116">指定 a<xref:System.Runtime.Caching.MemoryCache>實例可以增長到的最大允許大小（以百萬位元組為單位）的整數值。</span><span class="sxs-lookup"><span data-stu-id="fb90d-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="fb90d-117">預設值為 0，這意味著預設情況下使用<xref:System.Runtime.Caching.MemoryCache>類的自動啟發式調整大小。</span><span class="sxs-lookup"><span data-stu-id="fb90d-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="fb90d-118">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb90d-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="fb90d-119">介於 0 和 100 之間的整數值，指定緩存可以使用的物理安裝電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="fb90d-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="fb90d-120">預設值為 0，這意味著預設情況下使用<xref:System.Runtime.Caching.MemoryCache>類的自動啟發式調整大小。</span><span class="sxs-lookup"><span data-stu-id="fb90d-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="fb90d-121">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="fb90d-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="fb90d-122">此值以"HH：MM：SS"格式輸入。</span><span class="sxs-lookup"><span data-stu-id="fb90d-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb90d-123">子元素</span><span class="sxs-lookup"><span data-stu-id="fb90d-123">Child Elements</span></span>  
  
|<span data-ttu-id="fb90d-124">元素</span><span class="sxs-lookup"><span data-stu-id="fb90d-124">Element</span></span>|<span data-ttu-id="fb90d-125">描述</span><span class="sxs-lookup"><span data-stu-id="fb90d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb90d-126">\<添加></span><span class="sxs-lookup"><span data-stu-id="fb90d-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="fb90d-127">將具名快取新增到記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="fb90d-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="fb90d-128">\<明確></span><span class="sxs-lookup"><span data-stu-id="fb90d-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="fb90d-129">清除記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="fb90d-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="fb90d-130">\<刪除></span><span class="sxs-lookup"><span data-stu-id="fb90d-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="fb90d-131">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="fb90d-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb90d-132">父項目</span><span class="sxs-lookup"><span data-stu-id="fb90d-132">Parent Elements</span></span>  
  
|<span data-ttu-id="fb90d-133">元素</span><span class="sxs-lookup"><span data-stu-id="fb90d-133">Element</span></span>|<span data-ttu-id="fb90d-134">描述</span><span class="sxs-lookup"><span data-stu-id="fb90d-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb90d-135">\<配置></span><span class="sxs-lookup"><span data-stu-id="fb90d-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="fb90d-136">指定通用語言運行時和 .NET Framework 應用程式使用的每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fb90d-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="fb90d-137">\<記憶體緩存></span><span class="sxs-lookup"><span data-stu-id="fb90d-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="fb90d-138">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="fb90d-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="fb90d-139">\<系統.運行時.緩存></span><span class="sxs-lookup"><span data-stu-id="fb90d-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="fb90d-140">包含允許您在內置於 .NET 框架中的應用程式中實現輸出緩存的類型。</span><span class="sxs-lookup"><span data-stu-id="fb90d-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb90d-141">備註</span><span class="sxs-lookup"><span data-stu-id="fb90d-141">Remarks</span></span>  
 <span data-ttu-id="fb90d-142">Web.config`add`檔的記憶體緩存配置部分可以包含 集合`remove`的`namedCaches``clear`和 屬性。</span><span class="sxs-lookup"><span data-stu-id="fb90d-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="fb90d-143">每個`namedCaches`條目都由`name`屬性唯一標識。</span><span class="sxs-lookup"><span data-stu-id="fb90d-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="fb90d-144">您可以通過引用應用程式佈建檔中的資訊來檢索記憶體緩存條目的實例。</span><span class="sxs-lookup"><span data-stu-id="fb90d-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="fb90d-145">預設情況下，只有預設緩存實例在設定檔中具有條目。</span><span class="sxs-lookup"><span data-stu-id="fb90d-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="fb90d-146">預設緩存實例是從屬性返回的<xref:System.Runtime.Caching.MemoryCache.Default%2A>實例。</span><span class="sxs-lookup"><span data-stu-id="fb90d-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="fb90d-147">如果將名稱屬性設置為"預設"，則元素將使用預設記憶體緩存實例。</span><span class="sxs-lookup"><span data-stu-id="fb90d-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb90d-148">範例</span><span class="sxs-lookup"><span data-stu-id="fb90d-148">Example</span></span>  
 <span data-ttu-id="fb90d-149">下面的示例演示如何通過將`name`屬性設置為"預設"來將緩存的名稱設置為預設緩存條目名稱。</span><span class="sxs-lookup"><span data-stu-id="fb90d-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="fb90d-150">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="fb90d-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="fb90d-151">將這些屬性設置為零意味著使用<xref:System.Runtime.Caching.MemoryCache>類的自動啟發式調整大小。</span><span class="sxs-lookup"><span data-stu-id="fb90d-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="fb90d-152">緩存實現將當前記憶體負載與絕對記憶體限制和基於百分比的記憶體限制每兩分鐘進行比較。</span><span class="sxs-lookup"><span data-stu-id="fb90d-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb90d-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb90d-153">See also</span></span>

- [<span data-ttu-id="fb90d-154">\<記憶體緩存>元素（緩存設置）</span><span class="sxs-lookup"><span data-stu-id="fb90d-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
