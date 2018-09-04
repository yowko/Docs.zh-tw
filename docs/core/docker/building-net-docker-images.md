---
title: 建置 .NET Core Docker 映像
description: 了解 Docker 映像和 .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e48a263334ebb93a5d281032336aeb4073d8467c
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "34827335"
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="2a10c-103">建置 .NET Core 應用程式的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-103">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="2a10c-104">在本教學課程中，著重在如何於 Docker 上使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2a10c-104">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="2a10c-105">首先，我們會探討 Microsoft 所提供及維護的不同 Docker 映像，以及使用案例。</span><span class="sxs-lookup"><span data-stu-id="2a10c-105">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="2a10c-106">我們接著會了解如何建置和 Docker 化 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-106">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="2a10c-107">您會在本教學課程中了解︰</span><span class="sxs-lookup"><span data-stu-id="2a10c-107">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="2a10c-108">了解 Microsoft.NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-108">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="2a10c-109">取得要 Docker 化的 ASP.NET Core 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="2a10c-109">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="2a10c-110">在本機執行 ASP.NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="2a10c-110">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="2a10c-111">使用 Docker for Linux 容器來建置並執行範例</span><span class="sxs-lookup"><span data-stu-id="2a10c-111">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="2a10c-112">使用 Docker for Windows 容器來建置並執行範例</span><span class="sxs-lookup"><span data-stu-id="2a10c-112">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="2a10c-113">Docker 映像最佳化</span><span class="sxs-lookup"><span data-stu-id="2a10c-113">Docker Image Optimizations</span></span>

<span data-ttu-id="2a10c-114">在建置開發人員的 Docker 映像時，我們會著重在三個主要案例︰</span><span class="sxs-lookup"><span data-stu-id="2a10c-114">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="2a10c-115">用來開發 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-115">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="2a10c-116">用來建置 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-116">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="2a10c-117">用來執行 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-117">Images used to run .NET Core apps</span></span>

<span data-ttu-id="2a10c-118">為何是三個映像？</span><span class="sxs-lookup"><span data-stu-id="2a10c-118">Why three images?</span></span>
<span data-ttu-id="2a10c-119">在開發、建置和執行容器化應用程式時，我們有不同的優先考量。</span><span class="sxs-lookup"><span data-stu-id="2a10c-119">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="2a10c-120">**開發︰** 優先順序快速聚焦於逐一查看變更以及偵錯變更的能力。</span><span class="sxs-lookup"><span data-stu-id="2a10c-120">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="2a10c-121">映像大小不那麼重要，而是變更及查看程式碼的速度。</span><span class="sxs-lookup"><span data-stu-id="2a10c-121">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="2a10c-122">**建置：** 此映像包含編譯您應用程式所需的所有項目，其中包含編譯器以及最佳化二進位檔的任何其他相依性。</span><span class="sxs-lookup"><span data-stu-id="2a10c-122">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="2a10c-123">您可以使用組建映像來建立您放入生產映像的資產。</span><span class="sxs-lookup"><span data-stu-id="2a10c-123">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="2a10c-124">組建映像將用於持續整合或組建環境。</span><span class="sxs-lookup"><span data-stu-id="2a10c-124">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="2a10c-125">此方法可讓組建代理程式在組建映像執行個體中編譯和建置應用程式 (含所有必要相依性)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-125">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="2a10c-126">組建代理程式只需要知道如何執行此 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="2a10c-126">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="2a10c-127">**生產︰** 多快可以部署和啟動映像？</span><span class="sxs-lookup"><span data-stu-id="2a10c-127">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="2a10c-128">此映像很小，因此最小化從 Docker 登錄到 Docker 主機的網路效能。</span><span class="sxs-lookup"><span data-stu-id="2a10c-128">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="2a10c-129">準備好執行的內容可用最短的時間完成 Docker 執行到處理結果。</span><span class="sxs-lookup"><span data-stu-id="2a10c-129">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="2a10c-130">在 Docker 模型中，不需要動態程式碼編譯。</span><span class="sxs-lookup"><span data-stu-id="2a10c-130">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="2a10c-131">您放置在此映像中的內容會限於執行應用程式所需的二進位檔和內容。</span><span class="sxs-lookup"><span data-stu-id="2a10c-131">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="2a10c-132">例如，`dotnet publish` 輸出包含：</span><span class="sxs-lookup"><span data-stu-id="2a10c-132">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="2a10c-133">已編譯的二進位檔</span><span class="sxs-lookup"><span data-stu-id="2a10c-133">the compiled binaries</span></span>
    * <span data-ttu-id="2a10c-134">.js 和 .css 檔案</span><span class="sxs-lookup"><span data-stu-id="2a10c-134">.js and .css files</span></span>


