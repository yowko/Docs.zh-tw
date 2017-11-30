---
title: "Docker 應用程式的開發工作流程"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Docker 應用程式的開發工作流程"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5a53aee4261a5a0bfc25b3520c50cf505b84f287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="95c1a-104">Docker 應用程式的開發工作流程</span><span class="sxs-lookup"><span data-stu-id="95c1a-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="95c1a-105">應用程式開發週期開始執行每個開發人員的電腦，其中代碼使用其偏好的語言的應用程式開發人員，並在本機測試它。</span><span class="sxs-lookup"><span data-stu-id="95c1a-105">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="95c1a-106">不論哪一個語言、 架構和開發人員選擇，此工作流程中，平台開發人員是一律開發和測試 Docker 容器，但是，在本機。</span><span class="sxs-lookup"><span data-stu-id="95c1a-106">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="95c1a-107">每個容器 （Docker 映像的執行個體） 包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="95c1a-107">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="95c1a-108">作業系統選擇 （例如 Linux 散發套件、 Windows Nano Server 或 Windows Server Core）。</span><span class="sxs-lookup"><span data-stu-id="95c1a-108">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="95c1a-109">開發人員 （應用程式二進位檔等等） 所加入的檔案。</span><span class="sxs-lookup"><span data-stu-id="95c1a-109">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="95c1a-110">（環境設定和相依性） 的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="95c1a-110">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="95c1a-111">工作流程開發 Docker 容器為基礎的應用程式</span><span class="sxs-lookup"><span data-stu-id="95c1a-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="95c1a-112">本章節描述*內部迴圈*Docker 容器基礎的應用程式的開發工作流程。</span><span class="sxs-lookup"><span data-stu-id="95c1a-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="95c1a-113">內部迴圈的工作流程表示它不考慮到更廣泛的 DevOps 工作流程，並只著重於開發人員的電腦上完成的開發工作。</span><span class="sxs-lookup"><span data-stu-id="95c1a-113">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="95c1a-114">設定環境的初始步驟不包含在內，因為這些只進行一次。</span><span class="sxs-lookup"><span data-stu-id="95c1a-114">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="95c1a-115">應用程式是由您的服務，再加上額外的程式庫 （相依性） 所組成。</span><span class="sxs-lookup"><span data-stu-id="95c1a-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="95c1a-116">以下是您通常會採用建置 Docker 應用程式的說明圖 5-1 的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="95c1a-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="95c1a-117">**圖 5-1。**</span><span class="sxs-lookup"><span data-stu-id="95c1a-117">**Figure 5-1.**</span></span> <span data-ttu-id="95c1a-118">供開發 Docker 容器化應用程式的逐步工作流程</span><span class="sxs-lookup"><span data-stu-id="95c1a-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="95c1a-119">在本指南中，這整個程序中有詳細說明，每個主要步驟，說明把焦點放在 Visual Studio 環境。</span><span class="sxs-lookup"><span data-stu-id="95c1a-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="95c1a-120">當使用編輯器/CLI 開發方法 （例如，Visual Studio Code 加上 macOS 上的 Docker CLI 或 Windows） 時，您需要知道每個步驟中，通常比使用 Visual Studio 的更多詳細資料中。</span><span class="sxs-lookup"><span data-stu-id="95c1a-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="95c1a-121">如需 CLI 環境中工作的詳細資訊，請參閱電子書[與 Microsoft 平台和工具的 Docker 容器化應用程式生命週期](http://aka.ms/dockerlifecycleebook/)。</span><span class="sxs-lookup"><span data-stu-id="95c1a-121">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="95c1a-122">當您使用 Visual Studio 2015 或 Visual Studio 2017 時，許多個步驟會為您處理，這會大幅增加產能。</span><span class="sxs-lookup"><span data-stu-id="95c1a-122">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="95c1a-123">當您使用 Visual Studio 2017，而目標多個容器應用程式，這是特別有用。</span><span class="sxs-lookup"><span data-stu-id="95c1a-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="95c1a-124">比方說，只在一個滑鼠按一下 Visual Studio 將 Dockerfile 並 docker compose.yml 檔案加入您的專案與您的應用程式的組態。</span><span class="sxs-lookup"><span data-stu-id="95c1a-124">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="95c1a-125">當您在 Visual Studio 中執行應用程式時，建立 Docker 映像和直接在 Docker; 中執行多個容器應用程式即使可讓您一次偵錯數個容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="95c1a-126">這些功能可大幅提高開發速度。</span><span class="sxs-lookup"><span data-stu-id="95c1a-126">These features will boost your development speed.</span></span>

