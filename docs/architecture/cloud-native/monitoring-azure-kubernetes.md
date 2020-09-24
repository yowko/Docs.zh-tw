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
# <a name="monitoring-in-azure-kubernetes-services"></a><span data-ttu-id="848eb-103">在 Azure Kubernetes Service 中監視</span><span class="sxs-lookup"><span data-stu-id="848eb-103">Monitoring in Azure Kubernetes Services</span></span>

<span data-ttu-id="848eb-104">內建的 Kubernetes 記錄是基本的。</span><span class="sxs-lookup"><span data-stu-id="848eb-104">The built-in logging in Kubernetes is primitive.</span></span> <span data-ttu-id="848eb-105">不過，有一些絕佳的選項可讓您從 Kubernetes 中取得記錄，並放入適當的分析。</span><span class="sxs-lookup"><span data-stu-id="848eb-105">However, there are some great options for getting the logs out of Kubernetes and into a place where they can be properly analyzed.</span></span> <span data-ttu-id="848eb-106">如果您需要監視 AKS 叢集，設定 Kubernetes 的彈性堆疊是絕佳的解決方案。</span><span class="sxs-lookup"><span data-stu-id="848eb-106">If you need to monitor your AKS clusters, configuring Elastic Stack for Kubernetes is a great solution.</span></span>

## <a name="azure-monitor-for-containers"></a><span data-ttu-id="848eb-107">適用於容器的 Azure 監視器</span><span class="sxs-lookup"><span data-stu-id="848eb-107">Azure Monitor for Containers</span></span>

<span data-ttu-id="848eb-108">[容器的 Azure 監視器](/azure/azure-monitor/insights/container-insights-overview) 不僅支援取用 Kubernetes，也支援從其他協調流程引擎（例如 DC/OS、Docker Swarm 和 Red Hat OpenShift）使用記錄。</span><span class="sxs-lookup"><span data-stu-id="848eb-108">[Azure Monitor for Containers](/azure/azure-monitor/insights/container-insights-overview) supports consuming logs from not just Kubernetes but also from other orchestration engines such as DC/OS, Docker Swarm, and Red Hat OpenShift.</span></span>

<span data-ttu-id="848eb-109">![使用來自各種容器的記錄 ](./media/containers-diagram.png)
 **圖 7-10**。</span><span class="sxs-lookup"><span data-stu-id="848eb-109">![Consuming logs from various containers](./media/containers-diagram.png)
**Figure 7-10**.</span></span> <span data-ttu-id="848eb-110">使用來自各種容器的記錄</span><span class="sxs-lookup"><span data-stu-id="848eb-110">Consuming logs from various containers</span></span>

<span data-ttu-id="848eb-111">[Prometheus](https://prometheus.io/) 是受歡迎的開放原始碼計量監視解決方案。</span><span class="sxs-lookup"><span data-stu-id="848eb-111">[Prometheus](https://prometheus.io/) is a popular open source metric monitoring solution.</span></span> <span data-ttu-id="848eb-112">它是雲端原生計算基礎的一部分。</span><span class="sxs-lookup"><span data-stu-id="848eb-112">It is part of the Cloud Native Compute Foundation.</span></span> <span data-ttu-id="848eb-113">一般來說，使用 Prometheus 需要使用自己的存放區來管理 Prometheus 伺服器。</span><span class="sxs-lookup"><span data-stu-id="848eb-113">Typically, using Prometheus requires managing a Prometheus server with its own store.</span></span> <span data-ttu-id="848eb-114">不過， [容器的 Azure 監視器提供與 Prometheus 計量端點的直接整合](/azure/azure-monitor/insights/container-insights-prometheus-integration)，因此不需要個別的伺服器。</span><span class="sxs-lookup"><span data-stu-id="848eb-114">However, [Azure Monitor for Containers provides direct integration with Prometheus metrics endpoints](/azure/azure-monitor/insights/container-insights-prometheus-integration), so a separate server is not required.</span></span>

<span data-ttu-id="848eb-115">記錄和計量資訊不只是從叢集中執行的容器進行收集，也會從叢集主機本身進行收集。</span><span class="sxs-lookup"><span data-stu-id="848eb-115">Log and metric information is gathered not just from the containers running in the cluster but also from the cluster hosts themselves.</span></span> <span data-ttu-id="848eb-116">它可讓兩個記錄資訊相互關聯，讓追蹤錯誤變得更容易。</span><span class="sxs-lookup"><span data-stu-id="848eb-116">It allows correlating log information from the two making it much easier to track down an error.</span></span>

<span data-ttu-id="848eb-117">在 [Windows](/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) 和 [Linux](/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) 叢集上安裝記錄檔收集器會有所不同。</span><span class="sxs-lookup"><span data-stu-id="848eb-117">Installing the log collectors differs on [Windows](/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) and [Linux](/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) clusters.</span></span> <span data-ttu-id="848eb-118">但在這兩種情況下，記錄收集會實作為 Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)，這表示記錄檔收集器會在每個節點上以容器的形式執行。</span><span class="sxs-lookup"><span data-stu-id="848eb-118">But in both cases the log collection is implemented as a Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), meaning that the log collector is run as a container on each of the nodes.</span></span>

