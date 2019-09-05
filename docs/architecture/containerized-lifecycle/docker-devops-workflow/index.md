---
title: 使用 Microsoft 工具的 Docker 應用程式 DevOps 工作流程
description: 使用 Microsoft 工具之 Microsoft 平台及工具 DevOps 工作流程的容器化 Docker 應用程式生命週期
ms.date: 02/15/2019
ms.openlocfilehash: 6b138301a7e6794ce0a7b15957684b3b73e9f89f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295739"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a><span data-ttu-id="7bc4c-103">使用 Microsoft 工具的 Docker 應用程式 DevOps 工作流程</span><span class="sxs-lookup"><span data-stu-id="7bc4c-103">Docker application DevOps workflow with Microsoft tools</span></span>

<span data-ttu-id="7bc4c-104">*Microsoft Visual Studio、Azure DevOps Services、Team Foundation Server 和 Azure 監視器提供完整的開發和 IT 作業生態系統，可讓您的小組管理專案以及快速建置、測試和部署容器化應用程式。*</span><span class="sxs-lookup"><span data-stu-id="7bc4c-104">*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server, and Azure Monitor provide a comprehensive ecosystem for development and IT operations that give your team the tools to manage projects and rapidly build, test, and deploy containerized applications.*</span></span>

<span data-ttu-id="7bc4c-105">在雲端中使用 Visual Studio 和 Azure DevOps Services，以及在內部部署環境中使用 Team Foundation Server，開發小組就可以有效率地建置、測試和發行以 Windows 或 Linux 為目標的容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-105">With Visual Studio and Azure DevOps Services in the cloud, along with Team Foundation Server on-premises, development teams can productively build, test, and release containerized applications that target either Windows or Linux.</span></span>

<span data-ttu-id="7bc4c-106">Microsoft 工具可以自動化特定容器化應用程式實作的管線 (Docker、.NET Core 或與其他平台的任意組合)，範圍從全域組建和持續整合 (CI) 並使用 Azure DevOps Services 或 Team Foundation Server 的測試，到持續部署 (CD) 至 Docker 環境 (開發、預備、生產)，以及透過 Azure 監視器將服務的分析資訊傳輸至開發小組。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-106">Microsoft tools can automate the pipeline for specific implementations of containerized applications—Docker, .NET Core, or any combination with other platforms—from global builds and Continuous Integration (CI) and tests with Azure DevOps Services or Team Foundation Server, to Continuous Deployment (CD) to Docker environments (Development, Staging, Production), and to transmit analytics information about the services to the development team through Azure Monitor.</span></span> <span data-ttu-id="7bc4c-107">每個程式碼認可都可以啟始建置 (CI)，並將服務自動部署至特定容器化環境 (CD)。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-107">Every code commit can initiate a build (CI) and automatically deploy the services to specific containerized environments (CD).</span></span>

<span data-ttu-id="7bc4c-108">開發人員和測試人員可以使用 Microsoft Azure 中的範本，以根據 Docker 輕鬆且快速地佈建類似生產環境的開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-108">Developers and testers can easily and quickly provision production-like development and test environments based on Docker by using templates in Microsoft Azure.</span></span>

<span data-ttu-id="7bc4c-109">根據商務複雜性和延展性需求，容器化應用程式開發的複雜度會穩定增加。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-109">The complexity of containerized application development increases steadily depending on the business complexity and scalability needs.</span></span> <span data-ttu-id="7bc4c-110">這種複雜度之良好範例為根據微服務架構的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-110">A good example of this complexity are applications based on microservices architectures.</span></span> <span data-ttu-id="7bc4c-111">若要在這類環境中成功，您的專案必須自動化整個生命週期：不僅是建置和部署，還必須管理版本及遙測集合。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-111">To succeed in such an environment, your project must automate the entire life cycle—not only the build and deployment, but it also must manage versions along with the collection of telemetry.</span></span> <span data-ttu-id="7bc4c-112">Azure DevOps Services 和 Azure 提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="7bc4c-112">Azure DevOps Services and Azure offer the following capabilities:</span></span>

- <span data-ttu-id="7bc4c-113">Azure DevOps Services/Team Foundation Server 原始程式碼管理 (根據 Git 或 Team Foundation 版本控制)、Agile 規劃 (支援 Agile、Scrum 和 CMMI)、CI、發行管理，以及 Agile 小組的其他工具。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-113">Azure DevOps Services/Team Foundation Server source code management (based on Git or Team Foundation Version Control), Agile planning (Agile, Scrum, and CMMI are supported), CI, release management, and other tools for Agile teams.</span></span>

- <span data-ttu-id="7bc4c-114">Azure DevOps Services 和 Team Foundation Server 包含功能強大且不斷成長的第一方和第三方延伸模組生態系統，而您可以使用它輕鬆地建構微服務的 CI、建置、測試、傳遞和發行微服務的管理管線。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-114">Azure DevOps Services and Team Foundation Server include a powerful and growing ecosystem of first- and third-party extensions with which you easily can construct a CI, build, test, delivery, and release management pipeline for microservices.</span></span>

- <span data-ttu-id="7bc4c-115">在 Azure DevOps Services 中，於組建管線期間執行自動化測試。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-115">Run automated tests as part of your build pipeline in Azure DevOps Services.</span></span>

- <span data-ttu-id="7bc4c-116">Azure DevOps Services 可以利用傳遞至多個環境來加強 DevOps 生命週期，不只是傳遞至生產環境，也傳遞至測試環境 (包含 A/B 實驗、[Canary 發行](https://martinfowler.com/bliki/CanaryRelease.html) 等)。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-116">Azure DevOps Services can tighten the DevOps life cycle with delivery to multiple environments, not just for production environments, but also for testing, including A/B experimentation, [canary releases](https://martinfowler.com/bliki/CanaryRelease.html), and so on.</span></span>

- <span data-ttu-id="7bc4c-117">組織可以將 Azure Resource Manager 範本與他們已熟悉的工具搭配使用，從儲存在 Azure Container Registry 中私人映像和與 Azure 元件 (Data、PaaS 等) 的任何相依性來輕鬆地佈建 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="7bc4c-117">Organizations easily can provision Docker containers from private images stored in Azure Container Registry along with any dependency on Azure components (Data, PaaS, etc.) using Azure Resource Manager templates with tools they're already comfortable with.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7bc4c-118">[上一頁](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[下一頁](docker-application-outer-loop-devops-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7bc4c-118">[Previous](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
[Next](docker-application-outer-loop-devops-workflow.md)</span></span>
