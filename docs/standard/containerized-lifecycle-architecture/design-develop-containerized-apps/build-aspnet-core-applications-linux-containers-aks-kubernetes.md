---
title: 建置 ASP.NET Core 2.1 應用程式與 Linux 容器部署到 AKS/Kubernetes 叢集
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: a00a5c42facb105a23cd85fce79f9fd16a96ccfa
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835508"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="d6eb1-103">建置 ASP.NET Core 2.1 應用程式與 Linux 容器部署至 AKS/Kubernetes orchestrator</span><span class="sxs-lookup"><span data-stu-id="d6eb1-103">Build ASP.NET Core 2.1 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="d6eb1-104">Azure Kubernetes Service (AKS) 是簡化容器部署和管理的 Azure 的受管理的 Kubernetes 協調流程服務 」。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="d6eb1-105">AKS 主要功能如下：</span><span class="sxs-lookup"><span data-stu-id="d6eb1-105">AKS main features are:</span></span>

- <span data-ttu-id="d6eb1-106">Azure 託管的控制平面</span><span class="sxs-lookup"><span data-stu-id="d6eb1-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="d6eb1-107">自動化的升級</span><span class="sxs-lookup"><span data-stu-id="d6eb1-107">Automated upgrades</span></span>
- <span data-ttu-id="d6eb1-108">自我修復</span><span class="sxs-lookup"><span data-stu-id="d6eb1-108">Self-healing</span></span>
- <span data-ttu-id="d6eb1-109">使用者可設定調整</span><span class="sxs-lookup"><span data-stu-id="d6eb1-109">User configurable scaling</span></span>
- <span data-ttu-id="d6eb1-110">開發人員和叢集操作員更簡單的使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="d6eb1-111">下列範例會探索建立的 ASP.NET Core 2.1 應用程式在 Linux 上執行，且開發完成時，會部署到 AKS 叢集在 Azure 中，使用 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-111">The following examples explore the creation of an ASP.NET Core 2.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a><span data-ttu-id="d6eb1-112">建立 ASP.NET Core 2.1 專案使用 Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d6eb1-112">Creating the ASP.NET Core 2.1 Project using Visual Studio 2017</span></span>

<span data-ttu-id="d6eb1-113">ASP.NET Core 是由 Microsoft 與 GitHub 上的.NET 社群維護的一般用途開發平台。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="d6eb1-114">它可以跨平台支援 Windows、macOS 及 Linux，並可用於裝置、雲端和內嵌式系統/IoT等應用情境。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-114">It is cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="d6eb1-115">此範例使用的簡單專案為基礎的 Visual Studio Web API 範本中，因此您不需要任何額外的知識，來建立範例。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-115">This example uses a simple project that's based based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="d6eb1-116">您只需要使用標準的範本，其中包含透過 REST API，使用 ASP.NET Core 2.1 技術執行小型專案的所有項目建立專案。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.1 technology.</span></span>

![在 Visual Studio 中，選取 ASP.NET Core Web 應用程式中加入新的 專案 視窗。](media/create-aspnet-core-application.png)

<span data-ttu-id="d6eb1-118">**圖 4-36**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-118">**Figure 4-36**.</span></span> <span data-ttu-id="d6eb1-119">建立 ASP.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="d6eb1-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="d6eb1-120">若要建立範例專案在 Visual Studio 中，選取**檔案** > **新增** > **專案**，選取**Web**專案類型的左窗格中，後面接著**ASP.NET Core Web 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="d6eb1-121">Visual Studio 會列出 web 專案範本。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="d6eb1-122">我們的範例中，選取**API**建立 ASP.NET Web API 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="d6eb1-123">請確認您已選取 ASP.NET Core 2.1 作為架構。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-123">Verify that you have selected ASP.NET Core 2.1 as the framework.</span></span> <span data-ttu-id="d6eb1-124">.NET core 2.1 包含 Visual Studio 2017 的最後一個版本中是自動安裝及設定和為您安裝 Visual Studio 2017 時。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-124">.NET Core 2.1 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![針對選取的 API 選項，選取 [ASP.NET Core Web 應用程式類型的 visual Studio] 對話方塊。](media/create-web-api-application.png)

<span data-ttu-id="d6eb1-126">**圖 4-37**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-126">**Figure 4-37**.</span></span> <span data-ttu-id="d6eb1-127">選取 ASP.NET CORE 2.1 和 Web API 專案類型</span><span class="sxs-lookup"><span data-stu-id="d6eb1-127">Selecting ASP.NET CORE 2.1 and Web API project type</span></span>

<span data-ttu-id="d6eb1-128">如果您有任何舊版的.NET Core 時，您可以下載並安裝從 2.1 版<https://www.microsoft.com/net/download/core#/sdk>。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-128">If you have any previous version of .NET Core, you can download and install the 2.1 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="d6eb1-129">建立專案時，您可以新增 Docker 支援，或之後，因此您可以 「 docker 化 」 您的專案在任何時間。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="d6eb1-130">若要在專案建立之後新增 Docker 支援，以滑鼠右鍵按一下方案總管 中的專案節點，然後選取**新增** > **Docker 支援**的操作功能表上。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![若要將 Docker 支援新增至現有的專案快顯功能表選項：以滑鼠右鍵按一下 （專案） > 新增 > Docker 支援。](media/add-docker-support-to-project.png)

