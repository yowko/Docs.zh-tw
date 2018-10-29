---
title: 快取原則互動 — 最長使用期限和最長過時
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: 7a066f403e526c50054b58a099bb7978ef57e74d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181143"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="39ec5-102">快取原則互動 — 最長使用期限和最長過時</span><span class="sxs-lookup"><span data-stu-id="39ec5-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="39ec5-103">為了協助確保將最新內容傳回給用戶端應用程式，用戶端快取原則與伺服器重新驗證需求的互動一律會導致最保守的快取原則。</span><span class="sxs-lookup"><span data-stu-id="39ec5-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="39ec5-104">本主題中的所有範例都會說明在 1 月 1 日快取並在 1 月 4 日到期之資源的快取原則。</span><span class="sxs-lookup"><span data-stu-id="39ec5-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="39ec5-105">在下列範例中，最長過時值 (`maxStale`) 是與最長使用期限 (`maxAge`) 一起使用：</span><span class="sxs-lookup"><span data-stu-id="39ec5-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
-   <span data-ttu-id="39ec5-106">根據 `maxAge` 值，如果快取原則設定 `maxAge` = 5 天，但未指定 `maxStale` 值，則在 1 月 6 日之前可以使用內容。</span><span class="sxs-lookup"><span data-stu-id="39ec5-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="39ec5-107">不過，根據伺服器的重新驗證需求，內容會在 1 月 4 日到期。</span><span class="sxs-lookup"><span data-stu-id="39ec5-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="39ec5-108">因為內容到期日較為保守 (更快)，所以其優先順序高於 `maxAge` 原則。</span><span class="sxs-lookup"><span data-stu-id="39ec5-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="39ec5-109">因此，內容會在 1 月 4 日到期，而且必須重新驗證，即使未達到其最長使用期限也是一樣。</span><span class="sxs-lookup"><span data-stu-id="39ec5-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
-   <span data-ttu-id="39ec5-110">根據 `maxAge` 值，如果快取原則設定 `maxAge` = 5 天且 `maxStale` = 3 天，則在1 月 6 日之前可以使用內容。</span><span class="sxs-lookup"><span data-stu-id="39ec5-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="39ec5-111">根據 `maxStale` 值，在 1 月 7 日之前可以使用內容。</span><span class="sxs-lookup"><span data-stu-id="39ec5-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="39ec5-112">因此，會在 1 月 6 日重新驗證內容。</span><span class="sxs-lookup"><span data-stu-id="39ec5-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
-   <span data-ttu-id="39ec5-113">根據 `maxAge` 值，如果快取原則設定 `maxAge` = 5 天且 `maxStale` = 1 天，則在 1 月 6 日之前可以使用內容。</span><span class="sxs-lookup"><span data-stu-id="39ec5-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="39ec5-114">根據 `maxStale` 值，在 1 月 5 日之前可以使用內容。</span><span class="sxs-lookup"><span data-stu-id="39ec5-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="39ec5-115">因此，會在 1 月 5 日重新驗證內容。</span><span class="sxs-lookup"><span data-stu-id="39ec5-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="39ec5-116">最長使用期限小於內容到期日時，一律會使用更保守的快取行為，而且最長過時值沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="39ec5-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="39ec5-117">下列範例說明達到最長使用期限 (`maxAge`) 但在內容到期之前，設定最長過時 (`maxStale`) 值的效果：</span><span class="sxs-lookup"><span data-stu-id="39ec5-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
-   <span data-ttu-id="39ec5-118">如果快取原則設定 `maxAge` = 1 天，但未指定 `maxStale` 值的值，則會在 1 月 2 日重新驗證內容，即使未到期也是一樣。</span><span class="sxs-lookup"><span data-stu-id="39ec5-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
-   <span data-ttu-id="39ec5-119">如果快取原則設定 `maxAge` = 1 天且 `maxStale` = 3 天，則會在 1 月 2 日重新驗證內容，來強制執行更保守的原則設定。</span><span class="sxs-lookup"><span data-stu-id="39ec5-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
-   <span data-ttu-id="39ec5-120">如果快取原則設定 `maxAge` = 1 天且 `maxStale` = 1 天，則會在 1 月 2 日重新驗證內容。</span><span class="sxs-lookup"><span data-stu-id="39ec5-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39ec5-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="39ec5-121">See Also</span></span>  
 [<span data-ttu-id="39ec5-122">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="39ec5-122">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="39ec5-123">快取原則</span><span class="sxs-lookup"><span data-stu-id="39ec5-123">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="39ec5-124">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="39ec5-124">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="39ec5-125">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="39ec5-125">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="39ec5-126">設定網路應用程式的快取功能</span><span class="sxs-lookup"><span data-stu-id="39ec5-126">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="39ec5-127">快取原則互動 - 最長使用期限和最小有效期限</span><span class="sxs-lookup"><span data-stu-id="39ec5-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
