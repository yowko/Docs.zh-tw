---
title: 打造適用于雲端的復原服務。 接受雲端中的暫時性失敗
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |打造適用于雲端的復原服務。 接受雲端中的暫時性失敗
ms.date: 04/30/2018
ms.openlocfilehash: 8e9f1eda71e4b98a56cbfc1c7a4ff34e67bee3f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172153"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a><span data-ttu-id="72905-105">建置準備好在雲端執行的彈性服務：接受雲端中的暫時性失敗</span><span class="sxs-lookup"><span data-stu-id="72905-105">Build resilient services ready for the cloud: Embrace transient failures in the cloud</span></span>

<span data-ttu-id="72905-106">復原是從失敗中復原並繼續運作的能力。</span><span class="sxs-lookup"><span data-stu-id="72905-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="72905-107">復原不是為了避免失敗，而是要接受失敗的事實，然後以避免停機或資料遺失的方式回應。</span><span class="sxs-lookup"><span data-stu-id="72905-107">Resiliency is not about avoiding failures, but accepting the fact that failures will occur, and then responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="72905-108">復原的目標是在失敗後將應用程式返回完全運作的狀態。</span><span class="sxs-lookup"><span data-stu-id="72905-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="72905-109">當您的應用程式至少會執行以軟體為基礎的復原模型，而不是以硬體為基礎的模型時，您的應用程式就已準備好使用雲端。</span><span class="sxs-lookup"><span data-stu-id="72905-109">Your application is ready for the cloud when, at a minimum, it implements a software-based model of resiliency, rather than a hardware-based model.</span></span> <span data-ttu-id="72905-110">您的雲端應用程式必須採用一定會發生的部分失敗。</span><span class="sxs-lookup"><span data-stu-id="72905-110">Your cloud application must embrace the partial failures that will certainly occur.</span></span> <span data-ttu-id="72905-111">設計或局部重構您的應用程式，以透過預期的部分失敗來達到復原能力。</span><span class="sxs-lookup"><span data-stu-id="72905-111">Design or partially refactor your application to achieve resiliency with expected partial failures.</span></span> <span data-ttu-id="72905-112">其設計目的是要處理部分失敗，例如暫時性的網路中斷和節點，或在雲端中損毀的 Vm。</span><span class="sxs-lookup"><span data-stu-id="72905-112">It should be designed to cope with partial failures, like transient network outages and nodes, or VMs crashing in the cloud.</span></span> <span data-ttu-id="72905-113">即使是移至 orchestrator 叢集中不同節點的容器，也可能會導致應用程式中發生間歇性的短暫失敗。</span><span class="sxs-lookup"><span data-stu-id="72905-113">Even containers being moved to a different node within an orchestrator cluster can cause intermittent short failures within the application.</span></span>

## <a name="handling-partial-failure"></a><span data-ttu-id="72905-114">處理部分失敗</span><span class="sxs-lookup"><span data-stu-id="72905-114">Handling partial failure</span></span>

<span data-ttu-id="72905-115">在雲端式應用程式中，有部分失敗的風險存在。</span><span class="sxs-lookup"><span data-stu-id="72905-115">In a cloud-based application, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="72905-116">比方說，單一網站實例或容器可能會失敗，或是短時間可能無法使用或沒有回應。</span><span class="sxs-lookup"><span data-stu-id="72905-116">For instance, a single website instance or a container might fail, or it might be unavailable or unresponsive for a short time.</span></span> <span data-ttu-id="72905-117">或者，單一 VM 或伺服器可能會損毀。</span><span class="sxs-lookup"><span data-stu-id="72905-117">Or, a single VM or server might crash.</span></span>

