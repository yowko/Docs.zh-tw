---
title: 什麼是 Docker？
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c471c4bc1588aaa6c0e145ede0b67ab5340f254a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="what-is-docker"></a><span data-ttu-id="e13aa-103">什麼是 Docker？</span><span class="sxs-lookup"><span data-stu-id="e13aa-103">What is Docker?</span></span>

<span data-ttu-id="e13aa-104">[Docker](https://www.docker.com/)是[開放原始碼專案](https://github.com/docker/docker)自動化應用程式的部署，做為可攜式且足可雲端或內部部署中執行的容器 (請參閱圖 1-2）。</span><span class="sxs-lookup"><span data-stu-id="e13aa-104">[Docker](https://www.docker.com/) is an [open-source project](https://github.com/docker/docker) for automating the deployment of applications as portable, self-sufficient containers that can run in the cloud or on-premises (see Figure 1-2).</span></span> <span data-ttu-id="e13aa-105">Docker 也有[公司](https://www.docker.com/)的升級，並開發這項技術，在與雲端，Linux 和 Windows 廠商，包括 Microsoft 的共同作業工作。</span><span class="sxs-lookup"><span data-stu-id="e13aa-105">Docker is also a [company](https://www.docker.com/) that promotes and develops this technology, working in collaboration with cloud, Linux, and Windows vendors, including Microsoft.</span></span>

![](./media/image2.png)

<span data-ttu-id="e13aa-106">圖 1-2: Docker 部署混合式雲端的所有層級的容器</span><span class="sxs-lookup"><span data-stu-id="e13aa-106">Figure 1-2: Docker deploys containers at all layers of the hybrid cloud</span></span>

<span data-ttu-id="e13aa-107">Docker 映像容器可以原生 Linux 及 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="e13aa-107">Docker image containers can run natively on Linux and Windows.</span></span> <span data-ttu-id="e13aa-108">不過，Windows 映像可以只在 Windows 主機上執行，而且 Linux 映像可以只在 Linux 主機，這表示主機伺服器或 VM 上執行。</span><span class="sxs-lookup"><span data-stu-id="e13aa-108">However, Windows images can run only on Windows hosts and Linux images can run only on Linux hosts, meaning a host server or a VM.</span></span>

<span data-ttu-id="e13aa-109">開發人員可以在 Windows、 Linux 或 macOS 使用開發環境。</span><span class="sxs-lookup"><span data-stu-id="e13aa-109">Developers can use development environments on Windows, Linux, or macOS.</span></span> <span data-ttu-id="e13aa-110">在開發電腦上開發人員會執行的 docker 映像部署，包括應用程式和其相依性的 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="e13aa-110">On the development computer, the developer runs a Docker host to which Docker images are deployed, including the app and its dependencies.</span></span> <span data-ttu-id="e13aa-111">開發人員在 Linux 上或在 Mac 上使用 Linux 為基礎的 Docker 主機，而且可以建立 Linux 容器的影像。</span><span class="sxs-lookup"><span data-stu-id="e13aa-111">Developers who work on Linux or on the Mac use a Docker host that is Linux based, and they can create images only for Linux containers.</span></span> <span data-ttu-id="e13aa-112">(在 Mac 上工作的開發人員可以編輯的程式碼，或執行 Docker 命令列介面\[CLI\]從 macOS，但是，撰寫本文時，容器無法執行直接在 macOS。)在 Windows 合作的開發人員可以 for Linux 或 Windows 容器建立映像。</span><span class="sxs-lookup"><span data-stu-id="e13aa-112">(Developers working on the Mac can edit code or run the Docker command-line interface \[CLI\] from macOS, but, as of this writing, containers do not run directly on macOS.) Developers who work on Windows can create images for either Linux or Windows Containers.</span></span>

<span data-ttu-id="e13aa-113">若要裝載在開發環境中的容器，並提供額外的開發人員工具，Docker 隨附[Docker Community Edition (CE)](https://www.docker.com/community-edition) Windows 或 macOS。</span><span class="sxs-lookup"><span data-stu-id="e13aa-113">To host containers in development environments and provide additional developer tools, Docker ships [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows or for macOS.</span></span> <span data-ttu-id="e13aa-114">這些產品會安裝必要的 VM （Docker 主機） 來裝載容器。</span><span class="sxs-lookup"><span data-stu-id="e13aa-114">These products install the necessary VM (the Docker host) to host the containers.</span></span> <span data-ttu-id="e13aa-115">Docker 也會出現[Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)，這針對企業開發所設計，並且由 IT 團隊建置、 出貨，而且在生產中執行大型的業務關鍵應用程式。</span><span class="sxs-lookup"><span data-stu-id="e13aa-115">Docker also makes available [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), which is designed for enterprise development and is used by IT teams who build, ship, and run large business-critical applications in production.</span></span>

<span data-ttu-id="e13aa-116">若要執行[Windows 容器](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview)，有兩種類型的執行階段：</span><span class="sxs-lookup"><span data-stu-id="e13aa-116">To run [Windows Containers](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview), there are two types of runtimes:</span></span>

-   <span data-ttu-id="e13aa-117">**Windows Server 容器** 此執行階段提供透過程序和命名空間隔離技術的應用程式隔離。</span><span class="sxs-lookup"><span data-stu-id="e13aa-117">**Windows Server Container** This runtime provides application isolation through process and namespace isolation technology.</span></span> <span data-ttu-id="e13aa-118">與 Windows Server 容器共用核心的對象為容器主機以及在此主機上執行的所有容器。</span><span class="sxs-lookup"><span data-stu-id="e13aa-118">A Windows Server Container shares a kernel with the container host and with all containers running on the host.</span></span>

-   <span data-ttu-id="e13aa-119">**HYPER-V 容器** 這會展開，Windows Server 容器提供高度最佳化的 VM 中執行每個容器的隔離。</span><span class="sxs-lookup"><span data-stu-id="e13aa-119">**Hyper-V Container** This expands on the isolation provided by Windows Server Containers by running each container in a highly optimized VM.</span></span> <span data-ttu-id="e13aa-120">在此組態中，容器主機的核心不會與 Hyper-V 容器共用，以提供更好的隔離。</span><span class="sxs-lookup"><span data-stu-id="e13aa-120">In this configuration, the kernel of the container host is not shared with the Hyper-V Containers, providing better isolation.</span></span>

<span data-ttu-id="e13aa-121">這些容器的映像建立相同的方式和功能相同。</span><span class="sxs-lookup"><span data-stu-id="e13aa-121">The images for these containers are created in the same way and function the same.</span></span> <span data-ttu-id="e13aa-122">不同之處在於從映像建立容器時，執行 HYPER-V 容器需要額外的參數。</span><span class="sxs-lookup"><span data-stu-id="e13aa-122">The difference is in how the container is created from the image—running a Hyper-V Container requires an extra parameter.</span></span> <span data-ttu-id="e13aa-123">如需詳細資料，請參閱 [Hyper-V 容器](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-123">For details, see [Hyper-V Containers](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).</span></span>

## <a name="comparing-docker-containers-with-vms"></a><span data-ttu-id="e13aa-124">比較與 Vm 的 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="e13aa-124">Comparing Docker containers with VMs</span></span>

<span data-ttu-id="e13aa-125">圖 1-3 顯示比較 Vm 和 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="e13aa-125">Figure 1-3 shows a comparison between VMs and Docker containers.</span></span>

<span data-ttu-id="e13aa-126">因為容器需要少很多的資源 （例如，它們不需要在完整作業系統），它們是容易部署而且快速啟動。</span><span class="sxs-lookup"><span data-stu-id="e13aa-126">Because containers require far fewer resources (for example, they do not need a full OS), they are easy to deploy and they start fast.</span></span> <span data-ttu-id="e13aa-127">這可讓您擁有更高的密度，這表示，您可以執行更多服務在相同的硬體單元，藉此降低成本。</span><span class="sxs-lookup"><span data-stu-id="e13aa-127">This makes it possible for you to have higher density, meaning that you can run more services on the same hardware unit, thereby reducing costs.</span></span>

<span data-ttu-id="e13aa-128">在相同的核心上執行的副作用，您可以達到比 Vm 更少隔離。</span><span class="sxs-lookup"><span data-stu-id="e13aa-128">As a side effect of running on the same kernel, you achieve less isolation than VMs.</span></span>

<span data-ttu-id="e13aa-129">映像的主要目標是跨不同的部署建立相同的環境 (相依性)。</span><span class="sxs-lookup"><span data-stu-id="e13aa-129">The main goal of an image is that it makes the environment (dependencies) the same across different deployments.</span></span> <span data-ttu-id="e13aa-130">這表示您可以在自己的電腦上對它進行偵錯，再將它部署到另一部電腦，保證有相同的環境。</span><span class="sxs-lookup"><span data-stu-id="e13aa-130">This means that you can debug it on your machine and then deploy it to another machine with the same environment guaranteed.</span></span>

<span data-ttu-id="e13aa-131">容器映像是封裝的應用程式或服務，並將它部署可靠且可重現的方式的方法。</span><span class="sxs-lookup"><span data-stu-id="e13aa-131">A container image is a way to package an app or service and deploy it in a reliable and reproducible manner.</span></span> <span data-ttu-id="e13aa-132">在這一方面，Docker 不是一種技術，它也是基本概念和程序。</span><span class="sxs-lookup"><span data-stu-id="e13aa-132">In this respect, Docker is not only a technology, it's also a philosophy and a process.</span></span>

<span data-ttu-id="e13aa-133">當使用 Docker 時，您將無法聽到說出的開發人員、"﹐ 我的電腦，為何不在生產環境中？ 」</span><span class="sxs-lookup"><span data-stu-id="e13aa-133">When using Docker, you will not hear developers say, "It works on my machine, why not in production?"</span></span> <span data-ttu-id="e13aa-134">他們可以只需說，"執行 docker"因為封裝的 Docker 應用程式可以執行任何支援的 Docker 環境，而且它會執行它要設定所有的部署目的地 （開發、 品管暫存、 生產等。） 的方式。</span><span class="sxs-lookup"><span data-stu-id="e13aa-134">They can simply say, "It runs on Docker," because the packaged Docker application can be run on any supported Docker environment, and it will run the way it was intended to on all deployment destinations (Dev, QA, staging, production, etc.).</span></span>

![](./media/image3.png)

<span data-ttu-id="e13aa-135">圖 1-3： 的傳統 Vm 至 Docker 容器的比較</span><span class="sxs-lookup"><span data-stu-id="e13aa-135">Figure 1-3: Comparison of traditional VMs to Docker containers</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e13aa-136">[上一頁] (index.md) [上一頁] (docker-terminology.md)</span><span class="sxs-lookup"><span data-stu-id="e13aa-136">[Previous] (index.md) [Next] (docker-terminology.md)</span></span>
