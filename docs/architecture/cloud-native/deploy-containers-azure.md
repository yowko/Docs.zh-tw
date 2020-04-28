---
title: 在 Azure 中部署容器
description: 使用 Azure Container Registry、Azure Kubernetes Service 和 Azure Dev Spaces 在 Azure 中部署容器。
ms.date: 04/13/2020
ms.openlocfilehash: 6238460c6129583c34e6b328c38ed9042f32f3d6
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199556"
---
# <a name="deploying-containers-in-azure"></a><span data-ttu-id="b8088-103">在 Azure 中部署容器</span><span class="sxs-lookup"><span data-stu-id="b8088-103">Deploying containers in Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b8088-104">我們已討論過本章和第1章中的容器。</span><span class="sxs-lookup"><span data-stu-id="b8088-104">We've discussed containers in this chapter and in chapter 1.</span></span> <span data-ttu-id="b8088-105">我們已瞭解容器為雲端原生應用程式提供許多優點，包括可攜性。</span><span class="sxs-lookup"><span data-stu-id="b8088-105">We've seen that containers provide many benefits to cloud-native applications, including portability.</span></span> <span data-ttu-id="b8088-106">在 Azure 雲端中，您可以在預備和生產環境中部署相同的容器化服務。</span><span class="sxs-lookup"><span data-stu-id="b8088-106">In the Azure cloud, you can deploy the same containerized services across staging and production environments.</span></span> <span data-ttu-id="b8088-107">Azure 提供數個選項來裝載這些容器化的工作負載：</span><span class="sxs-lookup"><span data-stu-id="b8088-107">Azure provides several options for hosting these containerized workloads:</span></span>

- <span data-ttu-id="b8088-108">Azure Kubernetes Services (AKS)</span><span class="sxs-lookup"><span data-stu-id="b8088-108">Azure Kubernetes Services (AKS)</span></span>
- <span data-ttu-id="b8088-109">Azure 容器執行個體 (ACI)</span><span class="sxs-lookup"><span data-stu-id="b8088-109">Azure Container Instance (ACI)</span></span>
- <span data-ttu-id="b8088-110">適用于容器的 Azure Web Apps</span><span class="sxs-lookup"><span data-stu-id="b8088-110">Azure Web Apps for Containers</span></span>

## <a name="azure-container-registry"></a><span data-ttu-id="b8088-111">Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="b8088-111">Azure Container Registry</span></span>

<span data-ttu-id="b8088-112">容器化微服務時，您會先建立「映射」組建容器。</span><span class="sxs-lookup"><span data-stu-id="b8088-112">When containerizing a microservice, you first a build container "image."</span></span> <span data-ttu-id="b8088-113">影像是服務程式代碼、相依性和執行時間的二進位標記法。</span><span class="sxs-lookup"><span data-stu-id="b8088-113">The image is a binary representation of the service code, dependencies, and runtime.</span></span> <span data-ttu-id="b8088-114">雖然您可以使用 Docker API 中的`Docker Build`命令手動建立映射，但更好的方法是將它建立為自動化組建流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="b8088-114">While you can manually create an image using the `Docker Build` command from the Docker API, a better approach is to create it as part of an automated build process.</span></span>

<span data-ttu-id="b8088-115">建立之後，容器映射會儲存在容器登錄中。</span><span class="sxs-lookup"><span data-stu-id="b8088-115">Once created, container images are stored in container registries.</span></span> <span data-ttu-id="b8088-116">它們可讓您建立、儲存和管理容器映射。</span><span class="sxs-lookup"><span data-stu-id="b8088-116">They enable you to build, store, and manage container images.</span></span> <span data-ttu-id="b8088-117">有許多登錄可供使用，兩者都是公用和私用。</span><span class="sxs-lookup"><span data-stu-id="b8088-117">There are many registries available, both public and private.</span></span> <span data-ttu-id="b8088-118">Azure Container Registry （ACR）是 Azure 雲端中完全受控的 Container Registry 服務。</span><span class="sxs-lookup"><span data-stu-id="b8088-118">Azure Container Registry (ACR) is a fully managed container registry service in the Azure cloud.</span></span> <span data-ttu-id="b8088-119">它會將您的映射保存在 Azure 網路中，縮短將其部署至 Azure 容器主機的時間。</span><span class="sxs-lookup"><span data-stu-id="b8088-119">It persists your images inside the Azure network, reducing the time to deploy them to Azure container hosts.</span></span> <span data-ttu-id="b8088-120">您也可以使用其他 Azure 資源所使用的相同安全性和身分識別程式來保護它們。</span><span class="sxs-lookup"><span data-stu-id="b8088-120">You can also secure them using the same security and identity procedures that you use for other Azure resources.</span></span>

