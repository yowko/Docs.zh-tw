---
title: 構建為雲做好準備的彈性服務。 接受雲端中的暫時性失敗
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |構建為雲做好準備的彈性服務。 接受雲端中的暫時性失敗
ms.date: 04/30/2018
ms.openlocfilehash: e516dc675ceb8def25c6d676bced0ea7f253b2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711253"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a><span data-ttu-id="a7421-105">建置可用於雲端的復原服務：包含雲端中的暫時性失敗</span><span class="sxs-lookup"><span data-stu-id="a7421-105">Build resilient services ready for the cloud: Embrace transient failures in the cloud</span></span>

<span data-ttu-id="a7421-106">復原是從失敗中復原並繼續運作的能力。</span><span class="sxs-lookup"><span data-stu-id="a7421-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="a7421-107">恢復能力不是要避免故障，而是接受失敗將發生的事實，然後以避免停機或資料丟失的方式回應它們。</span><span class="sxs-lookup"><span data-stu-id="a7421-107">Resiliency is not about avoiding failures, but accepting the fact that failures will occur, and then responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="a7421-108">復原的目標是在失敗後將應用程式返回完全運作的狀態。</span><span class="sxs-lookup"><span data-stu-id="a7421-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="a7421-109">應用程式至少實現了基於軟體的恢復能力模型（而不是基於硬體的模型）即可訪問雲。</span><span class="sxs-lookup"><span data-stu-id="a7421-109">Your application is ready for the cloud when, at a minimum, it implements a software-based model of resiliency, rather than a hardware-based model.</span></span> <span data-ttu-id="a7421-110">您的雲應用程式必須接受肯定會發生的部分故障。</span><span class="sxs-lookup"><span data-stu-id="a7421-110">Your cloud application must embrace the partial failures that will certainly occur.</span></span> <span data-ttu-id="a7421-111">設計或部分重構應用程式，以在預期部分故障時實現彈性。</span><span class="sxs-lookup"><span data-stu-id="a7421-111">Design or partially refactor your application to achieve resiliency with expected partial failures.</span></span> <span data-ttu-id="a7421-112">它應設計為可應對部分故障，如瞬態網路中斷和節點，或雲中崩潰的 VM。</span><span class="sxs-lookup"><span data-stu-id="a7421-112">It should be designed to cope with partial failures, like transient network outages and nodes, or VMs crashing in the cloud.</span></span> <span data-ttu-id="a7421-113">即使容器移動到協調器群集中的其他節點也可能導致應用程式中間歇性短路故障。</span><span class="sxs-lookup"><span data-stu-id="a7421-113">Even containers being moved to a different node within an orchestrator cluster can cause intermittent short failures within the application.</span></span>

## <a name="handling-partial-failure"></a><span data-ttu-id="a7421-114">處理部分失敗</span><span class="sxs-lookup"><span data-stu-id="a7421-114">Handling partial failure</span></span>

<span data-ttu-id="a7421-115">在基於雲的應用程式中，存在部分故障的風險。</span><span class="sxs-lookup"><span data-stu-id="a7421-115">In a cloud-based application, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="a7421-116">例如，單個網站實例或容器可能會失敗，或者它可能在短時間內不可用或無回應。</span><span class="sxs-lookup"><span data-stu-id="a7421-116">For instance, a single website instance or a container might fail, or it might be unavailable or unresponsive for a short time.</span></span> <span data-ttu-id="a7421-117">或者，單個 VM 或伺服器可能會崩潰。</span><span class="sxs-lookup"><span data-stu-id="a7421-117">Or, a single VM or server might crash.</span></span>

