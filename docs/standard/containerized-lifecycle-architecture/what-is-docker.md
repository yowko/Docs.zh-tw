---
title: 什麼是 Docker？
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 056fb613c078cc407380060dc11890406ac8cffd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197674"
---
# <a name="what-is-docker"></a><span data-ttu-id="ed82f-103">什麼是 Docker？</span><span class="sxs-lookup"><span data-stu-id="ed82f-103">What is Docker?</span></span>

<span data-ttu-id="ed82f-104">[Docker](https://www.docker.com/)已[開放原始碼專案](https://github.com/docker/docker)自動化應用程式部署為可攜式且自給自足的容器，可以執行在雲端或內部部署 (請參閱 圖 1-2）。</span><span class="sxs-lookup"><span data-stu-id="ed82f-104">[Docker](https://www.docker.com/) is an [open-source project](https://github.com/docker/docker) for automating the deployment of applications as portable, self-sufficient containers that can run in the cloud or on-premises (see Figure 1-2).</span></span> <span data-ttu-id="ed82f-105">Docker 也是[公司](https://www.docker.com/)升級及開發這項技術，與雲端、 Linux 和 Windows 廠商，包括 Microsoft 的合作。</span><span class="sxs-lookup"><span data-stu-id="ed82f-105">Docker is also a [company](https://www.docker.com/) that promotes and develops this technology, working in collaboration with cloud, Linux, and Windows vendors, including Microsoft.</span></span>

![](./media/image2.png)

<span data-ttu-id="ed82f-106">圖 1-2: Docker 將容器部署在混合式雲端的所有層級</span><span class="sxs-lookup"><span data-stu-id="ed82f-106">Figure 1-2: Docker deploys containers at all layers of the hybrid cloud</span></span>

<span data-ttu-id="ed82f-107">Docker 映像容器可以原生方式在 Linux 及 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="ed82f-107">Docker image containers can run natively on Linux and Windows.</span></span> <span data-ttu-id="ed82f-108">不過，Windows 映像可以只在 Windows 主機上執行，而且只在 Linux 主機，這表示主機伺服器或 VM 上可以執行的 Linux 映像。</span><span class="sxs-lookup"><span data-stu-id="ed82f-108">However, Windows images can run only on Windows hosts and Linux images can run only on Linux hosts, meaning a host server or a VM.</span></span>

<span data-ttu-id="ed82f-109">開發人員可以使用 Windows、Linux 或 macOS 上的開發環境。</span><span class="sxs-lookup"><span data-stu-id="ed82f-109">Developers can use development environments on Windows, Linux, or macOS.</span></span> <span data-ttu-id="ed82f-110">開發電腦上，開發人員會執行的 docker 映像部署，包括應用程式和其相依性的 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="ed82f-110">On the development computer, the developer runs a Docker host to which Docker images are deployed, including the app and its dependencies.</span></span> <span data-ttu-id="ed82f-111">在 Linux 或 Mac 上工作的開發人員會使用 Linux 型的 Docker 主機，他們只能建立適用於 Linux 容器的映像。</span><span class="sxs-lookup"><span data-stu-id="ed82f-111">Developers who work on Linux or on the Mac use a Docker host that is Linux based, and they can create images only for Linux containers.</span></span> <span data-ttu-id="ed82f-112">(在 Mac 上工作的開發人員可以編輯程式碼，或執行 Docker 命令列介面\[CLI\]從 macOS，但，撰寫本文時，容器無法執行直接在 macOS 上。)在 Windows 上工作的開發人員可以建立適用於 Linux 或 Windows 容器的映像。</span><span class="sxs-lookup"><span data-stu-id="ed82f-112">(Developers working on the Mac can edit code or run the Docker command-line interface \[CLI\] from macOS, but, as of this writing, containers do not run directly on macOS.) Developers who work on Windows can create images for either Linux or Windows Containers.</span></span>

<span data-ttu-id="ed82f-113">為了在開發環境中裝載容器並且提供其他開發人員工具，Docker 提供適用於 Windows 或 macOS 的 [Docker Community Edition (CE)](https://www.docker.com/community-edition)。</span><span class="sxs-lookup"><span data-stu-id="ed82f-113">To host containers in development environments and provide additional developer tools, Docker ships [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows or for macOS.</span></span> <span data-ttu-id="ed82f-114">這些產品都會安裝必要的 VM (Docker 主機) 以裝載容器。</span><span class="sxs-lookup"><span data-stu-id="ed82f-114">These products install the necessary VM (the Docker host) to host the containers.</span></span> <span data-ttu-id="ed82f-115">Docker 也提供 [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)，這是專為企業開發所設計的，由在生產環境中建置、交付及執行大型商務關鍵性應用程式的 IT 小組來使用。</span><span class="sxs-lookup"><span data-stu-id="ed82f-115">Docker also makes available [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), which is designed for enterprise development and is used by IT teams who build, ship, and run large business-critical applications in production.</span></span>

<span data-ttu-id="ed82f-116">若要執行 [Windows 容器](/virtualization/windowscontainers/about/)，有兩種執行階段：</span><span class="sxs-lookup"><span data-stu-id="ed82f-116">To run [Windows Containers](/virtualization/windowscontainers/about/), there are two types of runtimes:</span></span>

-   <span data-ttu-id="ed82f-117">**Windows Server 容器** 此執行階段會提供透過程序和命名空間隔離技術的應用程式隔離。</span><span class="sxs-lookup"><span data-stu-id="ed82f-117">**Windows Server Container** This runtime provides application isolation through process and namespace isolation technology.</span></span> <span data-ttu-id="ed82f-118">與 Windows Server 容器共用核心的對象為容器主機以及在此主機上執行的所有容器。</span><span class="sxs-lookup"><span data-stu-id="ed82f-118">A Windows Server Container shares a kernel with the container host and with all containers running on the host.</span></span>

-   <span data-ttu-id="ed82f-119">**HYPER-V 容器** 這在高度最佳化的 VM 中執行每個容器，Windows Server 容器所提供的隔離上展開。</span><span class="sxs-lookup"><span data-stu-id="ed82f-119">**Hyper-V Container** This expands on the isolation provided by Windows Server Containers by running each container in a highly optimized VM.</span></span> <span data-ttu-id="ed82f-120">在此組態中，容器主機的核心不會與 Hyper-V 容器共用，以提供更好的隔離。</span><span class="sxs-lookup"><span data-stu-id="ed82f-120">In this configuration, the kernel of the container host is not shared with the Hyper-V Containers, providing better isolation.</span></span>

<span data-ttu-id="ed82f-121">這些容器的映像會建立相同的方式和功能相同。</span><span class="sxs-lookup"><span data-stu-id="ed82f-121">The images for these containers are created in the same way and function the same.</span></span> <span data-ttu-id="ed82f-122">不同之處在於如何從映像建立容器時，執行 HYPER-V 容器，需要額外的參數。</span><span class="sxs-lookup"><span data-stu-id="ed82f-122">The difference is in how the container is created from the image—running a Hyper-V Container requires an extra parameter.</span></span> <span data-ttu-id="ed82f-123">如需詳細資料，請參閱 [Hyper-V 容器](/virtualization/windowscontainers/about/)。</span><span class="sxs-lookup"><span data-stu-id="ed82f-123">For details, see [Hyper-V Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="comparing-docker-containers-with-vms"></a><span data-ttu-id="ed82f-124">比較使用 Vm 的 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="ed82f-124">Comparing Docker containers with VMs</span></span>

<span data-ttu-id="ed82f-125">圖 1-3 顯示比較 Vm 和 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="ed82f-125">Figure 1-3 shows a comparison between VMs and Docker containers.</span></span>

<span data-ttu-id="ed82f-126">因為容器只需要很少的資源 （例如，他們不需要完整的作業系統），可輕鬆地部署和快速啟動。</span><span class="sxs-lookup"><span data-stu-id="ed82f-126">Because containers require far fewer resources (for example, they do not need a full OS), they are easy to deploy and they start fast.</span></span> <span data-ttu-id="ed82f-127">這項功能可讓您擁有更高的密度，這表示您可以在相同的硬體單元，藉此降低成本上執行更多服務。</span><span class="sxs-lookup"><span data-stu-id="ed82f-127">This makes it possible for you to have higher density, meaning that you can run more services on the same hardware unit, thereby reducing costs.</span></span>

<span data-ttu-id="ed82f-128">在相同核心上執行的副作用，您可以達到比 Vm 更少隔離。</span><span class="sxs-lookup"><span data-stu-id="ed82f-128">As a side effect of running on the same kernel, you achieve less isolation than VMs.</span></span>

<span data-ttu-id="ed82f-129">映像的主要目標是跨不同的部署建立相同的環境 (相依性)。</span><span class="sxs-lookup"><span data-stu-id="ed82f-129">The main goal of an image is that it makes the environment (dependencies) the same across different deployments.</span></span> <span data-ttu-id="ed82f-130">這表示您可以在自己的電腦上對它進行偵錯，再將它部署到另一部電腦，保證有相同的環境。</span><span class="sxs-lookup"><span data-stu-id="ed82f-130">This means that you can debug it on your machine and then deploy it to another machine with the same environment guaranteed.</span></span>

<span data-ttu-id="ed82f-131">容器映像會用來在封裝的應用程式或服務，並將其部署可靠且可重現的方式。</span><span class="sxs-lookup"><span data-stu-id="ed82f-131">A container image is a way to package an app or service and deploy it in a reliable and reproducible manner.</span></span> <span data-ttu-id="ed82f-132">在這方面，Docker 不只一種技術，也更是哲學與處理程序。</span><span class="sxs-lookup"><span data-stu-id="ed82f-132">In this respect, Docker is not only a technology, it's also a philosophy and a process.</span></span>

<span data-ttu-id="ed82f-133">使用 Docker 時，您將無法聽到開發人員說，「 它能用在我的電腦上為何不在生產環境中？ 」</span><span class="sxs-lookup"><span data-stu-id="ed82f-133">When using Docker, you will not hear developers say, "It works on my machine, why not in production?"</span></span> <span data-ttu-id="ed82f-134">它們可以直接說 「 Docker 上可以執行，「 因為任何支援的 Docker 環境中，您可以執行封裝的 Docker 應用程式，而且它會執行其所有的部署目的地 （開發、 品管、 暫存、 生產等。） 在目標的方式。</span><span class="sxs-lookup"><span data-stu-id="ed82f-134">They can simply say, "It runs on Docker," because the packaged Docker application can be run on any supported Docker environment, and it will run the way it was intended to on all deployment destinations (Dev, QA, staging, production, etc.).</span></span>

![](./media/image3.png)

<span data-ttu-id="ed82f-135">圖 1-3： 的傳統 Vm 的 Docker 容器的比較</span><span class="sxs-lookup"><span data-stu-id="ed82f-135">Figure 1-3: Comparison of traditional VMs to Docker containers</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ed82f-136">[上一頁](index.md)
[下一頁](docker-terminology.md)</span><span class="sxs-lookup"><span data-stu-id="ed82f-136">[Previous](index.md)
[Next](docker-terminology.md)</span></span>
