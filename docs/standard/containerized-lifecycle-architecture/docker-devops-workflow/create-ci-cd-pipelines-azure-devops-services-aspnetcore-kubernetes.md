---
title: Docker 應用程式之外部迴圈 DevOps 工作流程中的步驟
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e11c9ec61ea7d5131595f01ce76b5bb810bb70c0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063305"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="64743-103">在 Azure DevOps Services 中為容器上的 .NET Core 2.0 應用程式建立 CI/CD 管線並部署到 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="64743-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="64743-104">圖 5-12，您可以看到的端對端 DevOps 案例，涵蓋的程式碼管理程式碼編譯、 建置 Docker 映像、 Docker 映像推送到 Docker 登錄及最後部署至 Azure 中的 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="64743-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![工作流程：在開發電腦中啟動。](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="64743-107">**圖 5-12**。</span><span class="sxs-lookup"><span data-stu-id="64743-107">**Figure 5-12**.</span></span> <span data-ttu-id="64743-108">建立 Docker 映像和部署到 Azure 中的 Kubernetes 叢集的 CI/CD 案例</span><span class="sxs-lookup"><span data-stu-id="64743-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="64743-109">請務必反白顯示兩個管線、 組建/CI 和發行/CD，透過 Docker 登錄 （例如 Docker Hub 或 Azure Container Registry） 連線。</span><span class="sxs-lookup"><span data-stu-id="64743-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="64743-110">Docker 登錄是其中一個主要的差異，相較於傳統的 CI/CD 程序，不使用 Docker。</span><span class="sxs-lookup"><span data-stu-id="64743-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="64743-111">如所示的圖 5-13，第一個階段是組建/CI 管線。</span><span class="sxs-lookup"><span data-stu-id="64743-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="64743-112">Azure DevOps 服務中，您可以建立組建/CI 管線，將會編譯程式碼、 建立 Docker 映像，並將其推送到 Docker Hub 或 Azure Container Registry 的 Docker 登錄。</span><span class="sxs-lookup"><span data-stu-id="64743-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Azure DevOps，建置程序工作定義的瀏覽器檢視。](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="64743-114">**圖 5-13**。</span><span class="sxs-lookup"><span data-stu-id="64743-114">**Figure 5-13**.</span></span> <span data-ttu-id="64743-115">Azure DevOps 建置 Docker 映像，並將映像推送到 Docker 登錄中的組建/CI 管線</span><span class="sxs-lookup"><span data-stu-id="64743-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="64743-116">第二個階段是建立的部署/發行管線。</span><span class="sxs-lookup"><span data-stu-id="64743-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="64743-117">在 Azure DevOps 服務中，您可以輕鬆建立使用 Azure DevOps 服務，Kubernetes 工作目標的 Kubernetes 叢集，如所示的圖 5-14 部署管線。</span><span class="sxs-lookup"><span data-stu-id="64743-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Azure DevOps 的瀏覽器檢視部署至 Kubernetes 工作定義。](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="64743-119">**圖 5-14**。</span><span class="sxs-lookup"><span data-stu-id="64743-119">**Figure 5-14**.</span></span> <span data-ttu-id="64743-120">Azure DevOps 服務部署到 Kubernetes 叢集的發行/CD 管線</span><span class="sxs-lookup"><span data-stu-id="64743-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [!逐步解說]<span data-ttu-id="64743-121"> eShopModernized 部署至 Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="64743-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="64743-122">Azure DevOps 的 CI/CD 管線的詳細逐步解說將部署至 Kubernetes，請參閱這篇文章: \\</span><span class="sxs-lookup"><span data-stu-id="64743-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: \\</span></span>
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="64743-123">[上一頁](docker-application-outer-loop-devops-workflow.md)
>[下一頁](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="64743-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
