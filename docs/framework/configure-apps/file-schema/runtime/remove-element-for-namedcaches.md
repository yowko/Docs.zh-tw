---
title: "&lt;移除&gt;元素&lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6170b59e87948225708c9e697cba1542d756d2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="83f30-102">&lt;移除&gt;元素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="83f30-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="83f30-103">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="83f30-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="83f30-104">\<system.runtime.caching ></span><span class="sxs-lookup"><span data-stu-id="83f30-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="83f30-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="83f30-105">\<memoryCache></span></span>  
<span data-ttu-id="83f30-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="83f30-106">\<namedCaches></span></span>  
<span data-ttu-id="83f30-107">\<移除 ></span><span class="sxs-lookup"><span data-stu-id="83f30-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f30-108">語法</span><span class="sxs-lookup"><span data-stu-id="83f30-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="83f30-109">類型</span><span class="sxs-lookup"><span data-stu-id="83f30-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83f30-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="83f30-110">Attributes and Elements</span></span>  
 <span data-ttu-id="83f30-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="83f30-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83f30-112">屬性</span><span class="sxs-lookup"><span data-stu-id="83f30-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="83f30-113">子項目</span><span class="sxs-lookup"><span data-stu-id="83f30-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="83f30-114">父項目</span><span class="sxs-lookup"><span data-stu-id="83f30-114">Parent Elements</span></span>  
  
|<span data-ttu-id="83f30-115">項目</span><span class="sxs-lookup"><span data-stu-id="83f30-115">Element</span></span>|<span data-ttu-id="83f30-116">說明</span><span class="sxs-lookup"><span data-stu-id="83f30-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83f30-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="83f30-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="83f30-118">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="83f30-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83f30-119">備註</span><span class="sxs-lookup"><span data-stu-id="83f30-119">Remarks</span></span>  
 <span data-ttu-id="83f30-120">`remove`項目會移除`namedCache`從記憶體快取具名快取集合的項目。</span><span class="sxs-lookup"><span data-stu-id="83f30-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f30-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83f30-121">See Also</span></span>  
 [<span data-ttu-id="83f30-122">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="83f30-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
