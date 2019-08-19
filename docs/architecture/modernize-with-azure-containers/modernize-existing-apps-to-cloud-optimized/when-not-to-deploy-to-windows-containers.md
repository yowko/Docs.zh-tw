---
title: 不要部署至 Windows 容器的時機
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |不部署至 Windows 容器的時機
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577951"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>不要部署至 Windows 容器的時機

Windows 容器不支援某些 Windows 技術。 在這些情況下, 您仍然需要遷移到標準 Vm, 通常只會使用 Windows 和 IIS。

Windows 容器中不支援的案例, 從 2018 5 月:

- Microsoft Message Queuing (MSMQ) 目前僅適用于以 Windows Server v1803 版本為基礎的 Windows 容器, 但在任何其他舊版中則否。

  - [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [討論論壇](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Windows 容器中目前不支援 Microsoft 分散式交易協調器 (MSDTC)。

  - [GitHub 問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office 目前不支援容器。

  - [UserVoice 要求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- UI 應用程式 (具有視覺化使用者介面的用戶端應用程式) 不是支援的案例。

- Windows 基礎結構角色 (DNS、DHCP、DC、NTP、列印、檔案伺服器、IAM 等) 不是支援的案例。

如需其他不支援的案例和來自社區的要求, 請參閱適用于 Windows 容器的<https://windowsserver.uservoice.com/forums/304624-containers>UserVoice 論壇:。

### <a name="additional-resources"></a>其他資源

- **Azure 中的虛擬機器和容器**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [上一頁](deploy-existing-net-apps-as-windows-containers.md)
> [下一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
