---
title: 將部署為 Linux 容器的 ASP.NET Core 應用程式建立至 AKS/Kubernetes 叢集中
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.date: 08/06/2020
ms.openlocfilehash: 831d2372131e20788d0f48190eb8c600aa02485c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440825"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="7846e-103">將部署為 Linux 容器的 ASP.NET Core 應用程式建立至 AKS/Kubernetes orchestrator</span><span class="sxs-lookup"><span data-stu-id="7846e-103">Build ASP.NET Core applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="7846e-104">Azure Kubernetes Service (AKS) 是 Azure 的受控 Kubernetes 協調流程服務，可簡化容器部署和管理。</span><span class="sxs-lookup"><span data-stu-id="7846e-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="7846e-105">AKS 的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="7846e-105">AKS main features are:</span></span>

- <span data-ttu-id="7846e-106">Azure 裝載的控制平面</span><span class="sxs-lookup"><span data-stu-id="7846e-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="7846e-107">自動升級</span><span class="sxs-lookup"><span data-stu-id="7846e-107">Automated upgrades</span></span>
- <span data-ttu-id="7846e-108">自我修復</span><span class="sxs-lookup"><span data-stu-id="7846e-108">Self-healing</span></span>
- <span data-ttu-id="7846e-109">使用者可設定的調整</span><span class="sxs-lookup"><span data-stu-id="7846e-109">User-configurable scaling</span></span>
- <span data-ttu-id="7846e-110">開發人員和叢集操作員更簡單的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="7846e-110">Simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="7846e-111">下列範例會探索如何建立在 Linux 上執行的 ASP.NET Core 3.1 應用程式，並部署至 Azure 中的 AKS 叢集，而開發則是使用 Visual Studio 2019 來完成。</span><span class="sxs-lookup"><span data-stu-id="7846e-111">The following examples explore the creation of an ASP.NET Core 3.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2019.</span></span>

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a><span data-ttu-id="7846e-112">使用 Visual Studio 2019 建立 ASP.NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="7846e-112">Creating the ASP.NET Core Project using Visual Studio 2019</span></span>

<span data-ttu-id="7846e-113">ASP.NET Core 是一般用途的開發平台，由 Microsoft 和 GitHub 上的 .NET 社群共同維護。</span><span class="sxs-lookup"><span data-stu-id="7846e-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="7846e-114">它可以跨平台支援 Windows、macOS 及 Linux，並可用於裝置、雲端和內嵌式系統/IoT 等應用情節。</span><span class="sxs-lookup"><span data-stu-id="7846e-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="7846e-115">此範例會根據 Visual Studio 範本使用幾個簡單的專案，因此您不需要額外的知識就能建立範例。</span><span class="sxs-lookup"><span data-stu-id="7846e-115">This example uses a couple of simple projects based on Visual Studio templates, so you don't need much additional knowledge to create the sample.</span></span> <span data-ttu-id="7846e-116">您只需要使用標準範本（包含所有專案）來建立專案，以執行具有 REST API 的小型專案，以及使用 ASP.NET Core 3.1 技術的 Razor pages Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7846e-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API and a Web App with Razor pages, using ASP.NET Core 3.1 technology.</span></span>

