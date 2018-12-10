---
title: Docker 應用程式的開發工作流程
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 應用程式的開發工作流程
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/05/2018
ms.openlocfilehash: bc6b1796ed7b12a04affc521ac2efee515c48ae2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150546"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="da472-103">Docker 應用程式的開發工作流程</span><span class="sxs-lookup"><span data-stu-id="da472-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="da472-104">應用程式開發生命週期開始於每位開發人員的電腦，開發人員在電腦上使用其偏好的語言撰寫應用程式的程式碼，並於本機上測試。</span><span class="sxs-lookup"><span data-stu-id="da472-104">The application development life cycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="da472-105">不論開發人員選擇哪一種語言、架構和平台，只要使用此工作流程，開發人員就一定能開發和測試 Docker 容器，但只能在本機作業。</span><span class="sxs-lookup"><span data-stu-id="da472-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="da472-106">每個容器 (Docker 映像的執行個體) 包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="da472-106">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="da472-107">作業系統選取項目 (例如 Linux 發行版本、Windows Nano Server 或 Windows Server Core)。</span><span class="sxs-lookup"><span data-stu-id="da472-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

- <span data-ttu-id="da472-108">開發人員新增的檔案 (應用程式二進位檔等等)。</span><span class="sxs-lookup"><span data-stu-id="da472-108">Files added by the developer (application binaries, etc.).</span></span>

- <span data-ttu-id="da472-109">組態資訊 (環境設定和相依性)。</span><span class="sxs-lookup"><span data-stu-id="da472-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="da472-110">開發 Docker 容器型應用程式的工作流程</span><span class="sxs-lookup"><span data-stu-id="da472-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="da472-111">本節描述 Docker 容器型應用程式的「內部迴圈」開發工作流程。</span><span class="sxs-lookup"><span data-stu-id="da472-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="da472-112">內部迴圈工作流程表示不考慮更廣泛的 DevOps 工作流程，只著重於在開發人員電腦上完成的開發工作。</span><span class="sxs-lookup"><span data-stu-id="da472-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="da472-113">設定環境的初始步驟不包含在內，因為這些只進行一次。</span><span class="sxs-lookup"><span data-stu-id="da472-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="da472-114">應用程式是由您自己的服務加上額外的程式庫 (相依性) 所組成。</span><span class="sxs-lookup"><span data-stu-id="da472-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="da472-115">以下是組建 Docker 應用程式時通常會採用的基本步驟，如圖 5-1 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![開發 Docker 容器化應用程式的逐步工作流程圖表](./media/image1.png)

<span data-ttu-id="da472-117">**圖 5-1。**</span><span class="sxs-lookup"><span data-stu-id="da472-117">**Figure 5-1.**</span></span> <span data-ttu-id="da472-118">開發 Docker 容器化應用程式的逐步工作流程</span><span class="sxs-lookup"><span data-stu-id="da472-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="da472-119">本指南會詳細說明這整個程序，並針對 Visual Studio 環境說明每個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="da472-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="da472-120">當您使用編輯器/CLI 開發方法 (例如，Visual Studio Code 加上 macOS 或 Windows 上的 Docker CLI) 時，您需要知道每一個步驟，通常要比使用 Visual Studio 更詳細。</span><span class="sxs-lookup"><span data-stu-id="da472-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="da472-121">如需在 CLI 環境中操作的詳細資訊，請參閱電子書 [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/)。</span><span class="sxs-lookup"><span data-stu-id="da472-121">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="da472-122">如果您使用的是 Visual Studio，系統會替您處理其中許多步驟，這將大幅提升您的生產力。</span><span class="sxs-lookup"><span data-stu-id="da472-122">When you're using Visual Studio, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="da472-123">特別是當您使用 Visual Studio 2017，並以多容器應用程式為目標時。</span><span class="sxs-lookup"><span data-stu-id="da472-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="da472-124">舉例來說，只要按一下滑鼠，Visual Studio 就會使用您應用程式的組態，將 *Dockerfile* 及 *docker-compose.yml* 檔案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="da472-124">For instance, with just one mouse click, Visual Studio adds the *Dockerfile* and *docker-compose.yml* files to your projects with the configuration for your application.</span></span> <span data-ttu-id="da472-125">當您在 Visual Studio 中執行應用程式時，其會建置 Docker 映像，並直接在 Docker 中執行多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="da472-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker.</span></span> <span data-ttu-id="da472-126">甚至可讓您同時對多個容器進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="da472-126">It even allows you to debug several containers at once.</span></span> <span data-ttu-id="da472-127">這些功能將大幅提高您的開發速度。</span><span class="sxs-lookup"><span data-stu-id="da472-127">These features boost your development speed.</span></span>

<span data-ttu-id="da472-128">在後續的指引中，我們將解釋 Docker 究竟如何運作。</span><span class="sxs-lookup"><span data-stu-id="da472-128">In the guidance that follows, we explain what's happening "under the covers" with Docker.</span></span>

