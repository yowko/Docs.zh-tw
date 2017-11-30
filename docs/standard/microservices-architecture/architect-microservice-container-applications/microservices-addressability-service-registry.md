---
title: "Microservices 可定址性與在服務登錄"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Microservices 可定址性與在服務登錄"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 19a0200dadfb90a455de690d880f4eeae4772ed7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a><span data-ttu-id="22d8a-104">Microservices 可定址性與在服務登錄</span><span class="sxs-lookup"><span data-stu-id="22d8a-104">Microservices addressability and the service registry</span></span>

<span data-ttu-id="22d8a-105">每個微服務有唯一的名稱 (URL)，用來解析其位置。</span><span class="sxs-lookup"><span data-stu-id="22d8a-105">Each microservice has a unique name (URL) that is used to resolve its location.</span></span> <span data-ttu-id="22d8a-106">您的微服務必須是可定址，只要它正在執行。</span><span class="sxs-lookup"><span data-stu-id="22d8a-106">Your microservice needs to be addressable wherever it is running.</span></span> <span data-ttu-id="22d8a-107">如果您有想想執行特定的微服務相關的電腦，可能發生錯誤快速。</span><span class="sxs-lookup"><span data-stu-id="22d8a-107">If you have to think about which computer is running a particular microservice, things can go bad quickly.</span></span> <span data-ttu-id="22d8a-108">DNS 解析 URL，特定電腦的相同方式，在您的微服務需要有唯一的名稱，使其目前位置是可探索。</span><span class="sxs-lookup"><span data-stu-id="22d8a-108">In the same way that DNS resolves a URL to a particular computer, your microservice needs to have a unique name so that its current location is discoverable.</span></span> <span data-ttu-id="22d8a-109">Microservices 需要可定址的名稱，因此獨立於基礎結構上執行。</span><span class="sxs-lookup"><span data-stu-id="22d8a-109">Microservices need addressable names that make them independent from the infrastructure that they are running on.</span></span> <span data-ttu-id="22d8a-110">這暗示會如何部署您的服務和其探索的方式之間的互動因為需要有[服務登錄](http://microservices.io/patterns/service-registry.html)。</span><span class="sxs-lookup"><span data-stu-id="22d8a-110">This implies that there is an interaction between how your service is deployed and how it is discovered, because there needs to be a [service registry](http://microservices.io/patterns/service-registry.html).</span></span> <span data-ttu-id="22d8a-111">同樣地，在電腦失敗時，登錄服務必須能夠指出現在正在服務執行。</span><span class="sxs-lookup"><span data-stu-id="22d8a-111">In the same vein, when a computer fails, the registry service must be able to indicate where the service is now running.</span></span>

<span data-ttu-id="22d8a-112">[服務登錄模式](http://microservices.io/patterns/service-registry.html)服務探索的主要部分。</span><span class="sxs-lookup"><span data-stu-id="22d8a-112">The [service registry pattern](http://microservices.io/patterns/service-registry.html) is a key part of service discovery.</span></span> <span data-ttu-id="22d8a-113">登錄是包含的服務執行個體的網路位置的資料庫。</span><span class="sxs-lookup"><span data-stu-id="22d8a-113">The registry is a database containing the network locations of service instances.</span></span> <span data-ttu-id="22d8a-114">服務登錄，就必須是高度可用且最新狀態。</span><span class="sxs-lookup"><span data-stu-id="22d8a-114">A service registry needs to be highly available and up to date.</span></span> <span data-ttu-id="22d8a-115">用戶端可以快取取得從服務登錄的網路位置。</span><span class="sxs-lookup"><span data-stu-id="22d8a-115">Clients could cache network locations obtained from the service registry.</span></span> <span data-ttu-id="22d8a-116">不過，該資訊最終會過期，而且用戶端不會再找出服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="22d8a-116">However, that information eventually goes out of date and clients can no longer discover service instances.</span></span> <span data-ttu-id="22d8a-117">因此，服務登錄使用複寫通訊協定，以維護一致性的伺服器叢集所組成。</span><span class="sxs-lookup"><span data-stu-id="22d8a-117">Consequently, a service registry consists of a cluster of servers that use a replication protocol to maintain consistency.</span></span>

<span data-ttu-id="22d8a-118">有些微服務部署在環境中 （稱為群集，以在稍後的章節中討論），服務探索是內建。</span><span class="sxs-lookup"><span data-stu-id="22d8a-118">In some microservice deployment environments (called clusters, to be covered in a later section), service discovery is built-in.</span></span> <span data-ttu-id="22d8a-119">例如，在 Azure 容器服務環境中，Kubernetes DC/OS 與馬拉松可以處理服務執行個體登錄和解除登錄。</span><span class="sxs-lookup"><span data-stu-id="22d8a-119">For example, within an Azure Container Service environment, Kubernetes and DC/OS with Marathon can handle service instance registration and deregistration.</span></span> <span data-ttu-id="22d8a-120">它們也扮演的角色的伺服器端探索路由器每一部叢集主機上執行的 proxy。</span><span class="sxs-lookup"><span data-stu-id="22d8a-120">They also run a proxy on each cluster host that plays the role of server-side discovery router.</span></span> <span data-ttu-id="22d8a-121">另一個例子是 Azure Service Fabric，它也會提供它的方塊外命名服務透過服務登錄。</span><span class="sxs-lookup"><span data-stu-id="22d8a-121">Another example is Azure Service Fabric, which also provides a service registry through its out-of-the-box Naming Service.</span></span>

<span data-ttu-id="22d8a-122">請注意，某些服務登錄和 API 閘道模式，可協助解決此問題也之間的重疊。</span><span class="sxs-lookup"><span data-stu-id="22d8a-122">Note that there is certain overlap between the service registry and the API gateway pattern, which helps solve this problem as well.</span></span> <span data-ttu-id="22d8a-123">例如， [Service Fabric 反向 Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)是一種 API 閘道服務 Fabrice 命名服務為基礎和以協助解析位址解析為內部服務實作。</span><span class="sxs-lookup"><span data-stu-id="22d8a-123">For example, the [Service Fabric Reverse Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) is a type of implementation of an API Gateway that is based on the Service Fabrice Naming Service and that helps resolve address resolution to the internal services.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="22d8a-124">其他資源</span><span class="sxs-lookup"><span data-stu-id="22d8a-124">Additional resources</span></span>

-   <span data-ttu-id="22d8a-125">**Chris Richardson。模式： 服務登錄**
    *http://microservices.io/patterns/service-registry.html*</span><span class="sxs-lookup"><span data-stu-id="22d8a-125">**Chris Richardson. Pattern: Service registry**
*http://microservices.io/patterns/service-registry.html*</span></span>

-   <span data-ttu-id="22d8a-126">**Auth0。服務登錄**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)</span><span class="sxs-lookup"><span data-stu-id="22d8a-126">**Auth0. The Service Registry**
[*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)</span></span>

-   <span data-ttu-id="22d8a-127">**Gabriel Schenker。服務探索**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)</span><span class="sxs-lookup"><span data-stu-id="22d8a-127">**Gabriel Schenker. Service discovery**
[*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="22d8a-128">[上一個](維護的微服務-apis.md) [下一步] (microservice-based-composite-ui-shape-layout.md)</span><span class="sxs-lookup"><span data-stu-id="22d8a-128">[Previous] (maintain-microservice-apis.md) [Next] (microservice-based-composite-ui-shape-layout.md)</span></span>
