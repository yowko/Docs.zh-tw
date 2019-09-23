---
title: 適用于 WCF 開發人員的 Kubernetes-gRPC
description: 在 Kubernetes 叢集中執行 ASP.NET Core gRPC 服務。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3af1b92ade106cf2338816ec69e6b13312681339
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184404"
---
# <a name="kubernetes"></a><span data-ttu-id="f6e54-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f6e54-103">Kubernetes</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f6e54-104">雖然可以在 Docker 主機上手動執行容器，但在可靠的生產系統中，最好是使用容器協調流程引擎來管理多個在叢集中多部伺服器執行的實例。</span><span class="sxs-lookup"><span data-stu-id="f6e54-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's preferable to use a Container Orchestration Engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="f6e54-105">有各種不同的容器協調流程引擎可供使用，包括 Kubernetes、Docker Swarm 和 Apache Mesos。</span><span class="sxs-lookup"><span data-stu-id="f6e54-105">There are various Container Orchestration Engines available, including Kubernetes, Docker Swarm and Apache Mesos.</span></span> <span data-ttu-id="f6e54-106">但在這些引擎中，Kubernetes 遠低於最廣泛使用的，因此將會成為本章的重點。</span><span class="sxs-lookup"><span data-stu-id="f6e54-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="f6e54-107">Kubernetes 包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="f6e54-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="f6e54-108">**排程**會在叢集內的多個節點上執行容器，確保可用資源的使用量達到平衡，並在發生中斷時讓容器保持運作，以及處理新版本映射或新設定的輪流更新。</span><span class="sxs-lookup"><span data-stu-id="f6e54-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="f6e54-109">**健全狀況檢查**會監視容器以確保繼續服務。</span><span class="sxs-lookup"><span data-stu-id="f6e54-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="f6e54-110">**DNS & 服務探索**會處理叢集中服務之間的路由。</span><span class="sxs-lookup"><span data-stu-id="f6e54-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="f6e54-111">輸入會從**外部公開選取**的服務，而且通常會提供這些服務實例之間的負載平衡。</span><span class="sxs-lookup"><span data-stu-id="f6e54-111">**Ingress** exposes selected services externally, and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="f6e54-112">**資源管理**會將儲存體之類的外部資源附加至容器。</span><span class="sxs-lookup"><span data-stu-id="f6e54-112">**Resource management** attaches external resources such as storage to containers.</span></span>

<span data-ttu-id="f6e54-113">本章將詳細說明如何將 ASP.NET Core gRPC 服務和使用此服務的網站部署至 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="f6e54-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="f6e54-114">使用的範例應用程式可從 GitHub 上的[RendleLabs/grpc-wcf 開發人員存放庫取得。](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample)</span><span class="sxs-lookup"><span data-stu-id="f6e54-114">The sample application used is available from on the [RendleLabs/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub,</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="f6e54-115">Kubernetes 術語</span><span class="sxs-lookup"><span data-stu-id="f6e54-115">Kubernetes terminology</span></span>

<span data-ttu-id="f6e54-116">Kubernetes 會使用*預期狀態*設定：此 API 可用來描述 pod、*部署*和*服務*等*物件，而* *控制平面*會負責在所有節點上執行所需的狀態*在叢集中。*</span><span class="sxs-lookup"><span data-stu-id="f6e54-116">Kubernetes uses *desired state configuration*: the API is used to describe objects such as *Pods*, *Deployments* and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="f6e54-117">Kubernetes 叢集具有執行*Kubernetes API*的`kubectl` *主要*節點，可以透過程式設計方式或使用命令列工具來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="f6e54-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which can be communicated with programmatically or using the `kubectl` command-line tool.</span></span> <span data-ttu-id="f6e54-118">`kubectl`可以使用命令列引數來建立和管理物件，但最適合用於包含 Kubernetes 物件之宣告資料的 YAML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f6e54-118">`kubectl` can create and manage objects using command-line arguments, but works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="f6e54-119">Kubernetes YAML 檔</span><span class="sxs-lookup"><span data-stu-id="f6e54-119">Kubernetes YAML files</span></span>

