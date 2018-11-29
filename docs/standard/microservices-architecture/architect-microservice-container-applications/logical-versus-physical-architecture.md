---
title: 邏輯架構與實體架構
description: 了解邏輯架構與實體架構之間的差異。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: fe3833a4b65317e2ebbeb562e19b473ff0374ddd
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296122"
---
# <a name="logical-architecture-versus-physical-architecture"></a><span data-ttu-id="a8b66-103">邏輯架構與實體架構</span><span class="sxs-lookup"><span data-stu-id="a8b66-103">Logical architecture versus physical architecture</span></span>

<span data-ttu-id="a8b66-104">現在適合停下來討論邏輯架構與實體架構之間的差異，以及如何將這點應用在微服務架構應用程式的設計。</span><span class="sxs-lookup"><span data-stu-id="a8b66-104">It's useful at this point to stop and discuss the distinction between logical architecture and physical architecture, and how this applies to the design of microservice-based applications.</span></span>

<span data-ttu-id="a8b66-105">首先要知道的是，建置微服務並不需要使用任何特定技術。</span><span class="sxs-lookup"><span data-stu-id="a8b66-105">To begin, building microservices doesn't require the use of any specific technology.</span></span> <span data-ttu-id="a8b66-106">例如，並非一定要有 Docker 容器，才能建立微服務架構。</span><span class="sxs-lookup"><span data-stu-id="a8b66-106">For instance, Docker containers aren't mandatory to create a microservice-based architecture.</span></span> <span data-ttu-id="a8b66-107">這些微服務也可以當做一般處理序來執行。</span><span class="sxs-lookup"><span data-stu-id="a8b66-107">Those microservices could also be run as plain processes.</span></span> <span data-ttu-id="a8b66-108">微服務是邏輯架構。</span><span class="sxs-lookup"><span data-stu-id="a8b66-108">Microservices is a logical architecture.</span></span>

