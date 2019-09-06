---
title: <namedCaches> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 4587234ad91fa3b1abbb376bd7ae517d5abea6c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252454"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="8eaa4-102">\<namedCaches > 元素（快取設定）</span><span class="sxs-lookup"><span data-stu-id="8eaa4-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="8eaa4-103">指定已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="8eaa4-104">屬性會從設定檔的一個或多個`namedCaches`元素，參考設定的集合。 <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A></span><span class="sxs-lookup"><span data-stu-id="8eaa4-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="8eaa4-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8eaa4-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8eaa4-106">&nbsp;&nbsp;[ **\<> 的緩存**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8eaa4-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="8eaa4-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8eaa4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="8eaa4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namedCaches >**</span><span class="sxs-lookup"><span data-stu-id="8eaa4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eaa4-109">語法</span><span class="sxs-lookup"><span data-stu-id="8eaa4-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="8eaa4-110">類型</span><span class="sxs-lookup"><span data-stu-id="8eaa4-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8eaa4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8eaa4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8eaa4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8eaa4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8eaa4-113">Attributes</span></span>  
  
|<span data-ttu-id="8eaa4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="8eaa4-114">Attribute</span></span>|<span data-ttu-id="8eaa4-115">描述</span><span class="sxs-lookup"><span data-stu-id="8eaa4-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="8eaa4-116">整數值，指定實例<xref:System.Runtime.Caching.MemoryCache>可以成長到的最大允許大小（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="8eaa4-117">預設值為0，表示預設會使用<xref:System.Runtime.Caching.MemoryCache>類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="8eaa4-118">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="8eaa4-119">介於0和100之間的整數值，指定可供快取使用之實際安裝電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="8eaa4-120">預設值為0，表示預設會使用<xref:System.Runtime.Caching.MemoryCache>類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="8eaa4-121">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="8eaa4-122">此值會以 "HH： MM： SS" 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8eaa4-123">子元素</span><span class="sxs-lookup"><span data-stu-id="8eaa4-123">Child Elements</span></span>  
  
|<span data-ttu-id="8eaa4-124">項目</span><span class="sxs-lookup"><span data-stu-id="8eaa4-124">Element</span></span>|<span data-ttu-id="8eaa4-125">說明</span><span class="sxs-lookup"><span data-stu-id="8eaa4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eaa4-126">\<add></span><span class="sxs-lookup"><span data-stu-id="8eaa4-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="8eaa4-127">將具名快取新增到記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="8eaa4-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="8eaa4-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="8eaa4-129">清除記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="8eaa4-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="8eaa4-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="8eaa4-131">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8eaa4-132">父項目</span><span class="sxs-lookup"><span data-stu-id="8eaa4-132">Parent Elements</span></span>  
  
|<span data-ttu-id="8eaa4-133">項目</span><span class="sxs-lookup"><span data-stu-id="8eaa4-133">Element</span></span>|<span data-ttu-id="8eaa4-134">描述</span><span class="sxs-lookup"><span data-stu-id="8eaa4-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eaa4-135">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8eaa4-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="8eaa4-136">指定通用語言執行時間和 .NET Framework 應用程式所使用之每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="8eaa4-137">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="8eaa4-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="8eaa4-138">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="8eaa4-139">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="8eaa4-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="8eaa4-140">包含類型，可讓您在內建于 .NET Framework 的應用程式中，執行輸出快取。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eaa4-141">備註</span><span class="sxs-lookup"><span data-stu-id="8eaa4-141">Remarks</span></span>  
 <span data-ttu-id="8eaa4-142">Web.config 檔案的記憶體快取設定區段`add`可以包含`namedCaches`集合的、 `remove`和`clear`屬性。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="8eaa4-143">每`namedCaches`個專案都是`name`由屬性唯一識別。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="8eaa4-144">您可以藉由參考應用程式佈建檔中的資訊，來取出記憶體快取專案的實例。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="8eaa4-145">根據預設，只有預設快取實例在設定檔中有一個專案。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="8eaa4-146">預設的快取實例是從<xref:System.Runtime.Caching.MemoryCache.Default%2A>屬性傳回的實例。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="8eaa4-147">如果您將 name 屬性設定為 "default"，元素會使用預設的記憶體快取實例。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eaa4-148">範例</span><span class="sxs-lookup"><span data-stu-id="8eaa4-148">Example</span></span>  
 <span data-ttu-id="8eaa4-149">下列範例示範如何透過將`name`屬性設定為 "default"，將快取的名稱設定為預設快取專案名稱。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="8eaa4-150">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="8eaa4-151">將這些屬性設定為零表示會使用<xref:System.Runtime.Caching.MemoryCache>類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="8eaa4-152">快取執行會比較目前的記憶體負載與以百分比為基礎的記憶體限制，每兩分鐘一次。</span><span class="sxs-lookup"><span data-stu-id="8eaa4-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8eaa4-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eaa4-153">See also</span></span>

- [<span data-ttu-id="8eaa4-154">\<memoryCache > 元素（快取設定）</span><span class="sxs-lookup"><span data-stu-id="8eaa4-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
