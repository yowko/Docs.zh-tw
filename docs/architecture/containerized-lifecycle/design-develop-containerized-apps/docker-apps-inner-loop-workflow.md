---
title: Docker 應用程式的內部迴圈開發工作流程
description: 了解用於開發 Docker 應用程式的「內部迴圈」工作流程。
ms.date: 02/15/2019
ms.openlocfilehash: 565852511f3a837066d5da5cf0e3ab0a902dd7da
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956504"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="8857f-103">Docker 應用程式的內部迴圈開發工作流程</span><span class="sxs-lookup"><span data-stu-id="8857f-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="8857f-104">在觸發跨越整個 DevOps 循環的外部迴圈工作流程之前，所有項目都從每個開發人員的機器開始，使用其慣用語言或平台對應用程式本身編碼，並在本機進行測試 (圖 4-21)。</span><span class="sxs-lookup"><span data-stu-id="8857f-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="8857f-105">但不論何種情況，不論您選擇何種語言、架構或平台，您都會有一個重要的共同點。</span><span class="sxs-lookup"><span data-stu-id="8857f-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="8857f-106">在此特定的工作流程中，您將一律開發並測試 Docker 容器，但僅在本機。</span><span class="sxs-lookup"><span data-stu-id="8857f-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![此圖顯示內部迴圈開發環境的概念。](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="8857f-108">**圖 4-21**：</span><span class="sxs-lookup"><span data-stu-id="8857f-108">**Figure 4-21**.</span></span> <span data-ttu-id="8857f-109">內部迴圈開發內容</span><span class="sxs-lookup"><span data-stu-id="8857f-109">Inner-loop development context</span></span>

