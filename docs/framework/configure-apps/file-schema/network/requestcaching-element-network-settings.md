---
title: <requestCaching> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697831"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="a8240-102">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="a8240-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="a8240-103">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="a8240-103">Controls the caching mechanism for network requests.</span></span>  
  
[<span data-ttu-id="a8240-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a8240-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a8240-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a8240-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="a8240-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requestCaching >**</span><span class="sxs-lookup"><span data-stu-id="a8240-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8240-107">語法</span><span class="sxs-lookup"><span data-stu-id="a8240-107">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8240-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8240-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a8240-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a8240-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8240-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a8240-110">Attributes</span></span>  
  
|<span data-ttu-id="a8240-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a8240-111">Attribute</span></span>|<span data-ttu-id="a8240-112">描述</span><span class="sxs-lookup"><span data-stu-id="a8240-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="a8240-113">指定快取是否在不同使用者的資訊之間提供隔離。</span><span class="sxs-lookup"><span data-stu-id="a8240-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="a8240-114">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a8240-114">The default value is `true`.</span></span> <span data-ttu-id="a8240-115">中介層應用程式的這個值應該 `false`。</span><span class="sxs-lookup"><span data-stu-id="a8240-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="a8240-116">指定停用所有 Web 回應的快取，而且無法以程式設計方式覆寫。</span><span class="sxs-lookup"><span data-stu-id="a8240-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="a8240-117"><xref:System.Net.Cache.RequestCacheLevel> 列舉中的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="a8240-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="a8240-118">預設值為 `BypassCache`。</span><span class="sxs-lookup"><span data-stu-id="a8240-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="a8240-119">指定將內容標示為過期的預設時間。</span><span class="sxs-lookup"><span data-stu-id="a8240-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="a8240-120">policyLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="a8240-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="a8240-121">值</span><span class="sxs-lookup"><span data-stu-id="a8240-121">Value</span></span>|<span data-ttu-id="a8240-122">描述</span><span class="sxs-lookup"><span data-stu-id="a8240-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="a8240-123">如果資源是最新的，則會傳回快取的資源、內容長度是正確的，而且會顯示到期、修改和內容長度屬性。</span><span class="sxs-lookup"><span data-stu-id="a8240-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="a8240-124">傳回伺服器的資源。</span><span class="sxs-lookup"><span data-stu-id="a8240-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="a8240-125">如果內容長度存在且符合專案大小，則傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="a8240-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="a8240-126">如果提供內容長度且符合專案大小，則傳回快取的資源;否則，資源會從伺服器下載並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="a8240-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="a8240-127">如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取的資源;否則，資源會從伺服器下載並儲存在快取中，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="a8240-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="a8240-128">從伺服器下載資源、將它儲存在快取中，然後將資源傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="a8240-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="a8240-129">如果快取的資源已存在，則會予以刪除。</span><span class="sxs-lookup"><span data-stu-id="a8240-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="a8240-130">資源會從伺服器下載，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="a8240-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="a8240-131">如果時間戳記與伺服器上資源的時間戳記相同，請使用資源的快取複本來滿足要求;否則，資源會從伺服器下載、呈現給呼叫端，並儲存在快取中。</span><span class="sxs-lookup"><span data-stu-id="a8240-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8240-132">子元素</span><span class="sxs-lookup"><span data-stu-id="a8240-132">Child Elements</span></span>  
  
|<span data-ttu-id="a8240-133">元素</span><span class="sxs-lookup"><span data-stu-id="a8240-133">Element</span></span>|<span data-ttu-id="a8240-134">描述</span><span class="sxs-lookup"><span data-stu-id="a8240-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8240-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="a8240-135">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="a8240-136">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a8240-136">Optional element.</span></span><br /><br /> <span data-ttu-id="a8240-137">描述 HTTP 快取是否作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="a8240-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="a8240-138">@no__t 1defaultFtpCachePolicy > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="a8240-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="a8240-139">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a8240-139">Optional element.</span></span><br /><br /> <span data-ttu-id="a8240-140">描述 FTP 快取是否作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="a8240-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8240-141">父項目</span><span class="sxs-lookup"><span data-stu-id="a8240-141">Parent Elements</span></span>  
  
|<span data-ttu-id="a8240-142">項目</span><span class="sxs-lookup"><span data-stu-id="a8240-142">Element</span></span>|<span data-ttu-id="a8240-143">描述</span><span class="sxs-lookup"><span data-stu-id="a8240-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8240-144">system.net</span><span class="sxs-lookup"><span data-stu-id="a8240-144">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="a8240-145">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="a8240-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a8240-146">範例</span><span class="sxs-lookup"><span data-stu-id="a8240-146">Example</span></span>  
 <span data-ttu-id="a8240-147">下列範例顯示如何停用所有快取。</span><span class="sxs-lookup"><span data-stu-id="a8240-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8240-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8240-148">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="a8240-149">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a8240-149">Network Settings Schema</span></span>](index.md)
