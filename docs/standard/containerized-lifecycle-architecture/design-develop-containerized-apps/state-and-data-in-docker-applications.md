---
title: Docker 應用程式中的狀態和資料
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a9f0750dbcffd051e9dae7d9f4f74b921e30af29
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="state-and-data-in-docker-applications"></a><span data-ttu-id="0d385-103">Docker 應用程式中的狀態和資料</span><span class="sxs-lookup"><span data-stu-id="0d385-103">State and data in Docker applications</span></span>

<span data-ttu-id="0d385-104">基本的容器項目是不變性。</span><span class="sxs-lookup"><span data-stu-id="0d385-104">A primitive of containers is immutability.</span></span> <span data-ttu-id="0d385-105">相較於 VM，容器就不會經常為消失。</span><span class="sxs-lookup"><span data-stu-id="0d385-105">When compared to a VM, containers don't disappear as a common occurrence.</span></span> <span data-ttu-id="0d385-106">VM 可能會以不同的形式從終止程序、 多載的 CPU 或完整或失敗的磁碟失敗。</span><span class="sxs-lookup"><span data-stu-id="0d385-106">A VM might fail in various forms from dead processes, overloaded CPU, or a full or failed disk.</span></span> <span data-ttu-id="0d385-107">棒的是，我們預期可用 VM 和 RAID 磁碟機以確保磁碟機失敗維護資料相差不多。</span><span class="sxs-lookup"><span data-stu-id="0d385-107">Yet, we expect the VM to be available and RAID drives are commonplace to assure drive failures maintain data.</span></span>

<span data-ttu-id="0d385-108">不過，容器凡是系統認為是處理程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d385-108">However, containers are thought to be instances of processes.</span></span> <span data-ttu-id="0d385-109">處理程序不會維護持久狀態。</span><span class="sxs-lookup"><span data-stu-id="0d385-109">A process doesn't maintain durable state.</span></span> <span data-ttu-id="0d385-110">即使容器可以寫入其本機儲存體，假設該執行個體將會無限期周圍就會相當於假設單一複本記憶體將會永久性。</span><span class="sxs-lookup"><span data-stu-id="0d385-110">Even though a container can write to its local storage, assuming that that instance will be around indefinitely would be equivalent to assuming a single-copy memory will be durable.</span></span> <span data-ttu-id="0d385-111">您應該假設重複容器，例如處理程序，刪除，或當容器 orchestrator 的管理，可能會移動。</span><span class="sxs-lookup"><span data-stu-id="0d385-111">You should assume that containers, like processes, are duplicated, killed, or, when managed with a container orchestrator, they might be moved.</span></span>

<span data-ttu-id="0d385-112">Docker 使用功能，又稱為*重疊檔案系統*若要實作儲存任何寫入時複製程序更新容器，相較於原始的映像所依據的根檔案系統資訊。</span><span class="sxs-lookup"><span data-stu-id="0d385-112">Docker uses a feature known as an *overlay file system* to implement a copy-on-write process that stores any updated information to the root file system of a container, compared to the original image on which it is based.</span></span> <span data-ttu-id="0d385-113">如果從系統，接下來刪除容器，這些變更會遺失。</span><span class="sxs-lookup"><span data-stu-id="0d385-113">These changes are lost if the container is subsequently deleted from the system.</span></span> <span data-ttu-id="0d385-114">一種容器，因此，沒有永續性儲存體預設。</span><span class="sxs-lookup"><span data-stu-id="0d385-114">A container, therefore, does not have persistent storage by default.</span></span> <span data-ttu-id="0d385-115">雖然可以儲存容器的狀態，在設計系統，以解決這個問題會是與容器架構的原則衝突。</span><span class="sxs-lookup"><span data-stu-id="0d385-115">Although it's possible to save the state of a container, designing a system around this would be in conflict with the principle of container architecture.</span></span>

<span data-ttu-id="0d385-116">若要管理 Docker 應用程式中的永續性資料，有常見的解決方案：</span><span class="sxs-lookup"><span data-stu-id="0d385-116">To manage persistent data in Docker applications, there are common solutions:</span></span>

