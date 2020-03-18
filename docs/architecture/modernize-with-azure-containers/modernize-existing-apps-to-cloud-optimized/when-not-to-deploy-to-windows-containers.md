---
title: 不要部署至 Windows 容器的時機
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |何時不部署到 Windows 容器
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577951"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>不要部署至 Windows 容器的時機

某些 Windows 技術不受 Windows 容器的支援。 在這些情況下，您仍然需要遷移到標準 VM，通常只需使用 Windows 和 IIS。

截至 2018 年 5 月，Windows 容器中不支援的案例：

- Microsoft 訊息佇列 （MSMQ） 目前僅在基於 Windows Server v1803 版本的 Windows 容器中可用，但在任何其他以前的版本中不可用。

  - [使用者語音請求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [討論論壇](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- 當前在 Windows 容器中不支援 Microsoft 分散式交易協調器 （MSDTC）。

  - [GitHub 問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- 微軟 Office 當前不支援容器。

  - [使用者語音請求論壇](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- 不支援 UI 應用（具有可視使用者介面的用戶端應用）。

- 不支援 Windows 基礎結構角色（DNS、DHCP、DC、NTP、PRINT、檔案伺服器、IAM 等）。

有關社區的其他不支援的方案和請求，請參閱 Windows 容器的使用者語音論壇： <https://windowsserver.uservoice.com/forums/304624-containers>。

### <a name="additional-resources"></a>其他資源

- **Azure 中的虛擬機器和容器**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [上一個](deploy-existing-net-apps-as-windows-containers.md)
> [下一個](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
