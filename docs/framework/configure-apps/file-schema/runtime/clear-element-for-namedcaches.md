---
title: <namedCaches> 的 <clear> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: e563f8f27538e70ba90465fc28d300754509f7a4
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423313"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="0eead-102">\<清除 > 項目\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="0eead-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="0eead-103">清除所有`namedCache`中的項目`namedCaches`記憶體快取的集合。</span><span class="sxs-lookup"><span data-stu-id="0eead-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="0eead-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="0eead-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="0eead-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="0eead-105">\<memoryCache></span></span>  
<span data-ttu-id="0eead-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="0eead-106">\<namedCaches></span></span>  
<span data-ttu-id="0eead-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0eead-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eead-108">語法</span><span class="sxs-lookup"><span data-stu-id="0eead-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="0eead-109">type</span><span class="sxs-lookup"><span data-stu-id="0eead-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eead-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0eead-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0eead-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0eead-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eead-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0eead-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="0eead-113">子元素</span><span class="sxs-lookup"><span data-stu-id="0eead-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="0eead-114">父項目</span><span class="sxs-lookup"><span data-stu-id="0eead-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0eead-115">項目</span><span class="sxs-lookup"><span data-stu-id="0eead-115">Element</span></span>|<span data-ttu-id="0eead-116">描述</span><span class="sxs-lookup"><span data-stu-id="0eead-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eead-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="0eead-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="0eead-118">包含集合的組態設定具名<xref:System.Runtime.Caching.MemoryCache>執行個體。</span><span class="sxs-lookup"><span data-stu-id="0eead-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eead-119">備註</span><span class="sxs-lookup"><span data-stu-id="0eead-119">Remarks</span></span>  
 <span data-ttu-id="0eead-120">`clear`項目清除所有`namedCache`記憶體內部快取的具名快取集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="0eead-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="0eead-121">您可以使用`clear`項目才能使用`add`項目將加入新的具名快取項目，才能確定有沒有其他具名集合中的快取。</span><span class="sxs-lookup"><span data-stu-id="0eead-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eead-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eead-122">See also</span></span>

- [<span data-ttu-id="0eead-123">\<namedCaches > 項目 （快取設定）</span><span class="sxs-lookup"><span data-stu-id="0eead-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
