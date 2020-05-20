---
title: 調整容器和無伺服器應用程式的規模
description: 使用 Azure Kubernetes Service 調整雲端原生應用程式，以滿足使用者需求。
ms.date: 05/13/2020
ms.openlocfilehash: a5e1e8df785fd08901d9be41c0a06db35e09296b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613716"
---
# <a name="scaling-containers-and-serverless-applications"></a>調整容器和無伺服器應用程式的規模

有兩種方式可以調整應用程式：向上或向外。前者是指將容量新增至單一資源，而後者則是指新增更多資源以增加容量。

## <a name="the-simple-solution-scaling-up"></a>簡單的解決方案：向上延展

升級具有增加的 CPU、記憶體、磁片 i/o 速度和網路 i/o 速度的現有主機伺服器，也稱為相應*增加*。 相應增加雲端原生應用程式包含從雲端廠商選擇更強大的資源。 例如，您可以在 Kubernetes 叢集中具有較大 Vm 的新節點集區。 然後，將您的容器化服務遷移至新的集區。

無伺服器應用程式：從專用的 app service 方案選擇高階[函數計畫](https://docs.microsoft.com/azure/azure-functions/functions-scale)或高階實例大小，以相應增加規模。

## <a name="scaling-out-cloud-native-apps"></a>相應放大雲端原生應用程式

雲端原生應用程式通常會遇到大量的需求波動，而且需要一段時間才能進行調整。 它們偏好相應放大。向外延展會藉由將其他電腦（稱為節點）或應用程式實例新增至現有的叢集來進行水準調整。 在 Kubernetes 中，您可以藉由調整應用程式的設定（例如，調整[節點集](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)區）或透過自動調整來手動調整。

AKS 叢集可以透過下列兩種方式的其中一種進行自動調整：

首先，[水準 Pod 自動調整程式](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale#autoscale-pods)會監視資源需求，並自動調整您的 Pod 複本以符合它。 當流量增加時，會自動布建額外的複本，以相應放大您的服務。 同樣地，當需求降低時，就會將它們移除以相應縮小您的服務。 您可以定義要調整的度量，例如 CPU 使用量。 您也可以指定要執行之複本的最小和最大數目。 AKS 會監視該度量，並據以調整。

接下來， [AKS 叢集自動調整程式](https://docs.microsoft.com/azure/aks/cluster-autoscaler)功能可讓您自動調整跨 Kubernetes 叢集的計算節點，以符合需求。 有了此功能，您就可以在需要更多的計算容量時，自動將新的 Vm 新增至基礎的 Azure 虛擬機器擴展集。 它也會在不再需要時移除節點。

圖3-13 顯示這兩個調整服務之間的關聯性。

![相應放大 App Service 計畫。](./media/aks-cluster-autoscaler.png)

**圖 3-13**。 相應放大 App Service 計畫。

共同作業可確保容器實例和計算節點的最佳數目，以支援變動的需求。 水準 pod 自動調整程式會優化所需的 pod 數目。 叢集自動調整程式會優化所需的節點數目。

### <a name="scaling-azure-functions"></a>調整 Azure Functions

Azure Functions 視需要自動相應放大。 系統會根據觸發事件的數目，動態配置和移除伺服器資源。 您只需支付函式執行時所耗用的計算資源費用。 計費是根據執行次數、執行時間和使用的記憶體。

雖然預設取用方案為大部分應用程式提供經濟實惠且可調整的解決方案，但 premium 選項可讓開發人員彈性自訂 Azure Functions 需求。 升級至 premium 方案可讓您控制實例大小、預先準備就緒的實例（以避免冷啟動延遲）和專用 Vm。

>[!div class="step-by-step"]
>[上一個](deploy-containers-azure.md) 
>[下一步](other-deployment-options.md)
