---
title: "Docker 應用程式的內部迴圈的開發工作流程"
description: "Microsoft 平台和工具的容器化 Docker 應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 632c04507c1478238a5dc2573542f8c88bae2a51
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="d6039-104">Docker 應用程式的內部迴圈的開發工作流程</span><span class="sxs-lookup"><span data-stu-id="d6039-104">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="d6039-105">觸發跨越整個 DevOps 外部迴圈工作流程之前循環，所有開始每位開發人員在電腦上，撰寫程式碼應用程式本身、 使用其偏好的語言或平台，以及在本機測試它 (圖 4-14)。</span><span class="sxs-lookup"><span data-stu-id="d6039-105">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="d6039-106">但在每個案例中，您會有一點很重要共通點，無論您選擇何種語言、 架構或平台。</span><span class="sxs-lookup"><span data-stu-id="d6039-106">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="d6039-107">在此特定的工作流程，您一律開發和測試 Docker 容器，但只能在本機。</span><span class="sxs-lookup"><span data-stu-id="d6039-107">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="d6039-108">圖 4-14： 內部迴圈開發內容</span><span class="sxs-lookup"><span data-stu-id="d6039-108">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="d6039-109">容器或 Docker 映像的執行個體將會包含這些元件：</span><span class="sxs-lookup"><span data-stu-id="d6039-109">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="d6039-110">作業系統的選取範圍 （例如 Linux 散發套件或 Windows）</span><span class="sxs-lookup"><span data-stu-id="d6039-110">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="d6039-111">加入的開發人員 （例如，應用程式二進位檔） 檔案</span><span class="sxs-lookup"><span data-stu-id="d6039-111">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="d6039-112">設定 （例如，環境設定和相依性）</span><span class="sxs-lookup"><span data-stu-id="d6039-112">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="d6039-113">若要執行 Docker 哪些處理程序指示</span><span class="sxs-lookup"><span data-stu-id="d6039-113">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="d6039-114">您可以設定為 （下一節中所述） 的程序會利用 Docker 內部迴圈開發工作流程。</span><span class="sxs-lookup"><span data-stu-id="d6039-114">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="d6039-115">考慮設定環境的初始步驟不包含在內，因為您需要這樣做，就可以一次。</span><span class="sxs-lookup"><span data-stu-id="d6039-115">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="d6039-116">建置 Visual Studio 程式碼和 Docker CLI 使用 Docker 容器內的單一應用程式</span><span class="sxs-lookup"><span data-stu-id="d6039-116">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="d6039-117">應用程式會啟動從您的服務，再加上額外的程式庫 （相依性）。</span><span class="sxs-lookup"><span data-stu-id="d6039-117">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="d6039-118">圖 4-15 會顯示您通常需要時建置 Docker 應用程式，後面接著每個步驟的詳細描述執行的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="d6039-118">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="d6039-119">圖 4-15： 使用 Docker CLI Docker 容器化應用程式生命週期的高層級工作流程</span><span class="sxs-lookup"><span data-stu-id="d6039-119">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="d6039-120">步驟 1： 開始撰寫程式碼在 Visual Studio 程式碼中，並建立初始應用程式/服務基準</span><span class="sxs-lookup"><span data-stu-id="d6039-120">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="d6039-121">開發應用程式的方式是不 Docker 的方式很類似。</span><span class="sxs-lookup"><span data-stu-id="d6039-121">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="d6039-122">差別在於，在開發時，會在部署並測試您的應用程式或放在本機環境 （例如 Linux VM 或 Windows） 的 Docker 容器內執行的服務。</span><span class="sxs-lookup"><span data-stu-id="d6039-122">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="d6039-123">**設定您的本機環境**</span><span class="sxs-lookup"><span data-stu-id="d6039-123">**Setting up your local environment**</span></span>

