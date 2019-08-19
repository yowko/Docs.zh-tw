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
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)

如果您的組織使用 Azure Vm, 即使您也使用 Windows 容器, 您仍在處理 IaaS。 這表示當您需要部署到負載平衡基礎結構中的多個 Vm 時, 會處理可高度擴充應用程式的基礎結構作業、VM OS 修補程式和基礎結構複雜度。 在 Azure VM 中使用 Windows 容器的主要案例如下:

- **開發/測試環境**:雲端中的 VM 非常適合用於雲端中的開發和測試。 根據您的需求, 您可以快速建立或停止環境。

- **小型和中型的擴充性需求**:在您的生產環境中可能只需要幾個 Vm 的情況下, 管理少量的 Vm 可能會很實惠, 直到您可以移至更先進的 PaaS 環境, 例如協調器。

- **具有現有部署工具的生產環境**:您可能會從內部部署環境進行移動, 其中已投資工具來對 Vm 或裸機伺服器進行複雜的部署 (例如 Puppet 或類似的工具)。 若要移至雲端, 並對生產環境部署程式進行最少的變更, 您可以繼續使用這些工具來部署至 Azure Vm。 不過, 您會想要使用 Windows 容器作為部署單位, 以改善部署體驗。

>[!div class="step-by-step"]
>[上一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[下一頁](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
