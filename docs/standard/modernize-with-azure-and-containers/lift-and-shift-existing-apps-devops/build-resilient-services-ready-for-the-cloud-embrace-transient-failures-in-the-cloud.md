---
title: "建立具有恢復功能服務就緒雲端。 運用雲端中的暫時性失敗"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |建立具有恢復功能服務就緒雲端。 運用雲端中的暫時性失敗"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eef0197edb3aba555da63f1ea0b75726a826bd32
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a><span data-ttu-id="184d4-105">建立具有恢復功能服務就緒定域機組： 面向的雲端中的暫時性失敗</span><span class="sxs-lookup"><span data-stu-id="184d4-105">Build resilient services ready for the cloud: Embrace transient failures in the cloud</span></span> 

<span data-ttu-id="184d4-106">「復原」是指能夠從失敗中復原並繼續運作的能力。</span><span class="sxs-lookup"><span data-stu-id="184d4-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="184d4-107">恢復功能不是關於避免失敗，但接受的事實，將會失敗，並再回應給它們的方式可避免停機時間或資料遺失。</span><span class="sxs-lookup"><span data-stu-id="184d4-107">Resiliency is not about avoiding failures, but accepting the fact that failures will occur, and then responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="184d4-108">復原的目標是在失敗後將應用程式返回完全運作的狀態。</span><span class="sxs-lookup"><span data-stu-id="184d4-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="184d4-109">您的應用程式可供雲端時最少，它會實作軟體為基礎的模型的恢復功能，而不是硬體為基礎的模型。</span><span class="sxs-lookup"><span data-stu-id="184d4-109">Your application is ready for the cloud when, at a minimum, it implements a software-based model of resiliency, rather than a hardware-based model.</span></span> <span data-ttu-id="184d4-110">您的雲端應用程式也必須不怕一定會發生部分失敗。</span><span class="sxs-lookup"><span data-stu-id="184d4-110">Your cloud application must embrace the partial failures that will certainly occur.</span></span> <span data-ttu-id="184d4-111">您要設計或部分重構您的應用程式，如果您想要達到預期的部分失敗的恢復功能。</span><span class="sxs-lookup"><span data-stu-id="184d4-111">You need to design or partially refactor your application if you want to achieve resiliency to expected partial failures.</span></span> <span data-ttu-id="184d4-112">它應該設計成處理部分失敗，例如暫時性網路中斷和節點或 Vm 雲端中損毀。</span><span class="sxs-lookup"><span data-stu-id="184d4-112">It should be designed to cope with partial failures, like transient network outages and nodes, or VMs crashing in the cloud.</span></span> <span data-ttu-id="184d4-113">即使正在移動至另一個節點 orchestrator 叢集內的容器可能會導致應用程式中的間歇性簡短失敗。</span><span class="sxs-lookup"><span data-stu-id="184d4-113">Even containers being moved to a different node within an orchestrator cluster can cause intermittent short failures within the application.</span></span>

## <a name="handling-partial-failure"></a><span data-ttu-id="184d4-114">處理部分失敗</span><span class="sxs-lookup"><span data-stu-id="184d4-114">Handling partial failure</span></span>

<span data-ttu-id="184d4-115">以雲端為基礎的應用程式，在沒有部分失敗無所不在風險。</span><span class="sxs-lookup"><span data-stu-id="184d4-115">In a cloud-based application, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="184d4-116">例如，單一網站執行個體或容器可能會失敗，或可能無法使用或沒有回應的短暫時間。</span><span class="sxs-lookup"><span data-stu-id="184d4-116">For instance, a single website instance or a container might fail, or it might be unavailable or unresponsive for a short time.</span></span> <span data-ttu-id="184d4-117">或者，在單一 VM 或伺服器可能會當機。</span><span class="sxs-lookup"><span data-stu-id="184d4-117">Or, a single VM or server might crash.</span></span>

