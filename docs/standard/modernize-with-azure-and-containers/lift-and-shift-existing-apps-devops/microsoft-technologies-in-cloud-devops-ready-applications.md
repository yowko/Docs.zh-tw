---
title: 雲端 devops 已備妥應用程式中的 Microsoft 技術
description: 容器化的.NET 應用程式的.NET Microservices 架構 |DevOps 雲端應用程式中的 Microsoft 技術
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d3a0572b833a4ca3be1db3b3b531a76ca34fe4ab
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-technologies-in-cloud-devops-ready-applications"></a>雲端 devops 已備妥應用程式中的 Microsoft 技術

下列清單說明工具、 技術和解決方案，都會識別為 DevOps 雲端應用程式需求。 您可以根據自己的優先，選擇性地或逐漸，採用 DevOps 雲端應用程式。

-   **雲端基礎結構**： 提供運算平台、 作業系統、 網路和儲存體基礎結構。 在此層級位於 Microsoft Azure。

-   **執行階段**： 這一層提供執行應用程式的環境。 如果您使用的容器，此圖層通常會根據[Docker 引擎](https://docs.docker.com/engine/)、 Linux 主機上或在 Windows 主機上執行。 ([Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)支援從 Windows Server 2016 開始。 Windows 容器是在 Windows 執行的現有.NET Framework 應用程式的最佳選擇）。

-   **管理雲端**： 當您選擇的受管理的雲端選項時，您可以避免成本以及複雜性的管理和支援的基礎的基礎結構，Vm OS 修補程式，以及網路組態。 如果您選擇使用 IaaS 移轉，您必須負責所有這些工作，以及相關聯的成本。 在受管理的雲端選項中，您只能管理的應用程式及您開發的服務。 雲端服務提供者通常用來管理所有其他項目。 在 Azure 中的受管理的雲端服務的範例包括[Azure SQL Database](https://azure.microsoft.com/services/sql-database)， [Azure Redis 快取](https://azure.microsoft.com/services/cache/)， [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)， [Azure 儲存體](https://azure.microsoft.com/services/storage/)，[Azure 資料庫的 MySQL](https://azure.microsoft.com/services/mysql/)， [Azure PostgreSQL 資料庫](https://azure.microsoft.com/services/postgresql/)， [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)，及管理計算服務，例如[VM 規模調整設定](https://azure.microsoft.com/services/virtual-machine-scale-sets/)， [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)， [Azure App Service](https://azure.microsoft.com/services/app-service/)，和[Azure 容器服務](https://azure.microsoft.com/services/container-service/)。

-   **應用程式開發**： 當您建置在容器中執行的應用程式時，您可以選擇從許多語言。 在本指南中，我們將重點放在[.NET](https://www.microsoft.com/net)，但您可以開發容器架構的應用程式使用其他語言，例如 Node.js、 Python、 Spring/Java 或 GoLang。

-   **監視、 遙測記錄和稽核**： 監視和稽核應用程式和雲端中執行的容器的能力是重要的任何 DevOps 雲端應用程式。 [Azure 的 Application Insights](https://azure.microsoft.com/services/application-insights/)和[Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) DevOps 雲端應用程式提供監視和稽核主要 Microsoft 工具。

-   **佈建**： 自動化工具可協助您準備基礎結構，以及應用程式部署至多個環境 （生產、 測試、 預備）。 您可以使用 Chef 和 Puppet 等工具來管理應用程式的組態和環境。 此圖層也可以使用來實作更簡單且更直接的方法。 比方說，您可以直接使用部署工具，Azure 命令列介面 (Azure CLI)，然後使用連續的部署和 release management 中的管線[Visual Studio Team Services](https://www.visualstudio.com/team-services/)。

-   **應用程式生命週期**: [Visual Studio Team Services](https://www.visualstudio.com/team-services/)和其他工具，如 Jenkins，則會建置的 automation 伺服程式可協助您實作 CI/CD 管線，包括版本管理。

接下來的這一章，以及相關的逐步解說，章節特別著重於執行階段層 （Windows 容器） 的相關詳細資料。 本指南說明您可以將 Windows Server 2016 （含） 以後版本上的 Windows 容器的 Vm 部署的方式。 其中也涵蓋更多進階的 orchestrator 圖層，例如 Azure Service Fabric、 Kubernetes，以及 Azure 容器服務。 設定 orchestrator 圖層是種現有.NET Framework (windows) 應用程式做為 DevOps 雲端應用程式的基本需求。

## <a name="monolithic-applications-can-be-cloud-devops-ready"></a>整合應用程式*可以*雲端 DevOps 就緒

請務必反白顯示該整合的應用程式 （不根據 microservices 的應用程式）*可以*是 DevOps 雲端應用程式。 您可以建立和操作充分利用雲端運算所使用的容器、 持續傳遞和 DevOps 組合模型的整合應用程式。 如果現有的整合應用程式最適合您的商務目標，您可以現代化它，並讓雲端 DevOps 就緒。

同樣地，如果 DevOps 雲端應用程式時，可以是整合的應用程式，其他、 更複雜的架構，像是多層式架構應用程式也可以被現代化 DevOps 雲端應用程式。

>[!div class="step-by-step"]
[上一頁](reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications.md)
[下一頁](what-about-cloud-optimized-applications.md)
