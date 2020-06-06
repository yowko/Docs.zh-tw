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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088433"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="faf02-102">\<defaultFtpCachePolicy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="faf02-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="faf02-103">描述 FTP 快取是否作用中，並描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="faf02-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="faf02-104">語法</span><span class="sxs-lookup"><span data-stu-id="faf02-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faf02-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="faf02-105">Attributes and Elements</span></span>  
 <span data-ttu-id="faf02-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="faf02-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faf02-107">屬性</span><span class="sxs-lookup"><span data-stu-id="faf02-107">Attributes</span></span>  
  
|<span data-ttu-id="faf02-108">屬性</span><span class="sxs-lookup"><span data-stu-id="faf02-108">Attribute</span></span>|<span data-ttu-id="faf02-109">描述</span><span class="sxs-lookup"><span data-stu-id="faf02-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="faf02-110">指定 FTP 快取原則。</span><span class="sxs-lookup"><span data-stu-id="faf02-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="faf02-111">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="faf02-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="faf02-112">policyLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="faf02-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="faf02-113">值</span><span class="sxs-lookup"><span data-stu-id="faf02-113">Value</span></span>|<span data-ttu-id="faf02-114">描述</span><span class="sxs-lookup"><span data-stu-id="faf02-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="faf02-115">如果資源是最新的，則會傳回快取的資源、內容長度是正確的，而且會顯示到期、修改和內容長度屬性。</span><span class="sxs-lookup"><span data-stu-id="faf02-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="faf02-116">傳回伺服器的資源。</span><span class="sxs-lookup"><span data-stu-id="faf02-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="faf02-117">如果內容長度存在且符合專案大小，則傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="faf02-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="faf02-118">如果提供內容長度且符合專案大小，則傳回快取的資源;否則，資源會從伺服器下載並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="faf02-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="faf02-119">如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取的資源;否則，資源會從伺服器下載、儲存在快取中，然後傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="faf02-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="faf02-120">從伺服器下載資源、將它儲存在快取中，然後將資源傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="faf02-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="faf02-121">如果快取的資源已存在，則會予以刪除。</span><span class="sxs-lookup"><span data-stu-id="faf02-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="faf02-122">資源會從伺服器下載，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="faf02-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="faf02-123">如果時間戳記與伺服器上資源的時間戳記相同，則使用資源的快取複本滿足要求，否則，會從伺服器下載該資源，將其呈現給呼叫端，並儲存在快取中。</span><span class="sxs-lookup"><span data-stu-id="faf02-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="faf02-124">子元素</span><span class="sxs-lookup"><span data-stu-id="faf02-124">Child Elements</span></span>  
 <span data-ttu-id="faf02-125">無。</span><span class="sxs-lookup"><span data-stu-id="faf02-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="faf02-126">父項目</span><span class="sxs-lookup"><span data-stu-id="faf02-126">Parent Elements</span></span>  
  
|<span data-ttu-id="faf02-127">元素</span><span class="sxs-lookup"><span data-stu-id="faf02-127">Element</span></span>|<span data-ttu-id="faf02-128">描述</span><span class="sxs-lookup"><span data-stu-id="faf02-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faf02-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="faf02-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="faf02-130">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="faf02-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faf02-131">備註</span><span class="sxs-lookup"><span data-stu-id="faf02-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="faf02-132">範例</span><span class="sxs-lookup"><span data-stu-id="faf02-132">Example</span></span>  
 <span data-ttu-id="faf02-133">下列範例顯示如何指定的 FTP 快取原則 `NoCacheNoStore` 。</span><span class="sxs-lookup"><span data-stu-id="faf02-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="faf02-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faf02-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="faf02-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="faf02-135">Network Settings Schema</span></span>](index.md)
