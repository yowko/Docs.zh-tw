---
title: 不要部署至 Windows 容器的時機
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |無法將部署至 Windows 容器的時機
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638903"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>不要部署至 Windows 容器的時機

Windows 容器不支援某些 Windows 技術。 在這些情況下，您仍需要將移轉至標準 Vm，通常會有只以 Windows 和 IIS。

不支援在 Windows 容器中，自 2018 年起的案例：

- Microsoft Message Queuing (MSMQ) 目前只可在 Windows 容器，根據 Windows Server v1803 版本中，但不是在任何先前的版本。

  - [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [討論論壇](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft Distributed Transaction Coordinator (MSDTC) 目前不支援在 Windows 容器中。

  - [GitHub 問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office 目前不支援容器。

  - [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- UI 應用程式 （用戶端應用程式以視覺化的使用者介面中） 不支援的案例。

- Windows 基礎結構角色 (DNS、 DHCP、 DC、 NTP、 列印、 檔案伺服器，IAM 等等) 不支援的案例。

如需其他不支援的案例和社群的要求，請參閱 UserVoice 論壇適用於 Windows 容器： <https://windowsserver.uservoice.com/forums/304624-containers>。

### <a name="additional-resources"></a>其他資源

- **Azure 中虛擬機器和容器**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [上一頁](deploy-existing-net-apps-as-windows-containers.md)
> [下一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
