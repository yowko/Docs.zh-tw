---
title: Docker 應用程式的內部迴圈開發工作流程
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: f7acb60e6136c0250d18bdce23ac21fb6aa80b34
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148851"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="300c4-103">Docker 應用程式的內部迴圈開發工作流程</span><span class="sxs-lookup"><span data-stu-id="300c4-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="300c4-104">之前觸發外部迴圈工作流程跨越整個 DevOps 循環，所有開始每位開發人員在電腦上，應用程式本身程式碼撰寫、 使用其慣用的語言或平台，以及在本機進行測試 (圖 4-14)。</span><span class="sxs-lookup"><span data-stu-id="300c4-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="300c4-105">但在每個案例中，您會有非常重要的一點共通點，無論選擇何種語言、 架構或平台。</span><span class="sxs-lookup"><span data-stu-id="300c4-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="300c4-106">在此特定的工作流程，您一律開發和測試 Docker 容器，但只能在本機。</span><span class="sxs-lookup"><span data-stu-id="300c4-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="300c4-107">圖 4-14:內部迴圈開發內容</span><span class="sxs-lookup"><span data-stu-id="300c4-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="300c4-108">Docker 映像的執行個體的容器將會包含這些元件：</span><span class="sxs-lookup"><span data-stu-id="300c4-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="300c4-109">作業系統選取項目 （例如，對 Linux 散發套件或 Windows）</span><span class="sxs-lookup"><span data-stu-id="300c4-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="300c4-110">加入開發人員 （例如，應用程式二進位檔） 的檔案</span><span class="sxs-lookup"><span data-stu-id="300c4-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="300c4-111">設定 （例如，環境設定和相依性）</span><span class="sxs-lookup"><span data-stu-id="300c4-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="300c4-112">指示的哪些處理程序來執行 docker</span><span class="sxs-lookup"><span data-stu-id="300c4-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="300c4-113">您可以設定內部迴圈開發工作流程，利用 Docker 處理序 （下一節中所述）。</span><span class="sxs-lookup"><span data-stu-id="300c4-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="300c4-114">考慮設定環境的初始步驟不包含在內，因為您需要這樣做，就可以一次。</span><span class="sxs-lookup"><span data-stu-id="300c4-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="300c4-115">建置使用 Visual Studio Code 和 Docker CLI 的 Docker 容器內的單一應用程式</span><span class="sxs-lookup"><span data-stu-id="300c4-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="300c4-116">應用程式是由您自己的服務加上額外的程式庫 （相依性） 所組成。</span><span class="sxs-lookup"><span data-stu-id="300c4-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="300c4-117">圖 4-15 示範您通常需要執行時建置的 Docker 應用程式，後面接著每個步驟的詳細描述的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="300c4-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="300c4-118">圖 4-15:使用 Docker CLI 的容器化 Docker 應用程式的生命週期的高階工作流程</span><span class="sxs-lookup"><span data-stu-id="300c4-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="300c4-119">步驟 1:開始在 Visual Studio Code 中撰寫程式碼，並建立初始應用程式/服務基準</span><span class="sxs-lookup"><span data-stu-id="300c4-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="300c4-120">開發您的應用程式的方式是未 Docker 的方式十分類似。</span><span class="sxs-lookup"><span data-stu-id="300c4-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="300c4-121">差別在於，在開發時，您部署和測試您的應用程式或服務放在您的本機環境 （例如 Linux VM 或 Windows） 中的 Docker 容器內執行。</span><span class="sxs-lookup"><span data-stu-id="300c4-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="300c4-122">**設定您的本機環境**</span><span class="sxs-lookup"><span data-stu-id="300c4-122">**Setting up your local environment**</span></span>

