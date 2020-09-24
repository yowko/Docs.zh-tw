---
title: 其他容器部署選項
description: 使用 Azure 的其他容器部署選項
ms.date: 05/13/2020
ms.openlocfilehash: 2eac822b74af636e0ab0ed24b58eb7139526f4a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163618"
---
# <a name="other-container-deployment-options"></a><span data-ttu-id="a0736-103">其他容器部署選項</span><span class="sxs-lookup"><span data-stu-id="a0736-103">Other container deployment options</span></span>

<span data-ttu-id="a0736-104">除了 Azure Kubernetes Service (AKS) ，您也可以將容器部署至容器和 Azure 容器實例的 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="a0736-104">Aside from Azure Kubernetes Service (AKS), you can also deploy containers to Azure App Service for Containers and Azure Container Instances.</span></span>

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a><span data-ttu-id="a0736-105">部署到容器 App Service 有什麼意義？</span><span class="sxs-lookup"><span data-stu-id="a0736-105">When does it make sense to deploy to App Service for Containers?</span></span>

<span data-ttu-id="a0736-106">不需要協調流程的簡單實際執行應用程式很適合用於容器 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="a0736-106">Simple production applications that don't require orchestration are well suited to Azure App Service for Containers.</span></span>

## <a name="how-to-deploy-to-app-service-for-containers"></a><span data-ttu-id="a0736-107">如何部署至適用于容器的 App Service</span><span class="sxs-lookup"><span data-stu-id="a0736-107">How to deploy to App Service for Containers</span></span>

