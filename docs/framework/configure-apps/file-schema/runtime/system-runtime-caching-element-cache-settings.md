---
title: <system.runtime.caching> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ead643afd34b4c3422d85e6f7876879de477ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927234"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="ffff7-102">\<> 元素 (快取設定)</span><span class="sxs-lookup"><span data-stu-id="ffff7-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="ffff7-103">透過組態檔中的 <xref:System.Runtime.Caching.ObjectCache> 項目，提供預設記憶體內 `memoryCache` 實作的組態。</span><span class="sxs-lookup"><span data-stu-id="ffff7-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="ffff7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ffff7-104">\<configuration></span></span>  
<span data-ttu-id="ffff7-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="ffff7-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffff7-106">語法</span><span class="sxs-lookup"><span data-stu-id="ffff7-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffff7-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ffff7-107">Attributes and Elements</span></span>

<span data-ttu-id="ffff7-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ffff7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffff7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ffff7-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="ffff7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ffff7-110">Child Elements</span></span>

|<span data-ttu-id="ffff7-111">項目</span><span class="sxs-lookup"><span data-stu-id="ffff7-111">Element</span></span>|<span data-ttu-id="ffff7-112">描述</span><span class="sxs-lookup"><span data-stu-id="ffff7-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffff7-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="ffff7-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="ffff7-114">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="ffff7-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ffff7-115">父項目</span><span class="sxs-lookup"><span data-stu-id="ffff7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ffff7-116">項目</span><span class="sxs-lookup"><span data-stu-id="ffff7-116">Element</span></span>|<span data-ttu-id="ffff7-117">描述</span><span class="sxs-lookup"><span data-stu-id="ffff7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffff7-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ffff7-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="ffff7-119">指定通用語言執行時間和 .NET Framework 應用程式所使用之每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ffff7-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffff7-120">備註</span><span class="sxs-lookup"><span data-stu-id="ffff7-120">Remarks</span></span>

<span data-ttu-id="ffff7-121">這個命名空間中的類別提供如同在 ASP.NET 中使用快取設備的方式，但是不需要在 `System.Web` 組件上的相依性。</span><span class="sxs-lookup"><span data-stu-id="ffff7-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="ffff7-122">如需詳細資訊，請參閱 [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="ffff7-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffff7-123"><xref:System.Runtime.Caching>命名空間中的輸出快取功能和類型在 .NET Framework 4 中是新的。</span><span class="sxs-lookup"><span data-stu-id="ffff7-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffff7-124">範例</span><span class="sxs-lookup"><span data-stu-id="ffff7-124">Example</span></span>

<span data-ttu-id="ffff7-125">下列範例示範如何設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取，</span><span class="sxs-lookup"><span data-stu-id="ffff7-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="ffff7-126">並示範如何設定記憶體快取之 `namedCaches` 項目的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffff7-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="ffff7-127">快取的名稱會設定為預設快取專案名稱, 方法是將`name`屬性設定為 "default"。</span><span class="sxs-lookup"><span data-stu-id="ffff7-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="ffff7-128">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="ffff7-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="ffff7-129">將這些屬性設定為零表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 自動調整啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="ffff7-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="ffff7-130">快取實作應該會每隔兩分鐘即比較目前的記憶體負載與絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="ffff7-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffff7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffff7-131">See also</span></span>

- [<span data-ttu-id="ffff7-132">\<memoryCache > 元素 (快取設定)</span><span class="sxs-lookup"><span data-stu-id="ffff7-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
