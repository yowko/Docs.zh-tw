---
title: Docker 簡介
description: 此文章在 .NET Core 應用程式內容中提供了 Docker 的簡介及概觀。
ms.date: 03/20/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: acf1307c241d9462278bc0fce5cf59fdde0750a3
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480725"
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="9902c-103">.NET 和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="9902c-103">Introduction to .NET and Docker</span></span>

<span data-ttu-id="9902c-104">.NET Core 能夠很容易地在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="9902c-104">.NET Core can easily run in a Docker container.</span></span> <span data-ttu-id="9902c-105">容器提供精簡的方式將您的應用程式與主機系統的其餘部分隔離、只共用核心，以及使用提供給應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="9902c-105">Containers provide a lightweight way to isolate your application from the rest of the host system, sharing just the kernel, and using resources given to your application.</span></span> <span data-ttu-id="9902c-106">如果不熟悉 Docker，強烈建議閱讀 Docker 的[概觀文件](https://docs.docker.com/engine/docker-overview/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="9902c-106">If you're unfamiliar with Docker, it's highly recommended that you read through Docker's [overview documentation](https://docs.docker.com/engine/docker-overview/).</span></span>

<span data-ttu-id="9902c-107">如需有關如何安裝 Docker 的詳細資訊，請參閱 [Docker Desktop：Community Edition](https://www.docker.com/products/docker-desktop) \(英文\) 的下載頁面。</span><span class="sxs-lookup"><span data-stu-id="9902c-107">For more information about how to install Docker, see the download page for [Docker Desktop: Community Edition](https://www.docker.com/products/docker-desktop).</span></span>

## <a name="docker-basics"></a><span data-ttu-id="9902c-108">Docker 基本知識</span><span class="sxs-lookup"><span data-stu-id="9902c-108">Docker basics</span></span>

<span data-ttu-id="9902c-109">有幾個概念您應該很熟悉。</span><span class="sxs-lookup"><span data-stu-id="9902c-109">There are a few concepts you should be familiar with.</span></span> <span data-ttu-id="9902c-110">Docker 用戶端有命令列介面方案，可讓您用來管理映像和容器。</span><span class="sxs-lookup"><span data-stu-id="9902c-110">The Docker client has a command line interface program you use to manage images and containers.</span></span> <span data-ttu-id="9902c-111">如先前所述，您應該仔細閱讀 [Docker 概觀](https://docs.docker.com/engine/docker-overview/) \(英文\) 文件。</span><span class="sxs-lookup"><span data-stu-id="9902c-111">As previously stated, you should take the time to read through the [Docker overview](https://docs.docker.com/engine/docker-overview/) documentation.</span></span> 

### <a name="images"></a><span data-ttu-id="9902c-112">影像</span><span class="sxs-lookup"><span data-stu-id="9902c-112">Images</span></span>

<span data-ttu-id="9902c-113">映像是構成容器基礎且已排序的檔案系統變更集合。</span><span class="sxs-lookup"><span data-stu-id="9902c-113">An image is an ordered collection of filesystem changes that form the basis of a container.</span></span> <span data-ttu-id="9902c-114">映像沒有狀態，而且是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="9902c-114">The image doesn't have a state and is read-only.</span></span> <span data-ttu-id="9902c-115">映像很多時候會以另一個映像作為基礎，但包含一些自訂項目。</span><span class="sxs-lookup"><span data-stu-id="9902c-115">Much the time an image is based on another image, but with some customization.</span></span> <span data-ttu-id="9902c-116">例如，在建立新的應用程式映像時，可以利用已包含 .NET Core 執行階段的現有映像作為基礎。</span><span class="sxs-lookup"><span data-stu-id="9902c-116">For example, when you create an new image for your application, you would base it on an existing image that already contains the .NET Core runtime.</span></span>

<span data-ttu-id="9902c-117">因為容器是從映像建立的，所以映像會有一組在容器啟動時執行的執行參數 (例如啟動可執行檔)。</span><span class="sxs-lookup"><span data-stu-id="9902c-117">Because containers are created from images, images have a set of run parameters (such as a starting executable) that run when the container starts.</span></span>

### <a name="containers"></a><span data-ttu-id="9902c-118">容器</span><span class="sxs-lookup"><span data-stu-id="9902c-118">Containers</span></span>

<span data-ttu-id="9902c-119">容器是可執行的映像執行個體。</span><span class="sxs-lookup"><span data-stu-id="9902c-119">A container is a runnable instance of an image.</span></span> <span data-ttu-id="9902c-120">建置映像時，可以部署您的應用程式和相依項目。</span><span class="sxs-lookup"><span data-stu-id="9902c-120">As you build your image, you deploy your application and dependencies.</span></span> <span data-ttu-id="9902c-121">然後，可以具現化多個容器，每個都會彼此隔離。</span><span class="sxs-lookup"><span data-stu-id="9902c-121">Then, multiple containers can be instantiated, each isolated from one another.</span></span> <span data-ttu-id="9902c-122">每個容器執行個體都有自己的檔案系統、記憶體和網路介面。</span><span class="sxs-lookup"><span data-stu-id="9902c-122">Each container instance has its own filesystem, memory, and network interface.</span></span>

### <a name="registries"></a><span data-ttu-id="9902c-123">登錄</span><span class="sxs-lookup"><span data-stu-id="9902c-123">Registries</span></span>

<span data-ttu-id="9902c-124">容器登錄是映像存放庫的集合。</span><span class="sxs-lookup"><span data-stu-id="9902c-124">Container registries are a collection of image repositories.</span></span> <span data-ttu-id="9902c-125">您可以使用登錄映像作為映像的基礎。</span><span class="sxs-lookup"><span data-stu-id="9902c-125">You can base your images on a registry image.</span></span> <span data-ttu-id="9902c-126">您可以在登錄中直接從映像建立容器。</span><span class="sxs-lookup"><span data-stu-id="9902c-126">You can create containers directly from an image in a registry.</span></span> <span data-ttu-id="9902c-127">在[進行容器化應用程式或微服務的架構設計及建置](../../standard/microservices-architecture/architect-microservice-container-applications/index.md)時，[Docker 容器、映像和登錄之間的關係](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md)是相當重要的概念。</span><span class="sxs-lookup"><span data-stu-id="9902c-127">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="9902c-128">此作法能大幅縮短開發和部署之間的時間。</span><span class="sxs-lookup"><span data-stu-id="9902c-128">This approach greatly shortens the time between development and deployment.</span></span>

<span data-ttu-id="9902c-129">Docker 擁有公用登錄，已裝載於 [Docker Hub](https://hub.docker.com/) \(英文\) 供您使用。</span><span class="sxs-lookup"><span data-stu-id="9902c-129">Docker has a public registry hosted at the [Docker Hub](https://hub.docker.com/) that you can use.</span></span> <span data-ttu-id="9902c-130">Docker Hub 會列出 [.NET core 相關映像](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="9902c-130">[.NET Core related images](https://hub.docker.com/_/microsoft-dotnet-core/) are listed at the Docker Hub.</span></span> 

<span data-ttu-id="9902c-131">Microsoft 容器登錄 (MCR) 是 Microsoft 提供容器映像的官方來源。</span><span class="sxs-lookup"><span data-stu-id="9902c-131">The Microsoft Container Registry (MCR) is the official source of Microsoft-provided container images.</span></span> <span data-ttu-id="9902c-132">MCR 建置在 Azure CDN 上，用來提供全域複寫的映像。</span><span class="sxs-lookup"><span data-stu-id="9902c-132">The MCR is built on Azure CDN to provide globally-replicated images.</span></span> <span data-ttu-id="9902c-133">不過，MCR 並沒有公開網站，因此了解 Microsoft 所提供容器映像的主要方式是透過 [Microsoft Docker Hub 頁面](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="9902c-133">However, the MCR does not have a public-facing website and the primary way to learn about Microsoft-provided container images is through the [Microsoft Docker Hub pages](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

### <a name="dockerfile"></a><span data-ttu-id="9902c-134">Dockerfile</span><span class="sxs-lookup"><span data-stu-id="9902c-134">Dockerfile</span></span>

<span data-ttu-id="9902c-135">**Dockerfile** 是一個檔案，定義了一組建立映像的指示。</span><span class="sxs-lookup"><span data-stu-id="9902c-135">A **Dockerfile** is a file that defines a set of instructions that creates an image.</span></span> <span data-ttu-id="9902c-136">**Dockerfile** 中的每個指示都會在映像中建立一個圖層。</span><span class="sxs-lookup"><span data-stu-id="9902c-136">Each instruction in the **Dockerfile** creates a layer in the image.</span></span> <span data-ttu-id="9902c-137">在大部分的情況下，當您重建映像時，系統只會重建已變更的圖層。</span><span class="sxs-lookup"><span data-stu-id="9902c-137">For the most part, when you rebuild the image only the layers that have changed are rebuilt.</span></span> <span data-ttu-id="9902c-138">**Dockerfile** 可以散發給其他人，並讓他們以和您相同的方式重新建立新的映像。</span><span class="sxs-lookup"><span data-stu-id="9902c-138">The **Dockerfile** can be distributed to others and allows them to recreate to create a new image in the same manner you created it.</span></span> <span data-ttu-id="9902c-139">雖然這可讓您散發映像建立方式的*指示*，但散發映像的主要方式是將它發行至登錄。</span><span class="sxs-lookup"><span data-stu-id="9902c-139">While this allows you to distribute the *instructions* on how to create the image, the main way to distribute your image is to publish it to a registry.</span></span>

## <a name="net-core-images"></a><span data-ttu-id="9902c-140">.NET Core 映像</span><span class="sxs-lookup"><span data-stu-id="9902c-140">.NET Core images</span></span>

<span data-ttu-id="9902c-141">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="9902c-141">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="9902c-142">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="9902c-142">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span> 

<span data-ttu-id="9902c-143">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="9902c-143">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="9902c-144">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="9902c-144">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

## <a name="azure-services"></a><span data-ttu-id="9902c-145">Azure 服務</span><span class="sxs-lookup"><span data-stu-id="9902c-145">Azure services</span></span>

<span data-ttu-id="9902c-146">各種 Azure 服務支援容器。</span><span class="sxs-lookup"><span data-stu-id="9902c-146">Various Azure services support containers.</span></span> <span data-ttu-id="9902c-147">您可以為應用程式建立 Docker 映像，並將它部署到下列其中一個服務：</span><span class="sxs-lookup"><span data-stu-id="9902c-147">You create a Docker image for your application and deploy it to one of the following services:</span></span>

* [<span data-ttu-id="9902c-148">Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="9902c-148">Azure Kubernetes Service (AKS)</span></span>](https://azure.microsoft.com/services/kubernetes-service/)\
<span data-ttu-id="9902c-149">調整規模及協調使用 Kubernetes 的 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="9902c-149">Scale and orchestrate Linux containers using Kubernetes.</span></span>

* [<span data-ttu-id="9902c-150">Azure App Service</span><span class="sxs-lookup"><span data-stu-id="9902c-150">Azure App Service</span></span>](https://azure.microsoft.com/services/app-service/containers/)\
<span data-ttu-id="9902c-151">在 PaaS 環境中使用 Linux 容器部署 Web 應用程式或 API。</span><span class="sxs-lookup"><span data-stu-id="9902c-151">Deploy web apps or APIs using Linux containers in a PaaS environment.</span></span>

* [<span data-ttu-id="9902c-152">Azure 容器執行個體</span><span class="sxs-lookup"><span data-stu-id="9902c-152">Azure Container Instances</span></span>](https://azure.microsoft.com/services/container-instances/)\
<span data-ttu-id="9902c-153">在沒有任何較高層級管理服務的情況下，將容器裝載於雲端。</span><span class="sxs-lookup"><span data-stu-id="9902c-153">Host your container in the cloud without any higher-level management services.</span></span>

* [<span data-ttu-id="9902c-154">Azure Batch</span><span class="sxs-lookup"><span data-stu-id="9902c-154">Azure Batch</span></span>](https://azure.microsoft.com/services/batch/)\
<span data-ttu-id="9902c-155">使用容器執行重複的計算工作。</span><span class="sxs-lookup"><span data-stu-id="9902c-155">Run repetitive compute jobs using containers.</span></span>

* [<span data-ttu-id="9902c-156">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="9902c-156">Azure Service Fabric</span></span>](https://azure.microsoft.com/services/service-fabric/)\
<span data-ttu-id="9902c-157">使用 Windows Server 容器將 .NET 應用程式提升、轉移及現代化至微服務</span><span class="sxs-lookup"><span data-stu-id="9902c-157">Lift, shift, and modernize .NET applications to microservices using Windows Server containers</span></span>

* [<span data-ttu-id="9902c-158">Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="9902c-158">Azure Container Registry</span></span>](https://azure.microsoft.com/services/container-registry/)\
<span data-ttu-id="9902c-159">儲存及管理所有 Azure 部署類型的容器映像。</span><span class="sxs-lookup"><span data-stu-id="9902c-159">Store and manage container images across all types of Azure deployments.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9902c-160">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9902c-160">Next steps</span></span>

* [<span data-ttu-id="9902c-161">了解如何將 .NET Core 應用程式容器化。</span><span class="sxs-lookup"><span data-stu-id="9902c-161">Learn how to containerize a .NET Core application.</span></span>](build-docker-netcore-container.md)
* [<span data-ttu-id="9902c-162">嘗試「了解 ASP.NET Core 微服務」教學課程。</span><span class="sxs-lookup"><span data-stu-id="9902c-162">Try the Learn ASP.NET Core Microservice tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
