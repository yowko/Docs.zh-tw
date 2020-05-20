---
title: 具有復原性的通訊
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |復原通訊
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 33e4c03c1f3d8c01f72c588326fbb0bdfa512cdd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613742"
---
# <a name="resilient-communications"></a><span data-ttu-id="138ca-103">復原通訊</span><span class="sxs-lookup"><span data-stu-id="138ca-103">Resilient communications</span></span>

<span data-ttu-id="138ca-104">在本書中，我們採用了以微服務為基礎的架構方法。</span><span class="sxs-lookup"><span data-stu-id="138ca-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="138ca-105">雖然這類架構提供重要的優點，但卻帶來許多挑戰：</span><span class="sxs-lookup"><span data-stu-id="138ca-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="138ca-106">*跨進程的網路通訊。*</span><span class="sxs-lookup"><span data-stu-id="138ca-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="138ca-107">每個微服務都會透過網路通訊協定進行通訊，這會引進網路擁塞、延遲和暫時性錯誤。</span><span class="sxs-lookup"><span data-stu-id="138ca-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="138ca-108">*服務探索。*</span><span class="sxs-lookup"><span data-stu-id="138ca-108">*Service discovery.*</span></span> <span data-ttu-id="138ca-109">在具有自己的 IP 位址和埠的電腦叢集上執行時，微服務會如何探索彼此，並彼此通訊？</span><span class="sxs-lookup"><span data-stu-id="138ca-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="138ca-110">*恢復.*</span><span class="sxs-lookup"><span data-stu-id="138ca-110">*Resiliency.*</span></span> <span data-ttu-id="138ca-111">如何管理短期失敗並讓系統穩定？</span><span class="sxs-lookup"><span data-stu-id="138ca-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="138ca-112">*負載平衡。*</span><span class="sxs-lookup"><span data-stu-id="138ca-112">*Load balancing.*</span></span> <span data-ttu-id="138ca-113">輸入流量如何分散到微服務的多個實例？</span><span class="sxs-lookup"><span data-stu-id="138ca-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="138ca-114">*安全級.*</span><span class="sxs-lookup"><span data-stu-id="138ca-114">*Security.*</span></span> <span data-ttu-id="138ca-115">如何強制執行傳輸層級加密和憑證管理等安全性考慮？</span><span class="sxs-lookup"><span data-stu-id="138ca-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="138ca-116">*分散式監視。*</span><span class="sxs-lookup"><span data-stu-id="138ca-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="138ca-117">-如何在多個取用微服務中相互關聯和取得單一要求的可追蹤性和監視？</span><span class="sxs-lookup"><span data-stu-id="138ca-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="138ca-118">您可以使用不同的程式庫和架構來解決這些問題，但執行的成本很高、複雜且耗時。</span><span class="sxs-lookup"><span data-stu-id="138ca-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="138ca-119">最後，您也會得到結合商務邏輯的基礎結構顧慮。</span><span class="sxs-lookup"><span data-stu-id="138ca-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="138ca-120">服務網格</span><span class="sxs-lookup"><span data-stu-id="138ca-120">Service mesh</span></span>

<span data-ttu-id="138ca-121">較佳的方法是一種已發展的*服務網格*技術。</span><span class="sxs-lookup"><span data-stu-id="138ca-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="138ca-122">[服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是一個可設定的基礎結構層，具有可處理服務通訊的內建功能，以及前述的其他挑戰。</span><span class="sxs-lookup"><span data-stu-id="138ca-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="138ca-123">它會將這些考慮移到服務 proxy 中，以將這些顧慮分離。</span><span class="sxs-lookup"><span data-stu-id="138ca-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="138ca-124">Proxy 會部署到個別的進程（稱為[側車](https://docs.microsoft.com/azure/architecture/patterns/sidecar)），以提供與商務程式碼的隔離。</span><span class="sxs-lookup"><span data-stu-id="138ca-124">The proxy is deployed into a separate process (called a [sidecar](https://docs.microsoft.com/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="138ca-125">不過，側車會連結至服務-它是使用它建立的，並且會共用其生命週期。</span><span class="sxs-lookup"><span data-stu-id="138ca-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="138ca-126">圖6-7 顯示這種情況。</span><span class="sxs-lookup"><span data-stu-id="138ca-126">Figure 6-7 shows this scenario.</span></span>

