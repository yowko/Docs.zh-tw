---
title: '&lt;defaultFtpCachePolicy&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e03fb02bd351058c1fcdedb8367d03318418a12c
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316437"
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="8f638-102">&lt;defaultFtpCachePolicy&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="8f638-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8f638-103">描述 FTP 快取是否作用中，並且描述的預設快取原則。</span><span class="sxs-lookup"><span data-stu-id="8f638-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="8f638-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8f638-104">\<configuration></span></span>  
<span data-ttu-id="8f638-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8f638-105">\<system.net></span></span>  
<span data-ttu-id="8f638-106">\<Requestcaching> ></span><span class="sxs-lookup"><span data-stu-id="8f638-106">\<requestCaching></span></span>  
<span data-ttu-id="8f638-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="8f638-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f638-108">語法</span><span class="sxs-lookup"><span data-stu-id="8f638-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f638-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8f638-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8f638-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8f638-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f638-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8f638-111">Attributes</span></span>  
  
|<span data-ttu-id="8f638-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8f638-112">Attribute</span></span>|<span data-ttu-id="8f638-113">描述</span><span class="sxs-lookup"><span data-stu-id="8f638-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="8f638-114">指定 FTP 快取原則。</span><span class="sxs-lookup"><span data-stu-id="8f638-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="8f638-115">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="8f638-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="8f638-116">Securityclasses 屬性</span><span class="sxs-lookup"><span data-stu-id="8f638-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="8f638-117">值</span><span class="sxs-lookup"><span data-stu-id="8f638-117">Value</span></span>|<span data-ttu-id="8f638-118">描述</span><span class="sxs-lookup"><span data-stu-id="8f638-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="8f638-119">如果資源是新的、 內容長度正確無誤，且到期、 修改和內容長度屬性都存在，則會傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="8f638-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="8f638-120">從伺服器傳回的資源。</span><span class="sxs-lookup"><span data-stu-id="8f638-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="8f638-121">如果內容長度，且符合項目大小，則會傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="8f638-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="8f638-122">如果內容長度提供，且符合項目大小; 會傳回快取的資源否則，資源從伺服器下載，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="8f638-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="8f638-123">如果快取的資源的時間戳記是伺服器上之資源的時間戳記相同，會傳回快取的資源否則為資源是從伺服器下載、 儲存在快取，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="8f638-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="8f638-124">從伺服器下載的資源、 將它儲存在快取，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="8f638-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="8f638-125">如果快取的資源存在，則會將它刪除。</span><span class="sxs-lookup"><span data-stu-id="8f638-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="8f638-126">資源從伺服器下載，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="8f638-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="8f638-127">如果時間戳記伺服器上之資源的時間戳記相同，使用資源的快取的複本滿足要求否則，資源是從伺服器下載、 呈現給呼叫者，和存放在快取。</span><span class="sxs-lookup"><span data-stu-id="8f638-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f638-128">子元素</span><span class="sxs-lookup"><span data-stu-id="8f638-128">Child Elements</span></span>  
 <span data-ttu-id="8f638-129">無。</span><span class="sxs-lookup"><span data-stu-id="8f638-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f638-130">父項目</span><span class="sxs-lookup"><span data-stu-id="8f638-130">Parent Elements</span></span>  
  
|<span data-ttu-id="8f638-131">項目</span><span class="sxs-lookup"><span data-stu-id="8f638-131">Element</span></span>|<span data-ttu-id="8f638-132">描述</span><span class="sxs-lookup"><span data-stu-id="8f638-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f638-133">Requestcaching></span><span class="sxs-lookup"><span data-stu-id="8f638-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="8f638-134">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="8f638-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f638-135">備註</span><span class="sxs-lookup"><span data-stu-id="8f638-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f638-136">範例</span><span class="sxs-lookup"><span data-stu-id="8f638-136">Example</span></span>  
 <span data-ttu-id="8f638-137">下列範例示範如何指定快取原則的 FTP `NoCacheNoStore`。</span><span class="sxs-lookup"><span data-stu-id="8f638-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f638-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f638-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="8f638-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8f638-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
