---
title: Docker 應用程式的內部迴圈開發工作流程
description: 了解開發 Docker 應用程式的 「 內部迴圈 」 工作流程。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 36fcf5769376375854c2a2631e26e8b136df0de6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050539"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="bfb80-103">Docker 應用程式的內部迴圈開發工作流程</span><span class="sxs-lookup"><span data-stu-id="bfb80-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="bfb80-104">之前觸發外部迴圈工作流程跨越整個 DevOps 循環，所有開始每位開發人員在電腦上，應用程式本身程式碼撰寫、 使用其慣用的語言或平台，以及在本機進行測試 (圖 4-21)。</span><span class="sxs-lookup"><span data-stu-id="bfb80-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="bfb80-105">但在每個案例中，您有很重要的一點共通點，無論選擇何種語言、 架構或平台。</span><span class="sxs-lookup"><span data-stu-id="bfb80-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="bfb80-106">在此特定的工作流程，您一律開發並測試 Docker 容器，但只能在本機。</span><span class="sxs-lookup"><span data-stu-id="bfb80-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![步驟 1-程式碼/執行/偵錯](./media/image18.png)

<span data-ttu-id="bfb80-108">**圖 4-21**：</span><span class="sxs-lookup"><span data-stu-id="bfb80-108">**Figure 4-21**.</span></span> <span data-ttu-id="bfb80-109">內部迴圈開發內容</span><span class="sxs-lookup"><span data-stu-id="bfb80-109">Inner-loop development context</span></span>

<span data-ttu-id="bfb80-110">Docker 映像的執行個體的容器將會包含這些元件：</span><span class="sxs-lookup"><span data-stu-id="bfb80-110">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="bfb80-111">作業系統選取項目 （例如，對 Linux 散發套件或 Windows）</span><span class="sxs-lookup"><span data-stu-id="bfb80-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="bfb80-112">加入開發人員 （例如，應用程式二進位檔） 的檔案</span><span class="sxs-lookup"><span data-stu-id="bfb80-112">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="bfb80-113">設定 （例如，環境設定和相依性）</span><span class="sxs-lookup"><span data-stu-id="bfb80-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="bfb80-114">指示的哪些處理程序來執行 docker</span><span class="sxs-lookup"><span data-stu-id="bfb80-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="bfb80-115">您可以設定內部迴圈開發工作流程，利用 Docker 處理序 （下一節中所述）。</span><span class="sxs-lookup"><span data-stu-id="bfb80-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="bfb80-116">請考慮設定環境的初始步驟不包含在內，因為您只需要進行一次。</span><span class="sxs-lookup"><span data-stu-id="bfb80-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="bfb80-117">建置使用 Visual Studio Code 和 Docker CLI 的 Docker 容器內的單一應用程式</span><span class="sxs-lookup"><span data-stu-id="bfb80-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="bfb80-118">應用程式是由您自己的服務加上額外的程式庫 （相依性） 所組成。</span><span class="sxs-lookup"><span data-stu-id="bfb80-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="bfb80-119">圖 4-22 顯示您通常需要執行時建置的 Docker 應用程式，後面接著每個步驟的詳細描述的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="bfb80-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![工作流程概觀：步驟 1-程式碼中，步驟 2-撰寫 Dockerfile，步驟 3-建立 Dockerfile，步驟 4 中所定義的映像-定義服務使用 docker-compose 檔案，步驟 5-執行容器或組成的應用程式，步驟 6-測試應用程式，步驟 7-推播開始外部迴圈 （CI/CD 管線），或繼續 developing。](./media/image19.png)

