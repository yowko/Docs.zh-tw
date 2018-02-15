---
title: "當部署到 Azure Vm （IaaS 雲端） 的 Windows 容器"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |當部署到 Azure Vm （IaaS 雲端） 的 Windows 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 832faed135d5b8ec9f8ad0a6ca82b5fac0273284
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>當部署到 Azure Vm （IaaS 雲端） 的 Windows 容器

如果您的組織使用 Azure Vm，即使您也正在使用 Windows 容器，但您仍是 IaaS 處理。 當您需要將部署到多個負載平衡的基礎結構中的 Vm 時，這表示具有高擴充性的應用程式該處理基礎結構作業、 VM OS 修補程式和基礎結構的複雜度。 在 Azure VM 中使用 Windows 容器的主要案例包括：

-   **開發/測試環境**： 雲端中的 VM 也非常適合用於開發和測試在雲端中。 您可以快速建立，或停止環境，根據您的需求。

-   **小型和中型延展性需要**： 在案例中，您可能需要幾 Vm，您的生產環境，管理少數的 Vm 可能價格合理直到您可以將它移至更進階的 PaaS 環境，例如 orchestrators。

-   **實際執行環境與現有的部署工具**： 您可能會從您投資中 Vm 或裸機伺服器 （例如 Puppet 或類似工具） 來讓複雜的部署工具的內部部署環境移動。 若要移至雲端最少變更生產環境部署程序，您可能會繼續使用這些工具來部署至 Azure Vm。 不過，您會想要使用 Windows 容器做為部署的單位，來改善部署經驗。

>[!div class="step-by-step"]
[上一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[下一頁](when-to-deploy-windows-containers-to-service-fabric.md)
