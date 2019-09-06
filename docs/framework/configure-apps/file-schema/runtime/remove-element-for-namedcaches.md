---
title: <namedCaches> 的 <remove> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252343"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="7919d-102">\<移除 namedCaches > 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="7919d-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="7919d-103">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="7919d-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="7919d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7919d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7919d-105">&nbsp;&nbsp;[ **\<> 的緩存**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7919d-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="7919d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7919d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="7919d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7919d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="7919d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="7919d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7919d-109">語法</span><span class="sxs-lookup"><span data-stu-id="7919d-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="7919d-110">類型</span><span class="sxs-lookup"><span data-stu-id="7919d-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7919d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7919d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7919d-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7919d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7919d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7919d-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="7919d-114">子元素</span><span class="sxs-lookup"><span data-stu-id="7919d-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="7919d-115">父項目</span><span class="sxs-lookup"><span data-stu-id="7919d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7919d-116">項目</span><span class="sxs-lookup"><span data-stu-id="7919d-116">Element</span></span>|<span data-ttu-id="7919d-117">描述</span><span class="sxs-lookup"><span data-stu-id="7919d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7919d-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="7919d-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="7919d-119">包含已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。</span><span class="sxs-lookup"><span data-stu-id="7919d-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7919d-120">備註</span><span class="sxs-lookup"><span data-stu-id="7919d-120">Remarks</span></span>  
 <span data-ttu-id="7919d-121">元素會從記憶體`namedCache`快取的命名快取集合中移除專案。 `remove`</span><span class="sxs-lookup"><span data-stu-id="7919d-121">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7919d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7919d-122">See also</span></span>

- [<span data-ttu-id="7919d-123">\<namedCaches > 元素（快取設定）</span><span class="sxs-lookup"><span data-stu-id="7919d-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
