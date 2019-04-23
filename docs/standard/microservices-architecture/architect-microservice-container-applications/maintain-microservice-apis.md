---
title: 建立、發展以及版本控制微服務 API 與協定
description: 因為需求會變更，所以要建立考慮演進和版本控制的 API 與合約。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: f42de3895f7f9affe09891fd89621fbb414313e9
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612104"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a><span data-ttu-id="274bf-103">建立、發展以及版本控制微服務 API 與協定</span><span class="sxs-lookup"><span data-stu-id="274bf-103">Creating, evolving, and versioning microservice APIs and contracts</span></span>

<span data-ttu-id="274bf-104">微服務 API 是服務與其用戶端之間的協定。</span><span class="sxs-lookup"><span data-stu-id="274bf-104">A microservice API is a contract between the service and its clients.</span></span> <span data-ttu-id="274bf-105">您只能在不中斷微服務 API 合約的前提下獨立演進微服務，因此合約十分重要。</span><span class="sxs-lookup"><span data-stu-id="274bf-105">You'll be able to evolve a microservice independently only if you do not break its API contract, which is why the contract is so important.</span></span> <span data-ttu-id="274bf-106">如果您變更協定，會影響用戶端應用程式或您的 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="274bf-106">If you change the contract, it will impact your client applications or your API Gateway.</span></span>

<span data-ttu-id="274bf-107">API 定義的性質取決於您所用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="274bf-107">The nature of the API definition depends on which protocol you're using.</span></span> <span data-ttu-id="274bf-108">例如，若您使用傳訊 (像是 [AMQP](https://www.amqp.org/))，API 會由訊息類型組成。</span><span class="sxs-lookup"><span data-stu-id="274bf-108">For instance, if you're using messaging (like [AMQP](https://www.amqp.org/)), the API consists of the message types.</span></span> <span data-ttu-id="274bf-109">如果您使用 HTTP 和 RESTful 服務，API 則包含 URL 和要求與回應的 JSON 格式。</span><span class="sxs-lookup"><span data-stu-id="274bf-109">If you're using HTTP and RESTful services, the API consists of the URLs and the request and response JSON formats.</span></span>

<span data-ttu-id="274bf-110">但是，即使您審慎考量您的初始合約，服務 API 仍必須隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="274bf-110">However, even if you're thoughtful about your initial contract, a service API will need to change over time.</span></span> <span data-ttu-id="274bf-111">發生這種情況時，尤其如果您的 API 是由多個用戶端應用程式取用的公用 API，您通常無法強制所有用戶端升級到新的 API 合約。</span><span class="sxs-lookup"><span data-stu-id="274bf-111">When that happens—and especially if your API is a public API consumed by multiple client applications — you typically can't force all clients to upgrade to your new API contract.</span></span> <span data-ttu-id="274bf-112">您通常需要以累加方式部署服務的新版本，並且要能夠同時執行服務協定的新舊兩種版本。</span><span class="sxs-lookup"><span data-stu-id="274bf-112">You usually need to incrementally deploy new versions of a service in a way that both old and new versions of a service contract are running simultaneously.</span></span> <span data-ttu-id="274bf-113">因此，為您的服務版本控制制定策略非常重要。</span><span class="sxs-lookup"><span data-stu-id="274bf-113">Therefore, it's important to have a strategy for your service versioning.</span></span>

<span data-ttu-id="274bf-114">當 API 變化很小時，例如對 API 新增屬性或參數時，使用舊 API 的用戶端應該切換並使用新版本的服務。</span><span class="sxs-lookup"><span data-stu-id="274bf-114">When the API changes are small, like if you add attributes or parameters to your API, clients that use an older API should switch and work with the new version of the service.</span></span> <span data-ttu-id="274bf-115">您可以為所需的任何遺漏屬性提供預設值，而用戶端可以略過任何額外的回應屬性。</span><span class="sxs-lookup"><span data-stu-id="274bf-115">You might be able to provide default values for any missing attributes that are required, and the clients might be able to ignore any extra response attributes.</span></span>

<span data-ttu-id="274bf-116">不過，有時候您會需要對服務 API 進行重大且不相容的變更。</span><span class="sxs-lookup"><span data-stu-id="274bf-116">However, sometimes you need to make major and incompatible changes to a service API.</span></span> <span data-ttu-id="274bf-117">因為您可能無法強制用戶端應用程式或服務立刻升級到新版本，所以服務必須繼續支援舊版的 API 一段時間。</span><span class="sxs-lookup"><span data-stu-id="274bf-117">Because you might not be able to force client applications or services to upgrade immediately to the new version, a service must support older versions of the API for some period.</span></span> <span data-ttu-id="274bf-118">如果您使用 HTTP 式的機制 (例如 REST)，其中一個方法是在 URL 或是 HTTP 標頭內嵌 API 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="274bf-118">If you're using an HTTP-based mechanism such as REST, one approach is to embed the API version number in the URL or into an HTTP header.</span></span> <span data-ttu-id="274bf-119">然後您可以決定要在相同的服務執行個體中同時實作服務的兩個版本，或是要部署不同的執行個體，分別處理各一個 API 版本。</span><span class="sxs-lookup"><span data-stu-id="274bf-119">Then you can decide between implementing both versions of the service simultaneously within the same service instance, or deploying different instances that each handle a version of the API.</span></span> <span data-ttu-id="274bf-120">有個不錯的方法是以[中繼程序模式](https://en.wikipedia.org/wiki/Mediator_pattern) (例如 [MediatR 程式庫](https://github.com/jbogard/MediatR)) 來將不同實作版本分離為獨立處理常式。</span><span class="sxs-lookup"><span data-stu-id="274bf-120">A good approach for this is the [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern) (for example, [MediatR library](https://github.com/jbogard/MediatR)) to decouple the different implementation versions into independent handlers.</span></span>

<span data-ttu-id="274bf-121">最後，如果您使用 REST 架構，[Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) (超媒體) 即為進行服務版本控制及允許演進 API 的最佳解決方案。</span><span class="sxs-lookup"><span data-stu-id="274bf-121">Finally, if you're using a REST architecture, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) is the best solution for versioning your services and allowing evolvable APIs.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="274bf-122">其他資源</span><span class="sxs-lookup"><span data-stu-id="274bf-122">Additional resources</span></span>

- <span data-ttu-id="274bf-123">**Scott Hanselman。ASP.NET Core RESTful Web API 版本設定變得更加容易** \\</span><span class="sxs-lookup"><span data-stu-id="274bf-123">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** \\</span></span>
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="274bf-124">**進行 RESTful web API 的版本設定** \\</span><span class="sxs-lookup"><span data-stu-id="274bf-124">**Versioning a RESTful web API** \\</span></span>
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="274bf-125">**Roy Fielding。版本設定、超媒體及 REST** \\</span><span class="sxs-lookup"><span data-stu-id="274bf-125">**Roy Fielding. Versioning, Hypermedia, and REST** \\</span></span>
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
><span data-ttu-id="274bf-126">[上一頁](asynchronous-message-based-communication.md)
>[下一頁](microservices-addressability-service-registry.md)</span><span class="sxs-lookup"><span data-stu-id="274bf-126">[Previous](asynchronous-message-based-communication.md)
[Next](microservices-addressability-service-registry.md)</span></span>
