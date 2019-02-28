---
title: 監視容器化應用程式服務
description: 了解一些重要的層面的監視容器架構
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 925db543617deb28590cf6631ebbda3ee96836c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975741"
---
# <a name="monitor-containerized-application-services"></a>監視容器化應用程式服務

最重要的是應用程式分割成多個容器和微服務的方式，來監視及分析整個應用程式的行為。

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)是可延伸分析服務，可監視您即時應用程式。 它可協助您偵測並診斷效能問題，並了解使用者實際如何運用您的應用程式。 它被專為開發人員，協助您持續改善效能的目的與您的服務或應用程式的可用性。 Application Insights 可搭配 web/服務和獨立上各種不同的平台，例如.NET、 Java、 Node.js 和許多其他平台，裝載於內部部署或雲端中的應用程式。

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>在 QA 環境中使用 Application Insights 分析的 Docker 應用程式

因為它適用於 Docker，您可以圖表生命週期事件和從 Application Insights 上的 Docker 容器的效能計數器。 您只需要執行[Application Insights 的 Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)如的容器中您的主機，它會顯示的主機，以及其他的 Docker 映像的效能計數器。 此應用程式深入解析的 Docker 映像 (圖 6-1） 可協助您監視您的容器化應用程式所收集的效能和活動，您的 Docker 主機 (也就是您的 Linux Vm) 及 Docker 容器執行的應用程式的遙測在其中。

![範例](./media/image1.png)

**圖 6-1**. Application Insights 監視 Docker 主機和容器

當您執行[Application Insights 的 Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)上您的 Docker 主機，您可以從下列：

- 生命週期主機上執行的所有容器的相關遙測-啟動、 停止和等等。

- 所有容器的效能計數器：CPU、 記憶體、 網路使用量，等等。

- 如果您也安裝了[Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)在容器中執行的應用程式，這些應用程式的所有遙測資料會識別容器和主機電腦的其他屬性。 因此，比方說，如果您有一個以上的主控件上執行的應用程式的執行個體時，輕易地就能夠篩選由主應用程式的應用程式遙測。

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>設定 Application Insights 來監視 Docker 應用程式和 Docker 主機

若要建立 Application Insights 資源，請遵循下列清單所述的文章中的指示。 Azure 入口網站會為您建立必要的指令碼。

- **在 Application Insights 中監視 Docker 應用程式：** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-docker>

- **在 Docker Hub 和 GitHub 應用程式深入解析的 Docker 映像：** \
  <https://hub.docker.com/r/microsoft/applicationinsights/> 和 \
  <https://github.com/Microsoft/ApplicationInsights-Docker>

- **設定 ASP.NET web 應用程式和 ASP.NET Core 的 Application Insights:** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-asp-net>

- **適用於網頁的 application Insights:**  
  <https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="security-backup-and-monitoring-services"></a>安全性、 備份及監視服務

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

- **監視**。 具有[Azure 監視](https://azure.microsoft.com/solutions/monitoring/)， [Log Analytics](https://azure.microsoft.com/services/log-analytics/)，並[Application Insights](https://azure.microsoft.com/services/application-insights/)。
  - 取得完整的可見性的健全狀況和效能，您的 Azure 工作負載、 應用程式和基礎結構。
  - 從任何來源收集資料，並取得豐富的深入了解您的虛擬機器、 容器和應用程式。
  - 尋找您需要使用互動式查詢和全文檢索搜尋的資訊。 
  - 執行根本原因分析使用進階分析，包括機器學習服務演算法。

- **在內部部署資源**。 具有[真正的一致性混合式雲端](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)。

>[!div class="step-by-step"]
>[上一頁](manage-production-docker-environments.md)
>[下一頁](../key-takeaways/index.md)
