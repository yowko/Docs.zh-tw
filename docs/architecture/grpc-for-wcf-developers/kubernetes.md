---
title: 適用于 WCF 開發人員的 Kubernetes-gRPC
description: 在 Kubernetes 叢集中執行 ASP.NET Core gRPC services。
ms.date: 12/15/2020
ms.openlocfilehash: 0b457d6fa982b5f5b983194d4aedbff0eb782f36
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938051"
---
# <a name="kubernetes"></a><span data-ttu-id="f77c7-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f77c7-103">Kubernetes</span></span>

<span data-ttu-id="f77c7-104">雖然可以在 Docker 主機上手動執行容器，但是針對可靠的生產系統，最好使用容器協調流程引擎來管理叢集中數部伺服器上執行的多個實例。</span><span class="sxs-lookup"><span data-stu-id="f77c7-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's better to use a container orchestration engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="f77c7-105">有各種可用的容器協調流程引擎，包括 Kubernetes、Docker Swarm 和 Apache Mesos。</span><span class="sxs-lookup"><span data-stu-id="f77c7-105">There are various container orchestration engines available, including Kubernetes, Docker Swarm, and Apache Mesos.</span></span> <span data-ttu-id="f77c7-106">但在這些引擎中，Kubernetes 的範圍遠超出最廣泛使用的範圍，因此將會是本章的焦點。</span><span class="sxs-lookup"><span data-stu-id="f77c7-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="f77c7-107">Kubernetes 包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="f77c7-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="f77c7-108">**排程** 會在叢集中的多個節點上執行容器，以確保可用資源的使用量達到平衡，並在發生中斷時讓容器保持執行狀態，以及處理新版本映射或新設定的輪流更新。</span><span class="sxs-lookup"><span data-stu-id="f77c7-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="f77c7-109">**健康情況檢查** 會監視容器，以確保持續的服務。</span><span class="sxs-lookup"><span data-stu-id="f77c7-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="f77c7-110">**DNS & 服務探索** 會處理叢集中服務之間的路由。</span><span class="sxs-lookup"><span data-stu-id="f77c7-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="f77c7-111">輸入會在 **外部公開選取** 的服務，通常會在這些服務的實例之間提供負載平衡。</span><span class="sxs-lookup"><span data-stu-id="f77c7-111">**Ingress** exposes selected services externally and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="f77c7-112">**資源管理** 會將儲存體等外部資源（例如儲存體）附加至容器。</span><span class="sxs-lookup"><span data-stu-id="f77c7-112">**Resource management** attaches external resources like storage to containers.</span></span>

<span data-ttu-id="f77c7-113">本章將詳細說明如何將 ASP.NET Core gRPC 服務和取用服務的網站部署至 Kubernetes 叢集中。</span><span class="sxs-lookup"><span data-stu-id="f77c7-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="f77c7-114">使用的範例應用程式可在 GitHub 上的 [dotnet 架構/grpc-適用于 wcf 的開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) 存放庫中取得。</span><span class="sxs-lookup"><span data-stu-id="f77c7-114">The sample application used is available in the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="f77c7-115">Kubernetes 術語</span><span class="sxs-lookup"><span data-stu-id="f77c7-115">Kubernetes terminology</span></span>

<span data-ttu-id="f77c7-116">Kubernetes 使用 *預期的狀態* 設定：此 API 可用來描述物件（*例如 pod*、*部署* 和 *服務*），而 *控制平面* 會負責在叢集中的所有 *節點* 上執行所需的 *狀態。*</span><span class="sxs-lookup"><span data-stu-id="f77c7-116">Kubernetes uses *desired state configuration*: the API is used to describe objects like *Pods*, *Deployments*, and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="f77c7-117">Kubernetes 叢集具有執行 *KUBERNETES API* 的 *主要* 節點，您可以用程式設計方式或使用 `kubectl` 命令列工具進行通訊。</span><span class="sxs-lookup"><span data-stu-id="f77c7-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which you can communicate with programmatically or by using the `kubectl` command-line tool.</span></span> <span data-ttu-id="f77c7-118">`kubectl` 可以透過命令列引數來建立和管理物件，但它與包含 Kubernetes 物件之宣告資料的 YAML 檔案效果最好。</span><span class="sxs-lookup"><span data-stu-id="f77c7-118">`kubectl` can create and manage objects through command-line arguments, but it works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="f77c7-119">Kubernetes YAML 檔</span><span class="sxs-lookup"><span data-stu-id="f77c7-119">Kubernetes YAML files</span></span>