-   <span data-ttu-id="0d385-117">[**資料磁碟區**](https://docs.docker.com/engine/tutorials/dockervolumes/) 這些掛接至主機，如剛才所述。</span><span class="sxs-lookup"><span data-stu-id="0d385-117">[**Data volumes**](https://docs.docker.com/engine/tutorials/dockervolumes/) These mount to the host, as just noted.</span></span>

-   <span data-ttu-id="0d385-118">[**資料磁碟區容器**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) 這些容器，使用可以循環的外部容器提供共用存放裝置。</span><span class="sxs-lookup"><span data-stu-id="0d385-118">[**Data volume containers**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) These provide shared storage across containers, using an external container that can cycle.</span></span>

-   <span data-ttu-id="0d385-119">[**磁碟區外掛程式**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) 這些掛接至遠端位置，提供長期持續性的磁碟區。</span><span class="sxs-lookup"><span data-stu-id="0d385-119">[**Volume Plugins**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) These mount volumes to remote locations, providing long-term persistence.</span></span>

-   <span data-ttu-id="0d385-120">**遠端資料來源** 範例包括 SQL 和 NO SQL 資料庫或服務，例如 Redis 快取。</span><span class="sxs-lookup"><span data-stu-id="0d385-120">**Remote data sources** Examples include SQL and NO-SQL databases or cache services like Redis.</span></span>

-   <span data-ttu-id="0d385-121">[**Azure 儲存體**](https://docs.microsoft.com/azure/storage/) 這會提供地理可散布平台做為服務 (PaaS) 儲存，以長期持續性提供最佳的容器。</span><span class="sxs-lookup"><span data-stu-id="0d385-121">[**Azure Storage**](https://docs.microsoft.com/azure/storage/) This provides geo distributable platform as a service (PaaS) storage, providing the best of containers as long-term persistence.</span></span>

<span data-ttu-id="0d385-122">資料磁碟區會特別指定略過的一或多個容器內的目錄[聯集的檔案系統](https://docs.docker.com/v1.8/reference/glossary#union-file-system)。</span><span class="sxs-lookup"><span data-stu-id="0d385-122">Data volumes are specially designated directories within one or more containers that bypass the [Union File System](https://docs.docker.com/v1.8/reference/glossary#union-file-system).</span></span> <span data-ttu-id="0d385-123">資料磁碟區被設計來維護容器的生命週期的獨立資料。</span><span class="sxs-lookup"><span data-stu-id="0d385-123">Data volumes are designed to maintain data, independent of the container's life cycle.</span></span> <span data-ttu-id="0d385-124">Docker 因此永遠不會自動刪除磁碟區時您移除容器，也無法將它不再參考由容器的 「 記憶體回收收集 「 磁碟區。</span><span class="sxs-lookup"><span data-stu-id="0d385-124">Docker therefore never automatically deletes volumes when you remove a container, nor will it "garbage collect" volumes that are no longer referenced by a container.</span></span> <span data-ttu-id="0d385-125">主機作業系統可以瀏覽和編輯任何磁碟區中的資料自由，即盡量不要使用資料磁碟區只是另一個原因。</span><span class="sxs-lookup"><span data-stu-id="0d385-125">The host operating system can browse and edit the data in any volume freely, which is just another reason to use data volumes sparingly.</span></span>

<span data-ttu-id="0d385-126">A[資料磁碟區容器](https://docs.docker.com/v1.8/userguide/dockervolumes/)是一般資料磁碟區。</span><span class="sxs-lookup"><span data-stu-id="0d385-126">A [data volume container](https://docs.docker.com/v1.8/userguide/dockervolumes/) is an improvement over regular data volumes.</span></span> <span data-ttu-id="0d385-127">其本質上是休眠容器具有一個或多個資料磁碟區，在其中建立 （如先前所述）。</span><span class="sxs-lookup"><span data-stu-id="0d385-127">It is essentially a dormant container that has one or more data volumes created within it (as described earlier).</span></span> <span data-ttu-id="0d385-128">資料磁碟區容器可讓您從中央掛接點存取容器。</span><span class="sxs-lookup"><span data-stu-id="0d385-128">The data volume container provides access to containers from a central mount point.</span></span> <span data-ttu-id="0d385-129">這種存取方法的優點是它擷取原始的資料，讓資料容器的邏輯的掛接點的位置。</span><span class="sxs-lookup"><span data-stu-id="0d385-129">The benefit of this method of access is that it abstracts the location of the original data, making the data container a logical mount point.</span></span> <span data-ttu-id="0d385-130">它也允許存取資料容器的磁碟區建立和終結同時資料持續性專用的容器中的 「 應用程式 」 容器。</span><span class="sxs-lookup"><span data-stu-id="0d385-130">It also allows "application" containers accessing the data container volumes to be created and destroyed while keeping the data persistent in a dedicated container.</span></span>

<span data-ttu-id="0d385-131">圖 4-5 顯示規則的 Docker 磁碟區可以置於容器本身之外，但主應用程式伺服器 VM/實體界限內的儲存體。</span><span class="sxs-lookup"><span data-stu-id="0d385-131">Figure 4-5 shows that regular Docker volumes can be placed on storage out of the containers themselves but within the host server/VM physical boundaries.</span></span> <span data-ttu-id="0d385-132">*Docker 磁碟區沒有使用從一部主機伺服器/VM 到另一個磁碟區的能力*。</span><span class="sxs-lookup"><span data-stu-id="0d385-132">*Docker volumes don't have the ability to use a volume from one host server/VM to another*.</span></span>

![](./media/image5.png)

<span data-ttu-id="0d385-133">圖 4-5： 資料磁碟區和容器應用程式/容器的外部資料來源</span><span class="sxs-lookup"><span data-stu-id="0d385-133">Figure 4-5: Data volumes and external data sources for containers apps/containers</span></span>

<span data-ttu-id="0d385-134">因為無法管理個別的實體主機執行的容器之間共用的資料，建議您不要使用磁碟區的商務資料除非 Docker 主機已固定的主機/VM，因為在 orchestrator 中，使用 Docker 容器時容器應該要移動一到另一部主機，根據在叢集中所要執行的最佳化。</span><span class="sxs-lookup"><span data-stu-id="0d385-134">Due to the inability to manage data shared between containers that run on separate physical hosts, it is recommended that you not use volumes for business data unless the Docker host is a fixed host/VM, because when using Docker containers in an orchestrator, containers are expected to be moved from one to another host, depending on the optimizations to be performed by the cluster.</span></span>

<span data-ttu-id="0d385-135">因此，一般資料磁碟區會使用追蹤檔案、 暫存檔案或任何類似的概念，或如果您的容器移動遍及多部主機時不會影響商務資料一致性的良好機制。</span><span class="sxs-lookup"><span data-stu-id="0d385-135">Therefore, regular data volumes are a good mechanism to work with trace files, temporal files, or any similar concept that won't affect the business data consistency if or when your containers are moved across multiple hosts.</span></span>

<span data-ttu-id="0d385-136">磁碟區外掛程式喜歡[Flocker](https://clusterhq.com/flocker/)不同叢集中所有主機之間提供資料。</span><span class="sxs-lookup"><span data-stu-id="0d385-136">Volume plug-ins like [Flocker](https://clusterhq.com/flocker/) provide data across all hosts in a cluster.</span></span> <span data-ttu-id="0d385-137">雖然並非所有的磁碟區外掛程式建立同樣地，磁碟區外掛程式通常提供外部化持續的可靠存放在不可變的容器。</span><span class="sxs-lookup"><span data-stu-id="0d385-137">Although not all volume plug-ins are created equally, volume plug-ins typically provide externalized persistent reliable storage from the immutable containers.</span></span>

<span data-ttu-id="0d385-138">遠端資料來源，例如 SQL Database、 DocumentDB 或遠端像 Redis 快取的快取會做為開發容器不相同。</span><span class="sxs-lookup"><span data-stu-id="0d385-138">Remote data sources and caches like SQL Database, DocumentDB, or a remote cache like Redis would be the same as developing without containers.</span></span> <span data-ttu-id="0d385-139">這是一種慣用及經過驗證，來儲存商業應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="0d385-139">This is one of the preferred, and proven, ways to store business application data.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0d385-140">[上一個] (龐大-applications.md) [下一步] (soa applications.md)</span><span class="sxs-lookup"><span data-stu-id="0d385-140">[Previous] (monolithic-applications.md) [Next] (soa-applications.md)</span></span>
