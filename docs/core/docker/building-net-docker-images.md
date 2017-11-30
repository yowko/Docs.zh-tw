---
title: "建置 .NET Core Docker 映像"
description: "了解 Docker 映像和 .NET Core"
keywords: ".NET、.NET Core、Docker"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="358dd-104">建置 .NET Core 應用程式的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="358dd-104">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="358dd-105">在本教學課程中，我們會著重在如何使用.NET 核心上 Docker。</span><span class="sxs-lookup"><span data-stu-id="358dd-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="358dd-106">首先，我們會探討不同的 Docker images 提供及維護 Microsoft，並使用案例。</span><span class="sxs-lookup"><span data-stu-id="358dd-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="358dd-107">然後，我們會了解如何建置和 dockerize ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="358dd-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="358dd-108">本教學課程的過程中，您了解：</span><span class="sxs-lookup"><span data-stu-id="358dd-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="358dd-109">深入了解 Microsoft.NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="358dd-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="358dd-110">取得 ASP.NET Core Dockerize 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="358dd-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="358dd-111">在本機上執行 ASP.NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="358dd-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="358dd-112">建置及執行範例，以 Docker 的 Linux 容器</span><span class="sxs-lookup"><span data-stu-id="358dd-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="358dd-113">建置及執行範例，以 Docker for Windows 容器</span><span class="sxs-lookup"><span data-stu-id="358dd-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="358dd-114">Docker 映像最佳化</span><span class="sxs-lookup"><span data-stu-id="358dd-114">Docker Image Optimizations</span></span>

<span data-ttu-id="358dd-115">在建置開發人員的 Docker 映像時，我們會著重在三個主要案例︰</span><span class="sxs-lookup"><span data-stu-id="358dd-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="358dd-116">用來開發 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="358dd-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="358dd-117">用來建置 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="358dd-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="358dd-118">用來執行 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="358dd-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="358dd-119">為何是三個映像？</span><span class="sxs-lookup"><span data-stu-id="358dd-119">Why three images?</span></span>
<span data-ttu-id="358dd-120">當開發、 建置及執行容器化應用程式時，我們會有不同的優先權。</span><span class="sxs-lookup"><span data-stu-id="358dd-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="358dd-121">**開發：**優先順序著重於快速地逐一查看變更，以及偵錯所做的變更的功能。</span><span class="sxs-lookup"><span data-stu-id="358dd-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="358dd-122">映像大小並不重要，而是可以變更您的程式碼並快速看到它們嗎？</span><span class="sxs-lookup"><span data-stu-id="358dd-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="358dd-123">**組建中：**此映像包含編譯您的應用程式，其中包含編譯器及最佳化的二進位檔的任何其他相依性所需的所有項目。</span><span class="sxs-lookup"><span data-stu-id="358dd-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="358dd-124">您可以使用建置映像來建立您放入實際執行映像的資產。</span><span class="sxs-lookup"><span data-stu-id="358dd-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="358dd-125">會用於建置映像，持續整合，或在建置環境。</span><span class="sxs-lookup"><span data-stu-id="358dd-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="358dd-126">這個方法可讓組建代理程式可編譯及建立應用程式 （具有所有必要的相依性） 中建置的映像執行個體。</span><span class="sxs-lookup"><span data-stu-id="358dd-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="358dd-127">組建代理程式只需要知道如何執行此 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="358dd-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="358dd-128">**生產環境：**方式快速部署和啟動您的映像嗎？</span><span class="sxs-lookup"><span data-stu-id="358dd-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="358dd-129">此映像很小，因此從 Docker 登錄您的 Docker 主機的網路效能會最佳化。</span><span class="sxs-lookup"><span data-stu-id="358dd-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="358dd-130">準備好執行的內容可用最短的時間完成 Docker 執行到處理結果。</span><span class="sxs-lookup"><span data-stu-id="358dd-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="358dd-131">Docker 模型中，不需要動態程式碼編譯。</span><span class="sxs-lookup"><span data-stu-id="358dd-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="358dd-132">您放置在此映像中的內容會限於執行應用程式所需的二進位檔和內容。</span><span class="sxs-lookup"><span data-stu-id="358dd-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="358dd-133">例如，`dotnet publish`輸出包含：</span><span class="sxs-lookup"><span data-stu-id="358dd-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="358dd-134">已編譯的二進位檔</span><span class="sxs-lookup"><span data-stu-id="358dd-134">the compiled binaries</span></span>
    * <span data-ttu-id="358dd-135">.js 和.css 檔案</span><span class="sxs-lookup"><span data-stu-id="358dd-135">.js and .css files</span></span>


