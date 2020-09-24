---
title: 具有復原性的通訊
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |復原通訊
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 18b26223634efc5c05f680d0cbb7c8cbc2490a59
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166036"
---
# <a name="resilient-communications"></a><span data-ttu-id="4f10b-103">復原通訊</span><span class="sxs-lookup"><span data-stu-id="4f10b-103">Resilient communications</span></span>

<span data-ttu-id="4f10b-104">在本書中，我們採用了以微服務為基礎的架構方法。</span><span class="sxs-lookup"><span data-stu-id="4f10b-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="4f10b-105">雖然這類架構提供重要的優點，但卻帶來許多挑戰：</span><span class="sxs-lookup"><span data-stu-id="4f10b-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="4f10b-106">*跨進程網路通訊。*</span><span class="sxs-lookup"><span data-stu-id="4f10b-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="4f10b-107">每個微服務都會透過網路通訊協定進行通訊，而這些網路通訊協定會引進網路擁塞、延遲和暫時性錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f10b-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="4f10b-108">*服務探索。*</span><span class="sxs-lookup"><span data-stu-id="4f10b-108">*Service discovery.*</span></span> <span data-ttu-id="4f10b-109">在具有自己的 IP 位址和埠的電腦叢集上執行時，微服務如何探索和彼此通訊？</span><span class="sxs-lookup"><span data-stu-id="4f10b-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="4f10b-110">*彈性。*</span><span class="sxs-lookup"><span data-stu-id="4f10b-110">*Resiliency.*</span></span> <span data-ttu-id="4f10b-111">您要如何管理短期失敗並讓系統穩定？</span><span class="sxs-lookup"><span data-stu-id="4f10b-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="4f10b-112">*負載平衡。*</span><span class="sxs-lookup"><span data-stu-id="4f10b-112">*Load balancing.*</span></span> <span data-ttu-id="4f10b-113">輸入流量如何分散到微服務的多個實例？</span><span class="sxs-lookup"><span data-stu-id="4f10b-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="4f10b-114">*安全性。*</span><span class="sxs-lookup"><span data-stu-id="4f10b-114">*Security.*</span></span> <span data-ttu-id="4f10b-115">如何強制執行傳輸層級加密和憑證管理等安全性問題？</span><span class="sxs-lookup"><span data-stu-id="4f10b-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="4f10b-116">*分散式監視。*</span><span class="sxs-lookup"><span data-stu-id="4f10b-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="4f10b-117">-您如何在多個取用微服務之間相互關聯和捕捉單一要求的可追蹤性和監視？</span><span class="sxs-lookup"><span data-stu-id="4f10b-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="4f10b-118">您可以使用不同的程式庫和架構來解決這些問題，但其實作可能很耗費資源、複雜且耗時。</span><span class="sxs-lookup"><span data-stu-id="4f10b-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="4f10b-119">您最後也會有與商務邏輯結合的基礎結構考慮。</span><span class="sxs-lookup"><span data-stu-id="4f10b-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="4f10b-120">服務網格</span><span class="sxs-lookup"><span data-stu-id="4f10b-120">Service mesh</span></span>

<span data-ttu-id="4f10b-121">更好的方法是具有 *服務網格*的不斷演進技術。</span><span class="sxs-lookup"><span data-stu-id="4f10b-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="4f10b-122">[服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是可設定的基礎結構層，具有可處理服務通訊的內建功能，以及上述的其他挑戰。</span><span class="sxs-lookup"><span data-stu-id="4f10b-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="4f10b-123">它會將這些考慮移至服務 proxy，以分離這些問題。</span><span class="sxs-lookup"><span data-stu-id="4f10b-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="4f10b-124">Proxy 會部署到個別的進程 (稱為 [側車](/azure/architecture/patterns/sidecar)) ，以提供與商務程式碼的隔離。</span><span class="sxs-lookup"><span data-stu-id="4f10b-124">The proxy is deployed into a separate process (called a [sidecar](/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="4f10b-125">不過，側車會連結至服務-它會使用它建立並共用其生命週期。</span><span class="sxs-lookup"><span data-stu-id="4f10b-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="4f10b-126">圖6-7 顯示此案例。</span><span class="sxs-lookup"><span data-stu-id="4f10b-126">Figure 6-7 shows this scenario.</span></span>

![具有側面汽車的服務網格](./media/service-mesh-with-side-car.png)

