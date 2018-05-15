---
title: '&lt;清除&gt;元素&lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cdd6e4a4849a031dc6bcad909509498406fcb129
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="ae779-102">&lt;清除&gt;元素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="ae779-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="ae779-103">清除所有`namedCache`中的項目`namedCaches`記憶體快取的集合。</span><span class="sxs-lookup"><span data-stu-id="ae779-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="ae779-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="ae779-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="ae779-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="ae779-105">\<memoryCache></span></span>  
<span data-ttu-id="ae779-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="ae779-106">\<namedCaches></span></span>  
<span data-ttu-id="ae779-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ae779-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae779-108">語法</span><span class="sxs-lookup"><span data-stu-id="ae779-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ae779-109">類型</span><span class="sxs-lookup"><span data-stu-id="ae779-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae779-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ae779-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ae779-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ae779-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae779-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ae779-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="ae779-113">子項目</span><span class="sxs-lookup"><span data-stu-id="ae779-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="ae779-114">父項目</span><span class="sxs-lookup"><span data-stu-id="ae779-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ae779-115">項目</span><span class="sxs-lookup"><span data-stu-id="ae779-115">Element</span></span>|<span data-ttu-id="ae779-116">描述</span><span class="sxs-lookup"><span data-stu-id="ae779-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae779-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="ae779-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="ae779-118">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae779-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae779-119">備註</span><span class="sxs-lookup"><span data-stu-id="ae779-119">Remarks</span></span>  
 <span data-ttu-id="ae779-120">`clear`項目清除所有`namedCache`記憶體快取具名快取在集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="ae779-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="ae779-121">您可以使用`clear`使用之前的項目`add`元素將加入新的具名快取項目，以便確定有沒有其他具名快取，在集合中的。</span><span class="sxs-lookup"><span data-stu-id="ae779-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae779-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae779-122">See Also</span></span>  
 [<span data-ttu-id="ae779-123">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="ae779-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
