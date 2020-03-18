---
title: 在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |借助雲中的 CI/CD 管道和 DevOps 工具實現應用生命週期的現代化
ms.date: 04/30/2018
ms.openlocfilehash: 17a78c108bfc61471128a34191ec7a5d7cc28289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503844"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="3e9c4-103">在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化</span><span class="sxs-lookup"><span data-stu-id="3e9c4-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="3e9c4-104">當今的企業需要快速創新，才能在市場上具有競爭力。</span><span class="sxs-lookup"><span data-stu-id="3e9c4-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="3e9c4-105">交付高品質、現代的應用程式需要 DevOps 工具和流程，這對於實現這種持續的創新週期至關重要。</span><span class="sxs-lookup"><span data-stu-id="3e9c4-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="3e9c4-106">借助正確的 DevOps 工具，開發人員可以簡化持續部署，並更快地將創新應用程式送到使用者手中。</span><span class="sxs-lookup"><span data-stu-id="3e9c4-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="3e9c4-107">儘管持續集成和部署實踐已經確立，但引入容器會帶來新的注意事項，尤其是在使用多容器應用程式時。</span><span class="sxs-lookup"><span data-stu-id="3e9c4-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="3e9c4-108">Azure DevOps 服務支援通過正式的 Azure DevOps 服務部署任務持續集成多容器應用程式並部署到各種環境：</span><span class="sxs-lookup"><span data-stu-id="3e9c4-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="3e9c4-109">部署到容器的 Azure Web 應用</span><span class="sxs-lookup"><span data-stu-id="3e9c4-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="3e9c4-110">部署到 Azure 庫伯奈斯服務</span><span class="sxs-lookup"><span data-stu-id="3e9c4-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="3e9c4-111">但是，您也可以通過使用基於 Azure DevOps 服務腳本的任務部署到[Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html)或 DC/OS。</span><span class="sxs-lookup"><span data-stu-id="3e9c4-111">But you also can deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="3e9c4-112">為了繼續提高部署敏捷性，這些工具為容器工作負載提供了出色的從開發到測試到生產的部署體驗，並可以選擇開發和 CI/CD 解決方案。</span><span class="sxs-lookup"><span data-stu-id="3e9c4-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="3e9c4-113">圖 4-12 顯示了一個連續部署管道，該管道部署到 Azure 容器服務中的 Kubernetes 群集。</span><span class="sxs-lookup"><span data-stu-id="3e9c4-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![部署到庫伯奈斯群集的 Azure DevOps 服務的螢幕截圖。](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="3e9c4-115">**圖 4-12。**</span><span class="sxs-lookup"><span data-stu-id="3e9c4-115">**Figure 4-12.**</span></span> <span data-ttu-id="3e9c4-116">Azure DevOps 服務連續部署管道，部署到庫伯內斯群集</span><span class="sxs-lookup"><span data-stu-id="3e9c4-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3e9c4-117">[上一個](modernize-your-apps-with-monitoring-and-telemetry.md)
>[下一個](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="3e9c4-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
