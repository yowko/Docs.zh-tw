---
title: 建置以 Linux 容器部署到 AKS/Kubernetes 叢集的 ASP.NET Core 2.2 應用程式
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.date: 02/25/2019
ms.openlocfilehash: 89843e0041c12f001f974360da2e5903499155d1
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644789"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="d1d1e-103">建置以 Linux 容器部署到 AKS/Kubernetes 協調器的 ASP.NET Core 2.2 應用程式</span><span class="sxs-lookup"><span data-stu-id="d1d1e-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="d1d1e-104">Azure Kubernetes Service (AKS) 是 Azure 的受控 Kubernetes 協調流程服務，可簡化容器部署和管理。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="d1d1e-105">AKS 的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="d1d1e-105">AKS main features are:</span></span>

- <span data-ttu-id="d1d1e-106">Azure 裝載的控制平面</span><span class="sxs-lookup"><span data-stu-id="d1d1e-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="d1d1e-107">自動升級</span><span class="sxs-lookup"><span data-stu-id="d1d1e-107">Automated upgrades</span></span>
- <span data-ttu-id="d1d1e-108">自我修復</span><span class="sxs-lookup"><span data-stu-id="d1d1e-108">Self-healing</span></span>
- <span data-ttu-id="d1d1e-109">可由使用者設定的調整大小功能</span><span class="sxs-lookup"><span data-stu-id="d1d1e-109">User configurable scaling</span></span>
- <span data-ttu-id="d1d1e-110">對開發人員和叢集操作員更簡單的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="d1d1e-111">下列範例探索如何建立在 Linux 上執行並部署到 Azure 中 AKS 叢集的 ASP.NET Core 2.2 應用程式，同時使用 Visual Studio 2017 進行開發。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="d1d1e-112">使用 Visual Studio 2017 建立 ASP.NET Core 2.2 專案</span><span class="sxs-lookup"><span data-stu-id="d1d1e-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="d1d1e-113">ASP.NET Core 是一般用途的開發平台，由 Microsoft 和 GitHub 上的 .NET 社群共同維護。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="d1d1e-114">它可以跨平台支援 Windows、macOS 及 Linux，並可用於裝置、雲端和內嵌式系統/IoT 等應用情節。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="d1d1e-115">此範例使用以 Visual Studio Web API 範本為基礎的簡單專案，因此您不需要任何額外的知識來建立範例。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="d1d1e-116">您只需要使用一個標準範本來建立專案，該範本採用 ASP.NET Core 2.2 技術，內含可透過 REST API 執行小型專案的所有項目。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![在 Visual Studio 中新增專案視窗，並選取 ASP.NET Core Web 應用程式。](media/create-aspnet-core-application.png)

<span data-ttu-id="d1d1e-118">**圖 4-36**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-118">**Figure 4-36**.</span></span> <span data-ttu-id="d1d1e-119">建立 ASP.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="d1d1e-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="d1d1e-120">若要在 Visual Studio 中建立範例專案，請選取 [檔案]   > [新增]   > [專案]  ，然後依序選取左窗格中的 [Web]  專案類型和 [ASP.NET Web 應用程式]  。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="d1d1e-121">Visual Studio 會列出適用於 Web 專案的範本。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="d1d1e-122">在我們的範例中，選取 [API]  以建立 ASP.NET Web API 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="d1d1e-123">確認您已選取 ASP.NET Core 2.2 作為架構。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="d1d1e-124">.NET Core 2.2 隨附於上一版的 Visual Studio 2017，並會在您安裝 Visual Studio 2017 時自動為您安裝和設定。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![用於選取 ASP.NET Core Web 應用程式類型並已選取 API 選項的 Visual Studio 對話方塊。](media/create-web-api-application.png)

<span data-ttu-id="d1d1e-126">**圖 4-37**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-126">**Figure 4-37**.</span></span> <span data-ttu-id="d1d1e-127">選取 ASP.NET CORE 2.2 和 Web API 專案類型</span><span class="sxs-lookup"><span data-stu-id="d1d1e-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="d1d1e-128">如果您有任何舊版 .NET Core，您可以從 <https://www.microsoft.com/net/download/core#/sdk> 下載並安裝 2.2 版。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="d1d1e-129">您可以在建立專案期間或之後新增 Docker 支援，以便可隨時將您的專案「Docker 化」。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="d1d1e-130">若要在建立專案之後新增 Docker 支援，請在 [方案總管] 中以滑鼠右鍵按一下專案節點，然後從操作功能表選取 [新增]   > [Docker 支援]  。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![將 Docker 支援新增至現有專案的操作功能表選項：按一下滑鼠右鍵 (在專案上) > [新增] > [Docker 支援]。](media/add-docker-support-to-project.png)

