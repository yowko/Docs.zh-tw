---
title: <defaultFtpCachePolicy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088433"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="21a04-102">\<defaultFtpCachePolicy > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="21a04-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="21a04-103">描述 FTP 快取是否作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="21a04-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

<span data-ttu-id="21a04-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="21a04-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="21a04-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="21a04-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="21a04-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestcaching> >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="21a04-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>\
<span data-ttu-id="21a04-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultFtpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="21a04-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="21a04-108">語法</span><span class="sxs-lookup"><span data-stu-id="21a04-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21a04-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="21a04-109">Attributes and Elements</span></span>  
 <span data-ttu-id="21a04-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="21a04-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21a04-111">屬性</span><span class="sxs-lookup"><span data-stu-id="21a04-111">Attributes</span></span>  
  
|<span data-ttu-id="21a04-112">屬性</span><span class="sxs-lookup"><span data-stu-id="21a04-112">Attribute</span></span>|<span data-ttu-id="21a04-113">描述</span><span class="sxs-lookup"><span data-stu-id="21a04-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="21a04-114">指定 FTP 快取原則。</span><span class="sxs-lookup"><span data-stu-id="21a04-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="21a04-115">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="21a04-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="21a04-116">policyLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="21a04-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="21a04-117">值</span><span class="sxs-lookup"><span data-stu-id="21a04-117">Value</span></span>|<span data-ttu-id="21a04-118">描述</span><span class="sxs-lookup"><span data-stu-id="21a04-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="21a04-119">如果資源是最新的，則會傳回快取的資源、內容長度是正確的，而且會顯示到期、修改和內容長度屬性。</span><span class="sxs-lookup"><span data-stu-id="21a04-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="21a04-120">傳回伺服器的資源。</span><span class="sxs-lookup"><span data-stu-id="21a04-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="21a04-121">如果內容長度存在且符合專案大小，則傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="21a04-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="21a04-122">如果提供內容長度且符合專案大小，則傳回快取的資源;否則，資源會從伺服器下載並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="21a04-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="21a04-123">如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取的資源;否則，資源會從伺服器下載、儲存在快取中，然後傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="21a04-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="21a04-124">從伺服器下載資源、將它儲存在快取中，然後將資源傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="21a04-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="21a04-125">如果快取的資源已存在，則會予以刪除。</span><span class="sxs-lookup"><span data-stu-id="21a04-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="21a04-126">資源會從伺服器下載，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="21a04-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="21a04-127">如果時間戳記與伺服器上資源的時間戳記相同，請使用資源的快取複本來滿足要求;否則，資源會從伺服器下載、呈現給呼叫端，並儲存在快取中。</span><span class="sxs-lookup"><span data-stu-id="21a04-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21a04-128">子項目</span><span class="sxs-lookup"><span data-stu-id="21a04-128">Child Elements</span></span>  
 <span data-ttu-id="21a04-129">無。</span><span class="sxs-lookup"><span data-stu-id="21a04-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21a04-130">父項目</span><span class="sxs-lookup"><span data-stu-id="21a04-130">Parent Elements</span></span>  
  
|<span data-ttu-id="21a04-131">項目</span><span class="sxs-lookup"><span data-stu-id="21a04-131">Element</span></span>|<span data-ttu-id="21a04-132">描述</span><span class="sxs-lookup"><span data-stu-id="21a04-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21a04-133">Requestcaching></span><span class="sxs-lookup"><span data-stu-id="21a04-133">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="21a04-134">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="21a04-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21a04-135">備註</span><span class="sxs-lookup"><span data-stu-id="21a04-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="21a04-136">範例</span><span class="sxs-lookup"><span data-stu-id="21a04-136">Example</span></span>  
 <span data-ttu-id="21a04-137">下列範例顯示如何指定 `NoCacheNoStore`的 FTP 快取原則。</span><span class="sxs-lookup"><span data-stu-id="21a04-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21a04-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="21a04-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="21a04-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="21a04-139">Network Settings Schema</span></span>](index.md)
