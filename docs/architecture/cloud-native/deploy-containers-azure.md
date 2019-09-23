---
title: 在 Azure 中部署容器
description: 使用 Azure Container Registry、Azure Kubernetes Service 和 Azure Dev Spaces 在 Azure 中部署容器。
ms.date: 06/30/2019
ms.openlocfilehash: 6d95db26b6a45dd6825c88693308ffe90d1ed071
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183263"
---
# <a name="deploying-containers-in-azure"></a><span data-ttu-id="78ba0-103">在 Azure 中部署容器</span><span class="sxs-lookup"><span data-stu-id="78ba0-103">Deploying containers in Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="78ba0-104">容器提供許多優點，其中一個是可攜性。</span><span class="sxs-lookup"><span data-stu-id="78ba0-104">Containers provide many benefits, one of which is portability.</span></span> <span data-ttu-id="78ba0-105">您可以輕鬆地採用您已在本機開發和測試的相同容器，並將其部署至 Azure，以便在預備和生產環境中執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="78ba0-105">You can easily take the same container you've developed and tested locally and deploy it to Azure where it can run your app in staging and production environments.</span></span> <span data-ttu-id="78ba0-106">Azure 提供許多適用于容器型應用程式裝載的選項，同樣支援數種不同的部署方法。</span><span class="sxs-lookup"><span data-stu-id="78ba0-106">Azure provides a number of options for container-based app hosting and likewise supports several different means of deployment.</span></span> <span data-ttu-id="78ba0-107">最常見且最有彈性的方法，就是將您的容器部署至 Azure Container Registry （ACR），而您想要使用這些服務來裝載它們。</span><span class="sxs-lookup"><span data-stu-id="78ba0-107">The most common and most flexible approach is to deploy your containers to Azure Container Registry (ACR), where they're accessible by whatever services you wish to use to host them.</span></span> <span data-ttu-id="78ba0-108">Azure 用於容器的 Web App、Azure Kubernetes Services （AKS）和 Azure 容器實例（ACI）都可以存取已推送至 ACR 的容器映射。</span><span class="sxs-lookup"><span data-stu-id="78ba0-108">Azure Web App for Containers, Azure Kubernetes Services (AKS), and Azure Container Instance (ACI) all can access container images that have been pushed to ACR.</span></span>

## <a name="azure-container-registry"></a><span data-ttu-id="78ba0-109">Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="78ba0-109">Azure Container Registry</span></span>

<span data-ttu-id="78ba0-110">Azure Container Registry （ACR）可讓您建立、儲存和管理所有容器部署的映射。</span><span class="sxs-lookup"><span data-stu-id="78ba0-110">Azure Container Registry (ACR) lets you build, store, and manage images for all of your container deployments.</span></span> <span data-ttu-id="78ba0-111">還有其他容器登錄，也就是公用和私用，您可以在其中部署容器。</span><span class="sxs-lookup"><span data-stu-id="78ba0-111">There are other container registries, both public and private, to which you can deploy containers.</span></span> <span data-ttu-id="78ba0-112">ACR 透過其他選項的優點是，您可以讓影像靠近生產環境，以改善組建和部署時間。</span><span class="sxs-lookup"><span data-stu-id="78ba0-112">The benefit of ACR over other options is that you can keep your images close to your production environment, improving build and deployment times.</span></span> <span data-ttu-id="78ba0-113">您也可以使用您用於其他 Azure 資源的相同安全性程式來保護它們，以提高安全性並降低資產管理工作。</span><span class="sxs-lookup"><span data-stu-id="78ba0-113">You can also secure them using the same security procedures you use for the rest of your Azure resources, improving security and reducing asset management effort.</span></span>

<span data-ttu-id="78ba0-114">您可以[使用 Azure 入口網站](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal)或[使用 Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli)或[PowerShell 工具](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell)來建立容器登錄。</span><span class="sxs-lookup"><span data-stu-id="78ba0-114">You [create a container registry using the Azure Portal](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) or [using the Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli) or [PowerShell tools](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell).</span></span> <span data-ttu-id="78ba0-115">建立新的 container registry 只需要 Azure 訂用帳戶、資源群組和唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="78ba0-115">Creating a new container registry just requires an Azure subscription, a resource group, and a unique name.</span></span> <span data-ttu-id="78ba0-116">圖3-11 顯示建立登錄的基本選項，其將裝載于*于: registryname*. azurecr.io。</span><span class="sxs-lookup"><span data-stu-id="78ba0-116">Figure 3-11 shows the basic options for creating a registry, which will be hosted at *registryname*.azurecr.io.</span></span>