<span data-ttu-id="f77c7-120">每個 Kubernetes YAML 檔案至少會有三個最上層屬性：</span><span class="sxs-lookup"><span data-stu-id="f77c7-120">Every Kubernetes YAML file will have at least three top-level properties:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="f77c7-121">`apiVersion`屬性可用來指定 (的版本，以及檔案所要) 的 API。</span><span class="sxs-lookup"><span data-stu-id="f77c7-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="f77c7-122">`kind`屬性會指定 YAML 所代表的物件類型。</span><span class="sxs-lookup"><span data-stu-id="f77c7-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="f77c7-123">`metadata`屬性包含物件屬性，例如 `name` 、 `namespace` 和 `labels` 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-123">The `metadata` property contains object properties like `name`, `namespace`, and `labels`.</span></span>

<span data-ttu-id="f77c7-124">大部分的 Kubernetes YAML 檔也會有一個 `spec` 區段，描述建立物件所需的資源和設定。</span><span class="sxs-lookup"><span data-stu-id="f77c7-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="f77c7-125">Pod</span><span class="sxs-lookup"><span data-stu-id="f77c7-125">Pods</span></span>

<span data-ttu-id="f77c7-126">Pod 是 Kubernetes 中的基本執行單位。</span><span class="sxs-lookup"><span data-stu-id="f77c7-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="f77c7-127">他們可以執行多個容器，但也可以用來執行單一容器。</span><span class="sxs-lookup"><span data-stu-id="f77c7-127">They can run multiple containers, but they're also used to run single containers.</span></span> <span data-ttu-id="f77c7-128">Pod 也包含容器所需的任何儲存體資源，以及網路 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f77c7-128">The pod also includes any storage resources required by the containers, and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="f77c7-129">服務</span><span class="sxs-lookup"><span data-stu-id="f77c7-129">Services</span></span>

<span data-ttu-id="f77c7-130">服務是中繼物件，可描述 pod (或 pod 集合) 並提供在叢集中存取它們的方式，例如使用叢集 DNS 服務將服務名稱對應至一組 pod IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f77c7-130">Services are meta-objects that describe Pods (or sets of Pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses by using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="f77c7-131">部署</span><span class="sxs-lookup"><span data-stu-id="f77c7-131">Deployments</span></span>

<span data-ttu-id="f77c7-132">部署是 pod 的 *預期狀態* 物件。</span><span class="sxs-lookup"><span data-stu-id="f77c7-132">Deployments are the *desired state* objects for Pods.</span></span> <span data-ttu-id="f77c7-133">如果您以手動方式建立 pod，它就不會在終止時重新開機。</span><span class="sxs-lookup"><span data-stu-id="f77c7-133">If you create a pod manually, it won't be restarted when it terminates.</span></span> <span data-ttu-id="f77c7-134">部署是用來告訴叢集哪些 pod 以及這些 pod 的複本數目，應該在目前的時間執行。</span><span class="sxs-lookup"><span data-stu-id="f77c7-134">Deployments are used to tell the cluster which Pods, and how many replicas of those Pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="f77c7-135">其他物件</span><span class="sxs-lookup"><span data-stu-id="f77c7-135">Other objects</span></span>

<span data-ttu-id="f77c7-136">Pod、服務和部署只是其中三種最基本的物件類型。</span><span class="sxs-lookup"><span data-stu-id="f77c7-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="f77c7-137">Kubernetes 叢集還管理了許多其他的物件類型。</span><span class="sxs-lookup"><span data-stu-id="f77c7-137">There are dozens of other object types that are managed by Kubernetes clusters.</span></span> <span data-ttu-id="f77c7-138">如需詳細資訊，請參閱 [Kubernetes 概念](https://kubernetes.io/docs/concepts/) 檔。</span><span class="sxs-lookup"><span data-stu-id="f77c7-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="f77c7-139">命名空間</span><span class="sxs-lookup"><span data-stu-id="f77c7-139">Namespaces</span></span>