<span data-ttu-id="358dd-136">要包含的原因`dotnet publish`生產映像中的命令輸出都是要保留其 ' 大小為最小值。</span><span class="sxs-lookup"><span data-stu-id="358dd-136">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="358dd-137">某些.NET Core 映像共用層之間不同的標記，以便下載最新的標籤是一個相當輕便的程序。</span><span class="sxs-lookup"><span data-stu-id="358dd-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="358dd-138">如果您已經在電腦上有較舊的版本，此架構會減少所需的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="358dd-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="358dd-139">當多個應用程式使用同一部電腦上的通用映像時，常見的映像之間會共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="358dd-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="358dd-140">影像必須是共用相同。</span><span class="sxs-lookup"><span data-stu-id="358dd-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="358dd-141">Docker 映像變化</span><span class="sxs-lookup"><span data-stu-id="358dd-141">Docker image variations</span></span>

<span data-ttu-id="358dd-142">為了達成上述目標，我們會提供下的映像變異[ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="358dd-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="358dd-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) 這個映像包含.NET Core SDK，其中包含.NET Core 和命令列工具 (CLI)。</span><span class="sxs-lookup"><span data-stu-id="358dd-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="358dd-144">此映像會對應至**開發案例**。</span><span class="sxs-lookup"><span data-stu-id="358dd-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="358dd-145">您可以使用此映像的本機開發、 偵錯和執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="358dd-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="358dd-146">此映像也可用於**建置**案例。</span><span class="sxs-lookup"><span data-stu-id="358dd-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="358dd-147">使用`microsoft/dotnet:sdk`一律提供最新版本。</span><span class="sxs-lookup"><span data-stu-id="358dd-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="358dd-148">您不確定您的需求有關，如果您想要使用`microsoft/dotnet:<version>-sdk`映像。</span><span class="sxs-lookup"><span data-stu-id="358dd-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="358dd-149">做為 「 既定 」 影像，它的設計是要做為擲回離開容器 （裝載您的原始程式碼，啟動容器啟動應用程式），以及做為基礎的映像，以建立從其他映像。</span><span class="sxs-lookup"><span data-stu-id="358dd-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="358dd-150">`microsoft/dotnet:<version>-runtime`： 此映像包含.NET Core （執行階段和程式庫），而且會在執行.NET Core 應用程式的最佳化**生產**。</span><span class="sxs-lookup"><span data-stu-id="358dd-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="358dd-151">替代的映像</span><span class="sxs-lookup"><span data-stu-id="358dd-151">Alternative images</span></span>

