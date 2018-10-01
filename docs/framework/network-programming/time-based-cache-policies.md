---
title: 以時間為基礎的快取原則
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d24fa2ece34d20a3d9e8d6f971eebae5da0f496e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198081"
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="0b9e0-102">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="0b9e0-102">Time-Based Cache Policies</span></span>
<span data-ttu-id="0b9e0-103">以時間為基礎的快取原則會使用擷取資源的時間、與資源一起傳回的標頭，以及目前時間，定義快取項目的有效期限。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-103">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="0b9e0-104">設定以時間為基礎的快取原則時，您可以使用 <xref:System.Net.Cache.HttpRequestCacheLevel.Default> 時間基礎原則，或建立自訂的時間基礎原則。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-104">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="0b9e0-105">為使用超文字傳輸通訊協定 (HTTP) 取得的資源，使用以時間為基礎的預設原則時，確切的快取行為是由快取回應中包含的標頭，以及 RFC 2616 的 13 與 14 一節中所指定的行為來決定，RFC 2616 可在 [http://www.ietf.org](http://www.ietf.org/) 中取得。如需示範如何為 HTTP 資源設定以時間為基礎之預設原則的程式碼範例，請參閱[如何：為應用程式設定以時間為基礎的預設快取原則](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-105">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="0b9e0-106">如需示範如何建立和使用快取原則的程式碼範例，請參閱[設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-106">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="0b9e0-107">判斷快取項目有效期限的準則</span><span class="sxs-lookup"><span data-stu-id="0b9e0-107">Criteria to Determine Freshness of Cached Entries</span></span>  
 <span data-ttu-id="0b9e0-108">若要自訂以時間為基礎的快取原則，您可以指定要使用下列一或多個準則來判斷快取項目的有效期限：</span><span class="sxs-lookup"><span data-stu-id="0b9e0-108">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
-   <span data-ttu-id="0b9e0-109">最長使用期限</span><span class="sxs-lookup"><span data-stu-id="0b9e0-109">Maximum age</span></span>  
  
-   <span data-ttu-id="0b9e0-110">最長過時</span><span class="sxs-lookup"><span data-stu-id="0b9e0-110">Maximum staleness</span></span>  
  
-   <span data-ttu-id="0b9e0-111">最短有效期限</span><span class="sxs-lookup"><span data-stu-id="0b9e0-111">Minimum freshness</span></span>  
  
-   <span data-ttu-id="0b9e0-112">快取同步處理日期</span><span class="sxs-lookup"><span data-stu-id="0b9e0-112">Cache synchronization date</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b9e0-113">使用時間為基礎的預設快取原則不應與設定應用程式的預設快取原則混淆。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-113">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="0b9e0-114">以時間為基礎的預設原則是可以用於要求或應用程式層級的特定原則。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-114">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="0b9e0-115">應用程式的預設快取原則是在要求上未設定原則時生效的原則 (以位置為基礎或以時間為基礎)。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-115">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="0b9e0-116">如需設定應用程式之預設快取原則的詳細資料，請參閱<xref:System.Net.WebRequest.DefaultCachePolicy%2A>。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-116">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="0b9e0-117">最長使用期限</span><span class="sxs-lookup"><span data-stu-id="0b9e0-117">Maximum Age</span></span>  
 <span data-ttu-id="0b9e0-118">最長使用期限原則準則指定可以使用資源快取複本的時間量。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-118">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="0b9e0-119">如果資源的快取複本超過指定的時間量，則必須藉由針對伺服器上的內容檢查資源，來重新驗證資源。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-119">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="0b9e0-120">如果最長使用期限允許在資源到期後還使用它，則除非同時指定最長過時值，否則不會採用此準則。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-120">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="0b9e0-121">最長過時</span><span class="sxs-lookup"><span data-stu-id="0b9e0-121">Maximum Staleness</span></span>  
 <span data-ttu-id="0b9e0-122">最長過時原則準則指定在可以使用資源的快取複本，且在內容到期日之後的時間長度。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-122">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="0b9e0-123">這是唯一允許在資源過期之後仍使用資源的快取原則準則。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-123">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="0b9e0-124">最短有效期限</span><span class="sxs-lookup"><span data-stu-id="0b9e0-124">Minimum Freshness</span></span>  
 <span data-ttu-id="0b9e0-125">最短有效期限原則準則指定在可以使用資源的快取複本，且在內容到期日之前的時間長度。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-125">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="0b9e0-126">此原則的效果會使快取項目在它的到期日之前便過期，因此最短有效期限和最長過時設定兩者互斥。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-126">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="0b9e0-127">快取同步處理日期</span><span class="sxs-lookup"><span data-stu-id="0b9e0-127">Cache Synchronization Date</span></span>  
 <span data-ttu-id="0b9e0-128">快取同步處理日期原則準則會藉由針對伺服器上的內容檢查資源的快取複本，判斷它何時必須重新驗證。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-128">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="0b9e0-129">如果項目快取後內容已變更，則會從伺服器擷取它、儲存在快取，並傳回到應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-129">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="0b9e0-130">如果內容未變更，其時間戳記會更新，且應用程式會取得快取的內容。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-130">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="0b9e0-131">快取同步處理日期可讓您指定必須重新驗證快取內容的絕對日期。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-131">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="0b9e0-132">如果新的快取項目上次重新驗證是在快取同步處理日期之前，仍會發生與伺服器的重新驗證。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-132">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="0b9e0-133">如果快取項目重新驗證是在快取同步處理日期之後，而且沒有其他有效期限或伺服器重新驗證需求使快取項目失效，則會使用來自快取的項目。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-133">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="0b9e0-134">如果快取同步處理日期設定為未來的日期，則每次要求時都會重新驗證項目，直到快取同步處理日期已過為止。</span><span class="sxs-lookup"><span data-stu-id="0b9e0-134">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="0b9e0-135">下列主題提供結合以時間為基礎之快取原則準則的影響資訊：</span><span class="sxs-lookup"><span data-stu-id="0b9e0-135">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
-   [<span data-ttu-id="0b9e0-136">快取原則互動 — 最長使用期限和最長過時</span><span class="sxs-lookup"><span data-stu-id="0b9e0-136">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [<span data-ttu-id="0b9e0-137">快取原則互動 - 最長使用期限和最小有效期限</span><span class="sxs-lookup"><span data-stu-id="0b9e0-137">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b9e0-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b9e0-138">See Also</span></span>  
 [<span data-ttu-id="0b9e0-139">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="0b9e0-139">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="0b9e0-140">快取原則</span><span class="sxs-lookup"><span data-stu-id="0b9e0-140">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="0b9e0-141">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="0b9e0-141">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="0b9e0-142">設定網路應用程式的快取功能</span><span class="sxs-lookup"><span data-stu-id="0b9e0-142">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="0b9e0-143">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="0b9e0-143">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
