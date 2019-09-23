---
title: 利用容器和協調器
description: 在 Azure 中利用 Docker 容器和 Kubernetes 協調器
ms.date: 06/30/2019
ms.openlocfilehash: 4008a14e4db28e07d5fda0a1f175aada9ffe6734
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182878"
---
# <a name="leveraging-containers-and-orchestrators"></a><span data-ttu-id="ed7e9-103">利用容器和協調器</span><span class="sxs-lookup"><span data-stu-id="ed7e9-103">Leveraging containers and orchestrators</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ed7e9-104">容器和協調器的設計是為了解決整合型部署方法常見的問題。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-104">Containers and orchestrators are designed to solve problems common to monolithic deployment approaches.</span></span>

## <a name="challenges-with-monolithic-deployments"></a><span data-ttu-id="ed7e9-105">整合型部署的挑戰</span><span class="sxs-lookup"><span data-stu-id="ed7e9-105">Challenges with monolithic deployments</span></span>

<span data-ttu-id="ed7e9-106">傳統上，大部分的應用程式都已部署為單一單位。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-106">Traditionally, most applications have been deployed as a single unit.</span></span> <span data-ttu-id="ed7e9-107">這類應用程式稱為單體。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-107">Such applications are referred to as a monolith.</span></span> <span data-ttu-id="ed7e9-108">這種將應用程式部署為單一單位的一般方法，即使它們是由多個模組或元件所組成，也稱為整合型架構，如圖3-1 所示。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-108">This general approach of deploying applications as single units even if they're composed of multiple modules or assemblies is known as monolithic architecture, as shown in Figure 3-1.</span></span>

![整合型架構。](./media/monolithic-architecture.png)

<span data-ttu-id="ed7e9-110">**圖 3-1**。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-110">**Figure 3-1**.</span></span> <span data-ttu-id="ed7e9-111">整合型架構。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-111">Monolithic architecture.</span></span>

<span data-ttu-id="ed7e9-112">雖然它們具有簡單的優點，但是整合型架構也面臨一些挑戰：</span><span class="sxs-lookup"><span data-stu-id="ed7e9-112">Although they have the benefit of simplicity, monolithic architectures face a number of challenges:</span></span>

### <a name="deployments"></a><span data-ttu-id="ed7e9-113">部署</span><span class="sxs-lookup"><span data-stu-id="ed7e9-113">Deployments</span></span>

<span data-ttu-id="ed7e9-114">部署到整合型應用程式通常需要重新開機整個應用程式，即使只更換一個小模組也一樣。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-114">Deploying to monolithic applications typically requires restarting the entire application, even if only one small module is being replaced.</span></span> <span data-ttu-id="ed7e9-115">視裝載應用程式的機器數目而定，這可能會導致部署期間的停機時間。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-115">Depending on the number of machines hosting the application, this can result in downtime during deployments.</span></span>

### <a name="hosting"></a><span data-ttu-id="ed7e9-116">裝載</span><span class="sxs-lookup"><span data-stu-id="ed7e9-116">Hosting</span></span>

<span data-ttu-id="ed7e9-117">整合型應用程式完全裝載于單一機器實例上。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-117">Monolithic applications are hosted entirely on a single machine instance.</span></span> <span data-ttu-id="ed7e9-118">這可能需要更高功能的硬體，而不是分散式應用程式所需的任何模組。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-118">This may require higher-capability hardware than any module in a distributed application would need.</span></span> <span data-ttu-id="ed7e9-119">此外，如果應用程式有任何部分變成瓶頸，則整個應用程式必須部署到其他電腦節點，才能相應放大。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-119">Also, if any part of the app becomes a bottleneck, the entire application must be deployed to additional machine nodes in order to scale out.</span></span>

### <a name="environment"></a><span data-ttu-id="ed7e9-120">環境</span><span class="sxs-lookup"><span data-stu-id="ed7e9-120">Environment</span></span>

<span data-ttu-id="ed7e9-121">整合型應用程式通常會部署到現有的裝載環境（作業系統、已安裝的架構等）。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-121">Monolithic applications are typically deployed into an existing hosting environment (operating system, installed frameworks, etc.).</span></span> <span data-ttu-id="ed7e9-122">此環境可能不符合開發或測試應用程式的環境。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-122">This environment may not match the environment in which the application was developed or tested.</span></span> <span data-ttu-id="ed7e9-123">應用程式環境中的不一致是整合型部署問題的常見來源。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-123">Inconsistencies in the application's environment are a common source of problems for monolithic deployments.</span></span>

### <a name="coupling"></a><span data-ttu-id="ed7e9-124">緊密</span><span class="sxs-lookup"><span data-stu-id="ed7e9-124">Coupling</span></span>