<span data-ttu-id="d1d1e-132">**圖 4-38**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-132">**Figure 4-38**.</span></span> <span data-ttu-id="d1d1e-133">將 Docker 支援新增至現有的專案</span><span class="sxs-lookup"><span data-stu-id="d1d1e-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="d1d1e-134">若要完成新增 Docker 支援，您可以選擇 [Windows] 或 [Linux]。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="d1d1e-135">在此案例中，請選取 [Linux]  ，因為 AKS 不支援 Windows 容器 (自 2018 年起)。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![用於選取 Dockerfile 目標 OS 的選項對話方塊。](media/select-linux-docker-support.png)

<span data-ttu-id="d1d1e-137">**圖 4-39**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-137">**Figure 4-39**.</span></span> <span data-ttu-id="d1d1e-138">選取 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-138">Selecting Linux containers.</span></span>

<span data-ttu-id="d1d1e-139">透過這些簡單的步驟，您就會有在 Linux 容器上執行的 ASP.NET Core 2.2 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="d1d1e-140">如您所見，Visual Studio 2017 與 Docker 之間的整合完全取決於開發人員生產力。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="d1d1e-141">現在，您可以按 **F5** 鍵或使用 [播放]  按鈕來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="d1d1e-142">執行專案之後，您可以使用 `docker images` 命令列出映像。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="d1d1e-143">您應該會看到使用 Visual Studio 2017 自動部署專案所建立的 `mssampleapplication` 映像。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![docker images 命令的主控台輸出，顯示下列項目清單：存放庫、標記、映像識別碼、建立時間 (日期) 和大小。](media/docker-images-command.png)

<span data-ttu-id="d1d1e-145">**圖 4-40**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-145">**Figure 4-40**.</span></span> <span data-ttu-id="d1d1e-146">Docker 映像檢視</span><span class="sxs-lookup"><span data-stu-id="d1d1e-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="d1d1e-147">在 Azure Container Registry 中註冊方案</span><span class="sxs-lookup"><span data-stu-id="d1d1e-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="d1d1e-148">將映像上傳到任何 Docker 登錄 (例如 [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) 或 Docker Hub)，以便將映像從該登錄部署到 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="d1d1e-149">在此案例中，我們會將映像上傳到 Azure Container Registry。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="d1d1e-150">在 [發行] 模式中建立映像</span><span class="sxs-lookup"><span data-stu-id="d1d1e-150">Create the image in Release mode</span></span>

<span data-ttu-id="d1d1e-151">我們現在要在 [發行]  模式中建立映像 (用於生產環境)，做法是變更為 [發行]  (如圖 4-41 所示)，然後如往常般執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![在 [發行] 模式中建置的 VS 工具列選項。](media/select-release-mode.png)

<span data-ttu-id="d1d1e-153">**圖 4-41**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-153">**Figure 4-41**.</span></span> <span data-ttu-id="d1d1e-154">選取 [發行] 模式</span><span class="sxs-lookup"><span data-stu-id="d1d1e-154">Selecting Release Mode</span></span>

<span data-ttu-id="d1d1e-155">如果您執行 `docker image` 命令，您會看到建立兩個映像，一個用於 `debug` 模式，另一個用於 `release` 模式。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="d1d1e-156">為映像建立新的標記</span><span class="sxs-lookup"><span data-stu-id="d1d1e-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="d1d1e-157">每個容器映像都必須標記登錄的 `loginServer` 名稱。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="d1d1e-158">將容器映像推送到映像登錄時，此標籤可用於路由傳送。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="d1d1e-159">您可以從 Azure 入口網站檢視 `loginServer` 名稱，然後從 Azure Container Registry 擷取資訊</span><span class="sxs-lookup"><span data-stu-id="d1d1e-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Azure Container Registry 名稱的瀏覽器檢視，位於右上方。](media/loginServer-name.png)

<span data-ttu-id="d1d1e-161">**圖 4-42**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-161">**Figure 4-42**.</span></span> <span data-ttu-id="d1d1e-162">Registry 名稱檢視</span><span class="sxs-lookup"><span data-stu-id="d1d1e-162">View of the name of the Registry</span></span>

<span data-ttu-id="d1d1e-163">或執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d1d1e-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![上述命令的主控台輸出。](media/az-cli-loginServer-name.png)

<span data-ttu-id="d1d1e-165">**圖 4-43**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-165">**Figure 4-43**.</span></span> <span data-ttu-id="d1d1e-166">使用 PowerShell 取得登錄名稱</span><span class="sxs-lookup"><span data-stu-id="d1d1e-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="d1d1e-167">在這兩種情況下，您都會取得名稱。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="d1d1e-168">在我們的範例中為 `mssampleacr.azurecr.io`。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="d1d1e-169">現在您可以使用命令來標記映像，然後擷取最新的映像 (發行映像)：</span><span class="sxs-lookup"><span data-stu-id="d1d1e-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="d1d1e-170">執行 `docker tag` 命令之後，請使用 `docker images` 命令列出映像，您應該會看到具有新標記的映像。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![docker images 命令的主控台輸出。](media/tagged-docker-images-list.png)

