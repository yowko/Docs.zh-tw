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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="1877c-103">不要部署至 Windows 容器的時機</span><span class="sxs-lookup"><span data-stu-id="1877c-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="1877c-104">Windows 容器不支援某些 Windows 技術。</span><span class="sxs-lookup"><span data-stu-id="1877c-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="1877c-105">在這些情況下，您仍然需要遷移至標準 Vm，通常只需使用 Windows 和 IIS。</span><span class="sxs-lookup"><span data-stu-id="1877c-105">In those cases, you still need to migrate to the standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="1877c-106">Windows 容器中不支援的案例，從2018到5月：</span><span class="sxs-lookup"><span data-stu-id="1877c-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="1877c-107">Microsoft Message Queuing (MSMQ) 目前僅適用于以 Windows Server v1803 版本為基礎的 Windows 容器，而非任何其他先前的版本。</span><span class="sxs-lookup"><span data-stu-id="1877c-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="1877c-108">UserVoice 要求論壇</span><span class="sxs-lookup"><span data-stu-id="1877c-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="1877c-109">討論論壇</span><span class="sxs-lookup"><span data-stu-id="1877c-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="1877c-110">Windows 容器目前不支援 Microsoft Distributed Transaction Coordinator (MSDTC) 。</span><span class="sxs-lookup"><span data-stu-id="1877c-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="1877c-111">GitHub 問題</span><span class="sxs-lookup"><span data-stu-id="1877c-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="1877c-112">Microsoft Office 目前不支援容器。</span><span class="sxs-lookup"><span data-stu-id="1877c-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="1877c-113">UserVoice 要求論壇</span><span class="sxs-lookup"><span data-stu-id="1877c-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="1877c-114">UI 應用程式 (用戶端應用程式與視覺使用者介面) 不是支援的案例。</span><span class="sxs-lookup"><span data-stu-id="1877c-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="1877c-115">Windows 基礎結構角色 (DNS、DHCP、DC、NTP、列印、檔案伺服器、IAM 等 ) 不是支援的案例。</span><span class="sxs-lookup"><span data-stu-id="1877c-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="1877c-116">如需其他不支援案例和來自社區的要求，請參閱 Windows 容器的 UserVoice 論壇： <https://windowsserver.uservoice.com/forums/304624-containers> 。</span><span class="sxs-lookup"><span data-stu-id="1877c-116">For other nonsupported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1877c-117">其他資源</span><span class="sxs-lookup"><span data-stu-id="1877c-117">Additional resources</span></span>

- <span data-ttu-id="1877c-118">**Azure 中的虛擬機器和容器**</span><span class="sxs-lookup"><span data-stu-id="1877c-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="1877c-119">[上一個](deploy-existing-net-apps-as-windows-containers.md) 
> [下一步](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="1877c-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