<span data-ttu-id="b8088-121">您可以使用[Azure 入口網站](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal)、 [Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli)或[PowerShell 工具](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell)來建立 Azure Container Registry。</span><span class="sxs-lookup"><span data-stu-id="b8088-121">You create an Azure Container Registry using the [Azure portal](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal), [Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli), or [PowerShell tools](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell).</span></span> <span data-ttu-id="b8088-122">在 Azure 中建立登錄非常簡單。</span><span class="sxs-lookup"><span data-stu-id="b8088-122">Creating a registry in Azure is simple.</span></span> <span data-ttu-id="b8088-123">它需要 Azure 訂用帳戶、資源群組和唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8088-123">It requires an Azure subscription, resource group, and a unique name.</span></span> <span data-ttu-id="b8088-124">圖3-11 顯示用來建立登錄的基本選項，其將裝載于`registryname.azurecr.io`。</span><span class="sxs-lookup"><span data-stu-id="b8088-124">Figure 3-11 shows the basic options for creating a registry, which will be hosted at `registryname.azurecr.io`.</span></span>

![建立容器登錄](./media/create-container-registry.png)

<span data-ttu-id="b8088-126">**圖 3-11**。</span><span class="sxs-lookup"><span data-stu-id="b8088-126">**Figure 3-11**.</span></span> <span data-ttu-id="b8088-127">建立容器登錄</span><span class="sxs-lookup"><span data-stu-id="b8088-127">Create container registry</span></span>

<span data-ttu-id="b8088-128">建立登錄之後，您必須先向它進行驗證，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="b8088-128">Once you've created the registry, you'll need to authenticate with it before you can use it.</span></span> <span data-ttu-id="b8088-129">一般來說，您會使用 Azure CLI 命令登入登錄：</span><span class="sxs-lookup"><span data-stu-id="b8088-129">Typically, you'll log into the registry using the Azure CLI command:</span></span>

```azurecli
az acr login --name *registryname*
```

<span data-ttu-id="b8088-130">驗證之後，您可以使用 docker 命令將容器映射推送至該檔案。</span><span class="sxs-lookup"><span data-stu-id="b8088-130">Once authenticated, you can use docker commands to push container images to it.</span></span> <span data-ttu-id="b8088-131">不過，您必須先使用 ACR 登入伺服器的完整名稱（URL）來標記映射，才能執行此動作。</span><span class="sxs-lookup"><span data-stu-id="b8088-131">Before you can do so, however, you must tag your image with the fully qualified name (URL) of your ACR login server.</span></span> <span data-ttu-id="b8088-132">它的格式會是*于: registryname*. azurecr.io。</span><span class="sxs-lookup"><span data-stu-id="b8088-132">It will have the format *registryname*.azurecr.io.</span></span>

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="b8088-133">標記影像之後，您可以使用`docker push`命令將映射推送至您的 ACR 實例。</span><span class="sxs-lookup"><span data-stu-id="b8088-133">After you've tagged the image, you use the `docker push` command to push the image to your ACR instance.</span></span>

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="b8088-134">將映射推送至登錄之後，使用下列命令從本機 Docker 環境中移除映射是個不錯的主意：</span><span class="sxs-lookup"><span data-stu-id="b8088-134">After you push an image to the registry, it's a good idea to remove the image from your local Docker environment, using this command:</span></span>

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="b8088-135">最佳做法是，開發人員不應將映射手動推送至容器登錄。</span><span class="sxs-lookup"><span data-stu-id="b8088-135">As a best practice, developers shouldn't manually push images to a container registry.</span></span> <span data-ttu-id="b8088-136">相反地，在 GitHub 或 Azure DevOps 這類工具中定義的組建管線，應負責處理此程式。</span><span class="sxs-lookup"><span data-stu-id="b8088-136">Instead, a build pipeline defined in a tool like GitHub or Azure DevOps should be responsible for this process.</span></span> <span data-ttu-id="b8088-137">在[雲端原生 DevOps 一章](devops.md)中深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="b8088-137">Learn more in the [Cloud-Native DevOps chapter](devops.md).</span></span>