<span data-ttu-id="2a10c-135">在生產映像中包含 `dotnet publish` 命令輸出的原因是要將其大小保持最小值。</span><span class="sxs-lookup"><span data-stu-id="2a10c-135">The reason to include the `dotnet publish` command output in your production image is to keep its size to a minimum.</span></span>

<span data-ttu-id="2a10c-136">有些 .NET Core 映像共用不同標記之間的層，因此下載最新標記是相當輕量的程序。</span><span class="sxs-lookup"><span data-stu-id="2a10c-136">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="2a10c-137">如果您的電腦上已經有舊版本，則此架構會減少所需的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="2a10c-137">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="2a10c-138">多個應用程式使用同一部電腦上的通用映像時，通用映像之間會共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="2a10c-138">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="2a10c-139">映像必須相同才能共用。</span><span class="sxs-lookup"><span data-stu-id="2a10c-139">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="2a10c-140">Docker 映像變化</span><span class="sxs-lookup"><span data-stu-id="2a10c-140">Docker image variations</span></span>

<span data-ttu-id="2a10c-141">為達成上述目標，我們在 [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/) 下提供映像變化。</span><span class="sxs-lookup"><span data-stu-id="2a10c-141">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="2a10c-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) 此映像包含具有 .NET Core 和命令列工具 (CLI) 的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="2a10c-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="2a10c-143">此映像會對應至**開發案例**。</span><span class="sxs-lookup"><span data-stu-id="2a10c-143">This image maps to the **development scenario**.</span></span> <span data-ttu-id="2a10c-144">您可以使用此映像進行本機開發、偵錯和單元測試。</span><span class="sxs-lookup"><span data-stu-id="2a10c-144">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="2a10c-145">此映像也可用於**建置**案例。</span><span class="sxs-lookup"><span data-stu-id="2a10c-145">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="2a10c-146">使用 `microsoft/dotnet:sdk` 一律可以提供最新版本。</span><span class="sxs-lookup"><span data-stu-id="2a10c-146">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="2a10c-147">如果您不確定需求，則需要使用 `microsoft/dotnet:<version>-sdk` 映像。</span><span class="sxs-lookup"><span data-stu-id="2a10c-147">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="2a10c-148">作為「既定」映像，其設計是要用作擲離容器 (裝載原始程式碼，並啟動容器來啟動應用程式)，以及用作從中建置其他映像的基底映像。</span><span class="sxs-lookup"><span data-stu-id="2a10c-148">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="2a10c-149">`microsoft/dotnet:<version>-runtime`：此映像包含.NET Core (執行階段和程式庫)，以及最佳化以在**生產**中執行 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-149">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="2a10c-150">替代的映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-150">Alternative images</span></span>

