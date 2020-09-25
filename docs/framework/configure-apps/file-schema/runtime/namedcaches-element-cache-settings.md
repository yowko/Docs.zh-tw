---
title: <namedCaches> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: ad76c01bba859934be399d73262bd974309efe98
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192395"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="ebbea-102">\<namedCaches> 項目 (快取設定)</span><span class="sxs-lookup"><span data-stu-id="ebbea-102">\<namedCaches> Element (Cache Settings)</span></span>

<span data-ttu-id="ebbea-103">指定已命名實例的設定集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="ebbea-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="ebbea-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>屬性會參考設定檔的一或多個專案中的設定設定集合 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="ebbea-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="ebbea-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ebbea-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ebbea-106">類型</span><span class="sxs-lookup"><span data-stu-id="ebbea-106">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebbea-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ebbea-107">Attributes and Elements</span></span>  

 <span data-ttu-id="ebbea-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ebbea-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebbea-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ebbea-109">Attributes</span></span>  
  
|<span data-ttu-id="ebbea-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ebbea-110">Attribute</span></span>|<span data-ttu-id="ebbea-111">描述</span><span class="sxs-lookup"><span data-stu-id="ebbea-111">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="ebbea-112">整數值，指定的實例可成長的大小上限（以 mb 為單位） <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="ebbea-112">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="ebbea-113">預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="ebbea-113">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="ebbea-114">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="ebbea-114">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="ebbea-115">介於0與100之間的整數值，指定快取可以取用的實際安裝電腦記憶體百分比上限。</span><span class="sxs-lookup"><span data-stu-id="ebbea-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="ebbea-116">預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="ebbea-116">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="ebbea-117">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="ebbea-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="ebbea-118">此值是以 "HH： MM： SS" 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="ebbea-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebbea-119">子元素</span><span class="sxs-lookup"><span data-stu-id="ebbea-119">Child Elements</span></span>  
  
|<span data-ttu-id="ebbea-120">項目</span><span class="sxs-lookup"><span data-stu-id="ebbea-120">Element</span></span>|<span data-ttu-id="ebbea-121">描述</span><span class="sxs-lookup"><span data-stu-id="ebbea-121">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="ebbea-122">將具名快取新增到記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="ebbea-122">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="ebbea-123">清除記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="ebbea-123">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="ebbea-124">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="ebbea-124">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ebbea-125">父項目</span><span class="sxs-lookup"><span data-stu-id="ebbea-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ebbea-126">項目</span><span class="sxs-lookup"><span data-stu-id="ebbea-126">Element</span></span>|<span data-ttu-id="ebbea-127">描述</span><span class="sxs-lookup"><span data-stu-id="ebbea-127">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="ebbea-128">指定 common language runtime 和 .NET Framework 應用程式所使用之每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ebbea-128">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="ebbea-129">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="ebbea-129">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="ebbea-130">包含類型，可讓您在 .NET Framework 內建的應用程式中，執行輸出快取。</span><span class="sxs-lookup"><span data-stu-id="ebbea-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebbea-131">備註</span><span class="sxs-lookup"><span data-stu-id="ebbea-131">Remarks</span></span>  

 <span data-ttu-id="ebbea-132">Web.config 檔案的 memory cache configuration 區段可以包含集合的 `add` 、 `remove` 和 `clear` 屬性 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="ebbea-132">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="ebbea-133">每個 `namedCaches` 專案都是由屬性唯一識別 `name` 。</span><span class="sxs-lookup"><span data-stu-id="ebbea-133">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="ebbea-134">您可以參考應用程式佈建檔中的資訊，以取出記憶體快取專案的實例。</span><span class="sxs-lookup"><span data-stu-id="ebbea-134">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="ebbea-135">依預設，只有預設快取實例在設定檔中有一個專案。</span><span class="sxs-lookup"><span data-stu-id="ebbea-135">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="ebbea-136">預設快取實例是從屬性傳回的實例 <xref:System.Runtime.Caching.MemoryCache.Default%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ebbea-136">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="ebbea-137">如果您將 [名稱] 屬性設定為 "default"，元素就會使用預設的記憶體快取實例。</span><span class="sxs-lookup"><span data-stu-id="ebbea-137">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebbea-138">範例</span><span class="sxs-lookup"><span data-stu-id="ebbea-138">Example</span></span>  

 <span data-ttu-id="ebbea-139">下列範例顯示如何藉由將 `name` 屬性設定為 "default"，將快取的名稱設定為預設快取專案名稱。</span><span class="sxs-lookup"><span data-stu-id="ebbea-139">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="ebbea-140">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="ebbea-140">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="ebbea-141">將這些屬性設定為零，表示會使用類別的自動調整大小啟發學習法 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="ebbea-141">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="ebbea-142">快取執行會將目前的記憶體負載與每兩分鐘的絕對和百分比型記憶體限制進行比較。</span><span class="sxs-lookup"><span data-stu-id="ebbea-142">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebbea-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebbea-143">See also</span></span>

- [<span data-ttu-id="ebbea-144">\<memoryCache> (快取設定的元素) </span><span class="sxs-lookup"><span data-stu-id="ebbea-144">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