![步驟 1 - 撰寫您的應用程式圖表](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="da472-130">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="da472-130">Step 1.</span></span> <span data-ttu-id="da472-131">開始撰寫程式碼，並建立您的初始應用程式或服務比較基準</span><span class="sxs-lookup"><span data-stu-id="da472-131">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="da472-132">開發 Docker 應用程式類似於不使用 Docker 開發應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="da472-132">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="da472-133">差別在於，開發 Docker 時，您要在本機環境中部署並測試 Docker 容器內執行的應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="da472-133">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="da472-134">容器可以是 Linux 容器或 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="da472-134">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="da472-135">設定使用 Visual Studio 的本機環境</span><span class="sxs-lookup"><span data-stu-id="da472-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="da472-136">開始前，請確定您已安裝 [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows，如下列指示所述：</span><span class="sxs-lookup"><span data-stu-id="da472-136">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

<span data-ttu-id="da472-137">[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/) (開始使用 Docker CE for Windows)</span><span class="sxs-lookup"><span data-stu-id="da472-137">[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/)</span></span>

<span data-ttu-id="da472-138">此外，您還需要安裝了 **.NET Core 跨平台開發**工作負載的 Visual Studio 2017，如圖 5-2 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-138">In addition, you need Visual Studio 2017 with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="da472-139">**圖 5-2**。</span><span class="sxs-lookup"><span data-stu-id="da472-139">**Figure 5-2**.</span></span> <span data-ttu-id="da472-140">在 Visual Studio 2017 安裝期間選取 [.NET Core and Docker] 工作負載</span><span class="sxs-lookup"><span data-stu-id="da472-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="da472-141">您甚至可以在於您的應用程式中啟用 Docker，並在 Docker 中部署與測試之前，只使用 .NET 開始撰寫應用程式程式碼 (如果您打算使用容器通常會使用 .NET Core)。</span><span class="sxs-lookup"><span data-stu-id="da472-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="da472-142">不過，建議您盡快開始使用 Docker，因為它會成為實際環境，可以盡快發現任何問題。</span><span class="sxs-lookup"><span data-stu-id="da472-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="da472-143">我們建議您這樣做，因為 Visual Studio 能夠輕易與 Docker 搭配運作，幾乎暢行無阻 - 最好的例子就是透過 Visual Studio 對多容器應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="da472-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent — the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="da472-144">其他資源</span><span class="sxs-lookup"><span data-stu-id="da472-144">Additional resources</span></span>

- <span data-ttu-id="da472-145">**Get started with Docker CE for Windows** (開始使用 Docker CE for Windows)</span><span class="sxs-lookup"><span data-stu-id="da472-145">**Get started with Docker CE for Windows**</span></span>

   [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

- <span data-ttu-id="da472-146">**Visual Studio 2017**</span><span class="sxs-lookup"><span data-stu-id="da472-146">**Visual Studio 2017**</span></span>

   [*https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![步驟 2 - 寫入 Dockerfile 圖表](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="da472-148">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="da472-148">Step 2.</span></span> <span data-ttu-id="da472-149">建立與現有 .NET 基底映像有關的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="da472-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="da472-150">每個您想建置的自訂映像都需要 Dockerfile；且不論您是從 Visual Studio 自動部署或使用 Docker CLI (docker run 及 docker-compose 命令) 手動部署，每個要部署的容器也都需要 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="da472-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="da472-151">如果您的應用程式包含單一的自訂服務，您需要單一的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="da472-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="da472-152">如果您的應用程式包含多項服務 (如微服務架構)，每項服務都需要一個 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="da472-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="da472-153">Dockerfile 放在您應用程式或服務的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="da472-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="da472-154">它包含告訴 Docker 如何設定及執行容器中應用程式或服務的命令。</span><span class="sxs-lookup"><span data-stu-id="da472-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="da472-155">您可以使用程式碼手動建立 Dockerfile，將它與您的 .NET 相依性一起新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="da472-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="da472-156">有了 Visual Studio Tools for Docker，這項工作只須按幾下滑鼠即可完成。</span><span class="sxs-lookup"><span data-stu-id="da472-156">With Visual Studio Tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="da472-157">當您在 Visual Studio 2017 中建立新專案時，會有一個名為 [啟用 Docker 支援] 的選項，如圖 5-3 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-157">When you create a new project in Visual Studio 2017, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![在 Visual Studio 2017 中建立新專案時啟用 Docker 支援](./media/image5.png)

<span data-ttu-id="da472-159">**圖 5-3**。</span><span class="sxs-lookup"><span data-stu-id="da472-159">**Figure 5-3**.</span></span> <span data-ttu-id="da472-160">在 Visual Studio 2017 中建立新專案時啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="da472-160">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="da472-161">您也可以在現有的 .NET Core Web 應用程式專案上啟用 Docker 支援，方法是以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [新增] > [Docker 支援]，如圖 5-4 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-161">You can also enable Docker support on an existing .NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![在 Visual Studio 中新增 Docker 支援功能表選項](./media/add-docker-support.png)

<span data-ttu-id="da472-163">**圖 5-4**。</span><span class="sxs-lookup"><span data-stu-id="da472-163">**Figure 5-4**.</span></span> <span data-ttu-id="da472-164">在現有的 Visual Studio 2017 專案中啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="da472-164">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="da472-165">這個動作會將具有所需組態的 *Dockerfile* 新增至專案，而且只能在 .NET Core Web 應用程式專案上使用。</span><span class="sxs-lookup"><span data-stu-id="da472-165">This action adds a *Dockerfile* to the project with the required configuration, and is only available on .NET Core web app projects.</span></span>

<span data-ttu-id="da472-166">若要為整個解決方案新增 *docker-compose.yml* 檔案，請以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [新增] > [容器協調器支援]，如圖 5-5 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-166">To add a *docker-compose.yml* file for the whole solution, right-click on the project in **Solution Explorer** and select **Add** > **Container Orchestrator Support**, as shown in Figure 5-5.</span></span>

![在 Visual Studio 中新增容器協調器支援功能表選項](./media/add-container-orchestrator-support.png)

<span data-ttu-id="da472-168">**圖 5-5**。</span><span class="sxs-lookup"><span data-stu-id="da472-168">**Figure 5-5**.</span></span> <span data-ttu-id="da472-169">將容器協調器支援新增至 Visual Studio 2017 中的現有專案。</span><span class="sxs-lookup"><span data-stu-id="da472-169">Adding container orchestrator support to an existing project in Visual Studio 2017.</span></span>

<span data-ttu-id="da472-170">在下列章節中，我們會說明這些檔案每一個的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="da472-170">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="da472-171">Visual Studio 可以為您執行這項工作，但深入了解 Dockerfile 會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="da472-171">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="da472-172">選項 A：使用現有的官方 .NET Docker 映像建立專案</span><span class="sxs-lookup"><span data-stu-id="da472-172">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="da472-173">您通常會在基底映像的基礎上，為您的容器組建自訂映像，此基底映像可從 [Docker Hub](https://hub.docker.com/) 登錄的官方存放庫制取得。</span><span class="sxs-lookup"><span data-stu-id="da472-173">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="da472-174">這就是當您在 Visual Studio 中啟用 Docker 支援時，實際發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="da472-174">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="da472-175">Dockerfile 使用現有的 aspnetcore 映像。</span><span class="sxs-lookup"><span data-stu-id="da472-175">The Dockerfile uses an existing aspnetcore image.</span></span>

<span data-ttu-id="da472-176">前文曾說明您可以使用的 Docker 映像和存放庫，視您選擇的架構和作業系統而定。</span><span class="sxs-lookup"><span data-stu-id="da472-176">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="da472-177">例如，如果您想要使用 ASP.NET Core (Linux 或 Windows)，則要使用的映像就是 microsoft/aspnetcore:2.0。</span><span class="sxs-lookup"><span data-stu-id="da472-177">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="da472-178">因此，您只需要指定要為容器使用的基底 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="da472-178">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="da472-179">將 FROM microsoft/aspnetcore:2.0 新增至您的 Dockerfile 即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="da472-179">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="da472-180">Visual Studio 會自動執行此作業，但如果您更新該版本，同時也會更新該值。</span><span class="sxs-lookup"><span data-stu-id="da472-180">This is automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="da472-181">使用 Docker Hub 中有版本號碼的官方 .NET 映像存放庫，可確保所有電腦上都能使用相同的語言功能 (包括開發、測試和生產環境)。</span><span class="sxs-lookup"><span data-stu-id="da472-181">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="da472-182">下例示範 ASP.NET Core 容器的範例 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="da472-182">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0

ARG source

WORKDIR /app

EXPOSE 80

COPY ${source:-obj/Docker/publish} .

ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="da472-183">在本例中，容器是以 2.0 版的官方 ASP.NET Core Docker 映像為基礎 (適用於 Linux 和 Windows 的多架構)。</span><span class="sxs-lookup"><span data-stu-id="da472-183">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="da472-184">這是 `FROM microsoft/aspnetcore:2.0` 設定。</span><span class="sxs-lookup"><span data-stu-id="da472-184">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="da472-185">(如需這個基底映像的詳細資訊，請參閱 [ASP.NET Core Docker 映像](https://hub.docker.com/r/microsoft/aspnetcore/)頁面及 [.NET Core Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)頁面。)在 Dockerfile 中，您也需要指示 Docker 接聽您會在執行階段使用的 TCP 通訊埠 (本例中為通訊埠 80，如 EXPOSE 設定的設定)。</span><span class="sxs-lookup"><span data-stu-id="da472-185">(For more information about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="da472-186">您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。</span><span class="sxs-lookup"><span data-stu-id="da472-186">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="da472-187">例如，ENTRYPOINT 行中有 \["dotnet"，"MySingleContainerWebApp.dll"\] 會指示 Docker 執行 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="da472-187">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="da472-188">如果您使用 SDK 和 .NET Core CLI (dotnet CLI) 組建及執行 .NET 應用程式，此項設定會有所不同。</span><span class="sxs-lookup"><span data-stu-id="da472-188">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="da472-189">重點是 ENTRYPOINT 行與其他設定會不一樣，視您選擇的應用程式語言和平台而定。</span><span class="sxs-lookup"><span data-stu-id="da472-189">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="da472-190">其他資源</span><span class="sxs-lookup"><span data-stu-id="da472-190">Additional resources</span></span>

- <span data-ttu-id="da472-191">**建置 .NET Core 應用程式的 Docker 映像**</span><span class="sxs-lookup"><span data-stu-id="da472-191">**Building Docker Images for .NET Core Applications**</span></span>

   [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="da472-192">**組建您自己的映像**.</span><span class="sxs-lookup"><span data-stu-id="da472-192">**Build your own image**.</span></span> <span data-ttu-id="da472-193">在正式 Docker 文件中。</span><span class="sxs-lookup"><span data-stu-id="da472-193">In the official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="da472-194">使用多架構映像存放庫</span><span class="sxs-lookup"><span data-stu-id="da472-194">Using multi-arch image repositories</span></span>

<span data-ttu-id="da472-195">一個存放庫可以包含多種平台變化，例如 Linux 映像和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="da472-195">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="da472-196">這項功能可讓像 Microsoft (基底映像建立者) 這樣的廠商建立單一存放庫以涵蓋多個平台 (即 Linux 和 Windows)。</span><span class="sxs-lookup"><span data-stu-id="da472-196">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="da472-197">例如，Docker Hub 登錄提供的 [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) 存放庫，會使用相同的存放庫名稱提供 Linux 和 Windows Nano Server 支援。</span><span class="sxs-lookup"><span data-stu-id="da472-197">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="da472-198">如果您指定標籤，如下列案例一樣明確鎖定平台：</span><span class="sxs-lookup"><span data-stu-id="da472-198">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- <span data-ttu-id="da472-199">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="da472-199">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

- <span data-ttu-id="da472-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="da472-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="da472-201">但如果您指定相同的映像名稱，甚至是使用相同的標籤，新的多架構映像 (例如支援多架構的 aspnetcore 映像) 將會根據您目前部署的 Docker 主機 OS 使用 Linux 或 Windows 版本，這是 2017 年中以來的新功能，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="da472-201">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image, which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

- <span data-ttu-id="da472-202">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="da472-202">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="da472-203">如此一來，當您從 Windows 主機提取映像時，它會提取 Windows variant，而從 Linux 主機提取相同的映像名稱則會提取 Linux variant。</span><span class="sxs-lookup"><span data-stu-id="da472-203">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="da472-204">選項 B：建立全新的基底映像</span><span class="sxs-lookup"><span data-stu-id="da472-204">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="da472-205">您可以從頭開始建立您自己的 Docker 基底映像。</span><span class="sxs-lookup"><span data-stu-id="da472-205">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="da472-206">Docker 新手不建議此方案，但如果您想要設定專屬基底映像的特點，您可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="da472-206">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="da472-207">其他資源</span><span class="sxs-lookup"><span data-stu-id="da472-207">Additional resources</span></span>

- <span data-ttu-id="da472-208">**多架構 .NET Core 映像**。</span><span class="sxs-lookup"><span data-stu-id="da472-208">**Multi-arch .NET Core images**.</span></span>

   https://github.com/dotnet/announcements/issues/14

- <span data-ttu-id="da472-209">**建立基底映像**。</span><span class="sxs-lookup"><span data-stu-id="da472-209">**Create a base image**.</span></span> <span data-ttu-id="da472-210">正式 Docker 文件。</span><span class="sxs-lookup"><span data-stu-id="da472-210">Official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![步驟 3 - 建立映像圖表](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="da472-212">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="da472-212">Step 3.</span></span> <span data-ttu-id="da472-213">建立您的自訂 Docker 映像並在其中內嵌您的應用程式或服務</span><span class="sxs-lookup"><span data-stu-id="da472-213">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="da472-214">您需要為應用程式中的每項服務建立相關的映像。</span><span class="sxs-lookup"><span data-stu-id="da472-214">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="da472-215">如果您的應用程式組成為單一的服務或 Web 應用程式，您只需要單一映像。</span><span class="sxs-lookup"><span data-stu-id="da472-215">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="da472-216">Docker 映像會自動在 Visual Studio 中替您建置。</span><span class="sxs-lookup"><span data-stu-id="da472-216">The Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="da472-217">只有編輯器/CLI 工作流程需要下列步驟，我們會清楚說明發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="da472-217">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="da472-218">您身為開發人員，需要在本機上開發和測試，直到完成原始檔控制系統 (例如 GitHub) 的完整功能或變更。</span><span class="sxs-lookup"><span data-stu-id="da472-218">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="da472-219">這表示，您需要建立 Docker 映像，將容器部署到本機的 Docker 主機 (Windows 或 Linux VM) 並執行、測試及偵錯這些本機容器。</span><span class="sxs-lookup"><span data-stu-id="da472-219">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="da472-220">若要使用 Docker CLI 及您的 Dockerfile 在本機環境中建立自訂映像，您可以使用 docker build 命令，如圖 5-5 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-220">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![建立自訂的 Docker 映像](./media/image8.png)

<span data-ttu-id="da472-222">**圖 5-5**。</span><span class="sxs-lookup"><span data-stu-id="da472-222">**Figure 5-5**.</span></span> <span data-ttu-id="da472-223">建立自訂的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="da472-223">Creating a custom Docker image</span></span>

<span data-ttu-id="da472-224">除了直接從專案資料夾執行 docker build 以外，您可以選擇執行 dotnet publish，這樣就能使用所需的 .NET 程式庫及二進位先產生可部署的資料夾，再使用 docker build 命令。</span><span class="sxs-lookup"><span data-stu-id="da472-224">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="da472-225">這會建立一個名為 **cesardl/netcore-webapi-microservice-docker:first** 的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="da472-225">This will create a Docker image with the name **cesardl/netcore-webapi-microservice-docker:first**.</span></span> <span data-ttu-id="da472-226">本例中的 :first 是代表特定版本的標籤。</span><span class="sxs-lookup"><span data-stu-id="da472-226">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="da472-227">您可以為組成 Docker 應用程式所需建立的每個自訂映像重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="da472-227">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="da472-228">當應用程式組成為多個容器時 (即多容器應用程式)，您也可以使用 docker-compose up --build 命令，使用相關 docker-compose.yml 檔案公開的中繼資料，以單一命令組建所有相關的映像。</span><span class="sxs-lookup"><span data-stu-id="da472-228">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="da472-229">您可以使用 docker images 命令在本機存放庫中尋找現有的映像，如圖 5-6 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-229">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![使用 docker images 命令檢視現有映像](./media/image9.png)

<span data-ttu-id="da472-231">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="da472-231">**Figure 5-6.**</span></span> <span data-ttu-id="da472-232">使用 docker images 命令檢視現有的映像</span><span class="sxs-lookup"><span data-stu-id="da472-232">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="da472-233">使用 Visual Studio 建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="da472-233">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="da472-234">當您使用 Visual Studio 建立具有 Docker 支援的專案時，不用明確地建立映像。</span><span class="sxs-lookup"><span data-stu-id="da472-234">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="da472-235">反之，當您按 **F5** 執行 Docker 化的應用程式或服務時，就會為您建立映像。</span><span class="sxs-lookup"><span data-stu-id="da472-235">Instead, the image is created for you when you press **F5** to run the dockerized application or service.</span></span> <span data-ttu-id="da472-236">雖然這個步驟會在 Visual Studio 中自動執行，而不會在您眼前發生，但知道背後情況也相當重要。</span><span class="sxs-lookup"><span data-stu-id="da472-236">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![步驟 4 - 定義服務圖表](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="da472-238">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="da472-238">Step 4.</span></span> <span data-ttu-id="da472-239">組建多容器 Docker 應用程式時，在 docker-compose.yml 中定義您的服務</span><span class="sxs-lookup"><span data-stu-id="da472-239">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="da472-240">[Docker compose.yml](https://docs.docker.com/compose/compose-file/) 檔案可讓您定義一組相關服務，部署為具有部署命令的組成應用程式。</span><span class="sxs-lookup"><span data-stu-id="da472-240">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="da472-241">若要使用 docker-compose.yml 檔案，您需要使用與下列範例類似的內容，在您的 Main 或根解決方案資料夾中建立檔案：</span><span class="sxs-lookup"><span data-stu-id="da472-241">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="da472-242">此 docker-compose.yml 檔案為簡化的合併版本。</span><span class="sxs-lookup"><span data-stu-id="da472-242">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="da472-243">它包含每個容器的靜態組態資料 (例如自訂映像的名稱)，這一律會套用，再加上可能相依於部署環境的組態資訊，例如連接字串。</span><span class="sxs-lookup"><span data-stu-id="da472-243">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="da472-244">在後列各節中，您會了解如何根據環境和執行類型 (偵錯或發行)，將 docker-compose.yml 組態分割成多個 docker-compose 檔案和覆寫值。</span><span class="sxs-lookup"><span data-stu-id="da472-244">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="da472-245">docker-compose.yml 檔案範例會定義四項服務：webmvc 服務 (Web 應用程式)、兩項微服務 (catalog.api 和 ordering.api)，以及 sql.data，一個以 SQL Server for Linux 為基礎執行為容器的資料來源容器。</span><span class="sxs-lookup"><span data-stu-id="da472-245">The docker-compose.yml file example defines four services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="da472-246">每項服務都會部署為容器，因此每個都需要 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="da472-246">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="da472-247">docker-compose.yml 檔案指定的不只是使用何種容器，還會指定它們個別設定的方式。</span><span class="sxs-lookup"><span data-stu-id="da472-247">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="da472-248">例如，.yml 檔案中的 webmvc 容器定義：</span><span class="sxs-lookup"><span data-stu-id="da472-248">For instance, the webmvc container definition in the .yml file:</span></span>

- <span data-ttu-id="da472-249">使用預先組建的 eshop/web:latest 映像。</span><span class="sxs-lookup"><span data-stu-id="da472-249">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="da472-250">不過，您也可以設定映像，讓它組建為 docker-compose 的一部分，附帶以 docker-compose 檔案 build: 區段為基礎的額外組態。</span><span class="sxs-lookup"><span data-stu-id="da472-250">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="da472-251">初始化兩個環境變數 (CatalogUrl 和 OrderingUrl)。</span><span class="sxs-lookup"><span data-stu-id="da472-251">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="da472-252">將容器上公開的通訊埠 80 轉送至主機的外部通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="da472-252">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="da472-253">使用 depends\_on 設定連結 Web 應用程式與目錄和訂購服務。</span><span class="sxs-lookup"><span data-stu-id="da472-253">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="da472-254">這會導致服務一直等候到這些服務啟動。</span><span class="sxs-lookup"><span data-stu-id="da472-254">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="da472-255">當我們討論到如何實作微服務和多容器應用程式時，會在後節重新審視 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="da472-255">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="da472-256">在 Visual Studio 2017 中使用 docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="da472-256">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="da472-257">當您將容器協調器支援新增至 Web 應用程式專案時 (如圖 5-7 所示)，Visual Studio 會在包含 docker-compose.yml 檔案的解決方案中新增服務區段 (專案)。</span><span class="sxs-lookup"><span data-stu-id="da472-257">When you add container orchestrator support to a web app project, as shown in Figure 5-7, Visual Studio adds a service section (project) to the solution that contains a docker-compose.yml file.</span></span> <span data-ttu-id="da472-258">這是開始撰寫多容器解決方案的簡單方法。</span><span class="sxs-lookup"><span data-stu-id="da472-258">This is an easy way to start composing a multiple-container solution.</span></span>

![在 Visual Studio 中新增容器協調器支援功能表項目](./media/add-container-orchestrator-support.png)

<span data-ttu-id="da472-260">**圖 5-7**。</span><span class="sxs-lookup"><span data-stu-id="da472-260">**Figure 5-7**.</span></span> <span data-ttu-id="da472-261">以滑鼠右鍵按一下 ASP.NET Core 專案，在 Visual Studio 2017 中新增 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="da472-261">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="da472-262">新增容器協調器支援會將 Dockerfile 新增至您的專案 (如果其尚未存在)。</span><span class="sxs-lookup"><span data-stu-id="da472-262">Adding container orchestrator support adds the Dockerfile to your project (if it doesn't already exist).</span></span> <span data-ttu-id="da472-263">該動作也會將組態資訊新增至解決方案層級的全域 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="da472-263">It also adds configuration information to a global docker-compose.yml file at the solution level.</span></span> <span data-ttu-id="da472-264">您將會在包含 docker-compose.yml 檔案的**方案總管**中看見新的專案節點 (*docker-compose.dcproj* 專案檔)，如圖 5-8 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-264">You'll see a new project node (the *docker-compose.dcproj* project file) in **Solution Explorer** that contains the docker-compose.yml file, as shown in Figure 5-8.</span></span>

![方案總管中的 docker-compose 節點](./media/docker-compose-files.png)

<span data-ttu-id="da472-266">**圖 5-8**。</span><span class="sxs-lookup"><span data-stu-id="da472-266">**Figure 5-8**.</span></span> <span data-ttu-id="da472-267">Visual Studio 2017 方案總管中新增的 **docker-compose** 樹狀節點</span><span class="sxs-lookup"><span data-stu-id="da472-267">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="da472-268">然後您可以開啟 docker-compose.yml 檔案並予以更新，以增加功能。</span><span class="sxs-lookup"><span data-stu-id="da472-268">You can then open the docker-compose.yml file and update it with additional features.</span></span>

<span data-ttu-id="da472-269">您可以透過 `docker-compose up` 命令來使用單一 docker-compose.yml 檔案部署多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="da472-269">You can deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span>

![步驟 5 - 執行應用程式圖表](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="da472-271">步驟 5：</span><span class="sxs-lookup"><span data-stu-id="da472-271">Step 5.</span></span> <span data-ttu-id="da472-272">組建並執行您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="da472-272">Build and run your Docker application</span></span>

<span data-ttu-id="da472-273">如果您的應用程式只有單一容器，您可以將它部署至您的 Docker 主機 (VM 或實體伺服器) 來執行。</span><span class="sxs-lookup"><span data-stu-id="da472-273">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="da472-274">但如果您的應用程式包含多個服務，您可以使用單一 CLI 命令 (docker-compose up) 將其部署為組成應用程式，也可以使用 Visual Studio 來部署，其會在幕後使用該命令。</span><span class="sxs-lookup"><span data-stu-id="da472-274">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="da472-275">讓我們看看不同的選項。</span><span class="sxs-lookup"><span data-stu-id="da472-275">Let’s look at the different options.</span></span>

### <a name="option-a-run-a-single-container-app"></a><span data-ttu-id="da472-276">選項 A：執行單一容器應用程式</span><span class="sxs-lookup"><span data-stu-id="da472-276">Option A: Run a single-container app</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="da472-277">Docker CLI</span><span class="sxs-lookup"><span data-stu-id="da472-277">Docker CLI</span></span>

<span data-ttu-id="da472-278">您可以使用 docker run 命令來執行 Docker 容器，如圖 5-9 所示：</span><span class="sxs-lookup"><span data-stu-id="da472-278">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![使用 docker run 命令執行 Docker 容器](./media/image13.png)

<span data-ttu-id="da472-280">**圖 5-9**。</span><span class="sxs-lookup"><span data-stu-id="da472-280">**Figure 5-9**.</span></span> <span data-ttu-id="da472-281">使用 docker run 命令執行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="da472-281">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="da472-282">在本列中，命令會將容器的內部通訊埠 5000 繫結到主機電腦的通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="da472-282">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="da472-283">這表示主機會接聽通訊埠 80 並轉送至容器的通訊埠 5000。</span><span class="sxs-lookup"><span data-stu-id="da472-283">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="da472-284">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da472-284">Visual Studio</span></span>

<span data-ttu-id="da472-285">如果您尚未新增容器協調器支援，您也可以按 **F5** 來在 Visual Studio 中執行單一容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="da472-285">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **F5**.</span></span> <span data-ttu-id="da472-286">容器使用 docker run 於本機上執行。</span><span class="sxs-lookup"><span data-stu-id="da472-286">The container runs locally using docker run.</span></span>

### <a name="option-b-run-a-multi-container-app"></a><span data-ttu-id="da472-287">選項 B：執行多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="da472-287">Option B: Run a multi-container app</span></span>

<span data-ttu-id="da472-288">在大部分的企業案例中，Docker 應用程式會由多項服務組成，這表示您需要執行多容器應用程式，如圖 5-10 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-288">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![顯示部署了 Docker 容器的 VM 圖表](./media/image14.png)

<span data-ttu-id="da472-290">**圖 5-10**。</span><span class="sxs-lookup"><span data-stu-id="da472-290">**Figure 5-10**.</span></span> <span data-ttu-id="da472-291">部署了 Docker 容器的 VM</span><span class="sxs-lookup"><span data-stu-id="da472-291">VM with Docker containers deployed</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="da472-292">Docker CLI</span><span class="sxs-lookup"><span data-stu-id="da472-292">Docker CLI</span></span>

<span data-ttu-id="da472-293">若要執行使用 Docker CLI 的多容器應用程式，您可以執行 docker-compose up 命令。</span><span class="sxs-lookup"><span data-stu-id="da472-293">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="da472-294">此命令會使用您在解決方案層級的 docker-compose.yml 檔案來部署多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="da472-294">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="da472-295">圖 5-11 顯示從您的主要專案目錄執行命令的結果，這會包含 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="da472-295">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![執行的 docker-compose up 命令的範例結果](./media/image15.png)

<span data-ttu-id="da472-297">**圖 5-11**。</span><span class="sxs-lookup"><span data-stu-id="da472-297">**Figure 5-11**.</span></span> <span data-ttu-id="da472-298">執行的 docker-compose up 命令的範例結果</span><span class="sxs-lookup"><span data-stu-id="da472-298">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="da472-299">在執行 docker-compose up 命令後，應用程式及其相關容器便已部署至您的 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="da472-299">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="da472-300">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da472-300">Visual Studio</span></span>

<span data-ttu-id="da472-301">使用 Visual Studio 2017 執行多容器應用程式非常簡單。</span><span class="sxs-lookup"><span data-stu-id="da472-301">Running a multi-container application using Visual Studio 2017 is simple.</span></span> <span data-ttu-id="da472-302">您不只能執行多容器應用程式，還能藉由設定一般中斷點，直接從 Visual Studio 對其所有容器偵錯。</span><span class="sxs-lookup"><span data-stu-id="da472-302">Not only can you run the multi-container application, but you're able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="da472-303">如前所述，每次您將容器協調器支援新增至解決方案中的專案時，該專案都會在全域 (解決方案層級) docker-compose.yml 檔案中設定，如此可讓您一次執行整個解決方案或對其偵錯。</span><span class="sxs-lookup"><span data-stu-id="da472-303">As mentioned before, each time you add container orchestrator support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="da472-304">Visual Studio 會為每個啟用 Docker 解決方案支援的專案啟動一個容器，並為您執行所有內部步驟 (dotnet publish、docker build 等)。</span><span class="sxs-lookup"><span data-stu-id="da472-304">Visual Studio will start one container for each project that has Docker solution support enabled and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="da472-305">此處的重點是，Visual Studio 2017 中有 **F5** 按鍵動作的額外 **Docker** 命令，如圖 5-12 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-305">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there's an additional **Docker** command for the **F5** key action.</span></span> <span data-ttu-id="da472-306">此選項藉由執行在解決方案層級之 docker-compose.yml 檔案中定義的所有容器，讓您執行或偵錯多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="da472-306">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="da472-307">偵錯多容器解決方案的能力，表示您可以設定多個中斷點，不同的專案 (容器) 各一個中斷點；而從 Visual Studio 偵錯時，您會停在不同專案中定義的中斷點，然後在不同的容器上執行。</span><span class="sxs-lookup"><span data-stu-id="da472-307">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![在 Visual Studio 2017 中執行多容器應用程式](./media/image16.png)

<span data-ttu-id="da472-309">**圖 5-12**。</span><span class="sxs-lookup"><span data-stu-id="da472-309">**Figure 5-12**.</span></span> <span data-ttu-id="da472-310">在 Visual Studio 2017 中執行多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="da472-310">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="da472-311">其他資源</span><span class="sxs-lookup"><span data-stu-id="da472-311">Additional resources</span></span>

-  <span data-ttu-id="da472-312">**將 ASP.NET 容器部署至遠端 Docker 主機**</span><span class="sxs-lookup"><span data-stu-id="da472-312">**Deploy an ASP.NET container to a remote Docker host**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="da472-313">測試與部署協調器的注意事項</span><span class="sxs-lookup"><span data-stu-id="da472-313">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="da472-314">Docker-compose up 及 docker run 命令 (或在 Visual Studio 中執行容器及對其偵錯) 適用於在您的開發環境中測試容器。</span><span class="sxs-lookup"><span data-stu-id="da472-314">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="da472-315">但如果您的目標是 Docker 叢集和協調器，像是 Docker Swarm、Mesosphere DC/OS 或 Kubernetes，就不應該使用這種方法。</span><span class="sxs-lookup"><span data-stu-id="da472-315">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="da472-316">如果您使用類似 [Docker Swarm 模式](https://docs.docker.com/engine/swarm/)的叢集 (自 Docker CE for Windows 和 Mac 1.12 版起提供)，單一服務就需要使用其他命令部署和測試，例如 [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/)。</span><span class="sxs-lookup"><span data-stu-id="da472-316">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="da472-317">如果您要部署由數個容器組成的應用程式，要使用 [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) 和 [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) 將組成的應用程式部署為「堆疊」。</span><span class="sxs-lookup"><span data-stu-id="da472-317">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="da472-318">如需詳細資訊，請參閱 Docker 文件的部落格文章 [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) (實驗性分散式應用程式組合簡介)。</span><span class="sxs-lookup"><span data-stu-id="da472-318">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="da472-319">在 Docker 網站。</span><span class="sxs-lookup"><span data-stu-id="da472-319">on the Docker site.</span></span>

<span data-ttu-id="da472-320">若為 [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) 和 [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/)，您也會使用不同的部署命令和指令碼。</span><span class="sxs-lookup"><span data-stu-id="da472-320">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![步驟 6 圖表](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="da472-322">步驟 6：</span><span class="sxs-lookup"><span data-stu-id="da472-322">Step 6.</span></span> <span data-ttu-id="da472-323">使用本機的 Docker 主機測試您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="da472-323">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="da472-324">此步驟會隨應用程式執行的作業而異。</span><span class="sxs-lookup"><span data-stu-id="da472-324">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="da472-325">在部署為單一容器或服務的簡單 .NET Core Web 應用程式中，您可以藉由在 Docker 主機上開啟瀏覽器並瀏覽至該網站來存取服務，如圖 5-13 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-325">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="da472-326">(如果 Dockerfile 中的組態對應至主機通訊埠 80 以外的容器，包括 URL 中的主機連接埠。)</span><span class="sxs-lookup"><span data-stu-id="da472-326">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![使用 localhost 在本機測試 Docker 應用程式的範例](./media/image18.png)

<span data-ttu-id="da472-328">**圖 5-13**。</span><span class="sxs-lookup"><span data-stu-id="da472-328">**Figure 5-13**.</span></span> <span data-ttu-id="da472-329">使用 localhost 在本機測試 Docker 應用程式的範例</span><span class="sxs-lookup"><span data-stu-id="da472-329">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="da472-330">如果 localhost 未指向 Docker 主機 IP (根據預設，當使用 Docker CE 時應該會指向 Docker 主機 IP)，請使用您電腦網路卡的 IP 位址巡覽至您的服務。</span><span class="sxs-lookup"><span data-stu-id="da472-330">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="da472-331">此瀏覽器中的 URL 針對討論中的特定容器範例使用連接埠 80。</span><span class="sxs-lookup"><span data-stu-id="da472-331">This URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="da472-332">不過，要求在內部會重新導向至通訊埠 5000，因為它是以 docker run 命令如此部署的，如上一個步驟中所述。</span><span class="sxs-lookup"><span data-stu-id="da472-332">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="da472-333">您也可以從終端機使用 curl 測試應用程式，如圖 5-14 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-333">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="da472-334">在 Windows 的 Docker 安裝中，在您電腦的實際 IP 位址以外，預設的 Docker 主機 IP 一律為 10.0.75.1。</span><span class="sxs-lookup"><span data-stu-id="da472-334">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![使用 curl 在本機測試 Docker 應用程式的範例](./media/image19.png)

<span data-ttu-id="da472-336">**圖 5-14**。</span><span class="sxs-lookup"><span data-stu-id="da472-336">**Figure 5-14**.</span></span> <span data-ttu-id="da472-337">使用 curl 在本機測試 Docker 應用程式的範例</span><span class="sxs-lookup"><span data-stu-id="da472-337">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="da472-338">使用 Visual Studio 2017 測試和偵錯容器</span><span class="sxs-lookup"><span data-stu-id="da472-338">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="da472-339">使用 Visual Studio 2017 執行和偵錯容器時，您可以用和不執行容器時一樣的方式，偵錯 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="da472-339">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="da472-340">不使用 Visual Studio 偵錯和測試</span><span class="sxs-lookup"><span data-stu-id="da472-340">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="da472-341">如果您正在使用編輯器/CLI 方法進行開發，偵錯容器會更困難，而且您會想要產生追蹤來偵錯。</span><span class="sxs-lookup"><span data-stu-id="da472-341">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="da472-342">其他資源</span><span class="sxs-lookup"><span data-stu-id="da472-342">Additional resources</span></span>

- <span data-ttu-id="da472-343">**對本機 Docker 容器中的應用程式偵錯**</span><span class="sxs-lookup"><span data-stu-id="da472-343">**Debugging apps in a local Docker container**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- <span data-ttu-id="da472-344">**Steve Lasker。使用 Docker 組建、偵錯、部署 ASP.NET Core 應用程式。**</span><span class="sxs-lookup"><span data-stu-id="da472-344">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="da472-345">影片。</span><span class="sxs-lookup"><span data-stu-id="da472-345">Video.</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="da472-346">使用 Visual Studio 開發容器時的簡化工作流程</span><span class="sxs-lookup"><span data-stu-id="da472-346">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="da472-347">實際上，使用 Visual Studio 時的工作流程時遠比您使用編輯器/CLI 方法更簡單。</span><span class="sxs-lookup"><span data-stu-id="da472-347">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="da472-348">Visual Studio 會隱藏或簡化與 Dockerfile 和 docker-compose.yml 檔案有關，為 Docker 所需的大部分步驟，如圖 5-15 所示。</span><span class="sxs-lookup"><span data-stu-id="da472-348">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![使用 Visual Studio 開發時的簡化工作流程](./media/image20.png)

<span data-ttu-id="da472-350">**圖 5-15**。</span><span class="sxs-lookup"><span data-stu-id="da472-350">**Figure 5-15**.</span></span> <span data-ttu-id="da472-351">使用 Visual Studio 開發時的簡化工作流程</span><span class="sxs-lookup"><span data-stu-id="da472-351">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="da472-352">此外，您只需要執行一次步驟 2 (將 Docker 支援新增至您的專案)。</span><span class="sxs-lookup"><span data-stu-id="da472-352">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="da472-353">因此，工作流程類似於您使用 .NET 處理任何其他開發時的一般開發工作。</span><span class="sxs-lookup"><span data-stu-id="da472-353">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="da472-354">您需要知道實際狀況 (映像建置程序、使用哪些基底映像、容器部署等等)，有時也需要編輯 Dockerfile 或 docker-compose.yml 檔案以自訂行為。</span><span class="sxs-lookup"><span data-stu-id="da472-354">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="da472-355">但使用 Visual Studio 已大幅簡化工作，提高您的產能。</span><span class="sxs-lookup"><span data-stu-id="da472-355">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="da472-356">其他資源</span><span class="sxs-lookup"><span data-stu-id="da472-356">Additional resources</span></span>

- <span data-ttu-id="da472-357">**Steve Lasker。使用Visual Studio 2017 進行.NET Docker 開發**</span><span class="sxs-lookup"><span data-stu-id="da472-357">**Steve Lasker. .NET Docker Development with Visual Studio 2017**</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

- <span data-ttu-id="da472-358">**Jeffrey T. Fritz。使用新的 Docker Tools for Visual Studio 將 .NET Core 應用程式放入容器**</span><span class="sxs-lookup"><span data-stu-id="da472-358">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**</span></span>

   [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="da472-359">在 DockerFile 中使用 PowerShell 命令來設定 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="da472-359">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="da472-360">[Windows 容器](/virtualization/windowscontainers/about/)可讓您將現有的 Windows 應用程式轉換成 Docker 映像，並使用相同的工具將它們部署為 Docker 生態系統的其他部分。</span><span class="sxs-lookup"><span data-stu-id="da472-360">[Windows Containers](/virtualization/windowscontainers/about/) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="da472-361">您要在 Dockerfile 中執行 PowerShell 命令才能使用 Windows 容器，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="da472-361">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore

LABEL Description="IIS" Vendor="Microsoft" Version="10"

RUN powershell -Command Add-WindowsFeature Web-Server

CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="da472-362">在本例中，我們使用 Windows Server Core 基底映像 (FROM 設定)，並使用 PowerShell 命令 (RUN 設定) 安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="da472-362">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="da472-363">使用類似的方式，您也可以使用 PowerShell 命令安裝其他元件，例如 ASP.NET 4.x、.NET 4.6 或任何其他 Windows 軟體。</span><span class="sxs-lookup"><span data-stu-id="da472-363">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="da472-364">例如，Dockerfile 中的下列命令會安裝 ASP.NET 4.5：</span><span class="sxs-lookup"><span data-stu-id="da472-364">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="da472-365">其他資源</span><span class="sxs-lookup"><span data-stu-id="da472-365">Additional resources</span></span>

- <span data-ttu-id="da472-366">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="da472-366">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="da472-367">從 dockerfiles 執行範例 Powershell 命令以包含 Windows 功能。</span><span class="sxs-lookup"><span data-stu-id="da472-367">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>

   [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
><span data-ttu-id="da472-368">[上一頁](index.md)
>[下一頁](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="da472-368">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