<span data-ttu-id="ed7e9-125">整合型應用程式的不同元件之間，以及應用程式與其環境之間，可能會有很多的結合。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-125">Monolithic applications are likely to have a great deal of coupling between different parts of the application, and between the application and its environment.</span></span> <span data-ttu-id="ed7e9-126">這可能會使它難以分解特定的服務，或在稍後考慮，以便增加其擴充性或交換替代的執行方式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-126">This can make it difficult to factor out a particular service or concern later, in order to increase its scalability or swap in an alternative implementation.</span></span> <span data-ttu-id="ed7e9-127">這種結合也會導致對系統變更有更大的潛在影響，需要在較大型的應用程式中進行大量測試。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-127">This coupling also leads to much larger potential impacts for changes to the system, requiring extensive testing in larger applications.</span></span>

### <a name="technology-choice"></a><span data-ttu-id="ed7e9-128">技術選擇</span><span class="sxs-lookup"><span data-stu-id="ed7e9-128">Technology choice</span></span>

<span data-ttu-id="ed7e9-129">整合型應用程式會建立並部署為一個單位。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-129">Monolithic applications are built and deployed as a unit.</span></span> <span data-ttu-id="ed7e9-130">這提供簡化和一致性，但可能是創新的障礙。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-130">This offers simplicity and uniformity but can be a barrier to innovation.</span></span> <span data-ttu-id="ed7e9-131">雖然系統中的新功能或模組可能較適合較新式的平臺或架構，但可能會使用應用程式目前的方法來建立，以達成一致性以及輕鬆的開發和部署。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-131">Although a new feature or module in the system might be better-suited to a more modern platform or framework, it's likely to be built using the application's current approach for the sake of consistency as well as ease of development and deployment.</span></span>

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a><span data-ttu-id="ed7e9-132">容器和協調器的優點為何？</span><span class="sxs-lookup"><span data-stu-id="ed7e9-132">What are the benefits of containers and orchestrators?</span></span>

<span data-ttu-id="ed7e9-133">Docker 是最受歡迎的容器管理和映射處理平臺，可讓您快速使用 Linux 和 Windows 上的容器。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-133">Docker is the most popular container management and imaging platform and allows you to quickly work with containers on Linux and Windows.</span></span> <span data-ttu-id="ed7e9-134">容器提供不同但可重現的應用程式環境，在任何系統上執行相同的方式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-134">Containers provide separate but reproducible application environments that run the same way on any system.</span></span> <span data-ttu-id="ed7e9-135">這讓它們適合用來在雲端原生應用程式中開發和裝載應用程式和應用程式元件。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-135">This makes them perfect for developing and hosting applications and app components in cloud-native applications.</span></span> <span data-ttu-id="ed7e9-136">容器會彼此隔離，因此相同主機硬體上的兩個容器可以有不同版本的軟體，甚至是安裝作業系統，而不會造成衝突。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-136">Containers are isolated from one another, so two containers on the same host hardware can have different versions of software and even operating system installed, without the dependencies causing conflicts.</span></span>

<span data-ttu-id="ed7e9-137">更多的是，容器是由可簽入原始檔控制的簡單檔案所定義。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-137">What’s more, containers are defined by simple files that can be checked into source control.</span></span> <span data-ttu-id="ed7e9-138">不同于完整伺服器，甚至是虛擬機器，通常需要手動執行工作來套用更新或安裝其他服務，容器基礎結構很容易受到版本控制。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-138">Unlike full servers, even virtual machines, which frequently require manual work to apply updates or install additional services, container infrastructure can easily be version-controlled.</span></span> <span data-ttu-id="ed7e9-139">因此，建立在容器中執行的應用程式可以使用自動化工具來進行開發、測試及部署，以作為組建管線的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-139">Thus, apps built to run in containers can be developed, tested, and deployed using automated tools as part of a build pipeline.</span></span>

<span data-ttu-id="ed7e9-140">容器是不可變的。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-140">Containers are immutable.</span></span> <span data-ttu-id="ed7e9-141">一旦有了容器的定義，您就可以重新建立該容器，而且它會以完全相同的方式執行。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-141">Once you have the definition of a container, you can recreate that container and it will run exactly the same way.</span></span> <span data-ttu-id="ed7e9-142">這種不會將其本身用於以元件為基礎的設計。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-142">This immutability lends itself to component-based design.</span></span> <span data-ttu-id="ed7e9-143">如果應用程式的某些部分不會經常變更，當您可以直接部署最常變更的元件時，為什麼要重新部署整個應用程式？</span><span class="sxs-lookup"><span data-stu-id="ed7e9-143">If some parts of an application don’t change as often as others, why redeploy the entire app when you can just deploy the parts that change most frequently?</span></span> <span data-ttu-id="ed7e9-144">應用程式的不同功能和跨領域考慮可能會分成不同的單位。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-144">Different features and cross-cutting concerns of an app can be broken up into separate units.</span></span> <span data-ttu-id="ed7e9-145">圖3-2 顯示單一應用程式如何藉由委派特定的功能來利用容器和微服務。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-145">Figure 3-2 shows how a monolithic app can take advantage of containers and microservices by delegating certain features or functionality.</span></span> <span data-ttu-id="ed7e9-146">應用程式本身的其餘功能也已容器化。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-146">The remaining functionality in the app itself has also been containerized.</span></span>