<span data-ttu-id="72905-118">由於用戶端和服務是不同的進程，因此服務可能無法及時回應用戶端的要求。</span><span class="sxs-lookup"><span data-stu-id="72905-118">Because clients and services are separate processes, a service might not be able to respond in a timely manner to a client's request.</span></span> <span data-ttu-id="72905-119">服務可能會多載且回應速度變慢，或可能因為網路問題而無法存取一小段時間。</span><span class="sxs-lookup"><span data-stu-id="72905-119">The service might be overloaded and respond slowly to requests, or it might not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="72905-120">例如，假設有一個可在 Azure SQL Database 中存取資料庫的整合型 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="72905-120">For example, consider a monolithic .NET application that accesses a database in Azure SQL Database.</span></span> <span data-ttu-id="72905-121">如果 Azure SQL database 或其他任何協力廠商服務沒有回應短暫的時間 (Azure SQL database 可能會移至不同的節點或伺服器，而且沒有回應幾秒鐘的時間) ，當使用者嘗試執行任何動作時，應用程式可能會損毀，並同時顯示例外狀況。</span><span class="sxs-lookup"><span data-stu-id="72905-121">If the Azure SQL database or any other third-party service is unresponsive for a brief time (an Azure SQL database might be moved to a different node or server, and be unresponsive for a few seconds), when the user tries to do any action, the application might crash and show an exception at the same moment.</span></span>

<span data-ttu-id="72905-122">使用 HTTP 服務的應用程式可能會發生類似的情況。</span><span class="sxs-lookup"><span data-stu-id="72905-122">A similar scenario might occur in an app that consumes HTTP services.</span></span> <span data-ttu-id="72905-123">在短暫的暫時性失敗期間，網路或服務本身可能無法在雲端中使用。</span><span class="sxs-lookup"><span data-stu-id="72905-123">The network or the service itself might not be available in the cloud during a short, transient failure.</span></span>

<span data-ttu-id="72905-124">如圖4-9 中所示的復原性應用程式應該採用「以指數輪詢重試」之類的技術，讓應用程式有機會處理資源中的暫時性失敗。</span><span class="sxs-lookup"><span data-stu-id="72905-124">A resilient application like the one shown in Figure 4-9 should implement techniques like "retries with exponential backoff" to give the application an opportunity to handle transient failures in resources.</span></span> <span data-ttu-id="72905-125">您也應該在您的應用程式中使用「斷路器」。</span><span class="sxs-lookup"><span data-stu-id="72905-125">You also should use "circuit breakers" in your applications.</span></span> <span data-ttu-id="72905-126">當應用程式實際上是長期失敗時，斷路器會阻止應用程式嘗試存取資源。</span><span class="sxs-lookup"><span data-stu-id="72905-126">A circuit breaker stops an application from trying to access a resource when it's actually a long-term failure.</span></span> <span data-ttu-id="72905-127">藉由使用斷路器，應用程式可避免誘發本身的拒絕服務。</span><span class="sxs-lookup"><span data-stu-id="72905-127">By using a circuit breaker, the application avoids provoking a denial of service to itself.</span></span>

![以指數輪詢重試所處理部分失敗的圖表。](./media/retry-partial-failures.png)

<span data-ttu-id="72905-129">**圖4-9。**</span><span class="sxs-lookup"><span data-stu-id="72905-129">**Figure 4-9.**</span></span> <span data-ttu-id="72905-130">以指數輪詢重試處理的部分失敗</span><span class="sxs-lookup"><span data-stu-id="72905-130">Partial failures handled by retries with exponential backoff</span></span>

<span data-ttu-id="72905-131">您可以在 HTTP 資源和資料庫資源中使用這些技術。</span><span class="sxs-lookup"><span data-stu-id="72905-131">You can use these techniques both in HTTP resources and in database resources.</span></span> <span data-ttu-id="72905-132">在圖4-9 中，應用程式是以三層架構為基礎，因此您在服務層級需要這些技術， (HTTP) 和資料層層級 (的 TCP) 。</span><span class="sxs-lookup"><span data-stu-id="72905-132">In Figure 4-9, the application is based on a 3-tier architecture, so you need these techniques at the services level (HTTP) and at the data tier level (TCP).</span></span> <span data-ttu-id="72905-133">在只使用單一應用層的整合型應用程式中， (沒有額外的服務或微服務) ，處理資料庫連接層級的暫時性失敗可能就已足夠。</span><span class="sxs-lookup"><span data-stu-id="72905-133">In a monolithic application that uses only a single app tier in addition to the database (no additional services or microservices), handling transient failures at the database connection level might be enough.</span></span> <span data-ttu-id="72905-134">在該情況下，只需要特定的資料庫連接設定。</span><span class="sxs-lookup"><span data-stu-id="72905-134">In that scenario, just a particular configuration of the database connection is required.</span></span>

