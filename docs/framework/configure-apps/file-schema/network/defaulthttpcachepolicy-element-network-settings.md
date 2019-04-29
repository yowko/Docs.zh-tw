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
ms.openlocfilehash: 20d9b92ca2bbffd6b98b8641e5cef5e567cb84cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705125"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="0c550-102">\<defaultHttpCachePolicy > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="0c550-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="0c550-103">描述 HTTP 快取是否作用中，並且描述的預設快取原則。</span><span class="sxs-lookup"><span data-stu-id="0c550-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="0c550-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0c550-104">\<configuration></span></span>  
<span data-ttu-id="0c550-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0c550-105">\<system.net></span></span>  
<span data-ttu-id="0c550-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="0c550-106">\<requestCaching></span></span>  
<span data-ttu-id="0c550-107">\<defaultHttpCachePolicy></span><span class="sxs-lookup"><span data-stu-id="0c550-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c550-108">語法</span><span class="sxs-lookup"><span data-stu-id="0c550-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c550-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c550-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0c550-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0c550-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c550-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0c550-111">Attributes</span></span>  
  
|<span data-ttu-id="0c550-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0c550-112">Attribute</span></span>|<span data-ttu-id="0c550-113">描述</span><span class="sxs-lookup"><span data-stu-id="0c550-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="0c550-114">快取的物件會標示為過期之前，請指定最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0c550-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="0c550-115">指定超過所計算的最近時間，才會快取的物件標示為已過期的時間上限。</span><span class="sxs-lookup"><span data-stu-id="0c550-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="0c550-116">指定要被視為有效的快取物件的最小時間。</span><span class="sxs-lookup"><span data-stu-id="0c550-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="0c550-117">指定是否快取原則會自動進行，或是否略過快取。</span><span class="sxs-lookup"><span data-stu-id="0c550-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="0c550-118">預設值為 `BypassCache`。</span><span class="sxs-lookup"><span data-stu-id="0c550-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c550-119">子元素</span><span class="sxs-lookup"><span data-stu-id="0c550-119">Child Elements</span></span>  
 <span data-ttu-id="0c550-120">None</span><span class="sxs-lookup"><span data-stu-id="0c550-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c550-121">父項目</span><span class="sxs-lookup"><span data-stu-id="0c550-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0c550-122">項目</span><span class="sxs-lookup"><span data-stu-id="0c550-122">Element</span></span>|<span data-ttu-id="0c550-123">描述</span><span class="sxs-lookup"><span data-stu-id="0c550-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c550-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="0c550-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="0c550-125">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="0c550-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c550-126">備註</span><span class="sxs-lookup"><span data-stu-id="0c550-126">Remarks</span></span>  
 <span data-ttu-id="0c550-127">值`policyLevel`屬性是`BypassCache`或`Default`。</span><span class="sxs-lookup"><span data-stu-id="0c550-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="0c550-128">值`maximumAge`， `maximumStale`，並`minimumFresh`項目所使用的格式可能是明確的時間間隔*d*。*hh*:*公釐*:*ss* （天、 小時、 分鐘和秒為單位），或常數`minValue`或`maxValue`視需要。</span><span class="sxs-lookup"><span data-stu-id="0c550-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0c550-129">組態檔</span><span class="sxs-lookup"><span data-stu-id="0c550-129">Configuration Files</span></span>  
 <span data-ttu-id="0c550-130">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="0c550-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c550-131">範例</span><span class="sxs-lookup"><span data-stu-id="0c550-131">Example</span></span>  
 <span data-ttu-id="0c550-132">下列範例示範如何指定最小全新六小時，最長使用期限時間為兩天，以及最大過時四個小時的時間。</span><span class="sxs-lookup"><span data-stu-id="0c550-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c550-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c550-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="0c550-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0c550-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
