---
title: 調整容器和無伺服器應用程式
description: 使用 Azure Kubernetes Service 調整雲端原生應用程式，藉由增加個別機器資源或增加應用程式叢集中的機器數目，以滿足使用者需求。
ms.date: 09/23/2019
ms.openlocfilehash: 2d0537fb3ed56beb4eccbf9b8c34a5d87793413b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184796"
---
# <a name="scaling-containers-and-serverless-applications"></a>調整容器和無伺服器應用程式

有兩種典型的方式可以調整應用程式：相應增加和相應放大。前者是指將功能新增至一部主機，而後者則是指新增到主機總數。 用來思考這種常見的比喻是如何讓自己和一些朋友橫跨城鎮。 如果只是一個 friend，您可以跳到您的兩個基座的賽車。 但如果有三或四個，您可能需要採用其中一個 SUVs 或 minivan，相應增加以提高容量。 不過，當您的總數最多會跳到一或多個時，您可能需要採用多個車輛（除非有人推動匯流排），這會示範藉由新增更多實例（在此案例中為更多車輛）來相應放大的概念。 讓我們來看看這如何適用于我們的應用程式。

## <a name="the-simple-solution-scaling-up"></a>簡單的解決方案：向上延展

升級現有伺服器以提供更多資源（CPU、記憶體、磁片 i/o 速度、網路 i/o 速度）的程式，稱為「相應*增加*」。 在雲端原生應用程式中，相應增加通常不是指購買和安裝實體電腦上的實際硬體，因此您可以從可用的選項清單中選擇更有能力的方案。 雲端原生應用程式通常會藉由修改用來裝載其 Kubernetes 節點集區中個別節點的虛擬機器（VM）大小進行相應增加。 [下一節](leverage-containers-orchestrators.md)會進一步說明節點、叢集和 pod 之類的 Kubernetes 概念。 Azure 支援各種同時執行[Windows](https://docs.microsoft.com/azure/virtual-machines/windows/sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json)和[Linux](https://docs.microsoft.com/azure/virtual-machines/linux/sizes)的 VM 大小。 若要以垂直方式調整您的應用程式，請建立具有較大節點 VM 大小的新節點集區，然後將工作負載遷移至新的集區。 這需要[AKS 叢集的多個節點](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)集區，這是一專案前處於預覽狀態的功能。 無伺服器應用程式會藉由選擇[premium 方案](https://docs.microsoft.com/azure/azure-functions/functions-scale)和 premium 實例大小，或選擇不同的專用 app service 方案來相應增加。

## <a name="scaling-out-cloud-native-apps"></a>相應放大雲端原生應用程式

雲端原生應用程式可將其他節點或 pod 新增至服務要求，以支援相應放大。 這可以藉由調整應用程式的設定（例如，調整[節點集](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)區）*或透過自動*調整來手動完成。 自動調整會調整應用程式所使用的資源，以回應需求，類似于控溫器如何藉由撥打額外的加熱或冷卻來回應溫度。 使用自動調整時，會停用手動縮放。

AKS 叢集可以透過下列兩種方式的其中一種進行調整：

- 叢集[自動調整程式](https://docs.microsoft.com/azure/aks/cluster-autoscaler)會監看因為資源限制而無法在節點上排程的 pod。 它會視需要新增其他節點。
- **水準 pod 自動調整程式**會使用 Kubernetes 叢集中的計量伺服器來監視 pod 的資源需求。 如果服務需要更多資源，自動調整程式會增加 pod 數目。

圖3-13 顯示這兩個調整服務之間的關聯性。

![相應放大 App Service 計畫。](./media/aks-cluster-autoscaler.png)

**圖 3-13**。 相應放大 App Service 計畫。

這些服務也可以視需要減少 pod 或節點的數目。 這兩項服務可以一起使用，而且通常會一起部署在叢集中。 合併時，水準 pod 自動調整程式著重于執行滿足應用程式需求所需的 pod 數目。 叢集自動調整程式著重于執行支援已排程 pod 所需的節點數目。

### <a name="scaling-azure-functions"></a>調整 Azure Functions

Azure Functions 會自動支援相應放大。預設取用方案會根據傳入的觸發事件數目，動態地新增（和移除）資源。 當您的函式執行時，您只需支付所使用的計算資源費用，取決於所使用的執行次數、執行時間和記憶體。 使用高階方案，您可以取得這些相同的功能，但您也可以控制使用的實例大小、已準備就緒的實例（以避免冷啟動延遲），以及設定要在其上執行函數的專用 Vm。 雖然預設設定應為大部分應用程式提供經濟實惠且可調整的解決方案，但 premium 選項可讓開發人員彈性自訂 Azure Functions 需求。

## <a name="references"></a>reference

- [AKS 多個節點集區](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [AKS Cluster 自動調整程式](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [教學課程：在 AKS 中調整應用程式](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Azure Functions 規模和裝載](https://docs.microsoft.com/azure/azure-functions/functions-scale)

>[!div class="step-by-step"]
>[上一頁](deploy-containers-azure.md)
>[下一頁](other-deployment-options.md)