<span data-ttu-id="a0736-108">若要部署至 [容器的 Azure App Service](https://azure.microsoft.com/services/app-service/containers/)，您需要 AZURE CONTAINER REGISTRY (ACR) 實例和認證才能存取。</span><span class="sxs-lookup"><span data-stu-id="a0736-108">To deploy to [Azure App Service for Containers](https://azure.microsoft.com/services/app-service/containers/), you'll need an Azure Container Registry (ACR) instance and credentials to access it.</span></span> <span data-ttu-id="a0736-109">將您的容器映射推送至 ACR 存放庫，讓它可以提取到您的 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="a0736-109">Push your container image to the ACR repository so it can pulled into your Azure App Service.</span></span> <span data-ttu-id="a0736-110">完成之後，您可以設定應用程式進行持續部署。</span><span class="sxs-lookup"><span data-stu-id="a0736-110">Once complete, you can configure the app for Continuous Deployment.</span></span> <span data-ttu-id="a0736-111">這樣做會在 ACR 中的映射變更時自動部署更新。</span><span class="sxs-lookup"><span data-stu-id="a0736-111">Doing so will automatically deploy updates whenever the image changes in ACR.</span></span>

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a><span data-ttu-id="a0736-112">部署至 Azure 容器實例的時機為何？</span><span class="sxs-lookup"><span data-stu-id="a0736-112">When does it make sense to deploy to Azure Container Instances?</span></span>

<span data-ttu-id="a0736-113">[Azure 容器實例 (ACI) ](https://azure.microsoft.com/services/container-instances/) 可讓您在受控、無伺服器的雲端環境中執行 Docker 容器，而不需要設定虛擬機器或叢集。</span><span class="sxs-lookup"><span data-stu-id="a0736-113">[Azure Container Instances (ACI)](https://azure.microsoft.com/services/container-instances/) enables you to run Docker containers in a managed, serverless cloud environment, without having to set up virtual machines or clusters.</span></span> <span data-ttu-id="a0736-114">這是可在隔離的容器中執行的短期工作負載的絕佳解決方案。</span><span class="sxs-lookup"><span data-stu-id="a0736-114">It's a great solution for short-running workloads that can run in an isolated container.</span></span> <span data-ttu-id="a0736-115">請考慮 ACI 以取得簡單的服務、測試案例、工作自動化和組建作業。</span><span class="sxs-lookup"><span data-stu-id="a0736-115">Consider ACI for simple services, testing scenarios, task automation, and build jobs.</span></span> <span data-ttu-id="a0736-116">ACI 會啟動容器實例、執行工作，然後將它向下旋轉。</span><span class="sxs-lookup"><span data-stu-id="a0736-116">ACI spins-up a container instance, performs the task, and then spins it down.</span></span>

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a><span data-ttu-id="a0736-117">如何將應用程式部署至 Azure 容器實例</span><span class="sxs-lookup"><span data-stu-id="a0736-117">How to deploy an app to Azure Container Instances</span></span>

<span data-ttu-id="a0736-118">若要 [ (ACI) 部署至 Azure 容器實例 ](/azure/container-instances/)，您需要 AZURE CONTAINER REGISTRY (ACR) 和認證來進行存取。</span><span class="sxs-lookup"><span data-stu-id="a0736-118">To deploy to [Azure Container Instances (ACI)](/azure/container-instances/), you need an Azure Container Registry (ACR) and credentials for accessing it.</span></span> <span data-ttu-id="a0736-119">當您將容器映射推送至存放庫之後，就可以將它提取至 ACI。</span><span class="sxs-lookup"><span data-stu-id="a0736-119">Once you push your container image to the repository, it's available to pull into ACI.</span></span> <span data-ttu-id="a0736-120">您可以使用 Azure 入口網站或命令列介面來處理 ACI。</span><span class="sxs-lookup"><span data-stu-id="a0736-120">You can work with ACI using the Azure portal or command-line interface.</span></span> <span data-ttu-id="a0736-121">ACR 提供與 ACI 的緊密整合。</span><span class="sxs-lookup"><span data-stu-id="a0736-121">ACR provides tight integration with ACI.</span></span> <span data-ttu-id="a0736-122">圖3-14 顯示如何將個別容器映射推送至 ACR。</span><span class="sxs-lookup"><span data-stu-id="a0736-122">Figure 3-14 shows how to push an individual container image to ACR.</span></span>

![Azure Container Registry 執行實例](./media/acr-runinstance-contextmenu.png)

<span data-ttu-id="a0736-124">**圖 3-14**。</span><span class="sxs-lookup"><span data-stu-id="a0736-124">**Figure 3-14**.</span></span> <span data-ttu-id="a0736-125">Azure Container Registry 執行實例</span><span class="sxs-lookup"><span data-stu-id="a0736-125">Azure Container Registry Run Instance</span></span>

<span data-ttu-id="a0736-126">在 ACI 中建立實例可以快速完成。</span><span class="sxs-lookup"><span data-stu-id="a0736-126">Creating an instance in ACI can be done quickly.</span></span> <span data-ttu-id="a0736-127">指定映射登錄、Azure 資源群組資訊、要配置的記憶體數量，以及要接聽的埠。</span><span class="sxs-lookup"><span data-stu-id="a0736-127">Specify the image registry, Azure resource group information, the amount of memory to allocate, and the port on which to listen.</span></span> <span data-ttu-id="a0736-128">本 [快速入門說明如何使用 Azure 入口網站將容器實例部署至 ACI](/azure/container-instances/container-instances-quickstart-portal)。</span><span class="sxs-lookup"><span data-stu-id="a0736-128">This [quickstart shows how to deploy a container instance to ACI using the Azure portal](/azure/container-instances/container-instances-quickstart-portal).</span></span>

<span data-ttu-id="a0736-129">部署完成後，請尋找新部署的容器 IP 位址，並透過您指定的埠與其通訊。</span><span class="sxs-lookup"><span data-stu-id="a0736-129">Once the deployment completes, find the newly deployed container's IP address and communicate with it over the port you specified.</span></span>

<span data-ttu-id="a0736-130">Azure 容器實例提供在 Azure 中執行簡單容器工作負載的最快速方式。</span><span class="sxs-lookup"><span data-stu-id="a0736-130">Azure Container Instances offers the fastest way to run simple container workloads in Azure.</span></span> <span data-ttu-id="a0736-131">您不需要設定 app service、orchestrator 或虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="a0736-131">You don't need to configure an app service, orchestrator, or virtual machine.</span></span> <span data-ttu-id="a0736-132">對於需要完整容器協調流程、服務探索、自動調整或協調升級的案例，我們建議 Azure Kubernetes Service (AKS) 。</span><span class="sxs-lookup"><span data-stu-id="a0736-132">For scenarios where you require full container orchestration, service discovery, automatic scaling, or coordinated upgrades, we recommend Azure Kubernetes Service (AKS).</span></span>

## <a name="references"></a><span data-ttu-id="a0736-133">參考資料</span><span class="sxs-lookup"><span data-stu-id="a0736-133">References</span></span>

- [<span data-ttu-id="a0736-134">什麼是 Kubernetes？</span><span class="sxs-lookup"><span data-stu-id="a0736-134">What is Kubernetes?</span></span>](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [<span data-ttu-id="a0736-135">使用 Minikube 安裝 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a0736-135">Installing Kubernetes with Minikube</span></span>](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [<span data-ttu-id="a0736-136">MiniKube 與 Docker Desktop</span><span class="sxs-lookup"><span data-stu-id="a0736-136">MiniKube vs Docker Desktop</span></span>](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [<span data-ttu-id="a0736-137">Visual Studio Tools for Docker</span><span class="sxs-lookup"><span data-stu-id="a0736-137">Visual Studio Tools for Docker</span></span>](/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)
- [<span data-ttu-id="a0736-138">瞭解無伺服器冷啟動</span><span class="sxs-lookup"><span data-stu-id="a0736-138">Understanding serverless cold start</span></span>](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [<span data-ttu-id="a0736-139">預先準備就緒 Azure Functions 實例</span><span class="sxs-lookup"><span data-stu-id="a0736-139">Pre-warmed Azure Functions instances</span></span>](/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [<span data-ttu-id="a0736-140">在使用自訂映像的 Linux 上建立函式</span><span class="sxs-lookup"><span data-stu-id="a0736-140">Create a function on Linux using a custom image</span></span>](/azure/azure-functions/functions-create-function-linux-custom-image)
- [<span data-ttu-id="a0736-141">在 Docker 容器中執行 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="a0736-141">Run Azure Functions in a Docker Container</span></span>](https://markheath.net/post/azure-functions-docker)
- [<span data-ttu-id="a0736-142">在使用自訂映像的 Linux 上建立函式</span><span class="sxs-lookup"><span data-stu-id="a0736-142">Create a function on Linux using a custom image</span></span>](/azure/azure-functions/functions-create-function-linux-custom-image)
- [<span data-ttu-id="a0736-143">具有 Kubernetes 事件驅動自動調整的 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="a0736-143">Azure Functions with Kubernetes Event Driven Autoscaling</span></span>](/azure/azure-functions/functions-kubernetes-keda)
- [<span data-ttu-id="a0736-144">未的版本</span><span class="sxs-lookup"><span data-stu-id="a0736-144">Canary Release</span></span>](https://martinfowler.com/bliki/CanaryRelease.html)
- [<span data-ttu-id="a0736-145">使用 VS Code Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="a0736-145">Azure Dev Spaces with VS Code</span></span>](/azure/dev-spaces/quickstart-netcore)
- [<span data-ttu-id="a0736-146">使用 Visual Studio Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="a0736-146">Azure Dev Spaces with Visual Studio</span></span>](/azure/dev-spaces/quickstart-netcore-visualstudio)
- [<span data-ttu-id="a0736-147">AKS 多個節點集區</span><span class="sxs-lookup"><span data-stu-id="a0736-147">AKS Multiple Node Pools</span></span>](/azure/aks/use-multiple-node-pools)
- [<span data-ttu-id="a0736-148">AKS 叢集自動調整程式</span><span class="sxs-lookup"><span data-stu-id="a0736-148">AKS Cluster Autoscaler</span></span>](/azure/aks/cluster-autoscaler)
- [<span data-ttu-id="a0736-149">教學課程：在 AKS 中調整應用程式</span><span class="sxs-lookup"><span data-stu-id="a0736-149">Tutorial: Scale applications in AKS</span></span>](/azure/aks/tutorial-kubernetes-scale)
- [<span data-ttu-id="a0736-150">Azure Functions 的級別和裝載</span><span class="sxs-lookup"><span data-stu-id="a0736-150">Azure Functions scale and hosting</span></span>](/azure/azure-functions/functions-scale)
- [<span data-ttu-id="a0736-151">Azure 容器實例檔</span><span class="sxs-lookup"><span data-stu-id="a0736-151">Azure Container Instances Docs</span></span>](/azure/container-instances/)
- [<span data-ttu-id="a0736-152">從 ACR 部署容器實例</span><span class="sxs-lookup"><span data-stu-id="a0736-152">Deploy Container Instance from ACR</span></span>](/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
><span data-ttu-id="a0736-153">[上一個](scale-containers-serverless.md) 
>[下一步](communication-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="a0736-153">[Previous](scale-containers-serverless.md)
[Next](communication-patterns.md)</span></span>
