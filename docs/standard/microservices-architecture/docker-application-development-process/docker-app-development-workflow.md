---
title: Docker 應用程式的開發工作流程
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 應用程式的開發工作流程
keywords: Docker, 微服務, ASP.NET, 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 73d4ad82ef8c48f57aa4cceceedba862a2c9ffa4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="ccbea-104">Docker 應用程式的開發工作流程</span><span class="sxs-lookup"><span data-stu-id="ccbea-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="ccbea-105">應用程式開發生命週期從每位開發人員的電腦開始，開發人員在此使用其偏好的語言撰寫應用程式的程式碼，並在本機進行測試。</span><span class="sxs-lookup"><span data-stu-id="ccbea-105">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="ccbea-106">不論開發人員選擇哪一種語言、架構和平台，只要使用此工作流程，開發人員就一定能開發和測試 Docker 容器，但只能在本機作業。</span><span class="sxs-lookup"><span data-stu-id="ccbea-106">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="ccbea-107">每個容器 (Docker 映像的執行個體) 包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="ccbea-107">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="ccbea-108">作業系統選取項目 (例如 Linux 發行版本、Windows Nano Server 或 Windows Server Core)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-108">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="ccbea-109">開發人員新增的檔案 (應用程式二進位檔等等)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-109">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="ccbea-110">組態資訊 (環境設定和相依性)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-110">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="ccbea-111">開發 Docker 容器型應用程式的工作流程</span><span class="sxs-lookup"><span data-stu-id="ccbea-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="ccbea-112">本節描述 Docker 容器型應用程式的「內部迴圈」開發工作流程。</span><span class="sxs-lookup"><span data-stu-id="ccbea-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="ccbea-113">內部迴圈工作流程表示不考慮更廣泛的 DevOps 工作流程，只著重於在開發人員電腦上完成的開發工作。</span><span class="sxs-lookup"><span data-stu-id="ccbea-113">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="ccbea-114">設定環境的初始步驟不包含在內，因為這些只進行一次。</span><span class="sxs-lookup"><span data-stu-id="ccbea-114">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="ccbea-115">應用程式是由您自己的服務加上額外的程式庫 (相依性) 所組成。</span><span class="sxs-lookup"><span data-stu-id="ccbea-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="ccbea-116">以下是組建 Docker 應用程式時通常會採用的基本步驟，如圖 5-1 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="ccbea-117">**圖 5-1。**</span><span class="sxs-lookup"><span data-stu-id="ccbea-117">**Figure 5-1.**</span></span> <span data-ttu-id="ccbea-118">開發 Docker 容器化應用程式的逐步工作流程</span><span class="sxs-lookup"><span data-stu-id="ccbea-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="ccbea-119">本指南會詳細說明這整個程序，並針對 Visual Studio 環境說明每個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="ccbea-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="ccbea-120">當您使用編輯器/CLI 開發方法 (例如，Visual Studio Code 加上 macOS 或 Windows 上的 Docker CLI) 時，您需要知道每一個步驟，通常要比使用 Visual Studio 更詳細。</span><span class="sxs-lookup"><span data-stu-id="ccbea-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="ccbea-121">如需在 CLI 環境中工作的詳細資訊，請參閱電子書 [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/) (使用 Microsoft 平台和工具的 Docker 容器化應用程式生命週期)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-121">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="ccbea-122">當您使用 Visual Studio 2015 或 Visual Studio 2017 時，這些步驟有很多已為您處理，大幅提升您的產能。</span><span class="sxs-lookup"><span data-stu-id="ccbea-122">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="ccbea-123">特別是當您使用 Visual Studio 2017，並以多容器應用程式為目標時。</span><span class="sxs-lookup"><span data-stu-id="ccbea-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="ccbea-124">例如，只要按一下滑鼠，Visual Studio 就會將 Dockerfile 和 docker-compose.yml 檔案新增至您的專案，使用您的應用程式組態。</span><span class="sxs-lookup"><span data-stu-id="ccbea-124">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="ccbea-125">當您在 Visual Studio 中執行應用程式時，它會組建 Docker 映像並直接在 Docker 中執行多容器應用程式，甚至可讓您立即偵錯數個容器。</span><span class="sxs-lookup"><span data-stu-id="ccbea-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="ccbea-126">這些功能可大幅提高開發速度。</span><span class="sxs-lookup"><span data-stu-id="ccbea-126">These features will boost your development speed.</span></span>

