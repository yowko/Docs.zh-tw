---
title: '&lt;移除&gt;元素&lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6ffaea24910a6b8f4a120d6b72219bff592fab17
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745210"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="75438-102">&lt;移除&gt;元素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="75438-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="75438-103">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="75438-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="75438-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="75438-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="75438-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="75438-105">\<memoryCache></span></span>  
<span data-ttu-id="75438-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="75438-106">\<namedCaches></span></span>  
<span data-ttu-id="75438-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="75438-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75438-108">語法</span><span class="sxs-lookup"><span data-stu-id="75438-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="75438-109">類型</span><span class="sxs-lookup"><span data-stu-id="75438-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75438-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="75438-110">Attributes and Elements</span></span>  
 <span data-ttu-id="75438-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="75438-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75438-112">屬性</span><span class="sxs-lookup"><span data-stu-id="75438-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="75438-113">子項目</span><span class="sxs-lookup"><span data-stu-id="75438-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="75438-114">父項目</span><span class="sxs-lookup"><span data-stu-id="75438-114">Parent Elements</span></span>  
  
|<span data-ttu-id="75438-115">項目</span><span class="sxs-lookup"><span data-stu-id="75438-115">Element</span></span>|<span data-ttu-id="75438-116">描述</span><span class="sxs-lookup"><span data-stu-id="75438-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75438-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="75438-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="75438-118">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="75438-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75438-119">備註</span><span class="sxs-lookup"><span data-stu-id="75438-119">Remarks</span></span>  
 <span data-ttu-id="75438-120">`remove`項目會移除`namedCache`從記憶體快取具名快取集合的項目。</span><span class="sxs-lookup"><span data-stu-id="75438-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75438-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75438-121">See Also</span></span>  
 [<span data-ttu-id="75438-122">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="75438-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
