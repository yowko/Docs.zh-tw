---
title: 監視容器化應用程式服務
description: 了解一些重要的層面的監視容器架構
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 4553a35c8db6cfc46187525ef2ffc65cb3ba07c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672044"
---
# <a name="monitor-containerized-application-services"></a>監視容器化應用程式服務

最重要的是應用程式分割成多個容器和微服務的方式，來監視及分析整個應用程式的行為。

## <a name="azure-monitor"></a>Azure Monitor

[Azure 監視器](https://azure.microsoft.com/services/monitor/)是可延伸分析服務，可監視您即時應用程式。 它可協助您偵測並診斷效能問題，並了解使用者實際如何運用您的應用程式。 它被專為開發人員，協助您持續改善效能的目的與您的服務或應用程式的可用性。 Azure 監視器可搭配 web/服務和獨立上各種不同的平台，例如.NET、 Java、 Node.js 和許多其他平台，裝載於內部部署或雲端中的應用程式。

### <a name="additional-resources"></a>其他資源

- **Azure 監視器概觀** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **什麼是 Application Insights？** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **什麼是 Azure 監視器計量？** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Azure 監視器中的容器監視解決方案** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>安全性與備份服務

有許多支援例行工作，有許多您必須處理以確保您的應用程式和基礎結構來支援商務需求的最上層的波陷條件的詳細資料，而且這種情況就會變成更複雜的微服務領域中，而您需要想辦法當您需要採取動作時，有高階和詳細檢視。

Azure 有工具來管理，並提供四個重要層面雲端和內部部署資源的統一的檢視：

- **安全性**。 具有[Azure 資訊安全中心](https://azure.microsoft.com/services/security-center/)。
  - 取得完整的可見度及控制您的虛擬機器、 應用程式和工作負載的安全性。
  - 集中管理您的安全性原則，並整合現有的程序和工具。
  - 偵測真正的威脅，使用進階分析。

- **備份**。 具有[Azure 備份](https://azure.microsoft.com/services/backup/)。
  - 避免耗費資源的業務中斷情況、 符合合規性目標和保護資料不受勒索軟體和人為錯誤。
  - 保留備份資料傳輸中和待用加密。
  - 請確定以防止未經授權的使用多重要素驗證為基礎的存取。

- **在內部部署資源**。 具有[真正的一致性混合式雲端](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)。

>[!div class="step-by-step"]
>[上一頁](manage-production-docker-environments.md)
>[下一頁](../key-takeaways/index.md)
