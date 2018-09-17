---
title: 使用 Visual Studio Tools for Docker (Windows 上的 Visual Studio)
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: af14c92ab27885deec878dc33e7b94035f43e65b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743822"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="a5166-103">使用 Visual Studio Tools for Docker (Windows 上的 Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="a5166-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="a5166-104">使用 Visual Studio Code 和 Docker CLI 時，類似於工作流程時使用 Visual Studio Tools for Docker 開發工作流程。</span><span class="sxs-lookup"><span data-stu-id="a5166-104">The development workflow when using Visual Studio Tools for Docker is similar to the workflow when using Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="a5166-105">事實上，它根據相同的 Docker CLI，但您更輕鬆地開始使用、 簡化程序，並提供更高的生產力組建、 執行和撰寫工作。</span><span class="sxs-lookup"><span data-stu-id="a5166-105">In fact, it's based on the same Docker CLI, but it's easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="a5166-106">它也可執行和偵錯您的容器，透過簡單的動作，例如 F5 以及從 Visual Studio 的 Ctrl + F5。</span><span class="sxs-lookup"><span data-stu-id="a5166-106">It's also able to execute and debug your containers via simple actions like F5 and Ctrl+F5 from Visual Studio.</span></span> <span data-ttu-id="a5166-107">選擇性的容器協調流程的支援，除了能夠執行和偵錯單一容器中，您可以執行，並同時在偵錯容器 （整個解決方案） 的群組。</span><span class="sxs-lookup"><span data-stu-id="a5166-107">With the optional container orchestration support, in addition to being able to run and debug a single container, you can run and debug a group of containers (a whole solution) at the same time.</span></span> <span data-ttu-id="a5166-108">只在同一個定義的容器*docker compose.yml*方案層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="a5166-108">Just define the containers in the same *docker-compose.yml* file at the solution level.</span></span>

## <a name="configuring-your-local-environment"></a><span data-ttu-id="a5166-109">設定您的本機環境</span><span class="sxs-lookup"><span data-stu-id="a5166-109">Configuring your local environment</span></span>

<span data-ttu-id="a5166-110">在 Visual Studio 2017 包含 docker 的支援，與任何已安裝的.NET 和.NET Core 工作負載。</span><span class="sxs-lookup"><span data-stu-id="a5166-110">Docker support is included in Visual Studio 2017 with any of the .NET and .NET Core workloads installed.</span></span> <span data-ttu-id="a5166-111">個別安裝 Docker for Windows。</span><span class="sxs-lookup"><span data-stu-id="a5166-111">Install Docker for Windows separately.</span></span>

<span data-ttu-id="a5166-112">使用 Docker for Windows 的最新版本，就比以往若要開發 Docker 應用程式因為下列參考中所述，安裝程式很簡單，更容易。</span><span class="sxs-lookup"><span data-stu-id="a5166-112">With the latest versions of Docker for Windows, it is easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

<span data-ttu-id="a5166-113">**更多資訊：** 若要深入了解安裝 Docker for Windows，請前往<https://docs.docker.com/docker-for-windows/>。</span><span class="sxs-lookup"><span data-stu-id="a5166-113">**More info:** To learn more about installing Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>

<span data-ttu-id="a5166-114">**更多資訊：** 如需安裝 Visual Studio 的指示，請移至[ https://visualstudio.microsoft.com/downloads/ ](https://visualstudio.microsoft.com/downloads/)。</span><span class="sxs-lookup"><span data-stu-id="a5166-114">**More info:** For instructions on installing Visual Studio, go to [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/).</span></span>

<span data-ttu-id="a5166-115">若要查看安裝 Visual Studio Tools for Docker 的詳細資訊，請前往<http://aka.ms/vstoolsfordocker>和<https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>。</span><span class="sxs-lookup"><span data-stu-id="a5166-115">To see more about installing Visual Studio Tools for Docker, go to <http://aka.ms/vstoolsfordocker> and <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span></span>

## <a name="using-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="a5166-116">Visual Studio 2017 中使用 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="a5166-116">Using Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="a5166-117">將 Docker 支援新增至專案時 （請參閱圖 4-26），Visual Studio 會加入*Dockerfile*至專案根目錄。</span><span class="sxs-lookup"><span data-stu-id="a5166-117">When adding Docker support to a project (see Figure 4-26), Visual Studio adds a *Dockerfile* to the project root.</span></span>

![開啟 Visual Studio 2017 專案中的 Docker 解決方案支援](./media/image32.png)

<span data-ttu-id="a5166-119">圖 4-26： 開啟 Visual Studio 2017 專案中的 Docker 解決方案支援</span><span class="sxs-lookup"><span data-stu-id="a5166-119">Figure 4-26: Turning on Docker Solution support in a Visual Studio 2017 project</span></span>

 <span data-ttu-id="a5166-120">新增容器協調流程支援，透過 Docker Compose，預設會在 Visual Studio 2017 版本 15.7 或更早版本。</span><span class="sxs-lookup"><span data-stu-id="a5166-120">Container orchestration support, via Docker Compose, is added by default in Visual Studio 2017 versions 15.7 or earlier.</span></span> <span data-ttu-id="a5166-121">容器協調流程的支援是在 Visual Studio 2017 版本 15.8 選擇加入的功能或更新版本中，在此情況下 Docker Compose 與 Service Fabric 支援。</span><span class="sxs-lookup"><span data-stu-id="a5166-121">Container orchestration support is an opt-in feature in Visual Studio 2017 versions 15.8 or later, in which case Docker Compose and Service Fabric are supported.</span></span>

<span data-ttu-id="a5166-122">使用 Visual Studio 15.8 和更新版本中,，您可以新增多個專案的支援方案，每個有相關聯的容器中。</span><span class="sxs-lookup"><span data-stu-id="a5166-122">With Visual Studio version 15.8 and later, you can add support for multiple projects in a solution that each have an associated container.</span></span> <span data-ttu-id="a5166-123">中的方案或專案節點上按一下滑鼠右鍵**方案總管 中**，然後選擇**新增** > **容器協調流程支援**。</span><span class="sxs-lookup"><span data-stu-id="a5166-123">Right-click on the solution or project node in **Solution Explorer**, and choose **Add** > **Container Orchestration Support**.</span></span>  <span data-ttu-id="a5166-124">然後選擇**Docker Compose**或是**Service Fabric**管理容器。</span><span class="sxs-lookup"><span data-stu-id="a5166-124">Then choose **Docker Compose** or **Service Fabric** to manage the containers.</span></span>

<span data-ttu-id="a5166-125">當您選擇**Docker Compose**，Visual Studio 在您的方案中新增服務 區段*docker compose.yml*檔案 （或建立檔案，如果不存在的話）。</span><span class="sxs-lookup"><span data-stu-id="a5166-125">When you choose **Docker Compose**, Visual Studio adds a service section in your solution's *docker-compose.yml* files (or creates the files if they didn't exist).</span></span> <span data-ttu-id="a5166-126">這是簡單的方法，開始撰寫多容器解決方案;接著，您可以開啟*docker compose.yml*檔案，並使用額外的功能更新這些值。</span><span class="sxs-lookup"><span data-stu-id="a5166-126">It's an easy way to begin composing your multi-container solution; you then can open the *docker-compose.yml* files and update them with additional features.</span></span>