<span data-ttu-id="a7421-118">由於用戶端和服務是單獨的進程，因此服務可能無法及時回應用戶端的請求。</span><span class="sxs-lookup"><span data-stu-id="a7421-118">Because clients and services are separate processes, a service might not be able to respond in a timely manner to a client's request.</span></span> <span data-ttu-id="a7421-119">服務可能超載並緩慢回應請求，或者由於網路問題，該服務可能在短時間內無法訪問。</span><span class="sxs-lookup"><span data-stu-id="a7421-119">The service might be overloaded and respond slowly to requests, or it might not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="a7421-120">例如，考慮訪問 Azure SQL 資料庫中資料庫的單片 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7421-120">For example, consider a monolithic .NET application that accesses a database in Azure SQL Database.</span></span> <span data-ttu-id="a7421-121">如果 Azure SQL 資料庫或任何其他協力廠商服務在一段時間內無回應（Azure SQL 資料庫可能移動到其他節點或伺服器，並且無回應幾秒鐘），當使用者嘗試執行任何操作時，應用程式可能會崩潰和在同一時刻顯示異常。</span><span class="sxs-lookup"><span data-stu-id="a7421-121">If the Azure SQL database or any other third-party service is unresponsive for a brief time (an Azure SQL database might be moved to a different node or server, and be unresponsive for a few seconds), when the user tries to do any action, the application might crash and show an exception at the same moment.</span></span>

<span data-ttu-id="a7421-122">在使用 HTTP 服務的應用中可能會出現類似的情況。</span><span class="sxs-lookup"><span data-stu-id="a7421-122">A similar scenario might occur in an app that consumes HTTP services.</span></span> <span data-ttu-id="a7421-123">在短暫的瞬態故障期間，網路或服務本身可能在雲中不可用。</span><span class="sxs-lookup"><span data-stu-id="a7421-123">The network or the service itself might not be available in the cloud during a short, transient failure.</span></span>

<span data-ttu-id="a7421-124">如圖 4-9 所示的彈性應用程式應實現"使用指數回退重試"等技術，使應用程式有機會處理資源中的瞬態故障。</span><span class="sxs-lookup"><span data-stu-id="a7421-124">A resilient application like the one shown in Figure 4-9 should implement techniques like "retries with exponential backoff" to give the application an opportunity to handle transient failures in resources.</span></span> <span data-ttu-id="a7421-125">您還應在應用程式中使用"斷路器"。</span><span class="sxs-lookup"><span data-stu-id="a7421-125">You also should use "circuit breakers" in your applications.</span></span> <span data-ttu-id="a7421-126">斷路器阻止應用程式嘗試訪問資源時，它實際上是一個長期故障。</span><span class="sxs-lookup"><span data-stu-id="a7421-126">A circuit breaker stops an application from trying to access a resource when it's actually a long-term failure.</span></span> <span data-ttu-id="a7421-127">通過使用斷路器，應用程式避免了引發對自身的拒絕服務。</span><span class="sxs-lookup"><span data-stu-id="a7421-127">By using a circuit breaker, the application avoids provoking a denial of service to itself.</span></span>

![通過使用指數回退重試處理的部分故障圖。](./media/retry-partial-failures.png)

<span data-ttu-id="a7421-129">**圖 4-9。**</span><span class="sxs-lookup"><span data-stu-id="a7421-129">**Figure 4-9.**</span></span> <span data-ttu-id="a7421-130">通過使用指數回退重試處理的部分故障</span><span class="sxs-lookup"><span data-stu-id="a7421-130">Partial failures handled by retries with exponential backoff</span></span>

<span data-ttu-id="a7421-131">您可以在 HTTP 資源和資料庫資源中使用這些技術。</span><span class="sxs-lookup"><span data-stu-id="a7421-131">You can use these techniques both in HTTP resources and in database resources.</span></span> <span data-ttu-id="a7421-132">在圖 4-9 中，應用程式基於 3 層體系結構，因此您需要在服務等級 （HTTP） 和資料層級別 （TCP） 使用這些技術。</span><span class="sxs-lookup"><span data-stu-id="a7421-132">In Figure 4-9, the application is based on a 3-tier architecture, so you need these techniques at the services level (HTTP) and at the data tier level (TCP).</span></span> <span data-ttu-id="a7421-133">在除了資料庫（沒有其他服務或微服務）之外僅使用單個應用層的單一應用程式中，在資料庫連接級別處理瞬態故障可能就足夠了。</span><span class="sxs-lookup"><span data-stu-id="a7421-133">In a monolithic application that uses only a single app tier in addition to the database (no additional services or microservices), handling transient failures at the database connection level might be enough.</span></span> <span data-ttu-id="a7421-134">在這種情況下，只需要資料庫連接的特定配置。</span><span class="sxs-lookup"><span data-stu-id="a7421-134">In that scenario, just a particular configuration of the database connection is required.</span></span>

