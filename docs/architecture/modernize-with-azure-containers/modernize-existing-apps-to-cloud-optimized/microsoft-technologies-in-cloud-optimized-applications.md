---
title: 雲端優化應用程式中的 Microsoft 技術
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |雲端優化應用程式中的 Microsoft 技術
ms.date: 04/28/2018
ms.openlocfilehash: 915aa99d2331c5b9c46eabef3335fb809baa9370
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578221"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>雲端優化應用程式中的 Microsoft 技術

下列清單說明可辨識為雲端優化應用程式需求的工具、技術和解決方案。 視您的優先順序而定, 您可以選擇性或逐漸地採用雲端優化的元素。

- **雲端基礎結構**:提供計算平臺、作業系統、網路和存放裝置的基礎結構。 Microsoft Azure 位於此層級。

- **運行**時間:這一層提供了執行應用程式的環境。 如果您使用容器, 此層通常是以[Docker 引擎](https://docs.docker.com/engine/)為基礎, 它是在 Linux 主機或 Windows 主機上執行。 (從 Windows Server 2016 開始支援[Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)。 Windows 容器是在 Windows 上執行的現有 .NET Framework 應用程式的最佳選擇)。

- **受控雲端**:當您選擇受控雲端選項時, 可以避免管理和支援基礎結構、Vm、OS 修補程式和網路設定的費用和複雜性。 如果您選擇使用 IaaS 進行遷移, 則必須負責所有這些工作, 以及相關聯的成本。 在受管理的雲端選項中, 您只會管理您所開發的應用程式和服務。 雲端服務提供者通常會管理所有其他專案。 Azure 中受控雲端服務的範例包括[Azure SQL Database](https://azure.microsoft.com/services/sql-database)、 [Azure Redis Cache](https://azure.microsoft.com/services/cache/)、 [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)、 [Azure 儲存體](https://azure.microsoft.com/services/storage/)、[適用於 MySQL 的 Azure 資料庫](https://azure.microsoft.com/services/mysql/)、[適用於 PostgreSQL 的 Azure 資料庫](https://azure.microsoft.com/services/postgresql/)、 [Azure Active目錄](https://azure.microsoft.com/services/active-directory/)和受控計算服務, 例如[VM 擴展集](https://azure.microsoft.com/services/virtual-machine-scale-sets/)、 [Azure App Service](https://azure.microsoft.com/services/app-service/)和[Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/)。

- **應用程式開發**:當您建立在容器中執行的應用程式時, 可以選擇多種語言。 本指南著重于[.net](https://www.microsoft.com/net), 但是您可以使用其他語言 (例如 Node.js、Python、春季/JAVA 或 Go) 開發以容器為基礎的應用程式。

- **監視、遙測、記錄和審核**:監視和審核在雲端中執行之應用程式和容器的功能, 對於任何雲端優化應用程式都很重要。 [Azure 應用程式 Insights](https://azure.microsoft.com/services/application-insights/)和[Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite)是主要的 Microsoft 工具, 可提供雲端優化應用程式的監視和審核。

- 布建:自動化工具可協助您布建基礎結構, 並將應用程式部署到多個環境 (生產、測試、預備)。 您可以使用 Chef 和 Puppet 之類的工具來管理應用程式的設定和環境。 這一層也可以使用更簡單且更直接的方法來執行。 例如, 您可以使用 Azure 命令列介面 (Azure CLI) 工具直接部署, 然後在[Azure DevOps Services](https://azure.microsoft.com/services/devops/)中使用持續部署和發行管理管線。

- **應用程式生命週期**:[Azure DevOps Services](https://azure.microsoft.com/services/devops/)和其他工具 (例如 Jenkins) 都是建立的 automation 伺服器, 可協助您執行 CI/CD 管線, 包括 release management。

本章的下一節和相關的逐步解說, 特別著重于執行時間層 (Windows 容器) 的詳細資料。 本指南說明您可以在 Windows Server 2016 (和更新版本) 的 Vm 和 Azure 容器實例上部署 Windows 容器的方式。 它也涵蓋更先進的 PaaS 平臺, 例如 Azure Kubernetes Service 的 Azure App Service 和協調器。

## <a name="monolithic-applications-can-be-cloud-optimized"></a>整合型應用程式*可以*是雲端優化的

請務必強調, 整合型應用程式 (不是以微服務為基礎的應用程式)*可以*是雲端優化應用程式。 您可以使用容器、持續傳遞和 DevOps 的組合, 建立和操作整合式應用程式, 以利用雲端運算模型。 如果現有的整合型應用程式適合您的商務目標, 您可以將它現代化並使其成為雲端優化。

同樣地, 如果整合型應用程式可以是雲端優化的應用程式, 其他更複雜的架構 (例如多層式應用程式) 也可以現代化為雲端優化應用程式。

>[!div class="step-by-step"]
>[上一頁](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[下一頁](what-about-cloud-native-applications.md)
