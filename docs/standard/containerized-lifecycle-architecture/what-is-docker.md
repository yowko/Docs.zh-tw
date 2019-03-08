---
title: 什麼是 Docker？
description: 取得深入了解 Docker，簡單的比喻可以幫助您。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: fbb91466a86c7082e89d0ac4a3673ad83ab39b88
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680122"
---
# <a name="what-is-docker"></a><span data-ttu-id="56c12-103">什麼是 Docker？</span><span class="sxs-lookup"><span data-stu-id="56c12-103">What is Docker?</span></span>

<span data-ttu-id="56c12-104">[Docker](https://www.docker.com/) 是[開放原始碼專案](https://github.com/docker/docker)，將應用程式自動化部署為可攜式且可自足的容器，在雲端或內部部署上執行。</span><span class="sxs-lookup"><span data-stu-id="56c12-104">[Docker](https://www.docker.com/) is an [open-source project](https://github.com/docker/docker) for automating the deployment of applications as portable, self-sufficient containers that can run on the cloud or on-premises.</span></span> <span data-ttu-id="56c12-105">Docker 也是一家升級及發展這項技術的[公司](https://www.docker.com/)，並且與雲端、Linux 和 Windows 廠商 (包括 Microsoft) 合作。</span><span class="sxs-lookup"><span data-stu-id="56c12-105">Docker is also a [company](https://www.docker.com/) that promotes and evolves this technology, working in collaboration with cloud, Linux, and Windows vendors, including Microsoft.</span></span>

![Docker 容器可以在任何位置執行，例如客戶資料中心的內部部署、外部服務提供者或雲端 (在 Azure 上)。](./media/image2.png)

<span data-ttu-id="56c12-107">**圖 1-2**。</span><span class="sxs-lookup"><span data-stu-id="56c12-107">**Figure 1-2**.</span></span> <span data-ttu-id="56c12-108">Docker 將容器部署在混合式雲端的所有圖層</span><span class="sxs-lookup"><span data-stu-id="56c12-108">Docker deploys containers at all layers of the hybrid cloud</span></span>

<span data-ttu-id="56c12-109">Docker 映像容器可以原生方式在 Linux 及 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="56c12-109">Docker image containers can run natively on Linux and Windows.</span></span> <span data-ttu-id="56c12-110">不過，Windows 映像只能在 Windows 主機上執行，而 Linux 映像可以在 Linux 主機和 Windows 主機上執行 (目前是使用 Hyper-V Linux VM)，其中主機是指伺服器或 VM。</span><span class="sxs-lookup"><span data-stu-id="56c12-110">However, Windows images can run only on Windows hosts and Linux images can run on Linux hosts and Windows hosts (using a Hyper-V Linux VM, so far), where host means a server or a VM.</span></span>

<span data-ttu-id="56c12-111">開發人員可以使用 Windows、Linux 或 macOS 上的開發環境。</span><span class="sxs-lookup"><span data-stu-id="56c12-111">Developers can use development environments on Windows, Linux, or macOS.</span></span> <span data-ttu-id="56c12-112">在開發電腦上，開發人員執行的 Docker 主機是 Docker 映像部署所在，包括應用程式及其相依性。</span><span class="sxs-lookup"><span data-stu-id="56c12-112">On the development computer, the developer runs a Docker host where Docker images are deployed, including the app and its dependencies.</span></span> <span data-ttu-id="56c12-113">開發人員在 Linux 或 Mac 上使用的是以 Linux 為基礎的 Docker 主機，而且只可以建立適用於 Linux 容器映像。</span><span class="sxs-lookup"><span data-stu-id="56c12-113">Developers who work on Linux or on the Mac, use a Docker host that's Linux-based, and they can only create images for Linux containers.</span></span> <span data-ttu-id="56c12-114">（在 Mac 上工作的開發人員可以編輯程式碼或執行 Docker 命令列介面 (CLI) 從 macOS，但不撰寫本文時，直接在 macOS 上執行容器）。在 Windows 上工作的開發人員可以建立適用於 Linux 或 Windows 容器的映像。</span><span class="sxs-lookup"><span data-stu-id="56c12-114">(Developers working on the Mac can edit code or run the Docker command-line interface (CLI) from macOS, but as of this writing, containers don't run directly on macOS.) Developers who work on Windows can create images for either Linux or Windows Containers.</span></span>

