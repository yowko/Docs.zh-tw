---
title: 利用 DDD 和 CQRS 模式解決微服務中的商務複雜度
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 利用 DDD 和 CQRS 模式解決微服務中的商務複雜度
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 1af53f8f37e516219767fdde49eb7da9927d9e29
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50047263"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="0c61f-103">利用 DDD 和 CQRS 模式解決微服務中的商務複雜度</span><span class="sxs-lookup"><span data-stu-id="0c61f-103">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="0c61f-104">設計每個微服務的領域模型，或反映對業務領域了解程度的繫結內容。</span><span class="sxs-lookup"><span data-stu-id="0c61f-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="0c61f-105">本節著重於當您需要解決複雜的子系統時所實作的更進階微服務，或是衍生自領域專家對不斷改變之商務規則知識的微服務。</span><span class="sxs-lookup"><span data-stu-id="0c61f-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="0c61f-106">本節中所使用的架構模式是以領域驅動設計 (Domain-Driven Design，DDD) 以及命令和查詢職責分離 (Command and Query Responsibility Segregation，CQRS) 方法為基礎，如圖 9-1 所示。</span><span class="sxs-lookup"><span data-stu-id="0c61f-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="0c61f-107">**圖 9-1**.</span><span class="sxs-lookup"><span data-stu-id="0c61f-107">**Figure 9-1**.</span></span> <span data-ttu-id="0c61f-108">外部微服務架構與每個微服務的內部架構模式</span><span class="sxs-lookup"><span data-stu-id="0c61f-108">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="0c61f-109">不過，資料驅動微服務的大多數技術，像是如何實作 ASP.NET Core Web API 服務，或如何使用 Swashbuckle 公開 Swagger 中繼資料，也適用於以 DDD 模式在內部實作之更進階的微服務。</span><span class="sxs-lookup"><span data-stu-id="0c61f-109">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="0c61f-110">本節是前面幾節的延伸，因為稍早所述的大部分實務也適用於這裡或任何類型的微服務。</span><span class="sxs-lookup"><span data-stu-id="0c61f-110">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="0c61f-111">本節會先提供 eShopOnContainers 參考應用程式中所使用之簡化 CQRS 模式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0c61f-111">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="0c61f-112">稍後會對您概要說明 DDD 技術，這些技術可讓您尋找常見的模式，以便在應用程式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="0c61f-112">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="0c61f-113">DDD 是一個龐大的主題，內含一組豐富的學習資源。</span><span class="sxs-lookup"><span data-stu-id="0c61f-113">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="0c61f-114">您可以從 Eric Evans 所著 [Domain-Driven Design](https://domainlanguage.com/ddd/) 之類的書籍，以及 Vaughn Vernon、Jimmy Nilsson、Greg Young、Udi Dahan、Jimmy Bogard 和許多其他 DDD/CQRS 專家所提供的其他教材開始著手。</span><span class="sxs-lookup"><span data-stu-id="0c61f-114">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="0c61f-115">但最重要的是，您需要試著了解如何在專家協助下，將來自交談、白板與領域模型課程的 DDD 技術，應用在您的實體業務領域中。</span><span class="sxs-lookup"><span data-stu-id="0c61f-115">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="0c61f-116">其他資源</span><span class="sxs-lookup"><span data-stu-id="0c61f-116">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="0c61f-117">DDD (領域驅動設計)</span><span class="sxs-lookup"><span data-stu-id="0c61f-117">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="0c61f-118">**Eric Evans：領域語言**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-118">**Eric Evans. Domain Language**
[*https://domainlanguage.com/*](https://domainlanguage.com/)</span></span>

-   <span data-ttu-id="0c61f-119">**Martin Fowler：領域導向設計**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="0c61f-119">**Martin Fowler. Domain-Driven Design**
[*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="0c61f-120">**Jimmy Bogard：加強您的領域：初階**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-120">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="0c61f-121">DDD 書籍</span><span class="sxs-lookup"><span data-stu-id="0c61f-121">DDD books</span></span>

-   <span data-ttu-id="0c61f-122">**Eric Evans：Domain-Driven Design: Tackling Complexity in the Heart of Software**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-122">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="0c61f-123">**Eric Evans：Domain-Driven Design Reference: Definitions and Pattern Summaries**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-123">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="0c61f-124">**Vaughn Vernon：Implementing Domain-Driven Design**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-124">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="0c61f-125">**Vaughn Vernon：Domain-Driven Design Distilled**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-125">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="0c61f-126">**Jimmy Nilsson：Applying Domain-Driven Design and Patterns**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-126">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="0c61f-127">**Cesar de la Torre：N-Layered Domain-Oriented Architecture Guide with .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-127">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="0c61f-128">**Abel Avram 和 Floyd Marinescu：Domain-Driven Design Quickly**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="0c61f-128">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="0c61f-129">DDD 訓練課程</span><span class="sxs-lookup"><span data-stu-id="0c61f-129">DDD training</span></span>

-   <span data-ttu-id="0c61f-130">**Julie Lerman 和 Steve Smith：網域導向設計的基本概念**
    [*https://bit.ly/PS-DDD*](https://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="0c61f-130">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*https://bit.ly/PS-DDD*](https://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0c61f-131">[上一頁](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[下一頁](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="0c61f-131">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>