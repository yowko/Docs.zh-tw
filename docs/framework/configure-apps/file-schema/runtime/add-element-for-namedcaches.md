---
title: <namedCaches> 的 <add> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252881"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="34d3b-102">\<新增 namedCaches > 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="34d3b-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="34d3b-103">將專案加入至記憶體`namedCaches`快取的集合。 `namedCache`</span><span class="sxs-lookup"><span data-stu-id="34d3b-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="34d3b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="34d3b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="34d3b-105">&nbsp;&nbsp;[ **\<> 的緩存**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="34d3b-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="34d3b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="34d3b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="34d3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="34d3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="34d3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="34d3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34d3b-109">語法</span><span class="sxs-lookup"><span data-stu-id="34d3b-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="34d3b-110">類型</span><span class="sxs-lookup"><span data-stu-id="34d3b-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34d3b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="34d3b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="34d3b-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="34d3b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34d3b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="34d3b-113">Attributes</span></span>  
  
|<span data-ttu-id="34d3b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="34d3b-114">Attribute</span></span>|<span data-ttu-id="34d3b-115">描述</span><span class="sxs-lookup"><span data-stu-id="34d3b-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="34d3b-116">整數值, 指定實例<xref:System.Runtime.Caching.MemoryCache>可以成長到的最大允許大小 (以 mb 為單位)。</span><span class="sxs-lookup"><span data-stu-id="34d3b-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="34d3b-117">預設值為 0, 表示<xref:System.Runtime.Caching.MemoryCache>預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="34d3b-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="34d3b-118">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="34d3b-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="34d3b-119">介於0和100之間的整數值, 指定可供快取使用之實際安裝電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="34d3b-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="34d3b-120">預設值為 0, 表示<xref:System.Runtime.Caching.MemoryCache>預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="34d3b-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="34d3b-121">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="34d3b-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="34d3b-122">此值會以 "HH: MM: SS" 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="34d3b-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34d3b-123">子元素</span><span class="sxs-lookup"><span data-stu-id="34d3b-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="34d3b-124">父項目</span><span class="sxs-lookup"><span data-stu-id="34d3b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="34d3b-125">項目</span><span class="sxs-lookup"><span data-stu-id="34d3b-125">Element</span></span>|<span data-ttu-id="34d3b-126">說明</span><span class="sxs-lookup"><span data-stu-id="34d3b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34d3b-127">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="34d3b-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="34d3b-128">包含已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。</span><span class="sxs-lookup"><span data-stu-id="34d3b-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34d3b-129">備註</span><span class="sxs-lookup"><span data-stu-id="34d3b-129">Remarks</span></span>  
 <span data-ttu-id="34d3b-130">元素會將專案加入至記憶體`namedCaches`快取的集合。 `add`</span><span class="sxs-lookup"><span data-stu-id="34d3b-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="34d3b-131">在您使用`add`專案之前, 您可以使用[clear](clear-element-for-namedcaches.md)元素, 以確定集合中沒有任何其他已命名的快取。</span><span class="sxs-lookup"><span data-stu-id="34d3b-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="34d3b-132">這個元素可以在 machine.config 檔案和 web.config 檔案中使用。</span><span class="sxs-lookup"><span data-stu-id="34d3b-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d3b-133">範例</span><span class="sxs-lookup"><span data-stu-id="34d3b-133">Example</span></span>  
 <span data-ttu-id="34d3b-134">下列範例示範如何將預設`namedCache`專案的設定定義為記憶體快取的`namedCaches`集合。</span><span class="sxs-lookup"><span data-stu-id="34d3b-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34d3b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34d3b-135">See also</span></span>

- [<span data-ttu-id="34d3b-136">\<namedCaches > 元素 (快取設定)</span><span class="sxs-lookup"><span data-stu-id="34d3b-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
