---
title: 監視容器化應用程式服務
description: 了解監視容器架構的一些重要層面
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641203"
---
# <a name="monitor-containerized-application-services"></a>監視容器化應用程式服務

對於分割成多個容器和微服務的應用程式來說，最重要的是要有一種方法來監視及分析整個應用程式行為。

## <a name="azure-monitor"></a>Azure 監視器

[Azure 監視器](https://azure.microsoft.com/services/monitor/)是一項可延伸的分析服務，用來監視您的即時應用程式。 它可協助您偵測並診斷效能問題，以及了解實際上使用者如何運用您的應用程式。 它專為開發人員而設計，目的是協助您持續改善服務或應用程式的效能與可用性。 Azure 監視器可與內部部署或雲端中所裝載之各種不同平台 (例如 .NET、Java、Node.js 及許多其他平台) 的 Web/服務和獨立應用程式搭配運作。

### <a name="additional-resources"></a>其他資源

- **Azure 監視器的概觀** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **什麼是 Application Insights？** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Azure 監視器計量是什麼？** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Azure 監視器中的容器監視解決方案** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>安全性與備份服務

您必須處理許多內含大量詳細資料的支援例行工作，以確保您的應用程式和基礎結構處於最佳狀態來支援商務需求，且這種情況在微服務領域中變得更加複雜，因此當您需要採取動作時，您需要想辦法同時擁有高階和詳細檢視。

Azure 具有工具可用來管理雲端和內部部署資源的四個重要層面，並提供其統一檢視：

- **安全性**。 使用 [Azure 資訊安全中心](https://azure.microsoft.com/services/security-center/)。
  - 完整檢視及控制虛擬機器、應用程式和工作負載的安全性。
  - 集中管理您的安全性原則，並整合現有的處理序和工具。
  - 使用進階分析偵測真正的威脅。

- **備份**。 使用 [Azure 備份](https://azure.microsoft.com/services/backup/)。
  - 避免耗費資源的業務中斷情況、符合相容性目標，以及保護資料不受勒索軟體和人為錯誤影響。
  - 使資料在傳送過程及待用期間保持加密。
  - 確保根據多重要素驗證進行存取，以防止未經授權的使用。

- **內部部署資源**。 使用[真正一致的混合式雲端](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)。

>[!div class="step-by-step"]
>[上一頁](manage-production-docker-environments.md)
>[下一頁](../key-takeaways/index.md)