## <a name="acr-tasks"></a><span data-ttu-id="b8088-138">ACR 工作</span><span class="sxs-lookup"><span data-stu-id="b8088-138">ACR Tasks</span></span>

<span data-ttu-id="b8088-139">[ACR 工作](https://docs.microsoft.com/azure/container-registry/container-registry-tasks-overview)是可從 Azure Container Registry 取得的一組功能。</span><span class="sxs-lookup"><span data-stu-id="b8088-139">[ACR Tasks](https://docs.microsoft.com/azure/container-registry/container-registry-tasks-overview) is a set of features available from the Azure Container Registry.</span></span> <span data-ttu-id="b8088-140">它會在 Azure 雲端中建立和管理容器映射，以擴充您的[內部迴圈開發週期](https://docs.microsoft.com/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/docker-apps-inner-loop-workflow)。</span><span class="sxs-lookup"><span data-stu-id="b8088-140">It extends your [inner-loop development cycle](https://docs.microsoft.com/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/docker-apps-inner-loop-workflow) by building and managing container images in the Azure cloud.</span></span> <span data-ttu-id="b8088-141">它們不會在`docker build`您`docker push`的開發電腦上叫用和本機，而是由雲端中的 ACR 工作自動處理。</span><span class="sxs-lookup"><span data-stu-id="b8088-141">Instead of invoking a `docker build` and `docker push` locally on your development machine, they're automatically handled by ACR Tasks in the cloud.</span></span>

<span data-ttu-id="b8088-142">下列 AZ CLI 命令會建立容器映射，並將其推送至 ACR：</span><span class="sxs-lookup"><span data-stu-id="b8088-142">The following AZ CLI command both builds a container image and pushes it to ACR:</span></span>

```azurecli
# create a container registry
az acr create --resource-group myResourceGroup --name myContainerRegistry008 --sku Basic

# build container image in ACR and push it into your container regsitry
az acr build --image sample/hello-world:v1  --registry myContainerRegistry008 --file Dockerfile .
```

<span data-ttu-id="b8088-143">您可以從先前的命令區塊看到，不需要在您的開發電腦上安裝 Docker Desktop。</span><span class="sxs-lookup"><span data-stu-id="b8088-143">As you can see from the previous command block, there's no need to install Docker Desktop on your development machine.</span></span> <span data-ttu-id="b8088-144">此外，您可以設定 ACR 工作觸發程式，以在原始程式碼和基底映射更新上重建容器映射。</span><span class="sxs-lookup"><span data-stu-id="b8088-144">Additionally, you can configure ACR Task triggers to rebuild containers images on both source code and base image updates.</span></span>

## <a name="azure-kubernetes-service"></a><span data-ttu-id="b8088-145">Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="b8088-145">Azure Kubernetes Service</span></span>

<span data-ttu-id="b8088-146">我們在本章中討論了 Azure Kubernetes Service （AKS）。</span><span class="sxs-lookup"><span data-stu-id="b8088-146">We discussed Azure Kubernetes Service (AKS) at length in this chapter.</span></span> <span data-ttu-id="b8088-147">我們已瞭解，它是管理容器化雲端原生應用程式的容器協調器。</span><span class="sxs-lookup"><span data-stu-id="b8088-147">We've seen that it's the de facto container orchestrator managing containerized cloud-native applications.</span></span>

<span data-ttu-id="b8088-148">將映射部署至登錄（例如 ACR）之後，您可以將 AKS 設定為自動提取並部署它。</span><span class="sxs-lookup"><span data-stu-id="b8088-148">Once you deploy an image to a registry, such as ACR, you can configure AKS to automatically pull and deploy it.</span></span> <span data-ttu-id="b8088-149">備妥 CI/CD 管線之後，您可能會設定未完成的[發行](https://martinfowler.com/bliki/CanaryRelease.html)策略，以將快速部署更新時所牽涉到的風險降到最低。</span><span class="sxs-lookup"><span data-stu-id="b8088-149">With a CI/CD pipeline in place, you might configure a  [canary release](https://martinfowler.com/bliki/CanaryRelease.html) strategy to minimize the risk involved when rapidly deploying updates.</span></span> <span data-ttu-id="b8088-150">新版本的應用程式一開始會在生產環境中設定，而不會路由傳送流量。</span><span class="sxs-lookup"><span data-stu-id="b8088-150">The new version of the app is initially configured in production with no traffic routed to it.</span></span> <span data-ttu-id="b8088-151">然後，系統會將少量的使用者路由傳送至新部署的版本。</span><span class="sxs-lookup"><span data-stu-id="b8088-151">Then, the system will route a small percentage of users to the newly deployed version.</span></span> <span data-ttu-id="b8088-152">隨著小組在新版本中獲得信心，它可以推出更多實例並淘汰舊的。</span><span class="sxs-lookup"><span data-stu-id="b8088-152">As the team gains confidence in the new version, it can roll out more instances and retire the old.</span></span> <span data-ttu-id="b8088-153">AKS 輕鬆支援這種部署樣式。</span><span class="sxs-lookup"><span data-stu-id="b8088-153">AKS easily supports this style of deployment.</span></span>

<span data-ttu-id="b8088-154">如同 Azure 中的大部分資源，您可以使用入口網站、命令列或自動化工具（例如 Helm 或 Terraform）來建立 Azure Kubernetes Service 叢集。</span><span class="sxs-lookup"><span data-stu-id="b8088-154">As with most resources in Azure, you can create an Azure Kubernetes Service cluster using the portal, command-line, or automation tools like Helm or Terraform.</span></span> <span data-ttu-id="b8088-155">若要開始使用新的叢集，您必須提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="b8088-155">To get started with a new cluster, you need to provide the following information:</span></span>

- <span data-ttu-id="b8088-156">Azure 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="b8088-156">Azure subscription</span></span>
- <span data-ttu-id="b8088-157">資源群組</span><span class="sxs-lookup"><span data-stu-id="b8088-157">Resource group</span></span>
- <span data-ttu-id="b8088-158">Kubernetes 叢集名稱</span><span class="sxs-lookup"><span data-stu-id="b8088-158">Kubernetes cluster name</span></span>
- <span data-ttu-id="b8088-159">區域</span><span class="sxs-lookup"><span data-stu-id="b8088-159">Region</span></span>
- <span data-ttu-id="b8088-160">Kubernetes 版本</span><span class="sxs-lookup"><span data-stu-id="b8088-160">Kubernetes version</span></span>
- <span data-ttu-id="b8088-161">DNS 名稱前置詞</span><span class="sxs-lookup"><span data-stu-id="b8088-161">DNS name prefix</span></span>
- <span data-ttu-id="b8088-162">節點大小</span><span class="sxs-lookup"><span data-stu-id="b8088-162">Node size</span></span>
- <span data-ttu-id="b8088-163">節點計數</span><span class="sxs-lookup"><span data-stu-id="b8088-163">Node count</span></span>

<span data-ttu-id="b8088-164">這種資訊就足以開始使用。</span><span class="sxs-lookup"><span data-stu-id="b8088-164">This information is sufficient to get started.</span></span> <span data-ttu-id="b8088-165">在 Azure 入口網站的建立過程中，您也可以為叢集的下列功能設定選項：</span><span class="sxs-lookup"><span data-stu-id="b8088-165">As part of the creation process in the Azure portal, you can also configure options for the following features of your cluster:</span></span>

- <span data-ttu-id="b8088-166">調整</span><span class="sxs-lookup"><span data-stu-id="b8088-166">Scale</span></span>
- <span data-ttu-id="b8088-167">驗證</span><span class="sxs-lookup"><span data-stu-id="b8088-167">Authentication</span></span>
- <span data-ttu-id="b8088-168">網路功能</span><span class="sxs-lookup"><span data-stu-id="b8088-168">Networking</span></span>
- <span data-ttu-id="b8088-169">監視</span><span class="sxs-lookup"><span data-stu-id="b8088-169">Monitoring</span></span>
- <span data-ttu-id="b8088-170">Tags</span><span class="sxs-lookup"><span data-stu-id="b8088-170">Tags</span></span>

<span data-ttu-id="b8088-171">本[快速入門會逐步引導您使用 Azure 入口網站來部署 AKS](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)叢集。</span><span class="sxs-lookup"><span data-stu-id="b8088-171">This [quickstart walks through deploying an AKS cluster using the Azure portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).</span></span>

## <a name="azure-dev-spaces"></a><span data-ttu-id="b8088-172">Azure 開發人員空間</span><span class="sxs-lookup"><span data-stu-id="b8088-172">Azure Dev Spaces</span></span>

<span data-ttu-id="b8088-173">雲端原生應用程式可能很快就會變得很大，而且需要大量計算資源才能執行。</span><span class="sxs-lookup"><span data-stu-id="b8088-173">Cloud-native applications can quickly grow large and complex, requiring significant compute resources to run.</span></span> <span data-ttu-id="b8088-174">在這些情況下，整個應用程式無法裝載于開發電腦（特別是膝上型電腦）上。</span><span class="sxs-lookup"><span data-stu-id="b8088-174">In these scenarios, the entire application can't be hosted on a development machine (especially a laptop).</span></span> <span data-ttu-id="b8088-175">Azure Dev Spaces 的設計目的是要使用 AKS 來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="b8088-175">Azure Dev Spaces is designed to address this problem using AKS.</span></span> <span data-ttu-id="b8088-176">它可讓開發人員使用其服務的本機版本，同時在 AKS 開發叢集中裝載應用程式的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="b8088-176">It enables developers to work with a local version of their services while hosting the rest of the application in an AKS development cluster.</span></span>

<span data-ttu-id="b8088-177">開發人員會在包含整個容器化應用程式的 AKS 叢集中共用執行中（開發）實例。</span><span class="sxs-lookup"><span data-stu-id="b8088-177">Developers share a running (development) instance in an AKS cluster that contains the entire containerized application.</span></span> <span data-ttu-id="b8088-178">但他們會在其電腦上使用個人空間設定，以在本機開發其服務。</span><span class="sxs-lookup"><span data-stu-id="b8088-178">But they use personal spaces set up on their machine to locally develop their services.</span></span> <span data-ttu-id="b8088-179">準備好時，他們會在 AKS 叢集中從端對端測試，而不會複寫相依性。</span><span class="sxs-lookup"><span data-stu-id="b8088-179">When ready, they test from end-to-end in the AKS cluster - without replicating dependencies.</span></span> <span data-ttu-id="b8088-180">Azure Dev Spaces 會將本機電腦的程式碼與 AKS 中的服務合併。</span><span class="sxs-lookup"><span data-stu-id="b8088-180">Azure Dev Spaces merges code from the local machine with services in AKS.</span></span> <span data-ttu-id="b8088-181">開發人員可以使用 Visual Studio 或 Visual Studio Code，直接在 Kubernetes 中快速反復查看和偵錯工具代碼。</span><span class="sxs-lookup"><span data-stu-id="b8088-181">Developers can rapidly iterate and debug code directly in Kubernetes using Visual Studio or Visual Studio Code.</span></span>

<span data-ttu-id="b8088-182">若要瞭解 Azure Dev Spaces 的值，請在 Microsoft Azure，讓我在容器的領導處 Gabe Monroy 分享此報價：</span><span class="sxs-lookup"><span data-stu-id="b8088-182">To understand the value of Azure Dev Spaces, let me share this quotation from Gabe Monroy, PM Lead of Containers at Microsoft Azure:</span></span>

> <span data-ttu-id="b8088-183">假設您是新的員工，嘗試修正由數十個元件組成的複雜微服務應用程式中的 bug，每一個都有自己的設定和支援服務。</span><span class="sxs-lookup"><span data-stu-id="b8088-183">Imagine you're a new employee trying to fix a bug in a complex microservices application consisting of dozens of components, each with their own configuration and backing services.</span></span> <span data-ttu-id="b8088-184">若要開始使用，您必須設定本機開發環境，讓它可以模擬生產，包括設定您的 IDE、建立工具鏈、容器化服務相依性、本機 Kubernetes 環境、支援服務的模擬等等。</span><span class="sxs-lookup"><span data-stu-id="b8088-184">To get started, you must configure your local development environment so that it can mimic production including setting up your IDE, building tool chain, containerized service dependencies, a local Kubernetes environment, mocks for backing services, and more.</span></span> <span data-ttu-id="b8088-185">只要設定您的開發環境，修正該第一個錯誤可能需要數天的時間。</span><span class="sxs-lookup"><span data-stu-id="b8088-185">With all the time involved setting up your development environment, fixing that first bug could take days.</span></span>
> <span data-ttu-id="b8088-186">或者，您可以使用 Dev Spaces 和 AKS。</span><span class="sxs-lookup"><span data-stu-id="b8088-186">Or you could use Dev Spaces and AKS.</span></span>

<span data-ttu-id="b8088-187">處理 Azure Dev Spaces 的套裝程式含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b8088-187">The process for working with Azure Dev Spaces involves the following steps:</span></span>

1. <span data-ttu-id="b8088-188">建立開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="b8088-188">Create the dev space.</span></span>
2. <span data-ttu-id="b8088-189">設定根開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="b8088-189">Configure the root dev space.</span></span>
3. <span data-ttu-id="b8088-190">設定子開發人員空間（適用于您自己的系統版本）。</span><span class="sxs-lookup"><span data-stu-id="b8088-190">Configure a child dev space (for your own version of the system).</span></span>
4. <span data-ttu-id="b8088-191">連接到開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="b8088-191">Connect to the dev space.</span></span>

<span data-ttu-id="b8088-192">所有這些步驟都可以使用 Azure CLI 和新`azds`的命令列工具來執行。</span><span class="sxs-lookup"><span data-stu-id="b8088-192">All of these steps can be performed using the Azure CLI and new  `azds` command-line tools.</span></span> <span data-ttu-id="b8088-193">例如，若要為指定的 Kubernetes 叢集建立新的 Azure 開發人員空間，您可以使用如下所示的命令：</span><span class="sxs-lookup"><span data-stu-id="b8088-193">For example, to create a new Azure Dev Space for a given Kubernetes cluster, you would use a command like this one:</span></span>

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

<span data-ttu-id="b8088-194">接下來，您可以使用`azds prep`命令來產生必要的 Docker 和 Helm 圖表資產，以執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8088-194">Next, you can use the `azds prep` command to generate the necessary Docker and Helm chart assets for running the application.</span></span> <span data-ttu-id="b8088-195">然後，您可以使用`azds up`在 AKS 中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="b8088-195">Then you run your code in AKS using `azds up`.</span></span> <span data-ttu-id="b8088-196">第一次執行此命令時，將會安裝 Helm 圖表。</span><span class="sxs-lookup"><span data-stu-id="b8088-196">The first time you run this command, the Helm chart will be installed.</span></span> <span data-ttu-id="b8088-197">系統會根據您的指示來建立和部署容器。</span><span class="sxs-lookup"><span data-stu-id="b8088-197">The containers will be built and deployed according to your instructions.</span></span> <span data-ttu-id="b8088-198">這項工作可能會在第一次執行時需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="b8088-198">This task may take a few minutes the first time it's run.</span></span> <span data-ttu-id="b8088-199">不過，在您進行變更之後，您可以使用`azds space select`連接到您自己的子開發人員空間，然後在隔離的子開發人員空間中部署和偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b8088-199">However, after you make changes, you can connect to your own child dev space using `azds space select` and then deploy and debug your updates in your isolated child dev space.</span></span> <span data-ttu-id="b8088-200">開發人員空間啟動並執行之後，您可以藉由重新發出`azds up`命令將更新傳送給它，或者您可以在 Visual Studio 或 Visual Studio Code 中使用內建工具。</span><span class="sxs-lookup"><span data-stu-id="b8088-200">Once you have your dev space up and running, you can send updates to it by reissuing the `azds up` command or you can use built-in tooling in Visual Studio or Visual Studio Code.</span></span> <span data-ttu-id="b8088-201">使用 VS Code，您可以使用命令選擇區來連接到您的開發人員空間。</span><span class="sxs-lookup"><span data-stu-id="b8088-201">With VS Code, you use the command palette to connect to your dev space.</span></span> <span data-ttu-id="b8088-202">圖3-12 顯示如何使用 Visual Studio 中的 Azure Dev Spaces 啟動 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8088-202">Figure 3-12 shows how to launch your web application using Azure Dev Spaces in Visual Studio.</span></span>

<span data-ttu-id="b8088-203">![連接到 Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**圖 3-12**中的 Azure Dev Spaces。</span><span class="sxs-lookup"><span data-stu-id="b8088-203">![Connect to Azure Dev Spaces in Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**Figure 3-12**.</span></span> <span data-ttu-id="b8088-204">連接到 Visual Studio 中的 Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="b8088-204">Connect to Azure Dev Spaces in Visual Studio</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b8088-205">[上一頁](combine-containers-serverless-approaches.md)
>[下一頁](scale-containers-serverless.md)</span><span class="sxs-lookup"><span data-stu-id="b8088-205">[Previous](combine-containers-serverless-approaches.md)
[Next](scale-containers-serverless.md)</span></span>
