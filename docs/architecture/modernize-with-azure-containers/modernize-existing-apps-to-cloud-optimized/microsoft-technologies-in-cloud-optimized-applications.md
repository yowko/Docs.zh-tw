---
title: 雲端優化應用程式中的 Microsoft 技術
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |雲端優化應用程式中的 Microsoft 技術
ms.date: 04/28/2018
ms.openlocfilehash: b257497835638dd65c894998e95bd7e9d784b7bf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172010"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>雲端優化應用程式中的 Microsoft 技術

下列清單說明可辨識為雲端優化應用程式需求的工具、技術和解決方案。 您可以根據您的優先順序，選擇性或漸進式地採用雲端優化元素。

- **雲端基礎結構**：提供計算平臺、作業系統、網路和儲存體的基礎結構。 Microsoft Azure 位於此層級。

- **運行**時間：此層提供執行應用程式的環境。 如果您使用容器，此層通常是以在 Linux 主機或 Windows 主機上執行的 [Docker 引擎](https://docs.docker.com/engine/)為基礎。 從 Windows Server 2016 開始支援 ([Windows 容器](/virtualization/windowscontainers/about/) 。 Windows 容器是在 Windows 上執行之現有 .NET Framework 應用程式的最佳選擇。 ) 

- **受控雲端**：當您選擇受控雲端選項時，您可以避免管理及支援基礎結構、VM、OS 修補程式和網路設定的費用和複雜性。 如果您選擇使用 IaaS 進行遷移，您必須負責所有這些工作，以及相關聯的成本。 在受控雲端選項中，您只會管理您開發的應用程式和服務。 雲端服務提供者通常會管理其他所有專案。 Azure 中受控雲端服務的範例包括 [Azure SQL Database](https://azure.microsoft.com/services/sql-database)、 [Azure Redis](https://azure.microsoft.com/services/cache/)快取、 [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)、 [Azure 儲存體](https://azure.microsoft.com/services/storage/)、 [適用於 MySQL 的 Azure 資料庫](https://azure.microsoft.com/services/mysql/)、 [適用於 PostgreSQL 的 Azure 資料庫](https://azure.microsoft.com/services/postgresql/)、 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)和受控計算服務，例如 [VM 擴展集](https://azure.microsoft.com/services/virtual-machine-scale-sets/)、 [Azure App Service](https://azure.microsoft.com/services/app-service/)和 [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/)。

- **應用程式開發**：當您建立在容器中執行的應用程式時，可以從許多語言中選擇。 本指南著重于 [.net](https://dotnet.microsoft.com)，但您可以使用其他語言來開發以容器為基礎的應用程式，例如 Node.js、Python、春季/JAVA 或 Go。

- **監視、遙測、記錄和審核**：監視和審核在雲端中執行之應用程式和容器的能力，對任何雲端優化應用程式來說都很重要。 [Azure 應用程式見解](https://azure.microsoft.com/services/application-insights/) 和 [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) 是提供雲端優化應用程式監視和審核的主要 Microsoft 工具。

- 布**建：自動化**工具可協助您布建基礎結構，並將應用程式部署到多個環境， (生產、測試、暫存) 。 您可以使用 Chef 和 Puppet 等工具來管理應用程式的設定和環境。 您也可以使用更簡單且更直接的方法來執行這一層。 例如，您可以使用 Azure 命令列介面 (Azure CLI) 工具來直接部署，然後使用 [Azure DevOps Services](https://azure.microsoft.com/services/devops/)中的持續部署和發行管理管線。

- **應用程式生命週期**： [Azure DevOps Services](https://azure.microsoft.com/services/devops/) 和其他工具（例如 Jenkins）都是建立的自動化伺服器，可協助您執行 CI/CD 管線，包括 release management。

本章的下一節和相關的逐步解說，特別著重于)  (Windows 容器的執行時間層詳細資料。 本指南說明您可以將 Windows 容器部署在 Windows Server 2016 (和更新版本) Vm 和 Azure 容器實例的方式。 它也涵蓋更先進的 PaaS 平臺，例如 Azure App Service 和協調器，例如 Azure Kubernetes Service。

## <a name="monolithic-applications-can-be-cloud-optimized"></a>整合型應用程式 *可* 進行雲端優化

重要的是， (不是以微服務) 為基礎的應用程式 *可以* 是雲端優化應用程式，這點很重要。 您可以使用容器、持續傳遞和 DevOps 的組合，建立及操作可利用雲端運算模型的整合型應用程式。 如果現有的整合型應用程式最適合您的業務目標，您可以將它現代化，並使其成為雲端優化。

同樣地，如果整合型應用程式可以是雲端優化應用程式，其他更複雜的架構（例如多層式應用程式）也可以現代化為雲端優化應用程式。

>[!div class="step-by-step"]
>[上一個](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md) 
>[下一步](what-about-cloud-native-applications.md)