<span data-ttu-id="95c1a-127">不過，因為 Visual Studio 會自動執行這些步驟並不表示您不需要知道發生什麼事使用 Docker 在下方。</span><span class="sxs-lookup"><span data-stu-id="95c1a-127">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="95c1a-128">因此，會遵循的指導方針，在我們詳細說明每個步驟。</span><span class="sxs-lookup"><span data-stu-id="95c1a-128">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="95c1a-129">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="95c1a-129">Step 1.</span></span> <span data-ttu-id="95c1a-130">開始撰寫程式碼，並建立您的初始應用程式或服務比較基準</span><span class="sxs-lookup"><span data-stu-id="95c1a-130">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="95c1a-131">開發 Docker 應用程式是您開發應用程式沒有 Docker 的方式類似。</span><span class="sxs-lookup"><span data-stu-id="95c1a-131">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="95c1a-132">差別在於，在開發 Docker 時，會在部署並測試您的應用程式或服務在本機環境中的 Docker 容器內執行。</span><span class="sxs-lookup"><span data-stu-id="95c1a-132">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="95c1a-133">容器可以 Linux 容器或 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-133">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="95c1a-134">設定 Visual Studio 中的本機環境</span><span class="sxs-lookup"><span data-stu-id="95c1a-134">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="95c1a-135">若要開始，請確定您有[Docker Community Edition (CE)](https://www.docker.com/community-edition)適用於 Windows 的安裝，在下列指示中所述：</span><span class="sxs-lookup"><span data-stu-id="95c1a-135">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="95c1a-136">開始使用 Docker CE for Windows</span><span class="sxs-lookup"><span data-stu-id="95c1a-136">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="95c1a-137">此外，您必須安裝 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="95c1a-137">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="95c1a-138">這是慣用透過 Visual Studio 2015 與 Visual Studio Tools for Docker 增益集，因為 Visual Studio 2017 具有較進階的 Docker，像是支援偵錯容器的支援。</span><span class="sxs-lookup"><span data-stu-id="95c1a-138">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="95c1a-139">Visual Studio 2017 包含對 Docker 的工具，如果您選取**.NET Core 和 Docker**在安裝期間，如圖 5-2 所示的工作負載。</span><span class="sxs-lookup"><span data-stu-id="95c1a-139">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="95c1a-140">**圖 5-2**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-140">**Figure 5-2**.</span></span> <span data-ttu-id="95c1a-141">選取**.NET Core 和 Docker**在 Visual Studio 2017 安裝期間的工作負載</span><span class="sxs-lookup"><span data-stu-id="95c1a-141">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="95c1a-142">您可以開始撰寫程式碼中 （通常是在.NET Core 如果您打算使用容器) 的一般.NET 應用程式之前在您的應用程式中啟用 Docker 並部署與測試在 Docker 中。</span><span class="sxs-lookup"><span data-stu-id="95c1a-142">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="95c1a-143">不過，建議您開始使用 Docker 儘速，因為它即是對真實環境，而且可以儘速發現任何問題。</span><span class="sxs-lookup"><span data-stu-id="95c1a-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="95c1a-144">這因為 Visual Studio 會很容易使用，它幾乎感覺透明 Docker 我們鼓勵 — 從 Visual Studio 的多個容器應用程式進行偵錯時的最佳範例。</span><span class="sxs-lookup"><span data-stu-id="95c1a-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="95c1a-145">其他資源</span><span class="sxs-lookup"><span data-stu-id="95c1a-145">Additional resources</span></span>

-   <span data-ttu-id="95c1a-146">**開始使用 Docker CE for Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="95c1a-146">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="95c1a-147">**Visual Studio 2017**
    [*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)</span><span class="sxs-lookup"><span data-stu-id="95c1a-147">**Visual Studio 2017**
