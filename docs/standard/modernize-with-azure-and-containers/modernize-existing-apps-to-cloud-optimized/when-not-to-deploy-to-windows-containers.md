---
title: 不要部署至 Windows 容器的時機
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |無法將部署至 Windows 容器的時機
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: c5d8f50c7b9967eba0ec01c9e864a02b6a3b201a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012005"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="821b7-103">不要部署至 Windows 容器的時機</span><span class="sxs-lookup"><span data-stu-id="821b7-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="821b7-104">Windows 容器不支援某些 Windows 技術。</span><span class="sxs-lookup"><span data-stu-id="821b7-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="821b7-105">在這些情況下，您仍需要將移轉至標準 Vm，通常會有只以 Windows 和 IIS。</span><span class="sxs-lookup"><span data-stu-id="821b7-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="821b7-106">不支援在 Windows 容器中，自 2018 年起的案例：</span><span class="sxs-lookup"><span data-stu-id="821b7-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="821b7-107">Microsoft Message Queuing (MSMQ) 目前只可在 Windows 容器，根據 Windows Server v1803 版本中，但不是在任何先前的版本。</span><span class="sxs-lookup"><span data-stu-id="821b7-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="821b7-108">UserVoice 要求論壇</span><span class="sxs-lookup"><span data-stu-id="821b7-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="821b7-109">討論論壇</span><span class="sxs-lookup"><span data-stu-id="821b7-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="821b7-110">Microsoft Distributed Transaction Coordinator (MSDTC) 目前不支援在 Windows 容器中。</span><span class="sxs-lookup"><span data-stu-id="821b7-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="821b7-111">GitHub 問題</span><span class="sxs-lookup"><span data-stu-id="821b7-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="821b7-112">Microsoft Office 目前不支援容器。</span><span class="sxs-lookup"><span data-stu-id="821b7-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="821b7-113">UserVoice 要求論壇</span><span class="sxs-lookup"><span data-stu-id="821b7-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="821b7-114">UI 應用程式 （用戶端應用程式以視覺化的使用者介面中） 不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="821b7-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="821b7-115">Windows 基礎結構角色 (DNS、 DHCP、 DC、 NTP、 列印、 檔案伺服器，IAM 等等) 不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="821b7-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="821b7-116">如需其他不支援的案例和社群的要求，請參閱 UserVoice 論壇適用於 Windows 容器： <https://windowsserver.uservoice.com/forums/304624-containers>。</span><span class="sxs-lookup"><span data-stu-id="821b7-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="821b7-117">其他資源</span><span class="sxs-lookup"><span data-stu-id="821b7-117">Additional resources</span></span>

- <span data-ttu-id="821b7-118">**Azure 中虛擬機器和容器**</span><span class="sxs-lookup"><span data-stu-id="821b7-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="821b7-119">[上一頁](deploy-existing-net-apps-as-windows-containers.md)
> [下一頁](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="821b7-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
