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
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)

如果您的組織使用 Azure Vm，即使您也正在使用 Windows 容器，但您仍是使用 IaaS 時的處理。 當您需要部署負載平衡的基礎結構中的多個 vm 時，這表示可高度擴充的應用程式的該處理基礎結構作業、 VM OS 修補程式和基礎結構的複雜性。 在 Azure VM 中使用 Windows 容器的主要案例包括：

-   **開發/測試環境**:在雲端中的 VM 非常適合開發和測試雲端中項目。 您可以快速建立，或視需要停止環境。

-   **小型和中型的延展性需求**:在案例中，您可能需要幾次的 Vm，為您的生產環境，管理少量的 Vm 可能是經濟實惠直到您可以將它移到更進階的 PaaS 環境，例如協調器。

-   **與現有的部署工具的生產環境**:您可能會從您已投資對 Vm 或裸機伺服器 （例如 Puppet 或類似工具） 進行複雜的部署工具 中的內部部署環境移動。 若要移至雲端，幾乎不需要變更實際執行環境的部署程序，您可能會繼續使用這些工具來部署至 Azure Vm。 不過，您會想要使用 Windows 容器作為部署單位，以改善部署經驗。

>[!div class="step-by-step"]
>[上一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[下一頁](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)