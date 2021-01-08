---
title: 不要部署至 Windows 容器的時機
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |不部署至 Windows 容器的時機
ms.date: 12/21/2020
ms.openlocfilehash: 4eea24ab8deb3719c778b45b3ddc1309277a3f50
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025169"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>不要部署至 Windows 容器的時機

Windows 容器不支援某些 Windows 技術。 在這些情況下，您仍然需要遷移至標準 Vm，通常只需使用 Windows 和 IIS。

Windows 容器中不支援的案例，從2018到5月：

- Microsoft Message Queuing (MSMQ) 目前僅適用于以 Windows Server v1803 版本為基礎的 Windows 容器，而非任何其他先前的版本。

  - [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [討論論壇](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Windows 容器目前不支援 Microsoft Distributed Transaction Coordinator (MSDTC) 。

  - [GitHub 問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office 目前不支援容器。

  - [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- UI 應用程式 (用戶端應用程式與視覺使用者介面) 不是支援的案例。

- Windows 基礎結構角色 (DNS、DHCP、DC、NTP、列印、檔案伺服器、IAM 等 ) 不是支援的案例。

如需其他不支援案例和來自社區的要求，請參閱 Windows 容器的 UserVoice 論壇： <https://windowsserver.uservoice.com/forums/304624-containers> 。

### <a name="additional-resources"></a>其他資源

- **Azure 中的虛擬機器和容器**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [上一個](deploy-existing-net-apps-as-windows-containers.md) 
> [下一步](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
