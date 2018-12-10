---
title: 處理部分失敗
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 處理部分失敗
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 94239fc30292760b2bb28849f8c6ab72c7ceb33d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144724"
---
# <a name="handling-partial-failure"></a><span data-ttu-id="f651b-103">處理部分失敗</span><span class="sxs-lookup"><span data-stu-id="f651b-103">Handling partial failure</span></span>

<span data-ttu-id="f651b-104">在微服務架構應用程式等分散式系統中，部分失敗的風險無所不在。</span><span class="sxs-lookup"><span data-stu-id="f651b-104">In distributed systems like microservices-based applications, there is an ever-present risk of partial failure.</span></span> <span data-ttu-id="f651b-105">例如，單一微服務/容器可能會失敗或暫時無法回應，或是單一 VM 或伺服器可能會當機。</span><span class="sxs-lookup"><span data-stu-id="f651b-105">For instance, a single microservice/container can fail or might not be available to respond for a short time, or a single VM or server can crash.</span></span> <span data-ttu-id="f651b-106">由於用戶端和服務是不同的處理序，服務可能無法及時回應用戶端的要求。</span><span class="sxs-lookup"><span data-stu-id="f651b-106">Since clients and services are separate processes, a service might not be able to respond in a timely way to a client’s request.</span></span> <span data-ttu-id="f651b-107">服務可能會多載且回應要求的速度相當慢，或只是因為網路問題而暫時無法存取。</span><span class="sxs-lookup"><span data-stu-id="f651b-107">The service might be overloaded and responding extremely slowly to requests or might simply not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="f651b-108">以 eShopOnContainers 範例應用程式中的 [訂單] 詳細資料頁面為例。</span><span class="sxs-lookup"><span data-stu-id="f651b-108">For example, consider the Order details page from the eShopOnContainers sample application.</span></span> <span data-ttu-id="f651b-109">如果當使用者嘗試送出訂單時，訂購微服務沒有回應，不正確的用戶端處理序 (MVC Web 應用程式) 實作 (例如若用戶端程式碼使用沒有逾時的同步 RPC) 會無限期地封鎖等候回應的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f651b-109">If the ordering microservice is unresponsive when the user tries to submit an order, a bad implementation of the client process (the MVC web application)—for example, if the client code were to use synchronous RPCs with no timeout—would block threads indefinitely waiting for a response.</span></span> <span data-ttu-id="f651b-110">除了造成不良的使用者體驗之外，每個沒有回應的等候都會耗用或封鎖執行緒，而執行緒對於可高度擴充的應用程式而言相當重要。</span><span class="sxs-lookup"><span data-stu-id="f651b-110">In addition to creating a bad user experience, every unresponsive wait consumes or blocks a thread, and threads are extremely valuable in highly scalable applications.</span></span> <span data-ttu-id="f651b-111">若有許多封鎖的執行緒，應用程式的執行階段最後可能會用盡執行緒。</span><span class="sxs-lookup"><span data-stu-id="f651b-111">If there are many blocked threads, eventually the application’s runtime can run out of threads.</span></span> <span data-ttu-id="f651b-112">在此情況下，應用程式可能會變得全域沒有回應，而不只是部分沒有回應，如圖 10-1 所示。</span><span class="sxs-lookup"><span data-stu-id="f651b-112">In that case, the application can become globally unresponsive instead of just partially unresponsive, as show in Figure 10-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="f651b-113">**圖 10-1**：</span><span class="sxs-lookup"><span data-stu-id="f651b-113">**Figure 10-1**.</span></span> <span data-ttu-id="f651b-114">由於影響服務執行緒可用性的相依性所造成的部分失敗</span><span class="sxs-lookup"><span data-stu-id="f651b-114">Partial failures because of dependencies that impact service thread availability</span></span>

