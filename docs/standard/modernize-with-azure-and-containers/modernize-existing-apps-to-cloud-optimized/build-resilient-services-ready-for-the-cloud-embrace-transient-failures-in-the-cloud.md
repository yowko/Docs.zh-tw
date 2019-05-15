---
title: 建置開始使用雲端的復原服務。 接受雲端中的暫時性失敗
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |建置開始使用雲端的復原服務。 接受雲端中的暫時性失敗
ms.date: 04/30/2018
ms.openlocfilehash: ca5d5e0c3af772ac52a02894c96889c776cf7d48
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643729"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a><span data-ttu-id="7a124-105">建置準備好在雲端執行的彈性服務：接受雲端中的暫時性失敗</span><span class="sxs-lookup"><span data-stu-id="7a124-105">Build resilient services ready for the cloud: Embrace transient failures in the cloud</span></span>

<span data-ttu-id="7a124-106">「復原」是指能夠從失敗中復原並繼續運作的能力。</span><span class="sxs-lookup"><span data-stu-id="7a124-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="7a124-107">復原不是關於避免失敗，但接受，將會失敗，事實，然後回應它們以避免停機或資料遺失的方式。</span><span class="sxs-lookup"><span data-stu-id="7a124-107">Resiliency is not about avoiding failures, but accepting the fact that failures will occur, and then responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="7a124-108">復原的目標是在失敗後將應用程式返回完全運作的狀態。</span><span class="sxs-lookup"><span data-stu-id="7a124-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="7a124-109">您的應用程式時，開始使用雲端，最小值，它會實作的復原能力，以軟體為基礎的模型，而不是以硬體為基礎的模型。</span><span class="sxs-lookup"><span data-stu-id="7a124-109">Your application is ready for the cloud when, at a minimum, it implements a software-based model of resiliency, rather than a hardware-based model.</span></span> <span data-ttu-id="7a124-110">您的雲端應用程式必須不怕當然就會發生部分失敗。</span><span class="sxs-lookup"><span data-stu-id="7a124-110">Your cloud application must embrace the partial failures that will certainly occur.</span></span> <span data-ttu-id="7a124-111">設計或部分重構您的應用程式，以達到預期的部分失敗的恢復功能。</span><span class="sxs-lookup"><span data-stu-id="7a124-111">Design or partially refactor your application to achieve resiliency with expected partial failures.</span></span> <span data-ttu-id="7a124-112">它應該設計成能夠回應部分失敗，例如暫時性網路中斷和節點或在雲端中損毀的 Vm。</span><span class="sxs-lookup"><span data-stu-id="7a124-112">It should be designed to cope with partial failures, like transient network outages and nodes, or VMs crashing in the cloud.</span></span> <span data-ttu-id="7a124-113">移至不同的節點，協調器叢集內的平均容器可能會導致在應用程式中的間歇性短暫性失敗。</span><span class="sxs-lookup"><span data-stu-id="7a124-113">Even containers being moved to a different node within an orchestrator cluster can cause intermittent short failures within the application.</span></span>

## <a name="handling-partial-failure"></a><span data-ttu-id="7a124-114">處理部分失敗</span><span class="sxs-lookup"><span data-stu-id="7a124-114">Handling partial failure</span></span>

<span data-ttu-id="7a124-115">在雲端為基礎的應用程式，則部分失敗的風險無所不在。</span><span class="sxs-lookup"><span data-stu-id="7a124-115">In a cloud-based application, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="7a124-116">比方說，單一網站執行個體或容器可能會失敗，或可能無法使用或無回應一小段時間。</span><span class="sxs-lookup"><span data-stu-id="7a124-116">For instance, a single website instance or a container might fail, or it might be unavailable or unresponsive for a short time.</span></span> <span data-ttu-id="7a124-117">或者，您也可以在單一 VM 或伺服器可能會當機。</span><span class="sxs-lookup"><span data-stu-id="7a124-117">Or, a single VM or server might crash.</span></span>

