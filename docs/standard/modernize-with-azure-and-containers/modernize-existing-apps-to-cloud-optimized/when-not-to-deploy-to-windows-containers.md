---
title: 不要將部署到 Windows 容器的時機
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |不要將部署到 Windows 容器的時機
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 819f32955ff019414bef8820d17d272eddc11bf8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957958"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>不要將部署到 Windows 容器的時機

Windows 容器不支援某些 Windows 技術。 在這些情況下，您仍然要移轉到標準的 Vm，通常只以 Windows 和 IIS。

不支援在 Windows 容器中，為準，可能 2018年案例： 

-   Microsoft Message Queuing (MSMQ) 目前僅可用在 Windows 容器，根據 Windows Server v1803 版本中，但不是在任何先前的版本。 

    -   [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [討論區論壇](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft Distributed Transaction Coordinator (MSDTC) 目前不支援在 Windows 容器中。

    -   [GitHub 問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office 目前不支援容器。

    -   [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   UI 的應用程式 （用戶端應用程式以視覺化的使用者介面中） 不支援的案例。

-   Windows 基礎結構角色 (DNS、 DHCP、 DC、 NTP，列印，檔案伺服器，IAM 等) 不支援的案例。


其他不支援的案例及社群中的要求，請參閱 UserVoice 論壇 Windows 容器： <https://windowsserver.uservoice.com/forums/304624-containers>。

### <a name="additional-resources"></a>其他資源

-   **虛擬機器和 Azure 中的容器**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[上一頁](deploy-existing-net-apps-as-windows-containers.md)
[下一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
