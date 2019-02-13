---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: 了解如何部署應用程式使用 Azure Kubernetes 服務。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 984a72c9ca8883b338d10fdaa826a6007580372d
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221476"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>部署到 Azure Kubernetes Service (AKS)

您可以搭配 AKS 使用您慣用的用戶端的作業系統互動，這裡我們示範如何使用 Microsoft Windows 和內嵌的版本的 Windows，在 Ubuntu Linux 使用 Bash 命令。

使用 AKS 之前所必須具備的必要條件如下：

- Linux 或 Mac 開發電腦
- Windows 開發電腦
  - 啟用在 Windows 上的開發人員模式
  - 適用於 Linux 的 Windows 子系統
- 在上安裝 azure CLI [Windows、 Mac 或 Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)

> [!NOTE]
> 若要尋找完整相關資訊：
>
> Azure CLI: [https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest](https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest)
>
> 適用於 Linux 的 Windows 子系統： [https://docs.microsoft.com/windows/wsl/about](https://docs.microsoft.com/windows/wsl/about)

## <a name="create-the-aks-environment-in-azure"></a>在 Azure 中建立的 AKS 環境

有數種方式可建立 AKS 環境。 也可以使用 Azure CLI 命令，或使用 Azure 入口網站完成。

這裡您可以瀏覽一些範例使用 Azure CLI 來建立叢集和 Azure 入口網站中檢閱的結果。 您也需要在您的開發電腦上的 Kubectl 和 Docker。  

## <a name="create-the-aks-cluster"></a>建立 AKS 叢集

建立 AKS 叢集，使用下列命令：

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

建立作業完成後，您可以看到在 Azure 入口網站中建立的 AKS:

資源群組中：

![Azure AKS 資源群組的瀏覽器檢視。](media/aks-resource-group-view.png)

**圖 4-17**： 從 Azure AKS 資源群組檢視。

AKS 叢集：

![AKS 資源群組的瀏覽器檢視。](media/aks-cluster-view.png)

**圖 4-18**. 從 Azure AKS 檢視。

您也可以檢視建立使用的節點`Azure-CLI`和`Kubectl`。

首先，取得認證：

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![上述命令輸出的主控台：合併"MsSampleK8Cluster 為 /root/.kube/config 中目前的內容。](media/get-credentials-command-result.png)

**圖 4-19**. `aks get-credentials` 命令的結果。

然後，從 Kubectl 取得節點：

```console
kubectl get nodes
```

![上述命令輸出的主控台：節點狀態、 存留期 （時間執行），與版本的清單](media/kubectl-get-nodes-command-result.png)

**圖 4-20**： `kubectl get nodes` 命令的結果。

>[!div class="step-by-step"]
>[上一頁](orchestrate-high-scalability-availability.md)
>[下一頁](docker-apps-development-environment.md)
