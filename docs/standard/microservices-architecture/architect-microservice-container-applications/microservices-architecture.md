---
title: 微服務架構
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 微服務架構
keywords: Docker, 微服務, ASP.NET, 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 78d3903e7ed4abf27e78812de87ccbcb9f733663
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="microservices-architecture"></a><span data-ttu-id="81845-104">微服務架構</span><span class="sxs-lookup"><span data-stu-id="81845-104">Microservices architecture</span></span>

<span data-ttu-id="81845-105">如名稱所指，微服務架構是將伺服器應用程式建置為一組小型服務的方法。</span><span class="sxs-lookup"><span data-stu-id="81845-105">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="81845-106">每個服務會在自己的處理序中執行，並使用 HTTP/HTTPS、WebSocket 或 [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) 等通訊協定與其他處理序通訊。</span><span class="sxs-lookup"><span data-stu-id="81845-106">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="81845-107">每個微服務都會在特定內容界限內實作特定端對端領域或商務功能，而且每個微服務都必須自主開發並可獨立部署。</span><span class="sxs-lookup"><span data-stu-id="81845-107">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="81845-108">最後，根據不同的資料儲存技術 (SQL、NoSQL) 及不同的程式設計語言，每個微服務都應該擁有其相關的領域資料模型和領域邏輯 (主權和非集中式資料管理)。</span><span class="sxs-lookup"><span data-stu-id="81845-108">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="81845-109">微服務的大小應該為何？</span><span class="sxs-lookup"><span data-stu-id="81845-109">What size should a microservice be?</span></span> <span data-ttu-id="81845-110">開發微服務時，大小不應該是重點。</span><span class="sxs-lookup"><span data-stu-id="81845-110">When developing a microservice, size should not be the important point.</span></span> <span data-ttu-id="81845-111">相反地，重點應該是建立鬆散結合的服務，以便每個服務都能自主開發、部署及擴充。</span><span class="sxs-lookup"><span data-stu-id="81845-111">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="81845-112">當然，識別及設計微服務時，只要與其他微服務沒有太多直接相依性，都應該嘗試使其越小越好。</span><span class="sxs-lookup"><span data-stu-id="81845-112">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you do not have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="81845-113">比微服務大小更重要的是，它必須有內部凝聚力，而且獨立於其他服務。</span><span class="sxs-lookup"><span data-stu-id="81845-113">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="81845-114">為什麼選擇微服務架構？</span><span class="sxs-lookup"><span data-stu-id="81845-114">Why a microservices architecture?</span></span> <span data-ttu-id="81845-115">簡單來說，它提供長期靈活度。</span><span class="sxs-lookup"><span data-stu-id="81845-115">In short, it provides long-term agility.</span></span> <span data-ttu-id="81845-116">微服務可讓您建立以許多可獨立部署之服務為基礎的應用程式，而且每個服務會有細微且自主的生命週期，藉此提高複雜、大型且可高度擴充之系統的管理能力。</span><span class="sxs-lookup"><span data-stu-id="81845-116">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="81845-117">另一個優點是微服務可以獨立擴充。</span><span class="sxs-lookup"><span data-stu-id="81845-117">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="81845-118">您不需要具有必須以單位擴充的單一整合型應用程式，您可以改為擴充特定微服務。</span><span class="sxs-lookup"><span data-stu-id="81845-118">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="81845-119">這樣一來，您就可以只擴充需要更多處理能力或網路頻寬的功能區域來支援需求，而不是擴充不需要擴充的其他應用程式區域。</span><span class="sxs-lookup"><span data-stu-id="81845-119">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that do not need to be scaled.</span></span> <span data-ttu-id="81845-120">由於需要較少的硬體，因此會為您節省成本。</span><span class="sxs-lookup"><span data-stu-id="81845-120">That means cost savings because you need less hardware.</span></span>

![](./media/image6.png)