<span data-ttu-id="a7421-135">實現訪問資料庫的彈性通信時，根據正在使用的 .NET 版本，它非常簡單（例如，[使用實體框架 6 或更高版本](/ef/ef6/fundamentals/connection-resiliency/retry-logic)）。</span><span class="sxs-lookup"><span data-stu-id="a7421-135">When implementing resilient communications that access the database, depending on the version of .NET you are using, it can be straightforward (for example, [with Entity Framework 6 or later](/ef/ef6/fundamentals/connection-resiliency/retry-logic).</span></span> <span data-ttu-id="a7421-136">這只是設定資料庫連接的問題）。</span><span class="sxs-lookup"><span data-stu-id="a7421-136">It's just a matter of configuring the database connection).</span></span> <span data-ttu-id="a7421-137">或者，您可能需要使用其他庫，如[瞬態故障處理應用程式塊](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50))（對於早期版本的 .NET），甚至實現您自己的庫。</span><span class="sxs-lookup"><span data-stu-id="a7421-137">Or, you might need to use additional libraries like the [Transient Fault Handling Application Block](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (for earlier versions of .NET), or even implement your own library.</span></span>

<span data-ttu-id="a7421-138">在實現 HTTP 重試和斷路器時，建議 .NET 使用[Polly](https://github.com/App-vNext/Polly)庫，該庫的目標是 .NET 框架 4.0、.NET 框架 4.5 和 .NET 標準 1.1，其中包括 .NET 核心支援。</span><span class="sxs-lookup"><span data-stu-id="a7421-138">When implementing HTTP retries and circuit breakers, the recommendation for .NET is to use the [Polly](https://github.com/App-vNext/Polly) library, which targets .NET Framework 4.0, .NET Framework 4.5, and .NET Standard 1.1, which includes .NET Core support.</span></span>

<span data-ttu-id="a7421-139">要瞭解如何實施處理雲中部分故障的策略，請參閱以下參考。</span><span class="sxs-lookup"><span data-stu-id="a7421-139">To learn how to implement strategies for handling partial failures in the cloud, see the following references.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a7421-140">其他資源</span><span class="sxs-lookup"><span data-stu-id="a7421-140">Additional resources</span></span>

- <span data-ttu-id="a7421-141">**實現彈性通信以處理部分故障**</span><span class="sxs-lookup"><span data-stu-id="a7421-141">**Implementing resilient communication to handle partial failure**</span></span>

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- <span data-ttu-id="a7421-142">**實體框架連接恢復性和重試邏輯（版本 6 及更高版本）**</span><span class="sxs-lookup"><span data-stu-id="a7421-142">**Entity Framework connection resiliency and retry logic (version 6 and later)**</span></span>

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- <span data-ttu-id="a7421-143">**暫時性錯誤處理應用程式區塊**</span><span class="sxs-lookup"><span data-stu-id="a7421-143">**The Transient Fault Handling Application Block**</span></span>

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- <span data-ttu-id="a7421-144">**用於彈性 HTTP 通信的波利庫**</span><span class="sxs-lookup"><span data-stu-id="a7421-144">**Polly library for resilient HTTP communication**</span></span>

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
><span data-ttu-id="a7421-145">[上一個](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[下一個](modernize-your-apps-with-monitoring-and-telemetry.md)</span><span class="sxs-lookup"><span data-stu-id="a7421-145">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](modernize-your-apps-with-monitoring-and-telemetry.md)</span></span>
