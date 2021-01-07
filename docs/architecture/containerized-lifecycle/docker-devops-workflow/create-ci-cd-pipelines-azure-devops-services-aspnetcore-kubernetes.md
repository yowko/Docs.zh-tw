---
title: 在 Azure DevOps Services 中為容器上的 .NET 應用程式建立 CI/CD 管線，並部署至 Kubernetes 叢集
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.date: 01/06/2021
ms.openlocfilehash: ef994f132716547ee402237016ee71013528d779
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970482"
---
# <a name="create-cicd-pipelines-in-azure-devops-services-for-a-net-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="89088-103">在 Azure DevOps Services 中為容器上的 .NET 應用程式建立 CI/CD 管線，並部署至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="89088-103">Create CI/CD pipelines in Azure DevOps Services for a .NET application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="89088-104">在圖 5-12 中，您可以看到端對端 DevOps 案例，涵蓋程式碼管理、程式碼編譯、Docker 映像建置、Docker 映像推送至 Docker 登錄，最後部署至 Azure 中的 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="89088-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Workflow：在開發電腦上啟動。](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="89088-107">**圖 5-12**。</span><span class="sxs-lookup"><span data-stu-id="89088-107">**Figure 5-12**.</span></span> <span data-ttu-id="89088-108">CI/CD 案例建立 Docker 映像並部署至 Azure 中的 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="89088-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="89088-109">請務必注意這兩個管線，建置/CI 和發行/CD，這兩者是透過 Docker 登錄 (如 Docker Hub 或 Azure Container Registry) 連線。</span><span class="sxs-lookup"><span data-stu-id="89088-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="89088-110">相較於不具有 Docker 的傳統 CI/CD 程序，Docker 登錄是其中一項主要差異。</span><span class="sxs-lookup"><span data-stu-id="89088-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="89088-111">如圖 5-13 所示，第一個階段是建置/CI 管線。</span><span class="sxs-lookup"><span data-stu-id="89088-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="89088-112">在 Azure DevOps Services 中，您可以建立建置/CI 管線，這些管線將編譯程式碼、建立 Docker 映像，並將其推送至 Docker Hub 或 Azure Container Registry 等Docker 登錄。</span><span class="sxs-lookup"><span data-stu-id="89088-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Azure DevOps 中建置程序工作定義的瀏覽器檢視。](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="89088-114">**圖 5-13**。</span><span class="sxs-lookup"><span data-stu-id="89088-114">**Figure 5-13**.</span></span> <span data-ttu-id="89088-115">Azure DevOps 中的建置/CI 管線會建置 Docker 映像並將映像推送至 Docker 登錄</span><span class="sxs-lookup"><span data-stu-id="89088-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="89088-116">第二個階段是建立部署/發行管線。</span><span class="sxs-lookup"><span data-stu-id="89088-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="89088-117">在 Azure DevOps Services 中，您可以使用 Azure DevOps Services 的 Kubernetes 工作，輕鬆建立以 Kubernetes 叢集為目標的部署管線，如圖 5-14 所示。</span><span class="sxs-lookup"><span data-stu-id="89088-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Azure DevOps 中 [部署至 Kubernetes] 工作定義的瀏覽器檢視。](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="89088-119">**圖 5-14**。</span><span class="sxs-lookup"><span data-stu-id="89088-119">**Figure 5-14**.</span></span> <span data-ttu-id="89088-120">部署 Azure DevOps Services 中的發行/CD 管線至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="89088-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> <span data-ttu-id="89088-121">[!Walkthrough] 將 eShopModernized 部署至 Kubernetes：</span><span class="sxs-lookup"><span data-stu-id="89088-121">[!Walkthrough] Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="89088-122">如需部署至 Kubernetes 之 Azure DevOps CI/CD 管線的詳細逐步解說，請參閱此貼文： </span><span class="sxs-lookup"><span data-stu-id="89088-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="89088-123">[上一個](docker-application-outer-loop-devops-workflow.md) 
>[下一步](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="89088-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
