---
title: 快取原則互動 — 最長使用期限和最小有效期限
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: 93136d4c87463db7128a68957b243c1ef13a90eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174053"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="fc3d7-102">快取原則互動 — 最長使用期限和最小有效期限</span><span class="sxs-lookup"><span data-stu-id="fc3d7-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="fc3d7-103">為了協助確保將最新內容傳回給用戶端應用程式，用戶端快取原則與伺服器重新驗證需求的互動一律會導致最保守的快取原則。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="fc3d7-104">本主題中的所有範例都會說明在 1 月 1 日快取並在 1 月 4 日到期之資源的快取原則。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="fc3d7-105">下列範例說明最長使用期限 (`maxAge`) 與最小有效期限 (`minFresh`) 值的互動所造成的快取原則。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="fc3d7-106">如果快取原則設定 `maxAge` = 2 天，但未指定 `minFresh`，則會在 1 月 3 日重新驗證內容。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="fc3d7-107">根據 `maxAge`，如果快取原則設定 `maxAge` = 2 天且 `minFresh` = 1 天，則會在 1 月 3 日之前整理內容。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="fc3d7-108">根據 `minFresh`，會在 1 月 3 日之前整理內容。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="fc3d7-109">因此，必須在 1 月 3 日重新驗證內容。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="fc3d7-110">根據 `maxAge`，如果快取原則設定 `maxAge` = 2 天且 `minFresh` = 2 天，則會在 1 月 3 日之前整理內容。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="fc3d7-111">根據 `minFresh`，會在 1 月 2 日之前整理內容。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="fc3d7-112">因此，必須在 1 月 2 日重新驗證內容。</span><span class="sxs-lookup"><span data-stu-id="fc3d7-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3d7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc3d7-113">See also</span></span>

- [<span data-ttu-id="fc3d7-114">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="fc3d7-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="fc3d7-115">快取原則</span><span class="sxs-lookup"><span data-stu-id="fc3d7-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="fc3d7-116">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="fc3d7-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="fc3d7-117">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="fc3d7-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="fc3d7-118">設定網路應用程式的快取功能</span><span class="sxs-lookup"><span data-stu-id="fc3d7-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [<span data-ttu-id="fc3d7-119">快取原則互動 - 最長使用期限和最長過時</span><span class="sxs-lookup"><span data-stu-id="fc3d7-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