<span data-ttu-id="d6eb1-132">**圖 4-38**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-132">**Figure 4-38**.</span></span> <span data-ttu-id="d6eb1-133">將 Docker 支援新增至現有的專案</span><span class="sxs-lookup"><span data-stu-id="d6eb1-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="d6eb1-134">若要完成新增 Docker 支援，您可以選擇 Windows 或 Linux。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="d6eb1-135">在此案例中，選取**Linux**，因為 AKS 不支援 Windows 容器 （如晚期 2018)。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![選項對話方塊以選取目標作業系統的 Dockerfile。](media/select-linux-docker-support.png)

<span data-ttu-id="d6eb1-137">**圖 4-39**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-137">**Figure 4-39**.</span></span> <span data-ttu-id="d6eb1-138">選取 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-138">Selecting Linux containers.</span></span>

<span data-ttu-id="d6eb1-139">透過這些簡單的步驟，您會有 Linux 容器上執行的 ASP.NET Core 2.1 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-139">With these simple steps, you have your ASP.NET Core 2.1 application running on a Linux container.</span></span>

<span data-ttu-id="d6eb1-140">如您所見，Visual Studio 2017 與 Docker 之間的整合是完全導向的開發人員生產力。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="d6eb1-141">現在，您可以執行您的應用程式**F5**鍵，或使用**播放** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="d6eb1-142">執行專案之後, 您可以列出使用的映像`docker images`命令。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="d6eb1-143">您應該會看到`mssampleapplication`我們使用 Visual Studio 2017 的專案自動部署所建立的映像。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![主控台輸出 docker 映像的命令，從顯示的清單：存放庫、 標記、 映像識別碼、 建立 （日期） 和大小。](media/docker-images-command.png)

<span data-ttu-id="d6eb1-145">**圖 4-40**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-145">**Figure 4-40**.</span></span> <span data-ttu-id="d6eb1-146">Docker 映像的檢視</span><span class="sxs-lookup"><span data-stu-id="d6eb1-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="d6eb1-147">在 Azure 容器登錄中註冊方案</span><span class="sxs-lookup"><span data-stu-id="d6eb1-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="d6eb1-148">例如，任何 Docker 登錄，來上傳映像[Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/)或 Docker Hub，讓映像可以從登錄部署至 AKS 叢集。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="d6eb1-149">在此情況下，我們在影像上傳到 Azure Container Registry。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="d6eb1-150">在發行模式中建立映像</span><span class="sxs-lookup"><span data-stu-id="d6eb1-150">Create the image in Release mode</span></span>

<span data-ttu-id="d6eb1-151">我們現在將建立中的映像**發行**變更為 （可用於生產環境） 的模式**版本**，如下圖 4-41，並執行應用程式，如同我們先前所示。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![工具列選項在 VS 中以發行模式建置。](media/select-release-mode.png)

<span data-ttu-id="d6eb1-153">**圖 4-41**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-153">**Figure 4-41**.</span></span> <span data-ttu-id="d6eb1-154">選取 [發行] 模式</span><span class="sxs-lookup"><span data-stu-id="d6eb1-154">Selecting Release Mode</span></span>

<span data-ttu-id="d6eb1-155">如果您執行`docker image`命令，您會看到這兩個建立的映像，一個用於`debug`和另一個則用於`release`模式。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="d6eb1-156">映像建立新標記</span><span class="sxs-lookup"><span data-stu-id="d6eb1-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="d6eb1-157">每個容器映像必須加上`loginServer`登錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="d6eb1-158">此標記用於路由時將容器映像推送到映像登錄。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="d6eb1-159">您可以檢視`loginServer`名稱從 Azure 入口網站中，從 Azure Container Registry 中取得資訊</span><span class="sxs-lookup"><span data-stu-id="d6eb1-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Azure 容器登錄名稱的瀏覽器檢視右上方。](media/loginServer-name.png)

<span data-ttu-id="d6eb1-161">**圖 4-42**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-161">**Figure 4-42**.</span></span> <span data-ttu-id="d6eb1-162">登錄名稱的檢視</span><span class="sxs-lookup"><span data-stu-id="d6eb1-162">View of the name of the Registry</span></span>

<span data-ttu-id="d6eb1-163">或藉由執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d6eb1-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![上述命令輸出的主控台。](media/az-cli-loginServer-name.png)

<span data-ttu-id="d6eb1-165">**圖 4-43**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-165">**Figure 4-43**.</span></span> <span data-ttu-id="d6eb1-166">取得使用 PowerShell 的登錄名稱</span><span class="sxs-lookup"><span data-stu-id="d6eb1-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="d6eb1-167">在這兩種情況下，您會取得名稱。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="d6eb1-168">在我們的範例， `mssampleacr.azurecr.io`。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="d6eb1-169">現在您可以標記映像，採用最新的映像 （版本映像），使用命令：</span><span class="sxs-lookup"><span data-stu-id="d6eb1-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="d6eb1-170">執行後`docker tag`命令，列出與映像`docker images`命令，然後您應該會看到具有新標記的映像。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![從 docker images 命令輸出的主控台。](media/tagged-docker-images-list.png)

