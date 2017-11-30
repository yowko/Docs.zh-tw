---
title: "微服務架構"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Microservices 架構"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5ede1f0ad19270ca6b7556ff1bb7e4cf8ccf7cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="microservices-architecture"></a><span data-ttu-id="c48c8-104">微服務架構</span><span class="sxs-lookup"><span data-stu-id="c48c8-104">Microservices architecture</span></span>

<span data-ttu-id="c48c8-105">正如其名，microservices 架構就會是一種方法建立的一組小型服務的伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="c48c8-105">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="c48c8-106">每個服務會在自己的處理序中執行，並使用通訊協定，例如 HTTP/HTTPS，WebSockets，其他處理程序與通訊或[AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)。</span><span class="sxs-lookup"><span data-stu-id="c48c8-106">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="c48c8-107">每個微服務實作特定的端對端網域或在特定內容界限內的商務功能，每個必須獨立開發和獨立不可配置。</span><span class="sxs-lookup"><span data-stu-id="c48c8-107">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="c48c8-108">最後，每個微服務應該擁有網域邏輯 （sovereignty 和分散式的資料管理） 根據不同的資料儲存技術 （SQL、 NoSQL） 和不同的程式設計語言及其相關的網域資料模型。</span><span class="sxs-lookup"><span data-stu-id="c48c8-108">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="c48c8-109">微服務應該是何種大小？</span><span class="sxs-lookup"><span data-stu-id="c48c8-109">What size should a microservice be?</span></span> <span data-ttu-id="c48c8-110">在開發微服務時，大小不能很重要的一點。</span><span class="sxs-lookup"><span data-stu-id="c48c8-110">When developing a microservice, size should not be the important point.</span></span> <span data-ttu-id="c48c8-111">相反地，很重要的一點應該建立鬆散耦合服務因此需要自主性的開發、 部署和小數位數，每個服務。</span><span class="sxs-lookup"><span data-stu-id="c48c8-111">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="c48c8-112">當然，當識別並設計 microservices 時，您應該嘗試使其越小越好，只要您不需要與其他 microservices 太多直接相依性。</span><span class="sxs-lookup"><span data-stu-id="c48c8-112">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you do not have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="c48c8-113">更重要的微服務的大小大於它必須要有內部一致性和獨立於其他服務。</span><span class="sxs-lookup"><span data-stu-id="c48c8-113">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="c48c8-114">Microservices 架構為何？</span><span class="sxs-lookup"><span data-stu-id="c48c8-114">Why a microservices architecture?</span></span> <span data-ttu-id="c48c8-115">簡單地說，它提供長期的靈活度。</span><span class="sxs-lookup"><span data-stu-id="c48c8-115">In short, it provides long-term agility.</span></span> <span data-ttu-id="c48c8-116">Microservices 複雜、 大，且高度可擴充的系統中啟用更佳的可維護性，讓您建立基礎，其各有細微和自發生命週期的許多可獨立部署服務的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c48c8-116">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="c48c8-117">另一個好處是，microservices 可以向外延展獨立。</span><span class="sxs-lookup"><span data-stu-id="c48c8-117">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="c48c8-118">您不需要單一的整合應用程式，您必須向外擴充做為一個單位，您可以改為向外擴充特定 microservices。</span><span class="sxs-lookup"><span data-stu-id="c48c8-118">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="c48c8-119">這樣一來，您可以調整只需要較多處理電源或網路頻寬需求，而不是向外延展的應用程式不需要調整其他區域所支援的功能區域。</span><span class="sxs-lookup"><span data-stu-id="c48c8-119">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that do not need to be scaled.</span></span> <span data-ttu-id="c48c8-120">這表示節省成本，因為您需要較少的硬體。</span><span class="sxs-lookup"><span data-stu-id="c48c8-120">That means cost savings because you need less hardware.</span></span>

![](./media/image6.png)

