---
title: 處理部分失敗
description: 了解如何適當地處理部分失敗。 微服務可能無法完全正常運作，但它仍可能可以執行一些有用的工作。
ms.date: 10/16/2018
ms.openlocfilehash: f00e5349df74b543deb6ac941c751cb130b3837c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73732996"
---
# <a name="handle-partial-failure"></a><span data-ttu-id="8c70b-104">處理部分失敗</span><span class="sxs-lookup"><span data-stu-id="8c70b-104">Handle partial failure</span></span>

<span data-ttu-id="8c70b-105">在微服務架構應用程式等分散式系統中，部分失敗的風險無所不在。</span><span class="sxs-lookup"><span data-stu-id="8c70b-105">In distributed systems like microservices-based applications, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="8c70b-106">例如，單一微服務/容器可能會失敗或暫時無法回應，或是單一 VM 或伺服器可能會當機。</span><span class="sxs-lookup"><span data-stu-id="8c70b-106">For instance, a single microservice/container can fail or might not be available to respond for a short time, or a single VM or server can crash.</span></span> <span data-ttu-id="8c70b-107">由於用戶端和服務是不同的處理序，服務可能無法及時回應用戶端的要求。</span><span class="sxs-lookup"><span data-stu-id="8c70b-107">Since clients and services are separate processes, a service might not be able to respond in a timely way to a client’s request.</span></span> <span data-ttu-id="8c70b-108">服務可能會多載且回應要求的速度相當慢，或只是因為網路問題而暫時無法存取。</span><span class="sxs-lookup"><span data-stu-id="8c70b-108">The service might be overloaded and responding very slowly to requests or might simply not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="8c70b-109">以 eShopOnContainers 範例應用程式中的 [訂單] 詳細資料頁面為例。</span><span class="sxs-lookup"><span data-stu-id="8c70b-109">For example, consider the Order details page from the eShopOnContainers sample application.</span></span> <span data-ttu-id="8c70b-110">如果當使用者嘗試送出訂單時，訂購微服務沒有回應，不正確的用戶端處理序 (MVC Web 應用程式) 實作 (例如若用戶端程式碼使用沒有逾時的同步 RPC) 會無限期地封鎖等候回應的執行緒。</span><span class="sxs-lookup"><span data-stu-id="8c70b-110">If the ordering microservice is unresponsive when the user tries to submit an order, a bad implementation of the client process (the MVC web application)—for example, if the client code were to use synchronous RPCs with no timeout—would block threads indefinitely waiting for a response.</span></span> <span data-ttu-id="8c70b-111">除了造成不良的使用者體驗之外，每個沒有回應的等候都會耗用或封鎖執行緒，而執行緒對於可高度擴充的應用程式而言相當重要。</span><span class="sxs-lookup"><span data-stu-id="8c70b-111">Besides creating a bad user experience, every unresponsive wait consumes or blocks a thread, and threads are extremely valuable in highly scalable applications.</span></span> <span data-ttu-id="8c70b-112">若有許多封鎖的執行緒，應用程式的執行階段最後可能會用盡執行緒。</span><span class="sxs-lookup"><span data-stu-id="8c70b-112">If there are many blocked threads, eventually the application’s runtime can run out of threads.</span></span> <span data-ttu-id="8c70b-113">在此情況下，應用程式可能會變得全部沒有回應，而不只是部分沒有回應，如圖 8-1 所示。</span><span class="sxs-lookup"><span data-stu-id="8c70b-113">In that case, the application can become globally unresponsive instead of just partially unresponsive, as shown in Figure 8-1.</span></span>

![顯示部分故障的圖表。](./media/handle-partial-failure/partial-failures-diagram.png)

<span data-ttu-id="8c70b-115">**圖 8-1**：</span><span class="sxs-lookup"><span data-stu-id="8c70b-115">**Figure 8-1**.</span></span> <span data-ttu-id="8c70b-116">由於影響服務執行緒可用性的相依性所造成的部分失敗</span><span class="sxs-lookup"><span data-stu-id="8c70b-116">Partial failures because of dependencies that impact service thread availability</span></span>