<span data-ttu-id="78ba0-117">![建立 container registry](./media/create-container-registry.png)
**圖 3-11**。</span><span class="sxs-lookup"><span data-stu-id="78ba0-117">![Create container registry](./media/create-container-registry.png)
**Figure 3-11**.</span></span> <span data-ttu-id="78ba0-118">建立容器登錄</span><span class="sxs-lookup"><span data-stu-id="78ba0-118">Create container registry</span></span>

<span data-ttu-id="78ba0-119">建立登錄之後，您必須先向它進行驗證，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="78ba0-119">Once you've created a registry, you'll need to authenticate with it before you can use it.</span></span> <span data-ttu-id="78ba0-120">一般來說，您會使用 Azure CLI 命令登入登錄：</span><span class="sxs-lookup"><span data-stu-id="78ba0-120">Typically, you'll log into the registry using the Azure CLI command:</span></span>

```azurecli
az acr login --name *registryname*
```

<span data-ttu-id="78ba0-121">在 Azure Container Registry 中建立登錄之後，您就可以使用 docker 命令將容器映射推送到它。</span><span class="sxs-lookup"><span data-stu-id="78ba0-121">Once you've created a registry in Azure Container Registry, you can use docker commands to push container images to it.</span></span> <span data-ttu-id="78ba0-122">不過，在這樣做之前，您必須先使用 ACR 登入伺服器的完整名稱（URL）來標記映射。</span><span class="sxs-lookup"><span data-stu-id="78ba0-122">Before you can do so, however, you must first tag your image with the fully qualified name (URL) of your ACR login server.</span></span> <span data-ttu-id="78ba0-123">這會使用*于: registryname*. azurecr.io 格式。</span><span class="sxs-lookup"><span data-stu-id="78ba0-123">This will have the format *registryname*.azurecr.io.</span></span>

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="78ba0-124">標記影像之後，您可以使用`docker push`命令將映射推送至您的 ACR 實例。</span><span class="sxs-lookup"><span data-stu-id="78ba0-124">After you've tagged the image, you use the `docker push` command to push the image to your ACR instance.</span></span>

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="78ba0-125">將映射推送至登錄之後，使用下列命令從本機 Docker 環境中移除映射是個不錯的主意：</span><span class="sxs-lookup"><span data-stu-id="78ba0-125">After you push an image to the registry, it's a good idea to remove the image from your local Docker environment, using this command:</span></span>

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="78ba0-126">開發人員不應該直接從他們的電腦推送至容器登錄。</span><span class="sxs-lookup"><span data-stu-id="78ba0-126">Developers should rarely push directly from their machines to a container registry.</span></span> <span data-ttu-id="78ba0-127">相反地，在這 Azure DevOps 類工具中定義的組建管線應該負責此程式。</span><span class="sxs-lookup"><span data-stu-id="78ba0-127">Instead, a build pipeline defined in a tool like Azure DevOps should be responsible for this process.</span></span> <span data-ttu-id="78ba0-128">在[雲端原生 DevOps 一章](devops.md)中深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="78ba0-128">Learn more in the [Cloud-Native DevOps chapter](devops.md).</span></span>

## <a name="azure-kubernetes-service"></a><span data-ttu-id="78ba0-129">Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="78ba0-129">Azure Kubernetes Service</span></span>