<span data-ttu-id="300c4-123">使用適用於 Mac 和 Windows 的 Docker 的最新版本，這遠比以往若要開發 Docker 應用程式，而且安裝程式是直接的。</span><span class="sxs-lookup"><span data-stu-id="300c4-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="300c4-124">**進一歩** 如需有關設定 Docker for Windows 的指示，請移至[ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/)。</span><span class="sxs-lookup"><span data-stu-id="300c4-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="300c4-125">如需 Docker for Mac 設定指示，請移至<https://docs.docker.com/docker-for-mac/>。</span><span class="sxs-lookup"><span data-stu-id="300c4-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="300c4-126">此外，您需要的程式碼編輯器，讓您實際上可以開發應用程式時使用 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="300c4-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="300c4-127">Microsoft 提供的 Visual Studio Code 中，也就是支援 Mac、 Windows、 和 Linux 上，並提供 IntelliSense 的輕量型程式碼編輯器[支援用於多種語言](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、 Go、 Java、 Ruby、 Python 和大部分現代程式語言），[偵錯](https://code.visualstudio.com/Docs/editor/debugging)，[與 Git 整合](https://code.visualstudio.com/Docs/editor/versioncontrol)並[延伸模組支援](https://code.visualstudio.com/docs/extensions/overview)。</span><span class="sxs-lookup"><span data-stu-id="300c4-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="300c4-128">此編輯器是適用於 Mac 和 Linux 的開發人員的絕佳選擇。</span><span class="sxs-lookup"><span data-stu-id="300c4-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="300c4-129">在 Windows 中，您也可以使用完整的 Visual Studio 應用程式。</span><span class="sxs-lookup"><span data-stu-id="300c4-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="300c4-130">**進一歩** 如需安裝 Visual Studio for Windows、 Mac 或 Linux 的指示，請移至<https://code.visualstudio.com/docs/setup/setup-overview/>。</span><span class="sxs-lookup"><span data-stu-id="300c4-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>

<span data-ttu-id="300c4-131">您可以使用 Docker CLI，並撰寫程式碼，使用任何程式碼編輯器中，但如果您使用 Visual Studio Code，它可讓您輕鬆地撰寫 Dockerfile 和 docker-compose.yml 檔案在您的工作區中。</span><span class="sxs-lookup"><span data-stu-id="300c4-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="300c4-132">此外，您可以從 IDE，以提示所能執行使用 Docker CLI 底下的複雜的作業的指令碼執行 Visual Studio 程式碼工作。</span><span class="sxs-lookup"><span data-stu-id="300c4-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="300c4-133">Visual Studio Code 會提供的擴充功能，您必須安裝。</span><span class="sxs-lookup"><span data-stu-id="300c4-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="300c4-134">若要這樣做，請按 Ctrl + Shift + P，鍵入**ext 安裝**，然後執行 延伸模組：安裝延伸模組命令即可啟動 Marketplace 延伸模組清單。</span><span class="sxs-lookup"><span data-stu-id="300c4-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="300c4-135">接下來，輸入**docker**來篩選結果，然後按 Dockerfile 和 Docker Compose 檔案 (yml) 支援擴充功能，如上圖中圖 4-16。</span><span class="sxs-lookup"><span data-stu-id="300c4-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="300c4-136">圖 4-16:Visual Studio Code 中安裝 Docker 擴充功能</span><span class="sxs-lookup"><span data-stu-id="300c4-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="300c4-137">步驟 2：建立 DockerFile，現有的映像 （純文字的 OS 或開發環境，例如.NET Core、 Node.js 和 Ruby） 相關</span><span class="sxs-lookup"><span data-stu-id="300c4-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="300c4-138">您需要 DockerFile，每個要建置的自訂映像，以及每個要部署的容器，因此，如果您的應用程式組成單一的自訂服務，您將需要單一的 DockerFile。</span><span class="sxs-lookup"><span data-stu-id="300c4-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="300c4-139">但是，如果您的應用程式所組成 （就像在微服務架構） 的多個服務，您將需要一個 Dockerfile，每個服務。</span><span class="sxs-lookup"><span data-stu-id="300c4-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="300c4-140">DockerFile 通常會放在您的應用程式或服務的根資料夾內，並包含必要的命令，因此 Docker 知道如何設定及執行該應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="300c4-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="300c4-141">您可以建立您的 DockerFile，並將它新增至您的專案中，以及您的程式碼 (.NET Core、 node.js 等)，或如果您不熟悉的環境，看看以下的提示。</span><span class="sxs-lookup"><span data-stu-id="300c4-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="300c4-142">您可以使用命令列工具，稱為[yo docker](https://github.com/Microsoft/generator-docker)，這則來自您的專案，在您選擇的語言加入所需的 Docker 組態檔中的檔案。</span><span class="sxs-lookup"><span data-stu-id="300c4-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="300c4-143">基本上，協助開發人員開始使用，它會建立適當的 DockerFile 中，docker compose.yml 和其他相關聯的指令碼，以建置並執行 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="300c4-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="300c4-144">這個的 yeoman 產生器會提示您幾個問題，詢問您所選的開發語言和目的地容器主機。</span><span class="sxs-lookup"><span data-stu-id="300c4-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![yo docker](./media/image21.png)