<span data-ttu-id="ccbea-127">不過，Visual Studio 自動化這些步驟並不表示您不需要知道 Docker 在做什麼。</span><span class="sxs-lookup"><span data-stu-id="ccbea-127">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="ccbea-128">因此，在後續的指引中，我們會詳細說明每個步驟。</span><span class="sxs-lookup"><span data-stu-id="ccbea-128">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="ccbea-129">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="ccbea-129">Step 1.</span></span> <span data-ttu-id="ccbea-130">開始撰寫程式碼，並建立您的初始應用程式或服務比較基準</span><span class="sxs-lookup"><span data-stu-id="ccbea-130">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="ccbea-131">開發 Docker 應用程式類似於不使用 Docker 開發應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="ccbea-131">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="ccbea-132">差別在於，開發 Docker 時，您要在本機環境中部署並測試 Docker 容器內執行的應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="ccbea-132">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="ccbea-133">容器可以是 Linux 容器或 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="ccbea-133">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="ccbea-134">設定使用 Visual Studio 的本機環境</span><span class="sxs-lookup"><span data-stu-id="ccbea-134">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="ccbea-135">開始前，請確定您已安裝 [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows，如下列指示所述：</span><span class="sxs-lookup"><span data-stu-id="ccbea-135">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

<span data-ttu-id="ccbea-136">[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/) (開始使用 Docker CE for Windows)</span><span class="sxs-lookup"><span data-stu-id="ccbea-136">[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/)</span></span>

<span data-ttu-id="ccbea-137">此外，您還需要安裝 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="ccbea-137">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="ccbea-138">這比 Visual Studio 2015 更適合 Visual Studio Tools for Docker 增益集，因為 Visual Studio 2017 有更進階的 Docker 支援，例如支援偵錯容器。</span><span class="sxs-lookup"><span data-stu-id="ccbea-138">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="ccbea-139">如已在安裝期間選取 [.NET Core and Docker] 工作負載，則 Visual Studio 2017 會包含適用於 Docker 的工具，如圖 5-2 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-139">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="ccbea-140">**圖 5-2**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-140">**Figure 5-2**.</span></span> <span data-ttu-id="ccbea-141">在 Visual Studio 2017 安裝期間選取 [.NET Core and Docker] 工作負載</span><span class="sxs-lookup"><span data-stu-id="ccbea-141">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="ccbea-142">您甚至可以在於您的應用程式中啟用 Docker，並在 Docker 中部署與測試之前，只使用 .NET 開始撰寫應用程式程式碼 (如果您打算使用容器通常會使用 .NET Core)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-142">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="ccbea-143">不過，建議您盡快開始使用 Docker，因為它會成為實際環境，可以盡快發現任何問題。</span><span class="sxs-lookup"><span data-stu-id="ccbea-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="ccbea-144">我們鼓勵您這麼做，是因為 Visual Studio 和 Docker 合作很容易，您幾乎感覺不到它，最佳範例是從 Visual Studio 偵錯多容器應用程式時。</span><span class="sxs-lookup"><span data-stu-id="ccbea-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ccbea-145">其他資源</span><span class="sxs-lookup"><span data-stu-id="ccbea-145">Additional resources</span></span>

-   <span data-ttu-id="ccbea-146">**開始使用適用於 Windows 的 Docker CE**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="ccbea-146">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="ccbea-147">**Visual Studio 2017**
    [*https://www.visualstudio.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="ccbea-147">**Visual Studio 2017**
[*https://www.visualstudio.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="ccbea-148">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="ccbea-148">Step 2.</span></span> <span data-ttu-id="ccbea-149">建立與現有 .NET 基底映像有關的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="ccbea-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="ccbea-150">每個您想要組建的自訂映像都需要 Dockerfile，每個要部署的容器也需要 Dockerfile，無論您是從 Visual Studio 自動部署或使用 Docker CLI (docker run 和 docker-compose 命令) 手動部署。</span><span class="sxs-lookup"><span data-stu-id="ccbea-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="ccbea-151">如果您的應用程式包含單一的自訂服務，您需要單一的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="ccbea-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="ccbea-152">如果您的應用程式包含多項服務 (如微服務架構)，每項服務都需要一個 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="ccbea-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="ccbea-153">Dockerfile 放在您應用程式或服務的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ccbea-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="ccbea-154">它包含告訴 Docker 如何設定及執行容器中應用程式或服務的命令。</span><span class="sxs-lookup"><span data-stu-id="ccbea-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="ccbea-155">您可以使用程式碼手動建立 Dockerfile，將它與您的 .NET 相依性一起新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ccbea-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="ccbea-156">使用 Visual Studio 及其適用於 Docker 的工具，這項工作只需要按幾下滑鼠即可。</span><span class="sxs-lookup"><span data-stu-id="ccbea-156">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="ccbea-157">當您在 Visual Studio 2017 中建立新專案時，有一個選項名為 [Enable Container (Docker) Support] (啟用容器 (Docker) 支援)，如圖 5-3 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-157">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="ccbea-158">**圖 5-3**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-158">**Figure 5-3**.</span></span> <span data-ttu-id="ccbea-159">在 Visual Studio 2017 中建立新專案時啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="ccbea-159">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="ccbea-160">您也可以在 Visual Studio 中以滑鼠右鍵按一下您的專案檔，選取 [Add-Docker Project Support] (新增 Docker 專案支援) 選項，啟用新的或現有專案的 Docker 支援，如圖 5-4 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-160">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="ccbea-161">**圖 5-4**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-161">**Figure 5-4**.</span></span> <span data-ttu-id="ccbea-162">在現有的 Visual Studio 2017 專案中啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="ccbea-162">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="ccbea-163">專案 (例如 ASP.NET Web 應用程式或 Web API 服務) 的這個動作會將 Dockerfile 和所需組態新增至專案。</span><span class="sxs-lookup"><span data-stu-id="ccbea-163">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="ccbea-164">它也會新增整個解決方案的 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="ccbea-164">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="ccbea-165">在下列章節中，我們會說明這些檔案每一個的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ccbea-165">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="ccbea-166">Visual Studio 可以為您執行這項工作，但深入了解 Dockerfile 會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="ccbea-166">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="ccbea-167">選項 A：使用現有的官方 .NET Docker 映像建立專案</span><span class="sxs-lookup"><span data-stu-id="ccbea-167">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="ccbea-168">您通常會在基底映像的基礎上，為您的容器組建自訂映像，此基底映像可從 [Docker Hub](https://hub.docker.com/) 登錄的官方存放庫制取得。</span><span class="sxs-lookup"><span data-stu-id="ccbea-168">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="ccbea-169">這就是當您在 Visual Studio 中啟用 Docker 支援時，實際發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="ccbea-169">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="ccbea-170">您的 Dockerfile 會使用現有的 aspnetcore 映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-170">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="ccbea-171">前文曾說明您可以使用的 Docker 映像和存放庫，視您選擇的架構和作業系統而定。</span><span class="sxs-lookup"><span data-stu-id="ccbea-171">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="ccbea-172">例如，如果您想要使用 ASP.NET Core (Linux 或 Windows)，則要使用的映像就是 microsoft/aspnetcore:2.0。</span><span class="sxs-lookup"><span data-stu-id="ccbea-172">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="ccbea-173">因此，您只需要指定要為容器使用的基底 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-173">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="ccbea-174">將 FROM microsoft/aspnetcore:2.0 新增至您的 Dockerfile 即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="ccbea-174">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="ccbea-175">Visual Studio 會自動執行此作業，但如打算更新版本，則要更新此值。</span><span class="sxs-lookup"><span data-stu-id="ccbea-175">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="ccbea-176">使用 Docker Hub 中有版本號碼的官方 .NET 映像存放庫，可確保所有電腦上都能使用相同的語言功能 (包括開發、測試和生產環境)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-176">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="ccbea-177">下例示範 ASP.NET Core 容器的範例 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="ccbea-177">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="ccbea-178">在本例中，容器是以 2.0 版的官方 ASP.NET Core Docker 映像為基礎 (適用於 Linux 和 Windows 的多架構)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-178">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="ccbea-179">這是 `FROM microsoft/aspnetcore:2.0` 設定。</span><span class="sxs-lookup"><span data-stu-id="ccbea-179">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="ccbea-180">(如需此基底映像的進一步詳細資訊，請參閱 [ASP.NET Core Docker 映像](https://hub.docker.com/r/microsoft/aspnetcore/)頁面和 [.NET Core Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)頁面。)在 Dockerfile 中，您也需要指示 Docker 接聽您會在執行階段使用的 TCP 通訊埠 (本例中為通訊埠 80，如 EXPOSE 設定的設定)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-180">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="ccbea-181">您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。</span><span class="sxs-lookup"><span data-stu-id="ccbea-181">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="ccbea-182">例如，ENTRYPOINT 行中有 \["dotnet"，"MySingleContainerWebApp.dll"\] 會指示 Docker 執行 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccbea-182">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="ccbea-183">如果您使用 SDK 和 .NET Core CLI (dotnet CLI) 組建及執行 .NET 應用程式，此項設定會有所不同。</span><span class="sxs-lookup"><span data-stu-id="ccbea-183">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="ccbea-184">重點是 ENTRYPOINT 行與其他設定會不一樣，視您選擇的應用程式語言和平台而定。</span><span class="sxs-lookup"><span data-stu-id="ccbea-184">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ccbea-185">其他資源</span><span class="sxs-lookup"><span data-stu-id="ccbea-185">Additional resources</span></span>

-   <span data-ttu-id="ccbea-186">**建置 .NET Core 應用程式的 Docker 映像**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="ccbea-186">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span></span>

-   <span data-ttu-id="ccbea-187">**組建您自己的映像**.</span><span class="sxs-lookup"><span data-stu-id="ccbea-187">**Build your own image**.</span></span> <span data-ttu-id="ccbea-188">在正式 Docker 文件中。</span><span class="sxs-lookup"><span data-stu-id="ccbea-188">In the official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="ccbea-189">使用多架構映像存放庫</span><span class="sxs-lookup"><span data-stu-id="ccbea-189">Using multi-arch image repositories</span></span>

<span data-ttu-id="ccbea-190">一個存放庫可以包含多種平台變化，例如 Linux 映像和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-190">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="ccbea-191">這項功能可讓像 Microsoft (基底映像建立者) 這樣的廠商建立單一存放庫以涵蓋多個平台 (即 Linux 和 Windows)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-191">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="ccbea-192">例如，Docker Hub 登錄提供的 [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) 存放庫，會使用相同的存放庫名稱提供 Linux 和 Windows Nano Server 支援。</span><span class="sxs-lookup"><span data-stu-id="ccbea-192">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="ccbea-193">如果您指定標籤，如下列案例一樣明確鎖定平台：</span><span class="sxs-lookup"><span data-stu-id="ccbea-193">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="ccbea-194">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="ccbea-194">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="ccbea-195">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="ccbea-195">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="ccbea-196">但如果您指定相同的映像名稱，即使使用相同的標籤，新的多架構映像 (例如支援多架構的 aspnetcore 映像) 仍會使用 Linux 或 Windows 版本，視您要部署的 Docker 主機作業系統而定，這是 2017 下半年推出的新功能，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ccbea-196">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="ccbea-197">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="ccbea-197">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="ccbea-198">如此一來，當您從 Windows 主機提取映像時，它會提取 Windows variant，而從 Linux 主機提取相同的映像名稱則會提取 Linux variant。</span><span class="sxs-lookup"><span data-stu-id="ccbea-198">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="ccbea-199">選項 B：建立全新的基底映像</span><span class="sxs-lookup"><span data-stu-id="ccbea-199">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="ccbea-200">您可以從頭開始建立您自己的 Docker 基底映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-200">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="ccbea-201">Docker 新手不建議此方案，但如果您想要設定專屬基底映像的特點，您可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="ccbea-201">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ccbea-202">其他資源</span><span class="sxs-lookup"><span data-stu-id="ccbea-202">Additional resources</span></span>

-   <span data-ttu-id="ccbea-203">**多架構 .NET Core 映像**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-203">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="ccbea-204">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="ccbea-204">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="ccbea-205">**建立基底映像**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-205">**Create a base image**.</span></span> <span data-ttu-id="ccbea-206">正式 Docker 文件。</span><span class="sxs-lookup"><span data-stu-id="ccbea-206">Official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="ccbea-207">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="ccbea-207">Step 3.</span></span> <span data-ttu-id="ccbea-208">建立您的自訂 Docker 映像並在其中內嵌您的應用程式或服務</span><span class="sxs-lookup"><span data-stu-id="ccbea-208">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="ccbea-209">您需要為應用程式中的每項服務建立相關的映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-209">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="ccbea-210">如果您的應用程式組成為單一的服務或 Web 應用程式，您只需要單一映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-210">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="ccbea-211">請注意，Visual Studio 會自動為您建立 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-211">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="ccbea-212">只有編輯器/CLI 工作流程需要下列步驟，我們會清楚說明發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="ccbea-212">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="ccbea-213">您身為開發人員，需要在本機上開發和測試，直到完成原始檔控制系統 (例如 GitHub) 的完整功能或變更。</span><span class="sxs-lookup"><span data-stu-id="ccbea-213">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="ccbea-214">這表示，您需要建立 Docker 映像，將容器部署到本機的 Docker 主機 (Windows 或 Linux VM) 並執行、測試及偵錯這些本機容器。</span><span class="sxs-lookup"><span data-stu-id="ccbea-214">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="ccbea-215">若要使用 Docker CLI 和您的 Dockerfile 在本機環境中建立自訂映像，您可以使用 docker build 命令，如圖 5-5 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-215">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="ccbea-216">**圖 5-5**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-216">**Figure 5-5**.</span></span> <span data-ttu-id="ccbea-217">建立自訂的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="ccbea-217">Creating a custom Docker image</span></span>

<span data-ttu-id="ccbea-218">(選擇性) 不是直接從專案資料夾執行 docker build，而是可以執行 dotnet publish 使用所需的 .NET 程式庫和二進位檔先產生可部署資料夾，再使用 docker build 命令。</span><span class="sxs-lookup"><span data-stu-id="ccbea-218">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="ccbea-219">這會以 cesardl/netcore-webapi-microservice-docker:first 名稱建立 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-219">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="ccbea-220">本例中的 :first 是代表特定版本的標籤。</span><span class="sxs-lookup"><span data-stu-id="ccbea-220">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="ccbea-221">您可以為組成 Docker 應用程式所需建立的每個自訂映像重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="ccbea-221">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="ccbea-222">當應用程式組成為多個容器時 (即多容器應用程式)，您也可以使用 docker-compose up --build 命令，使用相關 docker-compose.yml 檔案公開的中繼資料，以單一命令組建所有相關的映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-222">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="ccbea-223">您可以使用 docker images 命令在本機存放庫中尋找現有的映像，如圖 5-6 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-223">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="ccbea-224">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="ccbea-224">**Figure 5-6.**</span></span> <span data-ttu-id="ccbea-225">使用 docker images 命令檢視現有的映像</span><span class="sxs-lookup"><span data-stu-id="ccbea-225">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="ccbea-226">使用 Visual Studio 建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="ccbea-226">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="ccbea-227">當您使用 Visual Studio 建立具有 Docker 支援的專案時，您不用明確建立映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-227">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="ccbea-228">而是在您按下 F5 執行 docker 化的應用程式或服務時，它會為您建立映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-228">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="ccbea-229">此步驟在 Visual Studio 中是自動的，您不會看到它運作，可是知道發生什麼事是很重要的。</span><span class="sxs-lookup"><span data-stu-id="ccbea-229">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="ccbea-230">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="ccbea-230">Step 4.</span></span> <span data-ttu-id="ccbea-231">組建多容器 Docker 應用程式時，在 docker-compose.yml 中定義您的服務</span><span class="sxs-lookup"><span data-stu-id="ccbea-231">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="ccbea-232">[Docker compose.yml](https://docs.docker.com/compose/compose-file/) 檔案可讓您定義一組相關服務，部署為具有部署命令的組成應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccbea-232">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="ccbea-233">若要使用 docker-compose.yml 檔案，您需要使用與下列範例類似的內容，在您的 Main 或根解決方案資料夾中建立檔案：</span><span class="sxs-lookup"><span data-stu-id="ccbea-233">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

<span data-ttu-id="ccbea-234">請注意，此 docker-compose.yml 檔案為簡化的合併版本。</span><span class="sxs-lookup"><span data-stu-id="ccbea-234">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="ccbea-235">它包含每個容器的靜態組態資料 (例如自訂映像的名稱)，這一律會套用，再加上可能相依於部署環境的組態資訊，例如連接字串。</span><span class="sxs-lookup"><span data-stu-id="ccbea-235">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="ccbea-236">在後列各節中，您會了解如何根據環境和執行類型 (偵錯或發行)，將 docker-compose.yml 組態分割成多個 docker-compose 檔案和覆寫值。</span><span class="sxs-lookup"><span data-stu-id="ccbea-236">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="ccbea-237">docker-compose.yml 檔案範例會定義五項服務：webmvc 服務 (Web 應用程式)、兩項微服務 (catalog.api 和 ordering.api)，以及 sql.data，一個以 SQL Server for Linux 為基礎執行為容器的資料來源容器。</span><span class="sxs-lookup"><span data-stu-id="ccbea-237">The docker-compose.yml file example defines five services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="ccbea-238">每項服務都會部署為容器，因此每個都需要 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-238">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="ccbea-239">docker-compose.yml 檔案指定的不只是使用何種容器，還會指定它們個別設定的方式。</span><span class="sxs-lookup"><span data-stu-id="ccbea-239">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="ccbea-240">例如，.yml 檔案中的 webmvc 容器定義：</span><span class="sxs-lookup"><span data-stu-id="ccbea-240">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="ccbea-241">使用預先組建的 eshop/web:latest 映像。</span><span class="sxs-lookup"><span data-stu-id="ccbea-241">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="ccbea-242">不過，您也可以設定映像，讓它組建為 docker-compose 的一部分，附帶以 docker-compose 檔案 build: 區段為基礎的額外組態。</span><span class="sxs-lookup"><span data-stu-id="ccbea-242">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="ccbea-243">初始化兩個環境變數 (CatalogUrl 和 OrderingUrl)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-243">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="ccbea-244">將容器上公開的通訊埠 80 轉送至主機的外部通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="ccbea-244">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="ccbea-245">使用 depends\_on 設定連結 Web 應用程式與目錄和訂購服務。</span><span class="sxs-lookup"><span data-stu-id="ccbea-245">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="ccbea-246">這會導致服務一直等候到這些服務啟動。</span><span class="sxs-lookup"><span data-stu-id="ccbea-246">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="ccbea-247">當我們討論到如何實作微服務和多容器應用程式時，會在後節重新審視 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="ccbea-247">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="ccbea-248">在 Visual Studio 2017 中使用 docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="ccbea-248">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="ccbea-249">當如圖 5-7 所示，當您將 Docker 解決方案支援新增至 Visual Studio 解決方案的服務專案時，Visual Studio 會將 Dockerfile 新增至您的專案，而且會在您附 docker-compose.yml 檔案的解決方案中新增服務區段 (專案)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-249">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="ccbea-250">這是撰寫多容器解決方案的簡單方法。</span><span class="sxs-lookup"><span data-stu-id="ccbea-250">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="ccbea-251">然後您可以開啟 docker-compose.yml 檔案，更新它們增加其他功能。</span><span class="sxs-lookup"><span data-stu-id="ccbea-251">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="ccbea-252">**圖 5-7**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-252">**Figure 5-7**.</span></span> <span data-ttu-id="ccbea-253">以滑鼠右鍵按一下 ASP.NET Core 專案，在 Visual Studio 2017 中新增 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="ccbea-253">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="ccbea-254">在 Visual Studio 中新增 Docker 支援，不僅會將 Dockerfile 新增至您的專案，還會將組態資訊新增至在解決方案層級設定的數個全域 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="ccbea-254">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="ccbea-255">在您將 Docker 支援新增至您的 Visual Studio 解決方案之後，您也會在方案總管中看到包含已新增 docker-compose.yml 檔案的新節點 (在 docker-compose.dcproj 專案檔中)，如圖 5-8 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-255">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="ccbea-256">**圖 5-8**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-256">**Figure 5-8**.</span></span> <span data-ttu-id="ccbea-257">Visual Studio 2017 方案總管中新增的 **docker-compose** 樹狀節點</span><span class="sxs-lookup"><span data-stu-id="ccbea-257">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="ccbea-258">您可以使用 docker-compose up 命令，單用一個 docker-compose.yml 檔案部署多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccbea-258">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="ccbea-259">不過，Visual Studio 會新增它們的群組，方便您根據環境 (開發與生產) 和執行類型 (發行與偵錯) 覆寫值。</span><span class="sxs-lookup"><span data-stu-id="ccbea-259">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="ccbea-260">這項功能會在後列各節中說明。</span><span class="sxs-lookup"><span data-stu-id="ccbea-260">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="ccbea-261">步驟 5：</span><span class="sxs-lookup"><span data-stu-id="ccbea-261">Step 5.</span></span> <span data-ttu-id="ccbea-262">組建並執行您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="ccbea-262">Build and run your Docker application</span></span>

<span data-ttu-id="ccbea-263">如果您的應用程式只有單一容器，您可以將它部署至您的 Docker 主機 (VM 或實體伺服器) 來執行。</span><span class="sxs-lookup"><span data-stu-id="ccbea-263">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="ccbea-264">不過，如果您的應用程式包含多項服務，您可以使用單一 CLI 命令 (docker-compose up) 或使用 Visual Studio 將它部署為組成的應用程式，這樣就會在幕後使用該命令。</span><span class="sxs-lookup"><span data-stu-id="ccbea-264">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="ccbea-265">讓我們看看不同的選項。</span><span class="sxs-lookup"><span data-stu-id="ccbea-265">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="ccbea-266">選項 A：以 Docker CLI 執行單一容器</span><span class="sxs-lookup"><span data-stu-id="ccbea-266">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="ccbea-267">您可以使用 docker run 命令執行 Docker 容器，如圖 5-9 所示：</span><span class="sxs-lookup"><span data-stu-id="ccbea-267">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="ccbea-268">**圖 5-9**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-268">**Figure 5-9**.</span></span> <span data-ttu-id="ccbea-269">使用 docker run 命令執行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="ccbea-269">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="ccbea-270">在本列中，命令會將容器的內部通訊埠 5000 繫結到主機電腦的通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="ccbea-270">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="ccbea-271">這表示主機會接聽通訊埠 80 並轉送至容器的通訊埠 5000。</span><span class="sxs-lookup"><span data-stu-id="ccbea-271">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="ccbea-272">選項 B：執行多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="ccbea-272">Option B: Running a multi-container application</span></span>

<span data-ttu-id="ccbea-273">在大部分的企業案例中，Docker 應用程式會由多項服務組成，這表示您需要執行多容器應用程式，如圖 5-10 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-273">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="ccbea-274">**圖 5-10**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-274">**Figure 5-10**.</span></span> <span data-ttu-id="ccbea-275">部署了 Docker 容器的 VM</span><span class="sxs-lookup"><span data-stu-id="ccbea-275">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="ccbea-276">執行使用 Docker CLI 的多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="ccbea-276">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="ccbea-277">若要執行使用 Docker CLI 的多容器應用程式，您可以執行 docker-compose up 命令。</span><span class="sxs-lookup"><span data-stu-id="ccbea-277">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="ccbea-278">此命令會使用您在解決方案層級的 docker-compose.yml 檔案來部署多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccbea-278">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="ccbea-279">圖 5-11 顯示從您的主要專案目錄執行命令的結果，這會包含 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="ccbea-279">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="ccbea-280">**圖 5-11**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-280">**Figure 5-11**.</span></span> <span data-ttu-id="ccbea-281">執行的 docker-compose up 命令的範例結果</span><span class="sxs-lookup"><span data-stu-id="ccbea-281">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="ccbea-282">執行 docker-compose up 命令之後，應用程式及其相關容器會部署到您的 Docker 主機，如圖 5-10 呈現的 VM 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-282">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="ccbea-283">使用 Visual Studio 執行和偵錯多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="ccbea-283">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="ccbea-284">使用 Visual Studio 2017 執行多容器應用程式不會比較簡單。</span><span class="sxs-lookup"><span data-stu-id="ccbea-284">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="ccbea-285">您不能只執行多容器應用程式，還要能夠設定一般中斷點，直接從 Visual Studio 偵錯它所有的容器。</span><span class="sxs-lookup"><span data-stu-id="ccbea-285">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="ccbea-286">如前所述，每次您將 Docker 解決方案支援新增至解決方案內的專案，就會在全域 (解決方案層級) docker-compose.yml 檔案中設定該專案，這可讓您立即執行或偵錯整個解決方案。</span><span class="sxs-lookup"><span data-stu-id="ccbea-286">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="ccbea-287">Visual Studio 會為每個啟用 Docker 解決方案支援的專案啟動一個容器，並為您執行所有內部步驟 (dotnet publish、docker build 等等)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-287">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="ccbea-288">此處的重點是，如圖 5-12 中所示，Visual Studio 2017 另有處理 F5 按鍵動作的 **Docker** 命令。</span><span class="sxs-lookup"><span data-stu-id="ccbea-288">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="ccbea-289">此選項藉由執行在解決方案層級之 docker-compose.yml 檔案中定義的所有容器，讓您執行或偵錯多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccbea-289">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="ccbea-290">偵錯多容器解決方案的能力，表示您可以設定多個中斷點，不同的專案 (容器) 各一個中斷點；而從 Visual Studio 偵錯時，您會停在不同專案中定義的中斷點，然後在不同的容器上執行。</span><span class="sxs-lookup"><span data-stu-id="ccbea-290">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="ccbea-291">**圖 5-12**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-291">**Figure 5-12**.</span></span> <span data-ttu-id="ccbea-292">在 Visual Studio 2017 中執行多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="ccbea-292">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ccbea-293">其他資源</span><span class="sxs-lookup"><span data-stu-id="ccbea-293">Additional resources</span></span>

-   <span data-ttu-id="ccbea-294">**將 ASP.NET 容器部署至遠端 Docker 主機**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="ccbea-294">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="ccbea-295">測試與部署協調器的注意事項</span><span class="sxs-lookup"><span data-stu-id="ccbea-295">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="ccbea-296">docker-compose up 和 docker run 命令 (在 Visual Studio 中執行和偵錯容器) 適合在開發環境中測試容器。</span><span class="sxs-lookup"><span data-stu-id="ccbea-296">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="ccbea-297">但如果您的目標是 Docker 叢集和協調器，像是 Docker Swarm、Mesosphere DC/OS 或 Kubernetes，就不應該使用這種方法。</span><span class="sxs-lookup"><span data-stu-id="ccbea-297">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="ccbea-298">如果您使用類似 [Docker Swarm 模式](https://docs.docker.com/engine/swarm/)的叢集 (自 Docker CE for Windows 和 Mac 1.12 版起提供)，單一服務就需要使用其他命令部署和測試，例如 [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-298">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="ccbea-299">如果您要部署由數個容器組成的應用程式，要使用 [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) 和 [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) 將組成的應用程式部署為「堆疊」。</span><span class="sxs-lookup"><span data-stu-id="ccbea-299">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="ccbea-300">如需詳細資訊，請參閱 Docker 文件的部落格文章 [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) (實驗性分散式應用程式組合簡介)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-300">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="ccbea-301">在 Docker 網站。</span><span class="sxs-lookup"><span data-stu-id="ccbea-301">on the Docker site.</span></span>

<span data-ttu-id="ccbea-302">若為 [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) 和 [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/)，您也會使用不同的部署命令和指令碼。</span><span class="sxs-lookup"><span data-stu-id="ccbea-302">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="ccbea-303">步驟 6：</span><span class="sxs-lookup"><span data-stu-id="ccbea-303">Step 6.</span></span> <span data-ttu-id="ccbea-304">使用本機的 Docker 主機測試您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="ccbea-304">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="ccbea-305">此步驟會隨應用程式執行的作業而異。</span><span class="sxs-lookup"><span data-stu-id="ccbea-305">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="ccbea-306">在部署為單一容器或服務的簡單 .NET Core Web 應用程式中，您可以開啟 Docker 主機上的瀏覽器，瀏覽至該網站存取服務，如圖 5-13 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-306">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="ccbea-307">(如果 Dockerfile 中的組態對應至主機通訊埠 80 以外的容器，包括 URL 中的主機連接埠。)</span><span class="sxs-lookup"><span data-stu-id="ccbea-307">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="ccbea-308">**圖 5-13**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-308">**Figure 5-13**.</span></span> <span data-ttu-id="ccbea-309">使用 localhost 在本機測試 Docker 應用程式的範例</span><span class="sxs-lookup"><span data-stu-id="ccbea-309">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="ccbea-310">如果 localhost 未指向 Docker 主機 IP (根據預設，當使用 Docker CE 時應該會指向 Docker 主機 IP)，請使用您電腦網路卡的 IP 位址巡覽至您的服務。</span><span class="sxs-lookup"><span data-stu-id="ccbea-310">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="ccbea-311">請注意，瀏覽器中這個 URL 為討論中的特定容器範例使用的是通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="ccbea-311">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="ccbea-312">不過，要求在內部會重新導向至通訊埠 5000，因為它是以 docker run 命令如此部署的，如上一個步驟中所述。</span><span class="sxs-lookup"><span data-stu-id="ccbea-312">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="ccbea-313">您也可以從終端機使用 curl 測試應用程式，如圖 5-14 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-313">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="ccbea-314">在 Windows 的 Docker 安裝中，在您電腦的實際 IP 位址以外，預設的 Docker 主機 IP 一律為 10.0.75.1。</span><span class="sxs-lookup"><span data-stu-id="ccbea-314">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="ccbea-315">**圖 5-14**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-315">**Figure 5-14**.</span></span> <span data-ttu-id="ccbea-316">使用 curl 在本機測試 Docker 應用程式的範例</span><span class="sxs-lookup"><span data-stu-id="ccbea-316">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="ccbea-317">使用 Visual Studio 2017 測試和偵錯容器</span><span class="sxs-lookup"><span data-stu-id="ccbea-317">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="ccbea-318">使用 Visual Studio 2017 執行和偵錯容器時，您可以用和不執行容器時一樣的方式，偵錯 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccbea-318">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="ccbea-319">不使用 Visual Studio 偵錯和測試</span><span class="sxs-lookup"><span data-stu-id="ccbea-319">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="ccbea-320">如果您正在使用編輯器/CLI 方法進行開發，偵錯容器會更困難，而且您會想要產生追蹤來偵錯。</span><span class="sxs-lookup"><span data-stu-id="ccbea-320">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ccbea-321">其他資源</span><span class="sxs-lookup"><span data-stu-id="ccbea-321">Additional resources</span></span>

-   <span data-ttu-id="ccbea-322">**在本機 Docker 容器內偵錯應用程式**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="ccbea-322">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="ccbea-323">**Steve Lasker。使用 Docker 組建、偵錯、部署 ASP.NET Core 應用程式。**</span><span class="sxs-lookup"><span data-stu-id="ccbea-323">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="ccbea-324">影片。</span><span class="sxs-lookup"><span data-stu-id="ccbea-324">Video.</span></span>
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="ccbea-325">使用 Visual Studio 開發容器時的簡化工作流程</span><span class="sxs-lookup"><span data-stu-id="ccbea-325">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="ccbea-326">實際上，使用 Visual Studio 時的工作流程時遠比您使用編輯器/CLI 方法更簡單。</span><span class="sxs-lookup"><span data-stu-id="ccbea-326">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="ccbea-327">Visual Studio 會隱藏或簡化與 Dockerfile 和 docker-compose.yml 檔案有關，為 Docker 所需的大部分步驟，如圖 5-15 所示。</span><span class="sxs-lookup"><span data-stu-id="ccbea-327">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="ccbea-328">**圖 5-15**。</span><span class="sxs-lookup"><span data-stu-id="ccbea-328">**Figure 5-15**.</span></span> <span data-ttu-id="ccbea-329">使用 Visual Studio 開發時的簡化工作流程</span><span class="sxs-lookup"><span data-stu-id="ccbea-329">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="ccbea-330">此外，您只需要執行一次步驟 2 (將 Docker 支援新增至您的專案)。</span><span class="sxs-lookup"><span data-stu-id="ccbea-330">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="ccbea-331">因此，工作流程類似於您使用 .NET 處理任何其他開發時的一般開發工作。</span><span class="sxs-lookup"><span data-stu-id="ccbea-331">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="ccbea-332">您需要知道實際狀況 (映像建置程序、使用哪些基底映像、容器部署等等)，有時也需要編輯 Dockerfile 或 docker-compose.yml 檔案以自訂行為。</span><span class="sxs-lookup"><span data-stu-id="ccbea-332">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="ccbea-333">但使用 Visual Studio 已大幅簡化工作，提高您的產能。</span><span class="sxs-lookup"><span data-stu-id="ccbea-333">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ccbea-334">其他資源</span><span class="sxs-lookup"><span data-stu-id="ccbea-334">Additional resources</span></span>

-   <span data-ttu-id="ccbea-335">**Steve Lasker。利用 Visual Studio 2017 進行 .NET Docker 開發**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="ccbea-335">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="ccbea-336">**Jeffrey T. Fritz。將 .NET Core 應用程式放在具備新版適用於 Visual Studio 之 Docker 工具的容器內**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="ccbea-336">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="ccbea-337">在 DockerFile 中使用 PowerShell 命令來設定 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="ccbea-337">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="ccbea-338">[Windows 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)可讓您將現有的 Windows 應用程式轉換成 Docker 映像，並使用相同的工具將它們部署為 Docker 生態系統的其他部分。</span><span class="sxs-lookup"><span data-stu-id="ccbea-338">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="ccbea-339">您要在 Dockerfile 中執行 PowerShell 命令才能使用 Windows 容器，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ccbea-339">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="ccbea-340">在本例中，我們使用 Windows Server Core 基底映像 (FROM 設定)，並使用 PowerShell 命令 (RUN 設定) 安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="ccbea-340">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="ccbea-341">使用類似的方式，您也可以使用 PowerShell 命令安裝其他元件，例如 ASP.NET 4.x、.NET 4.6 或任何其他 Windows 軟體。</span><span class="sxs-lookup"><span data-stu-id="ccbea-341">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="ccbea-342">例如，Dockerfile 中的下列命令會安裝 ASP.NET 4.5：</span><span class="sxs-lookup"><span data-stu-id="ccbea-342">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="ccbea-343">其他資源</span><span class="sxs-lookup"><span data-stu-id="ccbea-343">Additional resources</span></span>

-   <span data-ttu-id="ccbea-344">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="ccbea-344">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="ccbea-345">從 dockerfiles 執行範例 Powershell 命令以包含 Windows 功能。</span><span class="sxs-lookup"><span data-stu-id="ccbea-345">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="ccbea-346">[上一頁] (index.md) [Next] (../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="ccbea-346">[Previous] (index.md) [Next] (../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>
