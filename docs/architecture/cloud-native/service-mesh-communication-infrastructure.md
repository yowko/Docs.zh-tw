---
title: 服務網格通訊基礎結構
description: 瞭解服務網格技術如何簡化雲原生微服務通信
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 8bb57e990dbf1baf8c246fe4aacfbb2904a251e6
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805747"
---
# <a name="service-mesh-communication-infrastructure"></a><span data-ttu-id="6e371-103">服務網格通訊基礎結構</span><span class="sxs-lookup"><span data-stu-id="6e371-103">Service Mesh communication infrastructure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6e371-104">在本章中,我們探討了微服務通信的挑戰。</span><span class="sxs-lookup"><span data-stu-id="6e371-104">Throughout this chapter, we've explored the challenges of microservice communication.</span></span> <span data-ttu-id="6e371-105">我們說過,開發團隊需要對後端服務如何相互溝通敏感。</span><span class="sxs-lookup"><span data-stu-id="6e371-105">We said that development teams need to be sensitive to how back-end services communicate with each other.</span></span> <span data-ttu-id="6e371-106">理想情況下,服務間通信越少越好。</span><span class="sxs-lookup"><span data-stu-id="6e371-106">Ideally, the less inter-service communication, the better.</span></span> <span data-ttu-id="6e371-107">但是,由於後端服務通常相互依賴來完成操作,因此並非始終能夠避免。</span><span class="sxs-lookup"><span data-stu-id="6e371-107">However, avoidance isn't always possible as back-end services often rely on one another to complete operations.</span></span>

<span data-ttu-id="6e371-108">我們探討了實現同步 HTTP 通信和非同步訊息傳遞的不同方法。</span><span class="sxs-lookup"><span data-stu-id="6e371-108">We explored different approaches for implementing synchronous HTTP communication and asynchronous messaging.</span></span> <span data-ttu-id="6e371-109">在每種情況下,開發人員都肩負著實現通信代碼的負擔。</span><span class="sxs-lookup"><span data-stu-id="6e371-109">In each of the cases, the developer is burdened with implementing communication code.</span></span> <span data-ttu-id="6e371-110">通信代碼複雜且耗時。</span><span class="sxs-lookup"><span data-stu-id="6e371-110">Communication code is complex and time intensive.</span></span> <span data-ttu-id="6e371-111">不正確的決策可能會導致嚴重的性能問題。</span><span class="sxs-lookup"><span data-stu-id="6e371-111">Incorrect decisions can lead to significant performance issues.</span></span>

