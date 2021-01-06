---
title: 服務網格-適用于 WCF 開發人員的 gRPC
description: 使用服務網格來路由傳送要求，並對 Kubernetes 叢集中的 gRPC 服務進行平衡。
ms.date: 12/15/2020
ms.openlocfilehash: a1c72a4facf1c133af912bbee242328653a051b6
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938126"
---
# <a name="service-meshes"></a><span data-ttu-id="1664d-103">服務網格</span><span class="sxs-lookup"><span data-stu-id="1664d-103">Service meshes</span></span>

<span data-ttu-id="1664d-104">服務網格是一種基礎結構元件，可控制網路內的路由服務要求。</span><span class="sxs-lookup"><span data-stu-id="1664d-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="1664d-105">服務網格可以處理 Kubernetes 叢集中的各種網路層級問題，包括：</span><span class="sxs-lookup"><span data-stu-id="1664d-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="1664d-106">服務探索</span><span class="sxs-lookup"><span data-stu-id="1664d-106">Service discovery</span></span>
- <span data-ttu-id="1664d-107">負載平衡</span><span class="sxs-lookup"><span data-stu-id="1664d-107">Load balancing</span></span>
- <span data-ttu-id="1664d-108">容錯</span><span class="sxs-lookup"><span data-stu-id="1664d-108">Fault tolerance</span></span>
- <span data-ttu-id="1664d-109">加密</span><span class="sxs-lookup"><span data-stu-id="1664d-109">Encryption</span></span>
- <span data-ttu-id="1664d-110">監視</span><span class="sxs-lookup"><span data-stu-id="1664d-110">Monitoring</span></span>

<span data-ttu-id="1664d-111">Kubernetes 服務網格的運作方式是將額外的容器（稱為 *側車 proxy*）新增至網格中包含的每個 pod。</span><span class="sxs-lookup"><span data-stu-id="1664d-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="1664d-112">Proxy 會處理所有的輸入和輸出網路要求。</span><span class="sxs-lookup"><span data-stu-id="1664d-112">The proxy takes over handling all inbound and outbound network requests.</span></span> <span data-ttu-id="1664d-113">然後，您可以讓網路的設定和管理工作與應用程式容器分開。</span><span class="sxs-lookup"><span data-stu-id="1664d-113">You can then keep the configuration and management of networking matters separate from the application containers.</span></span> <span data-ttu-id="1664d-114">在許多情況下，此分隔不需要對應用程式程式碼進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="1664d-114">In many cases, this separation doesn't require any changes to the application code.</span></span>

