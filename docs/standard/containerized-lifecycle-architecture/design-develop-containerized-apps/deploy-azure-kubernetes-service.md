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
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="731d5-103">部署到 Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="731d5-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="731d5-104">您可以搭配 AKS 使用您慣用的用戶端的作業系統互動，這裡我們示範如何使用 Microsoft Windows 和內嵌的版本的 Windows，在 Ubuntu Linux 使用 Bash 命令。</span><span class="sxs-lookup"><span data-stu-id="731d5-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="731d5-105">使用 AKS 之前所必須具備的必要條件如下：</span><span class="sxs-lookup"><span data-stu-id="731d5-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="731d5-106">Linux 或 Mac 開發電腦</span><span class="sxs-lookup"><span data-stu-id="731d5-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="731d5-107">Windows 開發電腦</span><span class="sxs-lookup"><span data-stu-id="731d5-107">Windows development machine</span></span>
  - <span data-ttu-id="731d5-108">啟用在 Windows 上的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="731d5-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="731d5-109">適用於 Linux 的 Windows 子系統</span><span class="sxs-lookup"><span data-stu-id="731d5-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="731d5-110">在上安裝 azure CLI [Windows、 Mac 或 Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span><span class="sxs-lookup"><span data-stu-id="731d5-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span></span>

> [!NOTE]
> <span data-ttu-id="731d5-111">若要尋找完整相關資訊：</span><span class="sxs-lookup"><span data-stu-id="731d5-111">To find complete information about:</span></span>
>
> <span data-ttu-id="731d5-112">Azure CLI: [https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest](https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest)</span><span class="sxs-lookup"><span data-stu-id="731d5-112">Azure-CLI: [https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest](https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest)</span></span>
>
> <span data-ttu-id="731d5-113">適用於 Linux 的 Windows 子系統： [https://docs.microsoft.com/windows/wsl/about](https://docs.microsoft.com/windows/wsl/about)</span><span class="sxs-lookup"><span data-stu-id="731d5-113">Windows Subsystem for Linux: [https://docs.microsoft.com/windows/wsl/about](https://docs.microsoft.com/windows/wsl/about)</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="731d5-114">在 Azure 中建立的 AKS 環境</span><span class="sxs-lookup"><span data-stu-id="731d5-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="731d5-115">有數種方式可建立 AKS 環境。</span><span class="sxs-lookup"><span data-stu-id="731d5-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="731d5-116">也可以使用 Azure CLI 命令，或使用 Azure 入口網站完成。</span><span class="sxs-lookup"><span data-stu-id="731d5-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="731d5-117">這裡您可以瀏覽一些範例使用 Azure CLI 來建立叢集和 Azure 入口網站中檢閱的結果。</span><span class="sxs-lookup"><span data-stu-id="731d5-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="731d5-118">您也需要在您的開發電腦上的 Kubectl 和 Docker。</span><span class="sxs-lookup"><span data-stu-id="731d5-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="731d5-119">建立 AKS 叢集</span><span class="sxs-lookup"><span data-stu-id="731d5-119">Create the AKS cluster</span></span>

<span data-ttu-id="731d5-120">建立 AKS 叢集，使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="731d5-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="731d5-121">建立作業完成後，您可以看到在 Azure 入口網站中建立的 AKS:</span><span class="sxs-lookup"><span data-stu-id="731d5-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="731d5-122">資源群組中：</span><span class="sxs-lookup"><span data-stu-id="731d5-122">The resource group:</span></span>

![Azure AKS 資源群組的瀏覽器檢視。](media/aks-resource-group-view.png)

<span data-ttu-id="731d5-124">**圖 4-17**：</span><span class="sxs-lookup"><span data-stu-id="731d5-124">**Figure 4-17**.</span></span> <span data-ttu-id="731d5-125">從 Azure AKS 資源群組檢視。</span><span class="sxs-lookup"><span data-stu-id="731d5-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="731d5-126">AKS 叢集：</span><span class="sxs-lookup"><span data-stu-id="731d5-126">The AKS cluster:</span></span>

![AKS 資源群組的瀏覽器檢視。](media/aks-cluster-view.png)

<span data-ttu-id="731d5-128">**圖 4-18**.</span><span class="sxs-lookup"><span data-stu-id="731d5-128">**Figure 4-18**.</span></span> <span data-ttu-id="731d5-129">從 Azure AKS 檢視。</span><span class="sxs-lookup"><span data-stu-id="731d5-129">AKS view from Azure.</span></span>

<span data-ttu-id="731d5-130">您也可以檢視建立使用的節點`Azure-CLI`和`Kubectl`。</span><span class="sxs-lookup"><span data-stu-id="731d5-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="731d5-131">首先，取得認證：</span><span class="sxs-lookup"><span data-stu-id="731d5-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![上述命令輸出的主控台：合併"MsSampleK8Cluster 為 /root/.kube/config 中目前的內容。](media/get-credentials-command-result.png)

<span data-ttu-id="731d5-133">**圖 4-19**.</span><span class="sxs-lookup"><span data-stu-id="731d5-133">**Figure 4-19**.</span></span> <span data-ttu-id="731d5-134">`aks get-credentials` 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="731d5-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="731d5-135">然後，從 Kubectl 取得節點：</span><span class="sxs-lookup"><span data-stu-id="731d5-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![上述命令輸出的主控台：節點狀態、 存留期 （時間執行），與版本的清單](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="731d5-137">**圖 4-20**：</span><span class="sxs-lookup"><span data-stu-id="731d5-137">**Figure 4-20**.</span></span> <span data-ttu-id="731d5-138">`kubectl get nodes` 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="731d5-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="731d5-139">[上一頁](orchestrate-high-scalability-availability.md)
>[下一頁](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="731d5-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
