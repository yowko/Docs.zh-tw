---
title: "建立、 發展，以及版本控制的微服務應用程式開發介面和合約"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |建立、 發展，以及版本控制的微服務應用程式開發介面和合約"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 433711c3479eafd52bf9f5d53faf8e5707c6c624
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a><span data-ttu-id="1a811-104">建立、 發展，以及版本控制的微服務應用程式開發介面和合約</span><span class="sxs-lookup"><span data-stu-id="1a811-104">Creating, evolving, and versioning microservice APIs and contracts</span></span>

<span data-ttu-id="1a811-105">應用程式開發介面的微服務是服務與其用戶端之間的合約。</span><span class="sxs-lookup"><span data-stu-id="1a811-105">A microservice API is a contract between the service and its clients.</span></span> <span data-ttu-id="1a811-106">您可以獨立進行微服務，才不會中斷其 API 合約，合約是很重要的原因。</span><span class="sxs-lookup"><span data-stu-id="1a811-106">You will be able to evolve a microservice independently only if you do not break its API contract, which is why the contract is so important.</span></span> <span data-ttu-id="1a811-107">如果您變更合約時，它會影響用戶端應用程式或您應用程式開發介面的閘道。</span><span class="sxs-lookup"><span data-stu-id="1a811-107">If you change the contract, it will impact your client applications or your API Gateway.</span></span>

<span data-ttu-id="1a811-108">API 定義的性質取決於您所使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1a811-108">The nature of the API definition depends on which protocol you are using.</span></span> <span data-ttu-id="1a811-109">比方說，如果您使用的訊息 (像是[AMQP](https://www.amqp.org/))，應用程式開發介面所組成的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1a811-109">For instance, if you are using messaging (like [AMQP](https://www.amqp.org/)), the API consists of the message types.</span></span> <span data-ttu-id="1a811-110">如果您使用 HTTP 和 RESTful 服務，應用程式開發介面包含和要求和回應的 JSON 格式的 Url。</span><span class="sxs-lookup"><span data-stu-id="1a811-110">If you are using HTTP and RESTful services, the API consists of the URLs and the request and response JSON formats.</span></span>

<span data-ttu-id="1a811-111">不過，即使您即將仔細考量您初始的合約，服務 API 必須隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="1a811-111">However, even if you are thoughtful about your initial contract, a service API will need to change over time.</span></span> <span data-ttu-id="1a811-112">當發生這種情況，特別是如果您的 API 是由多個用戶端應用程式的公用 API — 通常無法強制升級到新的 API 合約的所有用戶端。</span><span class="sxs-lookup"><span data-stu-id="1a811-112">When that happens—and especially if your API is a public API consumed by multiple client applications—you typically cannot force all clients to upgrade to your new API contract.</span></span> <span data-ttu-id="1a811-113">您通常需要以累加方式部署新版本的服務，同時執行的服務合約的舊的和新版本的方式。</span><span class="sxs-lookup"><span data-stu-id="1a811-113">You usually need to incrementally deploy new versions of a service in a way that both old and new versions of a service contract are running simultaneously.</span></span> <span data-ttu-id="1a811-114">因此，就一定要有您的服務版本控制的策略。</span><span class="sxs-lookup"><span data-stu-id="1a811-114">Therefore, it is important to have a strategy for your service versioning.</span></span>

<span data-ttu-id="1a811-115">很小，如果屬性或新增參數到您的 API 類似的應用程式開發介面變更時，使用較舊的 API 的用戶端應該切換，並使用新版本的服務。</span><span class="sxs-lookup"><span data-stu-id="1a811-115">When the API changes are small, like if you add attributes or parameters to your API, clients that use an older API should switch and work with the new version of the service.</span></span> <span data-ttu-id="1a811-116">您可以提供預設值是必要的任何遺漏的屬性，而且用戶端可能無法略過任何額外的回應屬性。</span><span class="sxs-lookup"><span data-stu-id="1a811-116">You might be able to provide default values for any missing attributes that are required, and the clients might be able to ignore any extra response attributes.</span></span>

<span data-ttu-id="1a811-117">不過，有時候您需要對服務 API 的主要和不相容的變更。</span><span class="sxs-lookup"><span data-stu-id="1a811-117">However, sometimes you need to make major and incompatible changes to a service API.</span></span> <span data-ttu-id="1a811-118">因為您不可能強制立即升級為新版本的用戶端應用程式或服務，服務必須支援舊版的 API 段。</span><span class="sxs-lookup"><span data-stu-id="1a811-118">Because you might not be able to force client applications or services to upgrade immediately to the new version, a service must support older versions of the API for some period.</span></span> <span data-ttu-id="1a811-119">如果您使用以 HTTP 為基礎的機制，例如 REST，其中一個方法是內嵌的應用程式開發介面版本號碼，在 URL 或 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="1a811-119">If you are using an HTTP-based mechanism such as REST, one approach is to embed the API version number in the URL or into a HTTP header.</span></span> <span data-ttu-id="1a811-120">然後您可以決定實作這兩個版本的服務同時在相同的服務執行個體，或部署每個處理的 API 版本的不同執行個體之間。</span><span class="sxs-lookup"><span data-stu-id="1a811-120">Then you can decide between implementing both versions of the service simultaneously within the same service instance, or deploying different instances that each handle a version of the API.</span></span> <span data-ttu-id="1a811-121">很好的方法，這個[暫留處理器模式](https://en.wikipedia.org/wiki/Mediator_pattern)(例如， [MediatR 文件庫](https://github.com/jbogard/MediatR)) 獨立的處理常式分離的不同實作版本。</span><span class="sxs-lookup"><span data-stu-id="1a811-121">A good approach for this is the [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern) (for example, [MediatR library](https://github.com/jbogard/MediatR)) to decouple the different implementation versions into independent handlers.</span></span>

<span data-ttu-id="1a811-122">最後，如果您使用 REST 架構[超](https://www.infoq.com/articles/mark-baker-hypermedia)是最佳的解決方案進行版本控制您的服務，並允許 evolvable 應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="1a811-122">Finally, if you are using a REST architecture, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) is the best solution for versioning your services and allowing evolvable APIs.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1a811-123">其他資源</span><span class="sxs-lookup"><span data-stu-id="1a811-123">Additional resources</span></span>

-   <span data-ttu-id="1a811-124">**Scott Hanselman。ASP.NET Core RESTful Web API 版本設定輕鬆**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx></span><span class="sxs-lookup"><span data-stu-id="1a811-124">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
<http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx></span></span>

-   <span data-ttu-id="1a811-125">**版本控制 RESTful web API**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span><span class="sxs-lookup"><span data-stu-id="1a811-125">**Versioning a RESTful web API**
[*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span></span>

-   <span data-ttu-id="1a811-126">**伊 Fielding。版本控制、 超和 REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning></span><span class="sxs-lookup"><span data-stu-id="1a811-126">**Roy Fielding. Versioning, Hypermedia, and REST**
<https://www.infoq.com/articles/roy-fielding-on-versioning></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1a811-127">[上一個](非同步的訊息為基礎-communication.md) [下一步] (microservices-可定址性-服務-registry.md)</span><span class="sxs-lookup"><span data-stu-id="1a811-127">[Previous] (asynchronous-message-based-communication.md) [Next] (microservices-addressability-service-registry.md)</span></span>
