---
title: 處理部分失敗的策略
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 處理部分失敗的策略
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c36ea31ad19b02fb02bc8e7185bfe8687b87764f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104205"
---
# <a name="strategies-for-handling-partial-failure"></a><span data-ttu-id="51b88-103">處理部分失敗的策略</span><span class="sxs-lookup"><span data-stu-id="51b88-103">Strategies for handling partial failure</span></span>

<span data-ttu-id="51b88-104">處理部分失敗的策略包含下列項目。</span><span class="sxs-lookup"><span data-stu-id="51b88-104">Strategies for dealing with partial failures include the following.</span></span>

<span data-ttu-id="51b88-105">**使用跨內部微服務的非同步通訊 (例如以訊息為基礎的通訊)**。</span><span class="sxs-lookup"><span data-stu-id="51b88-105">**Use asynchronous communication (for example, message-based communication) across internal microservices**.</span></span> <span data-ttu-id="51b88-106">我們強烈建議您不要跨內部微服務建立一長串的同步 HTTP 呼叫，因為不正確的設計最終可能會成為不良中斷的主要原因。</span><span class="sxs-lookup"><span data-stu-id="51b88-106">It is highly advisable not to create long chains of synchronous HTTP calls across the internal microservices because that incorrect design will eventually become the main cause of bad outages.</span></span> <span data-ttu-id="51b88-107">相反地，除了用戶端應用程式與微服務第一層或微調 API 閘道之間的前端通訊，通常建議在通過初始要求/回應循環之後僅使用跨內部微服務的非同步式 (以訊息為基礎) 通訊。</span><span class="sxs-lookup"><span data-stu-id="51b88-107">On the contrary, except for the front-end communications between the client applications and the first level of microservices or fine-grained API Gateways, it is recommended to use only asynchronous (message-based) communication once past the initial request/response cycle, across the internal microservices.</span></span> <span data-ttu-id="51b88-108">最終一致性和事件驅動架構會協助最小化漣漪效果。</span><span class="sxs-lookup"><span data-stu-id="51b88-108">Eventual consistency and event-driven architectures will help to minimize ripple effects.</span></span> <span data-ttu-id="51b88-109">這些方法會強制更高層級微服務的自主性，從而防止此處註明的問題。</span><span class="sxs-lookup"><span data-stu-id="51b88-109">These approaches enforce a higher level of microservice autonomy and therefore prevent against the problem noted here.</span></span>

