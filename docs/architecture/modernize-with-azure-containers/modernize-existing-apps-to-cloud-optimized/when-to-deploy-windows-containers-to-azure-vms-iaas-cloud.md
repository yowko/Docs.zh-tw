---
title: 將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |何時將 Windows 容器部署到 Azure VM（IaaS 雲）
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577901"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>將 Windows 容器部署至 Azure VM 的時機 (IaaS 雲端)

如果您的組織正在使用 Azure VM，即使您也在使用 Windows 容器，您仍在處理 IaaS。 這意味著，當您需要在負載平衡的基礎結構中部署到多個 VM 時，處理高度可擴展應用程式的基礎結構操作、VM OS 修補程式和基礎結構複雜性。 在 Azure VM 中使用 Windows 容器的主要方案是：

- **開發/測試環境**：雲中的 VM 非常適合在雲中的開發和測試。 您可以根據您的需要快速建立或停止環境。

- **中小型可擴充性需求**：在生產環境中可能只需要幾個 VM 的情況下，管理少量 VM 可能經濟實惠，直到可以遷移到更高級的 PaaS 環境（如協調器）。

- **使用現有部署工具的生產環境**：您可能正在從已投資工具進行複雜部署到 VM 或裸機伺服器（如 Puppet 或類似工具）的本地環境。 要以最少的更改遷移到雲，可以繼續使用這些工具部署到 Azure VM。 但是，您需要使用 Windows 容器作為部署單元，以改善部署體驗。

>[!div class="step-by-step"]
>[上一個](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[下一個](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
