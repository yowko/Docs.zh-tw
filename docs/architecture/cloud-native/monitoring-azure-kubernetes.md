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
# <a name="monitoring-in-azure-kubernetes-services"></a><span data-ttu-id="db0c0-103">在 Azure Kubernetes Services 中進行監視</span><span class="sxs-lookup"><span data-stu-id="db0c0-103">Monitoring in Azure Kubernetes Services</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="db0c0-104">Kubernetes 中的內建記錄是基本的。</span><span class="sxs-lookup"><span data-stu-id="db0c0-104">The built-in logging in Kubernetes is primitive.</span></span> <span data-ttu-id="db0c0-105">不過，有一些絕佳的選項可讓您從 Kubernetes 中取得記錄檔，並放在適當的分析位置。</span><span class="sxs-lookup"><span data-stu-id="db0c0-105">However, there are some great options for getting the logs out of Kubernetes and into a place where they can be properly analyzed.</span></span> <span data-ttu-id="db0c0-106">如果您需要監視 AKS 叢集，設定 Kubernetes 的彈性堆疊是絕佳的解決方案。</span><span class="sxs-lookup"><span data-stu-id="db0c0-106">If you need to monitor your AKS clusters, configuring Elastic Stack for Kubernetes is a great solution.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="db0c0-107">彈性堆疊</span><span class="sxs-lookup"><span data-stu-id="db0c0-107">Elastic Stack</span></span>

<span data-ttu-id="db0c0-108">彈性堆疊是一種功能強大的選項，可從 Kubernetes 叢集收集資訊。</span><span class="sxs-lookup"><span data-stu-id="db0c0-108">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="db0c0-109">Kubernetes 支援將記錄傳送至 Elasticsearch 端點，而在[大部分的情況](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)下，您只需要設定環境變數，如圖7-5 所示：</span><span class="sxs-lookup"><span data-stu-id="db0c0-109">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="db0c0-110">**圖 7-5** -Kubernetes 的設定變數</span><span class="sxs-lookup"><span data-stu-id="db0c0-110">**Figure 7-5** - Configuration variables for Kubernetes</span></span>

<span data-ttu-id="db0c0-111">這會在叢集上安裝 Elasticsearch，並將所有叢集記錄檔傳送至該叢集。</span><span class="sxs-lookup"><span data-stu-id="db0c0-111">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="db0c0-112">![Kibana 儀表板的範例，其中顯示針對從 Kubernetes](./media/kibana-dashboard.png)
**圖 7-6**內嵌的記錄進行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="db0c0-112">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="db0c0-113">Kibana 儀表板的範例，其中顯示針對內嵌自 Kubernetes 的記錄進行查詢的結果</span><span class="sxs-lookup"><span data-stu-id="db0c0-113">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="azure-container-monitoring"></a><span data-ttu-id="db0c0-114">Azure 容器監視</span><span class="sxs-lookup"><span data-stu-id="db0c0-114">Azure Container Monitoring</span></span>

<span data-ttu-id="db0c0-115">Azure 容器監視不僅支援從 Kubernetes 取用記錄，還能從其他協調流程引擎（例如 DC/OS、Docker Swarm 和 Red Hat OpenShift）使用。</span><span class="sxs-lookup"><span data-stu-id="db0c0-115">Azure Container Monitoring supports consuming logs from not just Kubernetes but also from other orchestration engines such as DC/OS, Docker Swarm, and Red Hat OpenShift.</span></span>

<span data-ttu-id="db0c0-116">![使用來自不同容器](./media/containers-diagram.png)
的記錄**圖 7-7**。</span><span class="sxs-lookup"><span data-stu-id="db0c0-116">![Consuming logs from various containers](./media/containers-diagram.png)
**Figure 7-7**.</span></span>  <span data-ttu-id="db0c0-117">使用來自不同容器的記錄</span><span class="sxs-lookup"><span data-stu-id="db0c0-117">Consuming logs from various containers</span></span>