<span data-ttu-id="f6e54-120">每個 Kubernetes YAML 檔至少會有三個最上層屬性。</span><span class="sxs-lookup"><span data-stu-id="f6e54-120">Every Kubernetes YAML file will have at least three top-level properties.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="f6e54-121">`apiVersion`屬性是用來指定檔案的目標版本（以及哪個 API）。</span><span class="sxs-lookup"><span data-stu-id="f6e54-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="f6e54-122">`kind`屬性會指定 YAML 代表的物件種類。</span><span class="sxs-lookup"><span data-stu-id="f6e54-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="f6e54-123">屬性包含物件屬性`name`，例如、 `namespace`或`labels`。 `metadata`</span><span class="sxs-lookup"><span data-stu-id="f6e54-123">The `metadata` property contains object properties such as `name`, `namespace`, or `labels`.</span></span>

<span data-ttu-id="f6e54-124">大部分的 Kubernetes YAML 檔案也會有`spec`一個區段，描述建立物件所需的資源和設定。</span><span class="sxs-lookup"><span data-stu-id="f6e54-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="f6e54-125">Pod</span><span class="sxs-lookup"><span data-stu-id="f6e54-125">Pods</span></span>

<span data-ttu-id="f6e54-126">Pod 是 Kubernetes 中的基本執行單位。</span><span class="sxs-lookup"><span data-stu-id="f6e54-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="f6e54-127">它們可以執行多個容器，但也會用來執行單一容器。</span><span class="sxs-lookup"><span data-stu-id="f6e54-127">They can run multiple containers, but are also used to run single containers.</span></span> <span data-ttu-id="f6e54-128">Pod 也包含容器所需的任何儲存體資源，以及網路 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f6e54-128">The pod also includes any storage resources required by the container(s), and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="f6e54-129">服務</span><span class="sxs-lookup"><span data-stu-id="f6e54-129">Services</span></span>

<span data-ttu-id="f6e54-130">服務是一種中繼物件，可描述 pod （或 pod 集），並提供在叢集中存取它們的方式，例如使用叢集 DNS 服務將服務名稱對應至一組 pod IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f6e54-130">Services are meta-objects that describe pods (or sets of pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="f6e54-131">部署</span><span class="sxs-lookup"><span data-stu-id="f6e54-131">Deployments</span></span>

<span data-ttu-id="f6e54-132">部署是適用于 pod 的*說明狀態*物件。</span><span class="sxs-lookup"><span data-stu-id="f6e54-132">Deployments are the *described state* objects for Pods.</span></span> <span data-ttu-id="f6e54-133">如果您手動建立 Pod，當它終止時，將不會重新開機。</span><span class="sxs-lookup"><span data-stu-id="f6e54-133">If you create a Pod manually, when it terminates it won't be restarted.</span></span> <span data-ttu-id="f6e54-134">部署是用來告訴叢集哪些 pod，以及這些 pod 的多少複本應該在目前的時間執行。</span><span class="sxs-lookup"><span data-stu-id="f6e54-134">Deployments are used to tell the cluster which pods, and how many replicas of those pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="f6e54-135">其他物件</span><span class="sxs-lookup"><span data-stu-id="f6e54-135">Other objects</span></span>

<span data-ttu-id="f6e54-136">Pod、服務和部署只是其中三個最基本的物件類型。</span><span class="sxs-lookup"><span data-stu-id="f6e54-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="f6e54-137">Kubernetes 叢集會管理數十種其他類型的物件。</span><span class="sxs-lookup"><span data-stu-id="f6e54-137">There are dozens of other types of object that are managed by a Kubernetes cluster.</span></span> <span data-ttu-id="f6e54-138">如需詳細資訊，請參閱[Kubernetes 概念](https://kubernetes.io/docs/concepts/)檔。</span><span class="sxs-lookup"><span data-stu-id="f6e54-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="f6e54-139">命名空間</span><span class="sxs-lookup"><span data-stu-id="f6e54-139">Namespaces</span></span>