<span data-ttu-id="a8b66-109">此外，即使微服務可實際實作為單一服務、處理序或容器 (為了方便作業，這是 [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) 的初始版本中所採取的方法)，每當您建置由數十個或甚至是數百個服務所組成的大型複雜應用程式時，商務微服務與實體服務或容器之間也不一定需要有此同位。</span><span class="sxs-lookup"><span data-stu-id="a8b66-109">Moreover, even when a microservice could be physically implemented as a single service, process, or container (for simplicity's sake, that's the approach taken in the initial version of [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), this parity between business microservice and physical service or container isn't necessarily required in all cases when you build a large and complex application composed of many dozens or even hundreds of services.</span></span>

<span data-ttu-id="a8b66-110">這就是應用程式邏輯架構與實體架構之間的差異所在。</span><span class="sxs-lookup"><span data-stu-id="a8b66-110">This is where there's a difference between an application's logical architecture and physical architecture.</span></span> <span data-ttu-id="a8b66-111">系統的邏輯架構和邏輯界限不一定會以一對一的方式對應至實體或部署架構。</span><span class="sxs-lookup"><span data-stu-id="a8b66-111">The logical architecture and logical boundaries of a system do not necessarily map one-to-one to the physical or deployment architecture.</span></span> <span data-ttu-id="a8b66-112">這有可能發生，但並不常見。</span><span class="sxs-lookup"><span data-stu-id="a8b66-112">It can happen, but it often doesn't.</span></span>

<span data-ttu-id="a8b66-113">雖然您可能已識別特定商務微服務或限定內容，但不表示為每個商務微服務建立單一服務 (例如 ASP.NET Web API) 或單一 Docker 容器一律為最佳實作方式。</span><span class="sxs-lookup"><span data-stu-id="a8b66-113">Although you might have identified certain business microservices or Bounded Contexts, it doesn't mean that the best way to implement them is always by creating a single service (such as an ASP.NET Web API) or single Docker container for each business microservice.</span></span> <span data-ttu-id="a8b66-114">以規則指出每個商務微服務必須使用單一服務或容器來實作會太嚴格。</span><span class="sxs-lookup"><span data-stu-id="a8b66-114">Having a rule saying each business microservice has to be implemented using a single service or container is too rigid.</span></span>

<span data-ttu-id="a8b66-115">因此，商務微服務或限定內容是邏輯架構，不一定會與實體架構一致。</span><span class="sxs-lookup"><span data-stu-id="a8b66-115">Therefore, a business microservice or Bounded Context is a logical architecture that might coincide (or not) with physical architecture.</span></span> <span data-ttu-id="a8b66-116">重點是商務微服務或限定內容必須是自主的，這可藉由允許對程式碼和狀態獨立建立版本、進行部署和擴充來達成。</span><span class="sxs-lookup"><span data-stu-id="a8b66-116">The important point is that a business microservice or Bounded Context must be autonomous by allowing code and state to be independently versioned, deployed, and scaled.</span></span>

<span data-ttu-id="a8b66-117">如圖 4-8 所示，目錄商務微服務可能是由數個服務或處理序所組成。</span><span class="sxs-lookup"><span data-stu-id="a8b66-117">As Figure 4-8 shows, the catalog business microservice could be composed of several services or processes.</span></span> <span data-ttu-id="a8b66-118">這些服務可以是多個 ASP.NET Web API 服務，或是使用 HTTP 或任何其他通訊協定的任何其他服務類型。</span><span class="sxs-lookup"><span data-stu-id="a8b66-118">These could be multiple ASP.NET Web API services or any other kind of services using HTTP or any other protocol.</span></span> <span data-ttu-id="a8b66-119">更重要的是，只要這些服務與相同的業務領域相關，就可以共用相同的資料。</span><span class="sxs-lookup"><span data-stu-id="a8b66-119">More importantly, the services could share the same data, as long as these services are cohesive with respect to the same business domain.</span></span>

![目錄商務微服務圖表，其中包含 API 服務、搜尋服務和 SQL Server 資料庫。](./media/image8.png)

<span data-ttu-id="a8b66-121">**圖 4-8**：</span><span class="sxs-lookup"><span data-stu-id="a8b66-121">**Figure 4-8**.</span></span> <span data-ttu-id="a8b66-122">具有數項實體服務的商務微服務</span><span class="sxs-lookup"><span data-stu-id="a8b66-122">Business microservice with several physical services</span></span>

<span data-ttu-id="a8b66-123">範例中的服務會共用相同的資料模型，因為 Web API 服務與 Search 服務是以相同的資料為目標。</span><span class="sxs-lookup"><span data-stu-id="a8b66-123">The services in the example share the same data model because the Web API service targets the same data as the Search service.</span></span> <span data-ttu-id="a8b66-124">因此，實際實作商務微服務時，您會分割該功能，因此可視需要縮放每個內部服務。</span><span class="sxs-lookup"><span data-stu-id="a8b66-124">So, in the physical implementation of the business microservice, you're splitting that functionality so you can scale each of those internal services up or down as needed.</span></span> <span data-ttu-id="a8b66-125">Web API 服務通常可能需要比 Search 服務更多的執行個體，也可能相反。</span><span class="sxs-lookup"><span data-stu-id="a8b66-125">Maybe the Web API service usually needs more instances than the Search service, or vice versa.</span></span>

<span data-ttu-id="a8b66-126">簡單來說，微服務的邏輯架構不一定會與實體部署架構一致。</span><span class="sxs-lookup"><span data-stu-id="a8b66-126">In short, the logical architecture of microservices doesn't always have to coincide with the physical deployment architecture.</span></span> <span data-ttu-id="a8b66-127">在本指南中，每當我們提到微服務時，指的是無法對應至一或多個 (實體) 服務的商務或邏輯微服務。</span><span class="sxs-lookup"><span data-stu-id="a8b66-127">In this guide, whenever we mention a microservice, we mean a business or logical microservice that could map to one or more (physical) services.</span></span> <span data-ttu-id="a8b66-128">在大部分情況下，這會是單一服務，但可能更多。</span><span class="sxs-lookup"><span data-stu-id="a8b66-128">In most cases, this will be a single service, but it might be more.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a8b66-129">[上一頁](data-sovereignty-per-microservice.md)
[下一頁](distributed-data-management.md)</span><span class="sxs-lookup"><span data-stu-id="a8b66-129">[Previous](data-sovereignty-per-microservice.md)
[Next](distributed-data-management.md)</span></span>