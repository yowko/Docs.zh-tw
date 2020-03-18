---
title: 雲優化應用程式中的微軟技術
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |雲優化應用程式中的微軟技術
ms.date: 04/28/2018
ms.openlocfilehash: 915aa99d2331c5b9c46eabef3335fb809baa9370
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69578221"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>雲優化應用程式中的微軟技術

下面的清單描述了可識別為雲優化應用要求的工具、技術和解決方案。 您可以根據優先順序有選擇地或逐步採用雲優化元素。

- **雲基礎架構**：提供計算平臺、作業系統、網路和存儲的基礎結構。 Microsoft Azure 位於此級別。

- **運行時**：此層為應用程式提供運行的環境。 如果使用容器，此層通常基於[Docker 引擎](https://docs.docker.com/engine/)，在 Linux 主機上運行或在 Windows 主機上運行。 （支援從 Windows 伺服器 2016 年開始的[Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)。 對於在 Windows 上運行的現有 .NET 框架應用程式，Windows 容器是最佳選擇。

- **託管雲**：當您選擇託管雲選項時，可以避免管理和支援底層基礎結構、VM、作業系統修補程式和網路設定的費用和複雜性。 如果選擇使用 IaaS 進行遷移，則負責所有這些任務以及相關成本。 在託管雲選項中，您只管理開發的應用程式和服務。 雲服務提供者通常管理其他所有內容。 Azure 中託管雲服務的示例包括[Azure SQL 資料庫](https://azure.microsoft.com/services/sql-database)[、Azure Redis 緩存](https://azure.microsoft.com/services/cache/)[、Azure 宇宙資料庫](https://azure.microsoft.com/services/cosmos-db/)[、Azure 存儲](https://azure.microsoft.com/services/storage/)[、MySQL Azure 資料庫](https://azure.microsoft.com/services/mysql/)[、PostgreSQL Azure 資料庫](https://azure.microsoft.com/services/postgresql/)[、Azure 活動目錄](https://azure.microsoft.com/services/active-directory/)以及[VM 規模集](https://azure.microsoft.com/services/virtual-machine-scale-sets/)[、Azure 應用服務和](https://azure.microsoft.com/services/app-service/) [Azure Kubernetes 服務](https://azure.microsoft.com/services/container-service/)等託管計算服務。

- **應用程式開發**：在生成在容器中運行的應用程式時，可以從多種語言中進行選擇。 本指南重點介紹[.NET](https://www.microsoft.com/net)，但是，您可以使用其他語言（如 Node.js、Python、Spring/JAVA 或 Go）開發基於容器的應用。

- **監視、遙測、日誌記錄和審核**：監視和審核在雲中運行的應用程式和容器的能力對於任何雲優化應用程式都至關重要。 [Azure 應用程式見解](https://azure.microsoft.com/services/application-insights/)和[Microsoft 操作管理套件](https://www.microsoft.com/cloud-platform/operations-management-suite)是 Microsoft 的主要工具，為雲優化應用提供監視和審核。

- **預配**：自動化工具可説明您預配基礎結構並將應用程式部署到多個環境（生產、測試、暫存）。 您可以使用 Chef 和 Puppet 等工具來管理應用程式的配置和環境。 此層也可以通過使用更簡單、更直接的方法實現。 例如，可以使用 Azure 命令列介面 （Azure CLI） 工具直接部署，然後在[Azure DevOps 服務](https://azure.microsoft.com/services/devops/)中使用連續部署和發佈管理管道。

- **應用程式生命週期**[：Azure DevOps 服務](https://azure.microsoft.com/services/devops/)和其他工具（如 Jenkins）是構建的自動化伺服器，可説明您實現 CI/CD 管道，包括發佈管理。

本章的下一部分以及相關的演練特別側重于有關運行時層（Windows 容器）的詳細資訊。 本指南介紹了在 Windows Server 2016（和更高版本）VM 和 Azure 容器實例上部署 Windows 容器的方法。 它還涵蓋更高級的 PaaS 平臺，如 Azure 應用服務和業務流程庫伯奈斯服務等協調器。

## <a name="monolithic-applications-can-be-cloud-optimized"></a>單片應用程式*可以*進行雲優化

必須強調，單一應用程式（不基於微服務的應用程式）*可以是*雲優化應用程式。 您可以使用容器、連續交付和 DevOps 的組合來構建和操作利用雲計算模型的單體應用程式。 如果現有的單片應用程式適合您的業務目標，則可以對其進行現代化改造，使其實現雲優化。

同樣，如果單一應用程式可以是雲優化應用程式，那麼其他更複雜的體系結構（如 N-Tier 應用程式）也可以作為雲優化應用程式進行現代化改造。

>[!div class="step-by-step"]
>[上一個](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[下一個](what-about-cloud-native-applications.md)