<span data-ttu-id="db0c0-118">記錄和計量資訊不只是從叢集中執行的容器，也是從叢集主機本身收集而來。</span><span class="sxs-lookup"><span data-stu-id="db0c0-118">Log and metric information is gathered not just from the containers running in the cluster but also from the cluster hosts themselves.</span></span> <span data-ttu-id="db0c0-119">它允許從兩者相互關聯記錄資訊，讓它更容易追蹤錯誤。</span><span class="sxs-lookup"><span data-stu-id="db0c0-119">It allows correlating log information from the two making it much easier to track down an error.</span></span>

<span data-ttu-id="db0c0-120">在[Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes)和[Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes)叢集上安裝記錄收集器會有所不同。</span><span class="sxs-lookup"><span data-stu-id="db0c0-120">Installing the log collectors differs on [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) and [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) clusters.</span></span> <span data-ttu-id="db0c0-121">但在這兩種情況下，記錄檔集合都會實作為 Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)，這表示記錄檔收集器會在每個節點上以容器的形式執行。</span><span class="sxs-lookup"><span data-stu-id="db0c0-121">But in both cases the log collection is implemented as a Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), meaning that the log collector is run as a container on each of the nodes.</span></span>

<span data-ttu-id="db0c0-122">無論哪個協調器或作業系統正在執行 Azure 監視器 daemon，記錄資訊都會轉送到與使用者熟悉的相同 Azure 監視器工具。</span><span class="sxs-lookup"><span data-stu-id="db0c0-122">No matter which orchestrator or operating system is running the Azure Monitor daemon, the log information is forwarded to the same Azure Monitor tools with which users are familiar.</span></span> <span data-ttu-id="db0c0-123">這可確保在混合不同記錄來源（例如混合式 Kubernetes/Azure Functions 環境）的環境中具有平行體驗。</span><span class="sxs-lookup"><span data-stu-id="db0c0-123">This ensures a parallel experience in environments that mix different log sources such as a hybrid Kubernetes/Azure Functions environment.</span></span>

<span data-ttu-id="db0c0-124">![範例儀表板，顯示來自數個執行中容器的記錄和度量資訊。**圖 7-8**。 ](./media/containers-dashboard.png)
</span><span class="sxs-lookup"><span data-stu-id="db0c0-124">![A sample dashboard showing logging and metric information from a number of running containers.](./media/containers-dashboard.png)
**Figure 7-8**.</span></span> <span data-ttu-id="db0c0-125">範例儀表板，顯示來自數個執行中容器的記錄和度量資訊。</span><span class="sxs-lookup"><span data-stu-id="db0c0-125">A sample dashboard showing logging and metric information from a number of running containers.</span></span>

## <a name="logfinalize"></a><span data-ttu-id="db0c0-126">Log. Finalize （）</span><span class="sxs-lookup"><span data-stu-id="db0c0-126">Log.Finalize()</span></span>

<span data-ttu-id="db0c0-127">記錄是大規模部署任何應用程式最常忽略且最重要的部分。</span><span class="sxs-lookup"><span data-stu-id="db0c0-127">Logging is one of the most overlooked and yet most important parts of deploying any application at scale.</span></span> <span data-ttu-id="db0c0-128">隨著應用程式的大小和複雜度增加，這也會讓您難以進行這項調試。</span><span class="sxs-lookup"><span data-stu-id="db0c0-128">As the size and complexity of applications increase, then so does the difficulty of debugging them.</span></span> <span data-ttu-id="db0c0-129">擁有最高品質記錄可讓您更輕鬆地進行調試，並將它從「幾乎不可能」的領域移到「愉快的體驗」。</span><span class="sxs-lookup"><span data-stu-id="db0c0-129">Having top quality logs available makes debugging much easier and moves it from the realm of "nearly impossible" to "a pleasant experience".</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="db0c0-130">[上一頁](logging-with-elastic-stack.md)
>[下一頁](azure-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="db0c0-130">[Previous](logging-with-elastic-stack.md)
[Next](azure-monitor.md)</span></span>