<span data-ttu-id="72905-135">當您在執行可存取資料庫的復原通訊時，視您使用的 .NET 版本而定，它可以很簡單 (例如， [Entity Framework 6 或更新](/ef/ef6/fundamentals/connection-resiliency/retry-logic)版本。</span><span class="sxs-lookup"><span data-stu-id="72905-135">When implementing resilient communications that access the database, depending on the version of .NET you are using, it can be straightforward (for example, [with Entity Framework 6 or later](/ef/ef6/fundamentals/connection-resiliency/retry-logic).</span></span> <span data-ttu-id="72905-136">這只是設定資料庫連接) 。</span><span class="sxs-lookup"><span data-stu-id="72905-136">It's just a matter of configuring the database connection).</span></span> <span data-ttu-id="72905-137">或者，您可能需要使用其他程式庫（例如 [暫時性錯誤處理應用程式區塊](/previous-versions/msp-n-p/hh680934(v=pandp.50)) (針對舊版 .net) ），或甚至是執行您自己的程式庫。</span><span class="sxs-lookup"><span data-stu-id="72905-137">Or, you might need to use additional libraries like the [Transient Fault Handling Application Block](/previous-versions/msp-n-p/hh680934(v=pandp.50)) (for earlier versions of .NET), or even implement your own library.</span></span>

<span data-ttu-id="72905-138">當您執行 HTTP 重試和斷路器時，.NET 的建議是使用 [Polly](https://github.com/App-vNext/Polly) 程式庫，該程式庫的目標 .NET Framework 4.0、.NET Framework 4.5 和 .NET Standard 1.1，其中包括 .net Core 支援。</span><span class="sxs-lookup"><span data-stu-id="72905-138">When implementing HTTP retries and circuit breakers, the recommendation for .NET is to use the [Polly](https://github.com/App-vNext/Polly) library, which targets .NET Framework 4.0, .NET Framework 4.5, and .NET Standard 1.1, which includes .NET Core support.</span></span>

<span data-ttu-id="72905-139">若要瞭解如何在雲端中執行處理部分失敗的策略，請參閱下列參考。</span><span class="sxs-lookup"><span data-stu-id="72905-139">To learn how to implement strategies for handling partial failures in the cloud, see the following references.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="72905-140">其他資源</span><span class="sxs-lookup"><span data-stu-id="72905-140">Additional resources</span></span>

- <span data-ttu-id="72905-141">**執行復原通訊來處理部分失敗**</span><span class="sxs-lookup"><span data-stu-id="72905-141">**Implementing resilient communication to handle partial failure**</span></span>

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- <span data-ttu-id="72905-142">\*\*Entity Framework 連接復原和重試邏輯 (第6版和更新版本) \*\*</span><span class="sxs-lookup"><span data-stu-id="72905-142">**Entity Framework connection resiliency and retry logic (version 6 and later)**</span></span>

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- <span data-ttu-id="72905-143">**暫時性錯誤處理應用程式區塊**</span><span class="sxs-lookup"><span data-stu-id="72905-143">**The Transient Fault Handling Application Block**</span></span>

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- <span data-ttu-id="72905-144">**適用于復原 HTTP 通訊的 Polly 程式庫**</span><span class="sxs-lookup"><span data-stu-id="72905-144">**Polly library for resilient HTTP communication**</span></span>

    <https://github.com/App-vNext/Polly>

>[!div class="step-by-step"]
><span data-ttu-id="72905-145">[上一個](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md) 
>[下一步](modernize-your-apps-with-monitoring-and-telemetry.md)</span><span class="sxs-lookup"><span data-stu-id="72905-145">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](modernize-your-apps-with-monitoring-and-telemetry.md)</span></span>
