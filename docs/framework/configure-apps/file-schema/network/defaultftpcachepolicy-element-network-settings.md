---
title: "&lt;defaultFtpCachePolicy&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6b9a5fb2f62c27d278570ad789deab30917bc432
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="da3aa-102">&lt;defaultFtpCachePolicy&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="da3aa-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="da3aa-103">描述 FTP 快取是否作用中，並且描述預設的快取原則。</span><span class="sxs-lookup"><span data-stu-id="da3aa-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="da3aa-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="da3aa-104">\<configuration></span></span>  
<span data-ttu-id="da3aa-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="da3aa-105">\<system.net></span></span>  
<span data-ttu-id="da3aa-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="da3aa-106">\<requestCaching></span></span>  
<span data-ttu-id="da3aa-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="da3aa-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da3aa-108">語法</span><span class="sxs-lookup"><span data-stu-id="da3aa-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da3aa-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="da3aa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="da3aa-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="da3aa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da3aa-111">屬性</span><span class="sxs-lookup"><span data-stu-id="da3aa-111">Attributes</span></span>  
  
|<span data-ttu-id="da3aa-112">屬性</span><span class="sxs-lookup"><span data-stu-id="da3aa-112">Attribute</span></span>|<span data-ttu-id="da3aa-113">說明</span><span class="sxs-lookup"><span data-stu-id="da3aa-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="da3aa-114">指定 FTP 快取原則。</span><span class="sxs-lookup"><span data-stu-id="da3aa-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="da3aa-115">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="da3aa-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="da3aa-116">policyLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="da3aa-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="da3aa-117">值</span><span class="sxs-lookup"><span data-stu-id="da3aa-117">Value</span></span>|<span data-ttu-id="da3aa-118">說明</span><span class="sxs-lookup"><span data-stu-id="da3aa-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="da3aa-119">如果資源是新的內容長度正確無誤，，到期、 修改和內容長度屬性會，傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="da3aa-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="da3aa-120">從伺服器傳回的資源。</span><span class="sxs-lookup"><span data-stu-id="da3aa-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="da3aa-121">如果內容的長度且相符的項目大小，則傳回快取的資源。</span><span class="sxs-lookup"><span data-stu-id="da3aa-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="da3aa-122">如果已提供的內容長度，而相符的項目大小;，傳回的快取的資源否則，資源會從伺服器下載，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="da3aa-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="da3aa-123">如果快取資源的時間戳記為相同伺服器上資源的時間戳記會傳回快取的資源否則，資源是從伺服器下載、 儲存在快取，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="da3aa-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="da3aa-124">從伺服器下載的資源、 將它儲存在快取，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="da3aa-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="da3aa-125">如果快取的資源存在，會將其刪除。</span><span class="sxs-lookup"><span data-stu-id="da3aa-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="da3aa-126">資源從伺服器下載，並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="da3aa-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="da3aa-127">如果時間戳記是相同的時間戳記伺服器; 上的資源使用資源的快取的副本滿足要求否則，資源會從伺服器下載，向呼叫者，並儲存在快取。</span><span class="sxs-lookup"><span data-stu-id="da3aa-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da3aa-128">子元素</span><span class="sxs-lookup"><span data-stu-id="da3aa-128">Child Elements</span></span>  
 <span data-ttu-id="da3aa-129">無。</span><span class="sxs-lookup"><span data-stu-id="da3aa-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="da3aa-130">父項目</span><span class="sxs-lookup"><span data-stu-id="da3aa-130">Parent Elements</span></span>  
  
|<span data-ttu-id="da3aa-131">項目</span><span class="sxs-lookup"><span data-stu-id="da3aa-131">Element</span></span>|<span data-ttu-id="da3aa-132">說明</span><span class="sxs-lookup"><span data-stu-id="da3aa-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da3aa-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="da3aa-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="da3aa-134">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="da3aa-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da3aa-135">備註</span><span class="sxs-lookup"><span data-stu-id="da3aa-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="da3aa-136">範例</span><span class="sxs-lookup"><span data-stu-id="da3aa-136">Example</span></span>  
 <span data-ttu-id="da3aa-137">下列範例示範如何指定快取原則的 FTP `NoCacheNoStore`。</span><span class="sxs-lookup"><span data-stu-id="da3aa-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da3aa-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da3aa-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="da3aa-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="da3aa-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
