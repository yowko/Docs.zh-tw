---
title: <namedCaches> 的 <add> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154501"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="aa749-102">\<namedCaches> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="aa749-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="aa749-103">將 `namedCache` 專案加入至記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="aa749-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="aa749-104">語法</span><span class="sxs-lookup"><span data-stu-id="aa749-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="aa749-105">類型</span><span class="sxs-lookup"><span data-stu-id="aa749-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa749-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aa749-106">Attributes and Elements</span></span>  
 <span data-ttu-id="aa749-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aa749-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa749-108">屬性</span><span class="sxs-lookup"><span data-stu-id="aa749-108">Attributes</span></span>  
  
|<span data-ttu-id="aa749-109">屬性</span><span class="sxs-lookup"><span data-stu-id="aa749-109">Attribute</span></span>|<span data-ttu-id="aa749-110">描述</span><span class="sxs-lookup"><span data-stu-id="aa749-110">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="aa749-111">整數值，指定實例可以成長到的最大允許大小（以 mb 為單位） <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="aa749-111">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="aa749-112">預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="aa749-112">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="aa749-113">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="aa749-113">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="aa749-114">介於0和100之間的整數值，指定可供快取使用之實際安裝電腦記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="aa749-114">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="aa749-115">預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="aa749-115">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="aa749-116">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="aa749-116">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="aa749-117">此值會以 "HH： MM： SS" 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="aa749-117">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa749-118">子元素</span><span class="sxs-lookup"><span data-stu-id="aa749-118">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="aa749-119">父項目</span><span class="sxs-lookup"><span data-stu-id="aa749-119">Parent Elements</span></span>  
  
|<span data-ttu-id="aa749-120">元素</span><span class="sxs-lookup"><span data-stu-id="aa749-120">Element</span></span>|<span data-ttu-id="aa749-121">描述</span><span class="sxs-lookup"><span data-stu-id="aa749-121">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="aa749-122">包含已命名實例的設定集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="aa749-122">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa749-123">備註</span><span class="sxs-lookup"><span data-stu-id="aa749-123">Remarks</span></span>  
 <span data-ttu-id="aa749-124">`add`元素會將專案加入至記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="aa749-124">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="aa749-125">在您使用專案之前，您可以使用[clear](clear-element-for-namedcaches.md)元素， `add` 以確定集合中沒有任何其他已命名的快取。</span><span class="sxs-lookup"><span data-stu-id="aa749-125">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="aa749-126">這個元素可以在 machine.config 檔案和 web.config 檔案中使用。</span><span class="sxs-lookup"><span data-stu-id="aa749-126">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa749-127">範例</span><span class="sxs-lookup"><span data-stu-id="aa749-127">Example</span></span>  
 <span data-ttu-id="aa749-128">下列範例示範如何將預設專案的設定定義為 `namedCache` 記憶體快取的 `namedCaches` 集合。</span><span class="sxs-lookup"><span data-stu-id="aa749-128">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa749-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa749-129">See also</span></span>

- [<span data-ttu-id="aa749-130">\<namedCaches>元素（快取設定）</span><span class="sxs-lookup"><span data-stu-id="aa749-130">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
