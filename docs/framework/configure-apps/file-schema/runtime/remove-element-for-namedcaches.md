---
title: '&lt;移除&gt;項目&lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d31caf88e1376025484ed6d65d5277c015e70b5e
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613735"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="8d721-102">&lt;移除&gt;項目&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="8d721-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="8d721-103">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="8d721-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="8d721-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="8d721-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="8d721-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="8d721-105">\<memoryCache></span></span>  
<span data-ttu-id="8d721-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="8d721-106">\<namedCaches></span></span>  
<span data-ttu-id="8d721-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="8d721-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d721-108">語法</span><span class="sxs-lookup"><span data-stu-id="8d721-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="8d721-109">類型</span><span class="sxs-lookup"><span data-stu-id="8d721-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d721-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8d721-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d721-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8d721-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d721-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8d721-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="8d721-113">子項目</span><span class="sxs-lookup"><span data-stu-id="8d721-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="8d721-114">父項目</span><span class="sxs-lookup"><span data-stu-id="8d721-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8d721-115">項目</span><span class="sxs-lookup"><span data-stu-id="8d721-115">Element</span></span>|<span data-ttu-id="8d721-116">描述</span><span class="sxs-lookup"><span data-stu-id="8d721-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d721-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="8d721-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="8d721-118">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d721-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d721-119">備註</span><span class="sxs-lookup"><span data-stu-id="8d721-119">Remarks</span></span>  
 <span data-ttu-id="8d721-120">`remove`項目移除`namedCache`從記憶體快取的具名快取集合的項目。</span><span class="sxs-lookup"><span data-stu-id="8d721-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d721-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d721-121">See Also</span></span>  
- [<span data-ttu-id="8d721-122">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="8d721-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
