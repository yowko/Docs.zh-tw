---
title: 調整容器和無伺服器應用程式的規模
description: 使用 Azure Kubernetes Service 來調整雲端原生應用程式，以符合使用者需求。
ms.date: 05/13/2020
ms.openlocfilehash: edf56ba50ba391e06e588d682918cd473a2cf374
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165975"
---
# <a name="scaling-containers-and-serverless-applications"></a><span data-ttu-id="abf2e-103">調整容器和無伺服器應用程式的規模</span><span class="sxs-lookup"><span data-stu-id="abf2e-103">Scaling containers and serverless applications</span></span>

<span data-ttu-id="abf2e-104">有兩種方式可以調整應用程式：向上或向外擴充。前者是指將容量新增至單一資源，而後者則是指新增更多資源以增加容量。</span><span class="sxs-lookup"><span data-stu-id="abf2e-104">There are two ways to scale an application: up or out. The former refers to adding capacity to a single resource, while the latter refers to adding more resources to increase capacity.</span></span>

## <a name="the-simple-solution-scaling-up"></a><span data-ttu-id="abf2e-105">簡單的解決方案：向上擴充</span><span class="sxs-lookup"><span data-stu-id="abf2e-105">The simple solution: scaling up</span></span>

<span data-ttu-id="abf2e-106">使用更高的 CPU、記憶體、磁片 i/o 速度和網路 i/o 速度來升級現有的主機伺服器，就稱為*相應增加。*</span><span class="sxs-lookup"><span data-stu-id="abf2e-106">Upgrading an existing host server with increased CPU, memory, disk I/O speed, and network I/O speed is known as *scaling up*.</span></span> <span data-ttu-id="abf2e-107">相應增加雲端原生應用程式牽涉到從雲端廠商選擇更多可用的資源。</span><span class="sxs-lookup"><span data-stu-id="abf2e-107">Scaling up a cloud-native application involves choosing more capable resources from the cloud vendor.</span></span> <span data-ttu-id="abf2e-108">例如，您可以在 Kubernetes 叢集中使用較大的 Vm 來建立新的節點集區。</span><span class="sxs-lookup"><span data-stu-id="abf2e-108">For example, you can a new node pool with larger VMs in your Kubernetes cluster.</span></span> <span data-ttu-id="abf2e-109">然後，將容器化服務遷移至新的集區。</span><span class="sxs-lookup"><span data-stu-id="abf2e-109">Then, migrate your containerized services to the new pool.</span></span>

<span data-ttu-id="abf2e-110">無伺服器應用程式會從專用的 app service 方案中選擇高階函式 [方案](/azure/azure-functions/functions-scale) 或 premium 實例大小來擴大規模。</span><span class="sxs-lookup"><span data-stu-id="abf2e-110">Serverless apps scale up by choosing the [premium Functions plan](/azure/azure-functions/functions-scale) or premium instance sizes from a dedicated app service plan.</span></span>

## <a name="scaling-out-cloud-native-apps"></a><span data-ttu-id="abf2e-111">相應放大雲端原生應用程式</span><span class="sxs-lookup"><span data-stu-id="abf2e-111">Scaling out cloud-native apps</span></span>

<span data-ttu-id="abf2e-112">雲端原生應用程式通常會遇到大量的需求變動，而且需要一段時間才能進行調整。</span><span class="sxs-lookup"><span data-stu-id="abf2e-112">Cloud-native applications often experience large fluctuations in demand and require scale on a moment's notice.</span></span> <span data-ttu-id="abf2e-113">它們偏好相應放大。相應放大是以水準方式完成，方法是將 (稱為節點) 或應用程式實例的其他電腦新增至現有的叢集。</span><span class="sxs-lookup"><span data-stu-id="abf2e-113">They favor scaling out. Scaling out is done horizontally by adding additional machines (called nodes) or application instances to an existing cluster.</span></span> <span data-ttu-id="abf2e-114">在 Kubernetes 中，您可以調整應用程式的設定，以手動調整 (例如調整 [節點集](/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually) 區) 或透過自動調整。</span><span class="sxs-lookup"><span data-stu-id="abf2e-114">In Kubernetes, you can scale manually by adjusting configuration settings for the app (for example, [scaling a node pool](/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)), or through autoscaling.</span></span>

<span data-ttu-id="abf2e-115">AKS 叢集可透過下列兩種方式之一自動調整：</span><span class="sxs-lookup"><span data-stu-id="abf2e-115">AKS clusters can autoscale in one of two ways:</span></span>