<span data-ttu-id="ed7e9-147">![將整合型應用程式分解成在後端使用微服務。**圖 3-2**。 ](./media/breaking-up-monolith-with-backend-microservices.png)
</span><span class="sxs-lookup"><span data-stu-id="ed7e9-147">![Breaking up a monolithic app to use microservices in the back end.](./media/breaking-up-monolith-with-backend-microservices.png)
**Figure 3-2**.</span></span> <span data-ttu-id="ed7e9-148">將整合型應用程式分解成在後端使用微服務。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-148">Breaking up a monolithic app to use microservices in the back end.</span></span>

<span data-ttu-id="ed7e9-149">使用個別容器所建立的雲端原生應用程式，可讓您視需要部署最多或最少的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-149">Cloud-native apps built using separate containers benefit from the ability to deploy as much or as little of an application as needed.</span></span> <span data-ttu-id="ed7e9-150">個別服務可以裝載于節點上，並具有適用于每個服務的資源。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-150">Individual services can be hosted on nodes with resources appropriate to each service.</span></span> <span data-ttu-id="ed7e9-151">在中執行的每個服務都是不可變的，可以在開發、測試和生產環境之間共用，而且可以輕鬆地進行版本設定。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-151">The environment each service runs in is immutable, can be shared between dev, test, and production, and can easily be versioned.</span></span> <span data-ttu-id="ed7e9-152">應用程式的不同區域之間的結合，會明確成為服務之間的呼叫或訊息，而不是單體內的編譯時間相依性。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-152">Coupling between different areas of the application occurs explicitly as calls or messages between services, not compile-time dependencies within the monolith.</span></span> <span data-ttu-id="ed7e9-153">整體應用程式的任何特定部分都可以選擇最適合該功能或功能的技術，而不需要變更應用程式的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-153">And any given part of the overall app can choose the technology that makes the most sense for that feature or capability without requiring changes to the rest of the app.</span></span>

## <a name="what-are-the-scaling-benefits"></a><span data-ttu-id="ed7e9-154">什麼是調整優點？</span><span class="sxs-lookup"><span data-stu-id="ed7e9-154">What are the scaling benefits?</span></span>

<span data-ttu-id="ed7e9-155">以容器為基礎的服務可以利用協調流程工具（例如 Kubernetes）所提供的調整優勢。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-155">Services built on containers can leverage scaling benefits provided by orchestration tools like Kubernetes.</span></span> <span data-ttu-id="ed7e9-156">根據設計，容器只知道自己的關係。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-156">By design containers only know about themselves.</span></span> <span data-ttu-id="ed7e9-157">一旦您開始有多個需要共同作業的容器，就可以在較高的層級進行組織。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-157">Once you start to have multiple containers that need to work together, it can be worthwhile to organize them at a higher level.</span></span> <span data-ttu-id="ed7e9-158">組織大量的容器及其共用的相依性（例如網路設定）就是協調流程工具的儲存時間！</span><span class="sxs-lookup"><span data-stu-id="ed7e9-158">Organizing large numbers of containers and their shared dependencies, such as network configuration, is where orchestration tools come in to save the day!</span></span> <span data-ttu-id="ed7e9-159">Kubernetes 是一種容器協調流程平臺，專門設計來自動化部署、調整和管理容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-159">Kubernetes is a container orchestration platform designed to automate deployment, scaling, and management of containerized applications.</span></span> <span data-ttu-id="ed7e9-160">它會在容器群組之上建立抽象層，並將其*組織成 pod*。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-160">It creates an abstraction layer on top of groups of containers and organizes them into *pods*.</span></span> <span data-ttu-id="ed7e9-161">Pod 會在稱為*節點*的工作者機器上執行。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-161">Pods run on worker machines referred to as *nodes*.</span></span> <span data-ttu-id="ed7e9-162">整個組織的群組稱為「叢集」（ *cluster*）。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-162">The whole organized group is referred to as a *cluster*.</span></span> <span data-ttu-id="ed7e9-163">圖3-3 顯示 Kubernetes 叢集的不同元件。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-163">Figure 3-3 shows the different components of a Kubernetes cluster.</span></span>

