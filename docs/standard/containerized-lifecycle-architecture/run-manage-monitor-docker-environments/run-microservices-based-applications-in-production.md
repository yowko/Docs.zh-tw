---
title: 在生產環境中執行組成和 microservices 為基礎的應用程式
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1ba71a02c1f800fd65462b0df9a435af87c9a37f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a><span data-ttu-id="af453-103">在生產環境中執行組成和 microservices 為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="af453-103">Run composed and microservices-based applications in production environments</span></span>

<span data-ttu-id="af453-104">由多個 microservices 組成的應用程式需要部署到 orchestrator 叢集，以簡化部署的複雜性，並將其從 IT 的觀點可行。</span><span class="sxs-lookup"><span data-stu-id="af453-104">Applications composed by multiple microservices do need to be deployed into orchestrator clusters in order to simplify the complexity of deployment and make it viable from an IT point of view.</span></span> <span data-ttu-id="af453-105">與 orchestrator 的叢集，不會很難部署和向外延展複雜 microservices 應用程式。</span><span class="sxs-lookup"><span data-stu-id="af453-105">Without an orchestrator cluster, it would be very difficult to deploy and scale-out a complex microservices application.</span></span>

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a><span data-ttu-id="af453-106">簡介 orchestrators、 排程器，以及容器叢集</span><span class="sxs-lookup"><span data-stu-id="af453-106">Introduction to orchestrators, schedulers, and container clusters</span></span>

<span data-ttu-id="af453-107">稍早在本電子書，我們引進*叢集*和*排程器*，討論的軟體架構和開發的一部分。</span><span class="sxs-lookup"><span data-stu-id="af453-107">Earlier in this e-book, we introduced *clusters* and *schedulers* as part of the discussion on software architecture and development.</span></span> <span data-ttu-id="af453-108">Docker 叢集的範例為 Docker Swarm 和 Mesosphere Datacenter 作業系統 (DC/OS)。</span><span class="sxs-lookup"><span data-stu-id="af453-108">Examples of Docker clusters are Docker Swarm and Mesosphere Datacenter Operating System (DC/OS).</span></span> <span data-ttu-id="af453-109">這兩種可以執行 Microsoft Azure 容器服務所提供的基礎結構的一部分。</span><span class="sxs-lookup"><span data-stu-id="af453-109">Both of these can run as a part of the infrastructure provided by Microsoft Azure Container Service.</span></span>

<span data-ttu-id="af453-110">當應用程式會向外延展跨多個主機系統時，會變成吸引人能夠管理每個主機系統和提取出基礎平台的複雜性。</span><span class="sxs-lookup"><span data-stu-id="af453-110">When applications are scaled-out across multiple host systems, the ability to manage each host system and abstract away the complexity of the underlying platform becomes attractive.</span></span> <span data-ttu-id="af453-111">這就是精確 orchestrators 和排程器提供的內容。</span><span class="sxs-lookup"><span data-stu-id="af453-111">That is precisely what orchestrators and schedulers provide.</span></span> <span data-ttu-id="af453-112">讓我們看這裡簡短查看：</span><span class="sxs-lookup"><span data-stu-id="af453-112">Let's take a brief look at them here:</span></span>

-   <span data-ttu-id="af453-113">**排程器 * * * *「 排程 」 是指系統管理員可以載入到建立如何執行特定的容器主機系統上的服務檔案的能力。</span><span class="sxs-lookup"><span data-stu-id="af453-113">**Schedulers*** *"Scheduling" refers to the ability for an administrator to load a service file onto a host system that establishes how to run a specific container.</span></span> <span data-ttu-id="af453-114">通常會以稱為排程啟動 Docker 叢集中的容器。</span><span class="sxs-lookup"><span data-stu-id="af453-114">Launching containers in a Docker cluster tends to be known as scheduling.</span></span> <span data-ttu-id="af453-115">雖然排程的載入服務定義中的較通用的意義上，特定的動作是指排程器負責將連結到主機的 init 系統管理服務中任何所需的容量。</span><span class="sxs-lookup"><span data-stu-id="af453-115">Although scheduling refers to the specific act of loading the service definition, in a more general sense, schedulers are responsible for hooking into a host's init system to manage services in whatever capacity needed.</span></span>

<span data-ttu-id="af453-116">叢集的排程器有多個目標： 有效率地使用叢集的資源，請使用使用者提供位置條件約束，排程應用程式快速不讓它們留在暫止狀態，需要某種程度的"公平性，「 正在強固的錯誤，並一律可供使用。</span><span class="sxs-lookup"><span data-stu-id="af453-116">A cluster scheduler has multiple goals: using the cluster's resources efficiently, working with user-supplied placement constraints, scheduling applications rapidly to not leave them in a pending state, having a degree of "fairness," being robust to errors, and always be available.</span></span>

-   <span data-ttu-id="af453-117">**協調流程 * * * *平台擴充至的主機叢集上部署的複雜、 multicontainer 工作負載的生命週期管理功能。</span><span class="sxs-lookup"><span data-stu-id="af453-117">**Orchestration*** *Platforms extend life-cycle management capabilities to complex, multicontainer workloads deployed on a cluster of hosts.</span></span> <span data-ttu-id="af453-118">藉由抽象化主機基礎結構，協調流程工具可讓使用者將整個叢集視為單一部署目標。</span><span class="sxs-lookup"><span data-stu-id="af453-118">By abstracting the host infrastructure, orchestration tools give users a way to treat the entire cluster as a single deployment target.</span></span>

<span data-ttu-id="af453-119">協調流程程序包含工具和可以自動化初始放置或部署每個容器; 從應用程式管理的各個層面的平台將容器移到不同的主機，根據其主機的健全狀況或效能;版本控制和輪流更新，以及健全狀況監視縮放比例和容錯移轉，支援的函式等等。</span><span class="sxs-lookup"><span data-stu-id="af453-119">The process of orchestration involves tooling and a platform that can automate all aspects of application management from initial placement or deployment per container; moving containers to different hosts depending on its host's health or performance; versioning and rolling updates and health monitoring functions that support scaling and failover; and many more.</span></span>

<span data-ttu-id="af453-120">協調流程是廣泛的詞彙，意指容器排程、 叢集管理，以及可能在佈建其他主機。</span><span class="sxs-lookup"><span data-stu-id="af453-120">Orchestration is a broad term that refers to container scheduling, cluster management, and possibly the provisioning of additional hosts.</span></span>

<span data-ttu-id="af453-121">Orchestrators 和排程器所提供的功能是以開發並從從頭開始建立非常複雜，因此您通常會想要讓廠商所提供的協調流程解決方案。</span><span class="sxs-lookup"><span data-stu-id="af453-121">The capabilities provided by orchestrators and schedulers are very complex to develop and create from scratch, and therefore you usually would want to make use of orchestration solutions offered by vendors.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="af453-122">[上一個] (index.md) [下一步] (管理-生產-docker-environments.md)</span><span class="sxs-lookup"><span data-stu-id="af453-122">[Previous] (index.md) [Next] (manage-production-docker-environments.md)</span></span>
