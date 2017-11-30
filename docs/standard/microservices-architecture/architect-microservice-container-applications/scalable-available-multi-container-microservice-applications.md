---
title: "協調 microservices 及多容器應用程式的高延展性和可用性"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |協調 microservices 及多容器應用程式的高延展性和可用性"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ec33901a0ddc9e5b58263440b0e4399e687c6904
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a><span data-ttu-id="8bd4b-104">協調 microservices 及多容器應用程式的高延展性和可用性</span><span class="sxs-lookup"><span data-stu-id="8bd4b-104">Orchestrating microservices and multi-container applications for high scalability and availability</span></span>

<span data-ttu-id="8bd4b-105">如果您的應用程式是根據 microservices 或只分割到多個容器，可實際執行的應用程式使用 orchestrators 就很重要。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-105">Using orchestrators for production-ready applications is essential if your application is based on microservices or simply split across multiple containers.</span></span> <span data-ttu-id="8bd4b-106">推出之前，在微服務為基礎的方法中，每個微服務擁有其模型和資料，因此它會從開發和部署的觀點自發。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-106">As introduced previously, in a microservice-based approach, each microservice owns its model and data so that it will be autonomous from a development and deployment point of view.</span></span> <span data-ttu-id="8bd4b-107">但是，即使您擁有更傳統的應用程式所組成的多個服務 （例如 SOA)，您也必須多個容器或組成單一商務應用程式中需要部署為分散式系統的服務。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-107">But even if you have a more traditional application that is composed of multiple services (like SOA), you will also have multiple containers or services comprising a single business application that need to be deployed as a distributed system.</span></span> <span data-ttu-id="8bd4b-108">這類系統很複雜向外擴充和管理。因此，您一定需要 orchestrator 如果您想要已備妥且可延展的多重容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-108">These kinds of systems are complex to scale out and manage; therefore, you absolutely need an orchestrator if you want to have a production-ready and scalable multi-container application.</span></span>

<span data-ttu-id="8bd4b-109">圖 4-23 說明到叢集中的多個 microservices （容器） 所組成的應用程式的部署。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-109">Figure 4-23 illustrates deployment into a cluster of an application composed of multiple microservices (containers).</span></span>

![](./media/image23.PNG)

<span data-ttu-id="8bd4b-110">**圖 4-23**。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-110">**Figure 4-23**.</span></span> <span data-ttu-id="8bd4b-111">叢集的容器</span><span class="sxs-lookup"><span data-stu-id="8bd4b-111">A cluster of containers</span></span>

<span data-ttu-id="8bd4b-112">它看起來像邏輯方法。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-112">It looks like a logical approach.</span></span> <span data-ttu-id="8bd4b-113">不過，如何處理負載平衡、 路由及協調這些是您撰寫的應用程式嗎？</span><span class="sxs-lookup"><span data-stu-id="8bd4b-113">But how are you handling load-balancing, routing, and orchestrating these composed applications?</span></span>

<span data-ttu-id="8bd4b-114">一般 Docker 引擎單一 Docker 主機中符合的需求管理一部的主機上的單一映像執行個體，但管理更複雜的分散式應用程式的多個主機上部署的多個容器時落短。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-114">The plain Docker Engine in single Docker hosts meets the needs of managing single image instances on one host, but it falls short when it comes to managing multiple containers deployed on multiple hosts for more complex distributed applications.</span></span> <span data-ttu-id="8bd4b-115">在大部分情況下，您需要的管理平台會自動啟動容器，每個影像的多個執行個體的向外延展容器、 擱置那些或關閉它們需要時，並在理想情況下也控制存取資源，例如網路和資料的方式儲存體。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-115">In most cases, you need a management platform that will automatically start containers, scale-out containers with multiple instances per image, suspend them or shut them down when needed, and ideally also control how they access resources like the network and data storage.</span></span>

<span data-ttu-id="8bd4b-116">若要超越個別容器或非常簡單的組成應用程式和大型企業應用程式與 microservices 嚴的管理，您必須開啟協調流程和叢集平台。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-116">To go beyond the management of individual containers or very simple composed apps and move toward larger enterprise applications with microservices, you must turn to orchestration and clustering platforms.</span></span>

