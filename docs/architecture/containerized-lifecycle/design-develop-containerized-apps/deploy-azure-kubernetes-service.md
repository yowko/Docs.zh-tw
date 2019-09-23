---
title: 協調微服務和多容器應用程式的高延展性和可用性
description: 了解如何使用 Azure Kubernetes Service 部署應用程式。
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182366"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="28987-103">部署到 Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="28987-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="28987-104">您可以使用慣用的用戶端作業系統與 AKS 互動，這裡我們示範如何搭配 Bash 命令使用 Microsoft Windows 和 Windows 中的內嵌版本 Ubuntu Linux 來執行此作業。</span><span class="sxs-lookup"><span data-stu-id="28987-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="28987-105">使用 AKS 之前的必要條件如下：</span><span class="sxs-lookup"><span data-stu-id="28987-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="28987-106">Linux 或 Mac 開發電腦</span><span class="sxs-lookup"><span data-stu-id="28987-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="28987-107">Windows 開發電腦</span><span class="sxs-lookup"><span data-stu-id="28987-107">Windows development machine</span></span>
  - <span data-ttu-id="28987-108">啟用 Windows 的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="28987-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="28987-109">適用于 Linux 的 Windows 子系統</span><span class="sxs-lookup"><span data-stu-id="28987-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="28987-110">在 [Windows、Mac 或 Linux](https://docs.microsoft.com/cli/azure/install-azure-cli) 上安裝 Azure CLI</span><span class="sxs-lookup"><span data-stu-id="28987-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="28987-111">若要尋找下列完整相關資訊：</span><span class="sxs-lookup"><span data-stu-id="28987-111">To find complete information about:</span></span>
>
> <span data-ttu-id="28987-112">Azure CLI：<https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="28987-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="28987-113">適用於 Linux 的 Windows 子系統：<https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="28987-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="28987-114">在 Azure 中建立開發 AKS 環境</span><span class="sxs-lookup"><span data-stu-id="28987-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="28987-115">您可以使用幾種方式建立 AKS 環境。</span><span class="sxs-lookup"><span data-stu-id="28987-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="28987-116">您也可以使用 Azure CLI 命令，或使用 Azure 入口網站來完成。</span><span class="sxs-lookup"><span data-stu-id="28987-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="28987-117">這裡提供一些範例，供您探索如何使用 Azure CLI 來建立叢集，並使用 Azure 入口網站來檢閱結果。</span><span class="sxs-lookup"><span data-stu-id="28987-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="28987-118">您的開發電腦也必須具備 Kubectl 和 Docker。</span><span class="sxs-lookup"><span data-stu-id="28987-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="28987-119">建立 AKS 叢集</span><span class="sxs-lookup"><span data-stu-id="28987-119">Create the AKS cluster</span></span>

<span data-ttu-id="28987-120">使用此命令建立 AKS 叢集：</span><span class="sxs-lookup"><span data-stu-id="28987-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="28987-121">建立作業完成後，Azure 入口網站即會顯示已建立的 AKS：</span><span class="sxs-lookup"><span data-stu-id="28987-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="28987-122">資源群組：</span><span class="sxs-lookup"><span data-stu-id="28987-122">The resource group:</span></span>

![Azure AKS 資源群組的瀏覽器檢視。](media/aks-resource-group-view.png)

<span data-ttu-id="28987-124">**圖 4-17**：</span><span class="sxs-lookup"><span data-stu-id="28987-124">**Figure 4-17**.</span></span> <span data-ttu-id="28987-125">Azure 的 AKS 資源群組檢視。</span><span class="sxs-lookup"><span data-stu-id="28987-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="28987-126">AKS 叢集：</span><span class="sxs-lookup"><span data-stu-id="28987-126">The AKS cluster:</span></span>

![AKS 資源群組的瀏覽器檢視。](media/aks-cluster-view.png)

<span data-ttu-id="28987-128">**圖 4-18**.</span><span class="sxs-lookup"><span data-stu-id="28987-128">**Figure 4-18**.</span></span> <span data-ttu-id="28987-129">Azure 的 AKS 檢視。</span><span class="sxs-lookup"><span data-stu-id="28987-129">AKS view from Azure.</span></span>

<span data-ttu-id="28987-130">您也可以使用 `Azure-CLI` 和 `Kubectl` 檢視建立的節點。</span><span class="sxs-lookup"><span data-stu-id="28987-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="28987-131">首先，取得認證：</span><span class="sxs-lookup"><span data-stu-id="28987-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![上述命令的主控台輸出：已將 "MsSampleK8Cluster 合併為 /root/.kube/config 中的目前內容。](media/get-credentials-command-result.png)

<span data-ttu-id="28987-133">**圖 4-19**.</span><span class="sxs-lookup"><span data-stu-id="28987-133">**Figure 4-19**.</span></span> <span data-ttu-id="28987-134">`aks get-credentials` 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="28987-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="28987-135">然後，從 Kubectl 取得節點：</span><span class="sxs-lookup"><span data-stu-id="28987-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![上述命令的主控台輸出：具有狀態、存留期 (執行時間) 與版本的節點清單](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="28987-137">**圖 4-20**：</span><span class="sxs-lookup"><span data-stu-id="28987-137">**Figure 4-20**.</span></span> <span data-ttu-id="28987-138">`kubectl get nodes` 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="28987-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="28987-139">[上一頁](orchestrate-high-scalability-availability.md)
>[下一頁](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="28987-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
