---
title: 利用容器和協調器
description: 使用 Azure 中的 Docker 容器和庫伯內特協調器
ms.date: 06/30/2019
ms.openlocfilehash: 44b2fff8c9c88717d83e41a421b9817e2cc68135
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989034"
---
# <a name="leveraging-containers-and-orchestrators"></a><span data-ttu-id="2f5ae-103">利用容器和協調器</span><span class="sxs-lookup"><span data-stu-id="2f5ae-103">Leveraging containers and orchestrators</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2f5ae-104">容器和協調器旨在解決單一部署方法中常見的問題。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-104">Containers and orchestrators are designed to solve problems common to monolithic deployment approaches.</span></span>

## <a name="challenges-with-monolithic-deployments"></a><span data-ttu-id="2f5ae-105">整體部署的挑戰</span><span class="sxs-lookup"><span data-stu-id="2f5ae-105">Challenges with monolithic deployments</span></span>

<span data-ttu-id="2f5ae-106">傳統上,大多數應用程式都部署為單個單元。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-106">Traditionally, most applications have been deployed as a single unit.</span></span> <span data-ttu-id="2f5ae-107">此類應用程式稱為單體。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-107">Such applications are referred to as a monolith.</span></span> <span data-ttu-id="2f5ae-108">這種將應用程式部署為單個單元的一般方法,即使它們由多個模組或程式集組成,也稱為單片架構,如圖 3-1 所示。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-108">This general approach of deploying applications as single units even if they're composed of multiple modules or assemblies is known as monolithic architecture, as shown in Figure 3-1.</span></span>

![單體架構。](./media/monolithic-architecture.png)

<span data-ttu-id="2f5ae-110">**圖3-1**。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-110">**Figure 3-1**.</span></span> <span data-ttu-id="2f5ae-111">單體架構。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-111">Monolithic architecture.</span></span>

<span data-ttu-id="2f5ae-112">儘管單片式架構具有簡單性的優點,但它們面臨著許多挑戰:</span><span class="sxs-lookup"><span data-stu-id="2f5ae-112">Although they have the benefit of simplicity, monolithic architectures face a number of challenges:</span></span>

### <a name="deployments"></a><span data-ttu-id="2f5ae-113">部署</span><span class="sxs-lookup"><span data-stu-id="2f5ae-113">Deployments</span></span>

<span data-ttu-id="2f5ae-114">部署到單一應用程式通常需要重新啟動整個應用程式,即使只替換一個小型模組也是如此。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-114">Deploying to monolithic applications typically requires restarting the entire application, even if only one small module is being replaced.</span></span> <span data-ttu-id="2f5ae-115">根據託管應用程式的計算機數,這可能導致部署期間的停機時間。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-115">Depending on the number of machines hosting the application, this can result in downtime during deployments.</span></span>

### <a name="hosting"></a><span data-ttu-id="2f5ae-116">裝載</span><span class="sxs-lookup"><span data-stu-id="2f5ae-116">Hosting</span></span>

<span data-ttu-id="2f5ae-117">單片應用程式完全託管在單個計算機實例上。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-117">Monolithic applications are hosted entirely on a single machine instance.</span></span> <span data-ttu-id="2f5ae-118">這可能需要比分布式應用程式中任何模組所需的更高功能的硬體。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-118">This may require higher-capability hardware than any module in a distributed application would need.</span></span> <span data-ttu-id="2f5ae-119">此外,如果應用的任何部分成為瓶頸,則必須將整個應用程式部署到其他計算機節點才能橫向擴展。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-119">Also, if any part of the app becomes a bottleneck, the entire application must be deployed to additional machine nodes in order to scale out.</span></span>

### <a name="environment"></a><span data-ttu-id="2f5ae-120">環境</span><span class="sxs-lookup"><span data-stu-id="2f5ae-120">Environment</span></span>

<span data-ttu-id="2f5ae-121">單片應用程式通常部署到現有的託管環境(作業系統、已安裝的框架等)。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-121">Monolithic applications are typically deployed into an existing hosting environment (operating system, installed frameworks, etc.).</span></span> <span data-ttu-id="2f5ae-122">此環境可能與開發或測試應用程式的環境不匹配。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-122">This environment may not match the environment in which the application was developed or tested.</span></span> <span data-ttu-id="2f5ae-123">應用程序環境中的不一致是單一部署的常見問題來源。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-123">Inconsistencies in the application's environment are a common source of problems for monolithic deployments.</span></span>

### <a name="coupling"></a><span data-ttu-id="2f5ae-124">耦合</span><span class="sxs-lookup"><span data-stu-id="2f5ae-124">Coupling</span></span>