![具有側車的服務網格](./media/service-mesh-with-side-car.png)

<span data-ttu-id="138ca-128">**圖 6-7**。</span><span class="sxs-lookup"><span data-stu-id="138ca-128">**Figure 6-7**.</span></span> <span data-ttu-id="138ca-129">具有側車的服務網格</span><span class="sxs-lookup"><span data-stu-id="138ca-129">Service mesh with a side car</span></span>

<span data-ttu-id="138ca-130">在上圖中，請注意 proxy 如何攔截及管理微服務與叢集之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="138ca-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="138ca-131">服務網格會以邏輯方式分割成兩個不同的元件：[資料平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)和[控制平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)。</span><span class="sxs-lookup"><span data-stu-id="138ca-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="138ca-132">圖6-8 顯示這些元件及其責任。</span><span class="sxs-lookup"><span data-stu-id="138ca-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![服務網格控制項和資料平面](./media/istio-control-and-data-plane.png)

<span data-ttu-id="138ca-134">**圖6-8。**</span><span class="sxs-lookup"><span data-stu-id="138ca-134">**Figure 6-8.**</span></span> <span data-ttu-id="138ca-135">服務網格控制項和資料平面</span><span class="sxs-lookup"><span data-stu-id="138ca-135">Service mesh control and data plane</span></span>

<span data-ttu-id="138ca-136">設定好之後，服務網格就能發揮高功能。</span><span class="sxs-lookup"><span data-stu-id="138ca-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="138ca-137">它可以從服務探索端點取得對應的實例集區。</span><span class="sxs-lookup"><span data-stu-id="138ca-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="138ca-138">然後，網格可以將要求傳送至特定實例，並記錄結果的延遲和回應類型。</span><span class="sxs-lookup"><span data-stu-id="138ca-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="138ca-139">網格可以根據許多因素（包括觀察到最近要求的延遲），選擇最有可能傳回快速回應的實例。</span><span class="sxs-lookup"><span data-stu-id="138ca-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="138ca-140">如果實例沒有回應或失敗，網格將會重試另一個實例上的要求。</span><span class="sxs-lookup"><span data-stu-id="138ca-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="138ca-141">如果傳回錯誤，則網格會從負載平衡集區收回實例，並在修復之後加以重新聲明。</span><span class="sxs-lookup"><span data-stu-id="138ca-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="138ca-142">如果要求超時，網格可能會失敗，然後重試要求。</span><span class="sxs-lookup"><span data-stu-id="138ca-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="138ca-143">網格會在集中式計量系統上捕捉併發出計量和分散式追蹤。</span><span class="sxs-lookup"><span data-stu-id="138ca-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="138ca-144">Istio 和 Envoy</span><span class="sxs-lookup"><span data-stu-id="138ca-144">Istio and Envoy</span></span>

