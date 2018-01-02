---
title: "&lt;清除&gt;元素&lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 501371346b3c1496122d93a98eb89dd4afc6bcd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="868b4-102">&lt;清除&gt;元素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="868b4-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="868b4-103">清除所有`namedCache`中的項目`namedCaches`記憶體快取的集合。</span><span class="sxs-lookup"><span data-stu-id="868b4-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="868b4-104">\<system.runtime.caching ></span><span class="sxs-lookup"><span data-stu-id="868b4-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="868b4-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="868b4-105">\<memoryCache></span></span>  
<span data-ttu-id="868b4-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="868b4-106">\<namedCaches></span></span>  
<span data-ttu-id="868b4-107">\<add></span><span class="sxs-lookup"><span data-stu-id="868b4-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="868b4-108">語法</span><span class="sxs-lookup"><span data-stu-id="868b4-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="868b4-109">類型</span><span class="sxs-lookup"><span data-stu-id="868b4-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="868b4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="868b4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="868b4-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="868b4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="868b4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="868b4-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="868b4-113">子項目</span><span class="sxs-lookup"><span data-stu-id="868b4-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="868b4-114">父項目</span><span class="sxs-lookup"><span data-stu-id="868b4-114">Parent Elements</span></span>  
  
|<span data-ttu-id="868b4-115">項目</span><span class="sxs-lookup"><span data-stu-id="868b4-115">Element</span></span>|<span data-ttu-id="868b4-116">描述</span><span class="sxs-lookup"><span data-stu-id="868b4-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="868b4-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="868b4-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="868b4-118">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="868b4-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="868b4-119">備註</span><span class="sxs-lookup"><span data-stu-id="868b4-119">Remarks</span></span>  
 <span data-ttu-id="868b4-120">`clear`項目清除所有`namedCache`記憶體快取具名快取在集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="868b4-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="868b4-121">您可以使用`clear`使用之前的項目`add`元素將加入新的具名快取項目，以便確定有沒有其他具名快取，在集合中的。</span><span class="sxs-lookup"><span data-stu-id="868b4-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868b4-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="868b4-122">See Also</span></span>  
 [<span data-ttu-id="868b4-123">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="868b4-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
