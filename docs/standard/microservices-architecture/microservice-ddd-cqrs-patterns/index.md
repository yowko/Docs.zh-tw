---
title: 利用 DDD 和 CQRS 模式解決微服務中的商務複雜度
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 了解如何利用 DDD 與 CQRS 模式解決複雜的商業案例
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 2780e2d46ae1e9caf45e715a835998c8ef70413a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152548"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="d2824-103">使用 DDD 與 CQRS 模式解決微服務中的商務複雜度</span><span class="sxs-lookup"><span data-stu-id="d2824-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="d2824-104">設計每個微服務的領域模型，或反映對業務領域了解程度的繫結內容。</span><span class="sxs-lookup"><span data-stu-id="d2824-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="d2824-105">此節著重於當您需要解決複雜的子系統時所實作的更進階微服務，或是衍生自領域專家對不斷改變之商務規則知識的微服務。</span><span class="sxs-lookup"><span data-stu-id="d2824-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="d2824-106">此節中所使用的架構模式是以領域驅動設計 (Domain-Driven Design，DDD) 以及命令和查詢職責分離 (Command and Query Responsibility Segregation，CQRS) 方法為基礎，如圖 7-1 所示。</span><span class="sxs-lookup"><span data-stu-id="d2824-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

![外部架構的差異：微服務模式、API 閘道、彈性通訊、pub/sub 等：內部架構：資料 動/CRUD、DDD 模式、相依性插入、多程式庫等。](./media/image1.png)

<span data-ttu-id="d2824-108">**圖 7-1**.</span><span class="sxs-lookup"><span data-stu-id="d2824-108">**Figure 7-1**.</span></span> <span data-ttu-id="d2824-109">外部微服務架構與每個微服務的內部架構模式</span><span class="sxs-lookup"><span data-stu-id="d2824-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="d2824-110">不過，資料驅動微服務的大多數技術，像是如何實作 ASP.NET Core Web API 服務，或如何使用 Swashbuckle 或 NSwag 公開 Swagger 中繼資料，也適用於以 DDD 模式在內部實作之更進階的微服務。</span><span class="sxs-lookup"><span data-stu-id="d2824-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="d2824-111">此節是前面幾節的延伸，因為稍早所述的大部分實務也適用於這裡或任何類型的微服務。</span><span class="sxs-lookup"><span data-stu-id="d2824-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="d2824-112">此節會先提供 eShopOnContainers 參考應用程式中所使用之簡化 CQRS 模式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d2824-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="d2824-113">稍後會對您概要說明 DDD 技術，這些技術可讓您尋找常見的模式，以便在應用程式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="d2824-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="d2824-114">DDD 是一個龐大的主題，內含一組豐富的學習資源。</span><span class="sxs-lookup"><span data-stu-id="d2824-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="d2824-115">您可以從 Eric Evans 所著 [Domain-Driven Design](https://domainlanguage.com/ddd/) 之類的書籍，以及 Vaughn Vernon、Jimmy Nilsson、Greg Young、Udi Dahan、Jimmy Bogard 和許多其他 DDD/CQRS 專家所提供的其他教材開始著手。</span><span class="sxs-lookup"><span data-stu-id="d2824-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="d2824-116">但最重要的是，您需要試著了解如何在專家協助下，將來自交談、白板與領域模型課程的 DDD 技術，應用在您的實體業務領域中。</span><span class="sxs-lookup"><span data-stu-id="d2824-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="d2824-117">其他資源</span><span class="sxs-lookup"><span data-stu-id="d2824-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="d2824-118">DDD (領域驅動設計)</span><span class="sxs-lookup"><span data-stu-id="d2824-118">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="d2824-119">**Eric Evans：領域語言** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-119">**Eric Evans. Domain Language** \\</span></span>
  [*https://domainlanguage.com/*](https://domainlanguage.com/)

- <span data-ttu-id="d2824-120">**Martin Fowler：領域驅動設計** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-120">**Martin Fowler. Domain-Driven Design** \\</span></span>
  [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)

- <span data-ttu-id="d2824-121">**Jimmy Bogard：加強您的領域：初階** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-121">**Jimmy Bogard. Strengthening your domain: a primer** \\</span></span>
  [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a><span data-ttu-id="d2824-122">DDD 書籍</span><span class="sxs-lookup"><span data-stu-id="d2824-122">DDD books</span></span>

- <span data-ttu-id="d2824-123">**Eric Evans：領與導向設計：解決軟體核心的複雜度** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** \\</span></span>
  [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

- <span data-ttu-id="d2824-124">**Eric Evans：領域驅動設計參考：定義與模式摘要** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** \\</span></span>
  [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

- <span data-ttu-id="d2824-125">**Vaughn Vernon：實作領域驅動設計**  \\</span><span class="sxs-lookup"><span data-stu-id="d2824-125">**Vaughn Vernon. Implementing Domain-Driven Design** \\</span></span>
  [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

- <span data-ttu-id="d2824-126">**Vaughn Vernon：領域驅動設計精華** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-126">**Vaughn Vernon. Domain-Driven Design Distilled** \\</span></span>
  [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

- <span data-ttu-id="d2824-127">**Jimmy Nilsson：套用領域驅動設計與模式** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** \\</span></span>
  [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

- <span data-ttu-id="d2824-128">**Cesar de la Torre：N 層領域導向架構指南 (.NET)** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** \\</span></span>
  [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

- <span data-ttu-id="d2824-129">**Abel Avram 和 Floyd Marinescu：快速領域驅動設計** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** \\</span></span>
  [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

- <span data-ttu-id="d2824-130">**Scott Millett、Nick Tune - 領域驅動設計的模式、準則與實務** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-130">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** \\</span></span>
  [*http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html*](http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html)

##### <a name="ddd-training"></a><span data-ttu-id="d2824-131">DDD 訓練課程</span><span class="sxs-lookup"><span data-stu-id="d2824-131">DDD training</span></span>

- <span data-ttu-id="d2824-132">**Julie Lerman 和 Steve Smith：網域驅動設計基本概念** \\</span><span class="sxs-lookup"><span data-stu-id="d2824-132">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** \\</span></span>
  [*https://bit.ly/PS-DDD*](https://bit.ly/PS-DDD)

>[!div class="step-by-step"]
><span data-ttu-id="d2824-133">[上一頁](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[下一頁](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="d2824-133">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>