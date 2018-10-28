---
title: '&lt;Requestcaching>&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: fecb3c71e0686a557b8a4b0c85b7d91a9846204f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194965"
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="6c182-102">&lt;Requestcaching>&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="6c182-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6c182-103">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="6c182-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="6c182-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6c182-104">\<configuration></span></span>  
<span data-ttu-id="6c182-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6c182-105">\<system.net></span></span>  
<span data-ttu-id="6c182-106">\<Requestcaching> ></span><span class="sxs-lookup"><span data-stu-id="6c182-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c182-107">語法</span><span class="sxs-lookup"><span data-stu-id="6c182-107">Syntax</span></span>  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c182-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6c182-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6c182-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6c182-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c182-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6c182-110">Attributes</span></span>  
  
|<span data-ttu-id="6c182-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6c182-111">Attribute</span></span>|<span data-ttu-id="6c182-112">描述</span><span class="sxs-lookup"><span data-stu-id="6c182-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="6c182-113">指定是否快取之間提供隔離不同使用者的資訊。</span><span class="sxs-lookup"><span data-stu-id="6c182-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="6c182-114">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="6c182-114">The default value is `true`.</span></span> <span data-ttu-id="6c182-115">這個值應該是`false`中介層應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c182-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="6c182-116">指定，快取已停用所有的 Web 回應，而且不能以程式設計方式覆寫。</span><span class="sxs-lookup"><span data-stu-id="6c182-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="6c182-117"><xref:System.Net.Cache.RequestCacheLevel> 列舉中的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="6c182-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="6c182-118">預設值是 `BypassCache`。</span><span class="sxs-lookup"><span data-stu-id="6c182-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="6c182-119">指定預設的時間之後，內容會標示為已過期。</span><span class="sxs-lookup"><span data-stu-id="6c182-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="6c182-120">Securityclasses 屬性</span><span class="sxs-lookup"><span data-stu-id="6c182-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="6c182-121">值</span><span class="sxs-lookup"><span data-stu-id="6c182-121">Value</span></span>|<span data-ttu-id="6c182-122">描述</span><span class="sxs-lookup"><span data-stu-id="6c182-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="6c182-123">如果資源是新的、 內容長度正確無誤，且到期、 修改和內容長度屬性都存在，則會傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="6c182-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="6c182-124">從伺服器傳回的資源。</span><span class="sxs-lookup"><span data-stu-id="6c182-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="6c182-125">如果內容長度，且符合項目大小，則會傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="6c182-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="6c182-126">如果內容長度提供，且符合項目大小; 會傳回快取的資源否則，資源從伺服器下載，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="6c182-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="6c182-127">如果快取的資源的時間戳記是伺服器上之資源的時間戳記相同，會傳回快取的資源否則資源下載自伺服器，並儲存在快取，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="6c182-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="6c182-128">從伺服器下載的資源、 將它儲存在快取，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="6c182-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="6c182-129">如果快取的資源存在，則會將它刪除。</span><span class="sxs-lookup"><span data-stu-id="6c182-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="6c182-130">資源從伺服器下載，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="6c182-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="6c182-131">如果時間戳記伺服器上之資源的時間戳記相同，使用資源的快取的複本滿足要求否則資源下載自伺服器，向呼叫端，並會儲存在快取中，</span><span class="sxs-lookup"><span data-stu-id="6c182-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c182-132">子元素</span><span class="sxs-lookup"><span data-stu-id="6c182-132">Child Elements</span></span>  
  
|<span data-ttu-id="6c182-133">項目</span><span class="sxs-lookup"><span data-stu-id="6c182-133">Element</span></span>|<span data-ttu-id="6c182-134">描述</span><span class="sxs-lookup"><span data-stu-id="6c182-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c182-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="6c182-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="6c182-136">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="6c182-136">Optional element.</span></span><br /><br /> <span data-ttu-id="6c182-137">描述 HTTP 快取是否作用中，並且描述的預設快取原則。</span><span class="sxs-lookup"><span data-stu-id="6c182-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="6c182-138">\<defaultFtpCachePolicy > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="6c182-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="6c182-139">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="6c182-139">Optional element.</span></span><br /><br /> <span data-ttu-id="6c182-140">描述 FTP 快取是否作用中，並且描述的預設快取原則。</span><span class="sxs-lookup"><span data-stu-id="6c182-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c182-141">父項目</span><span class="sxs-lookup"><span data-stu-id="6c182-141">Parent Elements</span></span>  
  
|<span data-ttu-id="6c182-142">項目</span><span class="sxs-lookup"><span data-stu-id="6c182-142">Element</span></span>|<span data-ttu-id="6c182-143">描述</span><span class="sxs-lookup"><span data-stu-id="6c182-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c182-144">system.net</span><span class="sxs-lookup"><span data-stu-id="6c182-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="6c182-145">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="6c182-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c182-146">範例</span><span class="sxs-lookup"><span data-stu-id="6c182-146">Example</span></span>  
 <span data-ttu-id="6c182-147">下列範例示範如何停用所有快取。</span><span class="sxs-lookup"><span data-stu-id="6c182-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c182-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c182-148">See Also</span></span>  
- <xref:System.Net.Cache?displayProperty=nameWithType>  
- [<span data-ttu-id="6c182-149">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6c182-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