<span data-ttu-id="358dd-152">除了開發、建置和生產環境的最佳化案例，我們還提供其他映像︰</span><span class="sxs-lookup"><span data-stu-id="358dd-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="358dd-153">`microsoft/dotnet:<version>-runtime-deps`:**執行階段 deps**映像包含作業系統的所有原生.NET Core 所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="358dd-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="358dd-154">此映像為[各自獨立的應用程式](https://docs.microsoft.com/dotnet/core/deploying/index)。</span><span class="sxs-lookup"><span data-stu-id="358dd-154">This image is for [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index).</span></span>

<span data-ttu-id="358dd-155">每個變體的最新版本︰</span><span class="sxs-lookup"><span data-stu-id="358dd-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="358dd-156">`microsoft/dotnet`或`microsoft/dotnet:latest`（別名 SDK 映像）</span><span class="sxs-lookup"><span data-stu-id="358dd-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="358dd-157">若要瀏覽範例</span><span class="sxs-lookup"><span data-stu-id="358dd-157">Samples to explore</span></span>

* <span data-ttu-id="358dd-158">[此範例中 ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)示範建置 Docker images，適用於 ASP.NET Core 實際執行的應用程式的最佳作法模式。</span><span class="sxs-lookup"><span data-stu-id="358dd-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="358dd-159">範例適用於 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="358dd-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="358dd-160">這個.NET Core Docker 範例會示範的最佳作法模式[建置.NET Core 應用程式的實際執行的 Docker 映像。](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="358dd-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="358dd-161">第一個 ASP.NET Core Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="358dd-161">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="358dd-162">本教學課程，可讓您使用 ASP.NET Core Docker 範例應用程式，我們想要 dockerize 應用程式。</span><span class="sxs-lookup"><span data-stu-id="358dd-162">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="358dd-163">這個 ASP.NET Core Docker 範例應用程式示範如何建置 Docker images，適用於 ASP.NET Core 實際執行的應用程式的最佳作法模式。</span><span class="sxs-lookup"><span data-stu-id="358dd-163">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="358dd-164">範例適用於 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="358dd-164">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="358dd-165">範例 Dockerfile 建立 ASP.NET Core 執行階段 Docker 基底映像所依據的 ASP.NET Core 應用程式 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="358dd-165">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="358dd-166">它會使用[Docker 多階段建置功能](https://docs.docker.com/engine/userguide/eng-image/multistage-build/)至：</span><span class="sxs-lookup"><span data-stu-id="358dd-166">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="358dd-167">建立容器，根據在範例**較大**ASP.NET Core 建置 Docker 基底映像</span><span class="sxs-lookup"><span data-stu-id="358dd-167">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="358dd-168">複製到 Docker 映像為基礎的最後一個組建結果**小**ASP.NET Core Docker 執行階段基底映像</span><span class="sxs-lookup"><span data-stu-id="358dd-168">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!Note]
> <span data-ttu-id="358dd-169">建置映像包含建置應用程式，但不會執行階段映像的必要的工具。</span><span class="sxs-lookup"><span data-stu-id="358dd-169">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="358dd-170">必要條件</span><span class="sxs-lookup"><span data-stu-id="358dd-170">Prerequisites</span></span>

<span data-ttu-id="358dd-171">若要建置並執行，安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="358dd-171">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="358dd-172">.NET 核心 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="358dd-172">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="358dd-173">安裝[.NET Core SDK 2.0](https://www.microsoft.com/net/core)。</span><span class="sxs-lookup"><span data-stu-id="358dd-173">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="358dd-174">如果您還沒有這麼做，請安裝您最愛的程式碼編輯器 中。</span><span class="sxs-lookup"><span data-stu-id="358dd-174">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="358dd-175">需要安裝的程式碼編輯器？</span><span class="sxs-lookup"><span data-stu-id="358dd-175">Need to install a code editor?</span></span> <span data-ttu-id="358dd-176">再試一次[Visual Studio](https://visualstudio.com/downloads)！</span><span class="sxs-lookup"><span data-stu-id="358dd-176">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="358dd-177">安裝 Docker 用戶端</span><span class="sxs-lookup"><span data-stu-id="358dd-177">Installing Docker Client</span></span>

<span data-ttu-id="358dd-178">安裝[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/)或更新版本的 Docker 用戶端。</span><span class="sxs-lookup"><span data-stu-id="358dd-178">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="358dd-179">Docker 用戶端可以安裝在：</span><span class="sxs-lookup"><span data-stu-id="358dd-179">The Docker client can be installed in:</span></span>

* <span data-ttu-id="358dd-180">Linux 散發套件</span><span class="sxs-lookup"><span data-stu-id="358dd-180">Linux distributions</span></span>

   * [<span data-ttu-id="358dd-181">CentOS</span><span class="sxs-lookup"><span data-stu-id="358dd-181">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="358dd-182">Debian</span><span class="sxs-lookup"><span data-stu-id="358dd-182">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="358dd-183">Fedora</span><span class="sxs-lookup"><span data-stu-id="358dd-183">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="358dd-184">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="358dd-184">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="358dd-185">macOS</span><span class="sxs-lookup"><span data-stu-id="358dd-185">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="358dd-186">[Windows](https://docs.docker.com/docker-for-windows/)。</span><span class="sxs-lookup"><span data-stu-id="358dd-186">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="358dd-187">安裝適用於範例儲存機制的 Git</span><span class="sxs-lookup"><span data-stu-id="358dd-187">Installing Git for sample repository</span></span>

* <span data-ttu-id="358dd-188">安裝[git](https://git-scm.com/download)如果您想要複製儲存機制。</span><span class="sxs-lookup"><span data-stu-id="358dd-188">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="358dd-189">取得範例應用程式</span><span class="sxs-lookup"><span data-stu-id="358dd-189">Getting the sample application</span></span>

<span data-ttu-id="358dd-190">取得範例的最簡單方式是藉由複製[範例儲存機制](https://github.com/dotnet/dotnet-docker-samples)使用 git，請使用下列指示：</span><span class="sxs-lookup"><span data-stu-id="358dd-190">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="358dd-191">您也可以下載.NET Core Docker 範例儲存機制從 zip （它是小型的） 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="358dd-191">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="358dd-192">在本機執行的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="358dd-192">Run the ASP.NET app locally</span></span>

<span data-ttu-id="358dd-193">針對參考點，在將應用程式放入容器前，要先在本機執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="358dd-193">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="358dd-194">您可以建置及執行應用程式在本機使用.NET 核心 2.0 SDK 使用下列命令 （的指示會假設儲存機制的根目錄）：</span><span class="sxs-lookup"><span data-stu-id="358dd-194">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="358dd-195">在應用程式啟動之後，請瀏覽**http://localhost:5000/** web 瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="358dd-195">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="358dd-196">建置及執行範例，以 Docker 的 Linux 容器</span><span class="sxs-lookup"><span data-stu-id="358dd-196">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="358dd-197">您可以建置及執行 Docker 使用 Linux 容器，使用下列命令 （的指示會假設儲存機制的根目錄） 中的範例：</span><span class="sxs-lookup"><span data-stu-id="358dd-197">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] <span data-ttu-id="358dd-198">`docker run` '-P' 引數對應連接埠的通訊埠 80 的容器中本機電腦上的 5000 (連接埠對應表單`host:container`)。</span><span class="sxs-lookup"><span data-stu-id="358dd-198">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="358dd-199">如需詳細資訊，請參閱[執行 docker](https://docs.docker.com/engine/reference/commandline/exec/)命令列參數的參考。</span><span class="sxs-lookup"><span data-stu-id="358dd-199">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="358dd-200">在應用程式啟動之後，請瀏覽**http://localhost:5000/** web 瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="358dd-200">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="358dd-201">建置及執行範例，以 Docker for Windows 容器</span><span class="sxs-lookup"><span data-stu-id="358dd-201">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="358dd-202">您可以建置及執行 Docker 使用 Windows 容器，使用下列命令 （的指示會假設儲存機制的根目錄） 中的範例：</span><span class="sxs-lookup"><span data-stu-id="358dd-202">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="358dd-203">您必須瀏覽至**容器 IP 位址**（相對於 http://localhost) 直接瀏覽器中使用 Windows 容器時。</span><span class="sxs-lookup"><span data-stu-id="358dd-203">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="358dd-204">您可以取得 IP 位址，您的容器進行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="358dd-204">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="358dd-205">開啟另一個命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="358dd-205">Open up another command prompt.</span></span>
* <span data-ttu-id="358dd-206">執行`docker ps`以查看您執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="358dd-206">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="358dd-207">應該有"aspnetcore_sample 」 容器。</span><span class="sxs-lookup"><span data-stu-id="358dd-207">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="358dd-208">執行 `docker exec aspnetcore_sample ipconfig`。</span><span class="sxs-lookup"><span data-stu-id="358dd-208">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="358dd-209">複製的容器 IP 位址並貼到您的瀏覽器 (例如，172.29.245.43)。</span><span class="sxs-lookup"><span data-stu-id="358dd-209">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!Note]
> <span data-ttu-id="358dd-210">Docker exec 支援雜湊或名稱識別的容器。</span><span class="sxs-lookup"><span data-stu-id="358dd-210">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="358dd-211">在本例中，會使用名稱 (aspnetcore_sample)。</span><span class="sxs-lookup"><span data-stu-id="358dd-211">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="358dd-212">請參閱下列如何取得執行中的 Windows 容器的 IP 位址的範例。</span><span class="sxs-lookup"><span data-stu-id="358dd-212">See the following example of how to get the IP address of a running Windows container.</span></span>

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

> [!Note]
> <span data-ttu-id="358dd-213">Docker exec 執行新的命令在執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="358dd-213">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="358dd-214">如需詳細資訊，請參閱[docker exec 參考](https://docs.docker.com/engine/reference/commandline/exec/)命令列參數。</span><span class="sxs-lookup"><span data-stu-id="358dd-214">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="358dd-215">您可以產生應用程式準備好要部署到生產環境使用在本機的[dotnet 發行](../tools/dotnet-publish.md)命令。</span><span class="sxs-lookup"><span data-stu-id="358dd-215">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!Note]
> <span data-ttu-id="358dd-216">-C 的版本引數建置 （預設值是偵錯模式） 的發行模式中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="358dd-216">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="358dd-217">如需詳細資訊，請參閱[dotnet 執行參考](../tools/dotnet-run.md)命令列參數。</span><span class="sxs-lookup"><span data-stu-id="358dd-217">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="358dd-218">您可以在執行應用程式**Windows**使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="358dd-218">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="358dd-219">您可以在執行應用程式**Linux**或**macOS**使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="358dd-219">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="358dd-220">此範例中使用的 docker 映像</span><span class="sxs-lookup"><span data-stu-id="358dd-220">Docker Images used in this sample</span></span>

<span data-ttu-id="358dd-221">在此範例中使用下列的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="358dd-221">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="358dd-222">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="358dd-222">Congratulations!</span></span> <span data-ttu-id="358dd-223">只要有：</span><span class="sxs-lookup"><span data-stu-id="358dd-223">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="358dd-224">學到的 Microsoft.NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="358dd-224">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="358dd-225">取得 ASP.NET Core Dockerize 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="358dd-225">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="358dd-226">在本機執行 ASP.NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="358dd-226">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="358dd-227">建置和執行 Linux 容器與 Docker 的範例</span><span class="sxs-lookup"><span data-stu-id="358dd-227">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="358dd-228">建置和執行範例與 Docker for Windows 容器</span><span class="sxs-lookup"><span data-stu-id="358dd-228">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="358dd-229">**接下來的步驟**</span><span class="sxs-lookup"><span data-stu-id="358dd-229">**Next Steps**</span></span>

<span data-ttu-id="358dd-230">以下是一些您可以採取的後續步驟：</span><span class="sxs-lookup"><span data-stu-id="358dd-230">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="358dd-231">使用 Visual Studio Docker 工具</span><span class="sxs-lookup"><span data-stu-id="358dd-231">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="358dd-232">將從 Azure 容器登錄至 Azure 容器執行個體的 Docker 映像部署</span><span class="sxs-lookup"><span data-stu-id="358dd-232">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="358dd-233">使用 Visual Studio 程式碼進行偵錯</span><span class="sxs-lookup"><span data-stu-id="358dd-233">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="358dd-234">未授權者手上取得使用 Visual Studio for Mac、 容器和無伺服器的程式碼在雲端中</span><span class="sxs-lookup"><span data-stu-id="358dd-234">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="358dd-235">開始使用 Docker 和 Visual Studio for Mac 實驗室</span><span class="sxs-lookup"><span data-stu-id="358dd-235">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> <span data-ttu-id="358dd-236">如果您沒有 Azure 訂用帳戶，[立即註冊](https://azure.microsoft.com/free/?b=16.48)免費 30 天的帳戶和 Azure 信用額度試用 Azure 服務的任何組合中的 get 美金 200。</span><span class="sxs-lookup"><span data-stu-id="358dd-236">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