<span data-ttu-id="8c70b-117">在大型微服務架構應用程式中，任何部分失敗都可能會擴大，特別是如果大多數內部微服務互動是以同步 HTTP 呼叫為基礎 (視為反面模式)。</span><span class="sxs-lookup"><span data-stu-id="8c70b-117">In a large microservices-based application, any partial failure can be amplified, especially if most of the internal microservices interaction is based on synchronous HTTP calls (which is considered an anti-pattern).</span></span> <span data-ttu-id="8c70b-118">假設有個系統，每天會收到數百萬個傳入呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c70b-118">Think about a system that receives millions of incoming calls per day.</span></span> <span data-ttu-id="8c70b-119">如果您的系統有同步 HTTP 呼叫鏈結太長的不正確設計，這些傳入呼叫可能會導致對作為同步相依性之數十個內部微服務的傳出呼叫超過數百萬個 (假設比率為 1:4)。</span><span class="sxs-lookup"><span data-stu-id="8c70b-119">If your system has a bad design that's based on long chains of synchronous HTTP calls, these incoming calls might result in many more millions of outgoing calls (let’s suppose a ratio of 1:4) to dozens of internal microservices as synchronous dependencies.</span></span> <span data-ttu-id="8c70b-120">這種情況如圖 8-2 所示，尤其是啟動鏈\#、調用依賴項#4的依賴項 3。</span><span class="sxs-lookup"><span data-stu-id="8c70b-120">This situation is shown in Figure 8-2, especially dependency \#3, that starts a chain, calling dependency #4.</span></span> <span data-ttu-id="8c70b-121">呼叫#5。</span><span class="sxs-lookup"><span data-stu-id="8c70b-121">which the calls #5.</span></span>

![顯示多個分散式依賴項的圖表。](./media/handle-partial-failure/multiple-distributed-dependencies.png)

<span data-ttu-id="8c70b-123">**圖8-2**.</span><span class="sxs-lookup"><span data-stu-id="8c70b-123">**Figure 8-2**.</span></span> <span data-ttu-id="8c70b-124">HTTP 要求鏈結太長的不正確設計影響</span><span class="sxs-lookup"><span data-stu-id="8c70b-124">The impact of having an incorrect design featuring long chains of HTTP requests</span></span>

<span data-ttu-id="8c70b-125">分散式和雲端式系統一定會發生間歇性失敗，即使每個相依性本身有絕佳的可用性也一樣。</span><span class="sxs-lookup"><span data-stu-id="8c70b-125">Intermittent failure is guaranteed in a distributed and cloud-based system, even if every dependency itself has excellent availability.</span></span> <span data-ttu-id="8c70b-126">這是您需要考量的事實。</span><span class="sxs-lookup"><span data-stu-id="8c70b-126">It's a fact you need to consider.</span></span>

<span data-ttu-id="8c70b-127">如果您未設計及實作技術來確保容錯，即使是短暫的停機也可能會擴大。</span><span class="sxs-lookup"><span data-stu-id="8c70b-127">If you do not design and implement techniques to ensure fault tolerance, even small downtimes can be amplified.</span></span> <span data-ttu-id="8c70b-128">例如，可用性達 99.99% 的 50 個相依性會因為此漣漪效果而導致每個月數小時的停機。</span><span class="sxs-lookup"><span data-stu-id="8c70b-128">As an example, 50 dependencies each with 99.99% of availability would result in several hours of downtime each month because of this ripple effect.</span></span> <span data-ttu-id="8c70b-129">當微服務相依性處理大量要求失敗時，該失敗很快就會使每個服務中的所有可用要求執行緒達到飽和，而導致整個應用程式損毀。</span><span class="sxs-lookup"><span data-stu-id="8c70b-129">When a microservice dependency fails while handling a high volume of requests, that failure can quickly saturate all available request threads in each service and crash the whole application.</span></span>

![顯示部分故障放大微服務中的圖表。](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

<span data-ttu-id="8c70b-131">**圖 8-3**：</span><span class="sxs-lookup"><span data-stu-id="8c70b-131">**Figure 8-3**.</span></span> <span data-ttu-id="8c70b-132">部分失敗因同步 HTTP 呼叫鏈結太長的微服務而擴大</span><span class="sxs-lookup"><span data-stu-id="8c70b-132">Partial failure amplified by microservices with long chains of synchronous HTTP calls</span></span>

<span data-ttu-id="8c70b-133">若要減輕[非同步微服務整合會強制執行微服務的自主](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy)一節中的這個問題，此指南建議您跨內部微服務使用非同步通訊。</span><span class="sxs-lookup"><span data-stu-id="8c70b-133">To minimize this problem, in the section [Asynchronous microservice integration enforce microservice’s autonomy](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy), this guide encourages you to use asynchronous communication across the internal microservices.</span></span>

<span data-ttu-id="8c70b-134">此外，請務必設計微服務和用戶端應用程式來處理部分失敗，也就是建置具有恢復功能的微服務和用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="8c70b-134">In addition, it's essential that you design your microservices and client applications to handle partial failures—that is, to build resilient microservices and client applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8c70b-135">[上一個](index.md)
>[下一個](partial-failure-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="8c70b-135">[Previous](index.md)
[Next](partial-failure-strategies.md)</span></span>
