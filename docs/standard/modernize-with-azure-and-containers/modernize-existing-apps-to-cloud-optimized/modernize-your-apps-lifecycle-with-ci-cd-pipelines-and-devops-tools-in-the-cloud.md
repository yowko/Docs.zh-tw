---
title: 在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |現代化您的應用程式生命週期 CI/CD 管線與雲端中的 DevOps 工具
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833962"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="77f1d-103">在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化</span><span class="sxs-lookup"><span data-stu-id="77f1d-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="77f1d-104">現今的企業需要速度很快即可具競爭力的市場中發揮創意。</span><span class="sxs-lookup"><span data-stu-id="77f1d-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="77f1d-105">交付高品質、 現代化應用程式需要 DevOps 工具和程序會實作這個持續的循環的創新的關鍵。</span><span class="sxs-lookup"><span data-stu-id="77f1d-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="77f1d-106">使用適當的 DevOps 工具，開發人員可以簡化持續部署，並更快速創新的應用程式傳遞給的使用者。</span><span class="sxs-lookup"><span data-stu-id="77f1d-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="77f1d-107">雖然持續整合和部署作法全都堅實的建立，容器的簡介會介紹新的考量，特別是當您正在使用多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="77f1d-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="77f1d-108">Azure 的 DevOps 服務支援持續整合和多容器應用程式部署到各種不同的環境，透過的官方 Azure DevOps 服務部署工作：</span><span class="sxs-lookup"><span data-stu-id="77f1d-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="77f1d-109">For Containers 中部署為 Azure Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="77f1d-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [<span data-ttu-id="77f1d-110">部署至 Azure Container Service-Kubernetes</span><span class="sxs-lookup"><span data-stu-id="77f1d-110">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="77f1d-111">但是您也可以部署到[Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)或 DC/OS 使用 Azure DevOps 服務指令碼為基礎的工作。</span><span class="sxs-lookup"><span data-stu-id="77f1d-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="77f1d-112">若要繼續加速部署靈活度，這些工具會提供絕佳的開發到測試-至-生產部署容器工作負載，使用您選擇的開發和 CI/CD 解決方案體驗。</span><span class="sxs-lookup"><span data-stu-id="77f1d-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="77f1d-113">圖 4 到 12 個顯示持續部署管線，以部署至 Azure Container Service 中 Kubernetes 叢集。</span><span class="sxs-lookup"><span data-stu-id="77f1d-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Azure 的 DevOps 服務持續部署管線，將部署到 Kubernetes 叢集](./media/image12.png)

> <span data-ttu-id="77f1d-115">**圖 4 到 12 個。**</span><span class="sxs-lookup"><span data-stu-id="77f1d-115">**Figure 4-12.**</span></span> <span data-ttu-id="77f1d-116">Azure 的 DevOps 服務持續部署管線，將部署到 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="77f1d-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="77f1d-117">[上一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
>[下一頁](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="77f1d-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