<span data-ttu-id="d1d1e-172">**圖 4-44**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-172">**Figure 4-44**.</span></span> <span data-ttu-id="d1d1e-173">已標記的映像檢視</span><span class="sxs-lookup"><span data-stu-id="d1d1e-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="d1d1e-174">將映像推送到 Azure ACR</span><span class="sxs-lookup"><span data-stu-id="d1d1e-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="d1d1e-175">登入 Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="d1d1e-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="d1d1e-176">使用下列命令將映像推送到 Azure ACR：</span><span class="sxs-lookup"><span data-stu-id="d1d1e-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="d1d1e-177">此命令需要一些時間上傳映像，但會在程序中提供回饋給您。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![docker push 命令的主控台輸出：顯示以字元為主的進度列來表示每個圖層。](media/uploading-image-to-acr.png)

<span data-ttu-id="d1d1e-179">**圖 4-45**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-179">**Figure 4-45**.</span></span> <span data-ttu-id="d1d1e-180">將映像上傳到 ACR</span><span class="sxs-lookup"><span data-stu-id="d1d1e-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="d1d1e-181">當程序完成時，您應該會收到如下所示的結果：</span><span class="sxs-lookup"><span data-stu-id="d1d1e-181">You can see below the result you should get when the process completes:</span></span>

![docker push 命令的主控台輸出，已完成，並顯示所有圖層或節點。](media/uploading-docker-images-complete.png)

<span data-ttu-id="d1d1e-183">**圖 4-46**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-183">**Figure 4-46**.</span></span> <span data-ttu-id="d1d1e-184">節點檢視</span><span class="sxs-lookup"><span data-stu-id="d1d1e-184">View of nodes</span></span>

<span data-ttu-id="d1d1e-185">下一個步驟是將您的容器部署到 AKS Kubernetess 叢集。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="d1d1e-186">為此，您需要包含下列內容的檔案 ( **.yml 部署檔案**)：</span><span class="sxs-lookup"><span data-stu-id="d1d1e-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - name: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> <span data-ttu-id="d1d1e-187">如需使用 Kubernetes 部署的詳細資訊，請參閱：<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="d1d1e-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="d1d1e-188">現在，您幾乎準備好使用 **Kubectl** 進行部署，但首先，您必須使用下列命令將認證擷取到 AKS 叢集：</span><span class="sxs-lookup"><span data-stu-id="d1d1e-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![上述命令的主控台輸出：已將 "MSSampleK8Cluster 合併為 /root/.kube/config 中的目前內容](media/getting-aks-credentials.png)

<span data-ttu-id="d1d1e-190">**圖 4-47**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-190">**Figure 4-47**.</span></span> <span data-ttu-id="d1d1e-191">取得認證</span><span class="sxs-lookup"><span data-stu-id="d1d1e-191">getting credentials</span></span>

<span data-ttu-id="d1d1e-192">然後，使用 `kubectl create` 命令啟動部署。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![上述命令的主控台輸出：已建立部署 "mssamplesbook"。](media/kubectl-create-command.png)

<span data-ttu-id="d1d1e-195">**圖 4-48**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-195">**Figure 4-48**.</span></span> <span data-ttu-id="d1d1e-196">部署至 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d1d1e-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="d1d1e-197">部署完成時，您可以使用可透過下列命令暫時存取的本機 Proxy 來存取 Kubernetes 主控台：</span><span class="sxs-lookup"><span data-stu-id="d1d1e-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="d1d1e-198">然後存取 URL `http://127.0.0.1:8001`。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Kubernetes 儀表板的瀏覽器檢視，其中顯示 [部署]、[Pod]、[複本集] 和 [服務]。](media/kubernetes-cluster-information.png)

<span data-ttu-id="d1d1e-200">**圖 4-49**.</span><span class="sxs-lookup"><span data-stu-id="d1d1e-200">**Figure 4-49**.</span></span> <span data-ttu-id="d1d1e-201">檢視 Kubernetes 叢集資訊</span><span class="sxs-lookup"><span data-stu-id="d1d1e-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="d1d1e-202">現在您已使用 Linux 容器和 AKS Kubernetes 叢集在 Azure 上部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="d1d1e-203">您可以存取瀏覽至您服務公用 IP 的應用程式，並可從 Azure 入口網站取得此服務。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="d1d1e-204">您可以在本指南的[**部署到 Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) 一節中，了解如何為此範例建立 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="d1d1e-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d1d1e-205">[上一頁](set-up-windows-containers-with-powershell.md)
>[下一頁](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="d1d1e-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
