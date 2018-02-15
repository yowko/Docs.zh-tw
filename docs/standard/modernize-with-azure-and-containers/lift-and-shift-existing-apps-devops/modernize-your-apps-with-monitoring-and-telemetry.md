---
title: "現代化應用程式與監控與遙測"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |現代化應用程式與監控與遙測"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1535951eb648deab17cf8c2fe64db6ddf7df4cb5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>現代化應用程式與監控與遙測

當您在生產環境中執行應用程式時，務必確認您尚未深入了解如何執行您的應用程式。 它正在執行以高層級嗎？ 使用者會收到錯誤，或為穩定且可靠的應用程式嗎？ 您需要監視豐富的效能、 強大警示與儀表板，以協助確保您的應用程式會使用並如預期般執行。 您也必須能夠快速查看是否有問題，請判斷多少客戶受到影響，並執行根本原因分析，以找出並修正問題。

## <a name="monitor-your-application-with-application-insights"></a>監視您的應用程式使用 Application Insights

Application Insights 是可延伸應用程式效能管理 (APM) 服務的 web 開發人員在多個平台上運作。 您可以使用它來監視即時 web 應用程式。 Application Insights 會自動偵測效能的異常狀況。 它包括強大的分析工具以協助您診斷問題，並協助您了解使用者實際執行的工作與您的應用程式。 Application Insights 被設計來協助您持續改善效能和可用性。 這也適用於應用程式上各種不同的平台，包括.NET、 Node.js 和 J2EE，是否裝載於內部部署或雲端中。 Application Insights 整合與您的 DevOps 程序，並且有各種不同的開發工具的連接點。

圖 4-10 顯示如何 Application Insights 監視您的應用程式並將它提供這些 insights 諸如儀表板的範例。

![Application Insights 監視儀表板](./media/image10.png)

> **圖 4-10。** Application Insights 監視儀表板

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>監視與記錄分析和其容器的監視解決方案 Docker 基礎結構

[Azure 記錄分析](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)屬於[整體監控解決方案的 Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)。 它也是的服務[Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)。 記錄分析會監視雲端和內部部署環境 (內部部署的 OMS) 可以協助維護可用性和效能。 它會收集您的雲端和內部部署環境中的其他監視工具來分析跨多個來源的資源所產生的資料。

相對於 Azure 基礎結構記錄檔，記錄分析作為 Azure 服務，內嵌來自其他 Azure 服務的記錄檔和度量資料 (透過[Azure 監視器](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))，Azure Vm、 Docker 容器，並在內部部署或其他雲端基礎結構。 記錄分析提供彈性的記錄搜尋和不足的方塊分析此資料之上。 它提供豐富的工具，可用來分析資料來源間、 複雜的查詢可讓到所有的記錄檔，而它可以主動警示會根據指定的條件。 您甚至可以收集自訂資料的中央記錄分析儲存機制中，您可以在此查詢，並將其視覺化。 您也可以利用的記錄分析的內建解決方案立即深入了解安全性與您的基礎結構的功能。

您可以存取記錄分析透過 OMS 入口網站或 Azure 入口網站在任何瀏覽器中執行，並提供您的組態設定的存取權和多個工具必須分析以及操作收集的資料。

[容器監視解決方案](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)中記錄分析可讓您檢視和管理您的 Docker 和 Windows 容器主機，在單一位置。 解決方案會顯示哪些容器執行時，哪些容器映像它們正在執行，並執行容器。 您可以檢視詳細的稽核資訊，包括與容器正在使用的命令。 您也可以透過檢視和搜尋集中式記錄檔，而不需要從遠端檢視 Docker 或 Windows 主機疑難排解容器。 您可以找到可能會有很多雜訊並消耗多餘的資源，在主機上的容器。 此外，您可以檢視集中式的 CPU、 記憶體、 儲存和網路使用量和效能資訊的容器。 您可以在執行 Windows 的電腦，集中管理，並比較記錄檔，從 Windows Server HYPER-V 和 Docker 容器。 解決方案支援下列容器 orchestrators:

-   Docker 群集

-   DC/OS

-   Kubernetes

-   Service Fabric

-   Red Hat OpenShift

圖 4-11 顯示各種容器主機和代理程式和 OMS 之間的關聯性。

![記錄分析容器監視解決方案](./media/image11.png)

> **圖 4-11。** 記錄分析容器監視解決方案

您可以使用監視容器記錄分析解決方案：

-   請參閱在單一位置中的所有容器主機的資訊。

-   知道哪些容器執行時，哪些映像它們正在執行，並執行所在。

-   容器，請參閱動作的稽核線索。

-   透過檢視和搜尋沒有遠端登入 Docker 主機的集中式的記錄進行疑難排解。

-   尋找可能是 「 雜訊鄰近項目，"，而且會耗用過多的資源，在主機上的容器。

-   集中式的 CPU、 記憶體、 儲存和網路使用量和容器的效能資訊檢視。

### <a name="additional-resources"></a>其他資源

-   **監視 Microsoft Azure 中的概觀**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   **Application Insights 是什麼？**

[https://docs.microsoft.com/azure/application-insights/app-insights-overview](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   **什麼是記錄分析？**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-overview](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   **記錄分析容器監控解決方案**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-containers](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   **Azure 監視的概觀**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   **Operations Management Suite (OMS) 是什麼？**

[https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   **在 OMS 服務的網狀架構監視的 Windows Server 容器**

[https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
[上一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[下一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