<span data-ttu-id="8bd4b-117">從 架構和開發觀點來看，如果您要建置 microservices 為基礎的應用程式所組成的大型企業務必瞭解下列平台和產品可支援進階的案例：</span><span class="sxs-lookup"><span data-stu-id="8bd4b-117">From an architecture and development point of view, if you are building large enterprise composed of microservices-based applications, it is important to understand the following platforms and products that support advanced scenarios:</span></span>

<span data-ttu-id="8bd4b-118">**叢集和 orchestrators**。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-118">**Clusters and orchestrators**.</span></span> <span data-ttu-id="8bd4b-119">當您需要向外擴充的應用程式跨許多 Docker 主機，因為時的大型微服務應用程式，它是關鍵能夠管理與單一叢集的所有這些主機，藉由抽象化基礎平台的複雜性。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-119">When you need to scale out applications across many Docker hosts, as when a large microservice-based application, it is critical to be able to manage all those hosts as a single cluster by abstracting the complexity of the underlying platform.</span></span> <span data-ttu-id="8bd4b-120">這是容器叢集和 orchestrators 提供的內容。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-120">That is what the container clusters and orchestrators provide.</span></span> <span data-ttu-id="8bd4b-121">Orchestrators 範例包括 Azure Service Fabric、 Kubernetes、 Docker Swarm 和 Mesosphere DC/OS。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-121">Examples of orchestrators are Azure Service Fabric, Kubernetes, Docker Swarm and Mesosphere DC/OS.</span></span> <span data-ttu-id="8bd4b-122">最後三個開放原始碼 orchestrators Azure 容器服務透過 Azure 中可用。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-122">The last three open-source orchestrators are available in Azure through Azure Container Service.</span></span>

<span data-ttu-id="8bd4b-123">**排程器**。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-123">**Schedulers**.</span></span> <span data-ttu-id="8bd4b-124">*排程*表示系統管理員，才能啟動叢集中的容器，因此它們也會提供 UI 的功能。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-124">*Scheduling* means to have the capability for an administrator to launch containers in a cluster so they also provide a UI.</span></span> <span data-ttu-id="8bd4b-125">叢集的排程器有多項責任： 有效率地使用叢集的資源設定使用者，有效率地跨主機或節點負載平衡容器所提供的條件約束，是錯誤的穩固同時提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-125">A cluster scheduler has several responsibilities: to use the cluster’s resources efficiently, to set the constraints provided by the user, to efficiently load-balance containers across nodes or hosts, and to be robust against errors while providing high availability.</span></span>

<span data-ttu-id="8bd4b-126">密切相關的叢集，而排程器的概念，因此通常不同廠商所提供的產品提供兩個功能集。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-126">The concepts of a cluster and a scheduler are closely related, so the products provided by different vendors often provide both sets of capabilities.</span></span> <span data-ttu-id="8bd4b-127">下列清單顯示的最重要的平台和軟體選擇您的叢集和排程器。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-127">The following list shows the most important platform and software choices you have for clusters and schedulers.</span></span> <span data-ttu-id="8bd4b-128">這些 orchestrators 通常會提供如 Azure 公用雲端中。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-128">These orchestrators are generally offered in public clouds like Azure.</span></span>

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a><span data-ttu-id="8bd4b-129">叢集的容器、 協調流程，和排程軟體平台</span><span class="sxs-lookup"><span data-stu-id="8bd4b-129">Software platforms for container clustering, orchestration, and scheduling</span></span>

<span data-ttu-id="8bd4b-130">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="8bd4b-130">Kubernetes</span></span>

![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image24.png)

> <span data-ttu-id="8bd4b-132">Kubernetes 是開放原始碼產品，可提供功能，範圍可從叢集基礎結構和排程協調功能的容器。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-132">Kubernetes is an open-source product that provides functionality that ranges from cluster infrastructure and container scheduling to orchestrating capabilities.</span></span> <span data-ttu-id="8bd4b-133">它可讓您自動化部署、 調整及作業的應用程式容器主機的叢集上。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-133">It lets you automate deployment, scaling, and operations of application containers across clusters of hosts.</span></span>
>
> <span data-ttu-id="8bd4b-134">Kubernetes 提供應用程式容器分組便於管理及探索的邏輯單元的容器中心基礎結構。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-134">Kubernetes provides a container-centric infrastructure that groups application containers into logical units for easy management and discovery.</span></span>
>
> <span data-ttu-id="8bd4b-135">Kubernetes 是成熟 Linux，較不成熟在 Windows 中。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-135">Kubernetes is mature in Linux, less mature in Windows.</span></span>

