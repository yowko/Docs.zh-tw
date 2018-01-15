---
title: ".NET 和 Docker 簡介"
description: "了解 Docker 和 .NET Core"
keywords: ".NET、.NET Core、Docker"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.workload: dotnetcore
ms.openlocfilehash: 8c6daabb3040998d3376ad022790c16b9629233f
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2018
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="1038d-104">.NET 和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="1038d-104">Introduction to .NET and Docker</span></span>

<span data-ttu-id="1038d-105">本文提供在 Docker 上使用 .NET 的簡介和概念背景。</span><span class="sxs-lookup"><span data-stu-id="1038d-105">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span>

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="1038d-106">Docker：封裝您的應用程式以在任何位置部署及執行</span><span class="sxs-lookup"><span data-stu-id="1038d-106">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="1038d-107">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) 是一個開放的平台，可讓開發人員和系統管理員在稱為[容器](https://www.docker.com/what-container) \(英文\) 的鬆散隔離環境中，建立[映像](https://docs.docker.com/glossary/?term=image) \(英文\)、遞送及執行分散式應用程式。</span><span class="sxs-lookup"><span data-stu-id="1038d-107">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="1038d-108">此作法能在開發、QA 和生產環境之間，實現有效率的應用程式生命週期管理。</span><span class="sxs-lookup"><span data-stu-id="1038d-108">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="1038d-109">[Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform) \(英文\) 使用 [Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine) \(英文\) 來將應用程式快速建置及封裝為 [Docker 映像](https://docs.docker.com/glossary/?term=image) \(英文\)，映像是使用以 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) \(英文\) 格式撰寫的檔案來建立，並於後續會將它部署到[分層式容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers) \(英文\) 並在其中執行。</span><span class="sxs-lookup"><span data-stu-id="1038d-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="1038d-110">您可以建立自己的[分層式映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) \(英文\) 作為 Dockerfile，或使用來自 [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub) \(英文\) 等[登錄](https://docs.docker.com/glossary/?term=registry) \(英文\) 的現有分層式映像。</span><span class="sxs-lookup"><span data-stu-id="1038d-110">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="1038d-111">在[進行容器化應用程式或微服務的架構設計及建置](../../standard/microservices-architecture/architect-microservice-container-applications/index.md)時，[Docker 容器、映像和登錄之間的關係](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md)是相當重要的概念。</span><span class="sxs-lookup"><span data-stu-id="1038d-111">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="1038d-112">此作法能大幅縮短開發和部署之間的時間。</span><span class="sxs-lookup"><span data-stu-id="1038d-112">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="1038d-113">延伸閱讀 (及觀賞)</span><span class="sxs-lookup"><span data-stu-id="1038d-113">Further reading (and watching)</span></span>

* <span data-ttu-id="1038d-114">[Windows 型容器：具企業級控制的新式應用程式開發。](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-114">[Windows-based containers: Modern app development with enterprise-grade control.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)</span></span>
* <span data-ttu-id="1038d-115">[Docker 概觀](https://docs.docker.com/engine/docker-overview/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-115">[Docker overview](https://docs.docker.com/engine/docker-overview/)</span></span>
* [<span data-ttu-id="1038d-116">Windows 容器上的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="1038d-116">Dockerfile on Windows Containers</span></span>](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile.md)
* <span data-ttu-id="1038d-117">[撰寫 Dockerfile 的最佳做法](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-117">[Best practices for writing Dockerfiles](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)</span></span>
* [<span data-ttu-id="1038d-118">建置 .NET Core 應用程式的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="1038d-118">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="1038d-119">取得 .NET Docker 映像</span><span class="sxs-lookup"><span data-stu-id="1038d-119">Getting .NET Docker images</span></span>

<span data-ttu-id="1038d-120">官方 .NET Docker 映像是由 Microsoft 所建立及最佳化。</span><span class="sxs-lookup"><span data-stu-id="1038d-120">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="1038d-121">它們在 Docker Hub 上的 Microsoft 存放庫中公開提供。</span><span class="sxs-lookup"><span data-stu-id="1038d-121">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="1038d-122">視 .NET 版本和 OS 版本而定，每個存放庫可能會包含多個映像。</span><span class="sxs-lookup"><span data-stu-id="1038d-122">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="1038d-123">大部分的映像存放庫提供大量的標籤，來協助您選取特定的架構版本和 OS (Linux 發行版本或 Windows 版本)。</span><span class="sxs-lookup"><span data-stu-id="1038d-123">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="1038d-124">以案例為基礎的指引</span><span class="sxs-lookup"><span data-stu-id="1038d-124">Scenario based guidance</span></span>

<span data-ttu-id="1038d-125">Microsoft 針對 .NET 存放庫的目的，是要提供細微且專注的存放庫，以代表特定的案例或工作負載。</span><span class="sxs-lookup"><span data-stu-id="1038d-125">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="1038d-126">`microsoft/aspnetcore` 映像已針對 Docker 上的 ASP.NET Core 應用程式進行最佳化，使容器可以更快速地啟動。</span><span class="sxs-lookup"><span data-stu-id="1038d-126">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="1038d-127">.NET Core 映像 (`microsoft/dotnet`) 則適用於以 .NET Core 為基礎的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="1038d-127">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="1038d-128">例如，批次處理、Azure WebJobs 及其他主控台案例，都應使用最佳化的 .NET Core 映像。</span><span class="sxs-lookup"><span data-stu-id="1038d-128">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="1038d-129">最明顯的 Docker 和 .NET 應用程式水平使用案例，是將它們用於生產部署和裝載。</span><span class="sxs-lookup"><span data-stu-id="1038d-129">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="1038d-130">結果顯示生產只是單一案例，而其他案例也同樣有用。</span><span class="sxs-lookup"><span data-stu-id="1038d-130">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="1038d-131">這些案例並非 .NET 特定，但應該適用於大部分的開發人員平台。</span><span class="sxs-lookup"><span data-stu-id="1038d-131">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="1038d-132">**低負擔安裝**：不須在本機安裝就能試用 .NET。</span><span class="sxs-lookup"><span data-stu-id="1038d-132">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="1038d-133">只要下載具有 .NET 的 Docker 映像即可。</span><span class="sxs-lookup"><span data-stu-id="1038d-133">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="1038d-134">**在容器中開發**：您可以在一致的環境中開發，來使開發環境與生產環境相似 (避免開發人員電腦上的全域狀態等問題)。</span><span class="sxs-lookup"><span data-stu-id="1038d-134">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="1038d-135">Visual Studio Tools for Docker 甚至可讓您直接從 Visual Studio 啟動容器。</span><span class="sxs-lookup"><span data-stu-id="1038d-135">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="1038d-136">**在容器中測試**：您可以在容器中測試，以減少因環境設定不正確，或是因上一個測試所遺留的變更所造成的失敗。</span><span class="sxs-lookup"><span data-stu-id="1038d-136">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="1038d-137">**在容器中建置**：您可以在容器中建置程式碼，以免除針對多個環境正確設定共用組建電腦的必要性，並改為採用 "BYOC" (自備容器) 的作法。</span><span class="sxs-lookup"><span data-stu-id="1038d-137">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="1038d-138">**在所有環境中部署**：您可以透過所有環境部署映像。</span><span class="sxs-lookup"><span data-stu-id="1038d-138">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="1038d-139">此作法可減少因設定差異所造成的失敗，通常是因外部設定而變更映像行為 (例如插入環境變數)。</span><span class="sxs-lookup"><span data-stu-id="1038d-139">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="1038d-140">可協助針對 Docker 容器開發在 .NET Core 和 .NET Framework 之間進行決定的[一般指引](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="1038d-140">[General guidance](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="1038d-141">常見的 Docker 開發案例</span><span class="sxs-lookup"><span data-stu-id="1038d-141">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="1038d-142">.NET 核心</span><span class="sxs-lookup"><span data-stu-id="1038d-142">.NET Core</span></span>

<span data-ttu-id="1038d-143">**.NET Core 資源**</span><span class="sxs-lookup"><span data-stu-id="1038d-143">**.NET Core resources**</span></span>

 <span data-ttu-id="1038d-144">挑選符合感興趣之案例的 .NET Core 範例。</span><span class="sxs-lookup"><span data-stu-id="1038d-144">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="1038d-145">所有範例指示都會描述如何從 Windows、Linux 或 macOS 主機將 Windows 或 Linux Docker 映像設為目標。</span><span class="sxs-lookup"><span data-stu-id="1038d-145">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="1038d-146">範例使用 .NET Core 2.0。</span><span class="sxs-lookup"><span data-stu-id="1038d-146">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="1038d-147">它們會在適當之處使用 Docker [多階段建置](https://github.com/dotnet/announcements/issues/18) \(英文\) 和[多架構標籤](https://github.com/dotnet/announcements/issues/14) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="1038d-147">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* <span data-ttu-id="1038d-148">[Docker Hub 上的 .NET Core 映像](https://hub.docker.com/r/microsoft/dotnet/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-148">[.NET Core images on DockerHub](https://hub.docker.com/r/microsoft/dotnet/)</span></span>

* <span data-ttu-id="1038d-149">[將 .NET Core 應用程式 Docker 化](https://docs.docker.com/engine/examples/dotnetcore/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-149">[Dockerize a .NET Core application](https://docs.docker.com/engine/examples/dotnetcore/)</span></span>

* <span data-ttu-id="1038d-150">此 .NET Core Docker 範例示範如何[在您的 .NET Core 開發程序中使用 Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="1038d-150">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="1038d-151">該範例可與 Linux 或 Windows 容器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1038d-151">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="1038d-152">此 .NET Core Docker 範例示範[建置適用於生產之 .NET Core 應用程式的 Docker 映像](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) \(英文\) 的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="1038d-152">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="1038d-153">該範例可與 Linux 或 Windows 容器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1038d-153">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="1038d-154">此 [.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) \(英文\) 示範建置[獨立 .NET Core 應用程式](../deploying/index.md)的 Docker 映像的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="1038d-154">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](../deploying/index.md).</span></span> <span data-ttu-id="1038d-155">用於最小的生產容器，而沒有因[在容器之間共用基礎映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/) \(英文\) 所產生的優點。</span><span class="sxs-lookup"><span data-stu-id="1038d-155">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="1038d-156">不過，可共用較底層的 Docker 層。</span><span class="sxs-lookup"><span data-stu-id="1038d-156">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="1038d-157">ARM32 / Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="1038d-157">ARM32 / Raspberry Pi</span></span>

* <span data-ttu-id="1038d-158">[.NET Core 執行階段 ARM32 組建宣告](https://github.com/dotnet/announcements/issues/29) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-158">[.NET Core Runtime ARM32 builds announcement](https://github.com/dotnet/announcements/issues/29)</span></span>

* <span data-ttu-id="1038d-159">[Docker Hub 上的 ARM32 / Raspberry Pi .NET Core 映像](https://hub.docker.com/r/microsoft/dotnet/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-159">[ARM32 / Raspberry Pi .NET Core images on DockerHub](https://hub.docker.com/r/microsoft/dotnet/)</span></span>

* <span data-ttu-id="1038d-160">[GitHub 上的 ARM32 / Raspberry Pi .NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-160">[ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)</span></span>

#### <a name="net-framework"></a><span data-ttu-id="1038d-161">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1038d-161">.NET Framework</span></span>

* <span data-ttu-id="1038d-162">[Docker Hub 上的 .NET Framework 映像](https://hub.docker.com/r/microsoft/dotnet-framework/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-162">[.NET Framework images on DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/)</span></span>

<span data-ttu-id="1038d-163">此存放庫包含示範各種 .NET Framework Docker 設定的範例。</span><span class="sxs-lookup"><span data-stu-id="1038d-163">This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="1038d-164">您可以使用這些映像作為自己 Docker 映像的基礎。</span><span class="sxs-lookup"><span data-stu-id="1038d-164">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="1038d-165">**.NET Framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="1038d-165">**.NET Framework 4.7**</span></span>

<span data-ttu-id="1038d-166">[dotnet-framework:4.7 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) 示範 [.NET Framework 4.7](../../framework/whats-new/index.md#v47) 的基本 "Hello World" 使用方式。</span><span class="sxs-lookup"><span data-stu-id="1038d-166">The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span></span> <span data-ttu-id="1038d-167">它示範如何仰賴 [.NET Framework 4.7 Docker 映像](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile) \(英文\) 建置及部署該應用程式。</span><span class="sxs-lookup"><span data-stu-id="1038d-167">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span></span>

<span data-ttu-id="1038d-168">**.NET Framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="1038d-168">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="1038d-169">[dotnet-framework:4.6.2 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) \(英文\) 示範 [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462) 的基本 "Hello World" 使用方式。</span><span class="sxs-lookup"><span data-stu-id="1038d-169">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span></span> <span data-ttu-id="1038d-170">它示範如何仰賴 [.NET Framework 4.6.2 Docker 映像](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2) \(英文\) 建置及部署該應用程式。</span><span class="sxs-lookup"><span data-stu-id="1038d-170">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span></span>

<span data-ttu-id="1038d-171">**.NET Framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="1038d-171">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="1038d-172">[dotnet-framework:3.5 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) \(英文\) 示範 [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5) \(英文\) 的基本 "Hello World" 使用方式。</span><span class="sxs-lookup"><span data-stu-id="1038d-172">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span></span> <span data-ttu-id="1038d-173">它示範如何仰賴 Docker 中的 .NET Framework 3.5 建置及部署專案。</span><span class="sxs-lookup"><span data-stu-id="1038d-173">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="1038d-174">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1038d-174">ASP.NET Core</span></span>

* <span data-ttu-id="1038d-175">[此 ASP.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) \(英文\) 示範建置適用於生產之 ASP.NET Core 應用程式的 Docker 映像的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="1038d-175">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="1038d-176">該範例可與 Linux 或 Windows 容器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1038d-176">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="1038d-177">[Docker Hub 上的 ASP.NET Core 映像](https://hub.docker.com/r/microsoft/aspnetcore-build/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-177">[ASP.NET Core images on DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)</span></span>

* <span data-ttu-id="1038d-178">[GitHub 上的 ASP.NET Core 映像](https://github.com/aspnet/aspnet-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-178">[ASP.NET Core images on GitHub](https://github.com/aspnet/aspnet-docker)</span></span>

#### <a name="aspnet-framework"></a><span data-ttu-id="1038d-179">ASP.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1038d-179">ASP.NET Framework</span></span>

* <span data-ttu-id="1038d-180">[Docker Hub 上的 ASP.NET Framework 映像](https://hub.docker.com/r/microsoft/aspnet/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-180">[ASP.NET Framework images on DockerHub](https://hub.docker.com/r/microsoft/aspnet/)</span></span>

* <span data-ttu-id="1038d-181">[.NET Framework 4.6.2 範例上的 ASP.NET Web Form 應用程式](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-181">[ASP.NET Web Forms app on .NET Framework 4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)</span></span>

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="1038d-182">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="1038d-182">Windows Communication Framework (WCF)</span></span>

* <span data-ttu-id="1038d-183">[Docker Hub 上的 Windows Communication Framework (WCF) 映像](https://hub.docker.com/r/microsoft/wcf/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-183">[Windows Communication Framework (WCF) images on DockerHub](https://hub.docker.com/r/microsoft/wcf/)</span></span>

* <span data-ttu-id="1038d-184">[GitHub 上的 Windows Communication Framework (WCF) 映像](https://github.com/microsoft/iis-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-184">[Windows Communication Framework (WCF) images on GitHub](https://github.com/microsoft/iis-docker)</span></span>

* <span data-ttu-id="1038d-185">[使用 .NET Full Framework 4.6.2 的 Windows Communication Framework (WCF) Docker 範例](https://github.com/Microsoft/wcf-docker-samples) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-185">[Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2](https://github.com/Microsoft/wcf-docker-samples)</span></span>

#### <a name="internet-information-server-iis"></a><span data-ttu-id="1038d-186">Internet Information Server (IIS)</span><span class="sxs-lookup"><span data-stu-id="1038d-186">Internet Information Server (IIS)</span></span>

* <span data-ttu-id="1038d-187">[Docker Hub 上的 Internet Information Server (IIS) 映像](https://hub.docker.com/r/microsoft/iis/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-187">[Internet Information Server (IIS) images on DockerHub](https://hub.docker.com/r/microsoft/iis/)</span></span>

* <span data-ttu-id="1038d-188">[GitHub 上的 Internet Information Server (IIS) 映像](https://github.com/microsoft/wcf-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-188">[Internet Information Server (IIS) images on GitHub](https://github.com/microsoft/wcf-docker)</span></span>

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="1038d-189">與其他 Microsoft 堆疊容器映像互動</span><span class="sxs-lookup"><span data-stu-id="1038d-189">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="1038d-190">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="1038d-190">Microsoft SQL Server</span></span>

* <span data-ttu-id="1038d-191">[透過 Docker 快速入門執行適用於 Linux 的 Microsoft SQL Server 2017 容器映像](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker) \(機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="1038d-191">[Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)</span></span>

* <span data-ttu-id="1038d-192">[Docker Hub 上適用於 Linux 的 Microsoft SQL Server 映像](https://hub.docker.com/r/microsoft/mssql-server-windows/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-192">[Microsoft SQL Server for Linux images on DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)</span></span>

* <span data-ttu-id="1038d-193">[Docker Hub 上適用於 Windows 容器的 Microsoft SQL Server 映像](https://hub.docker.com/r/microsoft/mssql-server-windows/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-193">[Microsoft SQL Server for Windows Containers images on DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)</span></span>

* <span data-ttu-id="1038d-194">[Docker Hub 上適用於 Windows 容器的 Microsoft SQL Server Express 版本映像](https://hub.docker.com/r/microsoft/mssql-server-windows-express/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-194">[Microsoft SQL Server Express Edition images for Windows Containers on DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)</span></span>

* <span data-ttu-id="1038d-195">[Docker Hub 上適用於 Windows 容器的 Microsoft SQL Server Developer 版本映像](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-195">[Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)</span></span>

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="1038d-196">Visual Studio Team Services (VSTS) 代理程式</span><span class="sxs-lookup"><span data-stu-id="1038d-196">Visual Studio Team Services (VSTS) agent</span></span>

* <span data-ttu-id="1038d-197">[Docker Hub 上的 Visual Studio Team Services (VSTS) 代理程式映像](https://hub.docker.com/r/microsoft/vsts-agent/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-197">[Visual Studio Team Services (VSTS) agent images on DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)</span></span>

* <span data-ttu-id="1038d-198">[GitHub 上的 Visual Studio Team Services (VSTS) 代理程式映像](https://github.com/Microsoft/vsts-agent-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-198">[Visual Studio Team Services (VSTS) agent images on GitHub](https://github.com/Microsoft/vsts-agent-docker)</span></span>

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="1038d-199">Operations Management Suite (OMS) Linux 代理程式</span><span class="sxs-lookup"><span data-stu-id="1038d-199">Operations Management Suite (OMS) Linux agent</span></span>

* <span data-ttu-id="1038d-200">[Operations Management Suite (OMS) Linux 代理程式概觀](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-200">[Operations Management Suite (OMS) Linux agent overview](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)</span></span>

* <span data-ttu-id="1038d-201">[Docker Hub 上的 Operations Management Suite (OMS) 映像](https://hub.docker.com/r/microsoft/vsts-agent/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-201">[Operations Management Suite (OMS) images on DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)</span></span>

* <span data-ttu-id="1038d-202">[GitHub 上的 Operations Management Suite (OMS) 映像](https://github.com/Microsoft/OMS-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-202">[Operations Management Suite (OMS) images on GitHub](https://github.com/Microsoft/OMS-docker)</span></span>

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="1038d-203">Microsoft Azure 命令列介面 (CLI)</span><span class="sxs-lookup"><span data-stu-id="1038d-203">Microsoft Azure Command Line Interface (CLI)</span></span>

* <span data-ttu-id="1038d-204">[Docker Hub 上的 Microsoft Azure 命令列介面 (CLI) 映像](https://hub.docker.com/r/microsoft/azure-cli/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-204">[Microsoft Azure Command Line Interface (CLI) images on DockerHub](https://hub.docker.com/r/microsoft/azure-cli/)</span></span> 

* <span data-ttu-id="1038d-205">[GitHub 上的 Microsoft Azure 命令列介面 (CLI) 映像](https://github.com/Microsoft/OMS-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-205">[Microsoft Azure Command-Line Interface (CLI) images on GitHub](https://github.com/Microsoft/OMS-docker)</span></span>

> [!NOTE]
> <span data-ttu-id="1038d-206">如果您沒有 Azure 訂用帳戶，請[立即註冊](https://azure.microsoft.com/free/?b=16.48)可免費使用 30 天的帳戶，並獲得 $200 美元的 Azure 點數來試用其他的 Azure 服務組合。</span><span class="sxs-lookup"><span data-stu-id="1038d-206">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="1038d-207">Microsoft Azure Cosmos DB 模擬器 (僅限 Windows 容器)</span><span class="sxs-lookup"><span data-stu-id="1038d-207">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* <span data-ttu-id="1038d-208">[Docker Hub 上的 Microsoft Azure Cosmos DB 模擬器映像](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-208">[Microsoft Azure Cosmos DB Emulator images on DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator)</span></span> 

* [<span data-ttu-id="1038d-209">將 Azure Cosmos DB 模擬器用於本機開發及測試</span><span class="sxs-lookup"><span data-stu-id="1038d-209">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](/azure/cosmos-db/local-emulator.md#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="1038d-210">探索豐富的 Docker 開發生態系統</span><span class="sxs-lookup"><span data-stu-id="1038d-210">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="1038d-211">在了解 Docker 平台和不同的 Docker 映像之後，您接著可以探索豐富的 Docker 生態系統。</span><span class="sxs-lookup"><span data-stu-id="1038d-211">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="1038d-212">以下連結能提供 Microsoft 工具支援容器開發的方式。</span><span class="sxs-lookup"><span data-stu-id="1038d-212">The following links show you how the Microsoft tools complement container development.</span></span>

* <span data-ttu-id="1038d-213">[搭配使用 .NET 和 Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-213">[Using .NET and Docker together](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)</span></span>
* [<span data-ttu-id="1038d-214">設計和開發多容器和微服務 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="1038d-214">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* <span data-ttu-id="1038d-215">[Visual Studio Code Docker 擴充功能](https://code.visualstudio.com/docs/languages/dockerfile) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-215">[Visual Studio Code Docker extension](https://code.visualstudio.com/docs/languages/dockerfile)</span></span>
* [<span data-ttu-id="1038d-216">了解如何使用 Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="1038d-216">Learn how to use Azure Service Fabric</span></span>](/azure/service-fabric/index.md)
* <span data-ttu-id="1038d-217">[Service Fabric 使用者入門範例](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-217">[Service Fabric Getting Started Sample](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)</span></span>
* [<span data-ttu-id="1038d-218">Windows 容器的優點</span><span class="sxs-lookup"><span data-stu-id="1038d-218">Benefits of Windows Containers</span></span>](/virtualization/windowscontainers/about/index.md#video-overview)
* [<span data-ttu-id="1038d-219">使用 Visual Studio Docker 工具</span><span class="sxs-lookup"><span data-stu-id="1038d-219">Working with Visual Studio Docker Tools</span></span>](/aspnet/core/publishing/visual-studio-tools-for-docker/index.md)
* <span data-ttu-id="1038d-220">[將 Docker 映像從 Azure Container Registry 部署到 Azure 容器執行個體](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-220">[Deploying Docker Images from the Azure Container Registry to Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)</span></span>
* <span data-ttu-id="1038d-221">[使用 Visual Studio Code 進行偵錯](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-221">[Debugging with Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)</span></span>
* <span data-ttu-id="1038d-222">[開始使用 Visual Studio for Mac、容器，以及雲端中的無伺服器程式碼](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-222">[Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)</span></span>
* <span data-ttu-id="1038d-223">[開始使用 Docker 和 Visual Studio for Mac 實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1038d-223">[Getting Started with Docker and Visual Studio for Mac Lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)</span></span>

## <a name="next-steps"></a><span data-ttu-id="1038d-224">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1038d-224">Next steps</span></span>

* [<span data-ttu-id="1038d-225">了解 .NET Core 的 Docker 基本概念</span><span class="sxs-lookup"><span data-stu-id="1038d-225">Learn Docker Basics with .NET Core</span></span>](docker-basics-dotnet-core.md)
* [<span data-ttu-id="1038d-226">建置 .NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="1038d-226">Building .NET Core Docker Images</span></span>](building-net-docker-images.md)
