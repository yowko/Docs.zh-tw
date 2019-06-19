---
title: 在生產環境中執行已撰寫和以微服務為基礎的應用程式
description: 了解在生產環境中執行容器型應用程式的主要元件
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644970"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a><span data-ttu-id="bc99b-103">在生產環境中執行已撰寫和以微服務為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="bc99b-103">Run composed and microservices-based applications in production environments</span></span>

<span data-ttu-id="bc99b-104">由多個微服務組成的應用程式確實需要部署至協調器叢集，以簡化部署的複雜性，並使其從 IT 觀點看來成為可行。</span><span class="sxs-lookup"><span data-stu-id="bc99b-104">Applications composed by multiple microservices do need to be deployed into orchestrator clusters in order to simplify the complexity of deployment and make it viable from an IT point of view.</span></span> <span data-ttu-id="bc99b-105">如果沒有協調器叢集，將難以部署及相應放大複雜的微服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc99b-105">Without an orchestrator cluster, it would be difficult to deploy and scale out a complex microservices application.</span></span>

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a><span data-ttu-id="bc99b-106">協調器、排程器及容器叢集簡介</span><span class="sxs-lookup"><span data-stu-id="bc99b-106">Introduction to orchestrators, schedulers, and container clusters</span></span>

<span data-ttu-id="bc99b-107">本電子書中稍早介紹了「叢集」  和「排程器」  ，作為軟體架構設計和開發討論的一部分。</span><span class="sxs-lookup"><span data-stu-id="bc99b-107">Earlier in this e-book, *clusters* and *schedulers* were introduced as part of the discussion on software architecture and development.</span></span> <span data-ttu-id="bc99b-108">Kubernetes 和 Service Fabric 是 Docker 叢集的範例。</span><span class="sxs-lookup"><span data-stu-id="bc99b-108">Kubernetes and Service Fabric are examples of Docker clusters.</span></span> <span data-ttu-id="bc99b-109">這兩個協調器都可以作為 Microsoft Azure Kubernetes Service 所提供基礎結構的一部分執行。</span><span class="sxs-lookup"><span data-stu-id="bc99b-109">Both of these orchestrators can run as a part of the infrastructure provided by Microsoft Azure Kubernetes Service.</span></span>

<span data-ttu-id="bc99b-110">當應用程式跨多個主機系統相應放大時，管理每個主機系統和抽離基礎平台複雜性的能力會具有吸引力。</span><span class="sxs-lookup"><span data-stu-id="bc99b-110">When applications are scaled-out across multiple host systems, the ability to manage each host system and abstract away the complexity of the underlying platform becomes attractive.</span></span> <span data-ttu-id="bc99b-111">這正是協調器和排程器可提供的功能。</span><span class="sxs-lookup"><span data-stu-id="bc99b-111">That's precisely what orchestrators and schedulers provide.</span></span> <span data-ttu-id="bc99b-112">讓我們看看簡要介紹：</span><span class="sxs-lookup"><span data-stu-id="bc99b-112">Let's take a brief look at them here:</span></span>

- <span data-ttu-id="bc99b-113">**排程器**：</span><span class="sxs-lookup"><span data-stu-id="bc99b-113">**Schedulers**.</span></span><span data-ttu-id="bc99b-114"> 「排程」是指系統管理員將服務檔案載入主機系統的能力，該主機系統會確定如何執行特定容器。</span><span class="sxs-lookup"><span data-stu-id="bc99b-114"> "Scheduling" refers to the ability for an administrator to load a service file onto a host system that establishes how to run a specific container.</span></span> <span data-ttu-id="bc99b-115">在 Docker 叢集中啟動容器通常稱為排程。</span><span class="sxs-lookup"><span data-stu-id="bc99b-115">Launching containers in a Docker cluster tends to be known as scheduling.</span></span> <span data-ttu-id="bc99b-116">雖然排程意指載入服務定義的特定動作，但以更一般的意義而言，排程器負責連結到主機的 init 系統，以所需的容量來管理服務。</span><span class="sxs-lookup"><span data-stu-id="bc99b-116">Although scheduling refers to the specific act of loading the service definition, in a more general sense, schedulers are responsible for hooking into a host's init system to manage services in whatever capacity needed.</span></span>

   <span data-ttu-id="bc99b-117">叢集排程器有多個目標：有效率地使用叢集資源、使用使用者提供的放置條件約束、快速排程應用程式以使其不處於擱置狀態、具有某種程度的「公平性」、較能承受錯誤，以及一律可用。</span><span class="sxs-lookup"><span data-stu-id="bc99b-117">A cluster scheduler has multiple goals: using the cluster's resources efficiently, working with user-supplied placement constraints, scheduling applications rapidly to not leave them in a pending state, having a degree of "fairness," being robust to errors, and always be available.</span></span>

- <span data-ttu-id="bc99b-118">**協調器**。</span><span class="sxs-lookup"><span data-stu-id="bc99b-118">**Orchestrators**.</span></span><span data-ttu-id="bc99b-119"> 平台將生命週期管理功能擴充至部署在主機叢集上複雜的多容器工作負載。</span><span class="sxs-lookup"><span data-stu-id="bc99b-119"> Platforms extend life-cycle management capabilities to complex, multi-container workloads deployed on a cluster of hosts.</span></span> <span data-ttu-id="bc99b-120">藉由將主機基礎結構抽象化，協調器工具可為使用者提供將整個叢集視為單一部署目標的方法。</span><span class="sxs-lookup"><span data-stu-id="bc99b-120">By abstracting the host infrastructure, orchestration tools give users a way to treat the entire cluster as a single deployment target.</span></span>

   <span data-ttu-id="bc99b-121">協調流程程序涉及可從每個容器初始放置或部署中自動化應用程式管理之各個層面自動化的工具和平台；根據主機的健康狀態或效能，將容器移至不同的主機；版本控制和復原更新以及支援調整和容錯移轉的健康狀態監視功能；以及其他更多功能。</span><span class="sxs-lookup"><span data-stu-id="bc99b-121">The process of orchestration involves tooling and a platform that can automate all aspects of application management from initial placement or deployment per container; moving containers to different hosts depending on its host's health or performance; versioning and rolling updates and health monitoring functions that support scaling and failover; and many more.</span></span>

   <span data-ttu-id="bc99b-122">協調流程是一個廣義的詞彙，意指容器排程、叢集管理及可能的額外主機佈建。</span><span class="sxs-lookup"><span data-stu-id="bc99b-122">Orchestration is a broad term that refers to container scheduling, cluster management, and possibly the provisioning of additional hosts.</span></span>

<span data-ttu-id="bc99b-123">協調器和排程器所提供的功能很難從頭開發與建立，因此您通常希望使用廠商提供的協調流程解決方案。</span><span class="sxs-lookup"><span data-stu-id="bc99b-123">The capabilities provided by orchestrators and schedulers are complex to develop and create from scratch, therefore you usually would want to use orchestration solutions offered by vendors.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bc99b-124">[上一頁](index.md)
>[下一頁](manage-production-docker-environments.md)</span><span class="sxs-lookup"><span data-stu-id="bc99b-124">[Previous](index.md)
[Next](manage-production-docker-environments.md)</span></span>