<span data-ttu-id="f77c7-140">Kubernetes 叢集的設計目的是要擴充至數百個或數千個節點，並執行類似的服務數目。</span><span class="sxs-lookup"><span data-stu-id="f77c7-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes and to run similar numbers of services.</span></span> <span data-ttu-id="f77c7-141">為了避免物件名稱之間的衝突，命名空間是用來將物件群組在一起成為較大應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="f77c7-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="f77c7-142">Kubernetes 本身的服務會在 `default` 命名空間中執行。</span><span class="sxs-lookup"><span data-stu-id="f77c7-142">Kubernetes's own services run in a `default` namespace.</span></span> <span data-ttu-id="f77c7-143">所有使用者物件都應該在自己的命名空間中建立，以避免可能與叢集中的預設物件或其他租使用者發生衝突。</span><span class="sxs-lookup"><span data-stu-id="f77c7-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="f77c7-144">開始使用 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f77c7-144">Get started with Kubernetes</span></span>

<span data-ttu-id="f77c7-145">如果您正在執行適用于 Windows 的 Docker Desktop 或適用于 Mac 的 Docker Desktop，Kubernetes 已可供使用。</span><span class="sxs-lookup"><span data-stu-id="f77c7-145">If you're running Docker Desktop for Windows or Docker Desktop for Mac, Kubernetes is already available.</span></span> <span data-ttu-id="f77c7-146">請在 [**設定**] 視窗的 [ **Kubernetes** ] 區段中啟用它：</span><span class="sxs-lookup"><span data-stu-id="f77c7-146">Just enable it in the **Kubernetes** section of the **Settings** window:</span></span>

![在 Docker Desktop 中啟用 Kubernetes](media/kubernetes/enable-kubernetes-docker-desktop-v2.png)