<span data-ttu-id="abf2e-116">首先， [水準 Pod 自動調整程式](/azure/aks/tutorial-kubernetes-scale#autoscale-pods) 會監視資源需求，並自動調整您的 Pod 複本以符合此需求。</span><span class="sxs-lookup"><span data-stu-id="abf2e-116">First, the [Horizontal Pod Autoscaler](/azure/aks/tutorial-kubernetes-scale#autoscale-pods) monitors resource demand and automatically scales your POD replicas to meet it.</span></span> <span data-ttu-id="abf2e-117">當流量增加時，會自動布建額外的複本，以向外延展您的服務。</span><span class="sxs-lookup"><span data-stu-id="abf2e-117">When traffic increases, additional replicas are automatically provisioned to scale out your services.</span></span> <span data-ttu-id="abf2e-118">同樣地，當需求減少時，它們會被移除以相應縮小您的服務。</span><span class="sxs-lookup"><span data-stu-id="abf2e-118">Likewise, when demand decreases, they're removed to scale-in your services.</span></span> <span data-ttu-id="abf2e-119">您可以定義要調整規模的度量，例如 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="abf2e-119">You define the metric on which to scale, for example, CPU usage.</span></span> <span data-ttu-id="abf2e-120">您也可以指定要執行之複本的最小和最大數目。</span><span class="sxs-lookup"><span data-stu-id="abf2e-120">You can also specify the minimum and maximum number of replicas to run.</span></span> <span data-ttu-id="abf2e-121">AKS 會監視該度量並據以調整。</span><span class="sxs-lookup"><span data-stu-id="abf2e-121">AKS monitors that metric and scales accordingly.</span></span>

<span data-ttu-id="abf2e-122">接下來， [AKS Cluster 自動調整程式](/azure/aks/cluster-autoscaler) 功能可讓您自動調整跨 Kubernetes 叢集的計算節點，以滿足需求。</span><span class="sxs-lookup"><span data-stu-id="abf2e-122">Next, the [AKS Cluster Autoscaler](/azure/aks/cluster-autoscaler) feature enables you to automatically scale compute nodes across a Kubernetes cluster to meet demand.</span></span> <span data-ttu-id="abf2e-123">使用此功能時，您可以在需要更多計算容量時，自動將新的 Vm 新增至基礎 Azure 虛擬機器擴展集。</span><span class="sxs-lookup"><span data-stu-id="abf2e-123">With it, you can automatically add new VMs to the underlying Azure Virtual Machine Scale Set whenever more compute capacity of is required.</span></span> <span data-ttu-id="abf2e-124">當不再需要節點時，它也會移除節點。</span><span class="sxs-lookup"><span data-stu-id="abf2e-124">It also removes nodes when no longer required.</span></span>

<span data-ttu-id="abf2e-125">圖3-13 顯示這兩個調整服務之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="abf2e-125">Figure 3-13 shows the relationship between these two scaling services.</span></span>

![相應放大 App Service 計畫。](./media/aks-cluster-autoscaler.png)

<span data-ttu-id="abf2e-127">**圖 3-13**。</span><span class="sxs-lookup"><span data-stu-id="abf2e-127">**Figure 3-13**.</span></span> <span data-ttu-id="abf2e-128">相應放大 App Service 計畫。</span><span class="sxs-lookup"><span data-stu-id="abf2e-128">Scaling out an App Service plan.</span></span>

<span data-ttu-id="abf2e-129">共同作業可確保最佳的容器實例和計算節點數目，以支援變動需求。</span><span class="sxs-lookup"><span data-stu-id="abf2e-129">Working together, both ensure an optimal number of container instances and compute nodes to support fluctuating demand.</span></span> <span data-ttu-id="abf2e-130">水準 pod 自動調整程式會將所需的 pod 數目優化。</span><span class="sxs-lookup"><span data-stu-id="abf2e-130">The horizontal pod autoscaler optimizes the number of pods required.</span></span> <span data-ttu-id="abf2e-131">叢集自動調整程式會將所需的節點數目優化。</span><span class="sxs-lookup"><span data-stu-id="abf2e-131">The cluster autoscaler optimizes the number of nodes required.</span></span>

### <a name="scaling-azure-functions"></a><span data-ttu-id="abf2e-132">調整 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="abf2e-132">Scaling Azure Functions</span></span>

<span data-ttu-id="abf2e-133">Azure Functions 視需要自動相應放大。</span><span class="sxs-lookup"><span data-stu-id="abf2e-133">Azure Functions automatically scale out upon demand.</span></span> <span data-ttu-id="abf2e-134">系統會根據觸發的事件數目，動態配置和移除伺服器資源。</span><span class="sxs-lookup"><span data-stu-id="abf2e-134">Server resources are dynamically allocated and removed based on the number of triggered events.</span></span> <span data-ttu-id="abf2e-135">您只需針對函式執行時使用的計算資源付費。</span><span class="sxs-lookup"><span data-stu-id="abf2e-135">You're only charged for compute resources consumed when your functions run.</span></span> <span data-ttu-id="abf2e-136">計費是依據執行次數、執行時間和使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="abf2e-136">Billing is based upon the number of executions, execution time, and memory used.</span></span>

<span data-ttu-id="abf2e-137">雖然預設取用方案為大部分的應用程式提供經濟實惠且可調整的解決方案，但 premium 選項可讓開發人員彈性地自訂 Azure Functions 需求。</span><span class="sxs-lookup"><span data-stu-id="abf2e-137">While the default consumption plan provides an economical and scalable solution for most apps, the premium option allows developers flexibility for custom Azure Functions requirements.</span></span> <span data-ttu-id="abf2e-138">升級至高階方案可讓您控制實例大小、預先準備就緒的實例 (，以避免) 和專用 Vm 的冷啟動延遲。</span><span class="sxs-lookup"><span data-stu-id="abf2e-138">Upgrading to the premium plan provides control over instance sizes, pre-warmed instances (to avoid cold start delays), and dedicated VMs.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="abf2e-139">[上一個](deploy-containers-azure.md) 
>[下一步](other-deployment-options.md)</span><span class="sxs-lookup"><span data-stu-id="abf2e-139">[Previous](deploy-containers-azure.md)
[Next](other-deployment-options.md)</span></span>
