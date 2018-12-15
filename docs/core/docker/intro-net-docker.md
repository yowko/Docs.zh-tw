---
title: Docker 簡介 - .NET Core
description: 本文在 .NET Core 應用程式內容中提供了 Docker 的簡介及概觀。
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.custom: mvc, seodec18
ms.openlocfilehash: 1655d4652c4e9b48c48a2a22c2a1bf6cdd459088
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148863"
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="62cd9-103">.NET 和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="62cd9-103">Introduction to .NET and Docker</span></span>

<span data-ttu-id="62cd9-104">本文提供在 Docker 上使用 .NET 的簡介和概念背景。</span><span class="sxs-lookup"><span data-stu-id="62cd9-104">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span>

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="62cd9-105">Docker：封裝您的應用程式以在任何位置部署及執行</span><span class="sxs-lookup"><span data-stu-id="62cd9-105">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="62cd9-106">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) 是一個開放的平台，可讓開發人員和系統管理員在稱為[容器](https://www.docker.com/what-container) \(英文\) 的鬆散隔離環境中，建立[映像](https://docs.docker.com/glossary/?term=image) \(英文\)、遞送及執行分散式應用程式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-106">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="62cd9-107">此作法能在開發、QA 和生產環境之間，實現有效率的應用程式生命週期管理。</span><span class="sxs-lookup"><span data-stu-id="62cd9-107">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="62cd9-108">[Docker 平台](https://docs.docker.com/engine/docker-overview/#the-docker-platform) \(英文\) 使用 [Docker 引擎](https://docs.docker.com/engine/docker-overview/#docker-engine) \(英文\) 來將應用程式快速建置及封裝為 [Docker 映像](https://docs.docker.com/glossary/?term=image) \(英文\)，映像是使用以 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) \(英文\) 格式撰寫的檔案來建立，並於後續會將它部署到[分層式容器](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers) \(英文\) 並在其中執行。</span><span class="sxs-lookup"><span data-stu-id="62cd9-108">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="62cd9-109">您可以建立自己的[分層式映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) \(英文\) 作為 Dockerfile，或使用來自 [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub) \(英文\) 等[登錄](https://docs.docker.com/glossary/?term=registry) \(英文\) 的現有分層式映像。</span><span class="sxs-lookup"><span data-stu-id="62cd9-109">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="62cd9-110">在[進行容器化應用程式或微服務的架構設計及建置](../../standard/microservices-architecture/architect-microservice-container-applications/index.md)時，[Docker 容器、映像和登錄之間的關係](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md)是相當重要的概念。</span><span class="sxs-lookup"><span data-stu-id="62cd9-110">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="62cd9-111">此作法能大幅縮短開發和部署之間的時間。</span><span class="sxs-lookup"><span data-stu-id="62cd9-111">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="62cd9-112">延伸閱讀 (及觀賞)</span><span class="sxs-lookup"><span data-stu-id="62cd9-112">Further reading (and watching)</span></span>

* <span data-ttu-id="62cd9-113">[Windows 型容器：具企業級控制的新式應用程式開發。](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-113">[Windows-based containers: Modern app development with enterprise-grade control.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)</span></span>
* <span data-ttu-id="62cd9-114">[Docker 概觀](https://docs.docker.com/engine/docker-overview/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-114">[Docker overview](https://docs.docker.com/engine/docker-overview/)</span></span>
* [<span data-ttu-id="62cd9-115">Windows 容器上的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="62cd9-115">Dockerfile on Windows Containers</span></span>](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* <span data-ttu-id="62cd9-116">[撰寫 Dockerfile 的最佳做法](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-116">[Best practices for writing Dockerfiles](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)</span></span>
* [<span data-ttu-id="62cd9-117">建置 .NET Core 應用程式的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="62cd9-117">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="62cd9-118">取得 .NET Docker 映像</span><span class="sxs-lookup"><span data-stu-id="62cd9-118">Getting .NET Docker images</span></span>

<span data-ttu-id="62cd9-119">官方 .NET Docker 映像是由 Microsoft 所建立及最佳化。</span><span class="sxs-lookup"><span data-stu-id="62cd9-119">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="62cd9-120">它們在 Docker Hub 上的 Microsoft 存放庫中公開提供。</span><span class="sxs-lookup"><span data-stu-id="62cd9-120">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="62cd9-121">視 .NET 版本和 OS 版本而定，每個存放庫可能會包含多個映像。</span><span class="sxs-lookup"><span data-stu-id="62cd9-121">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="62cd9-122">大部分的映像存放庫提供大量的標籤，來協助您選取特定的架構版本和 OS (Linux 發行版本或 Windows 版本)。</span><span class="sxs-lookup"><span data-stu-id="62cd9-122">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="62cd9-123">以案例為基礎的指引</span><span class="sxs-lookup"><span data-stu-id="62cd9-123">Scenario based guidance</span></span>

<span data-ttu-id="62cd9-124">Microsoft 針對 .NET 存放庫的目的，是要提供細微且專注的存放庫，以代表特定的案例或工作負載。</span><span class="sxs-lookup"><span data-stu-id="62cd9-124">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="62cd9-125">`microsoft/aspnetcore` 映像已針對 Docker 上的 ASP.NET Core 應用程式進行最佳化，使容器可以更快速地啟動。</span><span class="sxs-lookup"><span data-stu-id="62cd9-125">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="62cd9-126">.NET Core 映像 (`microsoft/dotnet`) 則適用於以 .NET Core 為基礎的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-126">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="62cd9-127">例如，批次處理、Azure WebJobs 及其他主控台案例，都應使用最佳化的 .NET Core 映像。</span><span class="sxs-lookup"><span data-stu-id="62cd9-127">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="62cd9-128">最明顯的 Docker 和 .NET 應用程式水平使用案例，是將它們用於生產部署和裝載。</span><span class="sxs-lookup"><span data-stu-id="62cd9-128">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="62cd9-129">結果顯示生產只是單一案例，而其他案例也同樣有用。</span><span class="sxs-lookup"><span data-stu-id="62cd9-129">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="62cd9-130">這些案例並非 .NET 特定，但應該適用於大部分的開發人員平台。</span><span class="sxs-lookup"><span data-stu-id="62cd9-130">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="62cd9-131">**低負擔安裝**：不須在本機安裝就能試用 .NET。</span><span class="sxs-lookup"><span data-stu-id="62cd9-131">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="62cd9-132">只要下載具有 .NET 的 Docker 映像即可。</span><span class="sxs-lookup"><span data-stu-id="62cd9-132">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="62cd9-133">**在容器中開發**：您可以在一致的環境中開發，來使開發環境與生產環境相似 (避免開發人員電腦上的全域狀態等問題)。</span><span class="sxs-lookup"><span data-stu-id="62cd9-133">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="62cd9-134">Visual Studio Tools for Docker 甚至可讓您直接從 Visual Studio 啟動容器。</span><span class="sxs-lookup"><span data-stu-id="62cd9-134">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="62cd9-135">**在容器中測試**：您可以在容器中測試，以減少因環境設定不正確，或是因上一個測試所遺留的變更所造成的失敗。</span><span class="sxs-lookup"><span data-stu-id="62cd9-135">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="62cd9-136">**在容器中建置**：您可以在容器中建置程式碼，以免除針對多個環境正確設定共用組建電腦的必要性，並改為採用 "BYOC" (自備容器) 的作法。</span><span class="sxs-lookup"><span data-stu-id="62cd9-136">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="62cd9-137">**在所有環境中部署**：您可以透過所有環境部署映像。</span><span class="sxs-lookup"><span data-stu-id="62cd9-137">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="62cd9-138">此作法可減少因設定差異所造成的失敗，通常是因外部設定而變更映像行為 (例如插入環境變數)。</span><span class="sxs-lookup"><span data-stu-id="62cd9-138">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="62cd9-139">可協助針對 Docker 容器開發在 .NET Core 和 .NET Framework 之間進行決定的[一般指引](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="62cd9-139">[General guidance](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="62cd9-140">常見的 Docker 開發案例</span><span class="sxs-lookup"><span data-stu-id="62cd9-140">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="62cd9-141">.NET Core</span><span class="sxs-lookup"><span data-stu-id="62cd9-141">.NET Core</span></span>

<span data-ttu-id="62cd9-142">**.NET Core 資源**</span><span class="sxs-lookup"><span data-stu-id="62cd9-142">**.NET Core resources**</span></span>

 <span data-ttu-id="62cd9-143">挑選符合感興趣之案例的 .NET Core 範例。</span><span class="sxs-lookup"><span data-stu-id="62cd9-143">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="62cd9-144">所有範例指示都會描述如何從 Windows、Linux 或 macOS 主機將 Windows 或 Linux Docker 映像設為目標。</span><span class="sxs-lookup"><span data-stu-id="62cd9-144">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="62cd9-145">範例使用 .NET Core 2.0。</span><span class="sxs-lookup"><span data-stu-id="62cd9-145">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="62cd9-146">它們會在適當之處使用 Docker [多階段建置](https://github.com/dotnet/announcements/issues/18) \(英文\) 和[多架構標籤](https://github.com/dotnet/announcements/issues/14) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="62cd9-146">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* <span data-ttu-id="62cd9-147">[Docker Hub 上的 .NET Core 映像](https://hub.docker.com/r/microsoft/dotnet/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-147">[.NET Core images on DockerHub](https://hub.docker.com/r/microsoft/dotnet/)</span></span>

* <span data-ttu-id="62cd9-148">[將 .NET Core 應用程式 Docker 化](https://docs.docker.com/engine/examples/dotnetcore/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-148">[Dockerize a .NET Core application](https://docs.docker.com/engine/examples/dotnetcore/)</span></span>

* <span data-ttu-id="62cd9-149">此 .NET Core Docker 範例示範如何[在您的 .NET Core 開發程序中使用 Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="62cd9-149">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="62cd9-150">該範例可與 Linux 或 Windows 容器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="62cd9-150">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="62cd9-151">此 .NET Core Docker 範例示範[建置適用於生產之 .NET Core 應用程式的 Docker 映像](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) \(英文\) 的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-151">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="62cd9-152">該範例可與 Linux 或 Windows 容器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="62cd9-152">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="62cd9-153">此 [.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) \(英文\) 示範建置[獨立 .NET Core 應用程式](../deploying/index.md)的 Docker 映像的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-153">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](../deploying/index.md).</span></span> <span data-ttu-id="62cd9-154">用於最小的生產容器，而沒有因[在容器之間共用基礎映像](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/) \(英文\) 所產生的優點。</span><span class="sxs-lookup"><span data-stu-id="62cd9-154">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="62cd9-155">不過，可共用較底層的 Docker 層。</span><span class="sxs-lookup"><span data-stu-id="62cd9-155">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="62cd9-156">ARM32 / Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="62cd9-156">ARM32 / Raspberry Pi</span></span>

* <span data-ttu-id="62cd9-157">[.NET Core 執行階段 ARM32 組建宣告](https://github.com/dotnet/announcements/issues/29) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-157">[.NET Core Runtime ARM32 builds announcement](https://github.com/dotnet/announcements/issues/29)</span></span>

* <span data-ttu-id="62cd9-158">[Docker Hub 上的 ARM32 / Raspberry Pi .NET Core 映像](https://hub.docker.com/r/microsoft/dotnet/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-158">[ARM32 / Raspberry Pi .NET Core images on DockerHub](https://hub.docker.com/r/microsoft/dotnet/)</span></span>

* <span data-ttu-id="62cd9-159">[GitHub 上的 ARM32 / Raspberry Pi .NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-159">[ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)</span></span>

#### <a name="net-framework"></a><span data-ttu-id="62cd9-160">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="62cd9-160">.NET Framework</span></span>

* <span data-ttu-id="62cd9-161">[Docker Hub 上的 .NET Framework 映像](https://hub.docker.com/r/microsoft/dotnet-framework/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-161">[.NET Framework images on DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/)</span></span>

<span data-ttu-id="62cd9-162">此存放庫包含示範各種 .NET Framework Docker 設定的範例。</span><span class="sxs-lookup"><span data-stu-id="62cd9-162">This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="62cd9-163">您可以使用這些映像作為自己 Docker 映像的基礎。</span><span class="sxs-lookup"><span data-stu-id="62cd9-163">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="62cd9-164">**.NET Framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="62cd9-164">**.NET Framework 4.7**</span></span>

<span data-ttu-id="62cd9-165">[dotnet-framework:4.7 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) 示範 [.NET Framework 4.7](../../framework/whats-new/index.md#v47) 的基本 "Hello World" 使用方式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-165">The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span></span> <span data-ttu-id="62cd9-166">它示範如何仰賴 [.NET Framework 4.7 Docker 映像](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile) \(英文\) 建置及部署該應用程式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-166">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).</span></span>

<span data-ttu-id="62cd9-167">**.NET Framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="62cd9-167">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="62cd9-168">[dotnet-framework:4.6.2 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) \(英文\) 示範 [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462) 的基本 "Hello World" 使用方式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-168">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span></span> <span data-ttu-id="62cd9-169">它示範如何仰賴 [.NET Framework 4.6.2 Docker 映像](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile) \(英文\) 建置及部署該應用程式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-169">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).</span></span>

<span data-ttu-id="62cd9-170">**.NET Framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="62cd9-170">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="62cd9-171">[dotnet-framework:3.5 範例](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) \(英文\) 示範 [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile) \(英文\) 的基本 "Hello World" 使用方式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-171">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile).</span></span> <span data-ttu-id="62cd9-172">它示範如何仰賴 Docker 中的 .NET Framework 3.5 建置及部署專案。</span><span class="sxs-lookup"><span data-stu-id="62cd9-172">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="62cd9-173">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="62cd9-173">ASP.NET Core</span></span>

* <span data-ttu-id="62cd9-174">[此 ASP.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) \(英文\) 示範建置適用於生產之 ASP.NET Core 應用程式的 Docker 映像的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-174">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="62cd9-175">該範例可與 Linux 或 Windows 容器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="62cd9-175">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="62cd9-176">[Docker Hub 上的 ASP.NET Core 映像](https://hub.docker.com/r/microsoft/aspnetcore-build/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-176">[ASP.NET Core images on DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)</span></span>

* <span data-ttu-id="62cd9-177">[GitHub 上的 ASP.NET Core 映像](https://github.com/aspnet/aspnet-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-177">[ASP.NET Core images on GitHub](https://github.com/aspnet/aspnet-docker)</span></span>

#### <a name="aspnet-framework"></a><span data-ttu-id="62cd9-178">ASP.NET Framework</span><span class="sxs-lookup"><span data-stu-id="62cd9-178">ASP.NET Framework</span></span>

* <span data-ttu-id="62cd9-179">[Docker Hub 上的 ASP.NET Framework 映像](https://hub.docker.com/r/microsoft/aspnet/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-179">[ASP.NET Framework images on DockerHub](https://hub.docker.com/r/microsoft/aspnet/)</span></span>

* <span data-ttu-id="62cd9-180">[.NET Framework 4.6.2 範例上的 ASP.NET Web Form 應用程式](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-180">[ASP.NET Web Forms app on .NET Framework 4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)</span></span>

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="62cd9-181">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="62cd9-181">Windows Communication Framework (WCF)</span></span>

* <span data-ttu-id="62cd9-182">[Docker Hub 上的 Windows Communication Framework (WCF) 映像](https://hub.docker.com/r/microsoft/wcf/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-182">[Windows Communication Framework (WCF) images on DockerHub](https://hub.docker.com/r/microsoft/wcf/)</span></span>

* <span data-ttu-id="62cd9-183">[GitHub 上的 Windows Communication Framework (WCF) 映像](https://github.com/microsoft/wcf-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-183">[Windows Communication Framework (WCF) images on GitHub](https://github.com/microsoft/wcf-docker)</span></span>

* [<span data-ttu-id="62cd9-184">使用 .NET Framework 4.6.2 的 Windows Communication Framework (WCF) Docker 範例</span><span class="sxs-lookup"><span data-stu-id="62cd9-184">Windows Communication Framework (WCF) Docker samples using .NET Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="62cd9-185">Internet Information Server (IIS)</span><span class="sxs-lookup"><span data-stu-id="62cd9-185">Internet Information Server (IIS)</span></span>

* <span data-ttu-id="62cd9-186">[Docker Hub 上的 Internet Information Server (IIS) 映像](https://hub.docker.com/r/microsoft/iis/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-186">[Internet Information Server (IIS) images on DockerHub](https://hub.docker.com/r/microsoft/iis/)</span></span>

* <span data-ttu-id="62cd9-187">[GitHub 上的 Internet Information Server (IIS) 映像](https://github.com/microsoft/iis-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-187">[Internet Information Server (IIS) images on GitHub](https://github.com/microsoft/iis-docker)</span></span>

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="62cd9-188">與其他 Microsoft 堆疊容器映像互動</span><span class="sxs-lookup"><span data-stu-id="62cd9-188">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="62cd9-189">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="62cd9-189">Microsoft SQL Server</span></span>

* <span data-ttu-id="62cd9-190">[透過 Docker 快速入門執行適用於 Linux 的 Microsoft SQL Server 2017 容器映像](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker) \(機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-190">[Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)</span></span>

* <span data-ttu-id="62cd9-191">[Docker Hub 上適用於 Linux 的 Microsoft SQL Server 映像](https://hub.docker.com/r/microsoft/mssql-server-linux/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-191">[Microsoft SQL Server for Linux images on DockerHub](https://hub.docker.com/r/microsoft/mssql-server-linux/)</span></span>

* <span data-ttu-id="62cd9-192">[Docker Hub 上適用於 Windows 容器的 Microsoft SQL Server Express 版本映像](https://hub.docker.com/r/microsoft/mssql-server-windows-express/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-192">[Microsoft SQL Server Express Edition images for Windows Containers on DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)</span></span>

* <span data-ttu-id="62cd9-193">[Docker Hub 上適用於 Windows 容器的 Microsoft SQL Server Developer 版本映像](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-193">[Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)</span></span>

#### <a name="azure-devops-services-agent"></a><span data-ttu-id="62cd9-194">Azure DevOps Services 代理程式</span><span class="sxs-lookup"><span data-stu-id="62cd9-194">Azure DevOps Services agent</span></span>

* [<span data-ttu-id="62cd9-195">DockerHub 上的 Azure DevOps Services 代理程式</span><span class="sxs-lookup"><span data-stu-id="62cd9-195">Azure DevOps Services agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="62cd9-196">GitHub 上的 Azure DevOps Services 代理程式</span><span class="sxs-lookup"><span data-stu-id="62cd9-196">Azure DevOps Services agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="62cd9-197">Operations Management Suite (OMS) Linux 代理程式</span><span class="sxs-lookup"><span data-stu-id="62cd9-197">Operations Management Suite (OMS) Linux agent</span></span>

* <span data-ttu-id="62cd9-198">[Operations Management Suite (OMS) Linux 代理程式概觀](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-198">[Operations Management Suite (OMS) Linux agent overview](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md)</span></span>

* <span data-ttu-id="62cd9-199">[Docker Hub 上的 Operations Management Suite (OMS) 映像](https://hub.docker.com/r/microsoft/oms/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-199">[Operations Management Suite (OMS) images on DockerHub](https://hub.docker.com/r/microsoft/oms/)</span></span>

* <span data-ttu-id="62cd9-200">[GitHub 上的 Operations Management Suite (OMS) 映像](https://github.com/Microsoft/OMS-docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-200">[Operations Management Suite (OMS) images on GitHub](https://github.com/Microsoft/OMS-docker)</span></span>

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="62cd9-201">Microsoft Azure 命令列介面 (CLI)</span><span class="sxs-lookup"><span data-stu-id="62cd9-201">Microsoft Azure Command Line Interface (CLI)</span></span>

* <span data-ttu-id="62cd9-202">[Docker Hub 上的 Microsoft Azure 命令列介面 (CLI) 映像](https://hub.docker.com/r/microsoft/azure-cli/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-202">[Microsoft Azure Command Line Interface (CLI) images on DockerHub](https://hub.docker.com/r/microsoft/azure-cli/)</span></span> 

* <span data-ttu-id="62cd9-203">[GitHub 上的 Microsoft Azure 命令列介面 (CLI) 映像](https://github.com/Azure/azure-cli#Docker) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-203">[Microsoft Azure Command-Line Interface (CLI) images on GitHub](https://github.com/Azure/azure-cli#Docker)</span></span>

> [!NOTE]
> <span data-ttu-id="62cd9-204">如果您沒有 Azure 訂用帳戶，請[立即註冊](https://azure.microsoft.com/free/?b=16.48)可免費使用 30 天的帳戶，並獲得 $200 美元的 Azure 點數來試用其他的 Azure 服務組合。</span><span class="sxs-lookup"><span data-stu-id="62cd9-204">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="62cd9-205">Microsoft Azure Cosmos DB 模擬器 (僅限 Windows 容器)</span><span class="sxs-lookup"><span data-stu-id="62cd9-205">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* <span data-ttu-id="62cd9-206">[Docker Hub 上的 Microsoft Azure Cosmos DB 模擬器映像](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-206">[Microsoft Azure Cosmos DB Emulator images on DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator)</span></span> 

* [<span data-ttu-id="62cd9-207">將 Azure Cosmos DB 模擬器用於本機開發及測試</span><span class="sxs-lookup"><span data-stu-id="62cd9-207">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="62cd9-208">探索豐富的 Docker 開發生態系統</span><span class="sxs-lookup"><span data-stu-id="62cd9-208">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="62cd9-209">在了解 Docker 平台和不同的 Docker 映像之後，您接著可以探索豐富的 Docker 生態系統。</span><span class="sxs-lookup"><span data-stu-id="62cd9-209">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="62cd9-210">以下連結能提供 Microsoft 工具支援容器開發的方式。</span><span class="sxs-lookup"><span data-stu-id="62cd9-210">The following links show you how the Microsoft tools complement container development.</span></span>

* <span data-ttu-id="62cd9-211">[搭配使用 .NET 和 Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-211">[Using .NET and Docker together](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)</span></span>
* [<span data-ttu-id="62cd9-212">設計和開發多容器和微服務 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="62cd9-212">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* <span data-ttu-id="62cd9-213">[Visual Studio Code Docker 擴充功能](https://code.visualstudio.com/docs/languages/dockerfile) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-213">[Visual Studio Code Docker extension](https://code.visualstudio.com/docs/languages/dockerfile)</span></span>
* [<span data-ttu-id="62cd9-214">了解如何使用 Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="62cd9-214">Learn how to use Azure Service Fabric</span></span>](/azure/service-fabric/index)
* <span data-ttu-id="62cd9-215">[Service Fabric 使用者入門範例](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-215">[Service Fabric Getting Started Sample](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)</span></span>
* [<span data-ttu-id="62cd9-216">Windows 容器的優點</span><span class="sxs-lookup"><span data-stu-id="62cd9-216">Benefits of Windows Containers</span></span>](/virtualization/windowscontainers/about/index#video-overview)
* [<span data-ttu-id="62cd9-217">使用 Visual Studio Docker 工具</span><span class="sxs-lookup"><span data-stu-id="62cd9-217">Working with Visual Studio Docker Tools</span></span>](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* <span data-ttu-id="62cd9-218">[將 Docker 映像從 Azure Container Registry 部署到 Azure 容器執行個體](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-218">[Deploying Docker Images from the Azure Container Registry to Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)</span></span>
* <span data-ttu-id="62cd9-219">[使用 Visual Studio Code 進行偵錯](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-219">[Debugging with Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)</span></span>
* <span data-ttu-id="62cd9-220">[開始使用 Visual Studio for Mac、容器，以及雲端中的無伺服器程式碼](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-220">[Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)</span></span>
* <span data-ttu-id="62cd9-221">[開始使用 Docker 和 Visual Studio for Mac 實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="62cd9-221">[Getting Started with Docker and Visual Studio for Mac Lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)</span></span>

## <a name="next-steps"></a><span data-ttu-id="62cd9-222">後續步驟</span><span class="sxs-lookup"><span data-stu-id="62cd9-222">Next steps</span></span>

* [<span data-ttu-id="62cd9-223">了解 .NET Core 的 Docker 基本概念</span><span class="sxs-lookup"><span data-stu-id="62cd9-223">Learn Docker Basics with .NET Core</span></span>](docker-basics-dotnet-core.md)
* [<span data-ttu-id="62cd9-224">建置 .NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="62cd9-224">Building .NET Core Docker Images</span></span>](building-net-docker-images.md)
