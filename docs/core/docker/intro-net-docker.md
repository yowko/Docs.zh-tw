---
title: ".NET 和 Docker 簡介"
description: "了解 Docker 和.NET 核心"
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
ms.openlocfilehash: 1c9ce7a008c86d1c245ce8b7d616e05fcb3d4bbc
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="86d52-104">.NET 和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="86d52-104">Introduction to .NET and Docker</span></span>

 <span data-ttu-id="86d52-105">本文章提供簡介與使用.NET docker 的概念背景。</span><span class="sxs-lookup"><span data-stu-id="86d52-105">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span> 

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="86d52-106">Docker： 封裝您的應用程式部署和執行任何位置</span><span class="sxs-lookup"><span data-stu-id="86d52-106">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="86d52-107">[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined)是開放式平台，可讓開發人員和管理員建置[映像](https://docs.docker.com/glossary/?term=image)、 出貨，和呼叫鬆散隔離環境中執行分散式應用程式[容器](https://www.docker.com/what-container).</span><span class="sxs-lookup"><span data-stu-id="86d52-107">[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="86d52-108">這個方法可讓開發、 品管及生產環境之間的有效的應用程式生命週期管理。</span><span class="sxs-lookup"><span data-stu-id="86d52-108">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="86d52-109">[Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform)使用[Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine)快速建置並封裝為應用程式[Docker images](https://docs.docker.com/glossary/?term=image)使用檔案寫入建立[Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile)格式，然後部署及執行[分層容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)。</span><span class="sxs-lookup"><span data-stu-id="86d52-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="86d52-110">您可以建立您自己[分層映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)dockerfiles 或使用現有從[登錄](https://docs.docker.com/glossary/?term=registry)、 like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub)。</span><span class="sxs-lookup"><span data-stu-id="86d52-110">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="86d52-111">[Docker 容器、 影像和登錄之間的關聯性](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries)是重要的概念時[架構和建置容器化應用程式或 microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/)。</span><span class="sxs-lookup"><span data-stu-id="86d52-111">The [relationship between Docker containers, images, and registries](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries) is an important concept when [architecting and building containerized applications or microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/).</span></span> <span data-ttu-id="86d52-112">這種方法可大幅縮短開發到部署之間的時間。</span><span class="sxs-lookup"><span data-stu-id="86d52-112">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="86d52-113">進一步閱讀 （和觀賞）</span><span class="sxs-lookup"><span data-stu-id="86d52-113">Further reading (and watching)</span></span>

* [<span data-ttu-id="86d52-114">Windows 容器： 企業級控制與現代化應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="86d52-114">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="86d52-115">Docker 概觀</span><span class="sxs-lookup"><span data-stu-id="86d52-115">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="86d52-116">Windows 容器上的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="86d52-116">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="86d52-117">寫入 Dockerfiles 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="86d52-117">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="86d52-118">.NET Core 應用程式的建置 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-118">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="86d52-119">取得.NET Docker 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-119">Getting .NET Docker Images</span></span>

<span data-ttu-id="86d52-120">建立和最佳化 microsoft 官方.NET Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="86d52-120">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="86d52-121">它們會公開使用銜接站集線器上的 Microsoft 儲存機制中。</span><span class="sxs-lookup"><span data-stu-id="86d52-121">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="86d52-122">每個儲存機制可以包含多個映像，根據.NET 版本和作業系統版本上。</span><span class="sxs-lookup"><span data-stu-id="86d52-122">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="86d52-123">大部分的映像儲存機制提供更詳盡的標記，可協助您選取特定的 framework 版本和作業系統 （Linux distro 或 Windows 版本）。</span><span class="sxs-lookup"><span data-stu-id="86d52-123">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="86d52-124">案例基礎指引</span><span class="sxs-lookup"><span data-stu-id="86d52-124">Scenario Based Guidance</span></span>

<span data-ttu-id="86d52-125">.NET 的儲存機制的 Microsoft 的目的是讓細微和焦點代表特定案例或工作負載的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="86d52-125">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="86d52-126">`microsoft/aspnetcore`映像適合用於 ASP.NET Core 應用程式上 Docker，因此可以更快速啟動容器。</span><span class="sxs-lookup"><span data-stu-id="86d52-126">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="86d52-127">.NET Core 映像 (`microsoft/dotnet`) 是針對.NET 核心為基礎的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="86d52-127">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="86d52-128">例如，批次程序、 Azure Webjob 和其他主控台案例應該使用最佳化的.NET Core 映像。</span><span class="sxs-lookup"><span data-stu-id="86d52-128">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="86d52-129">使用 Docker 和.NET 應用程式的最明顯的水平案例適用於生產環境部署和裝載。</span><span class="sxs-lookup"><span data-stu-id="86d52-129">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="86d52-130">其實生產狀況下只有一個，和其他項目同樣適合。</span><span class="sxs-lookup"><span data-stu-id="86d52-130">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="86d52-131">這些案例不是特定的.NET 中，但應套用至大部分的開發人員平台。</span><span class="sxs-lookup"><span data-stu-id="86d52-131">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="86d52-132">**低人事安裝**— 您可以試用.NET 而不是本機安裝。</span><span class="sxs-lookup"><span data-stu-id="86d52-132">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="86d52-133">剛才下載.NET 中它的 Docker 映的像。</span><span class="sxs-lookup"><span data-stu-id="86d52-133">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="86d52-134">**開發在容器中**— 您可以開發一致性的環境中進行開發和生產環境類似 （避免程式開發人員電腦上的全域狀態等問題）。</span><span class="sxs-lookup"><span data-stu-id="86d52-134">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="86d52-135">Visual Studio Tools for Docker 甚至可讓您直接從 Visual Studio 啟動容器。</span><span class="sxs-lookup"><span data-stu-id="86d52-135">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="86d52-136">**測試容器中**— 您可以測試在容器中，減少因為設定不正確的環境而發生失敗或其他變更遺留從最後一次測試。</span><span class="sxs-lookup"><span data-stu-id="86d52-136">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="86d52-137">**在容器中建立**— 您可以建置程式碼，在容器中，需要正確地設定多個環境中共用的組建電腦，但改為將移至"BYOC"（攜帶您自己的容器） 的方法。</span><span class="sxs-lookup"><span data-stu-id="86d52-137">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="86d52-138">**在所有環境中的部署**— 您可以透過您的環境的所有部署映像。</span><span class="sxs-lookup"><span data-stu-id="86d52-138">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="86d52-139">這種方法可減少由於設定的差異，通常會透過外部組態 （例如，插入的環境變數） 的映像行為變更失敗。</span><span class="sxs-lookup"><span data-stu-id="86d52-139">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="86d52-140">[一般指引](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance)Docker 容器開發的.NET Core 和.NET Framework 之間決定。</span><span class="sxs-lookup"><span data-stu-id="86d52-140">[General guidance](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="86d52-141">常見的 Docker 開發案例</span><span class="sxs-lookup"><span data-stu-id="86d52-141">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="86d52-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="86d52-142">.NET Core</span></span>

<span data-ttu-id="86d52-143">**.NET 核心資源**</span><span class="sxs-lookup"><span data-stu-id="86d52-143">**.NET Core resources**</span></span>

 <span data-ttu-id="86d52-144">挑選適合您案例感興趣的.NET Core 範例。</span><span class="sxs-lookup"><span data-stu-id="86d52-144">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="86d52-145">所有範例的指示都說明如何從 Windows、 Linux 或 macOS 主機的 Windows 或 Linux Docker 映像的目標。</span><span class="sxs-lookup"><span data-stu-id="86d52-145">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="86d52-146">這些範例會使用.NET 核心 2.0。</span><span class="sxs-lookup"><span data-stu-id="86d52-146">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="86d52-147">在使用 Docker[多階段建置](https://github.com/dotnet/announcements/issues/18)和[多 arch 標記](https://github.com/dotnet/announcements/issues/14)適當的位置。</span><span class="sxs-lookup"><span data-stu-id="86d52-147">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="86d52-148">.NET core 映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-148">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="86d52-149">Dockerize.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="86d52-149">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="86d52-150">這個.NET Core Docker 範例會示範如何[.NET Core 開發程序中使用 Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev)。</span><span class="sxs-lookup"><span data-stu-id="86d52-150">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="86d52-151">範例適用於 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="86d52-151">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="86d52-152">這個.NET Core Docker 範例會示範的最佳作法模式[建置.NET Core 應用程式的實際執行的 Docker 映像。](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="86d52-152">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="86d52-153">範例適用於 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="86d52-153">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="86d52-154">這[.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained)示範建立 Docker 映像的最佳作法模式[各自獨立的.NET Core 應用程式](https://docs.microsoft.com/dotnet/core/deploying/)。</span><span class="sxs-lookup"><span data-stu-id="86d52-154">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](https://docs.microsoft.com/dotnet/core/deploying/).</span></span> <span data-ttu-id="86d52-155">用於沒有獲益最小的生產容器[共用容器之間的基本映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)。</span><span class="sxs-lookup"><span data-stu-id="86d52-155">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="86d52-156">不過，較低的 Docker 層無法共用。</span><span class="sxs-lookup"><span data-stu-id="86d52-156">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="86d52-157">ARM32 覆盆子 Pi /</span><span class="sxs-lookup"><span data-stu-id="86d52-157">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="86d52-158">.NET 核心執行階段 ARM32 組建通知</span><span class="sxs-lookup"><span data-stu-id="86d52-158">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="86d52-159">ARM32 / 覆盆子 Pi.NET Core 映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-159">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="86d52-160">ARM32 / 木莓澆 Pi.NET Core Docker GitHub 上的範例</span><span class="sxs-lookup"><span data-stu-id="86d52-160">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="86d52-161">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="86d52-161">.NET Framework</span></span>

* <span data-ttu-id="86d52-162">[.NET framework 映像上 DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/)這個儲存機制包含範例會示範各種不同的.NET Framework Docker 設定。</span><span class="sxs-lookup"><span data-stu-id="86d52-162">[.NET Framework images on DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/) This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="86d52-163">您可以使用這些映像為基礎的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="86d52-163">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="86d52-164">**.NET framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="86d52-164">**.NET Framework 4.7**</span></span>

<span data-ttu-id="86d52-165">[ [Dotnet-架構： 4.7 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7)示範基本"hello world"的使用方式[.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47)。</span><span class="sxs-lookup"><span data-stu-id="86d52-165">[The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47).</span></span> <span data-ttu-id="86d52-166">它會示範如何建置和部署應用程式依賴[.NET Framework 4.7 docker 映像](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile)。</span><span class="sxs-lookup"><span data-stu-id="86d52-166">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span></span>

<span data-ttu-id="86d52-167">**.NET framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="86d52-167">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="86d52-168">[Dotnet-架構： 4.6.2 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2)示範基本"hello world"的使用方式[.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462)。</span><span class="sxs-lookup"><span data-stu-id="86d52-168">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462).</span></span> <span data-ttu-id="86d52-169">它會示範如何建置和部署應用程式依賴[.NET Framework 4.6.2 docker 映像](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2)。</span><span class="sxs-lookup"><span data-stu-id="86d52-169">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span></span>

<span data-ttu-id="86d52-170">**.NET framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="86d52-170">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="86d52-171">[Dotnet-framework: 3.5 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5)示範基本"hello world"的使用方式[.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5)。</span><span class="sxs-lookup"><span data-stu-id="86d52-171">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span></span> <span data-ttu-id="86d52-172">它會顯示如何建置和部署上的 Docker 的.NET Framework 3.5 的專案。</span><span class="sxs-lookup"><span data-stu-id="86d52-172">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="86d52-173">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="86d52-173">ASP.NET Core</span></span>

* <span data-ttu-id="86d52-174">[此範例中 ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)示範建置 Docker images，適用於 ASP.NET Core 實際執行的應用程式的最佳作法模式。</span><span class="sxs-lookup"><span data-stu-id="86d52-174">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="86d52-175">範例適用於 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="86d52-175">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="86d52-176">ASP.NET Core 映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-176">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="86d52-177">GitHub 上的 ASP.NET Core 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-177">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="86d52-178">ASP.NET 架構</span><span class="sxs-lookup"><span data-stu-id="86d52-178">ASP.NET Framework</span></span> 

* [<span data-ttu-id="86d52-179">ASP.NET Framework DockerHub 上的映像</span><span class="sxs-lookup"><span data-stu-id="86d52-179">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="86d52-180">在.NET Framework 4.6.2 範例 ASP.NET Web Form 應用程式</span><span class="sxs-lookup"><span data-stu-id="86d52-180">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="86d52-181">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="86d52-181">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="86d52-182">Windows Communication Framework (WCF) 映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-182">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="86d52-183">GitHub 上的 Windows Communication Framework (WCF) 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-183">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

* [<span data-ttu-id="86d52-184">使用.NET Full Framework 4.6.2 Windows Communication Framework (WCF) Docker 範例</span><span class="sxs-lookup"><span data-stu-id="86d52-184">Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="86d52-185">Internet Information Server (IIS)</span><span class="sxs-lookup"><span data-stu-id="86d52-185">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="86d52-186">Internet Information Server (IIS) 上 DockerHub 的映像</span><span class="sxs-lookup"><span data-stu-id="86d52-186">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="86d52-187">GitHub 上的 Internet Information Server (IIS) 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-187">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="86d52-188">與其他 Microsoft 堆疊容器映像互動</span><span class="sxs-lookup"><span data-stu-id="86d52-188">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="86d52-189">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="86d52-189">Microsoft SQL Server</span></span>

* [<span data-ttu-id="86d52-190">執行 Microsoft SQL Server Linux 2017 容器映像使用 Docker 快速入門</span><span class="sxs-lookup"><span data-stu-id="86d52-190">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="86d52-191">Microsoft SQL Server 上 DockerHub Linux 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-191">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="86d52-192">Microsoft SQL Server 的 Windows 容器映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-192">Microsoft SQL Server for Windows Containers images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="86d52-193">Microsoft SQL Server Express Edition DockerHub 上的 Windows 容器映像</span><span class="sxs-lookup"><span data-stu-id="86d52-193">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="86d52-194">Microsoft SQL Server Developer Edition DockerHub 上的 Windows 容器映像</span><span class="sxs-lookup"><span data-stu-id="86d52-194">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="86d52-195">Visual Studio Team Services (VSTS) 代理程式</span><span class="sxs-lookup"><span data-stu-id="86d52-195">Visual Studio Team Services (VSTS) agent</span></span>

* [<span data-ttu-id="86d52-196">Visual Studio Team Services (VSTS) 代理程式映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-196">Visual Studio Team Services (VSTS) agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="86d52-197">GitHub 上的 visual Studio Team Services (VSTS) 代理程式映像</span><span class="sxs-lookup"><span data-stu-id="86d52-197">Visual Studio Team Services (VSTS) agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="86d52-198">Operations Management Suite (OMS) Linux 代理程式</span><span class="sxs-lookup"><span data-stu-id="86d52-198">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="86d52-199">Operations Management Suite (OMS) Linux 代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="86d52-199">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [<span data-ttu-id="86d52-200">Operations Management Suite (OMS) 的映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-200">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/) 

* [<span data-ttu-id="86d52-201">GitHub 上的 operations Management Suite (OMS) 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-201">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="86d52-202">Microsoft Azure 命令列介面 (CLI)</span><span class="sxs-lookup"><span data-stu-id="86d52-202">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="86d52-203">Microsoft Azure 命令列介面 (CLI) 映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-203">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](Docker image for Microsoft Azure Command Line Interface) 

* [<span data-ttu-id="86d52-204">GitHub 上的 Microsoft Azure 命令列介面 (CLI) 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-204">Microsoft Azure Command Line Interface (CLI) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

> [!Note]
> <span data-ttu-id="86d52-205">如果您沒有 Azure 訂用帳戶，[立即註冊](https://azure.microsoft.com/free/?b=16.48)免費 30 天的帳戶和 Azure 信用額度試用 Azure 服務的任何組合中的 get 美金 200。</span><span class="sxs-lookup"><span data-stu-id="86d52-205">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="86d52-206">Microsoft Azure Cosmos DB 模擬器 （Windows 容器）</span><span class="sxs-lookup"><span data-stu-id="86d52-206">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="86d52-207">Microsoft Azure Cosmos DB 模擬器映像上 DockerHub</span><span class="sxs-lookup"><span data-stu-id="86d52-207">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="86d52-208">使用 Azure Cosmos DB 模擬器進行本機開發和測試</span><span class="sxs-lookup"><span data-stu-id="86d52-208">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](https://docs.microsoft.com/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="86d52-209">瀏覽豐富的 Docker 開發生態系統</span><span class="sxs-lookup"><span data-stu-id="86d52-209">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="86d52-210">現在您已經學會關於 Docker 平台和不同的 Docker 映像下, 一個步驟就是瀏覽豐富的 Docker 生態系統。</span><span class="sxs-lookup"><span data-stu-id="86d52-210">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="86d52-211">下列連結會顯示您的 Microsoft 工具做容器開發的補充。</span><span class="sxs-lookup"><span data-stu-id="86d52-211">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="86d52-212">同時使用.NET 和 Docker</span><span class="sxs-lookup"><span data-stu-id="86d52-212">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) 
* [<span data-ttu-id="86d52-213">設計和開發多容器和微服務為基礎的.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="86d52-213">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../standard/microservices-architecture/multi-container-microservice-net-applications)
* [<span data-ttu-id="86d52-214">Visual Studio 程式碼的 Docker 擴充功能</span><span class="sxs-lookup"><span data-stu-id="86d52-214">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile) 
* [<span data-ttu-id="86d52-215">了解如何使用 Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="86d52-215">Learn how to use Azure Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/) 
* [<span data-ttu-id="86d52-216">取得 Service Fabric 啟動範例</span><span class="sxs-lookup"><span data-stu-id="86d52-216">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="86d52-217">Windows 容器的優點</span><span class="sxs-lookup"><span data-stu-id="86d52-217">Benefits of Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/about/index#video-overview)
* [<span data-ttu-id="86d52-218">使用 Visual Studio Docker 工具</span><span class="sxs-lookup"><span data-stu-id="86d52-218">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="86d52-219">將從 Azure 容器登錄至 Azure 容器執行個體的 Docker 映像部署</span><span class="sxs-lookup"><span data-stu-id="86d52-219">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="86d52-220">使用 Visual Studio 程式碼進行偵錯</span><span class="sxs-lookup"><span data-stu-id="86d52-220">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="86d52-221">未授權者手上取得使用 Visual Studio for Mac、 容器和無伺服器的程式碼在雲端中</span><span class="sxs-lookup"><span data-stu-id="86d52-221">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="86d52-222">開始使用 Docker 和 Visual Studio for Mac 實驗室</span><span class="sxs-lookup"><span data-stu-id="86d52-222">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="86d52-223">後續步驟</span><span class="sxs-lookup"><span data-stu-id="86d52-223">Next Steps</span></span>

* [<span data-ttu-id="86d52-224">了解 Docker 與.NET Core 的基本概念</span><span class="sxs-lookup"><span data-stu-id="86d52-224">Learn Docker Basics with .NET Core</span></span>](../docker/docker-basics-dotnet-core.md)
* [<span data-ttu-id="86d52-225">建置.NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="86d52-225">Building .NET Core Docker Images</span></span>](../docker/building-net-docker-images)