<span data-ttu-id="51b88-110">**利用指數輪詢來使用重試**。</span><span class="sxs-lookup"><span data-stu-id="51b88-110">**Use retries with exponential backoff**.</span></span> <span data-ttu-id="51b88-111">這項技術可在服務短時間內無法使用的情況下，藉由執行特定次數的呼叫重試，來協助避免簡短而間歇的失敗。</span><span class="sxs-lookup"><span data-stu-id="51b88-111">This technique helps to avoid short and intermittent failures by performing call retries a certain number of times, in case the service was not available only for a short time.</span></span> <span data-ttu-id="51b88-112">這可能會因為間歇性的網路問題或當微服務/容器移動到叢集中不同的節點時而發生。</span><span class="sxs-lookup"><span data-stu-id="51b88-112">This might occur due to intermittent network issues or when a microservice/container is moved to a different node in a cluster.</span></span> <span data-ttu-id="51b88-113">然而，若這些重試並未適當的使用斷路器進行設計，它可能會加劇漣漪效果，並最終導致[enial of Service (DoS) (拒絕服務)](https://en.wikipedia.org/wiki/Denial-of-service_attack)。</span><span class="sxs-lookup"><span data-stu-id="51b88-113">However, if these retries are not designed properly with circuit breakers, it can aggravate the ripple effects, ultimately even causing a [Denial of Service (DoS)](https://en.wikipedia.org/wiki/Denial-of-service_attack).</span></span>

<span data-ttu-id="51b88-114">**網路逾時的因應措施**。</span><span class="sxs-lookup"><span data-stu-id="51b88-114">**Work around network timeouts**.</span></span> <span data-ttu-id="51b88-115">一般情況下，用戶端應設計成不會無限期的進行封鎖，並在等待回應時總是使用逾時。</span><span class="sxs-lookup"><span data-stu-id="51b88-115">In general, clients should be designed not to block indefinitely and to always use timeouts when waiting for a response.</span></span> <span data-ttu-id="51b88-116">使用逾時可確保資源不會無限期的遭到繫結。</span><span class="sxs-lookup"><span data-stu-id="51b88-116">Using timeouts ensures that resources are never tied up indefinitely.</span></span>

<span data-ttu-id="51b88-117">**使用斷路器模式**。</span><span class="sxs-lookup"><span data-stu-id="51b88-117">**Use the Circuit Breaker pattern**.</span></span> <span data-ttu-id="51b88-118">在這種方法中，用戶端處理序會追蹤失敗要求的次數。</span><span class="sxs-lookup"><span data-stu-id="51b88-118">In this approach, the client process tracks the number of failed requests.</span></span> <span data-ttu-id="51b88-119">若錯誤率超過設定的限制，則「斷路器」便會進行往返，使得更進一步的嘗試都會立即失敗。</span><span class="sxs-lookup"><span data-stu-id="51b88-119">If the error rate exceeds a configured limit, a “circuit breaker” trips so that further attempts fail immediately.</span></span> <span data-ttu-id="51b88-120">(若有失敗的要求數目相當龐大，這表示服務無法使用，傳送要求沒有意義。)在逾時期間過後，用戶端應再試一次，並且當新的要求成功時，關閉斷路器。</span><span class="sxs-lookup"><span data-stu-id="51b88-120">(If a large number of requests are failing, that suggests the service is unavailable and that sending requests is pointless.) After a timeout period, the client should try again and, if the new requests are successful, close the circuit breaker.</span></span>

<span data-ttu-id="51b88-121">**提供後援**。</span><span class="sxs-lookup"><span data-stu-id="51b88-121">**Provide fallbacks**.</span></span> <span data-ttu-id="51b88-122">在這種方法中，用戶端處理序會在要求失敗時執行後援邏輯，例如傳回快取資料或預設值。</span><span class="sxs-lookup"><span data-stu-id="51b88-122">In this approach, the client process performs fallback logic when a request fails, such as returning cached data or a default value.</span></span> <span data-ttu-id="51b88-123">這是一種適合查詢的方法，而針對更新或命令會更為複雜。</span><span class="sxs-lookup"><span data-stu-id="51b88-123">This is an approach suitable for queries, and is more complex for updates or commands.</span></span>

<span data-ttu-id="51b88-124">**限制佇列要求的數目**。</span><span class="sxs-lookup"><span data-stu-id="51b88-124">**Limit the number of queued requests**.</span></span> <span data-ttu-id="51b88-125">用戶端也應設定用戶端微服務可傳送至特定服務之未處理要求的數目上限。</span><span class="sxs-lookup"><span data-stu-id="51b88-125">Clients should also impose an upper bound on the number of outstanding requests that a client microservice can send to a particular service.</span></span> <span data-ttu-id="51b88-126">若達到該限制，則繼續傳送額外的要求可能會沒有意義，因此應讓那些嘗試立即失敗。</span><span class="sxs-lookup"><span data-stu-id="51b88-126">If the limit has been reached, it is probably pointless to make additional requests, and those attempts should fail immediately.</span></span> <span data-ttu-id="51b88-127">在實作方面，Polly [Bulkhead Isolation](https://github.com/App-vNext/Polly/wiki/Bulkhead) 原則可用於完成這項要求。</span><span class="sxs-lookup"><span data-stu-id="51b88-127">In terms of implementation, the Polly [Bulkhead Isolation](https://github.com/App-vNext/Polly/wiki/Bulkhead) policy can be used to fulfil this requirement.</span></span> <span data-ttu-id="51b88-128">此方法本質上即是使用 <xref:System.Threading.SemaphoreSlim> 作為實作的並行節流。</span><span class="sxs-lookup"><span data-stu-id="51b88-128">This approach is essentially a parallelization throttle with <xref:System.Threading.SemaphoreSlim> as the implementation.</span></span> <span data-ttu-id="51b88-129">它也允許了艙壁之外的「佇列」。</span><span class="sxs-lookup"><span data-stu-id="51b88-129">It also permits a "queue" outside the bulkhead.</span></span> <span data-ttu-id="51b88-130">您甚至可以在執行之前主動流出過量的負載 (例如因為容量被視為已滿)。</span><span class="sxs-lookup"><span data-stu-id="51b88-130">You can proactively shed excess load even before execution (for example, because capacity is deemed full).</span></span> <span data-ttu-id="51b88-131">這可讓其回應特定失敗案例的速度比斷路器要來得更快，因為斷路器會等待失敗。</span><span class="sxs-lookup"><span data-stu-id="51b88-131">This makes its response to certain failure scenarios faster than a circuit breaker would be, since the circuit breaker waits for the failures.</span></span> <span data-ttu-id="51b88-132">Polly 中的 BulkheadPolicy 物件會公開艙壁及佇列充滿的程度，並在溢位時提供事件，使其也可用於驅動自動化水平縮放。</span><span class="sxs-lookup"><span data-stu-id="51b88-132">The BulkheadPolicy object in Polly exposes how full the bulkhead and queue are, and offers events on overflow so can also be used to drive automated horizontal scaling.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="51b88-133">其他資源</span><span class="sxs-lookup"><span data-stu-id="51b88-133">Additional resources</span></span>

-   <span data-ttu-id="51b88-134">**復原模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="51b88-134">**Resiliency patterns**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="51b88-135">**新增復原和最佳化效能**
    [*https://msdn.microsoft.com/library/jj591574.aspx*](https://msdn.microsoft.com/library/jj591574.aspx)</span><span class="sxs-lookup"><span data-stu-id="51b88-135">**Adding Resilience and Optimizing Performance**
[*https://msdn.microsoft.com/library/jj591574.aspx*](https://msdn.microsoft.com/library/jj591574.aspx)</span></span>

-   <span data-ttu-id="51b88-136">**Bulkhead。**</span><span class="sxs-lookup"><span data-stu-id="51b88-136">**Bulkhead.**</span></span> <span data-ttu-id="51b88-137">GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="51b88-137">GitHub repo.</span></span> <span data-ttu-id="51b88-138">Polly 原則的實作。\\</span><span class="sxs-lookup"><span data-stu-id="51b88-138">Implementation with Polly policy.\\</span></span>
    [*https://github.com/App-vNext/Polly/wiki/Bulkhead*](https://github.com/App-vNext/Polly/wiki/Bulkhead)

-   <span data-ttu-id="51b88-139">**為 Azure 設計具有復原功能的應用程式**
    [*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)</span><span class="sxs-lookup"><span data-stu-id="51b88-139">**Designing resilient applications for Azure**
[*https://docs.microsoft.com/azure/architecture/resiliency/*](https://docs.microsoft.com/azure/architecture/resiliency/)</span></span>

-   <span data-ttu-id="51b88-140">**暫時性錯誤處理**
    <https://docs.microsoft.com/azure/architecture/best-practices/transient-faults></span><span class="sxs-lookup"><span data-stu-id="51b88-140">**Transient fault handling**
<https://docs.microsoft.com/azure/architecture/best-practices/transient-faults></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="51b88-141">[上一頁](handle-partial-failure.md)
[下一頁](implement-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="51b88-141">[Previous](handle-partial-failure.md)
[Next](implement-retries-exponential-backoff.md)</span></span>
