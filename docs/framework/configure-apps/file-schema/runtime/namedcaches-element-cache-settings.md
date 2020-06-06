---
title: <namedCaches> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153954"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="5f487-102">\<namedCaches> 項目 (快取設定)</span><span class="sxs-lookup"><span data-stu-id="5f487-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="5f487-103">指定已命名實例的設定集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="5f487-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="5f487-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>屬性會從設定檔的一個或多個元素，參考設定的集合 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="5f487-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="5f487-105">語法</span><span class="sxs-lookup"><span data-stu-id="5f487-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="5f487-106">類型</span><span class="sxs-lookup"><span data-stu-id="5f487-106">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f487-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f487-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5f487-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5f487-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f487-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5f487-109">Attributes</span></span>  
  
|<span data-ttu-id="5f487-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5f487-110">Attribute</span></span>|<span data-ttu-id="5f487-111">描述</span><span class="sxs-lookup"><span data-stu-id="5f487-111">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="5f487-112">整數值，指定實例可以成長到的最大允許大小（以 mb 為單位） <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="5f487-112">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="5f487-113">預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="5f487-113">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="5f487-114">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f487-114">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="5f487-115">介於0和100之間的整數值，指定可供快取使用之實際安裝電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="5f487-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="5f487-116">預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="5f487-116">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="5f487-117">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="5f487-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="5f487-118">此值會以 "HH： MM： SS" 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="5f487-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f487-119">子元素</span><span class="sxs-lookup"><span data-stu-id="5f487-119">Child Elements</span></span>  
  
|<span data-ttu-id="5f487-120">元素</span><span class="sxs-lookup"><span data-stu-id="5f487-120">Element</span></span>|<span data-ttu-id="5f487-121">描述</span><span class="sxs-lookup"><span data-stu-id="5f487-121">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="5f487-122">將具名快取新增到記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="5f487-122">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="5f487-123">清除記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="5f487-123">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="5f487-124">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="5f487-124">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f487-125">父項目</span><span class="sxs-lookup"><span data-stu-id="5f487-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5f487-126">元素</span><span class="sxs-lookup"><span data-stu-id="5f487-126">Element</span></span>|<span data-ttu-id="5f487-127">描述</span><span class="sxs-lookup"><span data-stu-id="5f487-127">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="5f487-128">指定通用語言執行時間和 .NET Framework 應用程式所使用之每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5f487-128">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="5f487-129">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="5f487-129">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="5f487-130">包含類型，可讓您在內建于 .NET Framework 的應用程式中，執行輸出快取。</span><span class="sxs-lookup"><span data-stu-id="5f487-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f487-131">備註</span><span class="sxs-lookup"><span data-stu-id="5f487-131">Remarks</span></span>  
 <span data-ttu-id="5f487-132">Web.config 檔案的記憶體快取設定區段可以包含 `add` 集合的、 `remove` 和 `clear` 屬性 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="5f487-132">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="5f487-133">每個 `namedCaches` 專案都是由屬性唯一識別 `name` 。</span><span class="sxs-lookup"><span data-stu-id="5f487-133">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="5f487-134">您可以藉由參考應用程式佈建檔中的資訊，來取出記憶體快取專案的實例。</span><span class="sxs-lookup"><span data-stu-id="5f487-134">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="5f487-135">根據預設，只有預設快取實例在設定檔中有一個專案。</span><span class="sxs-lookup"><span data-stu-id="5f487-135">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="5f487-136">預設的快取實例是從屬性傳回的實例 <xref:System.Runtime.Caching.MemoryCache.Default%2A> 。</span><span class="sxs-lookup"><span data-stu-id="5f487-136">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="5f487-137">如果您將 name 屬性設定為 "default"，元素會使用預設的記憶體快取實例。</span><span class="sxs-lookup"><span data-stu-id="5f487-137">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f487-138">範例</span><span class="sxs-lookup"><span data-stu-id="5f487-138">Example</span></span>  
 <span data-ttu-id="5f487-139">下列範例示範如何透過將 `name` 屬性設定為 "default"，將快取的名稱設定為預設快取專案名稱。</span><span class="sxs-lookup"><span data-stu-id="5f487-139">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="5f487-140">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="5f487-140">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="5f487-141">將這些屬性設定為零表示會使用類別的自動調整大小啟發學習法 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="5f487-141">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="5f487-142">快取執行會比較目前的記憶體負載與以百分比為基礎的記憶體限制，每兩分鐘一次。</span><span class="sxs-lookup"><span data-stu-id="5f487-142">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f487-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f487-143">See also</span></span>

- [<span data-ttu-id="5f487-144">\<memoryCache>元素（快取設定）</span><span class="sxs-lookup"><span data-stu-id="5f487-144">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
