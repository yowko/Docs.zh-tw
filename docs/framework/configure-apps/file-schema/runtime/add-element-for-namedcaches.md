---
title: <namedCaches> 的 <add> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: fd6668a551663470a97b07ff131710dbe92a91f5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659022"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="58f13-102">\<新增 namedCaches > 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="58f13-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="58f13-103">將專案加入至記憶體`namedCaches`快取的集合。 `namedCache`</span><span class="sxs-lookup"><span data-stu-id="58f13-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="58f13-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="58f13-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="58f13-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="58f13-105">\<memoryCache></span></span>  
<span data-ttu-id="58f13-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="58f13-106">\<namedCaches></span></span>  
<span data-ttu-id="58f13-107">\<add></span><span class="sxs-lookup"><span data-stu-id="58f13-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f13-108">語法</span><span class="sxs-lookup"><span data-stu-id="58f13-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="58f13-109">類型</span><span class="sxs-lookup"><span data-stu-id="58f13-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58f13-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="58f13-110">Attributes and Elements</span></span>  
 <span data-ttu-id="58f13-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="58f13-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58f13-112">屬性</span><span class="sxs-lookup"><span data-stu-id="58f13-112">Attributes</span></span>  
  
|<span data-ttu-id="58f13-113">屬性</span><span class="sxs-lookup"><span data-stu-id="58f13-113">Attribute</span></span>|<span data-ttu-id="58f13-114">說明</span><span class="sxs-lookup"><span data-stu-id="58f13-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="58f13-115">整數值, 指定實例<xref:System.Runtime.Caching.MemoryCache>可以成長到的最大允許大小 (以 mb 為單位)。</span><span class="sxs-lookup"><span data-stu-id="58f13-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="58f13-116">預設值為 0, 表示<xref:System.Runtime.Caching.MemoryCache>預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="58f13-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="58f13-117">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="58f13-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="58f13-118">介於0和100之間的整數值, 指定可供快取使用之實際安裝電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="58f13-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="58f13-119">預設值為 0, 表示<xref:System.Runtime.Caching.MemoryCache>預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="58f13-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="58f13-120">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="58f13-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="58f13-121">此值會以 "HH: MM: SS" 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="58f13-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58f13-122">子元素</span><span class="sxs-lookup"><span data-stu-id="58f13-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="58f13-123">父項目</span><span class="sxs-lookup"><span data-stu-id="58f13-123">Parent Elements</span></span>  
  
|<span data-ttu-id="58f13-124">項目</span><span class="sxs-lookup"><span data-stu-id="58f13-124">Element</span></span>|<span data-ttu-id="58f13-125">描述</span><span class="sxs-lookup"><span data-stu-id="58f13-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58f13-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="58f13-126">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="58f13-127">包含已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。</span><span class="sxs-lookup"><span data-stu-id="58f13-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58f13-128">備註</span><span class="sxs-lookup"><span data-stu-id="58f13-128">Remarks</span></span>  
 <span data-ttu-id="58f13-129">元素會將專案加入至記憶體`namedCaches`快取的集合。 `add`</span><span class="sxs-lookup"><span data-stu-id="58f13-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="58f13-130">在您使用`add`專案之前, 您可以使用[clear](clear-element-for-namedcaches.md)元素, 以確定集合中沒有任何其他已命名的快取。</span><span class="sxs-lookup"><span data-stu-id="58f13-130">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="58f13-131">這個元素可以在 machine.config 檔案和 web.config 檔案中使用。</span><span class="sxs-lookup"><span data-stu-id="58f13-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58f13-132">範例</span><span class="sxs-lookup"><span data-stu-id="58f13-132">Example</span></span>  
 <span data-ttu-id="58f13-133">下列範例示範如何將預設`namedCache`專案的設定定義為記憶體快取的`namedCaches`集合。</span><span class="sxs-lookup"><span data-stu-id="58f13-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58f13-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58f13-134">See also</span></span>

- [<span data-ttu-id="58f13-135">\<namedCaches > 元素 (快取設定)</span><span class="sxs-lookup"><span data-stu-id="58f13-135">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