<span data-ttu-id="2a10c-151">除了開發、建置和生產環境的最佳化案例，我們還提供其他映像︰</span><span class="sxs-lookup"><span data-stu-id="2a10c-151">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="2a10c-152">`microsoft/dotnet:<version>-runtime-deps`：**runtime-deps** 映像包含作業系統與 .NET Core 所需的所有原生相依性。</span><span class="sxs-lookup"><span data-stu-id="2a10c-152">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="2a10c-153">此映像適用於[獨立應用程式](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-153">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="2a10c-154">每個變體的最新版本︰</span><span class="sxs-lookup"><span data-stu-id="2a10c-154">Latest versions of each variant:</span></span>

* <span data-ttu-id="2a10c-155">`microsoft/dotnet` 或 `microsoft/dotnet:latest` (SDK 映像的別名)</span><span class="sxs-lookup"><span data-stu-id="2a10c-155">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="2a10c-156">要探索的範例</span><span class="sxs-lookup"><span data-stu-id="2a10c-156">Samples to explore</span></span>

* <span data-ttu-id="2a10c-157">[此 ASP.NET Core Docker 範例](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) \(英文\) 示範建置適用於生產之 ASP.NET Core 應用程式的 Docker 映像的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-157">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="2a10c-158">該範例可與 Linux 或 Windows 容器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="2a10c-158">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="2a10c-159">此 .NET Core Docker 範例示範[建置適用於生產之 .NET Core 應用程式的 Docker 映像](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp) \(英文\) 的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-159">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span></span>

## <a name="forward-the-request-scheme-and-original-ip-address"></a><span data-ttu-id="2a10c-160">轉寄要求配置與原始 IP 位址</span><span class="sxs-lookup"><span data-stu-id="2a10c-160">Forward the request scheme and original IP address</span></span>

<span data-ttu-id="2a10c-161">Proxy 伺服器、負載平衡器及其他網路設備，通常會在要求觸達容器化應用程式之前，遮蔽要求的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="2a10c-161">Proxy servers, load balancers, and other network appliances often obscure information about a request before it reaches the containerized app:</span></span>

* <span data-ttu-id="2a10c-162">透過 HTTP 作為 Proxy 來處理 HTTPS 要求時，原始配置 (HTTPS) 會遺失而必須在標頭中轉送。</span><span class="sxs-lookup"><span data-stu-id="2a10c-162">When HTTPS requests are proxied over HTTP, the original scheme (HTTPS) is lost and must be forwarded in a header.</span></span>
* <span data-ttu-id="2a10c-163">由於應用程式會從 Proxy 而非從網際網路或公司網路上的真實來源，收到要求，因此必須也在標頭中轉寄原始用戶端 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="2a10c-163">Because an app receives a request from the proxy and not its true source on the Internet or corporate network, the original client IP address must also be forwarded in a header.</span></span>

<span data-ttu-id="2a10c-164">此資訊在要求處理方面可能相當重要，例如在重新導向、驗證、連結產生、原則評估及用戶端地理位置方面。</span><span class="sxs-lookup"><span data-stu-id="2a10c-164">This information may be important in request processing, for example in redirects, authentication, link generation, policy evaluation, and client geolocation.</span></span>

<span data-ttu-id="2a10c-165">若要將配置與原始 IP 位址轉寄到容器化的 ASP.NET Core 應用程式，請使用轉寄標頭中介軟體。</span><span class="sxs-lookup"><span data-stu-id="2a10c-165">To forward the scheme and original IP address to a containerized ASP.NET Core app, use Forwarded Headers Middleware.</span></span> <span data-ttu-id="2a10c-166">如需詳細資訊，請參閱[設定 ASP.NET Core 以處理 Proxy 伺服器和負載平衡器](/aspnet/core/host-and-deploy/proxy-load-balancer)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-166">For more information, see [Configure ASP.NET Core to work with proxy servers and load balancers](/aspnet/core/host-and-deploy/proxy-load-balancer).</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="2a10c-167">第一個 ASP.NET Core Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="2a10c-167">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="2a10c-168">在本教學課程中，將 ASP.NET Core Docker 範例應用程式用於要 Docker 化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-168">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="2a10c-169">此 ASP.NET Core Docker 範例應用程式示範建置適用於生產的 ASP.NET Core 應用程式之 Docker 映像的最佳做法模式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-169">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="2a10c-170">該範例可與 Linux 或 Windows 容器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="2a10c-170">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="2a10c-171">範例 Dockerfile 會根據 ASP.NET Core 執行階段 Docker 基底映像來建立 ASP.NET Core 應用程式 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="2a10c-171">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="2a10c-172">它會使用 [Docker 多階段建置功能](https://docs.docker.com/engine/userguide/eng-image/multistage-build/)來：</span><span class="sxs-lookup"><span data-stu-id="2a10c-172">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="2a10c-173">根據**較大的** ASP.NET Core 建置 Docker 基底映像，以在容器中建置範例</span><span class="sxs-lookup"><span data-stu-id="2a10c-173">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="2a10c-174">根據**較小的** ASP.NET Core Docker 執行階段基底映像，以將最終建置結果複製至 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-174">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="2a10c-175">組建映像包含建置應用程式但未建置執行階段映像的必要工具。</span><span class="sxs-lookup"><span data-stu-id="2a10c-175">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2a10c-176">必要條件</span><span class="sxs-lookup"><span data-stu-id="2a10c-176">Prerequisites</span></span>

<span data-ttu-id="2a10c-177">若要建置並執行，請安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="2a10c-177">To build and run, install the following items:</span></span>

#### <a name="net-core-21-sdk"></a><span data-ttu-id="2a10c-178">.NET Core 2.1 SDK</span><span class="sxs-lookup"><span data-stu-id="2a10c-178">.NET Core 2.1 SDK</span></span>

* <span data-ttu-id="2a10c-179">安裝 [.NET Core SDK 2.1](https://www.microsoft.com/net/core) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-179">Install [.NET Core SDK 2.1](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="2a10c-180">如果您還沒有這麼做，請安裝您慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="2a10c-180">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="2a10c-181">需要安裝程式碼編輯器嗎？</span><span class="sxs-lookup"><span data-stu-id="2a10c-181">Need to install a code editor?</span></span> <span data-ttu-id="2a10c-182">試用 [Visual Studio](https://visualstudio.com/downloads)！</span><span class="sxs-lookup"><span data-stu-id="2a10c-182">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="2a10c-183">安裝 Docker 用戶端</span><span class="sxs-lookup"><span data-stu-id="2a10c-183">Installing Docker Client</span></span>

<span data-ttu-id="2a10c-184">安裝 [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) \(英文\) 或更新版本的 Docker 用戶端。</span><span class="sxs-lookup"><span data-stu-id="2a10c-184">Install [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="2a10c-185">Docker 用戶端可以安裝於：</span><span class="sxs-lookup"><span data-stu-id="2a10c-185">The Docker client can be installed in:</span></span>

* <span data-ttu-id="2a10c-186">Linux 散發</span><span class="sxs-lookup"><span data-stu-id="2a10c-186">Linux distributions</span></span>

   * [<span data-ttu-id="2a10c-187">CentOS</span><span class="sxs-lookup"><span data-stu-id="2a10c-187">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="2a10c-188">Debian</span><span class="sxs-lookup"><span data-stu-id="2a10c-188">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="2a10c-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="2a10c-189">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="2a10c-190">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="2a10c-190">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="2a10c-191">macOS</span><span class="sxs-lookup"><span data-stu-id="2a10c-191">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="2a10c-192">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="2a10c-192">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="2a10c-193">安裝適用於範例存放庫的 Git</span><span class="sxs-lookup"><span data-stu-id="2a10c-193">Installing Git for sample repository</span></span>

* <span data-ttu-id="2a10c-194">如果您要複製存放庫，請安裝 [git](https://git-scm.com/download)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-194">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="2a10c-195">取得範例應用程式</span><span class="sxs-lookup"><span data-stu-id="2a10c-195">Getting the sample application</span></span>

<span data-ttu-id="2a10c-196">取得範例的最簡單方式是使用下列指示透過 Git 複製 [.NET Core Docker 存放庫](https://github.com/dotnet/dotnet-docker) \(英文\)：</span><span class="sxs-lookup"><span data-stu-id="2a10c-196">The easiest way to get the sample is by cloning the [.NET Core Docker repository](https://github.com/dotnet/dotnet-docker) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker
```

<span data-ttu-id="2a10c-197">您也可以從 .NET Core Docker 存放庫中將存放庫下載為 zip (它很小)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-197">You can also download the repository (it is small) as a zip from the .NET Core Docker repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="2a10c-198">在本機執行 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="2a10c-198">Run the ASP.NET app locally</span></span>

<span data-ttu-id="2a10c-199">針對參考點，在將應用程式放入容器前，要先在本機執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-199">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="2a10c-200">您可以搭配 .NET Core 2.1 SDK 使用下列命令，以在本機建置並執行應用程式 (這些指示會假設存放庫的根目錄)：</span><span class="sxs-lookup"><span data-stu-id="2a10c-200">You can build and run the application locally with the .NET Core 2.1 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

<span data-ttu-id="2a10c-201">應用程式啟動之後，請在網頁瀏覽器中瀏覽 **http://localhost:5000**。</span><span class="sxs-lookup"><span data-stu-id="2a10c-201">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="2a10c-202">使用 Docker for Linux 容器來建置並執行範例</span><span class="sxs-lookup"><span data-stu-id="2a10c-202">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="2a10c-203">您可以使用 Linux 容器並使用下列命令，以在 Docker 中建置和執行範例 (這些指示假設存放庫的根目錄)：</span><span class="sxs-lookup"><span data-stu-id="2a10c-203">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="2a10c-204">`docker run` '-p' 引數會將您本機電腦上的連接埠 5000 對應至容器中的連接埠 80 (連接埠對應形式為 `host:container`)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-204">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="2a10c-205">如需詳細資訊，請參閱命令列參數的 [docker run reference](https://docs.docker.com/engine/reference/commandline/exec/)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-205">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="2a10c-206">應用程式啟動之後，請在網頁瀏覽器中瀏覽 **http://localhost:5000**。</span><span class="sxs-lookup"><span data-stu-id="2a10c-206">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="2a10c-207">使用 Docker for Windows 容器來建置並執行範例</span><span class="sxs-lookup"><span data-stu-id="2a10c-207">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="2a10c-208">您可以使用 Windows 容器並使用下列命令，以在 Docker 中建置和執行範例 (這些示假設存放庫的根目錄)：</span><span class="sxs-lookup"><span data-stu-id="2a10c-208">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="2a10c-209">使用 Windows 容器時，您必須在瀏覽器中直接巡覽至**容器 IP 位址** (相對於 http://localhost) )。</span><span class="sxs-lookup"><span data-stu-id="2a10c-209">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="2a10c-210">您可以使用下列步驟來取得容器的 IP 位址：</span><span class="sxs-lookup"><span data-stu-id="2a10c-210">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="2a10c-211">開啟另一個命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2a10c-211">Open up another command prompt.</span></span>
* <span data-ttu-id="2a10c-212">執行 `docker ps` 以查看您的執行中容器。</span><span class="sxs-lookup"><span data-stu-id="2a10c-212">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="2a10c-213">其中應該會有 "aspnetcore_sample" 容器。</span><span class="sxs-lookup"><span data-stu-id="2a10c-213">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="2a10c-214">執行 `docker exec aspnetcore_sample ipconfig`。</span><span class="sxs-lookup"><span data-stu-id="2a10c-214">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="2a10c-215">複製容器 IP 位址，並將其貼入瀏覽器 (例如，172.29.245.43)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-215">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="2a10c-216">Docker exec 支援使用名稱或雜湊來識別容器。</span><span class="sxs-lookup"><span data-stu-id="2a10c-216">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="2a10c-217">在我們的範例中，使用名稱 (aspnetcore_sample)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-217">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="2a10c-218">請參閱下列有關如何取得執行中 Windows 容器的 IP 位址的範例。</span><span class="sxs-lookup"><span data-stu-id="2a10c-218">See the following example of how to get the IP address of a running Windows container.</span></span>

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!NOTE]
> <span data-ttu-id="2a10c-219">Docker exec 會在執行中容器內執行新的命令。</span><span class="sxs-lookup"><span data-stu-id="2a10c-219">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="2a10c-220">如需詳細資訊，請參閱命令列參數的 [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-220">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="2a10c-221">您可以使用 [dotnet publish](../tools/dotnet-publish.md) 命令，以在本機產生準備好部署至生產環境的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-221">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> <span data-ttu-id="2a10c-222">-c Release 引數會以發行模式建置應用程式 (預設值是偵錯模式)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-222">The -c Release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="2a10c-223">如需詳細資訊，請參閱命令列參數的 [dotnet run reference](../tools/dotnet-run.md)。</span><span class="sxs-lookup"><span data-stu-id="2a10c-223">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="2a10c-224">您可以使用下列命令，在 **Windows** 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-224">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="2a10c-225">您可以使用下列命令，在 **Linux** 或 **macOS** 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a10c-225">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="2a10c-226">此範例中所使用的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-226">Docker Images used in this sample</span></span>

<span data-ttu-id="2a10c-227">此範例的 dockerfile 使用的是下列 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="2a10c-227">The following Docker images are used in this sample's dockerfile.</span></span>

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

<span data-ttu-id="2a10c-228">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="2a10c-228">Congratulations!</span></span> <span data-ttu-id="2a10c-229">您已：</span><span class="sxs-lookup"><span data-stu-id="2a10c-229">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="2a10c-230">了解 Microsoft .NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="2a10c-230">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="2a10c-231">取得要 Docker 化的 ASP.NET Core 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="2a10c-231">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="2a10c-232">在本機執行 ASP.NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="2a10c-232">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="2a10c-233">使用 Docker for Linux 容器來建置並執行範例</span><span class="sxs-lookup"><span data-stu-id="2a10c-233">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="2a10c-234">使用 Docker for Windows 容器來建置並執行範例</span><span class="sxs-lookup"><span data-stu-id="2a10c-234">Built and ran the sample with Docker for Windows containers</span></span>

<span data-ttu-id="2a10c-235">**後續步驟**</span><span class="sxs-lookup"><span data-stu-id="2a10c-235">**Next Steps**</span></span>

<span data-ttu-id="2a10c-236">以下是一些您可以採取的後續步驟：</span><span class="sxs-lookup"><span data-stu-id="2a10c-236">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="2a10c-237">使用 Visual Studio Docker 工具</span><span class="sxs-lookup"><span data-stu-id="2a10c-237">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* <span data-ttu-id="2a10c-238">[將 Docker 映像從 Azure Container Registry 部署到 Azure 容器執行個體](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="2a10c-238">[Deploying Docker Images from the Azure Container Registry to Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)</span></span>
* <span data-ttu-id="2a10c-239">[使用 Visual Studio Code 進行偵錯](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="2a10c-239">[Debugging with Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)</span></span> 
* <span data-ttu-id="2a10c-240">[開始使用 Visual Studio for Mac、容器，以及雲端中的無伺服器程式碼](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="2a10c-240">[Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)</span></span>
* <span data-ttu-id="2a10c-241">[開始使用 Docker 和 Visual Studio for Mac 實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="2a10c-241">[Getting Started with Docker and Visual Studio for Mac Lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)</span></span>

> [!NOTE]
> <span data-ttu-id="2a10c-242">如果您沒有 Azure 訂用帳戶，請[立即註冊](https://azure.microsoft.com/free/?b=16.48)可免費使用 30 天的帳戶，並獲得 $200 美元的 Azure 點數來試用其他的 Azure 服務組合。</span><span class="sxs-lookup"><span data-stu-id="2a10c-242">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