<span data-ttu-id="848eb-119">無論哪個 orchestrator 或作業系統正在執行 Azure 監視器 daemon，記錄資訊都會轉送至與使用者熟悉的相同 Azure 監視器工具。</span><span class="sxs-lookup"><span data-stu-id="848eb-119">No matter which orchestrator or operating system is running the Azure Monitor daemon, the log information is forwarded to the same Azure Monitor tools with which users are familiar.</span></span> <span data-ttu-id="848eb-120">這可確保混合不同記錄檔來源的環境（例如混合式 Kubernetes/Azure Functions 環境）有平行體驗。</span><span class="sxs-lookup"><span data-stu-id="848eb-120">This ensures a parallel experience in environments that mix different log sources such as a hybrid Kubernetes/Azure Functions environment.</span></span>

<span data-ttu-id="848eb-121">![顯示記錄和計量資訊的儀表板範例，來自多個執行中的容器。 ](./media/containers-dashboard.png)
**圖 7-11**。</span><span class="sxs-lookup"><span data-stu-id="848eb-121">![A sample dashboard showing logging and metric information from a number of running containers.](./media/containers-dashboard.png)
**Figure 7-11**.</span></span> <span data-ttu-id="848eb-122">顯示記錄和計量資訊的儀表板範例，來自多個執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="848eb-122">A sample dashboard showing logging and metric information from a number of running containers.</span></span>

## <a name="logfinalize"></a><span data-ttu-id="848eb-123">Log. Finalize ( # A1</span><span class="sxs-lookup"><span data-stu-id="848eb-123">Log.Finalize()</span></span>

<span data-ttu-id="848eb-124">記錄是大規模部署任何應用程式最常被忽略和最重要的部分。</span><span class="sxs-lookup"><span data-stu-id="848eb-124">Logging is one of the most overlooked and yet most important parts of deploying any application at scale.</span></span> <span data-ttu-id="848eb-125">當應用程式的大小和複雜度增加時，就會難以進行調試。</span><span class="sxs-lookup"><span data-stu-id="848eb-125">As the size and complexity of applications increase, then so does the difficulty of debugging them.</span></span> <span data-ttu-id="848eb-126">擁有高品質記錄可讓您更輕鬆地進行偵錯工具，並將它從「幾乎不可能」的領域移至「愉快的體驗」。</span><span class="sxs-lookup"><span data-stu-id="848eb-126">Having top quality logs available makes debugging much easier and moves it from the realm of "nearly impossible" to "a pleasant experience".</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="848eb-127">[上一個](logging-with-elastic-stack.md) 
>[下一步](azure-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="848eb-127">[Previous](logging-with-elastic-stack.md)
[Next](azure-monitor.md)</span></span>
