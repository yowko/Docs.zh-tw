---
title: "處理部分失敗"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |處理部分失敗"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7d16acf3de2d395da70e8f46e59c129dec24f71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="handling-partial-failure"></a><span data-ttu-id="e51ba-104">處理部分失敗</span><span class="sxs-lookup"><span data-stu-id="e51ba-104">Handling partial failure</span></span>

<span data-ttu-id="e51ba-105">在分散式系統如 microservices 為基礎的應用程式中，會有部分失敗的無所不在風險。</span><span class="sxs-lookup"><span data-stu-id="e51ba-105">In distributed systems like microservices-based applications, there is an ever-present risk of partial failure.</span></span> <span data-ttu-id="e51ba-106">例如，單一微服務/容器可能會失敗，或可能無法回應一段時間，或單一 VM 或伺服器可能會損毀。</span><span class="sxs-lookup"><span data-stu-id="e51ba-106">For instance, a single microservice/container can fail or might not be available to respond for a short time, or a single VM or server can crash.</span></span> <span data-ttu-id="e51ba-107">由於用戶端和服務的個別處理序，服務可能無法在用戶端的要求能夠及時回應。</span><span class="sxs-lookup"><span data-stu-id="e51ba-107">Since clients and services are separate processes, a service might not be able to respond in a timely way to a client’s request.</span></span> <span data-ttu-id="e51ba-108">服務可能會多載和回應速度極為緩慢的要求，或可能只是無法存取一小段時間因為網路問題。</span><span class="sxs-lookup"><span data-stu-id="e51ba-108">The service might be overloaded and responding extremely slowly to requests, or might simply not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="e51ba-109">例如，請考慮從 eShopOnContainers 的訂單詳細資料頁面範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="e51ba-109">For example, consider the Order details page from the eShopOnContainers sample application.</span></span> <span data-ttu-id="e51ba-110">如果順序的微服務沒有回應當使用者嘗試送出訂單時，用戶端處理序 （MVC web 應用程式） 的不正確實作 — 比方說，如果用戶端程式碼都不會逾時與使用同步 Rpc — 會無限期地封鎖執行緒等待回應。</span><span class="sxs-lookup"><span data-stu-id="e51ba-110">If the ordering microservice is unresponsive when the user tries to submit an order, a bad implementation of the client process (the MVC web application)—for example, if the client code were to use synchronous RPCs with no timeout—would block threads indefinitely waiting for a response.</span></span> <span data-ttu-id="e51ba-111">除了提供不正確的使用者體驗，每一個回應的等候取用或會阻擋執行緒，而且執行緒高度可擴充的應用程式中非常重要。</span><span class="sxs-lookup"><span data-stu-id="e51ba-111">In addition to creating a bad user experience, every unresponsive wait consumes or blocks a thread, and threads are extremely valuable in highly scalable applications.</span></span> <span data-ttu-id="e51ba-112">如果有許多已封鎖的執行緒，最終應用程式的執行階段可以用完執行緒。</span><span class="sxs-lookup"><span data-stu-id="e51ba-112">If there are many blocked threads, eventually the application’s runtime can run out of threads.</span></span> <span data-ttu-id="e51ba-113">在此情況下，應用程式可能會變得全域沒有回應，而不是只部分沒有回應，以顯示圖 10-1。</span><span class="sxs-lookup"><span data-stu-id="e51ba-113">In that case, the application can become globally unresponsive instead of just partially unresponsive, as show in Figure 10-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="e51ba-114">**圖 10 1**。</span><span class="sxs-lookup"><span data-stu-id="e51ba-114">**Figure 10-1**.</span></span> <span data-ttu-id="e51ba-115">部分失敗，因為會影響服務的執行緒可用性的相依性</span><span class="sxs-lookup"><span data-stu-id="e51ba-115">Partial failures because of dependencies that impact service thread availability</span></span>

