---
title: '&lt;清除&gt;項目&lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: d71c5de42104961bc096b786dfe50bb4097bc4fc
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083557"
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="aea2a-102">&lt;清除&gt;項目&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="aea2a-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="aea2a-103">清除所有`namedCache`中的項目`namedCaches`記憶體快取的集合。</span><span class="sxs-lookup"><span data-stu-id="aea2a-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="aea2a-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="aea2a-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="aea2a-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="aea2a-105">\<memoryCache></span></span>  
<span data-ttu-id="aea2a-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="aea2a-106">\<namedCaches></span></span>  
<span data-ttu-id="aea2a-107">\<add></span><span class="sxs-lookup"><span data-stu-id="aea2a-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea2a-108">語法</span><span class="sxs-lookup"><span data-stu-id="aea2a-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="aea2a-109">類型</span><span class="sxs-lookup"><span data-stu-id="aea2a-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aea2a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aea2a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aea2a-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aea2a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aea2a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="aea2a-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="aea2a-113">子項目</span><span class="sxs-lookup"><span data-stu-id="aea2a-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="aea2a-114">父項目</span><span class="sxs-lookup"><span data-stu-id="aea2a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="aea2a-115">項目</span><span class="sxs-lookup"><span data-stu-id="aea2a-115">Element</span></span>|<span data-ttu-id="aea2a-116">描述</span><span class="sxs-lookup"><span data-stu-id="aea2a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aea2a-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="aea2a-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="aea2a-118">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="aea2a-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aea2a-119">備註</span><span class="sxs-lookup"><span data-stu-id="aea2a-119">Remarks</span></span>  
 <span data-ttu-id="aea2a-120">`clear`項目清除所有`namedCache`記憶體內部快取的具名快取集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="aea2a-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="aea2a-121">您可以使用`clear`項目才能使用`add`項目將加入新的具名快取項目，才能確定有沒有其他具名集合中的快取。</span><span class="sxs-lookup"><span data-stu-id="aea2a-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea2a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aea2a-122">See also</span></span>
- [<span data-ttu-id="aea2a-123">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="aea2a-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