<span data-ttu-id="bfb80-121">**圖 4-22**。</span><span class="sxs-lookup"><span data-stu-id="bfb80-121">**Figure 4-22**.</span></span> <span data-ttu-id="bfb80-122">使用 Docker CLI 的容器化 Docker 應用程式的生命週期的高階工作流程</span><span class="sxs-lookup"><span data-stu-id="bfb80-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="bfb80-123">步驟 1：開始在 Visual Studio Code 中撰寫程式碼，並建立初始應用程式/服務基準</span><span class="sxs-lookup"><span data-stu-id="bfb80-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="bfb80-124">開發您的應用程式的方式是類似於未 Docker 的方式。</span><span class="sxs-lookup"><span data-stu-id="bfb80-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="bfb80-125">差別在於，在開發時，您要部署與測試您的應用程式或服務放在您的本機環境 （例如 Linux VM 或 Windows） 中的 Docker 容器內執行。</span><span class="sxs-lookup"><span data-stu-id="bfb80-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="bfb80-126">**設定您的本機環境**</span><span class="sxs-lookup"><span data-stu-id="bfb80-126">**Setting up your local environment**</span></span>

<span data-ttu-id="bfb80-127">使用適用於 Mac 和 Windows 的 Docker 的最新版本，這遠比以往若要開發 Docker 應用程式，而且安裝程式是直接的。</span><span class="sxs-lookup"><span data-stu-id="bfb80-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!INFORMATION]
>
> <span data-ttu-id="bfb80-129">如需有關設定 Docker for Windows 的指示，請移至<https://docs.docker.com/docker-for-windows/>。</span><span class="sxs-lookup"><span data-stu-id="bfb80-129">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="bfb80-130">如需 Docker for Mac 設定指示，請移至<https://docs.docker.com/docker-for-mac/>。</span><span class="sxs-lookup"><span data-stu-id="bfb80-130">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="bfb80-131">此外，您需要的程式碼編輯器，讓您實際上可以開發應用程式時使用 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="bfb80-131">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="bfb80-132">Microsoft 提供的 Visual Studio Code 中，也就是支援 Mac、 Windows、 和 Linux 上，並提供 IntelliSense 的輕量型程式碼編輯器[支援用於多種語言](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、 Go、 Java、 Ruby、 Python 和大部分現代程式語言），[偵錯](https://code.visualstudio.com/Docs/editor/debugging)，[與 Git 整合](https://code.visualstudio.com/Docs/editor/versioncontrol)並[延伸模組支援](https://code.visualstudio.com/docs/extensions/overview)。</span><span class="sxs-lookup"><span data-stu-id="bfb80-132">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="bfb80-133">此編輯器是適用於 Mac 和 Linux 的開發人員的絕佳選擇。</span><span class="sxs-lookup"><span data-stu-id="bfb80-133">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="bfb80-134">在 Windows 中，您也可以使用完整的 Visual Studio 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfb80-134">In Windows, you also can use the full Visual Studio application.</span></span>

> [!INFORMATION]
>
> <span data-ttu-id="bfb80-136">如需安裝 Visual Studio 程式碼的 Windows、 Mac 或 Linux 的指示，請移至<https://code.visualstudio.com/docs/setup/setup-overview/>。</span><span class="sxs-lookup"><span data-stu-id="bfb80-136">For instructions on installing Visual Studio Code for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="bfb80-137">如需 Docker for Mac 設定指示，請移至<https://docs.docker.com/docker-for-mac/>。</span><span class="sxs-lookup"><span data-stu-id="bfb80-137">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="bfb80-138">您可以使用 Docker CLI，並撰寫程式碼，使用任何程式碼編輯器中，但使用 Visual Studio Code 的 Docker 擴充功能可輕鬆為作者`Dockerfile`和`docker-compose.yml`工作區中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bfb80-138">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="bfb80-139">您也可以從 Visual Studio 程式碼 IDE，來執行 Docker 命令使用 Docker CLI 之下執行工作和指令碼。</span><span class="sxs-lookup"><span data-stu-id="bfb80-139">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="bfb80-140">適用於 VS Code Docker 擴充功能提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="bfb80-140">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="bfb80-141">自動`Dockerfile`和`docker-compose.yml`檔案產生</span><span class="sxs-lookup"><span data-stu-id="bfb80-141">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="bfb80-142">語法反白顯示並暫留秘訣`docker-compose.yml`和`Dockerfile`檔案</span><span class="sxs-lookup"><span data-stu-id="bfb80-142">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="bfb80-143">（完成） 適用於 IntelliSense`Dockerfile`和`docker-compose.yml`檔案</span><span class="sxs-lookup"><span data-stu-id="bfb80-143">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="bfb80-144">Linting （錯誤和警告）`Dockerfile`檔案</span><span class="sxs-lookup"><span data-stu-id="bfb80-144">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="bfb80-145">最常見的 Docker 命令的命令選擇區 (F1) 整合</span><span class="sxs-lookup"><span data-stu-id="bfb80-145">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="bfb80-146">總管的整合來管理映像和容器</span><span class="sxs-lookup"><span data-stu-id="bfb80-146">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="bfb80-147">部署至 Azure App Service 從 DockerHub 和 Azure Container Registry 的映像</span><span class="sxs-lookup"><span data-stu-id="bfb80-147">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="bfb80-148">若要安裝 Docker 擴充功能中，按下 Ctrl + Shift + P，輸入`ext install`，然後執行安裝的延伸模組命令，以顯示 Marketplace 延伸模組清單。</span><span class="sxs-lookup"><span data-stu-id="bfb80-148">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="bfb80-149">接下來，輸入**docker**來篩選結果，並如上圖中 圖 4 月 23 日，然後選取支援 Docker 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="bfb80-149">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![適用於 VS Code 的 Docker 擴充功能檢視。](./media/image20.png)

