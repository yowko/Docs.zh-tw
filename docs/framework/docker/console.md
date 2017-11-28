---
title: "在 Docker 中執行主控台應用程式"
description: "了解如何擷取現有的 .NET Framework 主控台應用程式並在 Windows Docker 容器中執行。"
author: spboyer
keywords: ".NET, 容器, 主控台, 應用程式"
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 2fdce1e131eaa0d6952b2910f73105f097487711
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="running-console-applications-in-windows-containers"></a><span data-ttu-id="82e73-104">在 Windows 容器中執行主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="82e73-104">Running console applications in Windows containers</span></span>

<span data-ttu-id="82e73-105">主控台應用程式的用途有許多種；從簡單的狀態查詢，到長時間執行的文件影像處理工作。</span><span class="sxs-lookup"><span data-stu-id="82e73-105">Console applications are used for many purposes; from simple querying of a status to long running document image processing tasks.</span></span> <span data-ttu-id="82e73-106">在任何情況下，您都可以啟動並調整這些應用程式的規模，但具有硬體取得、啟動時間或執行多個執行個體的限制。</span><span class="sxs-lookup"><span data-stu-id="82e73-106">In any case, the ability to start up and scale these applications are met with limitations of hardware acquisitions, startup times or running multiple instances.</span></span>

<span data-ttu-id="82e73-107">藉由移動您的主控台應用程式以使用 Docker 和 Windows Server 容器，您就可以從初始狀態啟動這些應用程式，讓這些應用程式執行作業再完全關閉。</span><span class="sxs-lookup"><span data-stu-id="82e73-107">Moving your console applications to use Docker and Windows Server containers allows for starting these applications from a clean state, enabling them to perform the operation and then shutdown cleanly.</span></span> <span data-ttu-id="82e73-108">本主題說明將主控台應用程式移至 Windows 容器，再使用 PowerShell 指令碼加以啟動所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="82e73-108">This topic will show the steps needed to move a console application to a Windows based container and start it using a PowerShell script.</span></span>

<span data-ttu-id="82e73-109">此範例主控台應用程式是接受引數的簡單範例 (在本例中為一個問題)，並傳回隨機答案。</span><span class="sxs-lookup"><span data-stu-id="82e73-109">The sample console application is a simple example which takes an argument, a question in this case, and returns a random answer.</span></span> <span data-ttu-id="82e73-110">這可能會擷取 `customer_id` 並處理其稅金，或建立 `image_url` 引數的縮圖。</span><span class="sxs-lookup"><span data-stu-id="82e73-110">This could take a `customer_id` and process their taxes, or create a thumbnail for an `image_url` argument.</span></span>

<span data-ttu-id="82e73-111">除了答案之外，也已將 `Environment.MachineName` 加入回應，以顯示在本機執行應用程式與在 Windows 容器中執行應用程式之間的差異。</span><span class="sxs-lookup"><span data-stu-id="82e73-111">In addition to the answer, the `Environment.MachineName` has been added to the response to show the difference between running the application locally and in a Windows container.</span></span> <span data-ttu-id="82e73-112">在本機執行應用程式時，應該傳回您的本機電腦名稱；在 Windows 容器中執行時，則會傳回容器的工作階段識別碼。</span><span class="sxs-lookup"><span data-stu-id="82e73-112">When running the application locally, your local machine name should be returned and when running in a Windows Container; the container session id is returned.</span></span>

<span data-ttu-id="82e73-113">[完整範例 (英文)](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) 可在 GitHub 上的 dotnet/docs 儲存機制取得。</span><span class="sxs-lookup"><span data-stu-id="82e73-113">The [complete example](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) is available in the dotnet/docs repository on GitHub.</span></span> <span data-ttu-id="82e73-114">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="82e73-114">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="82e73-115">您必須先熟悉一些 Docker 術語，才能開始將應用程式移至容器的工作。</span><span class="sxs-lookup"><span data-stu-id="82e73-115">You need to be familiar with some Docker terms before you begin working on moving your application to a container.</span></span>

> <span data-ttu-id="82e73-116">「Docker 映像」是唯讀範本，為執行中容器定義環境，包括作業系統 (OS)、系統元件和應用程式。</span><span class="sxs-lookup"><span data-stu-id="82e73-116">A *Docker image* is a read-only template that defines the environment for a running container, including the operating system (OS), system components, and application(s).</span></span>