<span data-ttu-id="2f5ae-125">單片應用程式在應用程式的不同部分之間以及應用程式與其環境之間可能有很大的耦合。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-125">Monolithic applications are likely to have a great deal of coupling between different parts of the application, and between the application and its environment.</span></span> <span data-ttu-id="2f5ae-126">這會使以後難以分解特定服務或問題,以便增加其可伸縮性或在替代實現中交換。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-126">This can make it difficult to factor out a particular service or concern later, in order to increase its scalability or swap in an alternative implementation.</span></span> <span data-ttu-id="2f5ae-127">這種耦合還會導致對系統更改產生更大的潛在影響,需要在較大的應用中進行廣泛的測試。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-127">This coupling also leads to much larger potential impacts for changes to the system, requiring extensive testing in larger applications.</span></span>

### <a name="technology-choice"></a><span data-ttu-id="2f5ae-128">技術選擇</span><span class="sxs-lookup"><span data-stu-id="2f5ae-128">Technology choice</span></span>

<span data-ttu-id="2f5ae-129">單片應用程序作為一個單元構建和部署。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-129">Monolithic applications are built and deployed as a unit.</span></span> <span data-ttu-id="2f5ae-130">這提供了簡單性和統一性,但可能是創新的障礙。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-130">This offers simplicity and uniformity but can be a barrier to innovation.</span></span> <span data-ttu-id="2f5ae-131">儘管系統中的新功能或模組可能更適合更現代的平臺或框架,但為了一致性以及易於開發和部署,可能會使用應用程式的當前方法構建它。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-131">Although a new feature or module in the system might be better-suited to a more modern platform or framework, it's likely to be built using the application's current approach for the sake of consistency as well as ease of development and deployment.</span></span>

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a><span data-ttu-id="2f5ae-132">容器和協調器有什麼好處?</span><span class="sxs-lookup"><span data-stu-id="2f5ae-132">What are the benefits of containers and orchestrators?</span></span>

<span data-ttu-id="2f5ae-133">Docker 是最受歡迎的容器管理和映射平台,允許您快速處理 Linux 和 Windows 上的容器。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-133">Docker is the most popular container management and imaging platform and allows you to quickly work with containers on Linux and Windows.</span></span> <span data-ttu-id="2f5ae-134">容器提供單獨但可重現的應用程式環境,這些環境在任何系統上以相同的方式運行。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-134">Containers provide separate but reproducible application environments that run the same way on any system.</span></span> <span data-ttu-id="2f5ae-135">這使得它們非常適合在雲原生應用程式中開發和託管應用程式和應用程式元件。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-135">This makes them perfect for developing and hosting applications and app components in cloud-native applications.</span></span> <span data-ttu-id="2f5ae-136">容器彼此隔離,因此同一主機硬體上的兩個容器可以安裝不同版本的軟體,甚至操作系統,而不會造成依賴項衝突。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-136">Containers are isolated from one another, so two containers on the same host hardware can have different versions of software and even operating system installed, without the dependencies causing conflicts.</span></span>

<span data-ttu-id="2f5ae-137">此外,容器由可簽入原始程式碼管理的簡單檔定義。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-137">What's more, containers are defined by simple files that can be checked into source control.</span></span> <span data-ttu-id="2f5ae-138">與完整伺服器(甚至虛擬機器)不同,通常需要手動工作才能應用更新或安裝其他服務,因此容器基礎結構很容易被版本控制。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-138">Unlike full servers, even virtual machines, which frequently require manual work to apply updates or install additional services, container infrastructure can easily be version-controlled.</span></span> <span data-ttu-id="2f5ae-139">因此,在容器中運行構建的應用可以使用自動工具作為生成管道的一部分進行開發、測試和部署。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-139">Thus, apps built to run in containers can be developed, tested, and deployed using automated tools as part of a build pipeline.</span></span>

<span data-ttu-id="2f5ae-140">容器是不可改變的。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-140">Containers are immutable.</span></span> <span data-ttu-id="2f5ae-141">獲得容器的定義後,可以重新創建該容器,並且它將以完全相同的方式運行。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-141">Once you have the definition of a container, you can recreate that container and it will run exactly the same way.</span></span> <span data-ttu-id="2f5ae-142">這種不變性適用於基於元件的設計。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-142">This immutability lends itself to component-based design.</span></span> <span data-ttu-id="2f5ae-143">如果應用程式的某些部分更改頻率不如其他部分頻繁,那麼為什麼當您只需部署更改次數最多的部分時,才能重新部署整個應用程式?</span><span class="sxs-lookup"><span data-stu-id="2f5ae-143">If some parts of an application don't change as often as others, why redeploy the entire app when you can just deploy the parts that change most frequently?</span></span> <span data-ttu-id="2f5ae-144">應用的不同功能和交叉問題可以分解為單獨的單元。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-144">Different features and cross-cutting concerns of an app can be broken up into separate units.</span></span> <span data-ttu-id="2f5ae-145">圖 3-2 顯示了單片應用如何通過委派某些功能或功能來利用容器和微服務。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-145">Figure 3-2 shows how a monolithic app can take advantage of containers and microservices by delegating certain features or functionality.</span></span> <span data-ttu-id="2f5ae-146">應用本身的剩餘功能也已容器化。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-146">The remaining functionality in the app itself has also been containerized.</span></span>

