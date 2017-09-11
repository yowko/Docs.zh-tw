---
title: "建置 .NET Core Docker 映像"
description: "了解 Docker 映像和 .NET Core"
keywords: ".NET、.NET Core、Docker"
author: spboyer
ms.author: shboyer
ms.date: 08/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.translationtype: HT
ms.sourcegitcommit: 9dc52f3a8c74c1aa575a83cb3bbd579b93fae9ae
ms.openlocfilehash: 0e679ffc22f52de5e2ce8194942efbb2f5299ee4
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---

#<a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="909df-104">建置 .NET Core 應用程式的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="909df-104">Building Docker Images for .NET Core Applications</span></span>

 
> [!IMPORTANT]
> <span data-ttu-id="909df-105">我們正在更新 .NET Core 2.0。</span><span class="sxs-lookup"><span data-stu-id="909df-105">We are in the process of updating for .NET Core 2.0.</span></span> <span data-ttu-id="909df-106">下列說明已過時。</span><span class="sxs-lookup"><span data-stu-id="909df-106">The instructions below are out of date.</span></span> <span data-ttu-id="909df-107">造成您的不便，我們深感抱歉。</span><span class="sxs-lookup"><span data-stu-id="909df-107">We sincerely apologize for any inconvenience!</span></span>

<span data-ttu-id="909df-108">為了解如何同時使用 .NET Core 和 Docker，我們必須先了解取得的不同 Docker 映像，以及正確的使用時機。</span><span class="sxs-lookup"><span data-stu-id="909df-108">In order to get an understanding of how to use .NET Core and Docker together, we must first get to know the different Docker images that are offered and when is the right use case for them.</span></span> <span data-ttu-id="909df-109">在此，我們會逐步解說所獲得的變化、建置 ASP.NET Core Web API、使用 Yeoman Docker 工具建立可偵錯的容器，以及預覽 Visual Studio Code 如何在程序中提供協助。</span><span class="sxs-lookup"><span data-stu-id="909df-109">Here we will walk through the variations offered, build an ASP.NET Core Web API, use the Yeoman Docker tools to create a debuggable container as well as peek at how Visual Studio Code can assist in the process.</span></span> 

## <a name="docker-image-optimizations"></a><span data-ttu-id="909df-110">Docker 映像最佳化</span><span class="sxs-lookup"><span data-stu-id="909df-110">Docker Image Optimizations</span></span>

<span data-ttu-id="909df-111">在建置開發人員的 Docker 映像時，我們會著重在三個主要案例︰</span><span class="sxs-lookup"><span data-stu-id="909df-111">When building Docker images for developers, we focused on three main scenarios:</span></span>

- <span data-ttu-id="909df-112">用來開發 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="909df-112">Images used to develop .NET Core apps</span></span>
- <span data-ttu-id="909df-113">用來建置 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="909df-113">Images used to build .NET Core apps</span></span>
- <span data-ttu-id="909df-114">用來執行 .NET Core 應用程式的映像</span><span class="sxs-lookup"><span data-stu-id="909df-114">Images used to run .NET Core apps</span></span>

