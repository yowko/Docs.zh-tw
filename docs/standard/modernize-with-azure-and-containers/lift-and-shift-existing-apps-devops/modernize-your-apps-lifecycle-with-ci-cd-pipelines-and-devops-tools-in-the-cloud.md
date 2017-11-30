---
title: "現代化雲端中的 DevOps 工具 CI/CD 管線與您的應用程式生命週期"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |現代化雲端中的 DevOps 工具 CI/CD 管線與您的應用程式生命週期"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 2799f203cec2b01d2c9ff1a60ece801dc5939104
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="d8fd4-103">現代化雲端中的 DevOps 工具 CI/CD 管線與您的應用程式生命週期</span><span class="sxs-lookup"><span data-stu-id="d8fd4-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="d8fd4-104">現今的企業需要 marketplace 處於競爭腳步創新。</span><span class="sxs-lookup"><span data-stu-id="d8fd4-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="d8fd4-105">現代應用程式提供高品質，需要 DevOps 工具和實作的創新此常數週期不可或缺的程序。</span><span class="sxs-lookup"><span data-stu-id="d8fd4-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="d8fd4-106">使用適當的 DevOps 工具，開發人員可以簡化連續部署，並更快取得的使用者在未授權者手的創新應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8fd4-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="d8fd4-107">雖然全都堅實的連續整合及部署的作法，容器的簡介會引進新的考量，特別是當您正在使用多個容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8fd4-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="d8fd4-108">Visual Studio Team Services 支援連續整合及多容器應用程式部署到各種不同的環境，完成的官方 Team Services 部署工作：</span><span class="sxs-lookup"><span data-stu-id="d8fd4-108">Visual Studio Team Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Team Services deployment tasks:</span></span>

-   <span data-ttu-id="d8fd4-109">[將部署至獨立 Docker 主機 VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) （Linux 或 Windows Server 2016 或更新版本）</span><span class="sxs-lookup"><span data-stu-id="d8fd4-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="d8fd4-110">部署 Service fabric</span><span class="sxs-lookup"><span data-stu-id="d8fd4-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="d8fd4-111">部署至 Azure 的容器服務 – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d8fd4-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="d8fd4-112">但您也可以部署到[Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)或 DC/OS 使用 Team Services 指令碼為基礎的工作。</span><span class="sxs-lookup"><span data-stu-id="d8fd4-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Team Services script-based tasks.</span></span>

<span data-ttu-id="d8fd4-113">若要繼續促進部署靈活度，這些工具會提供絕佳的開發人員若要為測試-至生產部署發生時針對容器的工作負載，透過選擇的開發和 CI/CD 解決方案。</span><span class="sxs-lookup"><span data-stu-id="d8fd4-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="d8fd4-114">圖 4-12 顯示部署至 Kubernetes 叢集 Azure 容器服務中的連續部署管線。</span><span class="sxs-lookup"><span data-stu-id="d8fd4-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Visual Studio Team Services 連續部署管線，將部署至 Kubernetes 叢集](./media/image12.png)

> <span data-ttu-id="d8fd4-116">**圖 4-12。**</span><span class="sxs-lookup"><span data-stu-id="d8fd4-116">**Figure 4-12.**</span></span> <span data-ttu-id="d8fd4-117">Visual Studio Team Services 連續部署管線，將部署至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="d8fd4-117">Visual Studio Team Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="d8fd4-118">[上一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
[下一頁](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="d8fd4-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
