---
title: <namedCaches> 的 <remove> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: e9b126cee83bc8109606d915ea48549beea970c9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663479"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="047b6-102">\<移除 namedCaches > 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="047b6-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="047b6-103">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="047b6-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="047b6-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="047b6-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="047b6-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="047b6-105">\<memoryCache></span></span>  
<span data-ttu-id="047b6-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="047b6-106">\<namedCaches></span></span>  
<span data-ttu-id="047b6-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="047b6-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="047b6-108">語法</span><span class="sxs-lookup"><span data-stu-id="047b6-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="047b6-109">類型</span><span class="sxs-lookup"><span data-stu-id="047b6-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="047b6-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="047b6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="047b6-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="047b6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="047b6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="047b6-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="047b6-113">子元素</span><span class="sxs-lookup"><span data-stu-id="047b6-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="047b6-114">父項目</span><span class="sxs-lookup"><span data-stu-id="047b6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="047b6-115">項目</span><span class="sxs-lookup"><span data-stu-id="047b6-115">Element</span></span>|<span data-ttu-id="047b6-116">描述</span><span class="sxs-lookup"><span data-stu-id="047b6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="047b6-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="047b6-117">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="047b6-118">包含已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。</span><span class="sxs-lookup"><span data-stu-id="047b6-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="047b6-119">備註</span><span class="sxs-lookup"><span data-stu-id="047b6-119">Remarks</span></span>  
 <span data-ttu-id="047b6-120">元素會從記憶體`namedCache`快取的命名快取集合中移除專案。 `remove`</span><span class="sxs-lookup"><span data-stu-id="047b6-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047b6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="047b6-121">See also</span></span>

- [<span data-ttu-id="047b6-122">\<namedCaches > 元素 (快取設定)</span><span class="sxs-lookup"><span data-stu-id="047b6-122">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