<span data-ttu-id="d6039-124">Docker for Mac 和 Windows 的最新版本，比以往若要開發 Docker 應用程式，更輕鬆與安裝程式將更為簡單。</span><span class="sxs-lookup"><span data-stu-id="d6039-124">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="d6039-125">**進一歩** 如需有關設定 Docker for Windows 的指示，請移至[https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)。</span><span class="sxs-lookup"><span data-stu-id="d6039-125">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="d6039-126">如需 Docker for Mac 設定指示，請移至<https://docs.docker.com/docker-for-mac/>。</span><span class="sxs-lookup"><span data-stu-id="d6039-126">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="d6039-127">此外，您必須在程式碼編輯器，讓您實際上可以開發的應用程式使用 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="d6039-127">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="d6039-128">Microsoft 提供 Visual Studio 程式碼，其中是輕量型的程式碼編輯器支援 Mac、 Windows 和 Linux 上並提供 IntelliSense[多語言支援](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、 Go、 Java、 Ruby、 Python 和大部分現代的語言），[偵錯](https://code.visualstudio.com/Docs/editor/debugging)，[與 Git 整合](https://code.visualstudio.com/Docs/editor/versioncontrol)和[延伸模組支援](https://code.visualstudio.com/docs/extensions/overview)。</span><span class="sxs-lookup"><span data-stu-id="d6039-128">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="d6039-129">此編輯器是適用於 Mac 和 Linux 的開發人員的絕佳符合。</span><span class="sxs-lookup"><span data-stu-id="d6039-129">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="d6039-130">在 Windows 中，您也可以使用完整的 Visual Studio 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6039-130">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="d6039-131">**進一歩** 如需安裝 Visual Studio for Windows、 Mac 或 Linux 的指示，請移至[http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/)。</span><span class="sxs-lookup"><span data-stu-id="d6039-131">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span></span>