<span data-ttu-id="f6e54-140">Kubernetes 叢集的設計是要擴充至數百個或數千個節點，並執行類似的服務數目。</span><span class="sxs-lookup"><span data-stu-id="f6e54-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes, and run similar numbers of services.</span></span> <span data-ttu-id="f6e54-141">為了避免物件名稱之間的衝突，命名空間是用來將物件群組在一起，以作為較大應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="f6e54-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="f6e54-142">Kubernetes 本身的`default`服務會在命名空間中執行。</span><span class="sxs-lookup"><span data-stu-id="f6e54-142">Kubernetes own services run in a `default` namespace.</span></span> <span data-ttu-id="f6e54-143">所有使用者物件都應該建立在自己的命名空間中，以避免可能與叢集中的預設物件或其他租使用者衝突。</span><span class="sxs-lookup"><span data-stu-id="f6e54-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="f6e54-144">開始使用 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f6e54-144">Get started with Kubernetes</span></span>

<span data-ttu-id="f6e54-145">如果您執行的是適用于 Windows 或 macOS 的 Docker Desktop，Kubernetes 已經可以使用。</span><span class="sxs-lookup"><span data-stu-id="f6e54-145">If you're running Docker Desktop for Windows or macOS, Kubernetes is already available.</span></span> <span data-ttu-id="f6e54-146">只要在 [設定] 視窗的 [Kubernetes] 區段中啟用它即可。</span><span class="sxs-lookup"><span data-stu-id="f6e54-146">Just enable it in the Kubernetes section of the Settings window.</span></span>

![在 Docker Desktop 中啟用 Kubernetes](media/kubernetes/enable-kubernetes-docker-desktop.png)