[*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="95c1a-148">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="95c1a-148">Step 2.</span></span> <span data-ttu-id="95c1a-149">建立 Dockerfile，與現有.NET 基底映像</span><span class="sxs-lookup"><span data-stu-id="95c1a-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="95c1a-150">您想要建置; 每個自訂映像所需 Dockerfile。您也需要針對每個容器 Dockerfile 供部署，是否自動部署從 Visual Studio 或以手動方式使用 Docker CLI (執行 docker 和 docker-撰寫命令)。</span><span class="sxs-lookup"><span data-stu-id="95c1a-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="95c1a-151">如果您的應用程式包含單一的自訂服務，您需要單一 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="95c1a-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="95c1a-152">如果您的應用程式包含多個服務 （如同 microservices 架構），您需要一個 Dockerfile 每個服務。</span><span class="sxs-lookup"><span data-stu-id="95c1a-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="95c1a-153">Dockerfile 被放在應用程式或服務的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="95c1a-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="95c1a-154">它包含告訴 Docker 如何設定及執行應用程式或服務的容器中的命令。</span><span class="sxs-lookup"><span data-stu-id="95c1a-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="95c1a-155">您可以手動在程式碼中建立了 Dockerfile，並將它加入至您的專案中，您的.NET 相依性。</span><span class="sxs-lookup"><span data-stu-id="95c1a-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="95c1a-156">使用 Visual Studio 和其 tools for Docker，這項工作需要只按幾下滑鼠。</span><span class="sxs-lookup"><span data-stu-id="95c1a-156">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="95c1a-157">當您在 Visual Studio 2017 中建立新的專案時，名為一個選項是**啟用容器 (Docker) 支援**，如圖 5-3 所示。</span><span class="sxs-lookup"><span data-stu-id="95c1a-157">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="95c1a-158">**圖 5-3**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-158">**Figure 5-3**.</span></span> <span data-ttu-id="95c1a-159">在 Visual Studio 2017 中建立新的專案時，啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="95c1a-159">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="95c1a-160">您也可以以滑鼠右鍵按一下您的專案檔，Visual Studio 中選取的選項來啟用新的或現有的專案上的 Docker 支援**新增 Docker 專案支援**，如圖 5-4 所示。</span><span class="sxs-lookup"><span data-stu-id="95c1a-160">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="95c1a-161">**圖 5-4**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-161">**Figure 5-4**.</span></span> <span data-ttu-id="95c1a-162">啟用在現有的 Visual Studio 2017 專案的 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="95c1a-162">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="95c1a-163">此動作 （例如 ASP.NET Web 應用程式或 Web API 服務） 的專案上將所需的設定與專案的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="95c1a-163">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="95c1a-164">它也會加入整個方案的 docker compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="95c1a-164">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="95c1a-165">在下列章節中，我們將說明每個這些檔案會進入資訊。</span><span class="sxs-lookup"><span data-stu-id="95c1a-165">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="95c1a-166">Visual Studio 可以執行這項工作，但有助於您了解什麼進入 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="95c1a-166">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="95c1a-167">選項 a： 建立專案，使用現有的官方.NET Docker 映像</span><span class="sxs-lookup"><span data-stu-id="95c1a-167">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="95c1a-168">通常打造您的容器，您可以從官方儲存機制取得基底映像之上的自訂映像[Docker Hub](https://hub.docker.com/)登錄。</span><span class="sxs-lookup"><span data-stu-id="95c1a-168">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="95c1a-169">明確地說是當您啟用在 Visual Studio 中的 Docker 支援時，實際上會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="95c1a-169">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="95c1a-170">Dockerfile 會使用現有 aspnetcore 映像。</span><span class="sxs-lookup"><span data-stu-id="95c1a-170">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="95c1a-171">我們稍早說明的 Docker 映像和儲存機制，您可以使用，根據的架構和您所選擇的 OS。</span><span class="sxs-lookup"><span data-stu-id="95c1a-171">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="95c1a-172">比方說，如果您想要使用 ASP.NET Core （Linux 或 Windows），使用的影像是 microsoft / aspnetcore:2.0。</span><span class="sxs-lookup"><span data-stu-id="95c1a-172">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="95c1a-173">因此，您只需要指定何種基底的 Docker 映像將對您的容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-173">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="95c1a-174">您執行此動作將從 microsoft / aspnetcore:2.0 至 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="95c1a-174">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="95c1a-175">這將會自動執行 Visual Studio 中，但如果您要更新的版本，您必須更新此值。</span><span class="sxs-lookup"><span data-stu-id="95c1a-175">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="95c1a-176">使用一個版本號碼從 Docker Hub 官方.NET 映像儲存機制可確保可以相同的語言功能 （包括開發、 測試和生產環境） 的所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="95c1a-176">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="95c1a-177">下列範例顯示範例 Dockerfile ASP.NET Core 容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-177">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="95c1a-178">在此情況下，容器根據 2.0 版的官方 ASP.NET Core Docker 映像 (適用於 Linux 和 Windows 多 arch)。</span><span class="sxs-lookup"><span data-stu-id="95c1a-178">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="95c1a-179">這是設定`FROM microsoft/aspnetcore:2.0`。</span><span class="sxs-lookup"><span data-stu-id="95c1a-179">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="95c1a-180">(如需此基底映像進一步詳細資訊，請參閱[ASP.NET Core Docker 映像](https://hub.docker.com/r/microsoft/aspnetcore/)頁面和[.NET Core Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)頁面。)在 Dockerfile 中，您也需要會指示 Docker 以在您將會在執行階段 （在此情況下，連接埠 80，公開設定的設定） 使用的 TCP 連接埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="95c1a-180">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="95c1a-181">在 Dockerfile 中，視語言和您使用的架構而定，您可以指定其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="95c1a-181">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="95c1a-182">比方說，使用的進入點列\["dotnet"，"MySingleContainerWebApp.dll"\]告訴 Docker 執行.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95c1a-182">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="95c1a-183">如果您會建置並執行.NET 應用程式使用 SDK 和.NET 核心 CLI (dotnet CLI)，此設定會在不同。</span><span class="sxs-lookup"><span data-stu-id="95c1a-183">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="95c1a-184">營收是進入點線及其他設定將會根據您選擇您的應用程式之語言與平台而不同。</span><span class="sxs-lookup"><span data-stu-id="95c1a-184">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="95c1a-185">其他資源</span><span class="sxs-lookup"><span data-stu-id="95c1a-185">Additional resources</span></span>

-   <span data-ttu-id="95c1a-186">**.NET Core 應用程式的建置 Docker Images**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)</span><span class="sxs-lookup"><span data-stu-id="95c1a-186">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)</span></span>