<span data-ttu-id="ed7e9-164">![Kubernetes 叢集元件。**圖 3-3**。 ](./media/kubernetes-cluster-components.png)
</span><span class="sxs-lookup"><span data-stu-id="ed7e9-164">![Kubernetes cluster components.](./media/kubernetes-cluster-components.png)
**Figure 3-3**.</span></span> <span data-ttu-id="ed7e9-165">Kubernetes 叢集元件。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-165">Kubernetes cluster components.</span></span>

<span data-ttu-id="ed7e9-166">Kubernetes 有內建支援，可調整叢集以符合需求。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-166">Kubernetes has built-in support for scaling clusters to meet demand.</span></span> <span data-ttu-id="ed7e9-167">相較于容器化微服務，這可讓雲端原生應用程式能夠快速且有效率地回應需求尖峰，並在需要時使用其他資源。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-167">Combined with containerized micro-services, this provides cloud-native applications with the ability to quickly and efficiently respond to spikes in demand with additional resources when and where they're needed.</span></span>

### <a name="declarative-versus-imperative"></a><span data-ttu-id="ed7e9-168">宣告式與命令式</span><span class="sxs-lookup"><span data-stu-id="ed7e9-168">Declarative versus imperative</span></span>

<span data-ttu-id="ed7e9-169">Kubernetes 支援宣告式和命令式物件設定。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-169">Kubernetes supports both declarative and imperative object configuration.</span></span> <span data-ttu-id="ed7e9-170">命令式方法牽涉到執行各種命令，告訴 Kubernetes 該怎麼做的每個步驟。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-170">The imperative approach involves running various commands that tell Kubernetes what to do each step of the way.</span></span> <span data-ttu-id="ed7e9-171">*執行*此映射。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-171">*Run* this image.</span></span> <span data-ttu-id="ed7e9-172">*刪除*此 pod。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-172">*Delete* this pod.</span></span> <span data-ttu-id="ed7e9-173">*公開*此埠。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-173">*Expose* this port.</span></span> <span data-ttu-id="ed7e9-174">使用宣告式方法時，您可以使用設定檔來描述*您想要的內容*，而不是*要執行*的動作，並 Kubernetes 瞭解要怎麼做才能達成所要的結束狀態。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-174">With the declarative approach, you use a configuration file that describes *what you want* instead of *what to do* and Kubernetes figures out what to do to achieve the desired end state.</span></span> <span data-ttu-id="ed7e9-175">如果您已經使用命令式命令來設定您的叢集，您可以使用`kubectl get svc SERVICENAME -o yaml > service.yaml`來匯出宣告式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-175">If you've already configured your cluster using imperative commands, you can export a declarative manifest by using `kubectl get svc SERVICENAME -o yaml > service.yaml`.</span></span> <span data-ttu-id="ed7e9-176">這會產生資訊清單檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ed7e9-176">This will produce a manifest file like this one:</span></span>

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

<span data-ttu-id="ed7e9-177">使用宣告式設定時，您可以使用`kubectl diff -f FOLDERNAME` ，針對設定檔所在的資料夾，先預覽將進行的變更。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-177">When using declarative configuration, you can preview the changes that will be made before committing them by using `kubectl diff -f FOLDERNAME` against the folder where your configuration files are located.</span></span> <span data-ttu-id="ed7e9-178">一旦您確定要套用變更，請執行`kubectl apply -f FOLDERNAME`。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-178">Once you're sure you want to apply the changes, run `kubectl apply -f FOLDERNAME`.</span></span> <span data-ttu-id="ed7e9-179">新增`-R`以遞迴方式處理資料夾階層。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-179">Add `-R` to recursively process a folder hierarchy.</span></span>

<span data-ttu-id="ed7e9-180">除了服務以外，您還可以針對其他 Kubernetes 功能（例如*部署*）使用宣告式設定。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-180">In addition to services, you can use declarative configuration for other Kubernetes features, such as *deployments*.</span></span> <span data-ttu-id="ed7e9-181">部署控制器會使用宣告式部署來更新叢集資源。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-181">Declarative deployments are used by deployment controllers to update cluster resources.</span></span> <span data-ttu-id="ed7e9-182">部署是用來推出新的變更、相應增加以支援更多負載，或復原到先前的修訂版本。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-182">Deployments are used to roll out new changes, scale up to support more load, or roll back to a previous revision.</span></span> <span data-ttu-id="ed7e9-183">如果叢集不穩定，宣告式部署會提供一種機制，讓叢集自動復原成所需的狀態。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-183">If a cluster is unstable, declarative deployments provide a mechanism for automatically bringing the cluster back to a desired state.</span></span>

