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
ms.openlocfilehash: 4120c57fbb65da1c124414cbe9cfba7ae64388f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190315"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="59451-102">\<defaultHttpCachePolicy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="59451-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="59451-103">描述 HTTP 快取是否為作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="59451-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="59451-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="59451-104">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59451-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="59451-105">Attributes and Elements</span></span>  

 <span data-ttu-id="59451-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="59451-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59451-107">屬性</span><span class="sxs-lookup"><span data-stu-id="59451-107">Attributes</span></span>  
  
|<span data-ttu-id="59451-108">屬性</span><span class="sxs-lookup"><span data-stu-id="59451-108">Attribute</span></span>|<span data-ttu-id="59451-109">描述</span><span class="sxs-lookup"><span data-stu-id="59451-109">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="59451-110">指定快取物件標示為過期之前的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="59451-110">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="59451-111">指定在快取物件標示為過期之前，經過計算的最晚時間之前的最長時間。</span><span class="sxs-lookup"><span data-stu-id="59451-111">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="59451-112">指定將快取物件視為最新的最短時間。</span><span class="sxs-lookup"><span data-stu-id="59451-112">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="59451-113">指定快取原則為自動，還是略過快取。</span><span class="sxs-lookup"><span data-stu-id="59451-113">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="59451-114">預設值是 `BypassCache`。</span><span class="sxs-lookup"><span data-stu-id="59451-114">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59451-115">子元素</span><span class="sxs-lookup"><span data-stu-id="59451-115">Child Elements</span></span>  

 <span data-ttu-id="59451-116">無</span><span class="sxs-lookup"><span data-stu-id="59451-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59451-117">父項目</span><span class="sxs-lookup"><span data-stu-id="59451-117">Parent Elements</span></span>  
  
|<span data-ttu-id="59451-118">項目</span><span class="sxs-lookup"><span data-stu-id="59451-118">Element</span></span>|<span data-ttu-id="59451-119">描述</span><span class="sxs-lookup"><span data-stu-id="59451-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59451-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="59451-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="59451-121">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="59451-121">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59451-122">備註</span><span class="sxs-lookup"><span data-stu-id="59451-122">Remarks</span></span>  

 <span data-ttu-id="59451-123">屬性的值 `policyLevel` 為 `BypassCache` 或 `Default` 。</span><span class="sxs-lookup"><span data-stu-id="59451-123">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="59451-124">、和專案的值 `maximumAge` `maximumStale` `minimumFresh` 都是具有 *d*格式的明確時間間隔。*hh*：*mm*：*ss* (天、小時、分鐘和秒) ，或是常數 `minValue` 或 `maxValue` 。</span><span class="sxs-lookup"><span data-stu-id="59451-124">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="59451-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="59451-125">Configuration Files</span></span>  

 <span data-ttu-id="59451-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="59451-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59451-127">範例</span><span class="sxs-lookup"><span data-stu-id="59451-127">Example</span></span>  

 <span data-ttu-id="59451-128">下列範例示範如何指定最短時間為6小時、兩天的最長存留期時間，以及最長可達四小時的最長時間。</span><span class="sxs-lookup"><span data-stu-id="59451-128">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59451-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59451-129">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="59451-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="59451-130">Network Settings Schema</span></span>](index.md)
