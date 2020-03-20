---
title: <system.runtime.caching> 項目 (快取設定)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153850"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="0cd46-102">\<系統.運行時.緩存>元素（緩存設置）</span><span class="sxs-lookup"><span data-stu-id="0cd46-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="0cd46-103">透過組態檔中的 <xref:System.Runtime.Caching.ObjectCache> 項目，提供預設記憶體內 `memoryCache` 實作的組態。</span><span class="sxs-lookup"><span data-stu-id="0cd46-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="0cd46-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0cd46-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0cd46-105">&nbsp;&nbsp;**\<系統.運行時.緩存>**</span><span class="sxs-lookup"><span data-stu-id="0cd46-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cd46-106">語法</span><span class="sxs-lookup"><span data-stu-id="0cd46-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cd46-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0cd46-107">Attributes and Elements</span></span>

<span data-ttu-id="0cd46-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0cd46-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cd46-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0cd46-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="0cd46-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0cd46-110">Child Elements</span></span>

|<span data-ttu-id="0cd46-111">元素</span><span class="sxs-lookup"><span data-stu-id="0cd46-111">Element</span></span>|<span data-ttu-id="0cd46-112">描述</span><span class="sxs-lookup"><span data-stu-id="0cd46-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cd46-113">\<記憶體緩存></span><span class="sxs-lookup"><span data-stu-id="0cd46-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="0cd46-114">定義項目，這個項目會用來設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取。</span><span class="sxs-lookup"><span data-stu-id="0cd46-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0cd46-115">父項目</span><span class="sxs-lookup"><span data-stu-id="0cd46-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0cd46-116">元素</span><span class="sxs-lookup"><span data-stu-id="0cd46-116">Element</span></span>|<span data-ttu-id="0cd46-117">描述</span><span class="sxs-lookup"><span data-stu-id="0cd46-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cd46-118">\<配置></span><span class="sxs-lookup"><span data-stu-id="0cd46-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="0cd46-119">指定通用語言運行時和 .NET Framework 應用程式使用的每個設定檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0cd46-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cd46-120">備註</span><span class="sxs-lookup"><span data-stu-id="0cd46-120">Remarks</span></span>

<span data-ttu-id="0cd46-121">這個命名空間中的類別提供如同在 ASP.NET 中使用快取設備的方式，但是不需要在 `System.Web` 組件上的相依性。</span><span class="sxs-lookup"><span data-stu-id="0cd46-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="0cd46-122">如需詳細資訊，請參閱 [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="0cd46-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cd46-123">命名空間中的<xref:System.Runtime.Caching>輸出緩存功能和類型在 .NET 框架 4 中是新的。</span><span class="sxs-lookup"><span data-stu-id="0cd46-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cd46-124">範例</span><span class="sxs-lookup"><span data-stu-id="0cd46-124">Example</span></span>

<span data-ttu-id="0cd46-125">下列範例示範如何設定以 <xref:System.Runtime.Caching.MemoryCache> 類別為基礎的快取，</span><span class="sxs-lookup"><span data-stu-id="0cd46-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="0cd46-126">並示範如何設定記憶體快取之 `namedCaches` 項目的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0cd46-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="0cd46-127">通過將屬性設置為"預設"，`name`緩存的名稱將設置為預設緩存條目名稱。</span><span class="sxs-lookup"><span data-stu-id="0cd46-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="0cd46-128">`cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。</span><span class="sxs-lookup"><span data-stu-id="0cd46-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="0cd46-129">將這些屬性設定為零表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 自動調整啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="0cd46-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="0cd46-130">快取實作應該會每隔兩分鐘即比較目前的記憶體負載與絕對和百分比型記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="0cd46-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cd46-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cd46-131">See also</span></span>

- [<span data-ttu-id="0cd46-132">\<記憶體緩存>元素（緩存設置）</span><span class="sxs-lookup"><span data-stu-id="0cd46-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
