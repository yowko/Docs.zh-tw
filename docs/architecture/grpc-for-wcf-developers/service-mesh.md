---
title: 服務網格-適用于 WCF 開發人員的 gRPC
description: 使用服務網格來路由傳送要求，並將其與 Kubernetes 叢集中的 gRPC 服務進行平衡。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7fc80b95937dab9153b72aa6bc8da90f6453779f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184089"
---
# <a name="service-meshes"></a><span data-ttu-id="48578-103">服務網格</span><span class="sxs-lookup"><span data-stu-id="48578-103">Service meshes</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="48578-104">「服務網格」是一種基礎結構元件，可控制網路內的路由服務要求。</span><span class="sxs-lookup"><span data-stu-id="48578-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="48578-105">服務網格可以處理 Kubernetes 叢集內的各種網路層級問題，包括：</span><span class="sxs-lookup"><span data-stu-id="48578-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="48578-106">服務探索</span><span class="sxs-lookup"><span data-stu-id="48578-106">Service discovery</span></span>
- <span data-ttu-id="48578-107">負載平衡</span><span class="sxs-lookup"><span data-stu-id="48578-107">Load balancing</span></span>
- <span data-ttu-id="48578-108">容錯</span><span class="sxs-lookup"><span data-stu-id="48578-108">Fault tolerance</span></span>
- <span data-ttu-id="48578-109">加密</span><span class="sxs-lookup"><span data-stu-id="48578-109">Encryption</span></span>
- <span data-ttu-id="48578-110">監視</span><span class="sxs-lookup"><span data-stu-id="48578-110">Monitoring</span></span>

<span data-ttu-id="48578-111">Kubernetes 服務網格的工作是將額外的容器（稱為*側車 proxy*）新增至網格中包含的每個 pod。</span><span class="sxs-lookup"><span data-stu-id="48578-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="48578-112">Proxy 會接管處理所有的輸入和輸出網路要求，讓網路的設定和管理與應用程式容器保持分開，而且在許多情況下，不需要對應用程式程式碼進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="48578-112">The proxy takes over handling all inbound and outbound network requests, allowing configuration and management of networking matters to be kept separate from the application containers and, in many cases, without requiring any changes to the application code.</span></span>