<span data-ttu-id="e51ba-116">在大型 microservices 型應用程式中，任何部分失敗可以會隨之增加，尤其是如果大部分的內部 microservices 互動的同步 HTTP 呼叫 （這可反面模式）。</span><span class="sxs-lookup"><span data-stu-id="e51ba-116">In a large microservices-based application, any partial failure can be amplified, especially if most of the internal microservices interaction is based on synchronous HTTP calls (which is considered an anti-pattern).</span></span> <span data-ttu-id="e51ba-117">請思考接收每日的連入呼叫數百萬的系統。</span><span class="sxs-lookup"><span data-stu-id="e51ba-117">Think about a system that receives millions of incoming calls per day.</span></span> <span data-ttu-id="e51ba-118">如果您的系統具有不正確的設計為基礎的同步 HTTP 呼叫長的鏈結，這些連入呼叫可能會導致許多數百萬詳細 （假設的比率為 1:4） 的連出呼叫數十個內部 microservices 做為同步的相依性。</span><span class="sxs-lookup"><span data-stu-id="e51ba-118">If your system has a bad design that is based on long chains of synchronous HTTP calls, these incoming calls might result in many more millions of outgoing calls (let’s suppose a ratio of 1:4) to dozens of internal microservices as synchronous dependencies.</span></span> <span data-ttu-id="e51ba-119">這種情況下會顯示在圖 10-2，特別是相依性\#3。</span><span class="sxs-lookup"><span data-stu-id="e51ba-119">This situation is shown in Figure 10-2, especially dependency \#3.</span></span>

![](./media/image2.png)

<span data-ttu-id="e51ba-120">**圖 10 2**。</span><span class="sxs-lookup"><span data-stu-id="e51ba-120">**Figure 10-2**.</span></span> <span data-ttu-id="e51ba-121">讓包含很長的鏈結的 HTTP 要求的設計不正確的影響</span><span class="sxs-lookup"><span data-stu-id="e51ba-121">The impact of having an incorrect design featuring long chains of HTTP requests</span></span>

<span data-ttu-id="e51ba-122">幾乎是間歇性失敗保證在分散式部署和雲端架構的系統，即使每個相依性本身具有極佳的可用性。</span><span class="sxs-lookup"><span data-stu-id="e51ba-122">Intermittent failure is virtually guaranteed in a distributed and cloud based system, even if every dependency itself has excellent availability.</span></span> <span data-ttu-id="e51ba-123">這應該是您需要考慮的事實。</span><span class="sxs-lookup"><span data-stu-id="e51ba-123">This should be a fact you need to consider.</span></span>

<span data-ttu-id="e51ba-124">如果您未設計及實作以確保容錯技術，甚至小停機可以幅度加大。</span><span class="sxs-lookup"><span data-stu-id="e51ba-124">If you do not design and implement techniques to ensure fault tolerance, even small downtimes can be amplified.</span></span> <span data-ttu-id="e51ba-125">為例，50 與相依性每個 99.99%的可用性可能會導致數小時停機時間的每個月，因為此產生漣漪效果。</span><span class="sxs-lookup"><span data-stu-id="e51ba-125">As an example, 50 dependencies each with 99.99% of availability would result in several hours of downtime each month because of this ripple effect.</span></span> <span data-ttu-id="e51ba-126">當微服務相依性失敗時處理大量的要求時，該失敗快速 saturate 中每個服務的所有可用的要求執行緒和整個應用程式會損毀。</span><span class="sxs-lookup"><span data-stu-id="e51ba-126">When a microservice dependency fails while handling a high volume of requests, that failure can quickly saturate all available request threads in each service and crash the whole application.</span></span>

![](./media/image3.png)

<span data-ttu-id="e51ba-127">**圖 10-3**。</span><span class="sxs-lookup"><span data-stu-id="e51ba-127">**Figure 10-3**.</span></span> <span data-ttu-id="e51ba-128">幅度加大 microservices 使用長的鏈結的同步 HTTP 呼叫的部分失敗</span><span class="sxs-lookup"><span data-stu-id="e51ba-128">Partial failure amplified by microservices with long chains of synchronous HTTP calls</span></span>

<span data-ttu-id="e51ba-129">若要減少此問題，一節中的"*非同步的微服務整合，強制執行 「 微服務的自主*」 （本章架構），我們建議您在內部使用的非同步通訊microservices。</span><span class="sxs-lookup"><span data-stu-id="e51ba-129">To minimize this problem, in the section "*Asynchronous microservice integration enforce microservice’s autonomy*” (in the architecture chapter), we encouraged you to use asynchronous communication across the internal microservices.</span></span> <span data-ttu-id="e51ba-130">我們簡要說明更下一節。</span><span class="sxs-lookup"><span data-stu-id="e51ba-130">We briefly explain more in the next section.</span></span>

<span data-ttu-id="e51ba-131">此外，務必您設計 microservices 和用戶端應用程式處理部分失敗 — 也就是建立具有恢復功能 microservices 和用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="e51ba-131">In addition, it is essential that you design your microservices and client applications to handle partial failures—that is, to build resilient microservices and client applications.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e51ba-132">[上一個](index.md) [下一步] (部分-失敗-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="e51ba-132">[Previous] (index.md) [Next] (partial-failure-strategies.md)</span></span>