<span data-ttu-id="7a124-118">用戶端和服務是不同的處理序，因為服務可能無法及時回應用戶端的要求。</span><span class="sxs-lookup"><span data-stu-id="7a124-118">Because clients and services are separate processes, a service might not be able to respond in a timely manner to a client's request.</span></span> <span data-ttu-id="7a124-119">服務可能會多載，並回應變慢的要求，或它可能無法存取一小段時間因為網路問題。</span><span class="sxs-lookup"><span data-stu-id="7a124-119">The service might be overloaded and respond slowly to requests, or it might not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="7a124-120">例如，請考慮單體式的.NET 應用程式可存取 Azure SQL Database 中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="7a124-120">For example, consider a monolithic .NET application that accesses a database in Azure SQL Database.</span></span> <span data-ttu-id="7a124-121">如果 Azure SQL database 或任何其他第三方服務沒有回應的簡短時間 （Azure SQL database 可能會移到另一個節點或伺服器，而且沒有回應幾秒鐘的時間），當使用者嘗試執行任何動作時，應用程式可能會當機和顯示w 在相同時間點發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7a124-121">If the Azure SQL database or any other third-party service is unresponsive for a brief time (an Azure SQL database might be moved to a different node or server, and be unresponsive for a few seconds), when the user tries to do any action, the application might crash and show an exception at the same moment.</span></span>

<span data-ttu-id="7a124-122">使用 HTTP 服務的應用程式可能會發生類似的狀況。</span><span class="sxs-lookup"><span data-stu-id="7a124-122">A similar scenario might occur in an app that consumes HTTP services.</span></span> <span data-ttu-id="7a124-123">網路或服務本身可能無法在雲端中簡短的暫時性失敗。</span><span class="sxs-lookup"><span data-stu-id="7a124-123">The network or the service itself might not be available in the cloud during a short, transient failure.</span></span>

<span data-ttu-id="7a124-124">靈活的應用程式，在圖 4-9 所示應該實作 「 使用指數輪詢重試 」 等技術，以讓應用程式有機會處理暫時性失敗的資源。</span><span class="sxs-lookup"><span data-stu-id="7a124-124">A resilient application like the one shown in Figure 4-9 should implement techniques like "retries with exponential backoff" to give the application an opportunity to handle transient failures in resources.</span></span> <span data-ttu-id="7a124-125">您也應該在應用程式中使用 「 斷路器 」。</span><span class="sxs-lookup"><span data-stu-id="7a124-125">You also should use "circuit breakers" in your applications.</span></span> <span data-ttu-id="7a124-126">斷路器會停止應用程式嘗試存取資源時實際長期失敗。</span><span class="sxs-lookup"><span data-stu-id="7a124-126">A circuit breaker stops an application from trying to access a resource when it's actually a long-term failure.</span></span> <span data-ttu-id="7a124-127">藉由使用斷路器，應用程式可避免誘發阻絕服務本身。</span><span class="sxs-lookup"><span data-stu-id="7a124-127">By using a circuit breaker, the application avoids provoking a denial of service to itself.</span></span>

![使用指數輪詢重試處理部分失敗](./media/image9.png)

> <span data-ttu-id="7a124-129">**圖 4 至 9。**</span><span class="sxs-lookup"><span data-stu-id="7a124-129">**Figure 4-9.**</span></span> <span data-ttu-id="7a124-130">使用指數輪詢重試處理部分失敗</span><span class="sxs-lookup"><span data-stu-id="7a124-130">Partial failures handled by retries with exponential backoff</span></span>

<span data-ttu-id="7a124-131">在 HTTP 資源和資料庫資源，您可以使用這些技術。</span><span class="sxs-lookup"><span data-stu-id="7a124-131">You can use these techniques both in HTTP resources and in database resources.</span></span> <span data-ttu-id="7a124-132">在 圖 4-9、 應用程式根據 3 層式架構，因此您必須在服務層級 (HTTP) 和資料層級 (TCP)，這些技術。</span><span class="sxs-lookup"><span data-stu-id="7a124-132">In Figure 4-9, the application is based on a 3-tier architecture, so you need these techniques at the services level (HTTP) and at the data tier level (TCP).</span></span> <span data-ttu-id="7a124-133">使用只單一應用程式層除了資料庫 （不含其他服務或微服務） 的整合型應用程式，在處理暫時性失敗，資料庫層級的連線可能就足夠了。</span><span class="sxs-lookup"><span data-stu-id="7a124-133">In a monolithic application that uses only a single app tier in addition to the database (no additional services or microservices), handling transient failures at the database connection level might be enough.</span></span> <span data-ttu-id="7a124-134">在此情況下，只是資料庫連接的特定組態則是必要項目。</span><span class="sxs-lookup"><span data-stu-id="7a124-134">In that scenario, just a particular configuration of the database connection is required.</span></span>