<span data-ttu-id="bfb80-151">**圖 4-23**：</span><span class="sxs-lookup"><span data-stu-id="bfb80-151">**Figure 4-23**.</span></span> <span data-ttu-id="bfb80-152">Visual Studio Code 中安裝 Docker 擴充功能</span><span class="sxs-lookup"><span data-stu-id="bfb80-152">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="bfb80-153">步驟 2：建立 DockerFile，現有的映像 （純文字的 OS 或開發環境，例如.NET Core、 Node.js 和 Ruby） 相關</span><span class="sxs-lookup"><span data-stu-id="bfb80-153">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="bfb80-154">您將需要`DockerFile`每個要建置的自訂映像，以及每個要部署的容器。</span><span class="sxs-lookup"><span data-stu-id="bfb80-154">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="bfb80-155">如果您的應用程式組成單一的自訂服務，您將需要單一`DockerFile`。</span><span class="sxs-lookup"><span data-stu-id="bfb80-155">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="bfb80-156">但如果您的應用程式所組成 （就像在微服務架構） 的多個服務，您將需要一個`Dockerfile`每項服務。</span><span class="sxs-lookup"><span data-stu-id="bfb80-156">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="bfb80-157">`DockerFile`常放在您的應用程式或服務的根資料夾，而包含必要的命令，因此 Docker 知道如何設定及執行該應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="bfb80-157">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="bfb80-158">您可以建立您`DockerFile`並將它新增至您的專案，以及您的程式碼 (.NET Core、 node.js 等)，或如果您還不熟悉的環境，看看以下的提示。</span><span class="sxs-lookup"><span data-stu-id="bfb80-158">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
>
> <span data-ttu-id="bfb80-159">您可以使用 Docker 擴充功能來引導您使用`Dockerfile`和`docker-compose.yml`Docker 容器的相關檔案。</span><span class="sxs-lookup"><span data-stu-id="bfb80-159">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="bfb80-160">最後，您可能會撰寫這類檔案，而這項工具，但使用 Docker 擴充功能是不錯的起點，將可加速您的學習曲線。</span><span class="sxs-lookup"><span data-stu-id="bfb80-160">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="bfb80-161">在 圖 4-24，您可以看到如何 docker-compose 檔案會加入適用於 VS Code 中使用 Docker 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="bfb80-161">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![主控台檢視的 Docker 擴充功能適用於 VS Code。](./media/image24.png)

