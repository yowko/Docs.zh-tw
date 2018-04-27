---
title: 當部署到 Azure Vm （IaaS 雲端） 的 Windows 容器
description: 容器化的.NET 應用程式的.NET Microservices 架構 |當部署到 Azure Vm （IaaS 雲端） 的 Windows 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d1a9f0593b4b84cbe25da9e4164f4ecbe8513831
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="507b4-103">當部署到 Azure Vm （IaaS 雲端） 的 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="507b4-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="507b4-104">如果您的組織使用 Azure Vm，即使您也正在使用 Windows 容器，但您仍是 IaaS 處理。</span><span class="sxs-lookup"><span data-stu-id="507b4-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="507b4-105">當您需要將部署到多個負載平衡的基礎結構中的 Vm 時，這表示具有高擴充性的應用程式該處理基礎結構作業、 VM OS 修補程式和基礎結構的複雜度。</span><span class="sxs-lookup"><span data-stu-id="507b4-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="507b4-106">在 Azure VM 中使用 Windows 容器的主要案例包括：</span><span class="sxs-lookup"><span data-stu-id="507b4-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="507b4-107">**開發/測試環境**： 雲端中的 VM 也非常適合用於開發和測試在雲端中。</span><span class="sxs-lookup"><span data-stu-id="507b4-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="507b4-108">您可以快速建立，或停止環境，根據您的需求。</span><span class="sxs-lookup"><span data-stu-id="507b4-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="507b4-109">**小型和中型延展性需要**： 在案例中，您可能需要幾 Vm，您的生產環境，管理少數的 Vm 可能價格合理直到您可以將它移至更進階的 PaaS 環境，例如 orchestrators。</span><span class="sxs-lookup"><span data-stu-id="507b4-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="507b4-110">**實際執行環境與現有的部署工具**： 您可能會從您投資中 Vm 或裸機伺服器 （例如 Puppet 或類似工具） 來讓複雜的部署工具的內部部署環境移動。</span><span class="sxs-lookup"><span data-stu-id="507b4-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="507b4-111">若要移至雲端最少變更生產環境部署程序，您可能會繼續使用這些工具來部署至 Azure Vm。</span><span class="sxs-lookup"><span data-stu-id="507b4-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="507b4-112">不過，您會想要使用 Windows 容器做為部署的單位，來改善部署經驗。</span><span class="sxs-lookup"><span data-stu-id="507b4-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="507b4-113">[上一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[下一頁](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="507b4-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
