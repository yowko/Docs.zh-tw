---
title: 調整容器和無伺服器應用程式的規模
description: 使用 Azure Kubernetes Service 調整雲端原生應用程式，以滿足使用者需求。
ms.date: 04/13/2020
ms.openlocfilehash: b4580e6994611ad394bbaa2d5bb07f64c2798569
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199920"
---
# <a name="scaling-containers-and-serverless-applications"></a><span data-ttu-id="33bba-103">調整容器和無伺服器應用程式的規模</span><span class="sxs-lookup"><span data-stu-id="33bba-103">Scaling containers and serverless applications</span></span>

<span data-ttu-id="33bba-104">有兩種方式可以調整應用程式：向上或向外。前者是指將容量新增至單一資源，而後者則是指新增更多資源以增加容量。</span><span class="sxs-lookup"><span data-stu-id="33bba-104">There are two ways to scale an application: up or out. The former refers to adding capacity to a single resource, while the latter refers to adding more resources to increase capacity.</span></span>

## <a name="the-simple-solution-scaling-up"></a><span data-ttu-id="33bba-105">簡單的解決方案：向上延展</span><span class="sxs-lookup"><span data-stu-id="33bba-105">The simple solution: scaling up</span></span>

<span data-ttu-id="33bba-106">升級具有增加的 CPU、記憶體、磁片 i/o 速度和網路 i/o 速度的現有主機伺服器，也稱為相應*增加*。</span><span class="sxs-lookup"><span data-stu-id="33bba-106">Upgrading an existing host server with increased CPU, memory, disk I/O speed, and network I/O speed is known as *scaling up*.</span></span> <span data-ttu-id="33bba-107">相應增加雲端原生應用程式包含從雲端廠商選擇更強大的資源。</span><span class="sxs-lookup"><span data-stu-id="33bba-107">Scaling up a cloud-native application involves choosing more capable resources from the cloud vendor.</span></span> <span data-ttu-id="33bba-108">例如，您可以在 Kubernetes 叢集中具有較大 Vm 的新節點集區。</span><span class="sxs-lookup"><span data-stu-id="33bba-108">For example, you can a new node pool with larger VMs in your Kubernetes cluster.</span></span> <span data-ttu-id="33bba-109">然後，將您的容器化服務遷移至新的集區。</span><span class="sxs-lookup"><span data-stu-id="33bba-109">Then, migrate your containerized services to the new pool.</span></span>

