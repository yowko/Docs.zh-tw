---
title: "官方 .NET Docker 映像"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 官方 .NET Docker 映像"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 42872caa1a9306187daeefd35feb9bec3fae60af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="official-net-docker-images"></a><span data-ttu-id="9c789-104">官方 .NET Docker 映像</span><span class="sxs-lookup"><span data-stu-id="9c789-104">Official .NET Docker images</span></span>

<span data-ttu-id="9c789-105">官方 .NET Docker 映像是 Microsoft 建立及最佳化的 .NET Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="9c789-105">The Official .NET Docker images are Docker images created and optimized by Microsoft.</span></span> <span data-ttu-id="9c789-106">[它們在 Docker Hub 上的 Microsoft 存放庫中公開提供](https://hub.docker.com/u/microsoft/)。</span><span class="sxs-lookup"><span data-stu-id="9c789-106">They are publicly available in the Microsoft repositories on [Docker Hub](https://hub.docker.com/u/microsoft/).</span></span> <span data-ttu-id="9c789-107">每個存放庫可以包含多個映像，視 .NET 版本及作業系統與版本而定 (Linux Debian、Linux Alpine、Windows Nano Server、Windows Server Core 等等)。</span><span class="sxs-lookup"><span data-stu-id="9c789-107">Each repository can contain multiple images, depending on .NET versions, and depending on the OS and versions (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core, etc.).</span></span>

<span data-ttu-id="9c789-108">Microsoft 對 .NET 存放庫的願景，是要提供細微且專注的存放庫，以代表特定的案例或工作負載。</span><span class="sxs-lookup"><span data-stu-id="9c789-108">Microsoft’s vision for .NET repositories is to have granular and focused repos, where a repo represents a specific scenario or workload.</span></span> <span data-ttu-id="9c789-109">例如，在 Docker 上使用 ASP.NET Core 時應該使用 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 映像，因為這些 ASP.NET Core 映像會提供其他最佳化，讓容器啟動更快速。</span><span class="sxs-lookup"><span data-stu-id="9c789-109">For instance, the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) images should be used when using ASP.NET Core on Docker, because those ASP.NET Core images provide additional optimizations so containers can start faster.</span></span>

<span data-ttu-id="9c789-110">另一方面，.NET Core 映像 (microsoft/Dotnet) 適用於以 .NET Core 為基礎的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c789-110">On the other hand, the .NET Core images (microsoft/dotnet) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="9c789-111">例如，批次處理、Azure WebJobs 及其他主控台案例都應使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="9c789-111">For example, batch processes, Azure WebJobs, and other console scenarios should use .NET Core.</span></span> <span data-ttu-id="9c789-112">這些映像不包含 ASP.NET Core 堆疊，以致容器映像較小。</span><span class="sxs-lookup"><span data-stu-id="9c789-112">Those images do not include the ASP.NET Core stack, resulting in a smaller container image.</span></span>

<span data-ttu-id="9c789-113">大部分的映像存放庫會提供大量的標籤，不僅協助您選取特定的架構版本，還協助您選擇作業系統 (Linux 發行版本或 Windows 版本)。</span><span class="sxs-lookup"><span data-stu-id="9c789-113">Most image repos provide extensive tagging to help you select not just a specific framework version, but also to choose an OS (Linux distro or Windows version).</span></span>