<span data-ttu-id="2f5ae-147">![分解單片應用,在後端使用微服務。](./media/breaking-up-monolith-with-backend-microservices.png)
**圖3-2**.</span><span class="sxs-lookup"><span data-stu-id="2f5ae-147">![Breaking up a monolithic app to use microservices in the back end.](./media/breaking-up-monolith-with-backend-microservices.png)
**Figure 3-2**.</span></span> <span data-ttu-id="2f5ae-148">分解單片應用,在後端使用微服務。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-148">Breaking up a monolithic app to use microservices in the back end.</span></span>

<span data-ttu-id="2f5ae-149">使用單獨的容器構建的雲原生應用可根據需要部署盡可能多的或很少的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-149">Cloud-native apps built using separate containers benefit from the ability to deploy as much or as little of an application as needed.</span></span> <span data-ttu-id="2f5ae-150">單個服務可以託管在具有適合每個服務的節點上。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-150">Individual services can be hosted on nodes with resources appropriate to each service.</span></span> <span data-ttu-id="2f5ae-151">每個服務運行的環境是不可變的,可以在開發、測試和生產之間共用,並且可以輕鬆進行版本控制。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-151">The environment each service runs in is immutable, can be shared between dev, test, and production, and can easily be versioned.</span></span> <span data-ttu-id="2f5ae-152">應用程式不同區域之間的耦合作為服務之間的調用或消息顯式發生,而不是單體中的編譯時間依賴項。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-152">Coupling between different areas of the application occurs explicitly as calls or messages between services, not compile-time dependencies within the monolith.</span></span> <span data-ttu-id="2f5ae-153">整個應用的任何給定部分都可以選擇對該功能或功能最有意義的技術,而無需更改應用的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-153">And any given part of the overall app can choose the technology that makes the most sense for that feature or capability without requiring changes to the rest of the app.</span></span>

## <a name="what-are-the-scaling-benefits"></a><span data-ttu-id="2f5ae-154">擴展優勢是什麼?</span><span class="sxs-lookup"><span data-stu-id="2f5ae-154">What are the scaling benefits?</span></span>

<span data-ttu-id="2f5ae-155">構建在容器上的服務可以利用庫伯奈斯等業務流程工具提供的擴展優勢。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-155">Services built on containers can leverage scaling benefits provided by orchestration tools like Kubernetes.</span></span> <span data-ttu-id="2f5ae-156">根據設計,容器只知道自己。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-156">By design containers only know about themselves.</span></span> <span data-ttu-id="2f5ae-157">一旦開始有多個容器需要協同工作,就可以在更高的級別組織它們。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-157">Once you start to have multiple containers that need to work together, it can be worthwhile to organize them at a higher level.</span></span> <span data-ttu-id="2f5ae-158">組織大量容器及其共享依賴項(如網路配置)是業務流程工具用於節省一天的位置!</span><span class="sxs-lookup"><span data-stu-id="2f5ae-158">Organizing large numbers of containers and their shared dependencies, such as network configuration, is where orchestration tools come in to save the day!</span></span> <span data-ttu-id="2f5ae-159">Kubernetes 是一個容器編排平臺,旨在自動部署、擴展和管理容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-159">Kubernetes is a container orchestration platform designed to automate deployment, scaling, and management of containerized applications.</span></span> <span data-ttu-id="2f5ae-160">在容器群組之上建立抽象層,並將它們組織到*窗格中*。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-160">It creates an abstraction layer on top of groups of containers and organizes them into *pods*.</span></span> <span data-ttu-id="2f5ae-161">在稱為*節點*的工作電腦上運行的 Pod。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-161">Pods run on worker machines referred to as *nodes*.</span></span> <span data-ttu-id="2f5ae-162">整個有組織的群組稱為*群組*。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-162">The whole organized group is referred to as a *cluster*.</span></span> <span data-ttu-id="2f5ae-163">圖 3-3 顯示了庫伯內斯群集的不同元件。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-163">Figure 3-3 shows the different components of a Kubernetes cluster.</span></span>

<span data-ttu-id="2f5ae-164">![庫伯內斯集群組。](./media/kubernetes-cluster-components.png)
**圖3-3**.</span><span class="sxs-lookup"><span data-stu-id="2f5ae-164">![Kubernetes cluster components.](./media/kubernetes-cluster-components.png)
**Figure 3-3**.</span></span> <span data-ttu-id="2f5ae-165">庫伯內斯集群組。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-165">Kubernetes cluster components.</span></span>