<span data-ttu-id="c48c8-121">**圖 4-6**。</span><span class="sxs-lookup"><span data-stu-id="c48c8-121">**Figure 4-6**.</span></span> <span data-ttu-id="c48c8-122">整合的部署與 microservices 方法</span><span class="sxs-lookup"><span data-stu-id="c48c8-122">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="c48c8-123">如圖 4-6 所示，microservices 方法允許敏捷式軟體開發的變更和快速的反覆項目的每個微服務，因為您可以變更的複雜、 大，且可延展的應用程式特定的小型區域。</span><span class="sxs-lookup"><span data-stu-id="c48c8-123">As Figure 4-6 shows, the microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="c48c8-124">更細緻的 microservices 應用程式可讓持續整合及連續傳遞作法架構。</span><span class="sxs-lookup"><span data-stu-id="c48c8-124">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="c48c8-125">它也會提升新函式的傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="c48c8-125">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="c48c8-126">更細緻的組合的應用程式也可讓您執行及測試 microservices 隔離中，並維持清除它們之間的合約、 發展。</span><span class="sxs-lookup"><span data-stu-id="c48c8-126">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="c48c8-127">只要您不要變更合約的介面，您可以變更任何微服務的內部實作，或加入新的功能，而不會中斷其他 microservices。</span><span class="sxs-lookup"><span data-stu-id="c48c8-127">As long as you do not change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="c48c8-128">以下是要啟用成功移到實際執行環境與 microservices 為基礎的系統中的重要層面：</span><span class="sxs-lookup"><span data-stu-id="c48c8-128">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

-   <span data-ttu-id="c48c8-129">監視與健全狀況檢查的服務和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c48c8-129">Monitoring and health checks of the services and infrastructure.</span></span>

-   <span data-ttu-id="c48c8-130">可擴充的服務 （也就是雲端及 orchestrators） 的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c48c8-130">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

-   <span data-ttu-id="c48c8-131">安全性設計和實作多個層級： 驗證、 授權、 密碼管理、 安全通訊等。</span><span class="sxs-lookup"><span data-stu-id="c48c8-131">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

-   <span data-ttu-id="c48c8-132">快速應用程式傳遞，通常會有不同的小組將焦點放在不同的 microservices。</span><span class="sxs-lookup"><span data-stu-id="c48c8-132">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

-   <span data-ttu-id="c48c8-133">DevOps 與 CI/CD 的作法和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c48c8-133">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="c48c8-134">其中前, 三個是涵蓋或本指南中導入。</span><span class="sxs-lookup"><span data-stu-id="c48c8-134">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="c48c8-135">最後兩個點，與應用程式生命週期，會包含在其他[容器化 Docker 應用程式生命週期的 Microsoft 平台和工具](https://aka.ms/dockerlifecycleebook)電子書。</span><span class="sxs-lookup"><span data-stu-id="c48c8-135">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c48c8-136">其他資源</span><span class="sxs-lookup"><span data-stu-id="c48c8-136">Additional resources</span></span>

-   <span data-ttu-id="c48c8-137">**Mark Russinovich。Microservices： 由雲端應用程式 revolution**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span><span class="sxs-lookup"><span data-stu-id="c48c8-137">**Mark Russinovich. Microservices: An application revolution powered by the cloud**
[*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span></span>

-   <span data-ttu-id="c48c8-138">**Martin Fowler：Microservices**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)</span><span class="sxs-lookup"><span data-stu-id="c48c8-138">**Martin Fowler. Microservices**
[*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)</span></span>

-   <span data-ttu-id="c48c8-139">**Martin Fowler：微服務必要條件**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)</span><span class="sxs-lookup"><span data-stu-id="c48c8-139">**Martin Fowler. Microservice Prerequisites**
[*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)</span></span>

-   <span data-ttu-id="c48c8-140">**Jimmy Nilsson：區塊雲端運算**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span><span class="sxs-lookup"><span data-stu-id="c48c8-140">**Jimmy Nilsson. Chunk Cloud Computing**
[*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span></span>

-   <span data-ttu-id="c48c8-141">**Cesar de la Torre：容器化 Microsoft 平台和工具與 Docker 的應用程式生命週期**（可下載的電子書） [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="c48c8-141">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="c48c8-142">[上一個](服務-導向-architecture.md) [下一步] (資料-sovereignty-每個-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="c48c8-142">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span></span>
