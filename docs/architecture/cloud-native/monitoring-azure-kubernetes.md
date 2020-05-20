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
# <a name="monitoring-in-azure-kubernetes-services"></a><span data-ttu-id="79fca-103">在 Azure Kubernetes Service 中監視</span><span class="sxs-lookup"><span data-stu-id="79fca-103">Monitoring in Azure Kubernetes Services</span></span>

<span data-ttu-id="79fca-104">Kubernetes 中的內建記錄是基本的。</span><span class="sxs-lookup"><span data-stu-id="79fca-104">The built-in logging in Kubernetes is primitive.</span></span> <span data-ttu-id="79fca-105">不過，有一些絕佳的選項可讓您從 Kubernetes 中取得記錄檔，並放在適當的分析位置。</span><span class="sxs-lookup"><span data-stu-id="79fca-105">However, there are some great options for getting the logs out of Kubernetes and into a place where they can be properly analyzed.</span></span> <span data-ttu-id="79fca-106">如果您需要監視 AKS 叢集，設定 Kubernetes 的彈性堆疊是絕佳的解決方案。</span><span class="sxs-lookup"><span data-stu-id="79fca-106">If you need to monitor your AKS clusters, configuring Elastic Stack for Kubernetes is a great solution.</span></span>

## <a name="azure-monitor-for-containers"></a><span data-ttu-id="79fca-107">適用於容器的 Azure 監視器</span><span class="sxs-lookup"><span data-stu-id="79fca-107">Azure Monitor for Containers</span></span>

<span data-ttu-id="79fca-108">[適用于容器的 Azure 監視器](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)不僅支援從 Kubernetes 取用記錄，還可從 DC/OS、Docker Swarm 和 Red Hat OpenShift 等其他協調流程引擎使用。</span><span class="sxs-lookup"><span data-stu-id="79fca-108">[Azure Monitor for Containers](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview) supports consuming logs from not just Kubernetes but also from other orchestration engines such as DC/OS, Docker Swarm, and Red Hat OpenShift.</span></span>

<span data-ttu-id="79fca-109">![使用來自不同容器的記錄 ](./media/containers-diagram.png)
 **圖 7-10**。</span><span class="sxs-lookup"><span data-stu-id="79fca-109">![Consuming logs from various containers](./media/containers-diagram.png)
**Figure 7-10**.</span></span> <span data-ttu-id="79fca-110">使用來自不同容器的記錄</span><span class="sxs-lookup"><span data-stu-id="79fca-110">Consuming logs from various containers</span></span>

<span data-ttu-id="79fca-111">[Prometheus](https://prometheus.io/)是受歡迎的開放原始碼計量監視解決方案。</span><span class="sxs-lookup"><span data-stu-id="79fca-111">[Prometheus](https://prometheus.io/) is a popular open source metric monitoring solution.</span></span> <span data-ttu-id="79fca-112">它是雲端原生計算基礎的一部分。</span><span class="sxs-lookup"><span data-stu-id="79fca-112">It is part of the Cloud Native Compute Foundation.</span></span> <span data-ttu-id="79fca-113">一般來說，使用 Prometheus 時，必須使用自己的存放區來管理 Prometheus 伺服器。</span><span class="sxs-lookup"><span data-stu-id="79fca-113">Typically, using Prometheus requires managing a Prometheus server with its own store.</span></span> <span data-ttu-id="79fca-114">不過，[適用于容器的 Azure 監視器會提供與 Prometheus 計量端點的直接整合](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-prometheus-integration)，因此不需要個別的伺服器。</span><span class="sxs-lookup"><span data-stu-id="79fca-114">However, [Azure Monitor for Containers provides direct integration with Prometheus metrics endpoints](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-prometheus-integration), so a separate server is not required.</span></span>

<span data-ttu-id="79fca-115">記錄和計量資訊不只是從叢集中執行的容器，也是從叢集主機本身收集而來。</span><span class="sxs-lookup"><span data-stu-id="79fca-115">Log and metric information is gathered not just from the containers running in the cluster but also from the cluster hosts themselves.</span></span> <span data-ttu-id="79fca-116">它允許從兩者相互關聯記錄資訊，讓它更容易追蹤錯誤。</span><span class="sxs-lookup"><span data-stu-id="79fca-116">It allows correlating log information from the two making it much easier to track down an error.</span></span>

<span data-ttu-id="79fca-117">在[Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes)和[Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes)叢集上安裝記錄收集器會有所不同。</span><span class="sxs-lookup"><span data-stu-id="79fca-117">Installing the log collectors differs on [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) and [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) clusters.</span></span> <span data-ttu-id="79fca-118">但在這兩種情況下，記錄檔集合都會實作為 Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)，這表示記錄檔收集器會在每個節點上以容器的形式執行。</span><span class="sxs-lookup"><span data-stu-id="79fca-118">But in both cases the log collection is implemented as a Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), meaning that the log collector is run as a container on each of the nodes.</span></span>

<span data-ttu-id="79fca-119">無論哪個協調器或作業系統正在執行 Azure 監視器 daemon，記錄資訊都會轉送到與使用者熟悉的相同 Azure 監視器工具。</span><span class="sxs-lookup"><span data-stu-id="79fca-119">No matter which orchestrator or operating system is running the Azure Monitor daemon, the log information is forwarded to the same Azure Monitor tools with which users are familiar.</span></span> <span data-ttu-id="79fca-120">這可確保在混合不同記錄來源（例如混合式 Kubernetes/Azure Functions 環境）的環境中具有平行體驗。</span><span class="sxs-lookup"><span data-stu-id="79fca-120">This ensures a parallel experience in environments that mix different log sources such as a hybrid Kubernetes/Azure Functions environment.</span></span>

<span data-ttu-id="79fca-121">![範例儀表板，顯示來自數個執行中容器的記錄和度量資訊。 ](./media/containers-dashboard.png)
**圖 7-11**。</span><span class="sxs-lookup"><span data-stu-id="79fca-121">![A sample dashboard showing logging and metric information from a number of running containers.](./media/containers-dashboard.png)
**Figure 7-11**.</span></span> <span data-ttu-id="79fca-122">範例儀表板，顯示來自數個執行中容器的記錄和度量資訊。</span><span class="sxs-lookup"><span data-stu-id="79fca-122">A sample dashboard showing logging and metric information from a number of running containers.</span></span>

## <a name="logfinalize"></a><span data-ttu-id="79fca-123">Log. Finalize （）</span><span class="sxs-lookup"><span data-stu-id="79fca-123">Log.Finalize()</span></span>

<span data-ttu-id="79fca-124">記錄是大規模部署任何應用程式最常忽略且最重要的部分。</span><span class="sxs-lookup"><span data-stu-id="79fca-124">Logging is one of the most overlooked and yet most important parts of deploying any application at scale.</span></span> <span data-ttu-id="79fca-125">隨著應用程式的大小和複雜度增加，這也會讓您難以進行這項調試。</span><span class="sxs-lookup"><span data-stu-id="79fca-125">As the size and complexity of applications increase, then so does the difficulty of debugging them.</span></span> <span data-ttu-id="79fca-126">擁有最高品質記錄可讓您更輕鬆地進行調試，並將它從「幾乎不可能」的領域移到「愉快的體驗」。</span><span class="sxs-lookup"><span data-stu-id="79fca-126">Having top quality logs available makes debugging much easier and moves it from the realm of "nearly impossible" to "a pleasant experience".</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="79fca-127">[上一個](logging-with-elastic-stack.md) 
>[下一步](azure-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="79fca-127">[Previous](logging-with-elastic-stack.md)
[Next](azure-monitor.md)</span></span>