<span data-ttu-id="81845-121">**圖 4-6**：</span><span class="sxs-lookup"><span data-stu-id="81845-121">**Figure 4-6**.</span></span> <span data-ttu-id="81845-122">整合型部署與微服務方法</span><span class="sxs-lookup"><span data-stu-id="81845-122">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="81845-123">如圖 4-6 所示，微服務方法可彈性變更及快速反覆執行每個微服務，因為您可以變更複雜、大型且可擴充之應用程式的特定一小部分。</span><span class="sxs-lookup"><span data-stu-id="81845-123">As Figure 4-6 shows, the microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="81845-124">架構更細緻的微服務架構應用程式可進行持續整合與持續傳遞實務。</span><span class="sxs-lookup"><span data-stu-id="81845-124">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="81845-125">它也會加速將新功能傳遞到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="81845-125">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="81845-126">應用程式的更細緻組合也可讓您隔離執行及測試微服務，以及自主發展微服務，同時確保這些服務之間有清楚的合約。</span><span class="sxs-lookup"><span data-stu-id="81845-126">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="81845-127">只要您未變更介面或合約，您就可以變更任何微服務的內部實作或新增功能，而不會中斷其他微服務。</span><span class="sxs-lookup"><span data-stu-id="81845-127">As long as you do not change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="81845-128">以下是使用微服務架構系統成功進入生產環境的重點：</span><span class="sxs-lookup"><span data-stu-id="81845-128">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

-   <span data-ttu-id="81845-129">服務和基礎結構的監視和健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="81845-129">Monitoring and health checks of the services and infrastructure.</span></span>

-   <span data-ttu-id="81845-130">服務 (也就是雲端和協調器) 的可擴充基礎結構。</span><span class="sxs-lookup"><span data-stu-id="81845-130">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

-   <span data-ttu-id="81845-131">多個層級的安全性設計和實作：驗證、授權、秘密管理、安全通訊等等。</span><span class="sxs-lookup"><span data-stu-id="81845-131">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

-   <span data-ttu-id="81845-132">快速傳遞應用程式，通常有不同的小組著重於不同的微服務。</span><span class="sxs-lookup"><span data-stu-id="81845-132">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

-   <span data-ttu-id="81845-133">DevOps 與 CI/CD 的實務和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="81845-133">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="81845-134">本指南只會涵蓋或介紹其中的前三點。</span><span class="sxs-lookup"><span data-stu-id="81845-134">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="81845-135">最後兩點與應用程式生命週期相關，其他電子書 [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (利用 Microsoft 平台和工具的容器化 Docker 應用程式生命週期) 中會提供說明。</span><span class="sxs-lookup"><span data-stu-id="81845-135">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="81845-136">其他資源</span><span class="sxs-lookup"><span data-stu-id="81845-136">Additional resources</span></span>

-   <span data-ttu-id="81845-137">**Mark Russinovich：微服務：採用雲端技術的應用程式變革**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span><span class="sxs-lookup"><span data-stu-id="81845-137">**Mark Russinovich. Microservices: An application revolution powered by the cloud**
[*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span></span>

-   <span data-ttu-id="81845-138">**Martin Fowler：微服務**
    [*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)</span><span class="sxs-lookup"><span data-stu-id="81845-138">**Martin Fowler. Microservices**
[*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)</span></span>

-   <span data-ttu-id="81845-139">**Martin Fowler：微服務先決條件**
    [*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)</span><span class="sxs-lookup"><span data-stu-id="81845-139">**Martin Fowler. Microservice Prerequisites**
[*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)</span></span>

-   <span data-ttu-id="81845-140">**Jimmy Nilsson：區塊雲端運算**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span><span class="sxs-lookup"><span data-stu-id="81845-140">**Jimmy Nilsson. Chunk Cloud Computing**
[*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span></span>

-   <span data-ttu-id="81845-141">**Cesar de la Torre：Microsoft 平台和工具的容器化 Docker 應用程式生命週期** (可下載的電子書) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="81845-141">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="81845-142">[上一個] (service-oriented-architecture.md) [下一個] (data-sovereignty-per-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="81845-142">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span></span>
