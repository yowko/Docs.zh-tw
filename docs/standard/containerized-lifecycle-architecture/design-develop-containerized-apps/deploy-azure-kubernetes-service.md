---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: 了解如何使用 Azure Kubernetes Service 部署應用程式。
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644678"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>部署到 Azure Kubernetes Service (AKS)

您可以使用慣用的用戶端作業系統與 AKS 互動，這裡我們示範如何搭配 Bash 命令使用 Microsoft Windows 和 Windows 中的內嵌版本 Ubuntu Linux 來執行此作業。

使用 AKS 之前的必要條件如下：

- Linux 或 Mac 開發電腦
- Windows 開發電腦
  - 啟用 Windows 的開發人員模式
  - 適用於 Linux 的 Windows 子系統
- 在 [Windows、Mac 或 Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) 上安裝 Azure CLI

> [!NOTE]
> 若要尋找下列完整相關資訊：
>
> Azure CLI：<https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest>
>
> 適用於 Linux 的 Windows 子系統：<https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>在 Azure 中建立開發 AKS 環境

您可以使用幾種方式建立 AKS 環境。 您也可以使用 Azure CLI 命令，或使用 Azure 入口網站來完成。

這裡提供一些範例，供您探索如何使用 Azure CLI 來建立叢集，並使用 Azure 入口網站來檢閱結果。 您的開發電腦也必須具備 Kubectl 和 Docker。  

## <a name="create-the-aks-cluster"></a>建立 AKS 叢集

使用此命令建立 AKS 叢集：

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

建立作業完成後，Azure 入口網站即會顯示已建立的 AKS：

資源群組：

![Azure AKS 資源群組的瀏覽器檢視。](media/aks-resource-group-view.png)

**圖 4-17**： Azure 的 AKS 資源群組檢視。

AKS 叢集：

![AKS 資源群組的瀏覽器檢視。](media/aks-cluster-view.png)

**圖 4-18**. Azure 的 AKS 檢視。

您也可以使用 `Azure-CLI` 和 `Kubectl` 檢視建立的節點。

首先，取得認證：

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![上述命令的主控台輸出：已將 "MsSampleK8Cluster 合併為 /root/.kube/config 中的目前內容。](media/get-credentials-command-result.png)

**圖 4-19**. `aks get-credentials` 命令的結果。

然後，從 Kubectl 取得節點：

```console
kubectl get nodes
```

![上述命令的主控台輸出：具有狀態、存留期 (執行時間) 與版本的節點清單](media/kubectl-get-nodes-command-result.png)

**圖 4-20**： `kubectl get nodes` 命令的結果。

>[!div class="step-by-step"]
>[上一頁](orchestrate-high-scalability-availability.md)
>[下一頁](docker-apps-development-environment.md)
