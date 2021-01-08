---
title: 將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)
description: '使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |將 Windows 容器部署至 Azure Vm 的時機 (IaaS 雲端) '
ms.date: 12/21/2020
ms.openlocfilehash: 64ba53fa56227266ee0e61a128d18373a2dbbc93
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025090"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)

如果您的組織使用 Azure Vm，即使您也使用 Windows 容器，仍在處理 IaaS。 這表示當您需要在負載平衡的基礎結構中部署至多個 Vm 時，會處理高擴充性應用程式的基礎結構作業、VM 作業系統修補程式和基礎結構複雜度。 在 Azure VM 中使用 Windows 容器的主要案例如下：

- **開發/測試環境**：雲端中的 VM 最適合用於雲端中的開發和測試。 您可以根據自己的需求，快速建立或停止環境。

- **中小型的擴充性需求**：在您的生產環境中，您可能只需要幾個 vm 的案例中，在您可以移至更先進的 PaaS 環境（例如協調器）之前，管理幾部 vm 可能會很實惠。

- **具有現有部署工具的生產環境**：您可能會從已投資工具的內部部署環境中移動，以對 vm 或裸機伺服器 (例如 Puppet 或類似的工具) 進行複雜的部署。 若要以最少量的生產環境部署程式變更移至雲端，您可能會繼續使用這些工具來部署至 Azure Vm。 不過，您會想要使用 Windows 容器作為部署的單位，以改善部署體驗。

>[!div class="step-by-step"]
>[上一個](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md) 
>[下一步](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