<span data-ttu-id="d6039-132">您可以使用 Docker CLI，並撰寫程式碼，使用任何程式碼編輯器 中，但如果您使用 Visual Studio 程式碼，它可以輕鬆地撰寫 Dockerfile 和 docker compose.yml 檔案工作區中。</span><span class="sxs-lookup"><span data-stu-id="d6039-132">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="d6039-133">此外，您可以從 IDE，以提示可以執行複雜的作業使用 Docker CLI 底下的指令碼執行 Visual Studio 程式碼工作。</span><span class="sxs-lookup"><span data-stu-id="d6039-133">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="d6039-134">Visual Studio 程式碼係由延伸模組，您必須安裝。</span><span class="sxs-lookup"><span data-stu-id="d6039-134">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="d6039-135">若要這樣做，請按 Ctrl + Shift + P，輸入**ext 安裝**，然後執行 延伸模組： 安裝延伸模組命令，以顯示 Marketplace 擴充功能清單。</span><span class="sxs-lookup"><span data-stu-id="d6039-135">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="d6039-136">接著，輸入**docker**來篩選結果，然後選取 Dockerfile 和 Docker 撰寫檔案 (yml) 支援擴充功能，如圖 4-16。</span><span class="sxs-lookup"><span data-stu-id="d6039-136">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="d6039-137">圖 4-16： 安裝 Visual Studio 程式碼中的 Docker 擴充功能</span><span class="sxs-lookup"><span data-stu-id="d6039-137">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="d6039-138">步驟 2： 建立 DockerFile，現有的映像 （純文字的 OS 或開發環境，例如.NET Core、 Node.js 和 Ruby） 相關</span><span class="sxs-lookup"><span data-stu-id="d6039-138">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="d6039-139">您需要 DockerFile 每個要建置自訂的影像和每個要部署的容器，因此，如果您的應用程式由單一的自訂服務所組成，您將需要單一 DockerFile。</span><span class="sxs-lookup"><span data-stu-id="d6039-139">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="d6039-140">但是，如果您的應用程式所組成 （如同 microservices 架構） 的多個服務，您將需要每個服務的一個 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="d6039-140">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="d6039-141">DockerFile 通常會放在應用程式或服務的根資料夾內，並包含所需的命令，讓該 Docker 知道如何設定及執行該應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="d6039-141">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="d6039-142">您可以建立 DockerFile，並將它加入至您的專案中，以及您的程式碼 (.NET Core node.js 等等)，或如果您不熟悉的環境，看看下列提示。</span><span class="sxs-lookup"><span data-stu-id="d6039-142">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="d6039-143">您可以使用命令列工具，稱為[yo docker](https://github.com/Microsoft/generator-docker)，其中 scaffold 從您的專案，在您選擇的語言新增必要的 Docker 組態檔中的檔案。</span><span class="sxs-lookup"><span data-stu-id="d6039-143">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="d6039-144">基本上，來協助開發人員快速入門，它會建立適當的 DockerFile 中，docker compose.yml 和其他相關聯的指令碼，以建置並執行 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="d6039-144">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="d6039-145">此 yeoman 產生器會提示您要求您選取的開發語言和目的地容器主機的幾個問題。</span><span class="sxs-lookup"><span data-stu-id="d6039-145">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![yo docker](./media/image21.png)

<span data-ttu-id="d6039-147">比方說，圖 4-17 顯示兩個螢幕擷取畫面，將終端機視窗中，以及在 Mac 上，在這兩種情況下，執行 yo docker，將會產生的範例程式碼專案 （目前.NET Core、 Golang 和支援的語言為 Node.js） 已設定成使用Docker 的頂端。</span><span class="sxs-lookup"><span data-stu-id="d6039-147">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="d6039-148">圖 4-17: yo docker 命令在 Windows 中 （左），並在 Mac 上的工具</span><span class="sxs-lookup"><span data-stu-id="d6039-148">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="d6039-149">圖 4-18 顯示 yo docker 後使用您已有現有的.NET Core 專案會建立結構的範例。</span><span class="sxs-lookup"><span data-stu-id="d6039-149">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="d6039-150">圖 4-18: yo docker 與現有的.NET Core 專案中的位置</span><span class="sxs-lookup"><span data-stu-id="d6039-150">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="d6039-151">DockerFile 中，從您指定哪些基底的 Docker 映像，選擇您要使用 （例如使用 從 microsoft/dotnet:1.0.0-core"）。</span><span class="sxs-lookup"><span data-stu-id="d6039-151">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="d6039-152">您通常會建置您自訂的映像，您可以從任何正式儲存機制取得基底映像之上[Docker Hub 登錄](https://hub.docker.com/)(像是[適用於.NET Core 的映像](https://hub.docker.com/r/microsoft/dotnet/)或一個[for Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="d6039-152">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="d6039-153">***選項 a： 使用現有的官方 Docker 映像***</span><span class="sxs-lookup"><span data-stu-id="d6039-153">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="d6039-154">使用版本號碼為語言堆疊官方儲存機制可確保可以相同的語言功能 （包括開發、 測試和生產環境） 的所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="d6039-154">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="d6039-155">以下是範例 DockerFile.NET Core 容器：</span><span class="sxs-lookup"><span data-stu-id="d6039-155">Following is a sample DockerFile for a .NET Core container:</span></span>

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="d6039-156">在此情況下，它適用於 Linux 名為 microsoft/aspnetcore:1.0.1 使用 1.0.1 版的官方 ASP.NET Core Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="d6039-156">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="d6039-157">如需詳細資訊，請參閱[ASP.NET Core Docker 映像頁面](https://hub.docker.com/r/microsoft/aspnetcore/)和[.NET Core Docker 映像頁面](https://hub.docker.com/r/microsoft/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="d6039-157">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="d6039-158">您也可以使用另一個可比較像的映像節點： 4-Node.js 或開發語言，可從許多其他預先設定的影像 onbuild [Docker Hub](https://hub.docker.com/explore/)。</span><span class="sxs-lookup"><span data-stu-id="d6039-158">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="d6039-159">在 DockerFile 中，您也需要會指示 Docker 以接聽 TCP 通訊埠，您將使用在執行階段 （例如連接埠 80）。</span><span class="sxs-lookup"><span data-stu-id="d6039-159">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="d6039-160">有其他您可以根據您使用的語言/架構 DockerFile 中新增讓 Docker 知道如何執行應用程式的組態中的行。</span><span class="sxs-lookup"><span data-stu-id="d6039-160">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="d6039-161">例如，您需要的進入點線條\["dotnet"，"MyCustomMicroservice.dll"\]執行是.NET Core 應用程式中，雖然您可以根據要建置並執行您的服務方法的多個變異。</span><span class="sxs-lookup"><span data-stu-id="d6039-161">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="d6039-162">如果您使用的 SDK 和 dotnet CLI 建置並執行.NET 應用程式，它會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="d6039-162">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="d6039-163">營收是進入點的行，加上額外的線條將會根據您選擇您的應用程式的語言/平台而不同。</span><span class="sxs-lookup"><span data-stu-id="d6039-163">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="d6039-164">**進一歩** 建置.NET Core 應用程式的 Docker 映像的相關資訊，請移至<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。</span><span class="sxs-lookup"><span data-stu-id="d6039-164">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="d6039-165">若要了解如何建置自己的映像，請前往[https://docs.docker.com/engine/ \ 教學課程/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)。</span><span class="sxs-lookup"><span data-stu-id="d6039-165">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="d6039-166">**多平台映像儲存機制**</span><span class="sxs-lookup"><span data-stu-id="d6039-166">**Multiplatform image repositories**</span></span>

<span data-ttu-id="d6039-167">由於 Windows 容器變得更普遍的單一的存放庫可包含平台的變異，例如的 Linux 和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="d6039-167">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="d6039-168">這是一項新功能，可讓廠商使用單一的儲存機制以涵蓋多個平台，例如 Docker 的未來[microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)儲存機制，會使用可在 DockerHub 登錄。</span><span class="sxs-lookup"><span data-stu-id="d6039-168">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="d6039-169">功能都運作時，從 Windows 主機提取此映像將會提取 Windows 的變體，而在 Linux 主機從提取相同的映像名稱將會提取 Linux variant。</span><span class="sxs-lookup"><span data-stu-id="d6039-169">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="d6039-170">***選項 b： 建立您從頭的基底映像***</span><span class="sxs-lookup"><span data-stu-id="d6039-170">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="d6039-171">您可以從頭開始建立您自己的 Docker 基底映像中所述[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)從 Docker。</span><span class="sxs-lookup"><span data-stu-id="d6039-171">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="d6039-172">這是不可能最適合您如果您剛開始使用 Docker 的案例，但如果您想要設定特定的位元基底映像，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="d6039-172">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="d6039-173">步驟 3： 建立您自訂的 Docker 映像嵌入您的服務</span><span class="sxs-lookup"><span data-stu-id="d6039-173">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="d6039-174">針對每個包含您的應用程式的自訂服務，您必須建立相關的映像。</span><span class="sxs-lookup"><span data-stu-id="d6039-174">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="d6039-175">如果您的應用程式所組成的單一服務或 web 應用程式，您必須只以單一影像。</span><span class="sxs-lookup"><span data-stu-id="d6039-175">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="d6039-176">不顧及 「 外部迴圈 DevOps workflow"，影像將會建立由自動化的建置處理序時就是您推送您的程式碼至 Git 儲存機制 （連續整合） 因此會在全域環境中建立映像從您原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6039-176">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="d6039-177">但是，我們認為該外部迴圈路由時，將之前，我們需要確定 Docker 應用程式實際上運作正常，讓它們不發送可能無法正常運作 （Git 等等） 時，原始檔控制系統的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6039-177">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="d6039-178">因此，每位開發人員第一次需要進行整個內部迴圈處理序，在本機測試，並繼續開發，直到他們想要推送的完整功能，或變更原始檔控制系統。</span><span class="sxs-lookup"><span data-stu-id="d6039-178">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="d6039-179">若要在本機環境和使用 DockerFile 建立映像，您可以使用 docker 建置命令中，示圖 4-19 (您也可以執行 docker 撰寫向上-由數個的容器服務組成的應用程式的組建)。</span><span class="sxs-lookup"><span data-stu-id="d6039-179">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="d6039-180">圖 4-19： 執行 docker 建置</span><span class="sxs-lookup"><span data-stu-id="d6039-180">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="d6039-181">（選擇性） 而不是直接執行 docker 來建立專案的資料夾，則第一次可以產生可部署的資料夾與使用執行的 dotnet 發行命令，然後再執行 docker 建置所需的.NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="d6039-181">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="d6039-182">在此範例中，這會建立 Docker 映像名稱 cesardl/netcore-webapi-微服務-docker： 第一個 (: 第一個是標記，例如特定的版本)。</span><span class="sxs-lookup"><span data-stu-id="d6039-182">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="d6039-183">您可以採取此步驟，您必須建立數個容器與 Docker 組成應用程式的每個自訂映像。</span><span class="sxs-lookup"><span data-stu-id="d6039-183">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="d6039-184">您可以找到現有的映像在本機儲存機制 （在開發電腦） 中使用 docker 映像命令的說明圖 4-20。</span><span class="sxs-lookup"><span data-stu-id="d6039-184">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="d6039-185">圖 4-20： 檢視現有的映像使用 docker 映像</span><span class="sxs-lookup"><span data-stu-id="d6039-185">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="d6039-186">步驟 4: （選擇性） 定義 docker compose.yml 時建置含有多個服務組成的 Docker 應用程式中的服務</span><span class="sxs-lookup"><span data-stu-id="d6039-186">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="d6039-187">使用 docker compose.yml 檔案中，您可以定義一組相關的服務一起部署為組成的應用程式的下一個步驟中說明的部署命令。</span><span class="sxs-lookup"><span data-stu-id="d6039-187">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="d6039-188">您必須建立該檔案在您的 main 或根方案資料夾。下列 docker compose.yml 檔案應該類似的內容：</span><span class="sxs-lookup"><span data-stu-id="d6039-188">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

```yml
version: '2'
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

<span data-ttu-id="d6039-189">在此特定情況下，此檔案會定義兩個服務： web 服務 （您自訂的服務） 和 redis 服務 （熱門的快取服務）。</span><span class="sxs-lookup"><span data-stu-id="d6039-189">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="d6039-190">將當做容器時，部署每個服務，因此我們必須針對每個使用具體的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="d6039-190">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="d6039-191">此特定 web 服務、 映像必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d6039-191">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="d6039-192">從目前目錄中 DockerFile 建置</span><span class="sxs-lookup"><span data-stu-id="d6039-192">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="d6039-193">轉送公開的連接埠 80 上的容器主機上的連接埠 81</span><span class="sxs-lookup"><span data-stu-id="d6039-193">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="d6039-194">讓您修改程式碼，而不必重建映像容器內的 /code 在主機上裝載專案目錄</span><span class="sxs-lookup"><span data-stu-id="d6039-194">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="d6039-195">連結至 redis 服務的 web 服務</span><span class="sxs-lookup"><span data-stu-id="d6039-195">Link the web service to the redis service</span></span>

<span data-ttu-id="d6039-196">Redis 服務會使用[最新的公用 redis 映像](https://hub.docker.com/_/redis/)提取從 Docker Hub 登錄。</span><span class="sxs-lookup"><span data-stu-id="d6039-196">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="d6039-197">[redis](http://redis.io/)是非常普遍的快取系統的伺服器端應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6039-197">[redis](http://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="d6039-198">步驟 5： 建置並執行您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="d6039-198">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="d6039-199">如果您的應用程式具有單一容器，您只需要執行，請將它部署至您的 Docker 主機 （VM 或實體伺服器）。</span><span class="sxs-lookup"><span data-stu-id="d6039-199">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="d6039-200">不過，如果您的應用程式由多個服務所組成，您需要*撰寫*、 太。</span><span class="sxs-lookup"><span data-stu-id="d6039-200">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="d6039-201">我們來看看不同的選項。</span><span class="sxs-lookup"><span data-stu-id="d6039-201">Let's see the different options.</span></span>

<span data-ttu-id="d6039-202">***選項 a： 執行單一容器或服務***</span><span class="sxs-lookup"><span data-stu-id="d6039-202">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="d6039-203">您可以執行的 Docker 映像使用 docker run 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d6039-203">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="d6039-204">請注意，針對此特定的部署，我們會重新導向要求傳送至連接埠 80 的內部連接埠為 5000。</span><span class="sxs-lookup"><span data-stu-id="d6039-204">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="d6039-205">現在，應用程式正在接聽的外部連接埠 80，主機層級。</span><span class="sxs-lookup"><span data-stu-id="d6039-205">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="d6039-206">***選項 b： 撰寫和執行多個容器應用程式***</span><span class="sxs-lookup"><span data-stu-id="d6039-206">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="d6039-207">在大部分的企業案例中，Docker 應用程式將由多個服務。</span><span class="sxs-lookup"><span data-stu-id="d6039-207">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="d6039-208">這些情況下，您可以執行命令，docker 撰寫向上 (圖 4-21)，就會使用您可能會有先前建立的 docker compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="d6039-208">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="d6039-209">執行此命令會將部署組成的應用程式與它的所有相關容器。</span><span class="sxs-lookup"><span data-stu-id="d6039-209">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="d6039-210">圖 4-21： 執行"docker-撰寫"命令的結果</span><span class="sxs-lookup"><span data-stu-id="d6039-210">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="d6039-211">在執行 docker 之後-向上撰寫，您將應用程式和其相關的容器到您的 Docker 主機中所示在圖 4-22，VM 表示法。</span><span class="sxs-lookup"><span data-stu-id="d6039-211">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="d6039-212">圖 4-22: VM 部署的 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="d6039-212">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="d6039-213">注意 docker-撰寫向上 docker 執行可能不足以在您的開發環境中測試您的容器，但您可能不會使用它們完全如果您想要使用 Docker 群集，而且 orchestrators 像 Docker Swarm、 Mesosphere DC/作業系統或 Kubernetes若要能夠向上延展。</span><span class="sxs-lookup"><span data-stu-id="d6039-213">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="d6039-214">如果您使用類似的叢集[Docker Swarm 模式](https://docs.docker.com/engine/swarm/)（適用於 Docker for Windows 和 Mac 版本 1.12 之後），您需要部署和測試與其他命令，例如，docker 服務建立單一服務，或當您準備部署數個容器所組成的應用程式，使用 docker 撰寫組合和 docker 來組成的應用程式部署為堆疊，發行項中所述部署 myBundleFile，[分散式應用程式套件組合](https://blog.docker.com/2016/06/docker-app-bundle/)從 Docker。</span><span class="sxs-lookup"><span data-stu-id="d6039-214">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="d6039-215">如[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)和[Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment)您會使用不同的部署命令和指令碼，以及。</span><span class="sxs-lookup"><span data-stu-id="d6039-215">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="d6039-216">步驟 6： 測試您的 Docker 應用程式 （在本機，在您本機的 CD VM)</span><span class="sxs-lookup"><span data-stu-id="d6039-216">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="d6039-217">此步驟會因您的應用程式正在執行。</span><span class="sxs-lookup"><span data-stu-id="d6039-217">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="d6039-218">在非常簡單.NET Core Web 應用程式開發介面"Hello World"部署為單一容器或服務，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。</span><span class="sxs-lookup"><span data-stu-id="d6039-218">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="d6039-219">如果 localhost 未開啟，瀏覽至您的服務，尋找電腦的 IP 位址，使用這個命令：</span><span class="sxs-lookup"><span data-stu-id="d6039-219">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="d6039-220">docker 機器 ip*您的容器名稱*</span><span class="sxs-lookup"><span data-stu-id="d6039-220">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="d6039-221">Docker 主機上，開啟瀏覽器並瀏覽至該網站。您應該會看到您的應用程式/服務執行，如圖 4-23 所示範。</span><span class="sxs-lookup"><span data-stu-id="d6039-221">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="d6039-222">圖 4-23： 測試 Docker 應用程式在本機使用 localhost</span><span class="sxs-lookup"><span data-stu-id="d6039-222">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="d6039-223">請注意，它會使用通訊埠 80，內部它已被重新導向到 5000 之間，因為它的部署方式執行時，docker 稍早所述。</span><span class="sxs-lookup"><span data-stu-id="d6039-223">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="d6039-224">您可以使用 CURL 從終端機來測試。</span><span class="sxs-lookup"><span data-stu-id="d6039-224">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="d6039-225">在 Windows 上的 Docker 安裝，預設是 IP 10.0.75.1，如上圖 4-24。</span><span class="sxs-lookup"><span data-stu-id="d6039-225">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="d6039-226">圖 4-24： 由使用 CURL 在本機測試 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="d6039-226">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="d6039-227">**偵錯執行 docker 容器**</span><span class="sxs-lookup"><span data-stu-id="d6039-227">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="d6039-228">如果您使用 Node.js 和.NET Core 容器等其他平台，visual Studio 程式碼支援偵錯的 Docker。</span><span class="sxs-lookup"><span data-stu-id="d6039-228">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="d6039-229">您也可以偵錯.NET Core 容器在 Docker 中的使用 Visual Studio 中下, 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="d6039-229">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="d6039-230">**更多資訊：** 若要了解有關偵錯 Node.js Docker 容器的詳細資訊，請移至<https://blog.docker.com/2016/07/live-debugging-docker/>和[https://blogs.msdn.microsoft.com/ \ 使用者\_ed/2016年/02/27 /visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/)。</span><span class="sxs-lookup"><span data-stu-id="d6039-230">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d6039-231">[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="d6039-231">[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)</span></span>