-   <span data-ttu-id="95c1a-187">**建置您自己的映像**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-187">**Build your own image**.</span></span> <span data-ttu-id="95c1a-188">中的正式的 Docker 文件。</span><span class="sxs-lookup"><span data-stu-id="95c1a-188">In the official Docker documentation.</span></span>
    [<span data-ttu-id="95c1a-189">*https://docs.docker.com/engine/tutorials/dockerimages/*</span><span class="sxs-lookup"><span data-stu-id="95c1a-189">*https://docs.docker.com/engine/tutorials/dockerimages/*</span></span>](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="95c1a-190">使用多重 arch 映像儲存機制</span><span class="sxs-lookup"><span data-stu-id="95c1a-190">Using multi-arch image repositories</span></span>

<span data-ttu-id="95c1a-191">單一儲存機制可以包含平台的變異，例如 Linux 映像和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="95c1a-191">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="95c1a-192">這項功能可讓廠商像 Microsoft （基底映像建立者） 建立的單一儲存機制以涵蓋多個平台 （這是 Linux 和 Windows）。</span><span class="sxs-lookup"><span data-stu-id="95c1a-192">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="95c1a-193">例如， [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) Docker Hub 登錄中的儲存機制使用相同的儲存機制名稱提供適用於 Linux 和 Windows Nano Server 的支援。</span><span class="sxs-lookup"><span data-stu-id="95c1a-193">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="95c1a-194">如果您指定的標籤，以明確的平台為目標喜歡在下列情況：</span><span class="sxs-lookup"><span data-stu-id="95c1a-194">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="95c1a-195">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="95c1a-195">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="95c1a-196">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="95c1a-196">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="95c1a-197">但是，這是新自 mid 2017，如果您指定相同的映像名稱，即使使用相同的標記，新的多 arch 映像 （例如可支援多 arch aspnetcore 映像） 都會使用 Linux 或 Windows 版本視您要部署的 Docker 主機 OS如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="95c1a-197">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="95c1a-198">**microsoft / aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="95c1a-198">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="95c1a-199">如此一來，當您從 Windows 主機提取映像時，它會提取 Windows 的變體，並從 Linux 主機提取相同的映像名稱將會提取 Linux variant。</span><span class="sxs-lookup"><span data-stu-id="95c1a-199">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="95c1a-200">選項 b： 建立您從頭的基底映像</span><span class="sxs-lookup"><span data-stu-id="95c1a-200">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="95c1a-201">您可以從頭開始建立您自己的 Docker 基底映像。</span><span class="sxs-lookup"><span data-stu-id="95c1a-201">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="95c1a-202">這種情況下不建議在開始使用 Docker，向其他人要求，但如果您想要設定特定的位元基底映像，您可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="95c1a-202">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="95c1a-203">其他資源</span><span class="sxs-lookup"><span data-stu-id="95c1a-203">Additional resources</span></span>

-   <span data-ttu-id="95c1a-204">**多重 arch.NET Core 映像**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-204">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="95c1a-205">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="95c1a-205">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="95c1a-206">**建立基底映像**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-206">**Create a base image**.</span></span> <span data-ttu-id="95c1a-207">官方 Docker 文件集。</span><span class="sxs-lookup"><span data-stu-id="95c1a-207">Official Docker documentation.</span></span>
    [<span data-ttu-id="95c1a-208">*https://docs.docker.com/engine/userguide/eng-image/baseimages/*</span><span class="sxs-lookup"><span data-stu-id="95c1a-208">*https://docs.docker.com/engine/userguide/eng-image/baseimages/*</span></span>](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="95c1a-209">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="95c1a-209">Step 3.</span></span> <span data-ttu-id="95c1a-210">建立自訂的 Docker 映像並將應用程式或服務內嵌在其中</span><span class="sxs-lookup"><span data-stu-id="95c1a-210">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="95c1a-211">每個服務應用程式中，您需要建立相關的映像。</span><span class="sxs-lookup"><span data-stu-id="95c1a-211">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="95c1a-212">如果您的應用程式所組成的單一服務或 web 應用程式，您只需要單一映像。</span><span class="sxs-lookup"><span data-stu-id="95c1a-212">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="95c1a-213">請注意，Docker 映像會自動為您建立 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="95c1a-213">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="95c1a-214">下列步驟只會需要編輯器/CLI 工作流程，而且時會發生的情況下說明為了清楚起見。</span><span class="sxs-lookup"><span data-stu-id="95c1a-214">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="95c1a-215">您身為開發人員，需要開發和測試推入完成之前，在本機功能或變更為您的原始檔控制系統，（例如，若要 GitHub)。</span><span class="sxs-lookup"><span data-stu-id="95c1a-215">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="95c1a-216">這表示您要建立 Docker 映像並部署到本機的 Docker 主機 （Windows 或 Linux VM） 的容器和執行、 測試及偵錯對這些本機的容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-216">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="95c1a-217">若要使用 Docker CLI 和 Dockerfile，本機環境中建立自訂映像，您可以使用 docker 建置命令，如圖 5-5。</span><span class="sxs-lookup"><span data-stu-id="95c1a-217">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="95c1a-218">**圖 5-5**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-218">**Figure 5-5**.</span></span> <span data-ttu-id="95c1a-219">建立自訂的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="95c1a-219">Creating a custom Docker image</span></span>

<span data-ttu-id="95c1a-220">（選擇性） 而不是直接執行 docker 建置專案資料夾中，您可以先產生所需的.NET 程式庫的部署資料夾並執行 dotnet 二進位檔發行，然後使用 docker 建置命令。</span><span class="sxs-lookup"><span data-stu-id="95c1a-220">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="95c1a-221">這將使用名稱 cesardl/netcore-webapi-微服務建立 Docker 映像-docker： 第一個。</span><span class="sxs-lookup"><span data-stu-id="95c1a-221">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="95c1a-222">在此情況下，： 第一個是代表特定版本的標記。</span><span class="sxs-lookup"><span data-stu-id="95c1a-222">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="95c1a-223">您可以重複此步驟，針對每個您需要建立 Docker 應用程式組成的自訂映像。</span><span class="sxs-lookup"><span data-stu-id="95c1a-223">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="95c1a-224">當應用程式由多個容器 （也就是說，它位於多個容器應用程式），您也可以使用 docker 撰寫向上-建置命令，以建置使用公開中相關的中繼資料的所有相關的映像使用單一命令docker compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="95c1a-224">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="95c1a-225">您可以找到現有的映像在本機儲存機制使用 docker 映像的命令，如圖 5-6 所示。</span><span class="sxs-lookup"><span data-stu-id="95c1a-225">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="95c1a-226">**圖 5-6。**</span><span class="sxs-lookup"><span data-stu-id="95c1a-226">**Figure 5-6.**</span></span> <span data-ttu-id="95c1a-227">檢視現有的映像使用 docker 映像的命令</span><span class="sxs-lookup"><span data-stu-id="95c1a-227">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="95c1a-228">使用 Visual Studio 中建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="95c1a-228">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="95c1a-229">當您使用 Visual Studio 建立專案與 Docker 的支援時，您未明確建立映像。</span><span class="sxs-lookup"><span data-stu-id="95c1a-229">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="95c1a-230">相反地，建立映像，當您按下 F5，並執行 dockerized 應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="95c1a-230">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="95c1a-231">此步驟會自動在 Visual Studio 中，但將不會看到它，就可能發生，請務必確定您知道發生什麼事的下方。</span><span class="sxs-lookup"><span data-stu-id="95c1a-231">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="95c1a-232">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="95c1a-232">Step 4.</span></span> <span data-ttu-id="95c1a-233">建立多個容器 Docker 應用程式時，docker compose.yml 中定義您的服務</span><span class="sxs-lookup"><span data-stu-id="95c1a-233">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="95c1a-234">[Docker compose.yml](https://docs.docker.com/compose/compose-file/)檔案可讓您定義一組部署為組成的應用程式部署命令的相關服務。</span><span class="sxs-lookup"><span data-stu-id="95c1a-234">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="95c1a-235">若要使用 docker compose.yml 檔案，您需要使用類似於下列範例中的內容建立根方案資料夾中的檔案在您的 main 中：</span><span class="sxs-lookup"><span data-stu-id="95c1a-235">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="95c1a-236">請注意，此 docker compose.yml 檔案之簡化且合併版本。</span><span class="sxs-lookup"><span data-stu-id="95c1a-236">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="95c1a-237">它包含靜態設定的每個容器 （例如自訂映像的名稱），這會一律套用再加上可能會取決於部署環境，例如連接字串的組態資訊的資料。</span><span class="sxs-lookup"><span data-stu-id="95c1a-237">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="95c1a-238">在稍後的章節裡，您將學習分割成多個 docker compose.yml 組態的方式 docker 撰寫的檔案和覆寫值，視環境和執行的類型 （偵錯或發行） 而定。</span><span class="sxs-lookup"><span data-stu-id="95c1a-238">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="95c1a-239">Docker compose.yml 檔案範例會定義五個服務： webmvc 服務 （web 應用程式）、 兩個 microservices （catalog.api 和 ordering.api） 和一個資料來源容器，sql.data，根據適用於 Linux 的容器執行的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="95c1a-239">The docker-compose.yml file example defines five services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="95c1a-240">每個服務會部署為容器，因此 Docker 映像需要每個。</span><span class="sxs-lookup"><span data-stu-id="95c1a-240">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="95c1a-241">Docker compose.yml 檔案會指定使用何種容器，不僅個別設定方式。</span><span class="sxs-lookup"><span data-stu-id="95c1a-241">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="95c1a-242">比方說，webmvc 容器會定義.yml 檔案中：</span><span class="sxs-lookup"><span data-stu-id="95c1a-242">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="95c1a-243">使用預先建置的資格 / web： 最新的映像。</span><span class="sxs-lookup"><span data-stu-id="95c1a-243">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="95c1a-244">不過，您也可以設定要建置的一部分的映像 docker 撰寫額外的組態執行根據組建： docker-compose 檔案 > 一節。</span><span class="sxs-lookup"><span data-stu-id="95c1a-244">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="95c1a-245">初始化兩個環境變數 （CatalogUrl 和 OrderingUrl）。</span><span class="sxs-lookup"><span data-stu-id="95c1a-245">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="95c1a-246">將轉送公開的連接埠 80 上的容器主機上的外部連接埠 80。</span><span class="sxs-lookup"><span data-stu-id="95c1a-246">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="95c1a-247">連結的 web 應用程式類別目錄和排序服務相依\_上設定。</span><span class="sxs-lookup"><span data-stu-id="95c1a-247">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="95c1a-248">這會導致等候，直到這些服務都已啟動服務。</span><span class="sxs-lookup"><span data-stu-id="95c1a-248">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="95c1a-249">我們將討論如何實作 microservices 和多個容器應用程式時，我們會重新審視 docker compose.yml 檔案，在稍後的章節。</span><span class="sxs-lookup"><span data-stu-id="95c1a-249">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="95c1a-250">使用 docker-compose.yml 在 Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="95c1a-250">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="95c1a-251">當如圖 5-7 所示，您可以新增至服務專案在 Visual Studio 方案中的 Docker 解決方案支援時，Visual Studio 將您的專案，加入了 Dockerfile，並在方案中新增服務 > 一節 （專案） docker compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="95c1a-251">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="95c1a-252">它是簡單的方法，撰寫您的多個容器解決方案。</span><span class="sxs-lookup"><span data-stu-id="95c1a-252">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="95c1a-253">您可以開啟 docker compose.yml 檔案並加以更新與其他功能。</span><span class="sxs-lookup"><span data-stu-id="95c1a-253">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="95c1a-254">**圖 5-7**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-254">**Figure 5-7**.</span></span> <span data-ttu-id="95c1a-255">在 Visual Studio 2017 新增 Docker 的支援，以滑鼠右鍵按一下 ASP.NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="95c1a-255">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="95c1a-256">Visual Studio 中加入 Docker 支援 Dockerfile 加入您的專案，不僅會在解決方案層級設定的數個通用的 docker compose.yml 檔案中加入組態資訊。</span><span class="sxs-lookup"><span data-stu-id="95c1a-256">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="95c1a-257">Docker 的支援加入至您在 Visual Studio 中的方案之後，您也會看到新的節點 （docker compose.dcproj 專案檔中） 包含已新增的 docker compose.yml 檔案，如圖 5-8 所示的方案總管 中。</span><span class="sxs-lookup"><span data-stu-id="95c1a-257">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="95c1a-258">**圖 5-8**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-258">**Figure 5-8**.</span></span> <span data-ttu-id="95c1a-259">**Docker 撰寫**加入 Visual Studio 2017 方案總管 中的樹狀節點</span><span class="sxs-lookup"><span data-stu-id="95c1a-259">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="95c1a-260">您可以使用單一的 docker compose.yml 檔案部署多個容器應用程式使用 docker 撰寫 up 命令。</span><span class="sxs-lookup"><span data-stu-id="95c1a-260">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="95c1a-261">不過，Visual Studio 會加入其中的群組讓您可以覆寫值取決於環境 （與實際執行的程式開發） 和執行類型 （與偵錯版本）。</span><span class="sxs-lookup"><span data-stu-id="95c1a-261">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="95c1a-262">這項功能將在稍後的章節中說明。</span><span class="sxs-lookup"><span data-stu-id="95c1a-262">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="95c1a-263">步驟 5：</span><span class="sxs-lookup"><span data-stu-id="95c1a-263">Step 5.</span></span> <span data-ttu-id="95c1a-264">建置並執行您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="95c1a-264">Build and run your Docker application</span></span>

<span data-ttu-id="95c1a-265">如果您的應用程式只有單一容器，您可以將它部署至您的 Docker 主機 （VM 或實體伺服器） 來執行。</span><span class="sxs-lookup"><span data-stu-id="95c1a-265">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="95c1a-266">不過，如果您的應用程式包含多個服務，您可以將其部署為組成的應用程式中，使用單一的 CLI 命令 （docker-撰寫組成），或使用 Visual Studio，就會使用該命令在過程中。</span><span class="sxs-lookup"><span data-stu-id="95c1a-266">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="95c1a-267">讓我們看看不同的選項。</span><span class="sxs-lookup"><span data-stu-id="95c1a-267">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="95c1a-268">選項 a： 執行單一容器與 Docker CLI</span><span class="sxs-lookup"><span data-stu-id="95c1a-268">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="95c1a-269">您可以執行使用 docker run 命令，如圖 5-9 的 Docker 容器：</span><span class="sxs-lookup"><span data-stu-id="95c1a-269">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="95c1a-270">**圖 5-9**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-270">**Figure 5-9**.</span></span> <span data-ttu-id="95c1a-271">執行使用 docker run 命令的 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="95c1a-271">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="95c1a-272">在此情況下，命令會將繫結容器的內部連接埠 5000 到主機電腦的連接埠 80。</span><span class="sxs-lookup"><span data-stu-id="95c1a-272">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="95c1a-273">這表示主機會接聽通訊埠 80 和轉送至容器的連接埠 5000。</span><span class="sxs-lookup"><span data-stu-id="95c1a-273">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="95c1a-274">選項 b： 執行多個容器應用程式</span><span class="sxs-lookup"><span data-stu-id="95c1a-274">Option B: Running a multi-container application</span></span>

<span data-ttu-id="95c1a-275">在大部分的企業案例中，Docker 應用程式將由多個服務，這表示您需要執行多個容器應用程式，如圖 5-10 所示。</span><span class="sxs-lookup"><span data-stu-id="95c1a-275">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="95c1a-276">**圖 5-10**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-276">**Figure 5-10**.</span></span> <span data-ttu-id="95c1a-277">使用 Docker 容器部署的 VM</span><span class="sxs-lookup"><span data-stu-id="95c1a-277">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="95c1a-278">使用 Docker CLI 執行多個容器應用程式</span><span class="sxs-lookup"><span data-stu-id="95c1a-278">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="95c1a-279">若要執行 Docker CLI 多容器應用程式，您可以執行 docker-撰寫 up 命令。</span><span class="sxs-lookup"><span data-stu-id="95c1a-279">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="95c1a-280">您在解決方案層級來部署多個容器應用程式有此命令會使用 docker compose.yml 檔。</span><span class="sxs-lookup"><span data-stu-id="95c1a-280">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="95c1a-281">圖 5-11 顯示時從您的主要專案目錄，其中包含 docker compose.yml 檔案中執行命令的結果。</span><span class="sxs-lookup"><span data-stu-id="95c1a-281">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="95c1a-282">**圖 5-11**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-282">**Figure 5-11**.</span></span> <span data-ttu-id="95c1a-283">範例會產生執行時 docker 撰寫向上命令</span><span class="sxs-lookup"><span data-stu-id="95c1a-283">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="95c1a-284">Docker 之後-撰寫排命令、 應用程式和其相關的容器會部署到您的 Docker 主機，如所述的 VM 表示圖 5-10。</span><span class="sxs-lookup"><span data-stu-id="95c1a-284">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="95c1a-285">執行和偵錯 Visual Studio 中的多個容器應用程式</span><span class="sxs-lookup"><span data-stu-id="95c1a-285">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="95c1a-286">執行使用 Visual Studio 2017 多容器應用程式無法取得更簡單。</span><span class="sxs-lookup"><span data-stu-id="95c1a-286">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="95c1a-287">您不只能執行多個容器應用程式，但您可以設定規則的中斷點來偵錯它直接從 Visual Studio 的所有容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-287">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="95c1a-288">如所述之前，每次您將 Docker 解決方案支援加入方案中的專案，該專案已在全域 （方案層級） docker compose.yml 檔案中，可讓您執行或偵錯整個方案一次。</span><span class="sxs-lookup"><span data-stu-id="95c1a-288">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="95c1a-289">Visual Studio 將會啟動一個已啟用，Docker 解決方案支援的每個專案的容器，並為您執行所有內部的步驟 （dotnet 發行，docker 建置等。）。</span><span class="sxs-lookup"><span data-stu-id="95c1a-289">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="95c1a-290">此處的重點是，即會顯示在圖 5-12 版中，在 Visual Studio 2017 沒有額外**Docker** F5 按鍵動作的命令。</span><span class="sxs-lookup"><span data-stu-id="95c1a-290">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="95c1a-291">此選項可讓您執行或偵錯多個容器應用程式，藉由執行 docker compose.yml 檔案，在方案層級中定義的所有容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-291">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="95c1a-292">偵錯多個容器解決方案的功能表示在不同的專案 （容器），設定多個中斷點，而每個中斷點，從 Visual Studio 偵錯時您會定義在不同的專案上且正在執行的中斷點處停止不同的容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-292">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="95c1a-293">**圖 5-12**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-293">**Figure 5-12**.</span></span> <span data-ttu-id="95c1a-294">在 Visual Studio 2017 中執行多個容器應用程式</span><span class="sxs-lookup"><span data-stu-id="95c1a-294">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="95c1a-295">其他資源</span><span class="sxs-lookup"><span data-stu-id="95c1a-295">Additional resources</span></span>

-   <span data-ttu-id="95c1a-296">**部署至遠端 Docker 主機 ASP.NET 容器**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="95c1a-296">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="95c1a-297">關於測試和部署與 orchestrators 附註</span><span class="sxs-lookup"><span data-stu-id="95c1a-297">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="95c1a-298">向上撰寫 docker 和 docker 執行命令 （或執行和偵錯 Visual Studio 中的容器） 是適合開發環境中測試容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-298">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="95c1a-299">但您不應該使用這種方法，如果您的目標 Docker 叢集，而且 orchestrators 像 Docker Swarm、 Mesosphere DC/作業系統或 Kubernetes。</span><span class="sxs-lookup"><span data-stu-id="95c1a-299">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="95c1a-300">如果您使用 「 類似叢集[Docker Swarm 模式](https://docs.docker.com/engine/swarm/)（適用於 Docker CE for Windows 和 Mac 版本 1.12 之後），您需要部署和測試使用類似的其他命令[docker 服務建立](https://docs.docker.com/engine/reference/commandline/service_create/)的單一服務。</span><span class="sxs-lookup"><span data-stu-id="95c1a-300">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="95c1a-301">如果您要部署數個容器所組成的應用程式，您使用[docker 撰寫配套](https://docs.docker.com/compose/reference/bundle/)和[docker 部署 myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/)部署組成的應用程式做為*堆疊*.</span><span class="sxs-lookup"><span data-stu-id="95c1a-301">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="95c1a-302">如需詳細資訊，請參閱部落格文章[簡介實驗的分散式應用程式組合](https://blog.docker.com/2016/06/docker-app-bundle/)Docker 文件中。</span><span class="sxs-lookup"><span data-stu-id="95c1a-302">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="95c1a-303">上的 Docker 站台。</span><span class="sxs-lookup"><span data-stu-id="95c1a-303">on the Docker site.</span></span>

<span data-ttu-id="95c1a-304">如[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)和[Kubernetes](http://kubernetes.io/docs/user-guide/deployments/)您會使用不同的部署命令和指令碼以及。</span><span class="sxs-lookup"><span data-stu-id="95c1a-304">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="95c1a-305">步驟 6：</span><span class="sxs-lookup"><span data-stu-id="95c1a-305">Step 6.</span></span> <span data-ttu-id="95c1a-306">測試 Docker 應用程式使用本機的 Docker 主機</span><span class="sxs-lookup"><span data-stu-id="95c1a-306">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="95c1a-307">此步驟會因您的應用程式正在進行。</span><span class="sxs-lookup"><span data-stu-id="95c1a-307">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="95c1a-308">在簡單的.NET Core Web 應用程式部署為單一容器或服務，您可以存取服務開啟 Docker 主機上的瀏覽器並瀏覽至該網站，如圖 5-13 所示。</span><span class="sxs-lookup"><span data-stu-id="95c1a-308">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="95c1a-309">（如果 Dockerfile 中的設定會對應至連接埠是 80 以外的任何主機上的容器，包括主機 post URL 中）。</span><span class="sxs-lookup"><span data-stu-id="95c1a-309">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host post in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="95c1a-310">**圖 5-13**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-310">**Figure 5-13**.</span></span> <span data-ttu-id="95c1a-311">測試 Docker 應用程式在本機使用 localhost 的範例</span><span class="sxs-lookup"><span data-stu-id="95c1a-311">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="95c1a-312">如果 localhost 未指向 Docker 主機 IP （根據預設，當使用 Docker CE，它應該如此），巡覽至您的服務，使用您的電腦網路卡的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="95c1a-312">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="95c1a-313">請注意此 URL 在瀏覽器中的使用連接埠 80，例如討論特定容器。</span><span class="sxs-lookup"><span data-stu-id="95c1a-313">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="95c1a-314">不過，在內部將要求被重新導向至通訊埠 5000，因為這是它的部署方式與 docker 執行命令上, 一個步驟中所述。</span><span class="sxs-lookup"><span data-stu-id="95c1a-314">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="95c1a-315">如圖 5-14 版中所示，您也可以測試使用 curl 終端機中，從應用程式。</span><span class="sxs-lookup"><span data-stu-id="95c1a-315">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="95c1a-316">在 Windows 上的 Docker 安裝，預設 Docker 主機 IP 一律為 10.0.75.1 除了您電腦的實際 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="95c1a-316">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="95c1a-317">**圖 5-14**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-317">**Figure 5-14**.</span></span> <span data-ttu-id="95c1a-318">測試在本機使用 curl Docker 應用程式的範例</span><span class="sxs-lookup"><span data-stu-id="95c1a-318">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="95c1a-319">測試和偵錯使用 Visual Studio 2017 容器</span><span class="sxs-lookup"><span data-stu-id="95c1a-319">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="95c1a-320">時執行和偵錯使用 Visual Studio 2017 容器，您可以偵錯.NET 應用程式相同的方式一樣沒有容器執行時。</span><span class="sxs-lookup"><span data-stu-id="95c1a-320">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="95c1a-321">測試和不含 Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="95c1a-321">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="95c1a-322">如果您正在開發使用編輯器/CLI 方法，偵錯容器是更困難，且您會想要產生追蹤偵錯。</span><span class="sxs-lookup"><span data-stu-id="95c1a-322">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="95c1a-323">其他資源</span><span class="sxs-lookup"><span data-stu-id="95c1a-323">Additional resources</span></span>

-   <span data-ttu-id="95c1a-324">**在本機的 Docker 容器中的應用程式偵錯**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="95c1a-324">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="95c1a-325">**Steve Lasker。建置、 偵錯、 部署與 Docker 的 ASP.NET Core 應用程式。**</span><span class="sxs-lookup"><span data-stu-id="95c1a-325">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="95c1a-326">視訊。</span><span class="sxs-lookup"><span data-stu-id="95c1a-326">Video.</span></span>
    [<span data-ttu-id="95c1a-327">*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*</span><span class="sxs-lookup"><span data-stu-id="95c1a-327">*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*</span></span>](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="95c1a-328">開發 Visual Studio 中的容器時簡化的工作流程</span><span class="sxs-lookup"><span data-stu-id="95c1a-328">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="95c1a-329">實際上，工作流程時使用 Visual Studio 會比您使用的編輯器/CLI 方法很簡單。</span><span class="sxs-lookup"><span data-stu-id="95c1a-329">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="95c1a-330">Dockerfile 與的大部分步驟所需的 Docker 和 docker compose.yml 檔案隱藏或簡化 Visual Studio 中，如圖 5-15 所示。</span><span class="sxs-lookup"><span data-stu-id="95c1a-330">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="95c1a-331">**圖 5-15**。</span><span class="sxs-lookup"><span data-stu-id="95c1a-331">**Figure 5-15**.</span></span> <span data-ttu-id="95c1a-332">使用 Visual Studio 進行開發時簡化的工作流程</span><span class="sxs-lookup"><span data-stu-id="95c1a-332">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="95c1a-333">此外，您需要執行步驟 2 （新增 Docker 支援至您的專案），就可以一次。</span><span class="sxs-lookup"><span data-stu-id="95c1a-333">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="95c1a-334">因此，工作流程是類似於一般的開發工作時使用的.NET 之任何其他開發。</span><span class="sxs-lookup"><span data-stu-id="95c1a-334">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="95c1a-335">您需要知道狀況實際上映像建置程序、 哪些您使用的基底映像 （部署容器等），有時您也要編輯的 Dockerfile 或 docker compose.yml 檔案，以自訂行為。</span><span class="sxs-lookup"><span data-stu-id="95c1a-335">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="95c1a-336">但大部分的工作已大幅簡化使用 Visual Studio 中，讓您提高產能。</span><span class="sxs-lookup"><span data-stu-id="95c1a-336">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="95c1a-337">其他資源</span><span class="sxs-lookup"><span data-stu-id="95c1a-337">Additional resources</span></span>

-   <span data-ttu-id="95c1a-338">**Steve Lasker。.NET docker 開發使用 Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="95c1a-338">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="95c1a-339">**Jeffrey T Fritz。將.NET Core 應用程式中放入新的 Docker 工具容器中，適用於 Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="95c1a-339">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="95c1a-340">在 Dockerfile 中使用 PowerShell 命令來設定 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="95c1a-340">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="95c1a-341">[Windows 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)可讓您將現有的 Windows 應用程式轉換成的 Docker 映像，並將其部署在 Docker 生態系統的其他部分相同的工具。</span><span class="sxs-lookup"><span data-stu-id="95c1a-341">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="95c1a-342">若要使用 Windows 容器，您執行 PowerShell 命令在 Dockerfile 中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="95c1a-342">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="95c1a-343">在此情況下，我們會使用 Windows Server Core 基本映像 （FROM 設定），並使用 PowerShell 命令 （執行設定） 安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="95c1a-343">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="95c1a-344">類似的方式，您也可以使用 PowerShell 命令來設定 ASP.NET 4.x、.NET 4.6 或任何其他 Windows 軟體這類其他元件。</span><span class="sxs-lookup"><span data-stu-id="95c1a-344">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="95c1a-345">例如，下列命令在 Dockerfile 中的上設定 ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="95c1a-345">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="95c1a-346">其他資源</span><span class="sxs-lookup"><span data-stu-id="95c1a-346">Additional resources</span></span>

-   <span data-ttu-id="95c1a-347">**aspnet-docker/Dockerfile。**</span><span class="sxs-lookup"><span data-stu-id="95c1a-347">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="95c1a-348">若要從包含 Windows 功能的 dockerfiles 執行範例 Powershell 命令。</span><span class="sxs-lookup"><span data-stu-id="95c1a-348">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [<span data-ttu-id="95c1a-349">*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*</span><span class="sxs-lookup"><span data-stu-id="95c1a-349">*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*</span></span>](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="95c1a-350">[上一個](index.md) [下一步] (.../ net-core-single-containers-linux-windows-server-hosts/index.md）</span><span class="sxs-lookup"><span data-stu-id="95c1a-350">[Previous] (index.md) [Next] (../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>
