---
title: <namedCaches> 的 <add> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154501"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="6026b-102">\<為\<具名快取添加>元素></span><span class="sxs-lookup"><span data-stu-id="6026b-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="6026b-103">向`namedCache`記憶體緩存`namedCaches`的集合添加條目。</span><span class="sxs-lookup"><span data-stu-id="6026b-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="6026b-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6026b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6026b-105">&nbsp;&nbsp;[**\<系統.運行時.緩存>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6026b-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="6026b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<記憶體緩存>**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6026b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="6026b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<具名快取>**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6026b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="6026b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**</span><span class="sxs-lookup"><span data-stu-id="6026b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6026b-109">語法</span><span class="sxs-lookup"><span data-stu-id="6026b-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="6026b-110">類型</span><span class="sxs-lookup"><span data-stu-id="6026b-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6026b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6026b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6026b-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6026b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6026b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6026b-113">Attributes</span></span>  
  
|<span data-ttu-id="6026b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6026b-114">Attribute</span></span>|<span data-ttu-id="6026b-115">描述</span><span class="sxs-lookup"><span data-stu-id="6026b-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="6026b-116">指定 a<xref:System.Runtime.Caching.MemoryCache>實例可以增長到的最大允許大小（以百萬位元組為單位）的整數值。</span><span class="sxs-lookup"><span data-stu-id="6026b-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="6026b-117">預設值為 0，這意味著預設情況下使用<xref:System.Runtime.Caching.MemoryCache>類的自動調整啟發式。</span><span class="sxs-lookup"><span data-stu-id="6026b-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="6026b-118">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="6026b-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="6026b-119">介於 0 和 100 之間的整數值，指定緩存可以使用的物理安裝電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="6026b-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="6026b-120">預設值為 0，這意味著預設情況下使用<xref:System.Runtime.Caching.MemoryCache>類的自動調整啟發式。</span><span class="sxs-lookup"><span data-stu-id="6026b-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="6026b-121">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="6026b-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="6026b-122">此值以"HH：MM：SS"格式輸入。</span><span class="sxs-lookup"><span data-stu-id="6026b-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6026b-123">子元素</span><span class="sxs-lookup"><span data-stu-id="6026b-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="6026b-124">父項目</span><span class="sxs-lookup"><span data-stu-id="6026b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6026b-125">元素</span><span class="sxs-lookup"><span data-stu-id="6026b-125">Element</span></span>|<span data-ttu-id="6026b-126">描述</span><span class="sxs-lookup"><span data-stu-id="6026b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6026b-127">\<具名快取></span><span class="sxs-lookup"><span data-stu-id="6026b-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="6026b-128">包含命名<xref:System.Runtime.Caching.MemoryCache>實例的配置設置集合。</span><span class="sxs-lookup"><span data-stu-id="6026b-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6026b-129">備註</span><span class="sxs-lookup"><span data-stu-id="6026b-129">Remarks</span></span>  
 <span data-ttu-id="6026b-130">該`add`元素向記憶體緩存`namedCaches`的集合添加一個條目。</span><span class="sxs-lookup"><span data-stu-id="6026b-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="6026b-131">在使用 元素[clear](clear-element-for-namedcaches.md)之前，`add`可以使用 clear 元素來確保集合中沒有其他具名快取。</span><span class="sxs-lookup"><span data-stu-id="6026b-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="6026b-132">此元素可用於電腦.config 檔和 Web.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="6026b-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6026b-133">範例</span><span class="sxs-lookup"><span data-stu-id="6026b-133">Example</span></span>  
 <span data-ttu-id="6026b-134">下面的示例演示如何為記憶體緩存集合的`namedCache``namedCaches`預設條目定義設置。</span><span class="sxs-lookup"><span data-stu-id="6026b-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6026b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6026b-135">See also</span></span>

- [<span data-ttu-id="6026b-136">\<具名快取>元素（緩存設置）</span><span class="sxs-lookup"><span data-stu-id="6026b-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
