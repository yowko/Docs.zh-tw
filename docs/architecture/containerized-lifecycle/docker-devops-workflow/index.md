---
title: 使用 Microsoft 工具的 Docker 應用程式 DevOps 工作流程
description: 使用 Microsoft 工具之 Microsoft 平台及工具 DevOps 工作流程的容器化 Docker 應用程式生命週期
ms.date: 01/06/2021
ms.openlocfilehash: 7f2d380dec046804772ea7d13e764ab6f3224c12
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970150"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a><span data-ttu-id="b7de3-103">使用 Microsoft 工具的 Docker 應用程式 DevOps 工作流程</span><span class="sxs-lookup"><span data-stu-id="b7de3-103">Docker application DevOps workflow with Microsoft tools</span></span>

<span data-ttu-id="b7de3-104">*Microsoft Visual Studio、Azure DevOps Services、Team Foundation Server 和 Azure 監視器提供完整的開發和 IT 作業生態系統，可讓您的小組管理專案以及快速建置、測試和部署容器化應用程式。*</span><span class="sxs-lookup"><span data-stu-id="b7de3-104">*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server, and Azure Monitor provide a comprehensive ecosystem for development and IT operations that give your team the tools to manage projects and rapidly build, test, and deploy containerized applications.*</span></span>

<span data-ttu-id="b7de3-105">在雲端中使用 Visual Studio 和 Azure DevOps Services，以及在內部部署環境中使用 Team Foundation Server，開發小組就可以有效率地建置、測試和發行以 Windows 或 Linux 為目標的容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7de3-105">With Visual Studio and Azure DevOps Services in the cloud, along with Team Foundation Server on-premises, development teams can productively build, test, and release containerized applications that target either Windows or Linux.</span></span>

<span data-ttu-id="b7de3-106">Microsoft 工具可以將容器化應用程式的特定實施（Docker、.NET 或任何與其他平臺的組合）自動化，包括通用群組建和持續整合 (CI) 和 Azure DevOps Services 或 Team Foundation Server 的測試，持續部署 (CD) 至 Docker 環境 (開發、預備、生產) ，以及透過 Azure 監視器將服務的相關分析資訊傳送給開發小組。</span><span class="sxs-lookup"><span data-stu-id="b7de3-106">Microsoft tools can automate the pipeline for specific implementations of containerized applications—Docker, .NET, or any combination with other platforms—from global builds and Continuous Integration (CI) and tests with Azure DevOps Services or Team Foundation Server, to Continuous Deployment (CD) to Docker environments (Development, Staging, Production), and to transmit analytics information about the services to the development team through Azure Monitor.</span></span> <span data-ttu-id="b7de3-107">每個程式碼認可都可以啟始建置 (CI)，並將服務自動部署至特定容器化環境 (CD)。</span><span class="sxs-lookup"><span data-stu-id="b7de3-107">Every code commit can initiate a build (CI) and automatically deploy the services to specific containerized environments (CD).</span></span>

<span data-ttu-id="b7de3-108">開發人員和測試人員可以使用 Microsoft Azure 中的範本，以根據 Docker 輕鬆且快速地佈建類似生產環境的開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="b7de3-108">Developers and testers can easily and quickly provision production-like development and test environments based on Docker by using templates in Microsoft Azure.</span></span>

<span data-ttu-id="b7de3-109">根據商務複雜性和延展性需求，容器化應用程式開發的複雜度會穩定增加。</span><span class="sxs-lookup"><span data-stu-id="b7de3-109">The complexity of containerized application development increases steadily depending on the business complexity and scalability needs.</span></span> <span data-ttu-id="b7de3-110">這種複雜度之良好範例為根據微服務架構的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7de3-110">A good example of this complexity are applications based on microservices architectures.</span></span> <span data-ttu-id="b7de3-111">若要在這類環境中成功，您的專案必須自動化整個生命週期：不僅建置和部署，也必須管理版本和遙測集合。</span><span class="sxs-lookup"><span data-stu-id="b7de3-111">To succeed in such an environment, your project must automate the entire life cycle—not only the build and deployment, but it also must manage versions along with the collection of telemetry.</span></span> <span data-ttu-id="b7de3-112">Azure DevOps Services 和 Azure 提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="b7de3-112">Azure DevOps Services and Azure offer the following capabilities:</span></span>

- <span data-ttu-id="b7de3-113">Azure DevOps Services/Team Foundation Server 原始程式碼管理 (根據 Git 或 Team Foundation 版本控制)、Agile 規劃 (支援 Agile、Scrum 和 CMMI)、CI、發行管理，以及 Agile 小組的其他工具。</span><span class="sxs-lookup"><span data-stu-id="b7de3-113">Azure DevOps Services/Team Foundation Server source code management (based on Git or Team Foundation Version Control), Agile planning (Agile, Scrum, and CMMI are supported), CI, release management, and other tools for Agile teams.</span></span>

- <span data-ttu-id="b7de3-114">Azure DevOps Services 和 Team Foundation Server 包含一和協力廠商擴充功能的強大且不斷成長的生態系統，可讓您輕鬆地為微服務建立 CI、組建、測試、傳遞和發行管理管線。</span><span class="sxs-lookup"><span data-stu-id="b7de3-114">Azure DevOps Services and Team Foundation Server include a powerful and growing ecosystem of first and third-party extensions with which you easily can construct a CI, build, test, delivery, and release management pipeline for microservices.</span></span>

- <span data-ttu-id="b7de3-115">在 Azure DevOps Services 中，於組建管線期間執行自動化測試。</span><span class="sxs-lookup"><span data-stu-id="b7de3-115">Run automated tests as part of your build pipeline in Azure DevOps Services.</span></span>

- <span data-ttu-id="b7de3-116">Azure DevOps Services 可以利用傳遞至多個環境來加強 DevOps 生命週期，不只是傳遞至生產環境，也傳遞至測試環境 (包含 A/B 實驗、[Canary 發行](https://martinfowler.com/bliki/CanaryRelease.html) 等)。</span><span class="sxs-lookup"><span data-stu-id="b7de3-116">Azure DevOps Services can tighten the DevOps life cycle with delivery to multiple environments, not just for production environments, but also for testing, including A/B experimentation, [canary releases](https://martinfowler.com/bliki/CanaryRelease.html), and so on.</span></span>

- <span data-ttu-id="b7de3-117">組織可以將 Azure Resource Manager 範本與他們已熟悉的工具搭配使用，從儲存在 Azure Container Registry 中私人映像和與 Azure 元件 (Data、PaaS 等) 的任何相依性來輕鬆地佈建 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="b7de3-117">Organizations easily can provision Docker containers from private images stored in Azure Container Registry along with any dependency on Azure components (Data, PaaS, etc.) using Azure Resource Manager templates with tools they're already comfortable with.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b7de3-118">[上一個](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md) 
>[下一步](docker-application-outer-loop-devops-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b7de3-118">[Previous](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
[Next](docker-application-outer-loop-devops-workflow.md)</span></span>