<span data-ttu-id="4f10b-128">**圖 6-7**。</span><span class="sxs-lookup"><span data-stu-id="4f10b-128">**Figure 6-7**.</span></span> <span data-ttu-id="4f10b-129">具有側面汽車的服務網格</span><span class="sxs-lookup"><span data-stu-id="4f10b-129">Service mesh with a side car</span></span>

<span data-ttu-id="4f10b-130">在上圖中，請注意 proxy 如何攔截及管理微服務與叢集之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="4f10b-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="4f10b-131">服務網格會以邏輯方式分割成兩個不同的元件：一個 [資料平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) 和一個 [控制平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)。</span><span class="sxs-lookup"><span data-stu-id="4f10b-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="4f10b-132">圖6-8 顯示這些元件及其責任。</span><span class="sxs-lookup"><span data-stu-id="4f10b-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![服務網格控制項和資料平面](./media/istio-control-and-data-plane.png)

<span data-ttu-id="4f10b-134">**圖6-8。**</span><span class="sxs-lookup"><span data-stu-id="4f10b-134">**Figure 6-8.**</span></span> <span data-ttu-id="4f10b-135">服務網格控制項和資料平面</span><span class="sxs-lookup"><span data-stu-id="4f10b-135">Service mesh control and data plane</span></span>

<span data-ttu-id="4f10b-136">一旦設定之後，服務網格會具有高功能。</span><span class="sxs-lookup"><span data-stu-id="4f10b-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="4f10b-137">它可以從服務探索端點取出對應的實例集區。</span><span class="sxs-lookup"><span data-stu-id="4f10b-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="4f10b-138">然後，網格可以將要求傳送至特定的實例，記錄結果的延遲和回應類型。</span><span class="sxs-lookup"><span data-stu-id="4f10b-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="4f10b-139">網格可以根據許多因素（包括觀察到最近的要求所觀察到的延遲），選擇最可能傳回快速回應的實例。</span><span class="sxs-lookup"><span data-stu-id="4f10b-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="4f10b-140">如果實例沒有回應或失敗，網格將會在另一個實例上重試要求。</span><span class="sxs-lookup"><span data-stu-id="4f10b-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="4f10b-141">如果傳回錯誤，網狀架構將會從負載平衡集區中收回實例，並在修復之後重新聲明該實例。</span><span class="sxs-lookup"><span data-stu-id="4f10b-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="4f10b-142">如果要求超時，網格會失敗，然後重試要求。</span><span class="sxs-lookup"><span data-stu-id="4f10b-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="4f10b-143">網格會捕捉併發出計量，並將其發佈至集中式計量系統。</span><span class="sxs-lookup"><span data-stu-id="4f10b-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="4f10b-144">Istio 和 Envoy</span><span class="sxs-lookup"><span data-stu-id="4f10b-144">Istio and Envoy</span></span>

