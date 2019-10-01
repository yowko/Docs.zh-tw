---
title: <defaultHttpCachePolicy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: f3b029e8b931e976bee85c98dd926e020c5b8743
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698270"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="36a4a-102">@no__t 0defaultHttpCachePolicy > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="36a4a-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="36a4a-103">描述 HTTP 快取是否作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="36a4a-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
[<span data-ttu-id="36a4a-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="36a4a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="36a4a-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="36a4a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="36a4a-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="36a4a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>  
<span data-ttu-id="36a4a-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<defaultHttpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="36a4a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36a4a-108">語法</span><span class="sxs-lookup"><span data-stu-id="36a4a-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36a4a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="36a4a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="36a4a-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="36a4a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36a4a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="36a4a-111">Attributes</span></span>  
  
|<span data-ttu-id="36a4a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="36a4a-112">Attribute</span></span>|<span data-ttu-id="36a4a-113">描述</span><span class="sxs-lookup"><span data-stu-id="36a4a-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="36a4a-114">指定快取的物件標記為過期之前的時間間隔上限。</span><span class="sxs-lookup"><span data-stu-id="36a4a-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="36a4a-115">指定在快取的物件標示為過期之前，經過計算的最晚時間的時間上限。</span><span class="sxs-lookup"><span data-stu-id="36a4a-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="36a4a-116">指定快取物件被視為最新的時間下限。</span><span class="sxs-lookup"><span data-stu-id="36a4a-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="36a4a-117">指定快取原則是自動的，還是略過快取。</span><span class="sxs-lookup"><span data-stu-id="36a4a-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="36a4a-118">預設值為 `BypassCache`。</span><span class="sxs-lookup"><span data-stu-id="36a4a-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36a4a-119">子元素</span><span class="sxs-lookup"><span data-stu-id="36a4a-119">Child Elements</span></span>  
 <span data-ttu-id="36a4a-120">None</span><span class="sxs-lookup"><span data-stu-id="36a4a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36a4a-121">父項目</span><span class="sxs-lookup"><span data-stu-id="36a4a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="36a4a-122">項目</span><span class="sxs-lookup"><span data-stu-id="36a4a-122">Element</span></span>|<span data-ttu-id="36a4a-123">描述</span><span class="sxs-lookup"><span data-stu-id="36a4a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36a4a-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="36a4a-124">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="36a4a-125">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="36a4a-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36a4a-126">備註</span><span class="sxs-lookup"><span data-stu-id="36a4a-126">Remarks</span></span>  
 <span data-ttu-id="36a4a-127">@No__t-0 屬性的值可能是 `BypassCache` 或 `Default`。</span><span class="sxs-lookup"><span data-stu-id="36a4a-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="36a4a-128">@No__t-0、`maximumStale` 和 @no__t 2 元素的值，都是格式為*d*的明確時間間隔。*hh*：*mm*：*ss* （天、小時、分鐘和秒），或是適當的常數 `minValue` 或 `maxValue`。</span><span class="sxs-lookup"><span data-stu-id="36a4a-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="36a4a-129">組態檔</span><span class="sxs-lookup"><span data-stu-id="36a4a-129">Configuration Files</span></span>  
 <span data-ttu-id="36a4a-130">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="36a4a-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36a4a-131">範例</span><span class="sxs-lookup"><span data-stu-id="36a4a-131">Example</span></span>  
 <span data-ttu-id="36a4a-132">下列範例示範如何指定最短的新時間（六個小時）、兩天的最長存留期，以及最大過時時間（四小時）。</span><span class="sxs-lookup"><span data-stu-id="36a4a-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36a4a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36a4a-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="36a4a-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="36a4a-134">Network Settings Schema</span></span>](index.md)