<span data-ttu-id="f651b-115">在大型微服務架構應用程式中，任何部分失敗都可能會擴大，特別是如果大多數內部微服務互動是以同步 HTTP 呼叫為基礎 (視為反面模式)。</span><span class="sxs-lookup"><span data-stu-id="f651b-115">In a large microservices-based application, any partial failure can be amplified, especially if most of the internal microservices interaction is based on synchronous HTTP calls (which is considered an anti-pattern).</span></span> <span data-ttu-id="f651b-116">假設有個系統，每天會收到數百萬個傳入呼叫。</span><span class="sxs-lookup"><span data-stu-id="f651b-116">Think about a system that receives millions of incoming calls per day.</span></span> <span data-ttu-id="f651b-117">如果您的系統有同步 HTTP 呼叫鏈結太長的不正確設計，這些傳入呼叫可能會導致對作為同步相依性之數十個內部微服務的傳出呼叫超過數百萬個 (假設比率為 1:4)。</span><span class="sxs-lookup"><span data-stu-id="f651b-117">If your system has a bad design that is based on long chains of synchronous HTTP calls, these incoming calls might result in many more millions of outgoing calls (let’s suppose a ratio of 1:4) to dozens of internal microservices as synchronous dependencies.</span></span> <span data-ttu-id="f651b-118">圖 10-2 顯示這種情況，特別是相依性 \#3。</span><span class="sxs-lookup"><span data-stu-id="f651b-118">This situation is shown in Figure 10-2, especially dependency \#3.</span></span>

![](./media/image2.png)

<span data-ttu-id="f651b-119">**圖 10-2**：</span><span class="sxs-lookup"><span data-stu-id="f651b-119">**Figure 10-2**.</span></span> <span data-ttu-id="f651b-120">HTTP 要求鏈結太長的不正確設計影響</span><span class="sxs-lookup"><span data-stu-id="f651b-120">The impact of having an incorrect design featuring long chains of HTTP requests</span></span>

<span data-ttu-id="f651b-121">分散式和雲端式系統一定會發生間歇性失敗，即使每個相依性本身有絕佳的可用性也一樣。</span><span class="sxs-lookup"><span data-stu-id="f651b-121">Intermittent failure is guaranteed in a distributed and cloud-based system, even if every dependency itself has excellent availability.</span></span> <span data-ttu-id="f651b-122">這是您需要考量的事實。</span><span class="sxs-lookup"><span data-stu-id="f651b-122">It is fact you need to consider.</span></span>

<span data-ttu-id="f651b-123">如果您未設計及實作技術來確保容錯，即使是短暫的停機也可能會擴大。</span><span class="sxs-lookup"><span data-stu-id="f651b-123">If you do not design and implement techniques to ensure fault tolerance, even small downtimes can be amplified.</span></span> <span data-ttu-id="f651b-124">例如，可用性達 99.99% 的 50 個相依性會因為此漣漪效果而導致每個月數小時的停機。</span><span class="sxs-lookup"><span data-stu-id="f651b-124">As an example, 50 dependencies each with 99.99% of availability would result in several hours of downtime each month because of this ripple effect.</span></span> <span data-ttu-id="f651b-125">當微服務相依性處理大量要求失敗時，該失敗很快就會使每個服務中的所有可用要求執行緒達到飽和，而導致整個應用程式損毀。</span><span class="sxs-lookup"><span data-stu-id="f651b-125">When a microservice dependency fails while handling a high volume of requests, that failure can quickly saturate all available request threads in each service and crash the whole application.</span></span>

![](./media/image3.png)

<span data-ttu-id="f651b-126">**圖 10-3**：</span><span class="sxs-lookup"><span data-stu-id="f651b-126">**Figure 10-3**.</span></span> <span data-ttu-id="f651b-127">部分失敗因同步 HTTP 呼叫鏈結太長的微服務而擴大</span><span class="sxs-lookup"><span data-stu-id="f651b-127">Partial failure amplified by microservices with long chains of synchronous HTTP calls</span></span>

<span data-ttu-id="f651b-128">若要減輕＜非同步微服務整合會強制執行微服務的自主＞一節 (位於＜架構＞一章) 中的這個問題，此指引建議您跨內部微服務使用非同步通訊。</span><span class="sxs-lookup"><span data-stu-id="f651b-128">To minimize this problem, in the section "*Asynchronous microservice integration enforce microservice’s autonomy*” (in the architecture chapter), this guidance encourages you to use asynchronous communication across the internal microservices.</span></span> 

<span data-ttu-id="f651b-129">此外，請務必設計微服務和用戶端應用程式來處理部分失敗，也就是建置具有恢復功能的微服務和用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="f651b-129">In addition, it is essential that you design your microservices and client applications to handle partial failures—that is, to build resilient microservices and client applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f651b-130">[上一頁](index.md)
>[下一頁](partial-failure-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="f651b-130">[Previous](index.md)
[Next](partial-failure-strategies.md)</span></span>