<span data-ttu-id="f77c7-148">若要在 Linux 上執行本機 Kubernetes 叢集，請考慮使用 [minikube](https://github.com/kubernetes/minikube)或 [MicroK8s](https://microk8s.io/) （如果您的 linux 發行版本支援 [snap](https://snapcraft.io/)）。</span><span class="sxs-lookup"><span data-stu-id="f77c7-148">To run a local Kubernetes cluster on Linux, consider [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="f77c7-149">若要確認您的叢集正在執行且可供存取，請執行 `kubectl version` 下列命令：</span><span class="sxs-lookup"><span data-stu-id="f77c7-149">To confirm that your cluster is running and accessible, run the `kubectl version` command:</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:50:19Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:41:49Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="f77c7-150">在此範例中， `kubectl` CLI 和 Kubernetes 伺服器都是執行版本1.14.6。</span><span class="sxs-lookup"><span data-stu-id="f77c7-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="f77c7-151">的每個版本 `kubectl` 都應該支援舊版和下一版的伺服器，因此 `kubectl` 1.14 應該也適用于伺服器版本1.13 和1.15。</span><span class="sxs-lookup"><span data-stu-id="f77c7-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="f77c7-152">在 Kubernetes 上執行服務</span><span class="sxs-lookup"><span data-stu-id="f77c7-152">Run services on Kubernetes</span></span>

<span data-ttu-id="f77c7-153">範例應用程式有一個 `kube` 目錄，其中包含三個 YAML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f77c7-153">The sample application has a `kube` directory that contains three YAML files.</span></span> <span data-ttu-id="f77c7-154">檔案會宣告 `namespace.yml` 自訂命名空間： `stocks` 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-154">The `namespace.yml` file declares a custom namespace: `stocks`.</span></span> <span data-ttu-id="f77c7-155">此檔案 `stockdata.yml` 會宣告 gRPC 應用程式的部署和服務，而且此檔案 `stockweb.yml` 會宣告使用 gRPC 服務之 ASP.NET CORE 5.0 MVC web 應用程式的部署和服務。</span><span class="sxs-lookup"><span data-stu-id="f77c7-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 5.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="f77c7-156">若要搭配使用檔案 `YAML` `kubectl` ，請執行 `apply -f` 下列命令：</span><span class="sxs-lookup"><span data-stu-id="f77c7-156">To use a `YAML` file with `kubectl`, run the `apply -f` command:</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="f77c7-157">此 `apply` 命令會檢查 YAML 檔的有效性，並顯示從 API 收到的任何錯誤，但不會等到檔案中宣告的所有物件都已建立，因為此步驟可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="f77c7-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created because this step can take some time.</span></span> <span data-ttu-id="f77c7-158">使用 `kubectl get` 命令搭配相關的物件類型，以檢查叢集中的物件建立。</span><span class="sxs-lookup"><span data-stu-id="f77c7-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="f77c7-159">命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="f77c7-159">The namespace declaration</span></span>

<span data-ttu-id="f77c7-160">命名空間宣告很簡單，只需要指派 `name` ：</span><span class="sxs-lookup"><span data-stu-id="f77c7-160">Namespace declaration is simple and requires only assigning a `name`:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="f77c7-161">使用 `kubectl` 以套用檔案 `namespace.yml` ，並確認已成功建立命名空間：</span><span class="sxs-lookup"><span data-stu-id="f77c7-161">Use `kubectl` to apply the `namespace.yml` file and to confirm the namespace is created successfully:</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="f77c7-162">StockData 應用程式</span><span class="sxs-lookup"><span data-stu-id="f77c7-162">The StockData application</span></span>

<span data-ttu-id="f77c7-163">檔案會宣告 `stockdata.yml` 兩個物件：部署和服務。</span><span class="sxs-lookup"><span data-stu-id="f77c7-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="f77c7-164">StockData 部署</span><span class="sxs-lookup"><span data-stu-id="f77c7-164">The StockData Deployment</span></span>

<span data-ttu-id="f77c7-165">YAML 檔的部署部分會提供 `spec` 部署本身的，包括所需的複本數目，以及 `template` 要由部署建立和管理的 Pod 物件的。</span><span class="sxs-lookup"><span data-stu-id="f77c7-165">The Deployment part of the YAML file provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="f77c7-166">請注意，部署物件是由 `apps` API 管理，如中所指定 `apiVersion` ，而不是主要 Kubernetes API。</span><span class="sxs-lookup"><span data-stu-id="f77c7-166">Note that Deployment objects are managed by the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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
  replicas: 1
  template:
    metadata:
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

<span data-ttu-id="f77c7-167">`spec.selector`屬性是用來比對執行中的 pod 與部署。</span><span class="sxs-lookup"><span data-stu-id="f77c7-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="f77c7-168">Pod 的 `metadata.labels` 屬性必須符合屬性， `matchLabels` 否則 API 呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f77c7-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="f77c7-169">`template.spec`區段會宣告要執行的容器。</span><span class="sxs-lookup"><span data-stu-id="f77c7-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="f77c7-170">當您使用本機 Kubernetes 叢集（例如 Docker Desktop 提供的叢集）時，您可以指定在本機建立的映射（只要它們具有版本戳記）。</span><span class="sxs-lookup"><span data-stu-id="f77c7-170">When you're working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f77c7-171">根據預設，Kubernetes 一律會檢查並嘗試提取新的映射。</span><span class="sxs-lookup"><span data-stu-id="f77c7-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="f77c7-172">如果它在任何已知的儲存機制中找不到映射，Pod 建立將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f77c7-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="f77c7-173">若要使用本機映射，請將設定 `imagePullPolicy` 為 `Never` 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="f77c7-174">`ports`屬性會指定應該在 Pod 上發佈的容器埠。</span><span class="sxs-lookup"><span data-stu-id="f77c7-174">The `ports` property specifies which container ports should be published on the Pod.</span></span> <span data-ttu-id="f77c7-175">`stockservice`映射會在標準 HTTP 埠上執行服務，因此會發佈埠80。</span><span class="sxs-lookup"><span data-stu-id="f77c7-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="f77c7-176">`resources`區段會將資源限制套用至在 Pod 中執行的容器。</span><span class="sxs-lookup"><span data-stu-id="f77c7-176">The `resources` section applies resource limits to the container running within the Pod.</span></span> <span data-ttu-id="f77c7-177">這是很好的作法，因為它會防止個別的 Pod 耗用節點上的所有可用 CPU 或記憶體。</span><span class="sxs-lookup"><span data-stu-id="f77c7-177">This is a good practice because it prevents an individual Pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="f77c7-178">ASP.NET Core 5.0 已經過優化和調整，可在資源有限的容器中執行。</span><span class="sxs-lookup"><span data-stu-id="f77c7-178">ASP.NET Core 5.0 has been optimized and tuned to run in resource-limited containers.</span></span> <span data-ttu-id="f77c7-179">`dotnet/core/aspnet`Docker 映射會設定環境變數，以告訴 `dotnet` 執行時間它在容器中。</span><span class="sxs-lookup"><span data-stu-id="f77c7-179">The `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="f77c7-180">StockData 服務</span><span class="sxs-lookup"><span data-stu-id="f77c7-180">The StockData Service</span></span>

<span data-ttu-id="f77c7-181">YAML 檔的服務部分會宣告提供叢集內 pod 存取權的服務。</span><span class="sxs-lookup"><span data-stu-id="f77c7-181">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

<span data-ttu-id="f77c7-182">這項服務 `spec` `selector` 會使用屬性來比對 `Pods` 執行，在此案例中，尋找具有標籤 `run: stockdata` 的 pod。</span><span class="sxs-lookup"><span data-stu-id="f77c7-182">The Service `spec` uses the `selector` property to match running `Pods`, in this case looking for Pods that have a label `run: stockdata`.</span></span> <span data-ttu-id="f77c7-183">在相符 pod 上指定的 `port` 是由命名的服務發行。</span><span class="sxs-lookup"><span data-stu-id="f77c7-183">The specified `port` on matching Pods is published by the named service.</span></span> <span data-ttu-id="f77c7-184">在命名空間中執行的其他 pod `stocks` 可以使用做為位址，存取此服務上的 HTTP `http://stockdata` 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-184">Other Pods running in the `stocks` namespace can access HTTP on this service by using `http://stockdata` as the address.</span></span> <span data-ttu-id="f77c7-185">在其他命名空間中執行的 pod 可以使用 `http://stockdata.stocks` 主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f77c7-185">Pods running in other namespaces can use the `http://stockdata.stocks` host name.</span></span> <span data-ttu-id="f77c7-186">您可以使用 [網路原則](https://kubernetes.io/docs/concepts/services-networking/network-policies/)來控制跨命名空間的服務存取。</span><span class="sxs-lookup"><span data-stu-id="f77c7-186">You can control cross-namespace service access by using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="f77c7-187">部署 StockData 應用程式</span><span class="sxs-lookup"><span data-stu-id="f77c7-187">Deploy the StockData application</span></span>

<span data-ttu-id="f77c7-188">使用 `kubectl` 以套用檔案 `stockdata.yml` ，並確認已建立部署和服務：</span><span class="sxs-lookup"><span data-stu-id="f77c7-188">Use `kubectl` to apply the `stockdata.yml` file and confirm that the Deployment and Service were created:</span></span>

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a><span data-ttu-id="f77c7-189">StockWeb 應用程式</span><span class="sxs-lookup"><span data-stu-id="f77c7-189">The StockWeb application</span></span>

<span data-ttu-id="f77c7-190">檔案會宣告 `stockweb.yml` MVC 應用程式的部署和服務。</span><span class="sxs-lookup"><span data-stu-id="f77c7-190">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a><span data-ttu-id="f77c7-191">環境變數</span><span class="sxs-lookup"><span data-stu-id="f77c7-191">Environment variables</span></span>

<span data-ttu-id="f77c7-192">`env`Deployment 物件的區段會指定要在執行映射的容器中設定的環境變數 `stockweb:1.0.0` 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-192">The `env` section of the Deployment object specifies environment variables to be set in the container that's running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="f77c7-193">**`StockData__Address`** 由於 EnvironmentVariables 設定提供者，環境變數會對應至 `StockData:Address` 設定設定。</span><span class="sxs-lookup"><span data-stu-id="f77c7-193">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="f77c7-194">此設定會在名稱之間使用雙底線來分隔區段。</span><span class="sxs-lookup"><span data-stu-id="f77c7-194">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="f77c7-195">位址會使用服務的服務名稱 `stockdata` （在相同的 Kubernetes 命名空間中執行）。</span><span class="sxs-lookup"><span data-stu-id="f77c7-195">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="f77c7-196">**`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** 環境變數 <xref:System.AppContext> 會設定參數，以啟用的未加密 HTTP/2 連接 <xref:System.Net.Http.HttpClient> 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-196">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="f77c7-197">此環境變數執行的動作與在程式碼中設定參數相同，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f77c7-197">This environment variable does the same thing as setting the switch in code, as shown here:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="f77c7-198">如果您針對參數使用環境變數，您可以輕鬆地根據應用程式執行所在的內容來變更內容。</span><span class="sxs-lookup"><span data-stu-id="f77c7-198">If you use an environment variable for the switch, you can easily change the context depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="f77c7-199">服務類型</span><span class="sxs-lookup"><span data-stu-id="f77c7-199">Service types</span></span>

<span data-ttu-id="f77c7-200">`type: NodePort`屬性是用來使 web 應用程式可從叢集外部存取。</span><span class="sxs-lookup"><span data-stu-id="f77c7-200">The `type: NodePort` property is used to make the web application accessible from outside the cluster.</span></span> <span data-ttu-id="f77c7-201">此屬性類型會讓 Kubernetes 將服務上的埠80發佈到叢集外部網路通訊端上的任意埠。</span><span class="sxs-lookup"><span data-stu-id="f77c7-201">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="f77c7-202">您可以使用命令來尋找指派的埠 `kubectl get service` 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-202">You can find the assigned port by using the `kubectl get service` command.</span></span>

<span data-ttu-id="f77c7-203">`stockdata`服務不應從叢集外部存取，因此會使用預設類型 `ClusterIP` 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-203">The `stockdata` Service shouldn't be accessible from outside the cluster, so it uses the default type, `ClusterIP`.</span></span>

<span data-ttu-id="f77c7-204">生產系統很可能會使用整合式負載平衡器，將公用應用程式公開給外部取用者。</span><span class="sxs-lookup"><span data-stu-id="f77c7-204">Production systems will most likely use an integrated load balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="f77c7-205">以這種方式公開的服務應該使用 `LoadBalancer` 類型。</span><span class="sxs-lookup"><span data-stu-id="f77c7-205">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="f77c7-206">如需服務類型的詳細資訊，請參閱 [Kubernetes 發行服務](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) 檔。</span><span class="sxs-lookup"><span data-stu-id="f77c7-206">For more information on Service types, see the [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="f77c7-207">部署 StockWeb 應用程式</span><span class="sxs-lookup"><span data-stu-id="f77c7-207">Deploy the StockWeb application</span></span>

<span data-ttu-id="f77c7-208">使用 `kubectl` 以套用檔案 `stockweb.yml` ，並確認已建立部署和服務：</span><span class="sxs-lookup"><span data-stu-id="f77c7-208">Use `kubectl` to apply the `stockweb.yml` file and confirm that the Deployment and Service were created:</span></span>

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

<span data-ttu-id="f77c7-209">命令的輸出 `get service` 顯示 HTTP 埠已發佈至 `32564` 外部網路上的埠。</span><span class="sxs-lookup"><span data-stu-id="f77c7-209">The output of the `get service` command shows that the HTTP port has been published to port `32564` on the external network.</span></span> <span data-ttu-id="f77c7-210">若為 Docker Desktop，此 IP 位址會是 localhost。</span><span class="sxs-lookup"><span data-stu-id="f77c7-210">For Docker Desktop, this IP address will be localhost.</span></span> <span data-ttu-id="f77c7-211">您可以藉由流覽至來存取應用程式 `http://localhost:32564` 。</span><span class="sxs-lookup"><span data-stu-id="f77c7-211">You can access the application by browsing to `http://localhost:32564`.</span></span>

### <a name="test-the-application"></a><span data-ttu-id="f77c7-212">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="f77c7-212">Test the application</span></span>

<span data-ttu-id="f77c7-213">StockWeb 應用程式會顯示從簡單要求-回復服務取出的 NASDAQ 股票清單。</span><span class="sxs-lookup"><span data-stu-id="f77c7-213">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="f77c7-214">在此示範中，每一行也會顯示傳回它之服務實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="f77c7-214">For this demonstration, each line also shows the unique ID of the Service instance that returned it.</span></span>

![StockWeb 螢幕擷取畫面](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="f77c7-216">如果服務的複本數目 `stockdata` 已增加，您可能會預期 **伺服器** 值從行變更為行，但事實上，所有100記錄一律會從相同的實例傳回。</span><span class="sxs-lookup"><span data-stu-id="f77c7-216">If the number of replicas of the `stockdata` Service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="f77c7-217">如果您每隔幾秒重新整理頁面，伺服器識別碼會維持不變。</span><span class="sxs-lookup"><span data-stu-id="f77c7-217">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="f77c7-218">為什麼會這樣呢？</span><span class="sxs-lookup"><span data-stu-id="f77c7-218">Why does this happen?</span></span> <span data-ttu-id="f77c7-219">這裡有兩個因素。</span><span class="sxs-lookup"><span data-stu-id="f77c7-219">There are two factors at play here.</span></span>

<span data-ttu-id="f77c7-220">首先，Kubernetes 服務探索系統預設會使用迴圈配置資源負載平衡。</span><span class="sxs-lookup"><span data-stu-id="f77c7-220">First, the Kubernetes Service discovery system uses round-robin load balancing by default.</span></span> <span data-ttu-id="f77c7-221">第一次查詢 DNS 伺服器時，它會傳回第一個相符的服務 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f77c7-221">The first time the DNS server is queried, it will return the first matching IP address for the Service.</span></span> <span data-ttu-id="f77c7-222">下一次，它會傳回清單中的下一個 IP 位址，依此類推，直到結束為止。</span><span class="sxs-lookup"><span data-stu-id="f77c7-222">The next time, it will return the next IP address in the list, and so on, until the end.</span></span> <span data-ttu-id="f77c7-223">屆時，它會迴圈回到一開始。</span><span class="sxs-lookup"><span data-stu-id="f77c7-223">At that point, it loops back to the start.</span></span>

<span data-ttu-id="f77c7-224">其次， `HttpClient` 用於 StockWeb 應用程式 gRPC 用戶端的會由 [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)建立和管理，而且此用戶端的單一實例會用於每次呼叫頁面。</span><span class="sxs-lookup"><span data-stu-id="f77c7-224">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="f77c7-225">用戶端只會執行一次 DNS 查閱，因此所有要求都會路由至相同的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f77c7-225">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="f77c7-226">而且因為基於 `HttpClientHandler` 效能考慮而快取，所以快速連續的多個要求都會使用相同的 IP 位址，直到快取的 DNS 專案過期或因某些原因處置處理常式實例為止。</span><span class="sxs-lookup"><span data-stu-id="f77c7-226">And because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="f77c7-227">結果是 gRPC 服務的預設要求不會在叢集中該服務的所有實例之間平衡。</span><span class="sxs-lookup"><span data-stu-id="f77c7-227">The result is that by default requests to a gRPC Service aren't balanced across all instances of that Service in the cluster.</span></span> <span data-ttu-id="f77c7-228">不同的取用者會使用不同的實例，但這不保證會有良好的要求分配或資源的平衡使用。</span><span class="sxs-lookup"><span data-stu-id="f77c7-228">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests or a balanced use of resources.</span></span>

<span data-ttu-id="f77c7-229">下一章的 [服務網格](service-mesh.md)將解決此問題。</span><span class="sxs-lookup"><span data-stu-id="f77c7-229">The next chapter, [Service meshes](service-mesh.md), will address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f77c7-230">[上一個](docker.md) 
>[下一步](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="f77c7-230">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