<span data-ttu-id="a5166-127">這個動作會將必要的設定的程式碼來*docker compose.yml*在解決方案層級設定。</span><span class="sxs-lookup"><span data-stu-id="a5166-127">This action adds the required configuration lines of code to a *docker-compose.yml* set at the solution level.</span></span>

<span data-ttu-id="a5166-128">您也可以開啟 Docker 支援在 Visual Studio 2017 中，建立 ASP.NET Core 專案時，所示的圖 4-27。</span><span class="sxs-lookup"><span data-stu-id="a5166-128">You also can turn on Docker support when creating an ASP.NET Core project in Visual Studio 2017, as shown in Figure 4-27.</span></span>

![建立專案時，開啟 Docker 支援](./media/image33.png)

<span data-ttu-id="a5166-130">圖 4-27： 在建立專案時，要開啟 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="a5166-130">Figure 4-27: Turning on Docker support when creating a project</span></span>

<span data-ttu-id="a5166-131">您將 Docker 支援新增至您在 Visual Studio 中的方案之後，您也會看到新的節點樹狀目錄中**方案總管**以加入*docker compose.yml*檔案，如下所述在圖 4-28。</span><span class="sxs-lookup"><span data-stu-id="a5166-131">After you add Docker support to your solution in Visual Studio, you also will see a new node tree in **Solution Explorer** with the added *docker-compose.yml* files, as depicted in Figure 4-28.</span></span>

![docker-compose.yml 檔案現在會顯示在 方案總管](./media/image34.PNG)

<span data-ttu-id="a5166-133">[圖 4-28: docker-compose.yml 檔案現在會顯示在**方案總管]**</span><span class="sxs-lookup"><span data-stu-id="a5166-133">Figure 4-28: docker-compose.yml files now display in **Solution Explorer**</span></span>

<span data-ttu-id="a5166-134">您可以部署多容器應用程式使用單一*docker compose.yml*檔案，當您執行`docker-compose up`; 不過，Visual Studio 會加入它們的群組，因此您可以覆寫值取決於環境 （開發與生產環境） 和輸入 （發行與偵錯） 執行。</span><span class="sxs-lookup"><span data-stu-id="a5166-134">You could deploy a multi-container app by using a single *docker-compose.yml* file when you run `docker-compose up`; however, Visual Studio adds a group of them, so you can override values depending on the environment (development versus production) and the execution type (release versus debug).</span></span> <span data-ttu-id="a5166-135">後面的章節則會進一步說明這項功能。</span><span class="sxs-lookup"><span data-stu-id="a5166-135">This capability is better explained in later chapters.</span></span>

<span data-ttu-id="a5166-136">您也可以管理多個容器，而不是 Docker Compose 使用 Service Fabric。</span><span class="sxs-lookup"><span data-stu-id="a5166-136">You can also use Service Fabric instead of Docker Compose to manage multiple containers.</span></span> <span data-ttu-id="a5166-137">請參閱[教學課程： 將 Windows 容器中的.NET 應用程式部署至 Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container)。</span><span class="sxs-lookup"><span data-stu-id="a5166-137">See [Tutorial: Deploy a .NET application in a Windows container to Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).</span></span>

<span data-ttu-id="a5166-138">**更多資訊：** 如需詳細的服務實作和使用 Visual Studio Tools for Docker，請閱讀下列文章：</span><span class="sxs-lookup"><span data-stu-id="a5166-138">**More info:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="a5166-139">建置、 偵錯、 更新和重新整理本機 Docker 容器中的應用程式： [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="a5166-139">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="a5166-140">將 ASP.NET Core Docker 容器部署至容器登錄： [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="a5166-140">Deploy an ASP.NET Core Docker container to a container registry: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a5166-141">[上一頁](docker-apps-inner-loop-workflow.md)
[下一頁](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="a5166-141">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>
