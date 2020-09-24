---
title: 服務網格通訊基礎結構
description: 瞭解服務網格技術如何簡化雲端原生微服務通訊
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 39dc1ded06eb0b92a2a1b40cfe981d9bd49bf381
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165945"
---
# <a name="service-mesh-communication-infrastructure"></a><span data-ttu-id="9cb93-103">服務網格通訊基礎結構</span><span class="sxs-lookup"><span data-stu-id="9cb93-103">Service Mesh communication infrastructure</span></span>

<span data-ttu-id="9cb93-104">在本章節中，我們探討了微服務通訊的挑戰。</span><span class="sxs-lookup"><span data-stu-id="9cb93-104">Throughout this chapter, we've explored the challenges of microservice communication.</span></span> <span data-ttu-id="9cb93-105">我們說過，開發小組必須區分後端服務與彼此通訊的方式。</span><span class="sxs-lookup"><span data-stu-id="9cb93-105">We said that development teams need to be sensitive to how back-end services communicate with each other.</span></span> <span data-ttu-id="9cb93-106">在理想情況下，服務間通訊越少越好。</span><span class="sxs-lookup"><span data-stu-id="9cb93-106">Ideally, the less inter-service communication, the better.</span></span> <span data-ttu-id="9cb93-107">不過，因為後端服務通常會依賴另一個來完成作業，所以不一定可以避免。</span><span class="sxs-lookup"><span data-stu-id="9cb93-107">However, avoidance isn't always possible as back-end services often rely on one another to complete operations.</span></span>

<span data-ttu-id="9cb93-108">我們探討了各種不同的方法來執行同步 HTTP 通訊和非同步訊息處理。</span><span class="sxs-lookup"><span data-stu-id="9cb93-108">We explored different approaches for implementing synchronous HTTP communication and asynchronous messaging.</span></span> <span data-ttu-id="9cb93-109">在每個案例中，開發人員會負擔執行通訊程式碼。</span><span class="sxs-lookup"><span data-stu-id="9cb93-109">In each of the cases, the developer is burdened with implementing communication code.</span></span> <span data-ttu-id="9cb93-110">通訊程式碼很複雜，而且需要大量時間。</span><span class="sxs-lookup"><span data-stu-id="9cb93-110">Communication code is complex and time intensive.</span></span> <span data-ttu-id="9cb93-111">不正確的決策可能會導致明顯的效能問題。</span><span class="sxs-lookup"><span data-stu-id="9cb93-111">Incorrect decisions can lead to significant performance issues.</span></span>