<span data-ttu-id="7a124-135">實作具有恢復功能存取資料庫時，根據您使用的.NET 版本的通訊時可能很簡單 (例如[Entity Framework 6 或更新版本](/ef/ef6/fundamentals/connection-resiliency/retry-logic)。</span><span class="sxs-lookup"><span data-stu-id="7a124-135">When implementing resilient communications that access the database, depending on the version of .NET you are using, it can be straightforward (for example, [with Entity Framework 6 or later](/ef/ef6/fundamentals/connection-resiliency/retry-logic).</span></span> <span data-ttu-id="7a124-136">它是只需設定資料庫連接）。</span><span class="sxs-lookup"><span data-stu-id="7a124-136">It's just a matter of configuring the database connection).</span></span> <span data-ttu-id="7a124-137">或者，您可能需要使用額外的程式庫，例如[暫時性錯誤處理應用程式區塊](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50))（適用於舊版的.NET），或甚至是實作您自己的程式庫。</span><span class="sxs-lookup"><span data-stu-id="7a124-137">Or, you might need to use additional libraries like the [Transient Fault Handling Application Block](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (for earlier versions of .NET), or even implement your own library.</span></span>

<span data-ttu-id="7a124-138">實作 HTTP 重試與斷路器時，適用於.NET 的建議是使用[Polly](https://github.com/App-vNext/Polly)目標.NET Framework 4.0，.NET Framework 4.5 和.NET Standard 1.1 中，其中包含.NET Core 支援程式庫。</span><span class="sxs-lookup"><span data-stu-id="7a124-138">When implementing HTTP retries and circuit breakers, the recommendation for .NET is to use the [Polly](https://github.com/App-vNext/Polly) library, which targets .NET Framework 4.0, .NET Framework 4.5, and .NET Standard 1.1, which includes .NET Core support.</span></span>

<span data-ttu-id="7a124-139">若要了解如何實作的策略來處理雲端中的部分失敗，請參閱下列參考。</span><span class="sxs-lookup"><span data-stu-id="7a124-139">To learn how to implement strategies for handling partial failures in the cloud, see the following references.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7a124-140">其他資源</span><span class="sxs-lookup"><span data-stu-id="7a124-140">Additional resources</span></span>

- <span data-ttu-id="7a124-141">**實作具有恢復功能的通訊，來處理部分失敗**</span><span class="sxs-lookup"><span data-stu-id="7a124-141">**Implementing resilient communication to handle partial failure**</span></span>

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

- <span data-ttu-id="7a124-142">**Entity Framework 連接恢復功能和重試邏輯 （6 或更新版本）**</span><span class="sxs-lookup"><span data-stu-id="7a124-142">**Entity Framework connection resiliency and retry logic (version 6 and later)**</span></span>

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- <span data-ttu-id="7a124-143">**暫時性錯誤處理應用程式區塊**</span><span class="sxs-lookup"><span data-stu-id="7a124-143">**The Transient Fault Handling Application Block**</span></span>

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- <span data-ttu-id="7a124-144">**Polly 程式庫，適用於具有恢復功能的 HTTP 通訊**</span><span class="sxs-lookup"><span data-stu-id="7a124-144">**Polly library for resilient HTTP communication**</span></span>

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
><span data-ttu-id="7a124-145">[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[下一頁](modernize-your-apps-with-monitoring-and-telemetry.md)</span><span class="sxs-lookup"><span data-stu-id="7a124-145">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](modernize-your-apps-with-monitoring-and-telemetry.md)</span></span>