<span data-ttu-id="184d4-118">用戶端和服務會個別處理序，因為服務可能無法及時回應至用戶端的要求。</span><span class="sxs-lookup"><span data-stu-id="184d4-118">Because clients and services are separate processes, a service might not be able to respond in a timely manner to a client's request.</span></span> <span data-ttu-id="184d4-119">服務可能會多載，並回應速度極為緩慢要求，或它可能只是無法存取一小段時間因為網路問題。</span><span class="sxs-lookup"><span data-stu-id="184d4-119">The service might be overloaded and respond extremely slowly to requests, or it might simply not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="184d4-120">例如，請考慮龐大的.NET 應用程式可存取 Azure SQL Database 中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="184d4-120">For example, consider a monolithic .NET application that accesses a database in Azure SQL Database.</span></span> <span data-ttu-id="184d4-121">如果 Azure SQL 資料庫或任何其他第三方服務沒有回應的簡短時間 （Azure SQL database 可能會移到另一個節點或伺服器，而且沒有回應數秒鐘），當使用者嘗試執行任何動作時，應用程式可能會當機並顯示w 完全相同的目前例外狀況。</span><span class="sxs-lookup"><span data-stu-id="184d4-121">If the Azure SQL database or any other third-party service is unresponsive for a brief time (an Azure SQL database might be moved to a different node or server, and be unresponsive for a few seconds), when the user tries to do any action, the application might crash and show an exception at the very same moment.</span></span>

<span data-ttu-id="184d4-122">使用 HTTP 服務的應用程式中，會發生類似的情況。</span><span class="sxs-lookup"><span data-stu-id="184d4-122">A similar scenario might occur in an app that consumes HTTP services.</span></span> <span data-ttu-id="184d4-123">網路或服務本身可能無法在雲端中簡短、 暫時性的失敗期間。</span><span class="sxs-lookup"><span data-stu-id="184d4-123">The network or the service itself might not be available in the cloud during a short, transient failure.</span></span>

<span data-ttu-id="184d4-124">具有恢復功能的應用程式，例如在圖 4 至 9 中所示應該實作 「 重試指數型輪詢使用 「 類似的技術，讓應用程式有機會處理資源中的暫時性失敗。</span><span class="sxs-lookup"><span data-stu-id="184d4-124">A resilient application like the one shown in Figure 4-9 should implement techniques like "retries with exponential backoff" to give the application an opportunity to handle transient failures in resources.</span></span> <span data-ttu-id="184d4-125">您也應該在應用程式中使用 「 斷路器 」。</span><span class="sxs-lookup"><span data-stu-id="184d4-125">You also should use "circuit breakers" in your applications.</span></span> <span data-ttu-id="184d4-126">斷路器就會停止應用程式嘗試存取資源時，它實際上長期失敗。</span><span class="sxs-lookup"><span data-stu-id="184d4-126">A circuit breaker stops an application from trying to access a resource when it's actually a long-term failure.</span></span> <span data-ttu-id="184d4-127">藉由使用斷路器，應用程式可避免誘發阻絕服務本身。</span><span class="sxs-lookup"><span data-stu-id="184d4-127">By using a circuit breaker, the application avoids provoking a denial of service to itself.</span></span>

![使用指數型輪詢的重試所處理的部分失敗](./media/image9.png)

> <span data-ttu-id="184d4-129">**圖 4 至 9。**</span><span class="sxs-lookup"><span data-stu-id="184d4-129">**Figure 4-9.**</span></span> <span data-ttu-id="184d4-130">使用指數型輪詢的重試所處理的部分失敗</span><span class="sxs-lookup"><span data-stu-id="184d4-130">Partial failures handled by retries with exponential backoff</span></span>

<span data-ttu-id="184d4-131">在 HTTP 資源和資料庫資源中，您可以使用這些技術。</span><span class="sxs-lookup"><span data-stu-id="184d4-131">You can use these techniques both in HTTP resources and in database resources.</span></span> <span data-ttu-id="184d4-132">在圖 4-9、 應用程式為基礎的 3 層式架構，因此您必須在服務層級 (HTTP) 和資料層級 (TCP)，這些技術。</span><span class="sxs-lookup"><span data-stu-id="184d4-132">In Figure 4-9, the application is based on a 3-tier architecture, so you need these techniques at the services level (HTTP) and at the data tier level (TCP).</span></span> <span data-ttu-id="184d4-133">在使用只除了資料庫 （沒有其他服務或 microservices） 的單一應用程式層的整合應用程式，處理暫時性資料庫連接層級的失敗可能不夠。</span><span class="sxs-lookup"><span data-stu-id="184d4-133">In a monolithic application that uses only a single app tier in addition to the database (no additional services or microservices), handling transient failures at the database connection level might be enough.</span></span> <span data-ttu-id="184d4-134">在這種情況下，通常只資料庫連接的特定組態則是必要項目。</span><span class="sxs-lookup"><span data-stu-id="184d4-134">In that scenario, usually just a particular configuration of the database connection is required.</span></span>