<span data-ttu-id="8857f-110">Docker 映像的容器或執行個體將包含這些元件：</span><span class="sxs-lookup"><span data-stu-id="8857f-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="8857f-111">作業系統選取項目 (例如 Linux 發行版本或 Windows)</span><span class="sxs-lookup"><span data-stu-id="8857f-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="8857f-112">開發人員新增的檔案 (例如應用程式二進位檔)</span><span class="sxs-lookup"><span data-stu-id="8857f-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="8857f-113">組態 (例如環境設定和相依性)</span><span class="sxs-lookup"><span data-stu-id="8857f-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="8857f-114">由 Docker 執行哪些程序的指示</span><span class="sxs-lookup"><span data-stu-id="8857f-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="8857f-115">您可以設定利用 Docker 作為程序的內部迴圈開發工作流程 (在下一節中描述)。</span><span class="sxs-lookup"><span data-stu-id="8857f-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="8857f-116">請考慮不包含設定環境的初始步驟，因為您只需要進行一次。</span><span class="sxs-lookup"><span data-stu-id="8857f-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="8857f-117">使用 Visual Studio Code 和 Docker CLI，在 Docker 容器中建置單一應用程式</span><span class="sxs-lookup"><span data-stu-id="8857f-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="8857f-118">應用程式是由您自己的服務加上額外程式庫 (相依性) 所組成。</span><span class="sxs-lookup"><span data-stu-id="8857f-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="8857f-119">圖 4-22 顯示建置 Docker 應用程式時通常需要執行的基本步驟，後接每個步驟的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="8857f-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![此圖顯示建立容器化應用程式所需的七個步驟。](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="8857f-121">**圖 4-22**。</span><span class="sxs-lookup"><span data-stu-id="8857f-121">**Figure 4-22**.</span></span> <span data-ttu-id="8857f-122">使用 Docker CLI 之 Docker 容器化應用程式的生命週期工作流程概要</span><span class="sxs-lookup"><span data-stu-id="8857f-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="8857f-123">步驟 1:開始在 Visual Studio Code 中編碼，並建立您的初始應用程式/服務基準</span><span class="sxs-lookup"><span data-stu-id="8857f-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="8857f-124">開發 Docker 應用程式的方式，與不使用 Docker 開發應用程式的方式類似。</span><span class="sxs-lookup"><span data-stu-id="8857f-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="8857f-125">差別在於，在開發時，您要部署並測試放置於本機環境之 Docker 容器 (例如 Linux VM 或 Windows) 中正在執行的應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="8857f-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="8857f-126">**設定您的本機環境**</span><span class="sxs-lookup"><span data-stu-id="8857f-126">**Setting up your local environment**</span></span>

<span data-ttu-id="8857f-127">使用適用於 Mac 和 Windows 的最新版本 Docker，開發 Docker 應用程式比以往更加容易，且設定非常簡單。</span><span class="sxs-lookup"><span data-stu-id="8857f-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="8857f-128">如需設定適用於 Windows 之 Docker 的指示，請瀏覽 <https://docs.docker.com/docker-for-windows/>。</span><span class="sxs-lookup"><span data-stu-id="8857f-128">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="8857f-129">如需設定適用於 Mac 之 Docker 的指示，請瀏覽 <https://docs.docker.com/docker-for-mac/>。</span><span class="sxs-lookup"><span data-stu-id="8857f-129">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="8857f-130">此外，您也需要程式碼編輯器，讓您可在使用 Docker CLI 時實際開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="8857f-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="8857f-131">Microsoft 提供 Visual Studio Code，這是 Windows、Linux 和 macOS 上支援的輕量程式碼編輯器，並為 IntelliSense 提供[許多語言的支援](https://code.visualstudio.com/docs/languages/overview)（JavaScript、.Net、Go、JAVA、Ruby、Python 和最新式的語言）。[偵錯](https://code.visualstudio.com/Docs/editor/debugging)與 [使用 Git 的整合功能](https://code.visualstudio.com/Docs/editor/versioncontrol)及[延伸支援](https://code.visualstudio.com/docs/extensions/overview)。</span><span class="sxs-lookup"><span data-stu-id="8857f-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="8857f-132">此編輯器非常適合 macOS 和 Linux 開發人員。</span><span class="sxs-lookup"><span data-stu-id="8857f-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="8857f-133">在 Windows 中，您也可以使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8857f-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="8857f-134">如需安裝 Windows、Linux 或 macOS Visual Studio Code 的指示，請移至 <https://code.visualstudio.com/docs/setup/setup-overview/>。</span><span class="sxs-lookup"><span data-stu-id="8857f-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="8857f-135">如需設定適用於 Mac 之 Docker 的指示，請瀏覽 <https://docs.docker.com/docker-for-mac/>。</span><span class="sxs-lookup"><span data-stu-id="8857f-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="8857f-136">您可以使用 Docker CLI 並使用任何程式碼編輯器撰寫您的程式碼，但使用包含 Docker 延伸模組的 Visual Studio Code 可以輕鬆撰寫工作區中的 `Dockerfile` 和 `docker-compose.yml` 檔案。</span><span class="sxs-lookup"><span data-stu-id="8857f-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="8857f-137">您也可以從 Visual Studio Code IDE 執行工作和指令碼，以使用下面的 Docker CLI 執行 Docker 命令。</span><span class="sxs-lookup"><span data-stu-id="8857f-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="8857f-138">適用於 VS Code 的 Docker 延伸模組提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="8857f-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="8857f-139">`Dockerfile` 和 `docker-compose.yml` 檔案的自動產生</span><span class="sxs-lookup"><span data-stu-id="8857f-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="8857f-140">`docker-compose.yml` 和 `Dockerfile` 檔案的語法醒目提示及暫留提示</span><span class="sxs-lookup"><span data-stu-id="8857f-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="8857f-141">`Dockerfile` 和 `docker-compose.yml` 檔案的 IntelliSense (完成)</span><span class="sxs-lookup"><span data-stu-id="8857f-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="8857f-142">`Dockerfile` 檔案的 Linting (錯誤和警告)</span><span class="sxs-lookup"><span data-stu-id="8857f-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="8857f-143">最常見 Docker 命令的命令選擇區 (F1) 整合</span><span class="sxs-lookup"><span data-stu-id="8857f-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="8857f-144">用於管理映像和容器的總管整合</span><span class="sxs-lookup"><span data-stu-id="8857f-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="8857f-145">將映像從 DockerHub 和 Azure Container Registry 部署至 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="8857f-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="8857f-146">若要安裝 Docker 延伸模組，請按 Ctrl+Shift+P、鍵入 `ext install`，然後執行安裝延伸模組的命令來顯示 Marketplace 延伸模組清單。</span><span class="sxs-lookup"><span data-stu-id="8857f-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="8857f-147">接下來，輸入 **docker** 以篩選結果，然後選取 Docker 支援延伸模組，如圖 4-23 所示。</span><span class="sxs-lookup"><span data-stu-id="8857f-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![適用於 VS Code 的 Docker 延伸模組檢視。](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="8857f-149">**圖 4-23**：</span><span class="sxs-lookup"><span data-stu-id="8857f-149">**Figure 4-23**.</span></span> <span data-ttu-id="8857f-150">在 Visual Studio Code 中安裝 Docker 延伸模組</span><span class="sxs-lookup"><span data-stu-id="8857f-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="8857f-151">步驟 2:建立與現有映像 (純文字 OS 或開發環境，例如 .NET Core、Node.js 和 Ruby) 相關的 DockerFile</span><span class="sxs-lookup"><span data-stu-id="8857f-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="8857f-152">針對每個要建置的自訂映像，以及每個要部署的容器，您都需要一個 `DockerFile`。</span><span class="sxs-lookup"><span data-stu-id="8857f-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="8857f-153">如果您的應用程式由單一自訂服務所組成，您將需要單一 `DockerFile`。</span><span class="sxs-lookup"><span data-stu-id="8857f-153">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="8857f-154">但如果您的應用程式由多個服務所組成 (如同在微服務架構中)，針對每項服務您將需要一個 `Dockerfile`。</span><span class="sxs-lookup"><span data-stu-id="8857f-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="8857f-155">`DockerFile` 通常放在應用程式或服務的根資料夾中，並包含必要的命令，以讓 Docker 知道如何設定並執行該應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="8857f-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="8857f-156">您可以建立您的 `DockerFile`，並將其與您的程式碼 (node.js、.NET Core 等) 一起新增至專案中；如果您還不熟悉環境，請查看下列提示。</span><span class="sxs-lookup"><span data-stu-id="8857f-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="8857f-157">您可以使用 Docker 延伸模組來引導您使用與 Docker 容器相關的 `Dockerfile` 和 `docker-compose.yml` 檔案。</span><span class="sxs-lookup"><span data-stu-id="8857f-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="8857f-158">最後，您可能會在沒有此工具的情況下撰寫這類檔案，但使用 Docker 延伸模組是不錯的起點，可加速您的學習曲線。</span><span class="sxs-lookup"><span data-stu-id="8857f-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="8857f-159">在圖 4-24 中，您可以看到如何使用適用於 VS Code 的 Docker 延伸模組來新增 docker-compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="8857f-159">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![適用於 VS Code 的 Docker 延伸模組主控台檢視。](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="8857f-161">**圖 4-24**：</span><span class="sxs-lookup"><span data-stu-id="8857f-161">**Figure 4-24**.</span></span> <span data-ttu-id="8857f-162">使用**將 Docker 檔案新增至工作區命令**新增的 Docker 檔案</span><span class="sxs-lookup"><span data-stu-id="8857f-162">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="8857f-163">新增 DockerFile 時，您將指定您要使用哪些基礎 Docker 映像 (例如使用 `FROM mcr.microsoft.com/dotnet/core/aspnet`)。</span><span class="sxs-lookup"><span data-stu-id="8857f-163">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="8857f-164">您通常會在基底映像之上建置自訂映像，該基底映像可從 [Docker Hub登錄](https://hub.docker.com/)的任何官方存放庫取得 (例如 [.NET Core 的映像](https://hub.docker.com/_/microsoft-dotnet-core/)或 [Node.js](https://hub.docker.com/_/node/) 的映像)。</span><span class="sxs-lookup"><span data-stu-id="8857f-164">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="8857f-165">***使用現有的官方 Docker 映像***</span><span class="sxs-lookup"><span data-stu-id="8857f-165">***Use an existing official Docker image***</span></span>

<span data-ttu-id="8857f-166">使用具有版本號碼的官方語言堆疊存放庫，可確保所有電腦上都能使用相同的語言功能 (包括開發、測試和生產環境)。</span><span class="sxs-lookup"><span data-stu-id="8857f-166">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="8857f-167">下列是 .NET Core 容器的範例 DockerFile：</span><span class="sxs-lookup"><span data-stu-id="8857f-167">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="8857f-168">在此案例中，映像是以 2.2 版的官方 ASP.NET Core Docker 映像為基礎 (適用於 Linux 和 Windows 的多架構)，依據此行 `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`。</span><span class="sxs-lookup"><span data-stu-id="8857f-168">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="8857f-169">(如需本主題的詳細資訊，請參閱 [ASP.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)頁面及 [.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core/)頁面)。</span><span class="sxs-lookup"><span data-stu-id="8857f-169">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="8857f-170">在 DockerFile 中，您也可以指示 Docker 接聽您將在執行階段使用的 TCP 連接埠 (例如連接埠 80)。</span><span class="sxs-lookup"><span data-stu-id="8857f-170">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="8857f-171">您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。</span><span class="sxs-lookup"><span data-stu-id="8857f-171">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="8857f-172">例如，`ENTRYPOINT` 行中有 `["dotnet", "MySingleContainerWebApp.dll"]` 會指示 Docker 執行 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8857f-172">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="8857f-173">如果您使用 SDK 和 .NET Core CLI (`dotnet CLI`) 建置及執行 .NET 應用程式，此設定會有所不同。</span><span class="sxs-lookup"><span data-stu-id="8857f-173">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="8857f-174">此處的重點，是 ENTRYPOINT 行與其他設定會視您選擇的應用程式語言和平台而定。</span><span class="sxs-lookup"><span data-stu-id="8857f-174">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="8857f-175">如需如何建置 .NET Core 應用程式之 Docker 映像的詳細資訊，請瀏覽 <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。</span><span class="sxs-lookup"><span data-stu-id="8857f-175">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="8857f-176">若要深入了解如何建置您自己的映像，請瀏覽 <https://docs.docker.com/engine/tutorials/dockerimages/>。</span><span class="sxs-lookup"><span data-stu-id="8857f-176">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="8857f-177">**使用多架構映像存放庫**</span><span class="sxs-lookup"><span data-stu-id="8857f-177">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="8857f-178">存放庫中的單一映像名稱可以包含多種平台變化，例如 Linux 映像和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="8857f-178">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="8857f-179">這項功能可讓 Microsoft (基底映像建立者) 等廠商建立單一存放庫以涵蓋多個平台 (即 Linux 和 Windows)。</span><span class="sxs-lookup"><span data-stu-id="8857f-179">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="8857f-180">例如，Docker Hub 登錄提供的 [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) 存放庫，會使用相同的映像名稱提供 Linux 和 Windows Nano Server 支援。</span><span class="sxs-lookup"><span data-stu-id="8857f-180">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="8857f-181">從 Windows 主機提取 [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) 映像會提取 Windows 變化，而從 Linux 主機提取相同的映像名稱則會提取 Linux 變化。</span><span class="sxs-lookup"><span data-stu-id="8857f-181">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="8857f-182">***建立全新的基底映像***</span><span class="sxs-lookup"><span data-stu-id="8857f-182">***Create your base image from scratch***</span></span>

<span data-ttu-id="8857f-183">您可以從頭建立您自己的 Docker 基底映像，如 Docker 的此[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)中所述。</span><span class="sxs-lookup"><span data-stu-id="8857f-183">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="8857f-184">如果您是 Docker 新手，此方案可能不適合您，但如果您想要設定專屬基底映像的特點，您可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="8857f-184">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="8857f-185">步驟 3：建立自訂 Docker 映像並將服務嵌入其中</span><span class="sxs-lookup"><span data-stu-id="8857f-185">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="8857f-186">針對每個包含您應用程式的自訂服務，您需要建立相關映像。</span><span class="sxs-lookup"><span data-stu-id="8857f-186">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="8857f-187">如果您的應用程式組成為單一的服務或 Web 應用程式，則您只需要單一映像。</span><span class="sxs-lookup"><span data-stu-id="8857f-187">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="8857f-188">考慮「外部迴圈 DevOps 工作流程」時，每當您將原始程式碼推送至 Git 存放庫 (持續整合)，映像會透過自動建置程序建立，因此映像將於原始程式碼的全域環境中建立。</span><span class="sxs-lookup"><span data-stu-id="8857f-188">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="8857f-189">但在我們考慮進入該外部迴圈路由之前，我們需要確保 Docker 應用程式實際上正常運作，使其不會將可能無法正常運作的程式碼推送至原始檔控制系統 (Git 等)。</span><span class="sxs-lookup"><span data-stu-id="8857f-189">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="8857f-190">因此，每位開發人員首先需要執行整個內部迴圈程序，以在本機進行測試並繼續開發，直到他們想要推送完整的功能或變更為原始檔控制系統。</span><span class="sxs-lookup"><span data-stu-id="8857f-190">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="8857f-191">若要在您的本機環境中使用 DockerFile 建立映像，您可以使用 docker build 命令，如圖 4-25 所示 (針對由多個容器/服務所組成的應用程式，您也可以執行 `docker-compose up --build`)。</span><span class="sxs-lookup"><span data-stu-id="8857f-191">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![螢幕擷取畫面，顯示 docker build 命令的主控台輸出。](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="8857f-193">**圖 4-25**：</span><span class="sxs-lookup"><span data-stu-id="8857f-193">**Figure 4-25**.</span></span> <span data-ttu-id="8857f-194">執行 docker build</span><span class="sxs-lookup"><span data-stu-id="8857f-194">Running docker build</span></span>

<span data-ttu-id="8857f-195">(選用) 不直接從專案資料夾執行 `docker build`，而是先使用 run `dotnet publish` 命令產生具有所需 .NET 程式庫的可部署資料夾，然後執行 `docker build`。</span><span class="sxs-lookup"><span data-stu-id="8857f-195">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="8857f-196">此範例使用名稱 `cesardl/netcore-webapi-microservice-docker:first` 來建立 Docker 映像 (`:first` 是標籤，例如特定版本)。</span><span class="sxs-lookup"><span data-stu-id="8857f-196">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="8857f-197">您可以透過數個容器，為組成 Docker 應用程式所需建立的每個自訂映像採用此步驟。</span><span class="sxs-lookup"><span data-stu-id="8857f-197">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="8857f-198">您可以使用 docker images 命令在本機存放庫 (您的部署機器) 中尋找現有的映像，如圖 4-26 所示。</span><span class="sxs-lookup"><span data-stu-id="8857f-198">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![docker images 命令的主控台輸出，顯示現有的映像。](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="8857f-200">**圖 4-26**。</span><span class="sxs-lookup"><span data-stu-id="8857f-200">**Figure 4-26**.</span></span> <span data-ttu-id="8857f-201">使用 docker images 檢視現有的映像</span><span class="sxs-lookup"><span data-stu-id="8857f-201">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="8857f-202">步驟 4：建置具有多個服務的組成 Docker 應用程式時，在 docker-compose.yml 中定義您的服務</span><span class="sxs-lookup"><span data-stu-id="8857f-202">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="8857f-203">透過 `docker-compose.yml` 檔案，您可以定義一組相關服務，部署為具有部署命令 (將於下一節解釋) 的組成應用程式。</span><span class="sxs-lookup"><span data-stu-id="8857f-203">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="8857f-204">在主要或根方案資料夾中建立該檔案；其內容應與此 `docker-compose.yml` 檔案中顯示的內容類似：</span><span class="sxs-lookup"><span data-stu-id="8857f-204">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

<span data-ttu-id="8857f-205">在此特殊案例中，此檔案定義兩個服務：Web 服務 (您的自訂服務) 和 redis 服務 (熱門的快取服務)。</span><span class="sxs-lookup"><span data-stu-id="8857f-205">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="8857f-206">每項服務都會部署為容器，因此我們需要為每個服務使用具體的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="8857f-206">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="8857f-207">針對此特定的 Web 服務，映像必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8857f-207">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="8857f-208">從目前目錄中的 DockerFile 建置</span><span class="sxs-lookup"><span data-stu-id="8857f-208">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="8857f-209">將容器上公開通訊埠 80 轉送至主機的通訊埠 81</span><span class="sxs-lookup"><span data-stu-id="8857f-209">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="8857f-210">將主機上專案目錄裝載至容器內的 /code，可讓您修改程式碼而不需重建映像</span><span class="sxs-lookup"><span data-stu-id="8857f-210">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="8857f-211">將 Web 服務連結至 redis 服務</span><span class="sxs-lookup"><span data-stu-id="8857f-211">Link the web service to the redis service</span></span>

<span data-ttu-id="8857f-212">Redis 服務會使用從 Docker Hub 登錄提取的[最新公用 redis 映像](https://hub.docker.com/_/redis/)。</span><span class="sxs-lookup"><span data-stu-id="8857f-212">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="8857f-213">[redis](https://redis.io/) 是伺服器端應用程式的熱門快取系統。</span><span class="sxs-lookup"><span data-stu-id="8857f-213">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="8857f-214">步驟 5：建置並執行您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="8857f-214">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="8857f-215">如果您的應用程式只有單一容器，您只需要將其部署至您的 Docker 主機 (VM 或實體伺服器) 來執行。</span><span class="sxs-lookup"><span data-stu-id="8857f-215">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="8857f-216">不過，如果您的應用程式由多個服務組成，您也需要「撰寫」該應用程式。</span><span class="sxs-lookup"><span data-stu-id="8857f-216">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="8857f-217">讓我們看看不同的選項。</span><span class="sxs-lookup"><span data-stu-id="8857f-217">Let's see the different options.</span></span>

<span data-ttu-id="8857f-218">@no__t 0Option：執行單一容器或服務\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8857f-218">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="8857f-219">您可以使用 docker run 命令執行 Docker 映像，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8857f-219">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="8857f-220">針對此特定的部署，我們將會將傳送至連接埠 80 的要求重新導向至內部連接埠 5000。</span><span class="sxs-lookup"><span data-stu-id="8857f-220">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="8857f-221">現在應用程式正在主機層級的外部連接埠 80 上接聽。</span><span class="sxs-lookup"><span data-stu-id="8857f-221">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="8857f-222">***Option B：撰寫並執行多容器應用程式***</span><span class="sxs-lookup"><span data-stu-id="8857f-222">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="8857f-223">在大部分的企業案例中，Docker 應用程式由多個服務組成。</span><span class="sxs-lookup"><span data-stu-id="8857f-223">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="8857f-224">在這些案例中，您可以執行 `docker-compose up` 命令 (圖 4-27)，會使用您先前可能已建立的 docker compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="8857f-224">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="8857f-225">執行此命令會部署組成應用程式及其所有相關容器。</span><span class="sxs-lookup"><span data-stu-id="8857f-225">Running this command deploys a composed application with all of its related containers.</span></span>

![docker compose up 命令的主控台輸出。](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="8857f-227">**圖 4-27**。</span><span class="sxs-lookup"><span data-stu-id="8857f-227">**Figure 4-27**.</span></span> <span data-ttu-id="8857f-228">執行 "docker-compose up" 命令的結果</span><span class="sxs-lookup"><span data-stu-id="8857f-228">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="8857f-229">執行 `docker-compose up` 之後，您會將應用程式及其相關容器部署至您的 Docker 主機，如圖 4-28 以 VM 表示。</span><span class="sxs-lookup"><span data-stu-id="8857f-229">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![執行多容器應用程式的 VM。](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="8857f-231">**圖 4-28**。</span><span class="sxs-lookup"><span data-stu-id="8857f-231">**Figure 4-28**.</span></span> <span data-ttu-id="8857f-232">部署了 Docker 容器的 VM</span><span class="sxs-lookup"><span data-stu-id="8857f-232">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="8857f-233">步驟 6：測試您的 Docker 應用程式 (本機方式，在您的本機 CD VM 中)</span><span class="sxs-lookup"><span data-stu-id="8857f-233">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="8857f-234">此步驟會隨應用程式執行的作業而異。</span><span class="sxs-lookup"><span data-stu-id="8857f-234">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="8857f-235">在部署為單一容器或服務的簡單 .NET Core Web API "Hello World" 中，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。</span><span class="sxs-lookup"><span data-stu-id="8857f-235">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="8857f-236">如果 localhost 未開啟，請使用此命令尋找機器的 IP 位址以巡覽至您的服務：</span><span class="sxs-lookup"><span data-stu-id="8857f-236">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="8857f-237">在 Docker 主機上，開啟瀏覽器並巡覽至該網站；您應該會看到您的應用程式/服務正在執行，如圖 4-29 所示。</span><span class="sxs-lookup"><span data-stu-id="8857f-237">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![從 localhost/API/values 回應的瀏覽器檢視。](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="8857f-239">**圖 4-29**。</span><span class="sxs-lookup"><span data-stu-id="8857f-239">**Figure 4-29**.</span></span> <span data-ttu-id="8857f-240">使用 localhost 在本機測試 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="8857f-240">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="8857f-241">請注意，其正在使用連接埠 80，但在內部會重新導向至連接埠 5000，因為這是其與 `docker run` 一起部署的方式，如先前所述。</span><span class="sxs-lookup"><span data-stu-id="8857f-241">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="8857f-242">您可以從終端機使用 CURL 來測試。</span><span class="sxs-lookup"><span data-stu-id="8857f-242">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="8857f-243">在 Windows 上的 Docker 安裝中，預設 IP 是 10.0.75.1，如圖 4-30 所示。</span><span class="sxs-lookup"><span data-stu-id="8857f-243">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![使用 curl 取得 http://10.0.75.1/API/values 的主控台輸出](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="8857f-245">**圖 4-30**。</span><span class="sxs-lookup"><span data-stu-id="8857f-245">**Figure 4-30**.</span></span> <span data-ttu-id="8857f-246">使用 CURL 在本機測試 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="8857f-246">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="8857f-247">**對在 Docker 上執行的容器進行偵錯**</span><span class="sxs-lookup"><span data-stu-id="8857f-247">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="8857f-248">Visual Studio Code 支援對 Docker 的偵錯，如果您使用 Node.js 和像是 .NET Core 容器的其他平台。</span><span class="sxs-lookup"><span data-stu-id="8857f-248">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="8857f-249">在使用適用於 Windows 或 Mac 的 Visual Studio 時，您也可以對 Docker 中的 .NET Core 或 .NET Framework 容器進行偵錯，如下一節中所述。</span><span class="sxs-lookup"><span data-stu-id="8857f-249">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
><span data-ttu-id="8857f-250">@no__t 0To 深入瞭解如何對 node.js Docker 容器進行調試，請參閱 <https://blog.docker.com/2016/07/live-debugging-docker/> 和 <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>。</span><span class="sxs-lookup"><span data-stu-id="8857f-250"> To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8857f-251">[上一頁](docker-apps-development-environment.md)
>[下一頁](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="8857f-251">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
