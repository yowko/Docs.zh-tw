---
title: "不要將部署到 Windows 容器的時機"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |不要將部署到 Windows 容器的時機"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 538cb518cd169f42b3e8b7324ca108a1d366137a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="when-not-to-deploy-to-windows-containers"></a>不要將部署到 Windows 容器的時機

Windows 容器不支援某些 Windows 技術。 在這些情況下，您仍然要移轉到標準的 Vm，通常只以 Windows 和 IIS。

不支援在 Windows 容器中，為準，mid 2017 案例：

-   Microsoft Message Queuing (MSMQ) 目前不支援在 Windows 容器中。

    -   [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [討論區論壇](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft Distributed Transaction Coordinator (MSDTC) 目前不支援在 Windows 容器中

    -   [GitHub 問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office 目前不支援容器

    -   [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

其他不支援的案例及社群中的要求，請參閱 UserVoice 論壇 Windows 容器： <https://windowsserver.uservoice.com/forums/304624-containers>。

### <a name="additional-resources"></a>其他資源

-   **虛擬機器和 Azure 中的容器**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[上一頁](deploy-existing-net-apps-as-windows-containers.md)
[下一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