<span data-ttu-id="ed7e9-184">使用宣告式設定可讓基礎結構以程式碼的形式來表示，並可簽入和設定版本。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-184">Using declarative configuration allows infrastructure to be represented as code that can be checked in and versioned alongside the application code.</span></span> <span data-ttu-id="ed7e9-185">這可讓您使用組建和部署管線（系結至原始檔控制變更）來改善持續部署的變更控制和更好的支援。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-185">This provides improved change control and better support for continuous deployment using a build and deploy pipeline tied to source control changes.</span></span>

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a><span data-ttu-id="ed7e9-186">什麼是適用于容器和協調器的案例？</span><span class="sxs-lookup"><span data-stu-id="ed7e9-186">What scenarios are ideal for containers and orchestrators?</span></span>

<span data-ttu-id="ed7e9-187">下列案例適用于使用容器和協調器。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-187">The following scenarios are ideal for using containers and orchestrators.</span></span>

### <a name="applications-requiring-high-uptime-and-scalability"></a><span data-ttu-id="ed7e9-188">需要高執行時間和擴充性的應用程式</span><span class="sxs-lookup"><span data-stu-id="ed7e9-188">Applications requiring high uptime and scalability</span></span>

<span data-ttu-id="ed7e9-189">具有高執行時間和擴充性需求的個別應用程式，是使用微服務、容器和協調器之雲端原生架構的理想候選項目。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-189">Individual applications that have high uptime and scalability requirements are ideal candidates for cloud-native architectures using microservices, containers, and orchestrators.</span></span> <span data-ttu-id="ed7e9-190">這些應用程式可以在使用已建立版本環境的容器中開發，可以在進入生產階段之前進行廣泛的測試，而且可以部署到生產環境，而不會發生任何停機時間。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-190">These applications can be developed in containers using versioned environments, can be extensively tested before going to production, and can be deployed to production with zero downtime.</span></span> <span data-ttu-id="ed7e9-191">使用 Kubernetes 叢集可確保這類應用程式也可以根據需求進行調整，並自動從節點失敗中復原。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-191">The use of Kubernetes clusters ensures such apps can also scale on demand and recover automatically from node failures.</span></span>

### <a name="large-numbers-of-applications"></a><span data-ttu-id="ed7e9-192">大量應用程式</span><span class="sxs-lookup"><span data-stu-id="ed7e9-192">Large numbers of applications</span></span>

<span data-ttu-id="ed7e9-193">部署和之後必須維護大量應用程式的組織，可從容器和協調器獲益。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-193">Organizations that deploy and must subsequently maintain large numbers of applications benefit from containers and orchestrators.</span></span> <span data-ttu-id="ed7e9-194">設定容器化環境和 Kubernetes 叢集的前期工作，主要是固定成本。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-194">The up front effort of setting up containerized environments and Kubernetes clusters is primarily a fixed cost.</span></span> <span data-ttu-id="ed7e9-195">部署、維護和更新個別應用程式的成本，會因必須維護的應用程式數目而異。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-195">Deploying, maintaining, and updating individual applications has a cost that varies with the number of applications that must be maintained.</span></span> <span data-ttu-id="ed7e9-196">除了特定相當少的應用程式，維護自訂應用程式的複雜性也超出了使用容器和協調器來執行解決方案的成本。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-196">Beyond a certain fairly small number of applications, the complexity of maintaining custom applications manually exceeds the cost of implementing a solution using containers and orchestrators.</span></span>

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a><span data-ttu-id="ed7e9-197">何時應避免使用容器和協調器？</span><span class="sxs-lookup"><span data-stu-id="ed7e9-197">When should you avoid using containers and orchestrators?</span></span>

<span data-ttu-id="ed7e9-198">如果您不願意或無法遵循12因素應用程式原則來建立應用程式，您可能會更有效地避免容器和協調器。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-198">If you're unwilling or unable to build your application following Twelve-Factor App principles, you'll probably be better off avoiding containers and orchestrators.</span></span> <span data-ttu-id="ed7e9-199">在這些情況下，最好是使用以 VM 為基礎的裝載平臺，或可能是一些混合式系統，您可以在其中將特定功能關閉到個別容器或甚至無伺服器功能。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-199">In these cases, it may be best to move forward with a VM-based hosting platform, or possibly some hybrid system in which you can spin off certain pieces of functionality into separate containers or even serverless functions.</span></span> 

## <a name="development-resources"></a><span data-ttu-id="ed7e9-200">開發資源</span><span class="sxs-lookup"><span data-stu-id="ed7e9-200">Development resources</span></span>