<span data-ttu-id="2f5ae-166">Kubernetes 內置支援擴展群集以滿足需求。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-166">Kubernetes has built-in support for scaling clusters to meet demand.</span></span> <span data-ttu-id="2f5ae-167">結合容器化微服務,這為雲原生應用程式提供了在需要時和任何地方使用額外資源快速高效地回應需求高峰的能力。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-167">Combined with containerized micro-services, this provides cloud-native applications with the ability to quickly and efficiently respond to spikes in demand with additional resources when and where they're needed.</span></span>

### <a name="declarative-versus-imperative"></a><span data-ttu-id="2f5ae-168">宣告性與命令性</span><span class="sxs-lookup"><span data-stu-id="2f5ae-168">Declarative versus imperative</span></span>

<span data-ttu-id="2f5ae-169">庫伯內斯支援聲明性物件和命令性物件配置。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-169">Kubernetes supports both declarative and imperative object configuration.</span></span> <span data-ttu-id="2f5ae-170">命令性方法涉及運行各種命令,告訴 Kubernetes 如何執行每一步。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-170">The imperative approach involves running various commands that tell Kubernetes what to do each step of the way.</span></span> <span data-ttu-id="2f5ae-171">*運行*此映射。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-171">*Run* this image.</span></span> <span data-ttu-id="2f5ae-172">*刪除*此窗格。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-172">*Delete* this pod.</span></span> <span data-ttu-id="2f5ae-173">*公開*此埠。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-173">*Expose* this port.</span></span> <span data-ttu-id="2f5ae-174">使用聲明性方法,您可以使用一個配置檔來描述*您想要做什麼*而不是*做什麼*,Kubernetes 會找出要做什麼來實現所需的結束狀態。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-174">With the declarative approach, you use a configuration file that describes *what you want* instead of *what to do* and Kubernetes figures out what to do to achieve the desired end state.</span></span> <span data-ttu-id="2f5ae-175">如果已經使用指令命令設定群集,則可以使用 匯出宣告性`kubectl get svc SERVICENAME -o yaml > service.yaml`清單 。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-175">If you've already configured your cluster using imperative commands, you can export a declarative manifest by using `kubectl get svc SERVICENAME -o yaml > service.yaml`.</span></span> <span data-ttu-id="2f5ae-176">這會產生以下的清單檔:</span><span class="sxs-lookup"><span data-stu-id="2f5ae-176">This will produce a manifest file like this one:</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: "2019-09-13T13:58:47Z"
  labels:
    component: apiserver
    provider: kubernetes
  name: kubernetes
  namespace: default
  resourceVersion: "153"
  selfLink: /api/v1/namespaces/default/services/kubernetes
  uid: 9b1fac62-d62e-11e9-8968-00155d38010d
spec:
  clusterIP: 10.96.0.1
  ports:
  - name: https
    port: 443
    protocol: TCP
    targetPort: 6443
  sessionAffinity: None
  type: ClusterIP
status:
  loadBalancer: {}
