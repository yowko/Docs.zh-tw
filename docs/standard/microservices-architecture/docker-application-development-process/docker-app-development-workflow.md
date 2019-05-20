---
title: Docker 應用程式的開發工作流程
description: 了解開發 Docker 應用程式的工作流程詳細資料。 一開始會逐步了解一些用以最佳化 Dockerfile 的詳細資料，最後將取得使用 Visual Studio 時可用的簡化工作流程。
ms.date: 01/07/2019
ms.openlocfilehash: 34d2a90cb5208736b1b414e25ac3e627929f45a0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644482"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="c97ab-104">Docker 應用程式的開發工作流程</span><span class="sxs-lookup"><span data-stu-id="c97ab-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="c97ab-105">應用程式開發生命週期開始於您以開發人員身分使用的電腦，您會在電腦上使用慣用語言來撰寫應用程式的程式碼，並於本機上測試。</span><span class="sxs-lookup"><span data-stu-id="c97ab-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="c97ab-106">使用此工作流程，不論您選擇哪一種語言、架構和平台，一定能開發和測試 Docker 容器，但只能在本機作業。</span><span class="sxs-lookup"><span data-stu-id="c97ab-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="c97ab-107">每個容器 (Docker 映像的執行個體) 包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="c97ab-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="c97ab-108">作業系統選取項目，例如 Linux 發行版本、Windows Nano Server 或 Windows Server Core。</span><span class="sxs-lookup"><span data-stu-id="c97ab-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="c97ab-109">開發期間新增的檔案，例如原始程式碼和應用程式二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c97ab-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="c97ab-110">組態資訊，例如環境設定和相依性。</span><span class="sxs-lookup"><span data-stu-id="c97ab-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="c97ab-111">開發 Docker 容器型應用程式的工作流程</span><span class="sxs-lookup"><span data-stu-id="c97ab-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="c97ab-112">本節描述 Docker 容器型應用程式的「內部迴圈」開發工作流程。</span><span class="sxs-lookup"><span data-stu-id="c97ab-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="c97ab-113">內部迴圈工作流程表示不考慮更廣泛的 DevOps 工作流程 (最多可包含生產環境部署)，只著重於在開發人員電腦上完成的開發工作。</span><span class="sxs-lookup"><span data-stu-id="c97ab-113">The inner-loop workflow means it's not considering the broader DevOps workflow, that can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="c97ab-114">設定環境的初始步驟不包含在內，因為這些步驟只執行一次。</span><span class="sxs-lookup"><span data-stu-id="c97ab-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="c97ab-115">應用程式是由您自己的服務加上額外的程式庫 (相依性) 所組成。</span><span class="sxs-lookup"><span data-stu-id="c97ab-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="c97ab-116">以下是組建 Docker 應用程式時通常會採用的基本步驟，如圖 5-1 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![<span data-ttu-id="c97ab-117">Docker 應用程式的開發程序：1 - 撰寫應用程式的程式碼，2 - 寫入 Dockerfile，3 - 建立定義於 Dockerfile 的映像，4 -(選擇性) 在 docker-compose.yml 檔案中撰寫服務，5 - 執行容器或 docker-compose 應用程式，6 - 測試應用程式或微服務，7 - 推送至存放庫並重複執行。</span><span class="sxs-lookup"><span data-stu-id="c97ab-117">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span> ](./media/image1.png)

