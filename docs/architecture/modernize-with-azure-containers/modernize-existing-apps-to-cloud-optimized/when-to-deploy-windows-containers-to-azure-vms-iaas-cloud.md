---
title: 將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |將 Windows 容器部署至 Azure Vm 的時機 (IaaS 雲端)
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577901"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="5b57a-103">將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)</span><span class="sxs-lookup"><span data-stu-id="5b57a-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="5b57a-104">如果您的組織使用 Azure Vm, 即使您也使用 Windows 容器, 您仍在處理 IaaS。</span><span class="sxs-lookup"><span data-stu-id="5b57a-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="5b57a-105">這表示當您需要部署到負載平衡基礎結構中的多個 Vm 時, 會處理可高度擴充應用程式的基礎結構作業、VM OS 修補程式和基礎結構複雜度。</span><span class="sxs-lookup"><span data-stu-id="5b57a-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="5b57a-106">在 Azure VM 中使用 Windows 容器的主要案例如下:</span><span class="sxs-lookup"><span data-stu-id="5b57a-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

- <span data-ttu-id="5b57a-107">**開發/測試環境**:雲端中的 VM 非常適合用於雲端中的開發和測試。</span><span class="sxs-lookup"><span data-stu-id="5b57a-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="5b57a-108">根據您的需求, 您可以快速建立或停止環境。</span><span class="sxs-lookup"><span data-stu-id="5b57a-108">You can rapidly create or stop the environment depending on your needs.</span></span>

- <span data-ttu-id="5b57a-109">**小型和中型的擴充性需求**:在您的生產環境中可能只需要幾個 Vm 的情況下, 管理少量的 Vm 可能會很實惠, 直到您可以移至更先進的 PaaS 環境, 例如協調器。</span><span class="sxs-lookup"><span data-stu-id="5b57a-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

- <span data-ttu-id="5b57a-110">**具有現有部署工具的生產環境**:您可能會從內部部署環境進行移動, 其中已投資工具來對 Vm 或裸機伺服器進行複雜的部署 (例如 Puppet 或類似的工具)。</span><span class="sxs-lookup"><span data-stu-id="5b57a-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="5b57a-111">若要移至雲端, 並對生產環境部署程式進行最少的變更, 您可以繼續使用這些工具來部署至 Azure Vm。</span><span class="sxs-lookup"><span data-stu-id="5b57a-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="5b57a-112">不過, 您會想要使用 Windows 容器作為部署單位, 以改善部署體驗。</span><span class="sxs-lookup"><span data-stu-id="5b57a-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5b57a-113">[上一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[下一頁](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="5b57a-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>
