---
title: 在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式的生命週期現代化
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578161"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="ea035-103">在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化</span><span class="sxs-lookup"><span data-stu-id="ea035-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="ea035-104">現今的企業需要以快速的步調創新, 以在 marketplace 中獲得競爭優勢。</span><span class="sxs-lookup"><span data-stu-id="ea035-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="ea035-105">提供高品質的現代化應用程式需要 DevOps 的工具和流程, 這是實現這項不斷創新週期的關鍵。</span><span class="sxs-lookup"><span data-stu-id="ea035-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="ea035-106">開發人員可以使用適當的 DevOps 工具, 簡化持續部署, 並更快速地將創新的應用程式交給使用者。</span><span class="sxs-lookup"><span data-stu-id="ea035-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="ea035-107">雖然已妥善建立持續整合和部署作法, 但容器的引進會引進新的考慮, 特別是當您使用多容器應用程式時。</span><span class="sxs-lookup"><span data-stu-id="ea035-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="ea035-108">Azure DevOps Services 透過官方 Azure DevOps Services 部署工作, 支援多容器應用程式的持續整合和部署到各種環境:</span><span class="sxs-lookup"><span data-stu-id="ea035-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="ea035-109">部署至 Azure 用於容器的 Web App</span><span class="sxs-lookup"><span data-stu-id="ea035-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [<span data-ttu-id="ea035-110">部署至 Azure Container Service – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="ea035-110">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="ea035-111">但是您也可以使用 Azure DevOps Services 腳本工作, 部署到[Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)或 DC/OS。</span><span class="sxs-lookup"><span data-stu-id="ea035-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="ea035-112">為了繼續加速部署的靈活性, 這些工具為容器工作負載提供了絕佳的開發與測試對生產部署體驗, 並可選擇開發和 CI/CD 解決方案。</span><span class="sxs-lookup"><span data-stu-id="ea035-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="ea035-113">圖4-12 顯示會在 Azure Container Service 中部署至 Kubernetes 叢集的持續部署管線。</span><span class="sxs-lookup"><span data-stu-id="ea035-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Azure DevOps Services 持續部署管線, 部署至 Kubernetes 叢集](./media/image12.png)

> <span data-ttu-id="ea035-115">**圖4-12。**</span><span class="sxs-lookup"><span data-stu-id="ea035-115">**Figure 4-12.**</span></span> <span data-ttu-id="ea035-116">Azure DevOps Services 持續部署管線, 部署至 Kubernetes 叢集</span><span class="sxs-lookup"><span data-stu-id="ea035-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ea035-117">[上一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
>[下一頁](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="ea035-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
