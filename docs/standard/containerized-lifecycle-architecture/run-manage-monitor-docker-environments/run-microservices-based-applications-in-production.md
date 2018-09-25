---
title: 在生產環境中執行撰寫和以微服務為基礎的應用程式
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 18e6cb1fb5f496b66c89cb8e009a67894b8a76ad
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086537"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a><span data-ttu-id="feddb-103">在生產環境中執行撰寫和以微服務為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="feddb-103">Run composed and microservices-based applications in production environments</span></span>

<span data-ttu-id="feddb-104">由多個微服務組成的應用程式需要部署到 orchestrator 叢集，以簡化部署的複雜性，並使其從 IT 觀點來看變為可用。</span><span class="sxs-lookup"><span data-stu-id="feddb-104">Applications composed by multiple microservices do need to be deployed into orchestrator clusters in order to simplify the complexity of deployment and make it viable from an IT point of view.</span></span> <span data-ttu-id="feddb-105">協調器叢集，不會很難部署和向外延展的複雜的微服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="feddb-105">Without an orchestrator cluster, it would be very difficult to deploy and scale-out a complex microservices application.</span></span>

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a><span data-ttu-id="feddb-106">Orchestrator、 排程器及容器叢集簡介</span><span class="sxs-lookup"><span data-stu-id="feddb-106">Introduction to orchestrators, schedulers, and container clusters</span></span>

<span data-ttu-id="feddb-107">稍早在本電子書，我們引進了*叢集*並*排程器*，討論的軟體架構設計和開發的一部分。</span><span class="sxs-lookup"><span data-stu-id="feddb-107">Earlier in this e-book, we introduced *clusters* and *schedulers* as part of the discussion on software architecture and development.</span></span> <span data-ttu-id="feddb-108">Docker Swarm 和 Mesosphere Datacenter Operating System (DC/OS)，就會是 Docker 叢集的範例。</span><span class="sxs-lookup"><span data-stu-id="feddb-108">Examples of Docker clusters are Docker Swarm and Mesosphere Datacenter Operating System (DC/OS).</span></span> <span data-ttu-id="feddb-109">這兩種都可以執行 Microsoft Azure Container Service 所提供的基礎結構的一部分。</span><span class="sxs-lookup"><span data-stu-id="feddb-109">Both of these can run as a part of the infrastructure provided by Microsoft Azure Container Service.</span></span>

<span data-ttu-id="feddb-110">當應用程式會向外延展跨多個主機系統時，能夠管理每個主機系統，並抽離基礎平台的複雜性會成為吸引人。</span><span class="sxs-lookup"><span data-stu-id="feddb-110">When applications are scaled-out across multiple host systems, the ability to manage each host system and abstract away the complexity of the underlying platform becomes attractive.</span></span> <span data-ttu-id="feddb-111">這就是精確地協調器和排程器提供的內容。</span><span class="sxs-lookup"><span data-stu-id="feddb-111">That is precisely what orchestrators and schedulers provide.</span></span> <span data-ttu-id="feddb-112">以下讓我們簡短看：</span><span class="sxs-lookup"><span data-stu-id="feddb-112">Let's take a brief look at them here:</span></span>

- <span data-ttu-id="feddb-113">**排程器**：</span><span class="sxs-lookup"><span data-stu-id="feddb-113">**Schedulers**.</span></span><span data-ttu-id="feddb-114"> 「 排程 」 指的是系統管理員可以載入到建立如何執行特定的容器主機系統上的服務檔案的能力。</span><span class="sxs-lookup"><span data-stu-id="feddb-114"> "Scheduling" refers to the ability for an administrator to load a service file onto a host system that establishes how to run a specific container.</span></span> <span data-ttu-id="feddb-115">啟動 Docker 叢集中的容器，通常稱為排程。</span><span class="sxs-lookup"><span data-stu-id="feddb-115">Launching containers in a Docker cluster tends to be known as scheduling.</span></span> <span data-ttu-id="feddb-116">雖然排程是指特定的動作，載入服務定義中，更一般的意義而言，排程器負責連結到主機的 init 系統，來管理服務中任何所需的容量。</span><span class="sxs-lookup"><span data-stu-id="feddb-116">Although scheduling refers to the specific act of loading the service definition, in a more general sense, schedulers are responsible for hooking into a host's init system to manage services in whatever capacity needed.</span></span>

   <span data-ttu-id="feddb-117">叢集排程器有多個目標： 有效率地使用叢集的資源，請使用使用者提供的放置條件約束，排程應用程式快速不將它們保留在擱置狀態，需要某種程度的 「 公平起見，「 正在強固的錯誤，以及可使用。</span><span class="sxs-lookup"><span data-stu-id="feddb-117">A cluster scheduler has multiple goals: using the cluster's resources efficiently, working with user-supplied placement constraints, scheduling applications rapidly to not leave them in a pending state, having a degree of "fairness," being robust to errors, and always be available.</span></span>

- <span data-ttu-id="feddb-118">**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="feddb-118">**Orchestration**.</span></span><span data-ttu-id="feddb-119"> 平台擴充為複雜、 多容器的主機叢集上部署的工作負載的生命週期管理功能。</span><span class="sxs-lookup"><span data-stu-id="feddb-119"> Platforms extend life-cycle management capabilities to complex, multicontainer workloads deployed on a cluster of hosts.</span></span> <span data-ttu-id="feddb-120">藉由抽象化主機基礎結構，協調流程工具可讓使用者將在整個叢集中視為單一部署目標。</span><span class="sxs-lookup"><span data-stu-id="feddb-120">By abstracting the host infrastructure, orchestration tools give users a way to treat the entire cluster as a single deployment target.</span></span>

   <span data-ttu-id="feddb-121">協調流程程序包含工具和可以自動化初始放置或每個容器; 部署的應用程式管理的各個層面的平台將容器移至不同的主控件，取決於其主機的健康狀態或效能;版本控制和輪流更新，以及健全狀況監視支援縮放比例和容錯移轉，函式更多選擇。</span><span class="sxs-lookup"><span data-stu-id="feddb-121">The process of orchestration involves tooling and a platform that can automate all aspects of application management from initial placement or deployment per container; moving containers to different hosts depending on its host's health or performance; versioning and rolling updates and health monitoring functions that support scaling and failover; and many more.</span></span>

   <span data-ttu-id="feddb-122">協調流程是一個廣義的詞彙，指的是容器排程、 叢集管理，以及可能在佈建其他主機。</span><span class="sxs-lookup"><span data-stu-id="feddb-122">Orchestration is a broad term that refers to container scheduling, cluster management, and possibly the provisioning of additional hosts.</span></span>

<span data-ttu-id="feddb-123">協調器和排程器所提供的功能會很複雜，開發並從頭建立，並因此您通常會想要讓廠商所提供的協調流程解決方案的使用。</span><span class="sxs-lookup"><span data-stu-id="feddb-123">The capabilities provided by orchestrators and schedulers are very complex to develop and create from scratch, and therefore you usually would want to make use of orchestration solutions offered by vendors.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="feddb-124">[上一頁](index.md)
[下一頁](manage-production-docker-environments.md)</span><span class="sxs-lookup"><span data-stu-id="feddb-124">[Previous](index.md)
[Next](manage-production-docker-environments.md)</span></span>