<span data-ttu-id="33bba-110">無伺服器應用程式：從專用的 app service 方案選擇高階[函數計畫](https://docs.microsoft.com/azure/azure-functions/functions-scale)或高階實例大小，以相應增加規模。</span><span class="sxs-lookup"><span data-stu-id="33bba-110">Serverless apps scale up by choosing the [premium Functions plan](https://docs.microsoft.com/azure/azure-functions/functions-scale) or premium instance sizes from a dedicated app service plan.</span></span>

## <a name="scaling-out-cloud-native-apps"></a><span data-ttu-id="33bba-111">相應放大雲端原生應用程式</span><span class="sxs-lookup"><span data-stu-id="33bba-111">Scaling out cloud-native apps</span></span>

<span data-ttu-id="33bba-112">雲端原生應用程式通常會遇到大量的需求波動，而且需要一段時間才能進行調整。</span><span class="sxs-lookup"><span data-stu-id="33bba-112">Cloud-native applications often experience large fluctuations in demand and require scale on a moment's notice.</span></span> <span data-ttu-id="33bba-113">它們偏好相應放大。向外延展會藉由將其他電腦（稱為節點）或應用程式實例新增至現有的叢集來進行水準調整。</span><span class="sxs-lookup"><span data-stu-id="33bba-113">They favor scaling out. Scaling out is done horizontally by adding additional machines (called nodes) or application instances to an existing cluster.</span></span> <span data-ttu-id="33bba-114">在 Kubernetes 中，您可以藉由調整應用程式的設定（例如，調整[節點集](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)區）或透過自動調整來手動調整。</span><span class="sxs-lookup"><span data-stu-id="33bba-114">In Kubernetes, you can scale manually by adjusting configuration settings for the app (for example, [scaling a node pool](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)), or through autoscaling.</span></span>

<span data-ttu-id="33bba-115">AKS 叢集可以透過下列兩種方式的其中一種進行自動調整：</span><span class="sxs-lookup"><span data-stu-id="33bba-115">AKS clusters can autoscale in one of two ways:</span></span>

<span data-ttu-id="33bba-116">首先，[水準 Pod 自動調整程式](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale#autoscale-pods)會監視資源需求，並自動調整您的 Pod 複本以符合它。</span><span class="sxs-lookup"><span data-stu-id="33bba-116">First, the [Horizontal Pod Autoscaler](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale#autoscale-pods) monitors resource demand and automatically scales your POD replicas to meet it.</span></span> <span data-ttu-id="33bba-117">當流量增加時，會自動布建額外的複本，以相應放大您的服務。</span><span class="sxs-lookup"><span data-stu-id="33bba-117">When traffic increases, additional replicas are automatically provisioned to scale out your services.</span></span> <span data-ttu-id="33bba-118">同樣地，當需求降低時，就會將它們移除以相應縮小您的服務。</span><span class="sxs-lookup"><span data-stu-id="33bba-118">Likewise, when demand decreases, they're removed to scale-in your services.</span></span> <span data-ttu-id="33bba-119">您可以定義要調整的度量，例如 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="33bba-119">You define the metric on which to scale, for example, CPU usage.</span></span> <span data-ttu-id="33bba-120">您也可以指定要執行之複本的最小和最大數目。</span><span class="sxs-lookup"><span data-stu-id="33bba-120">You can also specify the minimum and maximum number of replicas to run.</span></span> <span data-ttu-id="33bba-121">AKS 會監視該度量，並據以調整。</span><span class="sxs-lookup"><span data-stu-id="33bba-121">AKS monitors that metric and scales accordingly.</span></span>

<span data-ttu-id="33bba-122">接下來， [AKS 叢集自動調整程式](https://docs.microsoft.com/azure/aks/cluster-autoscaler)功能可讓您自動調整跨 Kubernetes 叢集的計算節點，以符合需求。</span><span class="sxs-lookup"><span data-stu-id="33bba-122">Next, the [AKS Cluster Autoscaler](https://docs.microsoft.com/azure/aks/cluster-autoscaler) feature enables you to automatically scale compute nodes across a Kubernetes cluster to meet demand.</span></span> <span data-ttu-id="33bba-123">有了此功能，您就可以在需要更多的計算容量時，自動將新的 Vm 新增至基礎的 Azure 虛擬機器擴展集。</span><span class="sxs-lookup"><span data-stu-id="33bba-123">With it, you can automatically add new VMs to the underlying Azure Virtual Machine Scale Set whenever more compute capacity of is required.</span></span> <span data-ttu-id="33bba-124">它也會在不再需要時移除節點。</span><span class="sxs-lookup"><span data-stu-id="33bba-124">It also removes nodes when no longer required.</span></span>

<span data-ttu-id="33bba-125">圖3-13 顯示這兩個調整服務之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="33bba-125">Figure 3-13 shows the relationship between these two scaling services.</span></span>

![相應放大 App Service 計畫。](./media/aks-cluster-autoscaler.png)

<span data-ttu-id="33bba-127">**圖 3-13**。</span><span class="sxs-lookup"><span data-stu-id="33bba-127">**Figure 3-13**.</span></span> <span data-ttu-id="33bba-128">相應放大 App Service 計畫。</span><span class="sxs-lookup"><span data-stu-id="33bba-128">Scaling out an App Service plan.</span></span>

<span data-ttu-id="33bba-129">共同作業可確保容器實例和計算節點的最佳數目，以支援變動的需求。</span><span class="sxs-lookup"><span data-stu-id="33bba-129">Working together, both ensure an optimal number of container instances and compute nodes to support fluctuating demand.</span></span> <span data-ttu-id="33bba-130">水準 pod 自動調整程式會優化所需的 pod 數目。</span><span class="sxs-lookup"><span data-stu-id="33bba-130">The horizontal pod autoscaler optimizes the number of pods required.</span></span> <span data-ttu-id="33bba-131">叢集自動調整程式會優化所需的節點數目。</span><span class="sxs-lookup"><span data-stu-id="33bba-131">The cluster autoscaler optimizes the number of nodes required.</span></span>

### <a name="scaling-azure-functions"></a><span data-ttu-id="33bba-132">調整 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="33bba-132">Scaling Azure Functions</span></span>

<span data-ttu-id="33bba-133">Azure Functions 視需要自動相應放大。</span><span class="sxs-lookup"><span data-stu-id="33bba-133">Azure Functions automatically scale out upon demand.</span></span> <span data-ttu-id="33bba-134">系統會根據觸發事件的數目，動態配置和移除伺服器資源。</span><span class="sxs-lookup"><span data-stu-id="33bba-134">Server resources are dynamically allocated and removed based on the number of triggered events.</span></span> <span data-ttu-id="33bba-135">您只需支付函式執行時所耗用的計算資源費用。</span><span class="sxs-lookup"><span data-stu-id="33bba-135">You're only charged for compute resources consumed when your functions run.</span></span> <span data-ttu-id="33bba-136">計費是根據執行次數、執行時間和使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="33bba-136">Billing is based upon the number of executions, execution time, and memory used.</span></span>

<span data-ttu-id="33bba-137">雖然預設取用方案為大部分應用程式提供經濟實惠且可調整的解決方案，但 premium 選項可讓開發人員彈性自訂 Azure Functions 需求。</span><span class="sxs-lookup"><span data-stu-id="33bba-137">While the default consumption plan provides an economical and scalable solution for most apps, the premium option allows developers flexibility for custom Azure Functions requirements.</span></span> <span data-ttu-id="33bba-138">升級至 premium 方案可讓您控制實例大小、預先準備就緒的實例（以避免冷啟動延遲）和專用 Vm。</span><span class="sxs-lookup"><span data-stu-id="33bba-138">Upgrading to the premium plan provides control over instance sizes, pre-warmed instances (to avoid cold start delays), and dedicated VMs.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="33bba-139">[上一頁](deploy-containers-azure.md)
>[下一頁](other-deployment-options.md)</span><span class="sxs-lookup"><span data-stu-id="33bba-139">[Previous](deploy-containers-azure.md)
[Next](other-deployment-options.md)</span></span>
