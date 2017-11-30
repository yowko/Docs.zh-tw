---
title: "與實體架構的邏輯架構"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |與實體架構的邏輯架構"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 635774a8fcd0cf1c0ede6a73c604071f538a37fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a><span data-ttu-id="1e7fd-104">與實體架構的邏輯架構</span><span class="sxs-lookup"><span data-stu-id="1e7fd-104">Logical architecture versus physical architecture</span></span>

<span data-ttu-id="1e7fd-105">會很有用，此時若要停止，並討論邏輯架構和實體架構，和如何這適用於微服務為基礎的應用程式的設計之間的差別。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-105">It is useful at this point to stop and discuss the distinction between logical architecture and physical architecture, and how this applies to the design of microservice-based applications.</span></span>

<span data-ttu-id="1e7fd-106">若要開始，建置 microservices 不需要任何特定技術的使用。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-106">To begin, building microservices does not require the use of any specific technology.</span></span> <span data-ttu-id="1e7fd-107">比方說，Docker 容器不是強制性，才能建立微服務為基礎的架構。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-107">For instance, Docker containers are not mandatory in order to create a microservice-based architecture.</span></span> <span data-ttu-id="1e7fd-108">這些 microservices 也無法做為一般的處理序執行。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-108">Those microservices could also be run as plain processes.</span></span> <span data-ttu-id="1e7fd-109">Microservices 是邏輯架構。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-109">Microservices is a logical architecture.</span></span>

<span data-ttu-id="1e7fd-110">此外，即使微服務無法實體方式實作成單一服務、 處理序或容器 (為了簡單起見，是在初始的版本中所採取的方法[eShopOnContainers](http://aka.ms/MicroservicesArchitecture))，這之間的同位檢查商務微服務和實體的服務或容器是不一定需要在所有情況下當您建置許多數十個或甚至數百個服務所組成的大型且複雜的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-110">Moreover, even when a microservice could be physically implemented as a single service, process, or container (for simplicity’s sake, that is the approach taken in the initial version of [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), this parity between business microservice and physical service or container is not necessarily required in all cases when you build a large and complex application composed of many dozens or even hundreds of services.</span></span>

<span data-ttu-id="1e7fd-111">這是 where 沒有應用程式的邏輯架構和實體架構之間的差異。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-111">This is where there is a difference between an application’s logical architecture and physical architecture.</span></span> <span data-ttu-id="1e7fd-112">邏輯架構和系統的邏輯界限不一定會對應一對一實體或部署的架構。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-112">The logical architecture and logical boundaries of a system do not necessarily map one-to-one to the physical or deployment architecture.</span></span> <span data-ttu-id="1e7fd-113">還是有可能發生，但它通常沒有。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-113">It can happen, but it often does not.</span></span>

<span data-ttu-id="1e7fd-114">雖然您可能會發現特定商務 microservices 或繫結的內容，不表示的最佳方式將它們實作一律會藉由建立單一服務 （例如 ASP.NET Web API) 或單一 Docker 容器的每個商務微服務。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-114">Although you might have identified certain business microservices or Bounded Contexts, it does not mean that the best way to implement them is always by creating a single service (such as an ASP.NET Web API) or single Docker container for each business microservice.</span></span> <span data-ttu-id="1e7fd-115">規則，指出每個商務微服務會有單一的服務實作，或容器太嚴格。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-115">Having a rule saying each business microservice has to be implemented using a single service or container is too rigid.</span></span>

<span data-ttu-id="1e7fd-116">因此，「 商務微服務 」 或 「 繫結內容是邏輯架構 （或停用），同時可能會發生與實體架構。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-116">Therefore, a business microservice or Bounded Context is a logical architecture that might coincide (or not) with physical architecture.</span></span> <span data-ttu-id="1e7fd-117">很重要的一點是，商務微服務或繫結的內容必須是自發允許程式碼和狀態，進行獨立版本設定，部署，以及縮放。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-117">The important point is that a business microservice or Bounded Context must be autonomous by allowing code and state to be independently versioned, deployed, and scaled.</span></span>

<span data-ttu-id="1e7fd-118">如圖 4-8 所示，類別目錄商務微服務無法撰寫的數個服務或處理序。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-118">As Figure 4-8 shows, the catalog business microservice could be composed of several services or processes.</span></span> <span data-ttu-id="1e7fd-119">這些可能是多個 ASP.NET Web API 服務或任何其他種類的服務使用 HTTP 或任何其他通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-119">These could be multiple ASP.NET Web API services or any other kind of services using HTTP or any other protocol.</span></span> <span data-ttu-id="1e7fd-120">更重要的是，服務無法共用相同的資料，只要這些服務是凝聚力相對於相同商務網域。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-120">More importantly, the services could share the same data, as long as these services are cohesive with respect to the same business domain.</span></span>

![](./media/image8.png)

<span data-ttu-id="1e7fd-121">**圖 4-8**。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-121">**Figure 4-8**.</span></span> <span data-ttu-id="1e7fd-122">數個實體的服務與商務微服務</span><span class="sxs-lookup"><span data-stu-id="1e7fd-122">Business microservice with several physical services</span></span>

<span data-ttu-id="1e7fd-123">此範例中的服務會共用相同的資料模型，因為 Web API 服務為目標的搜尋服務相同的資料。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-123">The services in the example share the same data model because the Web API service targets the same data as the Search service.</span></span> <span data-ttu-id="1e7fd-124">因此，在實體商務微服務實作中，因此您可以視需要調整每個這些內部服務向上或向下會分割該功能。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-124">So, in the physical implementation of the business microservice, you are splitting that functionality so you can scale each of those internal services up or down as needed.</span></span> <span data-ttu-id="1e7fd-125">可能只有 Web API 服務通常需要更多執行個體比搜尋服務，反之亦然。）</span><span class="sxs-lookup"><span data-stu-id="1e7fd-125">Maybe the Web API service usually needs more instances than the Search service, or vice versa.)</span></span>

<span data-ttu-id="1e7fd-126">簡單地說，microservices 的邏輯架構一律沒有與實際的部署架構一致。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-126">In short, the logical architecture of microservices does not always have to coincide with the physical deployment architecture.</span></span> <span data-ttu-id="1e7fd-127">本指南中，每當我們曾經提到的微服務，是指商務或無法對應至一或多個服務的邏輯微服務。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-127">In this guide, whenever we mention a microservice, we mean a business or logical microservice that could map to one or more services.</span></span> <span data-ttu-id="1e7fd-128">在大部分情況下，這會是一項服務，但可能更多。</span><span class="sxs-lookup"><span data-stu-id="1e7fd-128">In most cases, this will be a single service, but it might be more.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1e7fd-129">[上一個](資料-sovereignty-每個-microservice.md) [下一步] (分散式的資料-management.md)</span><span class="sxs-lookup"><span data-stu-id="1e7fd-129">[Previous] (data-sovereignty-per-microservice.md) [Next] (distributed-data-management.md)</span></span>
