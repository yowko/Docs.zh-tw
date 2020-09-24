---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: 了解如何使用 Azure Kubernetes Service 部署應用程式。
ms.date: 08/06/2020
ms.openlocfilehash: ba9887c0a4837c16a60ebeb006416c0fa8c105e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163592"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>部署到 Azure Kubernetes Service (AKS)

您可以使用慣用的用戶端作業系統， (Windows、macOS 或 Linux) 搭配 Azure 命令列介面 (Azure CLI) 安裝來與 AKS 互動。 如需詳細資訊，請參閱適用于可用環境的 [Azure CLI 檔](/cli/azure/?view=azure-cli-latest) 和 [安裝指南](/cli/azure/install-azure-cli?view=azure-cli-latest) 。

## <a name="create-the-aks-environment-in-azure"></a>在 Azure 中建立開發 AKS 環境

您可以使用幾種方式建立 AKS 環境。 您可以使用 Azure CLI 命令或使用 Azure 入口網站來完成此操作。

您可以在這裡探索使用 Azure CLI 建立叢集的一些範例，以及用來檢查結果的 Azure 入口網站。 您的開發電腦也必須具備 Kubectl 和 Docker。

## <a name="create-the-aks-cluster"></a>建立 AKS 叢集

使用下列命令建立 AKS 叢集 (資源群組必須存在) ：

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> `--node-vm-size`和 `--node-count` 參數值對於範例/開發應用程式來說夠好用。

建立作業完成後，您可以看到：

- 在初始資源群組中建立的 AKS 叢集
- 新的相關資源群組，其中包含與 AKS 叢集相關的資源，如下列影像所示。

具有 AKS 叢集的初始資源群組：

![AKS 資源群組的瀏覽器檢視。](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

**圖 4-17**： Azure 的 AKS 資源群組檢視。

AKS 叢集資源群組：

![Azure AKS 資源群組的瀏覽器檢視。](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

**圖 4-18**. Azure 的 AKS 檢視。

> [!IMPORTANT]
> 一般而言，您不需要修改 AKS 叢集資源群組中的資源。 例如，當您刪除 AKS 叢集時，會刪除資源群組。

您也可以使用 `Azure CLI` 和 `Kubectl` 檢視建立的節點。

首先，取得認證：

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![上述命令的主控台輸出：合併 "aks" 作為/home/miguel/.kube/config. 中的目前內容](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

**圖 4-19**. `aks get-credentials` 命令的結果。

然後，從 Kubectl 取得節點：

```console
kubectl get nodes
```

![上述命令的主控台輸出：具有狀態的節點清單、執行) 的存留期 (時間，以及版本](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

**圖 4-20**： `kubectl get nodes` 命令的結果。

> [!div class="step-by-step"]
> [上一個](orchestrate-high-scalability-availability.md) 
> [下一步](docker-apps-development-environment.md)
