---
title: 使用監視和遙測將應用程式現代化
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |使用監視和遙測將應用程式現代化
ms.date: 04/30/2018
ms.openlocfilehash: a6094435eece661d99904876ac49b3ca85ec45a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171997"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>使用監視和遙測將應用程式現代化

當您在生產環境中執行應用程式時，您必須深入瞭解應用程式的執行方式。 它是以高層級執行嗎？ 使用者是否會收到錯誤，或應用程式穩定且可靠？ 您需要豐富的效能監視、強大的警示和儀表板，以協助確保您的應用程式可供使用，並如預期般執行。 如果發生問題，您也必須能夠快速查看，判斷有多少客戶受到影響，並執行根本原因分析，以找出並修正問題。

## <a name="monitor-your-application-with-application-insights"></a>使用 Application Insights 監視您的應用程式

Application Insights 是適用于多個平臺的 網頁程式開發人員，可延伸的應用程式效能管理 (APM) 服務。 您可以使用它來監視即時 Web 應用程式。 Application Insights 會自動偵測效能異常。 它包含強大的分析工具，可協助您診斷問題，並協助您瞭解使用者實際如何運用您的應用程式。 Application Insights 設計用來協助您持續改善效能和可用性。 它適用于各種平臺上的應用程式，包括 .NET、Node.js 和 J2EE，無論是裝載于內部部署或雲端。 Application Insights 與您的 DevOps 程式整合，並有各種開發工具的連接點。

圖4-10 顯示 Application Insights 如何監視您的應用程式，以及它如何向儀表板呈現這些深入解析的範例。

![Application Insights 監視儀表板的螢幕擷取畫面。](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**圖4-10。** Application Insights 監視儀表板

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>使用 Log Analytics 與其容器監視解決方案來監視您的 Docker 基礎結構

[Azure Log Analytics](/azure/log-analytics/log-analytics-overview) 是 [Microsoft Azure 整體監視解決方案](/azure/monitoring-and-diagnostics/monitoring-overview)的一部分。 它也是 [Operations Management Suite (OMS) ](/azure/operations-management-suite/operations-management-suite-overview)的服務。 Log Analytics 會監視雲端和內部部署環境 (OMS 進行內部部署) ，以協助維護可用性和效能。 它會收集您的雲端和內部部署環境中的資源所產生的資料，以及從其他監視工具提供橫跨多個來源的分析。

與 Azure 基礎結構記錄檔、Log Analytics 和 azure 服務相關，可透過 [Azure 監視器](/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)) 、Azure Vm、Docker 容器，以及內部部署或其他雲端基礎結構，從其他 Azure 服務 (內嵌記錄和度量資料。 Log Analytics 提供彈性的記錄搜尋，以及此資料之上的現成分析。 它提供豐富的工具，可讓您用來跨來源分析資料、允許跨所有記錄進行複雜的查詢，而且可以根據指定的條件主動發出警示。 您甚至可以在中央 Log Analytics 存放庫中收集自訂資料，您可以在其中進行查詢並將其視覺化。 您也可以利用 Log Analytics 內建解決方案來立即深入瞭解基礎結構的安全性和功能。

您可以透過 OMS 入口網站或 Azure 入口網站（在任何瀏覽器中執行）來存取 Log Analytics，並讓您能夠存取設定和多個工具來分析及處理收集到的資料。

Log Analytics 中的 [容器監視解決方案](/azure/log-analytics/log-analytics-containers) 可協助您在單一位置中查看和管理 Docker 和 Windows 容器主機。 解決方案會顯示正在執行的容器、它們正在執行的容器映射，以及容器的執行位置。 您可以查看詳細的審核資訊，包括搭配容器使用的命令。 您也可以藉由查看及搜尋集中式記錄來疑難排解容器，而不需要遠端查看 Docker 或 Windows 主機。 您可以找出可能有雜訊的容器，並在主機上耗用過度的資源。 此外，您可以針對容器查看集中式 CPU、記憶體、儲存體和網路使用量，以及效能資訊。 您可以在執行 Windows 的電腦上集中管理，並從 Windows Server、HYPER-V 和 Docker 容器比較記錄。 解決方案支援下列容器協調者：

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

圖4-11 顯示各種容器主機和代理程式與 OMS 之間的關聯性。

![Log Analytics 容器監視解決方案的螢幕擷取畫面。](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**圖4-11。** Log Analytics 容器監視解決方案

您可以使用 Log Analytics 容器監視解決方案來：

- 查看單一位置中所有容器主機的相關資訊。

- 知道哪些容器正在執行、其正在執行的映射，以及執行的位置。

- 查看容器上動作的審核記錄。

- 藉由在不遠端登入 Docker 主機的情況下，查看及搜尋集中式記錄來進行疑難排解。

- 尋找可能是「有雜訊的鄰近專案」的容器，並在主機上耗用過度的資源。

- 查看容器的集中式 CPU、記憶體、儲存體和網路使用量，以及效能資訊。

### <a name="additional-resources"></a>其他資源

- **Microsoft Azure 中的監視總覽**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **什麼是 Application Insights？**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **什麼是 Log Analytics？**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Azure 監視器中的容器監視解決方案**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Azure 監視器的概觀**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Operations Management Suite (OMS) 是什麼？**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[上一個](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md) 
>[下一步](life-cycle-ci-cd-pipelines-devops-tools.md)
