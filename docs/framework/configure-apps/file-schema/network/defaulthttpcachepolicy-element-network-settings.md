---
title: '&lt;defaultHttpCachePolicy&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0425711687a2f8b40f2c645e1c478d52b56ad979
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="f1a98-102">&lt;defaultHttpCachePolicy&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="f1a98-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f1a98-103">說明 HTTP 快取是否作用中，並且描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="f1a98-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="f1a98-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f1a98-104">\<configuration></span></span>  
<span data-ttu-id="f1a98-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f1a98-105">\<system.net></span></span>  
<span data-ttu-id="f1a98-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="f1a98-106">\<requestCaching></span></span>  
<span data-ttu-id="f1a98-107">\<defaultHttpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="f1a98-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a98-108">語法</span><span class="sxs-lookup"><span data-stu-id="f1a98-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1a98-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f1a98-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f1a98-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f1a98-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1a98-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f1a98-111">Attributes</span></span>  
  
|<span data-ttu-id="f1a98-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f1a98-112">Attribute</span></span>|<span data-ttu-id="f1a98-113">描述</span><span class="sxs-lookup"><span data-stu-id="f1a98-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="f1a98-114">快取的物件標示為已過期之前，請指定最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f1a98-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="f1a98-115">指定的最長的時間超過快取的物件標示為已過期之前所計算的有效期限時間。</span><span class="sxs-lookup"><span data-stu-id="f1a98-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="f1a98-116">指定要視為有效的快取物件的最小時間。</span><span class="sxs-lookup"><span data-stu-id="f1a98-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="f1a98-117">指定是否快取的原則會自動進行，或是否略過快取。</span><span class="sxs-lookup"><span data-stu-id="f1a98-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="f1a98-118">預設值是 `BypassCache`。</span><span class="sxs-lookup"><span data-stu-id="f1a98-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1a98-119">子項目</span><span class="sxs-lookup"><span data-stu-id="f1a98-119">Child Elements</span></span>  
 <span data-ttu-id="f1a98-120">無</span><span class="sxs-lookup"><span data-stu-id="f1a98-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1a98-121">父項目</span><span class="sxs-lookup"><span data-stu-id="f1a98-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f1a98-122">項目</span><span class="sxs-lookup"><span data-stu-id="f1a98-122">Element</span></span>|<span data-ttu-id="f1a98-123">描述</span><span class="sxs-lookup"><span data-stu-id="f1a98-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1a98-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="f1a98-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="f1a98-125">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="f1a98-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1a98-126">備註</span><span class="sxs-lookup"><span data-stu-id="f1a98-126">Remarks</span></span>  
 <span data-ttu-id="f1a98-127">值`policyLevel`屬性是`BypassCache`或`Default`。</span><span class="sxs-lookup"><span data-stu-id="f1a98-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="f1a98-128">值`maximumAge`， `maximumStale`，和`minimumFresh`項目所使用的格式的其中一個明確的時間間隔*d*。*hh*:*公釐*:*ss* （天數、 時、 分、 秒為單位），或常數`minValue`或`maxValue`視情況。</span><span class="sxs-lookup"><span data-stu-id="f1a98-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f1a98-129">組態檔</span><span class="sxs-lookup"><span data-stu-id="f1a98-129">Configuration Files</span></span>  
 <span data-ttu-id="f1a98-130">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="f1a98-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1a98-131">範例</span><span class="sxs-lookup"><span data-stu-id="f1a98-131">Example</span></span>  
 <span data-ttu-id="f1a98-132">下列範例會示範如何指定新的最小時間，為六小時，最長使用期限時間為兩天和四個小時的最長過時時間。</span><span class="sxs-lookup"><span data-stu-id="f1a98-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1a98-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1a98-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="f1a98-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f1a98-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