<span data-ttu-id="d6eb1-172">**圖 4-44**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-172">**Figure 4-44**.</span></span> <span data-ttu-id="d6eb1-173">已加上標記的映像的檢視</span><span class="sxs-lookup"><span data-stu-id="d6eb1-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="d6eb1-174">將映像推送到 Azure ACR</span><span class="sxs-lookup"><span data-stu-id="d6eb1-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="d6eb1-175">將映像推送到 Azure 的 ACR，使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="d6eb1-175">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="d6eb1-176">此命令需要一些時間上傳影像，但可讓您在程序的意見反應。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-176">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![主控台從 docker push 命令的輸出： 顯示每個圖層的字元為基礎的進度列。](media/uploading-image-to-acr.png)

<span data-ttu-id="d6eb1-178">**圖 4-45**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-178">**Figure 4-45**.</span></span> <span data-ttu-id="d6eb1-179">映像上傳至 ACR</span><span class="sxs-lookup"><span data-stu-id="d6eb1-179">Uploading the image to the ACR</span></span>

<span data-ttu-id="d6eb1-180">您可以看到下列結果的程序完成時，您應該取得：</span><span class="sxs-lookup"><span data-stu-id="d6eb1-180">You can see below the result you should get when the process completes:</span></span>

![主控台輸出 docker push 命令，完成之後，顯示所有的圖層或節點。](media/uploading-docker-images-complete.png)

<span data-ttu-id="d6eb1-182">**圖 4-46**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-182">**Figure 4-46**.</span></span> <span data-ttu-id="d6eb1-183">節點檢視</span><span class="sxs-lookup"><span data-stu-id="d6eb1-183">View of nodes</span></span>

<span data-ttu-id="d6eb1-184">下一個步驟是將您的容器部署到 AKS 的 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-184">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="d6eb1-185">為此，您需要的檔案 (**.yml 檔案部署**) 包含下列：</span><span class="sxs-lookup"><span data-stu-id="d6eb1-185">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
        - mane: mssample-services-app
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
> <span data-ttu-id="d6eb1-186">如需使用 Kubernetes 的部署詳細資訊，請參閱： <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="d6eb1-186">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="d6eb1-187">現在，您可以幾乎準備好要部署使用**Kubectl**，但首先您必須取得 AKS 叢集使用此命令的認證：</span><span class="sxs-lookup"><span data-stu-id="d6eb1-187">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![上述命令輸出的主控台：合併"MSSampleK8Cluster 做為目前的內容中 /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="d6eb1-189">**圖 4-47**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-189">**Figure 4-47**.</span></span> <span data-ttu-id="d6eb1-190">取得認證</span><span class="sxs-lookup"><span data-stu-id="d6eb1-190">getting credentials</span></span>

<span data-ttu-id="d6eb1-191">然後，使用`kubectl create`命令，以啟動部署。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-191">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![主控台上述命令的輸出： 部署 「 mssamplesbook 」 建立。](media/kubectl-create-command.png)

<span data-ttu-id="d6eb1-194">**圖 4-48**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-194">**Figure 4-48**.</span></span> <span data-ttu-id="d6eb1-195">部署至 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d6eb1-195">Deploy to Kubernetes</span></span>

<span data-ttu-id="d6eb1-196">完成部署之後，您可以使用本機 proxy，您可以使用此命令暫時存取來存取 Kubernetes 主控台：</span><span class="sxs-lookup"><span data-stu-id="d6eb1-196">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="d6eb1-197">存取的 url 和`http://127.0.0.1:8001`。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-197">And accessing the url `http://127.0.0.1:8001`.</span></span>

![瀏覽器檢視 Kubernetes 儀表板，顯示部署、 Pod，複本集和服務。](media/kubernetes-cluster-information.png)

<span data-ttu-id="d6eb1-199">**圖 4-49**。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-199">**Figure 4-49**.</span></span> <span data-ttu-id="d6eb1-200">檢視 Kubernetes 叢集資訊</span><span class="sxs-lookup"><span data-stu-id="d6eb1-200">View Kubernetes cluster information</span></span>

<span data-ttu-id="d6eb1-201">現在您已在 Azure 上使用 Linux 容器和 AKS 的 Kubernetes 叢集中部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-201">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="d6eb1-202">您可以存取您的應用程式瀏覽至您的服務，您可以從 Azure 入口網站取得的公用 IP。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-202">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="d6eb1-203">您可以了解如何建立 AKS 叢集，此範例一節[**部署到 Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md)有關本指南。</span><span class="sxs-lookup"><span data-stu-id="d6eb1-203">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d6eb1-204">[上一頁](set-up-windows-containers-with-powershell.md)
>[下一頁](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="d6eb1-204">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
