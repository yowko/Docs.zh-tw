---
title: 使用監視和遙測將應用程式現代化
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |使用監視和遙測將應用程式現代化
ms.date: 04/30/2018
ms.openlocfilehash: 5bffb336234f63dca150acc9ef31f9efa2e3937b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578171"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>使用監視和遙測將應用程式現代化

當您在生產環境中執行應用程式時, 請務必深入瞭解應用程式的執行方式。 它在高階執行嗎？ 使用者是否遇到錯誤, 或是應用程式穩定且可靠？ 您需要豐富的效能監視、強大的警示和儀表板, 以協助確保您的應用程式可供使用並如預期般執行。 如果發生問題、判斷有多少客戶受到影響, 以及執行根本原因分析以找出問題並加以修正, 您也必須能夠快速查看。

## <a name="monitor-your-application-with-application-insights"></a>使用 Application Insights 監視您的應用程式

Application Insights 是可延伸的應用程式效能管理 (APM) 服務, 適用于在多個平臺上工作的 網頁程式開發人員。 使用它來監視您的即時 web 應用程式。 Application Insights 會自動偵測效能異常。 其中包含功能強大的分析工具, 可協助您診斷問題, 並協助您瞭解使用者實際上如何使用您的應用程式。 Application Insights 的設計可協助您持續改善效能和可用性。 它適用于各種平臺上的應用程式, 包括 .NET、node.js 和 J2EE, 不論是裝載于內部部署或雲端。 Application Insights 與您的 DevOps 流程整合, 並具有各種開發工具的連接點。

圖4-10 顯示 Application Insights 如何監視您的應用程式, 以及它如何將這些深入解析加入儀表板的範例。

![Application Insights 監視儀表板](./media/image10.png)

> **圖4-10。** Application Insights 監視儀表板

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>使用 Log Analytics 和其容器監視解決方案監視您的 Docker 基礎結構

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)是[Microsoft Azure 整體監視解決方案](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)的一部分。 它也是[Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)中的一項服務。 Log Analytics 會監視雲端和內部部署環境 (適用于內部部署的 OMS), 以協助維護可用性和效能。 它會收集您的雲端和內部部署環境中的資源所產生的資料, 以及從其他監視工具來提供跨多個來源的分析。

相對於 Azure 基礎結構記錄檔, Log Analytics 是 Azure 服務, 可從其他 Azure 服務 (透過[Azure 監視器](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))、Azure Vm、Docker 容器, 以及內部部署或其他雲端基礎結構內嵌記錄和計量資料。 Log Analytics 提供彈性的記錄搜尋, 以及此資料之上的現成分析。 它提供豐富的工具, 讓您用來跨來源分析資料、允許跨所有記錄進行複雜的查詢, 而且可以根據指定的條件主動發出警示。 您甚至可以在中央 Log Analytics 存放庫中收集自訂資料, 您可以在其中查詢並將其視覺化。 您也可以利用 Log Analytics 內建解決方案, 立即深入瞭解基礎結構的安全性和功能。

您可以透過 OMS 入口網站或 Azure 入口網站 (在任何瀏覽器中執行) 存取 Log Analytics, 並讓您存取設定和多項工具來分析及處理所收集的資料。

Log Analytics 中的[容器監視解決方案](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)可協助您在單一位置中, 查看及管理您的 Docker 和 Windows 容器主機。 解決方案會顯示哪些容器正在執行、其執行所在的容器映射, 以及容器的執行位置。 您可以查看詳細的審核資訊, 包括與容器搭配使用的命令。 您也可以藉由查看及搜尋集中式記錄來對容器進行疑難排解, 而不需要遠端查看 Docker 或 Windows 主機。 您可以在主機上找到可能有雜訊和耗用過量資源的容器。 此外, 您可以針對容器來查看集中式 CPU、記憶體、儲存體和網路使用量, 以及效能資訊。 在執行 Windows 的電腦上, 您可以集中化和比較 Windows Server、Hyper-v 和 Docker 容器的記錄檔。 此解決方案支援下列容器協調器:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

圖4-11 顯示各種容器主機和代理程式與 OMS 之間的關聯性。

![Log Analytics 容器監視解決方案](./media/image11.png)

> **圖4-11。** Log Analytics 容器監視解決方案

您可以使用 Log Analytics 容器監視解決方案來執行下列動作:

- 請參閱單一位置中所有容器主機的相關資訊。

- 知道哪些容器正在執行、它們正在執行哪些映射, 以及它們在何處執行。

- 查看容器上動作的審核記錄。

- 藉由在不遠端登入 Docker 主機的情況下, 查看及搜尋集中式記錄來進行疑難排解。

- 尋找可能是「有雜訊的鄰近專案」的容器, 並耗用主機上的過量資源。

- 針對容器, 觀看集中化的 CPU、記憶體、儲存體和網路使用量, 以及效能資訊。

### <a name="additional-resources"></a>其他資源

- **在 Microsoft Azure 中監視的總覽**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **什麼是 Application Insights？**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **什麼是 Log Analytics？**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Azure 監視器中的容器監視解決方案**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Azure 監視器總覽**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **何謂 Operations Management Suite (OMS)？**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[上一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[下一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