<span data-ttu-id="6e371-112">一種更現代的微服務通信方法圍繞一種名為 *「服務網格*」的新的、快速發展的技術。</span><span class="sxs-lookup"><span data-stu-id="6e371-112">A more modern approach to microservice communication centers around a new and rapidly evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="6e371-113">[服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是一個可配置的基礎結構層,具有處理服務到服務的通信、恢復能力和許多交叉問題的能力。</span><span class="sxs-lookup"><span data-stu-id="6e371-113">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service-to-service communication, resiliency, and many cross-cutting concerns.</span></span> <span data-ttu-id="6e371-114">它將這些問題的責任從微服務轉移到服務網格層中。</span><span class="sxs-lookup"><span data-stu-id="6e371-114">It moves the responsibility for these concerns out of the microservices and into service mesh layer.</span></span> <span data-ttu-id="6e371-115">通信從微服務中抽象出來。</span><span class="sxs-lookup"><span data-stu-id="6e371-115">Communication is abstracted away from your microservices.</span></span>

<span data-ttu-id="6e371-116">服務網格的關鍵元件是代理。</span><span class="sxs-lookup"><span data-stu-id="6e371-116">A key component of a service mesh is a proxy.</span></span> <span data-ttu-id="6e371-117">在雲本機應用程式中,代理的實例通常與每個微服務共存。</span><span class="sxs-lookup"><span data-stu-id="6e371-117">In a cloud-native application, an instance of a proxy is typically colocated with each microservice.</span></span> <span data-ttu-id="6e371-118">當它們在單獨的進程中執行時,兩者是緊密相連的,並且共用相同的生命週期。</span><span class="sxs-lookup"><span data-stu-id="6e371-118">While they execute in separate processes, the two are closely linked and share the same lifecycle.</span></span> <span data-ttu-id="6e371-119">此模式稱為[側車模式](https://docs.microsoft.com/azure/architecture/patterns/sidecar),如圖 4-24 所示。</span><span class="sxs-lookup"><span data-stu-id="6e371-119">This pattern, known as the [Sidecar pattern](https://docs.microsoft.com/azure/architecture/patterns/sidecar), and is shown in Figure 4-24.</span></span>

![帶側車的服務網](./media/service-mesh-with-side-car.png)

<span data-ttu-id="6e371-121">**圖 4-24**：</span><span class="sxs-lookup"><span data-stu-id="6e371-121">**Figure 4-24**.</span></span> <span data-ttu-id="6e371-122">帶側車的服務網</span><span class="sxs-lookup"><span data-stu-id="6e371-122">Service mesh with a side car</span></span>

<span data-ttu-id="6e371-123">請注意,在上圖中,與每個微服務一起運行的代理如何截獲消息。</span><span class="sxs-lookup"><span data-stu-id="6e371-123">Note in the previous figure how messages are intercepted by a proxy that runs alongside each microservice.</span></span> <span data-ttu-id="6e371-124">每個代理都可以配置特定於微服務的流量規則。</span><span class="sxs-lookup"><span data-stu-id="6e371-124">Each proxy can be configured with traffic rules specific to the microservice.</span></span> <span data-ttu-id="6e371-125">它瞭解消息,並可以路由它們跨越您的服務和外部世界。</span><span class="sxs-lookup"><span data-stu-id="6e371-125">It understands messages and can route them across your services and the outside world.</span></span>

<span data-ttu-id="6e371-126">除了管理服務到服務的通信外,服務網格還提供對服務發現和負載平衡的支援。</span><span class="sxs-lookup"><span data-stu-id="6e371-126">Along with managing service-to-service communication, the Service Mesh provides support for service discovery and load balancing.</span></span>

<span data-ttu-id="6e371-127">配置後,服務網格功能極致。</span><span class="sxs-lookup"><span data-stu-id="6e371-127">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="6e371-128">網格從服務發現終結點檢索相應的實例池。</span><span class="sxs-lookup"><span data-stu-id="6e371-128">The mesh retrieves a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="6e371-129">它將請求發送到特定的服務實例,記錄結果的延遲和回應類型。</span><span class="sxs-lookup"><span data-stu-id="6e371-129">It sends a request to a specific service instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="6e371-130">它根據不同因素(包括最近請求的觀察延遲)選擇最有可能返回快速回應的實例。</span><span class="sxs-lookup"><span data-stu-id="6e371-130">It chooses the instance most likely to return a fast response based on different factors, including the observed latency for recent requests.</span></span>

<span data-ttu-id="6e371-131">服務網格在應用程式級別管理流量、通信和網路問題。</span><span class="sxs-lookup"><span data-stu-id="6e371-131">A service mesh manages traffic, communication, and networking concerns at the application level.</span></span> <span data-ttu-id="6e371-132">它瞭解消息和請求。</span><span class="sxs-lookup"><span data-stu-id="6e371-132">It understands messages and requests.</span></span> <span data-ttu-id="6e371-133">服務網格通常與容器協調器集成。</span><span class="sxs-lookup"><span data-stu-id="6e371-133">A service mesh typically integrates with a container orchestrator.</span></span> <span data-ttu-id="6e371-134">Kubernetes 支援一種可擴展的體系結構,可以在其中添加服務網格。</span><span class="sxs-lookup"><span data-stu-id="6e371-134">Kubernetes supports an extensible architecture in which a service mesh can be added.</span></span>

<span data-ttu-id="6e371-135">在第 6 章中,我們深入探討了服務網格技術,包括討論其體系結構和可用的開源實現。</span><span class="sxs-lookup"><span data-stu-id="6e371-135">In chapter 6, we deep-dive into Service Mesh technologies including a discussion on its architecture and available open-source implementations.</span></span>

## <a name="summary"></a><span data-ttu-id="6e371-136">摘要</span><span class="sxs-lookup"><span data-stu-id="6e371-136">Summary</span></span>

<span data-ttu-id="6e371-137">在本章中,我們討論了雲原生通信模式。</span><span class="sxs-lookup"><span data-stu-id="6e371-137">In this chapter, we discussed cloud-native communication patterns.</span></span> <span data-ttu-id="6e371-138">我們首先研究前端用戶端如何與後端微服務通信。</span><span class="sxs-lookup"><span data-stu-id="6e371-138">We started by examining how front-end clients communicate with back-end microservices.</span></span> <span data-ttu-id="6e371-139">在此過程中,我們討論了 API 閘道平臺和即時通信。</span><span class="sxs-lookup"><span data-stu-id="6e371-139">Along the way, we talked about API Gateway platforms and real-time communication.</span></span> <span data-ttu-id="6e371-140">然後,我們研究了微服務如何與其他後端服務通信。</span><span class="sxs-lookup"><span data-stu-id="6e371-140">We then looked at how microservices communicate with other back-end services.</span></span> <span data-ttu-id="6e371-141">我們研究了同步 HTTP 通信和跨服務的非同步訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="6e371-141">We looked at both synchronous HTTP communication and asynchronous messaging across services.</span></span> <span data-ttu-id="6e371-142">我們介紹了 gRPC,這是雲原生世界中即將推出的技術。</span><span class="sxs-lookup"><span data-stu-id="6e371-142">We covered gRPC, an upcoming technology in the cloud-native world.</span></span> <span data-ttu-id="6e371-143">最後,我們推出了一種名為"服務網格"的快速發展的新技術,該技術可以簡化微服務通信。</span><span class="sxs-lookup"><span data-stu-id="6e371-143">Finally, we introduced a new and rapidly evolving technology entitled Service Mesh that can streamline microservice communication.</span></span>

<span data-ttu-id="6e371-144">特別強調託管 Azure 服務,這些服務可説明在雲本機系統中實現通信:</span><span class="sxs-lookup"><span data-stu-id="6e371-144">Special emphasis was on managed Azure services that can help implement communication in cloud-native systems:</span></span>

- [<span data-ttu-id="6e371-145">Azure 應用程式閘道</span><span class="sxs-lookup"><span data-stu-id="6e371-145">Azure Application Gateway</span></span>](https://docs.microsoft.com/azure/application-gateway/overview)
- [<span data-ttu-id="6e371-146">Azure API 管理</span><span class="sxs-lookup"><span data-stu-id="6e371-146">Azure API Management</span></span>](https://azure.microsoft.com/services/api-management/)
- [<span data-ttu-id="6e371-147">Azure SignalR 服務</span><span class="sxs-lookup"><span data-stu-id="6e371-147">Azure SignalR Service</span></span>](https://azure.microsoft.com/services/signalr-service/)
- [<span data-ttu-id="6e371-148">Azure 儲存體佇列</span><span class="sxs-lookup"><span data-stu-id="6e371-148">Azure Storage Queues</span></span>](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [<span data-ttu-id="6e371-149">Azure 服務匯流排</span><span class="sxs-lookup"><span data-stu-id="6e371-149">Azure Service Bus</span></span>](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [<span data-ttu-id="6e371-150">Azure 事件網格</span><span class="sxs-lookup"><span data-stu-id="6e371-150">Azure Event Grid</span></span>](https://docs.microsoft.com/azure/event-grid/overview)
- [<span data-ttu-id="6e371-151">Azure 事件中心</span><span class="sxs-lookup"><span data-stu-id="6e371-151">Azure Event Hub</span></span>](https://azure.microsoft.com/services/event-hubs/)

<span data-ttu-id="6e371-152">接下來,我們將轉向雲原生系統中的分散式數據及其帶來的益處和挑戰。</span><span class="sxs-lookup"><span data-stu-id="6e371-152">We next move to distributed data in cloud-native systems and the benefits and challenges that it presents.</span></span>

### <a name="references"></a><span data-ttu-id="6e371-153">參考</span><span class="sxs-lookup"><span data-stu-id="6e371-153">References</span></span>

- [<span data-ttu-id="6e371-154">.NET 微服務:容器化 .NET 應用程式的體系結構</span><span class="sxs-lookup"><span data-stu-id="6e371-154">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="6e371-155">為微服務設計服務間通訊</span><span class="sxs-lookup"><span data-stu-id="6e371-155">Designing Interservice Communication for Microservices</span></span>](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [<span data-ttu-id="6e371-156">Azure SignalR 服務,一個完全託管的服務,用於新增即時功能</span><span class="sxs-lookup"><span data-stu-id="6e371-156">Azure SignalR Service, a fully managed service to add real-time functionality</span></span>](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [<span data-ttu-id="6e371-157">Azure API 閘道閘道控制器</span><span class="sxs-lookup"><span data-stu-id="6e371-157">Azure API Gateway Ingress Controller</span></span>](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [<span data-ttu-id="6e371-158">關於 Azure 庫伯內斯服務 (AKS) 中的入口</span><span class="sxs-lookup"><span data-stu-id="6e371-158">About Ingress in Azure Kubernetes Service (AKS)</span></span>](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [<span data-ttu-id="6e371-159">gRPC 文件</span><span class="sxs-lookup"><span data-stu-id="6e371-159">gRPC Documentation</span></span>](https://grpc.io/docs/guides/)

- [<span data-ttu-id="6e371-160">適用於 WCF 開發人員的 gRPC</span><span class="sxs-lookup"><span data-stu-id="6e371-160">gRPC for WCF Developers</span></span>](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [<span data-ttu-id="6e371-161">將 gRPC 服務與 HTTP API 進行比較</span><span class="sxs-lookup"><span data-stu-id="6e371-161">Comparing gRPC Services with HTTP APIs</span></span>](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [<span data-ttu-id="6e371-162">使用 .NET 視訊建構 gRPC 服務</span><span class="sxs-lookup"><span data-stu-id="6e371-162">Building gRPC Services with .NET video</span></span>](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
><span data-ttu-id="6e371-163">[前一個](grpc.md)
>[下一個](database-per-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="6e371-163">[Previous](grpc.md)
[Next](database-per-microservice.md)</span></span>