<span data-ttu-id="184d4-135">實作存取資料庫時，根據您使用的.NET 版本的彈性通訊時可能非常直接 (例如， [Entity Framework 6 或更新版本](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)，它是只需設定資料庫連接）。</span><span class="sxs-lookup"><span data-stu-id="184d4-135">When implementing resilient communications that access the database, depending on the version of .NET you are using, it can be very straightforward (for example, [with Entity Framework 6 or later](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), it's just a matter of configuring the database connection).</span></span> <span data-ttu-id="184d4-136">或者，您可能需要使用額外的程式庫，例如[暫時性錯誤處理應用程式區塊](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)（適用於舊版的.NET），或甚至會實作您自己的程式庫。</span><span class="sxs-lookup"><span data-stu-id="184d4-136">Or, you might need to use additional libraries like the [Transient Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (for earlier versions of .NET), or even implement your own library.</span></span>

<span data-ttu-id="184d4-137">實作 HTTP 重試與斷路器時，適用於.NET 的建議是使用[Polly](https://github.com/App-vNext/Polly)目標.NET 4.0、.NET 4.5 和.NET 標準 1.1 中，其中包含.NET Core 支援程式庫。</span><span class="sxs-lookup"><span data-stu-id="184d4-137">When implementing HTTP retries and circuit breakers, the recommendation for .NET is to use the [Polly](https://github.com/App-vNext/Polly) library, which targets .NET 4.0, .NET 4.5, and .NET Standard 1.1, which includes .NET Core support.</span></span>

<span data-ttu-id="184d4-138">若要深入了解如何實作的策略來處理在雲端中的部分失敗，請參閱下列參考。</span><span class="sxs-lookup"><span data-stu-id="184d4-138">To learn how to implement strategies for handling partial failures in the cloud, see the following references.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="184d4-139">其他資源</span><span class="sxs-lookup"><span data-stu-id="184d4-139">Additional resources</span></span>

-   <span data-ttu-id="184d4-140">**實作有彈性的通訊，來處理部分失敗**</span><span class="sxs-lookup"><span data-stu-id="184d4-140">**Implementing resilient communication to handle partial failure**</span></span>

    [<span data-ttu-id="184d4-141">https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies</span><span class="sxs-lookup"><span data-stu-id="184d4-141">https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies</span></span>](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

-   <span data-ttu-id="184d4-142">**Entity Framework 連接恢復功能和重試邏輯 （6 或更新版本）**</span><span class="sxs-lookup"><span data-stu-id="184d4-142">**Entity Framework connection resiliency and retry logic (version 6 and later)**</span></span>

    <span data-ttu-id="184d4-143">[https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)</span><span class="sxs-lookup"><span data-stu-id="184d4-143">[https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)</span></span>

-   <span data-ttu-id="184d4-144">**暫時性錯誤處理應用程式區塊**</span><span class="sxs-lookup"><span data-stu-id="184d4-144">**The Transient Fault Handling Application Block**</span></span>

-   <span data-ttu-id="184d4-145">[https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)</span><span class="sxs-lookup"><span data-stu-id="184d4-145">[https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)</span></span>

-   <span data-ttu-id="184d4-146">**具有恢復功能的 HTTP 通訊的 Polly 程式庫**</span><span class="sxs-lookup"><span data-stu-id="184d4-146">**Polly library for resilient HTTP communication**</span></span>

    <span data-ttu-id="184d4-147">https://github.com/App-vNext/Polly</span><span class="sxs-lookup"><span data-stu-id="184d4-147">https://github.com/App-vNext/Polly</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="184d4-148">[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[下一頁](modernize-your-apps-with-monitoring-and-telemetry.md)</span><span class="sxs-lookup"><span data-stu-id="184d4-148">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](modernize-your-apps-with-monitoring-and-telemetry.md)</span></span>
