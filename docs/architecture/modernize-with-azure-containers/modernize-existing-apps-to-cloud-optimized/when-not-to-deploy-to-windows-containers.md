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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="7bf56-103">不要部署至 Windows 容器的時機</span><span class="sxs-lookup"><span data-stu-id="7bf56-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="7bf56-104">Windows 容器不支援某些 Windows 技術。</span><span class="sxs-lookup"><span data-stu-id="7bf56-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="7bf56-105">在這些情況下, 您仍然需要遷移到標準 Vm, 通常只會使用 Windows 和 IIS。</span><span class="sxs-lookup"><span data-stu-id="7bf56-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="7bf56-106">Windows 容器中不支援的案例, 從 2018 5 月:</span><span class="sxs-lookup"><span data-stu-id="7bf56-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="7bf56-107">Microsoft Message Queuing (MSMQ) 目前僅適用于以 Windows Server v1803 版本為基礎的 Windows 容器, 但在任何其他舊版中則否。</span><span class="sxs-lookup"><span data-stu-id="7bf56-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="7bf56-108">UserVoice 要求論壇</span><span class="sxs-lookup"><span data-stu-id="7bf56-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="7bf56-109">討論論壇</span><span class="sxs-lookup"><span data-stu-id="7bf56-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="7bf56-110">Windows 容器中目前不支援 Microsoft 分散式交易協調器 (MSDTC)。</span><span class="sxs-lookup"><span data-stu-id="7bf56-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="7bf56-111">GitHub 問題</span><span class="sxs-lookup"><span data-stu-id="7bf56-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="7bf56-112">Microsoft Office 目前不支援容器。</span><span class="sxs-lookup"><span data-stu-id="7bf56-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="7bf56-113">UserVoice 要求論壇</span><span class="sxs-lookup"><span data-stu-id="7bf56-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="7bf56-114">UI 應用程式 (具有視覺化使用者介面的用戶端應用程式) 不是支援的案例。</span><span class="sxs-lookup"><span data-stu-id="7bf56-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="7bf56-115">Windows 基礎結構角色 (DNS、DHCP、DC、NTP、列印、檔案伺服器、IAM 等) 不是支援的案例。</span><span class="sxs-lookup"><span data-stu-id="7bf56-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="7bf56-116">如需其他不支援的案例和來自社區的要求, 請參閱適用于 Windows 容器的<https://windowsserver.uservoice.com/forums/304624-containers>UserVoice 論壇:。</span><span class="sxs-lookup"><span data-stu-id="7bf56-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7bf56-117">其他資源</span><span class="sxs-lookup"><span data-stu-id="7bf56-117">Additional resources</span></span>

- <span data-ttu-id="7bf56-118">**Azure 中的虛擬機器和容器**</span><span class="sxs-lookup"><span data-stu-id="7bf56-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="7bf56-119">[上一頁](deploy-existing-net-apps-as-windows-containers.md)
> [下一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="7bf56-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
