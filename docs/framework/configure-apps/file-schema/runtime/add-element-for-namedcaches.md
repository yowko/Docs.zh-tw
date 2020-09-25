---
title: <namedCaches> 的 <add> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: cd920b58290050fcc30ea5d0a1ac113a333902fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195359"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="b195e-102">\<namedCaches> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="b195e-102">\<add> Element for \<namedCaches></span></span>

<span data-ttu-id="b195e-103">將 `namedCache` 專案加入至記憶體快取的集合中 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="b195e-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b195e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b195e-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="b195e-105">類型</span><span class="sxs-lookup"><span data-stu-id="b195e-105">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b195e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b195e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b195e-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b195e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b195e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b195e-108">Attributes</span></span>  
  
|<span data-ttu-id="b195e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b195e-109">Attribute</span></span>|<span data-ttu-id="b195e-110">描述</span><span class="sxs-lookup"><span data-stu-id="b195e-110">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="b195e-111">整數值，指定的實例可成長的大小上限 () （以 mb 為單位） <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="b195e-111">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="b195e-112">預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="b195e-112">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="b195e-113">快取的名稱。</span><span class="sxs-lookup"><span data-stu-id="b195e-113">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="b195e-114">介於0與100之間的整數值，指定快取可以取用的實際安裝電腦記憶體百分比上限。</span><span class="sxs-lookup"><span data-stu-id="b195e-114">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="b195e-115">預設值為0，表示 <xref:System.Runtime.Caching.MemoryCache> 預設會使用類別的自動調整大小啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="b195e-115">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="b195e-116">表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="b195e-116">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="b195e-117">此值是以 "HH： MM： SS" 格式輸入。</span><span class="sxs-lookup"><span data-stu-id="b195e-117">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b195e-118">子元素</span><span class="sxs-lookup"><span data-stu-id="b195e-118">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="b195e-119">父項目</span><span class="sxs-lookup"><span data-stu-id="b195e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b195e-120">項目</span><span class="sxs-lookup"><span data-stu-id="b195e-120">Element</span></span>|<span data-ttu-id="b195e-121">描述</span><span class="sxs-lookup"><span data-stu-id="b195e-121">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="b195e-122">包含已命名實例的設定設定集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="b195e-122">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b195e-123">備註</span><span class="sxs-lookup"><span data-stu-id="b195e-123">Remarks</span></span>  

 <span data-ttu-id="b195e-124">`add`元素會將專案加入至記憶體快取的 `namedCaches` 集合中。</span><span class="sxs-lookup"><span data-stu-id="b195e-124">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="b195e-125">您可以在使用元素之前，先使用 [clear](clear-element-for-namedcaches.md) 元素， `add` 確定集合中沒有任何其他命名快取。</span><span class="sxs-lookup"><span data-stu-id="b195e-125">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="b195e-126">這個元素可用於 machine.config 檔案和 Web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="b195e-126">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b195e-127">範例</span><span class="sxs-lookup"><span data-stu-id="b195e-127">Example</span></span>  

 <span data-ttu-id="b195e-128">下列範例示範如何為記憶體快取的集合定義預設專案的設定 `namedCache` `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="b195e-128">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b195e-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b195e-129">See also</span></span>

- [<span data-ttu-id="b195e-130">\<namedCaches> (快取設定的元素) </span><span class="sxs-lookup"><span data-stu-id="b195e-130">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