<span data-ttu-id="1664d-115">在 [上一章的範例](kubernetes.md#test-the-application)中，web 應用程式的 gRPC 要求都會路由傳送至 gRPC 服務的單一實例。</span><span class="sxs-lookup"><span data-stu-id="1664d-115">In the [previous chapter's example](kubernetes.md#test-the-application), the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="1664d-116">發生這種情況是因為服務的主機名稱已解析為 IP 位址，且該 IP 位址會在實例的存留期內快取 `HttpClientHandler` 。</span><span class="sxs-lookup"><span data-stu-id="1664d-116">This happens because the service's host name is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="1664d-117">您可以手動處理 DNS 查閱或建立多個用戶端，以解決這種行為。</span><span class="sxs-lookup"><span data-stu-id="1664d-117">It might be possible to work around this behavior by handling DNS lookups manually or creating multiple clients.</span></span> <span data-ttu-id="1664d-118">但此因應措施會使應用程式程式碼變得複雜，而不會增加任何商務或客戶價值。</span><span class="sxs-lookup"><span data-stu-id="1664d-118">But this workaround would complicate the application code without adding any business or customer value.</span></span>

<span data-ttu-id="1664d-119">當您使用服務網格時，來自應用程式容器的要求會傳送至側車 proxy。</span><span class="sxs-lookup"><span data-stu-id="1664d-119">When you use a service mesh, the requests from the application container are sent to the sidecar proxy.</span></span> <span data-ttu-id="1664d-120">然後，側車 proxy 可以在其他服務的所有實例上以智慧方式散發它們。</span><span class="sxs-lookup"><span data-stu-id="1664d-120">The sidecar proxy can then distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="1664d-121">網格也可以：</span><span class="sxs-lookup"><span data-stu-id="1664d-121">The mesh can also:</span></span>

- <span data-ttu-id="1664d-122">順暢地回應服務的個別實例失敗。</span><span class="sxs-lookup"><span data-stu-id="1664d-122">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="1664d-123">處理失敗呼叫或超時的重試語義。</span><span class="sxs-lookup"><span data-stu-id="1664d-123">Handle retry semantics for failed calls or timeouts.</span></span>
- <span data-ttu-id="1664d-124">將失敗的要求重新路由傳送至替代的實例，而不傳回用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="1664d-124">Reroute failed requests to an alternate instance without returning to the client application.</span></span>

<span data-ttu-id="1664d-125">下列螢幕擷取畫面顯示以 Linkerd 服務網格執行的 StockWeb 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1664d-125">The following screenshot shows the StockWeb application running with the Linkerd service mesh.</span></span> <span data-ttu-id="1664d-126">應用程式程式碼沒有任何變更，也沒有使用 Docker 映射。</span><span class="sxs-lookup"><span data-stu-id="1664d-126">There are no changes to the application code, and the Docker image isn't being used.</span></span> <span data-ttu-id="1664d-127">唯一需要的變更是在和服務的 YAML 檔中，將批註新增至部署 `stockdata` `stockweb` 。</span><span class="sxs-lookup"><span data-stu-id="1664d-127">The only change required was the addition of an annotation to the deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb 與服務網格](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="1664d-129">您可以從 [ **伺服器** ] 資料行看到 StockWeb 應用程式的要求已路由傳送至 StockData 服務的這兩個複本，儘管是源自 `HttpClient` 應用程式程式碼中的單一實例。</span><span class="sxs-lookup"><span data-stu-id="1664d-129">You can see from the **Server** column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="1664d-130">事實上，如果您檢查程式碼，就會看到 StockData 服務的所有100要求都是使用相同的實例同時進行 `HttpClient` 。</span><span class="sxs-lookup"><span data-stu-id="1664d-130">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously by using the same `HttpClient` instance.</span></span> <span data-ttu-id="1664d-131">使用服務網格時，這些要求將會平衡，不過有許多可用的服務實例。</span><span class="sxs-lookup"><span data-stu-id="1664d-131">With the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="1664d-132">服務網格只適用于叢集中的流量。</span><span class="sxs-lookup"><span data-stu-id="1664d-132">Service meshes apply only to traffic within a cluster.</span></span> <span data-ttu-id="1664d-133">若為外部用戶端，請參閱下一章的 [負載平衡](load-balancing.md)。</span><span class="sxs-lookup"><span data-stu-id="1664d-133">For external clients, see the next chapter, [Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="1664d-134">服務網格選項</span><span class="sxs-lookup"><span data-stu-id="1664d-134">Service mesh options</span></span>

<span data-ttu-id="1664d-135">目前有三種一般用途的服務網狀架構可與 Kubernetes 搭配使用： [Istio](https://istio.io)、 [Linkerd](https://linkerd.io)和 [Consul Connect](https://consul.io/mesh.html)。</span><span class="sxs-lookup"><span data-stu-id="1664d-135">Three general-purpose service mesh implementations are currently available for use with Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io), and [Consul Connect](https://consul.io/mesh.html).</span></span> <span data-ttu-id="1664d-136">這三個都提供要求路由/proxy 處理、流量加密、復原、主機對主機驗證，以及流量控制。</span><span class="sxs-lookup"><span data-stu-id="1664d-136">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="1664d-137">選擇服務網格取決於多個因素：</span><span class="sxs-lookup"><span data-stu-id="1664d-137">Choosing a service mesh depends on multiple factors:</span></span>

- <span data-ttu-id="1664d-138">組織對成本、合規性、付費支援方案等方面的特定需求。</span><span class="sxs-lookup"><span data-stu-id="1664d-138">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="1664d-139">叢集的本質、其大小、部署的服務數目，以及叢集網路內的流量量。</span><span class="sxs-lookup"><span data-stu-id="1664d-139">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="1664d-140">輕鬆地部署和管理網格，並將其與服務搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1664d-140">Ease of deploying and managing the mesh and using it with services.</span></span>

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="1664d-141">範例：將 Linkerd 新增至部署</span><span class="sxs-lookup"><span data-stu-id="1664d-141">Example: Add Linkerd to a deployment</span></span>

<span data-ttu-id="1664d-142">在此範例中，您將瞭解如何使用 Linkerd 服務網格與 [上一節](kubernetes.md)中的 *StockKube* 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1664d-142">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="1664d-143">若要遵循此範例，您必須 [安裝 LINKERD CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli)。</span><span class="sxs-lookup"><span data-stu-id="1664d-143">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="1664d-144">您可以從列出 GitHub 版本的區段下載 Windows 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="1664d-144">You can download Windows binaries from the section that lists GitHub releases.</span></span> <span data-ttu-id="1664d-145">請務必使用最新的 *穩定* 版本，而不是其中一個 edge 版本。</span><span class="sxs-lookup"><span data-stu-id="1664d-145">Be sure to use the most recent *stable* release and not one of the edge releases.</span></span>

<span data-ttu-id="1664d-146">安裝 Linkerd CLI 之後，請遵循 [消費者入門](https://linkerd.io/2/getting-started/index.html) 指示，在您的 Kubernetes 叢集上安裝 Linkerd 元件。</span><span class="sxs-lookup"><span data-stu-id="1664d-146">With the Linkerd CLI installed, follow the [Getting Started](https://linkerd.io/2/getting-started/index.html) instructions to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="1664d-147">這些指示很簡單，而安裝只需要幾分鐘的時間就可以在本機 Kubernetes 實例上執行。</span><span class="sxs-lookup"><span data-stu-id="1664d-147">The instructions are straightforward, and the installation should take only a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="1664d-148">將 Linkerd 新增至 Kubernetes 部署</span><span class="sxs-lookup"><span data-stu-id="1664d-148">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="1664d-149">Linkerd CLI 提供 `inject` 命令，以將必要的區段和屬性新增至 Kubernetes 檔案。</span><span class="sxs-lookup"><span data-stu-id="1664d-149">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="1664d-150">您可以執行命令，並將輸出寫入至新的檔案。</span><span class="sxs-lookup"><span data-stu-id="1664d-150">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="1664d-151">您可以檢查新的檔案，以查看已進行的變更。</span><span class="sxs-lookup"><span data-stu-id="1664d-151">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="1664d-152">針對部署物件，會加入中繼資料注釋，以告知 Linkerd 在建立時將側車 proxy 容器插入至 pod。</span><span class="sxs-lookup"><span data-stu-id="1664d-152">For deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the pod when it's created.</span></span>

<span data-ttu-id="1664d-153">您也可以透過管線將命令的輸出 `linkerd inject` 直接傳送到 `kubectl` 。</span><span class="sxs-lookup"><span data-stu-id="1664d-153">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="1664d-154">下列命令可在 PowerShell 或任何 Linux shell 中運作。</span><span class="sxs-lookup"><span data-stu-id="1664d-154">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="1664d-155">檢查 Linkerd 儀表板中的服務</span><span class="sxs-lookup"><span data-stu-id="1664d-155">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="1664d-156">使用 CLI 開啟 Linkerd 儀表板 `linkerd` 。</span><span class="sxs-lookup"><span data-stu-id="1664d-156">Open the Linkerd dashboard by using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="1664d-157">儀表板會提供與網格連接的所有服務相關的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1664d-157">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![顯示 StockKube 應用程式的 Linkerd 儀表板](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="1664d-159">如果您增加 StockData gRPC 服務的複本數目（如下列範例所示），並重新整理瀏覽器中的 [StockWeb] 頁面，您應該會在 [ **伺服器** ] 資料行中看到混合的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1664d-159">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the **Server** column.</span></span> <span data-ttu-id="1664d-160">這種混合表示所有可用的實例都為要求提供服務。</span><span class="sxs-lookup"><span data-stu-id="1664d-160">This mix indicates that all the available instances are serving requests.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

>[!div class="step-by-step"]
><span data-ttu-id="1664d-161">[上一個](kubernetes.md) 
>[下一步](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="1664d-161">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