<span data-ttu-id="8bd4b-136">Docker 群集</span><span class="sxs-lookup"><span data-stu-id="8bd4b-136">Docker Swarm</span></span>

![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image25.png)

> <span data-ttu-id="8bd4b-138">Docker 群集可讓您叢集並排程 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-138">Docker Swarm lets you cluster and schedule Docker containers.</span></span> <span data-ttu-id="8bd4b-139">藉由使用群集，可以轉換成單一的虛擬的 Docker 主機的 Docker 主機的集區。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-139">By using Swarm, you can turn a pool of Docker hosts into a single, virtual Docker host.</span></span> <span data-ttu-id="8bd4b-140">用戶端可以讓應用程式開發介面要求廣域相同的方式一樣這表示，群集輕鬆的應用程式擴充至多部主機的主機。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-140">Clients can make API requests to Swarm the same way they do to hosts, meaning that Swarm makes it easy for applications to scale to multiple hosts.</span></span>
>
> <span data-ttu-id="8bd4b-141">Docker 群集是從 Docker，公司的產品。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-141">Docker Swarm is a product from Docker, the company.</span></span>
>
> <span data-ttu-id="8bd4b-142">Docker v1.12 或更新版本可以執行原生和內建廣域模式。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-142">Docker v1.12 or later can run native and built-in Swarm Mode.</span></span>

<span data-ttu-id="8bd4b-143">Mesosphere DC/OS</span><span class="sxs-lookup"><span data-stu-id="8bd4b-143">Mesosphere DC/OS</span></span>

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> <span data-ttu-id="8bd4b-145">Mesosphere 企業 DC/OS （根據 Apache Mesos） 是可實際執行的平台執行容器和分散式應用程式。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-145">Mesosphere Enterprise DC/OS (based on Apache Mesos) is a production-ready platform for running containers and distributed applications.</span></span>
>
> <span data-ttu-id="8bd4b-146">DC/OS 運作方式是抽象化叢集中可用的資源集合，並讓這些資源可供在其上建置的元件。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-146">DC/OS works by abstracting a collection of the resources available in the cluster and making those resources available to components built on top of it.</span></span> <span data-ttu-id="8bd4b-147">馬拉松通常做為與 DC/OS 整合的排程器。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-147">Marathon is usually used as a scheduler integrated with DC/OS.</span></span>
>
> <span data-ttu-id="8bd4b-148">DC/OS 已成熟 Linux，較不成熟在 Windows 中。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-148">DC/OS is mature in Linux, less mature in Windows.</span></span>

<span data-ttu-id="8bd4b-149">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="8bd4b-149">Azure Service Fabric</span></span>

![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image27.png)