<span data-ttu-id="f6e54-148">若要在 Linux 中執行本機 Kubernetes 叢集，請查看[minikube](https://github.com/kubernetes/minikube)或[MicroK8s](https://microk8s.io/) （如果您的 linux 發行版本支援[snap](https://snapcraft.io/)）。</span><span class="sxs-lookup"><span data-stu-id="f6e54-148">To run a local Kubernetes cluster in Linux, look at [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="f6e54-149">若要檢查您的叢集是否正在執行且可供`kubectl version`存取，請執行命令。</span><span class="sxs-lookup"><span data-stu-id="f6e54-149">To check that your cluster is running and accessible, run the `kubectl version` command.</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="f6e54-150">在此範例中， `kubectl` CLI 和 Kubernetes 伺服器都是執行版本1.14.6。</span><span class="sxs-lookup"><span data-stu-id="f6e54-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="f6e54-151">的`kubectl`每個版本都應該支援伺服器的上一個和下一個版本，因此`kubectl` 1.14 也應該與伺服器版本1.13 和1.15 搭配運作。</span><span class="sxs-lookup"><span data-stu-id="f6e54-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="f6e54-152">在 Kubernetes 上執行服務</span><span class="sxs-lookup"><span data-stu-id="f6e54-152">Run services on Kubernetes</span></span>

<span data-ttu-id="f6e54-153">範例應用程式有一個`kube`包含三個 YAML 檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="f6e54-153">The sample application has a `kube` directory containing three YAML files.</span></span> <span data-ttu-id="f6e54-154">檔案會宣告自訂`stocks`命名空間。 `namespace.yml`</span><span class="sxs-lookup"><span data-stu-id="f6e54-154">The `namespace.yml` file declares a custom namespace, `stocks`.</span></span> <span data-ttu-id="f6e54-155">檔案會宣告 gRPC 應用程式的部署和服務，而此`stockweb.yml`檔案會針對使用 gRPC 服務的 ASP.NET Core 3.0 MVC web 應用程式宣告部署和服務。 `stockdata.yml`</span><span class="sxs-lookup"><span data-stu-id="f6e54-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 3.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="f6e54-156">若要使用`YAML` `kubectl`檔案搭配，請使用`apply -f`命令。</span><span class="sxs-lookup"><span data-stu-id="f6e54-156">To use a `YAML` file with `kubectl`, use the `apply -f` command.</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="f6e54-157">此`apply`命令會檢查 YAML 檔案的有效性，並顯示從 API 收到的任何錯誤，但不會等到檔案中宣告的所有物件都已建立，因為這可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="f6e54-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created as this can take some time.</span></span> <span data-ttu-id="f6e54-158">`kubectl get`使用命令搭配相關的物件類型，以檢查叢集中的物件建立。</span><span class="sxs-lookup"><span data-stu-id="f6e54-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="f6e54-159">命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="f6e54-159">The namespace declaration</span></span>

<span data-ttu-id="f6e54-160">命名空間宣告很簡單，而且只需要`name`指派。</span><span class="sxs-lookup"><span data-stu-id="f6e54-160">Namespace declaration is simple and requires only assigning a `name`.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="f6e54-161">使用`kubectl` 來`namespace.yml`套用檔案，並檢查是否已成功建立命名空間。</span><span class="sxs-lookup"><span data-stu-id="f6e54-161">Use `kubectl` to apply the `namespace.yml` file and check the namespace is created successfully.</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="f6e54-162">StockData 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6e54-162">The StockData application</span></span>

<span data-ttu-id="f6e54-163">`stockdata.yml`檔案會宣告兩個物件：部署和服務。</span><span class="sxs-lookup"><span data-stu-id="f6e54-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="f6e54-164">StockData 部署</span><span class="sxs-lookup"><span data-stu-id="f6e54-164">The StockData Deployment</span></span>

<span data-ttu-id="f6e54-165">部署元件會`spec`為部署本身提供，包括所需的複本數目， `template`以及要由部署建立和管理 Pod 物件的。</span><span class="sxs-lookup"><span data-stu-id="f6e54-165">The Deployment part provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="f6e54-166">請注意，部署物件是使用`apps` API 來管理，如中`apiVersion`所指定，而不是主要的 Kubernetes API。</span><span class="sxs-lookup"><span data-stu-id="f6e54-166">Note that Deployment objects are managed with the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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

<span data-ttu-id="f6e54-167">`spec.selector`屬性會用來比對執行中的 pod 與部署。</span><span class="sxs-lookup"><span data-stu-id="f6e54-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="f6e54-168">Pod 的`metadata.labels`屬性必須符合屬性， `matchLabels`否則 API 呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6e54-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="f6e54-169">`template.spec`區段會宣告要執行的容器。</span><span class="sxs-lookup"><span data-stu-id="f6e54-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="f6e54-170">使用本機 Kubernetes 叢集（例如 Docker Desktop 提供的叢集）時，您可以指定在本機建立的映射，只要它們有版本戳記即可。</span><span class="sxs-lookup"><span data-stu-id="f6e54-170">When working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6e54-171">根據預設，Kubernetes 一律會檢查並嘗試提取新的映射。</span><span class="sxs-lookup"><span data-stu-id="f6e54-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="f6e54-172">如果它在其已知的存放庫中找不到映射，Pod 建立將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6e54-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="f6e54-173">若要使用本機影像，請將`imagePullPolicy`設定`Never`為。</span><span class="sxs-lookup"><span data-stu-id="f6e54-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="f6e54-174">`ports`屬性會指定要在 Pod 上發佈的容器埠。</span><span class="sxs-lookup"><span data-stu-id="f6e54-174">The `ports` property specifies which container ports should be published on the Pod.</span></span>  <span data-ttu-id="f6e54-175">`stockservice`映射會在標準 HTTP 埠上執行服務，因此會發佈埠80。</span><span class="sxs-lookup"><span data-stu-id="f6e54-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="f6e54-176">`resources`區段會將資源限制套用至在 pod 中執行的容器。</span><span class="sxs-lookup"><span data-stu-id="f6e54-176">The `resources` section applies resource limits to the container running within the pod.</span></span> <span data-ttu-id="f6e54-177">這是很好的作法，因為它會防止個別 pod 耗用節點上的所有可用 CPU 或記憶體。</span><span class="sxs-lookup"><span data-stu-id="f6e54-177">This is good practice as it prevents an individual pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="f6e54-178">ASP.NET Core 3.0 已優化並微調為在資源限制的容器中執行，且`dotnet/core/aspnet` Docker 映射會設定環境變數，以`dotnet`告知執行時間其位於容器中。</span><span class="sxs-lookup"><span data-stu-id="f6e54-178">ASP.NET Core 3.0 has been optimized and tuned to run in resource-limited containers, and the `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="f6e54-179">StockData 服務</span><span class="sxs-lookup"><span data-stu-id="f6e54-179">The StockData Service</span></span>

<span data-ttu-id="f6e54-180">YAML 檔案的服務部分會宣告服務，以提供對叢集中 pod 的存取權。</span><span class="sxs-lookup"><span data-stu-id="f6e54-180">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

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

<span data-ttu-id="f6e54-181">服務規格會使用`selector`屬性來比對`Pods`執行，在此情況下，會尋找具有卷`run: stockdata`標的 pod。</span><span class="sxs-lookup"><span data-stu-id="f6e54-181">The Service spec uses the `selector` property to match running `Pods`, in this case looking for Pods with a label `run: stockdata`.</span></span> <span data-ttu-id="f6e54-182">在相符`port` pod 上指定的會由已命名的服務發行。</span><span class="sxs-lookup"><span data-stu-id="f6e54-182">The specified `port` on matching Pods are published by the named service.</span></span> <span data-ttu-id="f6e54-183">在命名空間中執行`stocks`的其他 pod 可以使用`http://stockdata`作為位址，在此服務上存取 HTTP。</span><span class="sxs-lookup"><span data-stu-id="f6e54-183">Other Pods running in the `stocks` namespace can access HTTP on this service using `http://stockdata` as the address.</span></span> <span data-ttu-id="f6e54-184">在其他命名空間中執行的`http://stockdata.stocks` pod 可以使用主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f6e54-184">Pods running in other namespaces can use the `http://stockdata.stocks` hostname.</span></span> <span data-ttu-id="f6e54-185">您可以使用[網路原則](https://kubernetes.io/docs/concepts/services-networking/network-policies/)來控制跨命名空間服務存取。</span><span class="sxs-lookup"><span data-stu-id="f6e54-185">You can control cross-namespace service access using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="f6e54-186">部署 StockData 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6e54-186">Deploy the StockData application</span></span>

<span data-ttu-id="f6e54-187">使用`kubectl` 來`stockdata.yml`套用檔案，並檢查是否已建立部署和服務。</span><span class="sxs-lookup"><span data-stu-id="f6e54-187">Use `kubectl` to apply the `stockdata.yml` file and check that the Deployment and Service were created.</span></span>

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

### <a name="the-stockweb-application"></a><span data-ttu-id="f6e54-188">StockWeb 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6e54-188">The StockWeb application</span></span>

<span data-ttu-id="f6e54-189">`stockweb.yml`檔案會宣告 MVC 應用程式的部署和服務。</span><span class="sxs-lookup"><span data-stu-id="f6e54-189">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

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

#### <a name="environment-variables"></a><span data-ttu-id="f6e54-190">環境變數</span><span class="sxs-lookup"><span data-stu-id="f6e54-190">Environment variables</span></span>

<span data-ttu-id="f6e54-191">部署`env`物件的區段會指定要在執行`stockweb:1.0.0`映射的容器中設定的環境變數。</span><span class="sxs-lookup"><span data-stu-id="f6e54-191">The `env` section of the Deployment object specifies environment variables to be set in the container running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="f6e54-192">由於 EnvironmentVariables 設定提供者的不同`StockData:Address` ，**環境變數將會對應到configuration設定。`StockData__Address`**</span><span class="sxs-lookup"><span data-stu-id="f6e54-192">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="f6e54-193">此設定會在名稱之間使用雙底線來分隔區段。</span><span class="sxs-lookup"><span data-stu-id="f6e54-193">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="f6e54-194">此位址會使用`stockdata`服務的服務名稱，這會在相同的 Kubernetes 命名空間中執行。</span><span class="sxs-lookup"><span data-stu-id="f6e54-194">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="f6e54-195">環境變數會<xref:System.AppContext>設定參數，以啟用的<xref:System.Net.Http.HttpClient>未加密 HTTP/2 連接。 **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`**</span><span class="sxs-lookup"><span data-stu-id="f6e54-195">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="f6e54-196">此環境變數相當於在程式碼中設定參數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f6e54-196">This environment variable is the equivalent of setting the switch in code as shown here.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="f6e54-197">針對參數使用環境變數，表示可以根據應用程式執行所在的內容，輕鬆地變更設定。</span><span class="sxs-lookup"><span data-stu-id="f6e54-197">Using an environment variable for the switch means the setting can easily be changed depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="f6e54-198">服務類型</span><span class="sxs-lookup"><span data-stu-id="f6e54-198">Service types</span></span>

<span data-ttu-id="f6e54-199">若要讓 Web 應用程式可從叢集外部存取， `type: NodePort`則會使用屬性。</span><span class="sxs-lookup"><span data-stu-id="f6e54-199">To make the Web application accessible from outside the cluster, the `type: NodePort` property is used.</span></span> <span data-ttu-id="f6e54-200">此屬性類型會導致 Kubernetes 將服務上的埠80發佈至叢集的外部網路通訊端上的任意埠。</span><span class="sxs-lookup"><span data-stu-id="f6e54-200">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="f6e54-201">您可以使用`kubectl get service`命令來尋找指派的埠。</span><span class="sxs-lookup"><span data-stu-id="f6e54-201">The port assigned can be found using the `kubectl get service` command.</span></span>

<span data-ttu-id="f6e54-202">服務不應可從叢集外部存取，因此會使用預設`ClusterIP`類型。 `stockdata`</span><span class="sxs-lookup"><span data-stu-id="f6e54-202">The `stockdata` service shouldn't be accessible from outside the cluster, so it used the default type, `ClusterIP`.</span></span>

<span data-ttu-id="f6e54-203">生產系統很可能會使用整合式負載平衡器向外部取用者公開公用應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6e54-203">Production systems will most likely use an integrated load-balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="f6e54-204">以這種方式公開的服務應該`LoadBalancer`使用型別。</span><span class="sxs-lookup"><span data-stu-id="f6e54-204">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="f6e54-205">如需有關服務類型的詳細資訊，請參閱[Kubernetes 的發佈服務](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types)檔。</span><span class="sxs-lookup"><span data-stu-id="f6e54-205">For more information on service types, see the [Kubernetes' Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="f6e54-206">部署 StockWeb 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6e54-206">Deploy the StockWeb application</span></span>

<span data-ttu-id="f6e54-207">使用`kubectl` 來`stockweb.yml`套用檔案，並檢查是否已建立部署和服務。</span><span class="sxs-lookup"><span data-stu-id="f6e54-207">Use `kubectl` to apply the `stockweb.yml` file and check that the Deployment and Service were created.</span></span>

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

<span data-ttu-id="f6e54-208">`get service`命令的輸出顯示 HTTP 埠已發佈至外部網路上的埠`32564` ; 針對 Docker Desktop，這會是 localhost。</span><span class="sxs-lookup"><span data-stu-id="f6e54-208">The output from the `get service` command shows that the HTTP port has been published to port `32564` on the external network; for Docker Desktop, this will be localhost.</span></span> <span data-ttu-id="f6e54-209">您可以流覽至來`http://localhost:32564`存取應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6e54-209">The application can be accessed by browsing to `http://localhost:32564`.</span></span>

### <a name="testing-the-application"></a><span data-ttu-id="f6e54-210">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="f6e54-210">Testing the application</span></span>

<span data-ttu-id="f6e54-211">StockWeb 應用程式會顯示從簡單的要求-回復服務中取出的 NASDAQ 股票清單。</span><span class="sxs-lookup"><span data-stu-id="f6e54-211">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="f6e54-212">基於示範目的，每一行也會顯示傳回它之服務實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="f6e54-212">For demonstration purposes, each line also shows the unique ID of the service instance that returned it.</span></span>

![StockWeb 螢幕擷取畫面](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="f6e54-214">如果`stockdata`服務的複本數目已增加，您可能會預期**伺服器**值從行變更為行，但事實上，所有100記錄一律會從相同的實例傳回。</span><span class="sxs-lookup"><span data-stu-id="f6e54-214">If the number of replicas of the `stockdata` service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="f6e54-215">如果您每隔幾秒鐘就重新整理頁面，伺服器識別碼會維持不變。</span><span class="sxs-lookup"><span data-stu-id="f6e54-215">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="f6e54-216">為什麼會發生這種情況？</span><span class="sxs-lookup"><span data-stu-id="f6e54-216">Why does this happen?</span></span> <span data-ttu-id="f6e54-217">這裡有兩個因素。</span><span class="sxs-lookup"><span data-stu-id="f6e54-217">There are two factors at play here.</span></span>

<span data-ttu-id="f6e54-218">首先，Kubernetes 服務探索系統預設會使用「迴圈配置資源」負載平衡。</span><span class="sxs-lookup"><span data-stu-id="f6e54-218">First, the Kubernetes service discovery system uses "round-robin" load-balancing by default.</span></span> <span data-ttu-id="f6e54-219">第一次查詢 DNS 伺服器時，它會傳回服務的第一個相符的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f6e54-219">The first time the DNS server is queried, it will return the first matching IP address for the service.</span></span> <span data-ttu-id="f6e54-220">下一次是清單中的下一個 IP 位址，依此類推，直到結束為止，然後才會迴圈回到開始位置。</span><span class="sxs-lookup"><span data-stu-id="f6e54-220">The next time, the next IP address in the list, and so on, until the end, at which point it loops back to the start.</span></span>

<span data-ttu-id="f6e54-221">第二， `HttpClient`用於 StockWeb 應用程式的 gRPC 用戶端的會由[ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)建立和管理，而這個用戶端的單一實例會用於每次呼叫頁面。</span><span class="sxs-lookup"><span data-stu-id="f6e54-221">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="f6e54-222">用戶端只會執行一個 DNS 查閱，因此所有要求都會路由傳送至相同的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f6e54-222">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="f6e54-223">此外，因為`HttpClientHandler`會基於效能考慮而快取，所以快速連續的多個要求*全都*會使用相同的 IP 位址，直到快取的 DNS 專案到期，或因某些原因處置處理常式實例為止。</span><span class="sxs-lookup"><span data-stu-id="f6e54-223">Furthermore, because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="f6e54-224">這表示根據預設，gRPC 服務的要求不會在叢集中該服務的所有實例之間平衡。</span><span class="sxs-lookup"><span data-stu-id="f6e54-224">This means that by default requests to a gRPC service aren't balanced across all instances of that service in the cluster.</span></span> <span data-ttu-id="f6e54-225">不同的取用者會使用不同的實例，但這並不保證會有良好的要求散發和平衡的資源使用。</span><span class="sxs-lookup"><span data-stu-id="f6e54-225">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests and a balanced use of resources.</span></span>

<span data-ttu-id="f6e54-226">下一章的[服務網格](service-mesh.md)將探討如何解決此問題。</span><span class="sxs-lookup"><span data-stu-id="f6e54-226">The next chapter, [Service Meshes](service-mesh.md), will look at how to address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f6e54-227">[上一頁](docker.md)
>[下一頁](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="f6e54-227">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
