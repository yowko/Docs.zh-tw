---
title: <namedCaches> 的 <remove> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252343"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="ad90a-102">\<namedCaches> 的 \<remove> 項目</span><span class="sxs-lookup"><span data-stu-id="ad90a-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="ad90a-103">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="ad90a-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="ad90a-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad90a-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ad90a-105">類型</span><span class="sxs-lookup"><span data-stu-id="ad90a-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad90a-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad90a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ad90a-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ad90a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad90a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ad90a-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="ad90a-109">子元素</span><span class="sxs-lookup"><span data-stu-id="ad90a-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="ad90a-110">父項目</span><span class="sxs-lookup"><span data-stu-id="ad90a-110">Parent Elements</span></span>  
  
|<span data-ttu-id="ad90a-111">元素</span><span class="sxs-lookup"><span data-stu-id="ad90a-111">Element</span></span>|<span data-ttu-id="ad90a-112">描述</span><span class="sxs-lookup"><span data-stu-id="ad90a-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="ad90a-113">包含已命名實例的設定集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="ad90a-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad90a-114">備註</span><span class="sxs-lookup"><span data-stu-id="ad90a-114">Remarks</span></span>  
 <span data-ttu-id="ad90a-115">`remove`元素會從記憶體快取的命名快取 `namedCache` 集合中移除專案。</span><span class="sxs-lookup"><span data-stu-id="ad90a-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad90a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad90a-116">See also</span></span>

- [<span data-ttu-id="ad90a-117">\<namedCaches>元素（快取設定）</span><span class="sxs-lookup"><span data-stu-id="ad90a-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
