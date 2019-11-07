---
title: 什麼是 Docker？
description: 進一步增進您對 Docker 的理解，以下提供的簡單比喻或許能幫上您。
ms.date: 02/15/2019
ms.openlocfilehash: 8636ae3b1ad32158e10ce2aa58423f9c9824d8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738134"
---
# <a name="what-is-docker"></a><span data-ttu-id="702d1-103">什麼是 Docker？</span><span class="sxs-lookup"><span data-stu-id="702d1-103">What is Docker?</span></span>

<span data-ttu-id="702d1-104">[Docker](https://www.docker.com/) 是[開放原始碼專案](https://github.com/docker/docker)，將應用程式自動化部署為可攜式且可自足的容器，在雲端或內部部署上執行。</span><span class="sxs-lookup"><span data-stu-id="702d1-104">[Docker](https://www.docker.com/) is an [open-source project](https://github.com/docker/docker) for automating the deployment of applications as portable, self-sufficient containers that can run on the cloud or on-premises.</span></span> <span data-ttu-id="702d1-105">Docker 也是一家升級及發展這項技術的[公司](https://www.docker.com/)，並且與雲端、Linux 和 Windows 廠商 (包括 Microsoft) 合作。</span><span class="sxs-lookup"><span data-stu-id="702d1-105">Docker is also a [company](https://www.docker.com/) that promotes and evolves this technology, working in collaboration with cloud, Linux, and Windows vendors, including Microsoft.</span></span>

![此圖顯示 Docker 容器可執行檔位置。](./media/what-is-docker/docker-containers-run-anywhere.png)

<span data-ttu-id="702d1-107">**圖 1-2**。</span><span class="sxs-lookup"><span data-stu-id="702d1-107">**Figure 1-2**.</span></span> <span data-ttu-id="702d1-108">Docker 將容器部署在混合式雲端的所有圖層</span><span class="sxs-lookup"><span data-stu-id="702d1-108">Docker deploys containers at all layers of the hybrid cloud</span></span>

<span data-ttu-id="702d1-109">如上圖所示，在 Azure 上的外部服務提供者或雲端中，Docker 容器可以在任何位置執行，不論是在內部部署的客戶資料中心內。</span><span class="sxs-lookup"><span data-stu-id="702d1-109">As shown in the above diagram, Docker containers can run anywhere, on-premises in the customer datacenter, in an external service provider or in the cloud, on Azure.</span></span> <span data-ttu-id="702d1-110">Docker 映射容器也可以在 Linux 和 Windows 上以原生方式執行。</span><span class="sxs-lookup"><span data-stu-id="702d1-110">Docker image containers can also run natively on Linux and Windows.</span></span> <span data-ttu-id="702d1-111">不過，Windows 映像只能在 Windows 主機上執行，而 Linux 映像可以在 Linux 主機和 Windows 主機上執行 (目前是使用 Hyper-V Linux VM)，其中主機是指伺服器或 VM。</span><span class="sxs-lookup"><span data-stu-id="702d1-111">However, Windows images can run only on Windows hosts and Linux images can run on Linux hosts and Windows hosts (using a Hyper-V Linux VM, so far), where host means a server or a VM.</span></span>

<span data-ttu-id="702d1-112">開發人員可以使用 Windows、Linux 或 macOS 上的開發環境。</span><span class="sxs-lookup"><span data-stu-id="702d1-112">Developers can use development environments on Windows, Linux, or macOS.</span></span> <span data-ttu-id="702d1-113">在開發電腦上，開發人員執行的 Docker 主機是 Docker 映像部署所在，包括應用程式及其相依性。</span><span class="sxs-lookup"><span data-stu-id="702d1-113">On the development computer, the developer runs a Docker host where Docker images are deployed, including the app and its dependencies.</span></span> <span data-ttu-id="702d1-114">在 Linux 或 Mac 上工作的開發人員會使用 Linux 型的 Docker 主機，他們只能建立適用於 Linux 容器的映像。</span><span class="sxs-lookup"><span data-stu-id="702d1-114">Developers who work on Linux or on the Mac, use a Docker host that's Linux-based, and they can only create images for Linux containers.</span></span> <span data-ttu-id="702d1-115">（在 Mac 上工作的開發人員可以編輯程式碼，或從 macOS 執行 Docker 命令列介面（CLI），但在撰寫本文時，容器不會直接在 macOS 上執行）。在 Windows 上工作的開發人員可以建立 Linux 或 Windows 容器的映射。</span><span class="sxs-lookup"><span data-stu-id="702d1-115">(Developers working on the Mac can edit code or run the Docker command-line interface (CLI) from macOS, but as of this writing, containers don't run directly on macOS.) Developers who work on Windows can create images for either Linux or Windows Containers.</span></span>

