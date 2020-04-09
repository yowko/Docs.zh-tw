---
title: 何時將 Windows 容器部署到 Azure 容器實體 (ACI)
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |何時將 Windows 容器部署到 Azure 容器實體 (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 6c889db6f0475f24a196144c7fb62faec4c173ed
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989151"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>何時將 Windows 容器部署到 Azure 容器實體 (ACI)

Azure 容器實例的主要價值主張是,您可以立即向其部署容器,並且不需要維護該環境,無需升級/修補基礎操作系統或 VM,所有這些都是透明的,只需將容器部署到即用型環境中即可。

要使用 ACI 的原因和方案與將 Azure VM 與容器一起使用時的主要方案類似,因此,使用 Azure 容器實例的主要方案基本上是:

- **開發/測試機制**
- **工作自動化**
- **CI/CD 代理程式**
- **小規模/規模批量處理**
- **簡單的 Web 應用程式**

簡單的 Web 應用方案對於 ACI 來說是一個公平的方案,但考慮到在 ACI 中,每個容器映射只能有一個容器實例,因此您不會具有高可用性,並且只有有限的可擴充性。

但是,即使 ACI 被視為基礎結構,因為它只提供單個容器實例,但與具有 Windows Server 的常規 Azure VM 相比,也具有巨大的優勢。 使用 ACI,只需將容器部署到自我維護的環境中,只需為這些容器付費。 您無需維護/更新/修補 VM,因此對於大多數可能將 VM 與容器一起使用的方案來說,這是一個更好的平臺。 使用 ACI 是直接的,您只需部署一個容器,就無需創建僅部署容器的 VM 環境。

Azure 容器實例 (ACI) 的主要優點是:

- 執行容器而不管理伺服器
- 按需使用容器提高敏捷性
- 使用單個命令,以前所未有的簡單性和速度將容器部署到雲中。
- 使用虛擬機器管理程式隔離保護應用程式

簡而言之,藉助 ACI,您可以快速開發應用,而無需管理虛擬機或學習新工具。 它只是您的應用程式,在容器中,在雲中運行。

> [!div class="step-by-step"]
> [前一個](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [下一個](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
