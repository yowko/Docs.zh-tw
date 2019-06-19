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
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="f1b24-103">部署到 Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="f1b24-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="f1b24-104">您可以使用慣用的用戶端作業系統與 AKS 互動，這裡我們示範如何搭配 Bash 命令使用 Microsoft Windows 和 Windows 中的內嵌版本 Ubuntu Linux 來執行此作業。</span><span class="sxs-lookup"><span data-stu-id="f1b24-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="f1b24-105">使用 AKS 之前的必要條件如下：</span><span class="sxs-lookup"><span data-stu-id="f1b24-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="f1b24-106">Linux 或 Mac 開發電腦</span><span class="sxs-lookup"><span data-stu-id="f1b24-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="f1b24-107">Windows 開發電腦</span><span class="sxs-lookup"><span data-stu-id="f1b24-107">Windows development machine</span></span>
  - <span data-ttu-id="f1b24-108">啟用 Windows 的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="f1b24-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="f1b24-109">適用於 Linux 的 Windows 子系統</span><span class="sxs-lookup"><span data-stu-id="f1b24-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="f1b24-110">在 [Windows、Mac 或 Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) 上安裝 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="f1b24-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span></span>

> [!NOTE]
> <span data-ttu-id="f1b24-111">若要尋找下列完整相關資訊：</span><span class="sxs-lookup"><span data-stu-id="f1b24-111">To find complete information about:</span></span>
>
> <span data-ttu-id="f1b24-112">Azure CLI：<https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span><span class="sxs-lookup"><span data-stu-id="f1b24-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span></span>
>
> <span data-ttu-id="f1b24-113">適用於 Linux 的 Windows 子系統：<https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="f1b24-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="f1b24-114">在 Azure 中建立開發 AKS 環境</span><span class="sxs-lookup"><span data-stu-id="f1b24-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="f1b24-115">您可以使用幾種方式建立 AKS 環境。</span><span class="sxs-lookup"><span data-stu-id="f1b24-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="f1b24-116">您也可以使用 Azure CLI 命令，或使用 Azure 入口網站來完成。</span><span class="sxs-lookup"><span data-stu-id="f1b24-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="f1b24-117">這裡提供一些範例，供您探索如何使用 Azure CLI 來建立叢集，並使用 Azure 入口網站來檢閱結果。</span><span class="sxs-lookup"><span data-stu-id="f1b24-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="f1b24-118">您的開發電腦也必須具備 Kubectl 和 Docker。</span><span class="sxs-lookup"><span data-stu-id="f1b24-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="f1b24-119">建立 AKS 叢集</span><span class="sxs-lookup"><span data-stu-id="f1b24-119">Create the AKS cluster</span></span>

<span data-ttu-id="f1b24-120">使用此命令建立 AKS 叢集：</span><span class="sxs-lookup"><span data-stu-id="f1b24-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="f1b24-121">建立作業完成後，Azure 入口網站即會顯示已建立的 AKS：</span><span class="sxs-lookup"><span data-stu-id="f1b24-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="f1b24-122">資源群組：</span><span class="sxs-lookup"><span data-stu-id="f1b24-122">The resource group:</span></span>

![Azure AKS 資源群組的瀏覽器檢視。](media/aks-resource-group-view.png)

<span data-ttu-id="f1b24-124">**圖 4-17**：</span><span class="sxs-lookup"><span data-stu-id="f1b24-124">**Figure 4-17**.</span></span> <span data-ttu-id="f1b24-125">Azure 的 AKS 資源群組檢視。</span><span class="sxs-lookup"><span data-stu-id="f1b24-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="f1b24-126">AKS 叢集：</span><span class="sxs-lookup"><span data-stu-id="f1b24-126">The AKS cluster:</span></span>

![AKS 資源群組的瀏覽器檢視。](media/aks-cluster-view.png)

<span data-ttu-id="f1b24-128">**圖 4-18**.</span><span class="sxs-lookup"><span data-stu-id="f1b24-128">**Figure 4-18**.</span></span> <span data-ttu-id="f1b24-129">Azure 的 AKS 檢視。</span><span class="sxs-lookup"><span data-stu-id="f1b24-129">AKS view from Azure.</span></span>

<span data-ttu-id="f1b24-130">您也可以使用 `Azure-CLI` 和 `Kubectl` 檢視建立的節點。</span><span class="sxs-lookup"><span data-stu-id="f1b24-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="f1b24-131">首先，取得認證：</span><span class="sxs-lookup"><span data-stu-id="f1b24-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![上述命令的主控台輸出：已將 "MsSampleK8Cluster 合併為 /root/.kube/config 中的目前內容。](media/get-credentials-command-result.png)

<span data-ttu-id="f1b24-133">**圖 4-19**.</span><span class="sxs-lookup"><span data-stu-id="f1b24-133">**Figure 4-19**.</span></span> <span data-ttu-id="f1b24-134">`aks get-credentials` 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="f1b24-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="f1b24-135">然後，從 Kubectl 取得節點：</span><span class="sxs-lookup"><span data-stu-id="f1b24-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![上述命令的主控台輸出：具有狀態、存留期 (執行時間) 與版本的節點清單](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="f1b24-137">**圖 4-20**：</span><span class="sxs-lookup"><span data-stu-id="f1b24-137">**Figure 4-20**.</span></span> <span data-ttu-id="f1b24-138">`kubectl get nodes` 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="f1b24-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f1b24-139">[上一頁](orchestrate-high-scalability-availability.md)
>[下一頁](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="f1b24-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
