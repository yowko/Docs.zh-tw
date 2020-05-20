---
title: 在 Azure Kubernetes Service 中監視
description: 在 Azure Kubernetes Service 中監視
ms.date: 05/13/2020
ms.openlocfilehash: 138acf9d27fb4a676ec422c848097a6bea98fa42
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613820"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>在 Azure Kubernetes Service 中監視

Kubernetes 中的內建記錄是基本的。 不過，有一些絕佳的選項可讓您從 Kubernetes 中取得記錄檔，並放在適當的分析位置。 如果您需要監視 AKS 叢集，設定 Kubernetes 的彈性堆疊是絕佳的解決方案。

## <a name="azure-monitor-for-containers"></a>適用於容器的 Azure 監視器

[適用于容器的 Azure 監視器](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)不僅支援從 Kubernetes 取用記錄，還可從 DC/OS、Docker Swarm 和 Red Hat OpenShift 等其他協調流程引擎使用。

![使用來自不同容器的記錄 ](./media/containers-diagram.png)
 **圖 7-10**。 使用來自不同容器的記錄

[Prometheus](https://prometheus.io/)是受歡迎的開放原始碼計量監視解決方案。 它是雲端原生計算基礎的一部分。 一般來說，使用 Prometheus 時，必須使用自己的存放區來管理 Prometheus 伺服器。 不過，[適用于容器的 Azure 監視器會提供與 Prometheus 計量端點的直接整合](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-prometheus-integration)，因此不需要個別的伺服器。

記錄和計量資訊不只是從叢集中執行的容器，也是從叢集主機本身收集而來。 它允許從兩者相互關聯記錄資訊，讓它更容易追蹤錯誤。

在[Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes)和[Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes)叢集上安裝記錄收集器會有所不同。 但在這兩種情況下，記錄檔集合都會實作為 Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)，這表示記錄檔收集器會在每個節點上以容器的形式執行。

無論哪個協調器或作業系統正在執行 Azure 監視器 daemon，記錄資訊都會轉送到與使用者熟悉的相同 Azure 監視器工具。 這可確保在混合不同記錄來源（例如混合式 Kubernetes/Azure Functions 環境）的環境中具有平行體驗。

![範例儀表板，顯示來自數個執行中容器的記錄和度量資訊。 ](./media/containers-dashboard.png)
**圖 7-11**。 範例儀表板，顯示來自數個執行中容器的記錄和度量資訊。

## <a name="logfinalize"></a>Log. Finalize （）

記錄是大規模部署任何應用程式最常忽略且最重要的部分。 隨著應用程式的大小和複雜度增加，這也會讓您難以進行這項調試。 擁有最高品質記錄可讓您更輕鬆地進行調試，並將它從「幾乎不可能」的領域移到「愉快的體驗」。

>[!div class="step-by-step"]
>[上一個](logging-with-elastic-stack.md) 
>[下一步](azure-monitor.md)
