---
title: 使用 Microsoft 工具的 Docker 應用程式 devops 工作流程
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期，使用 Microsoft 工具的 devops 工作流程
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b4a88725de78f59c62aac1bd33764db6b2e0887e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a><span data-ttu-id="a2b05-103">使用 Microsoft 工具的 Docker 應用程式 DevOps 工作流程</span><span class="sxs-lookup"><span data-stu-id="a2b05-103">Docker application DevOps workflow with Microsoft tools</span></span>

<span data-ttu-id="a2b05-104">Microsoft Visual Studio、Visual Studio Team Services、Team Foundation Server 和 Application Insights 提供完整的生態系統進行開發和 IT 作業，可讓您的小組管理專案以及快速建置、測試和部署容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="a2b05-104">Microsoft Visual Studio, Visual Studio Team Services, Team Foundation Server, and Application Insights provide a comprehensive ecosystem for development and IT operations that give your team the tools to manage projects and rapidly build, test, and deploy containerized applications.</span></span>

<span data-ttu-id="a2b05-105">在雲端中使用 Visual Studio 和 Visual Studio Team Services，以及在內部部署環境中使用 Team Foundation Server，開發小組就可以有效率地建置、測試和發行導向任何平台 (Windows 或 Linux) 的容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="a2b05-105">With Visual Studio and Visual Studio Team Services in the cloud, along with Team Foundation Server on-premises, development teams can productively build, test, and release containerized applications directed toward any platform (Windows or Linux).</span></span>

<span data-ttu-id="a2b05-106">Microsoft 工具可以自動化特定容器化應用程式實作的管線 (Docker、.NET Core 或與其他平台的任意組合)，範圍從全域組建和持續整合 (CI) 並使用 Visual Studio Team Services 或 Team Foundation Server 的測試，到持續部署 (CD) 到 Docker 環境 (開發、準備、生產)，以及透過 Application Insights 將服務的分析資訊傳輸至開發小組。</span><span class="sxs-lookup"><span data-stu-id="a2b05-106">Microsoft tools can automate the pipeline for specific implementations of containerized applications—Docker, .NET Core, or any combination with other platforms—from global builds and Continuous Integration (CI) and tests with Visual Studio Team Services or Team Foundation Server, to Continuous Deployment (CD) to Docker environments (Development, Staging, Production), and to transmit analytics information about the services to the development team through Application Insights.</span></span> <span data-ttu-id="a2b05-107">每個程式碼認可都可以啟始建置 (CI)，並將服務自動部署至特定容器化環境 (CD)。</span><span class="sxs-lookup"><span data-stu-id="a2b05-107">Every code commit can initiate a build (CI) and automatically deploy the services to specific containerized environments (CD).</span></span>

<span data-ttu-id="a2b05-108">開發人員和測試人員可以使用 Microsoft Azure 中的範本，以根據 Docker 輕鬆且快速地佈建類似生產環境的開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="a2b05-108">Developers and testers can easily and quickly provision production-like development and test environments based on Docker by using templates in Microsoft Azure.</span></span>

<span data-ttu-id="a2b05-109">根據商務複雜性和延展性需求，容器化應用程式開發的複雜度會穩定增加。</span><span class="sxs-lookup"><span data-stu-id="a2b05-109">The complexity of containerized application development increases steadily depending on the business complexity and scalability needs.</span></span> <span data-ttu-id="a2b05-110">這個的不錯範例是根據微服務架構的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a2b05-110">A good example of this are applications based on microservices architectures.</span></span> <span data-ttu-id="a2b05-111">若要在這類環境中成功，您的專案必須自動化整個生命週期：不僅建置和部署，也必須管理版本和遙測集合。</span><span class="sxs-lookup"><span data-stu-id="a2b05-111">To succeed in such an environment, your project must automate the entire life cycle—not only the build and deployment, but it also must manage versions along with the collection of telemetry.</span></span> <span data-ttu-id="a2b05-112">Visual Studio Team Services 和 Azure 提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="a2b05-112">Visual Studio Team Services and Azure offer the following capabilities:</span></span>

-   <span data-ttu-id="a2b05-113">Visual Studio Team Services/Team Foundation Server 原始程式碼管理 (根據 Git 或 Team Foundation 版本控制)、Agile 規劃 (支援 Agile、Scrum 和 CMMI)、CI、發行管理，以及 Agile 小組的其他工具。</span><span class="sxs-lookup"><span data-stu-id="a2b05-113">Visual Studio Team Services/Team Foundation Server source code management (based on Git or Team Foundation Version Control), Agile planning (Agile, Scrum, and CMMI are supported), CI, release management, and other tools for Agile teams.</span></span>

-   <span data-ttu-id="a2b05-114">Visual Studio Team Services/Team Foundation Server 包含功能強大且不斷成長的生態系統，而您可以使用其第一方和第三方延伸模組輕鬆地建構微服務的 CI、建置、測試、傳遞和發行管理管線。</span><span class="sxs-lookup"><span data-stu-id="a2b05-114">Visual Studio Team Services/Team Foundation Server include a powerful and growing ecosystem of first- and third-party extensions with which you easily can construct a CI, build, test, delivery, and release management pipeline for microservices.</span></span>

-   <span data-ttu-id="a2b05-115">在 Visual Studio Team Services 中，於組建管線期間執行自動化測試。</span><span class="sxs-lookup"><span data-stu-id="a2b05-115">Run automated tests as part of your build pipeline in Visual Studio Team Services.</span></span>

-   <span data-ttu-id="a2b05-116">Visual Studio Team Services 可以利用傳遞至多個環境來加強 DevOps 生命週期，不只是傳遞至生產環境，也傳遞至測試環境 (包含 A/B 實驗、[anary 發行](https://martinfowler.com/bliki/CanaryRelease.html)等等)。</span><span class="sxs-lookup"><span data-stu-id="a2b05-116">Visual Studio Team Services can tighten the DevOps life cycle with delivery to multiple environments, not just for production environments, but also for testing, including A/B experimentation, [canary releases](https://martinfowler.com/bliki/CanaryRelease.html), and so on.</span></span>

-   <span data-ttu-id="a2b05-117">組織可以搭配使用 Azure Resource Manager 範本與他們已用來輕鬆執行的工具，以從 Azure Container Registry 中所儲存的私人映像以及與 Azure 元件 (Data、PaaS 等等) 的任何相依性來輕鬆地佈建 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="a2b05-117">Organizations easily can provision Docker containers from private images stored in Azure Container Registry along with any dependency on Azure components (Data, PaaS, etc.) using Azure Resource Manager templates with tools with which they are already comfortable working.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a2b05-118">[上一個] (../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [下一個] (docker-application-outer-loop-devops-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a2b05-118">[Previous] (../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [Next] (docker-application-outer-loop-devops-workflow.md)</span></span>