<span data-ttu-id="48578-113">請使用[上一章的範例](kubernetes.md#testing-the-application)，其中 web 應用程式的 gRPC 要求全都路由傳送至 gRPC 服務的單一實例。</span><span class="sxs-lookup"><span data-stu-id="48578-113">Take the [previous chapter's example](kubernetes.md#testing-the-application), where the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="48578-114">之所以會發生這種情況，是因為服務的主機名稱解析為 ip 位址，而該 ip 位址會在`HttpClientHandler`實例的存留期內快取。</span><span class="sxs-lookup"><span data-stu-id="48578-114">This happens because the service's hostname is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="48578-115">您可以藉由手動處理 DNS 查閱或建立多個用戶端來解決此情況，但這會大幅增加應用程式的程式碼，而不需要新增任何商業或客戶價值。</span><span class="sxs-lookup"><span data-stu-id="48578-115">It might be possible to work around this by handling DNS lookups manually or creating multiple clients, but this would complicate the application code considerably without adding any business or customer value.</span></span>

<span data-ttu-id="48578-116">使用服務網格時，會將來自應用程式容器的要求傳送至側車 proxy，以智慧方式在其他服務的所有實例之間散發。</span><span class="sxs-lookup"><span data-stu-id="48578-116">Using a service mesh, the requests from the application container are sent to the sidecar proxy, which can distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="48578-117">網格也可以：</span><span class="sxs-lookup"><span data-stu-id="48578-117">The mesh can also:</span></span>

- <span data-ttu-id="48578-118">無縫回應服務的個別實例失敗。</span><span class="sxs-lookup"><span data-stu-id="48578-118">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="48578-119">處理失敗呼叫或超時的重試語義</span><span class="sxs-lookup"><span data-stu-id="48578-119">Handle retry semantics for failed calls or timeouts</span></span>
- <span data-ttu-id="48578-120">將失敗的要求重新路由至其他實例，完全不需要返回用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="48578-120">Reroute failed requests to an alternate instance without returning to the client application at all.</span></span>

<span data-ttu-id="48578-121">下列螢幕擷取畫面顯示使用 Linkerd 服務網格執行的 StockWeb 應用程式，不會變更應用程式程式碼，甚至是使用中的 Docker 映射。</span><span class="sxs-lookup"><span data-stu-id="48578-121">The following screenshot shows the StockWeb application running with the Linkerd service mesh, with no changes to the application code, or even the Docker image being used.</span></span> <span data-ttu-id="48578-122">唯一需要的變更是在`stockdata`和`stockweb`服務的 YAML 檔中，新增對部署的注釋。</span><span class="sxs-lookup"><span data-stu-id="48578-122">The only change required was the addition of an annotation to the Deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![使用服務網格的 StockWeb](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="48578-124">您可以從 [伺服器] 資料行看到，來自 StockWeb 應用程式的要求已路由傳送至 StockData 服務的兩個複本，儘管是源自`HttpClient`應用程式代碼中的單一實例。</span><span class="sxs-lookup"><span data-stu-id="48578-124">You can see from the Server column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="48578-125">事實上，如果您檢查程式碼，您會看到 StockData 服務的所有100要求都是使用相同`HttpClient`的實例同時進行，但是在服務網格中，這些要求將會在許多服務實例可供使用的情況下平衡。</span><span class="sxs-lookup"><span data-stu-id="48578-125">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously using the same `HttpClient` instance, yet with the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="48578-126">服務網格僅適用于叢集中的流量。</span><span class="sxs-lookup"><span data-stu-id="48578-126">Service meshes only apply to traffic within a cluster.</span></span> <span data-ttu-id="48578-127">若是外部用戶端，請參閱[下一章的負載平衡](load-balancing.md)。</span><span class="sxs-lookup"><span data-stu-id="48578-127">For external clients, see [the next chapter, Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="48578-128">服務網格選項</span><span class="sxs-lookup"><span data-stu-id="48578-128">Service mesh options</span></span>

<span data-ttu-id="48578-129">目前有三個一般用途的服務網格實現可與 Kubernetes 搭配使用：Istio、Linkerd 和 Consul Connect。</span><span class="sxs-lookup"><span data-stu-id="48578-129">There are three general-purpose service mesh implementations currently available for use with Kubernetes: Istio, Linkerd, and Consul Connect.</span></span> <span data-ttu-id="48578-130">這三個都提供要求路由/代理、流量加密、復原、主機對主機驗證，以及流量控制。</span><span class="sxs-lookup"><span data-stu-id="48578-130">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="48578-131">選擇服務網格取決於多個因素：</span><span class="sxs-lookup"><span data-stu-id="48578-131">Choosing a service mesh depends multiple factors:</span></span> 

- <span data-ttu-id="48578-132">組織對於成本、合規性、付費支援方案等方面的特定需求。</span><span class="sxs-lookup"><span data-stu-id="48578-132">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span> 
- <span data-ttu-id="48578-133">叢集的本質、其大小、已部署的服務數量，以及叢集網路內的流量量。</span><span class="sxs-lookup"><span data-stu-id="48578-133">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="48578-134">輕鬆部署和管理網格，並將其與服務搭配使用。</span><span class="sxs-lookup"><span data-stu-id="48578-134">Ease of deploying and managing the mesh and using it with services.</span></span>

<span data-ttu-id="48578-135">每個服務網格的詳細資訊都可從其各自的網站取得。</span><span class="sxs-lookup"><span data-stu-id="48578-135">More information on each service mesh is available from their respective websites.</span></span>

- [<span data-ttu-id="48578-136">**Istio** -istio.io</span><span class="sxs-lookup"><span data-stu-id="48578-136">**Istio** - istio.io</span></span>](https://istio.io)
- [<span data-ttu-id="48578-137">**Linkerd** -linkerd.io</span><span class="sxs-lookup"><span data-stu-id="48578-137">**Linkerd** - linkerd.io</span></span>](https://linkerd.io)
- [<span data-ttu-id="48578-138">**Consul** -consul.io/mesh.html</span><span class="sxs-lookup"><span data-stu-id="48578-138">**Consul** - consul.io/mesh.html</span></span>](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="48578-139">範例：將 Linkerd 新增至部署</span><span class="sxs-lookup"><span data-stu-id="48578-139">Example: add Linkerd to a deployment</span></span>

<span data-ttu-id="48578-140">在此範例中，您將瞭解如何搭配[上一節](kubernetes.md)的*StockKube*應用程式使用 Linkerd 服務網格。</span><span class="sxs-lookup"><span data-stu-id="48578-140">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="48578-141">若要遵循此範例，您必須[安裝 LINKERD CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli)。</span><span class="sxs-lookup"><span data-stu-id="48578-141">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="48578-142">您可以從 GitHub 版本區段下載 Windows 二進位檔;請務必使用最新的**穩定**版本，而不是其中一個 edge 版本。</span><span class="sxs-lookup"><span data-stu-id="48578-142">Windows binaries can be downloaded from the GitHub releases section; make sure to use the most recent **stable** release and not one of the edge releases.</span></span>

<span data-ttu-id="48578-143">安裝 Linkerd CLI 之後，請遵循 Linkerd 網站上的 [*消費者入門*指示]，在您的 Kubernetes 叢集上安裝 Linkerd 元件。</span><span class="sxs-lookup"><span data-stu-id="48578-143">With the Linkerd CLI installed, follow the [*Getting Started* instructions on the Linkerd web site] to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="48578-144">指示是直接的，而安裝只需要幾分鐘的時間，就能在本機 Kubernetes 實例上執行。</span><span class="sxs-lookup"><span data-stu-id="48578-144">The instructions are straight-forward and installation should only take a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="48578-145">將 Linkerd 新增至 Kubernetes 部署</span><span class="sxs-lookup"><span data-stu-id="48578-145">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="48578-146">Linkerd CLI 會提供一個`inject`命令，將必要的區段和屬性新增至 Kubernetes 檔案。</span><span class="sxs-lookup"><span data-stu-id="48578-146">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="48578-147">您可以執行命令，並將輸出寫入新的檔案。</span><span class="sxs-lookup"><span data-stu-id="48578-147">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="48578-148">您可以檢查新的檔案，以查看已進行的變更。</span><span class="sxs-lookup"><span data-stu-id="48578-148">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="48578-149">針對部署物件，會新增中繼資料注釋，告訴 Linkerd 在建立時將側車 proxy 容器插入 Pod 中。</span><span class="sxs-lookup"><span data-stu-id="48578-149">For Deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the Pod when it's created.</span></span>

<span data-ttu-id="48578-150">也可以直接將`linkerd inject`命令的輸出傳送至。 `kubectl`</span><span class="sxs-lookup"><span data-stu-id="48578-150">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="48578-151">下列命令可在 PowerShell 或任何 Linux shell 中使用。</span><span class="sxs-lookup"><span data-stu-id="48578-151">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="48578-152">在 Linkerd 儀表板中檢查服務</span><span class="sxs-lookup"><span data-stu-id="48578-152">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="48578-153">使用`linkerd` CLI 啟動 Linkerd 儀表板。</span><span class="sxs-lookup"><span data-stu-id="48578-153">Launch the Linkerd dashboard using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="48578-154">儀表板會提供連接到網格的所有服務的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="48578-154">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![顯示 StockKube 應用程式的 Linkerd 儀表板](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="48578-156">如果您增加 StockData gRPC 服務的複本數目（如下列範例所示），並在瀏覽器中重新整理 StockWeb 頁面，您應該會在 [伺服器] 資料行中看到識別碼的混合，表示所有可用的實例都已提供要求.</span><span class="sxs-lookup"><span data-stu-id="48578-156">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the Server column, indicating that requests are being served by all the available instances.</span></span>

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
><span data-ttu-id="48578-157">[上一頁](kubernetes.md)
>[下一頁](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="48578-157">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
