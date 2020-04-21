---
title: 使用監視和遙測將應用程式現代化
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |通過監視和遙測實現應用現代化
ms.date: 04/30/2018
ms.openlocfilehash: a5101f150d6548406db8638904fb4ab6375edf9c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739173"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>使用監視和遙測將應用程式現代化

在生產中運行應用程式時,瞭解應用程式的性能至關重要。 性能是否較高? 使用者是否收到錯誤,或者應用程式是否穩定可靠? 您需要豐富的性能監視、強大的警報和儀錶板,以幫助確保應用程式可用並按預期運行。 您還需要能夠快速查看是否存在問題,確定受影響的客戶數,並執行根本原因分析以查找和解決問題。

## <a name="monitor-your-application-with-application-insights"></a>使用應用程式見解監控應用程式

應用程式見解是一種可擴充的應用程式效能管理 (APM) 服務,適用於在多個平臺上工作的 Web 開發人員。 您可以使用它來監視即時 Web 應用程式。 應用程式見解可自動檢測性能異常。 它包括強大的分析工具,可説明您診斷問題,並説明您瞭解使用者實際使用你的應用做什麼。 Application Insights 設計用來協助您持續改善效能和可用性。 它適用於各種平臺上的應用,包括 .NET、Node.js 和 J2EE,無論是本地託管還是雲端中託管。 應用程式見解與您的 DevOps 流程整合,並具有與各種開發工具的連接點。

圖 4-10 顯示了應用程式見解如何監視應用程式以及如何將這些見解顯示到儀錶板的示例。

![應用程式見解監視儀錶板的螢幕截圖。](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**圖 4-10。** 應用程式洞察監控儀表板

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>使用紀錄分析及其容器監視解決方案監視 Docker 基礎結構

[Azure 日誌分析](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)是[Microsoft Azure整體監視解決方案](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)的一部分。 這也是[運營管理套件 (OMS) 中的](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)服務。 日誌分析監控雲和本地環境(用於本地的 OMS),以幫助維護可用性和性能。 它會收集您的雲端和內部部署環境中的資源所產生的資料，以及從其他監視工具提供橫跨多個來源的分析。

相對於 Azure 基礎結構日誌,日誌分析作為 Azure 服務,從其他 Azure 服務(透過[Azure 監視器](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))、Azure VM、Docker 容器以及本地或其他雲端基礎結構引入日誌和指標數據。 日誌分析提供靈活的日誌搜索和開箱即用的分析。 它提供了豐富的工具,可用於分析跨源的數據,它允許跨所有日誌進行複雜的查詢,並且它可以根據指定條件主動發出警報。 您甚至可以在中央日誌分析儲存庫中收集自定義數據,您可以在其中查詢和可視化這些數據。 您還可以利用日誌分析內置解決方案,立即深入瞭解基礎架構的安全性和功能。

您可以通過 OMS 門戶或在任何瀏覽器中執行的 Azure 門戶訪問日誌分析,並為您提供對配置設置和多個工具的訪問許可權,以分析和處理收集的數據。

日誌分析中的[容器監視解決方案](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)可説明您在單個位置查看和管理 Docker 和 Windows 容器主機。 該解決方案顯示正在運行的容器、正在運行的容器映射以及容器的運行位置。 您可以查看詳細的審核資訊,包括與容器一起使用的命令。 您還可以透過查看和搜索集中式日誌來對容器進行故障排除,而無需遠端查看 Docker 或 Windows 主機。 您可以找到可能嘈雜的容器,並在主機上消耗多餘的資源。 此外,您還可以查看容器的集中式 CPU、記憶體、儲存和網路使用方式以及性能資訊。 您可以在執行 Windows 的電腦上集中管理，並從 Windows Server、HYPER-V 和 Docker 容器比較記錄。 解決方案支援下列容器協調者：

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

圖 4-11 顯示了各種容器主機和代理與 OMS 之間的關係。

![日誌分析容器監視解決方案的螢幕截圖。](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**圖 4-11。** 紀錄分析容器監視解決方案

您可以使用紀錄分析容器監視解決方案:

- 查看有關單個位置中所有容器主機的資訊。

- 瞭解正在運行的容器、正在運行的映射以及它們運行的位置。

- 有關容器上的操作,請參閱審核跟蹤。

- 通過查看和搜索集中式日誌進行故障排除,而無需遠端登錄到 Docker 主機。

- 查找可能是"嘈雜鄰居"的容器,並在主機上消耗多餘的資源。

- 查看容器的集中式 CPU、記憶體、儲存和網路使用方式以及性能資訊。

### <a name="additional-resources"></a>其他資源

- **微軟 Azure 中的監視概述**

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
>[前一個](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[下一個](life-cycle-ci-cd-pipelines-devops-tools.md)
