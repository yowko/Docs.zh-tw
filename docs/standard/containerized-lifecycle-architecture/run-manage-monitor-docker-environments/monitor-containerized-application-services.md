---
title: 監視進行容器化應用程式服務
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 26854e9efc4d7e43d5896c30a1c5ce0801045f45
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="monitor-containerized-application-services"></a>監視進行容器化應用程式服務

務必將分割成多個容器和 microservices 的應用程式提供的方式來監視及分析應用程式的行為。

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)是監視即時應用程式的可延伸的分析服務。 它可以協助您偵測及診斷效能問題，以及了解使用者實際執行的工作與您的應用程式。 它被針對開發人員，可幫助您的意圖，持續改善效能，而且您的服務或應用程式的可用性。 Application Insights 適用於 web/服務和獨立各種不同的平台，例如.NET、 Java、 Node.js 和許多其他平台，裝載於內部部署或雲端上的應用程式。

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>分析使用 Application Insights 的 QA 環境 Docker 應用程式

因為它屬於 Docker 時，您可以圖表生命週期事件和效能計數器，從 Application Insights 上的 Docker 容器。 您只需要執行[應用程式 Insights Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)因為在您的主機和它的容器將會顯示效能計數器的主機，以及其他的 Docker 映像。 此應用程式 Insights Docker 映像 (圖 6-1） 可協助您監視您容器化應用程式所收集的效能和活動的 Docker 主機 (也就是您 Linux Vm)、 Docker 容器和執行的應用程式的遙測在其中。

![範例](./media/image1.png)

圖 6-1: Application Insights 監視 Docker 主機和容器

當您執行[應用程式 Insights Docker 映像](https://hub.docker.com/r/microsoft/applicationinsights/)上 Docker 主機時，您可以從下列：

-   生命週期有關主機上執行的所有容器的遙測，啟動、 停止和等等。

-   效能計數器的所有容器： CPU、 記憶體、 網路使用量，等等。

-   如果您同時安裝[Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)在容器中執行的應用程式，這些應用程式的所有遙測資料會用來識別容器與主機電腦的其他屬性。 因此，比方說，如果您有一個以上的主機中執行的應用程式的執行個體，您輕鬆地可以篩選您的應用程式遙測，由主應用程式。

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>設定 Application Insights 以監視 Docker 應用程式和 Docker 主機

若要建立 Application Insights 資源，請遵循下列清單中顯示的文件中的指示。 Azure 入口網站會為您建立必要的指令碼。

-   **在 Application Insights 監視 Docker 應用程式：**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **應用程式在 Docker Hub 和 Github Insights Docker 映像：**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) 和 <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **設定 ASP.NET 的 Application Insights:**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **網頁的應用程式 Insights:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](http://microsoft.com/oms)是簡化的 IT 管理解決方案，讓記錄分析、 自動化、 備份和站台復原。 根據[查詢](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/)在 Operations Management Suite，您可以提高[警示](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts)並將設定透過補救[Azure 自動化](https://docs.microsoft.com/azure/automation/)。 它也與緊密整合您現有的管理解決方案，以提供單一的半透明窗格的檢視。 Operations Management Suite 的資訊可協助您管理及保護在內部部署與雲端基礎結構。

### <a name="operations-management-suitehttpmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](http://microsoft.com/oms) Docker 容器解決方案

除了提供重要服務本身，Operations Management Suite 容器解決方案管理和監視 Docker 主機和容器，以顯示的詳細資訊，您的容器和容器主機，執行容器或失敗，並傳送至 Docker 精靈和容器記錄*stdout*和*stderr*。 它也會顯示效能計量 (例如容器和主機的 CPU、記憶體、網路和儲存體)，以協助您進行疑難排解，並找出有雜訊的鄰近容器。

![](./media/image2.png)

圖 6-2： 顯示 Operations Management Suite 的 Docker 容器資訊

Application Insights 和 Operations Management Suite 焦點放在監視活動。不過，Application Insights 著重於多監視的應用程式本身由於其應用程式內執行的 SDK。 不過，Operations Management Suite 更著重於基礎結構主機，周圍加上它同時提供富彈性，資料驅動型搜尋/查詢系統提供記錄在標尺上的深入分析。

Operations Management Suite 會實作為雲端式服務，因為您可以將它啟動並執行快速且需基礎結構服務中的最小投資。 新功能會自動傳遞，儲存您從持續性維護和升級的成本。

使用 Operations Management Suite 容器解決方案，您可以執行下列動作：

-   集中管理及相互關聯數百萬從大規模的 Docker 容器的記錄檔

-   請參閱在單一位置中的所有容器主機的資訊

-   知道哪些容器執行時，哪些映像它們正在執行，並執行所在

-   快速診斷可能會造成問題，容器主機的 「 雜訊芳鄰"容器

-   在容器上看到動作的稽核線索

-   透過檢視和搜尋沒有遠端 Docker 主機可集中式的記錄進行疑難排解

-   尋找可能"雜訊的鄰近項目 」、 在主機上的耗用過多資源的容器

-   集中式的 CPU、 記憶體、 儲存和容器的網路使用量和效能資訊檢視

-   產生測試與 Azure 自動化的 Docker 容器

您可以查看所執行的查詢類型的效能資訊 = 效能，如圖 6-3 所示。

![DockerPerfMetricsView](./media/image3.png){width="5.78625in" height="3.25in"}

圖 6-3： 效能度量的顯示 Operations Management Suite 的 Docker 主機

儲存查詢也是在 Operations Management Suite 中的標準功能，可協助您讓查詢所找到有用，並找出您的系統中的趨勢。

**進一歩** 找到有關安裝和設定 Docker 容器中的方案[Operations Management Suite](http://microsoft.com/oms)，請移至<https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>。

>[!div class="step-by-step"]
[上一個] (管理-生產-docker-environments.md) [下一步] (.../key-takeaways/index.md)
