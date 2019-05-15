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
ms.openlocfilehash: 4dc57ae05822a602b4647839da259ca8f469fb82
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613839"
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="1e7e1-102">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="1e7e1-102">Time-Based Cache Policies</span></span>
<span data-ttu-id="1e7e1-103">以時間為基礎的快取原則會使用擷取資源的時間、與資源一起傳回的標頭，以及目前時間，定義快取項目的有效期限。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-103">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="1e7e1-104">設定以時間為基礎的快取原則時，您可以使用 <xref:System.Net.Cache.HttpRequestCacheLevel.Default> 時間基礎原則，或建立自訂的時間基礎原則。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-104">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="1e7e1-105">為使用超文字傳輸通訊協定 (HTTP) 取得的資源，使用以時間為基礎的預設原則時，確切的快取行為是由快取回應中包含的標頭，以及 RFC 2616 的 13 與 14 一節中所指定的行為來，RFC 2616 可在[網際網路工程任務推動小組 (IETF)](https://www.ietf.org/) 網站取得。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-105">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="1e7e1-106">如需程式碼範例來示範如何為 HTTP 資源設定以時間為基礎的預設原則，請參閱[如何：為應用程式設定以時間為基礎的預設快取原則](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-106">For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="1e7e1-107">如需示範如何建立和使用快取原則的程式碼範例，請參閱[設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-107">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="1e7e1-108">判斷快取項目有效期限的準則</span><span class="sxs-lookup"><span data-stu-id="1e7e1-108">Criteria to Determine Freshness of Cached Entries</span></span>  
 <span data-ttu-id="1e7e1-109">若要自訂以時間為基礎的快取原則，您可以指定要使用下列一或多個準則來判斷快取項目的有效期限：</span><span class="sxs-lookup"><span data-stu-id="1e7e1-109">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
- <span data-ttu-id="1e7e1-110">最長使用期限</span><span class="sxs-lookup"><span data-stu-id="1e7e1-110">Maximum age</span></span>  
  
- <span data-ttu-id="1e7e1-111">最長過時</span><span class="sxs-lookup"><span data-stu-id="1e7e1-111">Maximum staleness</span></span>  
  
- <span data-ttu-id="1e7e1-112">最短有效期限</span><span class="sxs-lookup"><span data-stu-id="1e7e1-112">Minimum freshness</span></span>  
  
- <span data-ttu-id="1e7e1-113">快取同步處理日期</span><span class="sxs-lookup"><span data-stu-id="1e7e1-113">Cache synchronization date</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e7e1-114">使用時間為基礎的預設快取原則不應與設定應用程式的預設快取原則混淆。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-114">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="1e7e1-115">以時間為基礎的預設原則是可以用於要求或應用程式層級的特定原則。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-115">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="1e7e1-116">應用程式的預設快取原則是在要求上未設定原則時生效的原則 (以位置為基礎或以時間為基礎)。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-116">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="1e7e1-117">如需設定應用程式之預設快取原則的詳細資料，請參閱<xref:System.Net.WebRequest.DefaultCachePolicy%2A>。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-117">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="1e7e1-118">最長使用期限</span><span class="sxs-lookup"><span data-stu-id="1e7e1-118">Maximum Age</span></span>  
 <span data-ttu-id="1e7e1-119">最長使用期限原則準則指定可以使用資源快取複本的時間量。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-119">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="1e7e1-120">如果資源的快取複本超過指定的時間量，則必須藉由針對伺服器上的內容檢查資源，來重新驗證資源。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-120">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="1e7e1-121">如果最長使用期限允許在資源到期後還使用它，則除非同時指定最長過時值，否則不會採用此準則。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-121">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="1e7e1-122">最長過時</span><span class="sxs-lookup"><span data-stu-id="1e7e1-122">Maximum Staleness</span></span>  
 <span data-ttu-id="1e7e1-123">最長過時原則準則指定在可以使用資源的快取複本，且在內容到期日之後的時間長度。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-123">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="1e7e1-124">這是唯一允許在資源過期之後仍使用資源的快取原則準則。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-124">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="1e7e1-125">最短有效期限</span><span class="sxs-lookup"><span data-stu-id="1e7e1-125">Minimum Freshness</span></span>  
 <span data-ttu-id="1e7e1-126">最短有效期限原則準則指定在可以使用資源的快取複本，且在內容到期日之前的時間長度。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-126">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="1e7e1-127">此原則的效果會使快取項目在它的到期日之前便過期，因此最短有效期限和最長過時設定兩者互斥。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-127">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="1e7e1-128">快取同步處理日期</span><span class="sxs-lookup"><span data-stu-id="1e7e1-128">Cache Synchronization Date</span></span>  
 <span data-ttu-id="1e7e1-129">快取同步處理日期原則準則會藉由針對伺服器上的內容檢查資源的快取複本，判斷它何時必須重新驗證。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-129">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="1e7e1-130">如果項目快取後內容已變更，則會從伺服器擷取它、儲存在快取，並傳回到應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-130">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="1e7e1-131">如果內容未變更，其時間戳記會更新，且應用程式會取得快取的內容。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-131">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="1e7e1-132">快取同步處理日期可讓您指定必須重新驗證快取內容的絕對日期。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-132">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="1e7e1-133">如果新的快取項目上次重新驗證是在快取同步處理日期之前，仍會發生與伺服器的重新驗證。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-133">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="1e7e1-134">如果快取項目重新驗證是在快取同步處理日期之後，而且沒有其他有效期限或伺服器重新驗證需求使快取項目失效，則會使用來自快取的項目。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-134">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="1e7e1-135">如果快取同步處理日期設定為未來的日期，則每次要求時都會重新驗證項目，直到快取同步處理日期已過為止。</span><span class="sxs-lookup"><span data-stu-id="1e7e1-135">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="1e7e1-136">下列主題提供結合以時間為基礎之快取原則準則的影響資訊：</span><span class="sxs-lookup"><span data-stu-id="1e7e1-136">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
- [<span data-ttu-id="1e7e1-137">快取原則互動 — 最長使用期限和最長過時</span><span class="sxs-lookup"><span data-stu-id="1e7e1-137">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [<span data-ttu-id="1e7e1-138">快取原則互動 - 最長使用期限和最小有效期限</span><span class="sxs-lookup"><span data-stu-id="1e7e1-138">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e7e1-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e7e1-139">See also</span></span>

- [<span data-ttu-id="1e7e1-140">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="1e7e1-140">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="1e7e1-141">快取原則</span><span class="sxs-lookup"><span data-stu-id="1e7e1-141">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="1e7e1-142">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="1e7e1-142">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="1e7e1-143">設定網路應用程式的快取功能</span><span class="sxs-lookup"><span data-stu-id="1e7e1-143">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [<span data-ttu-id="1e7e1-144">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="1e7e1-144">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
