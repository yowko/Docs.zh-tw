---
title: 監視容器化應用程式服務
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 4bdc4470624ce6e905ab858a2bd8b607c8d3d646
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326461"
---
# <a name="monitor-containerized-application-services"></a>監視容器化應用程式服務

最重要的是應用程式分割成多個容器和微服務的方式，來監視及分析應用程式的行為。

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)是可延伸分析服務，可監視您即時應用程式。 它可協助您偵測並診斷效能問題，並了解使用者實際如何運用您的應用程式。 它被專為開發人員，協助您持續改善效能的目的與您的服務或應用程式的可用性。 Application Insights 可搭配 web/服務和獨立上各種不同的平台，例如.NET、 Java、 Node.js 和許多其他平台，裝載於內部部署或雲端中的應用程式。

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>在 QA 環境中使用 Application Insights 分析的 Docker 應用程式

因為它適用於 Docker，您可以圖表生命週期事件和從 Application Insights 上的 Docker 容器的效能計數器。 您只需要執行[Application Insights 的 Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)如的容器中您的主機，它會顯示的主機，以及其他的 Docker 映像的效能計數器。 此應用程式深入解析的 Docker 映像 (圖 6-1） 可協助您監視您的容器化應用程式所收集的效能和活動，您的 Docker 主機 (也就是您的 Linux Vm) 及 Docker 容器執行的應用程式的遙測在其中。

![範例](./media/image1.png)

圖 6-1: Application Insights 監視 Docker 主機和容器

當您執行[Application Insights 的 Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)上您的 Docker 主機，您可以從下列：

-   生命週期主機上執行的所有容器的相關遙測-啟動、 停止和等等。

-   所有容器的效能計數器： CPU、 記憶體、 網路使用量，等等。

-   如果您也安裝了[Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)在容器中執行的應用程式，這些應用程式的所有遙測資料會識別容器和主機電腦的其他屬性。 因此，比方說，如果您有一個以上的主控件上執行的應用程式的執行個體時，輕易地就能夠篩選由主應用程式的應用程式遙測。

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>設定 Application Insights 來監視 Docker 應用程式和 Docker 主機

若要建立 Application Insights 資源，請遵循下列清單所述的文章中的指示。 Azure 入口網站會為您建立必要的指令碼。

-   **在 Application Insights 中監視 Docker 應用程式：**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **在 Docker Hub 和 Github 應用程式深入解析的 Docker 映像：**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) 和 <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **設定適用於 ASP.NET 的 Application Insights:**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **適用於網頁的 application Insights:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](https://microsoft.com/oms)是簡化的 IT 管理解決方案，提供 log analytics、 自動化、 備份和 site recovery。 根據[查詢](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/)在 Operations Management Suite，您可以提高[警示](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts)並設定透過補救[Azure 自動化](https://docs.microsoft.com/azure/automation/)。 它也會順暢地整合與您現有的管理解決方案，以提供單一的半透明效果 窗格檢視。 Operations Management Suite 可協助您管理並保護您內部部署和雲端基礎結構。

### <a name="operations-management-suitehttpsmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](https://microsoft.com/oms)適用於 Docker 的容器解決方案

除了自行提供重要服務，Operations Management Suite 的容器解決方案管理和監視 Docker 主機和容器所顯示的詳細資訊，您的容器和容器主機，哪些容器正在執行或失敗，並傳送至 Docker 精靈和容器記錄*stdout*並*stderr*。 它也會顯示效能計量 (例如容器和主機的 CPU、記憶體、網路和儲存體)，以協助您進行疑難排解，並找出有雜訊的鄰近容器。

![](./media/image2.png)

圖 6-2： 顯示 Operations Management suite 的 Docker 容器的資訊

Application Insights 和 Operations Management Suite 焦點放在監視活動;不過，Application Insights 著重於更監視的應用程式本身由於其應用程式內執行的 SDK。 不過，Operations Management Suite 更著重於基礎結構主機，再加上它同時提供極具彈性的資料導向搜尋/查詢系統提供大規模的記錄檔的深入分析。

由於 Operations Management Suite 會實作為雲端服務中，您可以將它啟動並執行快速且最少的投資，基礎結構服務中。 新功能會自動提供，以節省持續維護和升級成本。

使用 Operations Management Suite 容器解決方案，您可以執行下列作業：

-   集中管理，並將相互關聯數以百萬計的大規模的 Docker 容器記錄

-   請參閱在單一位置中的所有容器主機的相關資訊

-   了解哪些容器正在執行，就會有何種映像它們執行，並執行所在

-   快速診斷可能會造成問題，在容器主機的 「 吵雜鄰居 」 容器

-   在容器上查看動作的稽核線索

-   檢視及搜尋集中式記錄檔，而不需要遠端 Docker 主機來進行疑難排解

-   尋找可能 「 吵雜芳鄰 」 且耗用過多的資源，在主機上的容器

-   檢視集中式的 CPU、 記憶體、 儲存體，以及適用於容器的網路使用量和效能資訊

-   產生測試使用 Azure 自動化的 Docker 容器

您可以執行類似類型的查詢，以便查看效能資訊 = 效能，如所示的圖 6-3。

![DockerPerfMetricsView](./media/image3.png){width="5.78625in" height="3.25in"}

圖 6-3： 效能度量的顯示 Operations Management suite 的 Docker 主機

儲存查詢也是 Operations Management Suite 中的標準功能，可協助您保留您認為有用，並找出您的系統中的趨勢的查詢。

**進一歩** 若要尋找有關安裝及設定 Docker 中的容器解決方案[Operations Management Suite](https://microsoft.com/oms)，請移至<https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>。

>[!div class="step-by-step"]
[上一頁](manage-production-docker-environments.md)
[下一頁](../key-takeaways/index.md)
