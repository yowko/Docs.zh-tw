---
title: 使用 Microsoft 工具的 Docker 應用程式 devops 工作流程
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期，使用 Microsoft 工具的 devops 工作流程
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d313cb8ff6762eba6534ca20b214063315a456f0
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46517252"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a><span data-ttu-id="133c2-103">使用 Microsoft 工具的 Docker 應用程式 DevOps 工作流程</span><span class="sxs-lookup"><span data-stu-id="133c2-103">Docker application DevOps workflow with Microsoft tools</span></span>

<span data-ttu-id="133c2-104">Microsoft Visual Studio、 Azure DevOps 服務、 Team Foundation Server 和 Application Insights 提供完整的生態系統開發和 IT 作業，可讓您的小組管理專案和快速建置、 測試及部署工具容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="133c2-104">Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server, and Application Insights provide a comprehensive ecosystem for development and IT operations that give your team the tools to manage projects and rapidly build, test, and deploy containerized applications.</span></span>

<span data-ttu-id="133c2-105">使用 Visual Studio 和 Azure DevOps 服務在雲端中，以及 Team Foundation Server 在內部開發團隊可以有效率地建置、 測試和發行導向任何平台 （Windows 或 Linux） 的容器化應用程式。</span><span class="sxs-lookup"><span data-stu-id="133c2-105">With Visual Studio and Azure DevOps Services in the cloud, along with Team Foundation Server on-premises, development teams can productively build, test, and release containerized applications directed toward any platform (Windows or Linux).</span></span>

<span data-ttu-id="133c2-106">Microsoft 工具可以自動執行容器化應用程式的特定實作的管線，Docker、.NET Core 或任何其他平台的組合 — 從全域組建和持續整合 (CI) 及測試與 Azure DevOps 服務或小組Foundation Server，來持續部署 (CD) Docker 環境 （開發、 預備、 生產），並傳送給開發小組透過 Application Insights 服務的分析資訊。</span><span class="sxs-lookup"><span data-stu-id="133c2-106">Microsoft tools can automate the pipeline for specific implementations of containerized applications—Docker, .NET Core, or any combination with other platforms—from global builds and Continuous Integration (CI) and tests with Azure DevOps Services or Team Foundation Server, to Continuous Deployment (CD) to Docker environments (Development, Staging, Production), and to transmit analytics information about the services to the development team through Application Insights.</span></span> <span data-ttu-id="133c2-107">每個程式碼認可都可以啟始建置 (CI)，並將服務自動部署至特定容器化環境 (CD)。</span><span class="sxs-lookup"><span data-stu-id="133c2-107">Every code commit can initiate a build (CI) and automatically deploy the services to specific containerized environments (CD).</span></span>

<span data-ttu-id="133c2-108">開發人員和測試人員可以使用 Microsoft Azure 中的範本，以根據 Docker 輕鬆且快速地佈建類似生產環境的開發和測試環境。</span><span class="sxs-lookup"><span data-stu-id="133c2-108">Developers and testers can easily and quickly provision production-like development and test environments based on Docker by using templates in Microsoft Azure.</span></span>

<span data-ttu-id="133c2-109">根據商務複雜性和延展性需求，容器化應用程式開發的複雜度會穩定增加。</span><span class="sxs-lookup"><span data-stu-id="133c2-109">The complexity of containerized application development increases steadily depending on the business complexity and scalability needs.</span></span> <span data-ttu-id="133c2-110">這個的不錯範例是根據微服務架構的應用程式。</span><span class="sxs-lookup"><span data-stu-id="133c2-110">A good example of this are applications based on microservices architectures.</span></span> <span data-ttu-id="133c2-111">若要在這類環境中成功，您的專案必須自動化整個生命週期：不僅建置和部署，也必須管理版本和遙測集合。</span><span class="sxs-lookup"><span data-stu-id="133c2-111">To succeed in such an environment, your project must automate the entire life cycle—not only the build and deployment, but it also must manage versions along with the collection of telemetry.</span></span> <span data-ttu-id="133c2-112">Azure DevOps 服務和 Azure 提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="133c2-112">Azure DevOps Services and Azure offer the following capabilities:</span></span>

-   <span data-ttu-id="133c2-113">Azure DevOps Services/Team Foundation Server 原始程式碼管理 （根據 Git 或 Team Foundation 版本控制），敏捷式計劃 （Agile、 Scrum 和 CMMI 支援），CI、 發行管理和敏捷式軟體開發團隊的其他工具。</span><span class="sxs-lookup"><span data-stu-id="133c2-113">Azure DevOps Services/Team Foundation Server source code management (based on Git or Team Foundation Version Control), Agile planning (Agile, Scrum, and CMMI are supported), CI, release management, and other tools for Agile teams.</span></span>

-   <span data-ttu-id="133c2-114">Azure DevOps Services/Team Foundation Server 包含功能強大且不斷成長的生態系統，與您輕鬆地可以建構 CI、 建置、 測試、 傳遞和發行管理管線的微服務的第一個和第三方擴充功能。</span><span class="sxs-lookup"><span data-stu-id="133c2-114">Azure DevOps Services/Team Foundation Server include a powerful and growing ecosystem of first- and third-party extensions with which you easily can construct a CI, build, test, delivery, and release management pipeline for microservices.</span></span>

-   <span data-ttu-id="133c2-115">Azure DevOps 服務中您組建管線的一部分執行自動化的測試。</span><span class="sxs-lookup"><span data-stu-id="133c2-115">Run automated tests as part of your build pipeline in Azure DevOps Services.</span></span>

-   <span data-ttu-id="133c2-116">Azure 的 DevOps 服務可以加強 DevOps 生命週期傳遞至多個環境，不只是針對生產環境中，但也進行測試，包括 A / B 測試[canary 版本](https://martinfowler.com/bliki/CanaryRelease.html)，依此類推。</span><span class="sxs-lookup"><span data-stu-id="133c2-116">Azure DevOps Services can tighten the DevOps life cycle with delivery to multiple environments, not just for production environments, but also for testing, including A/B experimentation, [canary releases](https://martinfowler.com/bliki/CanaryRelease.html), and so on.</span></span>

-   <span data-ttu-id="133c2-117">組織可以搭配使用 Azure Resource Manager 範本與他們已用來輕鬆執行的工具，以從 Azure Container Registry 中所儲存的私人映像以及與 Azure 元件 (Data、PaaS 等等) 的任何相依性來輕鬆地佈建 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="133c2-117">Organizations easily can provision Docker containers from private images stored in Azure Container Registry along with any dependency on Azure components (Data, PaaS, etc.) using Azure Resource Manager templates with tools with which they are already comfortable working.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="133c2-118">[上一頁](../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md)
[下一頁](docker-application-outer-loop-devops-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="133c2-118">[Previous](../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md)
[Next](docker-application-outer-loop-devops-workflow.md)</span></span>