<span data-ttu-id="909df-115">為何是三個映像？</span><span class="sxs-lookup"><span data-stu-id="909df-115">Why three images?</span></span>
<span data-ttu-id="909df-116">在開發、建置及執行放入容器的應用程式時，我們有不同的優先考量。</span><span class="sxs-lookup"><span data-stu-id="909df-116">When developing, building and running containerized applications, we have different priorities.</span></span>
- <span data-ttu-id="909df-117">**開發︰**逐一查看變更的速度以及偵錯變更的能力。</span><span class="sxs-lookup"><span data-stu-id="909df-117">**Development:**  How fast can you iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="909df-118">映像大小不那麼重要，而是變更及查看程式碼的速度。</span><span class="sxs-lookup"><span data-stu-id="909df-118">The size of the image isn't as important, rather can you make changes to your code and see them quickly.</span></span> <span data-ttu-id="909df-119">我們有些工具，像是用於 Visual Studio Code 的 [yo docker](https://aka.ms/yodocker)，會在開發期間使用此映像。</span><span class="sxs-lookup"><span data-stu-id="909df-119">Some of our tools, like [yo docker](https://aka.ms/yodocker) for use in Visual Studio Code use this image during development time.</span></span> 
- <span data-ttu-id="909df-120">**建置︰**編譯應用程式需要的內容。</span><span class="sxs-lookup"><span data-stu-id="909df-120">**Build:** What's needed to compile your app.</span></span> <span data-ttu-id="909df-121">這包括編譯器和任何其他可最佳化二進位檔的相依性。</span><span class="sxs-lookup"><span data-stu-id="909df-121">This includes the compiler and any other dependencies to optimize the binaries.</span></span> <span data-ttu-id="909df-122">此映像不是您部署的映像，而是您用來建置實際執行映像內容的映像。</span><span class="sxs-lookup"><span data-stu-id="909df-122">This image isn't the image you deploy, rather it's an image you use to build the content you place into a production image.</span></span> <span data-ttu-id="909df-123">此映像可用於連續整合或建置環境。</span><span class="sxs-lookup"><span data-stu-id="909df-123">This image would be used in your continuous integration, or build environment.</span></span> <span data-ttu-id="909df-124">例如，不是直接在組建代理程式上安裝所有相依性，組建代理程式會引證建置映像，使用有建置映像內含應用程式所需的全部相依性，來編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="909df-124">For instance, rather than installing all the dependencies directly on a build agent, the build agent would instance a build image to compile the application with all the dependencies required to build the app contained within the image.</span></span> <span data-ttu-id="909df-125">組建代理程式只需要知道如何執行此 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="909df-125">Your build agent only needs to know how to run this Docker image.</span></span> 
- <span data-ttu-id="909df-126">**生產環境︰**多快可以部署及啟動映像。</span><span class="sxs-lookup"><span data-stu-id="909df-126">**Production:** How fast you can deploy and start your image.</span></span> <span data-ttu-id="909df-127">此映像很小，因此它可以快速地從 Docker 登錄到 Docker 主機在網路上傳輸。</span><span class="sxs-lookup"><span data-stu-id="909df-127">This image is small so it can quickly travel across the network from your Docker Registry to your Docker hosts.</span></span> <span data-ttu-id="909df-128">準備好執行的內容可用最短的時間完成 Docker 執行到處理結果。</span><span class="sxs-lookup"><span data-stu-id="909df-128">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="909df-129">在不可變的 Docker 模型中，沒必要動態編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="909df-129">In the immutable Docker model, there's no need for dynamic compilation of code.</span></span> <span data-ttu-id="909df-130">您放置在此映像中的內容會限於執行應用程式所需的二進位檔和內容。</span><span class="sxs-lookup"><span data-stu-id="909df-130">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span> <span data-ttu-id="909df-131">例如，已發行輸出使用的 `dotnet publish` 包含已編譯的二進位檔、映像、.js 和 .css 檔案。</span><span class="sxs-lookup"><span data-stu-id="909df-131">For example, the published output using `dotnet publish` which contains the compiled binaries, images, .js and .css files.</span></span> <span data-ttu-id="909df-132">經過一段時間，您會看到包含預先 JIT 編譯封裝的映像。</span><span class="sxs-lookup"><span data-stu-id="909df-132">Over time, you'll see images that contain pre-jitted packages.</span></span>  

<span data-ttu-id="909df-133">雖然有多種版本的 .NET Core 映像，但它們全都共用一或多個圖層。</span><span class="sxs-lookup"><span data-stu-id="909df-133">Though there are multiple versions of the .NET Core image, they all share one or more layers.</span></span> <span data-ttu-id="909df-134">儲存所需的磁碟空間量，或從登錄提取的差異，遠小於整體，因為所有的映像共用相同的基底層，可能還有其他層。</span><span class="sxs-lookup"><span data-stu-id="909df-134">The amount of disk space needed to store or the delta to pull from your registry is much smaller than the whole because all of the images share the same base layer and potentially others.</span></span>  

## <a name="docker-image-variations"></a><span data-ttu-id="909df-135">Docker 映像變化</span><span class="sxs-lookup"><span data-stu-id="909df-135">Docker image variations</span></span>