<span data-ttu-id="9c789-114">如需 Microsoft 提供之官方 .NET Docker 映像的進一步資訊，請參閱 [.NET Docker 映像摘要](https://aka.ms/dotnetdockerimages)。</span><span class="sxs-lookup"><span data-stu-id="9c789-114">For further information about the official .NET Docker images provided by Microsoft, see the [.NET Docker Images summary](https://aka.ms/dotnetdockerimages).</span></span>

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a><span data-ttu-id="9c789-115">開發與生產環境的 .NET core 和 Docker 映像最佳化比較</span><span class="sxs-lookup"><span data-stu-id="9c789-115">.NET Core and Docker image optimizations for development versus production</span></span>

<span data-ttu-id="9c789-116">在建置開發人員 Docker 映像時，Microsoft 會著重在下列主要案例︰</span><span class="sxs-lookup"><span data-stu-id="9c789-116">When building Docker images for developers, Microsoft focused on the following main scenarios:</span></span>

-   <span data-ttu-id="9c789-117">映像用來「開發」與建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c789-117">Images used to *develop* and build .NET Core apps.</span></span>

-   <span data-ttu-id="9c789-118">映像用來「執行」.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c789-118">Images used to *run* .NET Core apps.</span></span>

<span data-ttu-id="9c789-119">為何有多個映像？</span><span class="sxs-lookup"><span data-stu-id="9c789-119">Why multiple images?</span></span> <span data-ttu-id="9c789-120">在開發、建置及執行容器化應用程式時，您通常有不同的優先考量。</span><span class="sxs-lookup"><span data-stu-id="9c789-120">When developing, building, and running containerized applications, you usually have different priorities.</span></span> <span data-ttu-id="9c789-121">透過提供這些個別工作的不同映像，Microsoft 會協助最佳化開發、建置及部署應用程式的個別處理程序。</span><span class="sxs-lookup"><span data-stu-id="9c789-121">By providing different images for these separate tasks, Microsoft helps optimize the separate processes of developing, building, and deploying apps.</span></span>

### <a name="during-development-and-build"></a><span data-ttu-id="9c789-122">開發與建置期間</span><span class="sxs-lookup"><span data-stu-id="9c789-122">During development and build</span></span>

<span data-ttu-id="9c789-123">開發期間的重點是，您逐一查看變更的速度以及偵錯變更的能力。</span><span class="sxs-lookup"><span data-stu-id="9c789-123">During development, what is important is how fast you can iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="9c789-124">映像大小的重要性，不如變更程式碼及快速查看變更的能力。</span><span class="sxs-lookup"><span data-stu-id="9c789-124">The size of the image is not as important as the ability to make changes to your code and see the changes quickly.</span></span> <span data-ttu-id="9c789-125">有些工具和「組建代理程式容器」，會在開發及建置處理程序期間使用開發 ASP.NET Core 映像 (microsoft/aspnetcore-build)。</span><span class="sxs-lookup"><span data-stu-id="9c789-125">Some tools and "build-agent containers", use the development ASP.NET Core image (microsoft/aspnetcore-build) during development and build proces.</span></span> <span data-ttu-id="9c789-126">在 Docker 容器內部建置時，重要的層面是為編譯應用程式所需要的項目。</span><span class="sxs-lookup"><span data-stu-id="9c789-126">When building inside a Docker container, the important aspects are the elements that are needed in order to compile your app.</span></span> <span data-ttu-id="9c789-127">這包括編譯器和任何其他 .NET 相依性，加上如 npm、Gulp 和 Bower 等 Web 開發相依性。</span><span class="sxs-lookup"><span data-stu-id="9c789-127">This includes the compiler and any other .NET dependencies, plus web development dependencies like npm, Gulp, and Bower.</span></span>

<span data-ttu-id="9c789-128">這種組建映像為何如此重要？</span><span class="sxs-lookup"><span data-stu-id="9c789-128">Why is this type of build image important?</span></span> <span data-ttu-id="9c789-129">您不會將此映像部署到生產環境。</span><span class="sxs-lookup"><span data-stu-id="9c789-129">You do not deploy this image to production.</span></span> <span data-ttu-id="9c789-130">此映像是您用來建置要放入生產環境映像的內容。</span><span class="sxs-lookup"><span data-stu-id="9c789-130">Instead, it is an image you use to build the content you place into a production image.</span></span> <span data-ttu-id="9c789-131">此映像可用於持續整合 (CI) 環境或組建環境。</span><span class="sxs-lookup"><span data-stu-id="9c789-131">This image would be used in your continuous integration (CI) environment or build environment.</span></span> <span data-ttu-id="9c789-132">例如，不是直接在組建代理程式主機 (例如 VM) 上手動安裝所有應用程式相依性，組建代理程式會使用所需的全部相依性具現化 .NET Core 組建映像，來建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c789-132">For instance, rather than manually installing all your application dependencies directly on a build agent host (a VM, for example), the build agent would instantiate a .NET Core build image with all the dependencies required to build the application.</span></span> <span data-ttu-id="9c789-133">組建代理程式只需要知道如何執行此 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="9c789-133">Your build agent only needs to know how to run this Docker image.</span></span> <span data-ttu-id="9c789-134">這可簡化 CI 環境，並使其更容易預測。</span><span class="sxs-lookup"><span data-stu-id="9c789-134">This simplifies your CI environment and makes it much more predictable.</span></span>

### <a name="in-production"></a><span data-ttu-id="9c789-135">生產環境</span><span class="sxs-lookup"><span data-stu-id="9c789-135">In production</span></span>

<span data-ttu-id="9c789-136">生產環境的重點是部署和啟動以生產環境 .NET Core 映像為基礎之容器的速度。</span><span class="sxs-lookup"><span data-stu-id="9c789-136">What is important in production is how fast you can deploy and start your containers based on a production .NET Core image.</span></span> <span data-ttu-id="9c789-137">因此，以 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 為基礎的僅執行階段映像很小，方便它快速從您的 Docker 登錄跨越網路到您的 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="9c789-137">Therefore, the runtime-only image based on [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) is small so that it can travel quickly across the network from your Docker registry to your Docker hosts.</span></span> <span data-ttu-id="9c789-138">準備好執行的內容可用最短的時間完成啟動容器到處理結果的流程。</span><span class="sxs-lookup"><span data-stu-id="9c789-138">The contents are ready to run, enabling the fastest time from starting the container to processing results.</span></span> <span data-ttu-id="9c789-139">在 Docker 模型中不必編譯 C\# 程式碼，因為當您使用組建容器執行 Dotnet 組建或 Dotnet 發行時就有了。</span><span class="sxs-lookup"><span data-stu-id="9c789-139">In the Docker model, there is no need for compilation from C\# code, as there is when you run dotnet build or dotnet publish when using the build container.</span></span>

<span data-ttu-id="9c789-140">在此最佳化的映像中，您只放入執行應用程式所需的二進位檔和其他內容。</span><span class="sxs-lookup"><span data-stu-id="9c789-140">In this optimized image you put only the binaries and other content needed to run the application.</span></span> <span data-ttu-id="9c789-141">例如，Dotnet 發佈所建立的內容只包含已編譯的 .NET 二進位檔、映像、.js 和 .css 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c789-141">For example, the content created by dotnet publish contains only the compiled .NET binaries, images, .js, and .css files.</span></span> <span data-ttu-id="9c789-142">一段時間後，您會看到包含預先 JIT 編譯套件的映像。</span><span class="sxs-lookup"><span data-stu-id="9c789-142">Over time, you will see images that contain pre-jitted packages.</span></span>

<span data-ttu-id="9c789-143">雖然有多種版本的 .NET Core 和 ASP.NET Core 映像，但它們全都共用一或多個圖層，包括基底圖層。</span><span class="sxs-lookup"><span data-stu-id="9c789-143">Although there are multiple versions of the .NET Core and ASP.NET Core images, they all share one or more layers, including the base layer.</span></span> <span data-ttu-id="9c789-144">因此，儲存映像所需的磁碟空間量很小，僅為您自訂映像及其基底映像之間的差異。</span><span class="sxs-lookup"><span data-stu-id="9c789-144">Therefore, the amount of disk space needed to store an image is small; it consists only of the delta between your custom image and its base image.</span></span> <span data-ttu-id="9c789-145">結果是可從登錄快速提取映像。</span><span class="sxs-lookup"><span data-stu-id="9c789-145">The result is that it is quick to pull the image from your registry.</span></span>

<span data-ttu-id="9c789-146">當您瀏覽 Docker Hub 的 .NET 映像存放庫時，您會發現以標籤分類或標記的多個映像版本。</span><span class="sxs-lookup"><span data-stu-id="9c789-146">When you explore the .NET image repositories at Docker Hub, you will find multiple image versions classified or marked with tags.</span></span> <span data-ttu-id="9c789-147">這些標籤可協助您根據需要的版本決定使用的版本，如同下表中的這些：</span><span class="sxs-lookup"><span data-stu-id="9c789-147">These tags help to decide which one to use, depending on the version you need, like those in the following table:</span></span>

-   <span data-ttu-id="9c789-148">microsoft/**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="9c789-148">microsoft/**aspnetcore:2.0**</span></span>

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   <span data-ttu-id="9c789-149">microsoft/**aspnetcore-build:2.0**</span><span class="sxs-lookup"><span data-stu-id="9c789-149">microsoft/**aspnetcore-build:2.0**</span></span>

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
<span data-ttu-id="9c789-150">[上一頁] (net-container-os-targets.md) [下一頁] (../architect-microservice-container-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="9c789-150">[Previous] (net-container-os-targets.md) [Next] (../architect-microservice-container-applications/index.md)</span></span>