<span data-ttu-id="c97ab-118">**圖 5-1。**</span><span class="sxs-lookup"><span data-stu-id="c97ab-118">**Figure 5-1.**</span></span> <span data-ttu-id="c97ab-119">開發 Docker 容器化應用程式的逐步工作流程</span><span class="sxs-lookup"><span data-stu-id="c97ab-119">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="c97ab-120">本節會詳細說明這整個程序，並針對 Visual Studio 環境說明每個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="c97ab-120">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="c97ab-121">當您使用編輯器/CLI 開發方法 (例如 Visual Studio Code 加上 macOS 或 Windows 上的 Docker CLI) 時，您需要知道每一個步驟，通常要比使用 Visual Studio 更詳細。</span><span class="sxs-lookup"><span data-stu-id="c97ab-121">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="c97ab-122">如需在 CLI 環境中操作的詳細資訊，請參閱電子書 [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-122">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="c97ab-123">如果您使用的是 Visual Studio 2017，系統會替您處理其中許多步驟，這將大幅提升您的生產力。</span><span class="sxs-lookup"><span data-stu-id="c97ab-123">When you're using Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="c97ab-124">特別是當您使用 Visual Studio 2017，並以多容器應用程式為目標時。</span><span class="sxs-lookup"><span data-stu-id="c97ab-124">This is especially true when you're using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="c97ab-125">例如，只要按一下滑鼠，Visual Studio 就會將 Dockerfile 和 docker-compose.yml 檔案新增至您的專案，使用您的應用程式組態。</span><span class="sxs-lookup"><span data-stu-id="c97ab-125">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="c97ab-126">當您在 Visual Studio 中執行應用程式時，它會組建 Docker 映像並直接在 Docker 中執行多容器應用程式，甚至可讓您立即偵錯數個容器。</span><span class="sxs-lookup"><span data-stu-id="c97ab-126">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="c97ab-127">這些功能可大幅提高開發速度。</span><span class="sxs-lookup"><span data-stu-id="c97ab-127">These features will boost your development speed.</span></span>

<span data-ttu-id="c97ab-128">不過，Visual Studio 自動化這些步驟並不表示您不需要知道 Docker 在做什麼。</span><span class="sxs-lookup"><span data-stu-id="c97ab-128">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="c97ab-129">因此，下列指引將詳細說明每一個步驟。</span><span class="sxs-lookup"><span data-stu-id="c97ab-129">Therefore, the following guidance details every step.</span></span>

![1 - 撰寫應用程式的程式碼](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="c97ab-131">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="c97ab-131">Step 1.</span></span> <span data-ttu-id="c97ab-132">開始撰寫程式碼，並建立您的初始應用程式或服務比較基準</span><span class="sxs-lookup"><span data-stu-id="c97ab-132">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="c97ab-133">開發 Docker 應用程式類似於不使用 Docker 開發應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="c97ab-133">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="c97ab-134">差別在於，開發 Docker 時，您要在本機環境中部署並測試 Docker 容器內執行的應用程式或服務 (可能是 Docker 的 Linux VM 安裝程式，若使用 Windows 容器則直接使用 Windows)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-134">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="c97ab-135">設定使用 Visual Studio 的本機環境</span><span class="sxs-lookup"><span data-stu-id="c97ab-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="c97ab-136">開始前，請確定您已安裝 [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows，如下列指示所述：</span><span class="sxs-lookup"><span data-stu-id="c97ab-136">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

<span data-ttu-id="c97ab-137">[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/) (開始使用 Docker CE for Windows)</span><span class="sxs-lookup"><span data-stu-id="c97ab-137">[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/)</span></span>

<span data-ttu-id="c97ab-138">此外，您還需要安裝了 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 15.7 版或更新版本，如圖 5-2 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-138">In addition, you need Visual Studio 2017 version 15.7 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![在 Visual Studio 安裝期間選取 [.NET Core 跨平台開發] 工作負載。](./media/image3.png)

<span data-ttu-id="c97ab-140">**圖 5-2**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-140">**Figure 5-2**.</span></span> <span data-ttu-id="c97ab-141">在 Visual Studio 2017 安裝期間選取 [.NET Core 跨平台開發] 工作負載</span><span class="sxs-lookup"><span data-stu-id="c97ab-141">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="c97ab-142">您甚至可以在於您的應用程式中啟用 Docker，並在 Docker 中部署與測試之前，只使用 .NET 開始撰寫應用程式的程式碼 (如果您打算使用容器通常會使用 .NET Core)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-142">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="c97ab-143">不過，建議您盡快開始使用 Docker，因為它會成為實際環境，可以盡快發現任何問題。</span><span class="sxs-lookup"><span data-stu-id="c97ab-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="c97ab-144">我們鼓勵您這麼做，是因為 Visual Studio 和 Docker 合作很容易，您幾乎感覺不到它，最佳範例是從 Visual Studio 偵錯多容器應用程式時。</span><span class="sxs-lookup"><span data-stu-id="c97ab-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c97ab-145">其他資源</span><span class="sxs-lookup"><span data-stu-id="c97ab-145">Additional resources</span></span>

- <span data-ttu-id="c97ab-146">**Get started with Docker CE for Windows (開始使用 Docker CE for Windows)** \\</span><span class="sxs-lookup"><span data-stu-id="c97ab-146">**Get started with Docker CE for Windows** \\</span></span>
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="c97ab-147">**Visual Studio 2017** \\</span><span class="sxs-lookup"><span data-stu-id="c97ab-147">**Visual Studio 2017** \\</span></span>
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![2 - 寫入 Dockerfile](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="c97ab-149">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="c97ab-149">Step 2.</span></span> <span data-ttu-id="c97ab-150">建立與現有 .NET 基底映像有關的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="c97ab-150">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="c97ab-151">每個您想要組建的自訂映像都需要 Dockerfile，每個要部署的容器也需要 Dockerfile，無論您是從 Visual Studio 自動部署或使用 Docker CLI (docker run 和 docker-compose 命令) 手動部署。</span><span class="sxs-lookup"><span data-stu-id="c97ab-151">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="c97ab-152">如果您的應用程式包含單一的自訂服務，您需要單一的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="c97ab-152">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="c97ab-153">如果您的應用程式包含多項服務 (如微服務架構)，每項服務都需要一個 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="c97ab-153">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="c97ab-154">Dockerfile 放在您應用程式或服務的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c97ab-154">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="c97ab-155">它包含告訴 Docker 如何設定及執行容器中應用程式或服務的命令。</span><span class="sxs-lookup"><span data-stu-id="c97ab-155">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="c97ab-156">您可以使用程式碼手動建立 Dockerfile，將它與您的 .NET 相依性一起新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-156">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="c97ab-157">使用 Visual Studio 及其適用於 Docker 的工具，這項工作只需要按幾下滑鼠即可。</span><span class="sxs-lookup"><span data-stu-id="c97ab-157">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="c97ab-158">當您在 Visual Studio 2017 中建立新專案時，有一個選項名為 [Enable Container (Docker) Support] \(啟用容器 (Docker) 支援\)，如圖 5-3 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-158">When you create a new project in Visual Studio 2017, there's an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![在 Visual Studio 2017 中建立新 ASP.NET Core 專案時的 [Enable Docker Support] \(啟用 Docker 支援\) 核取方塊](./media/image5.png)

<span data-ttu-id="c97ab-160">**圖 5-3**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-160">**Figure 5-3**.</span></span> <span data-ttu-id="c97ab-161">在 Visual Studio 2017 中建立新的 ASP.NET Core 專案時啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="c97ab-161">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2017</span></span>

<span data-ttu-id="c97ab-162">您也可以在現有的 ASP.NET Core Web 應用程式專案上啟用 Docker 支援，方法是以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取 [新增] > [Docker 支援]，如圖 5-4 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-162">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![在 Visual Studio 中新增 Docker 支援功能表選項](./media/image6.png)

<span data-ttu-id="c97ab-164">**圖 5-4**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-164">**Figure 5-4**.</span></span> <span data-ttu-id="c97ab-165">在現有的 Visual Studio 2017 專案中啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="c97ab-165">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="c97ab-166">這個動作會將具有所需組態的 *Dockerfile* 新增至專案，且只能在 ASP.NET Core 專案上使用。</span><span class="sxs-lookup"><span data-stu-id="c97ab-166">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="c97ab-167">同樣地，Visual Studio 也可以使用 [新增] > [容器協調器支援] 選項，為整個方案新增 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-167">In a similar fashion, Visual Studio can also add a docker-compose.yml file for the whole solution with the option **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="c97ab-168">在步驟 4 中，我們將更詳細探索這個選項。</span><span class="sxs-lookup"><span data-stu-id="c97ab-168">In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="c97ab-169">使用現有的官方 .NET Docker 映像</span><span class="sxs-lookup"><span data-stu-id="c97ab-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="c97ab-170">您通常會在基底映像的基礎上，為您的容器建置自訂映像，此基底映像可從 [Docker Hub](https://hub.docker.com/) 登錄等官方存放庫取得。</span><span class="sxs-lookup"><span data-stu-id="c97ab-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="c97ab-171">這就是當您在 Visual Studio 中啟用 Docker 支援時，實際發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="c97ab-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="c97ab-172">您的 Dockerfile 會使用現有 `aspnetcore` 映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-172">Your Dockerfile will use an existing `aspnetcore` image.</span></span>

<span data-ttu-id="c97ab-173">前文曾說明您可以使用的 Docker 映像和存放庫，視您選擇的架構和作業系統而定。</span><span class="sxs-lookup"><span data-stu-id="c97ab-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="c97ab-174">例如，如果您想要使用 ASP.NET Core (Linux 或 Windows)，則要使用的映像就是 `mcr.microsoft.com/dotnet/core/aspnet:2.2`。</span><span class="sxs-lookup"><span data-stu-id="c97ab-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="c97ab-175">因此，您只需要指定要為容器使用的基底 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="c97ab-176">將 `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` 新增至您的 Dockerfile 即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="c97ab-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` to your Dockerfile.</span></span> <span data-ttu-id="c97ab-177">Visual Studio 會自動執行此作業，但如打算更新版本，則要更新此值。</span><span class="sxs-lookup"><span data-stu-id="c97ab-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="c97ab-178">使用 Docker Hub 中有版本號碼的官方 .NET 映像存放庫，可確保所有電腦上都能使用相同的語言功能 (包括開發、測試和生產環境)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="c97ab-179">下例示範 ASP.NET Core 容器的範例 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="c97ab-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="c97ab-180">在此情況下，映像是以 2.2 版的官方 ASP.NET Core Docker 映像為基礎 (適用於 Linux 和 Windows 的多架構)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-180">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="c97ab-181">這是 `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` 設定。</span><span class="sxs-lookup"><span data-stu-id="c97ab-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="c97ab-182">(如需這個基底映像的詳細資訊，請參閱 [.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core/)頁面。)在 Dockerfile 中，您也需要指示 Docker 接聽您會在執行階段使用的 TCP 通訊埠 (本例中為通訊埠 80，如 EXPOSE 設定的設定)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="c97ab-183">您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。</span><span class="sxs-lookup"><span data-stu-id="c97ab-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="c97ab-184">例如，ENTRYPOINT 行中有 `["dotnet", "MySingleContainerWebApp.dll"]` 會指示 Docker 執行 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ab-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="c97ab-185">如果您使用 SDK 和 .NET Core CLI (dotnet CLI) 建置及執行 .NET 應用程式，此設定會有所不同。</span><span class="sxs-lookup"><span data-stu-id="c97ab-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="c97ab-186">重點是 ENTRYPOINT 行與其他設定會不一樣，視您選擇的應用程式語言和平台而定。</span><span class="sxs-lookup"><span data-stu-id="c97ab-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c97ab-187">其他資源</span><span class="sxs-lookup"><span data-stu-id="c97ab-187">Additional resources</span></span>

- <span data-ttu-id="c97ab-188">**建置 .NET Core 應用程式的 Docker 映像** \\</span><span class="sxs-lookup"><span data-stu-id="c97ab-188">**Building Docker Images for .NET Core Applications** \\</span></span>
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="c97ab-189">**組建您自己的映像**.</span><span class="sxs-lookup"><span data-stu-id="c97ab-189">**Build your own image**.</span></span> <span data-ttu-id="c97ab-190">在官方 Docker 文件中。\\</span><span class="sxs-lookup"><span data-stu-id="c97ab-190">In the official Docker documentation.\\</span></span>
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="c97ab-191">**Staying up-to-date with .NET Container Images (保持 .NET 容器映像的最新狀態)** \\</span><span class="sxs-lookup"><span data-stu-id="c97ab-191">**Staying up-to-date with .NET Container Images** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="c97ab-192">**Using .NET and Docker Together - DockerCon 2018 Update (搭配使用 .NET 和 Docker - DockerCon 2018 更新)** \\</span><span class="sxs-lookup"><span data-stu-id="c97ab-192">**Using .NET and Docker Together - DockerCon 2018 Update** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="c97ab-193">使用多架構映像存放庫</span><span class="sxs-lookup"><span data-stu-id="c97ab-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="c97ab-194">一個存放庫可以包含多種平台變化，例如 Linux 映像和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="c97ab-195">這項功能可讓像 Microsoft (基底映像建立者) 這樣的廠商建立單一存放庫以涵蓋多個平台 (即 Linux 和 Windows)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="c97ab-196">例如，Docker Hub 登錄提供的 [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/)存放庫，會使用相同的存放庫名稱提供 Linux 和 Windows Nano Server 支援。</span><span class="sxs-lookup"><span data-stu-id="c97ab-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="c97ab-197">如果您指定標籤，如下列案例一樣明確鎖定平台：</span><span class="sxs-lookup"><span data-stu-id="c97ab-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  <span data-ttu-id="c97ab-198">目標：Linux 上的僅限 .NET Core 2.2 執行階段</span><span class="sxs-lookup"><span data-stu-id="c97ab-198">Targets: .NET Core 2.2 runtime-only on Linux</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  <span data-ttu-id="c97ab-199">目標：Windows Nano Server 上的僅限 .NET Core 2.2 執行階段</span><span class="sxs-lookup"><span data-stu-id="c97ab-199">Targets: .NET Core 2.2 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="c97ab-200">但如果您指定相同的映像名稱，甚至是使用相同的標籤，多架構映像 (例如 `aspnetcore` 映像) 將會根據您目前部署的 Docker 主機 OS 使用 Linux 或 Windows 版本，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c97ab-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnetcore` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  <span data-ttu-id="c97ab-201">多架構：Linux 或 Windows Nano Server 上的僅限 .NET Core 2.2 執行階段，視 Docker 主機 OS 而定</span><span class="sxs-lookup"><span data-stu-id="c97ab-201">Multi-arch: .NET Core 2.2 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="c97ab-202">如此一來，當您從 Windows 主機提取映像時，它會提取 Windows variant，而從 Linux 主機提取相同的映像名稱則會提取 Linux variant。</span><span class="sxs-lookup"><span data-stu-id="c97ab-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="c97ab-203">Dockerfile 中的多階段建置</span><span class="sxs-lookup"><span data-stu-id="c97ab-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="c97ab-204">Dockerfile 類似於批次指令碼。</span><span class="sxs-lookup"><span data-stu-id="c97ab-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="c97ab-205">類似於必須從命令列設定電腦時所要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="c97ab-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="c97ab-206">它會從設定初始內容的基底映像開始，就像是啟動檔案系統，都是位於主機 OS 之上。</span><span class="sxs-lookup"><span data-stu-id="c97ab-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="c97ab-207">雖然它不是 OS，但您可以將它想成容器內的 OS。</span><span class="sxs-lookup"><span data-stu-id="c97ab-207">It's not an OS, but you can think of if like "the" OS inside the container.</span></span>

<span data-ttu-id="c97ab-208">執行每個命令列都會在檔案系統上建立新的圖層，其中包含對上一個圖層所做的變更，這些圖層合併之後即會產生檔案系統。</span><span class="sxs-lookup"><span data-stu-id="c97ab-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="c97ab-209">由於每個新圖層都會「置於」上一個圖層之上，且產生的映像大小會隨著每個命令而增加，因此如果必須包含建置和發佈應用程式所需的 SDK 時，映像可能會變得非常大。</span><span class="sxs-lookup"><span data-stu-id="c97ab-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="c97ab-210">此時請考慮多階段建置 (從 Docker 17.05 和更高版本)，以發揮其功效。</span><span class="sxs-lookup"><span data-stu-id="c97ab-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="c97ab-211">其核心概念是，您可以將 Dockerfile 執行程序分成不同階段，其中一個階段是一個初始映像後面接著一或多個命令，而最後一個階段會決定最終映像大小。</span><span class="sxs-lookup"><span data-stu-id="c97ab-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="c97ab-212">簡單來說，多階段建置允許將建立作業分割成不同的「階段」，再組合最終映像，只從中間階段擷取相關目錄。</span><span class="sxs-lookup"><span data-stu-id="c97ab-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="c97ab-213">這項功能的一般使用方式如下：</span><span class="sxs-lookup"><span data-stu-id="c97ab-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="c97ab-214">使用基底 SDK 映像 (大小並不重要)，其中包含建置和發佈應用程式至資料夾所需的所有項目，然後</span><span class="sxs-lookup"><span data-stu-id="c97ab-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="c97ab-215">使用僅限執行階段的小型基底映像，並複製上一個階段中的發佈資料夾，以產生一個小型最終映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="c97ab-216">透過逐行詳細檢閱 Dockerfile 或許是了解多階段的最佳方式，就讓我們將從新增專案的 Docker 支援時由 Visual Studio 建立的初始 Dockerfile 開始，稍後再探討一些最佳化。</span><span class="sxs-lookup"><span data-stu-id="c97ab-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="c97ab-217">初始 Dockerfile 看起來可能像這樣：</span><span class="sxs-lookup"><span data-stu-id="c97ab-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks …
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="c97ab-218">以下逐行詳細說明：</span><span class="sxs-lookup"><span data-stu-id="c97ab-218">And these are the details, line by line:</span></span>

<!-- markdownlint-disable MD029-->
1. <span data-ttu-id="c97ab-219">以僅限執行階段的「小型」基底映像開始一個階段，並將它稱為**基底**以供參考。</span><span class="sxs-lookup"><span data-stu-id="c97ab-219">Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>
2. <span data-ttu-id="c97ab-220">在映像中建立 **/app** 目錄。</span><span class="sxs-lookup"><span data-stu-id="c97ab-220">Create **/app** directory in the image.</span></span>
3. <span data-ttu-id="c97ab-221">公開連接埠 **80**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-221">Expose port **80**.</span></span>
<!-- skip -->
5. <span data-ttu-id="c97ab-222">以用於建置/發佈的「大型」映像開始一個新階段，並將它稱為**建置**以供參考。</span><span class="sxs-lookup"><span data-stu-id="c97ab-222">Begin a new stage with "large" image for building/publishing, call it **build** for reference.</span></span>
6. <span data-ttu-id="c97ab-223">在映像中建立目錄 **/src**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-223">Create directory **/src** in the image.</span></span>
7. <span data-ttu-id="c97ab-224">最多 16 行，複製參考專案 **.csproj** 檔案，以便稍後能夠還原套件。</span><span class="sxs-lookup"><span data-stu-id="c97ab-224">Up to line 16, copy referenced projects **.csproj** files, to be able to restore packages later.</span></span>
<!-- skip -->
17. <span data-ttu-id="c97ab-225">還原 **Catalog.API** 專案和參考專案的套件。</span><span class="sxs-lookup"><span data-stu-id="c97ab-225">Restore packages for the **Catalog.API** project and the referenced projects.</span></span>
18. <span data-ttu-id="c97ab-226">將**方案所有樹狀目錄** (**.dockerignore** 檔案中所包含的檔案/目錄除外) 複製到映像的 **/src** 目錄。</span><span class="sxs-lookup"><span data-stu-id="c97ab-226">Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) from to the **/src** directory in the image.</span></span>
19. <span data-ttu-id="c97ab-227">將目前的資料夾變更為 **Catalog.API** 專案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-227">Change current folder to **Catalog.API** project.</span></span>
20. <span data-ttu-id="c97ab-228">建置專案 (及其他專案相依性) 並輸出至映像的 **/app** 目錄。</span><span class="sxs-lookup"><span data-stu-id="c97ab-228">Build project (and other project dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
22. <span data-ttu-id="c97ab-229">從建置繼續開始一個新階段，並將它稱為**發佈**以供參考。</span><span class="sxs-lookup"><span data-stu-id="c97ab-229">Begin a new stage continuing from build, call it **publish** for reference.</span></span>
23. <span data-ttu-id="c97ab-230">發佈專案 (及相依性) 並輸出至映像的 **/app** 目錄。</span><span class="sxs-lookup"><span data-stu-id="c97ab-230">Publish project (and dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
25. <span data-ttu-id="c97ab-231">從**基底**繼續開始一個新階段，並將它稱為**最終**</span><span class="sxs-lookup"><span data-stu-id="c97ab-231">Begin a new stage continuing from **base** and call it **final**</span></span>
26. <span data-ttu-id="c97ab-232">將目前的目錄變更為 **/app**</span><span class="sxs-lookup"><span data-stu-id="c97ab-232">Change current directory to **/app**</span></span>
27. <span data-ttu-id="c97ab-233">將 **/app** 目錄從**發佈**階段複製到目前的目錄</span><span class="sxs-lookup"><span data-stu-id="c97ab-233">Copy the **/app** directory from stage **publish** to the current directory</span></span>
28. <span data-ttu-id="c97ab-234">定義啟動容器時要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c97ab-234">Define the command to run when the container is started.</span></span>
<!-- markdownlint-enable MD029-->

<span data-ttu-id="c97ab-235">現在讓我們來探索一些可改善整體程序效能的最佳化，以 eShopOnContainers 為例，則表示在 Linux 容器中建置完整方案需要約 22 分鐘或更多的時間。</span><span class="sxs-lookup"><span data-stu-id="c97ab-235">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="c97ab-236">您將利用 Docker 的圖層快取功能，這項功能相當簡單：如果基底映像和命令與先前執行的某些項目相同，則可以直接使用產生的圖層，而不需要執行命令，因此節省一些時間。</span><span class="sxs-lookup"><span data-stu-id="c97ab-236">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="c97ab-237">讓我們將重點放在**建置**階段，第 5-6 行大致相同，但第 7-17 行會因 eShopOnContainers 中的每個服務而異，因此每次都必須執行，不過如果您將第 7-16 行變更為：</span><span class="sxs-lookup"><span data-stu-id="c97ab-237">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```Dockerfile
COPY . .
```

<span data-ttu-id="c97ab-238">則每個服務都會相同，它會複製整個方案並建立較大的圖層，但：</span><span class="sxs-lookup"><span data-stu-id="c97ab-238">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1) <span data-ttu-id="c97ab-239">複製程序只會在第一次執行 (以及因檔案變更而重建時執行)，並針對所有其他服務使用快取</span><span class="sxs-lookup"><span data-stu-id="c97ab-239">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2) <span data-ttu-id="c97ab-240">由於較大的映像出現在中間階段，因此不會影響最終映像大小。</span><span class="sxs-lookup"><span data-stu-id="c97ab-240">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="c97ab-241">下一個重要的最佳化涉及第 17 行所執行的 `restore` 命令，這也會因 eShopOnContainers 的每個服務而異。</span><span class="sxs-lookup"><span data-stu-id="c97ab-241">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="c97ab-242">如果您將該行變更為：</span><span class="sxs-lookup"><span data-stu-id="c97ab-242">If you change that line to just:</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="c97ab-243">它會還原整個方案的套件，但同樣地，它只會執行一次，而不是目前策略的 15 次。</span><span class="sxs-lookup"><span data-stu-id="c97ab-243">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="c97ab-244">不過，資料夾中必須只有單一專案或方案檔，`dotnet restore` 才會執行，因此達成此目的會比較複雜，而解決的方式 (不細究) 如下：</span><span class="sxs-lookup"><span data-stu-id="c97ab-244">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="c97ab-245">將下列各行新增至 **.dockerignore**：</span><span class="sxs-lookup"><span data-stu-id="c97ab-245">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="c97ab-246">`*.sln`，以忽略主要資料夾樹狀目錄中的所有方案檔</span><span class="sxs-lookup"><span data-stu-id="c97ab-246">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="c97ab-247">`!eShopOnContainers-ServicesAndWebApps.sln`，只包含此方案檔。</span><span class="sxs-lookup"><span data-stu-id="c97ab-247">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="c97ab-248">將 `/ignoreprojectextensions:.dcproj` 引數加入 `dotnet restore`，讓它也可忽略 docker-compose 專案，並只還原 eShopOnContainers-ServicesAndWebApps 方案的套件。</span><span class="sxs-lookup"><span data-stu-id="c97ab-248">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="c97ab-249">在最後一個最佳化中，第 20 行剛好是多餘的，因為第 23 行也會建置應用程式且基本上緊接在第 20 行後面，所以是另一個耗時的命令。</span><span class="sxs-lookup"><span data-stu-id="c97ab-249">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="c97ab-250">產生的檔案如下：</span><span class="sxs-lookup"><span data-stu-id="c97ab-250">The resulting file is then:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="c97ab-251">建立全新的基底映像</span><span class="sxs-lookup"><span data-stu-id="c97ab-251">Creating your base image from scratch</span></span>

<span data-ttu-id="c97ab-252">您可以從頭開始建立您自己的 Docker 基底映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-252">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="c97ab-253">Docker 新手不建議此方案，但如果您想要設定專屬基底映像的特點，您可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="c97ab-253">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c97ab-254">其他資源</span><span class="sxs-lookup"><span data-stu-id="c97ab-254">Additional resources</span></span>

- <span data-ttu-id="c97ab-255">**多架構 .NET Core 映像**。\\</span><span class="sxs-lookup"><span data-stu-id="c97ab-255">**Multi-arch .NET Core images**.\\</span></span>
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="c97ab-256">**建立基底映像**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-256">**Create a base image**.</span></span> <span data-ttu-id="c97ab-257">官方 Docker 文件。\\</span><span class="sxs-lookup"><span data-stu-id="c97ab-257">Official Docker documentation.\\</span></span>
  <https://docs.docker.com/develop/develop-images/baseimages/>

![3 - 建立定義於 Dockerfile 的映像](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="c97ab-259">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="c97ab-259">Step 3.</span></span> <span data-ttu-id="c97ab-260">建立您的自訂 Docker 映像並在其中內嵌您的應用程式或服務</span><span class="sxs-lookup"><span data-stu-id="c97ab-260">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="c97ab-261">您需要為應用程式中的每項服務建立相關的映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-261">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="c97ab-262">如果您的應用程式組成為單一的服務或 Web 應用程式，您只需要單一映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-262">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="c97ab-263">請注意，Visual Studio 會自動為您建立 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-263">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="c97ab-264">只有編輯器/CLI 工作流程需要下列步驟，我們會清楚說明發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="c97ab-264">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="c97ab-265">您身為開發人員，需要在本機上開發和測試，直到完成原始檔控制系統 (例如 GitHub) 的完整功能或變更。</span><span class="sxs-lookup"><span data-stu-id="c97ab-265">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="c97ab-266">這表示，您需要建立 Docker 映像，將容器部署到本機的 Docker 主機 (Windows 或 Linux VM) 並執行、測試及偵錯這些本機容器。</span><span class="sxs-lookup"><span data-stu-id="c97ab-266">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="c97ab-267">若要使用 Docker CLI 和您的 Dockerfile 在本機環境中建立自訂映像，您可以使用 docker build 命令，如圖 5-5 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-267">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![建置 Docker 映像的進度畫面](./media/image8.png)

<span data-ttu-id="c97ab-269">**圖 5-5**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-269">**Figure 5-5**.</span></span> <span data-ttu-id="c97ab-270">建立自訂的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="c97ab-270">Creating a custom Docker image</span></span>

<span data-ttu-id="c97ab-271">除了直接從專案資料夾執行 docker build 以外，您可以選擇執行 `dotnet publish`，這樣就能使用所需的 .NET 程式庫及二進位先產生可部署的資料夾，再使用 `docker build` 命令。</span><span class="sxs-lookup"><span data-stu-id="c97ab-271">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="c97ab-272">這會建立一個名為 `cesardl/netcore-webapi-microservice-docker:first` 的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-272">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="c97ab-273">本例中的 :first 是代表特定版本的標籤。</span><span class="sxs-lookup"><span data-stu-id="c97ab-273">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="c97ab-274">您可以為組成 Docker 應用程式所需建立的每個自訂映像重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="c97ab-274">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="c97ab-275">當應用程式是由多個容器組成時 (即多容器應用程式)，您也可以使用 `docker-compose up --build` 命令，使用相關 docker-compose.yml 檔案公開的中繼資料，以單一命令建置所有相關映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-275">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="c97ab-276">您可以使用 docker images 命令在本機存放庫中尋找現有的映像，如圖 5-6 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-276">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![從 docker images 命令列出的映像畫面檢視](./media/image9.png)

<span data-ttu-id="c97ab-278">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="c97ab-278">**Figure 5-6.**</span></span> <span data-ttu-id="c97ab-279">使用 docker images 命令檢視現有的映像</span><span class="sxs-lookup"><span data-stu-id="c97ab-279">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="c97ab-280">使用 Visual Studio 建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="c97ab-280">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="c97ab-281">當您使用 Visual Studio 建立具有 Docker 支援的專案時，不用明確地建立映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-281">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="c97ab-282">反之，當您按 **F5** (或 **Ctrl-F5**) 執行 Docker 化的應用程式或服務時，就會為您建立映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-282">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="c97ab-283">雖然這個步驟會在 Visual Studio 中自動執行，而不會在您眼前發生，但知道背後情況也相當重要。</span><span class="sxs-lookup"><span data-stu-id="c97ab-283">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![4 - (選擇性) 在 docker-compose.yml 檔案中撰寫服務](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="c97ab-285">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="c97ab-285">Step 4.</span></span> <span data-ttu-id="c97ab-286">組建多容器 Docker 應用程式時，在 docker-compose.yml 中定義您的服務</span><span class="sxs-lookup"><span data-stu-id="c97ab-286">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="c97ab-287">[Docker compose.yml](https://docs.docker.com/compose/compose-file/) 檔案可讓您定義一組相關服務，部署為具有部署命令的組成應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ab-287">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="c97ab-288">它也會設定其相依性關聯和執行階段組態。</span><span class="sxs-lookup"><span data-stu-id="c97ab-288">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="c97ab-289">若要使用 docker-compose.yml 檔案，您需要使用與下列範例類似的內容，在您的 Main 或根解決方案資料夾中建立檔案：</span><span class="sxs-lookup"><span data-stu-id="c97ab-289">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

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
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
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

<span data-ttu-id="c97ab-290">此 docker-compose.yml 檔案為簡化的合併版本。</span><span class="sxs-lookup"><span data-stu-id="c97ab-290">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="c97ab-291">它包含每個容器的靜態組態資料 (例如自訂映像的名稱)，這一律是必要的，可能相依於部署環境的組態資訊，例如連接字串。</span><span class="sxs-lookup"><span data-stu-id="c97ab-291">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="c97ab-292">在稍後各節中，您會了解如何根據環境和執行類型 (偵錯或發行)，將 docker-compose.yml 組態分割成多個 docker-compose 檔案和覆寫值。</span><span class="sxs-lookup"><span data-stu-id="c97ab-292">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="c97ab-293">docker-compose.yml 檔案範例會定義四項服務：`webmvc` 服務 (Web 應用程式)、兩項微服務 (`ordering.api` 和 `basket.api`)，以及 `sql.data`，一個以 SQL Server for Linux 為基礎執行為容器的資料來源容器。</span><span class="sxs-lookup"><span data-stu-id="c97ab-293">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering.api` and `basket.api`), and one data source container, `sql.data`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="c97ab-294">每項服務都會部署為容器，因此每個都需要 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-294">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="c97ab-295">docker-compose.yml 檔案指定的不只是使用何種容器，還會指定它們個別設定的方式。</span><span class="sxs-lookup"><span data-stu-id="c97ab-295">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="c97ab-296">例如，.yml 檔案中的 `webmvc` 容器定義：</span><span class="sxs-lookup"><span data-stu-id="c97ab-296">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="c97ab-297">使用預先建置的 `eshop/web:latest` 映像。</span><span class="sxs-lookup"><span data-stu-id="c97ab-297">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="c97ab-298">不過，您也可以設定映像，讓它組建為 docker-compose 的一部分，附帶以 docker-compose 檔案 build: 區段為基礎的額外組態。</span><span class="sxs-lookup"><span data-stu-id="c97ab-298">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="c97ab-299">初始化兩個環境變數 (CatalogUrl 和 OrderingUrl)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-299">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="c97ab-300">將容器上公開的通訊埠 80 轉送至主機的外部通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="c97ab-300">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="c97ab-301">使用 depends_on 設定連結 Web 應用程式與目錄和訂購服務。</span><span class="sxs-lookup"><span data-stu-id="c97ab-301">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="c97ab-302">這會導致服務一直等候到這些服務啟動。</span><span class="sxs-lookup"><span data-stu-id="c97ab-302">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="c97ab-303">當我們討論到如何實作微服務和多容器應用程式時，會在後節重新審視 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-303">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="c97ab-304">在 Visual Studio 2017 中使用 docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="c97ab-304">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="c97ab-305">除了將 Dockerfile 新增至專案 (如前所述)，Visual Studio 2017 (15.8 以後) 也可將 Docker Compose 的協調器支援新增至方案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-305">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="c97ab-306">當您第一次新增容器協調器支援時 (如圖 5-7 所示)，Visual Studio 會為專案建立 Dockerfile，並在包含數個全域 `docker-compose*.yml` 檔案的方案中建立新的 (服務區段) 專案，然後將專案新增至這些檔案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-306">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="c97ab-307">然後您可以開啟 docker-compose.yml 檔案，更新它們增加其他功能。</span><span class="sxs-lookup"><span data-stu-id="c97ab-307">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="c97ab-308">您必須從要包含在 docker-compose.yml 檔案中的每個專案重複此作業。</span><span class="sxs-lookup"><span data-stu-id="c97ab-308">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="c97ab-309">在撰寫本文時，Visual Studio 支援 Docker Compose 與 Service Fabric 協調器。</span><span class="sxs-lookup"><span data-stu-id="c97ab-309">At the time of this writing, Visual Studio supports Docker Compose and Service Fabric orchestrators.</span></span>

![將協調器支援新增至 ASP.NET Core 專案的操作功能表選項](./media/image21.png)

<span data-ttu-id="c97ab-311">**圖 5-7**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-311">**Figure 5-7**.</span></span> <span data-ttu-id="c97ab-312">以滑鼠右鍵按一下 ASP.NET Core 專案，在 Visual Studio 2017 中新增 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="c97ab-312">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="c97ab-313">在您將協調器支援新增至您的 Visual Studio 方案之後，您也會在 [方案總管] 中看到包含已新增 docker-compose.yml 檔案的新節點 (在 `docker-compose.dcproj` 專案檔中)，如圖 5-8 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-313">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![方案總管中的 docker-compose 節點](./media/image11.png)

<span data-ttu-id="c97ab-315">**圖 5-8**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-315">**Figure 5-8**.</span></span> <span data-ttu-id="c97ab-316">Visual Studio 2017 方案總管中新增的 **docker-compose** 樹狀節點</span><span class="sxs-lookup"><span data-stu-id="c97ab-316">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="c97ab-317">您可以透過 `docker-compose up` 命令來使用單一 docker-compose.yml 檔案部署多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ab-317">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="c97ab-318">不過，Visual Studio 會新增它們的群組，方便您根據環境 (開發或生產) 和執行類型 (發行或偵錯) 來覆寫值。</span><span class="sxs-lookup"><span data-stu-id="c97ab-318">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="c97ab-319">這項功能會在後列各節中說明。</span><span class="sxs-lookup"><span data-stu-id="c97ab-319">This capability will be explained in later sections.</span></span>

![5 - 執行容器或組成應用程式](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="c97ab-321">步驟 5：</span><span class="sxs-lookup"><span data-stu-id="c97ab-321">Step 5.</span></span> <span data-ttu-id="c97ab-322">組建並執行您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ab-322">Build and run your Docker application</span></span>

<span data-ttu-id="c97ab-323">如果您的應用程式只有單一容器，您可以將它部署至您的 Docker 主機 (VM 或實體伺服器) 來執行。</span><span class="sxs-lookup"><span data-stu-id="c97ab-323">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="c97ab-324">不過，如果您的應用程式包含多項服務，您可以使用單一 CLI 命令 (docker-compose up) 或使用 Visual Studio 將它部署為組成的應用程式，這樣就會在幕後使用該命令。</span><span class="sxs-lookup"><span data-stu-id="c97ab-324">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="c97ab-325">讓我們看看不同的選項。</span><span class="sxs-lookup"><span data-stu-id="c97ab-325">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="c97ab-326">選項 A：執行單一容器應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ab-326">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="c97ab-327">使用 Docker CLI</span><span class="sxs-lookup"><span data-stu-id="c97ab-327">Using Docker CLI</span></span>

<span data-ttu-id="c97ab-328">您可以使用 `docker run` 命令來執行 Docker 容器，如圖 5-9 所示：</span><span class="sxs-lookup"><span data-stu-id="c97ab-328">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="c97ab-329">上述命令會在每次執行時，從指定的映像建立新的容器執行個體。</span><span class="sxs-lookup"><span data-stu-id="c97ab-329">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="c97ab-330">您可以使用 `--name` 參數來指定容器的名稱，然後使用 `docker start {name}` (或是使用容器識別碼或自動名稱) 來執行現有的容器執行個體。</span><span class="sxs-lookup"><span data-stu-id="c97ab-330">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container id or automatic name) to run an existing container instance.</span></span>

![使用 docker run 命令執行 Docker 容器時的畫面檢視](./media/image13.png)

<span data-ttu-id="c97ab-332">**圖 5-9**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-332">**Figure 5-9**.</span></span> <span data-ttu-id="c97ab-333">使用 docker run 命令執行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="c97ab-333">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="c97ab-334">在本列中，命令會將容器的內部通訊埠 5000 繫結到主機電腦的通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="c97ab-334">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="c97ab-335">這表示主機會接聽通訊埠 80 並轉送至容器的通訊埠 5000。</span><span class="sxs-lookup"><span data-stu-id="c97ab-335">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="c97ab-336">顯示的雜湊是容器識別碼，若未使用 `--name` 選項，也會隨機指派可讀的名稱。</span><span class="sxs-lookup"><span data-stu-id="c97ab-336">The hash shown is the container id and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="c97ab-337">使用 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c97ab-337">Using Visual Studio</span></span>

<span data-ttu-id="c97ab-338">如果您尚未新增容器協調器支援，您也可以按 **Ctrl-F5** 在 Visual Studio 中執行單一容器應用程式；此外，您也可以使用 **F5** 對容器內的應用程式偵錯。</span><span class="sxs-lookup"><span data-stu-id="c97ab-338">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="c97ab-339">容器使用 docker run 於本機上執行。</span><span class="sxs-lookup"><span data-stu-id="c97ab-339">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="c97ab-340">選項 B：執行多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ab-340">Option B: Running a multi-container application</span></span>

<span data-ttu-id="c97ab-341">在大部分的企業案例中，Docker 應用程式會由多項服務組成，這表示您需要執行多容器應用程式，如圖 5-10 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-341">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![具有數個 Docker 容器的 VM](./media/image14.png)

<span data-ttu-id="c97ab-343">**圖 5-10**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-343">**Figure 5-10**.</span></span> <span data-ttu-id="c97ab-344">部署了 Docker 容器的 VM</span><span class="sxs-lookup"><span data-stu-id="c97ab-344">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="c97ab-345">使用 Docker CLI</span><span class="sxs-lookup"><span data-stu-id="c97ab-345">Using Docker CLI</span></span>

<span data-ttu-id="c97ab-346">若要使用 Docker CLI 執行多容器應用程式，請使用 `docker-compose up` 命令。</span><span class="sxs-lookup"><span data-stu-id="c97ab-346">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="c97ab-347">此命令會使用您在方案層級的 **docker-compose.yml** 檔案來部署多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ab-347">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="c97ab-348">圖 5-11 顯示從您主要方案目錄執行命令的結果，這會包含 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-348">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![執行 docker-compose up 命令時的畫面檢視](./media/image15.png)

<span data-ttu-id="c97ab-350">**圖 5-11**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-350">**Figure 5-11**.</span></span> <span data-ttu-id="c97ab-351">執行的 docker-compose up 命令的範例結果</span><span class="sxs-lookup"><span data-stu-id="c97ab-351">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="c97ab-352">在執行 docker-compose up 命令後，應用程式及其相關容器便已部署至您的 Docker 主機，如圖 5-10 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-352">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="c97ab-353">使用 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c97ab-353">Using Visual Studio</span></span>

<span data-ttu-id="c97ab-354">使用 Visual Studio 2017 執行多容器應用程式相當簡單。</span><span class="sxs-lookup"><span data-stu-id="c97ab-354">Running a multi-container application using Visual Studio 2017 can't get any simpler.</span></span> <span data-ttu-id="c97ab-355">您可以像往常一樣按 **Ctrl-F5** 執行，或按 **F5** 偵錯，並將 **docker-compose** 專案設定為啟始專案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-355">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="c97ab-356">Visual Studio 會處理所有必要的設定，因此您可以像往常一樣建立中斷點，並對最後會變成在「遠端伺服器」中執行的獨立處理序偵錯，就是這麼容易。</span><span class="sxs-lookup"><span data-stu-id="c97ab-356">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", just like that.</span></span>

<span data-ttu-id="c97ab-357">如前所述，每次您將 Docker 解決方案支援新增至解決方案內的專案，就會在全域 (解決方案層級) docker-compose.yml 檔案中設定該專案，這可讓您立即執行或偵錯整個解決方案。</span><span class="sxs-lookup"><span data-stu-id="c97ab-357">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="c97ab-358">Visual Studio 會為每個啟用 Docker 解決方案支援的專案啟動一個容器，並為您執行所有內部步驟 (dotnet publish、docker build 等等)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-358">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="c97ab-359">如果想要查看所有繁瑣的工作，請參閱下列檔案：</span><span class="sxs-lookup"><span data-stu-id="c97ab-359">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="c97ab-360">此處的重點是，如圖 5-12 中所示，Visual Studio 2017 另有處理 F5 按鍵動作的 **Docker** 命令。</span><span class="sxs-lookup"><span data-stu-id="c97ab-360">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="c97ab-361">此選項藉由執行在解決方案層級之 docker-compose.yml 檔案中定義的所有容器，讓您執行或偵錯多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ab-361">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="c97ab-362">偵錯多容器解決方案的能力，表示您可以設定多個中斷點，不同的專案 (容器) 各一個中斷點；而從 Visual Studio 偵錯時，您會停在不同專案中定義的中斷點，然後在不同的容器上執行。</span><span class="sxs-lookup"><span data-stu-id="c97ab-362">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![執行 docker-compose 專案的 Visual Studio 偵錯工具列](./media/image16.png)

<span data-ttu-id="c97ab-364">**圖 5-12**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-364">**Figure 5-12**.</span></span> <span data-ttu-id="c97ab-365">在 Visual Studio 2017 中執行多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ab-365">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c97ab-366">其他資源</span><span class="sxs-lookup"><span data-stu-id="c97ab-366">Additional resources</span></span>

- <span data-ttu-id="c97ab-367">**Deploy an ASP.NET container to a remote Docker host (將 ASP.NET 容器部署至遠端 Docker 主機)** \\</span><span class="sxs-lookup"><span data-stu-id="c97ab-367">**Deploy an ASP.NET container to a remote Docker host** \\</span></span>
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="c97ab-368">測試與部署協調器的注意事項</span><span class="sxs-lookup"><span data-stu-id="c97ab-368">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="c97ab-369">docker-compose up 和 docker run 命令 (在 Visual Studio 中執行和偵錯容器) 適合在開發環境中測試容器。</span><span class="sxs-lookup"><span data-stu-id="c97ab-369">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="c97ab-370">但您不應該針對生產環境部署使用這種方法，在此部署中，您應該以 [Kubernetes](https://kubernetes.io/) 或 [Service Fabric](https://azure.microsoft.com/services/service-fabric/) 等協調器為目標。</span><span class="sxs-lookup"><span data-stu-id="c97ab-370">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="c97ab-371">如果您使用 Kubernetes，您必須使用 [Pod](https://kubernetes.io/docs/concepts/workloads/pods/pod/) 來組織容器，並使用[服務](https://kubernetes.io/docs/concepts/services-networking/service/)來為其建立網路。</span><span class="sxs-lookup"><span data-stu-id="c97ab-371">If you're using Kubernetes you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="c97ab-372">您也必須使用[部署](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)來組織 Pod 建立和修改作業。</span><span class="sxs-lookup"><span data-stu-id="c97ab-372">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![6 - 測試應用程式或微服務](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="c97ab-374">步驟 6：</span><span class="sxs-lookup"><span data-stu-id="c97ab-374">Step 6.</span></span> <span data-ttu-id="c97ab-375">使用本機的 Docker 主機測試您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ab-375">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="c97ab-376">此步驟會隨應用程式執行的作業而異。</span><span class="sxs-lookup"><span data-stu-id="c97ab-376">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="c97ab-377">在部署為單一容器或服務的簡單 .NET Core Web 應用程式中，您可以藉由在 Docker 主機上開啟瀏覽器並瀏覽至該網站來存取服務，如圖 5-13 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-377">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="c97ab-378">(如果 Dockerfile 中的組態對應至主機通訊埠 80 以外的容器，包括 URL 中的主機連接埠。)</span><span class="sxs-lookup"><span data-stu-id="c97ab-378">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![API 端點回應的瀏覽器檢視](./media/image18.png)

<span data-ttu-id="c97ab-380">**圖 5-13**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-380">**Figure 5-13**.</span></span> <span data-ttu-id="c97ab-381">使用 localhost 在本機測試 Docker 應用程式的範例</span><span class="sxs-lookup"><span data-stu-id="c97ab-381">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="c97ab-382">如果 localhost 未指向 Docker 主機 IP (根據預設，當使用 Docker CE 時應該會指向 Docker 主機 IP)，請使用您電腦網路卡的 IP 位址來巡覽至您的服務。</span><span class="sxs-lookup"><span data-stu-id="c97ab-382">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="c97ab-383">請注意，瀏覽器中這個 URL 為討論中的特定容器範例使用的是通訊埠 80。</span><span class="sxs-lookup"><span data-stu-id="c97ab-383">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="c97ab-384">不過，要求在內部會重新導向至通訊埠 5000，因為它是以 docker run 命令如此部署的，如上一個步驟中所述。</span><span class="sxs-lookup"><span data-stu-id="c97ab-384">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="c97ab-385">您也可以從終端機使用 curl 測試應用程式，如圖 5-14 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-385">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="c97ab-386">在 Windows 的 Docker 安裝中，在您電腦的實際 IP 位址以外，預設的 Docker 主機 IP 一律為 10.0.75.1。</span><span class="sxs-lookup"><span data-stu-id="c97ab-386">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![使用 curl 的 API 端點回應畫面檢視](./media/image19.png)

<span data-ttu-id="c97ab-388">**圖 5-14**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-388">**Figure 5-14**.</span></span> <span data-ttu-id="c97ab-389">使用 curl 在本機測試 Docker 應用程式的範例</span><span class="sxs-lookup"><span data-stu-id="c97ab-389">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="c97ab-390">使用 Visual Studio 2017 測試和偵錯容器</span><span class="sxs-lookup"><span data-stu-id="c97ab-390">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="c97ab-391">使用 Visual Studio 2017 執行和偵錯容器時，您可以用和不執行容器時一樣的方式，偵錯 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ab-391">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="c97ab-392">不使用 Visual Studio 偵錯和測試</span><span class="sxs-lookup"><span data-stu-id="c97ab-392">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="c97ab-393">如果您正在使用編輯器/CLI 方法進行開發，偵錯容器會更困難，且您會想要藉由產生追蹤來偵錯。</span><span class="sxs-lookup"><span data-stu-id="c97ab-393">If you're developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c97ab-394">其他資源</span><span class="sxs-lookup"><span data-stu-id="c97ab-394">Additional resources</span></span>

- <span data-ttu-id="c97ab-395">**對本機 Docker 容器中的應用程式偵錯** \\</span><span class="sxs-lookup"><span data-stu-id="c97ab-395">**Debugging apps in a local Docker container** \\</span></span>
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="c97ab-396">**Steve Lasker。使用 Docker 組建、偵錯、部署 ASP.NET Core 應用程式。**</span><span class="sxs-lookup"><span data-stu-id="c97ab-396">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="c97ab-397">影片。</span><span class="sxs-lookup"><span data-stu-id="c97ab-397">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="c97ab-398">使用 Visual Studio 開發容器時的簡化工作流程</span><span class="sxs-lookup"><span data-stu-id="c97ab-398">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="c97ab-399">實際上，使用 Visual Studio 時的工作流程時遠比您使用編輯器/CLI 方法更簡單。</span><span class="sxs-lookup"><span data-stu-id="c97ab-399">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="c97ab-400">Visual Studio 會隱藏或簡化與 Dockerfile 和 docker-compose.yml 檔案有關，為 Docker 所需的大部分步驟，如圖 5-15 所示。</span><span class="sxs-lookup"><span data-stu-id="c97ab-400">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![使用 Visual Studio 的簡化容器開發工作流程：1 - 撰寫應用程式的程式碼，2 - 將 Docker 支援新增至專案 (只要一次)，3 - 執行容器或 docker-compose 應用程式，4 - 測試應用程式或微服務，5 - 推送至存放庫並重複執行。](./media/image20.png)

<span data-ttu-id="c97ab-402">**圖 5-15**。</span><span class="sxs-lookup"><span data-stu-id="c97ab-402">**Figure 5-15**.</span></span> <span data-ttu-id="c97ab-403">使用 Visual Studio 開發時的簡化工作流程</span><span class="sxs-lookup"><span data-stu-id="c97ab-403">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="c97ab-404">此外，您只需要執行一次步驟 2 (將 Docker 支援新增至您的專案)。</span><span class="sxs-lookup"><span data-stu-id="c97ab-404">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="c97ab-405">因此，工作流程類似於您使用 .NET 處理任何其他開發時的一般開發工作。</span><span class="sxs-lookup"><span data-stu-id="c97ab-405">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="c97ab-406">您需要知道實際狀況 (映像建置程序、使用哪些基底映像、容器部署等等)，有時也需要編輯 Dockerfile 或 docker-compose.yml 檔案以自訂行為。</span><span class="sxs-lookup"><span data-stu-id="c97ab-406">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="c97ab-407">但使用 Visual Studio 已大幅簡化工作，提高您的產能。</span><span class="sxs-lookup"><span data-stu-id="c97ab-407">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c97ab-408">其他資源</span><span class="sxs-lookup"><span data-stu-id="c97ab-408">Additional resources</span></span>

- <span data-ttu-id="c97ab-409">**Steve Lasker：.NET Docker Development with Visual Studio 2017 (使用 Visual Studio 2017 進行 .NET Docker 開發)** \\</span><span class="sxs-lookup"><span data-stu-id="c97ab-409">**Steve Lasker. .NET Docker Development with Visual Studio 2017** \\</span></span>
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="c97ab-410">在 DockerFile 中使用 PowerShell 命令來設定 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="c97ab-410">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="c97ab-411">[Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/index)可讓您將現有的 Windows 應用程式轉換成 Docker 映像，並使用相同的工具將它們部署為 Docker 生態系統的其他部分。</span><span class="sxs-lookup"><span data-stu-id="c97ab-411">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="c97ab-412">您要在 Dockerfile 中執行 PowerShell 命令才能使用 Windows 容器，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c97ab-412">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="c97ab-413">在本例中，我們使用 Windows Server Core 基底映像 (FROM 設定)，並使用 PowerShell 命令 (RUN 設定) 安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="c97ab-413">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="c97ab-414">使用類似的方式，您也可以使用 PowerShell 命令安裝其他元件，例如 ASP.NET 4.x、.NET 4.6 或任何其他 Windows 軟體。</span><span class="sxs-lookup"><span data-stu-id="c97ab-414">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="c97ab-415">例如，Dockerfile 中的下列命令會安裝 ASP.NET 4.5：</span><span class="sxs-lookup"><span data-stu-id="c97ab-415">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="c97ab-416">其他資源</span><span class="sxs-lookup"><span data-stu-id="c97ab-416">Additional resources</span></span>

- <span data-ttu-id="c97ab-417">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="c97ab-417">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="c97ab-418">要從 Dockerfile 執行以包含 Windows 功能的範例 PowerShell 命令。\\</span><span class="sxs-lookup"><span data-stu-id="c97ab-418">Example PowerShell commands to run from dockerfiles to include Windows features.\\</span></span>
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="c97ab-419">[上一頁](index.md)
>[下一頁](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="c97ab-419">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