<span data-ttu-id="300c4-146">在 Windows 和 Mac 上，在這兩種情況下，執行 yo docker，但這會產生的範例程式碼專案 （目前.NET Core、 Golang、 和 Node.js 作為支援的語言） 已設定為搭配使用上圖 4-17 比方說，顯示來自終端機的兩個螢幕擷取畫面Docker 的頂端。</span><span class="sxs-lookup"><span data-stu-id="300c4-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="300c4-147">圖 4-17: yo docker 命令在 Windows （左） 和 Mac 上的工具</span><span class="sxs-lookup"><span data-stu-id="300c4-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="300c4-148">圖 4-18 提供範例使用 yo docker 之後，您有現有的.NET Core 專案中會包含 scaffold 的地方。</span><span class="sxs-lookup"><span data-stu-id="300c4-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="300c4-149">圖 4-18: yo docker 使用現有的.NET Core 專案就緒</span><span class="sxs-lookup"><span data-stu-id="300c4-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="300c4-150">您可以從 DockerFile 中，指定哪些基底的 Docker 映像，選擇您要使用 （例如，使用"FROM microsoft/dotnet:1.0.0-core"）。</span><span class="sxs-lookup"><span data-stu-id="300c4-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="300c4-151">您通常會建置您自訂的映像，您可以從在任何官方存放庫取得基底映像[Docker Hub 登錄](https://hub.docker.com/)(像是[適用於.NET Core 的映像](https://hub.docker.com/r/microsoft/dotnet/)或一個[適用於 Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="300c4-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="300c4-152">***選項 a:使用現有的正式 Docker 映像***</span><span class="sxs-lookup"><span data-stu-id="300c4-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="300c4-153">使用版本號碼的語言在堆疊的官方存放庫可確保可以相同的語言功能 （包括開發、 測試和生產環境） 的所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="300c4-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="300c4-154">以下是.NET Core 容器的範例 DockerFile:</span><span class="sxs-lookup"><span data-stu-id="300c4-154">Following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="300c4-155">在此情況下，它使用官方 ASP.NET Core Docker 映像的 1.0.1 版適用於名為 microsoft/aspnetcore:1.0.1 Linux。</span><span class="sxs-lookup"><span data-stu-id="300c4-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="300c4-156">如需詳細資訊，請參閱[ASP.NET Core Docker 映像頁面](https://hub.docker.com/r/microsoft/aspnetcore/)並[.NET Core Docker 映像頁面](https://hub.docker.com/r/microsoft/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="300c4-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="300c4-157">您也可以使用另一個可比較像的映像節點： 4-Node.js 或許多其他預先設定映像開發語言，可在 onbuild [Docker Hub](https://hub.docker.com/explore/)。</span><span class="sxs-lookup"><span data-stu-id="300c4-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="300c4-158">在 DockerFile 中，您也需要指示 Docker 接聽您在執行階段 （例如連接埠 80） 會使用 TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="300c4-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="300c4-159">有其他線讓 Docker 知道如何執行應用程式，您可以加入根據您使用的語言/架構 DockerFile 中的設定。</span><span class="sxs-lookup"><span data-stu-id="300c4-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="300c4-160">比方說，您需要 ENTRYPOINT 行中的有\["dotnet"，"MyCustomMicroservice.dll"\]執行.NET Core 應用程式，雖然您可以根據以建置並執行您的服務方法的多個變異。</span><span class="sxs-lookup"><span data-stu-id="300c4-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="300c4-161">如果您使用的 SDK 和 dotnet CLI 來建置和執行.NET 應用程式，它會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="300c4-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="300c4-162">重點是 ENTRYPOINT 行，加上額外的線條將會根據您選擇您的應用程式的語言/平台而不同。</span><span class="sxs-lookup"><span data-stu-id="300c4-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="300c4-163">**進一歩** 建置.NET Core 應用程式的 Docker 映像的相關資訊，請移至<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。</span><span class="sxs-lookup"><span data-stu-id="300c4-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="300c4-164">若要深入了解如何建置自己的映像，請移至[https://docs.docker.com/engine/\教學課程/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)。</span><span class="sxs-lookup"><span data-stu-id="300c4-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="300c4-165">**多平台映像存放庫**</span><span class="sxs-lookup"><span data-stu-id="300c4-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="300c4-166">由於 Windows 容器變得更普遍的單一的存放庫可以包含多種平台變化，例如 Linux 和 Windows 的映像。</span><span class="sxs-lookup"><span data-stu-id="300c4-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="300c4-167">這是可讓廠商能夠涵蓋多個平台，例如使用單一儲存機制的 Docker 中的新功能[microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)存放庫中，會使用可在 DockerHub 登錄。</span><span class="sxs-lookup"><span data-stu-id="300c4-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="300c4-168">功能過來運作時，從 Windows 主機提取此映像會提取 Windows variant，而從 Linux 主機提取相同的映像名稱將會提取 Linux variant。</span><span class="sxs-lookup"><span data-stu-id="300c4-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="300c4-169">***選項 b:從頭開始建立您的基底映像***</span><span class="sxs-lookup"><span data-stu-id="300c4-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="300c4-170">在此所述，您可以從頭建立您自己的 Docker 基礎映像[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)從 Docker。</span><span class="sxs-lookup"><span data-stu-id="300c4-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="300c4-171">這是可能不是最適合您如果您剛開始使用 Docker 的案例，但如果您想要設定您自己的基底映像的特定位元，您可以執行。</span><span class="sxs-lookup"><span data-stu-id="300c4-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="300c4-172">步驟 3:建立自訂 Docker 映像嵌入您的服務</span><span class="sxs-lookup"><span data-stu-id="300c4-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="300c4-173">針對每個包含您的應用程式的自訂服務，您必須建立相關的映像。</span><span class="sxs-lookup"><span data-stu-id="300c4-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="300c4-174">如果您的應用程式組成的單一服務或 web 應用程式，您將需要一張圖片。</span><span class="sxs-lookup"><span data-stu-id="300c4-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="300c4-175">考慮 「 外部迴圈 DevOps 工作流程 」，映像將會建立自動化的建置程序時您將來源程式碼推送至 Git 存放庫 （連續整合），因此會在全域環境中建立的映像從您原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="300c4-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="300c4-176">但是，我們考慮移到該外部迴圈路由之前，我們需要確保 Docker 應用程式實際運作正常，讓它們不會推送程式碼，可能無法正常運作 （Git 等等），才會進行來源控制系統。</span><span class="sxs-lookup"><span data-stu-id="300c4-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="300c4-177">因此，每位開發人員第一次需要整個 「 內部迴圈 」 程序，在本機測試，並繼續開發，直到他們想要推送完整的功能或變更原始檔控制系統。</span><span class="sxs-lookup"><span data-stu-id="300c4-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="300c4-178">在您的本機環境中和使用 DockerFile 建立映像，您可以使用 docker build 命令，在圖 4-19 示 (您也可以執行 docker compose up--建置由數個容器/服務所組成的應用程式)。</span><span class="sxs-lookup"><span data-stu-id="300c4-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="300c4-179">圖 4-19:執行 docker 建置</span><span class="sxs-lookup"><span data-stu-id="300c4-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="300c4-180">（選擇性） 而不是直接執行 docker 建置的專案資料夾中，您第一次可以產生可部署的資料夾使用執行的 dotnet 發行命令，並執行 docker 建置所需的.NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="300c4-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="300c4-181">在此範例中，這會建立 Docker 映像名稱 cesardl/netcore webapi-微服務-docker： 第一個 (: 首先是標記，例如特定的版本)。</span><span class="sxs-lookup"><span data-stu-id="300c4-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="300c4-182">您可以採取此步驟中的每個您需要建立數個容器組成 Docker 應用程式的自訂映像。</span><span class="sxs-lookup"><span data-stu-id="300c4-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="300c4-183">您可以找到現有的映像在本機存放庫 （您的開發電腦） 使用 docker images 命令所示的 圖 4 到 20。</span><span class="sxs-lookup"><span data-stu-id="300c4-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="300c4-184">圖 4 到 20:檢視現有的映像使用 docker 映像</span><span class="sxs-lookup"><span data-stu-id="300c4-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="300c4-185">步驟 4:（選擇性）建置具有多個服務的組成的 Docker 應用程式時，在 docker-compose.yml 中定義您的服務</span><span class="sxs-lookup"><span data-stu-id="300c4-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="300c4-186">使用 docker-compose.yml 檔案中，您可以定義一組相關的服務一起部署為組成的應用程式的下一個步驟一節所述的部署命令。</span><span class="sxs-lookup"><span data-stu-id="300c4-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="300c4-187">您必須建立該檔案在您的 main 或根解決方案資料夾;下列 docker compose.yml 檔案應該類似的內容：</span><span class="sxs-lookup"><span data-stu-id="300c4-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

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

<span data-ttu-id="300c4-188">在此案例中，此檔案會定義兩個服務： web 服務 （您自訂的服務） 和 redis 服務 （受歡迎的快取服務）。</span><span class="sxs-lookup"><span data-stu-id="300c4-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="300c4-189">每個服務會部署為容器，，因此我們要用於每個具體的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="300c4-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="300c4-190">此特定的 web 服務，影像必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="300c4-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="300c4-191">建立從目前的目錄中的 DockerFile</span><span class="sxs-lookup"><span data-stu-id="300c4-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="300c4-192">轉送公開的連接埠 80 上的容器在主機電腦上的連接埠 81</span><span class="sxs-lookup"><span data-stu-id="300c4-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="300c4-193">讓您修改程式碼，而不需要重建映像的容器內的 /code 主機上掛接專案目錄</span><span class="sxs-lookup"><span data-stu-id="300c4-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="300c4-194">連結至 redis 服務的 web 服務</span><span class="sxs-lookup"><span data-stu-id="300c4-194">Link the web service to the redis service</span></span>

<span data-ttu-id="300c4-195">Redis 服務會使用[最新的公用 redis 映像](https://hub.docker.com/_/redis/)從 Docker Hub 登錄提取。</span><span class="sxs-lookup"><span data-stu-id="300c4-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="300c4-196">[redis](https://redis.io/)是伺服器端應用程式的非常受歡迎的快取系統。</span><span class="sxs-lookup"><span data-stu-id="300c4-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="300c4-197">步驟 5:建置並執行您的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="300c4-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="300c4-198">如果您的應用程式有單一容器，您只需要藉由將它部署至您的 Docker 主機 （VM 或實體伺服器） 執行它。</span><span class="sxs-lookup"><span data-stu-id="300c4-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="300c4-199">不過，如果您的應用程式多個服務組成，您需要*組合*也。</span><span class="sxs-lookup"><span data-stu-id="300c4-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="300c4-200">讓我們看到不同的選項。</span><span class="sxs-lookup"><span data-stu-id="300c4-200">Let's see the different options.</span></span>

<span data-ttu-id="300c4-201">***選項 a:執行單一容器或服務***</span><span class="sxs-lookup"><span data-stu-id="300c4-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="300c4-202">您可以執行的 Docker 映像使用 docker run 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="300c4-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="300c4-203">請注意，針對此特定的部署，我們將會將要求重新導向傳送至連接埠 80 的內部連接埠 5000。</span><span class="sxs-lookup"><span data-stu-id="300c4-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="300c4-204">現在，應用程式正在接聽的外部連接埠 80，在主機層級。</span><span class="sxs-lookup"><span data-stu-id="300c4-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="300c4-205">***選項 b:撰寫和執行多容器應用程式***</span><span class="sxs-lookup"><span data-stu-id="300c4-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="300c4-206">在大部分的企業案例中，將多個服務組成 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="300c4-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="300c4-207">在這些情況下，您可以執行命令 docker compose 設定 (圖 4-21)，它會使用您可能會有先前建立的 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="300c4-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="300c4-208">執行此命令會部署所有及其相關容器組成的應用程式。</span><span class="sxs-lookup"><span data-stu-id="300c4-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="300c4-209">圖 4-21:執行 「 啟動 docker compose"命令的結果</span><span class="sxs-lookup"><span data-stu-id="300c4-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="300c4-210">執行 docker 之後-docker-compose up，您將部署應用程式和其相關的容器到您的 Docker 主機中所示在圖 4-22，呈現的 VM。</span><span class="sxs-lookup"><span data-stu-id="300c4-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="300c4-211">圖 4-22:部署了 Docker 容器的 VM</span><span class="sxs-lookup"><span data-stu-id="300c4-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="300c4-212">附註啟動 docker compose 和 docker 執行可能不足以在您的開發環境中測試您的容器，但您可能完全不使用它們，如果您預期地使用 Docker 叢集和協調器，像是 Docker Swarm、 Mesosphere DC/OS 或 Kubernetes為了能夠相應增加。</span><span class="sxs-lookup"><span data-stu-id="300c4-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="300c4-213">如果您使用類似的叢集[Docker Swarm 模式](https://docs.docker.com/engine/swarm/)（可在 Docker for Windows 和 Mac 1.12 版之後），您需要部署及測試與其他命令，例如 docker 服務建立單一服務，或當您準備部署數個容器所組成的應用程式，搭配使用 docker compose bundle 及 docker 部署 myBundleFile，作為堆疊，部署組成的應用程式，如本文所述[分散式應用程式套件組合](https://blog.docker.com/2016/06/docker-app-bundle/)從 Docker。</span><span class="sxs-lookup"><span data-stu-id="300c4-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="300c4-214">針對[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)並[Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment)您可以使用不同的部署命令和指令碼，以及。</span><span class="sxs-lookup"><span data-stu-id="300c4-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="300c4-215">步驟 6:測試 Docker 應用程式 （在本機，在您本機的 CD VM)</span><span class="sxs-lookup"><span data-stu-id="300c4-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="300c4-216">此步驟會因應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="300c4-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="300c4-217">非常簡單.NET Core Web API 中"Hello World"部署為單一容器或服務，您只需要提供 DockerFile 中指定的 TCP 連接埠來存取服務。</span><span class="sxs-lookup"><span data-stu-id="300c4-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="300c4-218">如果 localhost 未開啟，以瀏覽至您的服務，尋找電腦的 IP 位址，使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="300c4-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="300c4-219">docker 機器 ip*您的容器名稱*</span><span class="sxs-lookup"><span data-stu-id="300c4-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="300c4-220">在 Docker 主機上，開啟瀏覽器並瀏覽至該網站;圖 4-23 示，應該會看到執行中，您的應用程式/服務。</span><span class="sxs-lookup"><span data-stu-id="300c4-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="300c4-221">圖 4-23:測試使用 localhost 在本機的 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="300c4-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="300c4-222">請注意，它使用連接埠 80，但在內部它已被重新導向至連接埠 5000，因為這是它的部署方式使用 docker 執行時，如先前所述。</span><span class="sxs-lookup"><span data-stu-id="300c4-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="300c4-223">您可以從終端機使用 CURL 來測試。</span><span class="sxs-lookup"><span data-stu-id="300c4-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="300c4-224">在 Docker 安裝在 Windows 中，預設值是 IP 10.0.75.1，如上圖中圖 4-24。</span><span class="sxs-lookup"><span data-stu-id="300c4-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="300c4-225">圖 4-24:由使用 CURL 在本機測試 Docker 應用程式</span><span class="sxs-lookup"><span data-stu-id="300c4-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="300c4-226">**偵錯在 Docker 上執行的容器**</span><span class="sxs-lookup"><span data-stu-id="300c4-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="300c4-227">Visual Studio Code 支援偵錯的 Docker，如果您使用 Node.js 和.NET Core 容器等其他平台。</span><span class="sxs-lookup"><span data-stu-id="300c4-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="300c4-228">您也可以偵錯在 Docker 中的.NET Core 容器時使用 Visual Studio 中下, 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="300c4-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="300c4-229">**更多資訊：** 若要深入了解偵錯 Node.js Docker 容器，請前往<https://blog.docker.com/2016/07/live-debugging-docker/>並[https://blogs.msdn.microsoft.com/\使用者\_ed/2016年/02/27 /visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/)。</span><span class="sxs-lookup"><span data-stu-id="300c4-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="300c4-230">[上一頁](docker-apps-development-environment.md)
>[下一頁](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="300c4-230">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>