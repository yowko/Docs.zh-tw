---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 協調微服務和多容器應用程式的高延展性和可用性
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: aab939af29849ceeef76d6f61b3d4f59d701094c
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105458"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a><span data-ttu-id="8fa5d-103">協調微服務和多容器應用程式的高延展性和可用性</span><span class="sxs-lookup"><span data-stu-id="8fa5d-103">Orchestrating microservices and multi-container applications for high scalability and availability</span></span>

<span data-ttu-id="8fa5d-104">如果您的應用程式是以微服務為基礎或分散於多個容器，您就必須為適用於生產環境的應用程式使用協調器。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-104">Using orchestrators for production-ready applications is essential if your application is based on microservices or simply split across multiple containers.</span></span> <span data-ttu-id="8fa5d-105">如之前所介紹，以微服務為基礎的方法中，每個微服務都擁有自己的模型和資料，因此從開發和部署的角度來看，它是非常自主的。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-105">As introduced previously, in a microservice-based approach, each microservice owns its model and data so that it will be autonomous from a development and deployment point of view.</span></span> <span data-ttu-id="8fa5d-106">但是，即使您擁有的是由多個服務組成的傳統應用程式 (例如 SOA)，您也會使用多個容器或服務來組成單一商務應用程式，而這些項目都必須部署為分散式系統。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-106">But even if you have a more traditional application that is composed of multiple services (like SOA), you will also have multiple containers or services comprising a single business application that need to be deployed as a distributed system.</span></span> <span data-ttu-id="8fa5d-107">向外延展和管理這類系統非常的複雜；因此，如果您想要擁有一個適用於生產環境且可延展的多容器應用程式，就一定要使用協調器。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-107">These kinds of systems are complex to scale out and manage; therefore, you absolutely need an orchestrator if you want to have a production-ready and scalable multi-container application.</span></span>

<span data-ttu-id="8fa5d-108">圖 4-23 說明由多個微服務 (容器) 所組成之應用程式叢集中的部署。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-108">Figure 4-23 illustrates deployment into a cluster of an application composed of multiple microservices (containers).</span></span>

![](./media/image23.PNG)

<span data-ttu-id="8fa5d-109">**圖 4-23**：</span><span class="sxs-lookup"><span data-stu-id="8fa5d-109">**Figure 4-23**.</span></span> <span data-ttu-id="8fa5d-110">容器叢集</span><span class="sxs-lookup"><span data-stu-id="8fa5d-110">A cluster of containers</span></span>

<span data-ttu-id="8fa5d-111">看起來像邏輯方法。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-111">It looks like a logical approach.</span></span> <span data-ttu-id="8fa5d-112">不過，您該如何處理這些組成應用程式的負載平衡、路由及協調作業？</span><span class="sxs-lookup"><span data-stu-id="8fa5d-112">But how are you handling load-balancing, routing, and orchestrating these composed applications?</span></span>

<span data-ttu-id="8fa5d-113">如果是一部主機上單一映像執行個體的管理需求，可靠單一 Docker 主機中的單純 Docker 引擎來滿足，但若是更複雜的分散式應用程式，它就無法滿足部署於多個主機上多個容器的管理需求。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-113">The plain Docker Engine in single Docker hosts meets the needs of managing single image instances on one host, but it falls short when it comes to managing multiple containers deployed on multiple hosts for more complex distributed applications.</span></span> <span data-ttu-id="8fa5d-114">在大部分情況下，您需要的管理平台應能自動啟動容器、向外延展容器 (其中每個映像含多個執行個體)、視需要暫停或關閉它們，最好也能控制資源 (例如網路和資料儲存體) 的存取方式。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-114">In most cases, you need a management platform that will automatically start containers, scale-out containers with multiple instances per image, suspend them or shut them down when needed, and ideally also control how they access resources like the network and data storage.</span></span>

<span data-ttu-id="8fa5d-115">如果您不只要管理個別容器或組成非常簡單的應用程式，而是要進展到含有微服務的大型企業應用程式，就必須採用協調流程和叢集平台。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-115">To go beyond the management of individual containers or very simple composed apps and move toward larger enterprise applications with microservices, you must turn to orchestration and clustering platforms.</span></span>

