---
title: 將 Windows 容器部署至 Azure 容器實例 (ACI) 的時機
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |將 Windows 容器部署至 Azure 容器實例 (ACI) 的時機
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577931"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>將 Windows 容器部署至 Azure 容器實例 (ACI) 的時機

Azure 容器實例的主要價值主張是, 您可以立即將容器部署到該環境, 而不需要維護該環境, 您不需要升級/修補基礎作業系統或 Vm, 這一切都是透明的, 而且您剛部署容器進入立即可用的環境。

當您使用 Azure Vm 搭配容器時, 您會想要使用 ACI 的原因和案例, 基本上, 使用 Azure 容器實例的主要案例如下:

- **開發/測試案例**
- **任務自動化**
- **CI/CD 代理程式**
- **小型/調整批次處理**
- **簡單的 web 應用程式**

簡單的 web 應用程式案例是 ACI 的公平案例, 但請將其納入考慮, 因為在 ACI 中, 每個容器映射只能有一個容器實例, 所以您不會有高可用性, 而且只有有限的擴充性。

不過, 即使 ACI 被視為基礎結構, 因為它只提供單一容器實例, 相較于使用 Windows Server 的一般 Azure Vm, 這項優點相當大。 使用 ACI 時, 您只需將容器部署到自我維護的環境, 就能為這些容器付費。 您不需要維護/更新/修補 Vm, 因此在大部分情況下, 您可能會將 Vm 與容器搭配使用, 這是更好的平臺。 使用 ACI 是直接的, 您只要部署容器, 就不需要建立您剛部署容器的 VM 環境。

Azure 容器實例 (ACI) 的主要優點如下:

- 在不管理伺服器的情況下執行容器
- 使用容器隨選增加靈活性
- 使用單一命令, 以前所未有的簡單性和速度將容器部署到雲端。
- 以虛擬程式隔離來保護應用程式

簡單地說, 透過 ACI, 您可以快速開發應用程式, 而不需要管理虛擬機器或學習新工具。 它只是您在雲端中執行的應用程式, 位於容器中。

> [!div class="step-by-step"]
> [上一頁](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [下一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
