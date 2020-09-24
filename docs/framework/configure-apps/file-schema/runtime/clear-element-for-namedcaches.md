---
title: <namedCaches> 的 <clear> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: d65712f091c5fb9212167b4759c70db7e5d744c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149409"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="58187-102">\<namedCaches> 的 \<clear> 項目</span><span class="sxs-lookup"><span data-stu-id="58187-102">\<clear> Element for \<namedCaches></span></span>

<span data-ttu-id="58187-103">清除集合中記憶體快取的所有 `namedCache` 專案 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="58187-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="58187-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="58187-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="58187-105">類型</span><span class="sxs-lookup"><span data-stu-id="58187-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58187-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="58187-106">Attributes and Elements</span></span>  

 <span data-ttu-id="58187-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="58187-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58187-108">屬性</span><span class="sxs-lookup"><span data-stu-id="58187-108">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="58187-109">子元素</span><span class="sxs-lookup"><span data-stu-id="58187-109">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="58187-110">父項目</span><span class="sxs-lookup"><span data-stu-id="58187-110">Parent Elements</span></span>  
  
|<span data-ttu-id="58187-111">項目</span><span class="sxs-lookup"><span data-stu-id="58187-111">Element</span></span>|<span data-ttu-id="58187-112">描述</span><span class="sxs-lookup"><span data-stu-id="58187-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="58187-113">包含已命名實例的設定設定集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="58187-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58187-114">備註</span><span class="sxs-lookup"><span data-stu-id="58187-114">Remarks</span></span>  

 <span data-ttu-id="58187-115">`clear`專案會清除已命名之快取集合中的所有 `namedCache` 專案，以取得記憶體快取。</span><span class="sxs-lookup"><span data-stu-id="58187-115">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="58187-116">您可以使用專案 `clear` `add` 來加入新的命名快取專案，以便確定集合中沒有其他已命名的快取。</span><span class="sxs-lookup"><span data-stu-id="58187-116">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58187-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58187-117">See also</span></span>

- [<span data-ttu-id="58187-118">\<namedCaches> (快取設定的元素) </span><span class="sxs-lookup"><span data-stu-id="58187-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
