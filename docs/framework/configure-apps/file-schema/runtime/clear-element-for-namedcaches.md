---
title: <namedCaches> 的 <clear> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658853"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="86f37-102">\<清除 namedCaches 的\<> 元素 ></span><span class="sxs-lookup"><span data-stu-id="86f37-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="86f37-103">清除`namedCache` 集合`namedCaches`中記憶體快取的所有專案。</span><span class="sxs-lookup"><span data-stu-id="86f37-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="86f37-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="86f37-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="86f37-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="86f37-105">\<memoryCache></span></span>  
<span data-ttu-id="86f37-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="86f37-106">\<namedCaches></span></span>  
<span data-ttu-id="86f37-107">\<add></span><span class="sxs-lookup"><span data-stu-id="86f37-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f37-108">語法</span><span class="sxs-lookup"><span data-stu-id="86f37-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="86f37-109">類型</span><span class="sxs-lookup"><span data-stu-id="86f37-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86f37-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="86f37-110">Attributes and Elements</span></span>  
 <span data-ttu-id="86f37-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="86f37-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86f37-112">屬性</span><span class="sxs-lookup"><span data-stu-id="86f37-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="86f37-113">子元素</span><span class="sxs-lookup"><span data-stu-id="86f37-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="86f37-114">父項目</span><span class="sxs-lookup"><span data-stu-id="86f37-114">Parent Elements</span></span>  
  
|<span data-ttu-id="86f37-115">項目</span><span class="sxs-lookup"><span data-stu-id="86f37-115">Element</span></span>|<span data-ttu-id="86f37-116">說明</span><span class="sxs-lookup"><span data-stu-id="86f37-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86f37-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="86f37-117">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="86f37-118">包含已命名<xref:System.Runtime.Caching.MemoryCache>實例的設定集合。</span><span class="sxs-lookup"><span data-stu-id="86f37-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86f37-119">備註</span><span class="sxs-lookup"><span data-stu-id="86f37-119">Remarks</span></span>  
 <span data-ttu-id="86f37-120">元素會清除已`namedCache`命名快取集合中記憶體快取的所有專案。 `clear`</span><span class="sxs-lookup"><span data-stu-id="86f37-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="86f37-121">您可以使用`clear`專案, 然後`add`使用專案來加入新的命名快取專案, 以確保集合中沒有其他命名的快取。</span><span class="sxs-lookup"><span data-stu-id="86f37-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f37-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86f37-122">See also</span></span>

- [<span data-ttu-id="86f37-123">\<namedCaches > 元素 (快取設定)</span><span class="sxs-lookup"><span data-stu-id="86f37-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