<span data-ttu-id="8fa5d-116">從架構和開發角度來看，如果您要建置由微服務應用程式所組成的大型企業應用程式，請務必了解下列可支援進階案例的平台和產品：</span><span class="sxs-lookup"><span data-stu-id="8fa5d-116">From an architecture and development point of view, if you are building large enterprise composed of microservices-based applications, it is important to understand the following platforms and products that support advanced scenarios:</span></span>

<span data-ttu-id="8fa5d-117">**叢集和協調器**：</span><span class="sxs-lookup"><span data-stu-id="8fa5d-117">**Clusters and orchestrators**.</span></span> <span data-ttu-id="8fa5d-118">當您要跨許多 Docker 主機向外延展應用程式時 (亦即大型微服務應用程式)，您必須簡化基礎平台的複雜性，並以單一叢集的形式來管理其中的所有主機。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-118">When you need to scale out applications across many Docker hosts, as when a large microservice-based application, it is critical to be able to manage all those hosts as a single cluster by abstracting the complexity of the underlying platform.</span></span> <span data-ttu-id="8fa5d-119">而這正是容器叢集和協調器所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-119">That is what the container clusters and orchestrators provide.</span></span> <span data-ttu-id="8fa5d-120">Azure Service Fabric、Kubernetes、Docker Swarm 和 Mesosphere DC/OS 都是範例協調器。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-120">Examples of orchestrators are Azure Service Fabric, Kubernetes, Docker Swarm and Mesosphere DC/OS.</span></span> <span data-ttu-id="8fa5d-121">最後三個是開放原始碼協調器；您可以透過 Azure Container Service 在 Azure 中取得。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-121">The last three open-source orchestrators are available in Azure through Azure Container Service.</span></span>

<span data-ttu-id="8fa5d-122">**排程器**：</span><span class="sxs-lookup"><span data-stu-id="8fa5d-122">**Schedulers**.</span></span> <span data-ttu-id="8fa5d-123">「排程」可讓系統管理員啟動叢集中的容器，因此這些排程器也會提供 UI。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-123">*Scheduling* means to have the capability for an administrator to launch containers in a cluster so they also provide a UI.</span></span> <span data-ttu-id="8fa5d-124">叢集排程器有下列職責：有效率地使用叢集的資源、設定使用者所提供的條件約束、跨節點或主機有效進行容器負載平衡，以及維持容錯性並保障高可用性。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-124">A cluster scheduler has several responsibilities: to use the cluster’s resources efficiently, to set the constraints provided by the user, to efficiently load-balance containers across nodes or hosts, and to be robust against errors while providing high availability.</span></span>

<span data-ttu-id="8fa5d-125">叢集與排程器的概念密切相關，因此不同廠商所提供的產品通常會兩組功能都提供。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-125">The concepts of a cluster and a scheduler are closely related, so the products provided by different vendors often provide both sets of capabilities.</span></span> <span data-ttu-id="8fa5d-126">下列清單顯示您可以針對叢集和排程器選擇的最重要平台和軟體。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-126">The following list shows the most important platform and software choices you have for clusters and schedulers.</span></span> <span data-ttu-id="8fa5d-127">一般來說，Azure 這類公用雲端都會提供這些協調器。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-127">These orchestrators are generally offered in public clouds like Azure.</span></span>

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a><span data-ttu-id="8fa5d-128">用於容器叢集、協調流程和排程的軟體平台</span><span class="sxs-lookup"><span data-stu-id="8fa5d-128">Software platforms for container clustering, orchestration, and scheduling</span></span>

<span data-ttu-id="8fa5d-129">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="8fa5d-129">Kubernetes</span></span>

![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image24.png)

