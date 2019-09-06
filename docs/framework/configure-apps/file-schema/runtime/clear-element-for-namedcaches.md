---
title: <namedCaches> 的 <clear> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252752"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="44488-102">\<清除 namedCaches 的\<> 元素 ></span><span class="sxs-lookup"><span data-stu-id="44488-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="44488-103">清除`namedCache` 集合`namedCaches`中記憶體快取的所有專案。</span><span class="sxs-lookup"><span data-stu-id="44488-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="44488-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="44488-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="44488-105">&nbsp;&nbsp;[ **\<> 的緩存**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="44488-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="44488-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="44488-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="44488-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="44488-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="44488-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<清除 >**</span><span class="sxs-lookup"><span data-stu-id="44488-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44488-109">語法</span><span class="sxs-lookup"><span data-stu-id="44488-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="44488-110">類型</span><span class="sxs-lookup"><span data-stu-id="44488-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44488-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="44488-111">Attributes and Elements</span></span>  
 <span data-ttu-id="44488-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="44488-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44488-113">屬性</span><span class="sxs-lookup"><span data-stu-id="44488-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="44488-114">子元素</span><span class="sxs-lookup"><span data-stu-id="44488-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="44488-115">父項目</span><span class="sxs-lookup"><span data-stu-id="44488-115">Parent Elements</span></span>  
  
|<span data-ttu-id="44488-116">項目</span><span class="sxs-lookup"><span data-stu-id="44488-116">Element</span></span>|<span data-ttu-id="44488-117">描述</span><span class="sxs-lookup"><span data-stu-id="44488-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44488-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="44488-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="44488-119">包含已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。</span><span class="sxs-lookup"><span data-stu-id="44488-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44488-120">備註</span><span class="sxs-lookup"><span data-stu-id="44488-120">Remarks</span></span>  
 <span data-ttu-id="44488-121">元素會清除已`namedCache`命名快取集合中記憶體快取的所有專案。 `clear`</span><span class="sxs-lookup"><span data-stu-id="44488-121">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="44488-122">您可以使用`clear`專案，然後`add`使用專案來加入新的命名快取專案，以確保集合中沒有其他命名的快取。</span><span class="sxs-lookup"><span data-stu-id="44488-122">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44488-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44488-123">See also</span></span>

- [<span data-ttu-id="44488-124">\<namedCaches > 元素（快取設定）</span><span class="sxs-lookup"><span data-stu-id="44488-124">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
