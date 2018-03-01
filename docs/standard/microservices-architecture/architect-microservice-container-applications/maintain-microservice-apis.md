---
title: "建立、發展以及版本控制微服務 API 與協定"
description: "適用於容器化 .NET 應用程式的.NET 微服務架構 | 建立、發展以及版本控制微服務 API 與協定"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3aaa7eaa8bc535874369cf08414f2211cae1bed9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a><span data-ttu-id="3432d-104">建立、發展以及版本控制微服務 API 與協定</span><span class="sxs-lookup"><span data-stu-id="3432d-104">Creating, evolving, and versioning microservice APIs and contracts</span></span>

<span data-ttu-id="3432d-105">微服務 API 是服務與其用戶端之間的協定。</span><span class="sxs-lookup"><span data-stu-id="3432d-105">A microservice API is a contract between the service and its clients.</span></span> <span data-ttu-id="3432d-106">您可以在不破壞微服務 API 協定的前提下獨立發展微服務，因此協定十分重要。</span><span class="sxs-lookup"><span data-stu-id="3432d-106">You will be able to evolve a microservice independently only if you do not break its API contract, which is why the contract is so important.</span></span> <span data-ttu-id="3432d-107">如果您變更協定，會影響用戶端應用程式或您的 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="3432d-107">If you change the contract, it will impact your client applications or your API Gateway.</span></span>

<span data-ttu-id="3432d-108">API 定義的性質取決於您所用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="3432d-108">The nature of the API definition depends on which protocol you are using.</span></span> <span data-ttu-id="3432d-109">比方說，如果您使用傳訊功能 (像是[AMQP](https://www.amqp.org/))，則 API 由訊息類型組成。</span><span class="sxs-lookup"><span data-stu-id="3432d-109">For instance, if you are using messaging (like [AMQP](https://www.amqp.org/)), the API consists of the message types.</span></span> <span data-ttu-id="3432d-110">如果您使用 HTTP 和 RESTful 服務，API 則包含 URL 和 JSON 格式的要求與回應。</span><span class="sxs-lookup"><span data-stu-id="3432d-110">If you are using HTTP and RESTful services, the API consists of the URLs and the request and response JSON formats.</span></span>

<span data-ttu-id="3432d-111">不過，即使您審慎考量您的初始協定，服務 API 仍必須隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="3432d-111">However, even if you are thoughtful about your initial contract, a service API will need to change over time.</span></span> <span data-ttu-id="3432d-112">發生這種情況時，尤其如果您的 API 是提供多個用戶端應用程式使用的公用 API，您通常無法強制所有用戶端升級到新的 API 協定。</span><span class="sxs-lookup"><span data-stu-id="3432d-112">When that happens—and especially if your API is a public API consumed by multiple client applications—you typically cannot force all clients to upgrade to your new API contract.</span></span> <span data-ttu-id="3432d-113">您通常需要以累加方式部署服務的新版本，並且要能夠同時執行服務協定的新舊兩種版本。</span><span class="sxs-lookup"><span data-stu-id="3432d-113">You usually need to incrementally deploy new versions of a service in a way that both old and new versions of a service contract are running simultaneously.</span></span> <span data-ttu-id="3432d-114">因此，為您的服務版本控制制定策略非常重要。</span><span class="sxs-lookup"><span data-stu-id="3432d-114">Therefore, it is important to have a strategy for your service versioning.</span></span>

<span data-ttu-id="3432d-115">當 API 變化很小時，例如對 API 新增屬性或參數時，使用舊 API 的用戶端應該切換並使用新版本的服務。</span><span class="sxs-lookup"><span data-stu-id="3432d-115">When the API changes are small, like if you add attributes or parameters to your API, clients that use an older API should switch and work with the new version of the service.</span></span> <span data-ttu-id="3432d-116">您可以為所需的任何遺漏屬性提供預設值，而用戶端可以略過任何額外的回應屬性。</span><span class="sxs-lookup"><span data-stu-id="3432d-116">You might be able to provide default values for any missing attributes that are required, and the clients might be able to ignore any extra response attributes.</span></span>

<span data-ttu-id="3432d-117">不過，有時候您會需要對服務 API 進行重大且不相容的變更。</span><span class="sxs-lookup"><span data-stu-id="3432d-117">However, sometimes you need to make major and incompatible changes to a service API.</span></span> <span data-ttu-id="3432d-118">因為您可能無法強制用戶端應用程式或服務立刻升級到新版本，所以服務必須繼續支援舊版的 API 一段時間。</span><span class="sxs-lookup"><span data-stu-id="3432d-118">Because you might not be able to force client applications or services to upgrade immediately to the new version, a service must support older versions of the API for some period.</span></span> <span data-ttu-id="3432d-119">如果您使用以 HTTP 為基礎的機制，例如 REST，其中一個方法是在 URL 或是 HTTP 標題內嵌 API 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="3432d-119">If you are using an HTTP-based mechanism such as REST, one approach is to embed the API version number in the URL or into a HTTP header.</span></span> <span data-ttu-id="3432d-120">然後您可以決定要在相同的服務執行個體中同時實作服務的兩個版本，或是要部署不同的執行個體，分別處理各一個 API 版本。</span><span class="sxs-lookup"><span data-stu-id="3432d-120">Then you can decide between implementing both versions of the service simultaneously within the same service instance, or deploying different instances that each handle a version of the API.</span></span> <span data-ttu-id="3432d-121">有個不錯的方法是以[中繼程序模式](https://en.wikipedia.org/wiki/Mediator_pattern) (例如 [MediatR 程式庫](https://github.com/jbogard/MediatR)) 來將不同實作版本分離為獨立處理常式。</span><span class="sxs-lookup"><span data-stu-id="3432d-121">A good approach for this is the [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern) (for example, [MediatR library](https://github.com/jbogard/MediatR)) to decouple the different implementation versions into independent handlers.</span></span>

<span data-ttu-id="3432d-122">最後，如果您使用 REST 架構，[超媒體](https://www.infoq.com/articles/mark-baker-hypermedia)即為進行服務版本控制及允許發展 API 的最佳解決方案。</span><span class="sxs-lookup"><span data-stu-id="3432d-122">Finally, if you are using a REST architecture, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) is the best solution for versioning your services and allowing evolvable APIs.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3432d-123">其他資源</span><span class="sxs-lookup"><span data-stu-id="3432d-123">Additional resources</span></span>

-   <span data-ttu-id="3432d-124">**Scott Hanselman。ASP.NET Core RESTful Web API versioning made easy (ASP.NET Core RESTful Web API 版本設定變得更輕鬆)**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx></span><span class="sxs-lookup"><span data-stu-id="3432d-124">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
<http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx></span></span>

-   <span data-ttu-id="3432d-125">**符合 REST 限制的 Web API 版本控制**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span><span class="sxs-lookup"><span data-stu-id="3432d-125">**Versioning a RESTful web API**
[*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span></span>

-   <span data-ttu-id="3432d-126">**Roy Fielding。Versioning, Hypermedia, and REST (版本控制、超媒體及 REST)**
    <https://www.infoq.com/articles/roy-fielding-on-versioning></span><span class="sxs-lookup"><span data-stu-id="3432d-126">**Roy Fielding. Versioning, Hypermedia, and REST**
<https://www.infoq.com/articles/roy-fielding-on-versioning></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="3432d-127">[上一頁] (asynchronous-message-based-communication.md) [下一頁] (microservices-addressability-service-registry.md)</span><span class="sxs-lookup"><span data-stu-id="3432d-127">[Previous] (asynchronous-message-based-communication.md) [Next] (microservices-addressability-service-registry.md)</span></span>
