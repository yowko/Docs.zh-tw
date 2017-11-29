---
title: "&lt;requestCaching&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2737e67fe1fe1e33b2600f448b02321f6ce1888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="95e31-102">&lt;requestCaching&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="95e31-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="95e31-103">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="95e31-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="95e31-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="95e31-104">\<configuration></span></span>  
<span data-ttu-id="95e31-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="95e31-105">\<system.net></span></span>  
<span data-ttu-id="95e31-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="95e31-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e31-107">語法</span><span class="sxs-lookup"><span data-stu-id="95e31-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95e31-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="95e31-108">Attributes and Elements</span></span>  
 <span data-ttu-id="95e31-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="95e31-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95e31-110">屬性</span><span class="sxs-lookup"><span data-stu-id="95e31-110">Attributes</span></span>  
  
|<span data-ttu-id="95e31-111">屬性</span><span class="sxs-lookup"><span data-stu-id="95e31-111">Attribute</span></span>|<span data-ttu-id="95e31-112">說明</span><span class="sxs-lookup"><span data-stu-id="95e31-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="95e31-113">指定是否快取之間提供隔離不同使用者的資訊。</span><span class="sxs-lookup"><span data-stu-id="95e31-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="95e31-114">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="95e31-114">The default value is `true`.</span></span> <span data-ttu-id="95e31-115">這個值應該是`false`中介層應用程式。</span><span class="sxs-lookup"><span data-stu-id="95e31-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="95e31-116">指定，快取所有的 Web 回應已停用，而且不能以程式設計方式覆寫。</span><span class="sxs-lookup"><span data-stu-id="95e31-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="95e31-117"><xref:System.Net.Cache.RequestCacheLevel> 列舉中的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="95e31-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="95e31-118">預設值是 `BypassCache`。</span><span class="sxs-lookup"><span data-stu-id="95e31-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="95e31-119">指定預設的時間之後的內容標示為已過期。</span><span class="sxs-lookup"><span data-stu-id="95e31-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="95e31-120">policyLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="95e31-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="95e31-121">值</span><span class="sxs-lookup"><span data-stu-id="95e31-121">Value</span></span>|<span data-ttu-id="95e31-122">說明</span><span class="sxs-lookup"><span data-stu-id="95e31-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="95e31-123">如果資源是新的內容長度正確無誤，，到期、 修改和內容長度屬性會，傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="95e31-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="95e31-124">從伺服器傳回的資源。</span><span class="sxs-lookup"><span data-stu-id="95e31-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="95e31-125">如果內容的長度且相符的項目大小，則傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="95e31-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="95e31-126">如果已提供的內容長度，而相符的項目大小;，傳回的快取的資源否則，資源會從伺服器下載，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="95e31-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="95e31-127">如果快取資源的時間戳記為相同伺服器上資源的時間戳記會傳回快取的資源否則，資源下載自伺服器，並儲存在快取，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="95e31-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="95e31-128">從伺服器下載的資源、 將它儲存在快取，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="95e31-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="95e31-129">如果快取的資源存在，會將其刪除。</span><span class="sxs-lookup"><span data-stu-id="95e31-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="95e31-130">資源從伺服器下載，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="95e31-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="95e31-131">如果時間戳記是相同的時間戳記伺服器; 上的資源使用資源的快取的副本滿足要求否則，會在伺服器上，向呼叫者，從下載資源，以及儲存在快取中，</span><span class="sxs-lookup"><span data-stu-id="95e31-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95e31-132">子元素</span><span class="sxs-lookup"><span data-stu-id="95e31-132">Child Elements</span></span>  
  
|<span data-ttu-id="95e31-133">項目</span><span class="sxs-lookup"><span data-stu-id="95e31-133">Element</span></span>|<span data-ttu-id="95e31-134">說明</span><span class="sxs-lookup"><span data-stu-id="95e31-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95e31-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="95e31-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="95e31-136">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="95e31-136">Optional element.</span></span><br /><br /> <span data-ttu-id="95e31-137">說明 HTTP 快取是否作用中，並且描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="95e31-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="95e31-138">\<defaultFtpCachePolicy > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="95e31-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="95e31-139">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="95e31-139">Optional element.</span></span><br /><br /> <span data-ttu-id="95e31-140">描述 FTP 快取是否作用中，並且描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="95e31-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95e31-141">父項目</span><span class="sxs-lookup"><span data-stu-id="95e31-141">Parent Elements</span></span>  
  
|<span data-ttu-id="95e31-142">項目</span><span class="sxs-lookup"><span data-stu-id="95e31-142">Element</span></span>|<span data-ttu-id="95e31-143">說明</span><span class="sxs-lookup"><span data-stu-id="95e31-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95e31-144">system.net</span><span class="sxs-lookup"><span data-stu-id="95e31-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="95e31-145">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="95e31-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95e31-146">範例</span><span class="sxs-lookup"><span data-stu-id="95e31-146">Example</span></span>  
 <span data-ttu-id="95e31-147">下列範例會示範如何停用所有快取。</span><span class="sxs-lookup"><span data-stu-id="95e31-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95e31-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e31-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="95e31-149">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="95e31-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
