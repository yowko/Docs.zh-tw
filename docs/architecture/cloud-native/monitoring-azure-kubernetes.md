---
title: 在 Azure Kubernetes Services 中進行監視
description: 在 Azure Kubernetes Services 中進行監視
ms.date: 09/23/2019
ms.openlocfilehash: 71192601eac2169db188b25da3dc91b71b860903
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184985"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>在 Azure Kubernetes Services 中進行監視

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kubernetes 中的內建記錄是基本的。 不過，有一些絕佳的選項可讓您從 Kubernetes 中取得記錄檔，並放在適當的分析位置。 如果您需要監視 AKS 叢集，設定 Kubernetes 的彈性堆疊是絕佳的解決方案。

## <a name="elastic-stack"></a>彈性堆疊

彈性堆疊是一種功能強大的選項，可從 Kubernetes 叢集收集資訊。 Kubernetes 支援將記錄傳送至 Elasticsearch 端點，而在[大部分的情況](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)下，您只需要設定環境變數，如圖7-5 所示：

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**圖 7-5** -Kubernetes 的設定變數

這會在叢集上安裝 Elasticsearch，並將所有叢集記錄檔傳送至該叢集。

![Kibana 儀表板的範例，其中顯示針對從 Kubernetes](./media/kibana-dashboard.png)
**圖 7-6**內嵌的記錄進行查詢的結果。 Kibana 儀表板的範例，其中顯示針對內嵌自 Kubernetes 的記錄進行查詢的結果

## <a name="azure-container-monitoring"></a>Azure 容器監視

Azure 容器監視不僅支援從 Kubernetes 取用記錄，還能從其他協調流程引擎（例如 DC/OS、Docker Swarm 和 Red Hat OpenShift）使用。

![使用來自不同容器](./media/containers-diagram.png)
的記錄**圖 7-7**。  使用來自不同容器的記錄

記錄和計量資訊不只是從叢集中執行的容器，也是從叢集主機本身收集而來。 它允許從兩者相互關聯記錄資訊，讓它更容易追蹤錯誤。

在[Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes)和[Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes)叢集上安裝記錄收集器會有所不同。 但在這兩種情況下，記錄檔集合都會實作為 Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)，這表示記錄檔收集器會在每個節點上以容器的形式執行。

無論哪個協調器或作業系統正在執行 Azure 監視器 daemon，記錄資訊都會轉送到與使用者熟悉的相同 Azure 監視器工具。 這可確保在混合不同記錄來源（例如混合式 Kubernetes/Azure Functions 環境）的環境中具有平行體驗。

![範例儀表板，顯示來自數個執行中容器的記錄和度量資訊。**圖 7-8**。 ](./media/containers-dashboard.png)
 範例儀表板，顯示來自數個執行中容器的記錄和度量資訊。

## <a name="logfinalize"></a>Log. Finalize （）

記錄是大規模部署任何應用程式最常忽略且最重要的部分。 隨著應用程式的大小和複雜度增加，這也會讓您難以進行這項調試。 擁有最高品質記錄可讓您更輕鬆地進行調試，並將它從「幾乎不可能」的領域移到「愉快的體驗」。

>[!div class="step-by-step"]
>[上一頁](logging-with-elastic-stack.md)
>[下一頁](azure-monitor.md)