```

<span data-ttu-id="2f5ae-177">使用聲明性配置時,可以通過對配置檔所在的資料夾進行`kubectl diff -f FOLDERNAME`引用 之前預覽這些更改。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-177">When using declarative configuration, you can preview the changes that will be made before committing them by using `kubectl diff -f FOLDERNAME` against the folder where your configuration files are located.</span></span> <span data-ttu-id="2f5ae-178">確定要套用變更後,`kubectl apply -f FOLDERNAME`請執行 。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-178">Once you're sure you want to apply the changes, run `kubectl apply -f FOLDERNAME`.</span></span> <span data-ttu-id="2f5ae-179">添加到`-R`遞歸處理資料夾層次結構。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-179">Add `-R` to recursively process a folder hierarchy.</span></span>

<span data-ttu-id="2f5ae-180">除了服務之外,還可以對其他 Kubernetes 功能(如*部署*)使用聲明性配置。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-180">In addition to services, you can use declarative configuration for other Kubernetes features, such as *deployments*.</span></span> <span data-ttu-id="2f5ae-181">聲明性部署由部署控制器用於更新群集資源。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-181">Declarative deployments are used by deployment controllers to update cluster resources.</span></span> <span data-ttu-id="2f5ae-182">部署用於添加新更改、向上擴展以支援更多負載或回滾到以前的修訂版。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-182">Deployments are used to roll out new changes, scale up to support more load, or roll back to a previous revision.</span></span> <span data-ttu-id="2f5ae-183">如果群集不穩定,聲明性部署提供了自動將群集恢復到所需狀態的機制。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-183">If a cluster is unstable, declarative deployments provide a mechanism for automatically bringing the cluster back to a desired state.</span></span>

<span data-ttu-id="2f5ae-184">使用聲明性配置可以將基礎結構表示為代碼,該代碼可以簽入並隨著應用程式代碼進行版本控制。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-184">Using declarative configuration allows infrastructure to be represented as code that can be checked in and versioned alongside the application code.</span></span> <span data-ttu-id="2f5ae-185">這提供了改進的更改控制,並更好地支援使用與原始程式碼管理更改關聯的生成和部署管道進行持續部署。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-185">This provides improved change control and better support for continuous deployment using a build and deploy pipeline tied to source control changes.</span></span>

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a><span data-ttu-id="2f5ae-186">哪些方案非常適合容器和協調器?</span><span class="sxs-lookup"><span data-stu-id="2f5ae-186">What scenarios are ideal for containers and orchestrators?</span></span>

<span data-ttu-id="2f5ae-187">以下方案非常適合使用容器和協調器。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-187">The following scenarios are ideal for using containers and orchestrators.</span></span>

### <a name="applications-requiring-high-uptime-and-scalability"></a><span data-ttu-id="2f5ae-188">需要高停機時間和可擴充性的應用程式</span><span class="sxs-lookup"><span data-stu-id="2f5ae-188">Applications requiring high uptime and scalability</span></span>

<span data-ttu-id="2f5ae-189">具有高高高高高高高擴展性和可擴充性要求的各個應用程式是使用微服務、容器和協調器的雲原生體系結構的理想選擇。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-189">Individual applications that have high uptime and scalability requirements are ideal candidates for cloud-native architectures using microservices, containers, and orchestrators.</span></span> <span data-ttu-id="2f5ae-190">這些應用程式可以使用版本化環境在容器中開發,可以在生產前進行廣泛測試,並且可以以零停機時間部署到生產中。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-190">These applications can be developed in containers using versioned environments, can be extensively tested before going to production, and can be deployed to production with zero downtime.</span></span> <span data-ttu-id="2f5ae-191">使用 Kubernetes 群集可確保此類應用還可以按需擴展,並從節點故障中自動恢復。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-191">The use of Kubernetes clusters ensures such apps can also scale on demand and recover automatically from node failures.</span></span>

### <a name="large-numbers-of-applications"></a><span data-ttu-id="2f5ae-192">大量應用</span><span class="sxs-lookup"><span data-stu-id="2f5ae-192">Large numbers of applications</span></span>

<span data-ttu-id="2f5ae-193">部署並隨後必須維護大量應用程式的組織受益於容器和協調器。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-193">Organizations that deploy and must subsequently maintain large numbers of applications benefit from containers and orchestrators.</span></span> <span data-ttu-id="2f5ae-194">設置容器化環境和 Kubernetes 群集的前期工作主要是固定成本。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-194">The up front effort of setting up containerized environments and Kubernetes clusters is primarily a fixed cost.</span></span> <span data-ttu-id="2f5ae-195">部署、維護和更新單個應用程式的成本隨必須維護的應用程序數量而異。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-195">Deploying, maintaining, and updating individual applications has a cost that varies with the number of applications that must be maintained.</span></span> <span data-ttu-id="2f5ae-196">除了數量相當少的應用程式之外,手動維護自定義應用程式的複雜性超過了使用容器和協調器實現解決方案的成本。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-196">Beyond a certain fairly small number of applications, the complexity of maintaining custom applications manually exceeds the cost of implementing a solution using containers and orchestrators.</span></span>

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a><span data-ttu-id="2f5ae-197">何時應避免使用容器和協調器?</span><span class="sxs-lookup"><span data-stu-id="2f5ae-197">When should you avoid using containers and orchestrators?</span></span>

<span data-ttu-id="2f5ae-198">如果您不願意或無法按照十二因子應用原則構建應用程式,則最好避免容器和協調器。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-198">If you're unwilling or unable to build your application following Twelve-Factor App principles, you'll probably be better off avoiding containers and orchestrators.</span></span> <span data-ttu-id="2f5ae-199">在這些情況下,最好使用基於 VM 的託管平臺,或者可能採用一些混合系統,您可以在其中將某些功能引入單獨的容器甚至無伺服器功能。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-199">In these cases, it may be best to move forward with a VM-based hosting platform, or possibly some hybrid system in which you can spin off certain pieces of functionality into separate containers or even serverless functions.</span></span>

## <a name="development-resources"></a><span data-ttu-id="2f5ae-200">開發資源</span><span class="sxs-lookup"><span data-stu-id="2f5ae-200">Development resources</span></span>

<span data-ttu-id="2f5ae-201">本節顯示一個開發資源的簡短清單,這些資源可説明您開始為下一個應用程式使用容器和協調器。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-201">This section shows a short list of development resources that may help you get started using containers and orchestrators for your next application.</span></span> <span data-ttu-id="2f5ae-202">如果您要尋找有關如何設計雲原生微服務體系結構應用的指導,請閱讀本書的配套書[.NET 微服務:容器化 .NET 應用程式的體系結構](https://aka.ms/microservicesebook)。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-202">If you're looking for guidance on how to design your cloud-native microservices architecture app, read this book's companion, [.NET Microservices: Architecture for Containerized .NET Applications](https://aka.ms/microservicesebook).</span></span>

### <a name="local-kubernetes-development"></a><span data-ttu-id="2f5ae-203">當地庫伯內斯開發</span><span class="sxs-lookup"><span data-stu-id="2f5ae-203">Local Kubernetes Development</span></span>

<span data-ttu-id="2f5ae-204">Kubernetes 部署在生產環境中提供了巨大的價值,但您也可以在本地運行它們。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-204">Kubernetes deployments provide great value in production environments, but you can also run them locally.</span></span> <span data-ttu-id="2f5ae-205">儘管大部分時間都能夠獨立處理單個應用或微服務是件好事,但有時能夠像部署到生產時一樣在本地運行整個系統是件好事。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-205">Although much of the time it's good to be able to work on individual apps or microservices independently, sometimes it's good to be able to run the whole system locally just as it will run when deployed to production.</span></span> <span data-ttu-id="2f5ae-206">有幾種方法可以實現此目的,其中兩種方法是 Minikube 和 Docker 桌面。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-206">There are several ways to achieve this, two of which are Minikube and Docker Desktop.</span></span> <span data-ttu-id="2f5ae-207">Visual Studio 還為 Docker 開發提供工具。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-207">Visual Studio also provides tooling for Docker development.</span></span>

### <a name="minikube"></a><span data-ttu-id="2f5ae-208">Minikube</span><span class="sxs-lookup"><span data-stu-id="2f5ae-208">Minikube</span></span>

<span data-ttu-id="2f5ae-209">什麼是米尼庫貝?</span><span class="sxs-lookup"><span data-stu-id="2f5ae-209">What is Minikube?</span></span> <span data-ttu-id="2f5ae-210">Minikube 專案說:「Minikube 在 macOS、Linux 和 Windows 上實現了本地 Kubernetes 群集。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-210">The Minikube project says "Minikube implements a local Kubernetes cluster on macOS, Linux, and Windows."</span></span> <span data-ttu-id="2f5ae-211">其主要目標是"成為本地Kubernetes應用程式開發的最佳工具,並支援所有適合的Kubernetes功能。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-211">Its primary goals are "to be the best tool for local Kubernetes application development and to support all Kubernetes features that fit."</span></span> <span data-ttu-id="2f5ae-212">安裝 Minikube 與 Docker 是分開的,但 Minikube 支援與 Docker 桌面支援不同的虛擬機器管理程式。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-212">Installing Minikube is separate from Docker, but Minikube supports different hypervisors than Docker Desktop supports.</span></span> <span data-ttu-id="2f5ae-213">Minikube 目前支援以下庫伯奈斯功能:</span><span class="sxs-lookup"><span data-stu-id="2f5ae-213">The following Kubernetes features are currently supported by Minikube:</span></span>

- <span data-ttu-id="2f5ae-214">DNS</span><span class="sxs-lookup"><span data-stu-id="2f5ae-214">DNS</span></span>
- <span data-ttu-id="2f5ae-215">節點連接埠</span><span class="sxs-lookup"><span data-stu-id="2f5ae-215">NodePorts</span></span>
- <span data-ttu-id="2f5ae-216">設定對應及機密</span><span class="sxs-lookup"><span data-stu-id="2f5ae-216">ConfigMaps and secrets</span></span>
- <span data-ttu-id="2f5ae-217">儀表板</span><span class="sxs-lookup"><span data-stu-id="2f5ae-217">Dashboards</span></span>
- <span data-ttu-id="2f5ae-218">容器執行時:碼頭、rkt、CRI-O 和容器</span><span class="sxs-lookup"><span data-stu-id="2f5ae-218">Container runtimes: Docker, rkt, CRI-O, and containerd</span></span>
- <span data-ttu-id="2f5ae-219">開啟容器網路介面 (CNI)</span><span class="sxs-lookup"><span data-stu-id="2f5ae-219">Enabling Container Network Interface (CNI)</span></span>
- <span data-ttu-id="2f5ae-220">輸入</span><span class="sxs-lookup"><span data-stu-id="2f5ae-220">Ingress</span></span>

<span data-ttu-id="2f5ae-221">安裝 Minikube 後,`minikube start`可以通過運行 命令快速開始使用它,該命令下載映射並啟動本地 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-221">After installing Minikube, you can quickly start using it by running the `minikube start` command, which downloads an image and start the local Kubernetes cluster.</span></span> <span data-ttu-id="2f5ae-222">群集啟動后,您將使用標準的 Kubernetes`kubectl`命令與其交互。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-222">Once the cluster is started, you interact with it using the standard Kubernetes `kubectl` commands.</span></span>

### <a name="docker-desktop"></a><span data-ttu-id="2f5ae-223">Docker Desktop</span><span class="sxs-lookup"><span data-stu-id="2f5ae-223">Docker Desktop</span></span>

<span data-ttu-id="2f5ae-224">您還可以直接從 Windows 上的 Docker 桌面使用 Kubernetes。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-224">You can also work with Kubernetes directly from Docker Desktop on Windows.</span></span> <span data-ttu-id="2f5ae-225">如果您使用的是 Windows 容器,這是您唯一的選擇,也是非 Windows 容器的絕佳選擇。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-225">This is your only option if you're using Windows Containers, and is a great choice for non-Windows containers as well.</span></span> <span data-ttu-id="2f5ae-226">標準 Docker 桌面設定應用用於設定從 Docker 桌面執行的庫伯內特。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-226">The standard Docker Desktop configuration app is used to configure Kubernetes running from Docker Desktop.</span></span>

![Docker 桌面中設定庫伯內斯](./media/docker-desktop-kubernetes.png)

<span data-ttu-id="2f5ae-228">**圖3-4**。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-228">**Figure 3-4**.</span></span> <span data-ttu-id="2f5ae-229">在 Docker 桌面中配置庫伯內斯。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-229">Configuring Kubernetes in Docker Desktop.</span></span>

<span data-ttu-id="2f5ae-230">Docker 桌面已經是本地配置和運行容器化應用的最常見工具。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-230">Docker Desktop is already the most popular tool for configuring and running containerized apps locally.</span></span> <span data-ttu-id="2f5ae-231">使用 Docker Desktop 時,可以針對要部署到生產的完全相同的 Docker 容器映射集在本地進行開發。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-231">When you work with Docker Desktop, you can develop locally against the exact same set of Docker container images that you'll deploy to production.</span></span> <span data-ttu-id="2f5ae-232">Docker 桌面旨在"在本地構建、測試和發貨"容器化應用。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-232">Docker Desktop is designed to "build, test, and ship" containerized apps locally.</span></span> <span data-ttu-id="2f5ae-233">將映射發送到映像註冊表(如 Azure 容器註冊表或 Docker Hub)後,Azure Kubernetes 服務 (AKS) 等服務將管理生產中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-233">Once the images have been shipped to an image registry like Azure Container Registry or Docker Hub, then services like Azure Kubernetes Service (AKS) manage the application in production.</span></span>

### <a name="visual-studio-docker-tooling"></a><span data-ttu-id="2f5ae-234">視覺工作室碼頭工具</span><span class="sxs-lookup"><span data-stu-id="2f5ae-234">Visual Studio Docker Tooling</span></span>

<span data-ttu-id="2f5ae-235">Visual Studio 支援 Web 應用程式的 Docker 開發。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-235">Visual Studio supports Docker development for web applications.</span></span> <span data-ttu-id="2f5ae-236">建立新的ASP.NET核心應用程式時,您可以選擇使用 Docker 支援來設定該應用程式,作為專案創建過程的一部分,如圖 3-5 所示。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-236">When you create a new ASP.NET Core application, you're given the option to configure it with Docker support as part of the project creation process, as shown in Figure 3-5.</span></span>

![視覺化工作室啟用 Docker 支援](./media/visual-studio-enable-docker-support.png)

<span data-ttu-id="2f5ae-238">**圖3-5**。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-238">**Figure 3-5**.</span></span> <span data-ttu-id="2f5ae-239">視覺化工作室啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="2f5ae-239">Visual Studio Enable Docker Support</span></span>

<span data-ttu-id="2f5ae-240">選擇此選項後,將使用 root`Dockerfile`中的專案創建專案,可用於在 Docker 容器中生成和託管應用。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-240">When this option is selected, the project is created with a `Dockerfile` in its root, which can be used to build and host the app in a Docker container.</span></span> <span data-ttu-id="2f5ae-241">如圖 3-6 所示有一個範例 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-241">An example Dockerfile is shown in Figure 3-6.</span></span>

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-stretch AS build
WORKDIR /src
COPY ["WebApplication3/WebApplication3.csproj", "WebApplication3/"]
RUN dotnet restore "WebApplication3/WebApplication3.csproj"
COPY . .
WORKDIR "/src/WebApplication3"
RUN dotnet build "WebApplication3.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication3.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication3.dll"]
```