<span data-ttu-id="9cb93-112">更新式的方法，微服務通訊中心圍繞著全新且快速發展的技術，以提供 *服務網格*。</span><span class="sxs-lookup"><span data-stu-id="9cb93-112">A more modern approach to microservice communication centers around a new and rapidly evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="9cb93-113">[服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是可設定的基礎結構層，具有內建功能可處理服務對服務的通訊、復原能力，以及許多跨領域考慮。</span><span class="sxs-lookup"><span data-stu-id="9cb93-113">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service-to-service communication, resiliency, and many cross-cutting concerns.</span></span> <span data-ttu-id="9cb93-114">它會將這些疑慮的責任移出微服務和服務網格層。</span><span class="sxs-lookup"><span data-stu-id="9cb93-114">It moves the responsibility for these concerns out of the microservices and into service mesh layer.</span></span> <span data-ttu-id="9cb93-115">從您的微服務抽離通訊。</span><span class="sxs-lookup"><span data-stu-id="9cb93-115">Communication is abstracted away from your microservices.</span></span>

<span data-ttu-id="9cb93-116">服務網格的主要元件是 proxy。</span><span class="sxs-lookup"><span data-stu-id="9cb93-116">A key component of a service mesh is a proxy.</span></span> <span data-ttu-id="9cb93-117">在雲端原生應用程式中，proxy 的實例通常會與每個微服務共存。</span><span class="sxs-lookup"><span data-stu-id="9cb93-117">In a cloud-native application, an instance of a proxy is typically colocated with each microservice.</span></span> <span data-ttu-id="9cb93-118">當它們在不同的進程中執行時，兩者會緊密連結並共用相同的生命週期。</span><span class="sxs-lookup"><span data-stu-id="9cb93-118">While they execute in separate processes, the two are closely linked and share the same lifecycle.</span></span> <span data-ttu-id="9cb93-119">這種模式也稱為 [側車模式](/azure/architecture/patterns/sidecar)，如 [圖 4-24] 所示。</span><span class="sxs-lookup"><span data-stu-id="9cb93-119">This pattern, known as the [Sidecar pattern](/azure/architecture/patterns/sidecar), and is shown in Figure 4-24.</span></span>

![具有側面汽車的服務網格](./media/service-mesh-with-side-car.png)

<span data-ttu-id="9cb93-121">**圖 4-24**：</span><span class="sxs-lookup"><span data-stu-id="9cb93-121">**Figure 4-24**.</span></span> <span data-ttu-id="9cb93-122">具有側面汽車的服務網格</span><span class="sxs-lookup"><span data-stu-id="9cb93-122">Service mesh with a side car</span></span>

<span data-ttu-id="9cb93-123">在上圖中，請注意，在每個微服務旁執行的 proxy 會攔截訊息。</span><span class="sxs-lookup"><span data-stu-id="9cb93-123">Note in the previous figure how messages are intercepted by a proxy that runs alongside each microservice.</span></span> <span data-ttu-id="9cb93-124">每個 proxy 都可以使用微服務特定的流量規則來設定。</span><span class="sxs-lookup"><span data-stu-id="9cb93-124">Each proxy can be configured with traffic rules specific to the microservice.</span></span> <span data-ttu-id="9cb93-125">它瞭解訊息，並且可以將訊息路由傳送到您的服務和外界。</span><span class="sxs-lookup"><span data-stu-id="9cb93-125">It understands messages and can route them across your services and the outside world.</span></span>

<span data-ttu-id="9cb93-126">除了管理服務對服務的通訊之外，服務網狀也提供服務探索和負載平衡的支援。</span><span class="sxs-lookup"><span data-stu-id="9cb93-126">Along with managing service-to-service communication, the Service Mesh provides support for service discovery and load balancing.</span></span>

<span data-ttu-id="9cb93-127">一旦設定之後，服務網格會具有高功能。</span><span class="sxs-lookup"><span data-stu-id="9cb93-127">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="9cb93-128">網格會從服務探索端點抓取對應的實例集區。</span><span class="sxs-lookup"><span data-stu-id="9cb93-128">The mesh retrieves a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="9cb93-129">它會將要求傳送至特定的服務實例，並記錄結果的延遲和回應類型。</span><span class="sxs-lookup"><span data-stu-id="9cb93-129">It sends a request to a specific service instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="9cb93-130">它會根據不同的因素，選擇最可能傳回快速回應的實例，包括最近要求的觀察延遲。</span><span class="sxs-lookup"><span data-stu-id="9cb93-130">It chooses the instance most likely to return a fast response based on different factors, including the observed latency for recent requests.</span></span>

<span data-ttu-id="9cb93-131">服務網格會管理應用層級的流量、通訊和網路考慮。</span><span class="sxs-lookup"><span data-stu-id="9cb93-131">A service mesh manages traffic, communication, and networking concerns at the application level.</span></span> <span data-ttu-id="9cb93-132">它瞭解訊息和要求。</span><span class="sxs-lookup"><span data-stu-id="9cb93-132">It understands messages and requests.</span></span> <span data-ttu-id="9cb93-133">服務網格通常會與容器協調器整合。</span><span class="sxs-lookup"><span data-stu-id="9cb93-133">A service mesh typically integrates with a container orchestrator.</span></span> <span data-ttu-id="9cb93-134">Kubernetes 支援可延伸的架構，可在其中新增服務網格。</span><span class="sxs-lookup"><span data-stu-id="9cb93-134">Kubernetes supports an extensible architecture in which a service mesh can be added.</span></span>

<span data-ttu-id="9cb93-135">在第6章中，我們將深入探討服務網格技術，包括對其架構和可用開放原始碼執行的討論。</span><span class="sxs-lookup"><span data-stu-id="9cb93-135">In chapter 6, we deep-dive into Service Mesh technologies including a discussion on its architecture and available open-source implementations.</span></span>

## <a name="summary"></a><span data-ttu-id="9cb93-136">摘要</span><span class="sxs-lookup"><span data-stu-id="9cb93-136">Summary</span></span>

<span data-ttu-id="9cb93-137">在本章中，我們討論了雲端原生通訊模式。</span><span class="sxs-lookup"><span data-stu-id="9cb93-137">In this chapter, we discussed cloud-native communication patterns.</span></span> <span data-ttu-id="9cb93-138">我們一開始先檢查前端用戶端與後端微服務通訊的方式。</span><span class="sxs-lookup"><span data-stu-id="9cb93-138">We started by examining how front-end clients communicate with back-end microservices.</span></span> <span data-ttu-id="9cb93-139">過程中，我們討論了 API 閘道平臺和即時通訊。</span><span class="sxs-lookup"><span data-stu-id="9cb93-139">Along the way, we talked about API Gateway platforms and real-time communication.</span></span> <span data-ttu-id="9cb93-140">我們接著探討了微服務如何與其他後端服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="9cb93-140">We then looked at how microservices communicate with other back-end services.</span></span> <span data-ttu-id="9cb93-141">我們探討了同步的 HTTP 通訊和跨服務的非同步訊息。</span><span class="sxs-lookup"><span data-stu-id="9cb93-141">We looked at both synchronous HTTP communication and asynchronous messaging across services.</span></span> <span data-ttu-id="9cb93-142">我們討論了 gRPC，這是雲端原生世界中即將推出的技術。</span><span class="sxs-lookup"><span data-stu-id="9cb93-142">We covered gRPC, an upcoming technology in the cloud-native world.</span></span> <span data-ttu-id="9cb93-143">最後，我們推出了一項全新且快速發展的技術，其可簡化微服務通訊的服務網格。</span><span class="sxs-lookup"><span data-stu-id="9cb93-143">Finally, we introduced a new and rapidly evolving technology entitled Service Mesh that can streamline microservice communication.</span></span>

<span data-ttu-id="9cb93-144">特別著重于受控 Azure 服務，可協助在雲端原生系統中執行通訊：</span><span class="sxs-lookup"><span data-stu-id="9cb93-144">Special emphasis was on managed Azure services that can help implement communication in cloud-native systems:</span></span>

- [<span data-ttu-id="9cb93-145">Azure 應用程式閘道</span><span class="sxs-lookup"><span data-stu-id="9cb93-145">Azure Application Gateway</span></span>](/azure/application-gateway/overview)
- [<span data-ttu-id="9cb93-146">Azure API 管理</span><span class="sxs-lookup"><span data-stu-id="9cb93-146">Azure API Management</span></span>](https://azure.microsoft.com/services/api-management/)
- [<span data-ttu-id="9cb93-147">Azure SignalR 服務</span><span class="sxs-lookup"><span data-stu-id="9cb93-147">Azure SignalR Service</span></span>](https://azure.microsoft.com/services/signalr-service/)
- [<span data-ttu-id="9cb93-148">Azure 儲存體佇列</span><span class="sxs-lookup"><span data-stu-id="9cb93-148">Azure Storage Queues</span></span>](/azure/storage/queues/storage-queues-introduction)
- [<span data-ttu-id="9cb93-149">Azure 服務匯流排</span><span class="sxs-lookup"><span data-stu-id="9cb93-149">Azure Service Bus</span></span>](/azure/service-bus-messaging/service-bus-messaging-overview)
- [<span data-ttu-id="9cb93-150">事件格線</span><span class="sxs-lookup"><span data-stu-id="9cb93-150">Azure Event Grid</span></span>](/azure/event-grid/overview)
- [<span data-ttu-id="9cb93-151">Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="9cb93-151">Azure Event Hub</span></span>](https://azure.microsoft.com/services/event-hubs/)

<span data-ttu-id="9cb93-152">接下來我們將移至雲端原生系統中的分散式資料，以及其所提供的優點和挑戰。</span><span class="sxs-lookup"><span data-stu-id="9cb93-152">We next move to distributed data in cloud-native systems and the benefits and challenges that it presents.</span></span>

### <a name="references"></a><span data-ttu-id="9cb93-153">參考資料</span><span class="sxs-lookup"><span data-stu-id="9cb93-153">References</span></span>

- [<span data-ttu-id="9cb93-154">.NET 微服務：容器化 .NET 應用程式的架構</span><span class="sxs-lookup"><span data-stu-id="9cb93-154">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="9cb93-155">設計微服務的服務間通訊</span><span class="sxs-lookup"><span data-stu-id="9cb93-155">Designing Interservice Communication for Microservices</span></span>](/azure/architecture/microservices/design/interservice-communication)

- [<span data-ttu-id="9cb93-156">Azure SignalR Service 是完全受控的服務，可新增即時功能</span><span class="sxs-lookup"><span data-stu-id="9cb93-156">Azure SignalR Service, a fully managed service to add real-time functionality</span></span>](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [<span data-ttu-id="9cb93-157">Azure API 閘道輸入控制器</span><span class="sxs-lookup"><span data-stu-id="9cb93-157">Azure API Gateway Ingress Controller</span></span>](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [<span data-ttu-id="9cb93-158">關於 Azure Kubernetes Service (AKS 中的輸入) </span><span class="sxs-lookup"><span data-stu-id="9cb93-158">About Ingress in Azure Kubernetes Service (AKS)</span></span>](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [<span data-ttu-id="9cb93-159">gRPC 檔</span><span class="sxs-lookup"><span data-stu-id="9cb93-159">gRPC Documentation</span></span>](https://grpc.io/docs/guides/)

- [<span data-ttu-id="9cb93-160">適用於 WCF 開發人員的 gRPC</span><span class="sxs-lookup"><span data-stu-id="9cb93-160">gRPC for WCF Developers</span></span>](../grpc-for-wcf-developers/index.md)

- [<span data-ttu-id="9cb93-161">比較 gRPC 服務與 HTTP Api</span><span class="sxs-lookup"><span data-stu-id="9cb93-161">Comparing gRPC Services with HTTP APIs</span></span>](/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [<span data-ttu-id="9cb93-162">使用 .NET 建立 gRPC 服務影片</span><span class="sxs-lookup"><span data-stu-id="9cb93-162">Building gRPC Services with .NET video</span></span>](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
><span data-ttu-id="9cb93-163">[上一個](grpc.md) 
>[下一步](distributed-data.md)</span><span class="sxs-lookup"><span data-stu-id="9cb93-163">[Previous](grpc.md)
[Next](distributed-data.md)</span></span>
