---
title: <namedCaches> 的 <remove> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: c8ad5a0ce6d7a3059943b3962b9255385cea6e15
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183984"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="e747c-102">\<namedCaches> 的 \<remove> 項目</span><span class="sxs-lookup"><span data-stu-id="e747c-102">\<remove> Element for \<namedCaches></span></span>

<span data-ttu-id="e747c-103">從記憶體快取的 `namedCaches` 集合移除具名快取項目。</span><span class="sxs-lookup"><span data-stu-id="e747c-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="e747c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e747c-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="e747c-105">類型</span><span class="sxs-lookup"><span data-stu-id="e747c-105">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e747c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e747c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e747c-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e747c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e747c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e747c-108">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="e747c-109">子元素</span><span class="sxs-lookup"><span data-stu-id="e747c-109">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="e747c-110">父項目</span><span class="sxs-lookup"><span data-stu-id="e747c-110">Parent Elements</span></span>  
  
|<span data-ttu-id="e747c-111">項目</span><span class="sxs-lookup"><span data-stu-id="e747c-111">Element</span></span>|<span data-ttu-id="e747c-112">描述</span><span class="sxs-lookup"><span data-stu-id="e747c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="e747c-113">包含已命名實例的設定設定集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="e747c-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e747c-114">備註</span><span class="sxs-lookup"><span data-stu-id="e747c-114">Remarks</span></span>  

 <span data-ttu-id="e747c-115">`remove`元素會從記憶體快取的命名快取 `namedCache` 集合中移除專案。</span><span class="sxs-lookup"><span data-stu-id="e747c-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e747c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e747c-116">See also</span></span>

- [<span data-ttu-id="e747c-117">\<namedCaches> (快取設定的元素) </span><span class="sxs-lookup"><span data-stu-id="e747c-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