<span data-ttu-id="bfb80-163">**圖 4-24**：</span><span class="sxs-lookup"><span data-stu-id="bfb80-163">**Figure 4-24**.</span></span> <span data-ttu-id="bfb80-164">Docker 檔案已新增使用**新增 Docker 檔案至工作區命令**</span><span class="sxs-lookup"><span data-stu-id="bfb80-164">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="bfb80-165">當您新增 DockerFile 時，您會指定您要使用哪些基礎 Docker 映像 (例如使用`FROM mcr.microsoft.com/dotnet/core/aspnet`)。</span><span class="sxs-lookup"><span data-stu-id="bfb80-165">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="bfb80-166">您通常會建置您自訂的映像，在您從在任何官方存放庫取得的基底映像之上[Docker Hub 登錄](https://hub.docker.com/)(像是[適用於.NET Core 的映像](https://hub.docker.com/_/microsoft-dotnet-core/)或[適用於 Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="bfb80-166">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="bfb80-167">***使用現有的正式 Docker 映像***</span><span class="sxs-lookup"><span data-stu-id="bfb80-167">***Use an existing official Docker image***</span></span>

<span data-ttu-id="bfb80-168">使用版本號碼的語言在堆疊的官方存放庫可確保可以相同的語言功能 （包括開發、 測試和生產環境） 的所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="bfb80-168">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="bfb80-169">以下是.NET Core 容器的範例 DockerFile:</span><span class="sxs-lookup"><span data-stu-id="bfb80-169">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="bfb80-170">在此情況下，映像為基礎的官方 ASP.NET Core Docker 映像 （適用於 Linux 和 Windows 的多架構），根據列 2.1 版`FROM mcr.microsoft.com/dotnet/core/aspnet:2.1`。</span><span class="sxs-lookup"><span data-stu-id="bfb80-170">In this case, the image is based on version 2.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.1`.</span></span> <span data-ttu-id="bfb80-171">(如需有關本主題的詳細資訊，請參閱 < [ASP.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)頁面並[.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core/)頁面)。</span><span class="sxs-lookup"><span data-stu-id="bfb80-171">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="bfb80-172">在 DockerFile 中，您也可以指示 Docker 接聽 TCP 連接埠，您將使用在執行階段 （例如連接埠 80）。</span><span class="sxs-lookup"><span data-stu-id="bfb80-172">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="bfb80-173">您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。</span><span class="sxs-lookup"><span data-stu-id="bfb80-173">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="bfb80-174">比方說，`ENTRYPOINT`使用直線`["dotnet", "MySingleContainerWebApp.dll"]`會指示 Docker 執行.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfb80-174">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="bfb80-175">如果您使用 SDK 和.NET Core CLI (`dotnet CLI`) 若要建置及執行.NET 應用程式，此設定會有所不同。</span><span class="sxs-lookup"><span data-stu-id="bfb80-175">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="bfb80-176">此處的重點是 ENTRYPOINT 行與其他設定，取決於您為您的應用程式選擇的語言及平台。</span><span class="sxs-lookup"><span data-stu-id="bfb80-176">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!INFORMATION]
>
> <span data-ttu-id="bfb80-178">如需有關如何建置.NET Core 應用程式的 Docker 映像的詳細資訊，請移至<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。</span><span class="sxs-lookup"><span data-stu-id="bfb80-178">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="bfb80-179">若要深入了解如何建置自己的映像，請移至<https://docs.docker.com/engine/tutorials/dockerimages/>。</span><span class="sxs-lookup"><span data-stu-id="bfb80-179">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="bfb80-180">**使用多架構映像儲存機制**</span><span class="sxs-lookup"><span data-stu-id="bfb80-180">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="bfb80-181">存放庫中的單一映像名稱可以包含多種平台變化，例如 Linux 映像和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="bfb80-181">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="bfb80-182">這項功能可讓像 Microsoft （基底映像建立者） 的廠商建立單一的存放庫，以涵蓋多個平台 （也就是 Linux 和 Windows）。</span><span class="sxs-lookup"><span data-stu-id="bfb80-182">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="bfb80-183">例如， [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)在 Docker Hub 登錄存放庫會提供適用於 Linux 和 Windows Nano Server 支援使用相同的映像名稱。</span><span class="sxs-lookup"><span data-stu-id="bfb80-183">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="bfb80-184">提取[dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)從 Windows 主機的映像會提取 Windows variant，而從 Linux 主機提取相同的映像名稱會提取 Linux variant。</span><span class="sxs-lookup"><span data-stu-id="bfb80-184">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="bfb80-185">***從頭開始建立您的基底映像***</span><span class="sxs-lookup"><span data-stu-id="bfb80-185">***Create your base image from scratch***</span></span>

<span data-ttu-id="bfb80-186">在此所述，您可以從頭建立您自己的 Docker 基礎映像[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)從 Docker。</span><span class="sxs-lookup"><span data-stu-id="bfb80-186">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="bfb80-187">這種情況下可能不是最適合您，如果您剛開始使用 Docker，但如果您想要設定您自己的基底映像的特定位元，您可以執行它。</span><span class="sxs-lookup"><span data-stu-id="bfb80-187">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="bfb80-188">步驟 3：建立自訂 Docker 映像嵌入您的服務</span><span class="sxs-lookup"><span data-stu-id="bfb80-188">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="bfb80-189">針對每個包含您的應用程式的自訂服務，您必須建立相關的映像。</span><span class="sxs-lookup"><span data-stu-id="bfb80-189">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="bfb80-190">如果您的應用程式組成的單一服務或 web 應用程式，您將需要一張圖片。</span><span class="sxs-lookup"><span data-stu-id="bfb80-190">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
>
> <span data-ttu-id="bfb80-191">當考慮 「 外部迴圈 DevOps 工作流程 」，每當您您的程式碼從推送至 Git 存放庫 （持續整合），因此會在全域環境中建立映像時，就會自動化的建置程序建立映像您原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="bfb80-191">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="bfb80-192">但我們考慮移到該外部迴圈路由之前，我們需要確保 Docker 應用程式實際運作正常，讓它們不會推送程式碼，可能無法正常運作 （Git 等等），才會進行來源控制系統。</span><span class="sxs-lookup"><span data-stu-id="bfb80-192">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="bfb80-193">因此，每位開發人員第一次需要整個 「 內部迴圈 」 程序，在本機測試，並繼續開發，直到他們想要推送完整的功能或變更原始檔控制系統。</span><span class="sxs-lookup"><span data-stu-id="bfb80-193">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="bfb80-194">在您的本機環境中和使用 DockerFile 建立映像，您可以使用 docker build 命令，在圖 4-25 示 (您也可以執行`docker-compose up --build`由數個容器/服務所組成的應用程式)。</span><span class="sxs-lookup"><span data-stu-id="bfb80-194">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Docker-compose build，顯示下載進度的映像的主控台輸出。](./media/image25.png)

<span data-ttu-id="bfb80-196">**圖 4-25**：</span><span class="sxs-lookup"><span data-stu-id="bfb80-196">**Figure 4-25**.</span></span> <span data-ttu-id="bfb80-197">執行 docker 建置</span><span class="sxs-lookup"><span data-stu-id="bfb80-197">Running docker build</span></span>

<span data-ttu-id="bfb80-198">（選擇性） 而不是直接執行`docker build`從 [專案] 資料夾中，您第一次可以產生可部署資料夾使用執行所需的.NET 程式庫`dotnet publish`命令，然後再執行`docker build`。</span><span class="sxs-lookup"><span data-stu-id="bfb80-198">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="bfb80-199">此範例會使用名稱來建立 Docker 映像`cesardl/netcore-webapi-microservice-docker:first`(`:first`是標記，例如特定的版本)。</span><span class="sxs-lookup"><span data-stu-id="bfb80-199">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="bfb80-200">您可以採取此步驟中的每個您需要建立數個容器組成 Docker 應用程式的自訂映像。</span><span class="sxs-lookup"><span data-stu-id="bfb80-200">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="bfb80-201">您可以找到現有的映像在本機存放庫 （您的開發電腦） 中使用 docker images 命令所示的圖 4-26。</span><span class="sxs-lookup"><span data-stu-id="bfb80-201">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![主控台輸出命令 docker 映像，顯示現有的映像。](./media/image26.png)

<span data-ttu-id="bfb80-203">**圖 4-26**。</span><span class="sxs-lookup"><span data-stu-id="bfb80-203">**Figure 4-26**.</span></span> <span data-ttu-id="bfb80-204">檢視現有的映像使用 docker 映像</span><span class="sxs-lookup"><span data-stu-id="bfb80-204">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="bfb80-205">步驟 4：建置具有多個服務的組成的 Docker 應用程式時，在 docker-compose.yml 中定義您的服務</span><span class="sxs-lookup"><span data-stu-id="bfb80-205">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="bfb80-206">使用`docker-compose.yml`檔案中，您可以定義一組相關的服務一起部署為組成的應用程式的下一個步驟一節所述的部署命令。</span><span class="sxs-lookup"><span data-stu-id="bfb80-206">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="bfb80-207">建立該檔案在您的 main 或根解決方案資料夾;它應該類似於此所示的內容`docker-compose.yml`檔案：</span><span class="sxs-lookup"><span data-stu-id="bfb80-207">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

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

<span data-ttu-id="bfb80-208">在此案例中，此檔案會定義兩個服務： web 服務 （您自訂的服務） 和 redis 服務 （受歡迎的快取服務）。</span><span class="sxs-lookup"><span data-stu-id="bfb80-208">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="bfb80-209">每個服務會部署為容器，，因此我們要用於每個具體的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="bfb80-209">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="bfb80-210">此特定的 web 服務，影像必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="bfb80-210">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="bfb80-211">建立從目前的目錄中的 DockerFile</span><span class="sxs-lookup"><span data-stu-id="bfb80-211">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="bfb80-212">轉送公開的連接埠 80 上的容器在主機電腦上的連接埠 81</span><span class="sxs-lookup"><span data-stu-id="bfb80-212">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="bfb80-213">讓您修改程式碼，而不需要重建映像的容器內的 /code 主機上掛接專案目錄</span><span class="sxs-lookup"><span data-stu-id="bfb80-213">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="bfb80-214">連結至 redis 服務的 web 服務</span><span class="sxs-lookup"><span data-stu-id="bfb80-214">Link the web service to the redis service</span></span>

<span data-ttu-id="bfb80-215">Redis 服務會使用[最新的公用 redis 映像](https://hub.docker.com/_/redis/)從 Docker Hub 登錄提取。</span><span class="sxs-lookup"><span data-stu-id="bfb80-215">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="bfb80-216">[redis](https://redis.io/)是伺服器端應用程式的受歡迎的快取系統。</span><span class="sxs-lookup"><span data-stu-id="bfb80-216">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="bfb80-217">步驟 5：建置並執行您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="bfb80-217">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="bfb80-218">如果您的應用程式有單一容器，您只需要藉由將它部署至您的 Docker 主機 （VM 或實體伺服器） 執行它。</span><span class="sxs-lookup"><span data-stu-id="bfb80-218">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="bfb80-219">不過，如果您的應用程式多個服務組成，您需要*組合*也。</span><span class="sxs-lookup"><span data-stu-id="bfb80-219">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="bfb80-220">讓我們看到不同的選項。</span><span class="sxs-lookup"><span data-stu-id="bfb80-220">Let's see the different options.</span></span>

<span data-ttu-id="bfb80-221">***選項 a:執行單一容器或服務***</span><span class="sxs-lookup"><span data-stu-id="bfb80-221">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="bfb80-222">您可以執行的 Docker 映像使用 docker run 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bfb80-222">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="bfb80-223">針對此特定的部署，我們將會將要求重新導向傳送至連接埠 80 的內部連接埠 5000。</span><span class="sxs-lookup"><span data-stu-id="bfb80-223">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="bfb80-224">現在應用程式正在接聽的外部連接埠 80，在主機層級。</span><span class="sxs-lookup"><span data-stu-id="bfb80-224">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="bfb80-225">***選項 b:撰寫和執行多容器應用程式***</span><span class="sxs-lookup"><span data-stu-id="bfb80-225">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="bfb80-226">在大部分的企業案例中，將多個服務組成 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfb80-226">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="bfb80-227">在這些情況下，您可以執行`docker-compose up`命令 (圖 4-27)，將使用您可能會有先前建立的 docker compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="bfb80-227">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="bfb80-228">執行此命令會部署所有及其相關容器組成的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfb80-228">Running this command deploys a composed application with all of its related containers.</span></span>

![主控台輸出 docker compose up 命令。](./media/image27.png)

<span data-ttu-id="bfb80-230">**圖 4-27**。</span><span class="sxs-lookup"><span data-stu-id="bfb80-230">**Figure 4-27**.</span></span> <span data-ttu-id="bfb80-231">執行 「 啟動 docker compose"命令的結果</span><span class="sxs-lookup"><span data-stu-id="bfb80-231">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="bfb80-232">執行之後`docker-compose up`，您將部署應用程式和其相關的容器到您的 Docker 主機中所示的圖 4-28，呈現的 VM。</span><span class="sxs-lookup"><span data-stu-id="bfb80-232">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![執行多容器應用程式的 VM。](./media/image28.png)

<span data-ttu-id="bfb80-234">**圖 4-28**。</span><span class="sxs-lookup"><span data-stu-id="bfb80-234">**Figure 4-28**.</span></span> <span data-ttu-id="bfb80-235">部署了 Docker 容器的 VM</span><span class="sxs-lookup"><span data-stu-id="bfb80-235">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="bfb80-236">步驟 6：測試 Docker 應用程式 （在本機，在您本機的 CD VM)</span><span class="sxs-lookup"><span data-stu-id="bfb80-236">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="bfb80-237">此步驟會因應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="bfb80-237">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="bfb80-238">中的簡單.NET Core Web API"Hello World"部署為單一容器或服務，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。</span><span class="sxs-lookup"><span data-stu-id="bfb80-238">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="bfb80-239">如果 localhost 未開啟，以瀏覽至您的服務，尋找電腦的 IP 位址，使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="bfb80-239">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="bfb80-240">在 Docker 主機上，開啟瀏覽器並瀏覽至該網站;示範在圖 4-29，應該會看到執行中，您的應用程式/服務。</span><span class="sxs-lookup"><span data-stu-id="bfb80-240">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![從 localhost/API/values 回應的瀏覽器檢視。](./media/image29.png)

<span data-ttu-id="bfb80-242">**圖 4-29**。</span><span class="sxs-lookup"><span data-stu-id="bfb80-242">**Figure 4-29**.</span></span> <span data-ttu-id="bfb80-243">測試使用 localhost 在本機的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="bfb80-243">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="bfb80-244">請注意，它使用連接埠 80，但在內部會被重新導向至連接埠 5000，因為這是如何部署與`docker run`，如先前所述。</span><span class="sxs-lookup"><span data-stu-id="bfb80-244">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="bfb80-245">您可以從終端機使用 CURL 來測試。</span><span class="sxs-lookup"><span data-stu-id="bfb80-245">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="bfb80-246">在 Docker 安裝在 Windows 中，預設值是 IP 10.0.75.1，如上圖中圖 4-30。</span><span class="sxs-lookup"><span data-stu-id="bfb80-246">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![主控台輸出取得 http://10.0.75.1/API/values與 curl](./media/image30.png)

<span data-ttu-id="bfb80-248">**圖 4-30**。</span><span class="sxs-lookup"><span data-stu-id="bfb80-248">**Figure 4-30**.</span></span> <span data-ttu-id="bfb80-249">由使用 CURL 在本機測試 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="bfb80-249">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="bfb80-250">**偵錯在 Docker 上執行的容器**</span><span class="sxs-lookup"><span data-stu-id="bfb80-250">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="bfb80-251">Visual Studio Code 支援偵錯的 Docker，如果您使用 Node.js 和.NET Core 容器等其他平台。</span><span class="sxs-lookup"><span data-stu-id="bfb80-251">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="bfb80-252">您也可以偵錯在 Docker 中的.NET Core 或.NET Framework 的容器時使用 Visual Studio for Windows 或 Mac 下, 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="bfb80-252">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!INFORMATION]
>
> <span data-ttu-id="bfb80-254">若要深入了解偵錯 Node.js Docker 容器，請前往<https://blog.docker.com/2016/07/live-debugging-docker/>和<https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>。</span><span class="sxs-lookup"><span data-stu-id="bfb80-254">To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bfb80-255">[上一頁](docker-apps-development-environment.md)
>[下一頁](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="bfb80-255">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
