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
# <a name="scaling-containers-and-serverless-applications"></a>調整容器和無伺服器應用程式的規模

有兩種方式可以調整應用程式：向上或向外擴充。前者是指將容量新增至單一資源，而後者則是指新增更多資源以增加容量。

## <a name="the-simple-solution-scaling-up"></a>簡單的解決方案：向上擴充

使用更高的 CPU、記憶體、磁片 i/o 速度和網路 i/o 速度來升級現有的主機伺服器，就稱為*相應增加。* 相應增加雲端原生應用程式牽涉到從雲端廠商選擇更多可用的資源。 例如，您可以在 Kubernetes 叢集中使用較大的 Vm 來建立新的節點集區。 然後，將容器化服務遷移至新的集區。

無伺服器應用程式會從專用的 app service 方案中選擇高階函式 [方案](/azure/azure-functions/functions-scale) 或 premium 實例大小來擴大規模。

## <a name="scaling-out-cloud-native-apps"></a>相應放大雲端原生應用程式

雲端原生應用程式通常會遇到大量的需求變動，而且需要一段時間才能進行調整。 它們偏好相應放大。相應放大是以水準方式完成，方法是將 (稱為節點) 或應用程式實例的其他電腦新增至現有的叢集。 在 Kubernetes 中，您可以調整應用程式的設定，以手動調整 (例如調整 [節點集](/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually) 區) 或透過自動調整。

AKS 叢集可透過下列兩種方式之一自動調整：

首先， [水準 Pod 自動調整程式](/azure/aks/tutorial-kubernetes-scale#autoscale-pods) 會監視資源需求，並自動調整您的 Pod 複本以符合此需求。 當流量增加時，會自動布建額外的複本，以向外延展您的服務。 同樣地，當需求減少時，它們會被移除以相應縮小您的服務。 您可以定義要調整規模的度量，例如 CPU 使用量。 您也可以指定要執行之複本的最小和最大數目。 AKS 會監視該度量並據以調整。

接下來， [AKS Cluster 自動調整程式](/azure/aks/cluster-autoscaler) 功能可讓您自動調整跨 Kubernetes 叢集的計算節點，以滿足需求。 使用此功能時，您可以在需要更多計算容量時，自動將新的 Vm 新增至基礎 Azure 虛擬機器擴展集。 當不再需要節點時，它也會移除節點。

圖3-13 顯示這兩個調整服務之間的關聯性。

![相應放大 App Service 計畫。](./media/aks-cluster-autoscaler.png)

**圖 3-13**。 相應放大 App Service 計畫。

共同作業可確保最佳的容器實例和計算節點數目，以支援變動需求。 水準 pod 自動調整程式會將所需的 pod 數目優化。 叢集自動調整程式會將所需的節點數目優化。

### <a name="scaling-azure-functions"></a>調整 Azure Functions

Azure Functions 視需要自動相應放大。 系統會根據觸發的事件數目，動態配置和移除伺服器資源。 您只需針對函式執行時使用的計算資源付費。 計費是依據執行次數、執行時間和使用的記憶體。

雖然預設取用方案為大部分的應用程式提供經濟實惠且可調整的解決方案，但 premium 選項可讓開發人員彈性地自訂 Azure Functions 需求。 升級至高階方案可讓您控制實例大小、預先準備就緒的實例 (，以避免) 和專用 Vm 的冷啟動延遲。

>[!div class="step-by-step"]
>[上一個](deploy-containers-azure.md) 
>[下一步](other-deployment-options.md)
