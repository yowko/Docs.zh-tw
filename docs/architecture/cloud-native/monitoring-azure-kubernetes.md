---
title: 在 Azure Kubernetes Service 中監視
description: 在 Azure Kubernetes Service 中監視
ms.date: 05/13/2020
ms.openlocfilehash: 3900f169b9be4f807e72392da38a1224d6ce28e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163696"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>在 Azure Kubernetes Service 中監視

內建的 Kubernetes 記錄是基本的。 不過，有一些絕佳的選項可讓您從 Kubernetes 中取得記錄，並放入適當的分析。 如果您需要監視 AKS 叢集，設定 Kubernetes 的彈性堆疊是絕佳的解決方案。

## <a name="azure-monitor-for-containers"></a>適用於容器的 Azure 監視器

[容器的 Azure 監視器](/azure/azure-monitor/insights/container-insights-overview) 不僅支援取用 Kubernetes，也支援從其他協調流程引擎（例如 DC/OS、Docker Swarm 和 Red Hat OpenShift）使用記錄。

![使用來自各種容器的記錄 ](./media/containers-diagram.png)
 **圖 7-10**。 使用來自各種容器的記錄

[Prometheus](https://prometheus.io/) 是受歡迎的開放原始碼計量監視解決方案。 它是雲端原生計算基礎的一部分。 一般來說，使用 Prometheus 需要使用自己的存放區來管理 Prometheus 伺服器。 不過， [容器的 Azure 監視器提供與 Prometheus 計量端點的直接整合](/azure/azure-monitor/insights/container-insights-prometheus-integration)，因此不需要個別的伺服器。

記錄和計量資訊不只是從叢集中執行的容器進行收集，也會從叢集主機本身進行收集。 它可讓兩個記錄資訊相互關聯，讓追蹤錯誤變得更容易。

在 [Windows](/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) 和 [Linux](/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) 叢集上安裝記錄檔收集器會有所不同。 但在這兩種情況下，記錄收集會實作為 Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)，這表示記錄檔收集器會在每個節點上以容器的形式執行。

無論哪個 orchestrator 或作業系統正在執行 Azure 監視器 daemon，記錄資訊都會轉送至與使用者熟悉的相同 Azure 監視器工具。 這可確保混合不同記錄檔來源的環境（例如混合式 Kubernetes/Azure Functions 環境）有平行體驗。

![顯示記錄和計量資訊的儀表板範例，來自多個執行中的容器。 ](./media/containers-dashboard.png)
**圖 7-11**。 顯示記錄和計量資訊的儀表板範例，來自多個執行中的容器。

## <a name="logfinalize"></a>Log. Finalize ( # A1

記錄是大規模部署任何應用程式最常被忽略和最重要的部分。 當應用程式的大小和複雜度增加時，就會難以進行調試。 擁有高品質記錄可讓您更輕鬆地進行偵錯工具，並將它從「幾乎不可能」的領域移至「愉快的體驗」。

>[!div class="step-by-step"]
>[上一個](logging-with-elastic-stack.md) 
>[下一步](azure-monitor.md)