<span data-ttu-id="138ca-145">雖然目前有一些服務網格選項存在，但[Istio](https://istio.io/docs/concepts/what-is-istio/)在撰寫本文時是最受歡迎的。</span><span class="sxs-lookup"><span data-stu-id="138ca-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="138ca-146">Istio 是 IBM、Google 和 Lyft 司機的聯合風險。</span><span class="sxs-lookup"><span data-stu-id="138ca-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="138ca-147">它是一個開放原始碼的供應專案，可以整合到新的或現有的分散式應用程式中。</span><span class="sxs-lookup"><span data-stu-id="138ca-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="138ca-148">這項技術提供一致且完整的解決方案來保護、連接和監視微服務。</span><span class="sxs-lookup"><span data-stu-id="138ca-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="138ca-149">其功能包括：</span><span class="sxs-lookup"><span data-stu-id="138ca-149">Its features include:</span></span>

- <span data-ttu-id="138ca-150">在具有強式身分識別型驗證和授權的叢集中，保護服務對服務的通訊。</span><span class="sxs-lookup"><span data-stu-id="138ca-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="138ca-151">HTTP、 [gRPC](https://grpc.io/)、WEBSOCKET 和 TCP 流量的自動負載平衡。</span><span class="sxs-lookup"><span data-stu-id="138ca-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="138ca-152">使用豐富的路由規則、重試、容錯移轉和錯誤插入來精細控制流量行為。</span><span class="sxs-lookup"><span data-stu-id="138ca-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="138ca-153">可插入的原則層和設定 API，支援存取控制、速率限制和配額。</span><span class="sxs-lookup"><span data-stu-id="138ca-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="138ca-154">叢集中所有流量的自動計量、記錄和追蹤，包括叢集輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="138ca-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="138ca-155">Istio 執行的主要元件是具有[Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)資格的 proxy 服務。</span><span class="sxs-lookup"><span data-stu-id="138ca-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="138ca-156">它會與每個服務一起執行，並為下列功能提供平臺中立的基礎：</span><span class="sxs-lookup"><span data-stu-id="138ca-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="138ca-157">動態服務探索。</span><span class="sxs-lookup"><span data-stu-id="138ca-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="138ca-158">負載平衡。</span><span class="sxs-lookup"><span data-stu-id="138ca-158">Load balancing.</span></span>
- <span data-ttu-id="138ca-159">TLS 終止。</span><span class="sxs-lookup"><span data-stu-id="138ca-159">TLS termination.</span></span>
- <span data-ttu-id="138ca-160">HTTP 和 gRPC proxy。</span><span class="sxs-lookup"><span data-stu-id="138ca-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="138ca-161">斷路器復原功能。</span><span class="sxs-lookup"><span data-stu-id="138ca-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="138ca-162">健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="138ca-162">Health checks.</span></span>
- <span data-ttu-id="138ca-163">[使用未](https://martinfowler.com/bliki/CanaryRelease.html)通過部署的輪流更新。</span><span class="sxs-lookup"><span data-stu-id="138ca-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="138ca-164">如先前所討論，Envoy 會以側車的形式部署至叢集中的每個微服務。</span><span class="sxs-lookup"><span data-stu-id="138ca-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="138ca-165">與 Azure Kubernetes Services 整合</span><span class="sxs-lookup"><span data-stu-id="138ca-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="138ca-166">Azure 雲端採用 Istio，並在 Azure Kubernetes Services 中提供對其的直接支援。</span><span class="sxs-lookup"><span data-stu-id="138ca-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="138ca-167">下列連結可協助您開始使用：</span><span class="sxs-lookup"><span data-stu-id="138ca-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="138ca-168">在 AKS 中安裝 Istio</span><span class="sxs-lookup"><span data-stu-id="138ca-168">Installing Istio in AKS</span></span>](https://docs.microsoft.com/azure/aks/istio-install)
- [<span data-ttu-id="138ca-169">使用 AKS 和 Istio</span><span class="sxs-lookup"><span data-stu-id="138ca-169">Using AKS and Istio</span></span>](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="138ca-170">參考</span><span class="sxs-lookup"><span data-stu-id="138ca-170">References</span></span>

- [<span data-ttu-id="138ca-171">Polly</span><span class="sxs-lookup"><span data-stu-id="138ca-171">Polly</span></span>](http://www.thepollyproject.org/)

- [<span data-ttu-id="138ca-172">重試模式</span><span class="sxs-lookup"><span data-stu-id="138ca-172">Retry pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [<span data-ttu-id="138ca-173">斷路器模式</span><span class="sxs-lookup"><span data-stu-id="138ca-173">Circuit Breaker pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="138ca-174">Azure 中的復原技術白皮書</span><span class="sxs-lookup"><span data-stu-id="138ca-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="138ca-175">網路延遲</span><span class="sxs-lookup"><span data-stu-id="138ca-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="138ca-176">備援性</span><span class="sxs-lookup"><span data-stu-id="138ca-176">Redundancy</span></span>](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="138ca-177">異地複寫</span><span class="sxs-lookup"><span data-stu-id="138ca-177">geo-replication</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="138ca-178">Azure 流量管理員</span><span class="sxs-lookup"><span data-stu-id="138ca-178">Azure Traffic Manager</span></span>](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="138ca-179">自動調整指引</span><span class="sxs-lookup"><span data-stu-id="138ca-179">Autoscaling guidance</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="138ca-180">Istio</span><span class="sxs-lookup"><span data-stu-id="138ca-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="138ca-181">Envoy proxy</span><span class="sxs-lookup"><span data-stu-id="138ca-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="138ca-182">[上一個](infrastructure-resiliency-azure.md) 
>[下一步](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="138ca-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>
