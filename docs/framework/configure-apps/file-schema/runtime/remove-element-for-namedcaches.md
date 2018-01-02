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
ms.workload: dotnet
ms.openlocfilehash: 4b360b206586b263627ab6f6b7e0309f3055f38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="48148-102">&lt;移除&gt;元素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="48148-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="48148-103">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="48148-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="48148-104">\<system.runtime.caching ></span><span class="sxs-lookup"><span data-stu-id="48148-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="48148-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="48148-105">\<memoryCache></span></span>  
<span data-ttu-id="48148-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="48148-106">\<namedCaches></span></span>  
<span data-ttu-id="48148-107">\<移除 ></span><span class="sxs-lookup"><span data-stu-id="48148-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48148-108">語法</span><span class="sxs-lookup"><span data-stu-id="48148-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="48148-109">類型</span><span class="sxs-lookup"><span data-stu-id="48148-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48148-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="48148-110">Attributes and Elements</span></span>  
 <span data-ttu-id="48148-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="48148-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48148-112">屬性</span><span class="sxs-lookup"><span data-stu-id="48148-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="48148-113">子項目</span><span class="sxs-lookup"><span data-stu-id="48148-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="48148-114">父項目</span><span class="sxs-lookup"><span data-stu-id="48148-114">Parent Elements</span></span>  
  
|<span data-ttu-id="48148-115">項目</span><span class="sxs-lookup"><span data-stu-id="48148-115">Element</span></span>|<span data-ttu-id="48148-116">描述</span><span class="sxs-lookup"><span data-stu-id="48148-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48148-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="48148-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="48148-118">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="48148-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48148-119">備註</span><span class="sxs-lookup"><span data-stu-id="48148-119">Remarks</span></span>  
 <span data-ttu-id="48148-120">`remove`項目會移除`namedCache`從記憶體快取具名快取集合的項目。</span><span class="sxs-lookup"><span data-stu-id="48148-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48148-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="48148-121">See Also</span></span>  
 [<span data-ttu-id="48148-122">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="48148-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