<span data-ttu-id="909df-136">為達成上述目標，我們在 [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) 下提供映像變體。</span><span class="sxs-lookup"><span data-stu-id="909df-136">To achieve the goals above, we provide image variants under [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

- <span data-ttu-id="909df-137">`microsoft/dotnet:<version>-sdk`：也就是 **microsoft/dotnet:1.0.0-preview2-sdk**，此映像包含具有 .NET Core 及命令列工具 (CLI) 的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="909df-137">`microsoft/dotnet:<version>-sdk` : that is **microsoft/dotnet:1.0.0-preview2-sdk**, this image contains the .NET Core SDK which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="909df-138">此映像會對應至**開發案例**。</span><span class="sxs-lookup"><span data-stu-id="909df-138">This image maps to the **development scenario**.</span></span> <span data-ttu-id="909df-139">您可以使用此映像處理本機開發、偵錯和單元測試。</span><span class="sxs-lookup"><span data-stu-id="909df-139">You would use this image for local development, debugging and unit testing.</span></span> <span data-ttu-id="909df-140">例如，所有的開發都要先於簽入程式碼。</span><span class="sxs-lookup"><span data-stu-id="909df-140">For example, all the development you do, before you check in your code.</span></span> <span data-ttu-id="909df-141">此映像也可用於**建置**案例。</span><span class="sxs-lookup"><span data-stu-id="909df-141">This image can also be used for your **build** scenarios.</span></span>

- <span data-ttu-id="909df-142">`microsoft/dotnet:<version>-core`︰也就是 **microsoft/dotnet:1.0.0-core**，此映像會執行[可攜式 .NET Core 應用程式](../deploying/index.md)，並為了在**生產環境**中執行應用程式而經過最佳化。</span><span class="sxs-lookup"><span data-stu-id="909df-142">`microsoft/dotnet:<version>-core` : that is **microsoft/dotnet:1.0.0-core**, image which runs [portable .NET Core applications](../deploying/index.md) and it is optimized for running your application in **production**.</span></span> <span data-ttu-id="909df-143">它不包含 SDK，且表示要採用最佳化的 `dotnet publish` 輸出。</span><span class="sxs-lookup"><span data-stu-id="909df-143">It does not contain the SDK, and is meant to take the optimized output of `dotnet publish`.</span></span> <span data-ttu-id="909df-144">可攜式執行階段非常適合 Docker 容器案例，因為執行多個容器可從共用的映像圖層中得益。</span><span class="sxs-lookup"><span data-stu-id="909df-144">The portable runtime is well suited for Docker container scenarios as running multiple containers benefit from shared image layers.</span></span>  

## <a name="alternative-images"></a><span data-ttu-id="909df-145">替代的映像</span><span class="sxs-lookup"><span data-stu-id="909df-145">Alternative images</span></span>

<span data-ttu-id="909df-146">除了開發、建置和生產環境的最佳化案例，我們還提供其他映像︰</span><span class="sxs-lookup"><span data-stu-id="909df-146">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

- <span data-ttu-id="909df-147">`microsoft/dotnet:<version>-onbuild`︰也就是 **microsoft/dotnet:1.0.0-preview2-onbuild**，包含 [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild) 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="909df-147">`microsoft/dotnet:<version>-onbuild` : that is **microsoft/dotnet:1.0.0-preview2-onbuild**, contains [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild) triggers.</span></span> <span data-ttu-id="909df-148">組建會[複製](https://docs.docker.com/engine/reference/builder/#/copy)應用程式，執行 `dotnet restore` 並建立 [進入點](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` 指示，在執行 Docker 映像時執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="909df-148">The build will [COPY](https://docs.docker.com/engine/reference/builder/#/copy) your application, run `dotnet restore` and create an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` instruction to run the application when the Docker image is run.</span></span> <span data-ttu-id="909df-149">至於未最佳化的生產環境映像，有些人可能會覺得它很有用，因為只要將原始程式碼複製到映像並執行即可。</span><span class="sxs-lookup"><span data-stu-id="909df-149">While not an optimized image for production, some may find it useful to simply copy their source code into an image and run it.</span></span> 

- <span data-ttu-id="909df-150">`microsoft/dotnet:<version>-core-deps`︰也就是 **microsoft/dotnet:1.0.0-core-deps**，如果想要執行自封式應用程式，請使用此映像。</span><span class="sxs-lookup"><span data-stu-id="909df-150">`microsoft/dotnet:<version>-core-deps` : that is **microsoft/dotnet:1.0.0-core-deps**, if you wish to run self-contained applications use this image.</span></span> <span data-ttu-id="909df-151">它包含作業系統及 .NET Core 所需的所有原生相依性。</span><span class="sxs-lookup"><span data-stu-id="909df-151">It contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="909df-152">此映像也可用為您自己自訂的 CoreFX 或 CoreCLR 組建的基礎映像。</span><span class="sxs-lookup"><span data-stu-id="909df-152">This image can also be used as a base image for your own custom CoreFX or CoreCLR builds.</span></span> <span data-ttu-id="909df-153">雖然 **onbuild** 變體經過最佳化後，只需將程式碼放入映像並執行即可，但此映像經過最佳化後，只具有執行 .NET Core 應用程式所需的作業系統相依性，使得 .NET 執行階段和應用程式封裝在一起。</span><span class="sxs-lookup"><span data-stu-id="909df-153">While the **onbuild** variant is optimized to simply place your code in an image and run it, this image is optimized to have only the operating system dependencies required to run .NET Core apps that have the .NET runtime packaged with the application.</span></span> <span data-ttu-id="909df-154">此映像通常不會為在相同的主機上執行多個 .NET Core 容器而最佳化，因為每個映像在應用程式內都會攜帶 .NET Core 執行階段，而您不會得益於映像圖層。</span><span class="sxs-lookup"><span data-stu-id="909df-154">This image isn't generally optimized for running multiple .NET Core containers on the same host, as each image carries the .NET Core runtime within the application, and you will not benefit from image layering.</span></span>   

<span data-ttu-id="909df-155">每個變體的最新版本︰</span><span class="sxs-lookup"><span data-stu-id="909df-155">Latest versions of each variant:</span></span>

- <span data-ttu-id="909df-156">`microsoft/dotnet:latest` 或 `microsoft/dotnet` (包括 SDK)</span><span class="sxs-lookup"><span data-stu-id="909df-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (includes SDK)</span></span>
- `microsoft/dotnet:onbuild`
- `microsoft/dotnet:core`
- `microsoft/dotnet:core-deps`

<span data-ttu-id="909df-157">以下是開發電腦上的 `docker pull <imagename>` 顯示各種大小後的映像清單。</span><span class="sxs-lookup"><span data-stu-id="909df-157">Here is a list of the images after a `docker pull <imagename>` on a development machine to show the various sizes.</span></span> <span data-ttu-id="909df-158">請注意，開發/建置變體 `microsoft/dotnet:1.0.0-preview2-sdk` 較大，因為它包含開發和建置應用程式的 SDK。</span><span class="sxs-lookup"><span data-stu-id="909df-158">Notice, the development/build variant, `microsoft/dotnet:1.0.0-preview2-sdk` is larger as it contains the SDK to develop and build your application.</span></span> <span data-ttu-id="909df-159">生產環境變體 `microsoft/dotnet:core` 較小，因為它只包含 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="909df-159">The production variant, `microsoft/dotnet:core` is smaller, as it only contains the .NET Core runtime.</span></span> <span data-ttu-id="909df-160">能夠在 Linux 上使用的最小映像 `core-deps` 相當小，但您的應用程式需要複製 .NET 執行階段的私用複本來加以搭配。</span><span class="sxs-lookup"><span data-stu-id="909df-160">The minimal image capable of being used on Linux, `core-deps`, is quite smaller, however your application will need to copy a private copy of the .NET runtime with it.</span></span> <span data-ttu-id="909df-161">因為容器已經是私人的隔離障礙，所以在執行多個 dotnet 型的容器時會遺失最佳化。</span><span class="sxs-lookup"><span data-stu-id="909df-161">Since containers are already private isolation barriers, you will lose that optimization when running multiple dotnet based containers.</span></span> 

```
REPOSITORY          TAG                     IMAGE ID            SIZE
microsoft/dotnet    1.0.0-preview2-onbuild  19b6a6c4b1db        540.4 MB
microsoft/dotnet    onbuild                 19b6a6c4b1db        540.4 MB
microsoft/dotnet    1.0.0-preview2-sdk      a92c3d9ad0e7        540.4 MB
microsoft/dotnet    core                    5224a9f2a2aa        253.2 MB
microsoft/dotnet    1.0.0-core-deps         c981a2eebe0e        166.2 MB
microsoft/dotnet    core-deps               c981a2eebe0e        166.2 MB
microsoft/dotnet    latest                  03c10abbd08a        540.4 MB
microsoft/dotnet    1.0.0-core              b8da4a1fd280        253.2 MB
```

## <a name="prerequisites"></a><span data-ttu-id="909df-162">必要條件</span><span class="sxs-lookup"><span data-stu-id="909df-162">Prerequisites</span></span>

<span data-ttu-id="909df-163">若要建置並執行，您需要安裝幾個項目︰</span><span class="sxs-lookup"><span data-stu-id="909df-163">To build and run, you'll need a few things installed:</span></span>

- [<span data-ttu-id="909df-164">.NET Core</span><span class="sxs-lookup"><span data-stu-id="909df-164">.NET Core</span></span>](http://dot.net)
- <span data-ttu-id="909df-165">[Docker](https://www.docker.com/products/docker)：在本機執行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="909df-165">[Docker](https://www.docker.com/products/docker) to run your Docker containers locally</span></span>
- [<span data-ttu-id="909df-166">Node.js</span><span class="sxs-lookup"><span data-stu-id="909df-166">Node.js</span></span>](https://nodejs.org/)
- <span data-ttu-id="909df-167">[ASP.NET Yeoman 產生器](https://github.com/omnisharp/generator-aspnet)：建立 Web API 應用程式</span><span class="sxs-lookup"><span data-stu-id="909df-167">[Yeoman generator for ASP.NET](https://github.com/omnisharp/generator-aspnet) for creating the Web API application</span></span>
- <span data-ttu-id="909df-168">[Docker Yeoman 產生器](http://aka.ms/yodocker)：來自 Microsoft</span><span class="sxs-lookup"><span data-stu-id="909df-168">[Yeoman generator for Docker](http://aka.ms/yodocker) from Microsoft</span></span>

<span data-ttu-id="909df-169">使用 npm 安裝 ASP.NET Core 和 Docker 的 Yeoman 產生器</span><span class="sxs-lookup"><span data-stu-id="909df-169">Install the Yeoman generators for ASP.NET Core and Docker using npm</span></span> 

```
npm install -g yo generator-aspnet generator-docker
```

> [!NOTE]
> <span data-ttu-id="909df-170">這個範例會使用 [Visual Studio Code](http://code.visualstudio.com) 當作編輯器。</span><span class="sxs-lookup"><span data-stu-id="909df-170">This sample will be using [Visual Studio Code](http://code.visualstudio.com) for the editor.</span></span>

## <a name="creating-the-web-api-application"></a><span data-ttu-id="909df-171">建立 Web API 應用程式</span><span class="sxs-lookup"><span data-stu-id="909df-171">Creating the Web API application</span></span>

<span data-ttu-id="909df-172">針對參考點，在將應用程式放入容器前，要先在本機執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="909df-172">For a reference point, before we containerize the application, first run the application locally.</span></span> 

<span data-ttu-id="909df-173">完成的應用程式位於 [GitHub 上的 dotnet/docs 儲存機制](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images)。</span><span class="sxs-lookup"><span data-stu-id="909df-173">The finished application is located in the [dotnet/docs repository on GitHub](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images).</span></span> <span data-ttu-id="909df-174">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="909df-174">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="909df-175">建立應用程式的目錄。</span><span class="sxs-lookup"><span data-stu-id="909df-175">Create a directory for your application.</span></span>

<span data-ttu-id="909df-176">在該目錄中開啟命令或終端機工作階段，並輸入下列內容使用 ASP.NET Yeoman 產生器︰</span><span class="sxs-lookup"><span data-stu-id="909df-176">Open a command or terminal session in that directory and use the ASP.NET Yeoman generator by typing the following:</span></span>
```
yo aspnet
```

<span data-ttu-id="909df-177">選取 [Web API 應用程式] 並在應用程式名稱輸入 **api**，然後點選 Enter。</span><span class="sxs-lookup"><span data-stu-id="909df-177">Select **Web API Application** and type **api** for the name of the app and tap enter.</span></span>  <span data-ttu-id="909df-178">應用程式建立結構後，請變更至 `/api` 目錄，並使用 `dotnet restore` 還原 NuGet 相依性。</span><span class="sxs-lookup"><span data-stu-id="909df-178">Once the application is scaffolded, change to the `/api` directory and restore the NuGet dependencies using `dotnet restore`.</span></span>

```
cd api
dotnet restore
```

<span data-ttu-id="909df-179">使用 `dotnet run` 並瀏覽至 **http://localhost:5000/api/values** 測試應用程式</span><span class="sxs-lookup"><span data-stu-id="909df-179">Test the application using `dotnet run` and browsing to **http://localhost:5000/api/values**</span></span>

```javascript
[
    "value1",
    "value2"
]
```

<span data-ttu-id="909df-180">使用 `Ctrl+C` 停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="909df-180">Use `Ctrl+C` to stop the application.</span></span>

## <a name="adding-docker-support"></a><span data-ttu-id="909df-181">新增 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="909df-181">Adding Docker support</span></span>

<span data-ttu-id="909df-182">使用來自 Microsoft 的 Yeoman 產生器可將 Docker 支援加入專案。</span><span class="sxs-lookup"><span data-stu-id="909df-182">Adding Docker support to the project is achieved using the Yeoman generator from Microsoft.</span></span> <span data-ttu-id="909df-183">目前，它透過建立協助在容器內建置和執行專案的 Dockerfile 和指令碼，支援 .NET Core、Node.js 和 Go 專案。</span><span class="sxs-lookup"><span data-stu-id="909df-183">It currently supports .NET Core, Node.js and Go projects by creating a Dockerfile and scripts that help build and run projects inside containers.</span></span> <span data-ttu-id="909df-184">也會加入 Visual Studio Code 特定檔案 (launch.json、tasks.json) 供編輯器偵錯和命令調色盤支援。</span><span class="sxs-lookup"><span data-stu-id="909df-184">Visual Studio Code specific files are also added (launch.json, tasks.json) for editor debugging and command palette support.</span></span>

```console
$ yo docker

     _-----_     ╭──────────────────────────╮
    |       |    │   Welcome to the Docker  │
    |--(o)--|    │        generator!        │
   `---------´   │     Let's add Docker     │
    ( _´U`_ )    │  container magic to your │
    /___A___\   /│           app!           │
     |  ~  |     ╰──────────────────────────╯
   __'.___.'__
 ´   `  |° ´ Y `

? What language is your project using? (Use arrow keys)
❯ .NET Core
  Golang
  Node.js
```

- <span data-ttu-id="909df-185">選取 `.NET Core` 作為專案類型</span><span class="sxs-lookup"><span data-stu-id="909df-185">Select `.NET Core` as the project type</span></span>
- <span data-ttu-id="909df-186">`rtm` 為 .NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="909df-186">`rtm` for the version of .NET Core</span></span>
- <span data-ttu-id="909df-187">`Y` 是使用網頁伺服器的專案</span><span class="sxs-lookup"><span data-stu-id="909df-187">`Y` the project uses a web server</span></span>
- <span data-ttu-id="909df-188">`5000` 是 Web API 應用程式接聽中的連接埠 (http://localhost:5000/)</span><span class="sxs-lookup"><span data-stu-id="909df-188">`5000` is the port the Web API application is listening on (http://localhost:5000)</span></span>
- <span data-ttu-id="909df-189">`api` 為映像名稱</span><span class="sxs-lookup"><span data-stu-id="909df-189">`api` for the image name</span></span>
- <span data-ttu-id="909df-190">`api` 為服務名稱</span><span class="sxs-lookup"><span data-stu-id="909df-190">`api` for the service name</span></span>
- <span data-ttu-id="909df-191">`api` 為撰寫專案</span><span class="sxs-lookup"><span data-stu-id="909df-191">`api` for the compose project</span></span> 
- <span data-ttu-id="909df-192">`Y` 會覆寫目前的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="909df-192">`Y` to overwrite the current Dockerfile</span></span>

<span data-ttu-id="909df-193">產生器完成時，下列檔案會加入專案中</span><span class="sxs-lookup"><span data-stu-id="909df-193">When the generator is complete, the following files are added to the project</span></span>

- <span data-ttu-id="909df-194">.vscode/launch.json</span><span class="sxs-lookup"><span data-stu-id="909df-194">.vscode/launch.json</span></span>
- <span data-ttu-id="909df-195">Dockerfile.debug</span><span class="sxs-lookup"><span data-stu-id="909df-195">Dockerfile.debug</span></span>
- <span data-ttu-id="909df-196">Dockerfile</span><span class="sxs-lookup"><span data-stu-id="909df-196">Dockerfile</span></span>
- <span data-ttu-id="909df-197">docker-compose.debug.yml</span><span class="sxs-lookup"><span data-stu-id="909df-197">docker-compose.debug.yml</span></span>
- <span data-ttu-id="909df-198">docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="909df-198">docker-compose.yml</span></span>
- <span data-ttu-id="909df-199">dockerTask.ps1</span><span class="sxs-lookup"><span data-stu-id="909df-199">dockerTask.ps1</span></span>
- <span data-ttu-id="909df-200">dockerTask.sh</span><span class="sxs-lookup"><span data-stu-id="909df-200">dockerTask.sh</span></span>
- <span data-ttu-id="909df-201">.vscode/tasks.json</span><span class="sxs-lookup"><span data-stu-id="909df-201">.vscode/tasks.json</span></span>

<span data-ttu-id="909df-202">產生器會建立兩個 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="909df-202">The generator creates two Dockerfiles.</span></span>

<span data-ttu-id="909df-203">**Dockerfile.debug**：這個檔案是以 **microsoft/dotnet:1.0.0-preview2-sdk** 映像為基礎，如果您注意到，它是出自映像變體清單，包括 SDK、CLI 和 .NET Core，而且會是開發和偵錯 (F5) 所用的映像。</span><span class="sxs-lookup"><span data-stu-id="909df-203">**Dockerfile.debug** - this file is based on the **microsoft/dotnet:1.0.0-preview2-sdk** image which if you note from the list of image variants, includes the SDK, CLI and .NET Core and will be the image used for development and debugging (F5).</span></span> <span data-ttu-id="909df-204">包括所有這些元件會產生較大的映像，大小約為 540 MB。</span><span class="sxs-lookup"><span data-stu-id="909df-204">Including all of these components produces a larger image with a size roughly of 540MB.</span></span>

<span data-ttu-id="909df-205">**Dockerfile**：此映像是以 **microsoft/dotnet:1.0.0-core** 為基礎的發行映像，應該用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="909df-205">**Dockerfile** - this image is the release image based on **microsoft/dotnet:1.0.0-core** and should be used for production.</span></span> <span data-ttu-id="909df-206">此映像在建置時約為 253 MB。</span><span class="sxs-lookup"><span data-stu-id="909df-206">This image when built is approximately 253 MB.</span></span>

### <a name="creating-the-docker-images"></a><span data-ttu-id="909df-207">建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="909df-207">Creating the Docker images</span></span>
<span data-ttu-id="909df-208">使用 `dockerTask.sh` 或 `dockerTask.ps1` 指令碼，我們可以針對特定的環境建置或撰寫 **api** 應用程式的映像和容器。</span><span class="sxs-lookup"><span data-stu-id="909df-208">Using the `dockerTask.sh` or `dockerTask.ps1` script, we can build or compose the image and container for the **api** application for a specific environment.</span></span> <span data-ttu-id="909df-209">執行下列命令以建置**偵錯**映像。</span><span class="sxs-lookup"><span data-stu-id="909df-209">Build the **debug** image by running the following command.</span></span>

```bash
./dockerTask.sh build debug
```

<span data-ttu-id="909df-210">此映像會建置 ASP.NET 應用程式、執行 `dotnet restore`、將偵錯工具加入映像、設定 `ENTRYPOINT`，最後將應用程式複製到映像。</span><span class="sxs-lookup"><span data-stu-id="909df-210">The image will build the ASP.NET application, run `dotnet restore`, add the debugger to the image, set an `ENTRYPOINT` and finally copy the app to the image.</span></span> <span data-ttu-id="909df-211">結果是名為 *api* 的 Docker 映像，附帶「偵錯」的 `TAG`。</span><span class="sxs-lookup"><span data-stu-id="909df-211">The result is a Docker image named *api* with a `TAG` of *debug*.</span></span>  <span data-ttu-id="909df-212">請使用 `docker images` 查看電腦上的映像。</span><span class="sxs-lookup"><span data-stu-id="909df-212">See the images on the machine using `docker images`.</span></span>

```bash
docker images

REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        a few seconds ago   779.8 MB
```

<span data-ttu-id="909df-213">產生映像並在 Docker 容器內執行應用程式的另一個方法，是在 Visual Studio Code 中開啟應用程式，並使用偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="909df-213">Another way to generate the image and run the application within the Docker container is to open the application in Visual Studio Code and use the debugging tools.</span></span> 

<span data-ttu-id="909df-214">在 Visual Studio Code 左側的 [檢視] 列中選取偵錯圖示。</span><span class="sxs-lookup"><span data-stu-id="909df-214">Select the debugging icon in the View Bar on the left side of Visual Studio Code.</span></span>

![vscode 偵錯圖示](./media/building-net-docker-images/debugging_debugicon.png)

<span data-ttu-id="909df-216">然後點選播放圖示或 F5 產生映像，在容器內啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="909df-216">Then tap the play icon or F5 to generate the image and start the application within the container.</span></span> <span data-ttu-id="909df-217">Web API 會使用您在 http://localhost:5000 的預設網頁瀏覽器啟動。</span><span class="sxs-lookup"><span data-stu-id="909df-217">The Web API will be launched using your default web browser at http://localhost:5000.</span></span>

![VSCode Docker 工具偵錯](./media/building-net-docker-images/docker-tools-vscode-f5.png)

<span data-ttu-id="909df-219">您可在應用程式、逐步執行等等設定中斷點，就像在開發電腦本機執行應用程式，而不是在容器內。</span><span class="sxs-lookup"><span data-stu-id="909df-219">You may set break points in your application, step through, etc. just as if the application was running locally on your development machine as opposed to inside the container.</span></span> <span data-ttu-id="909df-220">在容器內偵錯的優點是，這是會部署到生產環境的同一映像。</span><span class="sxs-lookup"><span data-stu-id="909df-220">The benefit to debugging within the container is this is the same image that would be deployed to a production environment.</span></span>

<span data-ttu-id="909df-221">建立發行或生產環境映像，只需要從終端機執行命令，傳遞 `release` 環境名稱。</span><span class="sxs-lookup"><span data-stu-id="909df-221">Creating the release or production image requires simply running the command from the terminal passing the `release` environment name.</span></span>

```bash
./dockerTask build release
```

<span data-ttu-id="909df-222">此命令會根據較小的 **microsoft/dotnet:core** 基礎映像建立映像、[EXPOSE](https://docs.docker.com/engine/reference/builder/#/expose) 連接埠 5000、設定 `dotnet api.dll` 的 [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint)，再將它複製到 `/app` 目錄。</span><span class="sxs-lookup"><span data-stu-id="909df-222">The command creates the image based on the smaller **microsoft/dotnet:core** base image, [EXPOSE](https://docs.docker.com/engine/reference/builder/#/expose) port 5000, sets the [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) for `dotnet api.dll` and copies it to the `/app` directory.</span></span> <span data-ttu-id="909df-223">不會有任何偵錯工具、SDK 或 `dotnet restore` 產生更小的映像。</span><span class="sxs-lookup"><span data-stu-id="909df-223">There is no debugger, SDK or `dotnet restore` resulting in a much smaller image.</span></span> <span data-ttu-id="909df-224">此映像名為 **api**，附帶**最新的**的 `TAG`。</span><span class="sxs-lookup"><span data-stu-id="909df-224">The image is named **api** with a `TAG` of **latest**.</span></span>

```
REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        1 hour ago        779.8 MB
api                 latest               ef17184c8de6        1 hour ago        260.7 MB
```

## <a name="summary"></a><span data-ttu-id="909df-225">總結</span><span class="sxs-lookup"><span data-stu-id="909df-225">Summary</span></span>

<span data-ttu-id="909df-226">使用 Docker 產生器將必要的檔案新增至 Web API 應用程式，曾經讓建立開發和生產環境版本映像的程序變得簡單。</span><span class="sxs-lookup"><span data-stu-id="909df-226">Using the Docker generator to add the necessary files to our Web API application made the process simple to create the development and production versions of the images.</span></span>  <span data-ttu-id="909df-227">這項工具之所以能夠跨平台，是因為它也提供 PowerShell 指令碼來達成，在提供於容器內逐步偵錯應用程式的 Windows 和 Visual Studio 整合中達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="909df-227">The tooling is cross platform by also providing a PowerShell script to accomplish the same results on Windows and Visual Studio Code integration providing step through debugging of the application within the container.</span></span> <span data-ttu-id="909df-228">透過了解映像變體和目標案例，您可以最佳化內部迴圈開發程序，同時達到最佳化生產環境部署的映像。</span><span class="sxs-lookup"><span data-stu-id="909df-228">By understanding the image variants and the target scenarios, you can optimize your inner-loop development process, while achieving optimized images for production deployments.</span></span>  