<span data-ttu-id="2f5ae-242">**圖3-6**.</span><span class="sxs-lookup"><span data-stu-id="2f5ae-242">**Figure 3-6**.</span></span> <span data-ttu-id="2f5ae-243">視覺化工作室產生的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="2f5ae-243">Visual Studio generated Dockerfile</span></span>

<span data-ttu-id="2f5ae-244">應用執行時的預設行為也配置為使用 Docker。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-244">The default behavior when the app runs is configured to use Docker as well.</span></span> <span data-ttu-id="2f5ae-245">圖 3-7 顯示了添加了 Docker 支援後創建的新ASP.NET核心專案中可用的不同運行選項。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-245">Figure 3-7 shows the different run options available from a new ASP.NET Core project created with Docker support added.</span></span>

![視覺化工作室 Docker 執行選項](./media/visual-studio-docker-run-options.png)

<span data-ttu-id="2f5ae-247">**圖3-7**。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-247">**Figure 3-7**.</span></span> <span data-ttu-id="2f5ae-248">視覺化工作室 Docker 執行選項</span><span class="sxs-lookup"><span data-stu-id="2f5ae-248">Visual Studio Docker Run Options</span></span>

<span data-ttu-id="2f5ae-249">除了本地開發之外[,Azure 開發人員空間](https://docs.microsoft.com/azure/dev-spaces/)還為多個開發人員提供了一種在 Azure 中處理其自己的 Kubernets 配置的便捷方法。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-249">In addition to local development, [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) provides a convenient way for multiple developers to work with their own Kubernetes configurations within Azure.</span></span> <span data-ttu-id="2f5ae-250">如圖 3-7 所示,您還可以在 Azure 開發空間中運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-250">As you can see in Figure 3-7, you can also run the application in Azure Dev Spaces.</span></span>

<span data-ttu-id="2f5ae-251">如果在創建ASP.NET酷應用程式時未將 Docker 支援添加到該應用程式,則始終可以在以後添加它。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-251">If you don't add Docker support to your ASP.NET Core application when you create it, you can always add it later.</span></span> <span data-ttu-id="2f5ae-252">在可視化工作室解決方案資源管理器中,右鍵單擊專案並選擇 **「添加** > **Docker 支援**」,如圖 3-8 所示。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-252">From the Visual Studio Solution Explorer, right click on the project and select **Add** > **Docker Support**, as shown in Figure 3-8.</span></span>

![視覺化工作室加入 Docker 支援](./media/visual-studio-add-docker-support.png)

<span data-ttu-id="2f5ae-254">**圖3-8**。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-254">**Figure 3-8**.</span></span> <span data-ttu-id="2f5ae-255">視覺化工作室加入 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="2f5ae-255">Visual Studio Add Docker Support</span></span>

<span data-ttu-id="2f5ae-256">除了 Docker 支援之外,您還可以添加容器業務流程支援,如圖 3-8 所示。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-256">In addition to Docker support, you can also add Container Orchestration Support, also shown in Figure 3-8.</span></span> <span data-ttu-id="2f5ae-257">默認情況下,協調器使用庫伯奈斯和赫爾姆。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-257">By default, the orchestrator uses Kubernetes and Helm.</span></span> <span data-ttu-id="2f5ae-258">選擇協調器後,將`azds.yaml`檔添加到專案根,並添加一個`charts`資料夾,其中包含用於配置應用程式並將應用程式部署到 Kubernetes 的 Helm 圖表。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-258">Once you've chosen the orchestrator, a `azds.yaml` file is added to the project root and a `charts` folder is added containing the Helm charts used to configure and deploy the application to Kubernetes.</span></span> <span data-ttu-id="2f5ae-259">圖 3-9 顯示了新專案中生成的檔。</span><span class="sxs-lookup"><span data-stu-id="2f5ae-259">Figure 3-9 shows the resulting files in a new project.</span></span>

![視覺化工作室新增協調器支援](./media/visual-studio-add-orchestrator-support.png)

<span data-ttu-id="2f5ae-261">**圖3-9**.</span><span class="sxs-lookup"><span data-stu-id="2f5ae-261">**Figure 3-9**.</span></span> <span data-ttu-id="2f5ae-262">視覺化工作室新增協調器支援</span><span class="sxs-lookup"><span data-stu-id="2f5ae-262">Visual Studio Add Orchestrator Support</span></span>

## <a name="references"></a><span data-ttu-id="2f5ae-263">參考</span><span class="sxs-lookup"><span data-stu-id="2f5ae-263">References</span></span>

- [<span data-ttu-id="2f5ae-264">什麼是 Kubernetes？</span><span class="sxs-lookup"><span data-stu-id="2f5ae-264">What is Kubernetes?</span></span>](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [<span data-ttu-id="2f5ae-265">安裝庫伯內斯與米尼庫貝</span><span class="sxs-lookup"><span data-stu-id="2f5ae-265">Installing Kubernetes with Minikube</span></span>](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [<span data-ttu-id="2f5ae-266">迷你庫貝 vs Docker 桌面</span><span class="sxs-lookup"><span data-stu-id="2f5ae-266">MiniKube vs Docker Desktop</span></span>](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [<span data-ttu-id="2f5ae-267">Visual Studio Tools for Docker</span><span class="sxs-lookup"><span data-stu-id="2f5ae-267">Visual Studio Tools for Docker</span></span>](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
><span data-ttu-id="2f5ae-268">[前一個](scale-applications.md)
>[下一個](leverage-serverless-functions.md)</span><span class="sxs-lookup"><span data-stu-id="2f5ae-268">[Previous](scale-applications.md)
[Next](leverage-serverless-functions.md)</span></span>