![在 Visual Studio 中新增專案視窗，並選取 ASP.NET Core Web 應用程式。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

<span data-ttu-id="7846e-118">**圖 4-35**.</span><span class="sxs-lookup"><span data-stu-id="7846e-118">**Figure 4-35**.</span></span> <span data-ttu-id="7846e-119">在 Visual Studio 2019 中建立 ASP.NET Core Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7846e-119">Creating an ASP.NET Core Web Application in Visual Studio 2019.</span></span>

<span data-ttu-id="7846e-120">若要在 Visual Studio 中建立範例專案， **請選取**  >  [檔案 **新增**  >  **專案** ]，選取 [ **web** 專案類型]，然後選取 [ **ASP.NET Core web 應用程式** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="7846e-120">To create the sample project in Visual Studio, select **File** > **New** > **Project** , select the **Web** project type and then the **ASP.NET Core Web Application** template.</span></span> <span data-ttu-id="7846e-121">您也可以視需要搜尋範本。</span><span class="sxs-lookup"><span data-stu-id="7846e-121">You can also search for the template if you need it.</span></span>

<span data-ttu-id="7846e-122">然後輸入應用程式名稱和位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="7846e-122">Then enter the application name and location as shown in the next image.</span></span>

![輸入專案名稱和位置。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

<span data-ttu-id="7846e-124">**圖 4-36**.</span><span class="sxs-lookup"><span data-stu-id="7846e-124">**Figure 4-36**.</span></span> <span data-ttu-id="7846e-125">輸入 Visual Studio 2019 中的專案名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="7846e-125">Enter the project name and location in Visual Studio 2019.</span></span>

<span data-ttu-id="7846e-126">確認您已選取 ASP.NET Core 3.1 作為架構。</span><span class="sxs-lookup"><span data-stu-id="7846e-126">Verify that you've selected ASP.NET Core 3.1 as the framework.</span></span> <span data-ttu-id="7846e-127">.NET Core 3.1 包含在 Visual Studio 2019 的最新版本中，當您安裝 Visual Studio 時，系統會自動為您安裝並設定。</span><span class="sxs-lookup"><span data-stu-id="7846e-127">.NET Core 3.1 is included in the latest release of Visual Studio 2019 and is automatically installed and configured for you when you install Visual Studio.</span></span>

![用於選取 ASP.NET Core Web 應用程式類型並已選取 API 選項的 Visual Studio 對話方塊。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

<span data-ttu-id="7846e-129">**圖 4-37**.</span><span class="sxs-lookup"><span data-stu-id="7846e-129">**Figure 4-37**.</span></span> <span data-ttu-id="7846e-130">選取 ASP.NET CORE 3.1 和 Web API 專案類型</span><span class="sxs-lookup"><span data-stu-id="7846e-130">Selecting ASP.NET CORE 3.1 and Web API project type</span></span>

<span data-ttu-id="7846e-131">請注意，目前尚未啟用 Docker 支援，只是要顯示它可以在專案建立之後完成。</span><span class="sxs-lookup"><span data-stu-id="7846e-131">Notice Docker support is not enabled now, just to show it can be done after project creation.</span></span>

<span data-ttu-id="7846e-132">如果您有任何舊版的 .NET Core，您可以從下載並安裝3.1 版 <https://dotnet.microsoft.com/download> 。</span><span class="sxs-lookup"><span data-stu-id="7846e-132">If you have any previous version of .NET Core, you can download and install the 3.1 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="7846e-133">若要顯示您隨時可以「Docker 化」您的專案，您可以立即新增 Docker 支援。</span><span class="sxs-lookup"><span data-stu-id="7846e-133">To show you can "Dockerize" your project at any time, you'll add Docker support now.</span></span> <span data-ttu-id="7846e-134">因此，在方案總管中的專案節點上按一下滑鼠右鍵，然後在內容功能表上選取 [ **新增**  >  **Docker 支援** ]。</span><span class="sxs-lookup"><span data-stu-id="7846e-134">So right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![將 Docker 支援新增至現有專案的內容功能表選項：以滑鼠右鍵按一下專案) 上的 (，> 新增 > Docker 支援。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

<span data-ttu-id="7846e-136">**圖 4-38**.</span><span class="sxs-lookup"><span data-stu-id="7846e-136">**Figure 4-38**.</span></span> <span data-ttu-id="7846e-137">將 Docker 支援新增至現有的專案</span><span class="sxs-lookup"><span data-stu-id="7846e-137">Adding Docker support to an existing project</span></span>

<span data-ttu-id="7846e-138">若要完成新增 Docker 支援，您可以選擇 [Windows] 或 [Linux]。</span><span class="sxs-lookup"><span data-stu-id="7846e-138">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="7846e-139">在此情況下，請選取 [ **Linux** ]。</span><span class="sxs-lookup"><span data-stu-id="7846e-139">In this case, select **Linux**.</span></span>

![用於選取 Dockerfile 目標 OS 的選項對話方塊。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

<span data-ttu-id="7846e-141">**圖 4-39**.</span><span class="sxs-lookup"><span data-stu-id="7846e-141">**Figure 4-39**.</span></span> <span data-ttu-id="7846e-142">選取 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="7846e-142">Selecting Linux containers.</span></span>

<span data-ttu-id="7846e-143">有了這些簡單的步驟，您就能在 Linux 容器上執行 ASP.NET Core 3.1 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7846e-143">With these simple steps, you have your ASP.NET Core 3.1 application running on a Linux container.</span></span>

<span data-ttu-id="7846e-144">同樣地，您也可以新增一個非常簡單的 **WebApp** 專案 (圖 4-40) 來取用 web API 端點，但此處並不討論詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7846e-144">In a similar way, you can also add a very simple **WebApp** project (Figure 4-40) to consume the web API endpoint, although the details are not discussed here.</span></span>

<span data-ttu-id="7846e-145">之後，您可以為 **WebApi** 專案新增協調器支援4-40，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="7846e-145">After that, you add orchestrator support for your **WebApi** project as shown next, in image 4-40.</span></span>

![將協調器支援新增至 WebApi 專案](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

<span data-ttu-id="7846e-147">**圖 4-40**.</span><span class="sxs-lookup"><span data-stu-id="7846e-147">**Figure 4-40**.</span></span> <span data-ttu-id="7846e-148">將協調器支援新增至 *WebApi* 專案。</span><span class="sxs-lookup"><span data-stu-id="7846e-148">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="7846e-149">當您選擇可 `Docker Compose` 用於本機開發的選項時，Visual Studio 會新增 docker 撰寫專案和 docker 組成的檔案，如影像4-41 所示。</span><span class="sxs-lookup"><span data-stu-id="7846e-149">When you choose the `Docker Compose` option, which is fine for local development, Visual Studio adds the docker-compose project, with the docker-compose files as shown in image 4-41.</span></span>

![Docker-撰寫新增至解決方案](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

<span data-ttu-id="7846e-151">**圖 4-41**.</span><span class="sxs-lookup"><span data-stu-id="7846e-151">**Figure 4-41**.</span></span> <span data-ttu-id="7846e-152">將協調器支援新增至 *WebApi* 專案。</span><span class="sxs-lookup"><span data-stu-id="7846e-152">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="7846e-153">新增的初始檔案如下所示：</span><span class="sxs-lookup"><span data-stu-id="7846e-153">The initial files added are similar to these ones:</span></span>

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

<span data-ttu-id="7846e-154">若要讓您的應用程式執行 Docker Compose 您只要進行一些調整 `docker-compose.override.yml`</span><span class="sxs-lookup"><span data-stu-id="7846e-154">To have you app running with Docker Compose you just have to make a few tweaks to `docker-compose.override.yml`</span></span>

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

<span data-ttu-id="7846e-155">現在您可以使用 **F5** 鍵來執行應用程式，或使用 [ **播放** ] 按鈕或按 **Ctrl + F5** 鍵，選取 docker 撰寫專案，如 [圖 4-42] 所示。</span><span class="sxs-lookup"><span data-stu-id="7846e-155">Now you can run your application with the **F5** key, or by using the **Play** button, or the **Ctrl+F5** key, selecting the docker-compose project, as shown in image 4-42.</span></span>

![使用 Visual Studio 執行 docker 撰寫專案](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

<span data-ttu-id="7846e-157">**圖 4-42**.</span><span class="sxs-lookup"><span data-stu-id="7846e-157">**Figure 4-42**.</span></span> <span data-ttu-id="7846e-158">將協調器支援新增至 *WebApi* 專案。</span><span class="sxs-lookup"><span data-stu-id="7846e-158">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="7846e-159">如所述執行 docker 撰寫應用程式時，您會取得：</span><span class="sxs-lookup"><span data-stu-id="7846e-159">When running the docker-compose application as explained, you get:</span></span>

1. <span data-ttu-id="7846e-160">建立的映射和依 docker 撰寫的檔案建立的容器。</span><span class="sxs-lookup"><span data-stu-id="7846e-160">The images built and containers created as per the docker-compose file.</span></span>
2. <span data-ttu-id="7846e-161">瀏覽器會在專案的 [屬性] 對話方塊中設定的位址開啟 `docker-compose` 。</span><span class="sxs-lookup"><span data-stu-id="7846e-161">The browser open in the address configured in the "Properties" dialog for the `docker-compose` project.</span></span>
3. <span data-ttu-id="7846e-162">[ **容器** ] 視窗會在 Visual Studio 2019 16.4 版和更新版本的) 中開啟 (。</span><span class="sxs-lookup"><span data-stu-id="7846e-162">The **Container** window open (in Visual Studio 2019 version 16.4 and later).</span></span>
4. <span data-ttu-id="7846e-163">解決方案中所有專案的偵錯工具支援，如下列影像所示。</span><span class="sxs-lookup"><span data-stu-id="7846e-163">Debugger support for all projects in the solution, as shown in the following images.</span></span>

<span data-ttu-id="7846e-164">開啟瀏覽器：</span><span class="sxs-lookup"><span data-stu-id="7846e-164">Browser opened:</span></span>

![Web 應用程式正在執行的瀏覽器視圖](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

<span data-ttu-id="7846e-166">**圖 4-43**.</span><span class="sxs-lookup"><span data-stu-id="7846e-166">**Figure 4-43**.</span></span> <span data-ttu-id="7846e-167">在多個容器上執行應用程式的瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="7846e-167">Browser window with an application running on multiple containers.</span></span>

<span data-ttu-id="7846e-168">容器視窗：</span><span class="sxs-lookup"><span data-stu-id="7846e-168">Containers window:</span></span>

![Visual Studio [容器] 視窗](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

<span data-ttu-id="7846e-170">**圖 4-44**.</span><span class="sxs-lookup"><span data-stu-id="7846e-170">**Figure 4-44**.</span></span> <span data-ttu-id="7846e-171">Visual Studio [容器] 視窗</span><span class="sxs-lookup"><span data-stu-id="7846e-171">Visual Studio "Containers" window</span></span>

<span data-ttu-id="7846e-172">[ **容器** ] 視窗可讓您查看執行中的容器、流覽可用的影像、查看環境變數、記錄和埠對應、檢查檔案系統、附加偵錯工具，或在容器環境內開啟終端機視窗。</span><span class="sxs-lookup"><span data-stu-id="7846e-172">The **Containers** window lets you view running containers, browse available images, view environment variables, logs, and port mappings, inspect the filesystem, attach a debugger, or open a terminal window inside the container environment.</span></span>

<span data-ttu-id="7846e-173">如您所見，Visual Studio 2019 與 Docker 之間的整合完全是以開發人員的生產力為導向。</span><span class="sxs-lookup"><span data-stu-id="7846e-173">As you can see, the integration between Visual Studio 2019 and Docker is completely oriented to the developer's productivity.</span></span>

<span data-ttu-id="7846e-174">當然，您也可以使用命令來列出映射 `docker images` 。</span><span class="sxs-lookup"><span data-stu-id="7846e-174">Of course, you can also list the images using the `docker images` command.</span></span> <span data-ttu-id="7846e-175">您應該會看到 `webapi` 和 `webapp` 影像，以及使用 `dev` Visual Studio 2019 自動部署專案所建立的標記。</span><span class="sxs-lookup"><span data-stu-id="7846e-175">You should see the `webapi` and `webapp` images with the `dev` tags created by the automatic deployment of our project with Visual Studio 2019.</span></span>

```console
docker images
```

![Docker images 命令的主控台輸出會顯示清單，其中包含：存放庫、標籤、映射識別碼、建立 (日期) 和大小。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

<span data-ttu-id="7846e-177">**圖 4-45**.</span><span class="sxs-lookup"><span data-stu-id="7846e-177">**Figure 4-45**.</span></span> <span data-ttu-id="7846e-178">Docker 映像檢視</span><span class="sxs-lookup"><span data-stu-id="7846e-178">View of Docker images</span></span>

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a><span data-ttu-id="7846e-179">在 Azure Container Registry (ACR 中註冊方案) </span><span class="sxs-lookup"><span data-stu-id="7846e-179">Register the Solution in an Azure Container Registry (ACR)</span></span>

<span data-ttu-id="7846e-180">您可以將映射上傳至 [Azure Container Registry (ACR) ](https://azure.microsoft.com/services/container-registry/)，但您也可以使用 Docker Hub 或其他任何登錄，以便從該登錄將映射部署至 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="7846e-180">You can upload the images to the [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), but you could also use Docker Hub or any other registry, so the images can be deployed to the AKS cluster from that registry.</span></span>

### <a name="create-an-acr-instance"></a><span data-ttu-id="7846e-181">建立 ACR 實例</span><span class="sxs-lookup"><span data-stu-id="7846e-181">Create an ACR instance</span></span>

<span data-ttu-id="7846e-182">從 **az cli** 執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7846e-182">Run the following command from the **az cli** :</span></span>

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="7846e-183">容器登錄名稱 (例如 `exploredocker` ，) 在 Azure 中必須是唯一的，且包含5-50 個英數位元。</span><span class="sxs-lookup"><span data-stu-id="7846e-183">The container registry name (e.g `exploredocker`) must be unique within Azure, and contain 5-50 alphanumeric characters.</span></span> <span data-ttu-id="7846e-184">如需詳細資訊，請參閱 [Create a container registry](/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)</span><span class="sxs-lookup"><span data-stu-id="7846e-184">For more details, refer [Create a container registry](/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="7846e-185">在 [發行] 模式中建立映像</span><span class="sxs-lookup"><span data-stu-id="7846e-185">Create the image in Release mode</span></span>

<span data-ttu-id="7846e-186">您現在會在 [ **發行** ] 模式中建立映射 (準備好用於生產) ，方法是變更為 [ **發行** ]，如 [圖 4-46] 所示，然後執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7846e-186">You'll now create the image in **Release** mode (ready for production) by changing to **Release** , as shown in Figure 4-46, and running the application as you did before.</span></span>

![在 [發行] 模式中建置的 VS 工具列選項。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

<span data-ttu-id="7846e-188">**圖 4-46**.</span><span class="sxs-lookup"><span data-stu-id="7846e-188">**Figure 4-46**.</span></span> <span data-ttu-id="7846e-189">選取 [發行] 模式</span><span class="sxs-lookup"><span data-stu-id="7846e-189">Selecting Release Mode</span></span>

<span data-ttu-id="7846e-190">如果您執行此 `docker images` 命令，您會看到兩個建立的映射，一個用於 `debug` ( **開發** ) ，另一個用於 `release` ( **最新** 的) 模式。</span><span class="sxs-lookup"><span data-stu-id="7846e-190">If you execute the `docker images` command, you'll see both images created, one for `debug` ( **dev** ) and the other for `release` ( **latest** ) mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="7846e-191">為映像建立新的標記</span><span class="sxs-lookup"><span data-stu-id="7846e-191">Create a new Tag for the Image</span></span>

<span data-ttu-id="7846e-192">每個容器映像都必須標記登錄的 `loginServer` 名稱。</span><span class="sxs-lookup"><span data-stu-id="7846e-192">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="7846e-193">將容器映像推送到映像登錄時，此標籤可用於路由傳送。</span><span class="sxs-lookup"><span data-stu-id="7846e-193">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="7846e-194">您可以從 Azure 入口網站檢視 `loginServer` 名稱，然後從 Azure Container Registry 擷取資訊</span><span class="sxs-lookup"><span data-stu-id="7846e-194">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Azure Container Registry 名稱的瀏覽器檢視，位於右上方。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

<span data-ttu-id="7846e-196">**圖 4-47**.</span><span class="sxs-lookup"><span data-stu-id="7846e-196">**Figure 4-47**.</span></span> <span data-ttu-id="7846e-197">Registry 名稱檢視</span><span class="sxs-lookup"><span data-stu-id="7846e-197">View of the name of the Registry</span></span>

<span data-ttu-id="7846e-198">或執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7846e-198">Or by running the following command:</span></span>

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![上述命令的主控台輸出。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

<span data-ttu-id="7846e-200">**圖 4-48**.</span><span class="sxs-lookup"><span data-stu-id="7846e-200">**Figure 4-48**.</span></span> <span data-ttu-id="7846e-201">使用 **az cli** 取得登錄的名稱</span><span class="sxs-lookup"><span data-stu-id="7846e-201">Get the name of the registry using **az cli**</span></span>

<span data-ttu-id="7846e-202">在這兩種情況下，您都會取得名稱。</span><span class="sxs-lookup"><span data-stu-id="7846e-202">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="7846e-203">在我們的範例中為 `exploredocker.azurecr.io`。</span><span class="sxs-lookup"><span data-stu-id="7846e-203">In our example, `exploredocker.azurecr.io`.</span></span>

<span data-ttu-id="7846e-204">現在您可以使用命令來標記映像，然後擷取最新的映像 (發行映像)：</span><span class="sxs-lookup"><span data-stu-id="7846e-204">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

<span data-ttu-id="7846e-205">執行 `docker tag` 命令之後，請使用 `docker images` 命令列出映像，您應該會看到具有新標記的映像。</span><span class="sxs-lookup"><span data-stu-id="7846e-205">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![docker images 命令的主控台輸出。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

<span data-ttu-id="7846e-207">**圖 4-49**.</span><span class="sxs-lookup"><span data-stu-id="7846e-207">**Figure 4-49**.</span></span> <span data-ttu-id="7846e-208">已標記的映像檢視</span><span class="sxs-lookup"><span data-stu-id="7846e-208">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="7846e-209">將映像推送到 Azure ACR</span><span class="sxs-lookup"><span data-stu-id="7846e-209">Push the image into the Azure ACR</span></span>

<span data-ttu-id="7846e-210">登入 Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="7846e-210">Log in to the Azure Container Registry</span></span>

```console
az acr login --name exploredocker
```

<span data-ttu-id="7846e-211">使用下列命令將映像推送到 Azure ACR：</span><span class="sxs-lookup"><span data-stu-id="7846e-211">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push <login-server-name>/<image-name>:v1
```

<span data-ttu-id="7846e-212">此命令需要一些時間上傳映像，但會在程序中提供回饋給您。</span><span class="sxs-lookup"><span data-stu-id="7846e-212">This command takes a while uploading the images but gives you feedback in the process.</span></span> <span data-ttu-id="7846e-213">在下圖中，您可以看到一個映射的輸出已完成，另一個則在進行中。</span><span class="sxs-lookup"><span data-stu-id="7846e-213">In the following image, you can see the output from one image completed and another in progress.</span></span>

![Docker push 命令的主控台輸出。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

<span data-ttu-id="7846e-215">**圖 4-50** 。</span><span class="sxs-lookup"><span data-stu-id="7846e-215">**Figure 4-50**.</span></span> <span data-ttu-id="7846e-216">推播命令的主控台輸出。</span><span class="sxs-lookup"><span data-stu-id="7846e-216">Console output from the push command.</span></span>

<span data-ttu-id="7846e-217">若要將多容器應用程式部署到您的 AKS 叢集中，您需要一些具有的資訊清單檔案 `.yaml` ，而這些屬性大多取自 `docker-compose.yml` 和檔案 `docker-compose.override.yml` 。</span><span class="sxs-lookup"><span data-stu-id="7846e-217">To deploy your multi-container app into your AKS cluster you need some manifest `.yaml` files that have, most of the properties taken from the `docker-compose.yml` and `docker-compose.override.yml` files.</span></span>

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> <span data-ttu-id="7846e-218">先前的檔案 `.yml` 只會 `HTTP` 使用參數來啟用埠， `ASPNETCORE_URLS` 以避免範例應用程式中遺失的憑證發生問題。</span><span class="sxs-lookup"><span data-stu-id="7846e-218">The previous `.yml` files only enable the `HTTP` ports, using the `ASPNETCORE_URLS` parameter, to avoid issues with the missing certificate in the sample app.</span></span>

> [!TIP]
> <span data-ttu-id="7846e-219">您可以在本指南的 [**部署到 Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) 一節中，了解如何為此範例建立 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="7846e-219">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

<span data-ttu-id="7846e-220">現在您已準備好使用 **kubectl** 進行部署，但您必須先使用下列命令從 AKS 叢集中取得認證：</span><span class="sxs-lookup"><span data-stu-id="7846e-220">Now you're almost ready to deploy using **kubectl** , but first you must get the credentials from the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![上述命令的主控台輸出：合併 "aks" 作為 C:\Users\Miguel.kube\config 中的目前內容](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

<span data-ttu-id="7846e-222">**圖 4-51** 。</span><span class="sxs-lookup"><span data-stu-id="7846e-222">**Figure 4-51**.</span></span> <span data-ttu-id="7846e-223">從 AKS 到 kubectl 環境中取得認證。</span><span class="sxs-lookup"><span data-stu-id="7846e-223">Getting credentials from AKS into the kubectl environment.</span></span>

<span data-ttu-id="7846e-224">您也必須使用下列命令，讓 AKS 叢集從 ACR 提取映射：</span><span class="sxs-lookup"><span data-stu-id="7846e-224">You also have to allow the AKS cluster to pull images from the ACR, using this command:</span></span>

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

<span data-ttu-id="7846e-225">上一個命令可能需要幾分鐘的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="7846e-225">The previous command might take a couple of minutes to complete.</span></span> <span data-ttu-id="7846e-226">然後，使用 `kubectl apply` 命令來啟動部署，然後 `kubectl get all` 取得叢集物件的清單。</span><span class="sxs-lookup"><span data-stu-id="7846e-226">Then, use the `kubectl apply` command to launch the deployments, and then `kubectl get all` get list the cluster objects.</span></span>

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![上述命令的主控台輸出：套用的部署。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

<span data-ttu-id="7846e-229">**圖 4-52** 。</span><span class="sxs-lookup"><span data-stu-id="7846e-229">**Figure 4-52**.</span></span> <span data-ttu-id="7846e-230">部署至 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7846e-230">Deployment to Kubernetes</span></span>

<span data-ttu-id="7846e-231">您必須等候一段時間，直到負載平衡器取得外部 IP 並檢查，然後 `kubectl get services` 應用程式應該可在該位址使用，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="7846e-231">You'll have to wait a while until the load balancer gets the external IP, checking with `kubectl get services`, and then the application should be available at that address, as shown in the next image:</span></span>

![部署至 AKS 之應用程式的瀏覽器視圖](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

<span data-ttu-id="7846e-233">**圖 4-53** 。</span><span class="sxs-lookup"><span data-stu-id="7846e-233">**Figure 4-53**.</span></span> <span data-ttu-id="7846e-234">部署至 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7846e-234">Deployment to Kubernetes</span></span>

<span data-ttu-id="7846e-235">當部署完成時，您可以使用 ssh 通道，以本機 proxy 存取 [Kubernetes WEB UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) 。</span><span class="sxs-lookup"><span data-stu-id="7846e-235">When the deployment completes, you can access the [Kubernetes Web UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) with a local proxy, using an ssh tunnel.</span></span>

<span data-ttu-id="7846e-236">首先，您必須使用下列命令建立 ClusterRoleBinding：</span><span class="sxs-lookup"><span data-stu-id="7846e-236">First you must create a ClusterRoleBinding with the following command:</span></span>

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

<span data-ttu-id="7846e-237">然後，此命令會啟動 proxy：</span><span class="sxs-lookup"><span data-stu-id="7846e-237">And then this command to start the proxy:</span></span>

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

<span data-ttu-id="7846e-238">瀏覽器視窗應該會開啟， `http://127.0.0.1:8001` 並顯示如下：</span><span class="sxs-lookup"><span data-stu-id="7846e-238">A browser window should open at `http://127.0.0.1:8001` with a view similar to this one:</span></span>

![Kubernetes 儀表板的瀏覽器檢視，其中顯示 [部署]、[Pod]、[複本集] 和 [服務]。](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

<span data-ttu-id="7846e-240">**圖 4-54** 。</span><span class="sxs-lookup"><span data-stu-id="7846e-240">**Figure 4-54**.</span></span> <span data-ttu-id="7846e-241">檢視 Kubernetes 叢集資訊</span><span class="sxs-lookup"><span data-stu-id="7846e-241">View Kubernetes cluster information</span></span>

<span data-ttu-id="7846e-242">現在您已有 ASP.NET Core 應用程式，在 Linux 容器中執行，並部署至 Azure 上的 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="7846e-242">Now you have your ASP.NET Core application, running in Linux containers, and deployed to an AKS cluster on Azure.</span></span>

> [!NOTE]
> <span data-ttu-id="7846e-243">如需使用 Kubernetes 部署的詳細資訊，請參閱：<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="7846e-243">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="7846e-244">[上一個](set-up-windows-containers-with-powershell.md) 
> [下一步](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="7846e-244">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