<span data-ttu-id="82e73-117">Docker 映像的一個重要特性是這些映像會從基礎映像組成。</span><span class="sxs-lookup"><span data-stu-id="82e73-117">One important feature of Docker images is that images are composed from a base image.</span></span> <span data-ttu-id="82e73-118">每個新的映像會將一小組功能加入現有的映像。</span><span class="sxs-lookup"><span data-stu-id="82e73-118">Each new image adds a small set of features to an existing image.</span></span> 

> <span data-ttu-id="82e73-119">「Docker 容器」是映像的執行中執行個體。</span><span class="sxs-lookup"><span data-stu-id="82e73-119">A *Docker container* is a running instance of an image.</span></span> 

<span data-ttu-id="82e73-120">您可以在許多容器中執行相同的映像，來調整應用程式的規模。</span><span class="sxs-lookup"><span data-stu-id="82e73-120">You scale an application by running the same image in many containers.</span></span>
<span data-ttu-id="82e73-121">就概念而言，這類似於在多部主機中執行相同的應用程式。</span><span class="sxs-lookup"><span data-stu-id="82e73-121">Conceptually, this is similar to running the same application in multiple hosts.</span></span>

<span data-ttu-id="82e73-122">您可以閱讀 Docker 網站上的 [Docker Overview](https://docs.docker.com/engine/understanding-docker/)，以深入了解 Docker 架構。</span><span class="sxs-lookup"><span data-stu-id="82e73-122">You can learn more about the Docker architecture by reading the [Docker Overview](https://docs.docker.com/engine/understanding-docker/) on the Docker site.</span></span> 

<span data-ttu-id="82e73-123">只需要幾個步驟，就可以移動您的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="82e73-123">Moving your console application is a matter of a few steps.</span></span>

1. [<span data-ttu-id="82e73-124">建置應用程式</span><span class="sxs-lookup"><span data-stu-id="82e73-124">Build the application</span></span>](#building-the-application)
1. [<span data-ttu-id="82e73-125">建立映像的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="82e73-125">Creating a Dockerfile for the image</span></span>](#creating-the-dockerfile)
1. [<span data-ttu-id="82e73-126">建置及執行 Docker 容器的程序</span><span class="sxs-lookup"><span data-stu-id="82e73-126">Process to build and run the Docker container</span></span>](#creating-the-image)

## <a name="prerequisites"></a><span data-ttu-id="82e73-127">必要條件</span><span class="sxs-lookup"><span data-stu-id="82e73-127">Prerequisites</span></span>
<span data-ttu-id="82e73-128">Windows 容器受到 [Windows 10 年度更新版](https://www.microsoft.com/en-us/software-download/windows10/)或 [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server) 的支援。</span><span class="sxs-lookup"><span data-stu-id="82e73-128">Windows containers are supported on [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) or [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span></span>

> [!NOTE]
><span data-ttu-id="82e73-129">如果您使用 Windows Server 2016，您必須手動啟用容器，因為 Docker for Windows 安裝程式不會啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="82e73-129">If you are using Windows Server 2016, you must enable containers manually since the Docker for Windows installer will not enable the feature.</span></span> <span data-ttu-id="82e73-130">請務必對作業系統執行所有更新，然後遵循[容器主機部署](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment)一文中的指示來安裝容器和 Docker 功能。</span><span class="sxs-lookup"><span data-stu-id="82e73-130">Make sure all updates have run for the OS and then follow the instructions from the [Container Host Deployment](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) article to install the containers and Docker features.</span></span>

<span data-ttu-id="82e73-131">您需要有 Docker for Windows 1.12 Beta 26 版或更高版本，才能支援 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="82e73-131">You need to have Docker for Windows, version 1.12 Beta 26 or higher to support Windows containers.</span></span> <span data-ttu-id="82e73-132">Docker 預設會啟用 Linux 容器；請以滑鼠右鍵按一下系統匣中的 Docker 圖示，然後選取 [切換至 Windows 容器]，以切換至 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="82e73-132">By default, Docker enables Linux based containers; switch to Windows containers by right clicking the Docker icon in the system tray and select **Switch to Windows containers**.</span></span> <span data-ttu-id="82e73-133">Docker 將會執行變更程序，而且可能需要重新啟動。</span><span class="sxs-lookup"><span data-stu-id="82e73-133">Docker will run the process to change and a restart may be required.</span></span>

![Windows-Containers](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a><span data-ttu-id="82e73-135">建置應用程式</span><span class="sxs-lookup"><span data-stu-id="82e73-135">Building the application</span></span>
<span data-ttu-id="82e73-136">主控台應用程式通常是透過安裝程式、FTP 或檔案共用部署來散發。</span><span class="sxs-lookup"><span data-stu-id="82e73-136">Typically console applications are distributed through an installer, FTP, or File Share deployment.</span></span> <span data-ttu-id="82e73-137">部署至容器時，這些資產必須加以編譯並暫存到建立 Docker 映像時可使用的位置。</span><span class="sxs-lookup"><span data-stu-id="82e73-137">When deploying to a container, the assets need to be compiled and staged to a location that can be used when the Docker image is created.</span></span>

<span data-ttu-id="82e73-138">在 *build.ps1* 中，指令碼會使用 [MSBuild](https://msdn.microsoft.com/library/dd393574.aspx) 來編譯應用程式，以完成建立資產的工作。</span><span class="sxs-lookup"><span data-stu-id="82e73-138">In *build.ps1*, the script uses [MSBuild](https://msdn.microsoft.com/library/dd393574.aspx) to compile the application to complete the task of building the assets.</span></span> <span data-ttu-id="82e73-139">您可以將幾個參數傳遞至 MSBuild，以確定所需的資產。</span><span class="sxs-lookup"><span data-stu-id="82e73-139">There are a few parameters passed to MSBuild to finalize the needed assets.</span></span> <span data-ttu-id="82e73-140">像是要編譯的專案檔或方案名稱，輸出的位置，以及最後的組態 (發行或偵錯)。</span><span class="sxs-lookup"><span data-stu-id="82e73-140">The name of the project file or solution to be compiled, the location for the output and finally the configuration (Release or Debug).</span></span>

<span data-ttu-id="82e73-141">在 `Invoke-MSBuild` 的呼叫中，`OutputPath` 會設定為 **publish**，而 `Configuration` 會設定為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="82e73-141">In the call to `Invoke-MSBuild` the `OutputPath` is set to **publish** and  `Configuration` set to **Release**.</span></span> 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a><span data-ttu-id="82e73-142">建立 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="82e73-142">Creating the Dockerfile</span></span>
<span data-ttu-id="82e73-143">.NET Framework 主控台應用程式所使用的基礎映像為 `microsoft/windowsservercore`，會在 [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/) 上公開提供。</span><span class="sxs-lookup"><span data-stu-id="82e73-143">The base image used for a console .NET Framework application is `microsoft/windowsservercore`, publicly available on [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span></span> <span data-ttu-id="82e73-144">基礎映像包含 Windows Server 2016 的最小安裝 .NET Framework 4.6.2，可作為 Windows 容器的基礎作業系統映像。</span><span class="sxs-lookup"><span data-stu-id="82e73-144">The base image contains a minimal installation of Windows Server 2016, .NET Framework 4.6.2 and serves as the base OS image for Windows Containers.</span></span>

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
<span data-ttu-id="82e73-145">Docerkfile 中的第一行會使用 [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) 指令來指定基礎映像。</span><span class="sxs-lookup"><span data-stu-id="82e73-145">The first line in the Dockerfile designates the base image using the [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) instruction.</span></span> <span data-ttu-id="82e73-146">接下來，檔案中的 [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) 會將應用程式資產從 **publish** 資料夾複製到容器的根資料夾；最後設定映像狀態的 [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint)，這是容器啟動時將執行的命令或應用程式。</span><span class="sxs-lookup"><span data-stu-id="82e73-146">Next, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) in the file copies the application assets from the **publish** folder to root folder of the container and last; setting the [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) of the image states that this is the command or application that will run when the container starts.</span></span> 

## <a name="creating-the-image"></a><span data-ttu-id="82e73-147">建立映像</span><span class="sxs-lookup"><span data-stu-id="82e73-147">Creating the image</span></span>
<span data-ttu-id="82e73-148">若要建立 Docker 映像，請將下列程式碼加入 *build.ps1* 指令碼。</span><span class="sxs-lookup"><span data-stu-id="82e73-148">In order to create the Docker image, the following code is added to the *build.ps1* script.</span></span> <span data-ttu-id="82e73-149">執行指令碼時，會使用從 MSBuild 編譯的資產來建立 `console-random-answer-generator` 映像，如[建置應用程式](#building-the-application)一節中所定義。</span><span class="sxs-lookup"><span data-stu-id="82e73-149">When the script is run, the `console-random-answer-generator` image is created using the assets compiled from MSBuild defined in the [Building the application](#building-the-application) section.</span></span>

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

<span data-ttu-id="82e73-150">從 PowerShell 命令提示字元使用 `.\build.ps1` 來執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="82e73-150">Run the script using `.\build.ps1` from the PowerShell command prompt.</span></span>

<span data-ttu-id="82e73-151">建置完成時，從命令列或 PowerShell 命令提示字元使用 `docker images` 命令；您將會看到映像已建立並準備好執行。</span><span class="sxs-lookup"><span data-stu-id="82e73-151">When the build is complete, using the `docker images` command from a command line or PowerShell prompt; you'll see that the image is created and ready to be run.</span></span>

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a><span data-ttu-id="82e73-152">執行容器</span><span class="sxs-lookup"><span data-stu-id="82e73-152">Running the container</span></span>
<span data-ttu-id="82e73-153">您可以從命令列使用 Docker 命令來啟動容器。</span><span class="sxs-lookup"><span data-stu-id="82e73-153">You can start the container from the command line using the Docker commands.</span></span>

```
docker run console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="82e73-154">輸出為</span><span class="sxs-lookup"><span data-stu-id="82e73-154">The output is</span></span>

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

<span data-ttu-id="82e73-155">如果您從 PowerShell 執行 `docker ps -a` 命令，您會看到容器仍然存在。</span><span class="sxs-lookup"><span data-stu-id="82e73-155">If you run the `docker ps -a` command from PowerShell, you can see that the container still exists.</span></span>

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

<span data-ttu-id="82e73-156">[狀態] 欄顯示在「約一分鐘前」，應用程式已完成並可以關閉。</span><span class="sxs-lookup"><span data-stu-id="82e73-156">The STATUS column shows at "About a minute ago", the application was complete and could be shut down.</span></span> <span data-ttu-id="82e73-157">如果執行此命令一百次，則會有一百個容器保持靜態且沒有可執行的工作。</span><span class="sxs-lookup"><span data-stu-id="82e73-157">If the command was run a hundred times, there would be a hundred containers left static with no work to do.</span></span> <span data-ttu-id="82e73-158">在一開始的案例中，理想作業是執行工作並關閉或清除。</span><span class="sxs-lookup"><span data-stu-id="82e73-158">In the beginning scenario the ideal operation was to do the work and shutdown or cleanup.</span></span> <span data-ttu-id="82e73-159">若要完成該工作流程，將 `--rm` 選項 `docker run` 加入命令會在收到 `Exited` 訊號時立即移除容器。</span><span class="sxs-lookup"><span data-stu-id="82e73-159">To accomplish that workflow, adding the `--rm` option to the `docker run` command will remove the container as soon as the `Exited` signal is received.</span></span>

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="82e73-160">執行命令並搭配此選項，然後檢視 `docker ps -a` 命令的輸出；請注意，容器識別碼 (`Environment.MachineName`) 不在清單中。</span><span class="sxs-lookup"><span data-stu-id="82e73-160">Running the command with this option and then looking at the output of `docker ps -a` command; notice that the container id (the `Environment.MachineName`) is not in the list.</span></span>

### <a name="running-the-container-using-powershell"></a><span data-ttu-id="82e73-161">使用 PowerShell 執行容器</span><span class="sxs-lookup"><span data-stu-id="82e73-161">Running the container using PowerShell</span></span>
<span data-ttu-id="82e73-162">在範例專案檔中，還有 *run.ps1*，此範例示範如何使用 PowerShell 來執行接受引數的應用程式。</span><span class="sxs-lookup"><span data-stu-id="82e73-162">In the sample project files there is also a *run.ps1* which is an example of how to use PowerShell to run the application accepting the arguments.</span></span>

<span data-ttu-id="82e73-163">若要執行，請開啟 PowerShell 並使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="82e73-163">To run, open PowerShell and use the following command:</span></span>

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a><span data-ttu-id="82e73-164">總結</span><span class="sxs-lookup"><span data-stu-id="82e73-164">Summary</span></span>
<span data-ttu-id="82e73-165">只要加入 Dockerfile 並發行應用程式，您就可以容器化 .NET Framework 主控台應用程式，並立即利用執行多個執行個體、正常啟動和停止及更多 Windows Server 2016 功能，完全不需要對應用程式程式碼進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="82e73-165">Just by adding a Dockerfile and publishing the application, you can containerize your .NET Framework console applications and now take the advantage of running multiple instances, clean start and stop and more Windows Server 2016 capabilities without making any changes to the application code at all.</span></span>
