---
title: 雲端最佳化應用程式中的 Microsoft 技術
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |雲端最佳化應用程式中的 Microsoft 技術
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 45eeee165a1dcbfc7b6dbc5146ce2c4b2be2e643
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296247"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>雲端最佳化應用程式中的 Microsoft 技術

下列清單說明工具、 技術和解決方案，會被辨識為雲端最佳化應用程式的需求。 您可以根據您的優先順序，選擇性地或逐漸地採用雲端最佳化的項目。

-   **雲端基礎結構**:所提供的計算平台、 作業系統、 網路和儲存體的基礎結構。 Microsoft Azure 被位於此層級。

-   **執行階段**:這一層會提供執行應用程式的環境。 如果您使用的容器，此圖層通常根據[Docker 引擎](https://docs.docker.com/engine/)，在 Linux 主機上或在 Windows 主機上執行。 ([Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)從 Windows Server 2016 開始，支援。 Windows 容器是在 Windows 執行的現有.NET Framework 應用程式的最佳選擇）。

-   **管理雲端**:當您選擇的受管理的雲端選項時，您可以避免費用和複雜的管理和支援的基礎結構，Vm、 OS 修補程式，網路組態。 如果您選擇使用 IaaS 移轉，您會負責所有這些工作，以及相關聯的成本。 在受管理的雲端選項中，您只能管理的應用程式及您開發的服務。 雲端服務提供者通常會管理所有其他項目。 在 Azure 中的受管理的雲端服務的範例包括[Azure SQL Database](https://azure.microsoft.com/services/sql-database)， [Azure Redis 快取](https://azure.microsoft.com/services/cache/)， [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)， [Azure 儲存體](https://azure.microsoft.com/services/storage/)，[適用於 MySQL 的 azure 資料庫](https://azure.microsoft.com/services/mysql/)，[適用於 PostgreSQL 的 Azure 資料庫](https://azure.microsoft.com/services/postgresql/)， [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)，以及管理計算服務，例如[VM 擴展設定](https://azure.microsoft.com/services/virtual-machine-scale-sets/)， [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)， [Azure App Service](https://azure.microsoft.com/services/app-service/)，和[Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/)。

-   **應用程式開發**:當您建置在容器中執行的應用程式時，您可以從許多語言進行選擇。 本指南著重[.NET](https://www.microsoft.com/net)，但您可以使用其他語言，例如 Node.js、 Python、 Spring/Java，開發以容器為基礎的應用程式，或移。

-   **監視、 記錄和稽核的遙測**:監視及稽核的應用程式和在雲端中執行的容器的能力是很重要的任何雲端最佳化應用程式。 [Azure Application Insights](https://azure.microsoft.com/services/application-insights/)並[Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite)是主要的 Microsoft 工具，提供雲端最佳化應用程式監視和稽核。

-   **佈建**:自動化工具可協助您佈建基礎結構和應用程式部署至多個環境 （生產、 測試、 預備環境）。 您可以使用 Chef 和 Puppet 等工具來管理應用程式的組態和環境。 此圖層也可以實作使用較為簡單且直接的方法。 比方說，您可以使用工具、 Azure 命令列介面 (Azure CLI) 來直接部署然後使用持續部署和發行管理中的管線[Azure DevOps 服務](https://azure.microsoft.com/services/devops/)。

-   **應用程式生命週期**:[Azure 的 DevOps 服務](https://azure.microsoft.com/services/devops/)和其他工具，例如 Jenkins 會建置的 automation 伺服器可協助您實作 CI/CD 管線，包括發行管理。

這一章，以及相關的逐步解說中下, 一節特別著重於執行階段層 （Windows 容器） 的相關詳細資料。 本指南說明您可以部署在 Windows Server 2016 （和更新版本） 的 Windows 容器的 Vm 和 Azure 容器執行個體的方式。 此外，它也會涵蓋更進階的 PaaS 平台，例如 Azure App Service 和 Azure Service Fabric 等 Azure Kubernetes 服務的協調器。

## <a name="monolithic-applications-can-be-cloud-optimized"></a>整合型應用程式*可以*雲端最佳化

務必要反白顯示該單體式應用程式 （不以微服務為基礎的應用程式）*可以*是雲端最佳化應用程式。 您可以建立及運作善用雲端運算模型所使用的容器、 持續傳遞和 DevOps 組合的單體式應用程式。 如果現有的單體式應用程式最適合您的商務目標，您如何將它現代化，並將它雲端最佳化。

同樣地，如果單體式應用程式可以是雲端最佳化應用程式，其他、 更複雜的架構，例如多層式架構應用程式也可以現代化雲端最佳化應用程式。

>[!div class="step-by-step"]
>[上一頁](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[下一頁](what-about-cloud-native-applications.md)