<span data-ttu-id="4f10b-145">雖然有一些服務網格選項目前存在，但是在撰寫本文時， [Istio](https://istio.io/docs/concepts/what-is-istio/) 是最受歡迎的。</span><span class="sxs-lookup"><span data-stu-id="4f10b-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="4f10b-146">Istio 是 IBM、Google 和 Lyft 的聯合風險。</span><span class="sxs-lookup"><span data-stu-id="4f10b-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="4f10b-147">它是開放原始碼的供應專案，可整合至新的或現有的分散式應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f10b-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="4f10b-148">此技術提供一致且完整的解決方案，可保護、連線及監視微服務。</span><span class="sxs-lookup"><span data-stu-id="4f10b-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="4f10b-149">其功能包括：</span><span class="sxs-lookup"><span data-stu-id="4f10b-149">Its features include:</span></span>

- <span data-ttu-id="4f10b-150">使用強式身分識別型驗證和授權，在叢集中保護服務對服務的通訊。</span><span class="sxs-lookup"><span data-stu-id="4f10b-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="4f10b-151">適用于 HTTP、 [gRPC](https://grpc.io/)、WEBSOCKET 和 TCP 流量的自動負載平衡。</span><span class="sxs-lookup"><span data-stu-id="4f10b-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="4f10b-152">使用豐富的路由規則、重試、容錯移轉和錯誤插入，更精細地控制流量行為。</span><span class="sxs-lookup"><span data-stu-id="4f10b-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="4f10b-153">可插入的原則層和設定 API，支援存取控制、速率限制和配額。</span><span class="sxs-lookup"><span data-stu-id="4f10b-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="4f10b-154">叢集中所有流量的自動計量、記錄和追蹤，包括叢集輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="4f10b-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="4f10b-155">Istio 執行的主要元件是有權 [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)的 proxy 服務。</span><span class="sxs-lookup"><span data-stu-id="4f10b-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="4f10b-156">它會與每個服務一起執行，並為下列功能提供平臺中立的基礎：</span><span class="sxs-lookup"><span data-stu-id="4f10b-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="4f10b-157">動態服務探索。</span><span class="sxs-lookup"><span data-stu-id="4f10b-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="4f10b-158">負載平衡。</span><span class="sxs-lookup"><span data-stu-id="4f10b-158">Load balancing.</span></span>
- <span data-ttu-id="4f10b-159">TLS 終止。</span><span class="sxs-lookup"><span data-stu-id="4f10b-159">TLS termination.</span></span>
- <span data-ttu-id="4f10b-160">HTTP 和 gRPC proxy。</span><span class="sxs-lookup"><span data-stu-id="4f10b-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="4f10b-161">斷路器復原。</span><span class="sxs-lookup"><span data-stu-id="4f10b-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="4f10b-162">健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="4f10b-162">Health checks.</span></span>
- <span data-ttu-id="4f10b-163">[使用未](https://martinfowler.com/bliki/CanaryRelease.html)部署的部署來輪流更新。</span><span class="sxs-lookup"><span data-stu-id="4f10b-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="4f10b-164">如先前所討論，Envoy 會以側車的形式部署至叢集中的每個微服務。</span><span class="sxs-lookup"><span data-stu-id="4f10b-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="4f10b-165">與 Azure Kubernetes Services 整合</span><span class="sxs-lookup"><span data-stu-id="4f10b-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="4f10b-166">Azure 雲端採用 Istio，並在 Azure Kubernetes Services 中為其提供直接支援。</span><span class="sxs-lookup"><span data-stu-id="4f10b-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="4f10b-167">下列連結可協助您開始使用：</span><span class="sxs-lookup"><span data-stu-id="4f10b-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="4f10b-168">在 AKS 中安裝 Istio</span><span class="sxs-lookup"><span data-stu-id="4f10b-168">Installing Istio in AKS</span></span>](/azure/aks/istio-install)
- [<span data-ttu-id="4f10b-169">使用 AKS 和 Istio</span><span class="sxs-lookup"><span data-stu-id="4f10b-169">Using AKS and Istio</span></span>](/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="4f10b-170">參考資料</span><span class="sxs-lookup"><span data-stu-id="4f10b-170">References</span></span>

- [<span data-ttu-id="4f10b-171">Polly</span><span class="sxs-lookup"><span data-stu-id="4f10b-171">Polly</span></span>](http://www.thepollyproject.org/)

- [<span data-ttu-id="4f10b-172">重試模式</span><span class="sxs-lookup"><span data-stu-id="4f10b-172">Retry pattern</span></span>](/azure/architecture/patterns/retry)

- [<span data-ttu-id="4f10b-173">斷路器模式</span><span class="sxs-lookup"><span data-stu-id="4f10b-173">Circuit Breaker pattern</span></span>](/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="4f10b-174">Azure 中的復原技術白皮書</span><span class="sxs-lookup"><span data-stu-id="4f10b-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="4f10b-175">網路延遲</span><span class="sxs-lookup"><span data-stu-id="4f10b-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="4f10b-176">備援性</span><span class="sxs-lookup"><span data-stu-id="4f10b-176">Redundancy</span></span>](/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="4f10b-177">異地複寫</span><span class="sxs-lookup"><span data-stu-id="4f10b-177">geo-replication</span></span>](/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="4f10b-178">Azure 流量管理員</span><span class="sxs-lookup"><span data-stu-id="4f10b-178">Azure Traffic Manager</span></span>](/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="4f10b-179">自動調整指引</span><span class="sxs-lookup"><span data-stu-id="4f10b-179">Autoscaling guidance</span></span>](/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="4f10b-180">Istio</span><span class="sxs-lookup"><span data-stu-id="4f10b-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="4f10b-181">Envoy proxy</span><span class="sxs-lookup"><span data-stu-id="4f10b-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="4f10b-182">[上一個](infrastructure-resiliency-azure.md) 
>[下一步](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="4f10b-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>