> <span data-ttu-id="8bd4b-151">[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)是 Microsoft microservices 平台建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-151">[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) is a Microsoft microservices platform for building applications.</span></span> <span data-ttu-id="8bd4b-152">它是[orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)的服務，並會建立叢集的電腦。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-152">It is an [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) of services and creates clusters of machines.</span></span> <span data-ttu-id="8bd4b-153">Service Fabric 可以部署服務，做為容器，或做為一般的處理序。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-153">Service Fabric can deploy services as containers or as plain processes.</span></span> <span data-ttu-id="8bd4b-154">它可以甚至混合中的服務處理程序與相同的應用程式和叢集內的容器中的服務。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-154">It can even mix services in processes with services in containers within the same application and cluster.</span></span>
>
> <span data-ttu-id="8bd4b-155">Service Fabric 提供其他和選擇性精準[程式設計模型的 Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)像[可設定狀態服務](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)和[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-155">Service Fabric provides additional and optional prescriptive [Service Fabric programming models ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) like [stateful services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) and [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).</span></span>
>
> <span data-ttu-id="8bd4b-156">服務網狀架構在 Windows 中 （在 Windows 中年發展），小於成熟在 Linux 中是成熟的。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-156">Service Fabric is mature in Windows (years evolving in Windows), less mature in Linux.</span></span> 
> <span data-ttu-id="8bd4b-157">自 2017年中 Service Fabric 支援 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-157">Both Linux and Windows containers are supported in Service Fabric since 2017.</span></span>

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a><span data-ttu-id="8bd4b-158">在 Microsoft Azure 中使用容器型 orchestrators</span><span class="sxs-lookup"><span data-stu-id="8bd4b-158">Using container-based orchestrators in Microsoft Azure</span></span>

<span data-ttu-id="8bd4b-159">許多雲端廠商提供 Docker 容器支援加上 Docker 叢集和協調流程的支援，包括 Microsoft Azure、 Amazon EC2 容器服務和 Google 容器引擎。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-159">Several cloud vendors offer Docker containers support plus Docker clusters and orchestration support, including Microsoft Azure, Amazon EC2 Container Service, and Google Container Engine.</span></span> <span data-ttu-id="8bd4b-160">Microsoft Azure 提供的 Docker 叢集和 orchestrator 支援透過 Azure 容器服務 (ACS) 下, 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-160">Microsoft Azure provides Docker cluster and orchestrator support through Azure Container Service (ACS), as explained in the next section.</span></span>

<span data-ttu-id="8bd4b-161">另一個選擇是使用 Microsoft Azure Service Fabric （microservices 平台），也支援根據 Linux 與 Windows 容器的 Docker。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-161">Another choice is to use Microsoft Azure Service Fabric (a microservices platform), which also supports Docker based on Linux and Windows Containers.</span></span> <span data-ttu-id="8bd4b-162">Service Fabric 在 Azure 或其他雲端上執行，而且也會執行[內部](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-162">Service Fabric runs on Azure or any other cloud, and also runs [on-premises](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).</span></span>

## <a name="using-azure-container-service"></a><span data-ttu-id="8bd4b-163">使用 Azure 容器服務</span><span class="sxs-lookup"><span data-stu-id="8bd4b-163">Using Azure Container Service</span></span>

<span data-ttu-id="8bd4b-164">Docker 叢集集區的多部 Docker 主機，其公開成單一虛擬 Docker 主機，主機，因此您可以部署到叢集中的多個容器。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-164">A Docker cluster pools multiple Docker hosts and exposes them as a single virtual Docker host, so you can deploy multiple containers into the cluster.</span></span> <span data-ttu-id="8bd4b-165">叢集會處理所有複雜的管理配置作業，例如延展性、 健康及其他等等。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-165">The cluster will handle all the complex management plumbing, like scalability, health, and so forth.</span></span> <span data-ttu-id="8bd4b-166">圖 4-24 表示組成應用程式的 Docker 叢集中將 Azure 容器服務 (ACS) 的對應。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-166">Figure 4-24 represents how a Docker cluster for composed applications maps to Azure Container Service (ACS).</span></span>

<span data-ttu-id="8bd4b-167">ACS 提供簡化建立、 設定及管理叢集的執行容器化應用程式已預先設定的虛擬機器的方式。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-167">ACS provides a way to simplify the creation, configuration, and management of a cluster of virtual machines that are preconfigured to run containerized applications.</span></span> <span data-ttu-id="8bd4b-168">ACS 使用最佳化的組態的熱門的開放原始碼排程和協調流程工具，讓您使用現有的技術或大量且不斷社群專業能力來部署和管理容器應用程式在 Microsoft Azure 上的主體上繪製.</span><span class="sxs-lookup"><span data-stu-id="8bd4b-168">Using an optimized configuration of popular open-source scheduling and orchestration tools, ACS enables you to use your existing skills or draw on a large and growing body of community expertise to deploy and manage container-based applications on Microsoft Azure.</span></span>

<span data-ttu-id="8bd4b-169">Azure 容器服務進行最佳化熱門 Docker 群集的開放原始碼工具和技術的組態，特別針對 Azure。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-169">Azure Container Service optimizes the configuration of popular Docker clustering open source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="8bd4b-170">您會取得開啟的方案，提供您的容器和應用程式組態的可攜性。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-170">You get an open solution that offers portability for both your containers and your application configuration.</span></span> <span data-ttu-id="8bd4b-171">您選取大小、 主機、 數目和 orchestrator 工具，且容器服務會處理所有其他項目。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-171">You select the size, the number of hosts, and the orchestrator tools, and Container Service handles everything else.</span></span>

![](./media/image28.png)

<span data-ttu-id="8bd4b-172">**圖 4-24**。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-172">**Figure 4-24**.</span></span> <span data-ttu-id="8bd4b-173">Azure 容器服務中的群集選項</span><span class="sxs-lookup"><span data-stu-id="8bd4b-173">Clustering choices in Azure Container Service</span></span>

<span data-ttu-id="8bd4b-174">ACS 會利用 Docker 映像，以確保您的應用程式容器可完整移植。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-174">ACS leverages Docker images to ensure that your application containers are fully portable.</span></span> <span data-ttu-id="8bd4b-175">它支援您選擇的開放原始碼的協調流程平台，如 DC/OS （由 Apache Mesos 所提供）、 Kubernetes （原本所建立 Google），以及 Docker Swarm，以確保這些應用程式，可以調整到數千、 數萬甚至數千張的容器。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-175">It supports your choice of open-source orchestration platforms like DC/OS (powered by Apache Mesos), Kubernetes (originally created by Google), and Docker Swarm, to ensure that these applications can be scaled to thousands or even tens of thousands of containers.</span></span>

<span data-ttu-id="8bd4b-176">Azure 容器服務可讓您利用 Azure 的企業級功能仍然維持應用程式可攜性，包括協調流程層級。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-176">The Azure Container service enables you to take advantage of the enterprise-grade features of Azure while still maintaining application portability, including at the orchestration layers.</span></span>

![](./media/image29.png)

<span data-ttu-id="8bd4b-177">**圖 4-25**。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-177">**Figure 4-25**.</span></span> <span data-ttu-id="8bd4b-178">在 ACS 中 orchestrators</span><span class="sxs-lookup"><span data-stu-id="8bd4b-178">Orchestrators in ACS</span></span>

<span data-ttu-id="8bd4b-179">所示圖 4-25，Azure 容器服務是只是為了部署 DC/OS、 Kubernetes 或 Docker Swarm，Azure 提供的基礎結構，但是 ACS 未實作任何其他 orchestrator。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-179">As shown in Figure 4-25, Azure Container Service is simply the infrastructure provided by Azure in order to deploy DC/OS, Kubernetes or Docker Swarm, but ACS does not implement any additional orchestrator.</span></span> <span data-ttu-id="8bd4b-180">因此，ACS 不 orchestrator 在這種情況，會利用現有的開放原始碼 orchestrators 容器的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-180">Therefore, ACS is not an orchestrator as such, only an infrastructure that leverages existing open-source orchestrators for containers.</span></span>

<span data-ttu-id="8bd4b-181">使用方式的觀點而言，Azure 容器服務的目標是提供容器的裝載環境使用熱門的開放原始碼工具和技術。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-181">From a usage perspective, the goal of Azure Container Service is to provide a container hosting environment by using popular open-source tools and technologies.</span></span> <span data-ttu-id="8bd4b-182">為此，它會為您所選擇的 orchestrator 公開標準的應用程式開發介面端點。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-182">To this end, it exposes the standard API endpoints for your chosen orchestrator.</span></span> <span data-ttu-id="8bd4b-183">藉由使用這些端點，您可以利用這些端點可以彼此通訊的任何軟體。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-183">By using these endpoints, you can leverage any software that can talk to those endpoints.</span></span> <span data-ttu-id="8bd4b-184">比方說，在 Docker Swarm 結束點的情況下，您可能會選擇使用 Docker 命令列介面 (CLI)。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-184">For example, in the case of the Docker Swarm endpoint, you might choose to use the Docker command-line interface (CLI).</span></span> <span data-ttu-id="8bd4b-185">DC/作業系統，您可能會選擇使用 DC/OS CLI。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-185">For DC/OS, you might choose to use the DC/OS CLI.</span></span>

### <a name="getting-started-with-azure-container-service"></a><span data-ttu-id="8bd4b-186">開始使用 Azure 容器服務</span><span class="sxs-lookup"><span data-stu-id="8bd4b-186">Getting started with Azure Container Service</span></span> 

<span data-ttu-id="8bd4b-187">若要開始使用 Azure 容器服務，您必須部署從 Azure 入口網站與 Azure 容器服務的叢集使用 Azure Resource Manager 範本或[CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-187">To begin using Azure Container Service, you deploy an Azure Container Service cluster from the Azure portal by using an Azure Resource Manager template or the [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli).</span></span> <span data-ttu-id="8bd4b-188">可用的範本包含[Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)， [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes)，和[DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos)。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-188">Available templates include [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), and [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos).</span></span> <span data-ttu-id="8bd4b-189">快速入門範本可以修改為包含其他或進階的 Azure 組態。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-189">The quickstart templates can be modified to include additional or advanced Azure configuration.</span></span> <span data-ttu-id="8bd4b-190">如需有關如何部署 Azure 容器服務叢集的詳細資訊，請參閱[部署 Azure 容器服務叢集](https://docs.microsoft.com/azure/container-service/container-service-deployment)Azure 網站上。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-190">For more information on deploying an Azure Container Service cluster, see [Deploy an Azure Container Service cluster](https://docs.microsoft.com/azure/container-service/container-service-deployment) on the Azure website.</span></span>

<span data-ttu-id="8bd4b-191">沒有任何預設安裝的 ACS 一部分的軟體的費用。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-191">There are no fees for any of the software installed by default as part of ACS.</span></span> <span data-ttu-id="8bd4b-192">使用開放原始碼軟體，來實作所有預設選項。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-192">All default options are implemented with open-source software.</span></span>

<span data-ttu-id="8bd4b-193">標準的、 D、 DS、 G 及 GS 系列 Azure 中 Linux 虛擬機器目前使用 ACS。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-193">ACS is currently available for Standard A, D, DS, G, and GS series Linux virtual machines in Azure.</span></span> <span data-ttu-id="8bd4b-194">您必須支付只選擇，計算執行個體，以及其他基本基礎結構耗用的資源，例如儲存體和網路功能。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-194">You are charged only for the compute instances you choose, as well as the other underlying infrastructure resources consumed, such as storage and networking.</span></span> <span data-ttu-id="8bd4b-195">沒有任何累加的費用，acs 本身。</span><span class="sxs-lookup"><span data-stu-id="8bd4b-195">There are no incremental charges for ACS itself.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8bd4b-196">其他資源</span><span class="sxs-lookup"><span data-stu-id="8bd4b-196">Additional resources</span></span>

-   <span data-ttu-id="8bd4b-197">**裝載 Azure 容器服務方案的 Docker 容器簡介**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)</span><span class="sxs-lookup"><span data-stu-id="8bd4b-197">**Introduction to Docker container hosting solutions with Azure Container Service**
[*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)</span></span>

-   <span data-ttu-id="8bd4b-198">**Docker 群集概觀**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)</span><span class="sxs-lookup"><span data-stu-id="8bd4b-198">**Docker Swarm overview**
[*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)</span></span>

-   <span data-ttu-id="8bd4b-199">**廣域模式概觀**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)</span><span class="sxs-lookup"><span data-stu-id="8bd4b-199">**Swarm mode overview**
[*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)</span></span>

-   <span data-ttu-id="8bd4b-200">**Mesosphere DC/OS 概觀**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)</span><span class="sxs-lookup"><span data-stu-id="8bd4b-200">**Mesosphere DC/OS Overview**
[*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)</span></span>

-   <span data-ttu-id="8bd4b-201">**Kubernetes。**</span><span class="sxs-lookup"><span data-stu-id="8bd4b-201">**Kubernetes.**</span></span> <span data-ttu-id="8bd4b-202">官方網站。 \\</span><span class="sxs-lookup"><span data-stu-id="8bd4b-202">The official site.\\</span></span>
    [<span data-ttu-id="8bd4b-203">*http://kubernetes.io/*</span><span class="sxs-lookup"><span data-stu-id="8bd4b-203">*http://kubernetes.io/*</span></span>](http://kubernetes.io/)


>[!div class="step-by-step"]
<span data-ttu-id="8bd4b-204">[上一個](具有恢復功能-高的可用性-microservices.md) [下一步] (使用-azure-服務-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="8bd4b-204">[Previous] (resilient-high-availability-microservices.md) [Next] (using-azure-service-fabric.md)</span></span>