> <span data-ttu-id="8fa5d-130">Kubernetes 是開放原始碼產品，可提供叢集基礎結構、容器排程到容器協調等功能。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-130">Kubernetes is an open-source product that provides functionality that ranges from cluster infrastructure and container scheduling to orchestrating capabilities.</span></span> <span data-ttu-id="8fa5d-131">它可讓您跨主機叢集自動化部署、規模調整及應用程式容器的作業。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-131">It lets you automate deployment, scaling, and operations of application containers across clusters of hosts.</span></span>
>
> <span data-ttu-id="8fa5d-132">Kubernetes 提供以容器為中心的基礎結構，讓您將應用程式容器分組為邏輯單元，以便於管理及探索。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-132">Kubernetes provides a container-centric infrastructure that groups application containers into logical units for easy management and discovery.</span></span>
>
> <span data-ttu-id="8fa5d-133">比起 Windows，Kubernetes 在 Linux 中相對成熟穩定。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-133">Kubernetes is mature in Linux, less mature in Windows.</span></span>

<span data-ttu-id="8fa5d-134">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="8fa5d-134">Docker Swarm</span></span>

![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image25.png)

> <span data-ttu-id="8fa5d-135">Docker Swarm 可讓您為 Docker 容器進行叢集與排程作業。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-135">Docker Swarm lets you cluster and schedule Docker containers.</span></span> <span data-ttu-id="8fa5d-136">使用 Swarm 時，您可以將 Docker 主機集區轉換成單一的虛擬 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-136">By using Swarm, you can turn a pool of Docker hosts into a single, virtual Docker host.</span></span> <span data-ttu-id="8fa5d-137">用戶端可以向 Swarm 提出 API 要求 (與向主機提出要求的方式相同)，也就是說 Swarm 可以輕鬆地讓應用程式順應多部主機來調整規模。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-137">Clients can make API requests to Swarm the same way they do to hosts, meaning that Swarm makes it easy for applications to scale to multiple hosts.</span></span>
>
> <span data-ttu-id="8fa5d-138">Docker Swarm 是 Docker 公司的產品。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-138">Docker Swarm is a product from Docker, the company.</span></span>
>
> <span data-ttu-id="8fa5d-139">Docker v1.12 或更新版本可以執行原生與內建的 Swarm 模式。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-139">Docker v1.12 or later can run native and built-in Swarm Mode.</span></span>

<span data-ttu-id="8fa5d-140">Mesosphere DC/OS</span><span class="sxs-lookup"><span data-stu-id="8fa5d-140">Mesosphere DC/OS</span></span>

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> <span data-ttu-id="8fa5d-141">Mesosphere Enterprise DC/OS (以 Apache Mesos 為基礎) 是一種適用於生產環境的平台，可執行容器和分散式應用程式。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-141">Mesosphere Enterprise DC/OS (based on Apache Mesos) is a production-ready platform for running containers and distributed applications.</span></span>
>
> <span data-ttu-id="8fa5d-142">DC/OS 的運作方式是將叢集中可用的資源集合簡化，讓這些資源可供建置其上的元件使用。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-142">DC/OS works by abstracting a collection of the resources available in the cluster and making those resources available to components built on top of it.</span></span> <span data-ttu-id="8fa5d-143">Marathon 通常作為與 DC/OS 整合的排程器。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-143">Marathon is usually used as a scheduler integrated with DC/OS.</span></span>
>
> <span data-ttu-id="8fa5d-144">比起 Windows，DC/OS 在 Linux 中相對成熟穩定。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-144">DC/OS is mature in Linux, less mature in Windows.</span></span>

<span data-ttu-id="8fa5d-145">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="8fa5d-145">Azure Service Fabric</span></span>

![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image27.png)