<span data-ttu-id="56c12-115">為了在開發環境中裝載容器並且提供其他開發人員工具，Docker 提供適用於 Windows 或 macOS 的 [Docker Community Edition (CE)](https://www.docker.com/community-edition)。</span><span class="sxs-lookup"><span data-stu-id="56c12-115">To host containers in development environments and provide additional developer tools, Docker ships [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows or for macOS.</span></span> <span data-ttu-id="56c12-116">這些產品都會安裝必要的 VM (Docker 主機) 以裝載容器。</span><span class="sxs-lookup"><span data-stu-id="56c12-116">These products install the necessary VM (the Docker host) to host the containers.</span></span> <span data-ttu-id="56c12-117">Docker 也提供 [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)，這是專為企業開發所設計的，由在生產環境中建置、交付及執行大型商務關鍵性應用程式的 IT 小組來使用。</span><span class="sxs-lookup"><span data-stu-id="56c12-117">Docker also makes available [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), which is designed for enterprise development and is used by IT teams who build, ship, and run large business-critical applications in production.</span></span>

<span data-ttu-id="56c12-118">若要執行 [Windows 容器](/virtualization/windowscontainers/about/)，有兩種執行階段：</span><span class="sxs-lookup"><span data-stu-id="56c12-118">To run [Windows Containers](/virtualization/windowscontainers/about/), there are two types of runtimes:</span></span>

- <span data-ttu-id="56c12-119">**Windows Server 容器**提供透過程序和命名空間隔離技術的應用程式隔離。</span><span class="sxs-lookup"><span data-stu-id="56c12-119">**Windows Server Containers** provide application isolation through process and namespace isolation technology.</span></span> <span data-ttu-id="56c12-120">與 Windows Server 容器共用核心的對象為容器主機以及在此主機上執行的所有容器。</span><span class="sxs-lookup"><span data-stu-id="56c12-120">A Windows Server Container shares a kernel with the container host and with all containers running on the host.</span></span>

- <span data-ttu-id="56c12-121">**HYPER-V 容器**擴充 Windows Server 容器所提供的高度最佳化的虛擬機器中執行每個容器的隔離能力。</span><span class="sxs-lookup"><span data-stu-id="56c12-121">**Hyper-V Containers** expand on the isolation provided by Windows Server Containers by running each container in a highly optimized virtual machine.</span></span> <span data-ttu-id="56c12-122">在此組態中，容器主機的核心不會與 Hyper-V 容器共用，以提供更好的隔離。</span><span class="sxs-lookup"><span data-stu-id="56c12-122">In this configuration, the kernel of the container host isn't shared with the Hyper-V Containers, providing better isolation.</span></span>

<span data-ttu-id="56c12-123">這些容器的映像建立，而且一樣運作方式。</span><span class="sxs-lookup"><span data-stu-id="56c12-123">The images for these containers are created and work just the same way.</span></span> <span data-ttu-id="56c12-124">不同之處在於如何從映像建立容器時，執行 HYPER-V 容器，需要額外的參數。</span><span class="sxs-lookup"><span data-stu-id="56c12-124">The difference is in how the container is created from the image—running a Hyper-V Container requires an extra parameter.</span></span> <span data-ttu-id="56c12-125">如需詳細資料，請參閱 [Hyper-V 容器](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)。</span><span class="sxs-lookup"><span data-stu-id="56c12-125">For details, see [Hyper-V Containers](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).</span></span>

## <a name="comparing-docker-containers-with-virtual-machines"></a><span data-ttu-id="56c12-126">比較 Docker 容器與虛擬機器</span><span class="sxs-lookup"><span data-stu-id="56c12-126">Comparing Docker containers with virtual machines</span></span>

<span data-ttu-id="56c12-127">圖 1-3 顯示比較 Vm 和 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="56c12-127">Figure 1-3 shows a comparison between VMs and Docker containers.</span></span>

![針對 VM，在主機伺服器中有三個基礎層，從下到上分別是：基礎結構、主機作業系統和 Hypervisor，每部 VM 在頂端都具有各自的作業系統和所有必要的程式庫。](./media/image3.png)

<span data-ttu-id="56c12-130">**圖 1-3**。</span><span class="sxs-lookup"><span data-stu-id="56c12-130">**Figure 1-3**.</span></span> <span data-ttu-id="56c12-131">傳統虛擬機器與 Docker 容器的比較</span><span class="sxs-lookup"><span data-stu-id="56c12-131">Comparison of traditional virtual machines to Docker containers</span></span>

<span data-ttu-id="56c12-132">因為容器只需要很少的資源 (例如，它們不需要完整的作業系統)，所以容易部署且會快速啟動。</span><span class="sxs-lookup"><span data-stu-id="56c12-132">Because containers require far fewer resources (for example, they don't need a full OS), they're easy to deploy and they start fast.</span></span> <span data-ttu-id="56c12-133">這可讓您擁有更高的密度，這表示可讓您在相同硬體單位上執行更多服務，藉此降低成本。</span><span class="sxs-lookup"><span data-stu-id="56c12-133">This allows you to have higher density, meaning that it allows you to run more services on the same hardware unit, thereby reducing costs.</span></span>

<span data-ttu-id="56c12-134">在相同核心上執行的副作用是隔離程度比 VM 低。</span><span class="sxs-lookup"><span data-stu-id="56c12-134">As a side effect of running on the same kernel, you get less isolation than VMs.</span></span>

<span data-ttu-id="56c12-135">映像的主要目標是確保相同的環境 （相依性），跨不同的部署。</span><span class="sxs-lookup"><span data-stu-id="56c12-135">The main goal of an image is to ensure the same environment (dependencies) across different deployments.</span></span> <span data-ttu-id="56c12-136">這表示您可以用來進行偵錯您的電腦上，然後再將它部署到另一部電腦，保證相同的環境。</span><span class="sxs-lookup"><span data-stu-id="56c12-136">This means that you can debug it on your machine and then deploy it to another machine, the same environment guaranteed.</span></span>

<span data-ttu-id="56c12-137">容器映像是一種封裝應用程式或服務，再以可靠且可重現的方式來部署它的方法。</span><span class="sxs-lookup"><span data-stu-id="56c12-137">A container image is a way to package an app or service and deploy it in a reliable and reproducible way.</span></span> <span data-ttu-id="56c12-138">您可以這麼認為：Docker 不只是一項技術，更是哲學與過程。</span><span class="sxs-lookup"><span data-stu-id="56c12-138">You could say that Docker isn't only a technology but also a philosophy and a process.</span></span>

<span data-ttu-id="56c12-139">使用 Docker 時，您不會聽到開發人員說：「機器上行得通，為什麼生產環境行不通？」</span><span class="sxs-lookup"><span data-stu-id="56c12-139">When using Docker, you won't hear developers say, "It works on my machine, why not in production?"</span></span> <span data-ttu-id="56c12-140">他們可以只是說: 「 Docker 上可以執行 「、 因為封裝的 Docker 應用程式可執行任何支援的 Docker 環境中，並在所有部署目標上執行它所要的方式 (例如開發、 品管、 預備及生產)。</span><span class="sxs-lookup"><span data-stu-id="56c12-140">They can just say, "It runs on Docker", because the packaged Docker application can be executed on any supported Docker environment, and it runs the way it was intended to on all deployment targets (such as Dev, QA, staging, and production).</span></span>

## <a name="a-simple-analogy"></a><span data-ttu-id="56c12-141">簡單的比喻</span><span class="sxs-lookup"><span data-stu-id="56c12-141">A simple analogy</span></span>

<span data-ttu-id="56c12-142">也許簡單的比喻可以協助您掌握 Docker 的核心概念。</span><span class="sxs-lookup"><span data-stu-id="56c12-142">Perhaps a simple analogy can help getting the grasp of the core concept of Docker.</span></span>

<span data-ttu-id="56c12-143">讓我們暫時回到 1950 年。</span><span class="sxs-lookup"><span data-stu-id="56c12-143">Let's go back in time to the 1950s for a moment.</span></span> <span data-ttu-id="56c12-144">沒有任何的文書處理器，而且在各處使用影印機 （那種）。</span><span class="sxs-lookup"><span data-stu-id="56c12-144">There were no word processors, and the photocopiers were used everywhere (well, kind of).</span></span>

<span data-ttu-id="56c12-145">假設您負責根據需求來快速發送大批信件，並使用信紙和信封，將信件實際投遞到每個客戶的地址 (當時並沒有電子郵件)。</span><span class="sxs-lookup"><span data-stu-id="56c12-145">Imagine you're responsible for quickly issuing batches of letters as required, to mail them to customers, using real paper and envelopes, to be delivered physically to each customer's address (there was no email back then).</span></span>

<span data-ttu-id="56c12-146">慢慢地，您了解到這些信件的內容是大量段落的組合，只是根據信件目的從中挑選和編排需要的段落，因此您設計一個系統，可以快速地發送信件來提高效率。</span><span class="sxs-lookup"><span data-stu-id="56c12-146">At some point, you realize the letters are just a composition of a large set of paragraphs, which are picked and arranged as needed, according to the purpose of the letter, so you devise a system to issue letters quickly, expecting to get a hefty raise.</span></span>

<span data-ttu-id="56c12-147">系統很簡單：</span><span class="sxs-lookup"><span data-stu-id="56c12-147">The system is simple:</span></span>

1. <span data-ttu-id="56c12-148">您開始準備一疊透明紙張，每一張紙都包含一個段落。</span><span class="sxs-lookup"><span data-stu-id="56c12-148">You begin with a deck of transparent sheets containing one paragraph each.</span></span>

2. <span data-ttu-id="56c12-149">若要發送一批信件，您就挑選具有所需段落的紙張，然後將其堆疊並且排列整齊，讓它們整潔易讀。</span><span class="sxs-lookup"><span data-stu-id="56c12-149">To issue a set of letters, you pick the sheets with the paragraphs you need, then you stack and align them so they look and read fine.</span></span>

3. <span data-ttu-id="56c12-150">最後，您將這個組合放入影印機中，然後按下開始以產生所需數量的信件。</span><span class="sxs-lookup"><span data-stu-id="56c12-150">Finally, you place the set in the photocopier and press start to produce as many letters as required.</span></span>

<span data-ttu-id="56c12-151">因此，工作精簡了，這就是 Docker 的核心概念。</span><span class="sxs-lookup"><span data-stu-id="56c12-151">So, simplifying, that's the core idea of Docker.</span></span>

<span data-ttu-id="56c12-152">Docker 中的每一層都是在執行命令 (例如安裝程式) 之後，檔案系統上所發生的變更結果集。</span><span class="sxs-lookup"><span data-stu-id="56c12-152">In Docker, each layer is the resulting set of changes that happen to the filesystem after executing a command, such as, installing a program.</span></span>

<span data-ttu-id="56c12-153">因此，當您在複製層之後「查看」檔案系統時，會看到檔案整體，包含安裝程式的層。</span><span class="sxs-lookup"><span data-stu-id="56c12-153">So, when you "look" at the filesystem after the layer has been copied, you see all the files, included the layer when the program was installed.</span></span>

<span data-ttu-id="56c12-154">您可以將映像當作是準備要在「電腦」(已安裝作業系統) 中安裝的輔助唯讀硬碟。</span><span class="sxs-lookup"><span data-stu-id="56c12-154">You can think of an image as an auxiliary read-only hard disk ready to be installed in a "computer" where the operating system is already installed.</span></span>

<span data-ttu-id="56c12-155">同樣地，您可以將容器當作是已安裝映像硬碟的「電腦」。</span><span class="sxs-lookup"><span data-stu-id="56c12-155">Similarly, you can think of a container as the "computer" with the image hard disk installed.</span></span> <span data-ttu-id="56c12-156">容器，就像電腦一樣，可以開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="56c12-156">The container, just like a computer, can be powered on or off.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="56c12-157">[上一頁](index.md)
>[下一頁](docker-terminology.md)</span><span class="sxs-lookup"><span data-stu-id="56c12-157">[Previous](index.md)
[Next](docker-terminology.md)</span></span>
