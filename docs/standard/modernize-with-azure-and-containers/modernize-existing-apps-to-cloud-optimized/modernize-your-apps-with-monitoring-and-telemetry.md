---
title: 使用監視和遙測將應用程式現代化
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |現代化您的應用程式監視和遙測
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: a8135031d2879ff377881d246c532573a2149fe7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611649"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>使用監視和遙測將應用程式現代化

當您在生產環境中執行應用程式時，務必您已深入了解如何執行您的應用程式。 它很高的層級嗎？ 使用者收到錯誤，或是為穩定且可靠的應用程式嗎？ 您需要豐富的效能監視、 功能強大警示與儀表板，以協助確保您的應用程式可用且如預期般執行。 您也需要能夠快速查看是否有問題、 判斷多少客戶會受到影響，以及執行根本原因分析，以找出並修正問題。

## <a name="monitor-your-application-with-application-insights"></a>監視您的應用程式使用 Application Insights

Application Insights 是可延伸的應用程式效能管理 (APM) 服務的 web 開發人員在多個平台上運作。 您可以使用它來監視即時 web 應用程式。 Application Insights 會自動偵測效能異常。 其中包括強大的分析工具可協助您診斷問題，並可協助您了解使用者實際如何運用您的應用程式。 Application Insights 可協助您持續改善效能和可用性。 它適用於應用程式在各種不同的平台，包括.NET、 Node.js 和 J2EE，是否裝載於內部部署或雲端中。 Application Insights 整合您的 DevOps 程序，並有各種不同的開發工具的連接點。

圖 4-10 說明 Application Insights 監視您的應用程式的方式，和如何它的儀表板，會在呈現這些深入資訊時的範例。

![Application Insights 監視儀表板](./media/image10.png)

> **圖 4-10。** Application Insights 監視儀表板

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>監視您的 Docker 基礎結構，與 Log Analytics 和其容器監視解決方案

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)屬於[Microsoft Azure 整體監視解決方案](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)。 它也是服務[Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)。 Log Analytics 監視雲端和內部部署環境 (如內部部署的 OMS) 以協助維護可用性和效能。 它會收集您的雲端和內部部署環境以及從其他監視工具，以分析跨多個來源的資源所產生的資料。

Azure 基礎結構記錄檔，與 Log Analytics，做為 Azure 服務，內嵌來自其他 Azure 服務的記錄和計量資料 (透過[Azure 監視器](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))，Azure Vm、 Docker 容器，並在內部部署環境或其他雲端基礎結構。 Log Analytics 提供彈性的記錄搜尋和外的分析此資料。 它提供豐富的工具，可用來跨來源分析資料、 允許跨所有記錄，將複雜的查詢，它可以主動警示會根據指定的條件。 您甚至可以在中央 Log Analytics 儲存機制，您可以在此查詢，並將其視覺化的自訂資料收集。 您也可以充分利用 Log Analytics 內建解決方案，可以立即從中取得深入了解安全性和基礎結構的功能。

您可以透過 OMS 入口網站或 Azure 入口網站，在任何瀏覽器中執行，存取 Log Analytics，並提供您存取組態設定和多個工具來分析及處理收集到的資料。

[容器監視解決方案](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)Log Analytics 可以協助您檢視和管理您的 Docker 和 Windows 容器主機，在單一位置。 解決方案會顯示哪些容器正在執行，哪些容器映像它們執行，以及容器執行的位置。 您可以檢視詳細的稽核資訊，包括容器正在使用的命令。 您也可以對容器進行疑難排解檢視及搜尋集中式記錄檔，而不需要從遠端檢視 Docker 或 Windows 的主機。 您可以找到可能會有雜訊且耗用過多的資源，在主機上的容器。 此外，您可以檢視集中式的 CPU、 記憶體、 儲存體和網路使用量和適用於容器的效能資訊。 在執行 Windows 的電腦，您可以集中管理，並比較記錄檔從 Windows Server、 HYPER-V 和 Docker 容器。 解決方案支援下列容器協調者：

- Docker Swarm

- DC/OS

- Kubernetes

- Service Fabric

- Red Hat OpenShift

圖 4-11 說明各種不同的容器主機和代理程式和 OMS 之間的關聯性。

![Log Analytics 容器監視解決方案](./media/image11.png)

> **圖 4-11。** Log Analytics 容器監視解決方案

您可以使用 Log Analytics 容器監視解決方案：

- 請參閱在單一位置中的所有容器主機的相關資訊。

- 了解哪些容器正在執行，就會有何種映像它們執行，並正在執行的所在。

- 容器，請參閱動作的稽核線索。

- 檢視及搜尋集中式記錄檔，而不需要 Docker 主機的遠端登入進行疑難排解。

- 尋找可能 「 吵雜的芳鄰 」，而且會耗用過多的資源，在主機上的容器。

- 集中式的 CPU、 記憶體、 儲存體和網路使用量和適用於容器的效能資訊檢視。

### <a name="additional-resources"></a>其他資源

- **Microsoft Azure 中的監視概觀**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **什麼是 Application Insights？**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **什麼是 Log Analytics？**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Azure 監視器中的容器監視解決方案**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Azure 監視器概觀**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **什麼是 Operations Management Suite (OMS)？**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

- **監視 Service Fabric 與 OMS 中的 Windows Server 容器**

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
>[上一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[下一頁](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
