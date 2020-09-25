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
ms.openlocfilehash: e081882aa8df89c0a1bf5d4c60f1395a3319c417
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190367"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="e8337-102">\<defaultFtpCachePolicy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="e8337-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="e8337-103">描述 FTP 快取是否為作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="e8337-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="e8337-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8337-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8337-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e8337-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e8337-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e8337-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8337-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e8337-107">Attributes</span></span>  
  
|<span data-ttu-id="e8337-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e8337-108">Attribute</span></span>|<span data-ttu-id="e8337-109">描述</span><span class="sxs-lookup"><span data-stu-id="e8337-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="e8337-110">指定 FTP 快取原則。</span><span class="sxs-lookup"><span data-stu-id="e8337-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="e8337-111">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="e8337-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="e8337-112">policyLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="e8337-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="e8337-113">值</span><span class="sxs-lookup"><span data-stu-id="e8337-113">Value</span></span>|<span data-ttu-id="e8337-114">描述</span><span class="sxs-lookup"><span data-stu-id="e8337-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="e8337-115">如果資源是最新的，則傳回快取的資源、內容長度正確，而且存在到期、修改和內容長度屬性。</span><span class="sxs-lookup"><span data-stu-id="e8337-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="e8337-116">從伺服器傳回資源。</span><span class="sxs-lookup"><span data-stu-id="e8337-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="e8337-117">如果內容長度存在且符合專案大小，則傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="e8337-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="e8337-118">如果提供內容長度且符合專案大小，則會傳回快取的資源;否則，就會從伺服器下載資源，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="e8337-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="e8337-119">如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取的資源;否則，就會從伺服器下載資源、儲存在快取中，然後傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="e8337-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="e8337-120">從伺服器下載資源、將它儲存在快取中，然後將資源傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e8337-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="e8337-121">如果有快取的資源存在，則會將其刪除。</span><span class="sxs-lookup"><span data-stu-id="e8337-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="e8337-122">資源會從伺服器下載，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="e8337-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="e8337-123">如果時間戳記與伺服器上資源的時間戳記相同，則使用資源的快取複本滿足要求，否則，會從伺服器下載該資源，將其呈現給呼叫端，並儲存在快取中。</span><span class="sxs-lookup"><span data-stu-id="e8337-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8337-124">子元素</span><span class="sxs-lookup"><span data-stu-id="e8337-124">Child Elements</span></span>  

 <span data-ttu-id="e8337-125">無。</span><span class="sxs-lookup"><span data-stu-id="e8337-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8337-126">父項目</span><span class="sxs-lookup"><span data-stu-id="e8337-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e8337-127">項目</span><span class="sxs-lookup"><span data-stu-id="e8337-127">Element</span></span>|<span data-ttu-id="e8337-128">描述</span><span class="sxs-lookup"><span data-stu-id="e8337-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8337-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="e8337-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="e8337-130">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="e8337-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8337-131">備註</span><span class="sxs-lookup"><span data-stu-id="e8337-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8337-132">範例</span><span class="sxs-lookup"><span data-stu-id="e8337-132">Example</span></span>  

 <span data-ttu-id="e8337-133">下列範例顯示如何指定的 FTP 快取原則 `NoCacheNoStore` 。</span><span class="sxs-lookup"><span data-stu-id="e8337-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8337-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8337-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="e8337-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e8337-135">Network Settings Schema</span></span>](index.md)
