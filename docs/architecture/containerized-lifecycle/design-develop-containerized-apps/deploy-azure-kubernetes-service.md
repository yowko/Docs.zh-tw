---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: 了解如何使用 Azure Kubernetes Service 部署應用程式。
ms.date: 08/06/2020
ms.openlocfilehash: b4deb9906e0fece7fb611b6988df576e8b07fe46
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916096"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="52522-103">部署到 Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="52522-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="52522-104">您可以使用慣用的用戶端作業系統， (Windows、macOS 或 Linux) 與已安裝 Azure 命令列介面 (Azure CLI) 來與 AKS 互動。</span><span class="sxs-lookup"><span data-stu-id="52522-104">You can interact with AKS using your preferred client operating system (Windows, macOS, or Linux) with Azure command-line interface(Azure CLI) installed.</span></span> <span data-ttu-id="52522-105">如需詳細資訊，請參閱適用于可用環境的[Azure CLI 檔](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)和[安裝指南](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)。</span><span class="sxs-lookup"><span data-stu-id="52522-105">For more details, refer [Azure CLI documentation](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) and [Installation guide](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) for the available environments.</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="52522-106">在 Azure 中建立開發 AKS 環境</span><span class="sxs-lookup"><span data-stu-id="52522-106">Create the AKS environment in Azure</span></span>

<span data-ttu-id="52522-107">您可以使用幾種方式建立 AKS 環境。</span><span class="sxs-lookup"><span data-stu-id="52522-107">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="52522-108">您可以使用 Azure CLI 命令或使用 Azure 入口網站來完成此作業。</span><span class="sxs-lookup"><span data-stu-id="52522-108">It can be done by using Azure CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="52522-109">您可以在這裡探索一些使用 Azure CLI 建立叢集的範例，以及用來檢查結果的 Azure 入口網站。</span><span class="sxs-lookup"><span data-stu-id="52522-109">Here you can explore some examples using the Azure CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="52522-110">您的開發電腦也必須具備 Kubectl 和 Docker。</span><span class="sxs-lookup"><span data-stu-id="52522-110">You also need to have Kubectl and Docker in your development machine.</span></span>

## <a name="create-the-aks-cluster"></a><span data-ttu-id="52522-111">建立 AKS 叢集</span><span class="sxs-lookup"><span data-stu-id="52522-111">Create the AKS cluster</span></span>

<span data-ttu-id="52522-112">使用此命令建立 AKS 叢集 (資源群組必須存在) ：</span><span class="sxs-lookup"><span data-stu-id="52522-112">Create the AKS cluster using this command (the resource group must exist):</span></span>

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> <span data-ttu-id="52522-113">`--node-vm-size`和 `--node-count` 參數值夠適合用於範例/開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="52522-113">The `--node-vm-size` and `--node-count` parameter values are good enough for a sample/dev application.</span></span>

<span data-ttu-id="52522-114">建立作業完成後，您可以看到：</span><span class="sxs-lookup"><span data-stu-id="52522-114">After the creation job finishes, you can see:</span></span>

- <span data-ttu-id="52522-115">在初始資源群組中建立的 AKS 叢集</span><span class="sxs-lookup"><span data-stu-id="52522-115">The AKS cluster created in the initial resource group</span></span>
- <span data-ttu-id="52522-116">新的相關資源群組，其中包含與 AKS 叢集相關的資源，如下列影像所示。</span><span class="sxs-lookup"><span data-stu-id="52522-116">A new, related resource group, containing the resources related to the AKS cluster, as show in the following images.</span></span>

<span data-ttu-id="52522-117">具有 AKS 叢集的初始資源群組：</span><span class="sxs-lookup"><span data-stu-id="52522-117">The initial resource group, with the AKS cluster:</span></span>

![AKS 資源群組的瀏覽器檢視。](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

<span data-ttu-id="52522-119">**圖 4-17**：</span><span class="sxs-lookup"><span data-stu-id="52522-119">**Figure 4-17**.</span></span> <span data-ttu-id="52522-120">Azure 的 AKS 資源群組檢視。</span><span class="sxs-lookup"><span data-stu-id="52522-120">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="52522-121">AKS 叢集資源群組：</span><span class="sxs-lookup"><span data-stu-id="52522-121">The AKS cluster resource group:</span></span>

![Azure AKS 資源群組的瀏覽器檢視。](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

<span data-ttu-id="52522-123">**圖 4-18**.</span><span class="sxs-lookup"><span data-stu-id="52522-123">**Figure 4-18**.</span></span> <span data-ttu-id="52522-124">Azure 的 AKS 檢視。</span><span class="sxs-lookup"><span data-stu-id="52522-124">AKS view from Azure.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52522-125">一般來說，您應該不需要修改 AKS 叢集資源群組中的資源。</span><span class="sxs-lookup"><span data-stu-id="52522-125">In general, you shouldn't need to modify the resources in the AKS cluster resource group.</span></span> <span data-ttu-id="52522-126">例如，當您刪除 AKS 叢集時，會刪除資源群組。</span><span class="sxs-lookup"><span data-stu-id="52522-126">For example, the resource group is deleted when you delete the AKS cluster.</span></span>

<span data-ttu-id="52522-127">您也可以使用 `Azure CLI` 和 `Kubectl` 檢視建立的節點。</span><span class="sxs-lookup"><span data-stu-id="52522-127">You can also view the node created using `Azure CLI` and `Kubectl`.</span></span>

<span data-ttu-id="52522-128">首先，取得認證：</span><span class="sxs-lookup"><span data-stu-id="52522-128">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![上述命令的主控台輸出：合併「探索-docker-aks」作為/home/miguel/.kube/config. 中的目前內容](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

<span data-ttu-id="52522-130">**圖 4-19**.</span><span class="sxs-lookup"><span data-stu-id="52522-130">**Figure 4-19**.</span></span> <span data-ttu-id="52522-131">`aks get-credentials` 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="52522-131">`aks get-credentials` command result.</span></span>

<span data-ttu-id="52522-132">然後，從 Kubectl 取得節點：</span><span class="sxs-lookup"><span data-stu-id="52522-132">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![上述命令的主控台輸出：具有狀態的節點清單、執行) 的年齡 (時間，以及版本](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

<span data-ttu-id="52522-134">**圖 4-20**：</span><span class="sxs-lookup"><span data-stu-id="52522-134">**Figure 4-20**.</span></span> <span data-ttu-id="52522-135">`kubectl get nodes` 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="52522-135">`kubectl get nodes` command result.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="52522-136">[上一個](orchestrate-high-scalability-availability.md) 
> [下一步](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="52522-136">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
