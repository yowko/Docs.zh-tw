---
title: 當 Azure 容器執行個體 (ACI) 部署 Windows 容器
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |當 Azure 容器執行個體 (ACI) 部署 Windows 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957948"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>當 Azure 容器執行個體 (ACI) 部署 Windows 容器

Azure 容器執行個體主要價值主張是以立即開始，您可以將容器部署它，而且您不需要維護該環境，您不需要升級/修補程式 underlaying 作業系統或 Vm，所有透明的而且您只部署已備妥要使用環境的容器。

原因和案例時，您會想要使用 ACI 類似的主要案例搭配使用 Azure Vm 和容器，因此基本上，使用 Azure 容器執行個體的主要案例包括：

-   **開發/測試案例**
-   **工作自動化**
-   **CI/CD 代理程式**
-   **小型/小數位數批次處理**
-   **簡單 web 應用程式**

簡單的 web 應用程式案例是普通的 ACI 狀況，但納入考量，因為 ACI 中只能有單一容器每個執行個體的容器映像，您不需要高可用性，並只具有有限的延展性。

不過，即使 ACI 會被視為基礎結構，因為它只提供單一容器執行個體，是一大優勢，相較於一般的 Azure Vm 與 Windows Server。 ACI，只要將容器部署到自我維護的環境與您只需支付這些容器。 您不需要維護/更新/修補的 Vm，所以較佳 platform 大部分的情況下，您也可以使用 Vm 與容器。 使用 ACI 直截了當，您只要部署容器，來建立您剛部署容器在 VM 環境不需要。

Azure 容器執行個體 (ACI) 的主要優點為：

-   執行的容器，而不需要管理伺服器
-   增加靈活性視容器
-   部署至雲端與前所未有的簡單和速度的容器，使用單一命令。 
-   安全 hypervisor 隔離的應用程式

簡單地說，ACI 與您可以快速而不需要管理虛擬機器或需要了解新的工具開發應用程式。 只要您的應用程式，在容器中，在雲端中執行它。

>[!div class="step-by-step"]
[上一頁](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[下一頁](when-to-deploy-windows-containers-to-service-fabric.md)
