---
title: 雲端原生通訊模式
description: 瞭解雲端原生應用程式中的重要服務通訊考慮
author: robvet
ms.date: 08/31/2019
ms.openlocfilehash: 0123d2e3da1bf8df29efcf2595a38c377dd1d1a1
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183375"
---
# <a name="cloud-native-communication-patterns"></a><span data-ttu-id="adfe8-103">雲端原生通訊模式</span><span class="sxs-lookup"><span data-stu-id="adfe8-103">Cloud-native communication patterns</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="adfe8-104">在建立雲端原生系統時，通訊會成為重要的設計決策。</span><span class="sxs-lookup"><span data-stu-id="adfe8-104">When constructing a cloud-native system, communication becomes a significant design decision.</span></span> <span data-ttu-id="adfe8-105">前端用戶端應用程式如何與後端微服務通訊？</span><span class="sxs-lookup"><span data-stu-id="adfe8-105">How does a front-end client application communicate with a back-end microservice?</span></span> <span data-ttu-id="adfe8-106">後端微服務如何彼此通訊？</span><span class="sxs-lookup"><span data-stu-id="adfe8-106">How do back-end microservices communicate with each other?</span></span> <span data-ttu-id="adfe8-107">在雲端原生應用程式中執行通訊時，需要考慮哪些原則、模式和最佳作法？</span><span class="sxs-lookup"><span data-stu-id="adfe8-107">What are the principles, patterns, and best practices to consider when implementing communication in cloud-native applications?</span></span>

## <a name="communication-considerations"></a><span data-ttu-id="adfe8-108">通訊考慮</span><span class="sxs-lookup"><span data-stu-id="adfe8-108">Communication considerations</span></span>

<span data-ttu-id="adfe8-109">在整合型應用程式中，通訊非常簡單。</span><span class="sxs-lookup"><span data-stu-id="adfe8-109">In a monolithic application, communication is straightforward.</span></span> <span data-ttu-id="adfe8-110">程式碼模組會在伺服器上的同一個可執行空間（進程）中一起執行。</span><span class="sxs-lookup"><span data-stu-id="adfe8-110">The code modules execute together in the same executable space (process) on a server.</span></span> <span data-ttu-id="adfe8-111">當所有專案都在共用記憶體中一起執行時，這個方法可能會有效能上的優勢，但會產生緊密結合的程式碼，而變得很容易維護、演進和調整。</span><span class="sxs-lookup"><span data-stu-id="adfe8-111">This approach can have performance advantages as everything runs together in shared memory, but results in tightly coupled code that becomes difficult to maintain, evolve, and scale.</span></span>

<span data-ttu-id="adfe8-112">雲端原生系統會實微服務架構，其中包含許多小型、獨立的微服務。</span><span class="sxs-lookup"><span data-stu-id="adfe8-112">Cloud-native systems implement a microservice-based architecture with many small, independent microservices.</span></span> <span data-ttu-id="adfe8-113">每個微服務會在個別的進程中執行，且通常會在部署至叢集*的容器內執行。*</span><span class="sxs-lookup"><span data-stu-id="adfe8-113">Each microservice executes in a separate process and typically runs inside a container that is deployed to a *cluster*.</span></span> 

<span data-ttu-id="adfe8-114">叢集會將虛擬機器的集區群組在一起，以形成高可用性的環境。</span><span class="sxs-lookup"><span data-stu-id="adfe8-114">A cluster groups a pool of virtual machines together to form a highly available environment.</span></span> <span data-ttu-id="adfe8-115">它們是使用協調流程工具來管理，負責部署和管理容器化微服務。</span><span class="sxs-lookup"><span data-stu-id="adfe8-115">They're managed with an orchestration tool, which is responsible for deploying and managing the containerized microservices.</span></span> <span data-ttu-id="adfe8-116">圖4-1 顯示使用完全受控[Azure Kubernetes 服務](https://docs.microsoft.com/azure/aks/intro-kubernetes)部署到 azure 雲端的[Kubernetes](https://kubernetes.io)叢集。</span><span class="sxs-lookup"><span data-stu-id="adfe8-116">Figure 4-1 shows a [Kubernetes](https://kubernetes.io) cluster deployed into the Azure cloud with the fully managed [Azure Kubernetes Services](https://docs.microsoft.com/azure/aks/intro-kubernetes).</span></span>

![Azure 中的 Kubernetes 叢集](./media/kubernetes-cluster-in-azure.png)

<span data-ttu-id="adfe8-118">**圖 4-1**：</span><span class="sxs-lookup"><span data-stu-id="adfe8-118">**Figure 4-1**.</span></span> <span data-ttu-id="adfe8-119">Azure 中的 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="adfe8-119">A Kubernetes cluster in Azure</span></span>

