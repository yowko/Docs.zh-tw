---
title: 使用 Microsoft 工具的 Docker 應用程式 devops 工作流程
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期，使用 Microsoft 工具的 devops 工作流程
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d313cb8ff6762eba6534ca20b214063315a456f0
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46561665"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>使用 Microsoft 工具的 Docker 應用程式 DevOps 工作流程

Microsoft Visual Studio、 Azure DevOps 服務、 Team Foundation Server 和 Application Insights 提供完整的生態系統開發和 IT 作業，可讓您的小組管理專案和快速建置、 測試及部署工具容器化應用程式。

使用 Visual Studio 和 Azure DevOps 服務在雲端中，以及 Team Foundation Server 在內部開發團隊可以有效率地建置、 測試和發行導向任何平台 （Windows 或 Linux） 的容器化應用程式。

Microsoft 工具可以自動執行容器化應用程式的特定實作的管線，Docker、.NET Core 或任何其他平台的組合 — 從全域組建和持續整合 (CI) 及測試與 Azure DevOps 服務或小組Foundation Server，來持續部署 (CD) Docker 環境 （開發、 預備、 生產），並傳送給開發小組透過 Application Insights 服務的分析資訊。 每個程式碼認可都可以啟始建置 (CI)，並將服務自動部署至特定容器化環境 (CD)。

開發人員和測試人員可以使用 Microsoft Azure 中的範本，以根據 Docker 輕鬆且快速地佈建類似生產環境的開發和測試環境。

根據商務複雜性和延展性需求，容器化應用程式開發的複雜度會穩定增加。 這個的不錯範例是根據微服務架構的應用程式。 若要在這類環境中成功，您的專案必須自動化整個生命週期：不僅建置和部署，也必須管理版本和遙測集合。 Azure DevOps 服務和 Azure 提供下列功能：

-   Azure DevOps Services/Team Foundation Server 原始程式碼管理 （根據 Git 或 Team Foundation 版本控制），敏捷式計劃 （Agile、 Scrum 和 CMMI 支援），CI、 發行管理和敏捷式軟體開發團隊的其他工具。

-   Azure DevOps Services/Team Foundation Server 包含功能強大且不斷成長的生態系統，與您輕鬆地可以建構 CI、 建置、 測試、 傳遞和發行管理管線的微服務的第一個和第三方擴充功能。

-   Azure DevOps 服務中您組建管線的一部分執行自動化的測試。

-   Azure 的 DevOps 服務可以加強 DevOps 生命週期傳遞至多個環境，不只是針對生產環境中，但也進行測試，包括 A / B 測試[canary 版本](https://martinfowler.com/bliki/CanaryRelease.html)，依此類推。

-   組織可以搭配使用 Azure Resource Manager 範本與他們已用來輕鬆執行的工具，以從 Azure Container Registry 中所儲存的私人映像以及與 Azure 元件 (Data、PaaS 等等) 的任何相依性來輕鬆地佈建 Docker 容器。


>[!div class="step-by-step"]
[上一頁](../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md)
[下一頁](docker-application-outer-loop-devops-workflow.md)