<span data-ttu-id="78ba0-130">如果您以容器為基礎的應用程式牽涉到多個容器，您很可能會想要使用 Kubernetes 之類的*協調*器來定義和管理容器之間的互動。</span><span class="sxs-lookup"><span data-stu-id="78ba0-130">If your container-based application involves multiple containers, you'll most likely want to define and manage the interactions between the containers using an *orchestrator* like Kubernetes.</span></span> <span data-ttu-id="78ba0-131">將容器映射部署至 ACR 之後，您就可以輕鬆地設定 Azure Kubernetes Services，從 ACR 自動部署更新的映射。</span><span class="sxs-lookup"><span data-stu-id="78ba0-131">Once you've deployed your container images to ACR, you can easily configure Azure Kubernetes Services to automatically deploy updated images from ACR.</span></span> <span data-ttu-id="78ba0-132">備妥完整的 CI/CD 管線之後，您可以設定未完成的[發行](https://martinfowler.com/bliki/CanaryRelease.html)策略，以將快速部署更新時所牽涉到的風險降到最低。</span><span class="sxs-lookup"><span data-stu-id="78ba0-132">With a full CI/CD pipeline in place, you can configure a [canary release](https://martinfowler.com/bliki/CanaryRelease.html) strategy to minimize the risk involved when rapidly deploying updates.</span></span> <span data-ttu-id="78ba0-133">新版本的應用程式一開始會在生產環境中設定，而不會路由傳送流量，然後少數的使用者會路由傳送至新部署的應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="78ba0-133">The new version of the app is initially configured in production with no traffic routed to it, and then a small number of users are routed to the newly-deployed version of the app.</span></span> <span data-ttu-id="78ba0-134">當小組在新版本的軟體中獲得信心時，新版本的更多實例會被推出，而舊版的實例也會淘汰。</span><span class="sxs-lookup"><span data-stu-id="78ba0-134">As the team gains confidence in the new version of the software, more instances of the new version are rolled out and the previous version's instances are retired.</span></span> <span data-ttu-id="78ba0-135">AKS 輕鬆支援這種部署樣式。</span><span class="sxs-lookup"><span data-stu-id="78ba0-135">AKS easily supports this style of deployment.</span></span>

<span data-ttu-id="78ba0-136">如同 Azure 中的大部分資源，您可以使用入口網站建立 Azure Kubernetes 叢集，或使用命令列工具或基礎結構自動化工具（例如 Helm 或 Terraform）。</span><span class="sxs-lookup"><span data-stu-id="78ba0-136">As with most resources in Azure, you can create Azure Kubernetes clusters using the portal or using command line tools or infrastructure automation tools like Helm or Terraform.</span></span> <span data-ttu-id="78ba0-137">若要開始使用新的叢集，您必須提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="78ba0-137">To get started with a new cluster, you need to provide the following information:</span></span>

- <span data-ttu-id="78ba0-138">Azure 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="78ba0-138">Azure subscription</span></span>
- <span data-ttu-id="78ba0-139">資源群組</span><span class="sxs-lookup"><span data-stu-id="78ba0-139">Resource group</span></span>
- <span data-ttu-id="78ba0-140">Kubernetes 叢集名稱</span><span class="sxs-lookup"><span data-stu-id="78ba0-140">Kubernetes cluster name</span></span>
- <span data-ttu-id="78ba0-141">區域</span><span class="sxs-lookup"><span data-stu-id="78ba0-141">Region</span></span>
- <span data-ttu-id="78ba0-142">Kubernetes 版本</span><span class="sxs-lookup"><span data-stu-id="78ba0-142">Kubernetes version</span></span>
- <span data-ttu-id="78ba0-143">DNS 名稱前置詞</span><span class="sxs-lookup"><span data-stu-id="78ba0-143">DNS name prefix</span></span>
- <span data-ttu-id="78ba0-144">節點大小</span><span class="sxs-lookup"><span data-stu-id="78ba0-144">Node size</span></span>
- <span data-ttu-id="78ba0-145">節點計數</span><span class="sxs-lookup"><span data-stu-id="78ba0-145">Node count</span></span>

<span data-ttu-id="78ba0-146">這種資訊就足以開始使用。</span><span class="sxs-lookup"><span data-stu-id="78ba0-146">This information is sufficient to get started.</span></span> <span data-ttu-id="78ba0-147">在 Azure 入口網站中建立程式的過程中，您也可以設定叢集下列功能的選項：</span><span class="sxs-lookup"><span data-stu-id="78ba0-147">As part of the creation process in the Azure Portal, you can also configure options for the following features of your cluster:</span></span>

- <span data-ttu-id="78ba0-148">縮放</span><span class="sxs-lookup"><span data-stu-id="78ba0-148">Scale</span></span>
- <span data-ttu-id="78ba0-149">驗證</span><span class="sxs-lookup"><span data-stu-id="78ba0-149">Authentication</span></span>
- <span data-ttu-id="78ba0-150">網路</span><span class="sxs-lookup"><span data-stu-id="78ba0-150">Networking</span></span>
- <span data-ttu-id="78ba0-151">監視</span><span class="sxs-lookup"><span data-stu-id="78ba0-151">Monitoring</span></span>
- <span data-ttu-id="78ba0-152">Tags</span><span class="sxs-lookup"><span data-stu-id="78ba0-152">Tags</span></span>

<span data-ttu-id="78ba0-153">本[快速入門會逐步引導您使用 Azure 入口網站來部署 AKS](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)叢集。</span><span class="sxs-lookup"><span data-stu-id="78ba0-153">This [quickstart walks through deploying an AKS cluster using the Azure portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).</span></span>

## <a name="azure-dev-spaces"></a><span data-ttu-id="78ba0-154">Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="78ba0-154">Azure Dev Spaces</span></span>

<span data-ttu-id="78ba0-155">複雜的 Kubernetes 叢集可能需要大量的資源來裝載，讓開發人員難以在單一電腦（尤其是膝上型電腦）上執行整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="78ba0-155">Complex Kubernetes clusters can require significant resources to host, which can make it difficult for developers to run the entire application on a single machine (especially a laptop).</span></span> <span data-ttu-id="78ba0-156">Azure Dev Spaces 提供這項解決方案，可讓開發人員使用自己在 Azure 中託管的 Azure Kubernetes 叢集版本。</span><span class="sxs-lookup"><span data-stu-id="78ba0-156">Azure Dev Spaces offers a solution to this by allowing developers to work with their own versions of Azure Kubernetes clusters hosted in Azure.</span></span> <span data-ttu-id="78ba0-157">Azure Dev Spaces 的設計目的是要使用 AKS 輕鬆地開發微服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="78ba0-157">Azure Dev Spaces is designed to ease development of microservice-based applications using AKS.</span></span>

<span data-ttu-id="78ba0-158">若要瞭解 Azure Dev Spaces 的值，請在 Microsoft Azure，讓我在容器的領導處 Gabe Monroy 分享此報價：</span><span class="sxs-lookup"><span data-stu-id="78ba0-158">To understand the value of Azure Dev Spaces, let me share this quotation from Gabe Monroy, PM Lead of Containers at Microsoft Azure:</span></span>

<span data-ttu-id="78ba0-159">「假設您是一個新的員工，嘗試修正由數十個元件組成的複雜微服務應用程式中的 bug，每一個都有自己的設定和支援服務。</span><span class="sxs-lookup"><span data-stu-id="78ba0-159">"Imagine you are a new employee trying to fix a bug in a complex microservices application consisting of dozens of components, each with their own configuration and backing services.</span></span> <span data-ttu-id="78ba0-160">若要開始使用，您必須設定本機開發環境，讓它可以模擬生產，包括設定您的 IDE、建立工具鏈、容器化服務相依性、本機 Kubernetes 環境、支援服務的模擬等等。</span><span class="sxs-lookup"><span data-stu-id="78ba0-160">To get started, you must configure your local development environment so that it can mimic production including setting up your IDE, building tool chain, containerized service dependencies, a local Kubernetes environment, mocks for backing services, and more.</span></span> <span data-ttu-id="78ba0-161">只要設定您的開發環境，修正該第一個錯誤可能需要數天的時間。</span><span class="sxs-lookup"><span data-stu-id="78ba0-161">With all the time involved setting up your development environment, fixing that first bug could take days.</span></span>

> <span data-ttu-id="78ba0-162">或者，您可以使用 Dev Spaces 和 AKS。」</span><span class="sxs-lookup"><span data-stu-id="78ba0-162">Or you could use Dev Spaces and AKS."</span></span>

<span data-ttu-id="78ba0-163">處理 Azure Dev Spaces 的套裝程式含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="78ba0-163">The process for working with Azure Dev Spaces involves the following steps:</span></span>

1. <span data-ttu-id="78ba0-164">建立開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="78ba0-164">Create the dev space.</span></span>
2. <span data-ttu-id="78ba0-165">設定根開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="78ba0-165">Configure the root dev space.</span></span>
3. <span data-ttu-id="78ba0-166">設定子開發人員空間（適用于您自己的系統版本）。</span><span class="sxs-lookup"><span data-stu-id="78ba0-166">Configure a child dev space (for your own version of the system).</span></span>
4. <span data-ttu-id="78ba0-167">連接到開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="78ba0-167">Connect to the dev space.</span></span>

<span data-ttu-id="78ba0-168">所有這些步驟都可以使用 Azure CLI 和新`azds`的命令列工具來執行。</span><span class="sxs-lookup"><span data-stu-id="78ba0-168">All of these steps can be performed using the Azure CLI and new  `azds` command line tools.</span></span> <span data-ttu-id="78ba0-169">例如，若要為指定的 Kubernetes 叢集建立新的 Azure 開發人員空間，您可以使用如下所示的命令：</span><span class="sxs-lookup"><span data-stu-id="78ba0-169">For example, to create a new Azure Dev Space for a given Kubernetes cluster, you would use a command like this one:</span></span>

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

<span data-ttu-id="78ba0-170">接下來，您可以使用`azds prep`命令來產生必要的 Docker 和 Helm 圖表資產，以執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78ba0-170">Next, you can use the `azds prep` command to generate the necessary Docker and Helm chart assets for running the application.</span></span> <span data-ttu-id="78ba0-171">然後，您可以使用`azds up`在 AKS 中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="78ba0-171">Then you run your code in AKS using `azds up`.</span></span> <span data-ttu-id="78ba0-172">當您第一次執行此命令時，將會安裝 Helm 圖，並根據您的指示來建立和部署容器。</span><span class="sxs-lookup"><span data-stu-id="78ba0-172">The first time you run this command, the Helm chart will be installed, and the container(s) will be built and deployed according to your instructions.</span></span> <span data-ttu-id="78ba0-173">這可能會在第一次執行時需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="78ba0-173">This may take a few minutes the first time it's run.</span></span> <span data-ttu-id="78ba0-174">不過，在您進行變更之後，您可以使用`azds space select`連接到您自己的子開發人員空間，然後在隔離的子開發人員空間中部署和偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="78ba0-174">However, after you make changes, you can connect to your own child dev space using `azds space select` and then deploy and debug your updates in your isolated child dev space.</span></span> <span data-ttu-id="78ba0-175">當開發人員空間啟動並執行之後，您可以藉由重新發出`azds up`命令，或使用 Visual Studio 或 Visual Studio Code 中的內建工具，將更新傳送給它。</span><span class="sxs-lookup"><span data-stu-id="78ba0-175">Once you have your dev space up and running, you can send updates to it by re-issuing the `azds up` command or you can use built-in tooling in Visual Studio or Visual Studio Code.</span></span> <span data-ttu-id="78ba0-176">使用 VS Code，您可以使用命令選擇區來連接到您的開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="78ba0-176">With VS Code, you use the command palette to connect to your dev space.</span></span> <span data-ttu-id="78ba0-177">圖3-12 顯示如何使用 Visual Studio 中的 Azure Dev Spaces 啟動 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78ba0-177">Figure 3-12 shows how to launch your web application using Azure Dev Spaces in Visual Studio.</span></span>

<span data-ttu-id="78ba0-178">![連接到 Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**圖 3-12**中的 Azure Dev Spaces。</span><span class="sxs-lookup"><span data-stu-id="78ba0-178">![Connect to Azure Dev Spaces in Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**Figure 3-12**.</span></span> <span data-ttu-id="78ba0-179">連接到 Visual Studio 中的 Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="78ba0-179">Connect to Azure Dev Spaces in Visual Studio</span></span>

## <a name="references"></a><span data-ttu-id="78ba0-180">reference</span><span class="sxs-lookup"><span data-stu-id="78ba0-180">References</span></span>

- [<span data-ttu-id="78ba0-181">未進行的版本</span><span class="sxs-lookup"><span data-stu-id="78ba0-181">Canary Release</span></span>](https://martinfowler.com/bliki/CanaryRelease.html)
- [<span data-ttu-id="78ba0-182">使用 VS Code 的 Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="78ba0-182">Azure Dev Spaces with VS Code</span></span>](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [<span data-ttu-id="78ba0-183">使用 Visual Studio 的 Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="78ba0-183">Azure Dev Spaces with Visual Studio</span></span>](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)

>[!div class="step-by-step"]
><span data-ttu-id="78ba0-184">[上一頁](combine-containers-serverless-approaches.md)
>[下一頁](scale-containers-serverless.md)</span><span class="sxs-lookup"><span data-stu-id="78ba0-184">[Previous](combine-containers-serverless-approaches.md)
[Next](scale-containers-serverless.md)</span></span>
