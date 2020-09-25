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
ms.openlocfilehash: 3eb32b7ae643efdb19892410b669c1e7ff80e0ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174156"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="b50d8-102">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="b50d8-102">\<requestCaching> Element (Network Settings)</span></span>

<span data-ttu-id="b50d8-103">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="b50d8-103">Controls the caching mechanism for network requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a><span data-ttu-id="b50d8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b50d8-104">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b50d8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b50d8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b50d8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b50d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b50d8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b50d8-107">Attributes</span></span>  
  
|<span data-ttu-id="b50d8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b50d8-108">Attribute</span></span>|<span data-ttu-id="b50d8-109">描述</span><span class="sxs-lookup"><span data-stu-id="b50d8-109">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="b50d8-110">指定快取是否提供不同使用者資訊之間的隔離。</span><span class="sxs-lookup"><span data-stu-id="b50d8-110">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="b50d8-111">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="b50d8-111">The default value is `true`.</span></span> <span data-ttu-id="b50d8-112">`false`中介層應用程式的這個值應該是。</span><span class="sxs-lookup"><span data-stu-id="b50d8-112">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="b50d8-113">指定停用所有 Web 回應的快取，而且無法以程式設計方式覆寫。</span><span class="sxs-lookup"><span data-stu-id="b50d8-113">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="b50d8-114"><xref:System.Net.Cache.RequestCacheLevel> 列舉中的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="b50d8-114">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="b50d8-115">預設值是 `BypassCache`。</span><span class="sxs-lookup"><span data-stu-id="b50d8-115">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="b50d8-116">指定將內容標示為已過期的預設時間。</span><span class="sxs-lookup"><span data-stu-id="b50d8-116">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="b50d8-117">policyLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="b50d8-117">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="b50d8-118">值</span><span class="sxs-lookup"><span data-stu-id="b50d8-118">Value</span></span>|<span data-ttu-id="b50d8-119">描述</span><span class="sxs-lookup"><span data-stu-id="b50d8-119">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="b50d8-120">如果資源是最新的，則傳回快取的資源、內容長度正確，而且存在到期、修改和內容長度屬性。</span><span class="sxs-lookup"><span data-stu-id="b50d8-120">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="b50d8-121">從伺服器傳回資源。</span><span class="sxs-lookup"><span data-stu-id="b50d8-121">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="b50d8-122">如果內容長度存在且符合專案大小，則傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="b50d8-122">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="b50d8-123">如果提供內容長度且符合專案大小，則會傳回快取的資源;否則，就會從伺服器下載資源，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b50d8-123">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="b50d8-124">如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取的資源;否則，資源會從伺服器下載，儲存在快取中，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b50d8-124">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="b50d8-125">從伺服器下載資源、將它儲存在快取中，然後將資源傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="b50d8-125">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="b50d8-126">如果有快取的資源存在，則會將其刪除。</span><span class="sxs-lookup"><span data-stu-id="b50d8-126">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="b50d8-127">資源會從伺服器下載，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b50d8-127">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="b50d8-128">如果時間戳記與伺服器上資源的時間戳記相同，請使用資源的快取複本來滿足要求;否則，就會從伺服器下載資源、向呼叫端顯示資源，然後儲存在快取中。</span><span class="sxs-lookup"><span data-stu-id="b50d8-128">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b50d8-129">子元素</span><span class="sxs-lookup"><span data-stu-id="b50d8-129">Child Elements</span></span>  
  
|<span data-ttu-id="b50d8-130">項目</span><span class="sxs-lookup"><span data-stu-id="b50d8-130">Element</span></span>|<span data-ttu-id="b50d8-131">描述</span><span class="sxs-lookup"><span data-stu-id="b50d8-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b50d8-132">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="b50d8-132">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="b50d8-133">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b50d8-133">Optional element.</span></span><br /><br /> <span data-ttu-id="b50d8-134">描述 HTTP 快取是否為作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="b50d8-134">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="b50d8-135">\<defaultFtpCachePolicy> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="b50d8-135">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="b50d8-136">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b50d8-136">Optional element.</span></span><br /><br /> <span data-ttu-id="b50d8-137">描述 FTP 快取是否為作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="b50d8-137">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b50d8-138">父項目</span><span class="sxs-lookup"><span data-stu-id="b50d8-138">Parent Elements</span></span>  
  
|<span data-ttu-id="b50d8-139">項目</span><span class="sxs-lookup"><span data-stu-id="b50d8-139">Element</span></span>|<span data-ttu-id="b50d8-140">描述</span><span class="sxs-lookup"><span data-stu-id="b50d8-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b50d8-141">system.net</span><span class="sxs-lookup"><span data-stu-id="b50d8-141">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b50d8-142">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="b50d8-142">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b50d8-143">範例</span><span class="sxs-lookup"><span data-stu-id="b50d8-143">Example</span></span>  

 <span data-ttu-id="b50d8-144">下列範例顯示如何停用所有快取。</span><span class="sxs-lookup"><span data-stu-id="b50d8-144">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b50d8-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b50d8-145">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="b50d8-146">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b50d8-146">Network Settings Schema</span></span>](index.md)