> <span data-ttu-id="8fa5d-146">[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) 是一種 Microsoft 微服務平台，可用來建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-146">[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) is a Microsoft microservices platform for building applications.</span></span> <span data-ttu-id="8fa5d-147">它是一種服務的[協調器](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)，並可建立電腦叢集。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-147">It is an [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) of services and creates clusters of machines.</span></span> <span data-ttu-id="8fa5d-148">Service Fabric 可以將服務部署為容器或一般處理序。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-148">Service Fabric can deploy services as containers or as plain processes.</span></span> <span data-ttu-id="8fa5d-149">它甚至可以將處理序中的服務與相同應用程式和叢集內容器中的服務混合。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-149">It can even mix services in processes with services in containers within the same application and cluster.</span></span>
>
> <span data-ttu-id="8fa5d-150">Service Fabric 也提供其他選用的規範 [Service Fabric 程式設計模型](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)，例如[具狀態的服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)和 [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-150">Service Fabric provides additional and optional prescriptive [Service Fabric programming models ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) like [stateful services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) and [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).</span></span>
>
> <span data-ttu-id="8fa5d-151">比起 Linux，Service Fabric 在 Windows 中相對成熟 (但仍在持續演進中)。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-151">Service Fabric is mature in Windows (years evolving in Windows), less mature in Linux.</span></span> 
> <span data-ttu-id="8fa5d-152">自 2017 年起，Service Fabric 即可支援 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-152">Both Linux and Windows containers are supported in Service Fabric since 2017.</span></span>

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a><span data-ttu-id="8fa5d-153">在 Microsoft Azure 中使用容器協調器</span><span class="sxs-lookup"><span data-stu-id="8fa5d-153">Using container-based orchestrators in Microsoft Azure</span></span>

<span data-ttu-id="8fa5d-154">許多雲端廠商都支援 Docker 容器以及 Docker 叢集和協調流程，包括 Microsoft Azure、Amazon EC2 Container Service 和 Google Container Engine。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-154">Several cloud vendors offer Docker containers support plus Docker clusters and orchestration support, including Microsoft Azure, Amazon EC2 Container Service, and Google Container Engine.</span></span> <span data-ttu-id="8fa5d-155">如下節所說明，Microsoft Azure 可透過 Azure Container Service (ACS) 支援 Docker 叢集和協調器。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-155">Microsoft Azure provides Docker cluster and orchestrator support through Azure Container Service (ACS), as explained in the next section.</span></span>

<span data-ttu-id="8fa5d-156">您也可以選擇使用 Microsoft Azure Service Fabric (微服務平台)，其亦可支援 Linux 和 Windows 容器的 Docker。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-156">Another choice is to use Microsoft Azure Service Fabric (a microservices platform), which also supports Docker based on Linux and Windows Containers.</span></span> <span data-ttu-id="8fa5d-157">Service Fabric 可在 Azure 或任何其他雲端上執行，亦可於[內部部署](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)執行。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-157">Service Fabric runs on Azure or any other cloud, and also runs [on-premises](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).</span></span>

## <a name="using-azure-container-service"></a><span data-ttu-id="8fa5d-158">使用 Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="8fa5d-158">Using Azure Container Service</span></span>

<span data-ttu-id="8fa5d-159">Docker 叢集裝載了多部 Docker 主機，並將其公開為單一虛擬 Docker 主機，因此您可以部署多個容器到該叢集中。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-159">A Docker cluster pools multiple Docker hosts and exposes them as a single virtual Docker host, so you can deploy multiple containers into the cluster.</span></span> <span data-ttu-id="8fa5d-160">叢集會處理所有複雜的管理配置作業，例如延展性、健康狀態等等。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-160">The cluster will handle all the complex management plumbing, like scalability, health, and so forth.</span></span> <span data-ttu-id="8fa5d-161">圖 4-24 表示組成應用程式的 Docker 叢集如何與 Azure Container Service (ACS) 對應。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-161">Figure 4-24 represents how a Docker cluster for composed applications maps to Azure Container Service (ACS).</span></span>

<span data-ttu-id="8fa5d-162">ACS 可讓您以簡化的方式，建立、設定及管理預先設定為執行容器化應用程式的虛擬機器叢集。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-162">ACS provides a way to simplify the creation, configuration, and management of a cluster of virtual machines that are preconfigured to run containerized applications.</span></span> <span data-ttu-id="8fa5d-163">ACS 使用熱門開放原始碼排程和協調流程工具的最佳化組態，可讓您使用現有技能，或運用大量且不斷成長的社群專業知識，在 Microsoft Azure 上部署及管理容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-163">Using an optimized configuration of popular open-source scheduling and orchestration tools, ACS enables you to use your existing skills or draw on a large and growing body of community expertise to deploy and manage container-based applications on Microsoft Azure.</span></span>

<span data-ttu-id="8fa5d-164">Azure Container Service 特別針對 Azure，提供熱門 Docker 叢集開放原始碼工具和技術的最佳化組態。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-164">Azure Container Service optimizes the configuration of popular Docker clustering open source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="8fa5d-165">這樣的開放解決方案，可賦予您容器和應用程式組態的可攜性。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-165">You get an open solution that offers portability for both your containers and your application configuration.</span></span> <span data-ttu-id="8fa5d-166">您只要選取主機大小和數目，其餘工作全都由協調器工具和 Container Service 處理。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-166">You select the size, the number of hosts, and the orchestrator tools, and Container Service handles everything else.</span></span>

![](./media/image28.png)

<span data-ttu-id="8fa5d-167">**圖 4-24**：</span><span class="sxs-lookup"><span data-stu-id="8fa5d-167">**Figure 4-24**.</span></span> <span data-ttu-id="8fa5d-168">Azure Container Service 中的叢集選項</span><span class="sxs-lookup"><span data-stu-id="8fa5d-168">Clustering choices in Azure Container Service</span></span>

<span data-ttu-id="8fa5d-169">ACS 會利用 Docker 映像，以確保您的應用程式容器具有完整可攜性。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-169">ACS leverages Docker images to ensure that your application containers are fully portable.</span></span> <span data-ttu-id="8fa5d-170">它可支援您選擇的開放原始碼協調流程平台，如 DC/OS (由 Apache Mesos 提供技術支援)、Kubernetes (由 Google 初創) 與 Docker Swarm，以確保這些應用程式可以調整到數千、甚至數萬個容器的規模。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-170">It supports your choice of open-source orchestration platforms like DC/OS (powered by Apache Mesos), Kubernetes (originally created by Google), and Docker Swarm, to ensure that these applications can be scaled to thousands or even tens of thousands of containers.</span></span>

<span data-ttu-id="8fa5d-171">藉由使用 Azure Container Service，您可以充分利用 Azure 的企業級功能，同時仍可保有應用程式的可攜性，包括協調流程層級。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-171">The Azure Container service enables you to take advantage of the enterprise-grade features of Azure while still maintaining application portability, including at the orchestration layers.</span></span>

![](./media/image29.png)

<span data-ttu-id="8fa5d-172">**圖 4-25**：</span><span class="sxs-lookup"><span data-stu-id="8fa5d-172">**Figure 4-25**.</span></span> <span data-ttu-id="8fa5d-173">ACS 的協調器</span><span class="sxs-lookup"><span data-stu-id="8fa5d-173">Orchestrators in ACS</span></span>

<span data-ttu-id="8fa5d-174">如圖 4-25 所示，Azure Container Service 只是 Azure 為了部署 DC/OS、Kubernetes 或 Docker Swarm 所提供的基礎結構，但是 ACS 並未實作任何其他協調器。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-174">As shown in Figure 4-25, Azure Container Service is simply the infrastructure provided by Azure in order to deploy DC/OS, Kubernetes or Docker Swarm, but ACS does not implement any additional orchestrator.</span></span> <span data-ttu-id="8fa5d-175">因此，ACS 不是協調器，而只是一種運用容器現有開放原始碼協調器的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-175">Therefore, ACS is not an orchestrator as such, only an infrastructure that leverages existing open-source orchestrators for containers.</span></span>

<span data-ttu-id="8fa5d-176">從用途角度來看，Azure Container Service 的目標是使用熱門的開放原始碼工具和技術來提供容器裝載環境。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-176">From a usage perspective, the goal of Azure Container Service is to provide a container hosting environment by using popular open-source tools and technologies.</span></span> <span data-ttu-id="8fa5d-177">為此，它會為您所選擇的協調器公開標準的 API 端點。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-177">To this end, it exposes the standard API endpoints for your chosen orchestrator.</span></span> <span data-ttu-id="8fa5d-178">藉由使用這些端點，您就能運用任何可與這些端點通訊的軟體。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-178">By using these endpoints, you can leverage any software that can talk to those endpoints.</span></span> <span data-ttu-id="8fa5d-179">比方說，若是 Docker Swarm 端點，您可能會選擇使用 Docker 命令列介面 (CLI)。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-179">For example, in the case of the Docker Swarm endpoint, you might choose to use the Docker command-line interface (CLI).</span></span> <span data-ttu-id="8fa5d-180">若是 DC/OS，您可能會選擇使用 DC/OS CLI。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-180">For DC/OS, you might choose to use the DC/OS CLI.</span></span>

### <a name="getting-started-with-azure-container-service"></a><span data-ttu-id="8fa5d-181">開始使用 Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="8fa5d-181">Getting started with Azure Container Service</span></span> 

<span data-ttu-id="8fa5d-182">若要開始使用 Azure Container Service，請使用 Azure Resource Manager 範本或 [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)，從 Azure 入口網站部署 Azure Container Service。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-182">To begin using Azure Container Service, you deploy an Azure Container Service cluster from the Azure portal by using an Azure Resource Manager template or the [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli).</span></span> <span data-ttu-id="8fa5d-183">可用的範本包括 [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)、[Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes) 和 [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos)。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-183">Available templates include [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), and [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos).</span></span> <span data-ttu-id="8fa5d-184">您可以修改快速入門範本，以包含其他或進階的 Azure 組態。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-184">The quickstart templates can be modified to include additional or advanced Azure configuration.</span></span> <span data-ttu-id="8fa5d-185">如需如何部署 Azure Container Service 叢集的詳細資訊，請參閱 Azure 網站上的[部署 Azure Container Service 叢集](https://docs.microsoft.com/azure/container-service/container-service-deployment)。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-185">For more information on deploying an Azure Container Service cluster, see [Deploy an Azure Container Service cluster](https://docs.microsoft.com/azure/container-service/container-service-deployment) on the Azure website.</span></span>

<span data-ttu-id="8fa5d-186">隨附於 ACS 預設安裝的軟體均不會收取任何費用。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-186">There are no fees for any of the software installed by default as part of ACS.</span></span> <span data-ttu-id="8fa5d-187">所有預設選項都是使用開放原始碼軟體來實作。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-187">All default options are implemented with open-source software.</span></span>

<span data-ttu-id="8fa5d-188">ACS 目前可供 Azure 中的標準 A、D、DS、G 及 GS 系列 Linux 虛擬機器使用。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-188">ACS is currently available for Standard A, D, DS, G, and GS series Linux virtual machines in Azure.</span></span> <span data-ttu-id="8fa5d-189">您僅需支付所選計算執行個體的費用，以及其他已使用的基礎結構資源費用，例如儲存體和網路功能。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-189">You are charged only for the compute instances you choose, as well as the other underlying infrastructure resources consumed, such as storage and networking.</span></span> <span data-ttu-id="8fa5d-190">ACS 本身沒有任何累加的費用。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-190">There are no incremental charges for ACS itself.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8fa5d-191">其他資源</span><span class="sxs-lookup"><span data-stu-id="8fa5d-191">Additional resources</span></span>

-   <span data-ttu-id="8fa5d-192">**使用 Azure Container Service 裝載解決方案的 Docker 容器簡介**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)</span><span class="sxs-lookup"><span data-stu-id="8fa5d-192">**Introduction to Docker container hosting solutions with Azure Container Service**
[*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)</span></span>

-   <span data-ttu-id="8fa5d-193">**Docker Swarm 概觀**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)</span><span class="sxs-lookup"><span data-stu-id="8fa5d-193">**Docker Swarm overview**
[*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)</span></span>

-   <span data-ttu-id="8fa5d-194">**Swarm 模式概觀**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)</span><span class="sxs-lookup"><span data-stu-id="8fa5d-194">**Swarm mode overview**
[*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)</span></span>

-   <span data-ttu-id="8fa5d-195">**Mesosphere DC/OS 概觀**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)</span><span class="sxs-lookup"><span data-stu-id="8fa5d-195">**Mesosphere DC/OS Overview**
[*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)</span></span>

-   <span data-ttu-id="8fa5d-196">**Kubernetes**</span><span class="sxs-lookup"><span data-stu-id="8fa5d-196">**Kubernetes.**</span></span> <span data-ttu-id="8fa5d-197">官方網站。</span><span class="sxs-lookup"><span data-stu-id="8fa5d-197">The official site.\\</span></span>
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
<span data-ttu-id="8fa5d-198">[上一頁](resilient-high-availability-microservices.md)
[下一頁](using-azure-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="8fa5d-198">[Previous](resilient-high-availability-microservices.md)
[Next](using-azure-service-fabric.md)</span></span>
