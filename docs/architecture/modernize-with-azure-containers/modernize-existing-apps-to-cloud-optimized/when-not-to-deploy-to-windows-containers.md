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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="bbfb1-103">不要部署至 Windows 容器的時機</span><span class="sxs-lookup"><span data-stu-id="bbfb1-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="bbfb1-104">某些 Windows 技術不受 Windows 容器的支援。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="bbfb1-105">在這些情況下，您仍然需要遷移到標準 VM，通常只需使用 Windows 和 IIS。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="bbfb1-106">截至 2018 年 5 月，Windows 容器中不支援的案例：</span><span class="sxs-lookup"><span data-stu-id="bbfb1-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="bbfb1-107">Microsoft 訊息佇列 （MSMQ） 目前僅在基於 Windows Server v1803 版本的 Windows 容器中可用，但在任何其他以前的版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="bbfb1-108">使用者語音請求論壇</span><span class="sxs-lookup"><span data-stu-id="bbfb1-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="bbfb1-109">討論論壇</span><span class="sxs-lookup"><span data-stu-id="bbfb1-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="bbfb1-110">當前在 Windows 容器中不支援 Microsoft 分散式交易協調器 （MSDTC）。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="bbfb1-111">GitHub 問題</span><span class="sxs-lookup"><span data-stu-id="bbfb1-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="bbfb1-112">微軟 Office 當前不支援容器。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="bbfb1-113">使用者語音請求論壇</span><span class="sxs-lookup"><span data-stu-id="bbfb1-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="bbfb1-114">不支援 UI 應用（具有可視使用者介面的用戶端應用）。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="bbfb1-115">不支援 Windows 基礎結構角色（DNS、DHCP、DC、NTP、PRINT、檔案伺服器、IAM 等）。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="bbfb1-116">有關社區的其他不支援的方案和請求，請參閱 Windows 容器的使用者語音論壇： <https://windowsserver.uservoice.com/forums/304624-containers>。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bbfb1-117">其他資源</span><span class="sxs-lookup"><span data-stu-id="bbfb1-117">Additional resources</span></span>

- <span data-ttu-id="bbfb1-118">**Azure 中的虛擬機器和容器**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="bbfb1-119">[上一個](deploy-existing-net-apps-as-windows-containers.md)
> [下一個](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="bbfb1-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
