---
title: "以位置為基礎的快取原則"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7a1be9f377f9b241bf46ac67f4f3f08fc5a43821
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="location-based-cache-policies"></a><span data-ttu-id="6169c-102">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="6169c-102">Location-Based Cache Policies</span></span>
<span data-ttu-id="6169c-103">以位置為基礎的快取原則，會根據所要求資源可以使用的位置，定義有效快取項目的有效期限。</span><span class="sxs-lookup"><span data-stu-id="6169c-103">A location-based cache policy defines the freshness of valid cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="6169c-104">如果使用它不違反伺服器指定的重新驗證需求，快取的資源即為有效。</span><span class="sxs-lookup"><span data-stu-id="6169c-104">A cached resource is valid if using it does not does not violate server-specified revalidation requirements.</span></span> <span data-ttu-id="6169c-105">使用 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 類別建構函式可以程式設計方式建立以位置為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="6169c-105">A location-based cache policy is created programmatically by using a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class constructor.</span></span> <span data-ttu-id="6169c-106">以位置為基礎的原則類型，是使用 <xref:System.Net.Cache.RequestCacheLevel> 或 <xref:System.Net.Cache.HttpRequestCacheLevel> 列舉值傳遞至建構函式。</span><span class="sxs-lookup"><span data-stu-id="6169c-106">The type of location-based policy is passed to the constructor using a <xref:System.Net.Cache.RequestCacheLevel> or <xref:System.Net.Cache.HttpRequestCacheLevel> enumeration value.</span></span> <span data-ttu-id="6169c-107">如需建立以位置為基礎之快取原則的程式碼範例，請參閱[如何：為應用程式設定以位置為基礎的快取原則](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6169c-107">For code examples that create location-based cache policies, see [How to: Set a Location-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="6169c-108">下列各節說明超文字傳輸通訊協定 (http 和 https) 資源的每種以位置為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="6169c-108">The following sections explain each type of location-based cache policy for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
## <a name="cache-if-available-policy"></a><span data-ttu-id="6169c-109">可用時快取原則</span><span class="sxs-lookup"><span data-stu-id="6169c-109">Cache If Available Policy</span></span>  
 <span data-ttu-id="6169c-110">如果有效的要求資源位於本機快取，則會使用快取的資源；否則，會向伺服器傳送資源要求。</span><span class="sxs-lookup"><span data-stu-id="6169c-110">If a valid requested resource is in the local cache, the cached resource is used; otherwise, the request for the resource is sent to the server.</span></span> <span data-ttu-id="6169c-111">如果在用戶端與伺服器之間的任何快取中都能取得要求的資源，中繼快取即可滿足要求。</span><span class="sxs-lookup"><span data-stu-id="6169c-111">If the requested resource is available in any cache between the client and the server, the request can be satisfied by an intermediate cache.</span></span>  
  
## <a name="cache-only-policy"></a><span data-ttu-id="6169c-112">僅限快取原則</span><span class="sxs-lookup"><span data-stu-id="6169c-112">Cache Only Policy</span></span>  
 <span data-ttu-id="6169c-113">如果有效的要求資源位在本機快取，則會使用快取的資源。</span><span class="sxs-lookup"><span data-stu-id="6169c-113">If a valid requested resource is in the local cache, the cached resource is used.</span></span> <span data-ttu-id="6169c-114">當指定這個快取原則層級時，如果項目不在本機快取，就會擲回 <xref:System.Net.WebException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6169c-114">When this cache policy level is specified, a <xref:System.Net.WebException> exception is thrown if the item is not in the local cache.</span></span>  
  
## <a name="cache-or-next-cache-only-policy"></a><span data-ttu-id="6169c-115">僅限快取或下一個快取原則</span><span class="sxs-lookup"><span data-stu-id="6169c-115">Cache Or Next Cache Only Policy</span></span>  
 <span data-ttu-id="6169c-116">如果有效的要求資源位在本機快取或區域網路的中繼快取，則會使用快取的資源。</span><span class="sxs-lookup"><span data-stu-id="6169c-116">If a valid requested resource is in the local cache or an intermediate cache on the local area network, the cached resource is used.</span></span> <span data-ttu-id="6169c-117">否則會擲回 <xref:System.Net.WebException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6169c-117">Otherwise, a <xref:System.Net.WebException> exception is thrown.</span></span> <span data-ttu-id="6169c-118">在 HTTP 快取通訊協定中，這是使用 only-if-cached 的快取控制指示詞所達成。</span><span class="sxs-lookup"><span data-stu-id="6169c-118">In the HTTP caching protocol, this is achieved using the only-if-cached cache control directive.</span></span>  
  
## <a name="no-cache-no-store-policy"></a><span data-ttu-id="6169c-119">無快取且無存放區原則</span><span class="sxs-lookup"><span data-stu-id="6169c-119">No Cache No Store Policy</span></span>  
 <span data-ttu-id="6169c-120">要求的資源絕不會從任何快取使用，也絕不會放在任何快取中。</span><span class="sxs-lookup"><span data-stu-id="6169c-120">A requested resource is never used from any cache and is never placed in any cache.</span></span> <span data-ttu-id="6169c-121">如果要求的資源出現在本機快取中，它會被移除。</span><span class="sxs-lookup"><span data-stu-id="6169c-121">If a requested resource is present in the local cache, it is removed.</span></span> <span data-ttu-id="6169c-122">這個原則層級指出也應該移除資源的中繼快取。</span><span class="sxs-lookup"><span data-stu-id="6169c-122">This policy level indicates to intermediate caches that they should also remove the resource.</span></span> <span data-ttu-id="6169c-123">在 HTTP 快取通訊協定中，這是使用 no-store 的快取控制指示詞所達成。</span><span class="sxs-lookup"><span data-stu-id="6169c-123">In the HTTP caching protocol, this is achieved using the no-store cache control directive.</span></span>  
  
## <a name="refresh-policy"></a><span data-ttu-id="6169c-124">重新整理原則</span><span class="sxs-lookup"><span data-stu-id="6169c-124">Refresh Policy</span></span>  
 <span data-ttu-id="6169c-125">如果要求的資源是從伺服器取得，或在本機快取以外的快取中找到，就可以使用。</span><span class="sxs-lookup"><span data-stu-id="6169c-125">A requested resource can be used if it is obtained from the server or found in a cache other than the local cache.</span></span> <span data-ttu-id="6169c-126">在中繼快取滿足要求之前，該快取必須重新向伺服器驗證其快取的項目。</span><span class="sxs-lookup"><span data-stu-id="6169c-126">Before the request can be satisfied by an intermediate cache, that cache must revalidate its cached entry with the server.</span></span> <span data-ttu-id="6169c-127">在 HTTP 快取通訊協定中，這是使用 max-age = 0 的快取控制指示詞和 no-cache Pragma 標頭所達成。</span><span class="sxs-lookup"><span data-stu-id="6169c-127">In the HTTP caching protocol, this is achieved using the max-age = 0 cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="reload-policy"></a><span data-ttu-id="6169c-128">重新載入原則</span><span class="sxs-lookup"><span data-stu-id="6169c-128">Reload Policy</span></span>  
 <span data-ttu-id="6169c-129">必須從伺服器取得要求的資源。</span><span class="sxs-lookup"><span data-stu-id="6169c-129">Requested resources must be obtained from the server.</span></span> <span data-ttu-id="6169c-130">回應可能是儲存在本機快取中。</span><span class="sxs-lookup"><span data-stu-id="6169c-130">The response might be saved in the local cache.</span></span> <span data-ttu-id="6169c-131">在 HTTP 快取通訊協定中，這是使用 no-cache 的快取控制指示詞和 no-cache Pragma 標頭所達成。</span><span class="sxs-lookup"><span data-stu-id="6169c-131">In the HTTP caching protocol, this is achieved using the no-cache cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="revalidate-policy"></a><span data-ttu-id="6169c-132">重新驗證原則</span><span class="sxs-lookup"><span data-stu-id="6169c-132">Revalidate Policy</span></span>  
 <span data-ttu-id="6169c-133">比較快取中的資源複本和伺服器上的複本。</span><span class="sxs-lookup"><span data-stu-id="6169c-133">Compares the copy of the resource in the cache with the copy on the server.</span></span> <span data-ttu-id="6169c-134">如果伺服器上的複本較新，就會用它來滿足要求，並取代快取中的複本。</span><span class="sxs-lookup"><span data-stu-id="6169c-134">If the copy on the server is newer, it is used to satisfy the request and replaces the copy in the cache.</span></span> <span data-ttu-id="6169c-135">如果快取中的複本和伺服器上的版本相同，就使用快取的複本。</span><span class="sxs-lookup"><span data-stu-id="6169c-135">If the copy in the cache is the same as the server copy, the cached copy is used.</span></span> <span data-ttu-id="6169c-136">在 HTTP 快取通訊協定中，使用條件式要求即可達成。</span><span class="sxs-lookup"><span data-stu-id="6169c-136">In the HTTP caching protocol, this is achieved using a conditional request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6169c-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6169c-137">See Also</span></span>  
 [<span data-ttu-id="6169c-138">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="6169c-138">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="6169c-139">快取原則</span><span class="sxs-lookup"><span data-stu-id="6169c-139">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="6169c-140">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="6169c-140">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="6169c-141">設定網路應用程式的快取功能</span><span class="sxs-lookup"><span data-stu-id="6169c-141">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="6169c-142">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="6169c-142">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
