---
title: 將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |將 Windows 容器部署至 Azure Vm （IaaS 雲端） 的時機
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 51217e2c94fd9727c8f7907e791cdebaec98f14f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011953"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="a7b3c-103">將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)</span><span class="sxs-lookup"><span data-stu-id="a7b3c-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="a7b3c-104">如果您的組織使用 Azure Vm，即使您也正在使用 Windows 容器，但您仍是使用 IaaS 時的處理。</span><span class="sxs-lookup"><span data-stu-id="a7b3c-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="a7b3c-105">當您需要部署負載平衡的基礎結構中的多個 vm 時，這表示可高度擴充的應用程式的該處理基礎結構作業、 VM OS 修補程式和基礎結構的複雜性。</span><span class="sxs-lookup"><span data-stu-id="a7b3c-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="a7b3c-106">在 Azure VM 中使用 Windows 容器的主要案例包括：</span><span class="sxs-lookup"><span data-stu-id="a7b3c-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="a7b3c-107">**開發/測試環境**:在雲端中的 VM 非常適合開發和測試雲端中項目。</span><span class="sxs-lookup"><span data-stu-id="a7b3c-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="a7b3c-108">您可以快速建立，或視需要停止環境。</span><span class="sxs-lookup"><span data-stu-id="a7b3c-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="a7b3c-109">**小型和中型的延展性需求**:在案例中，您可能需要幾次的 Vm，為您的生產環境，管理少量的 Vm 可能是經濟實惠直到您可以將它移到更進階的 PaaS 環境，例如協調器。</span><span class="sxs-lookup"><span data-stu-id="a7b3c-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="a7b3c-110">**與現有的部署工具的生產環境**:您可能會從您已投資對 Vm 或裸機伺服器 （例如 Puppet 或類似工具） 進行複雜的部署工具 中的內部部署環境移動。</span><span class="sxs-lookup"><span data-stu-id="a7b3c-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="a7b3c-111">若要移至雲端，幾乎不需要變更實際執行環境的部署程序，您可能會繼續使用這些工具來部署至 Azure Vm。</span><span class="sxs-lookup"><span data-stu-id="a7b3c-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="a7b3c-112">不過，您會想要使用 Windows 容器作為部署單位，以改善部署經驗。</span><span class="sxs-lookup"><span data-stu-id="a7b3c-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a7b3c-113">[上一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[下一頁](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="a7b3c-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>