<span data-ttu-id="ed7e9-201">本節顯示的開發資源簡短清單，可協助您開始使用容器和協調器來進行下一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-201">This section shows a short list of development resources that may help you get started using containers and orchestrators for your next application.</span></span> <span data-ttu-id="ed7e9-202">如果您要尋找如何設計雲端原生微服務架構應用程式的指引，請閱讀這本書的[.net 微服務：容器化 .NET 應用程式的架構](https://aka.ms/microservicesebook)。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-202">If you're looking for guidance on how to design your cloud-native microservices architecture app, read this book's companion, [.NET Microservices: Architecture for Containerized .NET Applications](https://aka.ms/microservicesebook).</span></span>

### <a name="local-kubernetes-development"></a><span data-ttu-id="ed7e9-203">本機 Kubernetes 開發</span><span class="sxs-lookup"><span data-stu-id="ed7e9-203">Local Kubernetes Development</span></span>

<span data-ttu-id="ed7e9-204">Kubernetes 部署在生產環境中提供絕佳價值，但您也可以在本機執行。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-204">Kubernetes deployments provide great value in production environments, but you can also run them locally.</span></span> <span data-ttu-id="ed7e9-205">雖然大部分的時間都可以單獨處理個別應用程式或微服務，但有時最好能夠在本機執行整個系統，就像是部署到生產環境時執行的一樣。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-205">Although much of the time it's good to be able to work on individual apps or microservices independently, sometimes it's good to be able to run the whole system locally just as it will run when deployed to production.</span></span> <span data-ttu-id="ed7e9-206">有幾種方式可以達到這個目的，其中兩個是 Minikube 和 Docker Desktop。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-206">There are several ways to achieve this, two of which are Minikube and Docker Desktop.</span></span> <span data-ttu-id="ed7e9-207">Visual Studio 也提供 Docker 開發的工具。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-207">Visual Studio also provides tooling for Docker development.</span></span>

### <a name="minikube"></a><span data-ttu-id="ed7e9-208">Minikube</span><span class="sxs-lookup"><span data-stu-id="ed7e9-208">Minikube</span></span>

<span data-ttu-id="ed7e9-209">什麼是 Minikube？</span><span class="sxs-lookup"><span data-stu-id="ed7e9-209">What is Minikube?</span></span> <span data-ttu-id="ed7e9-210">Minikube 專案指出「Minikube 在 macOS、Linux 和 Windows 上執行本機 Kubernetes 叢集」。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-210">The Minikube project says "Minikube implements a local Kubernetes cluster on macOS, Linux, and Windows."</span></span> <span data-ttu-id="ed7e9-211">其主要目標是「作為本機 Kubernetes 應用程式開發的最佳工具，並支援所有符合的 Kubernetes 功能」。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-211">Its primary goals are "to be the best tool for local Kubernetes application development and to support all Kubernetes features that fit."</span></span> <span data-ttu-id="ed7e9-212">安裝 Minikube 與 Docker 分開，但是 Minikube 支援不同于 Docker Desktop 支援的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-212">Installing Minikube is separate from Docker, but Minikube supports different hypervisors than Docker Desktop supports.</span></span> <span data-ttu-id="ed7e9-213">Minikube 目前支援下列 Kubernetes 功能：</span><span class="sxs-lookup"><span data-stu-id="ed7e9-213">The following Kubernetes features are currently supported by Minikube:</span></span>

- <span data-ttu-id="ed7e9-214">DNS</span><span class="sxs-lookup"><span data-stu-id="ed7e9-214">DNS</span></span>
- <span data-ttu-id="ed7e9-215">NodePorts</span><span class="sxs-lookup"><span data-stu-id="ed7e9-215">NodePorts</span></span>
- <span data-ttu-id="ed7e9-216">ConfigMaps 和秘密</span><span class="sxs-lookup"><span data-stu-id="ed7e9-216">ConfigMaps and secrets</span></span>
- <span data-ttu-id="ed7e9-217">儀表板</span><span class="sxs-lookup"><span data-stu-id="ed7e9-217">Dashboards</span></span>
- <span data-ttu-id="ed7e9-218">容器執行時間：Docker、rkt、CRI 和 containerd</span><span class="sxs-lookup"><span data-stu-id="ed7e9-218">Container runtimes: Docker, rkt, CRI-O, and containerd</span></span>
- <span data-ttu-id="ed7e9-219">啟用容器網路介面（CNI）</span><span class="sxs-lookup"><span data-stu-id="ed7e9-219">Enabling Container Network Interface (CNI)</span></span>
- <span data-ttu-id="ed7e9-220">站</span><span class="sxs-lookup"><span data-stu-id="ed7e9-220">Ingress</span></span>

<span data-ttu-id="ed7e9-221">安裝 Minikube 之後，您可以執行`minikube start`命令快速開始使用它，這會下載映射並啟動本機 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-221">After installing Minikube, you can quickly start using it by running the `minikube start` command, which downloads an image and start the local Kubernetes cluster.</span></span> <span data-ttu-id="ed7e9-222">啟動叢集之後，您可以使用標準 Kubernetes `kubectl`命令與它互動。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-222">Once the cluster is started, you interact with it using the standard Kubernetes `kubectl` commands.</span></span>

### <a name="docker-desktop"></a><span data-ttu-id="ed7e9-223">Docker Desktop</span><span class="sxs-lookup"><span data-stu-id="ed7e9-223">Docker Desktop</span></span>

<span data-ttu-id="ed7e9-224">您也可以直接從 Windows 上的 Docker Desktop 使用 Kubernetes。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-224">You can also work with Kubernetes directly from Docker Desktop on Windows.</span></span> <span data-ttu-id="ed7e9-225">如果您使用的是 Windows 容器，這是您唯一的選項，而且也是非 Windows 容器的絕佳選擇。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-225">This is your only option if you're using Windows Containers, and is a great choice for non-Windows containers as well.</span></span> <span data-ttu-id="ed7e9-226">標準 Docker 桌面設定應用程式是用來設定從 Docker Desktop 執行的 Kubernetes。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-226">The standard Docker Desktop configuration app is used to configure Kubernetes running from Docker Desktop.</span></span>

![在 Docker Desktop 中設定 Kubernetes](./media/docker-desktop-kubernetes.png)

<span data-ttu-id="ed7e9-228">**圖 3-4**。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-228">**Figure 3-4**.</span></span> <span data-ttu-id="ed7e9-229">在 Docker Desktop 中設定 Kubernetes。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-229">Configuring Kubernetes in Docker Desktop.</span></span>

<span data-ttu-id="ed7e9-230">Docker Desktop 已經是最受歡迎的工具，可在本機設定和執行容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-230">Docker Desktop is already the most popular tool for configuring and running containerized apps locally.</span></span> <span data-ttu-id="ed7e9-231">當您使用 Docker Desktop 時，可以針對您要部署到生產環境的完全相同 Docker 容器映射，在本機進行開發。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-231">When you work with Docker Desktop, you can develop locally against the exact same set of Docker container images that you'll deploy to production.</span></span> <span data-ttu-id="ed7e9-232">Docker Desktop 是設計成在本機「建立、測試及傳送」容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-232">Docker Desktop is designed to "build, test, and ship" containerized apps locally.</span></span> <span data-ttu-id="ed7e9-233">映射一旦送出至映射登錄（例如 Azure Container Registry 或 Docker Hub）之後，Azure Kubernetes Service （AKS）之類的服務就會在生產環境中管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-233">Once the images have been shipped to an image registry like Azure Container Registry or Docker Hub, then services like Azure Kubernetes Service (AKS) manage the application in production.</span></span>

### <a name="visual-studio-docker-tooling"></a><span data-ttu-id="ed7e9-234">Visual Studio Docker 工具</span><span class="sxs-lookup"><span data-stu-id="ed7e9-234">Visual Studio Docker Tooling</span></span>

<span data-ttu-id="ed7e9-235">Visual Studio 支援 web 應用程式的 Docker 開發。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-235">Visual Studio supports Docker development for web applications.</span></span> <span data-ttu-id="ed7e9-236">當您建立新的 ASP.NET Core 應用程式時，您可以選擇使用 Docker 支援來設定它，做為專案建立過程的一部分，如圖3-5 所示。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-236">When you create a new ASP.NET Core application, you're given the option to configure it with Docker support as part of the project creation process, as shown in Figure 3-5.</span></span>

![Visual Studio 啟用 Docker 支援](./media/visual-studio-enable-docker-support.png)

<span data-ttu-id="ed7e9-238">**圖 3-5**。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-238">**Figure 3-5**.</span></span> <span data-ttu-id="ed7e9-239">Visual Studio 啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="ed7e9-239">Visual Studio Enable Docker Support</span></span>

<span data-ttu-id="ed7e9-240">選取此選項時，會`Dockerfile`使用其根目錄中的建立專案，這可用來在 Docker 容器中建立和裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-240">When this option is selected, the project is created with a `Dockerfile` in its root, which can be used to build and host the app in a Docker container.</span></span> <span data-ttu-id="ed7e9-241">範例 Dockerfile 如圖3-6 所示。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-241">An example Dockerfile is shown in Figure 3-6.</span></span>

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

<span data-ttu-id="ed7e9-242">**圖 3-6**。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-242">**Figure 3-6**.</span></span> <span data-ttu-id="ed7e9-243">Visual Studio 產生的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="ed7e9-243">Visual Studio generated Dockerfile</span></span>

<span data-ttu-id="ed7e9-244">應用程式執行時的預設行為也會設定為使用 Docker。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-244">The default behavior when the app runs is configured to use Docker as well.</span></span> <span data-ttu-id="ed7e9-245">圖3-7 顯示新的 ASP.NET Core 專案提供的不同執行選項，並已新增 Docker 支援。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-245">Figure 3-7 shows the different run options available from a new ASP.NET Core project created with Docker support added.</span></span>

![Visual Studio Docker 執行選項](./media/visual-studio-docker-run-options.png)

<span data-ttu-id="ed7e9-247">**圖 3-7**。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-247">**Figure 3-7**.</span></span> <span data-ttu-id="ed7e9-248">Visual Studio Docker 執行選項</span><span class="sxs-lookup"><span data-stu-id="ed7e9-248">Visual Studio Docker Run Options</span></span>

<span data-ttu-id="ed7e9-249">除了本機開發以外， [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/)提供便利的方式讓多個開發人員在 Azure 內使用自己的 Kubernetes 設定。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-249">In addition to local development, [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) provides a convenient way for multiple developers to work with their own Kubernetes configurations within Azure.</span></span> <span data-ttu-id="ed7e9-250">如 [圖 3-10] 所示，您也可以在 Azure Dev Spaces 中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-250">As you can see in Figure 3-10, you can also run the application in Azure Dev Spaces.</span></span>

<span data-ttu-id="ed7e9-251">如果您在建立時未將 Docker 支援新增至 ASP.NET Core 應用程式，您可以隨時將其新增。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-251">If you don't add Docker support to your ASP.NET Core application when you create it, you can always add it later.</span></span> <span data-ttu-id="ed7e9-252">在 Visual Studio 方案總管中，以滑鼠右鍵按一下專案，然後選取 **新增** >  **Docker 支援**，如圖3-8 所示。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-252">From the Visual Studio Solution Explorer, right click on the project and select **Add** > **Docker Support**, as shown in Figure 3-8.</span></span>

![Visual Studio 新增 Docker 支援](./media/visual-studio-add-docker-support.png)

<span data-ttu-id="ed7e9-254">**圖 3-8**。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-254">**Figure 3-8**.</span></span> <span data-ttu-id="ed7e9-255">Visual Studio 新增 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="ed7e9-255">Visual Studio Add Docker Support</span></span>

<span data-ttu-id="ed7e9-256">除了 Docker 支援以外，您也可以新增容器協調流程支援，如圖3-11 所示。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-256">In addition to Docker support, you can also add Container Orchestration Support, also shown in Figure 3-11.</span></span> <span data-ttu-id="ed7e9-257">根據預設，orchestrator 會使用 Kubernetes 和 Helm。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-257">By default, the orchestrator uses Kubernetes and Helm.</span></span> <span data-ttu-id="ed7e9-258">一旦您選擇協調器， `azds.yaml`檔案就會新增至專案根目錄，並加入一個`charts`資料夾，其中包含用來設定和部署應用程式至 Kubernetes 的 Helm 圖表。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-258">Once you've chosen the orchestrator, a `azds.yaml` file is added to the project root and a `charts` folder is added containing the Helm charts used to configure and deploy the application to Kubernetes.</span></span> <span data-ttu-id="ed7e9-259">圖3-9 顯示新專案中產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-259">Figure 3-9 shows the resulting files in a new project.</span></span>

![Visual Studio 新增協調器支援](./media/visual-studio-add-orchestrator-support.png)

<span data-ttu-id="ed7e9-261">**圖 3-9**。</span><span class="sxs-lookup"><span data-stu-id="ed7e9-261">**Figure 3-9**.</span></span> <span data-ttu-id="ed7e9-262">Visual Studio 新增協調器支援</span><span class="sxs-lookup"><span data-stu-id="ed7e9-262">Visual Studio Add Orchestrator Support</span></span>

## <a name="references"></a><span data-ttu-id="ed7e9-263">reference</span><span class="sxs-lookup"><span data-stu-id="ed7e9-263">References</span></span>

- [<span data-ttu-id="ed7e9-264">什麼是 Kubernetes？</span><span class="sxs-lookup"><span data-stu-id="ed7e9-264">What is Kubernetes?</span></span>](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [<span data-ttu-id="ed7e9-265">使用 Minikube 安裝 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="ed7e9-265">Installing Kubernetes with Minikube</span></span>](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [<span data-ttu-id="ed7e9-266">MiniKube 與 Docker Desktop</span><span class="sxs-lookup"><span data-stu-id="ed7e9-266">MiniKube vs Docker Desktop</span></span>](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [<span data-ttu-id="ed7e9-267">Visual Studio Tools for Docker</span><span class="sxs-lookup"><span data-stu-id="ed7e9-267">Visual Studio Tools for Docker</span></span>](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
><span data-ttu-id="ed7e9-268">[上一頁](scale-applications.md)
>[下一頁](leverage-serverless-functions.md)</span><span class="sxs-lookup"><span data-stu-id="ed7e9-268">[Previous](scale-applications.md)
[Next](leverage-serverless-functions.md)</span></span>