<span data-ttu-id="adfe8-120">在整個叢集中，微服務透過 Api 和訊息技術彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="adfe8-120">Across the cluster, microservices communicate with each other through APIs and messaging technologies.</span></span>

<span data-ttu-id="adfe8-121">雖然它們提供許多優點，但微服務沒有免費的午餐。</span><span class="sxs-lookup"><span data-stu-id="adfe8-121">While they provide many benefits, microservices are no free lunch.</span></span> <span data-ttu-id="adfe8-122">元件之間的本機同進程方法呼叫現在已由網路呼叫取代。</span><span class="sxs-lookup"><span data-stu-id="adfe8-122">Local in-process method calls between components are now replaced with network calls.</span></span> <span data-ttu-id="adfe8-123">每個微服務都必須透過網路通訊協定進行通訊，這會增加系統的複雜度：</span><span class="sxs-lookup"><span data-stu-id="adfe8-123">Each microservice must communicate over a network protocol, which adds complexity to your system:</span></span>

- <span data-ttu-id="adfe8-124">網路擁塞、延遲和暫時性錯誤是一大考慮。</span><span class="sxs-lookup"><span data-stu-id="adfe8-124">Network congestion, latency, and transient faults are a constant concern.</span></span>

- <span data-ttu-id="adfe8-125">復原（也就是重試失敗的要求）是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="adfe8-125">Resiliency (that is, retrying failed requests) is essential.</span></span>

- <span data-ttu-id="adfe8-126">有些呼叫必須具有[等冪](https://www.restapitutorial.com/lessons/idempotency.html)性，才能保持一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="adfe8-126">Some calls must be [idempotent](https://www.restapitutorial.com/lessons/idempotency.html) as to keep consistent state.</span></span>

- <span data-ttu-id="adfe8-127">每個微服務都必須驗證和授權呼叫。</span><span class="sxs-lookup"><span data-stu-id="adfe8-127">Each microservice must authenticate and authorize calls.</span></span>

- <span data-ttu-id="adfe8-128">每個訊息都必須經過序列化，然後再還原序列化-這可能很耗費資源。</span><span class="sxs-lookup"><span data-stu-id="adfe8-128">Each message must be serialized and then deserialized - which can be expensive.</span></span>

- <span data-ttu-id="adfe8-129">訊息加密/解密變得很重要。</span><span class="sxs-lookup"><span data-stu-id="adfe8-129">Message encryption/decryption becomes important.</span></span>

<span data-ttu-id="adfe8-130">書籍[.net 微服務：容器化 .net 應用程式](https://docs.microsoft.com/dotnet/standard/microservices-architecture/)的架構（可從 Microsoft 免費取得）提供微服務應用程式通訊模式的深入涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="adfe8-130">The book [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture/), available for free from Microsoft, provides an in-depth coverage of communication patterns for microservice applications.</span></span> <span data-ttu-id="adfe8-131">在本章中，我們會提供這些模式的高階概述，以及 Azure 雲端中可用的實作為選項。</span><span class="sxs-lookup"><span data-stu-id="adfe8-131">In this chapter, we provide a high-level overview of these patterns along with implementation options available in the Azure cloud.</span></span>

<span data-ttu-id="adfe8-132">在本章中，我們會先解決前端應用程式與後端微服務之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="adfe8-132">In this chapter, we'll first address communication between front-end applications and back-end microservices.</span></span> <span data-ttu-id="adfe8-133">然後，我們將探討後端微服務彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="adfe8-133">We'll then look at back-end microservices communicate with each other.</span></span> <span data-ttu-id="adfe8-134">我們將探討 up 和 gRPC 通訊技術。</span><span class="sxs-lookup"><span data-stu-id="adfe8-134">We'll explore the up and gRPC communication technology.</span></span> <span data-ttu-id="adfe8-135">最後，我們將使用服務網格技術來探討新的創新通訊模式。</span><span class="sxs-lookup"><span data-stu-id="adfe8-135">Finally, we'll look new innovative communication patterns using service mesh technology.</span></span> <span data-ttu-id="adfe8-136">我們也將瞭解 Azure 雲端如何提供不同種類的支援*服務*，以支援雲端原生通訊。</span><span class="sxs-lookup"><span data-stu-id="adfe8-136">We'll also see how the Azure cloud provides different kinds of *backing services* to support cloud-native communication.</span></span>  


>[!div class="step-by-step"]
><span data-ttu-id="adfe8-137">[上一頁](other-deployment-options.md)
>[下一頁](front-end-communication.md)</span><span class="sxs-lookup"><span data-stu-id="adfe8-137">[Previous](other-deployment-options.md)
[Next](front-end-communication.md)</span></span>
