---
title: 微服務可定址性和服務登錄
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 微服務可定址性和服務登錄
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ec3ccdd823e00d148bb8a97e906132f44e7fa727
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106667"
---
# <a name="microservices-addressability-and-the-service-registry"></a><span data-ttu-id="7bb0d-103">微服務可定址性和服務登錄</span><span class="sxs-lookup"><span data-stu-id="7bb0d-103">Microservices addressability and the service registry</span></span>

<span data-ttu-id="7bb0d-104">每個微服務都有用來解析其位置的唯一名稱 (URL)。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-104">Each microservice has a unique name (URL) that is used to resolve its location.</span></span> <span data-ttu-id="7bb0d-105">只要您的微服務正在執行，就必須是可定址的。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-105">Your microservice needs to be addressable wherever it is running.</span></span> <span data-ttu-id="7bb0d-106">如果您必須想一下正在執行特定微服務的電腦為何，問題可能會急遽惡化。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-106">If you have to think about which computer is running a particular microservice, things can go bad quickly.</span></span> <span data-ttu-id="7bb0d-107">就像是 DNS 將 URL 解析為特定電腦，您的微服務也必須具有唯一名稱，才能探索其目前位置。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-107">In the same way that DNS resolves a URL to a particular computer, your microservice needs to have a unique name so that its current location is discoverable.</span></span> <span data-ttu-id="7bb0d-108">微服務需要可定址的名稱，以獨立於其執行所在的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-108">Microservices need addressable names that make them independent from the infrastructure that they are running on.</span></span> <span data-ttu-id="7bb0d-109">這表示服務的部署方式與探索方式之間會有互動，因為需要有[服務登錄](https://microservices.io/patterns/service-registry.html)。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-109">This implies that there is an interaction between how your service is deployed and how it is discovered, because there needs to be a [service registry](https://microservices.io/patterns/service-registry.html).</span></span> <span data-ttu-id="7bb0d-110">同樣地，當電腦失敗時，登錄服務必須能夠指出服務現在正在執行的位置。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-110">In the same vein, when a computer fails, the registry service must be able to indicate where the service is now running.</span></span>

<span data-ttu-id="7bb0d-111">[服務登錄模式](https://microservices.io/patterns/service-registry.html)是服務探索的主要部分。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-111">The [service registry pattern](https://microservices.io/patterns/service-registry.html) is a key part of service discovery.</span></span> <span data-ttu-id="7bb0d-112">登錄是包含服務執行個體之網路位置的資料庫。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-112">The registry is a database containing the network locations of service instances.</span></span> <span data-ttu-id="7bb0d-113">服務登錄必須高度可用且處於最新狀態。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-113">A service registry needs to be highly available and up to date.</span></span> <span data-ttu-id="7bb0d-114">用戶端可以快取從服務登錄取得的網路位置。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-114">Clients could cache network locations obtained from the service registry.</span></span> <span data-ttu-id="7bb0d-115">不過，該資訊最終會過期，此時用戶端將無法再探索服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-115">However, that information eventually goes out of date and clients can no longer discover service instances.</span></span> <span data-ttu-id="7bb0d-116">因此，服務登錄是由伺服器叢集所組成，這些伺服器使用複寫通訊協定來維護一致性。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-116">Consequently, a service registry consists of a cluster of servers that use a replication protocol to maintain consistency.</span></span>

<span data-ttu-id="7bb0d-117">在某些微服務部署環境中 (稱為叢集，本節稍後將會討論)，服務探索是內建的。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-117">In some microservice deployment environments (called clusters, to be covered in a later section), service discovery is built-in.</span></span> <span data-ttu-id="7bb0d-118">例如，在 Azure Container Service 環境中，Kubernetes 和 DC/OS 搭配 MarathonKubernetes 可以處理服務執行個體註冊和取消註冊。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-118">For example, within an Azure Container Service environment, Kubernetes and DC/OS with Marathon can handle service instance registration and deregistration.</span></span> <span data-ttu-id="7bb0d-119">它們也會在扮演伺服器端探索路由器角色的每部叢集主機上執行 Proxy。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-119">They also run a proxy on each cluster host that plays the role of server-side discovery router.</span></span> <span data-ttu-id="7bb0d-120">另一個例子是 Azure Service Fabric，它也會透過現成的 Naming Service 來提供服務登錄。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-120">Another example is Azure Service Fabric, which also provides a service registry through its out-of-the-box Naming Service.</span></span>

<span data-ttu-id="7bb0d-121">請注意，服務登錄與 API 閘道模式之間一定會有重疊，因此也可協助解決此問題。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-121">Note that there is certain overlap between the service registry and the API gateway pattern, which helps solve this problem as well.</span></span> <span data-ttu-id="7bb0d-122">例如，[Service Fabric 反向 Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) 是一種 API 閘道實作類型，該類型是以 Service Fabrice Naming Service 為基礎，並可協助將位址解析解析為內部服務。</span><span class="sxs-lookup"><span data-stu-id="7bb0d-122">For example, the [Service Fabric Reverse Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) is a type of implementation of an API Gateway that is based on the Service Fabrice Naming Service and that helps resolve address resolution to the internal services.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7bb0d-123">其他資源</span><span class="sxs-lookup"><span data-stu-id="7bb0d-123">Additional resources</span></span>

-   <span data-ttu-id="7bb0d-124">**Chris Richardson：模式：服務登錄**
    *https://microservices.io/patterns/service-registry.html*</span><span class="sxs-lookup"><span data-stu-id="7bb0d-124">**Chris Richardson. Pattern: Service registry**
*https://microservices.io/patterns/service-registry.html*</span></span>

-   <span data-ttu-id="7bb0d-125">**Auth0：服務登錄**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)</span><span class="sxs-lookup"><span data-stu-id="7bb0d-125">**Auth0. The Service Registry**
[*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)</span></span>

-   <span data-ttu-id="7bb0d-126">**Gabriel Schenker：服務探索**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)</span><span class="sxs-lookup"><span data-stu-id="7bb0d-126">**Gabriel Schenker. Service discovery**
[*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7bb0d-127">[上一頁](maintain-microservice-apis.md)
[下一頁](microservice-based-composite-ui-shape-layout.md)</span><span class="sxs-lookup"><span data-stu-id="7bb0d-127">[Previous](maintain-microservice-apis.md)
[Next](microservice-based-composite-ui-shape-layout.md)</span></span>