<span data-ttu-id="702d1-116">為了在開發環境中裝載容器並且提供其他開發人員工具，Docker 提供適用於 Windows 或 macOS 的 [Docker Community Edition (CE)](https://www.docker.com/community-edition)。</span><span class="sxs-lookup"><span data-stu-id="702d1-116">To host containers in development environments and provide additional developer tools, Docker ships [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows or for macOS.</span></span> <span data-ttu-id="702d1-117">這些產品都會安裝必要的 VM (Docker 主機) 以裝載容器。</span><span class="sxs-lookup"><span data-stu-id="702d1-117">These products install the necessary VM (the Docker host) to host the containers.</span></span> <span data-ttu-id="702d1-118">Docker 也提供 [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)，這是專為企業開發所設計的，由在生產環境中建置、交付及執行大型商務關鍵性應用程式的 IT 小組來使用。</span><span class="sxs-lookup"><span data-stu-id="702d1-118">Docker also makes available [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), which is designed for enterprise development and is used by IT teams who build, ship, and run large business-critical applications in production.</span></span>

<span data-ttu-id="702d1-119">若要執行 [Windows 容器](/virtualization/windowscontainers/about/)，有兩種執行階段：</span><span class="sxs-lookup"><span data-stu-id="702d1-119">To run [Windows Containers](/virtualization/windowscontainers/about/), there are two types of runtimes:</span></span>

- <span data-ttu-id="702d1-120">**Windows Server 容器**透過程序和命名空間隔離技術，提供應用程式隔離。</span><span class="sxs-lookup"><span data-stu-id="702d1-120">**Windows Server Containers** provide application isolation through process and namespace isolation technology.</span></span> <span data-ttu-id="702d1-121">與 Windows Server 容器共用核心的對象為容器主機以及在此主機上執行的所有容器。</span><span class="sxs-lookup"><span data-stu-id="702d1-121">A Windows Server Container shares a kernel with the container host and with all containers running on the host.</span></span>

- <span data-ttu-id="702d1-122">**Hyper-V 容器**可在 Windows Server 容器提供的隔離上展開，方法是在高度最佳化的虛擬機器中執行每個容器。</span><span class="sxs-lookup"><span data-stu-id="702d1-122">**Hyper-V Containers** expand on the isolation provided by Windows Server Containers by running each container in a highly optimized virtual machine.</span></span> <span data-ttu-id="702d1-123">在此組態中，容器主機的核心不會與 Hyper-V 容器共用，以提供更好的隔離。</span><span class="sxs-lookup"><span data-stu-id="702d1-123">In this configuration, the kernel of the container host isn't shared with the Hyper-V Containers, providing better isolation.</span></span>

<span data-ttu-id="702d1-124">這些容器映像的建立及運作方式都相同。</span><span class="sxs-lookup"><span data-stu-id="702d1-124">The images for these containers are created and work just the same way.</span></span> <span data-ttu-id="702d1-125">不同之處在於從執行 Hyper-V 容器的映像建立容器需要額外參數。</span><span class="sxs-lookup"><span data-stu-id="702d1-125">The difference is in how the container is created from the image—running a Hyper-V Container requires an extra parameter.</span></span> <span data-ttu-id="702d1-126">如需詳細資料，請參閱 [Hyper-V 容器](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)。</span><span class="sxs-lookup"><span data-stu-id="702d1-126">For details, see [Hyper-V Containers](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).</span></span>

## <a name="comparing-docker-containers-with-virtual-machines"></a><span data-ttu-id="702d1-127">比較 Docker 容器與虛擬機器</span><span class="sxs-lookup"><span data-stu-id="702d1-127">Comparing Docker containers with virtual machines</span></span>

<span data-ttu-id="702d1-128">圖 1-3 比較了 VM 和 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="702d1-128">Figure 1-3 shows a comparison between VMs and Docker containers.</span></span>

![顯示 VM 和容器環境比較的圖表。](./media/what-is-docker/comparison-vms-docker-conatiners.png)

<span data-ttu-id="702d1-130">**圖 1-3**。</span><span class="sxs-lookup"><span data-stu-id="702d1-130">**Figure 1-3**.</span></span> <span data-ttu-id="702d1-131">傳統虛擬機器與 Docker 容器的比較</span><span class="sxs-lookup"><span data-stu-id="702d1-131">Comparison of traditional virtual machines to Docker containers</span></span>

<span data-ttu-id="702d1-132">如上圖所示，針對 Vm，主機伺服器中有三個基本層。</span><span class="sxs-lookup"><span data-stu-id="702d1-132">As shown in the above diagram, for VMs, there are three base layers in the host server.</span></span> <span data-ttu-id="702d1-133">從底部：基礎結構、主機作業系統和虛擬程式。</span><span class="sxs-lookup"><span data-stu-id="702d1-133">From the bottom-up: Infrastructure, Host Operating System, and a Hypervisor.</span></span> <span data-ttu-id="702d1-134">除此之外，每個 VM 都有自己的 OS 和所有必要的程式庫。</span><span class="sxs-lookup"><span data-stu-id="702d1-134">On top of all that, each VM has its own OS and all necessary libraries.</span></span> <span data-ttu-id="702d1-135">另一方面，針對 Docker，主機伺服器只有基礎結構和作業系統。</span><span class="sxs-lookup"><span data-stu-id="702d1-135">On the other hand, for Docker, the host server only has the Infrastructure and the OS.</span></span> <span data-ttu-id="702d1-136">除此之外，容器引擎會讓容器保持隔離，但可讓它們共用單一基礎作業系統的服務。</span><span class="sxs-lookup"><span data-stu-id="702d1-136">On top of that, the container engine keeps containers isolated, but lets them share the single base OS's services.</span></span>

<span data-ttu-id="702d1-137">因為容器只需要很少的資源 (例如，它們不需要完整的作業系統)，所以容易部署且會快速啟動。</span><span class="sxs-lookup"><span data-stu-id="702d1-137">Because containers require far fewer resources (for example, they don't need a full OS), they're easy to deploy and they start fast.</span></span> <span data-ttu-id="702d1-138">這可讓您擁有更高的密度，這表示可讓您在相同硬體單位上執行更多服務，藉此降低成本。</span><span class="sxs-lookup"><span data-stu-id="702d1-138">This allows you to have higher density, meaning that it allows you to run more services on the same hardware unit, thereby reducing costs.</span></span>

<span data-ttu-id="702d1-139">在相同核心上執行的副作用是隔離程度比 VM 低。</span><span class="sxs-lookup"><span data-stu-id="702d1-139">As a side effect of running on the same kernel, you get less isolation than VMs.</span></span>

<span data-ttu-id="702d1-140">映像的主要目標是確保不同部署間均有相同的環境 (相依性)。</span><span class="sxs-lookup"><span data-stu-id="702d1-140">The main goal of an image is to ensure the same environment (dependencies) across different deployments.</span></span> <span data-ttu-id="702d1-141">這表示您可以在自己的電腦上對它進行偵錯，再將它部署到另一部電腦，保證有相同的環境。</span><span class="sxs-lookup"><span data-stu-id="702d1-141">This means that you can debug it on your machine and then deploy it to another machine, the same environment guaranteed.</span></span>

<span data-ttu-id="702d1-142">容器映像是一種封裝應用程式或服務，再以可靠且可重現的方式來部署它的方法。</span><span class="sxs-lookup"><span data-stu-id="702d1-142">A container image is a way to package an app or service and deploy it in a reliable and reproducible way.</span></span> <span data-ttu-id="702d1-143">您可以這麼認為：Docker 不只是一項技術，更是哲學與過程。</span><span class="sxs-lookup"><span data-stu-id="702d1-143">You could say that Docker isn't only a technology but also a philosophy and a process.</span></span>

<span data-ttu-id="702d1-144">使用 Docker 時，您不會聽到開發人員說：「機器上行得通，為什麼生產環境行不通？」</span><span class="sxs-lookup"><span data-stu-id="702d1-144">When using Docker, you won't hear developers say, "It works on my machine, why not in production?"</span></span> <span data-ttu-id="702d1-145">他們可以直接說：「在 Docker 上可以執行」，因為封裝的 Docker 應用程式可以在任何支援的 Docker 環境中執行，而且它是依照預期的方式在所有部署目標上執行 (例如開發、品管、預備及生產)。</span><span class="sxs-lookup"><span data-stu-id="702d1-145">They can just say, "It runs on Docker", because the packaged Docker application can be executed on any supported Docker environment, and it runs the way it was intended to on all deployment targets (such as Dev, QA, staging, and production).</span></span>

## <a name="a-simple-analogy"></a><span data-ttu-id="702d1-146">簡單的比喻</span><span class="sxs-lookup"><span data-stu-id="702d1-146">A simple analogy</span></span>

<span data-ttu-id="702d1-147">也許簡單的比喻可以協助您掌握 Docker 的核心概念。</span><span class="sxs-lookup"><span data-stu-id="702d1-147">Perhaps a simple analogy can help getting the grasp of the core concept of Docker.</span></span>

<span data-ttu-id="702d1-148">讓我們暫時回到 1950 年。</span><span class="sxs-lookup"><span data-stu-id="702d1-148">Let's go back in time to the 1950s for a moment.</span></span> <span data-ttu-id="702d1-149">當時沒有任何文書處理器，而且到處都在使用影印機 (差不多所有人都在用)。</span><span class="sxs-lookup"><span data-stu-id="702d1-149">There were no word processors, and the photocopiers were used everywhere (well, kind of).</span></span>

<span data-ttu-id="702d1-150">假設您負責根據需求來快速發送大批信件，並使用信紙和信封，將信件實際投遞到每個客戶的地址 (當時並沒有電子郵件)。</span><span class="sxs-lookup"><span data-stu-id="702d1-150">Imagine you're responsible for quickly issuing batches of letters as required, to mail them to customers, using real paper and envelopes, to be delivered physically to each customer's address (there was no email back then).</span></span>

<span data-ttu-id="702d1-151">慢慢地，您了解到這些信件的內容是大量段落的組合，只是根據信件目的從中挑選和編排需要的段落，因此您設計一個系統，可以快速地發送信件來提高效率。</span><span class="sxs-lookup"><span data-stu-id="702d1-151">At some point, you realize the letters are just a composition of a large set of paragraphs, which are picked and arranged as needed, according to the purpose of the letter, so you devise a system to issue letters quickly, expecting to get a hefty raise.</span></span>

<span data-ttu-id="702d1-152">系統很簡單：</span><span class="sxs-lookup"><span data-stu-id="702d1-152">The system is simple:</span></span>

1. <span data-ttu-id="702d1-153">您開始準備一疊透明紙張，每一張紙都包含一個段落。</span><span class="sxs-lookup"><span data-stu-id="702d1-153">You begin with a deck of transparent sheets containing one paragraph each.</span></span>

2. <span data-ttu-id="702d1-154">若要發送一批信件，您就挑選具有所需段落的紙張，然後將其堆疊並且排列整齊，讓它們整潔易讀。</span><span class="sxs-lookup"><span data-stu-id="702d1-154">To issue a set of letters, you pick the sheets with the paragraphs you need, then you stack and align them so they look and read fine.</span></span>

3. <span data-ttu-id="702d1-155">最後，您將這個組合放入影印機中，然後按下開始以產生所需數量的信件。</span><span class="sxs-lookup"><span data-stu-id="702d1-155">Finally, you place the set in the photocopier and press start to produce as many letters as required.</span></span>

<span data-ttu-id="702d1-156">因此，工作精簡了，這就是 Docker 的核心概念。</span><span class="sxs-lookup"><span data-stu-id="702d1-156">So, simplifying, that's the core idea of Docker.</span></span>

<span data-ttu-id="702d1-157">Docker 中的每一層都是在執行命令 (例如安裝程式) 之後，檔案系統上所發生的變更結果集。</span><span class="sxs-lookup"><span data-stu-id="702d1-157">In Docker, each layer is the resulting set of changes that happen to the filesystem after executing a command, such as, installing a program.</span></span>

<span data-ttu-id="702d1-158">因此，當您在複製層之後「查看」檔案系統時，會看到檔案整體，包含安裝程式的層。</span><span class="sxs-lookup"><span data-stu-id="702d1-158">So, when you "look" at the filesystem after the layer has been copied, you see all the files, included the layer when the program was installed.</span></span>

<span data-ttu-id="702d1-159">您可以將映像當作是準備要在「電腦」(已安裝作業系統) 中安裝的輔助唯讀硬碟。</span><span class="sxs-lookup"><span data-stu-id="702d1-159">You can think of an image as an auxiliary read-only hard disk ready to be installed in a "computer" where the operating system is already installed.</span></span>

<span data-ttu-id="702d1-160">同樣地，您可以將容器當作是已安裝映像硬碟的「電腦」。</span><span class="sxs-lookup"><span data-stu-id="702d1-160">Similarly, you can think of a container as the "computer" with the image hard disk installed.</span></span> <span data-ttu-id="702d1-161">容器，就像電腦一樣，可以開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="702d1-161">The container, just like a computer, can be powered on or off.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="702d1-162">[上一頁](index.md)
>[下一頁](docker-terminology.md)</span><span class="sxs-lookup"><span data-stu-id="702d1-162">[Previous](index.md)
[Next](docker-terminology.md)</span></span>
