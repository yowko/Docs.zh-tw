---
title: '當您將 Windows 容器部署至 Azure 容器實例時 (ACI) '
description: '使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |當您將 Windows 容器部署至 Azure 容器實例時 (ACI) '
ms.date: 12/21/2020
ms.openlocfilehash: 556fe7cbec7d259db9ec886b777feda9eed09116
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025129"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>當您將 Windows 容器部署至 Azure 容器實例時 (ACI) 

Azure 容器實例的主要價值主張是您可以立即將容器部署到該環境，而且您不需要維護該環境，您就不需要升級/修補基礎作業系統或 Vm，而且全都是透明的，而且只是將容器部署到現成可用的環境。

當您使用 Azure Vm 搭配容器時，您想要使用 ACI 的原因和案例，基本上是使用 Azure 容器實例的主要案例如下：

- **開發/測試案例**
- **工作自動化**
- **CI/CD 代理程式**
- **小規模/調整批次處理**
- **簡單的 web 應用程式**

簡單的 web 應用程式案例是 ACI 的公平案例，但請考慮，因為在 ACI 中，每個容器映射只能有一個容器實例，您將不會有高可用性，而且只會有有限的擴充性。

不過，即使 ACI 被視為基礎結構，因為它只提供單一容器實例，相較于使用 Windows Server 的一般 Azure Vm，有相當大的好處。 使用 ACI，您只需將容器部署到自我維護環境中，就可以為這些容器付費。 您不需要維護/更新/修補 Vm，因此在大部分情況下，您可能會使用具有容器的 Vm，因此是更好的平臺。 使用 ACI 相當簡單，您只需要部署容器，就不需要建立您只部署容器的 VM 環境。

Azure 容器實例 (ACI) 的主要優點如下：

- 在不管理伺服器的情況下執行容器
- 隨選容器提高靈活性
- 透過單一命令，以前所未有的簡潔性和速度將容器部署至雲端。
- 使用虛擬程式隔離來保護應用程式

簡單地說，您可以透過 ACI 快速開發應用程式，而不需要管理虛擬機器或學習新工具。 它只是您在雲端中執行的應用程式，在容器中執行。

> [!div class="step-by-step"]
> [上一個](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md) 
> [下一步](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
